1. Classes - Blueprints of Objects, Works with real-life entities in your code - Used to create multiple Objects quickly with same structure (just differs in the defails)

2. this keyword in typescript
   - this keyword as a parameter in a function describes which object can call this method, The structure of the object calling the method must match the structure of the this data type.

```

        Class Department {
            name: string

            constructor(n: string) {
                this.name = n;
            }

            describe(this: Department) {}
        }



        const accounting = new Department('Sales');

        accounting.describe();      // works fine as the accounting the object of Department class

        const accountingCopy1 = {describe: accounting.describe};

        accountingCopy1.describe()       // It will not work as the accountingCopy does not satisfy the object structure of Department class
                                        // If we add a name property in the accountingCopy object then it will wor

        const accountingCopy2 = {name: 'DUMMY', describe: accounting.describe};



        accountingCopy2.describe()       // works fine



```

3. Access modifiers

   - private, public, protected, readonly

   - In Javascript these access modifiers were not available, added in typescript

   - In latest Javascript we have # to make variable private

   - protected variables can be used by the same class and all the classes that inherits it(extends)

4. Shorthand initialization

   - here id and name are both the parameters of the constructor and the fields of Department class

```

    class Department {
        constructor(private id: string, private name: string){}
    }



```

5. Readonly

   - does not exist in javascript

   - Can only add the value at initialization, cannot update the value after that

```

    class Department {
        constructor(private radonly id: string, private name: string){}
    }

```

6. Inheritance

   - we can inherit from 1 class

   - No multi class inheritance

   - we dont create a constructor of the base class then the constructor of the parent class is used

   - if we have a constructor in the base class then we cannot directly use the constructor of the parent class

   - super() can be used to call the constructor of the parent class (must be the first line of the constructor)

   - we can overide methods of the base class

```

    class ITDepartment extends Department {

    }

    const accounting = new ITDepartment('d1', 'Accounting');

    class SalesDepartment extends Department {
        constructor(private id: string) {
            super(id, 'Sales');
        }

    }



```

7. Getter and setters

   - Present in javascript as well

   - can name anything, need not be same as the name of the variable

```

    class abc {
        constructor() {}
        private lastReport: string;

        get mostRecentReport() {
            return lastReport;
        }

        set mostRecentReport(report: string) {
            this.lastReport = report;
        }

    }


    const obj = new abc();
    obj.mostRecentReport = 'report';
    console.log(obj.mostRecentReport);      //report

```

8. static methods and properties

   - present in JS6

   - does not access using the object of a class

   - we cannot access the static properties in non-static properties directly using this keyword, need to use the className

```

    class ABC {

        static name = 'test';

        static printClassName {

            console.log('abc');

        }

        func1() {
            console.log(ABC.name);
        }
    }

    ABC.printClassName();
    console.log(ABC.name);

```

9. Abstract classes

   - forces the base class to implement some certain methods

   - class must contain abstract keyword that contains 1 or more abstract methods

   - Abstract classes cannot be instantiated

```

    abstract class ABC {
        abstract describe();
    }



    class XYZ extends ABC {

        describe {

            console.log('XYZ');

        }

    }



```

10. Singletons and private Constructors

    - Singleton pattern is when we have exactly 1 instance of a class

    - static methods can be used to get the single instance

    - this in a static method refers to the class

    - we can call static properties in a static function using this keyword

```

class ABC {

    private static instance: ABC;

    private constructor() {}

    static getInstance() {

        if(this.instance) {

            return this.instace;

        }

        this.instance = new ABC();

        return this.instace;

    }

}



```

11. Interface

    - Describes the structure of an object

    - only the declaration of methods

    - Used to define the type of complex objects

```
    interface Person {
        name: string;
        age: number;
        greet(): void;
    }

    let user1: Person;

    user1 = {
        name: 'abc',
        age: 1,
        greet() {
            console.log('Hello');
        }
    }



```

12. we can use type to do the same thing but interface are better as they are more clear to read

```

    type Person = {
        name: string;
        age: number;
        greet(): void;
    }
    let user1: Person;
    user1 = {
        name: 'abc',
        age: 1,
        greet() {
            console.log('Hello');
        }
    }

```

13. we can implement an interface but not a type
    - we can implement multiple interface
```
    class Abc implements Person, Greet {}
```

14. We use interface to force classes to have some basic properties and methods.

15. we cannot add any access specifier in interface other than the readonly

```

    type Person = {
        radonly name: string;
        age: number;
        greet(): void;
    }

    let user1: Person;

    user1 = {
        name: 'abc',
        age: 1,
        greet() {
            console.log('Hello');
        }

    }

    user1.name = 'xyz';     // error

```

16. Interface intehitance

    - An interface can extend another interface

```

    interface Named {
        readonly name: string;
    }

    interface Greet extends Named {

        greet(phrase: string): void;

    }



```

17. Interfaces as function types

    - other way we can do like (better approach):

```

    type AddFn = (a: number, b: number) => number;

    let add: AddFn

    add = (n1: number, n2: number) {

        return n1 + n2;

    };



```

    - Using interface

```
    interface AddFn {
        (a: number, b: number): number;
    }

    let add: AddFn

    add = (n1: number, n2: number) {
        return n1 + n2;
    };

```

18. Optional properties

    - we can have some optional properties in interface and classes

    - If it is in iterface then it will not force the classes implementing it to have it

    - Add (?) after the name of the property

    - we can even have functions as optional properties

```

interface Named {

    name: string;
    lastName?: string
    name?(): void;
}



```
