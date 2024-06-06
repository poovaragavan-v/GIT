**Git Credential Storage**

1. **Purpose:**
   - Facilitates secure authentication for Git operations over HTTP protocols.
   - Offers various storage options to avoid repetitive username/password inputs.

2. **Available Modes:**
   - Default (no caching): Prompts for credentials every time.
   - Cache: Stores credentials in memory for a limited time.
   - Store: Saves credentials in plain-text file on disk.
   - OSXKeychain (macOS): Stores credentials securely in system keychain.
   - Git Credential Manager (Windows): Utilizes Windows Credential Store for secure storage.

3. **Configuration:**
   - Set via `git config --global credential.helper <mode>`.
   - Additional options available for some helpers:
     - `store --file <path>`: Customize file location for stored credentials.
     - `cache --timeout <seconds>`: Adjust cache expiration time.

4. **Multiple Helpers:**
   - Configure multiple helpers in `.gitconfig` to prioritize storage methods.
   - Git queries helpers sequentially until credentials are provided.

5. **Under the Hood:**
   - Git's root command for credential helpers is `git credential`.
   - Helpers communicate via stdin/stdout.
   - Actions include get (request credentials), store (save credentials), and erase (delete credentials).
   - Credentials can be stored in various formats (e.g., plain text, system keychain).

6. **Custom Credential Cache:**
   - Write custom credential helpers to address specific needs.
   - Helpers respond to get action and utilize compatible file formats.
   - Extending the system is feasible with any programming language.

7. **Example Usage:**
   - Enable read-only custom helper:
     ```bash
     git config --global credential.helper 'read-only --file /mnt/shared/creds'
     ```

8. **Summary:**
   - Git's credential storage system offers flexibility and security in managing authentication, catering to different use cases and platforms.

---