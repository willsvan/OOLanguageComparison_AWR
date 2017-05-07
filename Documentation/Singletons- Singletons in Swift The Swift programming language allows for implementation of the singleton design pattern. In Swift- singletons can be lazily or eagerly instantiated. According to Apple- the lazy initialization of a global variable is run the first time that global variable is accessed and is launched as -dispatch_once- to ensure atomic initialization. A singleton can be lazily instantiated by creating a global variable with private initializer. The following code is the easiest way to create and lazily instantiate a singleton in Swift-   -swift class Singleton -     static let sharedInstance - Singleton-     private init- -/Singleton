# Singletons in Swift
The Swift programming language allows for implementation of the singleton design pattern. In Swift, singletons can be lazily or eagerly instantiated. According to Apple, the lazy initialization of a global variable is run the first time that global variable is accessed and is launched as `dispatch_once` to ensure atomic initialization. A singleton can be lazily instantiated by creating a global variable with private initializer. The following code is the easiest way to create and lazily instantiate a singleton in Swift: 

```swift
class Singleton {
    static let sharedInstance = Singleton()
    private init() {} // Marking init private launches as dispatch_once
    ...
}

private var Singleton: Singleton
``` 

Using this method ensures that `dispatch_once` is used on the singleton and ensures that the singleton is both unique and thread safe.

# Singletons in Golang
Singletons can be implemented in Go and can be made thread safe by implementing atomic locking. The following code shows how a thread safe singleton is created in the Go language:

```go
package GoSingleton

import "sync"

type single struct {
        O interface{};
}

var instantiated *single
var once sync.Once

func New() *single {
        once.Do(func() {
                instantiated = &single{}
                print("Singleton instantiated!")
        })
        return instantiated
}
``` 


By carefully implementing locking, a singleton can be lazily instantiated.

```go
package singleton

import (
    "sync"
)

type singleton struct {
}

var instance *singleton
var once sync.Once

func GetInstance() *singleton {
    once.Do(func() {
        instance = &singleton{}
    })
    return instance
}
``` 
