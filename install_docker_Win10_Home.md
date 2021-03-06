##  Install Docker:
1. Install Virtual Box from https://www.virtualbox.org/wiki/Downloads as Windows-10 Home edition doesn't have Hyper-v
2. Install Docker toolbox for windows. you can follow documentation provided at https://docs.docker.com/toolbox/toolbox_install_windows/

## Install docker image
1. Run docker from docker quickstart. 
2. Download docker image from docker-hub repositories or get your own.
3. load docker image using "docker load < image_name"
4. Create docker container using command "docker run -it -d --name "contaner_name" "image_name"
If you want to mount your own windows folder then you should frist stop docker-machine by "docker-machine stop" command, then go to
virtualbox -> shared folder and share your project folder by browsing the output folder path. The folder name should displayed under system
folder category.
Now run same command like this:
"docker run --it -d "container_name" --mount type=bind,source="/folder_name as assigned in Virtualbox",targe="path_to_folder" "image_name"

5. To excute or enter to container use "docker exec -it container_name" if already running. Otherwise you have to start your docker first 
and then execute. 

## Increasing VM Memory

By default Windows Docker dedicated 2Gb RAM, which is quite low. I’m using Elasticsearch in a few projects and it alone takes more than 1Gb of RAM.
And solutions is quite straightforward. It requires 2 steps. First: remove existing Docker virtual machine:
$ docker-machine rm default
Second: re-create virtual machine with amount of RAM, CPU cores or disk space you want:
$ docker-machine create -d virtualbox --virtualbox-cpu-count=2 --virtualbox-memory=4096 --virtualbox-disk-size=50000 default
Restart Docker and the issue if solved.

## Increase disk size
VBoxManage clonemedium "source.vmdk" "cloned.vdi" --format vdi
VBoxManage modifymedium "cloned.vdi" --resize 51200
VBoxManage clonemedium "cloned.vdi" "resized.vmdk" --format vmdk
