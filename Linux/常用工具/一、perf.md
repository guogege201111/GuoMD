1、安装
```
sudo apt install linux-tools-common linux-tools-generic
```

2、使用流程
```


1 快速评估程序整体表现


sudo perf stat -e task-clock,cycles,instructions,cache-misses,context-switches ./my_program

2 定位 CPU 热点函数（最常用）


# 采样（带调用栈）
sudo perf record -g ./my_program
# 分析报告（交互式界面，按 Enter 展开调用链）
sudo perf report -g

3 实时监控系统或进程

# 监控整个系统
sudo perf top
# 监控指定进程（PID 可通过 ps aux 获取）
sudo perf top -p <PID>
sudo perf record -g -p <PID> -- sleep 30

### 4.4 生成火焰图（可视化热点）

bash

sudo perf record -F 99 -g -- ./my_program
sudo perf script > out.perf
git clone https://github.com/brendangregg/FlameGraph.git
./FlameGraph/stackcollapse-perf.pl out.perf > out.folded
./FlameGraph/flamegraph.pl out.folded > flamegraph.svg
# 用浏览器打开 flamegraph.svg
```