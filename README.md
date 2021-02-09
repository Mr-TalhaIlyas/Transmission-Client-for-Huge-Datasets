# Transmission Client for Huge Datasets

This goes through the steps regarding how you can download the large datastes (> 200GB) from torrents.
You can use [Transmission](https://www.transmissionbt.com/) torrent client which supports all major operating systems:


## From the command line

For downloading from the command line you can use ctorrent locally or when connected over ssh to a server. To install ctorrent run:

```
$ sudo apt-get install ctorrent  ## for Ubuntu/Debian
$ sudo yum install ctorrent      ## for Fedora/Red Hat
$ brew install ctorrent          ## for Mac OSX
```

### Example

To use ctorrent you first need to download the .torrent file of the file/files that you want. You can do this using wget from the command line:
```
$ wget http://academictorrents.com/download/30ac2ef27829b1b5a7d0644097f55f335ca5241b.torrent
```
Then specify this .torrent when running ctorrent. The files will be downloaded as they are displayed on the technical tab of the details page
```
$ ctorrent 30ac2ef27829b1b5a7d0644097f55f335ca5241b.torrent
```
## Python

This [repo](https://github.com/academictorrents/at-python) is an implementation of the BitTorrent protocol written in Python and downloadable as a pip module.

### Installation

```
pip install academictorrents
```
### Example

```python
# Import the library
import academictorrents as at

# Download the data (or verify existing data)
filename = at.get("323a0048d87ca79b68f12a6350a57776b6a3b7fb")

# Then work with the data
import pickle, gzip
import sys, os, time

mnist = gzip.open(filename, 'rb')
train_set, valid_set, test_set = pickle.load(mnist, encoding='latin1')
mnist.close()
```
