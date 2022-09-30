In this excercis we will be launcing 3 VM's. 1st VM will be Ansible, 2nd and 3rd will be Vm's to be configured.
Requirement is to make make VM2, VM3 into web server by installing httpd server and enabling httpd service.

Step#1 Install Ansible 
yum install ansible

Step#2
inventory file:
[servers]
107.20.100.19 ansible_user=ec2-user
23.22.135.70 ansible_user=ec2-user

playbook.yaml
---
- name: install apache across our redhat machines
  hosts: servers
  become: yes
  tasks:
    - name: Install Apache nginx postgresql  httpd software
      ansible.builtin.yum:
        name: httpd
        state: present
    - name: Start and enable Apache
      service:
        name: httpd
        state: started
        enabled: yes

Step#3
configure key
Step3.1: 
get into server1
passwd <username>

Step 3.2:
vi /etc/ssh/sshd_config ---> search for --> #PasswordAuthentication yes --> change to --> PasswordAuthentication yes

Step 3.3:
service sshd restart

Step 4:
ssh-keygen (ansible server)
ssh-copy-id ec2-user@x.x.x.x

Step 4:
ansible-playbook -i inventory playbook.yml
