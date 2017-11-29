![Darknet Logo](http://pjreddie.com/media/files/darknet-black-small.png)

#Darknet#
Darknet is an open source neural network framework written in C and CUDA. It is fast, easy to install, and supports CPU and GPU computation.

For more information see the [Darknet project website](http://pjreddie.com/darknet).

For questions or issues please use the [Google Group](https://groups.google.com/forum/#!forum/darknet).

## Running Darknet 

In order to run yolo you will need some weights you can download our weights [here](https://drive.google.com/drive/folders/1eF-o82IRIRA0lSkEZCDYhDYmlo2CQqXo?usp=sharing) 


To run the detector on a single image run 
`./darknet detect test <path to .data> <path to .cfg> <path to weights> <path to image>`

Example:
`./darknet detector test cfg/coco.data cfg/yolo.cfg yolo.weights data/dog.jpg`

Running Tiny yolo is the same command, but substitute the your tiny.cfg and your tiny weights

Example:
`./darknet detector test cfg/voc.data cfg/tiny-yolo-voc.cfg tiny-yolo-voc.weights data/dog.jpg`

## Training Darknet 

First you will need to set up your data set. We followed this [tutorial](http://guanghan.info/blog/en/my-works/train-yolo/) 
**Note** this tutorial is for yolo v1, so steps 3 and 4 are little different 

Or you can download our [data set](https://drive.google.com/drive/folders/1-NaIYhqC54IDx6BShN5djhMmTzUbQ42K?usp=sharing)

Once you have completed steps 1 and 2 and you have your data set you will need to set up your .data file. Take a look at cfg/roomba.data. It should look like this:

```
classes= 1
train  = /home/eric/bbox/BBox-Label-Tool/stopsign_list.txt
test = /home/eric/bbox/BBox-Label-Tool/stopsign_list.txt
names = cfg/roomba.names
backup = /home/eric/backup/
```

Make sure train paths to the file that lists where all your training data is.
Then we will set up our .names file. This file lists all the names of the classes you trained. Our file looks like this. 
```
roomba
```
our weights are only trained with one class so we just have "roomba"

make sure to setup a backup directory this is where the weights you have trained will be made.

finally we can train. run somthing like 

`./darknet detector train cfg/roomba.data cfg/yolo.cfg`

on subsequent runs add your weights to the end of the command to continue to train your weights.

Example `./darknet detector train cfg/roomba.data cfg/yolo.cfg ~/backup/yolo.backup`

for more information be sure to read the official yolo [page](https://pjreddie.com/darknet/yolo/). 
