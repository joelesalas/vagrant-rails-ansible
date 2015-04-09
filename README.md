# vagrant-rails-ansible
Example Rails project using Vagrant and Ansible on CentOS 7. This makes use of Vagrant techniques such as NFS mounts for performance, package caching, and Ansible provisioning.

## Requirements
You will need the following:
- Virtualbox
- Vagrant
- `vagrant-cachier` plugin (recommended)
- `ansible` installed on your host machine (use `easy_install ansible` or `pip install ansible`)

## Instructions
- Run `vagrant up`. This will configure the vagrant box, install all the necessary software, and install Rails and its dependencies

- Shell into the vagrant box using `vagrant ssh`. Change directory to `/vagrant` and run `rails new .`. This will create a new Rails project
- Run `ifconfig`. There should be an IP somewhere in the 10.0.0.0/8 range (ex. `10.0.2.15`). Use this IP to invoke the WEBRick server: `rails server --binding=10.0.2.15`. This is necessary due to the NFS settings above.
- You should have a working Rails sample page at http://localhost:3000. 

## Troubleshooting
I tested this extensively but there may yet be issues. PRs and suggestions welcome! If you have issues:
- Make sure your gems are installing correctly
- Check your Rails debug output for clues
- Ensure that you're binding to the correct IP address (it will default to 127.0.0.1 which cannot receive forwarded traffic)
