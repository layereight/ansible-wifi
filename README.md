
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
  
* **wifi_control_interface_access_group**
  * default: root
  * description: potentially used to allow non-root users to use the control interface 
    [see wpa_supplicant for more information](https://w1.fi/cgit/hostap/tree/wpa_supplicant/wpa_supplicant.conf#n44)

* **wifi_apt_cache_valid_time**
  * default: 86400
  * description: number of seconds APT cache is valid for

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
    wifi_psk: "my_wifi_password"
```
