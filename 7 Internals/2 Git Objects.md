### Git Objects Cheat Sheet

#### Content-Addressable Filesystem
- **Definition:** Git operates as a content-addressable filesystem.
- **Key Concept:** Git uses a simple key-value data store where any content inserted into a repository is assigned a unique key for retrieval.

#### Blob Objects
- **Description:** Individual files' content stored in the Git database.
- **Creation:** Generated using the `git hash-object` command.
- **Format:** SHA-1 hash identifies the content, stored as a single file in `.git/objects` directory.
- **Retrieval:** Content can be accessed using `git cat-file`.

#### Tree Objects
- **Description:** Organizes blobs and other trees to represent directories and files' hierarchy.
- **Creation:** Generated from the staging area using `git write-tree`.
- **Format:** Contains entries with SHA-1 hashes of blobs or subtrees, along with mode, type, and filename.
- **Retrieval:** Accessed using `git cat-file`.

#### Commit Objects
- **Description:** Records changes and metadata, including author, committer, timestamp, and commit message.
- **Creation:** Created using `git commit-tree` referencing a tree and parent commit(s).
- **Format:** Contains references to a tree, parent commit(s), author, committer, timestamp, and message.
- **Retrieval:** Metadata viewable using `git cat-file -p`.

#### Object Storage
- **Header:** Specifies object type and content size.
- **Checksum:** SHA-1 hash calculated for the concatenated header and content.
- **Compression:** Content compressed using zlib library.
- **Storage:** Objects stored in `.git/objects` directory under subdirectories based on SHA-1 hash.

Understanding Git objects and their creation process provides insights into how Git stores and manages versioned content, facilitating efficient version control and collaboration.