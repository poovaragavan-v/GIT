## Git Search Cheat Sheet

### Git Grep
- **Basic Search**: Search through the working directory for a string.
  ```bash
  $ git grep 'search-string'
  ```
- **Show Line Numbers**: Display line numbers where matches are found.
  ```bash
  $ git grep -n 'search-string'
  ```
- **Count Matches**: Show the number of matches in each file.
  ```bash
  $ git grep --count 'search-string'
  ```
- **Show Function Context**: Display the enclosing function or method for matches.
  ```bash
  $ git grep -p 'search-string' *.c
  ```
- **Search with Conditions**: Find lines containing multiple conditions.
  ```bash
  $ git grep --break --heading -n -e '#define' --and \( -e LINK -e BUF_MAX \) v1.8.0
  ```

### Git Log Searching
- **Pickaxe Search**: Find commits that added or removed a particular string.
  ```bash
  $ git log -S 'search-string' --oneline
  ```
- **Regex Search**: Use a regular expression to find commits matching the pattern.
  ```bash
  $ git log -G 'regex-pattern'
  ```

### Line Log Search
- **Function History**: Show the history of a specific function in a file.
  ```bash
  $ git log -L :function_name:file_path
  ```
- **Custom Regex for Function**: Use a regex to specify the function.
  ```bash
  $ git log -L '/start-regex/', '/end-regex/':file_path
  ```
- **Line Range History**: Show the history of specific lines in a file.
  ```bash
  $ git log -L <start-line>,<end-line>:file_path
  ```

### Example Commands
- **Find occurrences of `gmtime_r` with line numbers**:
  ```bash
  $ git grep -n gmtime_r
  ```
- **Count occurrences of `gmtime_r` in each file**:
  ```bash
  $ git grep --count gmtime_r
  ```
- **Show functions calling `gmtime_r` in `.c` files**:
  ```bash
  $ git grep -p gmtime_r *.c
  ```
- **Search for commits introducing `ZLIB_BUF_MAX`**:
  ```bash
  $ git log -S ZLIB_BUF_MAX --oneline
  ```
- **Show history of `git_deflate_bound` function in `zlib.c`**:
  ```bash
  $ git log -L :git_deflate_bound:zlib.c
  ```

### Additional Tips
- Use `--break` and `--heading` options with `git grep` for better readability.
- Combine `git grep` with Git’s version control features to search through different versions of the codebase efficiently.
- The `-S` and `-L` options in `git log` are particularly powerful for tracing the evolution of code and identifying when specific changes were introduced.