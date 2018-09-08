# Ansible Playbook for my Thesis App
## Stress Analysis for Social Media Data

## Code Explanation


### 1.	Download and install Microsoft Visual Studio 2015 Community Edition. It is free and you can download it from
https://imagine.microsoft.com/en-us/Catalog/Product/101

Hosts:  thesis_ servers
Tasks:
- name: Install Microsoft Visual Studio 2015 Community Edition
 package:
path: https://imagine.microsoft.com/en-us/Catalog/Product/101
state: present

### 2.	You’ll also need to register for Twitter API. To do that follow the following link: https://dev.twitter.com/rest/public
You’ll need to create an account, you’ll be provided with 4 keys which are the following

### a.	Consumer Key

### b.	Consumer Secret

### c.	Access Token

### d.	Access Token Secret


 - name: Open Twitter API link
 
Twitterapi:

- uri:

    url: https://dev.twitter.com/rest/public
    
    return_content: yes
    register: webpage

name: Create Twitter API account
  uri:
    url: https://dev.twitter.com/rest/public
    
    method: POST
    
Access token: ****

Access token secret: ***

Consumer secret : ****

Consumer key: ****

### 3.Copy the folder named BackEnd, and folder named Twitter.csproj. Make sure it runs in your Microsoft Visual Studio 2015.


-name copy and execute files

- copy:
        src: /users/thesis/Backend
        
        dest: /users/thesis/Backend
        
Executable: /users/thesis/visualstudio2015

-copy:
        src: /users/thesis/ Twitter.csproj
        
        dest: /users/thesis/ Twitter.csproj
        
Executable: /users/thesis/visualstudio2015



### 4.	Open the file named user.service.js inside the user folder


-name: Open the file named user.service.js inside the user folder

-synchronize:

src: /first/absolute/user.service.js

delegate_to: /user/joefolder


### 5.	Install Configure and Restart SQL Server Management Studio 2012

       Install mysql
    hosts: thesis servers
        tasks:
          - name: Install SQL Server Management Studio 2012
            apt:  
    name= SQL Server Management Studio 2012
     state=present


	
	
	- name: Configure MySQL
	  hosts: mysql-service
	  tasks:
	    - name: Configure my.cnf
	      copy: src=./files/my.cnf
	            dest=/etc/mysql/my.cnf
	            owner=root
	            group=root
	            mode=0640
	      notify:
	        - restart mysql
	    
	    - name: Add mysql-user
	      mysql_user: name=mysql_service
	                  password=12345
	                  priv=*.*:ALL
	                  state=present
	      notify:
	        - start mysql

	
	  handlers:
	    - name: start mysql
	      service: name=mysql
	               enabled=yes
	               state=started
	    - name: restart mysql
	      service: name=mysql
	               enabled=yes
	               state=restarted

run another query to create an admin record.
run query from a file where path is relative to playbook dir

          - name: admin query
            db:mysql
            query: "{{playbook_dir}}/scripts/mysql/admininsert.sql"

### 6 run another query from a file where path is relative to playbook dir to create an admin record.

          - name: admin query
            db:mysql
            query: "{{playbook_dir}}/scripts/mysql/admininsert.sql"







