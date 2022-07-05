# Installing the NVIDIA driver, CUDA and cuDNN on Linux (Ubuntu 20.04)

This is a companion piece to my instructions on installing CUDA and cuDNN on Linux

- [CUDA](https://developer.nvidia.com/cuda-11-6-0-download-archive?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=20.04&target_type=runfile_local) (v11.6.0)
- [cuDNN](https://developer.nvidia.com/cudnn) (v8.4.1.50)

on an Ubuntu Linux system, in particular Ubuntu 20.04.


### Installing CUDA
Download the latest CUDA version [here](https://developer.nvidia.com/cuda-11-6-0-download-archive?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=20.04&target_type=runfile_local). For example, I downloaded:

    $ wget https://developer.download.nvidia.com/compute/cuda/11.6.0/local_installers/cuda_11.6.0_510.39.01_linux.run


    $ sudo sh cuda_11.6.0_510.39.01_linux.run

You may need to confirm that the display driver is already installed, and de-select installation of the display driver.

Once finished, you should see a summary like this:

	===========
	= Summary =
	===========

	Driver:   Not Selected
	Toolkit:  Installed in /usr/local/cuda-11.0/
	Samples:  Installed in /home/systemtrio/, but missing recommended libraries



Do what the instructions given in the summary say and add the given directories to your `PATH` and `LD_LIBRARY_PATH`. For example by adding the following lines to your `.bashrc`:

    export PATH=/usr/local/cuda/bin:$PATH
    export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH


### Installing cuDNN

Just go [here](https://developer.nvidia.com/cudnn) and follow the [instructions](https://docs.nvidia.com/deeplearning/sdk/cudnn-install/index.html). You'll have to log in, so downloading of the right cuDNN binary packages cannot be easily automated. Meh.

Once downloaded, un-tar the file and copy the contents to their respective locations:

    $ tar -xzvf cudnn-linux-x86_64-8.4.1.50_cuda11.6-archive.tar.xz
    $ cd Downloads/cudnn-linux-x86_64-8.4.1.50_cuda11.6-archive
    
    $ sudo cp include/cudnn*.h /usr/local/cuda/include
    $ sudo cp lib/libcudnn* /usr/local/cuda/lib64
    $ sudo chmod a+r /usr/local/cuda/include/cudnn*.h /usr/local/cuda/lib64/libcudnn*
