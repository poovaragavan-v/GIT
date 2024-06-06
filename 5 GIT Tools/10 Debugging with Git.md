## Debugging with Git

### Overview
Beyond version control, Git offers powerful commands to aid in debugging your source code. These tools help you identify and fix bugs by pinpointing when and why changes were made, and by tracing the origin of problematic code.

### File Annotation
File annotation is a useful feature that shows the last commit to modify each line of a file. This is helpful when you need to identify when a bug was introduced and by whom. The `git blame` command provides this information.

#### Example Usage
To determine which commit and committer were responsible for specific lines in a file, use:
```sh
$ git blame -L 69,82 Makefile
```
This command reveals the commit SHA, author, date, line number, and content of the file.

To trace code that was copied from elsewhere, use `-C`:
```sh
$ git blame -C -L 141,153 GITPackUpload.m
```
This command reveals the origin of code snippets, even if they were moved from another file.

### Binary Search
When you don't know where a bug was introduced, and there have been many commits since the last known good state, you can use `git bisect` to perform a binary search through your commit history.

#### Example Usage
1. Start bisecting:
    ```sh
    $ git bisect start
    $ git bisect bad
    $ git bisect good v1.0
    ```
2. Test the middle commit:
    ```sh
    Bisecting: 6 revisions left to test after this
    [ecb6e1bc347ccecc5f9350d878ce677feb13d3b2] Error handling on repo
    ```
    If the issue exists in this commit:
    ```sh
    $ git bisect bad
    ```
    If the issue does not exist:
    ```sh
    $ git bisect good
    ```
3. Continue testing until Git identifies the problematic commit:
    ```sh
    $ git bisect good
    b047b02ea83310a70fd603dc8cd7a6cd13d15c04 is the first bad commit
    ```
4. Reset the bisect state:
    ```sh
    $ git bisect reset
    ```

#### Automation
You can automate the `git bisect` process if you have a script to test for the issue:
```sh
$ git bisect start HEAD v1.0
$ git bisect run test-error.sh
```
This runs `test-error.sh` on each checked-out commit until Git finds the first broken commit.

### Conclusion
Git's debugging tools, such as `git blame` and `git bisect`, provide powerful methods to track down bugs in your code. By using these tools effectively, you can identify the source of problems quickly and accurately, making it easier to maintain and improve your codebase.