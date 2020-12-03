# Bug repro

## How to reproduce

```
tsc --build --verbose
tsc --build --verbose
```

## Expected

Project was built once.

## Actual

Project was built twice.

## Additional information

Second build logs this message:

```
[14:36:00] Project 'tsconfig.json' is out of date because output file 'dist/src/index.js' does not exist
```

`dist/src/index.js` is not supposed to exist. `dist/index.js` does.

Setting the following setting in the tsconfig.json fixes the problem:

```
"rootDir": "./src"
```

But the actual behavior should be consistent even without the `rootDir` setting
