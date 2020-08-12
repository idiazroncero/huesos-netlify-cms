# Eleventy + Netlify CMS Static Site Generator

[![Netlify Status](https://api.netlify.com/api/v1/badges/5d0ca7a5-6f8a-47fc-bb0c-b1f04b729bd1/deploy-status)](https://app.netlify.com/sites/eleventy-netlify-cms/deploys)


## Stack

This is a custom solution for static, NetlifyCMS-enabled websites developed by and for [idiaz.roncero](http://idiazroncero.com).

It is itself a fork of [eleventy-netlify-boilerplate](https://github.com/danurbanowicz/eleventy-netlify-boilerplate).

For the front-end, it depends on [huesos](https://www.npmjs.com/package/huesos), a custom SCSS framework. The framework configuration overrides are handled on  `/src/assets/scss/_config.scss`.

For JavaScript, it uses Parcel CLI without any further configuration. We intent to be able to write ES6 and `import` modules without having to configure a full-featured and unneded Webpack/SPA configuration, since we don't need most of Webpack's bells and whistles. Of course, you are free to ignore this and set your own JS toolbox.

## Image assets

Image handling is one of the biggest issues on static site generators. Without server-side tools like Imagick, the usual transform/crop/resize operations become a problem.

WIP: Migrated to netlify-img


### Image shortcodes

WIP: Migrated to netlify-img


## Favicons and PWA

Uploading a `src/assets/img/favicon.jpg` file is mandatory in order to be able to run `yarn pwa` (or `yarn images:favicons`, both start the same gulp task).

This commands will generate all the favicon sizes and all the manifest files for service workers / search engines. 

Please note this command needs to be __manually__ run on every favicon.jpg change because it has been left outside the build process in order to speed it up.

[Configuration reference](https://github.com/itgalaxy/favicons)


## Commands

`yarn build` triggers a complete build of all the static and compiled assets. It will look at the `lfs` value of `images.config.js` to decide wether to perform image conversions.

`yarn watch` starts the watch process for both Eleventy and sass.

`yarn serve` starts the watch process + a Browserify server for live-testing.

`yarn debug` triggers a eleventy build with the DEBUG flag for debugging.

`yarn css` compiles sass into css with sourcemaps and nested output.

`yarn css:prod` compiles sass into css __without__ sourcemaps and compressed. It is used on "build" command.

`yarn css:watch` starts a watch process for SASS. It is used on "watch" command.

`yarn css:post` runs postcss plugins, using .browserlistrc for browser usage and postcss.config.js to load plugins (postcssPresetEnv and stylelint by default). It is used on "build" command.

`yarn pwa` and `yarn images:favicons` both run a gulp process that will generate all favicons needed and all the manifest files for service workers / search engines. Please note this command needs to be __manually__ run once on every favicon.jpg change because it is not part of the build process (in order to make it faster).

`yarn js:build` runs a Parcel cli command that takes `/assets/js/script.js` and outputs a `script-bundle.js` file transpiled, tree-shaked and module-bundled.

## TODO

- Solve favicons bug
- Add cache buster