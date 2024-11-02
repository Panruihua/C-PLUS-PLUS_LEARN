
  
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
/*
Bjarne Stroustrup认为，原则是尽可能利用标准库功能，而非用指针和字节自行实现。优先标准库函数是内联的，有些甚至是用特定的机器指令实现的。因此，在决定选用手动编写的代码之前，最好确认它的性能优于标准库函数。即便如此，这种暂时的优越性也可能随着硬件和编译器的改变而不复存在。另外对于程序的维护者来说，使用手工编写的代码而非标准库函数会让他们头疼不已
*/
//循环拷贝以0结尾的C风格字符串
void cpy(char* p, const char* q)
{
    while(*p++ = *q++);
}

```