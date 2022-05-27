---
layout: post
title: C++ Installation on VSC (macOS)
---

# C++ Installation on VSC (MacOS)
## Introduction
*The process of setting up an IDE and an ideal workflow is usually not difficult, especially if you have a strong preference or a tried-and-tested personal workflow. However, installing and setting up the IDE still takes a lot of time, and might end up wasting your time if that single setting foils your entire setup.*

This article is a step-by-step guide to installing VSC on MacOS for C++ use. The process is easier for Python - thus we will only focus on the C++ setup.

## Overview
#### 1. Download XCode

![[Pasted image 20220527095600.png]]

Clang is the default C++ compiler on MacOS. The XCode IDE contains necessary tools to download clang. You can download Xcode from the AppStore. Make sure to check your MacOS version first before downloading, as it is a 5+ GB download...

##### What if the latest version of XCode isn't supported on my Mac?
You need to create an Apple Developer account -> https://developer.apple.com/
You can use your current Apple account and "upgrade" it to a developer account. Once you do that, find the right XCode version and download it from there.

#### 2. Install Clang ~ **clang --version**, **command xcode-select --install**
#### 3. Download VSC ~ [https://code.visualstudio.com/](https://code.visualstudio.com/)
#### 4. Install add-ons C/C++, CodeRunner, modify CodeRunner preferences, define default build (clang++)
