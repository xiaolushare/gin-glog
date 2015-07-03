# gin-glog
[Gin](https://github.com/gin-gonic/gin) middleware for Logging with
[glog](https://github.com/golang/glog). It is meant as drop in
replacement for the default logger used in gin.

## Usage
### Example

Start your webapp to log to STDERR and /tmp:

    % ./webapp -log_dir="/tmp" -logtostderr -v=2

```go
package main

import (
    "flag
    "time"

    "github.com/golang/glog"
    "github.com/zalando-techmonkeys/gin-glog"
    "github.com/gin-gonic/gin"
)

func main() {
    flag.Parse()
    router := gin.New()
    router.Use(ginglog.Logger(3 * time.Second))
    //..
    router.Use(gin.Recovery())
    glog.Info("bootstrapped application")
    router.Run(":8080")
}
```
