# Installation <!-- Metadata: type: Outline; tags: basics; created: 2018-03-20 16:19:07; reads: 280; read: 2018-05-29 11:38:35; revision: 280; modified: 2018-05-29 11:38:35; importance: 0/5; urgency: 0/5; -->

*Table of Contents*

* [Build from Source Code](#build-from-source-code)
* [Install a package](#install-package)
# Build from source code <!-- Metadata: type: Note; created: 2018-03-20 16:19:07; reads: 22; read: 2018-04-25 17:11:28; revision: 2; modified: 2018-04-25 17:11:28; -->
Build MindForger from source code.
## Build on Ubuntu <!-- Metadata: type: Note; created: 2018-03-20 16:19:07; reads: 73; read: 2018-05-17 09:45:38; revision: 39; modified: 2018-05-17 09:45:38; -->
Build MindForger on Ubuntu 14.04 or later.

Install build tools:

```sh
sudo apt-get install build-essential libqt5webkit5-dev qttools5-dev-tools qt5-default ccache
```

Get source code:

```
# clone MindForger repository
git clone https://github.com/dvorka/mindforger.git
# update repository sub-modules
git submodule init
git submodule update
```

Build dependencies:

```
# build Discount
cd deps/discount
./configure.sh
make
```

Compile and install:

```sh
qmake -r mindforger.pro
# consider speeding up compilation by increasing the number of CPU cores to use e.g. make -j8
make
sudo make install
```

Install documentation and stencils:

```
# clone MindForger documentation repository to home directory (location and directory name matters)
cd ~
git clone https://github.com/dvorka/mindforger-repository.git

# verify MindForger repository installation
ls mindforger-repository
  limbo  memory  mind  stencils
```

Run MindForger:

```
mindforger
```
## Build on Debian<!-- Metadata: type: Note; created: 2018-04-25 17:18:23; reads: 42; read: 2018-05-17 09:46:11; revision: 11; modified: 2018-05-17 09:46:11; -->
Build MindForger on Debian Stretch or later.

Install build tools:

```sh
sudo apt-get install build-essential libqt5webkit5-dev qttools5-dev-tools qt5-default ccache
```

Get source code:

```
# clone MindForger repository
git clone https://github.com/dvorka/mindforger.git
# update repository sub-modules
git submodule init
git submodule update
```

Build dependencies:

```
# build Discount
cd deps/discount
./configure.sh
make
```

Compile and install:

```sh
qmake -r mindforger.pro
# consider speeding up compilation by increasing the number of CPU cores to use e.g. make -j8
make
sudo make install
```

Install documentation and stencils:

```
# clone MindForger documentation repository to home directory (location and directory name matters)
cd ~
git clone https://github.com/dvorka/mindforger-repository.git

# verify MindForger repository installation
ls mindforger-repository
  limbo  memory  mind  stencils
```

Run MindForger:

```
mindforger
```
## Build on Fedora <!-- Metadata: type: Note; created: 2018-04-26 09:04:14; reads: 30; read: 2018-05-17 09:46:43; revision: 11; modified: 2018-05-17 09:46:43; -->
Build MindForger on Fedora.

Install build tools:

```sh
sudo dnf install qt-devel qt5-devel ccache
```

Get source code:

```
# clone MindForger repository
git clone https://github.com/dvorka/mindforger.git
# update repository sub-modules                                            
git submodule init
git submodule update
```

Build dependencies:

```
# build Discount
cd deps/discount
./configure.sh
make
```

Compile and install:

```sh
qmake-qt5 -r mindforger.pro
# consider speeding up compilation by increasing the number of CPU cores to use e.g. make -j8
make
sudo make install
```

Install documentation and stencils:

```
# clone MindForger documentation repository to home directory (location and directory name matters)
cd ~
git clone https://github.com/dvorka/mindforger-repository.git

# verify MindForger repository installation
ls mindforger-repository
  limbo  memory  mind  stencils
```

Run MindForger:

```
mindforger
```
# Install a package <!-- Metadata: type: Note; created: 2018-04-24 14:32:49; reads: 14; read: 2018-05-29 11:38:26; revision: 6; modified: 2018-05-29 11:38:26; -->
Install MindForger using a package.
## Ubuntu <!-- Metadata: type: Note; created: 2018-04-23 20:47:41; reads: 44; read: 2018-05-17 09:46:57; revision: 20; modified: 2018-05-17 09:46:57; -->
Install MindForger from **PPA**.
Add [my Lauchpad hosted PPA](https://launchpad.net/~ultradvorka/+archive/ubuntu/productivity) and install MindForger:

```
# add PPA to trusted repositories
sudo add-apt-repository ppa:ultradvorka/productivity

# update sources
sudo apt update

# install MindForger
sudo apt install mindforger
```
## Debian <!-- Metadata: type: Note; created: 2018-04-25 17:04:57; reads: 27; read: 2018-05-17 09:47:13; revision: 16; modified: 2018-05-17 09:47:13; -->
Install MindForger from **PPA**.
Add [my PPA](http://www.mindforger.com/debian), trust [GPG key](http://www.mindforger.com/gpgpubkey.txt) and 
install MindForger:

```
# add PPA to APT sources:
sudo echo -e "\ndeb http://www.mindforger.com/debian stretch main" >> /etc/apt/sources.list

# import PPA's GPG key
wget -qO - http://www.mindforger.com/gpgpubkey.txt | sudo apt-key add -

# update sources
sudo apt update

# install MindForger
sudo apt install mindforger
```

See also http://www.mindforger.com/debian/
## Fedora <!-- Metadata: type: Note; created: 2018-04-25 19:50:19; reads: 24; read: 2018-05-17 09:47:19; revision: 19; modified: 2018-05-17 09:47:19; -->
Install MindForger on Fedora (tested on FC 27):

* [download RPM](https://github.com/dvorka/mindforger/releases) from GitHub releases

Install RPM:

```
sudo dnf install mindforger-MAJOR.MINOR.REVISION.rpm
```
