# Swift
Swift supports traditional callback structure much like most other OO languages, but also provides us with a feature known as _delegates_ - which essentially serve as a way for an entity to pass a reference to itself into another entity, which can then be use to communicate events back to the parent. 

# Go
Event handlers, or more generally callbacks, are somewhat eschewed by the Go language. Since Go implements concurrency at a language level, it inherently encourages the use of it's special communication feature - channels. Channels are a simple mechanism to communicate with goroutines, and can easily be passed into them upon their creation. For example, we can spawn a goroutine to count up to 10000 and have it send a message back every time it hits a multiple of 120 or 250.

```
type CountEvent struct {
	multiple int
	num      int
}

func main() {
	eventChan := make(chan CountEvent)
	go generateEvents(eventChan)
	for event := range eventChan {
		switch event.multiple {
		case 120:
			fmt.Printf("Multiple of 120 happened at %v!\n", event.num)
		case 250:
			fmt.Printf("Multiple of 250 happened at %v!\n", event.num)
		}

	}
}

func generateEvents(event chan CountEvent) {
	for i := 0; i < 10000; i++ {
		if i%120 == 0 {
			event <- CountEvent{multiple: 120, num: i}
		}
		if i%250 == 0 {
			event <- CountEvent{multiple: 250, num: i}
		}
	}
	close(event)
}
```
It is, however, still perfectly possible to use a traditional callback model in Go, and the standard library does so in many cases where it makes sense. For example, the "net/http" server takes in handler callbacks for each URL. 

