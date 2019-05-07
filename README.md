# caffe-ssd-setup
## How to run:
### 安装依赖库
sudo apt-get update  
sudo apt-get upgrade  
sudo apt-get dist-upgrade  
echo "系统更新完成"  
sudo apt-get install -y build-essential   
sudo apt-get install -y doxygen cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev  
sudo apt-get install -y python-dev python-numpy python-pip libtbb-dev libjpeg-dev libpng12-dev libtiff5-dev libjasper-dev libdc1394-22-dev  
sudo apt-get install -y libatlas-base-dev gfortran  
sudo apt-get install -y cmake-qt-gui  
sudo apt-get install -y libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libboost-all-dev  
sudo apt-get install -y libhdf5-serial-dev libgflags-dev libgoogle-glog-dev liblmdb-dev protobuf-compiler   
sudo apt-get install -y libopenblas-dev  
echo"依赖库安装完成"  
## 安装CUDA
sudo dpkg -i cuda-repo-ubuntu1604_9.1.85-1_amd64.deb  
sudo apt-key adv --fetch-keys http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/7fa2af80.pub  
sudo apt-get update  
sudo apt-get install -y cuda  
echo"cuda 安装完成"  
## 安装 Anaconda
sh Anaconda2-5.0.1-Linux-x86_64.sh   
## 安装CUDNN
sudo cp cuda/include/cudnn.h /usr/local/cuda/include  
sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64  
sudo chmod a+r /usr/local/cuda/include/cudnn.h  /usr/local/cuda/lib64/libcudnn*  
sudo rm -rf /usr/local/cuda-9.1/targets/x86_64-linux/lib/libcudnn.so.7.1.1  
sudo ldconfig  
如果遇到  /usr/local/cuda-9.1/targets/x86_64-linux/lib/libcudnn.so.7 不是符号连接:  
        #进入该目录，删除so.7.1.1  

## 修改环境变量
sudo gedit /etc/profile  
#export PATH=/usr/local/cuda-9.1/bin:$PATH  
#export LD_LIBRARY_PATH=/usr/local/cuda-9.1/lib64:$LD_LIBRARY_PATH  

## 编译caffe
编译caffe遇到找不到libhdf5_hl.so.100和libhdf5.so.101问题解决办法  
sudo cp /home/sdu/anaconda2/lib/libhdf5_hl.so.100 /lib/x86_64-linux-gnu/  
sudo cp /home/sdu/anaconda2/lib/libhdf5_hl.so.100 /usr/lib/include  
sudo cp /home/sdu/anaconda2/lib/libhdf5.so.101 /lib/x86_64-linux-gnu/  
sudo cp /home/sdu/anaconda2/lib/libhdf5.so.101 /usr/lib/include  



## 编译 py-caffe
cd caffe-ssd/python  
for req in $(cat requirements.txt); do pip install $req; done  
