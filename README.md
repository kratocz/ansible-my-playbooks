# ansible-my-playbooks
The Ansible playbooks I use for my servers. You can get inspired.

Clone this repository and see the usage below or just get inspired from my playbook(s):
- [ubuntu-server.yml](ubuntu-server.yml)

## Usage
1. Install `ansible`
2. Clone this repository
3. Add your target hosts to the file `/etc/ansible/hosts` (alternatively you can use `inventory.ini` file in any directory, see the [Ansible documentation](https://docs.ansible.com/ansible/latest/getting_started/get_started_inventory.html)), e.g. add lines:
```
[servers_ubuntu]
web1.example.com
web2.example.com
```
4. In the cloned repository directory execute:
```
ansible-playbook ubuntu-server.yml
```
