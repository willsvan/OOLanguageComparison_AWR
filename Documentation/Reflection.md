# Swift 
The Swift language allows basic read-only object reflection through the use of the Mirror structure. After creating a Mirror of an object, you can query it for information about the object that it reflects. In the following example, we will create a mirror of a Dog struct..

```
struct Dog {
    let name: String
    let breed: String
    let age: Int
}

let dog1 = Dog(name: "George", breed: "Lab", age: 4)
let dog1Mirror = Mirror(reflecting: dog1)

for (name, value) in dog1Mirror.children {
    guard let name = name else { continue }
    print("\(name): \(type(of: value)) = '\(value)'")
}
```

This simple loop will output the name, type, and value of each property of our Dog

```
name: String = 'George'
breed: String = 'Lab'
age: Int = '4'
```

# Go
The implementation of reflection in Go is fairly similar, using the 'reflect' package this time. Notably, Go does allow modification in contrast to the read-only approach of swift. In this example we will iterate through the fields of a Dog structure, similar to the Swift example, and additionally modify one of the fields by name.

```
type Dog struct {
	Name  string
	Breed string
	Age   int
}

func main() {
	dog1 := &Dog{Name: "George", Breed: "Lab", Age: 5}
	dogVal := reflect.ValueOf(dog1).Elem()

	for i := 0; i < dogVal.NumField(); i++ {
		fieldValue := dogVal.Field(i)
		fieldType := dogVal.Type().Field(i)
		fmt.Printf("%s: %s = %v\n", fieldType.Name, fieldType.Type, fieldValue.Interface())
	}
	dogVal.FieldByName("Name").SetString("Steve")
	fmt.Println(dog1.Name)
}
```

One very useful application of reflection when working in Go is its use in determining the type of something received as an empty interface, which could feasibly contain any type. 
                                           
