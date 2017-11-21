Manual Testing
==============

This document describes a high-level script of manual tests to check for. We
should aim to replace items on this list with automated Spectron test cases.

Image Selection
---------------

- [ ] Cancel image selection dialog
- [ ] Select an unbootable image (without a partition table), and expect a
  sensible warning
- [ ] Attempt to select an unsupported image
- [ ] Change image selection

Drive Selection
---------------

- [ ] Open the drive selection modal
- [ ] Remove all drives
- [ ] Switch drive selection
- [ ] Insert a single drive, and expect auto-selection
- [ ] Insert one system drive, and don't expect auto-selection

Image Support
-------------

- [ ] Flash an uncompressed image
- [ ] Flash a Bzip2 image
- [ ] Flash a XZ image
- [ ] Flash a ZIP image
- [ ] Flash a GZ image
- [ ] Flash a DMG image
- [ ] Flash an image whose size is not a multiple of 512 bytes

Flashing Process
----------------

- [ ] Disable validation and flash an image
- [ ] Unplug the drive during flash or validation
- [ ] Click "Flash", cancel elevation dialog, and click "Flash" again

### Child Writer

- [ ] **Kill the child writer process (i.e. with `SIGINT` or `SIGKILL`), and
  check that the UI reacts appropriately**
- [ ] **Close the application while flashing using the window manager close
  icon**
- [ ] **Close the application while flashing using the OS keyboard shortcut**
- [ ] **Close the application from the terminal using Ctrl-C while flashing**
- [ ] **Force kill the application (using a process monitor tool, etc)**
- [ ] **Cancel the application close warning dialog**

In all these cases, the child writer process should not remain alive. Note that
in some systems you need to open your process monitor tool of choice with extra
permissions to see the elevated child writer process.

GUI
----

- [ ] Close application from the terminal using Ctrl-C
- [ ] Click footer links that take you to an external website
- [ ] Attempt to change image or drive selection while flashing
- [ ] Go to the settings page while flashing and come back
- [ ] Flash consecutive images without closing the application
- [ ] Remove the selected drive right before clicking "Flash"

Elevation Prompt
----------------

- [ ] Flash an image as `root`/administrator
- [ ] Reject elevation prompt
- [ ] Put incorrect elevation prompt password
- [ ] Enable unsafe mode, and check drive selector dialog

Unmounting
----------

- [ ] Disable unmounting and flash an image
- [ ] Flash an image with a file system that is readable by the host OS, and
  check that is unmounted correctly

Analytics
---------

- [ ] Disable analytics, open DevTools Network pane or a packet sniffer, and
  check that no request is sent
- [ ] **Disable analytics, refresh application from DevTools, check that
  initial events are not sent to Mixpanel**
