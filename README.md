# srinotes

Steps followed to copy the data from one EBS Volume to another EBS volume:

1/ create snapshot from the EBS volume and create volume from the snapshot [from volume].
2/ new volume should be created / available. Volume should be in Available state to use. `in use` state volumes cannot be mounted [to volume]
3/ attach volumes to the EC2 instance in the same availability zone as from volume and to volume
	aws ec2 attach-volume --volume-id <VolID> --instance-id <InstanceID> --device /dev/xvdab
	aws ec2 attach-volume --volume-id <VolID> --instance-id <InstanceID> --device /dev/xvdab
4/ Create mount points for old and new volume
	sudo mkdir /mnt/old-volume 
	sudo mkdir /mnt/new-volume
5/ Mount the new and old volume
	sudo mount /dev/xvdab /mnt/old-volume
	sudo mount /dev/xvdab /mnt/new-volume
6/ Copy the data from the old volume to new volume
	sudo rsync -avh /mnt/old-volume/ /mnt/new-volume/
		Or
	sudo cp -r /mnt/old-volume/* /mnt/new-volume/
7/ unmount after completion of copy
	sudo umount /mnt/old-volume 
	sudo umount /mnt/new-volume
8/ Use below commands to detach volumes
	aws ec2 detach-volume --volume-id <VolID> --instance-id <instanceID> --device /dev/xvdab
	aws ec2 detach-volume --volume-id <VolID> --instance-id <InstanceID> --device /dev/xvdbp


git clone https://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions

git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting

ZSH_THEME="powerlevel10k/powerlevel10k"
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)


Experienced in running 130+ Kubernetes (AWS EKS) clusters for telecom organization where scaling, resiliency, security, monitoring are prioritized 
Hands-on experience with Infrastructure as Code products on Terraform and AWS CDK
Experience in the design and implementation of scalable, secure, and resilient AWS solutions utilizing Serverless, EKS, storage, and networking best practices
Experienced in working in an SRE / DevOps team and part of its maturity journey
Proficiency with CI/CD on deployment, management, and monitoring of applications
Experienced working with using certificates for message signing and mutual TLS [Istio, AWS PCA]
Successfully configured and managed EKS add-ons, including External Secrets, EBS CSI Driver, EFS CSI Driver, CoreDNS, Local DNS Cache, Cert Manager, and both internal and external Ingress Controllers to enhance cluster functionality and security
Implemented a hybrid architecture utilizing Karpenter to optimize resource utilization, enhance high availability, and achieve significant cost reductions [ SPOT / On Demand], driving operational efficiency and scalability in cloud environments
Deployed Kyverno in the EKS cluster, establishing best practice policies to enforce security and compliance, thereby ensuring a robust and secure Kubernetes environment
Established end-to-end observability for both infrastructure and applications using the ELK stack with Fluent Bit, AMP, Grafana, SNS, CloudWatch, and Elasticsearch, providing holistic monitoring and actionable insights into system performance

