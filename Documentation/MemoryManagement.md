# Memory Management in Swift

In the Swift language memory is allocated automatically for the user. The amount of memory allocated is determined by Automatic Reference Counting, or ARC for short. ARC allocates a chunk of memory each time a class or variable is instantiated. ARC also automatically deallocates memory once the count of active references drops to zero. 

# Memory Management in Golang
Much in the same vain as Swift, the Go language handles memory allocation for the user automatically. When a class or variable is instantiated, memory is automatically allocated. When a Go program is run, a large chunk of virtual  memory (VIRT) is reserved along with a resident set size (RSS). Go implements a garbage collector so there is no need to manually deallocate memory. Typically, the garbage collector is run every two minutes or if a span is unused for five minutes the garbage collector scavenger allows the memory to released. 
