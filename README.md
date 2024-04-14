# ansible-my-playbooks
The Ansible playbooks I use for my Linux servers and desktops. You can get inspired.

Tip: Also ChatGPT can create or adjust a playbook for you very well.

Clone this repository and see the usage below or just get inspired from my playbook(s):
- [ubuntu-server.yml](roles/common/tasks/packages-debian.yml)

## Supported OS
- Debian based Linuxes
- SUSE based Linuxes (including openSUSE)

## Usage
1. Install `ansible`
2. Clone this repository
3. Add your target hosts to the file `/etc/ansible/hosts` (alternatively you can use `inventory.ini` file in any directory, see the [Ansible documentation](https://docs.ansible.com/ansible/latest/getting_started/get_started_inventory.html)), e.g. add lines:
```
[servers]
web1.example.com
web2.example.com
```
For localhost desktop:
```
[desktops]
127.0.0.1 ansible_connection=local
```
4. In the cloned repository directory execute:
```
sudo ansible-playbook main.yml
```
Or simply:
```bash
./run
```

## Example output
I executed the command `ansible-playbook ubuntu-server.yml` on one of my servers when for the playbook file `ubuntu-server.yml` in this revision: [ubuntu-server.yml@5551642](https://github.com/kratocz/ansible-my-playbooks/blob/5551642efbddca70ba4647083d9cdc52389173b3/ubuntu-server.yml)

```
web6:~/ansible-my-playbooks # ansible-playbook ubuntu-server.yml
                                                                                           
PLAY [Install Packages and Clone .tmux on Ubuntu 22.04] *******************************************************************************************************************************
                                                                                                                                                                                       
TASK [Gathering Facts] ****************************************************************************************************************************************************************
ok: [web8.krato.cz]
ok: [web9.krato.cz]

TASK [Update apt package cache] *******************************************************************************************************************************************************
changed: [web8.krato.cz]
changed: [web9.krato.cz]

TASK [Install required packages] ******************************************************************************************************************************************************
ok: [web8.krato.cz] => (item=mc)
ok: [web9.krato.cz] => (item=mc)
ok: [web8.krato.cz] => (item=vim)
ok: [web9.krato.cz] => (item=vim)
ok: [web8.krato.cz] => (item=tmux)
ok: [web9.krato.cz] => (item=tmux)
ok: [web8.krato.cz] => (item=docker.io)
ok: [web9.krato.cz] => (item=docker.io)
ok: [web8.krato.cz] => (item=docker-compose)
ok: [web9.krato.cz] => (item=docker-compose)
ok: [web8.krato.cz] => (item=ncdu)
ok: [web9.krato.cz] => (item=ncdu)
ok: [web8.krato.cz] => (item=btrfs-compsize)
ok: [web9.krato.cz] => (item=btrfs-compsize)
ok: [web8.krato.cz] => (item=git)
ok: [web9.krato.cz] => (item=git)
ok: [web8.krato.cz] => (item=wireguard)
ok: [web9.krato.cz] => (item=wireguard)

TASK [Clone .tmux repository if not exists] *******************************************************************************************************************************************
ok: [web8.krato.cz]
ok: [web9.krato.cz]

TASK [Set tmux.conf symlink if not exists] ********************************************************************************************************************************************
ok: [web8.krato.cz]
ok: [web9.krato.cz]

TASK [Create /root/.tmux.conf.local if not exists] ************************************************************************************************************************************
ok: [web8.krato.cz]
ok: [web9.krato.cz]

TASK [Configure .tmux.conf.local] *****************************************************************************************************************************************************
ok: [web8.krato.cz] => (item=set -g @plugin 'kratocz/tmux-screen')
ok: [web9.krato.cz] => (item=set -g @plugin 'kratocz/tmux-screen')
ok: [web8.krato.cz] => (item=set -g @plugin 'kratocz/tmux-kratocz')
ok: [web9.krato.cz] => (item=set -g @plugin 'kratocz/tmux-kratocz')
ok: [web8.krato.cz] => (item=set -g base-index 0)
ok: [web9.krato.cz] => (item=set -g base-index 0)

PLAY RECAP ****************************************************************************************************************************************************************************
web8.krato.cz              : ok=7    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
web9.krato.cz              : ok=7    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```
