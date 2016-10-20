# anisble-public
Ansible playbook setting up linux mint computers for use as public access computers for a public library.

This setup requires a control computer running linux to push out the configurations.  The computer only needs to be on the same subnet as your public computers. I am working on a bxe-boot setup that would make the first steps automatic, but that is still a work in progress.

1. On client computer:
  1. Install linux mint (This setup is tested for Mint 17.3 and 18)
  2. Install openssh-server 
  3. Edit /etc/ssh/sshd_config to allow for root login
  4. Restart sshd
2. On ansible computer:
  1. Add ip of client to /etc/ansible/hosts
  2. ssh-copy-id root@ip_of_client
  3. Run ansible-playbook public ansible/playbooks/public/public-setup.yml (this assumes you have a group called "public" setup in your /etc/ansible/hosts file)

You can setup multiple computers at a time 

In order to make changes to the setup:

1. Customize the public profile however you like on the client computer
2. Delete the Templates/public/public folder 
3. Copy /home/public from the client computer to Templates/public/ on your control computer.
4. Rerun ansible-playbooks public ansible/playbooks/public/public-setup.yml to push the changes out to all of your computers 

