# Swift 

Swift uses modules to organize and group methods and classes. You can import these modules easily and use them in your code without causing name collision and to promote organization. 
If I had a module called Example1 and a module called Example2, and Example1 had a method called add, I could use the method by doing this: 


```
import Example1 
import Example2 

Example1.add()
```

If you would like to make your own importable module, Xcode provides a template to create one. This template includes a header file for your module or framework, and an information configuration file.  

# Go 

Go uses packages to create namespaces. You can create a package and access it by importing it. 
Here we create a package called "example" with an add function at GolandProjects/example. 

```
package example

func add(x int, y int) int {
	return x + y
}
```

Import our package and call add on it in main: 

```
package main

import ( 
"GolandProjects/example"
“fmt” 
)

func main() {
fmt.Println(add(2, 4))
 
}
```
