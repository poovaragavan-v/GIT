### Git-Enforced Policy Example Cheat Sheet

#### Server-Side Hook (update)
- **Purpose:** Enforce commit message format and user-based ACL system.
- **Arguments:** Reference name, old revision, new revision.
- **Implementation:** Ruby script in `hooks/update`.
- **Functionality:**
  - Validates commit messages against a specified format.
  - Enforces user-based access control list (ACL) for directory permissions.
  
#### Commit Message Format Enforcement
- **Script:** commit-msg
- **Purpose:** Validate commit messages before committing.
- **Implementation:** Ruby script in `.git/hooks/commit-msg`.
- **Functionality:** Aborts commit if message format is incorrect.

#### User-Based ACL Enforcement
- **Script:** pre-commit
- **Purpose:** Enforce user-based ACL system.
- **Implementation:** Ruby script in `.git/hooks/pre-commit`.
- **Functionality:** Ensures user has access to modified directories/files.

#### Additional Checks (Optional)
- **Pre-Rebase Script:**
  - **Purpose:** Prevent non-fast-forward rebases.
  - **Implementation:** Ruby script in `.git/hooks/pre-rebase`.
  - **Functionality:** Aborts rebase if commits have already been pushed.