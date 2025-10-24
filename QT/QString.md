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