Getting Started Guide
=====================

The overview/tutorial video contains some slightly outdated information due to some screens changing but still provides good coverage of what to expect:

[![File Tracker Overview and Tutorial video](https://file-tracker.cubiclesoft.com/file_cache/18139/filetracker_overview_tutorial_video.920.png)](https://www.youtube.com/watch?v=1DSwPnEf308 "File Tracker Overview and Tutorial")

Installation
------------

To install the product, login to the [Product Support Center](https://file-tracker.cubiclesoft.com/product-support/) and download the latest version from there.

A current license of the software grants access to the installers for Windows, Mac OSX, and Linux.

During the first run of the software, it will ask for license information.  Enter the license information and save it.  After that, entering the Product Support Center in the future is as simple as clicking "Help/Support" from within File Tracker itself.

Available upgrades are automatically detected by File Tracker when it starts up.  To upgrade the software, visit the Product Support Center, download the update, then make sure File Tracker is completely stopped, and finally install the upgrade.

Configuration
-------------

After installation, the next step is to configure the scanner.  Under Edit Configuration, enter file paths on the local system to scan, set local version control environment variables, etc.

![File Tracker configuration](https://cubiclesoft.com/files/18093/filetracker_screenshot_edit_config.png)

For any remote SSH systems, set up SSH keys and connection profiles.  Each connection profile has configuration options similar to those found in Edit Configuration.  Be sure to click "Deploy Remote" to deploy the remote software to the host so that the scanner will function.

Under Manage Files, set up the first File Group.

![Managing file groups](https://cubiclesoft.com/files/18139/filetracker_screenshot_manage_files.png)

A file group is a collection of one or more files that are identical or nearly identical (e.g. a slightly different intro).  The goal of a file group is to keep all files within the group in relative sync with other files in the group and also predefines some things like a common commit message to use when File Tracker interacts with version control software.  A file group could consist of library files, support files, or even files spanning an entire application.  File groups can be differentiated by only including a file if it matches a specific string (e.g. the business name).

When using File Tracker for the first time, configuring just one File Group is recommended.

Workflow
--------

Once a File Group has been configured, File Tracker has a primary workflow cycle of:

* Find matching files (Synchronize)
* Adjust configuration as needed (Edit Configuration or Manage SSH Profiles)
* Adjust projects as needed (Manage Projects)
* Process files (Manage Files)
* Process commits and pushes (Manage Projects)
* Push out scheduled changes (Synchronize)

This workflow generally traverses the first three menu items and then back with rare stops at the configuration.

The first Synchronize operation is the slowest because it will most likely scan the entire directory tree.  After the first scan completes, take note of any "Slow paths" that were detected.  These are the paths of the directory tree that returned no file group matches but took the longest to scan.  If there are no future file groups down a particular part of the directory tree, then the paths can be added to the "Exclude Directories" list and the scanner will skip scanning that part of the directory structure during the next scan.  Many Synchronize system scans can generally be reduced from minutes to just a few seconds by adding some carefully selected exclusion paths.  Getting scan times reduced up front is worth the effort later on.

The Manage Projects portion of File Tracker allows for setting up automatic version control integration (git, svn, etc.) and grouping collections of files into logical projects.  Checking for files not assigned to a project is a good idea to do after every Synchronize operation.  Assign found files to projects before moving onto Manage Files.

Manage Files shows up to three major sections:

* Needs Processing
* Ready For Sync
* Nothing To Do

File Groups in the "Needs Processing" section appear there due to at least one of three different conditions:

* New files detected
* Removed files detected
* Maximum version count threshold for the File Group was exceeded

For the first scan, it is usually desireable to choose a specific file to move to the top of the list of files for the File Group.  For example, a library file might have a source project for that file.  Going into "Locations," locating the file, editing selecting "Options", setting "Move To Top" to "Yes", and then saving the configuration for the file.

File Tracker is actually a pseudo-merge tool.  Unlike traditional visual diff/merge tools, it's designed for making bulk changes, not one-offs.  In general, it will preserve the newline style of the target system for non-binary files (e.g. DOS/Windows vs. Linux line endings).  However, it can also preserve portions of files that it updates and/or apply string replacements.  These advanced features allow for near-identical copies of individual files within a File Group to be carefully preserved.

After adjusting per-file configurations in the files that are attached to the File Group, enter the "Process Diffs" section.  This section of File Tracker determines a file source, generates and shows diffs based on the file source, and determines the most plausible course of action to take by default.  However, every action can be manually overridden.  Also keep in mind that changes are not applied to any files until the next Synchronize operation takes place.

Once "Process Diffs" has been completed, the File Group will move to the "Ready For Sync" section.  Once all desired File Groups have been processed, return to Manage Projects.  Here, commits and pushes can be applied.  If all looks good, go to the bottom of the page and click the "Save" button.

The final step of the workflow is to return to the Synchronize screen and run a Synchronize operation.  All scheduled changes are made, commits and pushes to repositories are made, and a file scan is conducted.

The workflow should be repeated until all desired File Groups have reached the "Nothing To Do" state.  Note that setting a higher minimum unique version threshold may be required for some situations to get the File Group to change to the "Nothing To Do" state.

File Tracker leaves all changes in the hands of the user.  There is no one-size-fits-all solution that can be automated because, as you'll discover, each File Group has its own quirks that almost inevitably results in manual intervention on occasion.

Making Backups
--------------

It's always important to make good backups (e.g. the 3-2-1 rule).  Setting up File Tracker can represent a time investment of several hours.  Therefore, being able to preserve configuration, Project, and File Group settings when moving or restoring a system saves a lot of time.

Most backup software defaults to backing up and restoring the user's home directory.  This is, in general, good enough unless you are a software developer.  Software devs tend to do their own thing and not use the OS manufacturer-recommended per-user data storage mechanisms, especially on Windows.

The File Tracker SQLite database and configuration are stored at the following locations on various OSes:

* Windows - %LOCALAPPDATA%\CubicleSoft\File Tracker
* Mac OSX and Linux - %HOME%/.config/CubicleSoft/File Tracker

Be sure to add the relevant path to your backup software.
