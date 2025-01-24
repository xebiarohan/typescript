1. When we dont use the webpack, and we have multiple files then then browser sends multiple http request to load all the files and that is not good.

2. Webpack is a tool that helps us bundle our files togather and build it
   - webpack converts the typescript files in javascript, bundles it and sends it to the browser for execution

3. In normal setup
   - Multiple ts files (Http requests from browser to load their Js conversions)
   - Unoptimized code (not as small as possible)
   - External development server needed

4. With webpack
   - bundled code (so less HTTP calls)
   - Optimizes the code (smaller code)
   - Mode build steps can be added like webpack-dev-server

5. Installing webpack
   - npm install --save-dev webpack webpack-cli webpack-dev-server typescript ts-loader

6. Need to create a new config file next to tsconfig file
   - webpack.config.js



3rd party library

1. use npm install --save-dev @types/<library-name> example @types/lodash

   - it is used when we want to use vanilla javascript libraries in typescript

   - we have to use @types in front of the library name

2. Then import it in the class where you want to use it

   import \_ from 'lodash';

3. If there is a variable like in a script tag in a HTML page

<script>

    var GLOBAL = "global value"

</script>

    and when we try to access it in the ts file, it will throw an error that variable is not defined

    - we know that it will be available once it will run but typescript does not know that

    - in that case we uses the declare keyword in the typescipt file

```

    declare var GLOBAL: any;

```

4. There are typescript specific libraries also present

   - like we can have a object list, to map it to a model (class transformer library).

```product.model.ts

export class Product {

    title:string;

    price: number;



    constructor(t: string, p: number) {

        this.title = t;

        this.price = p;

    }

    getInformation() {
        return [this.title, `$${this.price}`];
    }

}



In App.js


import {Product} from './product.model'

const products = [

    {title: 'A carpet', price 29.99},

    {title: 'A book', price 15.00}

]

const loadedProducts = products.map(prod => {

    return new Product(prod.title, prod.price);

});



```

```

npm install class-transformer --save

npm install refrect-metadata --save



In ts class

import 'reflect-metadata';

import {plainToClass} from 'class-trasnform'

const loadedProducts = plainToClass(Product, products);

```
