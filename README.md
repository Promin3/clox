# clox

C 语言实现的 Lox 字节码虚拟机。

## 项目结构

```
├── CMakeLists.txt          # CMake 构建配置
├── main.c                  # 入口
├── common.h                # 公共头文件
├── chunk.h / chunk.c       # 字节码块（chunk）数据结构
├── value.h / value.c       # 值类型与动态值数组
├── memory.h / memory.c     # 内存管理宏与函数
├── debug.h / debug.c       # 字节码反汇编调试器
└── vm.h / vm.c             # 栈式虚拟机（执行引擎）
```
