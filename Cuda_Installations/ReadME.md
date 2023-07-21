## Installation for the correct drivers and compatiable CUDA

Please follow the link for having a greater view on the compatiable versions for a chart view

### For download toolkit manual

https://developer.nvidia.com/cuda-toolkit-archive

### Guide

https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#runfile-uninstallation%5B/url%5D

### For version check

https://docs.nvidia.com/deeplearning/cudnn/support-matrix/index.html#:~:text=For%20best%20performance%2C%20the%20recommended,was%20used%20for%20tuning%20heuristics.

### CuDnn

https://developer.nvidia.com/rdp/cudnn-archive

Please follow these steps for installing the correct versions of CUDA, NVIDIA and CUDNN.

1) Remove all the Nvidia via purge

		sudo apt-get --purge remove "*cublas*" "cuda*" "nsight*" 
		
		sudo apt-get --purge remove "*nvidia*"

2) Search via Nvidia drivers (additions drivers selection) or install via commandline using

		sudo apt install nvidia-driver-<version_name>

3) Install CUDA 
	
		sudo apt install cuda-11-7 

4) Use these commands to add path for the cuda the main directory

		echo 'export PATH=/usr/local/cuda-11.7/bin:$PATH' >> ~/.bashrc
		echo 'export LD_LIBRARY_PATH=/usr/local/cuda-11.7/lib64:$LD_LIBRARY_PATH' >> ~/.bashrc
		source ~/.bashrc
		sudo ldconfig

5) Download CUDNN manually with the mataching compataible versions

	https://developer.nvidia.com/rdp/cudnn-archive 

6) Use the following commands for extracting and installing the Cudnn perfectly 

		CUDNN_TAR_FILE="cudnn-linux-x86_64-8.5.0.96_cuda11-archive.tar.xz"(Check the downloaded version)
		tar -xvf ${CUDNN_TAR_FILE}
		
7) copy the following files into the cuda toolkit directory

Make sure to check the versions matching to ur downloaded and compaitable versions 

		sudo cp -P cudnn-linux-x86_64-8.5.0.96_cuda11-archive/include/cudnn.h /usr/local/cuda-11.7/include
		sudo cp -P cudnn-linux-x86_64-8.5.0.96_cuda11-archive/lib/libcudnn* /usr/local/cuda-11.7/lib64/
		sudo chmod a+r /usr/local/cuda-11.7/lib64/libcudnn*
	
8) Reboot 

		sudo reboot

9) Finally, to verify the installation, check
	
		nvidia-smi
		nvcc -V

10) install Pytorch (an open source machine learning framework)

		pip install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu117
	
