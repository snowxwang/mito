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
{: .fs-5 }
{: .fw-400 }

- Install [Visual Studio](https://visualstudio.microsoft.com/downloads/)
- Install [CUDA Toolkit](https://developer.nvidia.com/cuda-downloads)
- Install [Anaconda](https://www.anaconda.com/products/individual)
- Install Git
```bash
conda install -c anaconda git
```

Now follow the steps below to install the package:
{: .fs-5 }
{: .fw-400 }

1) Open your Anaconda Prompt (click Start, then search, or select Anaconda Prompt from the menu) and run the follow commands in sequence:
{: .text-green-100 }
```bash
conda create -n py3_torch python=3.8
activate py3_torch
conda install pytorch torchvision cudatoolkit=11.0 -c pytorch
```

2) Check your Pytorch version (we want the version to be >1.80):
{: .text-green-100 }
```bash
pip3 show torch
```

3) Check if Pytorch is installed with CUDA support:
{: .text-green-100 }
```bash
activate py3_torch
python
```
```python
import torch
torch.cuda.is_available() # output would be True or False
```

* Note: if you get a **False**, try to reinstall pytorch with CUDA in different ways; also, you should go to the [official website](https://pytorch.org/get-started/locally/#windows-anaconda) for detailed instructions; solutions that worked for us:
{: .fs-3 }
{: .text-purple-000 }
  
  * using conda:
  {: .fs-3 }
  {: .text-purple-000 }
  ```bash
  conda install pytorch torchvision torchaudio cudatoolkit=11.3 -c pytorch
  ```

  * using pip:
  {: .fs-3 }
  {: .text-purple-000 }
  ```bash
  pip3 install torch==1.10.1+cu113 torchvision==0.11.2+cu113 torchaudio===0.10.1+cu113 -f https://download.pytorch.org/whl/cu113/torch_stable.html
  ```

4) Verify if nvcc is accessible from terminal:
{: .text-green-100 }

```bash
nvcc --version
```

5) Finally, install the Pytorch Connectomics package:
{: .text-green-100 }

```bash
git clone https://github.com/zudi-lin/pytorch_connectomics.git
cd pytorch_connectomics
pip install --editable .
```

For installation on Linux machines, follow the instructions [here](https://connectomics.readthedocs.io/en/latest/).
{: .fs-5 }
{: .fw-400 }


## Semantic Segmentation
{: .text-purple-200 }

Before running the model, first install **wget** for Windows - a free network utility to retrieve files from the World Wide Web using HTTP and FTP. This post provides a detailed tutorial for installing [wget](https://builtvisible.com/download-your-website-with-wget/). In general, follow the steps below in sequence:
{: .fs-5 }
{: .fw-400 }

- Download wget: [https://eternallybored.org/misc/wget/](https://eternallybored.org/misc/wget/)
- Copy wget.exe to __C:\Windows\System32__ folder
- In your command line, type:
```bash
wget -h
```

Now start the training process:
{: .fs-5 }
{: .fw-400 }

1) Download the sample dataset:
{: .text-green-100 }
```bash
wget http://rhoana.rc.fas.harvard.edu/dataset/lucchi.zip
```
Note: **wget** downloads files in the current working directory where it is run
{: .fs-3 }
{: .text-red-100 }

2) Configure the model for training:
{: .text-green-100 }
```bash
# start anaconda prompt
conda activate py3_torch
python
```
```python
import torch

print(f"Is CUDA supported by this system? {torch.cuda.is_available()}") 
# Returns True if CUDA is supported by your system, else False

print(f"ID of current CUDA device: {torch.cuda.current_device()}")
# Returns ID of current device (you need this info for configuration)
```

3) Run the script for training:
{: .text-green-100 }



## Configure the model
{: .text-purple-200 }


## Instance Segmentation
{: .text-purple-200 }

