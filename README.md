## Using FCAF3D for 3D Apple detection

> **FCAF3D: Fully Convolutional Anchor-Free 3D Object Detection**<br>
> [FCAF3D] (https://github.com/SamsungLabs/fcaf3d)

For small object detection, the voxel_size of the model was changed from 0.01 to 0.005 and the feature level was changed from 4 to 3.

<p align="center">
  <img src="https://github.com/joshiaLee/3D_Object_Detection/assets/93809073/2278455e-af2a-416b-93c7-c0b2be09e397" alt="img1" width="50%"/>
</p>

<p align="center">
  <img src="https://github.com/joshiaLee/3D_Object_Detection/assets/93809073/e731a6f3-4511-441a-b3f9-7b0f6fef05d1" alt="img2" width="50%"/>
</p>



### Installation
For convenience, Docker is available [Dockerfile](docker/Dockerfile).

**Create your own Data**  
Look carefully [sunrgbd_trainval](data/sunrgbd/sunrgbd_trainval).
make your own data like sample files.   

```shell
python tools/create_data.py sunrgbd --root-path ./data/sunrgbd --out-dir ./data/sunrgbd --extra-tag sunrgbd
```

**Training**
```shell
python tools/train.py configs/fcaf3d/fcaf3d_sunrgbd-3d-10class.py
```

**Visualization**  
For better visualizations, you may set `score_thr` in configs to `0.25`:
```shell
python tools/test.py configs/fcaf3d/fcaf3d_sunrgbd-3d-10class.py \
/work_dirs/fcaf3d_sunrgbd-3d-10class/latest.pth --eval mAP --show --show-dir \
/work_dirs/fcaf3d_sunrgbd-3d-10class
```

**Precision on Apple Data**
| Object | mAP@0.25 | mAP@0.5 |
|:------:|:--------:|:-------:|
| Apple | 0.9894 | 0.9822 |



