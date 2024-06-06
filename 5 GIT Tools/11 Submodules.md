Certainly! Here's a revised version of the summary based on the cheat sheet:

---

**Adding Submodules**

1. **Add Submodule:** Use `git submodule add <repository URL> <path>` to include a submodule.
2. **Commit Changes:** After adding, commit the changes with `git commit -m "Added submodule <name>"`.

**Updating Submodules**

1. **Manual Update:** Navigate to the submodule directory and pull changes using `git pull`.
2. **Automatic Update:** Execute `git submodule update --remote` to update submodules automatically.
3. **Branch Tracking:** Define submodule branches in `.gitmodules` or local `.git/config` for specific tracking.

**Working with Submodules**

1. **Set Up Submodules:** Checkout a branch for submodules with `git checkout <branch>`.
2. **Merge Remote Changes:** Merge remote changes with `git submodule update --remote --merge`.
3. **Resolve Conflicts:** Resolve conflicts using `git submodule update --remote --rebase`.
4. **Push Changes:** Ensure submodule changes are pushed using `git push --recurse-submodules=check` or `on-demand`.
5. **Manual Conflict Resolution:** Resolve submodule merge conflicts manually by updating submodule references.

**Submodule Tips:**

1. **Batch Operations:** Utilize `git submodule foreach` for batch operations across submodules.
2. **Aliases:** Create aliases for common submodule commands like update and push.
3. **Caution:** Be cautious when switching branches or converting directories to submodules to avoid unexpected behavior.

---