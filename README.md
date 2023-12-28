# terraform_ansible_kubernetes
A solution to deploy kubernetes on aws based on terraform and ansible
### Some step need to improve keep manual for now
##Get Ip of servers from state file

head terraform.tfstate -n30

input private Ip to the adverstise address from master

kubernetes_apiserver_advertise_address: "mater_private_ip"

##Troubleshoot the kubeadm init, reset it first
 kubeadm reset --cri-socket=unix:///var/run/cri-dockerd.sock
 cat /etc/kubernetes/kubeadm-kubelet-config.yaml

##You still have to deloy flannel manully
kubectl apply -f https://raw.githubusercontent.com/flannel-io/flannel/master/Documentation/kube-flannel.yml

###Run:
terraform apply
 ansible-playbook -i inventory --become main.yml --limit=master,node1

