# Installing-_CUDA_toolkit_guide_LINUX
This is the repo for installing cuda toolkit in linux.

Installing CUDA toolkit is a little bit complicated thats why we should be a little bit conscious while installing it.

The following guide followed this link: https://docs.nvidia.com/cuda/cuda-quick-start-guide/index.html#ubuntu-x86_64

It is suggested to follow debian installer instead of runtime installer.

Commands followed:

1. ```
    sudo dpkg --install cuda-repo-<distro>-<version>.<architecture>.deb
	```
	
	```
	sudo apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/<distro>/<architecture>/7fa2af80.pub
	```
	
	```
	sudo apt-get update
	```
	
	```
	sudo apt-get install cuda
	```
	
Above commands is just an example actually you have to first download .deb file then run the following commands. For e.g. you have to choose between a lot of options.
(*Source*: https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1604&target_type=deblocal )

1. *OS*: Linux
2. *Architecture*: x86_64
3. *Distribution*: Ubuntu
4. *Version*: 16.04
5. *Installer type*: deb(local)

After deciding the target platform download the deb file (~1.2 GB). After that run the following commands.

1. ```
	sudo dpkg -i cuda-repo-ubuntu1604-9-2-local_9.2.88-1_amd64.deb
	```
	
	```
	sudo apt-key add /var/cuda-repo-<version>/7fa2af80.pub
	```
	
	```
	sudo apt-get update
	```
	
	```
	sudo apt-get install cuda
	```

At the time of installation CUDA had latest version of 9.2 that will change depending on the latest version.

## Post Installation Actions

### Mandatory Actions

1. You have to set up the development environment by modifying the PATH and LD_LIBRARY_PATH variables. Add these commands to .bashrc file.
	The .bashrc file is a script that is executed whenever a new terminal session is started in interactive mode. This is what happens when you open a new terminal window.
	You will need these environment settings on a new terminal every time I use CUDA, its libraries and other tool kits.

	Go to the home directory.

	```
	cd ~
	```
	
	Open the .bashrc file:
	
	```
	sudo gedit .bashrc
	```

	Add following two commands in .bashrc file.
	
	```
	export PATH=/usr/local/cuda-9.2/bin${PATH:+:${PATH}}
	```
	
	```
	export LD_LIBRARY_PATH=/usr/local/cuda-9.2/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
	```
	
	Save and close the .bashrc file . The new .bashrc would be installed the next time you log out and log back in, but if you are impatient like me and just want it installed now, you can just source the file.
	```
	source .bashrc
	```
### Recommended Actions

Other actions are recommended to verify the integrity of the installation.

1.  In order to modify, compile, and run the samples, the samples must be installed with
	write permissions. A convenience installation script is provided:
	
	```
	cuda-install-samples-9.2.sh ~
	```
	
	```
	cd ~/NVIDIA_CUDA-9.2_Samples/5_Simulations/nbody
	```
	
	```
	make
	```
	
	```
	./nbody
	```

2.  Verify the Installation
	
	*Verify the Driver Version*: If you installed the driver, verify that the correct version of it is loaded. When the driver is loaded, the driver version can be found by executing the command
	
	```
	cat /proc/driver/nvidia/version
	```
