1. Splitting code in multiple files

   - Using namespace and file bundling
   - ES6 Imports/Exports (Modern and better way to split code)

2. Adding classes, interface, constants, etc into namespace
   - These things will be available only inside of namespace, we cannot directly access them outside namespace
   - Only the values that have export keyword in front of it can be accessed from outside (not directly).
   - we can import the name in any other class using the 3 / (///) as shown below (let say the name of the file where the namespace is present is test.ts)
   - This call to namespace will be on the top of the class where we want to use it
   - Then we need to create the namespace with same name in the class where we want to use the name
   - and move all the (classes, enums, functions of that file in that namespace)
   - namespace is a typescript feature

test.ts

```
    namespace App {
        interface Abc {
            ...
        }

        interface xyz {
            ...
        }

        export class print {

        }

        const name = '';
    }

```

main.ts

```
    /// <reference path="test.ts">

    namespace App {

        class Project {
            ...             // Here we have access to print class
        }
    }

```

3. ES modules
   - we can export anything using the export keyword
   - The we can import it in another files (import contains js files as it is used for the compilation)
   - in the index.html we have to make a change in the main script tag (need to remove the defer and add the type ="module")
   - If we use webpack or any build tool then we dont need to add .js in the end of the import
   - If we rely on the browser then we have to add .js in the end of the imported file

```interface.ts
    export interface abc {
        ...
    }

    export interface xyz {
        ...
    }
```

```app.ts
    import {abc} from ''./interface.js
```

```index.html
    <script type="module" src="dist/app.js"></script>
```

2. Different import-export syntax
   - If we have multiple imports from the same file then we can use an alias like
   - If we want to change the name of the class or method that is imported then we can do that
   - we can have 1 default export in a class and we dont import it in the {} but with any name of our choice
   - There can max of 1 default export, other are called named export

```

import * as Validation from './validation.js'
Validation.validate
Validation.Invalidate

--------------------------------------

import {autobind as Autobind} from './abc.js'

--------------------------------------

export default class Component {
    ...
}

import Cmp from './Component.js'

```


