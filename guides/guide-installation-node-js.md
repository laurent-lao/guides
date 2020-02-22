# Node.js Installation

* If at any point, you are being told that you do not have permission, try adding `sudo` to the front of your commands.

* Install nvm (you might have to edit your `.zshrc` afterwards: see [this section](/mac/setting-mac-terminal.md#node-version-manager) for help)

* Type `nvm install node` (might have to be in sudo for this) or alternatively, `nvm install x.x.x` where `x.x.x` is the node version you want to install.

* Then, run `nvm install-latest-npm`.

* If there is an existing repo with node, then I would recommend cloning the repo, navigating to the checkout folder and to run `npm install` to install the packages outlined in the `package.json`.

* If not, then you might want to install some of the node.js frameworks

## Angular

For Angular, you might want to install the Angular CLI

* `npm install -g @angular/cli@latest`

This will install Angular globally so you can use `ng` commands from your terminal.

Then, use `ng new <nameOfProject>` to create a new Angular project

## React

Since react is fully compatible with `Node.js`, you do not need to install it globally.

Simply use the command `npm install react` onto your project folder to install React into your workspace.

## Vue.js

For Vue.js, you might want to install the Vue.js CLI

* `npm install -g @vue/cli`

This will install Vue.js globally so you can use `vue` commands from your terminal.

Then, use `vue create <nameOfProject>` to create a new Vue.js project
