# Multithreading in Swift

The Swift language allows users to implement multithreading with the use of Grand Central Dispatch (GCD) API.  Swift has shifted away from conventional threads in favor of asynchronous functions. GCD moves much of the code typically written for managing down to the system level, providing a higher level abstraction. Swift provides users with several different types of queues for executing code as threads. Two types of queues provided in Swift are:
1. ``` OperationQueue ``` which takes a set of ``` Operation ``` objects
1. ``` DispatchQueue ``` which manages the execution of work items

To use an ``` OperationQueue ``` users can use ``` addOperation(Operation) ``` to queue an ```Operation``` object for execution. Below is a program for executing two threads using an operation queue to dispatch the threads:

```swift
import Cocoa
import Dispatch
import PlaygroundSupport

// Fix to make Xcode playground stay running until thread finishes execution
PlaygroundPage.current.needsIndefiniteExecution = true

// Operation queue which launches operations to be executed by threads
let queue = OperationQueue()
// Start the first thread
queue.addOperation() {
    var threadName = "Thread 1"
    for i in 0 ... 100 {
        print("\(threadName) is \(i)")
    }
    
}
// Start the second thread
queue.addOperation() {
    var threadName = "Thread 2"
    for i in 0 ... 100 {
        print("\(threadName) is \(i)")
    }

}
```

# Multithreading in Go

The Go language does not support threads like many other languages such as Swift, Java, and C/C++. Instead, Go offers Goroutines, which are a sort of lightweight abstraction of threads. Goroutines require minimal system resources in terms of memory. Upon creation, a single Goroutine will take up 2kB of stack space which can grow by allocating heap storage. This is significantly cheaper than the cost of launching threads which usually take up ~1Mb of space upon creation. This allows Go to easily spawn thousands of Goroutines simultaneously without significant performance impact. The following is an example of spawning two Goroutines which both count to 100 and stop:

```go
package main

import "fmt"

func displayIteration(threadName string) {
        for i := 0; i <= 100; i++ {
                fmt.Println(threadName, ":", i)
        }
}

func main() {
        fmt.Println("Starting Goroutines:")

        go displayIteration("Goroutine 1")
        go displayIteration("Goroutine 2")

        var input string
        fmt.Scanln(&input)
        fmt.Println("Done")
} 
```

Go also offers "channels" which are analogous to pipes in C. Channels offer a way to communicate with Goroutines by sending values to and from them. A channel can be created like such `variableName := make(chan datatype)`. To send data from a variable to a channel you would use `ch <- v` and to receive data from a channel and assign it to a variable you would use `v := <-ch`. The following is an example of using channels in Go to sum the members of an array:

```go 
package main

import "fmt"

func sum(s []int, c chan int) {
	sum := 0
	for _, v := range s {
		sum += v
	}
	c <- sum // send sum to c
}

func main() {
	array := []int{1,2,3,4,5,6}

	c := make(chan int)
	go sum(array[:len(array)/2], c)
	go sum(array[len(array)/2:], c)
	x, y := <-c, <-c // receive from c

	fmt.Println(x, y, x+y)
}

```
