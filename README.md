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


#Reference maybe useful
https://github.com/weibeld/terraform-aws-kubeadm/blob/master/main.tf
https://kubernetes.io/docs/reference/setup-tools/kubeadm/kubeadm-init/
https://platform9.com/docs/openstack/authentication-ssh-key-value-generation
https://docs.ansible.com/ansible/latest/cli/ansible-playbook.html
https://stackoverflow.com/questions/17188147/how-to-run-ansible-without-specifying-the-inventory-but-the-host-directly
https://github.com/kubernetes/kubeadm/issues/1575
https://kubernetes.io/blog/2023/08/15/pkgs-k8s-io-introduction/
https://github.com/docker/for-linux/issues/1349


