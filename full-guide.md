# Safe to change — the complete learning guide

Build useful checks, a reviewed change and a careful client handoff.

Start with the included sample workspace. Use Python 3.11+, Git and OpenSSL 3. Replace python3 with python on Windows if that is your installed launcher.

## 1. Workspace camp — Start with a working sample

Get a small project you can change without touching client work.

You’ll leave with: A saved sample workspace with passing local checks.

Start here. Keep the terminal in this sample folder throughout the local lessons.

### 1. Get the complete workspace

Where: On this page · Files & full guide

You can learn with the included sample, even if you missed the earlier session.

1. Open Get the files and download the complete starter workspace.
2. Unzip it into a folder named safe-to-change-workspace. Open that folder, not the ZIP preview.
3. Keep this guide open beside it. Use a separate folder, away from real client files.

Check your result: You can see workspace.py, operator_gate.py, draft.json, change-plan.json, delivery-contract.json, VERSION, tests and .github inside the same folder.

If you need a hand: If your file viewer hides .github, turn on hidden files. Do not rename the .github folder.

If you need a hand: If you see an extra outer folder, open the inner safe-to-change-workspace folder containing workspace.py.

More help: Install Python — https://www.python.org/downloads/
More help: Install Git — https://git-scm.com/downloads

### 2. Check your three tools

Where: On your computer · Terminal or PowerShell

A quick version check tells you whether you can follow the local steps.

1. Open Terminal on macOS or Linux, or PowerShell on Windows.
2. Choose your computer above so the Python command matches.
3. Run the three commands below. You need Python 3.11 or newer, Git and OpenSSL 3.

```text
python3 --version
git --version
openssl version
```

Check your result: Each command shows its version. Python begins with 3.11 or newer; OpenSSL begins with 3.

If you need a hand: If Python is missing, install it from python.org and reopen the terminal. On Windows, enable the installer’s PATH option.

If you need a hand: On Windows, OpenSSL may be available from Git Bash after installing Git for Windows. If PowerShell cannot find it, use that shell, or install OpenSSL 3 through your approved tool setup.

If you need a hand: On macOS, the built-in openssl command may be LibreSSL. Use your approved OpenSSL 3 installation and put it on PATH; rerun the version command before continuing.

More help: Install Python — https://www.python.org/downloads/
More help: Install Git — https://git-scm.com/downloads
More help: OpenSSL installation options — https://github.com/openssl/openssl/blob/master/INSTALL.md

### 3. Open the sample folder in your terminal

Where: On your computer · in the unzipped workspace

All local commands in the guide run from the folder containing workspace.py.

1. Use your file viewer’s Open in Terminal option, or change into the unzipped folder.
2. Run the tool check from there.

```text
python3 workspace.py doctor
```

Check your result: The command ends with TOOLS READY. You see the Python, Git and OpenSSL versions.

If you need a hand: If you see “can’t open file workspace.py”, your terminal is in the wrong folder. Move into the folder that contains that file.

If you need a hand: If Windows uses the py launcher instead of python, replace the first word with py -3 for local Python commands.

More help: Install Python — https://www.python.org/downloads/
More help: Install Git — https://git-scm.com/downloads

### 4. Run your first complete check

Where: On your computer · in the workspace

You now have a baseline to come back to. This command reads a real plan, runs real tests and scans the sample source.

1. Run check before changing any files.
2. Keep the final line in view. A failure is a reason to pause and use the help below.

```text
python3 workspace.py check
```

Check your result: The tests end with OK, followed by SECRETS PASS and CHECKS PASS.

If you need a hand: If a test fails on the untouched sample, check Python and OpenSSL versions first.

If you need a hand: If the secret check flags an unexpected file, keep that file out of this sample workspace. Do not paste its contents into chat.

More help: Install Python — https://www.python.org/downloads/
More help: Install Git — https://git-scm.com/downloads

### 5. Save the starting point in Git

Where: On your computer · in the workspace

Git keeps a record of changes. This first saved point makes later experiments easy to review.

1. Run these commands once in the new sample folder.
2. If Git asks for your name and email, set your intended commit identity for this repository, then run the commit again.

```text
git init -b main
git add .
git commit -m "Start with a checked sample workspace"
git status --short
```

Check your result: Git reports a new commit on main. git status --short shows no pending source changes.

If you need a hand: Use repository-local identity settings if needed: git config --local user.name "Your display name" and git config --local user.email "Your chosen commit email". Replace the quoted values with your own intended identity.

If you need a hand: If this is already a Git repository, do not reinitialize an unrelated project. Begin again in the separate downloaded sample folder.

More help: Install Python — https://www.python.org/downloads/
More help: Install Git — https://git-scm.com/downloads

## 2. Plan house — Make the promise clear

Write down what should change and what people should still be able to rely on.

You’ll leave with: A real plan check that accepts a clear plan and stops an incomplete one.

Finish Workspace camp first. Use the included JSON files, not a real client contract.

### 1. Read the short change plan

Where: In your editor · change-plan.json

A useful plan makes the next decision smaller. It says what you are changing, why it helps and what stays out of scope.

1. Open change-plan.json in a plain-text or code editor.
2. Read change, why, acceptance, allowed_paths, out_of_scope and rollback.
3. Keep the sample focused on draft.json. The plan lists intended scope; code review still checks whether the actual change stayed inside it.

Check your result: You can explain the small change, how you will check it and how you would return to a known version.

If you need a hand: JSON uses double quotes and commas between entries. Keep the brackets and quotes when editing.

If you need a hand: The plan validator checks that these fields are present, useful and safely formed. It does not replace a reviewer’s comparison of the actual files.

More help: GitHub Actions: your first workflow — https://docs.github.com/en/actions/tutorials/create-an-example-workflow

### 2. Run the planning check

Where: On your computer · in the workspace

The plan is a file the checks can read, not a note that gets forgotten.

1. Run the plan command.
2. Notice that it reads your file before it gives a result.

```text
python3 workspace.py plan
```

Check your result: You see PLAN PASS.

More help: GitHub Actions: your first workflow — https://docs.github.com/en/actions/tutorials/create-an-example-workflow

### 3. See an incomplete plan stop

Where: In your editor, then your terminal

A check is easier to trust once you have seen it refuse the thing it is meant to catch.

1. In change-plan.json, change the acceptance list to an empty list: []. Save the file.
2. Run the command below.
3. After seeing it stop, restore the plan with git restore change-plan.json. That restores only this file to your saved starting point.

```text
python3 workspace.py plan
```

Keep in mind: Keep any plan wording you want before restoring the file. Do not bypass a failed planning check.

Check your result: The command stops with a message that the plan needs an acceptance item. After restoring the file, the same command passes.

If you need a hand: If the message is about JSON syntax instead, fix the missing quote or comma first. Then try the empty-list example again.

More help: GitHub Actions: your first workflow — https://docs.github.com/en/actions/tutorials/create-an-example-workflow

### 4. Read the delivery promise

Where: In your editor · delivery-contract.json and draft.json

The delivery promise says what a usable update contains. The tests will check that promise.

1. Open delivery-contract.json beside draft.json.
2. Find the required client, date, status, next_step and external_send fields.
3. Keep external_send set to false. A private extra field is not allowed in this output.

Check your result: You can point from each required field in the contract to its value in draft.json.

If you need a hand: This sample only prepares a local JSON update. It has no message-sending step.

If you need a hand: The list of allowed fields is deliberate. Keep team-only notes outside the client update.

More help: GitHub Actions: your first workflow — https://docs.github.com/en/actions/tutorials/create-an-example-workflow

### 5. Try one useful edit

Where: In your editor · draft.json, then the terminal

Make the kind of small change you would want someone else to understand.

1. Change only the status sentence in draft.json. Keep it short and helpful.
2. Leave the other fields in place and keep external_send false.
3. Run the full check.

```text
python3 workspace.py check
```

Check your result: The complete check passes with your clearer sentence.

If you need a hand: If a field is missing, restore it before moving on.

If you need a hand: If you want to keep your wording through the later reset exercise, copy that sentence into your notes first.

More help: GitHub Actions: your first workflow — https://docs.github.com/en/actions/tutorials/create-an-example-workflow

## 3. Test workshop — Let the tests catch a broken change

See what a failed test looks like, then use the result to put the sample right.

You’ll leave with: The same real test failing on a missing detail and passing after the fix.

Keep the plan valid before testing. These commands change only the included sample files.

### 1. Run the tests on a good update

Where: On your computer · in the workspace

A test is a repeatable question about the work. Here it checks the sample update and the handoff tools.

1. Run the test command.
2. Find the test named test_the_current_draft_meets_the_delivery_promise. It reads your actual draft.json.

```text
python3 workspace.py test
```

Check your result: The tests finish with OK.

If you need a hand: The test names explain what is being checked. You do not need to memorize the Python code to use the result.

More help: GitHub Actions: your first workflow — https://docs.github.com/en/actions/tutorials/create-an-example-workflow

### 2. Remove a required next step

Where: On your computer · in the workspace

The next command changes the real sample file. The test then reads that changed file.

1. Run demo-broken to remove next_step from draft.json.
2. Run the tests again.

```text
python3 workspace.py demo-broken
python3 workspace.py test
```

Keep in mind: Use this only in the downloaded sample workspace. It deliberately changes draft.json.

Check your result: The current-draft test fails and reports the missing next_step.

If you need a hand: If everything still passes, check that you ran both commands from the same sample folder.

If you need a hand: A failed command is expected here. Leave the failure visible long enough to read its reason.

More help: GitHub Actions: your first workflow — https://docs.github.com/en/actions/tutorials/create-an-example-workflow

### 3. Follow the failure to the file

Where: In your editor · draft.json and tests/test_delivery.py

The failure should tell you what to look at, rather than leave you guessing.

1. Open draft.json and notice the missing next_step.
2. Open tests/test_delivery.py and find the current-draft test.
3. Notice that the test calls the same update builder used for the release.

Check your result: You can connect the failed test to the missing field, not just to a red status. 

More help: GitHub Actions: your first workflow — https://docs.github.com/en/actions/tutorials/create-an-example-workflow

### 4. Restore the sample and check again

Where: On your computer · in the workspace

A small repair should turn the same test green again.

1. Run the explicit sample reset. It restores the included draft and removes the harmless course marker, if one exists.
2. Run the full check again.
3. Reapply a clearer status sentence later if you want to keep it.

```text
python3 workspace.py reset --yes
python3 workspace.py check
```

Keep in mind: Reset replaces draft.json with the included sample. Keep any sentence you want before running it.

Check your result: The current-draft test passes and the command ends with CHECKS PASS.

More help: GitHub Actions: your first workflow — https://docs.github.com/en/actions/tutorials/create-an-example-workflow

### 5. Keep the test with the work

Where: In your editor · tests/test_delivery.py

The next person should be able to ask the same question after another change.

1. Find the tests that reject a missing field, a private extra field and external sending.
2. When you adapt this pattern later, write tests for the real promise your own work must keep.
3. Do not delete a useful test just to make a change pass.

Check your result: You know which file holds the delivery checks and which behavior each test protects.

More help: GitHub Actions: your first workflow — https://docs.github.com/en/actions/tutorials/create-an-example-workflow

## 4. Secret lookout — Keep access keys out of the project

Use a harmless marker to see the real scan stop a value that should not travel with the source.

You’ll leave with: A passing scan, a genuine rejected marker and a clean sample again.

Use only the course marker. Keep all real credentials outside the sample repository.

### 1. Run the source scan

Where: On your computer · in the workspace

Access keys and private keys do not belong in project files or review messages.

1. Run the scan.
2. It reads source files, including untracked sample files, while leaving Git internals, build output and virtual environments out.

```text
python3 workspace.py scan
```

Keep in mind: This course scanner checks its listed patterns: a harmless course marker, common GitHub token patterns, AWS access-key IDs and private-key headers. It cannot promise to catch every secret or private fact.

Check your result: You see SECRETS PASS.

If you need a hand: A clean scan is one layer. Keep access keys in an approved secret store and review what you are publishing.

More help: GitHub: stop secrets before a push — https://docs.github.com/en/code-security/concepts/secret-security/push-protection
More help: GitHub: remove sensitive data — https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository

### 2. Add a harmless finding

Where: On your computer · in the workspace

You can test the stop without using a real account key.

1. Run demo-secret. It creates a clearly harmless course marker in .demo-secret.txt.
2. Run scan. The scanner reads the file and finds the marker.

```text
python3 workspace.py demo-secret
python3 workspace.py scan
```

Keep in mind: Never paste a real password or access key into this exercise.

Check your result: The scan exits with a failure and names the file and pattern. The marker’s value is hidden in the result.

More help: GitHub: stop secrets before a push — https://docs.github.com/en/code-security/concepts/secret-security/push-protection
More help: GitHub: remove sensitive data — https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository

### 3. Remove the finding and check again

Where: On your computer · in the workspace

The sample should be clean before you connect it to GitHub.

1. Reset the sample, then scan it again.
2. Check that .demo-secret.txt has gone.

```text
python3 workspace.py reset --yes
python3 workspace.py scan
```

Check your result: The same scan passes after the sample marker is removed.

If you need a hand: Reset also restores draft.json. Keep any personal wording in your notes first.

More help: GitHub: stop secrets before a push — https://docs.github.com/en/code-security/concepts/secret-security/push-protection
More help: GitHub: remove sensitive data — https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository

### 4. Understand why history matters

Where: In the included workflow · .github/workflows/ci.yml

Deleting a key from the latest file does not remove the copy in an earlier commit.

1. Find the secrets job in ci.yml. It checks the files and the new Git history against the comparison commit.
2. The GitHub lesson includes an unmerged, harmless secret-marker PR so you can see this job block a merge.
3. If a real key is exposed, revoke or rotate it promptly and follow your team’s incident process. Do not simply delete a line and assume the key is safe.

Check your result: You can explain the difference between removing a visible line and dealing with an exposed credential.

More help: GitHub: stop secrets before a push — https://docs.github.com/en/code-security/concepts/secret-security/push-protection
More help: GitHub: remove sensitive data — https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository

## 5. Review bridge — Make a failed check stop the merge

Put the same checks on GitHub, then make them required before a change can join main.

You’ll leave with: A real pull request blocked by a failing required check.

Use your own authorized sample repository. GitHub account and repository settings are changed by you in these steps.

### 1. Create a separate sample repository

Where: On GitHub · your authorized account

Use a clean public learning repository so GitHub Free can offer the branch protections used here.

1. Create a new repository named safe-to-change-workspace. Choose Public for this sample-only path.
2. Do not add a README, license or .gitignore on GitHub; your local sample already has its starting files.
3. Keep all real client files and credentials out. Review git status --short locally before the first push.

Keep in mind: Publish only the provided sample files. Required protections for private repositories depend on your plan; do not make private client work public to get a feature.

Check your result: The new repository is empty and its page shows the HTTPS address you will use.

More help: GitHub: required checks — https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches

### 2. Connect and run the first workflow

Where: In your sample terminal, then GitHub Actions

GitHub runs the plan, tests and scan whenever a change arrives. That is continuous integration, or CI. The workflow file holds those instructions.

1. Replace YOUR-OWNER in the address below with your actual GitHub username or organization.
2. Add the remote and push main. Complete GitHub’s normal sign-in flow if asked.
3. Open the repository’s Actions tab and wait for the run to finish.

```text
git remote add origin https://github.com/YOUR-OWNER/safe-to-change-workspace.git
git push -u origin main
```

Check your result: The run shows three successful checks named exactly plan, tests and secrets.

If you need a hand: If origin already exists, inspect it with git remote -v. Do not replace an unrelated remote.

If you need a hand: If Actions is disabled by your organization, ask its owner before enabling it. Do not add credentials to the workflow.

More help: GitHub Actions: your first workflow — https://docs.github.com/en/actions/tutorials/create-an-example-workflow

### 3. Make the checks required

Where: On GitHub · Settings → Rules → Rulesets

A red check is only a stop when the repository rules make it one.

1. Create a branch ruleset named Protect main. Set enforcement to Active and target the default branch, main.
2. Leave the bypass list empty. Require a pull request before merging. Require the status checks plan, tests and secrets; choose them from the first run.
3. Require branches to be up to date before merging. Block force pushes and deletion of main.
4. For a solo check exercise, leave required approvals at 0. If an already-authorized teammate can review, require 1 approval and dismiss stale approvals after new commits. Save the ruleset.

Keep in mind: You cannot approve your own pull request. A solo exercise proves the automated stop, not independent human review. Keep the workflow and scanner changes under careful review; people who can edit rules can change the boundary.

Check your result: The ruleset is Active, targets main and lists all three required checks with no bypass entries.

If you need a hand: If a check is not available to select, let the first workflow run finish and refresh.

If you need a hand: An equivalent branch-protection rule can use the same settings. Confirm the rule applies to main and does not exempt administrators.

More help: GitHub: rules for branches — https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/available-rules-for-rulesets
More help: GitHub: required checks — https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches

### 4. Open a change that should fail

Where: In your terminal, then GitHub Pull requests

A branch keeps a proposed change separate. A pull request asks to bring that change into the shared work after its checks and review.

1. Create the branch and remove the required sample next step. Commit only draft.json.
2. Push the branch. On GitHub, open a pull request from try-a-failing-change into main.
3. Explain in the PR that this is a safe missing-field exercise.

```text
git switch -c try-a-failing-change
python3 workspace.py demo-broken
git add draft.json
git commit -m "Try a missing next step"
git push -u origin try-a-failing-change
```

Check your result: The PR’s tests check fails while the change remains separate from main.

More help: GitHub: create a pull request — https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request

### 5. Prove that the merge is stopped

Where: On GitHub · the open pull request

This is the moment that proves the rule is doing work, rather than merely showing a colored icon.

1. Expand the checks and open the tests log. Read the missing next_step failure.
2. Return to the PR. Check that the merge area says the required check has not passed and does not permit the merge.
3. Keep a screenshot or note of the failed check and blocked merge together. Do not use a bypass.

Check your result: The failing tests check is the stated reason the PR cannot merge.

If you need a hand: If GitHub still permits the merge, stop here. Check Active enforcement, branch targeting, the required-check names and the bypass settings.

If you need a hand: A skipped or neutral job can count as acceptable to GitHub. These three jobs have no path filters or success-on-failure settings; keep it that way for the exercise.

More help: GitHub: rules for branches — https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/available-rules-for-rulesets
More help: GitHub: required checks — https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches
More help: GitHub Actions: your first workflow — https://docs.github.com/en/actions/tutorials/create-an-example-workflow

### 6. Fix the same PR and review it

Where: In your terminal, then the same pull request

The repair should pass the same checks that stopped the change.

1. Restore the included sample and push the repair on the same branch.
2. Wait for plan, tests and secrets to finish again. Read the changed files.
3. If you required a teammate’s approval, have that person review the latest version. Do not disable the rule to finish.

```text
python3 workspace.py reset --yes
git add draft.json
git commit -m "Restore the agreed next step"
git push
```

Check your result: The checks pass. The merge stays blocked until every configured review requirement is also met.

If you need a hand: Because this is a deliberate break-and-restore exercise, the final file may match main. You can still inspect the commits and the checks that stopped and then accepted the work.

More help: GitHub: rules for branches — https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/available-rules-for-rulesets
More help: GitHub: required checks — https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches
More help: GitHub Actions: your first workflow — https://docs.github.com/en/actions/tutorials/create-an-example-workflow

### 7. Merge, then return to main

Where: On GitHub, then your terminal

The shared version should now contain only the checked result.

1. Merge the passing PR using GitHub’s normal merge control.
2. Return to your local main branch and pull the reviewed result.
3. Keep main clean before preparing a release.

```text
git switch main
git pull --ff-only
python3 workspace.py check
```

Check your result: git status --short shows no pending source changes, and the full check passes.

More help: GitHub: rules for branches — https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/available-rules-for-rulesets
More help: GitHub: required checks — https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches
More help: GitHub Actions: your first workflow — https://docs.github.com/en/actions/tutorials/create-an-example-workflow

### 8. Prove the secret check stops a PR too

Where: In your sample terminal, then GitHub

A harmless marker lets you test the second merge stop without risking a real key.

1. Create the separate exercise branch below. The marker is normally ignored, so -f is used only for this clearly harmless fixture.
2. Open a PR into main and wait for the secrets check.
3. Do not merge this PR. Confirm that the required secrets check blocks it.

```text
git switch -c try-secret-stop
python3 workspace.py demo-secret
git add -f .demo-secret.txt
git commit -m "Test the harmless course marker"
git push -u origin try-secret-stop
```

Keep in mind: Use only the marker generated by this sample command. Never use -f to publish a real key.

Check your result: The secrets check fails and the PR cannot merge. No real credential was used.

More help: GitHub: rules for branches — https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/available-rules-for-rulesets
More help: GitHub: required checks — https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches
More help: GitHub Actions: your first workflow — https://docs.github.com/en/actions/tutorials/create-an-example-workflow

### 9. Close the marker exercise without merging

Where: On GitHub, then your sample terminal

The marker belongs in an unmerged test branch, not in the shared project’s history.

1. Close the secret-marker PR without merging it.
2. Switch back to main and reset the sample marker. Pull main if needed.
3. If you need a later real change, start a clean branch from main. Removing the marker in a later commit of its old branch does not make that branch’s earlier history clean.

```text
git switch main
python3 workspace.py reset --yes
git pull --ff-only
python3 workspace.py check
```

Check your result: Main is clean, the marker PR is closed and the full local check passes.

More help: GitHub: rules for branches — https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/available-rules-for-rulesets
More help: GitHub: required checks — https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches
More help: GitHub Actions: your first workflow — https://docs.github.com/en/actions/tutorials/create-an-example-workflow

## 6. Release harbor — Give the reviewed copy a clear version

Package the exact checked output and give everyone one version to point to.

You’ll leave with: A versioned ZIP, its fingerprint and a GitHub release tied to a source commit.

Finish the main-branch checks first. Packaging requires a real, clean Git commit.

### 1. Check the source you are releasing

Where: On your computer · main in the sample workspace

Continuous delivery keeps a checked version ready for a careful handoff. It does not mean every change goes live by itself. Begin with saved, reviewed source.

1. Open VERSION. The first version is v0.1.0.
2. Confirm you are on main and have pulled the passing merge.
3. Run the source checks below.

```text
git branch --show-current
git status --short
python3 workspace.py check
```

Check your result: You are on main, status is clean, and the complete check passes.

If you need a hand: If a source file is modified, do not hide it. Review and commit the intended change through your normal PR process first.

If you need a hand: The output folder is ignored by Git; it is not part of your source commit.

More help: GitHub: manage a release — https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository

### 2. Make the release package

Where: On your computer · in the workspace

The package command checks the source again before creating the client output. It does not include executable code or approval keys.

1. Run package once for this version.
2. Open the out folder and find v0.1.0.zip and v0.1.0.sha256.
3. Keep the printed source commit and package SHA256 with your release notes. SHA256 is a fingerprint of the exact file.

```text
python3 workspace.py package
```

Check your result: You see RELEASE READY, a source commit and a SHA256 fingerprint. The ZIP contains only client_update.json and manifest.json.

If you need a hand: If Git is not initialized or the source is dirty, return to the earlier steps. The release refuses to invent a source commit.

If you need a hand: If that version is already packaged, keep it. Use a new version name for new work instead of replacing an earlier release.

More help: GitHub: manage a release — https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository

### 3. Tag this exact saved version

Where: On your computer · in the workspace

A Git tag names a saved point in the project’s history. The release will use the same point.

1. Create and push the v0.1.0 tag after packaging the clean main commit.
2. Copy the full commit ID for the release notes.

```text
git tag v0.1.0
git push origin v0.1.0
git rev-parse HEAD
```

Keep in mind: If that tag already exists, do not move or force it. Use a new version for a new release.

Check your result: The tag appears on GitHub and points to the same commit recorded by the package.

More help: GitHub: manage a release — https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository

### 4. Publish the downloadable release

Where: On GitHub · Releases → Draft a new release

The release page keeps the version, files and change notes in one place.

1. Choose the existing v0.1.0 tag. Name the release v0.1.0.
2. Write what changed, the full source commit, the passing checks link and the package SHA256. For this first release, say there is no earlier approved return point yet.
3. Attach out/v0.1.0.zip and out/v0.1.0.sha256. Publish only when those details match.

Check your result: The published release shows both attached files and the correct source tag.

If you need a hand: GitHub also offers automatic source-code archives. The handoff lesson uses your attached v0.1.0.zip, not the automatic source archive.

More help: GitHub: manage a release — https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository

### 5. Check the downloaded file

Where: On GitHub, then your computer

The file someone receives should be the same file you reviewed.

1. Download your attached release ZIP and save the copy as out/downloaded-v0.1.0.zip.
2. Run the fingerprint command below and compare the full result with out/v0.1.0.sha256.
3. Keep the release URL for the approval request.

```text
python3 -c "from pathlib import Path; import hashlib; print(hashlib.sha256(Path('out/downloaded-v0.1.0.zip').read_bytes()).hexdigest())"
```

Check your result: The complete 64-character fingerprint matches. If it differs, stop and find out why.

If you need a hand: Keep the downloaded check copy under out, not in the source root.

If you need a hand: A matching fingerprint identifies the bytes. It does not replace checking who approved the file or what it is allowed to do.

More help: GitHub: manage a release — https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository

## 7. Approval lodge — Put a clear decision beside the release

Use Mattermost for the review conversation, then sign the exact decision the delivery tool will check.

You’ll leave with: A refused unsigned attempt and a signed decision for one release and one sample destination.

Use the same release from Release harbor. Have access to an existing authorized Mattermost workspace.

### 1. Choose the right place to review

Where: In your existing authorized Mattermost workspace

The decision should be easy to find and belong to the right people.

1. Use an approved learning channel, or create a private release-review channel if you have permission. If not, ask the workspace owner.
2. Set a short purpose: Review sample releases before client-folder handoff.
3. Agree who may approve and who performs the handoff. You can play both roles while learning with sample files.

Keep in mind: Do not create a new server or invite people just to follow the lesson. Real client discussions need the right private membership.

Check your result: The intended people can open the channel and know who makes the final decision.

More help: Mattermost: create a channel — https://docs.mattermost.com/end-user-guide/collaborate/create-channels

### 2. Set up the separate operator home

Where: On your computer · from the sample workspace

Keep the permission-checking tool and its trust settings outside the source repository.

1. Run setup with a new operator-home folder and a new sample-client-folder destination beside the source workspace.
2. Setup makes an approval key and a public checking key. It copies the trusted operator tool into operator-home.
3. Keep the operator home out of GitHub, chat and downloads.

```text
python3 operator_gate.py setup --home ../operator-home --destination ../sample-client-folder
```

Keep in mind: For real work, use separate protected accounts for the approver and operator. Protect the key, policy and installed tool. This one-person exercise is for learning the handoff, not for separating people who share full file access.

Check your result: You see OPERATOR HOME READY. The sample client folder has not been created.

If you need a hand: If operator-home already exists, do not overwrite its trust settings. Use the existing learning setup you created, or intentionally choose a separate new pair of sample folders.

If you need a hand: Use a local parent folder that only the operator can change. The client destination must stay separate from the source and operator home.

More help: Mattermost: create a channel — https://docs.mattermost.com/end-user-guide/collaborate/create-channels
More help: OpenSSL: sign and verify a file — https://docs.openssl.org/3.0/man1/openssl-pkeyutl/

### 3. Try the handoff before anyone says yes

Where: On your computer · from the sample workspace

Code can be saved and released while its use is still on hold. This command should prove that difference.

1. Run the installed operator tool against the release.
2. Read the refusal. Do not add a manual client-folder copy as a workaround.

```text
python3 ../operator-home/operator_gate.py deliver --home ../operator-home --package out/v0.1.0.zip
```

Check your result: It stops with “No signed approval exists for this exact release.” The sample client folder is still absent.

If you need a hand: If the handoff succeeds, that operator home already has a decision for these exact bytes. Use a fresh learning setup before testing the unsigned stop.

More help: Mattermost: create a channel — https://docs.mattermost.com/end-user-guide/collaborate/create-channels
More help: OpenSSL: sign and verify a file — https://docs.openssl.org/3.0/man1/openssl-pkeyutl/

### 4. Prepare the review request

Where: On your computer, then your Mattermost channel

The reviewer needs the exact version, file fingerprint, source, action and destination together.

1. Replace YOUR-OWNER in the release link below with your actual repository owner. Generate the request.
2. Open out/release-request.md. Add the real passing GitHub checks link and the named approver. Confirm its exact destination and fingerprint.
3. Review the text, then paste it into your authorized channel. Do not attach any private key.

```text
python3 workspace.py request --destination ../sample-client-folder --release-url https://github.com/YOUR-OWNER/safe-to-change-workspace/releases/tag/v0.1.0
```

Check your result: The post links to the release and passing checks, states the exact SHA256 and requests only copy-client-update to the named sample folder.

If you need a hand: If you used a different repository name, change that part of the URL too.

If you need a hand: The requested action is a controlled copy of the sample JSON output. It is not permission to run arbitrary code.

More help: Mattermost: create a channel — https://docs.mattermost.com/end-user-guide/collaborate/create-channels
More help: OpenSSL: sign and verify a file — https://docs.openssl.org/3.0/man1/openssl-pkeyutl/

### 5. Record the person’s decision

Where: In Mattermost · on the release request

A useful yes says which version, action and destination it covers.

1. Have the named approver inspect the release, checks, SHA256 and destination.
2. The approver replies with an explicit approve or hold decision for that exact version and job. Include an expiry, such as one hour.
3. Use Mattermost’s Copy Link action on the actual decision post. Keep that HTTPS permalink for the next command.

Keep in mind: A reaction or a passing check alone does not grant the handoff. If the decision is hold, stop here.

Check your result: The thread contains a clear human decision, and you can open its exact permalink.

More help: Mattermost: share a message link — https://docs.mattermost.com/end-user-guide/collaborate/share-links
More help: Mattermost: create a channel — https://docs.mattermost.com/end-user-guide/collaborate/create-channels

### 6. Sign that exact decision

Where: Approver’s computer · from the sample workspace

The separate gate checks a signed record. A chat message by itself cannot unlock the client folder.

1. Only the person authorized to use the approval key runs this step. Replace the post URL and approver name below with the actual decision.
2. Confirm the request’s digest and destination match the local release and trusted policy. Run the command.
3. The signed decision expires in one hour and applies only to these release bytes, this destination and this action.

```text
python3 ../operator-home/operator_gate.py approve --home ../operator-home --package out/v0.1.0.zip --post-url https://YOUR-MATTERMOST-SITE/YOUR-TEAM/pl/YOUR-DECISION-POST --approver "YOUR NAME" --expires-in 3600
```

Keep in mind: The post link is a reference, not an automatic identity check. The key holder must confirm who wrote the actual decision and what they approved before signing.

Check your result: You see APPROVAL SIGNED for v0.1.0 and the same package fingerprint.

If you need a hand: If the approval has expired or been put on hold, do not edit the saved decision or signature. Make a fresh release decision through the team’s process.

If you need a hand: A changed release needs a new review. Do not reuse a yes from different bytes.

More help: OpenSSL: sign and verify a file — https://docs.openssl.org/3.0/man1/openssl-pkeyutl/

## 8. Client garden — Let permission control the handoff

Use the separate gate to make the approved sample copy, then see how a changed file or a hold stops it.

You’ll leave with: A sample client update with a receipt, plus genuine refused handoff tests.

Use the approved sample release. Only new, empty, explicitly chosen sample destinations are used in this exercise.

### 1. Check the exact copy before use

Where: On your computer · release and operator-home folders

The right version and the right permission need to meet at the same handoff.

1. Keep out/v0.1.0.zip unchanged.
2. In operator-home/approvals, open the decision’s approval.json and compare its version, source commit, fingerprint, destination, action and expiry with the request.
3. Do not edit the record. The signature is checked by the installed operator tool.

Check your result: The details match the reviewed release and the destination is the separate sample client folder.

If you need a hand: If the approval is missing, return to Approval lodge.

If you need a hand: Never put approver/private.pem in a client folder or a review message.

More help: GitHub: manage a release — https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository
More help: OpenSSL: sign and verify a file — https://docs.openssl.org/3.0/man1/openssl-pkeyutl/

### 2. Run the approved handoff

Where: On your computer · from the sample workspace

The tool verifies the package, signature, current permission, expiry and destination before it writes the sample output.

1. Run the same handoff command that was refused before approval.
2. Open the new sample client folder after it succeeds.

```text
python3 ../operator-home/operator_gate.py deliver --home ../operator-home --package out/v0.1.0.zip
```

Check your result: You see HANDOFF ALLOWED. The folder contains only client_update.json and receipt.json.

If you need a hand: If it says expired, ask for a fresh decision through the approved process. Do not change the timestamp in the file.

If you need a hand: If the destination already exists, the gate refuses to overwrite it. Do not delete working client files to make the command pass.

If you need a hand: A stopped copy can leave an incomplete sample folder. The operator must inspect it before deciding how to recover; a refusal is not permission to erase it.

If you need a hand: The gate copies the sample output only. It does not run source code, send messages or activate a client system.

More help: GitHub: manage a release — https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository
More help: OpenSSL: sign and verify a file — https://docs.openssl.org/3.0/man1/openssl-pkeyutl/

### 3. Match the receipt to the conversation

Where: In the sample client folder, then Mattermost

A receipt makes it easier to see which decision led to which handoff.

1. Open receipt.json and compare its source commit, version, package fingerprint and decision-post link with the release request.
2. Open client_update.json and check the client, date, status and next step.
3. If your channel’s agreed process allows it, post a short completion reply with the receipt reference. Keep private local paths or client details out of broader rooms.

Check your result: The release, human decision and delivered receipt refer to the same version and job.

More help: GitHub: manage a release — https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository
More help: OpenSSL: sign and verify a file — https://docs.openssl.org/3.0/man1/openssl-pkeyutl/

### 4. See a changed package stop

Where: On your computer · from the sample workspace

Approval should not silently follow a file that changed after review.

1. Make a harmless changed copy under out. The original release stays untouched.
2. Try handing off that changed copy.

```text
python3 -c "from pathlib import Path; p=Path('out/v0.1.0.zip'); Path('out/changed.zip').write_bytes(p.read_bytes()+b'changed')"
python3 ../operator-home/operator_gate.py deliver --home ../operator-home --package out/changed.zip
```

Check your result: The command stops because the exact changed bytes have no signed approval. The existing sample output is untouched.

If you need a hand: The altered file is only a local test. Do not upload it as the approved release.

More help: GitHub: manage a release — https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository
More help: OpenSSL: sign and verify a file — https://docs.openssl.org/3.0/man1/openssl-pkeyutl/

### 5. Put a decision on hold

Where: On your computer · after completing the sample handoff

A hold should stop future attempts. It should not silently delete work that was already delivered.

1. Use revoke to put this sample approval on hold.
2. Try the normal handoff command once more.
3. Keep the delivered folder and its receipt as the record of what already happened.

```text
python3 ../operator-home/operator_gate.py revoke --home ../operator-home --package out/v0.1.0.zip
python3 ../operator-home/operator_gate.py deliver --home ../operator-home --package out/v0.1.0.zip
```

Keep in mind: Revocation stops future use through the gate. It does not recall an earlier copy or undo a client-side action.

Check your result: The retry stops with “This approval is on hold.” The earlier sample copy and receipt remain unchanged.

More help: GitHub: manage a release — https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository
More help: OpenSSL: sign and verify a file — https://docs.openssl.org/3.0/man1/openssl-pkeyutl/

### 6. Keep the path useful for the next change

Where: In your own working notes

The same pattern can carry to another project once its checks and permissions match the real job.

1. Keep the source commit, tag, release files, checks link, decision and receipt together.
2. For a later change, use a new branch, reviewed source, version and exact decision. Keep the last usable version as a named return point.
3. Agree the real destination and rollback method before using this pattern for client work. Never bypass the gate with a manual copy when it refuses.

Check your result: You can explain and repeat the whole path: plan → tests → secret scan → review → release → permission → controlled handoff.

If you need a hand: The first release has no earlier approved return point. On later work, make a deliberate, approved choice before returning to an older version.

If you need a hand: Real teams must protect the installed gate, trusted policy and public key from source contributors, and keep approval-key access separate. These controls are not created merely by publishing a repository.

More help: GitHub: manage a release — https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository
More help: OpenSSL: sign and verify a file — https://docs.openssl.org/3.0/man1/openssl-pkeyutl/

