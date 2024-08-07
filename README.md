# Technical-Assessment

1) Install Ansible setup and dependencies 
   $ sudo apt update 
   $ sudo apt install software-properties-common
   $ sudo add-apt-repository --yes --update ppa:ansible/ansible
   $ sudo apt install -y ansible
   $ sudo apt update
   $ ansible --version          # Check ansible version
       
root@master-server:~# ansible --version
ansible 2.9.6
  config file = /etc/ansible/ansible.cfg      # inside this you have to enable your inventory file 
  configured module search path = ['/root/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python3/dist-packages/ansible
  executable location = /usr/bin/ansible
  python version = 3.8.10 (default, Jul 29 2024, 17:02:10) [GCC 9.4.0]

 2) Install GPU packages ( ex. Nvidia GPU )  
 
  $ ubuntu-drivers devices       # Install GPU drivers on ubuntu 
  $ sudo apt-get install <recommended drivers> 
  $ nvidia-smi        # See GPUs 

  3) Install Docker and Nvidia Docker through creating ansible playbook 

   $ docker_install.yaml 
   
   $ localhost ansible_connection=local    # In my situation add this line on local machine to run ansible playbook locally  /etc/ansible/hosts
   $ ansible-playbook docker_install.yaml     # Play ansible playbook


