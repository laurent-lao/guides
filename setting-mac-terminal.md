# Setting the Mac terminal

This guide assumes that you are using Catalina and above. In Catalina, macOS now uses `zsh` instead of `bash` as a terminal shell. As such, some of the information available on the web is outdated. A workaround is to include `zsh` in your search parameters.

## iTerm2

Although the default Terminal is very powerful, you might want to look at an alternative called [iTerm2](https://iterm2.com/features.html) which is a better Terminal IMO. You could also install iTerm2 by executing `brew cask install iterm2` (only after you installed brew with the instructions below).

## Installing brew

In Debian-based Linux distros, they have a software package manager called Advanced Packaging Tool. Users can use `apt` (and also `apt-get`) to install packages for their OS (i.e. `apt install git`). In macOS, there is no such thing, so the open-source tool [Homebrew](https://brew.sh/) fills that void.

Before you can install Homebrew, you'll have to install Xcode's Command Line Tools by using `xcode-select --install`.

Then you can follow the instructions featured on the [Homebrew](https://brew.sh/) homepage. For the sake of completeness, the command is `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`, but it may be outdated.

## Creating and modifying your `~/.zshrc` file

Whenever you start any `zsh` Terminal window, it looks for a `.zshrc` file in your `~` directory (the default directory that simply writing `cd` brings you to). It is a bit different from the `~/.zprofile` file. That one is only read in a login shell. When you manually open a shell terminal, it is often not a login shell.

Since `~/.zshrc` is read for any shell (including login shells), we will be modifying that file to set some environment variables such as `$PATH`. More advanced configurations might require you to modify `~/.zprofile` instead, but they are outside of the scope of this guide.

The `~/.zshrc` is not usually created by default. Navigate to your `~` folder by typing `cd` and execute `ls -a` to see if `.zshrc` already exists.

If not, you can create the file with a  text editor or simply execute `touch .zshrc`.

You can then modify the file using any text editor , although I would recommend `vim` since `Finder` does not display files starting with a period (`.`) by default.

### Modify `~/.zshrc` using Vim

Just type `vim ~/.zshrc` to modify the `~/.zshrc` file. (You can alternatively use `nano ~/.zshrc` if you are unfamiliar with vim. It is way easier to use.)

## Modifying your $PATH

`$PATH` is an environment variable. macOS uses `$PATH` to specify a set of directories where executables (or binary files) are located. When your Terminal window is created, it uses the `$PATH` to load the shell executables that are on your system. That is how your shell knows what to execute when you type `vim` for example.

Modifying your $PATH is especially important for making `brew` (Homebrew's terminal shorthand) packages work seamlessly in the Terminal. When you type `vim`, it accesses a binary at `usr/bin/vim` with `usr/bin` being defined by your $PATH (you can get that path when you execute `which vim`). However, since Homebrew installs binaries at `usr/local/bin`, it might create some problems where you are not able to locate packages you have just installed. This is because your `$PATH` (`echo $PATH`) might not include that `usr/local/bin`. As an important node, the order of paths in `$PATH` is important. Paths included before have priority on paths included afterwards.

Below is the setting that worked well for me so far:

* Use a text editor to modify your `./zshrc` file (you can use `vim ~/.zshrc` or `nano ~/.zshrc`).

* Add: `export PATH=/usr/local/Cellar:/usr/local/bin:$HOME/bin:$PATH` to the `~/.zshrc` file.

## Other programs that will require you to edit your `~/.zshrc`

### Node Version Manager

Node Version Manager allows you to easily switch between different versions of node. You do not have to install it, unless you work with Node. It is included here as it requires a small modification to your `~/.zshrc` file.

* On the [Github page]((https://github.com/nvm-sh/nvm)), after the command `wget -q0- ...`, it says that the script would add it's settings automatically to your `~/.zshrc` file, but you might have to do manually.

* If you have to, add the `export NVM_DIR="$([...]"$NVM_DIR/nvm.sh" # This loads nvm` snippet available in the Github page to your `~/.zshrc` file (under the `export PATH...`, or anywhere else).

* You can follow the [Node.js install guide](node-js-installation.md) to get node, angular and/or react installed

### Oh My Zsh

Oh My Zsh allows you to run customize your zsh Terminal. It prettifies it but also adds a lot of features. I recommend that you backup your `~/.zshrc` file before [you install it](https://github.com/ohmyzsh/ohmyzsh) by executing `cp ~/.zshrc ~/.zshrc.copy`. Then, once the installation is done, copy anything from the `~/.zshrc.copy` to `~/.zshrc`. Although anything that modifies $PATH should be put at the top, anywhere is fine.

<!-- markdownlint-disable MD025 -->
# Installing other command-line tools

## Installing Git

Git is a version control system. It is probably the most important tool for a programmer. That is more often than not the way programmers use to collaborate with each other. With Git, you can use Github, Gitlab and other repository providers. I have written a [Git Guide](git-guide.md) to help with the process, but you should do a tutorial to understand Git better. Git is usually installed after you executed `xcode-select --install`. If not, or if you would like to use a more recent copy of Git, you can use `brew install git` to get Git on your Mac.

## Launching text editors with terminal

### VSCode

To launch VSCode by using `code` or `code <filename>` in the Terminal, launch VSCode first. Then, open the Command Panel (usually with `cmd+shift+P`). Type `Shell Command: Install 'code' command in PATH` and press enter. Now the command should work.

### Sublime Text 3

Try launching Sublime Text 3 by executing `open /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl`. If that works, then you can create a symlink in your `/usr/local/bin` by executing `ln -s /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl /usr/local/bin/sublime`. `sublime` and `sublime <filename>` will open Sublime Text 3.
