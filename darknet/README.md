## darknet installation July, 10, 2022
1. precondition  
  JetPack 4.6.1  
  Burn it to SD card.  
  [https://developer.nvidia.com/embedded/jetpack](https://developer.nvidia.com/embedded/jetpack)

2. follow pre setting.  
- [pre-procedure about default runtime "nvidia"](./default-rumtime-nvidia.md)

3. pull docker origin  
You need to select a pull tag to suit your JetPack version.  
[https://catalog.ngc.nvidia.com/orgs/nvidia/containers/l4t-base](https://catalog.ngc.nvidia.com/orgs/nvidia/containers/l4t-base)  
r32.6.1 is for JetPack 4.6.1.  
``` bash
docker pull nvcr.io/nvidia/l4t-base:r32.6.1
``` 

4. download this dockerfile and execute docker build  
```bash
git clone https://github.com/daizyu/jetson_xavier_nx_dockers.git

cd jetson_xavier_nx_dockers/darknet

sudo docker build -t darknet:1.0.0 ./
```

5. docker run  
``` bash
sudo docker run -it --network host --runtime nvidia darknet:1.0.0
```
To be honest , you don't need to add ***--runtime nvidia*** , because you already set default runtime to nvidia.    
Anyway, I recommend to put  ***--runtime nvidia*** in this step.

