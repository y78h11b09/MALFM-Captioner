# MALFM-Captioner: A Multi-Path Alignment Learning for Image Captioning with Feature Mask.


## Official implementation for the paper ["MALFM-Captioner: A Multi-Path Alignment Learning for Image Captioning with Feature Mask"](https://ieeexplore.ieee.org/document/11526804)


## Training prerequisites

[comment]: <> (Dependencies can be found at the [Inference notebook]&#40;https://colab.research.google.com/drive/1tuoAC5F4sC7qid56Z0ap-stR3rwdk0ZV?usp=sharing&#41; )
You can create environment and install dependencies:
```
conda env create -f environment.yml
```
or
```
bash install_req.sh
```
or
```
pip install -r requirements.txt
```


## COCO training

Download [train_captions](https://drive.google.com/file/d/1D3EzUK1d1lNhD2hAvRiKPThidiVbP2K_/view?usp=sharing).

Download the COCO region features from [hdf5](https://pan.baidu.com/s/1Au97sw12o7UdrEZN_QRzBg). Acess code: labl.

Download [training images](http://images.cocodataset.org/zips/train2014.zip) and [validation images](http://images.cocodataset.org/zips/val2014.zip) and unzip (We use Karpathy et el. split).

Download [oscar_split_ViT-B_32_train_512.pkl](https://drive.google.com/file/d/1CVsEQ5YRH3b6ZVRr7gY7ni7Ge1TgHvuM/view?usp=share_link)  in ./data/coco/

### Prepare evaluation
Change the work directory and set up the code of evaluation :
```
cd ./captioneval/coco_caption
bash ./get_stanford_models.sh
```
### Run

If you want train the model, you can use the command:
```
MKL_THREADING_LAYER=GPU python -m torch.distributed.launch \
    --nproc_per_node 8 \
    train.py \
    --tag my_experiment
```
## Citation
If you use this code for your research, please cite:
```
@article{yang2026malfm,
  title={MALFM-Captioner: A Multipath Alignment Learning for Image Captioning With Feature Mask},
  author={Yang, Xiaobao and Song, Bohui and Dong, Yizhuo and Sun, Wei and Sun, Tianyu and Zheng, Shuaikang and Hou, Zhiqiang},
  journal={IEEE Transactions on Neural Networks and Learning Systems},
  year={2026},
  publisher={IEEE}
}
```


## Acknowledgments
This repository is heavily based on [CLIP](https://github.com/openai/CLIP), [CLIP_prefix_caption](https://github.com/rmokady/CLIP_prefix_caption), [DiffCap](https://github.com/arealgoodname/DiffCap) and [Hugging Face](https://github.com/huggingface/transformers) repositories.
For training we used the data of [COCO dataset](https://cocodataset.org/#home).





