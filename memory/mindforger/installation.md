# Installation <!-- Metadata: type: Outline; tags: basics; created: 2018-03-20 16:19:07; reads: 389; read: 2018-06-05 08:11:45; revision: 389; modified: 2018-06-05 08:11:45; importance: 0/5; urgency: 0/5; -->

*Table of Contents*

* [Build from Source Code](#build-from-source-code)
* [Install a package](#install-package)
# Build from source code <!-- Metadata: type: Note; created: 2018-03-20 16:19:07; reads: 26; read: 2018-06-05 08:07:51; revision: 5; modified: 2018-06-05 08:07:51; -->
Build MindForger from source code:

* [build on Ubuntu](#build-on-ubuntu)
* [build on Debian](#build-on-debian)
* [build on Fedora](#build-on-fedora)
* [build on macOS](#build-on-macos)
## Build on Ubuntu <!-- Metadata: type: Note; created: 2018-03-20 16:19:07; reads: 82; read: 2018-06-05 08:11:28; revision: 42; modified: 2018-06-05 08:11:28; -->
Build MindForger on Ubuntu 16.04 or later.

Install build tools:

```sh
sudo apt-get install build-essential zlib1g-dev libqt5webkit5-dev qttools5-dev-tools qt5-default ccache
```

Get [source code](https://github.com/dvorka/mindforger):

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

Compile and install from Git repository root directory:

```sh
qmake -r mindforger.pro
# consider speeding up compilation by increasing the number of CPU cores to use e.g. make -j8
make
sudo make install
```

Install [documentation and stencils](https://github.com/dvorka/mindforger-repository):

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
## Build on Debian <!-- Metadata: type: Note; created: 2018-04-25 17:18:23; reads: 50; read: 2018-06-05 08:11:36; revision: 13; modified: 2018-06-05 08:11:36; -->
Build MindForger on Debian Stretch or later.

Install build tools:

```sh
sudo apt-get install build-essential zlib1g-dev libqt5webkit5-dev qttools5-dev-tools qt5-default ccache
```

Get [source code](https://github.com/dvorka/mindforger):

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

Compile and install from Git repository root directory:

```sh
qmake -r mindforger.pro
# consider speeding up compilation by increasing the number of CPU cores to use e.g. make -j8
make
sudo make install
```

Install [documentation and stencils](https://github.com/dvorka/mindforger-repository):

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
## Build on Fedora <!-- Metadata: type: Note; created: 2018-04-26 09:04:14; reads: 42; read: 2018-06-05 08:11:45; revision: 13; modified: 2018-06-05 08:11:45; -->
Build MindForger on Fedora.

Install build tools:

```sh
sudo dnf install zlib-devel qt-devel qt5-devel ccache
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

Compile and install from Git repository root directory:

```sh
qmake-qt5 -r mindforger.pro
# consider speeding up compilation by increasing the number of CPU cores to use e.g. make -j8
make
sudo make install
```

Install [documentation and stencils](https://github.com/dvorka/mindforger-repository):

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
## Build on macOS <!-- Metadata: type: Note; tags: experimental,unstable; created: 2018-06-04 21:07:57; reads: 48; read: 2018-06-05 08:11:16; revision: 44; modified: 2018-06-05 08:11:16; -->
Build MindForger on macOS Sierra 10.12+.

Open `Terminal` and install [Xcode](https://developer.apple.com/) command line tools:

```sh
xcode-select --install
```

Install [Homebrew](https://brew.sh) package manager:

```sh
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew doctor
```

Install build tools and dependencies:

```sh
brew install ccache qt
```

Add them to `PATH` (if they already not present):

```sh
# add newly installed deps to path
echo 'export PATH="/usr/local/bin:$PATH"' >> ~/.bashr_profile
echo 'export PATH="/usr/local/opt/qt/bin:$PATH"' >> ~/.bashr_profile

# apply changes
. ~/.bash_profile
```

Get [source code](https://github.com/dvorka/mindforger):

```sh
git clone https://github.com/dvorka/mindforger.git
git submodule init
git submodule update
```

Build dependencies:

```sh
# build Discount
cd mindforger/deps/discount
./configure.sh
make
```

Compile MindForger from Git repository root directory:

```sh
qmake -r mindforger.pro
# consider adding -j parameter with the number of CPU cores to use e.g. make -j 8
make
```

Optionally install MindForger:

```
cd app && cp -rvf mindforger.app /Applications
```

Install [documentation and stencils](https://github.com/dvorka/mindforger-repository):

```
# clone MindForger documentation repository to home directory - location and directory name matters
cd ~
git clone https://github.com/dvorka/mindforger-repository.git

# verify MindForger repository installation
ls ~/mindforger-repository
  limbo  memory  mind  stencils
```

Run MindForger either as application or using command line:

```
/Applications/mindforger.app/contents/MacOS/mindforger
```
# Install a package <!-- Metadata: type: Note; created: 2018-04-24 14:32:49; reads: 17; read: 2018-06-05 08:08:32; revision: 7; modified: 2018-06-05 08:08:32; -->
Install MindForger using a package:

* [Ubuntu](#ubuntu)
* [Debian](#debian)
* [Fedora](#fedora)
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
