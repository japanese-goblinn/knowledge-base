> [`NSLock` the best choice for locking in Swift](https://gist.github.com/tclementdev/6af616354912b0347cdf6db159c37057)

> [Acquiring an uncontended `os_unfair_lock` is just doing an atomic compare and swap of the current thread id with the lock int, and then checking if it failed due to being nonzero before. Releasing it is similar](https://twitter.com/Catfish_Man/status/1523337550076604417)

- **Notes**
	- [Swift Concurrency](../Swift/Swift%20Notes/Swift%20Concurrency.md)
	- [GCD. Grand Central Dispatch](Apple%20Platform%20Cuncurrency/GCD.%20Grand%20Central%20Dispatch.md)
		- [Concurrency by Tutorial](Apple%20Platform%20Cuncurrency/Concurrency%20by%20Tutorial.md)
	- [Apple Operations](Apple%20Operations.md)
	- [GCD vs Operations](Apple%20Platform%20Cuncurrency/GCD%20vs%20Operations.md)
- **Links**
	- [Full guide](https://www.uraimo.com/2017/05/07/all-about-concurrency-in-swift-1-the-present/#dispatch-assertions)
	- [Locks, Thread Safety, and Swift: 2017 Edition](https://www.mikeash.com/pyblog/friday-qa-2017-10-27-locks-thread-safety-and-swift-2017-edition.html)
	- [Info about locks and other useful stuff](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/Multithreading/ThreadSafety/ThreadSafety.html)

