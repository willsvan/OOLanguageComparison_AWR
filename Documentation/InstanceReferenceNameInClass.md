# Swift 

Swift automatically assumes that when you refer to a property or method of an instance, that it is the current instance. This means you do not have to use self unless you are working with two names that are the same. Let’s say we have a parameter name on an instance method that matches the name of a property on the instance. This is where you would need to use self in the context of the method to avoid using the instance property. 

Struct Example has a property called x. 
```
struct Example {
    var x = 0.0, y = 0.0
    func isMethod(x: Double) {
        return self.x 
    }
}

```
When I call isMethod, it knows to use its function parameter, not the property “x” on the struct Example. 

  

# Go 

In Go, to access a field of of the current instance of a structure, you use a receiver. Receivers can be either by value or by reference. These function receivers are similar to “this” and “self” in the sense that can access the current instance of your structure. Go’s departure from object orientation does away with “this” and “self.”

Here we will make a structure with a method that has a pointer receiver. 

```
package main
import "fmt"
type example struct {
    width, height int
}
```
Here is the area method, it has a pointer receiver called "this"
``` 
func (this *example) area() int {
    return this.width * this.height
}
func main() {
    this := example{width: 3, height: 6}
}

```

Here we create a struct, and pass in the values to our function receiver, calling the method on our current example struct. 


