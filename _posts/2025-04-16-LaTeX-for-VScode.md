---
title: "Streamline Scientific Writing with VS Code + Zotero + Github"
layout: post
usemathjax: true
description: "Learn how to setup an automated environment to make writing a breeze."
keywords: "LaTeX, VS Code, Zotero, GitHub, scientific writing, macOS, Better BibTeX, LaTeX with VS Code, automated citations, Zotero VS Code integration"
author: "Kevin Scheuer"
image: "/assets/images/2025-04-16-LaTeX-for-VScode/wide-preview.png"
square_image: "assets/images/2025-04-16-LaTeX-for-VScode/square-preview.jpeg"
---

*Check this out* 

<video controls autoplay loop muted style="max-width: 100%; height: auto;">
  <source src="/assets/videos/2025-04-16-LaTeX-for-VScode/clip.mp4" type="video/mp4">
  <source src="/assets/videos/2025-04-16-LaTeX-for-VScode/clip.webm" type="video/webm">
  Your browser does not support the video tag.
</video>
*Pretty neat, right?*

What you just saw above was the ability to save an article off the web, and
immediately cite it in your paper. This guide will show you how to configure
Visual Studio Code (VS Code), git, and Zotero together to automate your workflow
and make writing a breeze. Most likely, the big question on your mind is "Why
should I switch from Overleaf?", so consider the following:
* Work entirely offline
* Git integration means neat collaboration + version history (something overleaf
  *tries* to do, but locks most of it behind a paywall)
* No more compilation timeouts
* A fully customizable environment

If any of this sounds interesting to you, then read on!

### Pre-requisites
This guide is aimed at macOS users, but the [References](#references) section
includes some resources for Windows users. Some other requirements include:
1. A basic understanding of writing in LaTeX.
2. A free [Zotero](https://www.zotero.org/) account, with the [desktop app and
   browser "connector" extension](https://www.zotero.org/download/)
3. [VS Code](https://code.visualstudio.com/Download) downloaded.
    
---
## Table of Contents
- [Table of Contents](#table-of-contents)
- [Getting a LaTeX Distribution](#getting-a-latex-distribution)
- [LaTeX and Git on VS Code](#latex-and-git-on-vs-code)
- [Setting up Zotero](#setting-up-zotero)
- [Working with a Sample Document](#working-with-a-sample-document)
  - [VS Code Git Basics](#vs-code-git-basics)
  - [Zotero in VS Code](#zotero-in-vs-code)
  - [Congratulations!](#congratulations)
- [Tips](#tips)
  - [Useful VS Code Extensions:](#useful-vs-code-extensions)
  - [Settings \& Tricks](#settings--tricks)
- [References](#references)

---
## Getting a LaTeX Distribution
All the work will be done on VS Code, but we need a distribution of LaTeX behind
the curtain for VS Code to use. **TeXLive is strongly recommended** for working
with `LaTeX-Workshop`, a VS Code extension we'll set up later, and the easiest
way to do this for macOS machines is with MacTex. You can [find the download
link here](https://www.tug.org/mactex/mactex-download.html), but note this 
distribution will take almost 10 GB of space.

* The size is mainly because TeXLive contains many packages and fonts. If
  you'd like a lighter weight distribution, [LaTeX-Workshop has some
  alternatives under the Requirements
  section](https://github.com/James-Yu/latex-workshop/wiki/Install).

Once the MacTeX.pkg is downloaded, open it and follow the install instructions.
**At the `Installation Type` step, select `Customize` and make sure only
`TeXLive-2025` is selected.** There is no issue installing the other GUI
components, but we will functionally replace them with VS Code, so they aren't
needed.

---
## LaTeX and Git on VS Code
With our LaTeX ready, we now need to get VS Code to work with it. The power of
VS Code's customization and tools come from its Extensions Marketplace, which
we'll demonstrate how to access now. 
1. Open the primary side bar (**View > Appearance > Primary Side Bar**), and
   click the extensions icon. 
2. From there, enter `James-Yu.latex-workshop` in the search bar, select the
result, and click **Install**. 
   - We'll put it to use later in this guide, but we need to prepare Zotero
     first.

![Screenshot of VS Code, with the left sidebar open to the extensions tab, and
James-Yu.latex-workshop entered in the extensions search bar. The editor window
has the LaTeX Workshop extension
open](/assets/images/2025-04-16-LaTeX-for-VScode/LaTeX-extension.png)

While we're here, install these other extensions to boost our git capabilities:
1. [Github Repositories](https://marketplace.visualstudio.com/items/?itemName=GitHub.remotehub) (GitHub.remotehub)
2. [Github Pull Requests](https://marketplace.visualstudio.com/items/?itemName=GitHub.vscode-pull-request-github) (GitHub.vscode-pull-request-github)
3. [GitLens](https://marketplace.visualstudio.com/items/?itemName=eamodio.gitlens) (eamodio.gitlens)

---
## Setting up Zotero
<div style="display: flex; align-items: flex-start; gap: 40px;">
  <div style="flex: 1.5;">
    As you saw in the intro, we want our setup to auto-export a newly saved 
    citation to wherever our project is. We'll need Better BibTex to do this, 
    and the <a 
    href="https://retorque.re/zotero-better-bibtex/installation/index.html">
    easy install instructions can be found here</a>. As mentioned, make sure 
    you are installing this in the standalone Zotero application. If you're new 
    to Zotero and haven't made a collection yet, open the app and click the 
    <i>Add Collection</i> icon in the upper-left corner of the window.

    Now in your browser when you find a cool new paper, <a 
    href="https://arxiv.org/abs/2005.14272">like this one on the GlueX Detector</a>, 
    you can use the Zotero browser extension to easily save it to your collection.
  </div>
  <div style="flex: 1;">
    <img src="/assets/images/2025-04-16-LaTeX-for-VScode/collections.png" 
    alt="Screenshot showing the Add Collection icon placed above the My Library 
    drop-down menu" style="max-width: 50%; height: auto;">
  </div>
</div>

![Screenshot of an arxiv page, with the Zotero browser extension GUI open in the
upper right-hand corner](/assets/images/2025-04-16-LaTeX-for-VScode/arxiv.png)

---
## Working with a Sample Document
To best see the capabilities of git and Zotero, we'll need a LaTeX
document to test it out on.
* Do you already have a working LaTeX project in mind? On the *Welcome* editor
  tab you can select `Open` and navigate to your project's home folder, or select
  `Open Folder` from the Explorer tab on the sidebar.
  * If you haven't already, select `Initialize Repository` from the source
    control tab in the primary side bar to activate git tracking. This is the
    same as running `git init` in the terminal.
* Otherwise, you can use [this sample project off of
  github](https://github.com/kevScheuer/latex-sample). Follow the instructions
  at the bottom of the linked page to download it and open it in VS Code.
  * Note that it will automatically suggest the extensions listed in this
    tutorial and have a `settings.json` with the settings I'll suggest later.

The LaTeX-Workshop extension includes a LaTeX tab in the Primary Side Bar.
Select it, and you'll notice among other options the button to
$\textcolor{green}{\triangleright}$ **Build LaTeX project**. If you're most
familiar with Overleaf, this is equivalent to the *Recompile* option. If you
want to mimic the Overleaf style view, use the *Split Editor Right* button and
position your output pdf to the right, like below.

![Screenshot of VS Code's split editor view with the main.tex file on the left,
and the output pdf on the
right](/assets/images/2025-04-16-LaTeX-for-VScode/split-view.png)

Now that we know our LaTeX build works, let's take a quick look at what git can
do for us.

### VS Code Git Basics
If you've made any edits to your document, you may have noticed an
$\textcolor{#9E8D71}{\text{M}}$ appear next to your filename, and some textures
appear next to the line numbers that can expand to show you changes. 

![Screenshot of VS Code with the sidebar open to Source Control, and changes
made to the LaTeX document
highlighted](/assets/images/2025-04-16-LaTeX-for-VScode/git-changes.png)

If you navigate to the *Source Control* tab in the primary side bar, you'll see
that file is now listed under *Changes*. This tab is essentially your `git
status` view, where you can view changes and commit them, and push or pull
commits from a remote repository. You can access old commits, allowing you to
view and even revert to older versions of your project.


### Zotero in VS Code
We're in the home stretch now, only a few more steps to go. 
1. In Zotero, right-click on a collection and select `Export Collection`, which
   opens a dialog box. 
2. Select `Better BibTeX` for the format, and ensure `Keep Updated` is selected.   
3. Save the file in your LaTeX project, or if you're using the sample project
   from earlier you can replace the `bibliography.bib` file there with it. 
   
Now whenever a paper is added to the collection in Zotero, it will sync with
this file and the paper will be available to cite!
* For more info on how the auto-export works, [details can be found
  here](https://retorque.re/zotero-better-bibtex/exporting/auto/)

Since better BibTeX will auto-generate citation keys, they can make it a little
clumsy to find your paper, but the [Zotero LaTeX
extension](https://marketplace.visualstudio.com/items/?itemName=bnavetta.zoterolatex)
(bnavetta.zoterolatex) can fix that. 
* Note this extension uses `autocite` as its LaTeX citation command by default,
  which won't work with the `natbib` package (this is used in the example LaTeX
  project). You can change this to `cite`, or whatever command you need it to
  be, at `zotero.latexCommand` in VS Code's user settings.

With the extension added, go to your LaTeX project in VS Code and press `Alt+z`
to open a dialog box that allows you to search for any papers in your library.
Note: you need to have the Zotero app open while using this extension. 

![Screenshot of VS Code with a Zotero search dialog box open](/assets/images/2025-04-16-LaTeX-for-VScode/zotero_linker.png)

### Congratulations!
You are all done, and now have automated citation handling with built-in version
control with git! Below I've listed some other tips that are not necessary, but
you may find useful for this setup. If you have any comments / questions please
feel free to reach out to me via email at <scheuer.ks@gmail.com>. Happy writing!

---
## Tips
### Useful VS Code Extensions:
* The [Rewrap
  extension](https://marketplace.visualstudio.com/items/?itemName=dnut.rewrap-revived)
  (dnut.rewrap-revived) wraps text according to the VS Code ruler
  `editor.rulers` in the settings. This has two benefits:
  1. Better git differences - Git will check for changes line-by-line, so if an
     entire paragraph is on one line then any changes to it means git will flag
     the entire paragraph as being changed. Rewrap will put everything on a new
     line (this doesn't affect the output).
  2. Easier split view - I typically have the output pdf open in split view, and
  when editing on my small laptop screen it can get annoying having to scroll
  to see long lines of text.
* [Code Spell
  Checker](https://marketplace.visualstudio.com/items/?itemName=streetsidesoftware.code-spell-checker)
  (streetsidesoftware.code-spell-checker) works just as well for documents,
  flagging any typos you may have
  * It will flag typos as a `Problem` by default, which I find annoying. You can
    turn this off by changing `cSpell.diagnosticLevel` to *Hint*.

### Settings & Tricks
* If your projects tend to build pretty quickly, consider changing the
 user setting `latex-workshop.latex.autoBuild.run` to build `onSave`.
* If you used the sample LaTeX project, you may have noticed the use
of subfiles and the `% !TeX root = ../../main.tex` magic command 
placed at the top of the `experiment.tex` subfile, which instructs 
what file is to be built. If you make new subfiles, they can be easily 
inserted from the command palette using 
`LaTeX Workshop: Insert !TeX root magic comment`.


## References
* [This reddit thread gave me the original idea, and contains some instructions
  for Windows
  support](https://www.reddit.com/r/LaTeX/comments/10hrwd7/using_latex_with_vs_code_zotero_and_github/)