# Introduction 
The goal of this project is to investigate how recommender systems, might improve user experiences in various domains. This repository contains reference implementations of state-of-the-art recommender system methods on a variety of practical datasets. In particular, the following classes of recommender systems are explored. This includes: 
1. Introduction to Recommender Systems 
2. Collaborative filtering algorithms
3. Content-based filtering recommender systems
4. Sequence Aware recommender systems
5. Session-Based recommender systems 
6. Knowledge Graph Based Recommender Systems

**Please Note: The repository is under active development. As a result, the provided demos will not be stable until they are presented to project participants in the introductory demo sessions in mid-September.**

# Accessing Data
During the project, all of the datasets included in the demo will be available on the Vector cluster at: `/ssd003/projects/aieng/public/recsys_datasets/`

For external use, we are providing the following [link](https://tinyurl.com/2p8mxjsd) for downloading the datasets.

Please write [winnie.au@vectorinstitute.ai](mailto:winnie.au@vectorinstitute.ai) to request access.


# Environment Configuration 
Vector has provided a global kernel **recsys** that contains all the necessary packages to run the provided demos on the Vector cluster. From the jupyter notebook interface, simply select the **recsys** kernel from the *Change Kernel* dropdown and run the demo. For a comprehensive guide on how to configure the environment on the vector cluster, please refer to [Cluster Access Instructions](https://tinyurl.com/3dewf27p). 

If you are looking to configure the environment externally, from the root directory of the repo run the following commands:
```
conda create -n recsys python=3.7
conda activate recsys 
pip install -r requirements.txt
```
