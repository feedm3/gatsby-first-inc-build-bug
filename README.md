# Gatsby first incremental build bug

> On this branch we use styled-components for the global styling. This fixes the bug.

To see the bug, run `yarn build` 3 times and check the build log.

Issue on Github: https://github.com/gatsbyjs/gatsby/issues/33450

> This code is also on CodeSandbox. You can run the yarn command in the bash console on the
bottom right terminal: https://codesandbox.io/s/gatsby-first-inc-build-bug-83pbu

## Expected

The first build needs to build all HTML files. Starting with the
second build, only incremental builds should be done. As there
is no change in data or source, the first incremental build
shouldn't rebuild any HTML page.

## Actual

The first build builts all HTML files. This is correct. The
second file rebuilts all HTML files. This is incorrect. Only
with the third and upcoming builds, no HTML pages are built anymore.

First build (full build):

```
success Building HTML renderer - 1.964s
success Building static HTML for pages - 0.389s - 3/3 12.85/s
```

Second build (first incremental build):

```
success Building HTML renderer - 1.712s
success Building static HTML for pages - 6.326s - 3/3<> 0.79/s
```

Third and upcoming builds:

```
success Building HTML renderer - 0.802s
info There are no new or changed html files to build.
```
