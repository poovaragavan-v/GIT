Git commands cheatsheet

**1. First-Time Git Setup**
   - Configure user name: `git config --global user.name "Your Name"`
   - Configure user email: `git config --global user.email "your_email@example.com"`
   - Set default text editor: `git config --global core.editor "<editor_name>"`

**2. Git Basics**
   - Clone a repository: `git clone <repository_url>`
   - Initialize a new Git repository: `git init`
   - Add changes to the staging area: `git add <file_name>` or `git add .` (to add all changes)
   - Commit changes to the repository: `git commit -m "Commit message"`
   - View commit history: `git log`
   - View commit history with details: `git log --oneline --decorate --graph`
   - Undo changes in working directory: `git checkout -- <file_name>`
   - Unstage changes: `git reset HEAD <file_name>`
   - Revert changes in a commit: `git revert <commit_hash>`
   - Reset to a previous commit: `git reset --hard <commit_hash>`

**3. Working with Remotes**
   - Add a remote repository: `git remote add <remote_name> <repository_url>`
   - Push changes to a remote repository: `git push <remote_name> <branch_name>`
   - Pull changes from a remote repository: `git pull <remote_name> <branch_name>`
   - Fetch changes from a remote repository: `git fetch <remote_name>`
   - Show remote repositories: `git remote -v`

**4. Git Branching**
   - Create a new branch: `git checkout -b <branch_name>`
   - Switch to a branch: `git checkout <branch_name>`
   - Merge branches: `git merge <branch_name>`
   - Delete a branch: `git branch -d <branch_name>`
   - Rename a branch: `git branch -m <new_branch_name>`
   - List all branches: `git branch`
   - Show current branch: `git branch --show-current`

**5. Tagging**
   - Create a lightweight tag: `git tag <tag_name>`
   - Create an annotated tag: `git tag -a <tag_name> -m "Tag message"`
   - List all tags: `git tag`
   - Delete a tag: `git tag -d <tag_name>`
   - Push tags to a remote repository: `git push --tags`
   - Show tag details: `git show <tag_name>`

**6. Git Tools**
   - Select specific commits for an operation: `git rev-list <commit_range>`
   - Stage hunks or lines interactively: `git add -p`
   - Stash changes: `git stash`
   - Apply changes from a stash: `git stash apply`
   - Sign commits: `git commit -S`
   - Search for commits: `git log --grep="<search_pattern>"`
   - Rewrite commit history: `git rebase -i <base>`
   - Demystify reset options: `git reset --<mode> <commit>`
   - Perform advanced merges: `git merge --ours <branch>` or `git merge --theirs <branch>`
   - Enable Rerere: `git config --global rerere.enabled true`
   - Debug with Git: `git bisect start`

**7. Git on the Server**
   - Choose a protocol for communication: `git://`, `https://`, `ssh://`
   - Set up a Git server: `git init --bare`
   - Generate an SSH key pair: `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
   - Copy SSH public key to the server: `ssh-copy-id username@hostname`
   - Start Git daemon: `git daemon [--base-path=. --export-all]`
   - Configure Smart HTTP: Enable CGI and Apache modules
   - Set up GitWeb: Configure `gitweb.conf`
   - Install GitLab: Follow installation instructions
   - Explore third-party hosted options: GitHub, Bitbucket, GitLab

**8. Git Tools**
   - Configure Git: `git config`
   - Define attributes for files: `.gitattributes`
   - Customize Git behavior: `.git/hooks`
   - Implement Git-enforced policies: Script hooks to enforce policies

**9. Internals**
   - Understand Git internals: Core components and interactions
   - Explore Git objects: Blobs, trees, commits, tags
   - Manipulate Git references: Branches, tags, HEAD
   - Work with packfiles: Compressed storage of Git objects
   - Specify the refspec: `git push <remote> <refspec>`
   - Utilize transfer protocols: HTTP, SSH, Git protocol
   - Perform maintenance and recovery tasks: Garbage collection, fsck
   - Utilize environment variables: `GIT_DIR`, `GIT_WORK_TREE`, etc.

**10. Distributed Git**
   - Implement distributed workflows: Centralized, integration manager, dictator and lieutenants
   - Contribute to a project: Fork, clone, branch, commit, push, pull request
   - Maintain a project: Review, merge, resolve conflicts, release

This comprehensive set of commands covers various aspects of Git usage, from basic operations like cloning and committing to more advanced tasks like configuring Git server, managing hooks, and understanding Git internals. Feel free to explore and experiment with these commands to enhance your Git skills!
