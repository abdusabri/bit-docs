---
id: quick-start
title: Quick Start
permalink: docs/quick-start.html
layout: docs
category: Home
next: what-is-bit.html
---

Learn the basics of working with Bit to share your components and collaborate with your team.

In this tutorial, we'll go though the basics of how to use Bit in order to make components reusable. When done, you will have a component collection to use in all your projects, and share with your team or the community.

To begin, choose an existing repository containing components you’d like to share and reuse.  

You can also use one of our [example projects](/docs/example-projects.html), but we recommend starting with your own code.

Let’s get started.

### Install bit

```bash
npm install bit-bin -g
```

See more [installation methods](/docs/installation.html).

### Init Bit for your project

[Initialize a Bit workspace](/docs/initializing-bit.html) in the project’s directory.

```bash
$ cd project-directory
$ bit init
```

### Track components with Bit

Bit can [track components](/docs/add-and-isolate-components.html) in your repository, and isolates them so that they can be used in other projects.  

To track components, we’ll use the `bit add` command. In this example, we’ll use a glob pattern to track all the components in the `src/components` directory. 

```bash
bit add src/components/* # use a glob pattern or a specific path to track multiple components or a single component.
```

Bit automatically scans the files in the given path. It identifies your components, and resolves their dependencies (packages and files) so that it can isolate them and make them reusable. 

> **Tip**
>
> Use [bit status](/docs/cli-status.html) to verify that each component's dependency graph has been successfully resolved. This command provides useful information during any step of the process.  

#### Example

Let's track the components `button`, `login` and `logo` in the following project's directory structure.

```bash
$ tree
.
├── App.js
├── App.test.js
├── favicon.ico
├── index.js
└── src
    └── components
        ├── button
        │   ├── Button.js
        │   ├── Button.spec.js
        │   └── index.js
        ├── login
        │   ├── Login.js
        │   ├── Login.spec.js
        │   └── index.js
        └── logo
            ├── Logo.js
            ├── Logo.spec.js
            └── index.js

5 directories, 13 files
```

To track these files as components we can use [bit add](/docs/cli-add.html) with a glob pattern.

```bash
$ bit add src/components/*
tracking 3 new components
```

### Build and test components

Instead of having to add compiler and tester configurations for every component, Bit lets you predefine build and test environments which apply to all the components you share from a repository. 

You can use Bit’s [pre-made compilers and testers](https://bitsrc.io/bit/envs), or create your own. Learn more about [building](/docs/building-components.html) and [testing](/docs/testing-components.html) components.

#### Adding a compiler

To apply the compiler for the components in your repository, import the environment into your project using Bit (before tagging the components’ version). For example, here is how you can import the [Babel compiling environment](https://bitsrc.io/bit/envs/compilers/babel).

```
$ bit import bit.envs/compilers/babel --compiler
the following component environments were installed
- bit.envs/compilers/babel@0.0.7
```

#### Adding a tester

Bit lets you track your components’ test files alongside your components. This enables Bit to run these tests for every component, and present the results in your CLI or in [Bit’s component hub](https://bitsrc.io). 

You can [specify the component's test files](/docs/add-and-isolate-components.html#track-a-component-with-testspec-files) using the `bit add` and  `--test` flag, to let Bit know which test files should be a part of the component.

To import a testing environment which will be applied to these tests, import the environment to your project just like you’d import the compiler. For example, here is how you can import the [Mocha testing environment](https://bitsrc.io/bit/envs/testers/mocha).

```
$ bit import bit.envs/testers/mocha --tester
the following component environments were installed
- bit.envs/testers/mocha@0.0.7
```

Note that while you don’t have to add a tester to test your components, it is recommended to add a compiler to build your components.

### Versioning (Tagging) components

To lock a version for your components (and lock their dependency tree), we’ll use the `bit tag` command. It will set a semantic version for the components, making them version-immutable.  

You can tag all the components in your repository using the `--all` flag. Here is an example.

```bash
$ bit tag --all 1.0.0
3 components tagged | 3 added, 0 changed, 0 auto-tagged
added components:  components/button@1.0.0, components/login@1.0.0, components/logo@1.0.0
```

Note that when you tag your components, Bit will first run their build/test tasks to see that everything is working correctly, and only then tag the components.

### Share components to a remote collection

Now that our components are tracked and versioned, we can share them to a collection- making them organized, discoverable and reusable across our projects.

#### Create a Collection

Let’s create a collection to [host and share](/docs/organizing-components.html) our components. Head over to [Bit’s community hub](https://bitsrc.io), create a [free account](https://bitsrc.io/signup), and create a collection.

A [Collection](/docs/remote-collection.html) hosts and manages components. While it can be set up on any server, we recommend choosing Bit’s component hub, which provides better component discoverability and collaboration for your team.

Here is an [example collection](https://bitsrc.io/bit/movie-app) we've created with React UI components. Check it out.

#### Authenticate Bit CLI to bitsrc.io

Authenticate Bit CLI so it can interact with collections on [bitsrc.io](https://bitsrc.io).

Use `bit login` to open a login page in the browser. Enter your username and password and return to Bit-CLI to continue.

```bash
$ bit login
Your browser has been opened to visit: http://bitsrc.io/bit-login?redirect_uri=http://localhost:8085...
```

#### Export components

Now we are ready to [export the components](/docs/cli-export.html) in our project to the collection we created. Unlike publishing packages to package managers, this will not require any overhead or further setup.

Use the `bit export` command to share components from your project to [bitsrc.io](https://bitsrc.io). 

```bash
$ bit export user-name.collection-name  # Share components to a remote Collection
exported 3 components to collection user-name.collection-name
```

That’s it. Your components should now be available in your collection. Head over there to take a look and invite your team.

### Use components in other projects

#### Install with NPM / Yarn

All components shared with Bit can be [installed using NPM or Yarn](/docs/installing-components.html). This means every component can be used by any developer with access to it, whether they are using Bit or not.

#### Import components into a new project for parallel development

Apart from installing components using package managers, Bit lets you [import components](/docs/sourcing-components.html) into other projects.

When importing a component, Bit will source the component’s source code in that repository. Then, the component can be developed right from that repository.

To import components use the `bit import` command.

Each sourced and modified component can then be exported back to [bitsrc.io](https://bitsrc.io) as either a new version, or an entirely new component. Changes can be updated and synced across multiple repositories.

This makes it easier to maintain and modify components, and build software faster as a team.  

#### Update and sync changes

Changes to components made in different projects can be [updated](/docs/updating-sourced-components.html) and synced, and even [merged](/docs/merge-changes.html) between different repositories.

## Summary

Great! You’ve now learned the basics of Bit and can start putting it to use.  

You should now also have a collection of reusable components you and your team can use in your projects and apps. Can you think of more components to share?

Feel free to learn more through the different sections of the docs, visit [Bit on GitHub](https://github.com/teambit/bit), [discover components](https://bitsrc.io) shared by the community around in the world and invite your friends to collaborate.

For any questions don’t hesitate to [reach out](https://bitsrc.io/support) or chat with the team on [Gitter](https://gitter.im/bit-src/Bit). Happy coding!
