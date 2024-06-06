## Interactive Staging with Git

Interactive staging in Git helps you craft your commits by allowing you to stage specific changes from your working directory. This ensures your commits are logically separated and can be easily reviewed. Here's a summary of key commands and steps for interactive staging based on a cheat sheet.

### Entering Interactive Mode
- **Command**: `git add -i`
- **Description**: Opens an interactive shell displaying the status of your staged and unstaged changes along with available commands.

### Interactive Shell Commands
- **Commands Menu**:
  - `1: [s]tatus` - View the status of files.
  - `2: [u]pdate` - Stage selected files.
  - `3: [r]evert` - Unstage selected files.
  - `4: [a]dd untracked` - Add untracked files.
  - `5: [p]atch` - Stage parts of files (patch mode).
  - `6: [d]iff` - Show differences of staged changes.
  - `7: [q]uit` - Exit the interactive shell.
  - `8: [h]elp` - Display help information.

### Staging and Unstaging Files
1. **Staging Files**:
   - **Command**: `u` or `2`
   - **Prompt**: `Update>>`
   - **Example**: `Update>> 1,2` to stage files 1 and 2.
   - **Result**: Files marked with `*` are staged.

2. **Unstaging Files**:
   - **Command**: `r` or `3`
   - **Prompt**: `Revert>>`
   - **Example**: `Revert>> 1` to unstage file 1.
   - **Result**: Selected file is unstaged.

### Viewing Differences
- **Command**: `d` or `6`
- **Prompt**: `Review diff>>`
- **Example**: `Review diff>> 1` to view the diff of file 1.
- **Result**: Shows staged changes for selected files.

### Staging Patches
1. **Entering Patch Mode**:
   - **Command**: `p` or `5`
   - **Prompt**: Choose files to partially stage.

2. **Interactive Patch Options**:
   - `y` - Stage this hunk.
   - `n` - Do not stage this hunk.
   - `a` - Stage this and all remaining hunks.
   - `d` - Do not stage this nor any remaining hunks.
   - `j` - Skip this hunk, move to next.
   - `J` - Skip this hunk, move to next undecided.
   - `k` - Skip this hunk, move to previous undecided.
   - `K` - Skip this hunk, move to previous.
   - `s` - Split the current hunk into smaller hunks.
   - `e` - Edit the current hunk manually.
   - `?` - Show help for patch options.

### Partial Staging
- **Command**: `git add -p` or `git add --patch`
- **Description**: Start patch mode for partial-file staging without entering interactive mode.

### Additional Commands for Patch Mode
- **Reset**: `git reset --patch`
- **Checkout**: `git checkout --patch`
- **Stash**: `git stash save --patch`

These commands allow granular control over your staging area, enabling you to stage, unstage, and review changes effectively to maintain clean and focused commits.