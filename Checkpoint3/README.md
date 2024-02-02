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

### Merge Editor

### Creating Pull Request