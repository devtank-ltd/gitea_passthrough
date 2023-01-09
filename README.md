Gitea Passthrough
=================

This is to support two mount points of the same git location. One raw on the host machine, and one in a LXC container with gitea.

It allows you to pass through push event from the host machine to gitea in LXC.

It currently assumes MySQL/MariaDB DB for gitea.
It assumes gitea is at path /home/git/gitea.
It assumes a git user is being used. (You should make sure the UID and GID for git are the same in the LXC container due to the bind mount.)


Installing
==========

Rename/move this folder as /home/git
This will mean when git hooks try and call /home/git/gitea, they call this script.

Copy etc/sudoers.d/gitea_passthrough to /etc/sudoers.d/gitea_passthrough and change permissions to be read only and only by root.
This the script can change to the git user on the host and push to git user in gitea.

Fill in you MySQL login in the file mysql_vars.
Fill in you LXC gitea container's IP address in the file gitea_lxc.
Fill in the gitea git user information in the file gitea_static (leave GIT_PROTOCOL blank).
