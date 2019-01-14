# Windows Build and Distribution <!-- Metadata: type: Outline; tags: developer; created: 2019-01-13 08:57:31; reads: 54; read: 2019-01-13 11:15:01; revision: 54; modified: 2019-01-13 11:15:01; importance: 0/5; urgency: 0/5; -->
MindForger IDE, build and distribution on Windows. 
# Plan '19/1 <!-- Metadata: type: Note; created: 2019-01-13 09:10:13; reads: 22; read: 2019-01-13 11:15:01; revision: 18; modified: 2019-01-13 11:15:01; -->
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
## User feedback <!-- Metadata: type: Note; created: 2019-01-13 09:21:14; reads: 9; read: 2019-01-13 09:22:37; revision: 5; modified: 2019-01-13 09:21:35; -->
Get **pre-release** user feedback:

* https://github.com/dvorka/mindforger/issues/632
