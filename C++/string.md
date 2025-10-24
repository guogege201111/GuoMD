1、替换某个片段

```cpp
std::string replaceExtension(const std::string& filename) {
    std::string result = filename;
    size_t pos = result.rfind(".jpg");
    
    // 如果找到 .jpg 并且它在字符串的末尾（是扩展名）
    if (pos != std::string::npos && pos == result.length() - 4) {
        result.replace(pos, 4, ".tiff");
    }
    
    return result;
}

```