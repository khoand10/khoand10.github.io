+++
author = "khoand"
title = "Hello world"
date = "2022-04-15"
description = "test my first blog"
tags = [
    "golang",
]
summary ="test golang blog"
+++

Test first blog

## Hello would
```golang
package main

import (
	"fmt"
	"time"
)

func main() {
	fmt.Println("Welcome to the playground!")

	fmt.Println("The time is", time.Now())
}
```

## maximum
{{< highlight go >}}
package slices

func maximum(nums []int) int {
	var max int
	for i := 0; i < len(nums); i++ {
		if nums[i] > max {
			max = nums[i]
		}
	}
	return max
}

// BONUS!
func rangeMaximum(nums []int) int {
	var max int
	for _, val := range nums {
		if val > max {
			max = val
		}
	}
	return max
}
{{< / highlight >}}

## html
```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Example HTML5 Document</title>
</head>
<body>
  <p>Test</p>
</body>
</html>
```

## Test highlight code
{{< highlight go "linenos=table,linenostart=1,hl_lines=5-7" >}}
func GetTitleFunc(style string) func(s string) string {
  switch strings.ToLower(style) {
  case "go":
    return strings.Title
  case "chicago":
    return transform.NewTitleConverter(transform.ChicagoStyle)
  default:
    return transform.NewTitleConverter(transform.APStyle)
  }
}
{{< / highlight >}}