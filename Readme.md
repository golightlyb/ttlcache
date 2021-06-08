## TTLCache - an in-memory LRU cache with expiration

TTLCache is a minimal wrapper over a string map in golang, entries of which are

1. Thread-safe
2. Auto-Expiring after a certain time
3. Optionally auto-Extending expiration on `Get`s

#### Forked version changes

* Auto-extending expiration is now controlled by a Get parameter
* Items may contain any value, not only strings

#### Usage
```go
import (
  "time"
  "github.com/golightlyb/ttlcache"
)

func main () {
  cache := ttlcache.NewCache(time.Second)
  cache.Set("key", "any value (interface{})")
  updateTTL := false
  value, exists := cache.Get("key", updateTTL)
  count := cache.Count()
}
```
