---
url: deploy-hugo
title: Deploy Hugo
description: Lets deploy your Hugo website to multiple destinations from one codebase. for free!
lead: Hugo is awesome and free, but hosting is often paid, with Hugo its free, lets figure it out how
date: 2022-08-18
tags:
  - "Hugo"
authorbox: false
sidebar: false
pager: false
# weight: 2
# menu: main
---

Browse this FAQ page to find answers to frequently asked questions about the golang-book.

<!--more-->


## To deploy Hugo in Github pages

The main difference is you need to setup the `baseURL` to match your github pages for example this books base url is "https://mohamedallam1991.github.io/golang-book"

Secondly you need an action, to deploy the master/main branch to gh-pages branch, which turns into a breathing website, you can find the gh-pages in Github marketplace, other Hugo themes or Hugo documentation but here is an example

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches:
      - master
jobs:
  deploy:
    runs-on: ubuntu-20.04
    steps:
      - uses: actions/checkout@v3
        with:
          submodules: true  # Fetch Hugo themes (true OR recursive)
          fetch-depth: 0    # Fetch all history for .GitInfo and .Lastmod

      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2.5.0
        with:
          hugo-version: 'latest'
          extended: true

      - name: Build
        run: hugo --minify


    # push the generated content into the `gh-pages` branch.
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3.8.0
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_branch: gh-pages
          publish_dir: ./public
```

## Netlify
To deploy to netlify its easy, all you need is a cnofiguration file in your main Hugo repository, and here is main for this project.
I want to point out, the `-b $DEPLOY_PRIME_URL` at the end of the Hugo command, is to deploy to whatever is your Netlify URL, if you dont specify, Netlify will use your-github/github.io/yourrepo, which shows a borken links. so be careful

```toml
[build]
#   command = "cd exampleSite && hugo --gc --minify -D -b $URL"
  command = "git submodule update --remote --merge && hugo --gc --minify -D -b $DEPLOY_PRIME_URL"
  publish = "public"

[context.production.environment]
HUGO_VERSION = "0.100.2"
HUGO_ENV = "production"
HUGO_ENABLEGITINFO = "true"

[context.deploy-preview]
command = "hugo --gc --minify -D -b $DEPLOY_PRIME_URL"

[context.deploy-preview.environment]
HUGO_VERSION = "0.100.2"

[context.branch-deploy]
command = "npm run build && hugo --gc --minify -D -b $DEPLOY_PRIME_URL"

[context.branch-deploy.environment]
HUGO_VERSION = "0.100.2"

```

## Get yourName.pages.dev
Cloudflare deploy to `your project name.pages.dev` which is cool.
To do that:
- Just like netlify specify the base url in the Hugo command `hugo --gc --minify -D -b $CF_PAGES_URL` the CF (cloudflare) pages url.

- Sepcify your Hugo version into the variables `HUGO_VERSION` `0.100.2`

```
Build command: hugo --gc --minify -D -b $CF_PAGES_URL
Build output directory: /public
Root directory: /
```


Thats all there is to it
