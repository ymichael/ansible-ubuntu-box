# Ansible Plays
Simple Ansible plays to configure a Ubuntu Server (14.04).

- Creates and sets up a new user (`newuser.yml`)
    - Creates new user
    - Configures passwordless ssh access
    - Adds user to sudoers
    - Disable root ssh access
    - Disable ssh access via passwords

- Installs various things (`main.yml`)
    - Apt (`tasks/apt.yml`)
        - Updates and upgrades apt-cache and installed packages
        - Installs [Fail2ban](http://www.fail2ban.org/wiki/index.php/Main_Page)
        - Installs [unattended-upgrades](https://wiki.debian.org/UnattendedUpgrades)
    - UFW (`tasks/ufw.yml`)
        - Reject all incoming connections by default
        - Allow all outgoing connections by default
        - Allow 22, 80, 443
    - Nodejs (`tasks/nodejs.yml`)
    - Docker (`tasks/docker.yml`)
    - Git
    - pip (Python)


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
- <https://www.digitalocean.com/community/tutorials/how-to-setup-a-firewall-with-ufw-on-an-ubuntu-and-debian-cloud-server>
- <https://github.com/zenzire/ansible-bootstrap-ubuntu>
