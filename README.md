# Modeling Relationships in Referential Expressions with Compositional Modular Networks
This repository contains the code for the following paper:

* R. Hu, M. Rohrbach, J. Andreas, T. Darrell, K. Saenko, *Modeling Relationships in Referential Expressions with Compositional Modular Networks*. in CVPR, 2017. ([PDF](http://arxiv.org/pdf/1611.09978.pdf))
```
@article{hu2017modeling,
  title={Modeling Relationships in Referential Expressions with Compositional Modular Networks},
  author={Hu, Ronghang and Rohrbach, Marcus and Andreas, Jacob and Darrell, Trevor and Saenko, Kate},
  journal={Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition},
  year={2017}
}
```

Project Page: http://ronghanghu.com/cmn  

Note: part of this repository is built upon the Faster RCNN code (https://github.com/rbgirshick/py-faster-rcnn), which is under the MIT License.

## Installation
1. Install Python 3 (Anaconda recommended: https://www.continuum.io/downloads)
2. Install TensorFlow (v1.0.0 or higher) following the instructions [here](https://www.tensorflow.org/install/).
3. Download this repository or clone with Git, and then `cd` into the root directory of the repository.

## Download data
1. Download the model weights of VGG-16 network (and Faster-RCNN VGG-16 network) converted from Caffe model:  
`./models/convert_caffemodel/params/download_vgg_params.sh`
2. Download the GloVe matrix for word embedding:  
`./word_embedding/download_embed_matrix.sh`

## Training and evaluation on the Visual Genome relationship dataset
1. Download the Visual Genome dataset from http://visualgenome.org/ and symbol link it to `exp-visgeno-rel/visgeno-dataset`
2. Download the image data (imdb) for training and evaluation:  
`./exp-visgeno-rel/data/download_imdb.sh`  
Alternatively, you may build the imdb yourself using `./exp-visgeno-rel/build_visgeno_imdb.ipynb`
3. Add the repository root directory to Python's module path: `export PYTHONPATH=.:$PYTHONPATH`.
4. Train the model:  
Strong supervision: `python ./exp-visgeno-rel/exp_train_visgeno_attbilstm_strong.py`  
Weak supervision: `python ./exp-visgeno-rel/exp_train_visgeno_attbilstm_weak.py`
5. Evaluate the model:  
Subject region precision: `python ./exp-visgeno-rel/exp_test_visgeno_attbilstm.py`  
Subject-object pair precision: `python ./exp-visgeno-rel/exp_test_visgeno_pair_attbilstm.py`  
 (change model path in the above files to the snapshot path in `./exp-visgeno-rel/tfmodel`)

## Training and evaluation on the Google-Ref dataset
1. Download the Google-Ref dataset from https://github.com/mjhucla/Google_Refexp_toolbox and symbol link it to `exp-refgoog/refgoog-dataset`
2. Download the image data (imdb) for training and evaluation:  
`./exp-refgoog/data/download_imdb.sh`  
Alternatively, you may build the imdb yourself using `./exp-refgoog/build_refgoog_imdb.ipynb`
3. Add the repository root directory to Python's module path: `export PYTHONPATH=.:$PYTHONPATH`.
4. Train the model:  
`python ./exp-refgoog/exp_train_refgoog_attbilstm.py`  
5. Evaluate the model (generate prediction output file):  
`python ./exp-refgoog/exp_test_refgoog_attbilstm.py`  
(change model path in the above file to the snapshot path in `./exp-refgoog/tfmodel`)
6. Use the evaluation tool in the Google-Ref dataset for evaluation.

## Training and evaluation on the Visual-7W dataset (pointing task)
1. Download the Visual-7W dataset from http://web.stanford.edu/~yukez/visual7w/index.html and symbol link it to `exp-visual7w/visual7w-dataset`
2. Download the image data (imdb) for training and evaluation:  
`./exp-visual7w/data/download_imdb.sh`  
Alternatively, you may build the imdb yourself with `./exp-visual7w/build_visual7w_imdb.ipynb`, `exp-visual7w/extract_rpn_proposals.py` and  `exp-visual7w/build_visual7w_imdb_attention.ipynb`
3. Add the repository root directory to Python's module path: `export PYTHONPATH=.:$PYTHONPATH`.
4. Train the model:  
`python exp-visual7w/exp_train_visual7w_attbilstm.py`
5. Evaluate the model:  
`python exp-visual7w/exp_test_visual7w_attbilstm.py`  
(change model path in the above file to the snapshot path in `./exp-visual7w/tfmodel`)

## Training and evaluation on the synthetic shapes dataset
1. Add the repository root directory to Python's module path: `export PYTHONPATH=.:$PYTHONPATH`.
2. Download the synthetic shapes dataset:  
`./exp-shape/data/download_shape_data.sh`
3. Train the model:  
`python ./exp-shape/exp_train_shape_attention.py`  
4. Evaluate the model:  
`python ./exp-shape/exp_test_shape_attention.py`  
(change model path in the above file to the snapshot path in `./exp-shape/tfmodel`)
