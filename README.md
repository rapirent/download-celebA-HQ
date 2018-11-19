# download-celebA-HQ
Python script to download and create the celebA-HQ dataset.

To get the celebA-HQ dataset, you need to 
 a) download the celebA dataset `download_celebA.py` ,
 b) download some extra files `download_celebA_HQ.py`,
 c) do some processing to get the HQ images `make_HQ_images.py`.


# Usage
1) Clone the repository
```
git clone https://github.com/nperraud/download-celebA-HQ.git
cd download-celebA-HQ
```

2) Install necessary packages (Because specific versions are required Conda is recomended)
 * Install miniconda https://conda.io/miniconda.html
 * Create a new environement
 ```
 conda create -n celebaHQ python=3
 source activate celebaHQ
 ```
    * if you use pyenv, may need to follow up below:
    ```sh
    pyenv install miniconda3-3.7.0
    conda creat -n celebaHQ python=3
    pyenv activate miniconda3-3.7.0/envs/celebaHQ # or pyenv local miniconda3-3.7.0/envs/celebaHQ
    ```
 * Install the packages
 ```
 conda install jpeg tqdm requests pillow urllib3 numpy cryptography scipy
 pip install opencv-python==3.4.2.17 cryptography==2.1.4
 ```
* Install 7zip (On Ubuntu)
 ```
 sudo apt-get install p7zip-full
 ```

3) Run the scripts
```
python download_celebA.py ./
python download_celebA_HQ.py ./
python make_HQ_images.py ./

```
where `./` is the directory where you wish the data to be saved.

4) Go watch a movie, theses scripts will take a few hours to run depending on your internet connection and your CPU power. The final HQ images will be saved as `.npy` files in the `./celebA-HQ` folder.

## Docker

If you have Docker installed, skip the previous installation steps and run the following command from the root directory of this project:

`docker build -t celeba . && docker run -it -v $(pwd):/data celeba`

By default, this will create the dataset in same directory. To put it elsewhere, replace `$(pwd)` with the absolute path to the desired output directory.

# Outliers
It seems that the dataset has a few outliers. A of problematic images is stored in `bad_images.txt`. Please report if you find other outliers.

# Remark
This script is likely to break somewhere, but if it executes until the end, you should obtain the correct dataset.

# Sources
This code is inspired by these files
* https://github.com/tkarras/progressive_growing_of_gans/blob/master/dataset_tool.py
* https://github.com/andersbll/deeppy/blob/master/deeppy/dataset/celeba.py
* https://github.com/andersbll/deeppy/blob/master/deeppy/dataset/util.py

# Citing the dataset
You probably want to cite the paper "Progressive Growing of GANs for Improved Quality, Stability, and Variation" that was submitted to ICLR 2018 by Tero Karras (NVIDIA), Timo Aila (NVIDIA), Samuli Laine (NVIDIA), Jaakko Lehtinen (NVIDIA and Aalto University).
