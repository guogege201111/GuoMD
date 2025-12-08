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
