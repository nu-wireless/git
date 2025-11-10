# Northeastern University Wireless Club (W1KBN) Intro to Git Workshop

Welcome to the repository for the Northeastern University Wireless Club Intro to Git Workshop.

This repository contains the slide deck and related materials used for our Intro to Git Workshop.

## Download the Workshop Files

To follow along with the workshop, please download the demo `index.html` file and the precompiled slide deck `2025-fall-nuwc-git.pdf` from the Releases section:

https://github.com/nu-wireless/git/releases/tag/2025-fall

---

## Workshop Instructions

### Using the Demo `index.html` File

We will be providing you with a demo `index.html` file for this workshop.
The goal is not to teach HTML.
The goal is to give you a simple file you can edit while learning Git, commit your changes, and, if time allows, publish it using GitHub Pages so you leave with something you can show.

You do not need to know HTML or web design.
Just look for the `<!-- EDIT HERE -->` comments inside the file and fill in your own information.

---

## What you will do with `index.html`

1. Download the ZIP file from the Releases section.

2. Extract the ZIP file to your computer (for example, your Downloads folder).

3. Locate the `index.html` file inside the extracted folder.  
**Only this file will be used during the workshop.**  
Do not upload the slide deck (`2025-fall-nuwc-git.pdf`) or the entire ZIP file to your repository.

4. Create a new repository on your GitHub account. This will be your remote repository. When you clone it, Git creates your local repository on your computer, and GitHub stores a remote copy that you can push to and pull from.  
You may name it anything you like for now. If you decide to publish your page with GitHub Pages later, you can either use this same repository or create a second one specifically for GitHub Pages.

5. Add the `index.html` file into your new repository. You can drag and drop it through GitHub’s upload interface or place it in your local clone.

6. Open `index.html` in any text editor and edit only the sections marked with `<!-- EDIT HERE -->`.

   * Replace placeholder text such as your name, major, interests, or links.
   * Remove the “MODIFY AS NEEDED” pill once you customize your skill tags.

7. Use Git to stage, commit, and push your changes.
   The example below is only one of many commands you will practice in the workshop.

   ```bash
   git add index.html
   git commit -m "personalize my webpage"
   git push
   ```

8. If time permits, follow the Hosting Your Page instructions below to publish your webpage on GitHub Pages.

---

## Hosting Your Page on GitHub Pages (if time allows)
You can publish your page using either the repository you already created or by creating a new one.

* Option 1 requires a very specific repository name, so some students may choose to create a second repository for that method.  
* Option 2 works with any repository name, including the one you are already using.

There are two simple options. We will guide you through both during the workshop.

### Option 1: The simplest method

Create a repository named `yourusername.github.io`.

1. Create a new public repository named exactly:

   ```
   yourusername.github.io
   ```
2. Add `index.html` to the root of the repository.
3. Commit and push.

Your site will then be available at:

```
https://yourusername.github.io
```

---

### Option 2: Any repository name

1. Use any repository name you prefer.
2. Add `index.html` to the root of the repository.
3. Go to:
   Settings > Pages
4. Under "Build and deployment", select:

   * Source: Deploy from a branch
   * Branch: main
   * Folder: root or docs

GitHub will generate a link to your site after it builds.
This usually takes about one minute.

---

## What you should walk away with

By the end of the workshop, you should have:

* Used real Git commands on a real file
* Learned how to push changes to GitHub
* Optionally published a personal webpage
* Created something small but polished that you can show others
* Gained a working understanding of Git fundamentals

The focus is Git, not HTML.
The HTML file is simply a hands-on way to practice and leave with something you can be proud of.

---
## Compiling the Slides Yourself

### Intended Audience

This repository is primarily maintained by the Wireless Club Workshop Team.

The public can view the precompiled slide deck, but local compilation is primarily intended for officers. Successful compilation requires invoking the `--shell-escape` flag during build, as the source uses it to execute a Git command that retrieves the current commit hash for the footer.

To compile successfully, you must have a local clone of the repository that includes the `.git` directory. The build process depends on this metadata to parse the Git commit head through the `\iexec` command.

If you only download `main.tex` or a ZIP archive from GitHub, the `.git` directory will be missing and the version hash in the footer will not render correctly. In that case, you can still compile the slides by creating your own repository or removing the versioning command from the footer.

Officers with repository access can clone and compile directly. External users would need to fork or create their own repository to do the same.

---

### Requirements

To compile the slide deck locally, make sure you have:

* A clear distribution such as TeX Live, MiKTeX, or MacTeX
* The `minted` package
  (requires Python and Pygments; compile with the `--shell-escape` flag)
* A LaTeX editor such as VS Code with the
  [LaTeX Workshop extension](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop), TeXstudio, or TeXShop

---

### Why Local Compilation Is Required

This presentation cannot be built online (such as on Overleaf) because it needs the `--shell-escape` flag, which allows LaTeX to execute external commands.
To my knolwedge, Overleaf does not support user projects that invoke shell commands during compilation.

The `--shell-escape` flag is needed because of the following command defined in the source:

```latex
\usepackage{iexec}
\newcommand{\gitAbbrevHash}{\iexec{git rev-parse --short HEAD}}
```

The `iexec` package runs the system command `git rev-parse --short HEAD` to automatically insert the current commit hash into the footer.
This requires both Git and a repository clone with its `.git` directory intact.
If you download only `main.tex` without the `.git` folder, the command will not return anything, and the “Version” field in the footer will be blank.

---

### How to Compile

1. Clone the repository

2. Compile using `pdflatex` (or any compiler) with the shell escape flag

   ```bash
   pdflatex --shell-escape main.tex
   ```

   If you are using VS Code with LaTeX Workshop, make sure the `--shell-escape` flag is included in your build recipe.

   I personally have only ever compiled this slide deck with pdflatex, so I cannot speak for lualatex or any otehr compilers.

---

## Repository Structure

```
.                    
├── assets/          # Assets used in the slide deck
│   ├── branching.png
│   ├── git-logo.png
│   ├── git-snapshot.png
│   └── xkcd-git-comic.png
├── demo/
│   └── index.html   # Demo HTML file for workshop participants
├── README.md        # This README file
└── main.tex         # Main Beamer slide deck source file
```

---

## Troubleshooting

* **Blank version field in footer:** You are compiling outside a Git repository or missing the `.git` directory. You either need to be an officer with push access or create your own Git repo.
* **Error's mentioning shell escape** Re-run compilation with the `--shell-escape` flag.

---

## Questions

If you have any questions or feedback, please reach out:
* Contributor's Email: [elarbi.m@northeastern.edu](mailto:elarbi.m@northeastern.edu)
* Workshop Email: [workshops@nuwireless.org](mailto:workshops@nuwireless.org)
* Club Website: [https://nuwireless.org](https://nuwireless.org)

---

## License

This project is licensed under the
[**Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License**](https://creativecommons.org/licenses/by-nc-sa/4.0/). <img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1" alt=""> <img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1" alt=""> <img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/nc.svg?ref=chooser-v1" alt=""> <img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/sa.svg?ref=chooser-v1" alt="">
