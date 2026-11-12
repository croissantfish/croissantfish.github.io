---
title: 'FCC ASM Lab 汇编调试器'
date: 2026-11-12
summary: '面向编译原理课程的浏览器汇编调试器，支持 SPIM/MIPS32 与 RISC-V/RV32IM。'
tags:
  - 编译原理
  - 汇编
  - MIPS
  - RISC-V
  - Vue
links:
  - icon: hero/rocket-launch
    name: 打开应用
    url: /projects/fcc-web-simulator/
  - icon: brands/github
    name: GitHub 仓库
    url: https://github.com/croissantfish/fcc-web-simulator
---

FCC ASM Lab 是面向编译原理课程的浏览器汇编调试器，支持在浏览器本地执行 SPIM/MIPS32 与 RISC-V/RV32IM 汇编，无需后端服务，也无需单独安装模拟器。

## 功能特点

- 支持源码编辑、断点、单步、函数步过及执行控制。
- 支持寄存器查看与编辑，并提供十六进制、有符号数、无符号数和二进制显示。
- 提供堆栈、堆和数据段视图，支持 SP/FP 栈帧标记与小端内存显示。
- 支持交互式标准输入输出，内置 FCC 编译器生成的双架构示例。
- 使用浏览器本地存储保存当前程序。
