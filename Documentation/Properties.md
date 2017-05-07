# Properties in Swift

The Swift language programming language provides the "get" and "set" keywords which can be used inside of declaration to assign values. The "get" and "set" can be used like this:

```swift
class Dog {
    var name : String
    var breed : String
    var _age : Int = 0
    var age :  Int {
        get {
            return _age
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
Expected Output:
1. "Sherman is a 10 year old Lab"
1. "Sherman is now 11 years old"

Swift allows for computed properties using the "get" and "set" keywords to dynamically computed a properties value. Modifying the previous code we use "get" and "set" to create a computed property:

```swift
class Dog {
    var name : String
    var breed : String
    var _age : Int = 0
    var age :  Int {
        get { // Modified to compute the dog's age in "human" years
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
print("\(myDog.name) is a \(myDog.age) years old in human years")

// Set is triggered for age in the class
myDog.age = 11;

// Get is triggered for age in the Dog class
print("\(myDog.name) is now \(myDog.age) human years old")
```

Expected Output:
1. "Sherman is a 70 years old in human years"
1. "Sherman is now 77 human years old"

# Properties in Go

The Go language does not provide getters and setters by default, users must implement them on their own. The following shows how to implement getter and setter methods in Go:

```go

import "fmt"

type Dog struct {
        name string;
        breed string;
        age int;
}

func NewDog(name string, breed string, age int) Dog {
        d := new(Dog)
        d.name = name
        d.breed = breed
        d.age = age
        return *d
}

func (d Dog) GetDogAge() int {
        return d.age
}

func (d *Dog) SetDogAge(age int) {
        d.age = age
}

func main() {
        myDog := NewDog("Sherman", "Lab", 10)
        myDog.SetDogAge(11)
        age := myDog.GetDogAge()
        fmt.Println(age)
}
```

The Go language allows for users to create computed properties by modifying the code for the getters and setters like so:

```go



package main

import "fmt"

type Dog struct {
        name string;
        breed string;
        age int;
}

func NewDog(name string, breed string, age int) Dog {
        d := new(Dog)
        d.name = name
        d.breed = breed
        d.age = age
        return *d
}

func (d Dog) GetHumanYears() int {
        return d.age * 7
}

func (d *Dog) SetDogAge(age int) {
        d.age = age
}

func main() {
        myDog := NewDog("Sherman", "Lab", 10)
        myDog.SetDogAge(11)
        age := myDog.GetHumanYears()
        fmt.Println(age)
}
```
