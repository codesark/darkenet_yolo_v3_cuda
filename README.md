
# Instruction for Installing and running YOLO on Pop OS! 19.04
  
  Clone the repository `git clone https://github.com/iamsavinay/darkenet_yolo_v3_cuda ~/darknet`

  Download the weight file i.e., yolov3.weights from [here(273MB)](https://pjreddie.com/media/files/yolov3.weights)
  and copy it to main darknet directory
  OR run
    
    wget https://pjreddie.com/media/files/yolov3.weights ~/darknet/

  Run the following commands to setup the environments

    sudo apt update && sudo apt upgrade
    sudu apt install system76-cuda-latest
    sudo apt installl build-essential gcc gcc-7
    sudo apt install libopencv-dev
    sudo ln -s /usr/lib/cuda /usr/local/cuda
    sudo ln -s /usr/bin/gcc-7 /user/local/cuda/bin/gcc

  Copy following lines to `~/.bashrc` files at the end

    export CUDA_HOME=/usr/lib/cuda
    export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/cuda/lib64:/usr/lib/cuda/extra>
    export PATH=$PATH:$CUDA_HOME/bin

  Now it's time to compile the darknet open a new terminal and proceed

    cd ~/darknet
    make
  
  Run from webcam (requires compile with CUDA and OpenCV)
	
	  ./darknet detector demo cfg/coco.data cfg/yolov3.cfg yolov3.weights

  -- (Optional) If above command fails with `Error: Out of Memory`
	
   modify the file `cfg/yolov3.cfg` to

	  batch=1
	  subdivisions=1
	  width=416
	  height=416


# Darknet #

![Darknet Logo](http://pjreddie.com/media/files/darknet-black-small.png)

Darknet is an open source neural network framework written in C and CUDA. It is fast, easy to install, and supports CPU and GPU computation.

This is originally made by pjreddie. For more information see the [Darknet project website](http://pjreddie.com/darknet).
