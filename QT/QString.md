1、替换
```cpp
QString replaceExtension(const QString& filename) {
    QString result = filename;
    
    // 简单替换（区分大小写）
    if (result.endsWith(".jpg", Qt::CaseSensitive)) {
        result.replace(result.length() - 4, 4, ".tiff");
    }
    
    return result;
}

// 不区分大小写的版本
QString replaceExtensionCaseInsensitive(const QString& filename) {
    QString result = filename;
    
    if (result.endsWith(".jpg", Qt::CaseInsensitive)) {
        result = result.left(result.length() - 4) + ".tiff";
    }
    
    return result;
}

```

2、十六进制
```cpp
uint16_t u16 = 255;
int i = 4095;

// 基本转换
QString hexStr1 = QString::number(u16, 16);  // "abcd"
QString hexStr2 = QString::number(i, 16);    // "ff"

// 大写字母
QString hexStr3 = QString::number(u16, 16).toUpper();  // "ABCD"

// 指定宽度，不足补0
QString hexStr4 = QString::number(u16, 16).rightJustified(4, '0');  // "abcd"

// 直接格式化
QString hexStr1 = QString("%1").arg(u16, 4, 16, QChar('0'));  // "00ff"
QString hexStr2 = QString("%1").arg(i, 8, 16, QChar('0'));    // "00000fff"

// 大写
QString hexStr3 = QString("%1").arg(u16, 4, 16, QChar('0')).toUpper();  // "00FF

//  数组转16进制
QByteArray writeData((const char*)data, length);
QString writeHexStr = writeData.toHex(' ').toUpper();  // 用空格分隔，大写

```

3、lastIndexof

```cpp
QString str = "hello world, hello Qt";
int idx = str.lastIndexOf("hello");   // 从末尾向前找，返回 13（第二个"hello"的起始位置）
int idx2 = str.lastIndexOf("hello", 10); // 从索引10向前找，返回 0（第一个"hello"的起始位置）
int idx3 = str.lastIndexOf("Hi");     // 返回 -1
```

4、mid
```cpp
QString str = "Hello Qt";
QString sub1 = str.mid(6);      // 从索引6开始取到末尾 → "Qt"
QString sub2 = str.mid(6, 2);   // 从索引6开始取2个字符 → "Qt"
QString sub3 = str.mid(0, 5);   // 从索引0开始取5个字符 → "Hello"
QString sub4 = str.mid(10);     // 起始索引超出范围 → ""
```

5、left
```cpp
QString str = "Hello Qt";
QString left1 = str.left(5);    // 取前5个字符 → "Hello"
QString left2 = str.left(20);   // n 超过长度，返回整个字符串 → "Hello Qt"
QString left3 = str.left(0);    // 返回空字符串 ""
QString left4 = str.left(-1);   // n 为负数，返回空字符串 ""
```