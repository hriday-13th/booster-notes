# Go routines are lightweight abstractions over threads
# They're managed by the Go runtime scheduler

# The Go scheduler uses an M:N model
# M = OS threads
# N = goroutines

# GOMAXPROCS = Number of CPU cores

Side Note:
Concurrency means executing multiple tasks at the same time conceptually, not simultaneously.

Parallelism mean executing multiple tasks at the same exact time. Requires multiple CPU cores.

# Go routines are scheduled cooperatively; they run until they block or yield (I/O, channel ops)


## Code implementations

Create and run a go routine
```go
go someFunc()
```

WaitGroup -> WaitGroups help with the synchronization when you need to wait for all of the goroutines.
```go
package main

import (

)

func printNums(wg *sync.WaitGroup) {
    defer wg.Done()
    for i := 1; i < 6; i++ {
        fmt.Println(i)
    }
}

func main() {
    var wg sync.WaitGroup
    wg.Add(1)
    go printNums(wg)
    wg.Wait()
    fmt.Println("Fin")
}
```

# Channels: A communication medium and data synchronization between go routines. They provide a means for go routines to send and receive values safely.

# Types of channels
1. Unbuffered Channels - No capacity, sending and receiving blocks the routines.
Unbuffered channels promote stricter synchronous code execution.

```go
ch := make(chan int) // Creation of unbuffered channel
ch <- 10 // Sending a value to the channel
<- ch // Receiving from the channel
```

2. Buffered Channels - Have a capacity, allow only a certain number of values to be sent without locking.
Buffered channels promote flexibility in comparison to unbuffered ones.

```go
ch := make(chan int, 2) // Creation of a buffered channel of size 3
ch <- 1
ch <- 2
ch <- 3 // Gets blocked as channel is at its limit
```

# Select statement
Select statement allows you to handle multiple channel operations simultaneously. Enables non-blocking communication between go routines.

```go
package main

import (
    "fmt"
    "time"
)

func ping(ch chan <- string) {
    for {
        time.Sleep(time.Second)
        ch <- "ping"
    }
}

func pong(ch chan<- string) {
    for {
        time.Sleep(time.Second)
        ch <- "pong"
    }
}

func main() {
    pingCh := make(chan String)
    pongCh := make(chan String)

    go ping(pingCh)
    go pong(pongCh)

    for {
        select {
            case msg := <- pingCh:
                fmt.Println(msg)
            case msg := pongCh:
                fmt.Println(msg)
        }
    }
}
```

## Use cases
Concurrency, Parallelism, Asynchronous operations, Pipelines