---
title: "Streamline Scientific Writing with VS Code + Zotero + Github"
layout: post
usemathjax: true
---

*Check this out*
INCLUDE GIF HERE
*Pretty neat, right?*

What you just saw above was the ability to save an article off the web, and immediately cite it in your paper with fully integrated git providing version history + backups. This guide will show you how to configure Visual Studio Code (VS Code) and Zotero together to work together automatically, and if you're hesitant to take the leap from Overleaf, consider the following:
* You'll be able to edit / compile your work entirely locally
* Git integration means neat collaboration + version history (something overleaf *tries* to do and locks most of behind a paywall)
* No more compilation timeouts
* A fully customizable environment

### Pre-requisites
This guide is aimed at macOS users, see the [References](#references) section for Windows help. Below is some other requirements:
1. A basic understanding of writing in LaTeX.
2. A free [Zotero](https://www.zotero.org/) account, with the [desktop app and browser "connecter" extension](https://www.zotero.org/download/)
3. [VS Code](https://code.visualstudio.com/Download) downloaded.
Even if you don't fully know how to use each of these components yet, I'll walk you through getting started with them.

---
## Getting a LaTeX Distribution
All the work will be done on VS Code, but we need a distribution of LaTeX behind the curtain for VS Code to use. TeXLive is **strongly recommended** for working with LaTeX-Workshop, the VS Code extension we'll set up later, and the easiest way to do this for macOS machines is with MacTex. You can [find the download link here](https://www.tug.org/mactex/mactex-download.html). This distribution will take almost 10 GB of space.

* The size is mainly because TeXLive contains tons of packages and fonts. If you'd like a lighter weight distribution, [LaTeX-Workshop has some alternatives under the Requirements section](https://github.com/James-Yu/latex-workshop/wiki/Install).

Once the MacTeX.pkg is downloaded, open it and follow the install instructions. **At the *Installation Type* step, select *Customize* and make sure only TeXLive-2025 is selected.** There is no issue installing the other GUI components, but they are functionally being replaced by VS Code so they are not needed.

## Setting up VS Code
With our LaTeX ready, we now need to get VS Code to work with it. The power of VS Code's customization and tools comes from its Extensions Marketplace, which we'll demonstrate how to access now. Open the primary side bar (**View > Appearance > Primary Side Bar**), and click the extensions icon. 

![Screenshot of VS Code, with the left sidebar open to the extensions tab, and James-Yu.latex-workshop entered in the extensions search bar. The editor window has the LaTeX Workshop extension open](/assets/images/2025-04-16-LaTeX-for-VScode/LaTeX-extension.png)

From there, enter `James-Yu.latex-workshop` in the search bar, select the result, and click **Install**. 

---
## Setting up Zotero
Include better bibtex, explain using the browser extension to save to collections. 

## Working with a Sample Document
In order to best see the capabilities of git and zotero, we'll need LaTeX document to test it out on. 
* Do you already have a working LaTeX project in mind? On the *Welcome* editor tab you can select *Open* and navigate to your project's home folder or select *Open Folder* from the Explorer sidebar.
  * If you haven't already, select **Initialize Repository** from the source control tab in the primary side bar to activate git tracking. This is the same as running `git init` in the terminal.
* Otherwise, you can use [this sample project off of github](https://github.com/kevScheuer/latex-sample). Follow the instructions at the bottom of the linked page to download it and open it in VS Code.

The LaTeX-Workshop extension includes a LaTeX tab in the Primary Side Bar. Select it, and you'll notice among other options the button to $\textcolor{green}{\triangleright}$ **Build LaTeX project**. $\Delta$ Test. If you're most familiar with Overleaf, this is equivalent to the *Recompile* option. If you want to mimic the Overleaf style view, you can use the *Split Editor Right* button and position your output pdf to the right, like below.

![Screenshot of VS Code's split editor view with the main.tex file on the left, and the ouptut pdf on the right](/assets/images/2025-04-16-LaTeX-for-VScode/split-view.png)

Now that we know our LaTeX build works, lets take a look at what git can do for us.

### Git Basics


(Mention the rewarp extension here as a way to get nicer git diffs)

### Zotero in VS Code


---
## Useful Extensions and Tips
If your projects tend to build quickly, consider turning on the user setting (the one setting)

Subfile magic command
If you used the example github repo to test out the LaTeX environment, you might have noticed that the first line of the `experiment.tex` subfile was a "magic" command that specified the root TeX file. When you create a new subfile you can of course write this command yourself, but LaTeX workshop simply handles the pathing for you by using the command palette option **LaTeX Workshop: Insert !TeX root magic comment** and choosing your main file.



### References
