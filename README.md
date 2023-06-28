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


## Convention

Please follow these conventions while trying to contribute (click on each item to open the details):

<ol>
<li>
<details>
<summary>Code blocks</summary>

Please make sure to define the language in the markdown:

<pre><code>´´´sh
some commands here
```</code></pre>

</details>
</li>

<li>
<details>
<summary>Images of pages in <code>/content/docs/</code></summary>

- Image related to each markdown file goes into the dedicated folder for that markdown file. For instance the images of file `/content/docs/guide/wayland-help.md` goes into the folder `/static/media/content/docs/guide/wayland-help/`.
- Please make sure there is no copy-righted content in the image
- Please make sure the size is not too wide or too long
- For creating arrows and markings, please use the `#fa0164` color
- Please consider adding the caption/alt-text (it goes between double quotes after the address of the image path. Check the example below)

Example of a good practice:

```md
![gnome permission window](/media/content/docs/guide/wayland-help/2022-08-04_11-39_gnome_share_permission_indow.png "Screenshot of the Gnome permission window which has a Share button at the top right corner")
```

</details>
</li>

<li>
<details>
<summary>Referencing Flameshot buttons</summary>

The convention is to have the name of the button first (you can run Flameshot and use your mouse to hover over the button and see what it's name is), and then the icon.
For the icon you can find the button you want in:

<https://github.com/flameshot-org/flameshot/tree/master/data/img/material/black>

and then replace the filename with the `XXXX` in the following line:

```html
<img width="24" class="gui-button" src="https://raw.githubusercontent.com/flameshot-org/flameshot/master/data/img/material/black/XXXX.svg" />
```

</details>
</li>

<li>
<details>
<summary>Spelling</summary>

Although we are not very strict, but the preferred spelling is the American spelling of the words (e.g "analyze" instead of "analyse").
When in doubt, please check the word in the [Merriam-Webster](https://www.merriam-webster.com) dictionary.
Again, don't sweat about it, but it is good to be consistent.

</details>
</li>

<li>
<details>
<summary>Body text</summary>

- Although not very strict, it is preferred to have one sentence per line (this can be avoided in lists as it can break the continuity in Markdown lists
- The paragraphs should be separated by one empty line, and sections and headings by two empty lines
- try avoiding complicated words, but if you want to use one, please consider linking it to it's definition in [Wordnik](https://www.wordnik.com) or [Merriam-Webster](https://www.merriam-webster.com).

</details>
</li>
</ol>
