Here's a summarized version of the provided text tailored for a cheat sheet:

---

**Debugging with Git**

1. **File Annotation:**
   - Use `git blame <file>` to track down bugs by annotating each line with the commit that last modified it.
   - Example: `git blame -L 69,82 Makefile`

2. **Binary Search (git bisect):**
   - Identify the commit introducing an issue with `git bisect`.
   - Start: `git bisect start`
   - Mark current state as bad: `git bisect bad`
   - Mark last known good state: `git bisect good <commit>`
   - Git performs binary search, checking out commits for testing.
   - Mark tested commit as good or bad.
   - Git identifies first bad commit.
   - Reset: `git bisect reset`

3. **Automating git bisect:**
   - Provide known bad and good commits.
   - Run script to automate testing: `git bisect run <test_script>`

---
