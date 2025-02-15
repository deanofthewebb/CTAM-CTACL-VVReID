# CTAM-CTACL-VVReID
Official implementation of 'Camera-Tracklet-Aware Contrastive Learning for Unsupervised Vehicle Re-Identification'
*Source code for a under-review paper.

## Abastract
![workflow](https://user-images.githubusercontent.com/13298951/133180399-afdfeaec-4038-47df-82d1-9abde0ee5b30.png)
Recently, vehicle re-identification methods based on deep learning constitute remarkable achievement. However, this achievement requires large-scale and well-annotated datasets. In constructing the dataset, assigning globally available identities (Ids) to vehicles captured from a great number of cameras is labour-intensive, because it needs to consider their subtle appearance differences or viewpoint variations. In this paper, we propose camera-tracklet-aware contrastive learning (CTACL) using the multi-camera tracklet information without vehicle identity labels. The proposed CTACL divides an unlabelled domain, i.e., entire vehicle images, into multiple camera-level subdomains and conducts contrastive learning within and beyond the subdomains. The positive and negative samples for contrastive learning are defined using tracklet Ids of each camera. Additionally, the domain adaptation across camera networks is introduced to improve the generalisation performance of learnt representations and alleviate the performance degradation resulted from the domain gap between the subdomains. We demonstrate the effectiveness of our approach on video-based and image-based vehicle Re-ID datasets. Experimental results show that the proposed method outperforms the recent state-of-the-art unsupervised vehicle Re-ID methods. The source code for this paper is publicly available on this github



## Dependencies

This project mainly complied with Python3.6, Pytorch 1.2. Nvidia driver version is 460.91
All details are included in the 'requirement.txt'

~~~
#Setting the environment
pip install -r requirements.txt
~~~
* You may need to install additional libraries, but, just do 'pip install brbrbr'

## File configuration
Perhaps, you may need to create 'logs', 'models', and 'learnt_models' directries.
~~~
<br>
├── data #Extract dataset to this directory. <br>
├── experiments <br>
├── lib <br>
├── logs <br>
├── learnt_models #Extract weight files for reproducting experimental results <br>
├── models <br>
│   └── imagenet #Extract backbone network checkpoint here <br>
├── output # Extract the checkpoints to reproduct the results. <br>
└── tools <br>
~~~


## Dataset preparation
[VVeRI-901](https://gas.graviti.cn/dataset/hello-dataset/VVeRI901) is mainly used base a benchmark for the video-based vehicle re-id. Additonally, [Veri-776](https://vehiclereid.github.io/VeRi/) dataset and [Veri-wild](https://github.com/PKU-IMRE/VERI-Wild) dataset are also used for this work.
To train the proposed method, change the ditectory names to 'bounding_box_train' (training set), 'bounding_box_test' (test set), 'query' (query set).
In using VVeRI-901 dataset, 
~~~
Would be added.
~~~

In using Veri-Wild dataset, to evaluate the small, medium, and large test set. you have to make the directories as follows:
~~~
output_test_middle_img_path =  './test_middle/'
output_query_middle_img_path = './query_middle/'

output_test_small_img_path =  './test_small/'
output_query_small_img_path = './query_small/'
~~~

Please refer 'preprocessiong_dataset/veri_wild_transform.py' file to conduct experiments for veri-wild dataset.



## Backbone network (ResNet-50) Reference
You can download the backbone network model from [here](https://drive.google.com/file/d/1rfCcrOzIWNWakA3BYkqp5om2_nI5Ftr8/view?usp=sharing). Save the weight file on './models/imagenet'




## How to train and test
See the script file.
~~~
./exp.sh
~~~


## Reproduce the experimental results

You can download the checkpoint files to reproduct the experiment results from [here](https://www.dropbox.com/s/gzp6s6056facwsh/models.tar.gz?dl=0). After download it. Extract the file under the './learnt_models/'



## Code reference.
* The code is mainly encouraged by [SSML](https://github.com/andreYoo/VeRI_SSML_FD.git) 


## Reference.
~~~
@misc{yu2021cameratrackletaware,
      title={Camera-Tracklet-Aware Contrastive Learning for Unsupervised Vehicle Re-Identification}, 
      author={Jongmin Yu and Junsik Kim and Minkyung Kim and Hyeontaek Oh},
      year={2021},
      eprint={2109.06401},
      archivePrefix={arXiv},
      primaryClass={cs.CV}
}
~~~
