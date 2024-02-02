# Checkpoint3 Submission

- **COURSE INFORMATION: CAA900ZAA.08425.2241-Capstone Project**
- **STUDENT’S NAME: Komal Sharma**
- **STUDENT'S NUMBER: 129875217**
- **GITHUB USER_ID: 129875217-myseneca**
- **TEACHER’S NAME: Atoosa Nasiri**

---

## Table of Contents
1. [Part A - Manage Conflicts - Overwrite Remote Changes](#overwrite-remote-changes)
2. [Part B - Manage Conflicts - Reset Local Commit Head](#reset-local-commit-head)
3. [Part C - Manage Conflicts - Merge Editor](#merge-editor)
4. [Part D - Collaboration - Creating Pull Request](#creating-pull-request)

### Overwrite Remote Changes
Conflict Error Log
```plaintext

Pushing to https://github.com/129875217-myseneca/CAA900-Azure-Project.git
To https://github.com/129875217-myseneca/CAA900-Azure-Project.git
 ! [rejected]        main -> main (fetch first)
error: failed to push some refs to 'https://github.com/129875217-myseneca/CAA900-Azure-Project.git'
hint: Updates were rejected because the remote contains work that you do not
hint: have locally. This is usually caused by another repository pushing to
hint: the same ref. If you want to integrate the remote changes, use
hint: 'git pull' before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

Conflict Overwrite Log
```plaintext

POST git-receive-pack (6501 bytes)
Pushing to https://github.com/129875217-myseneca/CAA900-Azure-Project.git
To https://github.com/129875217-myseneca/CAA900-Azure-Project.git
 + b50aba7...f161d9e main -> main (forced update)
updating local tracking ref 'refs/remotes/origin/main'

```

Once the changes are overwritten in the remote repo with local repo changes the final colour is set to green. This is happening because the change in local repo was set to green and it was forced on the remote repo.

### Reset Local Commit Head
Pull Error Log
```plaintext
POST git-upload-pack (196 bytes)
POST git-upload-pack (533 bytes)
From https://github.com/129875217-myseneca/CAA900-Azure-Project
   c13341c..88f5ca9  main        -> origin/main
 = [up to date]      dummy       -> origin/dummy
 = [up to date]      feat-emojis -> origin/feat-emojis
Auto-merging Checkpoint3/conflict-resolution/index.html
CONFLICT (content): Merge conflict in Checkpoint3/conflict-resolution/index.html
Automatic merge failed; fix conflicts and then commit the result.
```

Reset Head Log
```plaintext
HEAD is now at c13341c Updated Readme.md with part 1
commit c13341c713ab80eb2c8d596f680bebca7165aaec
Author: 129875217-seneca <ksharma145@myseneca.ca>
Date:   Thu Feb 1 20:55:03 2024 -0500

    Updated Readme.md with part 1

```

Pull Success Log
```plaintext
POST git-upload-pack (196 bytes)
From https://github.com/129875217-myseneca/CAA900-Azure-Project
 = [up to date]      main        -> origin/main
 = [up to date]      dummy       -> origin/dummy
 = [up to date]      feat-emojis -> origin/feat-emojis
Updating c13341c..88f5ca9
Fast-forward
 Checkpoint3/conflict-resolution/index.html | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```

Once we have a sucessful pull request the color is changed to maroon in both the local and remote repo as we have pulled the changes from the remote repo which had the color maroon.

### Merge Editor

Here is the screenshot of index.html in VSCode:
<img src="index in vs.png"
     alt="Status VS Log"
     style="float: left; margin-right: 10px;" />


Here is the screenshot of Resolve in Merge Editor:
<img src="resolve in merge editor.png"
     alt="Status VS Log"
     style="float: left; margin-right: 10px;" />



### Creating Pull Request