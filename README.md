# Safe to change — GitHub 101 learning atlas

[Open the free learning book](https://github-101-project-book.vercel.app/).

A self-paced guide to planning a small change, testing it, checking for supported secret patterns, reviewing a pull request, creating a named release and giving separate permission for a sample client-folder handoff.

## Follow the world map

Eight connected places guide you through one working sample:

1. Workspace camp — start with a working sample.
2. Plan house — agree what the change must keep.
3. Test workshop — make a broken change fail a real test.
4. Secret lookout — try a harmless marker and learn the scanner’s limits.
5. Review bridge — make the named GitHub checks required before a merge.
6. Release harbor — package and name an exact saved version.
7. Approval lodge — record a human decision and sign its exact release and action.
8. Client garden — make the permitted sample copy and check its receipt.

Each step tells you where to work, what to do and how to check your result. Commands, troubleshooting and official tool guides are included. The book has a real cover, page turns, desktop landscape, phone-friendly place selection, progress, personal notes and a full print view. Page turns respect reduced-motion preferences.

## Get the working files

Use **Get the files** inside the book, or download `starter-workspace.zip` and `full-guide.md` from this repository.

The starter uses Python 3.11+, Git and OpenSSL 3. It includes actual sample files, plan validation, tests, supported-pattern scanning, a read-only GitHub Actions workflow, versioned packaging and a separate signed sample-handoff tool. The complete course is also included as `START-HERE.md` inside the ZIP.

The book itself needs only a modern browser. You can open `index.html` directly; the starter download is embedded for offline use too. No build step or account connection is needed to read it. Completing the GitHub and Mattermost lessons requires your own authorized accounts. The book does not create repositories, change rules, post messages, send client data or grant access for you.

## Keep the checks and permission separate

The GitHub workflow has jobs named `plan`, `tests` and `secrets`. Configure an active rule on your own learning repository to make those checks required; a workflow file by itself does not block merging. The scanner has a declared pattern scope, not a guarantee to find every secret.

The local handoff tool checks a signed decision for the exact package, source commit, action, destination and expiry. A Mattermost permalink is a review reference, not automatic verification of the post author. One learner can practise both roles; real use needs separate protected accounts, key ownership and trusted operator settings. Use sample files only.

## Personal notes

Notes and progress stay in your browser when storage is available. Earlier notes are preserved on the same website and browser. You can export them; the book does not send them to anyone. Do not enter credentials or private client data. Hosting providers may keep their normal website access logs.

## Hosting and scope

The public book uses an isolated project on the existing Vercel Hobby plan and its free `vercel.app` address. No paid feature, custom-domain change or client integration is required.

This guide was prepared around **Github 101: Continuous Dev and Continuous Integration**, November 16, 2026. The event repository and implementation were not supplied. The sample is its own learning workspace, with official tool guides linked at the relevant steps; it is not the organizer’s source code.

Only the public book, guide, starter ZIP, this README and `.nojekyll` belong in this repository. Private preparation records, test receipts, approval keys and real client files stay outside it.
