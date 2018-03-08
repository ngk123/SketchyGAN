SketchyGAN: Towards Diverse and Realistic Sketch to Image Synthesis
=====================================

Code for ["SketchyGAN: Towards Diverse and Realistic Sketch to Image Synthesis"](https://arxiv.org/abs/1801.02753).


## Prerequisites

- Python 3, NumPy, SciPy, OpenCV 3
- Tensorflow(>=1.4.0)
- A recent NVIDIA GPU


## Preparations

- The path to data files needs to be specified in `input_pipeline.py`. See below for detailed information on data files.
- You need to download ["Inception-V4 model"](http://download.tensorflow.org/models/inception_v4_2016_09_09.tar.gz), unzip it and put the checkpoint under `inception_v4_model`.


## Dataset
Pre-built tfrecord files are available for out of the box training.
- Files for the Sketchy Database can be found [here](https://gtvault-my.sharepoint.com/:f:/g/personal/wchen342_gatech_edu/EtKmg1alDNdIl09WcvtJp_cBFs_7td3wKnb5FUcWZswEmw?e=eBGO6G).
- Files for Augmented Sketchy(i.e. flickr images+edge maps), resized to 256x256 regardless of original aspect ratios, can be found [here](https://gtvault-my.sharepoint.com/:f:/g/personal/wchen342_gatech_edu/EmF7KlhqZ8ZPnpzbTIMDKBoBcjMrezh3X2eS1P_KtWiGCQ?e=BJhFPF).

If you wish to get the original image files:
- The Sketchy Database can be found [here](http://sketchy.eye.gatech.edu/).
- Use `extract_images.py` under `data_processing` to extract images from tfrecord files. You need to specify input and output paths. The extracted images will be sorted by class names.
- Please contact me if you need the original (not resized) Flickr images, since they are too large to upload to any online space.


## Configurations

The model can be trained out of the box, by running `main_single.py`. But there are several places you can change configurations:

- Commandline options in `main_single.py`
- Some global options in `config.py`
- Activation/Normalization functions in `models_mru.py`


## Others

- The model will be saved periodically. If you wish to resume, just use commandline switch `resume_from`.
- If you wish to test the model, change `mode` from `train` to `test` and fill in `resume_from`.