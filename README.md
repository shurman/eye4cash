## Introduction

Use tiny-yolo to train model for detect USD/NTD cash

## Installation

Please follow [Source Project](https://github.com/thtrieu/darkflow)

## Model

Tiny-YOLO for detect 13 classes which are containing 9 convolution layers

## Dataset

There are currently 507 images with
* NTD-1: 154 bounding boxes
* NTD-5: 80
* NTD-10: 168
* NTD-50: 46
* NTD-100: 56
* NTD-500: 30
* NTD-1000: 33
* USD-1c: 121
* USD-10c: 89
* USD-25c: 81
* USD-1: 38
* USD-20: 13
* USD-100: 20

## Training Script

1. Enter Goofy docker
	```
    $ docker exec -it TF_shurman_GPU2 bash
    ```

2. Go to /raidHDD/experimentData/Dev/Shurman/darkflow
    ```
    $ ./flow --model cfg/tiny-yolo-cash.cfg --train --dataset ../cashdata_new --annotation ../cashdata_new_label --gpu 0.8 --epoch 100 --savepb
    ```

Here `--train` means that start training with `--model` for #`--epoch`, and dataset locates at `--dataset` & `--annotation`, using `--gpu` in 0.8 of total memory, and finally output PB file(`--savepb`)

## Inference Sample

1. Enter Goofy docker
 	```
    $ docker exec -it TF_shurman_GPU2 bash
 	```
    
2. Go to /raidHDD/experimentData/Dev/Shurman/darkflow
	```
	$ ./flow --imgdir ../cashdata_test_scale --model cfg/tiny-yolo-cash.cfg --load -1 --gpu 0.5 --json
	```

Here `imgdir` is testing data path, `--load -1` means that picks the lasted checkpoint (or use `--load 9006`) for `--model`, and output in `--json`.

3. Output will be located at `imgdir`/out


## Future Work - Mobile Demostraction
![image](https://github.com/shurman/eye4cash/blob/master/ui19202.png?raw=true)
