# clox

C 语言实现的 Lox 字节码虚拟机。

## 项目结构

```
├── CMakeLists.txt          # CMake 构建配置
├── main.c                  # 入口（测试用例）
├── common.h                # 公共头文件 & 调试开关
├── chunk.h / chunk.c       # 字节码块（opcode/行号/常量池）
├── value.h / value.c       # Value 类型 & 动态值数组
├── memory.h / memory.c     # 动态数组内存管理（reallocate）
├── debug.h / debug.c       # 字节码反汇编（含全部 opcode）
└── vm.h / vm.c             # 栈式虚拟机（push/pop/run/算术运算）
```
