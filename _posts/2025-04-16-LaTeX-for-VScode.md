---
title: "Streamline Scientific Writing with VS Code + Zotero + Github"
layout: post
---

*Check this out*
INCLUDE GIF HERE
*Pretty neat, right?*

What you just saw above was the ability to save an article off the web, and immediately cite it in your paper with fully integrated git providing version history + backups. This guide will show you how to configure Visual Studio Code (VS Code) and Zotero together to work together automatically, and if you're hesitant to take the leap from Overleaf, consider the following:
1. You'll be able to edit / compile your work entirely locally
2. Git integration means neat collaboration + version history (something overleaf *tries* to do and locks most of behind a paywall)
3. No more compilation timeouts
4. A fully customizable environment

### Pre-requisites
This guide is aimed at macOS users, see the [References](#references) section for Windows help. Below is some other requirements:
* A basic understanding of making documents in LaTeX.
* A free [Zotero](https://www.zotero.org/) account, with the [desktop app and browser "connecter" extension](https://www.zotero.org/download/)
* [VS Code](https://code.visualstudio.com/Download) downloaded.

## Getting a LaTeX Distribution
VS Code will be our text editor where we do all of our work, but we need a distribution of LaTeX behind the curtain for VS Code to use. TeXLive is **strongly recommended** for working with the VS Code extension we'll set up later, and the easiest way to do this is with MacTex. You can [find the download link here](https://www.tug.org/mactex/mactex-download.html). Don't let the file size scare you, much of it is GUI applications that we won't be installing, as they'll functionally be replaced by our VS Code environment.

1. TODO: Write step by step instructions when you open mactex

## Setting up VS Code
With our LaTeX ready, we now need to get VS Code to work with it. The power of VS Code's customization and tools comes from its Extensions Marketplace, which we'll demonstrate here. To access extensions, open the primary side bar (**View > Appearance > Primary Side Bar**), and click the extensions icon. 

TODO: Annotated screenshot of each side bar element

From there, enter `James-Yu.latex-workshop` in the search bar, select the result, and click **Install**.



### References
