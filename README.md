
# ansible-wifi 

A simple Ansible role to install and configure wpa_supplicant.

## Requirements

* a user with sudo permissions

## Install the role via Ansible Galaxy

Typical run:
```sh
$ ansible-galaxy install layereight.wifi
```

If you want to install a specific version directly from github:
```sh
$ ansible-galaxy install -r requirements.yml
```
*requirements.yml*
```YAML
- name: layereight.wifi
  src: https://github.com/layereight/ansible-wifi
  version: "1.0"
```
* also see the [Ansible Galaxy documentation](http://docs.ansible.com/ansible/galaxy.html)


## Role Variables

### mandatory

* **wifi_ssid:** Your Wifi's SSID.

* **wifi_psk:** Your Wifi's password.

### optional

* **wifi_country**
  * default: "DE"
  * description: 

## Example Playbook

Typical playbook run:
```sh
$ ansible-playbook -i inventory wifi.yml
```

*inventory*
```INI
[wifihosts]
myhost ansible_host=192.168.0.101 ansible_user=myuser ansible_ssh_pass=password 
```

*wifi.yml*
```YAML
- hosts: wifihosts
  
  roles:
    - layereight.wifi
  
  vars:
    wifi_ssid: "my_wifi_name"
    wifi_psk": "my_wifi_password"
```
