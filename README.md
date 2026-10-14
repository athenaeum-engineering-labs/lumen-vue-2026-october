# Lumen Vue 2026, October

Three Vue 3 projects from the October 2026 course, each packed into a single `.bundle` file with its full history: every branch, every commit. You don't need access to the original GitHub repositories; the bundle *is* the repository.

The projects are listed below from the simplest to the most complex. If you're working through them on your own, go in that order.

---

## What a bundle is

A git bundle is a whole repository in one file. Git can clone from it exactly as it clones from GitHub, so once you've cloned a bundle you have a normal git repository: you can read the history, switch branches and commit your own work.

## What you need

- **Git**, any recent version (`git --version`).
- **Node.js** 22.18 or later, or 24.12 or later (`node --version`), which brings `npm` with it.
- **An editor.** VS Code with the **Vue (Official)** extension works well, and the **Vue.js devtools** browser extension helps you see what your components are doing.
- **An internet connection** for `npm install`, and for the branches that call a public demo API (noted below).

## How to use a bundle

These steps use `lumen-vue2026-playground` as the example. Every project works the same way; its own commands are in its section further down.

### 1. Get the bundles

Download this repository (the green **Code** button, then **Download ZIP**, and unzip it), or clone it:

```bash
git clone https://github.com/athenaeum-engineering-labs/lumen-vue-2026-october.git
cd lumen-vue-2026-october
```

### 2. Clone the project from its bundle

```bash
git clone lumen-vue2026-playground.bundle
cd lumen-vue2026-playground
```

This makes a folder named after the bundle, with the `main` branch checked out. `main` is the starting point: a fresh Vite + Vue 3 + TypeScript project.

### 3. See its branches

```bash
git branch -r
```

You'll see one `origin/<branch>` line per branch: every branch is already in your clone. Each branch is one topic, numbered in the order it was taught.

### 4. Switch to a branch

```bash
git switch 05-list-rendering
```

The first time, this turns `origin/05-list-rendering` into a local branch of the same name and checks it out. Switch back with `git switch main`.

To clone straight onto a branch instead, use `-b`:

```bash
git clone -b 05-list-rendering lumen-vue2026-playground.bundle
```

### 5. Install and run

```bash
npm install
npm run dev
```

Open the address it prints (usually `http://localhost:5173`). The page reloads as you edit the code.

**Run `npm install` again every time you switch branches.** Some branches add libraries (Bootstrap, Vue Router, Axios, FormKit, Pinia), and switching branches changes `package.json` but not your `node_modules` folder.

Every branch is a complete, runnable snapshot of its topic, so you can jump straight to any one of them.

### About `npm run build`

`npm run build` type-checks the code with `vue-tsc` before it builds. On a few branches the type check reports errors (listed under each project below), so `npm run build` stops there even though the app runs fine. To build those branches anyway, skip the type check:

```bash
npm run build-only
```

Fixing those type errors is a good exercise.

### Check a bundle (optional)

From inside any git repository (for example, a project you've just cloned):

```bash
git bundle verify ../lumen-vue2026-playground.bundle
```

It should say `... is okay`, list the bundle's branches, and say `The bundle records a complete history.`

### Keep your own copy on GitHub (optional)

Your clone's `origin` points at the bundle file. To push your work to a repository of your own:

```bash
git remote set-url origin https://github.com/<you>/<repository>.git
git push -u origin --all
```

Pushing every branch this way needs a local copy of each one, so `git switch` to each branch first.

---

## The projects, from simplest to most complex

### 1. lumen-vue2026-playground

**What it does:** the Vue 3 fundamentals, one idea per branch, all in a single `Playground` component written with `<script setup>`. It starts with showing a value and handling a click, moves through conditionals, lists, computed values and styling, then builds a small to-do list and splits it into components that talk to each other through props, events and slots.

**Branches:**

| Branch | Topic |
|---|---|
| `main` | A fresh Vite + Vue 3 + TypeScript project |
| `01-simple-value-binding` | `ref` and showing a value with `{{ }}` |
| `02-event-binding` | Handling a click with `v-on:click` and its shorthand `@click` |
| `03-conditionals` | `v-if` and `v-else` |
| `04-conditionals-1` | `v-else-if` chains, `v-show`, and `v-if` on a `<template>` group |
| `05-list-rendering` | `v-for` over arrays, arrays of objects, and an object's properties |
| `06-computed-properties` | `computed` values |
| `07-working-with-styles` | Adding Bootstrap; `:class` and `:style` bindings |
| `08-styles-2` | Object syntax for classes, and classes from a computed value |
| `09-use-case-1` | A to-do list with a summary |
| `10-composition-and-communication` | Splitting the to-do list into `Summary` and `TodoTable` components |
| `11-content-projection-with-slots` | A `Container` component that takes content through a `<slot>` |
| `12-named-slots` | Named slots |

```bash
git clone lumen-vue2026-playground.bundle
cd lumen-vue2026-playground
git switch 01-simple-value-binding
npm install
npm run dev
```

On branches `01` to `09`, `npm run build` stops at the type check, because `Playground.vue` is written in plain JavaScript (`<script setup>` without `lang="ts"`). Use `npm run dev`, or `npm run build-only`.

### 2. lumen-vue2026-advanced

**What it does:** the next layer of Vue, on a Bootstrap-styled app. Component lifecycle and catching errors, everything you can do inside a template, routing from the basics to nested routes, talking to a REST API with Axios, forms with FormKit, and how `reactive` differs from `ref`.

**Branches:**

| Branch | Topic |
|---|---|
| `main` | A fresh Vite + Vue 3 + TypeScript project with a `Playground` component |
| `01-setup-bootstrap` | Adding Bootstrap, and showing or hiding a component |
| `02-life-cycle-hooks-and-error-handling` | Lifecycle hooks (`onMounted`, `onUpdated`, `onUnmounted` and more), and catching a component's errors with `onErrorCaptured` |
| `03-template-interpolation` | Raw HTML with `v-html` (and why it's risky), attribute binding, dynamic attribute and event names, and event modifiers |
| `04-basic-routing` | Vue Router: routes, a navigation bar, and a not-found page |
| `05-advanced-routing-techniques` | Named routes, aliases, redirects, lazy-loaded pages, and route parameters |
| `06-routing-techniques-2` | Nested routes (a dashboard with its own child pages), and passing route parameters to a component as typed props |
| `07-http-communication` | Calling a REST API with Axios |
| `08-forms-using-formkit` | Contact, login and profile forms with FormKit, with validation |
| `09-other-features` | Two-way binding with `v-model`, `reactive` objects, and scoped styles |

```bash
git clone lumen-vue2026-advanced.bundle
cd lumen-vue2026-advanced
git switch 01-setup-bootstrap
npm install
npm run dev
```

`07-http-communication` calls the public demo API at `jsonplaceholder.typicode.com`.

Two branches stop `npm run build` at the type check; use `npm run dev`, or `npm run build-only`:

- `02-life-cycle-hooks-and-error-handling` on purpose: its **Crash!** button reads a variable that doesn't exist, so you can watch `onErrorCaptured` catch the error.
- `08-forms-using-formkit` because `formkit.config.ts` imports a type without `import type`.

### 3. lumen-vue2026-ancillary

**What it does:** what a real app needs around its components. Shared state with Pinia, from a simple store to signing in against an API, unit tests with Vitest and Vue Test Utils, and packaging the app in a Docker image and deploying it to Google Cloud Run.

**Branches:**

| Branch | Topic |
|---|---|
| `main` | A fresh Vite + Vue 3 project with Pinia, Vitest, ESLint and Oxlint |
| `01-state-management-basics` | A Pinia store for a light/dark theme, saved in the browser |
| `02-advanced-state-management` | An authentication store: signing in against an API, tracking loading and errors, and keeping the token |
| `03-state-management-exercise` | Exercise: a product list fetched into a Pinia store |
| `04-unit-testing-patterns` | Unit tests with Vitest: matchers, async code, mocking functions and modules, and mounting components to test their output and `v-model` |
| `05-containerization-and-deployment` | The product app from `03`, in a Docker image served by Nginx, and deployed to Google Cloud Run |

```bash
git clone lumen-vue2026-ancillary.bundle
cd lumen-vue2026-ancillary
git switch 01-state-management-basics
npm install
npm run dev
```

Branches `02` to `05` call the public demo API at `dummyjson.com`. On `02`, the sign-in button uses DummyJSON's published demo account (`emilys` / `emilyspass`), not a real one.

On `04-unit-testing-patterns`, run the tests with:

```bash
npm run test:unit
```

It watches your files and re-runs the tests when you save. To run them once and exit, use `npx vitest run`.

`05-containerization-and-deployment` also needs **Docker**. The commands for building and running the image locally are at the end of the `Dockerfile`:

```bash
docker image build --tag my-vue-app .
docker container run -d -p 9000:8080 \
    --read-only --tmpfs /tmp \
    --cap-drop ALL --security-opt no-new-privileges \
    my-vue-app
```

Then open `http://localhost:9000`. `http://localhost:9000/healthz` answers `ok` when the container is healthy.

The image is hardened. The base images are pinned to exact versions and digests, the build installs packages without running their install scripts, and Nginx runs as a non-root user. That's why it listens on port 8080, not 80. It also sends security headers, including a Content Security Policy that only lets the page talk to its own server and `dummyjson.com`. The run command above adds a read-only file system and drops every Linux capability.

The Google Cloud steps are in `gcloud-deployment-commands.txt`. They need the **Google Cloud CLI** (`gcloud`) and a Google Cloud billing account, and they **cost real money while the app is deployed**. Use your own project name in place of `my-unique-vue3-project` (project names are unique across all of Google Cloud). When you're done, delete the project, which removes everything in it and stops the charges:

```bash
gcloud projects delete <your-project-name>
```
