# mvps-cofigs

A collection of recommended development configuration files

## In Progress

- Git
	- .gitconfig - [Config](.gitconfig) | [Info](https://git-scm.com/docs/git-config)
	- .gitignore - [Config](.gitignore) | [Info](https://git-scm.com/docs/gitignore)
	- .gitattributes - [Config](.gitattributes) | [Info](https://git-scm.com/docs/gitattributes)
- Misc
	- .bashrc - [Config](.bashrc) | [Info](https://www.gnu.org/software/bash/manual/html_node/Bash-Startup-Files.html)
	- .editorconfig - [Config](.editorconfig]) | [Info](https://editorconfig.org/)
	- .npmrc - [Config](.npmrc) | [Info](https://docs.npmjs.com/files/npmrc)
- Linters
	- ESlint - [Config](.eslintrc.json) | [Info](https://eslint.org/)
	- Stylelint - [Config](.stylelint.json) | [Info](https://stylelint.io/)
	- HTML Lint - [Config](.htmllintrc.json) | [Info](https://github.com/htmllint/htmllint/wiki)
	- Lint HTML - [Config](.linthtmlrc.json) | [Info](https://github.com/linthtml/vscode-linthtml)

## Todo

- PHP CodeSniffer

## Installation & Setup

1. Show hidden files
2. [Install Git](https://git-scm.com/downloads)
	1. [Install Git LFS](https://git-lfs.github.com/)
3. [Install Node & NPM & PNPM](https://nodejs.org/en/download/)
	1. [Configure npm to allow global installs without admin rights](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally)
	2. Check if you have pnpm installed: `$ pnpm -v`
	3. If the terminal outputs a version number, skip to step 5.
	4. Install pnpm: `$ npm install -g pnpm`
	5. `$ pnpm install -g eslint babel-eslint postcss stylelint htmllint-cli @linthtml/linthtml`
4. Download the config files
	1. `$ cd ~/ && git clone https://github.com/mivaecommerce/mvps-configs.git`
	2. `$ cd mvps-configs && pnpm install`
5. [Install MAMP](https://www.mamp.info/en/downloads/) (or the following languages individually)
	1. Add the php, apache, python, mysql binaries to your PATH
	2. [Install Composer](https://getcomposer.org/doc/00-intro.md)
		1. _Configure composer to allow global installs without admin rights?_
		2. `$ composer global require "squizlabs/php_codesniffer=*"`
6. _Optionally, install python, pip, & mkdocs (Coming Soon)_
7. [Install VS Code](https://code.visualstudio.com/download)
	1. Install Miva IDE for syntax highlighting, snippets and tools for building websites with Miva.
		1. [Miva IDE](https://marketplace.visualstudio.com/items?itemName=mhegler.vscode-miva-ide)
	2. Install the language specific linter-packages
		1. [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
		2. [Stylelint](https://marketplace.visualstudio.com/items?itemName=stylelint.vscode-stylelint)
		3. [PHPCS](https://marketplace.visualstudio.com/items?itemName=ikappas.phpcs)
		4. [PostCSS Sorting](https://marketplace.visualstudio.com/items?itemName=mrmlnc.vscode-postcss-sorting)
		5. [LintHTML](https://marketplace.visualstudio.com/items?itemName=kamikillerto.vscode-linthtml)
	1. Update your VS Code Settings, `Command Prompt > Preferences Open Settings (JSON)`, and update them with settings indicated in [vs-code.settings.json](vs-code.settings.json)
8. Configure the linters to use the `mvps-configs` files.
	* This method is preferred because it supports unique linting settings for each repo you work with *and* it does not require configuring VS Code link at all.
	* Windows Users: Locate and update your `~/.bashrc` file and append with `export MSYS=winsymlinks:nativestrict` to enable symlinking. Launch Git Bash as administrator and perform the following step's command.
	* Symlink the linter files in your `mvps-configs` directory to `~/` by running `$ cd path/to/mvps-configs && pnpm run symlink:all` then perform your development in any subfolder of `~/` (ex. `~/Documents/Development/Clients/www.example.com/`)
9. Configure `git init` command to create repos based off of our config (which contains a git-hook to add Jira IDs to commits and set the default branch of new repos to `main`)
	1. `git config --global init.templateDir ~/mvps-configs/git/templates`
		- *Note:* You may need to change `~/` with the full path to where you cloned the mvps-configs repo (ex. `C:\Users\username\mvps-configs\git/templates`)
