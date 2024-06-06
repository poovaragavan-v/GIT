
**Starting the Daemon:**
- Run `git daemon --reuseaddr --base-path=/srv/git/ /srv/git/` to start the daemon.
- `--reuseaddr` allows the server to restart without waiting for old connections to time out.
- `--base-path` allows cloning projects without specifying the entire path.
- Ensure port 9418 is open on your firewall.

**Using systemd (for systemd-based systems):**
- Create a service file in `/etc/systemd/system/git-daemon.service`.
- Specify `git daemon` command with options in `ExecStart`.
- Set `User` and `Group` as appropriate.
- Enable the service with `systemctl enable git-daemon`.
- Start and stop the service with `systemctl start git-daemon` and `systemctl stop git-daemon`.

**Setting Up Repositories:**
- Create a file named `git-daemon-export-ok` in each repository to allow unauthenticated access.

With these steps, you can set up Git Daemon to serve repositories over the Git protocol.