---
name: Test-and-Deploy
description: Make sure to use this skill whenever the user mentions running tests, executing npm tests, checking lint rules, linting, code formatting, git pushing, pushing to GitHub, or deploying commits to the remote repository. This skill ensures a secure pre-push pipeline by validating tests and linter output prior to any git push.
---

# NPM Test, Lint, and GitHub Deployment Pipeline

Follow this systematic procedure to safely validate code and push verified changes to the remote GitHub repository.

## 1. Environment and Script Verification
Before executing any test or git command, verify the target project environment has the necessary tools:
* Check `package.json` to ensure the `test` and `lint` scripts are defined under `"scripts"`.
* Verify that Git is initialized (`git status`) and a remote origin repository is configured (`git remote -v`).

## 2. Test and Lint Phase
Run tests and linting to ensure zero regressions or formatting errors exist before code leaves the developer environment:
1. **Lint Verification**: Execute `npm run lint`.
   * If there are fixable lint errors, run the auto-fix command: `npm run lint -- --fix` (or the equivalent project command).
   * If any non-fixable lint errors persist, halt the execution, present the logs to the user, and prompt them to resolve the errors.
2. **Unit & Integration Tests**: Execute `npm test` or `npm run test`.
   * Wait for all tests to execute and finish successfully.
   * If any tests fail, do NOT proceed. Halt execution, print the failure details, and prompt for bug remediation.

## 3. Version Increment Phase
Before staging and committing, you MUST check and bump the version in `package.json` following the project's **3-Level Versioning Strategy**:
1. **Read Current Version**: Retrieve the current `"version"` value from `package.json`.
2. **Determine/Select Increment Level**: Clarify with the user which level should be bumped:
   * **Level 1 (Major)**: User-directed primary versions (e.g., `1.02.003` -> `2.00.000`). Resets minor and patch levels to double/triple zero padding.
   * **Level 2 (Minor)**: New feature versions (e.g., `1.02.003` -> `1.03.003`). Increments the minor level by 1, while preserving the patch level as-is.
   * **Level 3 (Patch)**: Routine deployment versions (e.g., `1.02.003` -> `1.02.004`). Increments the patch level by 1, while preserving the minor level as-is. If the user does not request a Major or Minor bump, increment this automatically.
3. **Update Files**: 
   * Write the updated version string back to the `"version"` field in `package.json`.
   * Append a new row to the **Release Log** table in `docs/logs/version-history.md` detailing the new version, current date, increment level, deployer name/model, and primary release highlights.
4. **Trace Version**: Ensure the new version (formatted e.g. `V1.2.3` or `1.2.3`) is prominently displayed in the commit message and noted in the agent changelog.

## 4. Git Staging & Local Commits
Only proceed to Git staging and committing after a 100% clean pass of BOTH linting and tests, and after successfully incrementing the version:
1. Run `git status` to identify modified, deleted, or untracked files.
2. Stage appropriate changes using selective staging (`git add <file>`) or full directory staging (`git add .`) depending on the context of modifications. Ensure the modified `package.json` and `docs/logs/version-history.md` are staged!
3. Formulate a highly informative, structured commit message summarizing the changes (following any workspace-specific logging rules, such as `AGENT.md` guidelines or standard conventional commits) and include the updated version.
4. Run `git commit -m "<message>"`.

## 5. GitHub Push
Push the local verified commits to the active branch on the remote repository:
1. Retrieve the active branch name using `git branch --show-current`.
2. Push changes safely: `git push origin <branch-name>`.
3. Confirm the push command prints success, and report the successful deployment to the user.
