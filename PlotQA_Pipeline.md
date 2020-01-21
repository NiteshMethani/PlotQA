#
# PlotQA Pipeline code
**VED stage**

For this stage, we used Detectron which is Facebook AI Research's software system that implements state-of-the-art object detection algorithms. It is written in Python and powered by the Caffe2 deep learning framework. We used the Faster RCNN with FPN model given at https://github.com/facebookresearch/Detectron for detecting different elements in the plot images.

Follow these instructions to train the Faster RCNN with FPN model on the PlotQA dataset:
1. Install Caffe2 and Detecron. You might have to use [this](https://drive.google.com/file/d/1uk8qqzcvLV7fWQ6EcavVBb0BYXxPGf5U/view?usp=sharing) script to install Caffe2 on a AWS GPU instance.
2. Download the PlotQA directory which contains the images and the coco-style annotations from [here](https://drive.google.com/drive/folders/15bWhzXxAN4WsXn4p37t_GYABb1F52nQw?usp=sharing) and extract it in the directory: '~/Detectron/detectron/datasets/data/.'
3. Replace the `~/Detectron/detectron/datasets/dataset_catalog.py` with the file which can be downloaded from [here](https://drive.google.com/file/d/1rbhiS-Q6-pHyPkdngDRKtZz51f6HA1AZ/view?usp=sharing).
4. Download the `e2e_faster_rcnn_R-50-FPN_1x.yaml` config file from [here](https://drive.google.com/file/d/1uv7EGLeAixkKseZZLBnLTikG2xmXZpRu/view?usp=sharing). This file has the hyperparameter settings that we have used for training.
5. Run the following command to start training followed by testing:
```
python tools/train_net.py --cfg [PATH_TO_THE_CONFIG]/e2e_faster_rcnn_R-50-FPN_1x.yaml  OUTPUT_DIR [PATH_TO_OUTPUT_DIR]
```
The model predictions will be saved in the file `[OUTPUT_DIR]/test/coco_val/generalized_rcnn/bbox_coco_val_results.json`.

You can download the saved weights from [here](https://drive.google.com/drive/folders/1P00jD-WFg_RBissIPmuWEWct3xoM3mgU?usp=sharing).

**Requirements**
Before moving to the next stage, you might need to install some packages like click, tqdm, pyocr, matplotlib, etc.
You can refer to `.sh` files in [this](https://drive.google.com/drive/folders/1hDlMCgxmrfiqhuydRT3OnP4Fqp9eyGu-?usp=sharing) directory for the exact commands that we used to install a particular package.

#
**OCR and SIE stage**

1. Download the python script `generate_detections_for_fasterrcnn.py` from [here](https://drive.google.com/file/d/1TQ4F0rDB8tL32wBUdhkAY0ZuuMav1mnR/view?usp=sharing) and run the following command to convert the model predictions obtained in the VED stage into the format required by the successive stages.
```
python2 generate_detections_for_fasterrcnn.py [OUTPUT_DIR]/test/coco_val/generalized_rcnn bbox_coco_val_results.json detections
```
This will store the modified model predictions at `[OUTPUT_DIR]/test/coco_val/generalized_rcnn/detections`. The detections are of the format: `CLASS_LABEL CLASS_CONFIDENCE XMIN YMIN XMAX YMAX` where (XMIN, YMIN) and (XMAX, YMAX) refers to the top-left and bottom-right co-ordinates of the predicted bounding box respectively.

2. Download the code directory from [here](https://drive.google.com/drive/folders/1cuvFdPVUI1IKx25g56mt5F0FeS_ai4XV?usp=sharing). Run the following command to extract the plot information inito a semi-strucutred table:
```
python ocr_and_sie.py [PATH_TO_PNG_DIR] [PATH_TO_DETECTIONS] [OUTPUT_DIR]
```
This command will store the tables into `.csv` format in the `[OUTPUT_DIR]`

#
**Table QA stage**

To be updated soon

#
Please cite the following if you use the PlotQA dataset in your work:
```
@article{DBLP:journals/corr/abs-1909-00997,
  author    = {Nitesh Methani and
               Pritha Ganguly and
               Mitesh M. Khapra and
               Pratyush Kumar},
  title     = {PlotQA: Reasoning over Scientific Plots},
  journal   = {CoRR},
  volume    = {abs/1909.00997},
  year      = {2019},
  url       = {http://arxiv.org/abs/1909.00997},
  archivePrefix = {arXiv},
  eprint    = {1909.00997},
  timestamp = {Mon, 16 Sep 2019 17:27:14 +0200},
  biburl    = {https://dblp.org/rec/bib/journals/corr/abs-1909-00997},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
```

#
# Contact
If you have any questions, suggestions or comments about the dataset in the paper, feel free to contact us at:
Nitesh Methani (nmethani@cse.iitm.ac.in), Pritha Ganguly (prithag@cse.iitm.ac.in).

