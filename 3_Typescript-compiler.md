1. Watch mode
    - tsc <file-name>.ts -w  OR
    - tsc <file-name>.ts --watch

2. Compiling the Entire project not just app.js
    - tsc --init        // generates the tsconfig file
    - tsc -w              // compiles the whole project

3. Excludes ts files from compiling
    - in tsconfig file we can add the name of the file/folder in the excludes array
    - Example all the ts files in node_modules
    - we can pass regex also in it
```
    {
      "compilerOptions": {...},
      "exclude": [
        "node_modules"
      ]
    }
```

4. Include file in compilation
    - if we know exactly all the files that we need to compile
    - best practice is not to add it if you want all your files to be compiled

```
    {
      "compilerOptions": {...},
      "exclude": [
        "node_modules"
      ],
      "include" {
        "app.ts",
        "analytics.ts"
      }
    }
```

5. Compiler options
    - target - tells the Ecmascript version es5, es2016, es6, etc
    - lib - tells which features by default typescript knows , if we dont specify any value then all the feature of target is added to lib
            - default setup is equal to
```
    "lib": [
        "dom", "es6", "dom.iterable", "scdripthost"
    ]

```

6. allowJs and checkJs is used to add the Js files with Ts files to be compiled and check for errors (if for some reason we have some javascript files with the typescript files)