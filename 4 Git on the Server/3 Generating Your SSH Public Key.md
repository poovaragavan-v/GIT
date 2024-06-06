# Generating your SSH public key:

**Checking Existing Keys:**
- Check for existing keys in the `~/.ssh` directory using `ls` command.

**Generating a New SSH Key:**
- Use the `ssh-keygen` command to generate a new key pair.
- Confirm the file to save the key, optionally set a passphrase (use `-o` option for better security), and save the key.

**Sending Public Key:**
- Users need to send their public keys to the administrator of the Git server.
- Public keys are stored in `.pub` files in the `~/.ssh` directory.
- Users can copy the contents of the `.pub` file and share it with the administrator.

**Public Key Format:**
- Public keys are in the format: `ssh-rsa <key-data> <comment>`.
- The public key contains a comment with information about the user's system.

For detailed instructions on creating SSH keys on different operating systems, users can refer to the GitHub guide on SSH keys.