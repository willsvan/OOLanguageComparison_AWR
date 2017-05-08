# Swift
## Safety and Primitives
Swift is a type-safe language, with expected types being checked at compile-time, rather than run-time. At the same time, it also features very powerful type inference, allowing the programmer to avoid explicitly declaring types in many situations. Swift doesn't specifically have primitive types at the language level. Instead, many common types (int, bool, etc) are implemented via structures in the standard library. Interestingly, some of these still receive special handling on the backend with regard to how their operations are mapped to CPU instructions. 

## Optionals
One interesting feature of the Swift is optional types, a clean way to handle the absence of values. A normal type in Swift can never be set to nil. Instead, you must use an optional. An optional Type is essentially a box that *might* contain a Type. The programmer can check if this variable contains anything, and then intentionally unwrap it to get the value inside. 

```
var optionalInt: Int? = 1
if optionalInt != nil {
    let unwrappedInt: Int = optionalInt!
    print(unwrappedInt)
}
```

## Reference and Value Types
Swift supports both reference and value types, but seems to favor value types in much of the standard library.

### Reference
_class_ objects, such as the following, are always reference types. 

```
class MyClass {
    var modified = false
}
instance1 = MyClass()
instance2 = instance1
instance1.modified = true
print(instance2.modified)
```

This example will output a value of true, because both variables reference the same memory location. 

### Value
Value types include, but are not limited to, _struct_, _enum_, and a variety of common standard library types such as _int_ and _string_. This allows the programmer to create their own value types as well, thanks to the inherent value typed property of structs and enums. 

```
struct MyStruct { var modified = false }
var instance1 = MyStruct()
var instance2 = instance1
instance1.modified = true
println("\(instance2.modified)")
``` 
This example will output a value of false, because the second instance was copied from the value of the first before we modified it, rather than copying a reference to the same memory. 

# Go
Similar to Swift, Go is also a strongly typed language. However, Go does actually implement some true primitive types, such as various sizes of signed and unsigned ints, floats, and complex numbers, as well as common types such as strings and bools. 

## Reference and Value Types
In Go, all types are passed by value nearly everything is a value type.
### Reference
A couple interesting exceptions to this are maps, slices, and channels, which are implemented as reference types. For example, passing a slice to a function is still technically passing by value, but the value in question is a pointer to the underlying array.

```
func modifySlice(s []int)  {
    s[1] = 3
    fmt.Printf("%v, ", s)
}
func main() {
    s := []int{1, 2}
    fmt.Printf("%v, ", s)
    modifySlice(s)
    fmt.Printf("%v\n", s)
}
```

This code block will output "{1, 2}, {1, 3}, {1, 3}" because the function is able to modify the data of the original slice reference. 

### Value
The vast majority of all types in Go are value types. Furthermore, all parameters are passed by value. Therefore, the programmer can easily create new value types of their own. 
