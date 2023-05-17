# TypeScript Starter

## TypeScript Compiler

## TypeScript Lint

Install and create `tslint.json` configuration.

```shell
npm i -D tslint # install tslint in dev dependency
./node_modules/.bin/tslinit --init  # create file tslint.json
```

After the file have been created, look at the `tslint.json`, Check to `rules` property, which should be empty array. Within the `rules` array, the default value for `no-console` is true if it is not specified explicitly. But in the development process we should show console to easier than debug code. The below is the full of content.

```json
{
    "defaultSeverity": "error",
    "extends": [
        "tslint:recommended"
    ],
    "jsRules": {},
    "rules": {
	      "no-console": false
    },
    "rulesDirectory": []
}
```

## Cold Reloading

When make changes to the code, the application can be run without the need to wait for code compilation. To archive that, need use `ts-node` to directly run without compiling code. Additionally, we are also use `nodemon` to automatically reload application whenever there are code changes. 

```shell
npm i -D ts-node nodemon
```

Add file `nodemon.json` if it is not existed. And add new command to run nodemon in the `scripts` property in the package.json.

```json
# file: nodemon.json
{
  "watch": ["src"],
  "ext": ".ts,.js",
  "ignore": [],
  "exec": "npx ts-node ./src/index.ts"
}
```

And ensure command run with nodemon in the `scripts` property.

```json
# package.json
{
  # ...
  "scripts": {
    "start:dev": "npx nodemon",
    # ...
  }
  # ...
}
```
