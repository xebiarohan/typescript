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