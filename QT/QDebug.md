
1、打印十六进制
```cpp
uint16_t u16 = 0xABCD;
int i = 255;

// 使用 qDebug() 直接输出
qDebug() << "uint16 十六进制:" << QString::number(u16, 16);
qDebug() << "int 十六进制:" << QString("%1").arg(i, 4, 16, QChar('0'));

```