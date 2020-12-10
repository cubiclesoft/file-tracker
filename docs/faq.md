Frequently Asked Questions
==========================

The following are a series of frequently asked questions and the answers to those questions grouped by category.

Pre-Purchase
------------

*What is File Tracker?*

If you've ever used [Beyond Compare](https://www.scootersoftware.com/) or [Meld](https://meldmerge.org/) or [KDiff3](http://kdiff3.sourceforge.net/), then you know what those tools are capable of...and their obvious limitations.

File Tracker is a bulk visual diff/merge tool.  It performs visual diff/merges with one source file to many destination files.  It can modify thousands of files, massively commit and push to upstream version control repositories, and synchronize changes across SSH hosts.  Any file in a collection of files (known as a File Group within File Tracker) can be chosen as the "source file," which defaults to the most recently modified version of a file to save time selecting the source file.  It also has a very fast system scanner with support for scanning and updating remote systems over SSH.

*Who is this product for?*

File Tracker is for any software developer or development team that manages common code shared across multiple projects.  Where "multiple projects" is a minimum of around 20 projects.

Let's say a specific file contains a security vulnerability.  The first step is to patch the library where that file is used.  The next step is to deploy the patched library to all locations where the library is used.  However, to safely upgrade an application with the patched file, the existing file needs to be compared to make sure that updating the file won't cause the application to break.  Repeat ad nauseum for each instance of the file.  And then repeat that ad nauseum for each file.

It can take hours to days to deploy a single change for one file let alone modifying changes of files at scale.  This leads to accumulating extensive technical debt by not deploying updates across projects in a timely fashion.  As a result, projects tend to end up with different versions of the same set of files that slowly becomes unmanageable.

File Tracker makes short work of the entire process and wipes out technical debt by being able to safely and confidently deploy changes across an unlimited number of projects on an unlimited number of hosts in minutes instead of hours, days, or even weeks.

*What does the license cover?*

A single license covers you and/or your whole team plus upgrades and product support for one year.

*What's the latest version of File Tracker?*

The [CubicleSoft File Hashes repository](https://github.com/cubiclesoft/product-hashes) tracks product hashes and version information about the latest releases of File Tracker.

*Is there a demo/shareware version?*

Nope.  Sorry.  Please use the [Getting Started Guide](docs/getting_started.md), the Overview Tutorial video, and the questions and answers here in the FAQ to make your decision about whether or not File Tracker is right for you.  If the previous questions are bringing up old memories, then there's been a lot of wasted time on a problem that File Tracker solves.

Post-Purchase
-------------

*Okay, I've bought a license, now what?*

Follow the [Getting Started Guide](docs/getting_started.md).

If you encounter any difficulties, reach out on the Help/Support channel.  File Tracker is a bit complex and can seem a little scary the first time it makes a ton of VCS commits and pushes, so don't be afraid to ask questions.

*How do I undo a major mistake?*

Hope you keep good backups.  Just kidding.  But you really should keep good backups.

If you haven't Synchronized yet, simply clear all of the scheduled changes for the Projects/Files.

If you have Synchronized, then restoring from a backup or using standard version control mechanisms to locate a previous version of the file and just restoring one file can get you back on the right track.  After manually restoring one file in one project, follow the usual File Tracker workflow to deploy the previous file across all projects, but make sure to select the older file as the source.  That will at least get you back to the previous state.

*How can I handle advanced git setups?*

The git distributed version control system (DVCS) is extremely complex.  It has submodules, branches, tags, history rewriting, forking/pulling, and more.  The File Tracker VCS support is generic.  It supports many different version control systems, which means git-specific features may be more difficult to configure.

For really complex setups where a single directory tree contains multiple git repos inside git repos, using the Manual file selection option in a Project is useful if only slightly more tedious.  If you are having issues planning out your Project setup/layout, feel free to reach out on the Help/Support channel.

*How to handle password-protected SSH keys with git?*

Unfortunately, you'll have to push to your origin(s) manually.  There are some limitations with the underlying SSH library.

Feel free to reach out on the Help/Support channel though for possible solutions.

*How do I share my configuration/File Groups/Project setup with the rest of my team?*

You just spent two hours configuring File Tracker and using it for the first time to make 220 commits across 43 different projects.  Now the rest of your team wants to use it too.

At the moment, the only thing that can be shared is the entire File Tracker database and maybe the configuration settings.  That option may or may not work for you/your team.

Sharing is definitely one of the weaker areas of File Tracker.  Keep in mind though that without File Tracker, it would take weeks to months of time to accomplish the same activities.  However, let's discuss your complex sharing needs on the Help/Support channel.

*What's the refund policy?*

File Tracker is somewhat complex to figure out, so it's entirely likely that you just need a little help for your particular use-case.

However, if File Tracker isn't to your liking or just isn't working out, simply ask nicely for a refund.

Feel free to reach out on the Help/Support channel for either option.
