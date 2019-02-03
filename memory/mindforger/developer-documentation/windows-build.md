# Windows Build and Distribution <!-- Metadata: type: Outline; tags: developer; created: 2019-01-13 08:57:31; reads: 136; read: 2019-02-03 19:01:40; revision: 136; modified: 2019-02-03 19:01:40; importance: 0/5; urgency: 0/5; -->
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

* [ ] **development environment**:
    * document IDE, compiler and OS setup - QtCreator, LLVM (would be nice), Win10 (VM)
* [ ] **backend lib build**:
    * rewrite using Qt to portable version (Qt is NOT intentionally used in backend now)
    * decide whether...
        * go with Qt functions on all platforms
        * conditional compilation which introduces Qt dependency for Win only
    * https://github.com/dvorka/mindforger/issues/77
* [ ] (preview) **frontend build** to identify non-portable code:
    * skip MD 2 HTML rendering (avoid its compilation) w/
      `html_outline_representation.cpp` and `MF_NO_MD_2_HTML` define
    * skip HTML rendering (avoid its compilation)
    * https://github.com/dvorka/mindforger/issues/648
* [ ] **MD 2 HTML rendering**:
    * refactor existing impl to iface & implementation allowing to switch renderer  
    * migrate to `cmark-GFM` library ~ GitHub's MD 2 HTML renderer
* [ ] HTML **viewer**: 
    * Qt uses the same engine as on macOS (WebEngine vs. WebKit)
* [ ] **full build** w/ lib, `cmark-GFM` and HTML viewer 
* [ ] Win **installer** (possibly Qt based)
* [ ] make MF real Win app:
    * keyboard shortcuts which follow Windows conventions
    * desktop integration which start associated app for opened attachments 
      (PDF, GIF, ...)
## User feedback <!-- Metadata: type: Note; created: 2019-01-13 09:21:14; reads: 15; read: 2019-02-03 17:10:13; revision: 5; modified: 2019-01-13 09:21:35; -->
Get **pre-release** user feedback:

* https://github.com/dvorka/mindforger/issues/632

### Building <!-- Metadata: type: Note; created: 2019-01-13 11:15:01; reads: 15; read: 2019-02-03 17:36:00; revision: 4; modified: 2019-02-02 12:38:40; -->
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
    * Enable **Desktop Qt 5.xx MSVC2017 64bit** build
    * Set the **Build Directory** to `$GIT\mindforger\build-mindforger-debug` for the **Debug** configuration and `$GIT\mindforger\build-mindforger-release` for the **Release** configuration 
    * Check zlib path in the `app.pro` and the `lib.pro`. It's absolute path, relative to pro file location. Current path counts with mindforger repo on the 2nd level, eg. `c:\git\mindforger`.
* Build MSVC 2017 64-bit
* For debugging mindforger follow instructions in Qt documention [Setting Up Debugger](http://doc.qt.io/qtcreator/creator-debugger-engines.htm) 
    * CDB is part for Windows SDK. If you have only Visual Studio, it must be installed additionaly. Download [Windows 10 SDK](https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk) and select `Debugging Tools for Windows` only. 
  
Running:

* Click _Run_ from QtCreator
* Manual run outside of QtCreator requires adding Qt libraries and Zlib libraries to _PATH_. 
# Installation <!-- Metadata: type: Note; created: 2019-02-03 17:11:28; reads: 9; read: 2019-02-03 17:36:00; revision: 5; modified: 2019-02-03 17:11:44; -->
Installation documentation draft.
## Build on Windows <!-- Metadata: type: Note; created: 2019-02-03 17:11:52; reads: 34; read: 2019-02-03 19:01:40; revision: 34; modified: 2019-02-03 19:01:40; -->
_This is documentation draft written as I do it on clean system_

Build on [Microsoft Windows](https://www.microsoft.com/en-us/windows).

Install build tools:

* Install [Microsoft Visual Studio IDE Community](https://visualstudio.microsoft.com/downloads/) edition.
    * Choose `Desktop development with C++` in installer.
* Install [Qt and Qt Creator IDE](https://www.qt.io/download)
    * Choose `Qt 5.9.5` (corresponds to Ubuntu 18.04 Qt version)
    * Choose `Qt Installer Framework 3.0`
    * Choose `MinGW 7.3.0 64-bit`

Install dependencies:

* Install Zlib 1.2.3
    * Download [developer files for Windows](http://gnuwin32.sourceforge.net/downlinks/zlib-lib-zip.php)
    * Download [DLLs](http://www.winimage.com/zLibDll/zlib123dllx64.zip)

Get source code:

* https://github.com/dvorka/mindforger

Build dependencies:

...

Build MindForger:

...

Install:

...

Run:

...
