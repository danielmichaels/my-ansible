# My Ansible Playbooks

My collection of playbooks for things I need to rebuild quickly,
frequently or with a level of consistency. 

This isn't production. Stuff might be broken or inefficient but it works well
enough for my simple use cases.

## Playbooks

**local**

For rebuilding my Ubuntu workstation.

Requirements:

- Ubuntu 20.04 or 22.04 
- User account `dan`.

To run it:

1. clone this repo
2. `sh ansible-setup`
3. `ansible-galaxy install -r requirements.yml`
4. `ansible-playbook local.yml -u dan -i <ip_or_localhost>, --ask-become-pass --ask-vault-pass` - note the `,`!

How to develop this in the future:

1. Create a virtualbox ubuntu VM (Ubuntu Desktop)
2. Install ssh (`sudo apt install ssh -y`)
3. Get its IP address
4. From host, `ssh-copy-id <ip-addr>`
5. Develop playbook
6. Run playbook as required to test functionality
