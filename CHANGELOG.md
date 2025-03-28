# Changelog

All notable changes to this project will be documented in this file.

## v15.1.3

- Ensure attachments are correctly added to HTML reports in case of retries, fixes [#931](https://github.com/badeball/cypress-cucumber-preprocessor/issues/931).

## v15.1.2

- Limit the size of internal variables contained within the Cypress environment, fixes [#908](https://github.com/badeball/cypress-cucumber-preprocessor/issues/908).

## v15.1.1

- Log hooks using log groups as well, fixes [#922](https://github.com/badeball/cypress-cucumber-preprocessor/issues/922).

## v15.1.0

- Log steps and commands using log groups, fixes [#796](https://github.com/badeball/cypress-cucumber-preprocessor/issues/796).

## v15.0.0

- Drop support for Cypress v8.

- Add support for Cypress v12.

## v14.0.0

- Drop support for Cypress v7.

- Add support for Cypress v11.

## v13.1.0

- Better support for worlds in TypeScript, fixes [#864](https://github.com/badeball/cypress-cucumber-preprocessor/issues/864).

- Extended documentation, particularly in regards to pairing step definitions.

## v13.0.3

- Performance improvements to diagnostics.

## v13.0.2

- Correctly assign `testState.pickleStep`, fixes [#836](https://github.com/badeball/cypress-cucumber-preprocessor/issues/836).

## v13.0.1

- Support absolute paths in `stepDefinitions`, fixes [#832](https://github.com/badeball/cypress-cucumber-preprocessor/issues/832).

## v13.0.0

- Add a very rudimentary way of diagnosing validity of steps, IE. whether each step is matching one, and only one, step definition, fixes [#754](https://github.com/badeball/cypress-cucumber-preprocessor/issues/754).

- Remove `And` and `But` from the public API, fixes [#821](https://github.com/badeball/cypress-cucumber-preprocessor/issues/821).

- Output snippet suggestions upon missing step definition, fixes [#799](https://github.com/badeball/cypress-cucumber-preprocessor/issues/799).

## v12.2.0

- Total execution time is correctly shown in HTML reports, fixes [#813](https://github.com/badeball/cypress-cucumber-preprocessor/issues/813).

- Validate inclusion of `addCucumberPreprocessorPlugin()` in `setupNodeEvents()`, fixes [#820](https://github.com/badeball/cypress-cucumber-preprocessor/issues/820).

## v12.1.0

- Start time and execution time is shown in HTML reports, fixes [#798](https://github.com/badeball/cypress-cucumber-preprocessor/issues/798).

- Add current step information to `window.testState`, fixes [#800](https://github.com/badeball/cypress-cucumber-preprocessor/issues/800).

## v12.0.1

- Allow overriding env using tags, fixes [#792](https://github.com/badeball/cypress-cucumber-preprocessor/issues/792).

- Correct some path handling on Windows, fixes [#788](https://github.com/badeball/cypress-cucumber-preprocessor/issues/788).

- Correct calculation of common ancestor path, even when specs are filtered, fixes [#785](https://github.com/badeball/cypress-cucumber-preprocessor/issues/785).

## v12.0.0

Breaking changes:

- A minor change to step definitions has been introduced, affecting users of Cypress v10 or higher. When upgrading to v11.0.0 of the processor, users was instructed to [remove certain prefixes](https://github.com/badeball/cypress-cucumber-preprocessor/releases/tag/v11.0.0) from their step definitions. This is no longer required and said prefixes can be re-introduced when upgrading to v12.0.0 of the preprocessor. In other words, if your configuration looks like this

```json
{
  "stepDefinitions": [
    "[filepath].{js,ts}",
    "cypress/support/step_definitions/**/*.{js,ts}"
  ]
}
```

.. then it should now look like this (notice the addition of `cypress/e2e`)

```json
{
  "stepDefinitions": [
    "cypress/e2e/[filepath].{js,ts}",
    "cypress/support/step_definitions/**/*.{js,ts}"
  ]
}
```

Note: Step definitions doesn't necessarily have to be put in `cypress/e2e` and alongside your feature files. They can be contained in an entirely separate directory, if desired. This fixes [#748](https://github.com/badeball/cypress-cucumber-preprocessor/issues/748).

Other changes:

- Updated all `@cucumber/*` dependencies.

- Added native support for HTML reports using `@cucumber/html-formatter`, fixes [#780](https://github.com/badeball/cypress-cucumber-preprocessor/issues/780).

- Correct an issue with non-array `stepDefinitions`, fixes [#781](https://github.com/badeball/cypress-cucumber-preprocessor/issues/781).

## v11.5.1

- Expose member `getStepDefinitionPatterns`.

## v11.5.0

- Improve error message upon missing step definition, fixes [#763](https://github.com/badeball/cypress-cucumber-preprocessor/issues/763).

## v11.4.0

- Step definition with extension `.tsx` is picked up by default, paving the way for component testing.

- Added an example illustrating component testing with React + Webpack.

## v11.3.1

- Retried test would eventually yield "No commands were issued in the test", fixes [#749](https://github.com/badeball/cypress-cucumber-preprocessor/issues/749).

## v11.3.0

- Enable configuring of JSON args, allowing for custom JSON formatters, fixes [#742](https://github.com/badeball/cypress-cucumber-preprocessor/pull/742).

## v11.2.0

- Enable `*.mjs` file extension by default, when looking for step definitions.

- Add a default export to `@badeball/cypress-cucumber-preprocessor/esbuild`.

- Add examples for CJS and ESM.

## v11.1.0

- Enable test configuration overrides, such as retrability of a single scenario, fixes [#697](https://github.com/badeball/cypress-cucumber-preprocessor/issues/697).

## v11.0.0

Breaking changes:

- Dropped support for Cypress v6.

Other changes:

- Added support for Cypress v10. :tada:

- Untitled scenario outline no longer errors, fixes [#731](https://github.com/badeball/cypress-cucumber-preprocessor/issues/731).

- Outputting *only* messages is now possible, fixes [#724](https://github.com/badeball/cypress-cucumber-preprocessor/issues/724).

- Allow absolute output paths, partially fixes [#736](https://github.com/badeball/cypress-cucumber-preprocessor/issues/736).

- Output directories are automatically created recursively, partially fixes [#736](https://github.com/badeball/cypress-cucumber-preprocessor/issues/736).

### Upgrading to Cypress v10

There's no changes to configuration options, but if your configuration looked like this pre-10

```json
{
  "stepDefinitions": [
    "cypress/integration/[filepath].{js,ts}",
    "cypress/support/step_definitions/**/*.{js,ts}"
  ]
}
```

.. then it should look like this post-10 (notice the removal of `cypress/integration`)

```json
{
  "stepDefinitions": [
    "[filepath].{js,ts}",
    "cypress/support/step_definitions/**/*.{js,ts}"
  ]
}
```

## v10.0.2

- Allow integration folders outside of project root, fixes [#719](https://github.com/badeball/cypress-cucumber-preprocessor/issues/719).

## v10.0.1

- Fixed an [issue](https://github.com/badeball/cypress-cucumber-preprocessor/issues/720) where internal calls to `cy.wrap` was being logged.

## v10.0.0

Breaking changes:

- Exported member `resolvePreprocessorConfiguration` now *requires* a `projectRoot` variable and a `environment` variable.

Other changes:

- Configuration values can now be overriden using (Cypress-) [environment variable](https://docs.cypress.io/guides/guides/environment-variables).

## v9.2.1

- Fixed an [issue](https://github.com/badeball/cypress-cucumber-preprocessor/issues/713) with returning chainables from step definitions.

## v9.2.0

- Allow handlers to be omitted and attached explicitly, fixes [#705](https://github.com/badeball/cypress-cucumber-preprocessor/issues/705) (undocumented, experimental and API is subject to change anytime).

## v9.1.3

- Fixed an [issue](https://github.com/badeball/cypress-cucumber-preprocessor/issues/704) where programmatically skipping a test would error.

## v9.1.2

- Fixed an [issue](https://github.com/badeball/cypress-cucumber-preprocessor/issues/701) where Before hooks would error.

## v9.1.1

- Add timestamps and durations to messages.

## v9.1.0

- Automatically skip tests marked with `@skip`.

## v9.0.5

- Correct types for `isFeature` and `doesFeatureMatch`.

## v9.0.4

- Prevent an error when `experimentalInteractiveRunEvents` is enabled.

## v9.0.3

- Fixed an issue where the preprocessor was throwing in interactive mode when JSON reports was enabled.

## v9.0.2

- Fixed an [issue](https://github.com/badeball/cypress-cucumber-preprocessor/issues/694) when running all specs.

## v9.0.1

Due to an publishing error from my side, this version is identical to v9.0.0.

## v9.0.0

This is the point where [badeball](https://github.com/badeball)'s fork becomes the mainline and replaces [TheBrainFamily](https://github.com/TheBrainFamily)'s implementation. This implementation has been re-written from scratch in TypeScript, has more thorough test coverage and is filled with a bunch of new feature. Read more about the transfer of ownership [here](https://github.com/badeball/cypress-cucumber-preprocessor/issues/689).

The changelog of the two ancestors can be found at

- [TheBrainFamily's history / changelog](https://github.com/badeball/cypress-cucumber-preprocessor/blob/7031d0283330bca814d6923d35d984224622b4cf/CHANGELOG.md)
- [badeball's history / changelog](https://github.com/badeball/cypress-cucumber-preprocessor/blob/v9.0.0/CHANGELOG.md)
