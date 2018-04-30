distsemaphore
=========
[![License](https://img.shields.io/github/license/mashape/apistatus.svg?maxAge=2592000)](LICENSE)

Fast distributed & resizable golang semaphore based on CAS.

* allows weighted acquire/release;
* supports cancellation via context;
* allows change semaphore limit after creation;
* faster than channel based semaphores.

Based off of [github.com/marusama/semaphore](https://github.com/marusama/semaphore)

### Usage
Initiate
```go
import "github.com/consyse/distsemaphore"
...
sem := semaphore.New(5) // new semaphore with limit = 5
```
Acquire
```go
sem.Acquire(ctx, n)     // acquire n with context
sem.TryAcquire(n)       // try acquire n without blocking 
...
ctx := context.WithTimeout(context.Background(), time.Second)
sem.Acquire(ctx, n)     // acquire n with timeout
``` 
Release
```go
sem.Release(n)          // release n
```
Change semaphore limit
```go
sem.SetLimit(new_limit) // set new semaphore limit
```
