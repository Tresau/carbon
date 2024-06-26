# transforms

> A folder of codemod transforms to be ran independently or via the
> @carbon/upgrade cli

## Usage

The transforms contained within this folder are primarily intended to be used
within @carbon/upgrade cli commands.

You can run a specific transform for a path in the project by running:

```bash
yarn jscodeshift -t transforms/<name>.js 'path/to/file'
```

If you want to preview changes that are being made, you should enable the `dry`
and `print` options:

```bash
yarn jscodeshift -d -p -t transforms/<name>.js 'path/to/file'
```

## Writing transforms

Transforms are written in the `transforms` directory with their tests and
fixtures written in the `__tests__` and `__testfixtures__` directories,
accordingly.

As an example, to add a transform called `sort-prop-types` one would create the
following files:

```
- codemods
  - transforms
    - __testfixtures__
      - sort-prop-types.input.js
      - sort-prop-types.output.js
    - __tests__
      - sort-prop-types-test.js
    - sort-prop-types.js
```

In this structure, the test file will determine which test fixtures get run.
Test fixtures are written with a `*.input.js` and `*.output.js` convention.
Files that end with `*.input.js` are given to your transform and the test runner
will assert that the output matches what is available in `*.output.js`.
