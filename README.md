# Turborepo + Lerna Template
This is an official Yarn v1 starter turborepo plus Lerna for versioning/publishing packages.  

Lerna has been added to aid in versioning and publishing packages.  

## TODO:
- Setup GitHub Actions
- Setup automatic deployments
- Write documentation on maintaining package versions with Lerna
## How to setup this template
1. `npx create-turbo` (`./defifofum-monorepo-template`)
2. `cd defifofum-monorepo-template`  
3. `npm install --global lerna`  (If not installed)
4. `lerna init` (Init `lerna.json`)


## Configure VSCode
This project uses prettier/eslint to format code.

To have prettier automatically format on file saves:
1. Select VS Code -> View -> Command Palette, and type: `Format Document With`
2. Then `Configure Default Formatter`... and then choose Prettier - Code formatter.

## Package Resolutions
Package resolutions allow us to explicitly set package versions for specific packages which may be exploitable. 

1. `yarn`: install packages if not installed
2. `yarn audit`: audit packages for vulnerabilities
3. Add module version resolutions to `resolutions` field in [package.json](./package.json)
4. `yarn`: install new packages
5. `yarn audit`: verify there are no more vulnerabilities

## Create a new package
If a new package is created, the package must be configured to be able to run jest tests
1. In the new package, update the package [jest.config.js](./apps/web/jest.config.js) with the proper name
2. Update the root [jest.config.js](./jest.config.js) to include the new package in the `roots` field

## What's inside?

This turborepo uses [Yarn](https://classic.yarnpkg.com/lang/en/) as a package manager. 

Lerna and Turborepo can be [used together](https://turborepo.org/docs/guides/migrate-from-lerna) in the same monorepo. 

```
Using with Lerna
Turborepo and Lerna have a lot a in common, but also some key differences.

tl;dr you can use Lerna and Turbo together.

Use lerna symlinking (lerna bootstrap) packages, publishing and changelog generation
Use turbo for task running and caching
```

It includes the following packages/apps:

### Apps and Packages

- `docs`: a [Next.js](https://nextjs.org) app
- `web`: another [Next.js](https://nextjs.org) app
- `ui`: a stub React component library shared by both `web` and `docs` applications
- `config`: `eslint` configurations (includes `eslint-config-next` and `eslint-config-prettier`)
- `tsconfig`: `tsconfig.json`s used throughout the monorepo

Each package/app is 100% [TypeScript](https://www.typescriptlang.org/).

### Utilities

This turborepo has some additional tools already setup for you:

- [TypeScript](https://www.typescriptlang.org/) for static type checking
- [ESLint](https://eslint.org/) for code linting
- [Prettier](https://prettier.io) for code formatting

## Setup

This repository is used in the `npx create-turbo` command, and selected when choosing which package manager you wish to use with your monorepo (Yarn).

### Build

To build all apps and packages, run the following command:

```
cd defifofum-monorepo-template
yarn run build
```

### Develop

To develop all apps and packages, run the following command:

```
cd defifofum-monorepo-template
yarn run dev
```

### Remote Caching

Turborepo can use a technique known as [Remote Caching (Beta)](https://turborepo.org/docs/features/remote-caching) to share cache artifacts across machines, enabling you to share build caches with your team and CI/CD pipelines.

By default, Turborepo will cache locally. To enable Remote Caching (Beta) you will need an account with Vercel. If you don't have an account you can [create one](https://vercel.com/signup), then enter the following commands:

```
cd defifofum-monorepo-template
npx turbo login
```

This will authenticate the Turborepo CLI with your [Vercel account](https://vercel.com/docs/concepts/personal-accounts/overview).

Next, you can link your Turborepo to your Remote Cache by running the following command from the root of your turborepo:

```
npx turbo link
```

## Useful Links

### Turborepo

Learn more about the power of Turborepo:

- [Pipelines](https://turborepo.org/docs/features/pipelines)
- [Caching](https://turborepo.org/docs/features/caching)
- [Remote Caching (Beta)](https://turborepo.org/docs/features/remote-caching)
- [Scoped Tasks](https://turborepo.org/docs/features/scopes)
- [Configuration Options](https://turborepo.org/docs/reference/configuration)
- [CLI Usage](https://turborepo.org/docs/reference/command-line-reference)

## Lerna

Learn about the useful commands Lerna offers.

- [lerna.js.org](https://lerna.js.org/)
- [Github README](https://github.com/lerna/lerna) (Explains commands)
- [Fixed/Locked Mode](https://github.com/lerna/lerna#fixedlocked-mode-default)