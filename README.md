# @monzo/flow-to-ts

[![npm version](https://badge.fury.io/js/%40khanacademy%2Fflow-to-ts.svg)](https://badge.fury.io/js/%40monzo%2Fflow-to-ts)

> :warning: Please note that is is an unsupported fork of `@khanacademy/flow-to-ts`.

Feel free to fork it yourself and base your work of it :-) 


# flow-to-ts

[![Actions Status](https://github.com/Khan/flow-to-ts/workflows/Node%20CI/badge.svg)](https://github.com/Khan/flow-to-ts/actions)
[![codecov](https://codecov.io/gh/Khan/flow-to-ts/branch/master/graph/badge.svg)](https://codecov.io/gh/Khan/flow-to-ts)
[![npm version](https://badge.fury.io/js/%40khanacademy%2Fflow-to-ts.svg)](https://badge.fury.io/js/%40khanacademy%2Fflow-to-ts)

Convert Flow code to TypeScript.

> :warning: This is a WIP and many things still do not work properly.  There
> may also be the odd regression from time to time as work progresses.

The goal of this project is to provide a tool that can translate 95% of Flow
to TypeScript while maintaining a high percentage of the existing type
information. We don't want to convert code and end up with everything using
`any`. We also want to avoid having to make a lot of manual changes to files
afterwards, e.g. changing `SyntheticEvent` to `React.Event`.

# Quick start

- `yarn global add @khanacademy/flow-to-ts`
- `flow-to-ts [options] <file globs>`

For a comprehensive list of available options, please check out the [CLI code](./src/cli.ts).

# Playground

https://flow-to-ts.netlify.com

# Principles

- when exact translation isn't possible:
  - downgrade to `any` when possible and provide a gentle warning
  - when it isn't possible to downgrade (e.g. `%checks`), remove the syntax
    and provide a forceful warning that the code in question will need a human
    to convert it manually.
- best effort to maintain blank lines and the position comments, this isn't
  always possible so warn in those situations where we can't, e.g. converting
  object type spreads to intersection types.

# Contributing

## Bugs

Bug reports for converting Flow to TypeScript should include a link to the
playground with an example of a minimal reproducible example of the bug.

## Feature Requests

Feature requests are welcome.

## Pull Requests

Please make sure there is a GitHub issue first before creating a pull request
except for small things. Also, please sign our [Contributor License Agreement](https://docs.google.com/forms/d/e/1FAIpQLSdyXYrc8ogVoA46J9KXyIj5nKlZzNkOnQG-4A1R7X_BWGTShQ/viewform).

Pull requests that fix a bug in the conversion code should include one or more
test cases and should have 100% diff coverage.

## Dev quick start

```bash
git clone git@github.com:Khan/flow-to-ts.git
cd flow-to-ts
git submodule update --depth 1 --init -- babel
cd babel
yarn
cd ..
yarn
yarn test
```

## Helpful resources

- https://github.com/niieani/typescript-vs-flowtype
- https://astexplorer.net/
