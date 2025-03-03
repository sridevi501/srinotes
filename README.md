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
