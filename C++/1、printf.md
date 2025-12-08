```cpp
    #include <stdio.h>
    #include <inttypes.h>
    // 不同整数类型的十六进制打印
    uint8_t u8 = 0xAB;
    uint16_t u16 = 0xABCD;
    uint32_t u32 = 0xABCD1234;
    uint64_t u64 = 0xABCD12345678ULL;
    
    printf("uint8_t: 0x%02" PRIx8 "\n", u8);   // 0xab
    printf("uint16_t: 0x%04" PRIx16 "\n", u16); // 0xabcd
    printf("uint32_t: 0x%08" PRIx32 "\n", u32); // 0xabcd1234
    printf("uint64_t: 0x%016" PRIx64 "\n", u64); // 0x0000abcd12345678
```