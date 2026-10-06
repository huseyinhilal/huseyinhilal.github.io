+++
date = '2026-10-06T11:30:00+03:00'
draft = false
title = 'Rebuilding My Blog: What I Got Wrong with Hugo and GitHub Pages'
tags = ['hugo', 'git', 'github-pages']
+++

My first attempt at this blog followed a tutorial that used **two repositories**: one for the Hugo source and one for the generated HTML, linked with a git submodule. It never worked the way I wanted. This post is a short record of why, and what I changed.

## What went wrong

1. **Wrong `baseURL`.** I had written the repository URL instead of the site URL:

   ```toml
   # wrong
   baseURL = 'https://huseyinhilal.github.io.git/'
   # right
   baseURL = 'https://huseyinhilal.github.io/'
   ```

2. **Local preview code ended up in the published site.** The output of `hugo server` was written into `public/`, including a `livereload.js` script that only works on `localhost:1313`.

3. **The second push was forgotten.** With a submodule you have to commit and push `public/` first, then the parent repo. I pushed the parent and forgot the submodule, so the site never changed.

4. **Line endings.** Windows (CRLF) and Linux (LF) line endings made `git status` show 20 changed files when nothing had actually changed.

## The new setup

| | Old | New |
|---|---|---|
| Repositories | 2 + submodule | 1 |
| Who builds the site | Me, locally | GitHub Actions |
| Pushes per post | 2 | 1 |
| `public/` in git | Yes | No |

Now the whole workflow is:

```bash
hugo new content posts/my-post.md   # create
hugo server                         # preview at localhost:1313
git add . && git commit -m "new post" && git push   # publish
```

GitHub Actions builds the site on every push to `main` and deploys it to GitHub Pages.

> Lesson: when a tutorial makes you do the same step in two places, that is where things will break.

## Next

I plan to use this blog for two things: posts about what I learn, and a short developer journal.
