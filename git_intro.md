# Git Intro Reading

### Version Control

A system that records changes to a file, allowing you to revisit or revert to a previous version, as well as track modificaitons.

### Git

Git is a DVCS (Distributed Version Control) that stores data in snapshots. It tracks any changes applied to any file. It has three main states: commited, modified, and staged.
Commited: Data is securely stored
Modified: File has been changed, but not yet committed.
Staged: Flagged a file's changed version to be committed in the next snapshot.

Useful commands:
'git clone "given url"'
'git commit -m "commit message here"' can use -a for all files.
'git push origin master' used mainly as this. Blank template is 'git push remote-name branch-name'

You can also stash changes using 'git stash' to remove and hide them, and then reapply them later using 'git stash apply'.

'git fetch [remote-name]' will pull data you don't have.
'git fetch origin' will pull any changes that were pushed since you last cloned or fetched.
These only pull data. They do not merge changes or modify local work.


[Back](README.md)
