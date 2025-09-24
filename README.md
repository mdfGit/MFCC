Using Github pages, Hugo generated PaperMod theme

Prerequisites
* git
* go
* dart sass
See: https://gohugo.io/installation/macos/
Also See: https://gohugo.io/getting-started/quick-start/
Also See: https://gohugo.io/host-and-deploy/host-on-github-pages/

1. Set up your Hugo Site with PaperMod:
Install Hugo: Follow the official Hugo documentation to install Hugo on your system.
Create a new Hugo site:

> hugo new site <your-site-name>
> cd <your-site-name>

Add PaperMod as a Git submodule: This is the recommended method for managing themes.

> git init
> git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod

Configure your hugo.toml (or config.toml): Add theme = "PaperMod" to your configuration file. You may also want to configure other PaperMod specific settings as outlined in its documentation.

Create content: Add your blog posts or pages in the content directory.

Test locally: Run hugo server to preview your site and ensure everything is working as expected.

2. Prepare for GitHub Pages Deployment:
Initialize a Git repository (if you haven't already):

> git init

Create a .gitignore file: Include public/ to prevent committing the generated site files to your source repository, as GitHub Pages will build them.

  # .gitignore
  public/

Commit your source files.

> git add .
> git commit -m "Initial Hugo site with PaperMod"

Create a GitHub repository: Create a new public repository on GitHub.
Link your local repository to GitHub:

> git remote add origin <your-github-repo-url>
> git push -u origin main

3. Deploy to GitHub Pages:
Manual Deployment (if not using Actions):
Generate your static site:

> hugo

This creates the public/ directory containing your built website.
Create a separate gh-pages branch (or main if deploying from the root):

> git checkout -b gh-pages
> git add -f public
> git commit -m "Deploying to GitHub Pages"
> git subtree push --prefix public origin gh-pages

(Alternatively, if deploying from the main branch and using a docs folder or the root, adjust your GitHub Pages settings.)

Configure GitHub Pages: In your GitHub repository, go to Settings > Pages. Under "Source," choose the branch (e.g., gh-pages) and the folder (e.g., /root or /docs) where your built site resides.

Your Hugo site with PaperMod should now be accessible via your GitHub Pages URL (e.g., username.github.io/repository-name or username.github.io for a user site).

