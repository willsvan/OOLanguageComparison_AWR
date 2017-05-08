# Swift
The Swift language, which prefers the "nil" nomenclature, has one unique core language feature for dealing with values that might be nil. 
### Optionals
In Swift, _only_ "Optional" types (`Integer?`, `String?`, etc) can possibly be nil. Non-optionals must always be instantiated and can never be nilled. Although dealing with these types adds a few extra steps such as unwrapping (see [Types](types.md) for more information), it guarantees via enforced language rules that the programmer will never encounter a nil value where they didn't expect it. 

# Go
Go, which also uses the word "nil", allows nil pointers but not nil values. Value types in Go are automatically instantiated to a sane 0/empty value if not otherwise declared. Nil pointers on the other hand, are seen somewhat commonly, especially in error handling. It is perfectly valid for any pointer, or specifically map, channel, function, slice, or interface (which are implemented as pointers), to be set to nil.  The most common way to check for errors from methods is `if err != nil` where err is a returned Error type, and we see this particular block all throughout most Go. 
