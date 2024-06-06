Git References

1. **Branches**:
   - Branches are simple pointers or references to the head of a line of work.
   - Stored in the `.git/refs/heads` directory.
   - Create a branch: `git branch <branch>`
   - Update a branch: `git update-ref refs/heads/<branch> <commit_SHA>`

2. **HEAD**:
   - The file `.git/HEAD` points to the current branch or commit.
   - Usually a symbolic reference to the current branch.
   - Manually set the value of HEAD: `git symbolic-ref HEAD refs/heads/<branch>`

3. **Tags**:
   - Lightweight tags: a reference that never moves.
     - Create: `git update-ref refs/tags/<tag_name> <commit_SHA>`
   - Annotated tags: points to a tag object, which then points to a commit.
     - Create: `git tag -a <tag_name> <commit_SHA> -m 'tag message'`

4. **Remote References**:
   - Stored in the `.git/refs/remotes` directory.
   - Holds the value of the last commit pushed to the remote.
   - Typically read-only.
   - Example: `git push origin master` updates `.git/refs/remotes/origin/master`