# Windows Build and Distribution <!-- Metadata: type: Outline; tags: developer; created: 2019-01-13 08:57:31; reads: 177; read: 2019-02-16 09:22:50; revision: 177; modified: 2019-02-16 09:22:50; importance: 0/5; urgency: 0/5; -->
MindForger IDE, build and distribution on Windows. 

Release checklist:

* [ ] credits for Saman and/or Bonitoo
* [ ] licenses for all libraries and code (snippets) included in MindForger repository
* [ ] user doc: installation
* [ ] user doc: build
* [ ] developer doc: polished developer doc w/ migration details and decisions

# Plan '19/1 <!-- Metadata: type: Note; created: 2019-01-13 09:10:13; reads: 24; read: 2019-02-03 08:02:18; revision: 18; modified: 2019-01-13 11:15:01; -->

GitHub:

* milestone: https://github.com/dvorka/mindforger/milestone/10
* branch: https://github.com/dvorka/mindforger/tree/dev/1.49.0-win

Plan:

* [x] **development environment**:
    * document IDE, compiler and OS setup - QtCreator, LLVM (would be nice), Win10 (VM)
* [x] **backend lib build**:
    * rewrite using Qt to portable version (Qt is NOT intentionally used in backend now)
    * decide whether...
        * go with Qt functions on all platforms
        * conditional compilation which introduces Qt dependency for Win only
    * https://github.com/dvorka/mindforger/issues/77
* [x] (preview) **frontend build** to identify non-portable code:
    * skip MD 2 HTML rendering (avoid its compilation) w/
      `html_outline_representation.cpp` and `MF_NO_MD_2_HTML` define
    * skip HTML rendering (avoid its compilation)
    * https://github.com/dvorka/mindforger/issues/648
* [x] **MD 2 HTML rendering**:
    * refactor existing impl to iface & implementation allowing to switch renderer  
    * migrate to `cmark-GFM` library ~ GitHub's MD 2 HTML renderer
* [x] HTML **viewer**: 
    * Qt uses the same engine as on macOS (WebEngine vs. WebKit)
* [x] **full build** w/ lib, `cmark-GFM` and HTML viewer 
* [x] Win **installer** (possibly Qt based)
* [ ] make MF real Win app:
    * keyboard shortcuts which follow Windows conventions
    * desktop integration which start associated app for opened attachments 
      (PDF, GIF, ...)
## User feedback <!-- Metadata: type: Note; created: 2019-01-13 09:21:14; reads: 15; read: 2019-02-03 17:10:13; revision: 5; modified: 2019-01-13 09:21:35; -->
Get **pre-release** user feedback:

* https://github.com/dvorka/mindforger/issues/632

### Building <!-- Metadata: type: Note; created: 2019-01-13 11:15:01; reads: 15; read: 2019-02-03 17:36:00; revision: 4; modified: 2019-02-02 12:38:40; -->
...
#### Install prerequisites: <!-- Metadata: type: Note; created: 2019-02-06 08:26:14; reads: 3; read: 2019-02-16 08:07:22; revision: 1; modified: 2019-02-06 08:26:14; -->

* [Microsoft Visual Studio](https://visualstudio.microsoft.com/downloads/) (Community Edition suffices), during installation add with C++ support (todo: detailed info or screenshot)
    * or [Windows 10 SDK] (untested)(https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk) 
* Qt
    * Download [Qt for Windows](https://www.qt.io/download) - Open Source
    * During installation select:
      * Qt->Qt 5.12.x->MSVC 2017 64-bit
      * Qt-> Qt WebEngine
* [cmake](https://github.com/Kitware/CMake/releases/download/v3.13.4/cmake-3.13.4-win64-x64.msi)
    
   
 #### Prepare MindForger sources

  * Checkout Mindforger
    * `git clone https://github.com/dvorka/mindforger.git`
    * `cd mindforger`
    * `git checkout dev/1.49.0-win`
  * Init dependencies  
    * `git submodule init`
    * `git supmodule update`

#### Build dependencies <!-- Metadata: type: Note; created: 2019-02-06 08:26:14; reads: 11; read: 2019-02-16 09:10:23; revision: 1; modified: 2019-02-06 08:26:14; -->
Building dependecies is required only once, during initial building.

Build cmake-gfm: It requires cmake on the path.
  * Goto cmark-gfm
    * `cd deps\cmark-gfm`
  * Use build directory
    * `mkdir build`
    * `cd build`
  * Generate build files
    * `cmake -G "Visual Studio 15 2017 Win64" -DCMAKE_CONFIGURATION_TYPES=Debug;Release -DCMARK_TESTS=OFF -DCMARK_SHARED=OFF ..` 
  * Build both release and debug profiles
    * `cmake --build . --config Release -- /m`
    * `cmake --build . --config Debug -- /m`

#### Build MindForger <!-- Metadata: type: Note; created: 2019-02-06 08:26:14; reads: 7; read: 2019-02-16 08:08:18; revision: 1; modified: 2019-02-06 08:26:14; -->
  * Goto repo dir
    * `cd $GIT\mindforger`
  * Setup development environment in cmd line. Change path according to your MSVC 2017 and Qt installation
    * `"C:\software\Qt\5.12.0\msvc2017_64\bin\qtenv2.bat"`
    * `"C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`
  * Generate make files
    * `qmake -r mindforger.pro`
  * Build MindForger
    * `nmake`
  * result exe is in the `app\release` folder
      

#### Build from QtCreator and Debuging  <!-- Metadata: type: Note; created: 2019-02-06 08:26:14; reads: 3; read: 2019-02-16 08:07:28; revision: 1; modified: 2019-02-06 08:26:14; -->

  * Start Qt creator
  * Open project `$GIT\mindforger\mindforger.pro`
    * Enable **Desktop Qt 5.xx MSVC2017 64bit** build
    * Set the **Build Directory** to `$GIT\mindforger`
  * Build MSVC 2017 64-bit
  * For setting debugger in QtCreator follow instructions in Qt documention [Setting Up Debugger](http://doc.qt.io/qtcreator/creator-debugger-engines.htm)
    * CDB is part for Windows SDK. If you have only Visual Studio, it must be installed additionaly. Download [Windows 10 SDK](https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk) and select `Debugging Tools for Windows` only. 

  
#### Running MindForger <!-- Metadata: type: Note; created: 2019-02-06 08:26:14; reads: 1; read: 2019-02-06 08:26:14; revision: 1; modified: 2019-02-06 08:26:14; -->
* Manual run outside of QtCreator requires adding Qt libraries and Zlib libraries to _PATH_. Zlib binaries are located in `$GIT\mindforger\deps\zlib-win\ 
  * Qt files. Change path according to your setup
    * `"C:\software\Qt\5.12.0\msvc2017_64\bin\qtenv2.bat"`
  * Zlib
    * `set "PATH=%PATH%;$GIT\mindforger\deps\zlib-win"`
  * Start MindForger
    * `app\release\mindforger.exe`

#### Creating installer <!-- Metadata: type: Note; created: 2019-02-06 08:26:14; reads: 1; read: 2019-02-06 08:26:14; revision: 1; modified: 2019-02-06 08:26:14; -->
* Install [Inno Setup 5](http://www.jrsoftware.org/download.php/is-unicode.exe)
* Prepare development environment. Change path according to your Qt installation
  * `"C:\software\Qt\5.12.0\msvc2017_64\bin\qtenv2.bat"`
* Gather dependencies
  * `cd $GIT\mindforger`
  * `windeployqt app\release\mindforger.exe  --dir app\release\bin --no-compiler-runtime`
* Build installer. Change path to the _vcredist_x64.exe_ according to your setup. 
  * `"c:\Program Files (x86)\Inno Setup 5\ISCC.exe" /Qp /DVcRedistPath="c:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Redist\MSVC\14.14.26405\vcredist_x64.exe" build\windows\installer\mindforger-setup.iss` 
* the result is in the `app\release\installer` folder

#### Building unit tests <!-- Metadata: type: Note; created: 2019-02-06 08:26:14; reads: 1; read: 2019-02-06 08:26:14; revision: 1; modified: 2019-02-06 08:26:14; -->
Unit tests are conducted by the [gtest](https://github.com/google/googletest) framework. Download, build and optionally install this framework before building MindForger unit tests. 

Gtest is expected at `C:\Program Files\gtest-distribution` by default. If you have it somewhere else you have to update the `lib\test\src\src.pro` Qt project file to change path to gtest.

Than:
* Prepare development environment. Change path according to your Qt and MSVC 2017 installation
  * `"C:\software\Qt\5.12.0\msvc2017_64\bin\qtenv2.bat"`
  * `"C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`
* Go to project file
  * `cd $GIT\mindforger\lib\test`
* Generate make files
  * `qmake -r mindforger-lib-unit-tests.pro "CONFIG+=debug" "CONFIG+=mfdebug"` 
* Build tests
  * `nmake`

#### Running unit tests <!-- Metadata: type: Note; created: 2019-02-06 08:26:14; reads: 1; read: 2019-02-06 08:26:14; revision: 1; modified: 2019-02-06 08:26:14; -->
* Prepare environment
  * `set "PATH=%PATH%;$GIT\mindforger\deps\zlib-win"`
  * `set M8R_GIT_PATH=$GIT\mindforger`
* Run tests
  * `cd $GIT\mindforger`
  * `lib\test\src\debug\mindforger-lib-unit-tests.exe`


#### Using scripts <!-- Metadata: type: Note; created: 2019-02-06 08:26:14; reads: 1; read: 2019-02-06 08:26:14; revision: 1; modified: 2019-02-06 08:26:14; -->
Alternatively, instead using of following above described manual steps, you can take advantage of batch files prepared for building and running MindForger, installer and unit tests. All the scripts are located in the ` $GIT\mindforger\build` folder:
  * build-app.bat
  * build-cmake.bat
  * build-installer.bat
  * build-unit-tests.bat
  * env.bat
  * run-app.bat
  * run-unit-tests.bat

Most important is the `env.bat`. It's called by others and sets up command line environment. Ammend this file to change paths based on your setup. Other scripts are self-explanatory. The `run-unit-tests.bat` can also take any argument. This is usefull for passing options to the _gtest_ framework. 


# Installation <!-- Metadata: type: Note; created: 2019-02-03 17:11:28; reads: 11; read: 2019-02-06 08:25:19; revision: 5; modified: 2019-02-03 17:11:44; -->
Installation documentation draft.
## Build cmark on Linux <!-- Metadata: type: Note; created: 2019-02-16 08:08:14; reads: 18; read: 2019-02-16 09:22:50; revision: 17; modified: 2019-02-16 09:22:50; -->
Build `cmake-gfm`: 

```
cd mindforger/deps/cmark-gfm`
mkdir build
cd build

# generate build files
cmake -DCMARK_TESTS=OFF -DCMARK_SHARED=OFF ..
# build
cmake --build .
```
## Build on Windows <!-- Metadata: type: Note; created: 2019-02-03 17:11:52; reads: 46; read: 2019-02-16 09:10:11; revision: 38; modified: 2019-02-16 08:09:26; -->
_This is documentation draft written as I do it on clean system._

Build on [Microsoft Windows](https://www.microsoft.com/en-us/windows).

Install build tools:

* Install [Microsoft Visual Studio IDE Community](https://visualstudio.microsoft.com/downloads/) edition.
    * Choose `Desktop development with C++` in installer.
* Install [Qt and Qt Creator IDE](https://www.qt.io/download)
    * Choose `Qt 5.9.5` (corresponds to Ubuntu 18.04 Qt version)
    * Choose `Qt Installer Framework 3.0`
    * Choose `MinGW 7.3.0 64-bit`
    * **TODO: WebEngine (didn't notice the option)**

Install dependencies:

* Install Zlib 1.2.3
    * Download [developer files for Windows](http://gnuwin32.sourceforge.net/downlinks/zlib-lib-zip.php)
    * Download [DLLs](http://www.winimage.com/zLibDll/zlib123dllx64.zip)

Get source code:

* https://github.com/dvorka/mindforger

Build dependencies:

... cmark ...

Build MindForger:

...

Install:

...

Run:

...
