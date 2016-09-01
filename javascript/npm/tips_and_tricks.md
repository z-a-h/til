# Tips and Tricks

## Open a package’s homepage

`npm home $package`

The home command opens the homepage of the $package.
Doesn't require the package to be installed globally on your machine or within the current project.

## Open package’s GitHub repo

`npm repo $package`

Opens the github repo of the package. Doesn't require the package to be installed.

## Check a package for outdated dependencies

`npm outdated`

Run the command within a project, and it will check to see if any of the packages are outdated.
Prints out a list in the command line of the current version, the wanted version, and the latest version.

## Check for packages not declared in package.json

`npm prune`

Compares the packages listed in `package.json` to the packages included in `/node_modules` and prints a list of modules not listed in the `package.json`

## Lock down your dependencies versions

`npm shrinkwrap`

Generates a `npm-shrinkwrap.json` file allowing you to pin the dependencies of your project to the specific version you’re currently using within your `node_modules` directory. When you run `npm install` and there is a `npm-shrinkwrap.json` present, it will override the listed dependencies and any semver ranges in `package.json`.

## Use npm v3 with Node.js v4 LTS

`npm install -g npm@3`

Installing `npm@3` globally with npm will update your npm v2 to npm v3, including on the Node.js v4 LTS release (“Argon”) ships with the npm v2 LTS release. This will install the latest stable release of npm v3 within your v4 LTS runtime.

## Allow npm install -g without needing sudo

`npm config set prefix $dir`

Run the command where `$dir` is the directory you want to install your global modules without using `sudo`.
Caveat: you will need to make sure you adjust your user permissions for that directory with `chown -R $USER $dir`.

## Change the default save prefix for all your projects

`npm config set save-prefix ~`

Npm defaults to, the caret (^), when installing a new package with the --save or --save-dev flags. While the tilde pins the dependency to the minor version, allowing patch releases to be installed with npm update. The caret pins the dependency to the major version, allowing minor releases to be installed with npm update.

## Strip your project's devDependencies for a production environment

Install your packages with the added `--production` flag when your project is ready for production. The `--production` flag installs your dependencies and ignores `devDependencies`. This ensures that your development tooling and packages won’t go into the production environment.

You can set your `NODE_ENV` environment variable to production to ensure that your project’s `devDependencies` are never installed.

## Take care when using `.npmignore`

Once you add a `.npmignore` file to your project the `.gitignore` rules are ignored.

## Automate npm init with defaults

`npm config set init.author.name $name`

`npm config set init.author.email $email`

To set defaults for npm init, use the `config set` command with extra arguments.

`npm config set init-module ~/.npm-init.js`

Additionally, you can completely customize your `npm init` by pointing to a self-made default init script.

