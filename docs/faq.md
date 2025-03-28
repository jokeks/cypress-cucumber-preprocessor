# Frequently asked questions

* [`--env` / `tags` isn't picked up](#--env--tags-isnt-picked-up)
* [I get `fs_1.promises.rm is not a function`](#i-get-fs_1promisesrm-is-not-a-function)
* [I get `spawn cucumber-json-formatter ENOENT`](#i-get-spawn-cucumber-json-formatter-enoent)
* [Why is `cypress-tags` missing?](#why-is-cypress-tags-missing)
* [My JSON report isn't generated](#my-json-report-isnt-generated)
* [JSON reports aren't generated in open / interactive mode](#json-reports-arent-generated-in-open--interactive-mode)
* [I get `cypress_esbuild_preprocessor_1.createBundler is not a function`](#i-get-cypress_esbuild_preprocessor_1createbundler-is-not-a-function)
* [I get `cypress_esbuild_preprocessor_1.default is not a function`](#i-get-cypress_esbuild_preprocessor_1default-is-not-a-function)
* [The members `And(..)` and `But(..)` are missing](#function-members-and-and-but-are-missing)

## `--env` / `tags` isn't picked up

This might be because you're trying to specify `-e / --env` multiple times, but [multiple values should be comma-separated](https://docs.cypress.io/guides/guides/command-line#cypress-run-env-lt-env-gt).

## I get `fs_1.promises.rm is not a function`

Upgrade your node version to at least [v14.14.0](https://nodejs.org/api/fs.html#fspromisesrmpath-options).

## I get `spawn cucumber-json-formatter ENOENT`

You need to install `cucumber-json-formatter` **yourself**, as per [documentation](json-report.md).

## Why is `cypress-tags` missing?

The `cypress-tags` executable has been removed and made redundant. Specs containing no matching scenarios are [automatically filtered](https://github.com/badeball/cypress-cucumber-preprocessor/blob/master/docs/tags.md#running-a-subset-of-scenarios), provided that `filterSpecs` is set to true.

## My JSON report isn't generated

You have likely stumbled upon a configuration caveat, see [docs/configuration.md: Caveats / Debugging](configuration.md#caveats--debugging).

## JSON reports aren't generated in open / interactive mode

JSON reports aren't typically generated in open / interactive mode. They rely on some events that aren't available in open-mode, at least not without `experimentalInteractiveRunEvents: true`. However, this experimental flag broke some time ago, ref. [cypress-io/cypress#18955](https://github.com/cypress-io/cypress/issues/18955).

## I get `cypress_esbuild_preprocessor_1.createBundler is not a function`

This can happen if you have a TypeScript Cypress configuration (IE. `cypress.config.ts` as opposed to `cypress.config.js`) similar to one of our examples and have a `tsconfig.json` _without_ `{ "compilerOptions": { "esModuleInterop": true } }`.

If you're really adamant about _not_ using `esModuleInterop: true`, you can change

```ts
import createBundler from "@bahmutov/cypress-esbuild-preprocessor";
```

.. to

```ts
import * as createBundler from "@bahmutov/cypress-esbuild-preprocessor";
```

However, I recommend just using `esModuleInterop: true` if you don't fully understand the implications of disabling it.

## I get `cypress_esbuild_preprocessor_1.default is not a function`

See answer above.

## Function members `And(..)` and `But(..)` are missing

These have been [deprecated](https://github.com/badeball/cypress-cucumber-preprocessor/issues/821).
