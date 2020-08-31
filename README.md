我是光年实验室高级招聘经理。
我在github上访问了你的开源项目，你的代码超赞。你最近有没有在看工作机会，我们在招软件开发工程师，拉钩和BOSS等招聘网站也发布了相关岗位，有公司和职位的详细信息。
我们公司在杭州，业务主要做流量增长，是很多大型互联网公司的流量顾问。公司弹性工作制，福利齐全，发展潜力大，良好的办公环境和学习氛围。
公司官网是http://www.gnlab.com,公司地址是杭州市西湖区古墩路紫金广场B座，若你感兴趣，欢迎与我联系，
电话是0571-88839161，手机号：18668131388，微信号：echo 'bGhsaGxoMTEyNAo='|base64 -D ,静待佳音。如有打扰，还请见谅，祝生活愉快工作顺利。

# ConcurrentSkipList
[![Build Status](https://travis-ci.org/AceDarkknight/ConcurrentSkipList.svg?branch=master)](https://travis-ci.org/AceDarkknight/ConcurrentSkipList)
[![Maintainability](https://api.codeclimate.com/v1/badges/1955c229bfe0ba0a5134/maintainability)](https://codeclimate.com/github/AceDarkknight/ConcurrentSkipList/maintainability)
![license](https://img.shields.io/github/license/mashape/apistatus.svg)
[![Coverage Status](https://coveralls.io/repos/github/AceDarkknight/ConcurrentSkipList/badge.svg?branch=master)](https://coveralls.io/github/AceDarkknight/ConcurrentSkipList?branch=master)
[![Go Report Card](https://goreportcard.com/badge/github.com/AceDarkknight/ConcurrentSkipList)](https://goreportcard.com/report/github.com/AceDarkknight/ConcurrentSkipList)

A light, high-performance, concurrent, thread-safe skip list implementation written in Golang.

## Getting Start
- **Import package**

```bash
go get github.com/AceDarkknight/ConcurrentSkipList
```
```go
import "github.com/AceDarkknight/ConcurrentSkipList"
```

- **Usage**
```go
// Create a new skip list. The parameter is the level of the skip list.
// Parameter must > 0 and <=32, if not, err is not nil.
skipList, err := ConcurrentSkipList.NewConcurrentSkipList(12)
if err != nil {
    fmt.Println(err)
}

// Insert index and value. The index must uint64 and value is interface.
skipList.Insert(uint64(1), 1)
skipList.Insert(uint64(2), 2)

// Search in skip list.
if node, ok := skipList.Search(uint64(1)); ok {
	fmt.Printf("index:%v value:%v\n", node.Index(), node.Value())
}

// Delete by index.
skipList.Delete(uint64(2))

// Get the level of skip list.
_ = skipList.Level()

// Get the length of skip list.
_ = skipList.Length()

// Iterate each node in skip list.
skipList.ForEach(func(node *ConcurrentSkipList.Node) bool {
	fmt.Printf("index:%v value:%v\n", node.Index(), node.Value())
	return true
})

// Select top 10 nodes of skip list.
nodes := skipList.Sub(0, 10)
```

## TODO
- [ ] Reduce memory.
- [ ] Add reverse operation.

## References
https://en.wikipedia.org/wiki/Skip_list
