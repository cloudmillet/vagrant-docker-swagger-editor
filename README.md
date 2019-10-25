## IaaC project : swagger editor 
 A Vagrantfile to build a docker host and deploy swagger editor on docker. We can access swagger editor from browser 
 
1. Docker Host  (centos/7)
    The docker node configured with docker software and ready to host containers. 
    

### Steps :  
  Step 1 :  Install virtual box (https://www.virtualbox.org)

  Step 2 :  Install vagrant  (https://www.vagrantup.com)

  Step 3 :  Download and  Vagrant file  
       git clone https://github.com/malyabee/vagrant-docker-swagger-editor.git 

  Step 4  : starting virtual machines 

       $ cd vagrant-docker-swagger-editor
 
       $ vagrant up
       # "vagrant up" might take a while for first time

###  accessing swagger-editor 
You can access swagger-editor using browse http://localhost:8080 

### commands to login docker virtual machines
    

     vagrant ssh 
     
     


### Host compatability :

    This Vagrant verified on Mac OS.


