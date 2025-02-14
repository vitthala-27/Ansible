- name: mybook      #defines a name of a playbook
  hosts: localhost  #it will define that the playbook runs on which host (local or other)
  become: true      #it gives the super user (root) permission's to the playbook
  connection: local #it tells that the playbook will run locally instead of connecting any remote server
  tasks:        #it contains the list of action that ansible will perform
   - name: install lemp      #here we can give a specific name or the task that we want to perform
     apt:                    #package manager of ubuntu, needs for installation
       name: "{{ item }}"    #it is a placeholder for multiple values
       state: present        # it means ansible has to install,if installed do nothing
     with_items:             # it will install all the below dependencies
      - nginx
      - php8.3-fpm
      - mariadb-server
