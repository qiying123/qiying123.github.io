---
layout: post
title: "可能是最全面的github pages搭建个人博客教程"
date:   2019-11-22
tags: [geek]
comments: true
author: lemonchann
---

from pwn import

context(os="linux",arch="x86/amd64",log_level="debug")

--系统为linux，文件调试环境为32位/x86，64位/amd64，之后debug是调试等级，这个可以在运行时实时显示你的发送的接受的内容，方便调试。

nc ip地址 端口
p = remote("xxxx.xxx.xx.xxx",xxxx)  --远程

p = process("文件路径（./xxx)")  --本地

p.interactive()  --用于写在脚本最后，在代码执行完后与端口进入交互模式。

p.send(参数)

p.sendline(参数)   --发送参数末尾自动添加换行符/n

p.sendlineafter("参数1",参数2)    --在接受到参数1，在其后面输入参数2

recv(numb=字节大小, timeout=default) : 接收指定字节数。
recvall() : 一直接收直到达到文件EOF。
recvline(keepends=True) : 接收一行，keepends为是否保留行尾的\n。
recvuntil(delims, drop=False) : 一直读到delims的pattern出现为止。
recvrepeat(timeout=default) : 持续接收直到EOF或timeout。**

elf = ELF("文件路径（./xxx)")   --载入一个elf文件。

elf_plt_addr = elf.plt["函数名"]   --得到文件elf对象的“函数名”的plt表地址

elf_got_addr = elf.got["函数名"]   --得到文件elf对象的“函数名”的got表地址

elf_got_addr = elf.symbols["函数名"]  --直接找到该函数的地址

next(elf.search("/bin/sh"))  --寻找/bin/sh字符串的地址

打包：

p64()
p32()

用于将一个16进制的地址数转化为相应字节数的字符串(64位是8字节，32位是4字节)

解包：
u64()
u32()

用于将一个相应字节数的字符串(64位是8字节，32位是4字节)转化为16进制的地址数

shellcode = asm(shellcraft.sh())

shellcraft.sh()生成/bin/sh的shellcode，通过asm()函数汇编后即可插入程序中执行

gdb.attach(io)
pause()
