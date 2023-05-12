# Changelog


## v0.0.3

[compare changes](https://github.com/nyxblabs/mimikrook/compare/v0.0.2...v0.0.3)


### 🏡 Chore

  - **package.json): fix typos in repository and bugs URLs 🐛 fix(utils.ts): remove @ts-expect-error comments 🐛 fix(types.test.ts:** Remove @ts-expect-error comments The repository and bugs URLs in package.json contained typos in the repository and bugs URLs. The URLs have been fixed to point to the correct repository and issues page. The @ts-expect-error comments in utils.ts and types.test.ts have been removed as they were no longer necessary. ([fa8e255](https://github.com/nyxblabs/mimikrook/commit/fa8e255))

### ❤️  Contributors

- Nyxb <contact@nyxb.xyz>

## v0.0.2


### 🏡 Chore

  - **.eslintrc): disable no-console rule 🚀 feat(package.json): add consolji and update dependencies 🎉 feat(debugger.ts): add createDebugger function to start debugging hook names and timing in console 🎉 feat(hookable.ts:** Add Hookable class to manage hooks and createHooks function to create a new instance of Hookable The no-console rule is disabled in the .eslintrc file to allow console logs in the codebase. The consolji package is added to the project to provide a better console logging experience. The dependencies are updated to their latest versions. The createDebugger function is added to the debugger.ts file to start debugging hook names and timing in console. The Hookable class is added to the hookable.ts file to manage hooks, and the createHooks function is added to create a new instance of Hookable. ([20738cf](https://github.com/nyxlabs/mimikrook/commit/20738cf))
  - **.eslintrc): disable @typescript-eslint/ban-ts-comment rule 🐛 fix(hookable.ts): remove ts-expect-error comment and fix variable declaration ✅ test(debuger.test.ts:** Add tests for createDebugger function The @typescript-eslint/ban-ts-comment rule was disabled in the .eslintrc file. The ts-expect-error comment was removed from the hookable.ts file, and the variable declaration was fixed. Tests were added to the debuger.test.ts file to test the createDebugger function. ([c864f37](https://github.com/nyxlabs/mimikrook/commit/c864f37))
  - **package.json:** Update scripts to include new build and test commands The `prepublish` script now runs `nyxr build` to ensure that the package is built before publishing. The `build` script now runs `unbuild` to remove any previous builds before building the package. The `dev` script now runs `vitest` to start the development server. The `lint` script now includes the `--cache` flag to improve performance. The `lint:fix` script now includes the `--cache` flag and the `--fix` flag to automatically fix linting errors. The `release` script now includes `nyxlx changelogen@latest --release --push` to generate a changelog and push it to the repository. The `test` script now includes `nyxr lint` to ensure that the code is linted before running tests. The `test:types` script now runs `tsc --noE ([0a2ba22](https://github.com/nyxlabs/mimikrook/commit/0a2ba22))
  - **.eslintrc): disable @next/next/no-html-link-for-pages rule 🚨 chore(mimikrook.ts): add type annotations and refactor code to improve readability 🚨 chore(debugger.test.ts:** Change Hookable to Mimikrook in import and variable declaration The changes made in the .eslintrc file disable the @next/next/no-html-link-for-pages rule. The rule was disabled to allow the use of HTML links in Next.js pages. The changes made in the mimikrook.ts file add type annotations and refactor the code to improve readability. The changes made in the debugger.test.ts file change Hookable to Mimikrook in the import and variable declaration. This is because the Hookable class was renamed to Mimikrook. ([5cc58aa](https://github.com/nyxlabs/mimikrook/commit/5cc58aa))
  - **package.json): add 'mimikrook' keyword to package.json 🚨 test(mimikrook.test.ts:** Remove @ts-nocheck directive and fix describe block title The 'mimikrook' keyword was added to the package.json file to improve searchability. The @ts-nocheck directive was removed from the test file to ensure that the types are being checked. The describe block title was updated to reflect the correct name of the module being tested. ([9a41424](https://github.com/nyxlabs/mimikrook/commit/9a41424))
  - Update project files This commit updates various project files, including adding a funding.yml file, issue templates for bug reports, feature requests, and typo fixes, and a pull request template. It also updates the CODE_OF_CONDUCT.md and CONTRIBUTING.md files to point to the project's contribution guidelines. These changes improve the project's organization and make it easier for contributors to understand how to contribute to the project. ([265e8e1](https://github.com/nyxlabs/mimikrook/commit/265e8e1))

### 🎨 Styles

  - **README.md:** Update cover image source and link The cover image source and link have been updated to reflect the new image file name and location. ([a5e222e](https://github.com/nyxlabs/mimikrook/commit/a5e222e))

### ❤️  Contributors

- Nyxb <contact@nyxb.xyz>

