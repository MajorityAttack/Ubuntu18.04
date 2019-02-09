Accidentally committed the wrong files to Git, but I haven't pushed the commit to the server yet.

How can I undo those commits from the local repository?

```sh
$ git commit -m "Something terribly misguided"             # (1)
$ git reset HEAD~                                          # (2)
<< edit files as necessary >>                              # (3)
$ git add ...                                              # (4)
$ git commit -c ORIG_HEAD  
```

1. This is what you want to undo.
2. This leaves your working tree (the state of your files on disk) unchanged but undoes the commit and leaves the changes you committed unstaged (so they'll appear as "Changes not staged for commit" in git status, so you'll need to add them again before committing). If you only want to add more changes to the previous commit, or change the commit message1, you could use git reset --soft HEAD~ instead, which is like git reset HEAD~ (where HEAD~ is the same as HEAD~1) but leaves your existing changes staged.
3. Make corrections to working tree files.
4. git add anything that you want to include in your new commit.
5. Commit the changes, reusing the old commit message. reset copied the old head to .git/ORIG_HEAD; commit with -c ORIG_HEAD will open an editor, which initially contains the log message from the old commit and allows you to edit it. If you do not need to edit the message, you could use the -C option.
Beware however that if you have added any new changes to the index, using commit --amend will add them to your previous commit.

If the code is already pushed to your server and you have permissions to overwrite history (rebase) then:

git push origin master --force
You can also look at this answer:

How to move HEAD back to a previous location? (Detached head)

The above answer will show you git reflog which is used to find out what is the SHA-1 which you wish to revert to. Once you found the point to which you wish to undo to use the sequence of commands as explained above.

1 Note, however, that you don't need to reset to an earlier commit if you just made a mistake in your commit message. The easier option is to git reset (to upstage any changes you've made since) and then git commit --amend, which will open your default commit message editor pre-populated with the last commit message.

Reference Link:
https://stackoverflow.com/questions/927358/how-do-i-undo-the-most-recent-commits-in-git
