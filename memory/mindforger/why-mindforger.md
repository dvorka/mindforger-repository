# Why MindForger? <!-- Metadata: type: Outline; tags: important; created: 2018-02-23 10:56:27; reads: 24; read: 2018-05-29 22:44:37; revision: 19; modified: 2018-05-29 22:44:37; importance: 0/5; urgency: 0/5; -->

This document describes driving principles and vision for MindForger.

Are you drowning in information, but starving for **knowledge**? Where do you 
keep your **private remarks** like ideas, personal plans, gift tips, how-tos, 
dreams, business vision, finance strategy, auto  coaching notes? Loads of 
documents, sketches and remarks spread around the file system, cloud, 
web and Post-it notes? Are you affraid of your knowledge **privacy**? Are you 
able to **find** then once you create them? Do you know how are they mutually
**related** when you read or write them? No?

MindForger is **human mind** inspired **knowledge management tool** which
aims to connect the tradition of outline editors with emerging technologies. 
Its mission is to help you in organization of your knowledge and associated 
local, web and real world resources in a way that enables quick navigation, 
concise representation, automatic interconnections, associative completion 
and inferencing.
# Motivation <!-- Metadata: type: Note; created: 2018-02-23 10:56:27; reads: 15; read: 2018-03-31 08:58:16; revision: 2; modified: 2018-03-31 08:58:16; -->
MindForger is **human mind** inspired **personal** knowledge management tool:

* **Personal**
    * MindFoger enables you to **own your data** - it's meant to store your 
      personal ideas, remarks, notes and plans in a [secure](#secure) way.
	* MindForger enables **privacy** and **security** of your knowledge.
    * MindForger doesn't compete with tools for sharing information like
      Wikis - its purpose is to maintain your **private** data.

* **Knowledge**
    * MindForger focus is put on knowledge management - efficient storage and
      lookup of your thoughts, ideas, how-tos, etc.

* **Human mind**
    * MindForger [mimics human mind](./human-mind-inspiration.md) in order to 
	  achieve **synergy** between your mind and MindForger whenever you use 
	  it. MindForger aims to be your mind *extender* whenever you learn, search
	  or managege knowledge.
	  
* **Unique**
    * MindForger unique features start where editors and search engines end - it
      **thinks** as you search > browse > edit.
	* Once you **FIND** your remark, MindForger brings associations as you **READ**
	  (hyperlinks and ideas suggestions).
	* If you decide to **EDIT** your remarks, MindForger brings associations
	  as you WRITE (auto-completion, links, suggestions).

* **Tool**
    * MindForger is a desktop application running on Linux (Mac and Windows).



# Features <!-- Metadata: type: Note; created: 2018-02-23 10:56:27; reads: 23; read: 2018-04-10 10:58:57; revision: 5; modified: 2018-04-10 10:58:57; -->
MindForger features:

* **Open**
    * Any text editor - like Remarkable, Uncolored or Vim - can be used to edit outlines 
      in MindForger repository as it uses ([Markdown](http://daringfireball.net/projects/markdown/syntax)) format 
	  hosted DSL - which is well defined, documented and human friendly.

* **Free**
    * You don't pay for downloading and using MindForger.

* **Respects Privacy**
    * MindForger stores your data locally on your machine. It does **not** upload any of your data 
	  to the internet (cloud, server, ...). You may check it yourself as MindForger source code 
	  is available for free and thus it can be audited/verified by anybody.

* **Secure** <a name="secure"></a>
    * MindForger repository might be locally encrypted using any tool by user e.g. `encfs`.
    * If you want, your data (repository) can be transfered e.g. using SSH or Git@SSH to a remote 
	  private location (this action is not supported/performed by MindForger).

* **Search and Navigation**
    * MindForger does indexation on top of the data repository.
    * MindFoger index can be rebuilt at any time from a repository content.

* **Analysis**
    * Git repository with text based outlines can be easily analyzed with variety of tools
      [SW for text analysis, mining and analytics](http://www.predictiveanalyticstoday.com/top-free-software-for-text-analysis-text-mining-text-analytics/).

* **Instant Availability**
    * If your prefer to use MindForger for a team work, then there are a number of options
	  that differ in security, privacy and availability.
    * Offline via a secure cloud storage (like local Git repository) on Linux, Mac, Windows,
      Android and iOS.
    * Online via Git repository hosted by a service of your choice - like GitHub or
      BitBucket - allowing you to access repository (and even edit text and markdown
      files) using Linux/Windows/Mac machines and Android/iOS devices.

* **Synchronization**
    * Data can be synchronized among all your devices - workstations, laptops and 
      mobiles/tablets - in a variety of way: 
        * Linux: Git, Google Drive, Dropbox, ...
        * Windows: Git, Google Drive, Dropbox, ...
        * Android: MGit, AGit, ...

* **Performance**
   * Even big Markdowns (like [CPP Guidelines](https://github.com/isocpp/CppCoreGuidelines) with ~2500 sections) 
     are parsed and indexed quickly and can be edited and viewed w/o problems.

* **Efficiency**
    * Command line efficiency in GUI as well as CLI (O~S like CLI).

* **Sharing**
    * Whole repository as well as individual outline(s) can be shared just by sending particular 
	  file(s)/archive as they are stored in open format.
    * If you want to share just certain private date, then you can leverage a Git repository
      to share it with others via a remote (private) repository.

* **Backup**
    * MindForger can create compressed archive w/ your data that can be easily stored as backup.
    * If you are fine with using a remote (private) repository, you can use
      any CMS or cloud drive to push your data for backup (even to multiple 
      locations).
