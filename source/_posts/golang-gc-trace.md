---
title: golang调试、查看gc信息
date: 2022-12-13 20:32:53
tags:
  - golang

---

golang提供了丰富的工具用来查看服务运行时状态，这次就来看一下如何查看golang服务的gc运行时信息。

这里我们以下面这段代码为例子来观察gc的信息，该代码在map中存储了大量的对象，这些对象会对gc造成很大的压力，导致gc每次都需要对他们进行扫描。

```go
package main
import "time"
type Item struct {
	A string
	B string
	C string
	D string
	E string
	F string
	G G
}
type G struct {
	H int
	I int
	K int
	L int
	M int
	N int
}
func main() {
	m := make(map[int]*Item, 10*1024*1024)
	for i := 0; i < 1024*1024; i++ {
		m[i] = &Item{}
	}
	for i := 0; ; i++ {
		delete(m, i)
		m[1024*1024+i] = &Item{}
		time.Sleep(10 * time.Millisecond)
	}
}
```

启用gc信息输出：

```
GODEBUG=gctrace=1 go run main.go
```

程序启动后会将gc信息输出到控制台：

```sh
GC forced
gc 2 @120.093s 0%: 0.050+173+0.002 ms clock, 0.40+0/344/0+0.023 ms cpu, 453->453->450 MB, 612 MB goal, 0 MB stacks, 0 MB globals, 8 P
GC forced
gc 5 @121.834s 0%: 0.35+2.1+0.007 ms clock, 2.8+0/2.9/0+0.058 ms cpu, 2->2->0 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
GC forced
gc 3 @240.273s 0%: 0.064+215+0.003 ms clock, 0.51+0/420/0+0.025 ms cpu, 451->451->450 MB, 900 MB goal, 0 MB stacks, 0 MB globals, 8 P
GC forced
gc 6 @243.549s 0%: 0.27+1.0+0.004 ms clock, 2.2+0/1.9/0+0.036 ms cpu, 0->0->0 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
GC forced
gc 4 @360.503s 0%: 0.11+199+0.006 ms clock, 0.89+0/388/0+0.053 ms cpu, 451->451->450 MB, 900 MB goal, 0 MB stacks, 0 MB globals, 8 P
GC forced
gc 7 @363.559s 0%: 0.50+2.2+0.012 ms clock, 4.0+0/4.0/0+0.098 ms cpu, 0->0->0 MB, 4 MB goal, 0 MB stacks, 0 MB globals, 8 P
```

这些输出信息的含义如下：

```sh
1. gc 2 @120.093s：第65次执行，进程已经启动16.996秒
2. 0%：本次执行gc占用的进程cpu时间的百分比
3. 0.050+173+0.002 ms clock：本次gc的耗时。依次是STW清扫的时间, 并发标记和扫描的时间，STW标记的时间。（STW即stop-the-world，STW时间内进程完全被挂起），可以看到标记阶段的耗时非常高，达到了173ms。
4. 0.40+0/344/0+0.023 ms cpu：本次gc占用cpu时间
5. 453->453->450 MB：堆的大小，gc后堆的大小，存活堆的大小
6. 612 MB goal：堆的大小
7. 0 MB stacks：栈的大小
8. 0 MB globaks：全局变量的大小
9. 8 P：CPU核数
10. GC forced：由runtime.GC()强制执行
11. 系统内存回收信息：scvg0: inuse: 6, idle: 12, sys: 18, released: 0, consumed: 18 (MB)
- inuse：使用多少M内存
- idle：剩下要清除的内存
- sys：系统映射的内存
- released：释放的系统内存
- consumed：申请的系统内存
```
