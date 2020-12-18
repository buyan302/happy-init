# Happy-Npm-Cli

Happy-Npm-Cli is a cli tool that help you develop and release npm package easily.

> Initial easily, develop quickly, publish confidently.

## Installation

```shell
$ npm install happy-npm-cli -g
```

## Usage

### `happy init`

```shell
$ happy init [es|ts|react]
```

A robust npm package should concern following aspects:

- code style: prettier...
- code quality: eslint,unit test...
- code compilation tool: babel,webpack...
- git hooks: precommit,prepublish...
- ci/cd: git actions
- documentation: README.md,CHANGELOG.md...

Happy-Init provides multiple kinds of boilerplate package,includes:

- [x] ES package
- [ ] TS package
- [ ] React component package

Each boilerplate contains complete development dependencies and workflow from initialization to release.

After run `happy init`, Happy-Npm-Cli will download specific boilerplate package files and then install dependencies.

![screenshots](https://github.com/buyan302/happy-init/blob/main/init.gif)

### `happy compare`

Compare packages' download frequency,quality,git star count,etc from https://www.npmjs.com/.

```shell
$ happy compare [package1] [package2] ...
```

### `happy run`

Inject environment variables into npm script, compatible with different os.

```shell
$ happy run [scriptName] [--env <envConfig>] [--dotenv <dotenv>]
```

- `--env <envConfig>`: environment variables config
- `--dotenv <dotenv>`: `.env` file path, default `.env'

Environment variables come from command line,`package.json` file and `.env` file.

`package.json` env config format:

```json
{
  "scripts": {
    "[scriptName]": "..."
  },
  "env": {
    "[scriptName]": {
      "[variable]": "..."
    }
  }
}
```

Environment variables priority: command line > `package.json` > `.env`.

For example:

```json
// package.json
{
  "scripts": {
    "build": "babel src --out-dir lib"
  },
  "env": {
    "build": {
      "NODE_ENV": "test"
    }
  }
}
```

```yml
# .env
NODE_ENV=development
```

Then executing `happy run build --env NODE_ENV=production` equals `NODE_ENV=production babel src --out-dir lib`

## More Command?

Leave a issue [here](https://github.com/buyan302/happy-init/issues).
