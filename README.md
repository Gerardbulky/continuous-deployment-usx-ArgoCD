### Install Grafana using Ansible playbook

#### Prerequisites:
2 VM ( 1 ansibleVM and 1 GrafanaVM)
ubuntu 20.04

#### Steps to setup SSH:
- Generate an rsa key on the Ansible server using `ssh-keygen -t rsa`
- Copy the Ansible public key to the authorized keys in the Grafana server using `ssh-copy-id ubuntu@<private-ip-ansible-server>`
- Remove # from PasswordAuthentication in the ssh_config directory to create a passwordless connnection for ssh. `sudo vi /etc/ssh/sshd_config`
- Restart SSH service: `sudo service sshd restart`
- In the Ansible host directory, add the private key to configure the Grafana server as a host for Ansible. `[webnode]
<private-ip-of-grafana server>` 

- Use ping to test the Ansible server setup `ansible -m ping webnode`.

#### Steps to setup Playbook:
- From the cli Create a playbook.yml file. In the playbook.yml create a Host and tasks. 
- Links to install the packages and Grafana.
Install prerequisite packages: https://grafana.com/docs/grafana/latest/setup-grafana/installation/debian/
Download Grafana: https://grafana.com/grafana/download


#### Steps to Run the Playbook:
- Connect to the ansibleVM using SSH and navigate to the cli containing the ansible-playbook.yml file. 
Run `ansible-playbook ansible-playbook.yml`

#### Live Grafana Server:
Server URL: http://13.49.175.73:3000

##### Optional Options:
Sign into the Grafana server using 
User: admin
Password: xxxxx
