1)***Declare variable Globally****

---
- name: Network Getting Started First Playbook
  hosts: all
  become: true
### variable declare here
  vars:
          filename: suraj.txt

  tasks:
          - name: update ubuntu
            apt:
                    name: "*"
                    state: latest
          - name: Run the equivalent of "apt-get update" as a separate step
            apt:
                    update_cache: yes
          - name: Touch or creat a file
            file:
                    path: /home/ubuntu/demo/{{ filename }}
                    state: touch
                    
                    
2)*** Declare a Variable In VAR File*** #create multiple files
---
- name: Network Getting Started First Playbook
  hosts: all
  become: true
### variable declare in file
  vars_files:
          - /home/ubuntu/var_file.yml
  tasks:
          - name: update ubuntu
            apt:
                    name: "*"
                    state: latest
          - name: Run the equivalent of "apt-get update" as a separate step
            apt:
                    update_cache: yes
          - name: Touch or creat a file
            file:
                    path: /home/ubuntu/demo/{{ filename }}
                    state: touch
         
***   OUTPUT=====ubuntu@uma:~/demo



$ ls
'['\''host.txt'\'', '\''runtime.txt'\'', '\''suraj.txt'\'', '\''test.conf'\'', '\''uma.txt'\'', '\''new.txt'\'']'   a.txt   suraj.txt
It will create files like this.....xxxx


***Right Way to Declare Or Create Multiple Files by using  ( With_items Module) ===

---
- name: Network Getting Started First Playbook
  hosts: all
  become: true
### variable declare in file
  vars_files:
          - /home/ubuntu/var_file.yml
  tasks:
          - name: update ubuntu
            apt:
                    name: "*"
                    state: latest
          - name: Run the equivalent of "apt-get update" as a separate step
            apt:
                    update_cache: yes
          - name: Touch or creat a file
            file:
                    path: /home/ubuntu/demo/{{item}}
                    state: touch
            with_items: "{{ filename }}"





