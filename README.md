# Imaging Toolkit README
**Author:** Elisa Warner  
**Last Updated:** Jan 06, 2020  

## Description:
This code is designed to help create an easy-to-use method for image preprocessing. It is for use with Python 3.6.

## Files Included:
* `patch_extractor.ipynb` : Extracts patches from histology slides
* `patch_functions.ipynb` : A notebook of functions for `patch_extractor.ipynb`

## Patch Extractor
An easy method for patch sampling, which requires only the changing of 5 hyperparameters to run the code.

### What to Expect:
* **Input:** a folder of histology slide images
* **Output:** a dictionary of patches by image and an output folder of subfolders, where each subfolder represents an image and every file within is a patch.

### Requirements:
* `openslide` : to manipulate histology images  
* `import_ipynb` : to access `patch_functions.ipynb`  
* `matplotlib.pyplot` : to plot the results  
* `tqdm` : to view progress bar  

This code has been tested on a Mac with Python 3.6 with Anaconda. To install the required packages, simply type in the command line: `pip install -r requirements.txt`  

More info on Anaconda: https://www.anaconda.com/distribution/  
More info on pip: https://pip.pypa.io/en/stable/reference/pip_download/

### How to Use:
Patch Extractor assumes you are extracting NxN tiles from a histology image that can be opened with openslide. There are five hyperparameters for this code:  
1. `FILETYPE` : [str] the file extension of your image (the code will only look for files with this file extension)  
2. `FILE_DIR` : [str] the directory of images. It is assumed that there exists a folder of images and that the images are not in subfolders.  
3. `OUT_DIR` : [str] the name of the directory for the output. It does not have to exist yet (the program will create the directory). The structure of the output directory will be a folder of subfolders, where each subfolder represents an original histology image, and within that subfolder will contain all the patches for the specified image.  
4. `TILE_SIZE` : [int] This is the length N of one side of the tile. The program assumes each tile is of size NxN.  
5. `WHITESPACE_CUTOFF` : [0,1] This is a percentage of whitespace that you will allow for any given tile. If you want to accept all tiles, input `0`. Otherwise input a value between `0` and `1` (default: `0.35`). Note that there also can exist whitespace within your sample.  
