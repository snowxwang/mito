---
layout: default
title: MitoNet
nav_order: 5
---

# MitoNet: a scalable framework for automated mitochondria segmentation
{: .text-purple-300 }
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

## Install Pytorch Connectomics
{: .text-purple-200 }

To prepare your Windows computer for the installation, first install these applications:

- Install [Visual Studio](https://visualstudio.microsoft.com/downloads/)
- Install [CUDA Toolkit](https://developer.nvidia.com/cuda-downloads)
- Install [Anaconda](https://www.anaconda.com/products/individual)
- Install Git:
```js
conda install -c anaconda git
```

Now follow the steps below to install the package:

- open your Anaconda Prompt (click Start, then search, or select Anaconda Prompt from the menu) and run the follow commands in sequence:
{: .text-green-100 }

```js
conda create -n py3_torch python=3.8
activate py3_torch
conda install pytorch torchvision cudatoolkit=11.0 -c pytorch
```

- check your Pytorch version (we want the version to be >1.80):
{: .text-green-100 }

```js
pip3 show torch
```

- then check if Pytorch is installed with CUDA support:
{: .text-green-100 }

```js
activate py3_torch
python
```
```python
import torch
torch.cuda.is_available() # output would be True or False
```

- if you get a 'False', try to reinstall pytorch with CUDA in different ways; also, you should go to the [official website](https://pytorch.org/get-started/locally/#windows-anaconda) for detailed instructions; solutions that worked for us:
{: .text-red-000 }{: .px-6 }

  - using conda:{: .px-6 }
  ```js
  conda install pytorch torchvision torchaudio cudatoolkit=11.3 -c pytorch
  ```
  {: .px-6 }
  - using pip:{: .px-6 }
  ```js
  pip3 install torch==1.10.1+cu113 torchvision==0.11.2+cu113 torchaudio===0.10.1+cu113 -f https://download.pytorch.org/whl/cu113/torch_stable.html
  ```
{: .px-6 }

- now verify if nvcc is accessible from terminal:
{: .text-green-100 }

```js
nvcc --version
```

- finally, install the Pytorch Connectomics package:
{: .text-green-100 }

```js
git clone https://github.com/zudi-lin/pytorch_connectomics.git
cd pytorch_connectomics
pip install --editable .
```

- For installation on Linux machines, follow the instructions [here](https://connectomics.readthedocs.io/en/latest/).
 

## Configure the model
{: .text-purple-200 }


## Semantic Segmentation
{: .text-purple-200 }


## Instance Segmentation
{: .text-purple-200 }

