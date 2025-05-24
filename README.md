Furcadia Technical Resources (FTR)
===================================================================================================

Overview
-------------------------------------------------------------------------------
FTR is an effort at documenting Furcadia, its file formats, protocols and other
resources, started around 2004. This project aims to help 3rd party developers,
as well as Furcadia staff and volunteers, with technical knowledge of the
entire system. It is a trove of info sourced primarily from the public domain,
official sources and reverse-engineering efforts by myself and others - for the
benefit of other Furcadians.

> **NOTICE**
> 
> This project starts with the basic knowledge from somewhere around 2009!
> Since then there were a bunch of changes that makes some of this information
> incomplete and/or outdated! Please bear with me while I try to update it
> piece by piece with whatever time I can muster these days.


Basic Info
-------------------------------------------------------------------------------
* [Furcadia Installation Paths]


Concepts
-------------------------------------------------------------------------------
* [Dynamic Avatars]
* [Furcadia Color Palette]
* [Furcadia Integer Encoding](concepts/Furcadia%20Integer%20Encoding.md) - #base95 and #base220 encoding
* [Furcadia Isometric Grid]


Protocols & Services
------------------------------------------------------------------------------
* [Commands](Commands.md)
* [Connection & Authentication] - logging into Furcadia over a raw TCP session
* [File Server Protocol]
* [Furcadia Client Connection Sequence]
* [Game Server Protocol]
* [Pounce Service]


File Formats
-------------------------------------------------------------------------------

| Ext.                    | Format                            | Comment                                                                                           |
| ----------------------- | --------------------------------- | ------------------------------------------------------------------------------------------------- |
| [DSB](formats/DSB.md)   | DragonSpeak Binary Data File      | Strictly numeric DS instructions                                                                  |
| [FBJ](formats/FBJ.md)   | Furcadia Object Properties File   | Additional FSH/FS2 properties                                                                     |
| [FCPT](formats/FCPT.md) | Furcadia Cached Portrait Data     | Cached portrait graphics                                                                          |
| [FOX](formats/FOX.md)   | Furcadia Objects Extended Format  | Successor format to FSH/FS2 since 0.26<br>(see [026_fox_format.pdf](official/026_fox_format.pdf)) |
| [FPRT](formats/FPRT.md) | Furcadia Portrait Data            | Portrait graphics & properties                                                                    |
| [FS2](formats/FS2.md)   | Furcadia Shape File v2            | Successor format to FSH                                                                           |
| [FSH](formats/FSH.md)   | Furcadia Shape File               | Graphical resources (objects, tiles, ...)                                                         |
| [HOWL](formats/HOWL.md) | File Cache (Horus)                | Cache format for portraits and other files                                                        |
| [MAP](formats/MAP.md)   | Furcadia Map (Dream)              | Assigns graphical objects to isometric grid                                                       |
| [RCH](formats/RCH.md)   | Furcadia Container/Archive        | Used to transfer dream-related files                                                              |
| [RCH2](formats/RCH2.md) | Furcadia Installer Container      | Used as a container inside Furcadia Installer                                                     |
| [TXB](formats/TXB.md)   | DragonSpeak Text File             | Contains text portion of a DSB file                                                               |


Other Files
-------------------------------------------------------------------------------

| Filename                                  | Description                                             |
| ----------------------------------------- | ------------------------------------------------------- |
| [images.howl](files/images.howl.md)       | Image cache ([HOWL](formats/HOWL.md) format)            |
| [localdir.ini](files/localdir.ini)        | Data path configuration - Furcadia on removable devices |
| [online.ini](files/online.ini.md)         | Pounce data file                                        |
| [portraits.howl](files/portraits.howl.md) | Portrait cache ([HOWL](formats/HOWL.md) format)         |


Obsolete File Formats
-------------------------------------------------------------------------------

| Ext.  | Format                    |
| ----- | ------------------------- |
| [CHC] | Portrait Cache Data File  |
| [CHP] | Portrait Cache Index File |


Official Documentation
-------------------------------------------------------------------------------
Documentation files written by sanctimonious and published by DEP at https://dev.furcadia.com/docs/.

| File                                                            | Date       | Title                                                                          |
| --------------------------------------------------------------- | ---------- | ------------------------------------------------------------------------------ |
| [third_party_proxies.html](official/third_party_proxies.html)   | 2005-10-25 | Recommendations for Furcadia Third<br>party Proxies and Other Similar Software |
| [base220.pdf](official/base220.pdf)                             | 2007-03-20 | Furcadia Base 220 Encoding                                                     |
| [023_file_hierarchy.pdf](official/023_file_hierarchy.pdf)       | 2007-03-20 | Update 023 File Hierarchy                                                      |
| [023_new_movement_v1.pdf](official/023_new_movement_v1.pdf)     | 2007-03-20 | Update 023 Avatar Movement v1                                                  |
| [new_color_code_format.pdf](official/new_color_code_format.pdf) | 2007-08-11 | Furcadia Color Code Format                                                     |
| [023_new_movement_v2.pdf](official/023_new_movement_v2.pdf)     | 2007-12-28 | Update 023 Avatar Movement v2                                                  |
| [023_new_tags.pdf](official/023_new_tags.pdf)                   | 2007-03-20 | Update 023 New FML Tags                                                        |
| [026_recoloring.pdf](official/026_recoloring.pdf)               | 2008-10-31 | Furcadia Re-coloring Layer                                                     |
| [026_attachment_points.pdf](official/026_attachment_points.pdf) | 2008-11-15 | Furcadia Attachment Points                                                     |
| [026_fox_format.pdf](official/026_fox_format.pdf)               | 2008-11-15 | Furcadia FOX File Format                                                       |
| [026_recolor_assistant.png](official/026_recolor_assistant.png) | *unknown*  | Recoloring Assistance Cheat Sheet                                              |
| [027_movement.html](official/027_movement.html)                 | *unknown*  | Update 027 Avatar Movement                                                     |


Cookbooks
-------------------------------------------------------------------------------
* [Shortcut - GNOME](cookbooks/Shortcut%20-%20GNOME.md) - creating a Furcadia shortcut in GNOME (Linux)
* [Furcadia on Cloud Storage] - multi-device access and sync via [Dropbox](https://dropbox.com), [Tresorit](https://tresorit.com), or other cloud provider


Tools & Software
-------------------------------------------------------------------------------
* [Numeric Conversion Tool](https://ftr.icerealm.org/ref-numeric) - JavaScript base95/base220 conversion tool
* [Ezoa's Resource Content Handler Archiver](https://ezoa.page/projects/ERCHA/) (ERCHA) - RCH packer/unpacker
	* [GitHub Project](https://github.com/ezoa-page/ERCHA)


Software Development Libraries
-------------------------------------------------------------------------------
* [libfurc](https://github.com/FelixWolf/libfurc) - Python library for Furcadia by [Félix Wolf](https://github.com/FelixWolf)


Resources
-------------------------------------------------------------------------------
* [Furcadia Development Center](https://dev.furcadia.com/docs/) - provides official documentation files
* [Furcadia Community Forums](https://forums.furcadia.com) (decommissioned)
	* [Related Links](https://forums.furcadia.com/index.php?showtopic=22593) (Third Party Development) - 3rd party projects & resources
