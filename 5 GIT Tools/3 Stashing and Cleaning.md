## Stashing and Cleaning Cheat Sheet

### Stashing Work
- **Purpose**: Temporarily save changes without committing.
- **Basic Commands**:
  - `git stash`: Stash all tracked and staged changes.
  - `git stash push`: Preferred over `git stash save`, supports selected pathspecs.
- **Options**:
  - `--keep-index`: Stash tracked changes but keep staged changes.
  - `-u` or `--include-untracked`: Include untracked files in stash.
  - `-a` or `--all`: Include both untracked and ignored files.
  - `--patch`: Interactively select changes to stash.
- **Applying Stashes**:
  - `git stash apply [stash@{n}]`: Apply a stash, specified by its identifier.
  - `git stash apply --index`: Reapply staged changes.
  - `git stash pop`: Apply and drop the stash.
- **Managing Stashes**:
  - `git stash list`: List all stashes.
  - `git stash drop [stash@{n}]`: Remove a specific stash.
  - `git stash branch <branchname>`: Create a branch from stashed changes.

### Cleaning Working Directory
- **Purpose**: Remove untracked files and directories.
- **Basic Commands**:
  - `git clean -f -d`: Remove untracked files and empty directories. Requires `-f` to force.
- **Options**:
  - `-n` or `--dry-run`: Preview what would be removed.
  - `-x`: Remove ignored files as well.
  - `-i`: Interactive mode for selective cleaning.
  - `-f -f`: Extra force to remove nested Git repositories.
- **Examples**:
  - `git clean -d -n`: Preview removal of untracked files and directories.
  - `git clean -d -f -x`: Remove untracked and ignored files.
  - `git clean -x -i`: Interactive removal, with steps to confirm each file.

### Best Practices
- **Preview Before Cleaning**: Always use `-n` before `-f` to avoid accidental data loss.
- **Use `--patch` for Stashing**: For selective stashing of changes.
- **Keep Index with Stashing**: Use `--keep-index` to maintain staged changes.

This cheat sheet summarizes essential commands for stashing and cleaning in Git, providing quick reference for common operations and best practices.