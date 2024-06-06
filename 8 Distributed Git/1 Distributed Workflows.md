
1. **Centralized Workflow:**
   - Single central repository accepts code contributions.
   - Developers synchronize their work with the central repository.
   - Avoids overwriting changes, requires merging before pushing.
   - Suitable for teams familiar with centralized workflows.

2. **Integration-Manager Workflow:**
   - Each developer has write access to their own public repository and read access to others'.
   - Contributors make changes in their repository, then send a pull request to the maintainer of the main project.
   - Maintainer reviews and merges changes into the main repository.
   - Allows contributors to work at their own pace without waiting for project incorporation.

3. **Dictator and Lieutenants Workflow:**
   - Used in large projects with many collaborators, like the Linux kernel.
   - Dictator (project leader) delegates work to lieutenants who manage certain parts of the repository.
   - Lieutenants merge developers' changes into their master branch, then dictator merges lieutenants' branches into the main master branch.
   - Dictator pushes master branch to a reference repository for other developers to rebase on.
   - Useful in highly hierarchical environments with a centralized authority for integration.