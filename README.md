![Arrow Banner](https://github.com/Arrow-air/.github/raw/main/profile/assets/arrow_v2_twitter-banner_neu.png)

# APP_NAME Front-end

*TODO after cloning:*

1. *Replace the repository name for each:*

![Sanity Checks](https://github.com/arrow-air/web-template-nuxt/actions/workflows/sanity_checks.yml/badge.svg?branch=main)
![Arrow DAO Discord](https://img.shields.io/discord/853833144037277726?style=plastic)

2. *Grep for 'template' in all files, replace with name of this service*
3. *Remove this and previous numbered bullets*

## Setup

Install dependencies:

```bash
yarn install
```

## Development

```bash
yarn dev
```

## Static Generation

Use the `generate` command to build your application.

The HTML files will be generated in the .output/public directory and ready to be deployed to any static compatible hosting.

```bash
yarn generate
```

## Preview build

You might want to preview the result of your build locally, to do so, run the following command:

```bash
yarn preview
```

## Running on iOS

MAKE SURE YOU ARE CONNECTED TO RELIABLE INTERNET.

If this is the first time running the app, run `npx cap add ios` to add
the iOS platform.

Run `npx cap open ios` to open the project in Xcode. Then, add the
following to your `info.plist`:

```
Privacy - Location Always Usage Description
Privacy - Location When In Use Usage Description
Privacy - Camera Usage Description
Privacy - Photo Library Additions Usage Description
Privacy - Photo Library Usage Description
```

To run in a simulator, `yarn ios`.

Note: it's always easier to run the app from XCode than using the `npx`
commands.
