Here's a cheat sheet summarizing the powerful revision selection techniques in Git:

### Single Revisions

#### Short SHA-1
- **Syntax:** `git show <short SHA-1>`
- **Example:** `git show 1c002d`
- **Notes:** The short SHA-1 must be at least four characters and unique within the project. Use `--abbrev-commit` with `git log` to show shorter SHA-1s.

#### Branch References
- **Syntax:** `git show <branch-name>`
- **Example:** `git show topic1`
- **Notes:** Use `git rev-parse <branch-name>` to get the full SHA-1.

### RefLog Shortnames
- **Syntax:** `git show <ref>@{<n>}` (where `<n>` is the entry number in reflog)
- **Example:** `git show HEAD@{5}`
- **Time-based:** `git show master@{yesterday}`
- **Formatted log:** `git log -g <ref>`

### Ancestry References
- **Caret (^)**
  - **First Parent:** `git show <ref>^`
  - **Nth Parent:** `git show <ref>^<n>`
  - **Example:** `git show HEAD^2`
- **Tilde (~)**
  - **Nth Generation:** `git show <ref>~<n>`
  - **Example:** `git show HEAD~3`
- **Combining Caret and Tilde:**
  - **Example:** `git show HEAD~2^2`

### Commit Ranges

#### Double Dot (..)
- **Syntax:** `git log <ref1>..<ref2>`
- **Example:**
  - **Commits in experiment but not in master:** `git log master..experiment`
  - **Commits in master but not in experiment:** `git log experiment..master`
  - **Commits to be pushed:** `git log origin/master..HEAD`

#### Multiple Points
- **Syntax:** `git log <refA> <refB> ^<refC>`
- **Example:** `git log refA refB --not refC`

#### Triple Dot (...)
- **Syntax:** `git log <ref1>...<ref2>`
- **Example:**
  - **Commits in either master or experiment but not both:** `git log master...experiment`
  - **With left-right indication:** `git log --left-right master...experiment`

### Notes
- **Reflog is local:** Reflog references are only relevant to your local repository and session.
- **Special Characters on Windows:**
  - **Caret (^)** must be doubled or quoted: `git show "HEAD^"` or `git show HEAD^^`
  - **Braces ({})** in PowerShell must be escaped or quoted: `git show HEAD@{0}` or `git show HEAD@`{0`}`

### Example History for Ranges
```
  A---B---C---D experiment
       \
        E---F master
```

Use these commands and techniques to navigate and manipulate your Git commit history more effectively.