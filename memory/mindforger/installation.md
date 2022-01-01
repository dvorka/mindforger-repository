# Installation <!-- Metadata: type: Outline; tags: basics; created: 2018-03-20 16:19:07; reads: 1213; read: 2021-12-31 10:23:19; revision: 1213; modified: 2021-12-31 10:23:19; importance: 3/5; urgency: 3/5; -->
Install:

* [Windows](#windows-)
* [Ubuntu](#ubuntu-)
* [Debian](#debian-)
* [Fedora](#fedora-)
* [openSUSE](#opensuse-)
* [Arch Linux](#arch-linux-)
* [macOS](#macos-)
* [WSL](#wsl-)

Build:

* [build on Windows](#build-on-windows-)
* [build on Ubuntu](#build-on-ubuntu-)
* [build on Debian](#build-on-debian-)
* [build on Fedora](#build-on-fedora-)
* [build on macOS](#build-on-macos-)
* [build on WSL](#build-on-wsl-)

Docker:

* [build and run container](#build-and-run-in-container-)

Tarball:

* [download tarball](https://github.com/dvorka/mindforger/releases)

> _Unfortunately links above must have trailing '-' to workaround GitHub MD to HTML rendering bug. Therefore these links are broken in Markdown editors (including MF)._
# Install a package <!-- Metadata: type: Note; created: 2018-04-24 14:32:49; reads: 57; read: 2021-12-31 10:08:23; revision: 18; modified: 2018-09-22 11:30:41; -->
Install MindForger using a package.

## macOS <!-- Metadata: type: Note; tags: macos; created: 2018-06-12 19:47:21; reads: 72; read: 2021-12-31 10:09:00; revision: 13; modified: 2021-12-31 10:09:00; -->
Install MindForger on macOS either using `brew` or by downloading `.dmg`.

**Homebrew**

Install MindForger using [HomeBrew](https://brew.sh):

```
brew install mindforger
```

**Disk iMaGe**

Install MindForger using `.dmg`:

* [download .dmg](https://github.com/dvorka/mindforger/releases) from [GitHub releases](https://github.com/dvorka/mindforger/releases)

Install `.dmg`:

* Open/mount `.dmg`
* Drag and drop/copy `mindforger` from `.dmg` to `Applications`
* Run `MindForger`

MindForger creates copy of the documentation in your home directory (`~/mindforger-repository`) and opens it as default repository.
## Windows <!-- Metadata: type: Note; tags: windows; created: 2019-02-16 09:43:18; reads: 44; read: 2021-12-31 10:09:35; revision: 6; modified: 2020-03-08 17:03:09; -->
Install MindForger using installer.

* Download installer executable from https://github.com/dvorka/mindforger/releases (or try [nightly build](https://ci.appveyor.com/project/dvorka/mindforger/build/artifacts))
* Run installer.

## WSL <!-- Metadata: type: Note; tags: windows; created: 2018-07-11 15:40:38; reads: 69; read: 2021-12-31 10:09:35; revision: 9; modified: 2020-03-08 17:03:04; -->
Install [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install-win10) (WSL) and check that you have Ubuntu 16.04 or newer:

```
lsb_release -a
  ...
  Release:        16.04
  Codename:       xenial
```
If not, then run `sudo do-release-upgrade`.

Install and start an X server for Windows like [Xming](https://sourceforge.net/projects/xming/).

---

Install MindForger from PPA. Add [my PPA](http://www.mindforger.com/debian) to Apt, trust [GPG key](http://www.mindforger.com/gpgpubkey.txt),
install MindForger and run it:

```sh
# add PPA to trusted repositories
sudo add-apt-repository ppa:ultradvorka/productivity

# update sources
sudo apt update

# install MindForger
sudo apt install mindforger

# run MindForger
DISPLAY=:0.0 mindforger
```
## Ubuntu <!-- Metadata: type: Note; tags: linux; created: 2018-04-23 20:47:41; reads: 99; read: 2021-12-31 10:09:35; revision: 21; modified: 2020-03-08 17:02:23; -->
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
## Debian <!-- Metadata: type: Note; tags: linux; created: 2018-04-25 17:04:57; reads: 79; read: 2021-12-31 10:09:35; revision: 18; modified: 2020-03-08 17:02:28; -->
Install MindForger on [Debian](https://www.debian.org/) from **PPA**.
Add [my PPA](http://www.mindforger.com/debian), trust [GPG key](http://www.mindforger.com/gpgpubkey.txt) and 
install MindForger:

```bash
# add PPA to APT sources:
sudo bash -c 'echo -e "\ndeb https://www.mindforger.com/debian stretch main" > /etc/apt/sources.list.d/mindforger.list'

# import PPA's GPG key
wget -qO - http://www.mindforger.com/gpgpubkey.txt | sudo apt-key add -

# update sources
sudo apt update

# install MindForger
sudo apt install mindforger
```

See also http://www.mindforger.com/debian/
## Fedora <!-- Metadata: type: Note; tags: linux; created: 2018-04-25 19:50:19; reads: 100; read: 2021-12-31 10:09:36; revision: 22; modified: 2020-03-08 17:02:33; -->
Install MindForger on [Fedora](https://getfedora.org/):

* [download RPM](https://github.com/dvorka/mindforger/releases) from GitHub releases

Install RPM:

```
sudo dnf install mindforger-MAJOR.MINOR.REVISION.rpm
```

## openSUSE <!-- Metadata: type: Note; tags: linux; created: 2020-01-21 08:08:06; reads: 55; read: 2021-12-31 10:09:36; revision: 5; modified: 2020-03-08 17:02:38; -->
Install MindForger on [openSUSE](https://www.opensuse.org/):

```
sudo zypper in opi
opi mindforger
```


## Arch Linux <!-- Metadata: type: Note; tags: linux; created: 2018-06-12 19:47:21; reads: 57; read: 2021-12-31 10:09:36; revision: 8; modified: 2020-03-08 17:02:45; -->
Install MindForger from Arch User Repository (AUR):

* https://aur.archlinux.org/packages/mindforger/

# Build from source code <!-- Metadata: type: Note; created: 2018-03-20 16:19:07; reads: 83; read: 2021-12-31 10:09:36; revision: 7; modified: 2018-09-22 11:30:51; -->
Build MindForger from source code.
## Build on macOS <!-- Metadata: type: Note; tags: macos; created: 2018-06-04 21:07:57; reads: 135; read: 2021-12-31 10:23:19; revision: 135; modified: 2021-12-31 10:23:19; -->
Build MindForger on macOS Sierra 10.12+.

Open `Terminal` and install/update [Xcode](https://developer.apple.com/) command line tools:

```sh
xcode-select --install
```

Install/update [HomeBrew](https://brew.sh) package manager:

```sh
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew doctor
```

Install build tools and dependencies:

```sh
brew install ccache
```

Download Qt from https://www.qt.io/download and in its online installer choose:

* `Qt/Qt 5.x.x`
    * latest available `5.x.x` (`Qt 5.9.9` or any newer Qt relese)
    * you can skip components like `Android` or `iOS` 
* `Developer and Designer Tools`
    * `Qt Creator`
    * `qmake`
    * `CMake`
    * `Qt Installer Framework`

Once Qt is installed you can use `~/Qt/MaintennanceTool.app` to add/remove Qt components.

Get [source code](https://github.com/dvorka/mindforger):

```sh
git clone https://github.com/dvorka/mindforger.git
git submodule init
git submodule update
```

There are two ways how to **build** MindForger Disk iMaGe package:

1. either using **scripts** from MindForger's GitHub repository:
    * `build/macos/mindforger-build.sh` which creates MindForger executable
    * `build/macos/dmg-package-build.sh` which creates Disk iMaGe `.dmg` package on top of binary executable build made by `mindforger-build.sh`
1. or using the **steps described below**

Add dependencies to `PATH`:

* fix paths: username, Qt and its components versions might be different
* add `PATH` modifications below to your `.bash_profile` and/or `.bashrc`
  or `.zshrc` depending on your shell (configuration)
* don't forget to apply changes e.g. using `. .bashr_profile`

```sh
# clang
export PATH="/Users/username/Qt/5.14.1/clang_64/bin:${PATH}"
# cmake
export PATH="${PATH}:/Users/username/Qt/Tools/CMake/CMake.app/Contents/bin"
# installer
export PATH="${PATH}:/Users/username/Qt/Tools/QtInstallerFramework/3.2/bin"
```

Get [source code](https://github.com/dvorka/mindforger):

```sh
git clone https://github.com/dvorka/mindforger.git
git submodule init
git submodule update
```

You don't have to build dependencies - like `cmark-gfm` or `hunspell` - as they are
built by `qmake`.

Compile MindForger from its Git repository **root** directory:

```sh
qmake -r mindforger.pro
# consider adding -j parameter with the number of CPU cores to use e.g. make -j 8
make
```

Optionally install MindForger:

```sh
cd app && cp -rvf mindforger.app /Applications
```

Install [documentation and stencils](https://github.com/dvorka/mindforger-repository):

```sh
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

---

Qt Creator **development environment** setup:

* start `Qt Creator` as application
* open project `mindforger.pro`
* configure project: `clang` kit, `debug` and `release` profiles
* menu `Build/Run qmake`
* menu `Build/Build all`
* menu `Build/Run`

Build `.dmg` **distribution**:

* start **terminal** session
* change to `mindforger/build/macos`
* run `build/macos/dmg-package-build.sh`
* check `.dmg` distro created in `mindforger/app/mindforger.dmg`
## Build on Windows <!-- Metadata: type: Note; tags: windows; created: 2019-02-03 17:11:52; reads: 152; read: 2021-12-22 20:04:22; revision: 124; modified: 2020-03-08 17:03:27; -->
Build MindForger on [Microsoft Windows](https://www.microsoft.com/en-us/windows).

Install build **tools**:

* Install [Microsoft Visual Studio IDE Community](https://visualstudio.microsoft.com/downloads/) edition.
    * Choose `Desktop development with C++` in installer.
* Install [Qt and Qt Creator IDE](https://www.qt.io/download)
    * Qt version - choose **latest** `5.x.x` Qt release available (must be `Qt 5.9.5` or newer, suggested `Qt 5.12.0` or newer)
    * Choose `Qt > Qt 5.x.x > QMSVC 2017 64-bit`
    * Choose `Qt > Qt 5.x.x > Qt WebEngine`
    * Choose `Qt > Developer and Designer tools > Qt Creator`
* Install `cmake`
* Install `patch`

Get MindForger **source code** [GitHub](https://github.com/dvorka/mindforger):

* Create directory where you want to build MindForger e.g.
  `C:\Users\USER\mindforger-build`
  
```
# create and change to build directory
C: | cd %HOMEPATH% | mkdir mindforger-build | cd mindforger-build
# clone MindForger repository
git clone https://github.com/dvorka/mindforger.git
# update repository sub-modules
cd mindforger
git submodule init
git submodule update
```

* MindForger sources can be found in 
  `C:\Users\USER\mindforger-build\mindforger`

Build **dependencies**:

* build `cmark-gfm`: 

```
cd deps\cmark-gfm
mkdir build                                                                                                                                                                                                      
cd build                                                                                                                                                                                                         
cmake -G "Visual Studio 15 2017 Win64" -DCMAKE_CONFIGURATION_TYPES=Debug;Release -DCMARK_TESTS=OFF -DCMARK_SHARED=OFF ..
cmake --build . --config Release -- /m
```

Get default MindForger repository - **documentation and examples** (will be loaded on the first start):

```
# change to home directory
C: | cd %HOMEPATH%
# clone MindForger documentation
git clone https://github.com/dvorka/mindforger-repository.git
```

**Build** MindForger in Qt Creator:

1. Start Qt Creator
2. Open MindForger project:
    * `Welcome/Open project`
    * Choose `C:\Users\USER\mindforger-build\mindforger\mindforger.pro` as project file.
3. Choose kit:
    * `Desktop Qt 5.x.x MSVC2017 64bit`
4. Set build directory:
    * Set left toolbar's `Projects/Build Settings/Build directory` to `C:\Users\USER\mindforger-build\mindforger`
5. Set build configuration:
    * Set `Projects/Build Settings/Edit build configuration` choose `Release`
6. Build:
    * Menu `Build/Build All`

**Run** MindForger from Qt Creator:

* Menu `Build\Run`

Create **installer**:

* Install [JRSoftware](http://www.jrsoftware.org) [Inno Setup 5](http://www.jrsoftware.org/download.php/is-unicode.exe)
* Prepare development environment. Change path according to your Qt installation
    * Run `%QT_HOME%\5.x.x\msvc2017_64\bin\qtenv2.bat`
* Gather dependencies
    * `cd C:\Users\USER\mindforger-build\mindforger`
    * `%QT_HOME%\5.x.x\msvc2017_64\bin\windeployqt app\release\mindforger.exe  --dir app\release\bin --no-compiler-runtime`
* Build installer - **update** path to `vcredist_x64.exe` in the command below according to your setup:
    * `cd C:\Users\USER\mindforger-build\mindforger`
    * `"C:\Program Files (x86)\Inno Setup 5\ISCC.exe" /Qp /DVcRedistPath="c:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Redist\MSVC\14.16.27012\vcredist_x64.exe" build\windows\installer\mindforger-setup.iss` 
* MindForger **installer** can be found in `app\release\installer` folder.

To create **debug** version of MindForger and executable replace `debug` with `release` in the steps above and 
use `mindforger-setup-debug.iss` installer configuration.

## Build on WSL <!-- Metadata: type: Note; tags: windows; created: 2018-07-10 10:20:59; reads: 65; read: 2021-12-22 20:04:22; revision: 15; modified: 2021-12-21 13:46:55; -->
Build MindForger on [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install-win10) (WSL).

Install build tools:

```sh
sudo apt-get install build-essential zlib1g-dev libhunspell-dev libqt5webkit5-dev qttools5-dev-tools qt5-default ccache
```

Update `gcc` and `g++` to version 5 (at least):

```sh
# adds the the test toolchain which includes gcc-5 and g++5 
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
sudo apt-get update
sudo apt-get install gcc-5 g++-5
# substitute gcc-5 for gcc and g++-5 for g++ (current version)
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-5 60 --slave /usr/bin/g++ g++ /usr/bin/g++-5
```

Get [source code](https://github.com/dvorka/mindforger):

```sh
# clone MindForger repository
git clone https://github.com/dvorka/mindforger.git
# update repository sub-modules
cd mindforger
git submodule init
git submodule update
```

Build dependencies:

```sh
# build cmark-gfm
cd mindforger/deps/cmark-gfm
mkdir build && cd build
cmake -DCMARK_TESTS=OFF -DCMARK_SHARED=OFF ..
cmake --build .
```

Compile and install from Git repository root directory:

```sh
qmake -r mindforger.pro
# consider speeding up compilation by increasing the number of CPU cores to use e.g. make -j8
make
sudo make install
```

Install [documentation and stencils](https://github.com/dvorka/mindforger-repository):

```sh
# clone MindForger documentation repository to home directory (location and directory name matters)
cd ~
git clone https://github.com/dvorka/mindforger-repository.git

# verify MindForger repository installation
ls mindforger-repository
  limbo  memory  mind  stencils
```

Run MindForger and start your XServer for Windows (e.g. [Xming](https://sourceforge.net/projects/xming/))

```sh
DISPLAY=:0.0 ./mindforger
```

## Build on Ubuntu <!-- Metadata: type: Note; tags: linux; created: 2018-03-20 16:19:07; reads: 162; read: 2021-12-22 20:04:22; revision: 60; modified: 2021-12-17 23:31:25; -->
Build MindForger on Ubuntu 16.04 or later.

Install build tools:

```sh
sudo apt-get install build-essential zlib1g-dev libhunspell-dev libqt5webkit5-dev qttools5-dev-tools qt5-default ccache
```

Get [source code](https://github.com/dvorka/mindforger):

```sh
# clone MindForger repository
git clone https://github.com/dvorka/mindforger.git
# update repository sub-modules
cd mindforger
git submodule init
git submodule update
```

Build dependencies:

```sh
# build cmark-gfm
cd mindforger/deps/cmark-gfm
mkdir build && cd build
cmake -DCMARK_TESTS=OFF -DCMARK_SHARED=OFF ..
cmake --build .
```

Compile and install from Git repository root directory:

```sh
qmake -r mindforger.pro
# consider speeding up compilation by increasing the number of CPU cores to use e.g. make -j8
make
sudo make install
```

Install [documentation and stencils](https://github.com/dvorka/mindforger-repository):

```sh
# clone MindForger documentation repository to home directory (location and directory name matters)
cd ~
git clone https://github.com/dvorka/mindforger-repository.git

# verify MindForger repository installation
ls mindforger-repository
  limbo  memory  mind  stencils
```

Run MindForger:

```
./mindforger
```

See also `mindforger/build/ubuntu/build-all-clean-system.sh`
## Build on Debian <!-- Metadata: type: Note; tags: linux; created: 2018-04-25 17:18:23; reads: 93; read: 2021-12-22 20:04:22; revision: 22; modified: 2021-12-21 13:47:08; -->
Build MindForger on Debian Stretch or later.

Install build tools:

```sh
sudo apt-get install build-essential zlib1g-dev libhunspell-dev libqt5webkit5-dev qttools5-dev-tools qt5-default ccache
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

```sh
# build cmark-gfm
cd mindforger/deps/cmark-gfm
mkdir build && cd build
cmake -DCMARK_TESTS=OFF -DCMARK_SHARED=OFF ..
cmake --build .
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
./mindforger
```
## Build on Fedora <!-- Metadata: type: Note; tags: linux; created: 2018-04-26 09:04:14; reads: 86; read: 2021-12-22 20:04:22; revision: 25; modified: 2021-12-21 13:48:36; -->
Build MindForger on Fedora.

Install build tools:

```sh
sudo dnf install zlib-devel hunspell-devel qt-devel qt5-devel ccache
```

Get source code:

```sh
# clone MindForger repository
git clone https://github.com/dvorka/mindforger.git
# update repository sub-modules                                            
git submodule init
git submodule update
```

Build dependencies:

```sh
# build cmark-gfm
cd mindforger/deps/cmark-gfm
mkdir build && cd build
cmake -DCMARK_TESTS=OFF -DCMARK_SHARED=OFF ..
cmake --build .
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
./mindforger
```
# Docker <!-- Metadata: type: Note; created: 2018-09-23 13:45:53; reads: 26; read: 2021-12-22 20:04:22; revision: 5; modified: 2018-09-23 13:49:01; -->
Run MindForger in Docker container.
## Build and run in container <!-- Metadata: type: Note; tags: docker; created: 2018-09-23 13:46:37; reads: 79; read: 2021-12-22 20:04:22; revision: 60; modified: 2020-03-08 17:04:07; -->
Build [Docker](https://www.docker.com/) image and run MindForger in Docker container.

Build image:

```
mkdir mindforger

# download Dockerfile
curl https://raw.githubusercontent.com/dvorka/mindforger/master/build/docker/mindforger/Dockerfile > mindforger/Dockerfile

# build image
docker build -t mindforger:latest mindforger
```

Run container:

```
# allow access to X server (UNSECURE, but simple):
xhost +local:root

# run image
docker run -it --env="DISPLAY" --env="QT_X11_NO_MITSHM=1" \
    --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" mindforger:latest mindforger

# determine and remember container ID
docker ps -l -q > ~/.mindforger.docker
```

Run MindForger by starting container:

```
# start (stopped) container
docker start $(cat ~/.mindforger.docker)
```

Check also https://github.com/dvorka/mindforger/tree/master/build/docker for handy scripts.

# Spell check <!-- Metadata: type: Note; created: 2021-12-22 20:04:34; reads: 14; read: 2021-12-22 20:07:55; revision: 6; modified: 2021-12-22 20:07:55; -->
MindForger's **spell check** implementation is based on [Hunspell](https://github.com/hunspell/hunspell).
## Spell check configuration on Linux <!-- Metadata: type: Note; created: 2021-12-22 20:07:03; reads: 21; read: 2021-12-22 20:16:07; revision: 18; modified: 2021-12-22 20:16:07; -->
Install [Hunspell](https://github.com/hunspell/hunspell):

```
sudo apt install hunspell
```

Download **vocabulary** for your language from:

* https://extensions.openoffice.org/en/project/english-dictionaries-apache-openoffice

**Install** vocabulary:

* extract `.sox` archive downloaded from the URL above to get `.dict` and `.aff` files
* determine Hunspell's vocabulary search path by running:
```
hunspell -D
```
* copy downloaded (`.dict` and `.aff`) vocabulary files to one of 
  the directories on Hunspell's search path e.g. `/usr/share/hunspell`
## Spell check configuration on Windows <!-- Metadata: type: Note; created: 2021-12-22 20:07:15; reads: 14; read: 2021-12-23 07:57:32; revision: 14; modified: 2021-12-23 07:57:32; -->
[Hunspell](https://github.com/hunspell/hunspell) is included
in MindForger executable, therefore it does not have to be installed.

Download **vocabulary** for your language from:

* https://extensions.openoffice.org/en/project/english-dictionaries-apache-openoffice

**Install** vocabulary:

* extract `.sox` archive downloaded from the URL above to get `.dict` and `.aff` files
* copy downloaded (`.dict` and `.aff`) vocabulary files to one of 
  the directories on Hunspell's search path:
```
C:\Users\<profile>\dictionaries
C:\Users\<profile>\Local Settings\dictionaries
C:\Users\<profile>\AppData\Local\dictionaries
```
