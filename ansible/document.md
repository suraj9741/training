https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html
```
[mysql-master]
db01.pru-test.ins.perfios.com  ansible_host=172.17.48.143   ansible_ssh_port=1729   ansible_user=surajv  ansible_ssh_private_key_file=/home/suraj/.ssh/id_rsa

[mysql-slave]
db02.pru-test.ins.perfios.com  ansible_host=172.17.48.154   ansible_ssh_port=1729   ansible_user=surajv  ansible_ssh_private_key_file=/home/suraj/.ssh/id_rsa

[appservers_qa]
localhost                            ansible_connection=local                              hostname=frogmouth            img_tag=qa     env_type=dev
#waxbill                               ansible_host=192.168.221.30   ansible_ssh_port=22     hostname=frogmouth            img_tag=prod   env_type=production  ansible_user=surajv  ansible_ssh_private_key_file=/home/suraj/.ssh/id_rsa

[appservers_uat]
#buzzard.hinagro.com                  ansible_host=172.17.3.68     ansible_ssh_port=1729    hostname=buzzard              img_tag=prod   env_type=uat

[appservers_prod]
#docparser.pru.ins.perfios.com        ansible_host=172.17.40.170   ansible_ssh_port=1729    hostname=docparser.pru.ins    img_tag=prod   env_type=production

[appservers_prod_test]
#docparser.pru-test.ins.perfios.com   ansible_host=172.17.48.165   ansible_ssh_port=1729    hostname=test                 img_tag=prod   env_type=production  # test

```


how to ping 
```
sudo ansible -m ping all -i hosts
```
how to run playbook
```
/usr/bin/ansible-playbook asb.yml
ansible-playbook -i hosts asb.yml
ansible-playbook asb.yml
```

