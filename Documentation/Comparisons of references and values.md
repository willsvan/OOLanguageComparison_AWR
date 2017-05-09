# Swift 

To compare values in swift, you also use the == operator. This works for strings, and other comparable data types. Swift also implements the !== and === operators for determining if two object references both refer to the same object instance. 
<br><br>
This is an example of string comparison, as well as using the === and !== operators. 
```
class Person {
}

let string1 = "Dale"
let string2 = "Dale"
let string3 = "Not Dale"

let person = Person()
let person2 = person
let person3 = Person()


person === person2 // true
person === person3 // false
//string1 === string2 compile error 
string1 == string2 //true 
string2 == string3 //false
```

# Go 

To compare values in go, you simply use the == and != operators. These will work for any data types, as long as they are comparable. For example you can not compare a boolean to a string, or other mismatched types. To compare pointer values, you dereference the pointer like you would and C, then compare the values. Otherwise you compare the addresses of the pointers. 
<br><br>
Here we will set up some comparable values and evaluate them. 
```
var a int = 1
var b int = 2
var s1 string “Dale” 
var s2 string “Dale”
var c float32 = 3.3
var d float32 = 4.4
fmt.Println(a == b) // false
fmt.Println(s1 == s2) //true
fmt.Println(c == d) // false
```
