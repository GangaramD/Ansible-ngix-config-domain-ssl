# Ansible-ngix-config-domain-ssl Centos 7
Ansible scripts to create the ssl certs on perticular IP or Host and configure the nginx with the configuation on centos server. 

# Domain SSL certs creation using letsencrypt
Use the Parameterized Jenkins Job.
 Params:
   1. DNS_name = platform.abc.com   #domain for which ssl needs to be configured 
   2. Email = abc@gmail.com  #email used to receive notification
   3. Host_ip = 232.12.233.43  #server Ip for which the certs to be created.
   4. Host_pwd = password   #server password to authenticate 
   
 Execute the Shell File That capture the IP into the inventory file to run ansible playbook.
  
 Jenkins Build Section: 
   Execute shell
   
           chmod +x ip_capture.sh
           sh ./ip_capture.sh $Host_ip $Host_pwd
           
   Execute shell
   
          export ANSIBLE_HOST_KEY_CHECKING=False
          ansible-playbook -i inventory ssl_certs.yaml --extra-vars "dns_name=$DNS_name cert_email=$Email"
          
 # Installing nginx and Deploying the nginx configuration for DNS
 
 
