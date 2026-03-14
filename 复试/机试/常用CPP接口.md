`transform` ：对数组每个元素进行操作后插入新数组, 参数如下:
- src.begin(): 原数组起始位置
- src.end()
- dst.begin(): 新数组起始位置
- func: 转换函数，例如 [](int x){return to_string(x);}
