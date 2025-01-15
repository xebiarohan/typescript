1. Intersection types
    - Combination of 2 types
    - Object of intersection type must contain properties of both type
    - Syntx is : &

```
    type Admin = {
        name: string;
        privileges: string[]
    }

    type Employee = {
        name: string;
        startDate: Date;
    }

    type ElevatedEmployee = Admin & Employee;

    const e1: ElevatedEmployee = {
        name: 'Rohan',
        privileges: [],
        startDate: new Date()
    }

```

2. Type Guards

    - Checking the type of variable before using it
    - Example we have a variable which can be a string or a number, we have to check if its type is string before concatenating
    - for checking user defined objects we can use 'in' keyword to check if the property is present in the object
    - we can also use instanceof in case of checking the type of object
```
    let a : string | number;
    let b : string | number;

    if(typeof a === 'string' || typeof b === 'string' ) {
        a.toString() + a.toString();
    } else {
        a + b;
    }

other example

    type Admin = {
        name: string;
        privileges: string[]
    }

    type Employee = {
        name: string;
        startDate: Date;
    }

    let user: Employee | Admin;

    if('priviledge' in user) {
        ...
    }

```

3. Discriminated unions
    - Pattern that makes type guards easier, it is available when we work with object types
    - In each class or interface that is part of the union type we can add one extra property 'type'
    - and give a unique value to it to uniquely identify the class

```

    interface Bird {
        type: 'bird'
        flyingSpeed: number;
    }

    interface Horse {
        type: 'horse'
        runningSpeed: number;
    }


    type Animal = Bird | Horse;

    function modeAnimal(animal: Animal) {
        switch(animal.type) {
            case 'bird':
                    console.log(animal.flyingSpeed);
                    break;
            case 'horse':
                    console.log(animal.runningSpeed);
                    break;
            default:
                    console.log('other');
        }
        
    }

```

4. Type casting
    - There are 2 syntax
        - using <> in front of any variable
        - Using as syntax
        - ! is used to mark that the value can never be null
    - If the type casting fails then we can get a run time error

```
const userInputElement = <HTMLInputElement>document.getElementById('user-input')!;

OR

const userInputElement = document.getElementById('user-input')! as HTMLInputElement;
```

5. Index properties
    - properties which are flexible about the name
    - we cannot add any other property in the object that does not satisfy the condition like
    - we can add id of type string but we cannot add id of type number

```
    interface ErrorContainer {
        id:  number;    // error
        id: string;
        [prop: string]: string;     // it means the object must contains a property that must be a string and the value of that property 
                                    // must also be a string
    }

    const a: ErrorContainer = {};      // valid
    const b: ErrorContainer = { error : 'Some error'} // valid
    const c: ErrorContainer = { error: 'some error', message: 'some message'} // valid
    const d : ErrorContainer = { message: 1}    // Invalid

```

6. Function overloading
    - Calling a same function with different parameters
    - just add the function declaration on top of other declaration

```

    function add(a: number, b: number): number;
    function add (a: Combinable, b: Combinable) {
        if(typeof a === 'string' || typeof b === 'string') {
            return a.toString() + b.toString();
        }
        return a + b;
    }


    const result =  add(10,20);     // type of result will be number

```

7. Optional chaining
    - Used when we are not sure that some property of a nested data object (like jsonobject) is null.
    - like we want to fetch user.job.tile (user can be null, job can be null, etc)
    - Syntax '?'
    - If will not try to access the statement after the ? when the first part is null or undefined

```

    console.log(user?.job?.title);

```

8. Nullish Coalescing
    - It checks if the value is null or undefined then set the default value
    - Empty string considers as true value and will be used (default value is not set)

```
    let value = null;

    let result = value ?? 'DEFAULT';

```