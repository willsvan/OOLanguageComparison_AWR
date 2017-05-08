# Swift (Protocols)

Protocols are defined and used in much the same way as interfaces in many object oriented languages. Any given class must explicitly adopt any protocol it wishes to conform to, and can freely adopt multiple protocols. Protocols can require both properties and methods. The following example conforms to both a property requirement protocol and a method requirement protocol at the same time.

```
protocol Named {
    var name: String { get }
}

protocol Speaker {
    func Speak()
}

class Person : Named, Speaker {
    var name = "Steve"
    var age = 26

    func Speak() {
        print("Hello!")
    }
}
```

# Go (Interfaces)
Go takes a somewhat unique approach to interfaces in that they are used implicitly rather than explicitly. If any type satisfies the requirements of an interface, and can be used as that interface.

```
type Speaker interface {
    Speak()
}

type Person struct {
    name = "Steve"
    age = 26
}

func (p Person) Speak() {
    fmt.Println("Hello")
}
```

In this example, our type Person is considered a Speaker even without declaring it as such simply because it fulfills all of the requirements of the interface. 

### The "Empty Interface"
Due to the implicit nature of interface implementation, the interface with no requirements - `interface{}` - is inherently satisfied by all types. Because of this, it can be used to handle unknown types. When using this, the programmer has to be careful to check the underlying type to avoid panics upon attempting to assert an interface{} into a type that it doesn't actually contain. 

```
var a interface{} = "hello"

b, ok := a.(string)
if ok {
    fmt.printf(b)
}
```
