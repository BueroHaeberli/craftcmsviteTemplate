A Craft CMS starter project using DDEV for local hosting and Vite for front-end bundling and HMR.

## Notable Features:

- [DDEV](https://ddev.readthedocs.io/) for local development
- [Vite 4.x](https://vitejs.dev/) for front-end bundling & HMR
- [Tailwind 3.x](https://tailwindcss.com) for utility-first CSS
- [Alpine 3.x](https://alpinejs.dev/) for lightweight reactivity
- [Makefile](https://www.gnu.org/software/make/manual/make.html) for common CLI commands

## Local machine prerequisites:

1. [Docker](https://www.docker.com/)
2. [DDEV](https://ddev.readthedocs.io/), minimum version 1.19
3. Optional but recommended, [Composer](https://getcomposer.org/)

## Getting Started

### Git CLI

Clone the repo via the Git CLI:

```shell
git clone git@github.com:BueroHaeberli/craftcmsviteTemplate.git PATH
```

Make sure that `PATH` is a **new** _or_ **existing and empty** folder.

Next, you'll want to discard the existing `/.git` directory. In the terminal, run:

```shell
cd PATH
rm -rf .git
```

Last, clean up and set some default files for use:

```shell
cp .env.example .env
mv -f composer.json.default composer.json
mv -f .gitignore.default .gitignore
rm CHANGELOG.md && rm LICENSE.md && rm README.md
```

## Configuring DDEV

To configure your project to operate on a domain other than `https://craftcms.ddev.site`, run:

```shell
ddev config
```

Follow the prompts.

- **Project name:** e.g. `mysite` would result in a project URL of `https://mysite.ddev.site` (make note of this for later in the installation process)
- **Docroot location:** defaults to `web`, keep as-is
- **Project Type:** defaults to `php`, keep as-is

## Installing Craft

To install a clean version of Craft, run:

```shell
make install
```

Follow the prompts.

This command will:

1. Copy your local SSH keys into the container (handy if you are setting up [craft-scripts](https://github.com/nystudio107/craft-scripts/))
2. Start your DDEV project
3. Install Composer
4. Install npm
5. Do a one-time build of Vite
6. Generate `APP_ID` and save to your `.env` file
7. Generate `SECURITY_KEY` and save to your `.env` file
8. Installing Craft for the first time, allowing you to set the admin's account credentials
9. Install all Craft plugins

Once the process is complete, type `ddev launch` to open the project in your default browser. 🚀

## Local development with Vite

To begin development with Vite's dev server & HMR, run:

```shell
make dev
```

This command will:

1. Copy your local SSH keys into the container (handy if you are setting up [craft-scripts](https://github.com/nystudio107/craft-scripts/))
2. Start your DDEV project
3. Install Composer
4. Install npm
5. Do a one-time build of Vite
6. Spin up the Vite dev server

Open up a browser to your project domain to verify that Vite is connected. Begin crafting beautiful things. ❤️

## Makefile

A Makefile has been included to provide a unified CLI for common development commands.

- `make install` - Runs a complete one-time process to set the project up and install Craft.
- `make up` - Starts the DDEV project, ensuring that SSH keys have been added, and npm & Composer have been installed.
- `make dev` - Runs a one-time build of all front-end assets, then starts Vite's server for HMR.
- `make build` - Builds all front-end assets.
- `make pull` - Pull remote db & assets (requires setting up [craft-scripts](https://github.com/nystudio107/craft-scripts/)

## Craft CMS Plugins

1. [CP Field Inspect](https://plugins.craftcms.com/cp-field-inspect)
1. [Craft Autocomplete](https://github.com/nystudio107/craft-autocomplete)
1. [Vite](https://github.com/nystudio107/craft-vite)
1. [CK editor](https://github.com/craftcms/ckeditor)
1. [Link Field](https://github.com/sebastian-lenz/craft-linkfield)

## Tailwind Plugins

1. [Aspect Ratio](https://github.com/tailwindlabs/tailwindcss-aspect-ratio)
1. [Line Clamp](https://github.com/tailwindlabs/tailwindcss-line-clamp)
1. [Typography](https://github.com/tailwindlabs/tailwindcss-typography)

## Javascript Libraries

1. [AlpineJS](https://alpinejs.dev/)
1. [Lazysizes](https://afarkas.github.io/lazysizes/)

## Roadmap

- Continue to improve docs
- Bugfixes, new features

## Acknowledgements & Credits

Aside from the obvious gratitude owed to the entire team at [Pixel & Tonic](https://pixelandtonic.com/) for their tireless work on Craft, a special thanks goes out to Andrew Welch of [nystudio107](https://nystudio107.com/). Not only has he developed some of the most widely used plugins in the Craft ecosystem, he has dedicated countless time and energy to pushing all of us in the community to excel at everything we do. He has an uncanny ability to see through the fog of development war to know what's best - not just for us, but for our future selves, our clients, and the users of the sites we build. His contributions have made all of our sites perform better in SEO, run faster in the browser, and made our development workflow more streamlined and efficient. Hats off to you, sir.
