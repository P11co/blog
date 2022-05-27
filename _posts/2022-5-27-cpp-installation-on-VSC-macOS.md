---
layout: post
title: C++ Installation on VSC (macOS)
---

## Introduction
*The process of setting up an IDE and an ideal workflow is usually not difficult, especially if you have a strong preference or a tried-and-tested personal workflow. However, installing and setting up the IDE still takes a lot of time, and might end up wasting your time if that single setting foils your entire setup.*

This article is a step-by-step guide to installing **VSC on MacOS for C++ use**.

## The Process
#### 1. [Download XCode](https://developer.apple.com/support/xcode/)
Clang is the default C++ compiler on MacOS. The XCode IDE contains necessary tools to download clang. In most cases, you should download Xcode from the [AppStore](https://apps.apple.com/us/app/xcode/id497799835?ls=1&mt=12).

*What if the latest version of XCode isn't supported on my Mac?*
Check the **"Minimum requirements and supported SDKs"**, and find the right XCode version and download it from the Apple Developer website. You will need to log into your Apple account.

#### 2. Install Clang
After downloading *XCode*, mount the *XCode.dmg* file and move *XCode.app* into your Applications folder.

Open Terminal and type `**clang --version**` to check whether it is already installed.

If not or if outdated, type `**command xcode-select --install**` to install clang.

You'll have to **Install**, **Agree**, and click **Done** to a few statements.

Finally, type `**clang --version**` again to check if clang is successfully installed.

![[Screen Shot 2022-05-27 at 10.19.47 AM.png]]

*What if I get an error message like this?:* `xcode-select: error: command line tools are already installed, use "Software Update" to install updates`
This means you've previously installed clang. We will delete the previous install, and reinstall clang. Enter the following in the terminal, sequentially.
`sudo rm -rf /Library/Developer/CommandLineTools`
`sudo xcode-select --install`

#### 3. [Download VSC](https://code.visualstudio.com/)
Download the IDE of your choice. In this guide, we will focus on the setup of the versatile VSC. Note that VSC is an **IDE without a compiler**. It can run C/C++, Java, Python, and pretty much any language. Thus, the setup is more confusing than an IDE with built-in compilers like CLion or Eclipse for C/C++, since the installation of the compiler and IDE is separate.



#### 4. Install add-ons C/C++, CodeRunner, modify CodeRunner preferences, define default build (clang++)


Source:

[Clang installation](https://www.ics.uci.edu/~pattis/common/handouts/macclion/clang.html)
[`xcode-select: error:`](https://investechnews.com/2021/06/15/mac-commandlinetools-setup-error/)
[CodeRunner Setup](https://wooono.tistory.com/299)
