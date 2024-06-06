**Replacing Commits with Git Replace**

1. **Purpose:**
   - Git's replace command allows substituting one commit with another without changing SHA-1s upstream.

2. **Usage Scenarios:**
   - Useful for replacing a commit in history without rebuilding the entire history.
   - Helpful for grafting separate histories onto one another.

3. **Procedure:**
   - Identify the commit to be replaced and the replacement commit.
   - Use `git replace <commit_to_replace> <replacement_commit>`.

4. **Example:**
   ```bash
   git replace 81a708d c6e1e95
   ```
   
5. **Verification:**
   - Normal Git tools like bisect and blame work as expected.
   - Use `git cat-file -p <commit>` to inspect replaced commit data.
   
6. **Sharing Replacement:**
   - Replaced data is kept in references, facilitating sharing.
   - Push replacement to the server for others to download.

7. **Summary:**
   - Allows replacing commits in Git history seamlessly, maintaining integrity and history coherence.

---