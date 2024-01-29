# Checkpoint2 Submission

- **COURSE INFORMATION: CAA900ZAA.08425.2241-Capstone Project**
- **STUDENT’S NAME: Komal Sharma**
- **STUDENT'S NUMBER: 129875217**
- **GITHUB USER_ID: 129875217-myseneca**
- **TEACHER’S NAME: Atoosa Nasiri**

---

## Table of Contents
1. [Part A - Adding Files - Local Repo Workflow](#adding-files-local-repo-workflow)
2. [Part B - Inspecting Local Repo with `git status` and `git log`](#inspecting-local-repo-with-git-status-and-git-log)
3. [Part C - Creating & Merging Branches](#creating-and-merging-branches)
4. [Part D - Git Branching Strategy Review Question](#git-branching-strategy-review-question)

### Adding Files Local Repo Workflow

Here are the link for the files added for each status change. You can also find these files in the checkpoint2 repository.

[Untracked Changes](git_status_untracked.txt)

[Uncommitted Changes](git_status_uncommitted.txt)

[Commited Changes](git_status_committed.txt)

### Inspecting Local Repo with git status and git log

Here is the screenshot for the git status and git log command:

<img src="statusvslog.png"
     alt="Status VS Log"
     style="float: left; margin-right: 10px;" />

How do these two commands differ?
When we do git status we get the brief information about the current status. What is added, what is commited. Further step that needs to be taken. It is like the present in our git time machine. It will only talk about the current status whereas in log we can the history from our time machine, whereall we travelled and what all we did. It give a detailed information about the changes that we have done.

Here in the example we can see that got status only give the information about the current status that everything is upto date but if we check the logs command we only ran for the last 5 commit and we can get the information about when that happened and who was the author. It also gives the information about the commit id and the commit message that we added during the time of commit.

### Creating and Merging Branches

## Git Log - Last 5 Commits

```bash
commit 1674fc59b2963a2a8fe113c6773bf0b554263625 (HEAD -> main, origin/main, origin/feat-emojis, origin/HEAD, feat-emojis)
Author: 129875217-myseneca <ksharma145@myseneca.ca>
Date:   Sun Jan 28 20:45:24 2024 -0500

    Adds emojis to feat-emojis branch

commit 898434ebe0e766e86a739582b2afe7de63ea562d
Author: 129875217-myseneca <ksharma145@myseneca.ca>
Date:   Sun Jan 28 20:27:47 2024 -0500

    adds footnotes folder

commit b647bd32ca8609066627959fd674b4cc53503fd4
Author: 129875217-myseneca <ksharma145@myseneca.ca>
Date:   Sun Jan 28 20:22:22 2024 -0500

    Updated part B of readme.

commit 3e469d280bae59aa1fb1b0b5d534c2b698b26a37
Author: 129875217-myseneca <ksharma145@myseneca.ca>
Date:   Sun Jan 28 20:18:49 2024 -0500

    Updated the readme with part b.

commit 81d90ae6c59d3ad8c8c1f3fdec04457106473918
Author: 129875217-myseneca <ksharma145@myseneca.ca>
Date:   Sun Jan 28 06:57:18 2024 -0500

    Added more information in README.md
```

### Git Branching Strategy Review Question

What are the differences between develop branch and main branch?

Differences between develop branch and main branch:
The primary distinction between the develop and main branches lies in their roles within the Git branching strategy. The develop branch serves as the active development area, housing ongoing work, feature development, and bug fixes. Developers create feature and bugfix branches from develop and merge them back upon completion. In contrast, the main branch represents production-ready code, with its HEAD reflecting the latest deployed version. Hotfix branches are created from main to address urgent issues, ensuring a stable production environment.

What are the three supporting branches? Briefly describe the function of each of these supporting branches.

Three Supporting Branches and Their Functions:
The three supporting branches in this Git branching model serve specific purposes in facilitating parallel development, bug tracking, and production issue resolution. 

Feature/Bugfix branches, branching from and merging into develop, are employed for developing new features or addressing bugs. 

Hotfix branches, originating from a tagged main, provide an avenue for immediate fixes to live production versions and merge back into both main and develop. 

Release branches, created from tagged develop, prepare for a release by bumping version numbers and conducting final housekeeping before merging into both main and develop.

What are the best practices in working with release branches?
Best Practices for Working with Release Branches:
Effective handling of release branches involves several best practices. Developers should create the release branch from a tagged develop, ensuring that all planned features and bugfixes for the release are merged into develop. Bumping version numbers and performing any last-minute housekeeping should occur within the release branch. After readiness, the release branch is merged into main and tagged for production deployment. Subsequently, merging the release branch back into develop keeps the development branch up to date with the latest release. Utilizing semantic versioning for version numbers helps convey the nature of changes (major, minor, patch) in the release, fostering clarity and consistency in versioning practices.
