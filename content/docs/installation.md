---
id: installation
title: Installing Bit
permalink: docs/installation.html
layout: docs
category: Getting Started
next: setup-authentication.html
prev: getting-help.html
---

Bit can be installed on Mac, Windows or Linux machines, and is available through various installation methods.

Once installed, verify the installation by running the following command:

```bash
bit --version
```

## NPM

Install Bit using [NPM](https://www.npmjs.com/package/bit-bin):

```bash
npm install bit-bin --global

# When installing Bit on windows, add the --no-optional fag:
npm install bit-bin --global --no-optional
```

## Yarn

Install Bit using [Yarn](https://yarnpkg.com/en/package/bit-bin):

```bash
yarn global add bit-bin
```

## macOS

### Homebrew

Bit can be installed via [Homebrew](https://brew.sh) package manager.

```bash
brew install bit
```
