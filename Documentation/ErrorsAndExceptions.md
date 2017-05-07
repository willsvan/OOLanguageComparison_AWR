[Home](../README.md)

# Errors and Exception Handling in Swift
The Swift programing language includes server ways of handling errors and exceptions. Swift provides the `Error` protocol for users to represent errors. The `Error` protocol is an empty protocol which allows users can use with enumerations to model error conditions. An `Error` enumeration might look something like this:

```swift
enum PossibleErrors: Error {
    case someError
    case someErrorWithParams(num: Int)
    case anotherError
}
```

Swift also allows users to throw errors using the `throw` keyword. Users can throw an error like this:

```swift
throw PossibleErrors.someErrorWithParams(num: 2)
```

Users can also propagate errors by using the `throws` keyword to indicate that a function, method, or initializer is capable of throwing an error. The `throws` keyword should be placed in the declaration following the parameters and before the `->`. Example of a function that can and cannot throw errors:

```swift
// Function that cannot throw an error
func myFunction() -> String

// Function that can throw an error
func myErrorThrowingFunction() throws -> String
```

More advanced and graceful error handling can be achieved with the use of try catch blocks. The `do-catch` statement is particularly useful for catching errors and appropriately handling any errors. A `do-catch` will be structured like this:

```swift
do {
    try expression
    statements
} catch error1 {
    statements
} catch error2 where condition {
    statements
}
```

The following code is an example of a program that handles errors using the `do-catch` structure:

```swift
enum PohoneError: Error {
    case noSignal
    case lowBattery
}

var noSignal: Bool = true
var lowBattery: Bool = false

func checkPhoneErrors() {
    if noSignal {
        print("No signal, need better reception!")
        // Do something about the error
    }
    if lowBattery {
        print("Low batter, charge your phone!")
        // Do something about the error
    }
}

do {
    try checkPhoneErrors()
} catch PohoneError.noSignal {
    print("No signal, need better reception!")
} catch PohoneError.lowBattery {
    print("Low batter, charge your phone!")
}
```
Expected output: "No signal, need better reception!"

Finally, Swift allows users to convert errors to optional values. `try?` can be used to evaluate an expression and determine if an error has been thrown. If an error is thrown when `try?` is evaluated, then the expression will evaluate to `nil`. An example of a function that uses `try?` might look like this:

```swift
func doSomthing() -> Data? {
    if let data = try? getData() {return data }
    return nil
}
```

# Errors and Exception Handling in Go

The Go language takes a rather simplistic approach to error handling and exceptions. Instead of try catch blocks, Go allows programmers to include multiple return values for a function. This functionality allows a programmer to return error codes or messages that can be displayed to the user or propagated to other functions so that they behave appropriately in the event of an error. Convention dictates that errors should be the last return value and have the type error, which is a built in interface. If the value in the error return position is `nil` it indicates that no error has occurred. Users can create their own custom error types by implementing the `Error()` method on them. The following code is an example of a custom error type with the `Error()` method implemented:

```go
// Function that returns a default Go error 
func normalErrorFunc(num int) (int, error) {
        if arg < 0 {
                return -1, errors.New("Must supply a non-negative number")
        }
        return num, nil
}
// Custom error type
type numError struct {
        num int
        msg string
}
// Error() method must be implemented on custom error types
func (e *numError) Error() string {
        return fmt.Sprintf("%d - %s", e.num, e.msg)
}
// Function that returns our custom numError type
func customErrorFunc(num int) (int, error) {
        if num < 0 {
                return -1, &numError{arg, "Negative number supplied"}
        }
        return num, nil
}

func main() {
        err := customErrorFunc(10)
        if err != nil {
            log.Fatal(err)
        }
}
```

After functions are executed it is common practice to immediately check for errors to deal with them as they arise.

[Home](../README.md)
