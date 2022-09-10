# My Ansible Playbooks

My collection of playbooks for things I need to rebuild quickly,
frequently or with a level of consistency. 

This isn't production. Stuff might be broken or inefficient, but it works well
enough for my simple use cases.

## Playbooks

### Local development environment

For rebuilding my Ubuntu workstation.

Requirements:

- Ubuntu 20.04.

Usage:

- Clone the repo on to a new installation
- cd into the directory
- `./local/dotfiles`

This will set up and install all the required packages for local development. This repo will 
then live at `$HOME/.dotfiles` and any future updates can be done there.

## Ansible-vault and values.yml

To add new values to the `values.yml` file, you need to run the following:

```shell
# encrypt contents of a file
 cat ~/.kube/k3s-remote | ansible-vault encrypt_string --vault-password-file ./local/vault-password.txt --stdin-name "kubectl_config.k3s-remote" >> ./local/values.yml
# encrypt from stdin
ansible-vault encrypt_string --vault-password ./local/vault-password.txt 'foobar' --name 'the_secret'
```

This will create an entry in the `values.yml` file in `yaml` format.

### Remote devices

To run it:

1. clone this repo
2. `ansible-playbook local.yml -u dan -i <ip_or_localhost>, --ask-become-pass --ask-vault-pass` - note the `,`!


## Development

How to develop this in the future:

1. Create a virtualbox ubuntu VM (Ubuntu Desktop)
2. Install ssh (`sudo apt install ssh -y`)
3. Get its IP address
4. From host, `ssh-copy-id <ip-addr>`
5. Develop playbook
6. Run playbook as required to test functionality
