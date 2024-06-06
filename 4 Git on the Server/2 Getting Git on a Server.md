# Setting up Git on a server:

**Exporting a Repository:**
- To set up a Git server, you need to export an existing repository into a new bare repository using the `git clone --bare` command.
- Bare repositories are repositories without a working directory and typically have a `.git` suffix.

**Putting the Bare Repository on a Server:**
- Once you have a bare copy of your repository, you can put it on a server by copying it over using `scp` or similar methods.
- Other users with SSH access to the server can clone the repository using the SSH URL.
- Users with write access to the repository directory on the server will also have push access.

**Small Setups:**
- For small setups or organizations with few developers, user management can be simple.
- If all developers have SSH access to a server, it's easiest to set up the first repository there.
- Access control can be managed using filesystem permissions of the server's operating system.

**SSH Access:**
- To grant write access, you can create individual user accounts on the server or create a single 'git' user account and add SSH public keys of authorized users to the `authorized_keys` file.
- Another method is to authenticate SSH access from a centralized authentication source like LDAP.

Setting up a Git server for collaboration is relatively straightforward, especially for small teams or organizations. It mainly involves exporting a repository as a bare repository and putting it on a server accessible via SSH, with additional user management considerations for access control.