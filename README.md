# clox

## 项目结构

```
├── CMakeLists.txt              # CMake 构建配置（C11）
├── main.c                      # 入口 & 测试用例
├── common.h                    # 公共头文件 & 调试开关
├── chunk.h / chunk.c           # 字节码块（opcode / 行号 / 常量池）
├── value.h / value.c           # Value 类型 & 动态值数组
├── memory.h / memory.c         # 动态数组内存管理（reallocate）
├── debug.h / debug.c           # 字节码反汇编（含全部 opcode）
├── vm.h / vm.c                 # 栈式虚拟机（push / pop / run / 算术运算）
├── scanner.h / scanner.c       # 词法分析器（词素识别、保留字匹配）
├── compiler.h / compiler.c     # 编译器（衔接扫描器，输出 Token 流）
└── README.md
```
