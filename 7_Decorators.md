1. A Decorator is just a function that you apply to something like a class.
    - Declare as a function (with the first character as capital(not mandatory))
    - Always takes some argument like in case when we apply it to a class then it takes class constructor
    - Decorators are executed first when the class is declared (not instantiated)

```

    function Logger(constructor: Function) {
        console.log('Logging...')
        console.log(constructor);
    }

    @Logger
    class Person {
        name = 'Max';

        constructor() {
            console.log('Creating Person object');
        }
    }

```

2. Another way to create a decorator using a Decorator factory
    - here we are passing 1 extra detail to the decorator factory and that detail can be used in the decorator
    - we are calling the @Logger() so that it can return the decorator function

```

    function Logger(logString: string) {
        return function(constructor: Function) {
            console.log(logString)
            console.log(constructor);
        }
    }

    @Logger('LOGGING-PERSON')
    class Person {
        name = 'Max';

        constructor() {
            console.log('Creating Person object');
        }
    }
```

3. More Useful decorators

```
    In HTML
    <body><div id="app></div></body>

    in ts file

    function WithTemplate(template: string, hookId: string) {
        return function(constructor: any) {
            const hookId = document.getElementById('app');
            if(hookId) {
                hookId.innerHTML = template
                let p = new constructor();
                hookId.querySelector('h1')!.textContent = p.name;
            }
        }
    }

    @WithTemplate('<h1>My Person Object</h1>','app')
    class Person {
        name = 'Max';

        constructor() {
            console.log('Creating Person object');
        }
    }

```

4. we can add more than 1 decorator
    - Order of execution is bottom-up (WithTemplate runs first and then Logger)

```
    @Logger('LOGGING-PERSON')
    @WithTemplate('<h1>My Person Object</h1>','app')
    class Person {
        name = 'Max';

        constructor() {
            console.log('Creating Person object');
        }
    }

```

5. We can add decorators at other places also like properties, accessor function (like setter), methods etc
    - When we add decorators to properties it takes 2 arguments
    - When on accessor function or any other method then it takes 3 arguments
    - Parameters also takes 3 arguments, target, name of the method and the parameter number in the parameter list

```

    function Log(target: any, propertyName: string | Symbol) {
        console.log('Log running');
        console.log(target, propertyName);
    }

    function Log2(target: any, name: string | Symbol, descriptor: PropertyDescriptor) {
        console.log('Access decorator!')
        console.log(target);
        console.log(name);
        console.log(descriptor);
    }

    function Log3(target: any, name: string |Symbol, descriptor: PropertyDescriptor) {
        console.log('Method decorator!')
    }

    function Log4(target: any, name: string |Symbol, position: number) {
        console.log('Parameter decorator!')
    }

    class Product{
        @Log
        title: string;
        _price: number;

        @Log2
        set price(val: number) {
            if(val > 0) {
                this._price = val;
            }
        }

        constructor(t:string, p: number) {
            this.title = t;
            this._price = p;
        }

        @Log3
        getPriceWithTax(@Log4 tax: number) {
            return this.price * (1 + tax);
        }
    }

```