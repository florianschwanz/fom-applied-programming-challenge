# Applied Programming Coding Challenge #2

## Approach #1 DCGAN with Pokemon sprites

* [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/florianschwanz/fom-applied-programming-challenge/blob/master/notebooks/challenge-2-pokemon-sprites.ipynb)

The GAN contained in the [Jupyter notebook](./notebooks/challenge-2-pokemon-sprites.ipynb) creates new images based
 on 151 pixelated Pokemon sprites. 

### Data

* Raw data for this GAN can be found in [./data/pokemon-sprites/raw](./data/pokemon-sprites/raw) or downloaded using
 the following functions which are contained in the notebook but commented.
 
 ```python
import urllib.request

try:
  from google.colab import drive
  IN_COLAB = True
except:
  IN_COLAB = False

if IN_COLAB:
    drive.mount('/content/gdrive')
    dataroot_parent = "/content/gdrive/My Drive/Colab Files"
else:
    dataroot_parent = ".."

dataroot = dataroot_parent + "/data/pokemon-sprites"

def download_file(url, file_name):
    """Downloads a file from a given URL using to arbitrary headers"""
    
    hdr = {'User-Agent': 'Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.11 (KHTML, like Gecko) Chrome/23.0.1271.64 Safari/537.11',
       'Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8',
       'Accept-Charset': 'ISO-8859-1,utf-8;q=0.7,*;q=0.3',
       'Accept-Ecolor_channelsoding': 'none',
       'Accept-Language': 'en-US,en;q=0.8',
       'Connection': 'keep-alive'}
    req = urllib.request.Request(url, headers=hdr)
    response = urllib.request.urlopen(req)
    
    # Write response to file
    with open(file_name, mode="wb") as d:
        d.write(response.read())

def download_sprites_151():
    """Download sprites of original pokemon from alexonsager.net"""
    
    pokemon_count = 151
    for i in range(1, pokemon_count+1):
        url = "https://images.alexonsager.net/pokemon/" + str(i) + ".png"
        file_name = dataroot + "/raw/" + str(i).zfill(3) + ".png"
        download_file(url, file_name)
```

## Approach #2 DCGAN with Pokemon sprites + augmented fused images

* [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/florianschwanz/fom-applied-programming-challenge/blob/master/notebooks/challenge-2-pokemon-sprites-fused.ipynb)

The GAN contained in the [Jupyter notebook](./notebooks/challenge-2-pokemon-sprites.ipynb) creates new images based
 on 151 pixelated Pokemon sprites + fused versions resulting in 22801 images in total.
 
### Data

* Raw data for this GAN can be found in [./data/pokemon-sprites-fused/raw](./data/pokemon-sprites-fused/raw) or
 downloaded using the following functions which are contained in the notebook but commented.
 
 ```python
import urllib.request

try:
  from google.colab import drive
  IN_COLAB = True
except:
  IN_COLAB = False

if IN_COLAB:
    drive.mount('/content/gdrive')
    dataroot_parent = "/content/gdrive/My Drive/Colab Files"
else:
    dataroot_parent = ".."

dataroot = dataroot_parent + "/data/pokemon-sprites"

def download_file(url, file_name):
    """Downloads a file from a given URL using to arbitrary headers"""
    
    hdr = {'User-Agent': 'Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.11 (KHTML, like Gecko) Chrome/23.0.1271.64 Safari/537.11',
       'Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8',
       'Accept-Charset': 'ISO-8859-1,utf-8;q=0.7,*;q=0.3',
       'Accept-Ecolor_channelsoding': 'none',
       'Accept-Language': 'en-US,en;q=0.8',
       'Connection': 'keep-alive'}
    req = urllib.request.Request(url, headers=hdr)
    response = urllib.request.urlopen(req)
    
    # Write response to file
    with open(file_name, mode="wb") as d:
        d.write(response.read())

#%%

        
def download_sprites_fused_151():
    """Download sprites of fused pokemon from alexonsager.net"""
    
    pokemon_count = 151
    for i in range(1, pokemon_count+1):
        for j in range(1, pokemon_count+1):
            url = "https://images.alexonsager.net/pokemon/fused/" + str(i) + "/" + str(i) + "." + str(j) + ".png"
            file_name = dataroot + "/raw/" + str(i).zfill(3) + "_" + str(j).zfill(3) + ".png"
            download_file(url, file_name)
```

## Approach #2 DCGAN with Pokemon images

* [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/florianschwanz/fom-applied-programming-challenge/blob/master/notebooks/challenge-2-pokemon-images-simple.ipynb)

The GAN contained in the [Jupyter notebook](./notebooks/challenge-2-pokemon-images.ipynb) creates new images based
 on 801 Pokemon images.
 
 ### Data

* Raw data for this GAN can be found in [./data/pokemon-images-jpg/raw](./data/pokemon-images-jpg/raw).
 