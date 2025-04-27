# DonkeyCar Installation using Docker Container

## This docker image works on Jetson Xavier NX/AGX, it comes built with OpenCV 4.10 and Tensorflow 2.14 with CUDA 11.4 built with Python 3.11

## First clone this git repository, change directory and make the run.sh script executable
```
git clone https://github.com/Triton-AI/donkeycontainer.git && 
cd donkeycontainer && 
sudo chmod +x run.sh
```
# To Pull a base image without donkey install do: 
### ```docker pull ghcr.io/ucsd-ecemae-148/donkeycontainer:base```

# To start the container run the start script
### ```./run.sh```

## Now lets install the dependencies for donkey
### Lets add some swap space
```
git clone https://github.com/JetsonHacksNano/installSwapfile
cd installSwapfile
./installSwapfile.sh -s 8
reboot 
```

### Lets install the donkeycar 
```
git clone https://github.com/autorope/donkeycar
cd donkeycar
git checkout main
pip install -e .[nano] && pip install --force-reinstall pillow
```

### Creating a Donkeycar from Template 

```
donkey createcar --path /home/projects/mycars/deep_learning_car
```
That creates a car using the default deep learning template. You can also create a car that uses the gps path follow template;
```
donkey createcar --template=path_follow --path /home/projects/mycars/gps_path_follow_car
```
You can also create a car that uses the computer vision template
```
donkey createcar --template=cv_control --path /home/projects/mycars/cv_car
```
You can name your car folder anything you want. 

## After that change to the directory of the created car and make changes to myconfig.py as per your car's specifications

# To Pull an image with donkeycar installed with all types of cars created under mycars
### ```docker pull ghcr.io/ucsd-ecemae-148/donkeycontainer:donkey_built```

# To start the container run the start script
### ```./run.sh```

## Once inside the container you will see a directory named mycars

###
```cd mycars```


