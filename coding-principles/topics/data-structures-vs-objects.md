# Data Structures vs Objects

It sometimes (often) becomes confusing when engineers talk about objects and data structures.

In summary, a data structure just represents data (all members are public if created as a class, JavaScript plain
object, or just JSON) and has no behavior or methods.

Objects, on the other hand, have behavior and methods, and hide their fields and implementation.

Another common term for data structures is data transfer objects (DTO).

They are the opposite of each other. They are both important and should be used correctly.

If we are representing data, such as a page model, it has to be a data structure. We should have a separate class that
operates on it.

If we are going to operate on the internal data, we should prefer classes or objects with methods and behavior.

There are hybrid classes or objects that try to do both. This is an antipattern and should be avoided. Some bad examples
are Java Beans which hide all fields as private but create setters and getters, which defeats the purpose of using privates.
Active Directory, which is a data structure and has all its fields public but has save and find methods.

Data structures should never have methods! Objects and classes should have methods and hide their data and implementation!

"Procedural code (code using data structures) makes it easy to add new functions without changing the existing data
structures. OO code, on the other hand, makes it easy to add new classes without changing existing functions. The
complement is also true: Procedural code makes it hard to add new data structures because all the functions must
change. OO code makes it hard to add new functions because all the classes must change." - [1](#references)

## [DS01] Do Not Mix Data Structures with Objects

The address data structures below have no behavior, and we have a class that manipulates the address.

```javascript
let usaAddress = {
    country: 'USA',
    city: 'San Francisco',
    state: 'California',
    zipcode: '94131',
    street: '312 Gardenside Drive',
    apt: '131'
}

let ukAddress = {
    country: 'UK',
    postTown: 'London',
    county: 'Essex',
    zipcode: 'ABC-94132',
    street: '345 Market Street',
    apt: ''
}

class AddressManager {
    #warehouseZipcode = '12345';

    constructor(address) {

    }

    create() {

    }

    read() {

    }

    update() {

    }

    delete() {

    }

    calculateShipping() {

    }
}
```

## References

1. Clean Code by Robert C. Martin, Objects and Data Structures.

---
