## Rewriting History in Git

### Introduction

When working with Git, you may need to revise your local commit history. Git allows you to make decisions at the last moment, including which files go into commits, stashing changes, and rewriting commits to appear differently. This includes changing commit order, messages, files, squashing, splitting, or removing commits—all before sharing your work with others.

### Key Points

- **Don't push your work until you're happy with it:** Once you push, treat it as final unless there's a good reason to change it. Rewrite history locally until you're ready to share.

### Changing the Last Commit

#### Modify Last Commit Message

To change the last commit message:

```bash
$ git commit --amend
```

This command opens the previous commit message in an editor for modification. Save and exit to update the commit message.

#### Modify Last Commit Content

To change the content of the last commit:

1. Make the necessary changes and stage them.
2. Amend the commit:

```bash
$ git commit --amend
```

#### Tip: Skipping the Editor Session

If the commit message doesn’t need updating:

```bash
$ git commit --amend --no-edit
```

### Changing Multiple Commit Messages

For modifying commit messages farther back in history, use interactive rebase. Specify how far back you want to rewrite commits:

```bash
$ git rebase -i HEAD~3
```

This opens an interactive rebase editor showing the last three commits. Change `pick` to `edit` or `reword` for the commits you want to modify.

Example interactive rebase list:

```
pick f7f3f6d Change my name a bit
reword 310154e Update README formatting and add blame
pick a5f4a0d Add cat-file
```

To change a commit message:

1. Mark the commit with `reword` or `edit`.
2. Save and exit the editor.
3. Modify the commit message.
4. Continue the rebase process:

```bash
$ git commit --amend
$ git rebase --continue
```

### Reordering Commits

To reorder commits, rearrange them in the interactive rebase editor.

Original order:

```
pick f7f3f6d Change my name a bit
pick 310154e Update README formatting and add blame
pick a5f4a0d Add cat-file
```

New order:

```
pick 310154e Update README formatting and add blame
pick f7f3f6d Change my name a bit
```

### Squashing Commits

To squash commits into a single commit:

```
pick f7f3f6d Change my name a bit
squash 310154e Update README formatting and add blame
squash a5f4a0d Add cat-file
```

Git will prompt you to combine commit messages.

### Splitting a Commit

To split a commit, change `pick` to `edit` for the commit to split:

```
pick f7f3f6d Change my name a bit
edit 310154e Update README formatting and add blame
pick a5f4a0d Add cat-file
```

Then:

1. Reset the commit.
2. Create multiple commits from the changes:

```bash
$ git reset HEAD^
$ git add README
$ git commit -m 'Update README formatting'
$ git add lib/simplegit.rb
$ git commit -m 'Add blame'
$ git rebase --continue
```

### Deleting a Commit

To delete a commit, change `pick` to `drop`:

```
pick 461cb2a This commit is OK
drop 5aecc10 This commit is broken
```

### The Nuclear Option: `filter-branch`

For extensive history rewriting, use `filter-branch`. This command is powerful but should be used cautiously, especially if the project is public. `git-filter-repo` is a better alternative.

#### Example Uses

- **Removing a file from every commit:**

```bash
$ git filter-branch --tree-filter 'rm -f passwords.txt' HEAD
```

- **Making a subdirectory the new root:**

```bash
$ git filter-branch --subdirectory-filter trunk HEAD
```

- **Changing email addresses globally:**

```bash
$ git filter-branch --commit-filter '
if [ "$GIT_AUTHOR_EMAIL" = "old@example.com" ];
then
    GIT_AUTHOR_NAME="New Name";
    GIT_AUTHOR_EMAIL="new@example.com";
    git commit-tree "$@";
else
    git commit-tree "$@";
fi' HEAD
```

### Conclusion

By leveraging Git’s powerful features for rewriting history, you can refine your commit history to accurately represent your work before sharing it with others.