# Swift 

Closures, which are similar to lambda expressions, are possible in Swift as well as Go. 
<br><br>
Here is an example of a closure in swift
```
func makeIterator(from start: Int, step: Int) -> () -> Int {
    var i = start
    return {
        let currentValue = i
        i += step
        return currentValue
    }
}

var iterator = makeIterator(from: 1, step: 1)

iterator() // 1
iterator() // 2
iterator() // 3

var anotherIterator = makeIterator(from: 1, step: 3)

anotherIterator() // 1
anotherIterator() // 4
anotherIterator() // 7
anotherIterator() // 10
```
# Go 

Go does not have lambda expressions, but here is a similar closure example to the one above. <br><br>
This iterator function returns a function, which closes over the variable x to form the closure. 

```
func iterator() func() int {
    x := 0
    return func() int {
        x += 1
        return x
    }
}
func main() {
```
We call our iterator, assigning its return, which is the anonymous inner function. The function captures the value, which will be updated each time we call nextInt.
```
    nextInt := iterator()
    fmt.Println(nextInt()) //1 
    fmt.Println(nextInt()) //2
    fmt.Println(nextInt()) //3

```
Let’s make a new function to make sure it gets a new state 
```
    newInts := iterator() 
    fmt.Println(newInts()) //1
}
```
