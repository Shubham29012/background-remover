# BackgroundRemover



### Requirements

* python >= 3.6
* python3.6-dev #or what ever version of python you use
* torch and torchvision stable version (https://pytorch.org)
* ffmpeg 4.4+

#### How to install torch and fmpeg

Go to https://pytorch.org and scroll down to `INSTALL PYTORCH` section and follow the instructions.

For example:

```
PyTorch Build: Stable (1.7.1)
Your OS: Windows
Package: Pip
Language: Python
CUDA: None
```

To install ffmpeg and python-dev

```

```

### Installation
To Install backgroundremover, install it from pypi

```bash
pip install --upgrade pip
pip install backgroundremover
```
Please note that when you first run the program, it will check to see if you have the u2net models, if you do not, it will pull them from this repo

It is also possible to run this without installing it via pip, just clone the git to local start a virtual env and install requirements and run
```bash
python -m backgroundremover.cmd.cli -i "video.mp4" -mk -o "output.mov"
```
and for windows
```bash
python.exe -m backgroundremover.cmd.cli -i "video.mp4" -mk -o "output.mov"
```
### Usage as a cli
## Image

Remove the background from a local file image

```bash
backgroundremover -i "/path/to/image.jpeg" -o "output.png"
```

### Advance usage for image background removal

Sometimes it is possible to achieve better results by turning on alpha matting. Example:

```bash
backgroundremover -i "/path/to/image.jpeg" -a -ae 15 -o "output.png"
```
change the model for different background removal methods between `u2netp`, `u2net`, or `u2net_human_seg`
```bash
backgroundremover -i "/path/to/image.jpeg" -m "u2net_human_seg" -o "output.png"
```
## Video

### remove background from video and make transparent mov

```bash
backgroundremover -i "/path/to/video.mp4" -tv -o "output.mov"
```
### remove background from local video and overlay it over other video
```bash
backgroundremover -i "/path/to/video.mp4" -tov "/path/to/videtobeoverlayed.mp4" -o "output.mov"
```
### remove background from local video and overlay it over an image
```bash
backgroundremover -i "/path/to/video.mp4" -toi "/path/to/videtobeoverlayed.mp4" -o "output.mov"
```

### remove background from video and make transparent gif


```bash
backgroundremover -i "/path/to/video.mp4" -tg -o "output.gif"
```
### Make matte key file (green screen overlay)

Make a matte file for premiere

```bash
backgroundremover -i "/path/to/video.mp4" -mk -o "output.matte.mp4"
```

### Advance usage for video

Change the framerate of the video (default is set to 30)

```bash
backgroundremover -i "/path/to/video.mp4" -fr 30 -tv -o "output.mov"
```

Set total number of frames of the video (default is set to -1, ie the remove background from full video)

```bash
backgroundremover -i "/path/to/video.mp4" -fl 150 -tv -o "output.mov"
```

Change the gpu batch size of the video (default is set to 1)

```bash
backgroundremover -i "/path/to/video.mp4" -gb 4 -tv -o "output.mov"
```

Change the number of workers working on video (default is set to 1)

```bash
backgroundremover -i "/path/to/video.mp4" -wn 4 -tv -o "output.mov"
```
change the model for different background removal methods between `u2netp`, `u2net`, or `u2net_human_seg` and limit the frames to 150
```bash
backgroundremover -i "/path/to/video.mp4" -m "u2net_human_seg" -fl 150 -tv -o "output.mov"
```
