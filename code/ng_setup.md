---
layout: default
title: neuroglancer
parent: visualization
#permalink: /vis/ng_setup
nav_order: 1
---

# Set up Neuroglancer (ng) locally
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

## Prepare for ng installation
{: .text-purple-200 }

To prepare your Windows computer for ng installation, first install these applications:
{: .fs-5 }
{: .fw-400 }

- Install [Visual Studio](https://visualstudio.microsoft.com/downloads/) - (download the free community version)
- Install [Anaconda](https://www.anaconda.com/products/individual)
- Install Git (call Anaconda Prompt or Command Prompt)
```bash
conda install -c anaconda git
```
- Install [chocolatey](https://chocolatey.org/install) 
    - Open Windows PowerShell and run as Administrator
    - In PowerShell, run:
    ```bash
    Get-ExecutionPolicy
    ```
    - In PowerShell, run:
    ```bash
    Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
    ```
    - Now check if choco is installed. In PowerShell, run:
    ```bash
    choco
    ```
    - If you get the message below, you are ready to go.
- Install nodejs
    - In PowerShell, run:
    ```bash
    choco install -y --force nodejs
    ```
    - If you get the message below, you are good to move on.
    - Test nodejs. In Command Prompt, run:
    ```bash
    node -v
    ```
    - If you see the message below, you are in good to go.

## Create a new virtual enviroment
{: .text-purple-200 }

To install the neuroglancer and the related components, we want to first create a new enviroment (let's call it ng_torch) and install Pytorch for it:
{: .fs-5 }
{: .fw-400 }

- Open Anaconda Prompt or Command Prompt, run:
```bash
conda create -n ng_torch python=3.8
activate ng_torch
conda install pytorch torchvision cudatoolkit=11.0 -c pytorch
```
- Now check your Pytorch version (we need the version to be >1.80):
```bash
pip3 show torch
```
- If you need to update pip in the virtual enviroment, run
```bash
python -m pip install --user --upgrade pip
```
- Now use pip to install ng and other packages you need:
```bash
pip install neuroglancer
pip install jupyter  # (optional) jupyter/ipykernel installation
pip install numpy Pillow requests tornado sockjs-tornado six google-apitools selenium imageio h5py cloud-volume
python -m pip install -U scikit-image
```
- Make a folder for ng:
```bash
mkdir project
cd project
git clone https://github.com/google/neuroglancer.git
cd neuroglancer
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")" \
    [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"    # This loads nvm
```
- Install npm. In Anaconda Prompt, run:
```bash
pip install npm
```
- After installation, run:
```bash
npm i
```
- Finally, in Anaconda Prompt, run:
```bash
python setup.py install
```
- If you encounter error messages in the last step, run this code before re-run the last line:
```bash
npm run build-python-min
```

## Use Jupyter Notebook to set up your ng viewer
{: .text-purple-200 }

Open Anaconda, locate your ng enviroment and start a Jupyter Notebook:
{: .fs-5 }
{: .fw-400 }

- Open Anaconda Prompt or Command Prompt, run: