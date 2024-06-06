**Advanced Merging in Git**

Git's powerful merging capabilities make it easy to manage long-lived branches, keeping them up to date and resolving small conflicts frequently to avoid significant issues later. However, more complex conflicts can arise, and Git provides various tools to handle these situations effectively. In this guide, we'll explore advanced merging techniques, handling tricky conflicts, and different types of merges in Git.

### Merge Conflicts

When performing merges in Git, conflicts can occur, especially if branches diverge significantly. Git's philosophy is to be smart about determining unambiguous merge resolutions but not overly clever in automatically resolving conflicts. Here are some techniques to manage and resolve merge conflicts.

1. **Preparing for a Merge**:
    - Ensure your working directory is clean before attempting a merge.
    - Commit or stash any work in progress to avoid losing changes.

2. **Simple Example**:
    - Consider a Ruby file `hello.rb` that prints 'hello world'.
    ```ruby
    #! /usr/bin/env ruby

    def hello
      puts 'hello world'
    end

    hello()
    ```
    - We create a new branch `whitespace` and make some changes.
    ```sh
    $ git checkout -b whitespace
    $ unix2dos hello.rb
    $ git commit -am 'Convert hello.rb to DOS'
    $ vim hello.rb
    $ git commit -am 'Use Spanish instead of English'
    ```
    - Switch back to `master` and add a comment.
    ```sh
    $ git checkout master
    $ vim hello.rb
    $ git commit -am 'Add comment documenting the function'
    ```

3. **Merging and Resolving Conflicts**:
    - Attempting to merge `whitespace` into `master` causes conflicts due to whitespace changes.
    ```sh
    $ git merge whitespace
    Auto-merging hello.rb
    CONFLICT (content): Merge conflict in hello.rb
    Automatic merge failed; fix conflicts and then commit the result.
    ```
    - To back out of the merge:
    ```sh
    $ git merge --abort
    ```

4. **Ignoring Whitespace**:
    - Use merge strategies to ignore whitespace changes.
    ```sh
    $ git merge -Xignore-space-change whitespace
    ```

### Manual File Re-merging

When Git cannot handle changes automatically, you can manually resolve conflicts.

1. **Extract File Versions**:
    ```sh
    $ git show :1:hello.rb > hello.common.rb
    $ git show :2:hello.rb > hello.ours.rb
    $ git show :3:hello.rb > hello.theirs.rb
    ```

2. **Manual Merge**:
    - Convert the file to the appropriate format and merge manually.
    ```sh
    $ dos2unix hello.theirs.rb
    $ git merge-file -p hello.ours.rb hello.common.rb hello.theirs.rb > hello.rb
    ```

### Tools for Checking and Resolving Conflicts

1. **Checkout Conflicts**:
    - Use `git checkout --conflict=diff3` for more context.
    ```sh
    $ git checkout --conflict=diff3 hello.rb
    ```

2. **Merge Log**:
    - Use `git log --oneline --left-right --merge` to see commits causing conflicts.
    ```sh
    $ git log --oneline --left-right --merge
    ```

3. **Combined Diff Format**:
    - Use `git diff` to see remaining conflicts.
    ```sh
    $ git diff
    ```

### Undoing Merges

1. **Fix the References**:
    - Use `git reset --hard HEAD~` to reset the branch pointer.
    ```sh
    $ git reset --hard HEAD~
    ```

2. **Reverse the Commit**:
    - Use `git revert -m 1 HEAD` to create a new commit that undoes changes from a merge.
    ```sh
    $ git revert -m 1 HEAD
    ```

### Other Types of Merges

1. **Preference Merging**:
    - Use `-Xours` or `-Xtheirs` to favor one side in case of conflicts.
    ```sh
    $ git merge -Xours mundo
    ```

By leveraging these advanced merging techniques and tools, you can handle complex conflicts and maintain a clean and consistent codebase in Git.