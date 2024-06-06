## Signing Your Work in Git

### Introduction to GPG
- **Purpose**: Ensure commits and tags are from a trusted source by signing and verifying with GPG.
- **Setup**:
  - **List GPG keys**: `gpg --list-keys`
  - **Generate a GPG key**: `gpg --gen-key`
  - **Configure Git to use GPG key**: `git config --global user.signingkey <key-id>`

### Signing Tags
- **Sign a Tag**: Use `-s` instead of `-a` to sign a tag.
  ```bash
  $ git tag -s <tagname> -m 'message'
  ```
- **Verify a Signed Tag**: 
  ```bash
  $ git tag -v <tagname>
  ```

### Signing Commits
- **Sign a Commit**: Add `-S` to your commit command.
  ```bash
  $ git commit -S -m 'Signed commit'
  ```
- **View Signed Commits**: Use `--show-signature` with `git log`.
  ```bash
  $ git log --show-signature -1
  ```

### Configuring for Team Use
- **Automatic Commit Signing**: Configure Git to sign all commits by default.
  ```bash
  $ git config --local commit.gpgsign true
  ```

### Verifying Signatures in Merges
- **Verify Commits in Merges**: Use `--verify-signatures` with `git merge` or `git pull`.
  ```bash
  $ git merge --verify-signatures <branch>
  ```
- **Sign Merge Commit**: Use `-S` with `git merge`.
  ```bash
  $ git merge --verify-signatures -S <branch>
  ```

### Important Notes
- Ensure all team members are familiar with signing and verifying commits.
- Signing commits and tags adds an additional layer of security and trust.
- Understand the implications and setup GPG correctly before integrating it into your workflow.