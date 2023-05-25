# Installation

## Make an environment
```bash
conda create -n polarformer python=3.8 -y
conda activate polarformer

git clone https://github.com/fudan-zvg/PolarFormer
cd PolarFormer
source activate cuda_11.0_env
cd ..
```

## Install pytorch

```bash
pip install torch==1.9.1+cu111 torchvision==0.10.1+cu111 torchaudio==0.9.1 -f https://download.pytorch.org/whl/torch_stable.html
```

## Install mmcv, mmdetection, mmsegmentation

```bash
pip install openmim
mim install mmcv-full==1.4.0
python -c "import mmcv._ext"

pip install mmdet==2.19.0
pip install mmsegmentation==0.14.1
```

## Install MMDetection3D

Please install MMDetection3D <= v0.18.1, since the coordinate systems are refactored in versions v1.x.x, for which this code may not work.

```bash
git clone  https://github.com/open-mmlab/mmdetection3d.git
cd mmdetection3d
git checkout v0.17.3 
pip install -r requirements/build.txt
python setup.py install
cd ..
```

## Install PolarFormer

```bash
cd PolarFormer
mkdir ckpts
mkdir data
ln -s ../mmdetection3d mmdetection3d
ln -s {nuscenes_path} data/nuscenes
```

## Install more dependencies

```bash
pip install -U llvmlite==0.31.0
pip install "numpy<1.20.0" pandas matplotlib
conda install -c conda-forge pyquaternion shapely scikit-learn cachetools tqdm
```
