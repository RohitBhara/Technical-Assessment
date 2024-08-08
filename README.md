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

  3) Install Docker and Nvidia Container Toolkit through creating ansible playbook 

   $ docker_install.yaml 
   
   $ localhost ansible_connection=local    # In my situation add this line on local machine to run ansible playbook locally  /etc/ansible/hosts
   $ ansible-playbook docker_install.yaml     # Play ansible
   
4) Install Kubernetes packages & Helm 

      kubernetes_setup.yaml
  
       $  kubectl get nodes    # verify nodes and cluster
       $  kubectl get pods -a  # see pods 

  
  5)  Install GPU Plugin for Kubernetes
   
  $ kubectl apply -f https://raw.githubusercontent.com/NVIDIA/k8s-device-plugin/v1.14.0/nvidia-device-plugin.yml
  
  6) Install GPU Operator through helm 

    $ helm repo add nvidia https://nvidia.github.io/gpu-operator/            # add
    $ kubectl create namespace gpu-operator                                  # create namespaces 
    $ helm install gpu-operator nvidia/gpu-operator --namespace gpu-operator # Install 


 7) Install Docker images 

 8)  Deployment application using GPU 

      $  deployment.yaml                  # yaml file for deployment example
      $ kubectl apply -f deployment.yaml  # deploy this pod 

9) Scaling 
       Autoscaling to automatically scale the number of pods based on CPU or GPU utilization.

       $ scaling.yaml                   # yaml file for scaling
       $ kubectl apply -f scaling.yaml  #  deploy this file

** My Outline for Deploying and Managing GPU Workloads:

* Create GPU MIG profiles to allocate specific profiles, enhancing reliability and resource management.
* Implement automated monitoring and alerting using DCGM and DCGM exporter tools, integrated with Prometheus and Grafana.
* Ensure security and compliance by implementing data encryption and role-based access control (RBAC).
* Configure high-availability settings for critical services to improve scalability and ensure high availability.
* Conduct benchmarking tests to assess the impact of different configurations.
* Integrate automation and CI/CD pipelines to streamline and enhance deployment processes. 

** Summary 
provide a comprehensive approach to deploying and managing GPU workloads in Kubernetes. By focusing on resource management, scalability, performance optimization, automation, and security, you can ensure that your GPU workloads are efficiently managed and well-optimized for both current and future needs.
      



