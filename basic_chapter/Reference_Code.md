
  
```cpp
//将命令行参数转换为 std::vector<std::string> 类型的容器并返回
vector<string> arguments(int argc,char* argv[]) {
    vector<string> res;
    for(int i = 0; i != argc; i++)
        res.push_back(argv[i]);
    return res;
}
```

```cpp
//循环拷贝以0结尾的C风格字符串
void cpy(char* p, const char* q)
{
    while(*p++ = *q++);
}
```