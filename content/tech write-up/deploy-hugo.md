---
title: 'Deploying a Blog Powered by Hugo to Netlify'
date: 2024-08-05T23:15:00+07:00
slug: deploy-hugo
category: tech
summary:
description:
cover:
  image: ''
  alt: 'Deploying a Blog Powered by Hugo to Netlify'
  caption:
  relative: true
showToc: true
draft: false
ShowReadingTime: true
tags:
  [
    'Hugo',
    'Netlify',
    'GitHub Pages',
    'Static Site Generator',
    'Web Development',
    'Custom Domain',
    'CI/CD',
    'Blogging Tools',
  ]
---

This guide explains how to set up a blog using Hugo and [PaperMod](https://github.com/adityatelange/hugo-PaperMod?tab=readme-ov-file), configure Netlify to deploy it, and link a custom domain to your Netlify site. You can also watch the step-by-step video by [theplaybook](https://theplaybook.dev/) on [YouTube](https://www.youtube.com/watch?v=_QSr2_pxIJs&ab_channel=dhij).

---

### Install Hugo

**On MacOS :**

```bash
brew install hugo
```

**On Windows :**

```bash
choco install hugo
```

**On Linux :**

```bash
sudo apt install hugo
```

---

### Create a New Site

```bash
hugo new site portfolio -f yml
```

- Run `hugo new site <site_name>` to create a new Hugo site in the `<site_name>` directory. The `-f yml` option specifies YAML for configuration instead of the default TOML files. For more details, check the [Hugo documentation](https://gohugo.io/getting-started/quick-start/).

- Leave the `baseurl` field in `config.yml` empty for now.

---

### Create a New Page

```bash
hugo new docs/test.md
```

- Generate a new page with `hugo new <filename>`.
- Open `test.md` and set `draft: false` to ensure the page renders.
- Add some content to `test.md`.
- You can preview the site locally with `hugo server` at `localhost:1313`, though it may show layout errors without a theme.

---

### Install a Theme

```bash
git init
git clone https://github.com/adityatelange/hugo-PaperMod themes/PaperMod --depth=1
git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
```

- Initialize a Git repository with `git init`.
- Install the PaperMod theme using the commands above or choose a theme from the [Hugo Themes](https://themes.gohugo.io/).

```yaml
theme: PaperMod
```

- Add `theme: PaperMod` to your `config.yml` file.

---

### Configure Netlify to Deploy the Site

#### Create a Git Repository and Initialize Git

```bash
echo "# README" >> README.md
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin <path_to_your_git_repo>
git push -u origin main
```

- Set up a Git repository on GitHub, create a README file, add the remote, and push your initial commit.

#### Set Up Netlify for Deployment

1. **Create a Netlify Account**: If you don't have a Netlify account, sign up at [Netlify](https://www.netlify.com/).

2. **Link Your Repository**: Go to the Netlify dashboard, click "New site from Git," and connect your GitHub repository.

3. **Configure Build Settings**:

   - **Build Command**: `hugo`
   - **Publish Directory**: `public`
   - **Site Name**: `<your-preferred-name>`

4. **Update `baseurl`**: In your `config.yml`, set the `baseurl` to your custom domain. Netlify enforces HTTPS, so the URL should use `https`.

```yaml
baseurl: 'https://rishabdhar.netlify.app/'
```

5. **Deploy the Site**: Netlify will build and deploy your site automatically. After deployment, Netlify will provide a URL for your site.

After committing and pushing the `config.yml` update, Netlify will rebuild and deploy your site. It might take some time for DNS changes to propagate and for your custom domain to start working.

---

> **Tomorrow's dawn heralds the Singularity**

---
