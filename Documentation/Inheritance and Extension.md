# Swift 

Swift - Swift fully supports inheritance. Here is an example of a sub class inheriting values from its super class and printing them

```
class Dog {
    var breed = "Labraboy"
    var speed = 14.0
    var description: String {
        return "This dog is a \(breed)"
    }

}

let doggo = Dog()

print(doggo.description)

class Pet: Dog {
    var name = "Clark"
}

let clarko = Pet()
clarko.breed = "Mini Aussie boy"
clarko.speed = 7575

print("\(clarko.description)")
```

Output: <br>
This dog is a Labraboy <br>
This dog is a Mini Aussie boy

# Go 

Golang does not support inheritance. You can perform object-like composition however, which is thought to be a better idea than inheritance. 

```
package main

import (
	"fmt"
)

type Pet struct {
  name string
}

type Dog struct {
  Pet
  Breed string
}

func (p *Pet) Bork() string {
  return fmt.Sprintf("my name is %v", p.name)
}

func (p *Pet) getName() string {
  return p.name
}

func (d *Dog) Bork() string {
  return fmt.Sprintf("%v and I am a %v", d.Pet.Bork(), d.Breed)
}

func main() {
  d := Dog{Pet: Pet{name: "Clark"}, Breed: "Mini Aussie Boy"}
  fmt.Println(d.getName())
  fmt.Println(d.Bork())
}
```
Output: <br>
Clark <br>
my name is Clark and I am a Mini Aussie Boy
