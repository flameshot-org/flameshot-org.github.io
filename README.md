[![License](https://img.shields.io/github/license/flameshot-org/flameshot.svg)](https://github.com/flameshot-org/flameshot/blob/master/LICENSE)
[![Release](https://img.shields.io/github/release/flameshot-org/flameshot.svg)](https://github.com/flameshot-org/flameshot/releases)

# [Flameshot.org](https://flameshot.org)

![image](static/favicon.png)
> Powerful yet simple to use screenshot software.

This is the repository of [flameshot.org](https://flameshot.org). For the software code, you should go to [the main repository](https://github.com/flameshot-org/flameshot/).

This static website is powered by [zola](https://www.getzola.org).

# Development

## building the website locally

It is essential that you build the website locally on your computer (it would take about 1 second) to check if the changes you have made are correctly getting converted to HTML. Typically typos can mess things up.
To build the website, you first need to install [zola](https://www.getzola.org/) (the static website generator that we use for this website), and then follow these steps:

- Navigate to the root directory of the cloned repository
- Run `zola serve` to start a local server for development
    - look for possible errors or messages
- Open `127.0.0.1:1111` in your browser to see the website

The browser will automatically refresh on any changes made. Sass is setup to auto compile when the scss is edited.
