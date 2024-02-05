# OVH DynHost Ansible playbook
Playbook which automatise installation of cron job,
which refresh OVH dynamic DNS service known as DynHost

## Prerequisites
- domain bought on OVH
- configured DynHost entry in OVH DNS zone
- configured DynHost login and password access

## Example

Content of inventory.yml file
```yml
all:
  hosts:
    raspberrypi-gate.local
  vars:
    dynhost_user: dynhostd
    dynhost_host: home.yourdomain.com
    dynhost_login: yourdomain.com-home
    dynhost_password: yourhomenewtorkpassword!123
    dynhost_log_dir: /var/log
    dynhost_cron_period_minutes: 10
```

Run Ansible
```sh
ansible-playbook dynhost.yml -u username -i inventory.yml
```

Check effects
```sh
cat /home/dynhostd/cronjob/update.dynhost.home.yourdomain.com.sh
cat /var/log/dynhostd.home.yourdomain.com.log
```

## Possible improvements of this script
- handling multiple subdomains gently

## Credits 
Credits for the [yjajkiew](https://github.com/yjajkiew), creator of 
[shell script used in this playbook](https://github.com/yjajkiew/dynhost-ovh)