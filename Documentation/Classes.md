[Home](../README.md)

# Classes in Swift

The Swift programming language allows programmers to create both structs and classes. Class and struct declarations are created using the "class" and "struct" keywords respectively and simply including the appropriate data types and functions. To following code is an example declaring a dog class in Swift:

```swift
class Dog {
    // Class fields
    var name: String
    var breed: String
    var age: Int
    
    ...
}
```

Swift does not have constructors per say, but instead has initializers. Initializers take a set of parameters which are then assigned to members of the struct. The following code is an example of using initializers to initialize the dog class:

```swift
class Dog {
    var name : String
    var breed : String
    var age: Int
    
    // This is a a Swift initializer
    init(name:String, breed:String, age: Int) {
        self.name = name
        self.breed = breed
        self.age = age
    }
}
```

To create an instance of a class in Swift users should use the "let" keyword followed by the name of the instance: 

```swift
// Create an instance of the Dog class from the initializer
let myDog = Dog(name: "Sherman", breed: "Lab", age: 10)
```

To de-initialize a class in Swift, users should use the `deinit` keyword followed by a set of curly braces inside of the class declaration. Inside the curly braces users can then define the procedure for initializing the class. De-initializing a class is not necessary in Swift since the Automatic Reference Counter will automatically free up any allocated memory when the number of references to a class drops to zero.

The following is a program for crating a dog class and printing information from it:

```swift
import Cocoa

var str = "Hello, playground"

class Dog {
    var name : String
    var breed : String
    var _age : Int = 0
    var age :  Int {
        get {
            return _age * 7
        }
        set (newAge) {
            if newAge >= 0 {
                _age = newAge
            }
            else {
                print("Error: Age cannot be less than zero")
            }
        }
    }
    
    init(name:String, breed:String, age: Int) {
        self.name = name
        self.breed = breed
        self.age = age
    }
    
}

let myDog = Dog(name: "Sherman", breed: "Lab", age: 10)

// Get is triggered for age in the Dog class
print("\(myDog.name) is a \(myDog.age) year old \(myDog.breed)")

// Set is triggered for age in the class
myDog.age = 11;

// Get is triggered for age in the Dog class
print("\(myDog.name) is now \(myDog.age) years old")
```
Expected output:
1. "Sherman is a 10 year old Lab"
1. "Sherman is now 11 years old"

# Classes in Go

The Go programming language also allows programmers to create structs and classes. The Go language does not require explicit class definitions like Java. In place of explicit declarations, classes are implicitly defined by creating a set of methods which act on a specified type such as a struct or other user-defined data type. The following is an example of creating a dog class in the Go language:

```go
type Dog struct {
        name string;
        breed string;
        age int;
}
```

The Go language does not support constructors, but users can use a constructor like factory design pattern achieve much the same effect. The following is an example of using the factory design pattern to initialize an instance of a dog class:

```go
func NewDog(name string, breed string, age int) Dog {
        d := new(Dog)
        d.name = name
        d.breed = breed
        d.age = age
        return *d
}
```

To create an instance of the dog class in the Go language users should use the following syntax:

```go
myDog := NewDog("Sherman", "Lab", 10)
```

The Go language does not provide a method for de-initializing or deconstructing a class since memory management if handled automatically for the user by the garbage collector.

[Home](../README.md)
