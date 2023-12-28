# terraform_ansible_kubernetes
A solution to deploy kubernetes on aws based on terraform and ansible
### Some step need to improve keep manual for now
Get Ip of servers from state file
head terraform.tfstate -n30
input private Ip to the adverstise address from master
kubernetes_apiserver_advertise_address: "mater_private_ip"
