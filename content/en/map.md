---
title: "Map"
type: docs
weight: 4
---

Applies a mapping function to each element of a source.

```go
func Map[T any](mapper Mapper[T], source any, dest any) *Builder[T]
```

* Description: Applies the mapper function to each element of source and stores the results in dest.
* Parameters:
    
    * mapper: Function that transforms each element of type T into another type. It takes an element of type T and returns a transformed value of type any.

    * source: Source data to transform (expects pointers to slices or maps).

    * dest: Destination where mapped results will be stored (expects pointers to lists or maps).

Example

```go
package main

import (
	"fmt"
	"github.com/jose78/go-collection"
)

func main() {
	slice := []int{1, 2, 3, 4, 5}
	var mappedSlice []string
	
	builder := collection.Map(func(elem int) any {
		return fmt.Sprintf("Number %d", elem)
	}, &slice, &mappedSlice)
	
	if err := builder.Error(); err != nil {
		fmt.Printf("Error during mapping: %v\n", err)
	} else {
		fmt.Println("Mapped slice:", mappedSlice)
	}
}
```
