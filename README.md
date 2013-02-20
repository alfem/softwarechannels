softwarechannels
================

Software Channels is a simple system to allow common (no admin) users to install
packages from restricted catalogs

Just define 'channels' (groups of packages) in a simple text file and 
give your users permissions to launch softwarechannels.

They will only see packages in channels matching their unix groups.

Set up:

- Place the binary "softwarechannels" in /usr/local/bin 
- Install PyZenity from Brian Ramos (http://brianramos.com/?page_id=38)
  (or use the copy in this git repo)
- Place the configuration file "softwarechannels.conf" in /etc/
- Add some packages to /etc/softwarechannels.conf (see provided sample file)
- Add these channels as groups to /etc/groups (use "addgroup yourgroup")
- Add a special group "softwarechannels" to /etc/groups
- Include one or more users in these groups (use "adduser youruser yourgroup")
- Include these users in the special group "softwarechannels"
- Add softwarechannels (binary) to /etc/sudoers with a line like this:

%softwarechannels ALL = NOPASSWD: /usr/local/bin/softwarechannels

Users in group "softwarechannels" will be allowed to launch softwarechannels
binary with sudo (or gksudo) without a password prompt.

Then, they will see a list of available "channels" and its packages.
