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
     1. ssh vagrant acs  #to login to Ansible control server

