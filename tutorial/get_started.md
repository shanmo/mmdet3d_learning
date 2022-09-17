# install 

- install follow https://mmdetection3d.readthedocs.io/en/latest/getting_started.html

# test

- to test, use 
```
python demo/pcd_demo.py demo/data/kitti/kitti_000008.bin configs/second/hv_second_secfpn_6x8_80e_kitti-3d-car.py /home/sean/workspace/mmdet3d/pretrain/hv_second_secfpn_6x8_80e_kitti-3d-car_20200620_230238-393f000c.pth --show
```

- visualization has bug https://github.com/open-mmlab/mmdetection3d/issues/1628

# docker 

- https://github.com/open-mmlab/mmdetection3d/issues/438

```
nvidia-docker run -it --gpus all --ipc=host --shm-size=8g -p 2022:22 -v /home/sean/mylibs/mmdetection3d:/mmdetection3d nvcr.io/nvidia/pytorch:20.12-py3
```