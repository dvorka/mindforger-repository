# Windows Build and Distribution <!-- Metadata: type: Outline; tags: developer; created: 2019-01-13 08:57:31; reads: 252; read: 2019-02-08 00:16:08; revision: 252; modified: 2019-02-08 00:16:08; importance: 0/5; urgency: 0/5; -->
MindForger IDE, build and distribution on Windows. 

Release checklist:

* [ ] credits for Saman and/or Bonitoo
* [ ] licenses for all libraries and code (snippets) included in MindForger repository
* [ ] user doc: installation
* [ ] user doc: build
* [ ] developer doc: polished developer doc w/ migration details and decisions

# Plan '19/1 <!-- Metadata: type: Note; created: 2019-01-13 09:10:13; reads: 26; read: 2019-02-07 21:51:14; revision: 18; modified: 2019-01-13 11:15:01; -->

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
* [ ] Win **installer** (possibly Qt based)
* [ ] make MF real Win app:
    * keyboard shortcuts which follow Windows conventions
    * desktop integration which start associated app for opened attachments 
      (PDF, GIF, ...)
## User feedback <!-- Metadata: type: Note; created: 2019-01-13 09:21:14; reads: 25; read: 2019-02-07 23:18:43; revision: 5; modified: 2019-01-13 09:21:35; -->
Get **pre-release** user feedback:

* https://github.com/dvorka/mindforger/issues/632

### Building <!-- Metadata: type: Note; created: 2019-01-13 11:15:01; reads: 45; read: 2019-02-08 00:12:50; revision: 6; modified: 2019-02-07 21:52:36; -->
Install prerequisites:

* [Microsoft Visual Studio](https://visualstudio.microsoft.com/downloads/) (Community Edition suffices), during installation add with C++ support (todo: detailed info or screenshot)
    * or [Windows 10 SDK] (untested)(https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk) 
* Qt
    * Download [Qt for Windows](https://www.qt.io/download) - Open Source
    * During installation select:
      * Qt->Qt 5.12.x->MSVC 2017 64-bit
      * Qt-> Qt WebEngine
* Zlib
    * Dowload [Zlib 1.2.3 developer files for Windows](http://gnuwin32.sourceforge.net/downlinks/zlib-lib-zip.php)
    * Unpack content to `c:\libs\zlib`
    * (Temporary) Patch `c:\libs\zlib\include\zconf.h`

```
      289,294c289,291
      < #  if not defined(WINDOWS) && not defined(WIN32)
      < #    include <unistd.h>    /* for SEEK_* and off_t */
      < #    ifdef VMS
      < #      include <unixio.h>   /* for off_t */
      < #    endif
      < #    define z_off_t off_t
      ---
      > #  include <unistd.h>    /* for SEEK_* and off_t */
      > #  ifdef VMS
      > #    include <unixio.h>   /* for off_t */
      295a293
      > #  define z_off_t off_t
```

* Download [Zlib 1.2.3 64-bit DLL files](http://www.winimage.com/zLibDll/zlib123dllx64.zip)
* Unpack `\dll_x64\zlibwapi.*` to  `c:\libs\zlib\lib`
    
Build:

* Checkout Mindforger
* Start Qt creator
* Open project `$GIT\mindforger\mindforger.pro`
       ```
    * Download [Zlib 1.2.3 64-bit DLL files](http://www.winimage.com/zLibDll/zlib123dllx64.zip)
    * Unpack `\dll_x64\zlibwapi.*` to  `c:\libs\zlib\lib`
* Install [cmake](https://github.com/Kitware/CMake/releases/download/v3.13.4/cmake-3.13.4-win64-x64.msi)
    
Build:

* Checkout Mindforger
    * `git clone https://github.com/dvorka/mindforger.git`
    * `git checkout dev/1.49.0-win`
    * Check zlib path in the `app\app.pro` and the `lib\lib.pro`. It's absolute path, relative to pro file location. Current path counts with mindforger repo on the 2nd level, eg. `c:\git\mindforger`.
* Build cmark
    * `cd mindforger`
    * `git submodule init`
    * `git supmodule update`
    * `cd deps\cmark-gfm`
    * `mkdir build`
    * `cd build`
    * `cmake -G "Visual Studio 15 2017 Win64" -DCMAKE_CONFIGURATION_TYPES=Debug;Release -DCMARK_TESTS=OFF -DCMARK_SHARED=OFF ..` 
    * `cmake --build . --config Release -- /m`
* Build mindforger
    * `cd $GIT\mindforger`
    * Setup dev env in cmd line
        * `"C:\software\Qt\5.12.0\msvc2017_64\bin\qtenv2.bat"`
        * `"C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`
    * `qmake -r mindforger.pro`
    * `nmake`
    * result exe is in the `app\release` folder
      

Build from QtCreator and Debuging 

* Start Qt creator
* Open project `$GIT\mindforger\mindforger.pro`
    * Enable **Desktop Qt 5.xx MSVC2017 64bit** build
    * Set the **Build Directory** to `$GIT\mindforger`
* Build MSVC 2017 64-bit
* For setting debugger in QtCreator follow instructions in Qt documention [Setting Up Debugger](http://doc.qt.io/qtcreator/creator-debugger-engines.htm)
* CDB is part for Windows SDK. If you have only Visual Studio, it must be installed additionaly. Download [Windows 10 SDK](https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk) and select `Debugging Tools for Windows` only. 

  
Running:

* Manual run outside of QtCreator requires adding Qt libraries and Zlib libraries to _PATH_. 

Creating installer:

* Install [Inno Setup 5](http://www.jrsoftware.org/download.php/is-unicode.exe)
* `cd $GIT\mindforger`
* `"C:\software\Qt\5.12.0\msvc2017_64\bin\qtenv2.bat"`
* `windeployqt app\release\mindforger.exe  --dir app\release\bin --no-compiler-runtime`
* `"c:\Program Files (x86)\Inno Setup 5\ISCC.exe" /Qp build\windows\installer\mindforger-setup.iss`
* the result is in the `app\release\installer` folder

# Installation <!-- Metadata: type: Note; created: 2019-02-03 17:11:28; reads: 29; read: 2019-02-07 23:48:33; revision: 5; modified: 2019-02-03 17:11:44; -->
Installation documentation draft.
## Build on Windows <!-- Metadata: type: Note; created: 2019-02-03 17:11:52; reads: 100; read: 2019-02-08 00:16:08; revision: 90; modified: 2019-02-08 00:16:08; -->
_This is documentation draft written as I do it on clean system._

Build on [Microsoft Windows](https://www.microsoft.com/en-us/windows).

Install build tools:

* Install [Microsoft Visual Studio IDE Community](https://visualstudio.microsoft.com/downloads/) edition.
    * Choose `Desktop development with C++` in installer.
* Install [Qt and Qt Creator IDE](https://www.qt.io/download)
    * Qt version should be `Qt 5.9.5` (corresponds to Qt shipped with Ubuntu 18.04) or newer
    * Choose `Qt > Qt 5.9.5 > QMSVC 2017 64-bit`
    * Choose `Qt > Qt 5.9.5 > Qt WebEngine`
    * Choose `Qt > Developer and Designer tools > Qt Creator`
* Install `cmake`
* Install `patch`

Get MindForger [source code](https://github.com/dvorka/mindforger):

```
# 1. create and change to git directory
C: | cd \ | mkdir git | cd git
# 2. clone MindForger repository
git clone https://github.com/dvorka/mindforger.git
# 3. update repository sub-modules
cd mindforger
git submodule init
git submodule update
```

Install dependencies:

* Zlib 1.2.3
    * Download [ZLib developer files for Windows](http://gnuwin32.sourceforge.net/downlinks/zlib-lib-zip.php)
    * Unpack content to `C:\libs\zlib`
    * Patch `C:\libs\zlib\include\zconf.h`
        * **PROBLEM**: for example: `git apply --unsafe-paths`
    * Download [Zlib 64-bit DLL files](http://www.winimage.com/zLibDll/zlib123dllx64.zip)
    * Unpack `dll_x64\zlibwapi.*` to  `C:\libs\zlib\lib`

Build dependencies:

* `cmark-gfm` build:

```
cd git/mindforger/deps/cmark-gfm
mkdir build                                                                                                                                                                                                      
cd build                                                                                                                                                                                                         
cmake -G "Visual Studio 15 2017 Win64" -DCMAKE_CONFIGURATION_TYPES=Debug;Release -DCMARK_TESTS=OFF -DCMARK_SHARED=OFF ..
cmake --build . --config Release -- /m
```

Build MindForger:

...

Install:

...

Run:

...
