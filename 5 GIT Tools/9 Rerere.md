## Git Tools - Rerere

### Overview
The `rerere` functionality in Git stands for "reuse recorded resolution." It allows Git to remember how you resolved a hunk conflict so that if it encounters the same conflict again, it can resolve it automatically for you. This feature is particularly useful for maintaining clean commit histories, especially in long-lived topic branches, frequent rebasing, or when merging evolving topic branches.

### Benefits
1. **Cleaner Commit History**: By using `rerere`, you can attempt merges and resolve conflicts without committing, then back out of the merge. This helps keep your commit history clean and organized.
2. **Rebasing Efficiency**: When rebasing branches, `rerere` can automatically resolve previously encountered conflicts, saving you from repetitive conflict resolution.
3. **Efficient Merge Handling**: Merging evolving topic branches into a testable head becomes easier. If tests fail, you can rewind merges and redo them without re-resolving conflicts.

### Enabling Rerere
To enable `rerere` globally:
```sh
$ git config --global rerere.enabled true
```
Alternatively, create the `.git/rr-cache` directory in a specific repository to enable it locally.

### Example Scenario
Consider a file `hello.rb` with the following content:
```ruby
#! /usr/bin/env ruby

def hello
  puts 'hello world'
end
```
- In one branch, change "hello" to "hola".
- In another branch, change "world" to "mundo".

#### Merge Conflict
When merging these branches, you encounter a conflict:
```sh
$ git merge i18n-world
Auto-merging hello.rb
CONFLICT (content): Merge conflict in hello.rb
Recorded preimage for 'hello.rb'
Automatic merge failed; fix conflicts and then commit the result.
```
`git rerere` has recorded the pre-merge state.

#### Resolving Conflict
Use `git status` to see conflicted files and `git rerere status` to check recorded pre-merge states:
```sh
$ git status
# Unmerged paths:
#   (use "git reset HEAD <file>..." to unstage)
#   (use "git add <file>..." to mark resolution)
#
#	both modified:      hello.rb

$ git rerere status
hello.rb
```
Resolve the conflict:
```sh
$ git rerere diff
--- a/hello.rb
+++ b/hello.rb
@@ -1,11 +1,11 @@
 #! /usr/bin/env ruby

 def hello
-<<<<<<<
-  puts 'hello mundo'
-=======
+<<<<<<< HEAD
   puts 'hola world'
->>>>>>>
+=======
+  puts 'hello mundo'
+>>>>>>> i18n-world
 end
```
Edit the file to:
```ruby
#! /usr/bin/env ruby

def hello
  puts 'hola mundo'
end
```
Then:
```sh
$ git add hello.rb
$ git commit
Recorded resolution for 'hello.rb'.
```

### Rebase Example
Undo the merge and rebase:
```sh
$ git reset --hard HEAD^
HEAD is now at ad63f15 i18n the hello

$ git checkout i18n-world
$ git rebase master
First, rewinding head to replay your work on top of it...
Applying: i18n one word
Auto-merging hello.rb
CONFLICT (content): Merge conflict in hello.rb
Resolved 'hello.rb' using previous resolution.
```
`git rerere` resolves the conflict using the recorded resolution.

### Final Steps
After rerere resolves the conflict:
```sh
$ git add hello.rb
$ git rebase --continue
Applying: i18n one word
```

### Conclusion
Using `rerere` can significantly streamline the process of merging and rebasing branches by automatically resolving previously encountered conflicts. This feature is particularly beneficial for keeping commit histories clean and reducing repetitive conflict resolution tasks.