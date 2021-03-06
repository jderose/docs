---
layout: article
title: Move the Launcher in 16.04 LTS
description: >
    Moving the Launcher to the bottom and back in Ubuntu 16.04.
keywords:
    - Unity
    - Unity 7
    - 7
    - Launcher
    - Bottom
    - Left
    - Moving
    - Broken
---

Ubuntu 16.04 LTS now includes the ability to move the Launcher at the left to the bottom edge of the screen. If you'd like to put the launcher at the bottom of the screen, then press <kbd>Ctrl</kbd> <kbd>Alt</kbd> <kbd>T</kbd> to open a terminal window, then enter in this command, followed by enter:

```
gsettings set com.canonical.Unity.Launcher launcher-position 'Bottom'
```
![Setting the Launcher to the bottom](/images/movelauncher/Step-1.png)

This will set the launcher to the bottom of the screen:

![Lanncher on the bottom](/images/movelauncher/Step-2.png)

To reset the position of the launcher to the left, run this command instead:

```
gsettings set com.canonical.Unity.Launcher launcher-position 'Left'
```
![Resetting the Launcher](/images/movelauncher/Step-3.png)
