---
title: "Contribute using github"
permalink: /contribute/github
layout: single
---

All data is stored in a [github repo](https://github.com/caribank/caribank).
If you feel uncomfortable using the [`git`](https://git-scm.com/) command line tool, a [Github desktop](https://docs.github.com/en/desktop/installing-and-configuring-github-desktop) application is available for macOS and Windows.
Github-based collaboration follows [a branch-based workflow](https://docs.github.com/en/get-started/quickstart/github-flow).
That means that you work in a separate branch and only when you are happy with your changes, you [create a pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request?tool=desktop) for them to be merged into the `main` branch.
Follow these instructions to get started:

1. If you don't have an account yet, follow [these instructions](https://docs.github.com/en/get-started/onboarding/getting-started-with-your-github-account).
2. [Contact us](mailto:caribanresources@gmail.com) to be added to the caribank organization and receive access for the repo.
3. [Clone](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository) the repository to your computer(s).
4. [Create a branch](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-and-deleting-branches-within-your-repository) with your name or label. Make sure that your local clone is **always** set to that branch.


## Editing CSV files
Once you have a local copy of the data, you can edit the [CSV](https://en.wikipedia.org/wiki/Comma-separated_values) files.
To do so, [LibreOffice](https://www.libreoffice.org/) is recommended (alternative suggestions are welcome).
Make sure to specify UTF-8 encoding and separation by comma (and nothing else) in the opening dialog.
The following files are relevant:

* [reconstruction/morphs.csv](https://github.com/caribank/caribank/blob/main/reconstruction/morphs.csv) is an annotation spreadsheet
* [reconstruction/forms.csv](https://github.com/caribank/caribank/blob/main/reconstruction/forms.csv) is an annotation spreadsheet
* [reconstruction/cognatesets.csv](https://github.com/caribank/caribank/blob/main/reconstruction/cognatesets.csv) contains identified cognate sets
* [reconstruction/proto_forms.csv](https://github.com/caribank/caribank/blob/main/reconstruction/proto_forms.csv) contains reconstructed forms
* [etc/contributors.csv](https://github.com/caribank/caribank/blob/main/etc/contributors.csv) contains information about all contributors

Follow the [general annotation guidelines](http://localhost:4000/contribute/comparative) when editing CSV files.
When you are done, review your changes and submit a pull request -- it is perfectly OK to submit a pull request that only has one new annotation or a bugfix or something.

## Command line workflow
There is also an interactive CLI workflow which can be called with `make annotate` from the base directory.
It is experimental but hopefully self-explanatory.