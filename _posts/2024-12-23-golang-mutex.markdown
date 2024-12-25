---
layout: post
title:  "Golang Mutex Usage"
date:   2024-12-23 22:00:00 +0300
categories: golang
---

## Goroutine and Mutex Usage

* Without Mutex

```golang
package main

import (
	"fmt"
	"sync"
)

func main() {
	var counter int
	var wg sync.WaitGroup

	for i := 0; i < 50000; i++ {
		wg.Add(1)
		go func() {
			defer wg.Done()
			counter++
		}()
	}

	wg.Wait()
	fmt.Println("Son Sayaç Değeri:", counter)
}
```

* Output

It gives different output for each run.

First Run: 48993
Second Run: 48780
Third Run: 48858

* Without Mutex

```golang
package main

import (
	"fmt"
	"sync"
)

func main() {
	var counter int
	var mu sync.Mutex // Define Mutex
	var wg sync.WaitGroup

	for i := 0; i < 50000; i++ {
		wg.Add(1)
		go func() {
			defer wg.Done()
			mu.Lock() // Locks
			counter++
			mu.Unlock() // Unlocks
		}()
	}

	wg.Wait()
	fmt.Println("Son Sayaç Değeri:", counter)
}
```

* Output

It gives same output for each run.

Output: 50000

* Mutex only protects a specific block of code or variables:
  * If you are working with multiple variables and want to protect them, the same mutex should be used in all code blocks accessing those variables.
* Not all variables are locked, only the code block protected by the mutex is:
  * mu.Lock() makes only the code or variable protected by mu thread-safe.
