# Ansible Plays
Simple Ansible plays to configure a Ubuntu Server (14.04).


## Background
I find myself having to do the same setup each time I start a new server.

## Usage

1. Add node ip to hosts file.

        echo NODE_ID > hosts

2. Create new user on the droplet

        ansible-playbook -i hosts newuser.yml -u root

3. Enter prompt for username and public key file.

4. Update hosts file to reflect new user

        // hosts
        NODE_ID ansible_ssh_private_key_file=PATH_TO_PRIVATE_KEY ansible_ssh_user=USERNAME

        // Alternatively, update your ~/.ssh/config file.

5. Run the main play.
    

        // Edit to exclude/include relevant tasks.
        ansible-playbook -i hosts main.yml


## TODO

- Add more tasks to install various things/dependencies

## Credits
- <https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-14-04>
- <https://github.com/zenzire/ansible-bootstrap-ubuntu>
