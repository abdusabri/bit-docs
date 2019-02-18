---
id: building-components
title: Building Components
permalink: docs/building-components.html
layout: docs
category: Getting Started
next: testing-components.html
prev: tag-component-version.html
---

Each component has a build task defined. Bit uses it to compile a component in a workspace.

## Basics of Building Components

A component contains source code. Sometimes source code requires a compilation process to be usable. Bit compiles source code using a unique components called Compilers. A Compiler is a component that takes another component’s code and uses other build tools to compile it.

### Where is the code compiled?

Bit builds components in an [isolated component environment](/docs/ext-concepts.html#what-is-an-isolated-component-environment). Bit does it to ensure true isolation of components. If a build process works, Bit can reproduce it anywhere.

## Defining a Compiler

Every component can have a compiler. Bit uses a global compiler configuration for a workspace. Bit propagate the global configuration to each component tracks in that workspace.  
Configured a global compiler with the `--compiler` flag when importing a compiler component.

```bash
$ bit import bit.envs/compilers/babel --compiler
the following component environments were installed
- bit.envs/compilers/babel@0.0.7
```

## Building a component

Use [bit build](/docs/cli-build.html) to build components that have a compiler:

```bash
$ bit build foo/bar
foo/bar
dist/foo/bar.js
dist/foo/bar.js.map
```

> **Set dist target and entry**
>
> It's possible to set `dist` target and entry by editing the [bit.json](/docs/conf-bit-json.html).

## Compilers maintained by bitsrc.io

Find a list of Compilers maintained by the [bitsrc.io](https://bitsrc.io) [here](https://bitsrc.io/bit/envs).

- [Babel](https://bitsrc.io/bit/envs/compilers/babel).
- [Flow](https://bitsrc.io/bit/envs/compilers/flow).
- [Preact](https://bitsrc.io/bit/envs/compilers/preact).
- [React](https://bitsrc.io/bit/envs/compilers/react).
- [TypeScript](https://bitsrc.io/bit/envs/compilers/typescript).