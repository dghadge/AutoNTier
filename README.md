### AutoNTier : Automated N-Tier infrastructure creation using Ansible, Vagrant & VirtualBox

###  Technical Components
     Vagrant     : environment creation & control
     Virtual Box : hypervisor
     Ansible     : change mgmt, provisioning, automation & orchestration

###  How to create VM(s) and install Ansible
     From command prompt run the following commands
     1. git clone https://github.com/dghadge/AutoNTier.git
     2. Create a new "Vagrantfile" or make changes to existing one depending on tour needs
     3. Run : vagrant up     #this will start VM(s) in Vagrant file
     4. Run : vboxmanage list runningvms   #to list running VM(s)
     5. Run : vagrant ssh <vm>  #vm=acs,web,db in our case
     6. Run : sudo apt-get install ansible  #On Debian systems
     7. Run : sudo yum install epel-release; sudo yum install ansible #On CentOS systems

###  Virtualbox VM(s) created using Vagrant
     acs : 192.168.33.10  ##Ansible Control Server
     web : 192.168.33.20  ##web server
     db  : 192.168.33.30  ##database host

###  How to use setup Ansible on the VM(s) created in previous steps
     From command prompt run the following commands
     1. ssh vagrant acs  #to login to Ansible control server
     2. ssh vagrant@ip-address-of-web-server #this will add this host fingerprint to list of know hosts
     3. sudo apt-get install sshpass
     4. ansible 192.168.33.20 -i inventory -u vagrant -m ping -k      #ping remote system
     5. ansible all  -i inventory -u vagrant -m ping -k               #ping all remote systems
     6. ansible 192.168.33.20 -i inventory -u vagrant -m ping -k -vvv #verbose mode
     7. ansible 192.168.33.20 -i inventory -u vagrant -m command -a "/usr/sbin/yum/update -y"  #use command module to update 

###  How to use Ansible to manage changes, provision, automate and orchestrate systems
     From command prompt run the following commands
     1. create inventory file "inventory-prod" consisting of hosts, groups and group variables of your system
     2. Run : ansible web1 -i inventory-prod -m ping           #ping individual server
     3. Run : ansible webservers -i inventory-prod -m ping     #ping group of servers
     4. Run : ansible datacenter -i inventory-prod -m ping     #ping entire datacenter
     5. Create directory structure and following files within those directories 
          ├── ansible.cfg
          ├── group_vars           #directory to hold group level variables
          │   ├── all
          │   ├── db
          │   └── webservers
          ├── host_vars            #directory to hold host level files
          │   └── web1
          └── inventory_prod
     6.  Create a varibale to entire group in groups_vars/all. To create username in all webservers run :
         ansible webservers -i inventory_prod -m user -a "name={{username}} password=12345" --sudo  
     7.  Create a varibale for specific host in host_vars/web1. To create username in that specific host run :
         ansible webservers -i inventory_prod -m user -a "name={{username}} password=12345" --sudo  

