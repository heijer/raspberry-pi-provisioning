# raspberry-pi-provisioning
Ansible provisioning for setting up Raspberry Pi with raspbian

## Preparation

* install ansible (http://docs.ansible.com/ansible/intro_installation.html).
  check version with `ansible --version`. I'm currently using `ansible 2.2.0.0`
* create a strong hashed password for your pi user (http://docs.ansible.com/ansible/faq.html#how-do-i-generate-crypted-passwords-for-the-user-module)
  create a file ``~/.ansible/vars.yml` and put your hashed password in like
  ```
  # password
  pi_passwd_hased: # put here your hashed password
  ```
* add an alias for your pi to your ssh config file ``~/.ssh/config`. Mine looks contains something like this:
  ```
  Host rp3b
     HostName <put-here-your-pi-ip-address>
     User <put-here-your-pi-user-name>
  ```

## Run the playbook

The first time you need to add the arguments to ask for connection and sudo password
```
ansible-playbook playbook.yml --ask-pass --ask-become-pass
```

After one successful run of the common role, ssh key authentication is used. Then you can simply run:
```
ansible-playbook playbook.yml
```
