---
name: update-github-info
description: Keep the GitHub Info page current with practical updates from the GitHub Blog and Changelog.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
engine:
  id: copilot
  copilot-sdk: true
tools:
  edit: true
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    draft: false
    allowed-files:
      - site/content/github-info.md
---

# Update GitHub Info

Read `notes/mona-notes.md` and the existing `site/content/github-info.md`. Fetch:

- https://github.blog/latest/
- https://github.blog/changelog/

Use recent, relevant information from those official sources to update `site/content/github-info.md`. Keep the guidance short and practical for developers, preserve its focus on GitHub collaboration, Copilot, and Actions, and cite each Blog or Changelog source used with a link. Do not add claims that the fetched sources do not support.

When there is a useful update, edit only `site/content/github-info.md` and use the `create-pull-request` safe output to open a pull request for Mona to review. Give the PR a clear title and summarize the changes and linked sources in its description. Do not write directly to the default branch. If neither source supports a meaningful update, use `noop` with a brief reason instead of opening an empty PR.
