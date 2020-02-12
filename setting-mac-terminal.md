# Setting the Mac terminal

This guide assumes that you are using Catalina and above. In Catalina, macOS now uses `zsh` instead of `bash` as a terminal shell. As such, some of the information available on the web is outdated. A workaround is to include `zsh` in your search parameters.

## Installing brew

In Debian-based Linux distros, they have a software package manager called Advanced Packaging Tool. Users can use `apt` (and also `apt-get`) to install packages for their OS (i.e. `apt install git`). In macOS, there is no such thing, so the open-source tool [Homebrew](https://brew.sh/) fills that void.

Before you can install Homebrew, you'll have to install Xcode's Command Line Tools by using `xcode-select --install`.

Then you can follow the instructions featured on the [Homebrew](https://brew.sh/) homepage. For the sake of completeness, the command is `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`, but it may be outdated.

## Creating and modifying your `~/.zshrc` file

Whenever you start any `zsh` Terminal window, it looks for a `.zshrc` file in your `~` directory (the default directory that simply writing `cd` brings you to). It is a bit different from the `~/.zprofile` file. That one is only read in a login shell. When you manually open a shell terminal, it is often not a login shell. Since `~/.zshrc` is read for any shell (including login shells), we will be modifying that file to set some environment variables such as `$PATH`. More advanced configurations might require you to modify `~/.zprofile` instead, but they are outside of the scope of this guide. 

The `~/.zshrc` is not usually created by default. Navigate to your `~` folder by typing `cd` and execute `ls -a` to see if `.zshrc` already exists.

If not, you can create the file with a  text editor or simply execute `touch .zshrc`.

You can then modify the file using any text editor, although I would recommend `vim` since `Finder` does not display files starting with a period (`.`) by default.

### Modify `~/.zshrc` using Vim

Just type `vim ~/.zshrc` to modify the `~/.zshrc` file. (You can alternatively use `nano ~/.zshrc` if you are unfamiliar with vim.)

## Modifying your $PATH

Modifying your $PATH is especially important for making `brew` (Homebrew's terminal shorthand) packages work seamlessly in the Terminal. When you type `vim`, it accesses a binary at `usr/bin/vim` (you can get that path when you execute `which vim`). However, Homebrew installs binaries at `usr/local/bin`, it might create some problems. This is because your `$PATH` (`echo $PATH`) might not include that `usr/local/bin`. Also, paths included before have priority on paths included afterwards.

* Add: `export PATH=/usr/local/Cellar:/usr/local/bin:$HOME/bin:$PATH` to the `~/.zshrc`.

Now it should work.

## Other programs that will require you to edit your `~/.zshrc`

### [Node Version Manager](https://github.com/nvm-sh/nvm)

* On the Github page, after the command `wget -q0- ...`, it says that the script would add it's settings automatically to your `~/.zshrc` file, but you might have to do manually.

* If you have to, add the `export NVM_DIR="$([...]"$NVM_DIR/nvm.sh" # This loads nvm` snippet to your `~/.zshrc` file (under the `export PATH...`).