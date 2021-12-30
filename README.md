# Pre-requisites
Basic Knowledge about AWS , SSH CLIENT ( MobaXterm ) , Unix Command
# ansible-server-deployment
Deployment of a distributed web application on cloud using fully automated Ansible playbooks

# Cloud Service Provider
I have used AWS Cloud service for the creation of the Virtual Machine .
Follow the steps below :

1 . First made three instances [ ami-0851b76e8b1bce90b (64-bit x86) ] Ubuntu Server 20.04 LTS .

2 . Rename the instances to avoid confusion 

3 . Create a elastic ip and associate to the control master node . (You can also assign elastic ip’s to target nodes (optional))

4 . Done .



# SSH CLIENT (MobaXterm)

Download  mobaXterm Home edition.
Https://mobaxterm.mobatek.net/download-home-edition.html

Install and then create a secret key : tools -> MobaKeyGen ( ssh key generator)

File -> load private key [load the .pem file here which was created while creating aws instances ]
Click on Generate .

While Creating new SSH session do not forgot to add the .pem file from the advanced ssh options .

# Procedure for the master node

Sudo apt update 

Sudo apt upgrade –y 

sudo passwd root     (set the root password for all the instances)

Update the /etc/ssh/sshd.config file . Add PermitRootLogin yes and PasswordAuthentication yes (set the root password for all the instances)

Restart sshd Service (set the root password for all the instances)




ssh keygen ( master node only)

ssh-copy-id  <private_ip> (run this command for all the instances with their private ip)


Now ssh <private_ip>  (for all instances)

Systemctl Restart  sshd ( for all instances )

Now , all the three servers are ready 


# How to run the playbook.yml

ansible-playbook playbook.yml  -i  inventory.txt

 




