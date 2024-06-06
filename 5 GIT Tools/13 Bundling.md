Here's a summarized version of the provided text tailored for a cheat sheet:

---

**Bundling with Git**

1. **Purpose:**
   - Bundling allows packaging Git data into a single file for offline transfer or backup.

2. **Creating a Bundle:**
   - Use `git bundle create <file> <branch>` to create a bundle file.
   - Example: `git bundle create repo.bundle HEAD master`

3. **Using a Bundle:**
   - To clone from a bundle: `git clone <bundle_file> <directory>`
   - Example: `git clone repo.bundle repo`

4. **Updating a Bundle:**
   - Determine commit range to include.
   - Create bundle: `git bundle create <file> <commit_range>`
   - Example: `git bundle create commits.bundle master ^9a466c5`

5. **Verifying and Importing:**
   - Verify bundle: `git bundle verify <file>`
   - Import commits: `git fetch <bundle_file> <branch>:<local_branch>`
   - Example: `git fetch ../commits.bundle master:other-master`

---