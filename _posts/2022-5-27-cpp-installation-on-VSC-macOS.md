---
layout: post
title: C++ Installation on VSC (macOS)
---

## Introduction
#### ==***WHY CAN'T I USE C++17 ON MY MAC, WHY IS IT STUCK ON C++98???***== [Hey, I can help you. Follow me!](#step4)
*The process of setting up an IDE and an ideal workflow is usually not difficult, especially if you have a tried-and-tested workflow. However, installing and setting up the IDE still takes a lot of time, and might end up wasting your time if that single setting foils your entire setup.*

This article is a step-by-step guide to installing **VSC on MacOS for C++ use**.

## Table of Contents:
1. [Download xCode](#step1)
2. [Install clang](#step2)
3. [Download VSC](#step3)
4. [Install VSC Extensions and setup](#step4)


## The Process[^1] 
### 1. [Download XCode](https://developer.apple.com/support/xcode/)  {#step1}
Clang is the default C++ compiler on MacOS. The XCode IDE contains necessary tools to download clang. In most cases, you should download Xcode from the [AppStore](https://apps.apple.com/us/app/xcode/id497799835?ls=1&mt=12).

==*What if the latest version of XCode isn't supported on my Mac?*==
*Check the **"Minimum requirements and supported SDKs"**, and find the right XCode version and download it from the Apple Developer website. You will need to log into your Apple account.*

### 2. Install Clang[^2] {#step2}
After downloading *XCode*, mount the *XCode.dmg* file and move *XCode.app* into your Applications folder.

* Open Terminal
- To check whether clang is already installed, type:
> `clang --version`
- To install clang, type:
> `command xcode-select --install`

You'll have to **Install**, **Agree**, and click **Done** to a few statements.
- To check if clang is successfully installed, type:
>  `clang --version`

![_config.yml]({{ site.baseurl }}/images/Screen Shot 2022-05-24 at 4.58.01 PM.png)

==*What if I get an error message like this?[^3]:*==
```
	xcode-select: error: command line tools are already installed, 
	use "Software Update" to install updates
```
*This means you've previously installed clang. We will delete the previous install, and reinstall clang. Enter the following in the terminal:*
```
	sudo rm -rf /Library/Developer/CommandLineTools
	sudo xcode-select --install
```

### 3. [Download VSC](https://code.visualstudio.com/) {#step3}
Download the IDE of your choice. In this guide, we will focus on the setup of the versatile VSC. Note that VSC is an **IDE without a compiler**. It can run C/C++, Java, Python, and pretty much any language. Thus, the setup is more confusing than an IDE with built-in compilers like CLion or Eclipse for C/C++, since the installation of the compiler and IDE is separate.

### 4. Install VSC Extensions[^4] {#step4}
This part of the guide is the most important, especially if you are not familiar with the VSC interface ~~or easily scared by .json files~~ (*I am too, no worries!*).

On the left panel, there is an icon with 4 squares. This is the extension tab. From here, we can download the plethora of add-ons that are coded by the community for VSC. 

![_config.yml]({{ site.baseurl }}/images/Screen Shot 2022-05-27 at 11.08.17 AM.png)

1. First, we must download the C/C++ extension by Microsoft. This is a prerequisite to run c++ code on VSC.
![_config.yml]({{ site.baseurl }}/images/Screen Shot 2022-05-27 at 11.10.30 AM.png)
2. Next, we will install CodeRunner. This extension allows us to efficiently run c++ code in a click of a button (instead of compiling and running in the Terminal by using command lines.)
![_config.yml]({{ site.baseurl }}/images/Screen Shot 2022-05-27 at 11.12.49 AM 1.png)
3. Right-clicking on CodeRunner > Extension Settings > Run in Terminal > True
![_config.yml]({{ site.baseurl }}/images/Screen Shot 2022-05-27 at 11.15.44 AM.png)
4. In Extension Settings > Executor Map > Edit settings.json
![_config.yml]({{ site.baseurl }}/images/Screen Shot 2022-05-27 at 11.17.50 AM.png)
5. ***Add/replace the following line to where "cpp" is located:***

```json
"cpp": "cd $dir && g++ -std=c++14 $fileName -o $fileNameWithoutExt && $dir$fileNameWithoutExt"
```
6. Now, create a new C++ file and paste the following code:
```
#include <iostream>
#include <vector>
#include <string>

using namespace std;

int main()
{
    vector<string> msg {"Hello", "C++", "World", "from", "VS Code", "and the C++ extension!"};

    for (const string& word : msg)
    {
        cout << word << " ";
    }
    cout << endl;
}
```

7. Go to VSC Menu (top of screen) > Terminal > Configure default build task > select "C/C++ clang++ build active file".
8.  This opens the tasks.json file. It looks like this:

```
{
  // See https://go.microsoft.com/fwlink/?LinkId=733558
  // for the documentation about the tasks.json format
  "version": "2.0.0",
  "tasks": [
    {
      "type": "shell",
      "label": "C/C++: clang++ build active file",
      "command": "/usr/bin/clang++",
      "args": [
        "-std=c++17",
        "-stdlib=libc++",
        "-g",
        "${file}",
        "-o",
        "${fileDirname}/${fileBasenameNoExtension}"
      ],
      "options": {
        "cwd": "${workspaceFolder}"
      },
      "problemMatcher": ["$gcc"],
      "group": {
        "kind": "build",
        "isDefault": true
      },
      "detail": "Task generated by Debugger."
    }
  ]
}
```

9. Instead of "-std=c++17", you may have "-std=c++98" or nothing at all. You can type the desired c++ version of choice (ex. c++11, c++17, c++20).
10. Now run your code by clicking the Run button on the top right -> your setup is complete!
 
[^1]: [The de facto standard installation guide by Microsoft, the creators of VSC!](https://code.visualstudio.com/docs/cpp/config-clang-mac)
[^2]: [Clang installation](https://www.ics.uci.edu/~pattis/common/handouts/macclion/clang.html)
[^3]: [`xcode-select: error:`](https://investechnews.com/2021/06/15/mac-commandlinetools-setup-error/)
[^4]: [CodeRunner Setup](https://wooono.tistory.com/299)
