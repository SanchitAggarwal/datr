# datr
Download image sets from flickr -> create your own training set for machine learning tasks etc.


## Usage
1. ```git clone https://github.com/peerdavid/datr/```
2. Register on flickr and create an application: https://www.flickr.com/services/apps/create/apply/
3. Copy the new API_Key and API_SECRET.
4. Create a file .datr in your home directory (into the cloned dir) with the following content:<br>
```
[Settings]
API_KEY =  YOUR_KEY
API_SECRET = YOUR_SECRET
```
5. cd INSTALLATION_PATH
6. python setup.py install --user
7. Use datr in your own application with:
``` python
import datr

path = "downloads"
search_tag = "car"
datr.download(path, search_tag)
```

## Execute directly
It is also possible, to call *python datr.py*:
```
Usage: datr.py [options]

Options:
  -h, --help            show this help message and exit
  -s SEARCH_TAGS, --search_tags=SEARCH_TAGS
                        A comma-delimited list of tags. Photos with one or
                        moreof the tags listed will be returned. You can
                        exclude results that match a term by prepending itwith
                        a - character.
  -t NUM_THREADS, --num_threads=NUM_THREADS
                        Number of downloader threads (speed up download)
  -p PATH, --path=PATH  Path where downloaded files should be saved
  -n MAX_NUM_IMG, --num_images=MAX_NUM_IMG
                        Max. number of images to download
  -l LICENSE, --license=LICENSE
                        License of images. 0=All Rights Reserved,
                        4=Attribution License, 6=Attribution-NoDerivs License,
                        3=Attribution-NonCommercial-NoDerivs License, 2
                        =Attribution-NonCommercial License, 1=Attribution-
                        NonCommercial-ShareAlike License, 5=Attribution-
                        ShareAlike License, 7=No known copyright restrictions,
                        8=United States Government Work, 9=Public Domain
                        Dedication (CC0) 10=Public Domain Mark
```

### Example
The following command will download 50 (Public Domain Dedication (CC0) license) images tagged with 'car'. 
To speed up the download we start 20 downloader threads.<br>

```
user@ubuntu:~/Dev/datr$ python datr.py --num_images 50 --search_tags cat --license 9 --num_threads 20
#############################################
Authenticate user on flickr.
Downloading images for search tags cat and license .
Filled downloader queue with 500 tagged images.                        

#############################################
Starting 20 downloader threads
  Downloading images ... 100%
Finished image download after 37.45 sec.
Successfully downloaded 500 images.


```

## Thanks to
https://github.com/alexis-mignon/python-flickr-api
