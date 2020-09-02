你好！
很冒昧用这样的方式来和你沟通，如有打扰请忽略我的提交哈。我是光年实验室（gnlab.com）的HR，在招Golang开发工程师，我们是一个技术型团队，技术氛围非常好。全职和兼职都可以，不过最好是全职，工作地点杭州。
我们公司是做流量增长的，Golang负责开发SAAS平台的应用，我们做的很多应用是全新的，工作非常有挑战也很有意思，是国内很多大厂的顾问。
如果有兴趣的话加我微信：13515810775  ，也可以访问 https://gnlab.com/，联系客服转发给HR。
#golog

simple log library for Golang

##case 

```
package main

import (
	"fmt"
	. "github.com/flike/golog"
	"os"
)

func main() {
	path := "/tmp/test_log"
	os.RemoveAll(path)
	os.Mkdir(path, 0777)
	fileName := path + "/test.log"

	h, err := NewRotatingFileHandler(fileName, 1024*1024, 2)
	if err != nil {
		fmt.Println(err.Error())
	}
	//GlobalLogger is a global variable
	GlobalLogger = New(h, Lfile|Ltime|Llevel)
	GlobalLogger.SetLevel(LevelTrace)
	args1 := "go"
	args2 := "log"
	args3 := "golog"
	//the log will record into the file(/tmp/test_log/test.log)
	Debug("Mode", "main", "OK", 0, "args1", args1, "args2", args2, "args3", args3)
	GlobalLogger.Close()
}

```
