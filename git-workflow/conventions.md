# Conventions for git usage

In our day to day with git, we follow certain conventions that make it easy for everyone to be aligned and consistent.

## Table of contents

1. [Commit Messages](#1-commit-messages)
2. [Branch names](#2-branch-names)
3. [Tag names](#3-tag-names)
4. [Special branches and branching strategy](#4-special-branches-and-branching-strategy)
5. [Merges](#5-merges)

## 1. Commit messages

**1.1.** Use commit messages in the past tense.

Commits are a snapshot of the repository status in a particular state, so the commit explains what last changes were already applied to it. It is easier to reason about what latest changes had been introduced in a particular commit.

Bad examples:

- `Updating styles`
- `Update styles`

Good examples:

- `Updated styles`
- `Refactored mainComponent.js`

**1.2.** Limit your commit message to 80 characters in the first line.

Some tools, including console and GitHub are optimized for message sizes of about 70-80 characters. If you need to add further information (which is a good idea!), leave a blank line and add the rest later on. These next lines don't have the length limitation because they are only shown when long descriptions are expected.

Bad examples:

- `Refactored mainComponent.js to avoid memory leaks on the second $scope.$digest() loop`
- `Updated mainComponent.js`

Good examples:

- Example 1:

    ```
    Refactored mainComponent.js

    Removed manual calls to $scope.$digest() to avoid events being invoked even when they already where unhooked.
    ```

- Example 2:

    ```
    Removed $scope.$digest() calls from mainComponent.js
    ```

**1.3.** Always include what changes you _did_ and not what you _intended to do_. Only time will tell if you achieved your real purpose, but the message will stay like that forever. Don't be afraid to include technical details -- this is for developers after all.

Bad examples:

- `Fixed memory leaks`
- `Fixed CFP-124`

Good examples:

- `Removed event handlers after use in main component loop`
- `Added cancellation token to async methods`

**1.4.** Final sentence period: Nope.

Bad example:

- `Removed event handlers after use in main component loop.`

Good example:

- `Removed event handlers after use in main component loop`

## 2. Branch names

**2.1.** Use lowercase and dash for word separation

Bad examples:

Good examples:

**2.2.** Avoid strange characters.

Avoid characters that could be troublesome to command interpreters at all costs (`"`, `'`, `\`, `&`, `*`, `(`, `)`, `[`, `]`, `{`, `}`).

**2.1.** Do NOT include your username or the current date in the branch name.

That information is already present in the commit itself.

Bad examples:

- `alphagit/20170303/fix-my-bug`

Good examples:

2.2. Include the ticket name


## 3. Tag names

**3.1.** Use `vM.m` and [semver](http://semver.org/) as your standard.

You can extend it to `vM.m.b`, `vM.m.b.p`, `vM.m.b.p-notes` as you see fit, but at the very least, stick to the `vM.m` (major, minor version) as a start.

## 4. Special branches and branching strategy

4.1. Keep the following branches with special meaning:

- `develop`: main development branch. Code should reach this branch after being reviewed by the proper approvers. This is where new features branches start from.
- `release`: the release candidate for your next upcoming release. If you have multiple releases happening simultaneously, feel free to have several `release-xxx` branches. (Replace `xxx` with a description that suits you.) This is where bugfixing branches for the release start from.
- `master`: the latest version of your production environment. This is where hotfix branches start from.

## 5. Merges

5.1. Avoid merge commits.

A proper exception could be when a frozen branch (like a production branch) is back-merged into the development branch. In such a case, you don't want to alter the production branch at all. For all other merges of the day to day development, look to have a linear code history.

