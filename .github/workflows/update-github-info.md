---
name: update-github-info
description: Draft website updates for Mona's GitHub Info site from official GitHub sources.
on:
  workflow_dispatch:
  schedule:
    - cron: '17 9 * * *'
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.com
    - github.blog
engine:
   id: copilot
   copilot-sdk: true
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making changes.
Do not automatically compile this workflow or regenerate its `.lock.yml` during
routine edits. Only update this Markdown source unless the user explicitly asks
for compilation.

Use these sources:
- `notes/mona-notes.md`
- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/

Update `site/content/github-info.md` with concise,
practical updates for readers and include source context when content comes
from the GitHub Blog or GitHub Changelog.

Open a pull request for Mona to review. 
Use a pull request title that mentions Mona or GitHub Info. 
Do not write directly to `main`;
rely on `safe-outputs` with `create-pull-request`.