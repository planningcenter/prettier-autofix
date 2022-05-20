# Prettier Auto-Fix

A composite GitHub Action that adds functionality to the [balto-prettier](https://github.com/planningcenter/balto-prettier) action.

It runs balto-prettier, commits any resulting changes, and adds that formatting commit to `.git-blame-ignore-revs`.

This is especially useful as an action to run on pull requests, keeping all of the code that lands in your main branch properly formatted while keeping formatting commits out of the way of `git blame`.

## Example Usage

As a convenience wrapper around a few other actions, it's probably worth looking at those individually and what's required.

At a minimum, you'll need to checkout the code before using this action.

```yaml
name: Auto-Fix

on: [pull_request]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
        with:
          ref: ${{ github.head_ref }}
          fetch-depth: 0
      - uses: planningcenter/prettier-autofix@v0.1
```
