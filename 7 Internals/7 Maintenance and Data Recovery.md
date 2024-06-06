# Maintenance and data recovery procedures

### Maintenance:
1. **Auto Garbage Collection (GC):** Git occasionally runs a command called "auto gc" to clean up the repository. If there are too many loose objects or packfiles, Git launches a full-fledged `git gc` command. It gathers loose objects, consolidates packfiles, and removes unreferenced objects.
   - Manually trigger auto gc: `$ git gc --auto`
   - Adjust limits with `gc.auto` and `gc.autopacklimit` config settings.

2. **Pack References:** Git packs up references into a single file (`.git/packed-refs`) for efficiency.

### Data Recovery:
1. **Recovering Lost Commits:**
   - Use `git reflog` to review the history of HEAD movements.
   - Use `git log -g` for a more detailed log output.
   - If commits are lost, find them in the reflog and create a new branch at that commit.

2. **Finding Lost Objects:**
   - Use `git fsck --full` to check for integrity and list dangling objects.
   - Identify lost commits or objects, and recover them by adding branches or references to them.

### Removing Large Objects:
1. **Identifying Large Objects:**
   - Use `git verify-pack` to identify large objects in packfiles.
   - Use `git rev-list --objects --all` to find blob SHA-1s and associated file paths.

2. **Removing Large Objects from History:**
   - Rewrite history using `git filter-branch --index-filter` to remove large objects from the index.
   - Remove old references and repack the repository to save space.

These procedures help maintain the efficiency and integrity of Git repositories, as well as recover lost or unwanted data.