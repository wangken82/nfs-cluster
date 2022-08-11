# Requires the latest Terraform and Ansible
Azure Cloudshell has both Terraform and Ansible preinstalled, so cloning and launching from Cloudshell is convienent.
if any issue found for this script, please email kenneth.wang@microsoft.com
# Clone the repository and run this command from root of project folder:
$ ansible-playbook -i hosts lab.yml

After deployment done
1. find the bastion VM ip
terraform output bastion_ip

2. log into bastion VM from cloudshell
ssh -i ~/.ssh/lab_rsa azureadmin@<bastion vm ip>

3. ssh into nfs cluster from bastion vm
ssh nfs-0  or ssh nfs-1

4. verify cluster status
sudo -s
crm status

Resource created
1. By default Resource group suse_cluster_resource created west US with 10.30.0.0/16 vnet
2. 1 Loadbalancer, 2 NFS VMs in availability set behind the LB, only private IP
3. 1 bastion VM has public IP
