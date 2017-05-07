[Home](../README.md)

# Unique Features of the Swift Language

The Swift programming language was created by Apple as a general purpose, multi-paradigm, compiled, programming language. Swift runs on a wide range of Apple products as well as Linux, and is capable of running C, C++, and Objective-C to all be run within a single program. Swift provides a high level abstraction of these lower level languages and does away with much of the code developers would usually have to write when developing applications. while still allowing programmers to use lower level functionality if need be. Swift handles a lot of work behind the scenes, which can be seen in things like Grand Central Dispatch which abstracts the the execution of threads with queues that ready tasks for execution by threads automatically. The language sacrifices some of the verbose language of Objective-C for this but requires a lot less code to do some more complex tasks.

Swift also provides support for optionals which act as a sort of wrapper type for most any type in the language. Optionals can help programmers to avoid nil pointer dereferences which is handy in many applications. Functions and closures in are also treated as first-class types. 

# Unique Features of the Go Language

It is often debated whether or not the Go language falls into the object orientated paradigm. The language feels a lot like C, but has a few modifications. Unlike what C++ was to C, Go does not fully embrace the object orientated idea of classes. Instead, Go offers the ability to write structs and declare methods for them. The language offers two features to replace class based inheritance. The first is embedding, which is essentially automated composition. The second is the implementation of interfaces which provide runtime polymorphism. So long as the type implements all methods of an interface it will automatically inherit that interface, without having to explicitly state it.

Aside from its questionable object-orientated status, the language is aimed at being a lightweight and minimal language that does away with unnecessary typing and overly verbose language. Go offers simplistic alternatives to many features presented in other languages in order to increase code readability. The language also enforces users to conform to a particular style of formatting code in order to offer a universal style of code. The language even offers the `gofmt` command which can be used on a `.go` file like so `$ gofmt source.go > new_source.go` to properly format the whitespace in their code.

[Home](../README.md)
