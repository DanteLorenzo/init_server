## What does the ansible do

1. Creates a new user 
2. Add to the "sudo" group 
3. Disable ssh access to root 
4. Login with ssh key only

---
## How to use

Install:

```bash
sudo apt install ansible sshpass -y
```

Clone repository:

```bash
git clone https://github.com/DanteLorenzo/init_server.git
cd ./init_server
```

Before start ansible playbook create ssh keys:

```bash
ssh-keygen -t rsa
```

In `inventory/hosts.ini` set your IP, uncomment and set password for root(or use `-k` in command):

```yml
[servers]
srv1 ansible_host=YOUR_IP

[servers:vars]
ansible_user=root
#ansible_password=YOUR_SSH_ROOT_PASSWORD
#ansible_ssh_private_key_file="~/.ssh/id_rsa"
```

How you can use this command to set up server:

```bash
ansible-playbook init_server.yml -i inventory/hosts.ini -k -e "user=NEW_USER password=PASSWORD_FOR_USER"
```

--- 