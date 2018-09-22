# MindForger Developer Documentation <!-- Metadata: type: Outline; created: 2018-02-23 10:56:27; reads: 290; read: 2018-07-10 10:07:09; revision: 290; modified: 2018-07-10 10:07:09; importance: 0/5; urgency: 0/5; -->

Contribute:

* [Source code](https://github.com/dvorka/mindforger)
* [Build](#development-environment)
* [Technical architecture](#technical-architecture)

Specifications:

* [Repository Structure](#repository-layout)
* [Outline Format - Markdown hosted DSL](#markdown-hosted-dsl)

In case that you have any question or want to learn more about technical details 
please don't hesitate to contact [me](mailto:martin.dvorak@mindforger.com).

# Development Environment <!-- Metadata: type: Note; created: 2018-03-18 08:58:55; reads: 111; read: 2018-04-01 08:09:28; revision: 71; modified: 2018-04-01 08:09:28; -->
Perhaps you may find useful description of my development environment:

* Backend library:
    * Source: GitHub
    * Compiler: GCC
    * Compilation speed-up: ccache (set in Eclipse/Qt creator as `ccache g++`)
    * Make: qmake + make
    * IDE: QtCreator (my own build w/ Emacs-style keyboard shortcuts - find it on GitHub)
    * Debugger: gdb
    * Leaks: valgrind
    * Profiler: GCC + gprof
    * Unit tests: Google Test Framework 

* Qt GUI frontend: 
    * Compiler: GCC
    * Make: qmake + make
    * IDE: QtCreator (my own build)
        * Tools/Options/Fonts: vim dark, 12pt, zoom: 100%
        * Whitespaces: no tabs, visible, no traling whitespaces
        * "Borland Turbo C style help" for Qt via F1
    * Debugger: 
        * QtCreator debugger
        * gdb
    * Unit tests: Sikulix
    * Editor: Emacs (quick edits w/ key bindings that enable my productivity)
        * set tabs for 4
        * no tabs just whitespaces
        * Alt-X compile > cd ../.. && make (make -k for keep going)

For more details see source code.
## Tests <!-- Metadata: type: Note; created: 2018-03-31 08:32:08; reads: 50; read: 2018-03-31 08:39:39; revision: 13; modified: 2018-03-31 08:39:39; -->
MindForger has:

* library unit tests
* frontend GUI tests

Library unit tests:

* based on [Google test framework](https://github.com/google/googletest)
* located in `lib/test/src`
* can be run using `build/test-lib-units.sh` - see source code for running all/particular
  test w/ or w/o valgrind/GDB/...

Frontend library tests:

* based on [Sikulix](http://sikulix.com/)
* located in `app/test/sikulix`
* can be run using `build/test-gui.sh`

For more details check tests source code.
## Benchmarks <!-- Metadata: type: Note; created: 2018-03-31 08:32:16; reads: 35; read: 2018-03-31 08:39:30; revision: 6; modified: 2018-03-31 08:39:30; -->
MindForger has also library benchmarks:

* based on [Google test framework](https://github.com/google/googletest)
* located in `lib/test/benchmark`
* can be run using `build/test-lib-units.sh` - see script source code to run particular benchark.

Benchmarks are *disabled* by default - go to benchmark source code and remove `DISABLED_` prefix
from its name. For more details see Google test framework documentation and benchmarks source code.
## Continuous Integration (CI) <!-- Metadata: type: Note; created: 2018-04-26 09:29:48; reads: 28; read: 2018-05-17 10:57:04; revision: 5; modified: 2018-05-17 10:57:04; -->
[Continous builds](https://travis-ci.org/dvorka/mindforger) via Travis CI, see also `.travis.yml`.
## Packaging <!-- Metadata: type: Note; created: 2018-04-26 09:33:46; reads: 14; read: 2018-04-26 09:39:04; revision: 2; modified: 2018-04-26 09:39:04; -->
Scripts used to created packages for Linux distributions can be found in:

* Ubuntu: `build/ubuntu`
    * tarball > local binary/source deb build (pbuilder) > Launchpad 
      upload > Launchpad PPA
* Debian: `build/debian`
    * tarball > local binary/source deb build > local Aptly PPA > PPA snapshot
      upload to http://www.mindforger.com/debian
* Fedora: `build/fedora`
    * deb > `alien` conversion w/ postprocessing to RPM > upload as release asset 

**Upstream tarball** is created in the same way as archive released via GitHub:

* GitHub release: `build/github`
## Branching Conventions <!-- Metadata: type: Note; created: 2018-06-02 07:05:00; reads: 8; read: 2018-06-04 11:12:22; revision: 5; modified: 2018-06-04 11:12:22; -->
Git branching naming convention:

* `fb/feature-name`
    * feature branch 
* `platform/platform-name`
    * platform support branch 
* `dev/1.42.0`
    * development branch used **before** release (stable master)
* `stabilization/1.42.0`
    * stable brach used **after** release (patch releases)
# Technical Architecture <!-- Metadata: type: Note; created: 2018-03-18 08:55:16; reads: 39; read: 2018-04-26 09:32:27; revision: 7; modified: 2018-04-26 09:32:27; -->
This section gives a brief summary of MindForger technical architecture highlights.
## Library <!-- Metadata: type: Note; tags: todo; created: 2018-03-18 08:57:10; reads: 36; read: 2018-05-30 07:33:03; revision: 3; modified: 2018-05-30 07:33:03; -->
...
### Markdown Recursive Descent Parser <!-- Metadata: type: Note; tags: todo; created: 2018-03-18 08:58:00; reads: 37; read: 2018-05-30 07:32:40; revision: 3; modified: 2018-05-30 07:32:40; -->
...
### NLP: Stemmer, Lexicon, BoW <!-- Metadata: type: Note; tags: todo; created: 2018-04-26 09:30:35; reads: 26; read: 2018-07-10 08:01:19; revision: 3; modified: 2018-07-10 08:01:19; -->
...
### Neural Network <!-- Metadata: type: Note; tags: todo; created: 2018-03-18 08:57:17; reads: 43; read: 2018-04-26 09:40:00; revision: 7; modified: 2018-04-26 09:40:00; -->
...
## GUI <!-- Metadata: type: Note; tags: todo; created: 2018-03-18 08:57:27; reads: 40; read: 2018-05-30 07:33:09; revision: 4; modified: 2018-05-30 07:33:09; -->
...
### Qt <!-- Metadata: type: Note; tags: todo; created: 2018-05-04 07:01:09; reads: 13; read: 2018-07-10 10:06:18; revision: 3; modified: 2018-07-10 10:06:18; -->
...
### Model View Presenter <!-- Metadata: type: Note; tags: todo; created: 2018-03-18 08:57:45; reads: 43; read: 2018-07-10 10:06:30; revision: 4; modified: 2018-07-10 10:06:30; -->
...
### Async UI Updates <!-- Metadata: type: Note; tags: todo; created: 2018-04-26 09:30:53; reads: 29; read: 2018-07-10 10:06:37; revision: 3; modified: 2018-07-10 10:06:37; -->
...
### Localization <!-- Metadata: type: Note; tags: todo; created: 2018-05-10 08:21:10; reads: 38; read: 2018-07-10 10:06:45; revision: 32; modified: 2018-07-10 10:06:45; -->
Adding a new/updating existing MindForger l10n:

* Add translation name to `app/app.pro`: `TRANSLATIONS += src/qt/translations/mindforger_en.ts`
* Run `lupdate mindforger.pro` - it will parse source code
  and prepare empty file for translations (later update). This is where is new translation
  written.
    * If `lupdate` is not present on Ubuntu, then install `sudo apt-get install qttools5-dev-tools`
* Edit translations using `linguist` tool.
* Run `lrelease app/app.pro` to release translations that might be used in build.
* Add translation `.qm` resource to `app/mf-resources.qrs`
* Build application.
* Test it: `export LANGUAGE=cs_CZ && export LANG=cs_CZ.UTF-8 && ./mindforger`

See also:

* http://doc.qt.io/qt-5/internationalization.html
* http://doc.qt.io/qt-5/qtlinguist-hellotr-example.html
### Force-driven Graph <!-- Metadata: type: Note; tags: todo; created: 2018-03-18 22:02:48; reads: 34; read: 2018-04-26 09:31:14; revision: 3; modified: 2018-04-26 09:31:14; -->
...
# Formats specification <!-- Metadata: type: Note; created: 2018-04-26 09:22:02; reads: 35; read: 2018-05-04 07:01:30; revision: 7; modified: 2018-05-04 07:01:30; -->
MindForger can open **any** file that uses Markdown format. MindForger
can also open **any** directory that contains Markdown files (also
in its sub-directories).

However, you can use MindForger's [Markdown hosted DSL](#markdown-hosted-dsl) and
[repository format](#repository-format) to get much more (mind related) features.
## Markdown hosted DSL <!-- Metadata: type: Note; tags: todo,review; created: 2018-01-03 15:37:23; reads: 52; read: 2018-07-10 10:07:03; revision: 13; modified: 2018-07-10 10:07:03; -->
This section describes MD conventions that MindForger uses to store outlines.

Description:

* **metadata** added by MindForger are optional
   * if user deletes metadata, then they are not added
   * user may activate creation of metadata by adding <!-- METADATA --> (any case) just after section title
   * `Metadata` keyword is case **insensitive** i.e. any other variant is valid substituation e.g. `metadata`, `MetaData`
     or `METADATA`
* **tags** chosen to follow typical naming e.g. GMail (labels, keywords, ... forbidden)

Example:

```
# Canonical Message Similarity Code <!-- metadata: revision: 3; timestamp: 2016/3/31 13:54.45; keywords: sv, matcher -->                

This document contains ideas related to the definition of similarity codes for
canonical messages.

## Requirements <!-- metadata: revision: 5; timestamp: 2016/3/31 13:54.45; category: IMPORTANT; type: note -->                

... here comes a text.
```
## Repository Layout <!-- Metadata: type: Note; tags: todo,review; created: 2018-01-03 15:37:23; reads: 39; read: 2018-07-10 10:07:09; revision: 19; modified: 2018-07-10 10:07:09; -->
Design goals:

* Repository specification SHOULD be general i.e. not bound to MindForger
  so that anybody can create it, use it and it won't be vendor specific.
* Repository format MUST be humand friendly i.e. easy to create and read
  for a normal person.

Repository layout:

```
[ROOT]/
  memory/
    [DIRECTORY-NAME]/
      [OUTLINE-NAME].md                 ... Markdown is default MF format. Source code/markup free text can be inlined
                                            using three back apostrophes. Intentionally there is no txt, TWiki, HTML
                                            as outline format to keep focus (txt/.../HTML can be an attachment of empty
                                            MD file).
      [OUTLINE-NAME].[ATTACH-NAME].png  ... '.' is reserved character
      [OUTLINE-NAME].[ATTACH-NAME].jpg
      [OUTLINE-NAME].[ATTACH-NAME].gif
    ...
  limbo/
  stencils/
    ...
  mind/                                 ... Git ignored directory w/ indexed knowledge base
    index.mf                            ... MF's index can be fully rebuilt from
                                            repository content (file internals and
                                            Git index information), it is used by
                                            MF runtime (navigation, ...)
    fts/                                ... Lucene stores its files to here  
      ...                                 
  .gitignore
  README.md                             ... MF generated info for nice Git repo
                                            that can be customized by user
```

Example repository:

```
ROOT/
  outlines/
    My Example/
      frontend-design.twiki
      frontend-design.mockup.jpg
      repository-design.md
      repository-design.overview.png
      repository-design.structure.png
      ideas.txt
  mind/
  .gitignore
  index
  README.md
```

Description:

* repository is Git repository
* .gitignore prevents storing of big attachments and indices to Git
* DIRECTORY-NAME ... A-Z a-z 0-9 SPACE - _
* OUTLINE-NAME   ... A-Z a-z 0-9 SPACE - _
* directory is outline *label* - name directories to be nice labels:
   * do NOT use plurals: 'templates' is not good label > use 'template' instead
   * user lower case for normal adjectives (template, import) and upper case for
     names like MindForger or Systinet
* MindForger home screen == cloud of is outline and/or note *labels* (split screen).
* Extensions:
   * files w/ extensions that are not explicitly enumerated are ignored by Git (global ignore)
