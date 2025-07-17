---
layout: default
title: Installation
header_title: "Jekyll Local Installation"
header_type: hero #base, post, hero,image, splash
header_img: assets/images/Jekyll_Logo.png
---

<div class="alert alert-warning">
<p>
<strong>This section is optional</strong>. You don't need to install Jekyll if you want to develop the website online using GitHub Pages.
</p>
<p>The advantages of developing the website locally are:</p>
<ul>
<li>You can test the website locally before pushing it to GitHub.</li>
<li>You can use a local editor to write the content and manage the files.</li>
<li>You don't have to wait for GitHub Pages to build the website every time you make a change</li>
</ul>
</div>

# Jekyll Installation Guide

To develop the Progettone® website, we will use a Static Site Generator (SSG), which allows you to create fast-loading websites without the need for complex backend systems or databases. In particular, we will use one of the most popular SSGs, **Jekyll**. Jekyll is a free, open-source SSG based on the Ruby programming language. **You do not need to know Ruby to use Jekyll**; you just need to have Ruby installed on your computer.
<hr>

#### The advantages of Jekyll

**Ease of use**: Jekyll uses plain text files and markdown syntax to create and manage content, so you do not need to know HTML or CSS to get started.

**Speed and security**: Jekyll does not interact with databases or server-side scripts, reducing the risk of vulnerabilities and attacks. It generates static HTML files, making the site incredibly fast and secure.

**Customizability**: Jekyll is highly customizable, allowing the use of layouts and templates or the creation of plugins to extend its functionality.

**Easy deployment**: Jekyll generates static HTML files that can be distributed on a web server or hosting provider without the need for a dynamic content management system.
<hr>
<br>

> **In the following guide you will find the prerequisites to make Jekyll work**

<br>
# How to Install Jekyll on Windows

To install Ruby and Jekyll on a Windows computer, you need to use RubyInstaller. This can be done by downloading and installing a Ruby+Devkit version from [RubyInstaller Downloads](https://rubyinstaller.org/downloads/) and **using the default installation options and taking the latest recommended version** (leave everything as is, especially **MSYS2**).

This operation will take a few minutes.

In the last phase of the guided installation, run <code>ridk <strong>install </strong></code> (as recommended), which is used to install the gems. For more information, see the [RubyInstaller Documentation](https://github.com/oneclick/rubyinstaller2#using-the-installer-on-a-target-system).

At the end of the installation, you will see this prompt:

![Ruby Installer on windows]({{site.baseurl}}/assets/images/RubyInstaller.png "image_tooltip")

Among the options, choose **MSYS2** and **MINGW development toolchain** (3 Enter).

This operation takes a few minutes, and it is normal for some alerts to appear.

Open a new **command prompt** window and install Jekyll and Bundler with the following command:

```
gem install jekyll bundler
```

Check that Jekyll is installed correctly:

```
jekyll -v
```

If you see the version number, it means Jekyll is installed and working correctly on your system. **Now everything is ready to start using Jekyll!**

<br>
# How to Install Jekyll on macOS

By default, Ruby is pre-installed on macOS, but you cannot use this version of Ruby to install Jekyll because it is outdated. For example, on Ventura, the pre-installed Ruby version is 2.6.10, while the latest version is 3.1.3.

To solve this problem, you need to install Ruby correctly using a version manager like **chruby**.

### Homebrew
First, you need to install **Homebrew** (in the unlikely event you haven't already done so).

To check if Homebrew is installed, run the command

```
brew -v
```

If it is already installed, you will see the version number.

**To install Homebrew** on your Mac, run the following command in your terminal:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

The system may ask you to accept the Homebrew license terms, follow the instructions that appear:

```bash
sudo xcodebuild -license
```

and after scrolling through the license terms, type

```bash
agree
```

to accept.

Once the installation is complete, configure your shell to automatically use brew: to use brew from your terminal you will need to add it to PATH, **the program will tell you exactly how to do this** at the end of the installation, it is something like:

```bash
(echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> /Users/username/.zprofile
    eval "$(/opt/homebrew/bin/brew shellenv)"
```

Once the installation is successful, **exit and restart the terminal**, then check if Homebrew is ready to use by running this command:

```bash
brew -v
```

### Chruby and Ruby-install
If you have seen the Homebrew version, you can proceed to install **chruby** and ruby-install with the following command.

Continue with the installation of chruby and ruby-install using the following command:

```bash
brew install chruby ruby-install
```

Now you can install the latest version of ruby, 3.1.3, using the ruby-install package you just installed:

```bash
ruby-install 3.1.3
```

This operation will take several minutes.

Once the installation is complete, configure your shell to automatically use chruby with the following command:

```bash
echo "source $(brew --prefix)/opt/chruby/share/chruby/chruby.sh" >> ~/.zshrc
echo "source $(brew --prefix)/opt/chruby/share/chruby/auto.sh" >> ~/.zshrc
echo "chruby ruby-3.1.3" >> ~/.zshrc
```

<div class="alert alert-warning" role="alert">
  <strong>Warning!</strong> If you are using a bash terminal instead of zsh, the command is the same, just point to the different terminal type: <code>~/.bash_profile</code>

N.B. if you use bash instead of zsh, the command is the same, just point to the different terminal type: <code>~/.bash_profile</code>
</div>

```bash
echo "source $(brew --prefix)/opt/chruby/share/chruby/chruby.sh" >> ~/.bash_profile
echo "source $(brew --prefix)/opt/chruby/share/chruby/auto.sh" >> ~/.bash_profile
echo "chruby ruby-3.1.3" >> ~/.bash_profile
```

At this point you can **exit and relaunch the Terminal**, then check that everything works by running this command:

```bash
ruby -v
```

It should say **<code>ruby 3.1.3.</code>**

### Jekyll and Bundler
You have installed the latest version of Ruby on your computer, so you can proceed to install the latest Jekyll and bundler gems:

```bash
gem install jekyll bundler
```

Check that Jekyll is installed correctly

```bash
jekyll -v
```

If you see the version number, it means Jekyll is installed and working correctly on your system. **Now everything is ready to start using Jekyll!**

<br>
# Test: Creating a Site

Important note: it is recommended to develop the website using an editor like Visual Studio Code or PyCharm.
<hr>
To create a new site that will work locally in the my-progettone folder, type:

```bash
jekyll new my-progettone
```

enter the folder

```bash
cd my-progettone
```

run

```bash
bundle exec jekyll serve
```

open your browser at [http://127.0.0.1:4000](http://127.0.0.1:4000) (as indicated in the terminal)

Congratulations, if you have made it this far you should see a website with the minimum elements.

WARNING! In the case of **windows** installations, it is possible that the **wdm** gem returns an error that prevents the site from being compiled.

In this case, open the Gemfile created during the execution of <code>jekyll <strong>new</strong> my-progettone</code>

comment out the line using the **#** character

```bash
# gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]
```

save the file and run:

```bash
bundle update
```

restart the site with

```bash
bundle exec jekyll serve
```

**open your browser at [http://127.0.0.1:4000](http://127.0.0.1:4000)**

<br>
# To clone this theme into your own repository

Go to the following link:

```bash
https://github.com/new/import
```

and enter the link of the repository to clone:

```bash
https://github.com/sobigdata-master/progettone-template.git
```

run

```bash
bundle install
```

start the site with the bundle command
```bash
bundle exec jekyll serve
```

**open your browser at [http://127.0.0.1:4000](http://127.0.0.1:4000)**
