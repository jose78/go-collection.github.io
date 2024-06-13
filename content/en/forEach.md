---
title: "ForEach"
weight: 3
---

Iterates over elements in a source and applies an action for each element.

```go
func ForEach[K any](action Action[K], src any) *Builder[K]
```

* Description: Iterates over elements of src and executes the action for each element.
* Parameters:
    
    * action: Function defining the action to perform on each element. It takes an index (int) and an element of type K.
        
    * src: Source data to iterate over (expects pointers to slices or maps).

### Example

```go
package main

import (
	"fmt"
	"github.com/jose78/go-collection"
)

func main() {
	slice := []int{1, 2, 3, 4, 5}
	builder := collection.ForEach(func(idx int, elem int) {
		fmt.Printf("Index %d: %d\n", idx, elem)
	}, &slice)
	
	if err := builder.Error(); err != nil {
		fmt.Printf("Error during iteration: %v\n", err)
	}
}

```