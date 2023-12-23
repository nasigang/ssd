# SSD (Single Shot Multibox Detection)
## Pytorch implementation of SSD 
Based on [this paper](https://arxiv.org/abs/1512.02325).
The authors' original implementation can be found [here](https://github.com/weiliu89/caffe/tree/ssd).

## Requirements
Python ≥ 3.6
Install libraries:  ``` pip install -r requirements.txt  ```

## DATA: COCO
```
cd datasets/coco/

wget http://images.cocodataset.org/zips/train2017.zip
wget http://images.cocodataset.org/zips/val2017.zip
wget http://images.cocodataset.org/annotations/annotations_trainval2017.zip
unzip train2017.zip
unzip val2017.zip
unzip annotations_trainval2017.zip

python prepare.py --root .
```

## Configuration
YAML configure management. See configs/ssd300.yaml for detail.

## Training
``` # Run python train.py --cfg config/ssd300.yaml --logdir <LOG_DIRECTORY> ```
<LOG_DIRECTORY> is a path for the will-be-trained log file.

An interrupted training can be resumed by:
```
# Run train.py with --resume to restore the latest saved checkpoint file in the log directory.
python train.py --cfg config/ssd300.yaml --logdir <LOG_DIRECTORY> --resume```

## Evaluation
``` # Run coco_eval.py to calculate the COCO mAP metric using pycocotools:  
python coco_eval.py --cfg <CONFIG_FILE> --pth <LOG_DIRECTORY>/best.pth --coco_dir <COCO_DIR>
```

## Result
![demo]()
