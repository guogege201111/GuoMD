1、变量与引用
```
msg="usb timeout on eth0"

echo $msg
echo "$msg"
echo '$msg'


- echo $msg：Shell 先把 $msg 展开成 usb timeout on eth0，再按空格拆成多个参数。
- echo "$msg"：变量会展开，但整体保持成一个参数。
- echo '$msg'：单引号里不展开，原样输出 $msg。
  
  
  读取变量：
  
  $dev 和 ${dev} 大多数时候都行，但当变量名后面紧跟别的字符时，最好用花括号：

name="eth0" 
echo "${name}_log"
如果你写成：

echo "$name_log"

Shell 会以为你要取的是变量 name_log，不是 name 再拼接 _log

```