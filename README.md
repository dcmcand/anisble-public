# anisble-public
Ansible playbook setting up linux mint computers for use as public access computers for a public library.


1. On client computer:
  1. Install linux mint (This setup is tested for Mint 17.3 and 18)
  2. Install openssh-server 
  3. Edit /etc/ssh/sshd_config to allow for root login
  4. Restart sshd
2. On ansible computer:
  1. Add ip of client to /etc/ansible/hosts
  2. ssh-copy-id root@ip_of_client
  3. Run anisble-playbook public ansible/playbooks/public/public-setup.yml (this assumes you have a group called "public" setup in your /etc/ansible/hosts file)

You can setup multiple computers at a time 

