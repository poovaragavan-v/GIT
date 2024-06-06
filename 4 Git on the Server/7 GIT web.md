
**Using Instaweb:**
- Git comes with a command `git instaweb` to start a temporary instance of GitWeb.
- Use `git instaweb --httpd=webrick` to start instaweb with the Webrick server.
- Use `git instaweb --httpd=webrick --stop` to stop the server.

**Manual Setup:**
1. **Clone Git Source:**
   - Clone Git source code: `git clone https://git.kernel.org/pub/scm/git/git.git`.
   - Navigate to the cloned directory: `cd git/`.

2. **Generate GitWeb Script:**
   - Use make to generate the custom CGI script:
     ```
     make GITWEB_PROJECTROOT="/srv/git" prefix=/usr gitweb
     ```

3. **Copy Files:**
   - Copy the generated files to the web server directory:
     ```
     sudo cp -Rf gitweb /var/www/
     ```

4. **Configure Apache:**
   - Add a VirtualHost configuration for GitWeb:
     ```
     <VirtualHost *:80>
         ServerName gitserver
         DocumentRoot /var/www/gitweb
         <Directory /var/www/gitweb>
             Options +ExecCGI +FollowSymLinks +SymLinksIfOwnerMatch
             AllowOverride All
             Order allow,deny
             Allow from all
             AddHandler cgi-script cgi
             DirectoryIndex gitweb.cgi
         </Directory>
     </VirtualHost>
     ```

**Accessing GitWeb:**
- Visit `http://gitserver/` to view your repositories online.

GitWeb provides a simple web-based interface for visualizing Git repositories and can be set up with either the temporary instaweb command or a manual configuration for a permanent solution.