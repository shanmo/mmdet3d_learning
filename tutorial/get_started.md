# install 

- install follow https://mmdetection3d.readthedocs.io/en/latest/getting_started.html

# docker 

- https://github.com/open-mmlab/mmdetection3d/issues/438
  - https://github.com/open-mmlab/mmdetection3d/issues/563
  - refer to [this](https://blog.csdn.net/claram/article/details/104228727) for how to set `-itd` for `docker run`

```
nvidia-docker run -it --gpus all --ipc=host --shm-size=8g -p 2022:22 -v /home/sean/mylibs/mmdetection3d:/mmdetection3d -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY nvcr.io/nvidia/pytorch:20.12-py3
```

```
apt update
apt install ffmpeg libsm6 libxext6 git ninja-build libglib2.0-0 libsm6 libxrender-dev libxext6
apt clean
rm -rf /var/lib/apt/lists/*
python -m pip install --upgrade pip
pip3 install --ignore-installed PyYAML
pip install open3d
git clone https://github.com/open-mmlab/mmcv.git
cd mmcv
MMCV_WITH_OPS=1 pip install -e .
cd ..
git clone https://github.com/open-mmlab/mmdetection.git
cd mmdetection
pip install -r requirements/build.txt
pip install -v -e .
pip install git+https://github.com/open-mmlab/mmsegmentation.git
git clone https://github.com/open-mmlab/mmdetection3d.git
cd mmdetection3d
pip install -v -e .
```

- after exit, to run it next time need to use `docker start [container ID]`
  - can use `docker attach [container ID]` to attach to running container 

# test

- to test, use 
```
python demo/pcd_demo.py demo/data/kitti/kitti_000008.bin configs/second/hv_second_secfpn_6x8_80e_kitti-3d-car.py /mmdetection3d/checkpoints/hv_second_secfpn_6x8_80e_kitti-3d-car_20200620_230238-393f000c.pth 
```

- need to visualize results offline https://mmdetection3d.readthedocs.io/en/latest/useful_tools.html#visualization

- visualization has bug https://github.com/open-mmlab/mmdetection3d/issues/1628
  - https://github.com/open-mmlab/mmdetection3d/issues/1287#issuecomment-1186727095
