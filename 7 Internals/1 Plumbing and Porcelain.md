### Git Internals Cheat Sheet

#### Plumbing and Porcelain
- **Definition:** Git has two types of commands:
  - **Porcelain:** High-level commands for common operations.
  - **Plumbing:** Low-level commands for internal operations.

#### .git Directory Structure
- **Purpose:** Contains nearly everything Git stores and manipulates.
- **Contents:** 
  - `config`: Project-specific configuration options.
  - `description`: Used by GitWeb program.
  - `HEAD`: Points to the currently checked out branch.
  - `hooks/`: Contains client- or server-side hook scripts.
  - `info/`: Stores global exclude file for ignored patterns.
  - `objects/`: Stores all content for the database.
  - `refs/`: Stores pointers into commit objects (branches, tags, etc.).
  - `index`: Stores staging area information.

#### Key Components
- **HEAD:** Points to the current branch.
- **Index:** Staging area for changes before committing.
- **Objects:** Stores compressed content of files.
- **Refs:** Stores pointers to commit objects.