# Ansible Plays
Simple Ansible plays to configure a Ubuntu Server (14.04).

Instructions here specific to Digital Ocean.

## Background
I find myself having to do the same setup each time I start a new server.

## Usage

1. Add droplet ip to hosts file.

        echo DROPLET_IP > hosts

2. Create new user on the droplet

        ansible-playbook -i hosts newuser.yml -u root

3. Enter prompt for username and public key file.

4. Update hosts file to reflect new user

        // hosts
        DROPLET_IP ansible_ssh_private_key_file=PATH_TO_PRIVATE_KEY ansible_ssh_user=USERNAME

        // Alternatively, update your ~/.ssh/config file.

5. Run the main play.

        ansible-playbook -i hosts main.yml


## Credits
- [https://github.com/zenzire/ansible-bootstrap-ubuntu](https://github.com/zenzire/ansible-bootstrap-ubuntu)