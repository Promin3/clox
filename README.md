# clox

## 构建与运行

CLion 打开项目后直接 `Run` 即可（默认构建目录为 `cmake-build-debug`）。

```bash
# REPL 模式
./cmake-build-debug/clox
```

```bash
# 执行脚本文件
./cmake-build-debug/clox test.lox
```

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

## garmmer
```
program        → declaration* EOF ;

declaration    → classDecl
                | funDecl
                | varDecl
                | statement ;

classDecl       → "class"  IDENTIFIER ( "<"  IDENTIFIER )?
                "{"  function * "}" ;

funDecl        → "fun" function ;

function       → IDENTIFIER "(" parameters? ")" block ;

parameters     → IDENTIFIER ( "," IDENTIFIER )* ;

varDecl        → "var" IDENTIFIER ( "=" expression )? ";" ;

statement      → exprStmt
                | forStmt
                | ifStmt
                | printStmt
                | returnStmt
                | whileStmt
                | block ;

returnStmt     → "return" expression? ";" ;

forStmt        → "for" "(" ( varDecl | exprStmt | ";" )
                expression? ";"
                expression? ")" statement ;

whileStmt      → "while" "(" expression ")" statement ;

ifStmt         → "if" "(" expression ")" statement
                 ( "else" statement )? ;

block          → "{" declaration* "}" ;

exprStmt       → expression ";" ;

printStmt      → "print" expression ";" ;

expression     → assignment ;

assignment     → ( call "." )? IDENTIFIER "=" assignment
                | logic_or ;

logic_or       → logic_and ( "or" logic_and )* ;

logic_and      → equality ( "and" equality )* ;

equality       → comparison ( ( "!=" | "==" ) comparison )* ;

comparison     → term ( ( ">" | ">=" | "<" | "<=" ) term )* ;

term           → factor ( ( "-" | "+" ) factor )* ;

factor         → unary ( ( "/" | "*" ) unary )* ;

unary          → ( "!" | "-" ) unary | call ;

call           → primary ( "(" arguments? ")" | "." IDENTIFIER )* ;

arguments      → expression ( "," expression )* ;

primary        → "true" | "false" | "nil" | "this"
                | NUMBER | STRING | IDENTIFIER | "(" expression ")"
                | "super" "." IDENTIFIER ;
```