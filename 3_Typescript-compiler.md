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

7. SourceMap
    - Helps in debug and development
    - If we set it to true then we can see the typescript files in the source tab of the dev tools.

8. outDir and rootDir
    - outDir is the location where all the compiled javascript files get stored for example './dist'.
    - rootDir is the location from where the typescript files will get compiled

9. noEmitOnError
    - false means generating Javascript files on compilation even when there is a potential error like a value can be null
    - default value is false
    - true means the javascript files will not be created, we need to fix all the poterntial errors like potential null pointers

10. Strict options
    - Strict: true means all the strict configuration is set to true
    - we can set few strict configuration individually (but need to set global strict config to false)
    - individual strict settings like
      - noImplicitAny: true  -> strictly checks the data types of the parameters of functions
      - strictNullChecks: true ->  stricktly checks possible null pointers

11. Code quality options
    - noUnusedLocals
    - noUnusedParameters
    - noImplicitReturns
    - These all are boolean configs