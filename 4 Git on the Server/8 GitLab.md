**Installation:**
- GitLab is installed via the official Omnibus GitLab package, which is well-documented and supported.
- Other installation options include Helm chart for Kubernetes, Dockerized packages, source files, and cloud providers.
- Installation via Omnibus GitLab generates a root password stored in /etc/gitlab/initial_root_password.

**Administration:**
- GitLab's administration interface is accessed via the web browser by logging in as the root user.
- Administration tasks include user management, group management, and project management.
- User accounts are associated with personal information and a namespace for projects.
- Groups are collections of projects with associated permissions for users.
- Projects correspond to Git repositories with visibility levels (Private, Internal, Public).

**Basic Usage:**
- Creating a new project involves specifying its name, namespace, and visibility level.
- Projects can be accessed over HTTPS or SSH with remote URLs visible on the project's home page.
- GitLab provides views for recent activity, files, and commit log for each project.
- Collaboration can be done by giving users push access or using merge requests for controlled contributions.
- Merge requests and issues are used for discussion and code review, assignable to users or organized into milestones.
- GitLab offers additional features like wikis and system maintenance tools for team collaboration.

GitLab offers a fully-featured Git server solution with extensive collaboration features accessible through a web-based interface, making it suitable for teams of any size.