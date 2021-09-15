# Git Branches Cheatsheet

{% raw %}

## Terms

- Head Branch - The currently **active** or **checked out** branch is head branch
- Local Branch - Branches only used locally in system
- Remote Branch - Branches on web like github or gitlab

## Commands

| Command                                                      | Action                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------------- |
| git status                                                   | Check current branch name                                           |
|                                                              |                                                                     |
| git branch                                                   | Get all local branch                                                |
| git branch -r                                                | Get all remote branch                                               |
| git branch -a                                                | Get all local and remote branch                                     |
| git branch -v                                                | Get all branches with hash and commit names                         |
|                                                              |                                                                     |
| git branch <new-branch-name>                                 | Create New Branch                                                   |
| git branch <other-new-branch> <commit-hash>                  | Create branch till perticular commit                                |
|                                                              |                                                                     |
| git checkout <branch-name>                                   | Change Branch                                                       |
| git switch                                                   | Only Switch/Change branch                                           |
|                                                              |                                                                     |
| git branch -m <new-name>                                     | Change current branch name                                          |
| git branch -m <branch-name> <new-name>                       | Change perticuar branch name                                        |
|                                                              |                                                                     |
| git push origin --delete <old-name>                          | delete current / old branch                                         |
| git push -u origin <new-name>                                | push new local branch with corrent name                             |
|                                                              |                                                                     |
| git push -u origin <local-branch>                            | Upload local branch                                                 |
|                                                              |                                                                     |
| git checkout --track origin/<remote-branch-name>             | track remote branch and local branch will be created with same name |
| git branch --track <branch-name> origin/<remote-branch-name> | track remote branch with local branch                               |
|                                                              |                                                                     |
| git pull                                                     | pull new changes                                                    |
| git push                                                     | push changes to remote                                              |
| git branch -v                                                | git branches details                                                |
|                                                              |                                                                     |
| git branch -d <branch-name>                                  | delete local branch                                                 |
| git push origin --delete <branch-name>                       | delete remote branch                                                |
|                                                              |                                                                     |
| git switch main                                              | switch branch to main                                               |
| git merge <other-branch-name>                                | merge current branch with other-branch                              |
|                                                              |                                                                     |
| git switch main                                              | switch branch to main                                               |
| git rebase <other-branch-name>                               | merge current branch with other without showing merge commit in log |
|                                                              |                                                                     |
| git log <one-branch>..<another-branch>                       | compare branch change                                               |
|                                                              |                                                                     |

{% endraw %}
