
  
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
Bjarne Stroustrup认为，原则是尽可能利用标准库功能，
而非用指针和字节自行实现。优先标准库函数是内联的，
有些甚至是用特定的机器指令实现的。因此，在决定选用手动编写的代码之前，
最好确认它的性能优于标准库函数。即便如此，
这种暂时的优越性也可能随着硬件和编译器的改变而不复存在。
另外对于程序的维护者来说，使用手工编写的代码而非标准库函数会让他们头疼不已
*/
//循环拷贝以0结尾的C风格字符串
void cpy(char* p, const char* q)
{
    while(*p++ = *q++);
}

```


```cpp
/*忽略下列代码的拼写和简写，这是某公司项目代码上的bug*/
/*
该代码存在一下问题：
1. 如果 rout_ 是 getRount() 函数中的局部变量，这里直接返回它的引用会导致未定义行为，因为局部变量在函数返回后会被销毁，后续对它的引用将指向无效内存。  
2.如果 rout_ 是一个成员变量（而不是局部变量），则 getRount() 会返回一个新的 std::vector<int> 对象。这里的 auto& rout = getRount(); 将绑定到一个临时对象的引用，这是不合法的，因为 rout 引用的是一个在语句结束后被销毁的临时对象。
*/
std::vector<int> getRount() {
    return rout_;
}

auto& rout = getRount(); 
for (int i = 0; i < rout.size(); i++) {
     out[i]
}



/*fix code*/
//
const std::vector<int>& getRount() const {
    return rout_;
}
// 通过 const auto& rout = getRount();我们确保 rout 引用的是一个有效的、持久存在的对象 rout_，而不是一个临时对象。这种方式既节省了内存和时间，又避免了悬空引用问题。
const auto& rout = getRount();
for (int i = 0; i < rout.size(); i++) {
    out[i];
}

```