# Node.js Installation

* If at any point, you are being told that you do not have permission, try adding `sudo` to the front of your commands.

* Install nvm (you might have to edit your `.zshrc` afterwards: see [this section](setting-mac-terminal.md#node-version-manager) for help)

* Type `nvm install node` (might have to be in sudo for this) or alternatively, `nvm install x.x.x` where `x.x.x` is the node version you want to install.

* Then, run `nvm install-latest-npm`.

* If there is an existing repo with node, then I would recommend cloning the repo, navigating to the checkout folder and to run `npm install` to install the packages outlined in the `package.json`.

* If not, then you might want to install Angular and/or React globally.

  * For Angular, you can use the command `npm install -g @angular/cli@latest`.

  * For React, you can use the command `npm install -g react`.