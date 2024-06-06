# Setting up SSH access on the server side:

**Creating a Git User and Directory:**
- Create a new user account for Git: `$ sudo adduser git`.
- Switch to the git user: `$ su git`.
- Create the `.ssh` directory and set permissions: `$ mkdir .ssh && chmod 700 .ssh`.
- Create the `authorized_keys` file and set permissions: `$ touch .ssh/authorized_keys && chmod 600 .ssh/authorized_keys`.

**Adding Developer SSH Keys:**
- Append developer SSH public keys to the `authorized_keys` file: `$ cat /tmp/id_rsa.john.pub >> ~/.ssh/authorized_keys`.

**Setting Up Empty Repository:**
- Create a directory for the repository: `$ mkdir project.git`.
- Initialize a bare Git repository: `$ git init --bare`.

**Pushing to the Repository:**
- Developers can push their project to the repository by adding it as a remote and pushing a branch.

**Restricting Git User Access:**
- Optionally, restrict shell access for the git user by changing the shell to `git-shell`.
- Add the path of `git-shell` to `/etc/shells`.
- Change the shell for the git user: `$ sudo chsh git -s $(which git-shell)`.
- Ensure SSH connection still works for Git operations but shell access is restricted.

**Additional Security Measures:**
- Optionally, prevent SSH port forwarding and other features by editing the `authorized_keys` file and adding restrictions to each key.

With these steps, you can set up SSH access for Git on your server, restrict shell access for the git user, and ensure secure collaboration on your Git repositories.