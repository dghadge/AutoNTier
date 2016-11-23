### AutoNTier : Automated N-Tier infrastructure creation using Ansible, Vagrant & VirtualBox

###  Technical Components
     Vagrant     : environment creation & control
     Virtual Box : hypervisor
     Ansible     : change mgmt, provisioning, automation & orchestration

###  How to start the application
     From command prompt run the following commands
     1. git clone https://github.com/dghadge/AutoNTier.git
     2. Create a new "Vagrantfile" or make changes to existing one depending on tour needs
     3. Run : vagrant up     #this will start VM(s) in Vagrant file
     4. Run : vboxmanage list runningvms   #to list running VM(s)
     5. Run : vagrant ssh <vm>  #vm=acs,web,db in our case
     6. Run : sudo apt-get install ansible  #this will install ansible (Run : 
     

