- [B 站视频演示](https://www.bilibili.com/video/BV15L411w7kU?share_source=copy_web "反转了, 我不是嘉心糖, 我是雏草姬"): 和视频中有出入的地方是文件名; 这个视频只是单纯的 demo, 并没有提到使用方式, 不看也罢.
- [代码结构分析](https://blog.csdn.net/qq_66550041/article/details/122606740): 原文发表于 CSDN, 防止它哪天倒闭, 现将其复制 (并稍加修改) 到本仓库的 [`COMMENTARY.txt`](COMMENTARY.txt) 文件.  同样地, 原文与本仓库中的文件名有出入.

___

# 食用方式

## 目录树 (只包含会用到的文件):

```
./
 |__MAIN.ASM
 |
 |__img/
 |     |  # 注意, 你得先解压 zip 文件
 |     |__zh-hans_windows_xp_home_with_service_pack_3_x86_cd_x14-92408.iso
 |     |
 |     |__main.img
 |
 |__bin/
       |__MASM.EXE
       |
       |__LINK.EXE
```

## 准备工作

首先安装 Windows XP.  考虑到有些朋友不知道如何安装, 鼠鼠这里先解释一下:

    安装 OS 时, 需要将光盘文件插入到虚拟机对应的光驱上,
    虚拟光盘文件就是 `zh-hans_windows_xp_home_with_service_pack_3_x86_cd_x14-92408.iso`;
    然后启动 PC, 它会直接运行安装程序, 将 OS 拷贝到硬盘上.

鼠鼠的大致配置如下 (创建虚拟机, 以及安装系统时的相关设定):

1. CPU x 2
2. 192MB 内存 + 32MB 显存
3. 4GB 硬盘
4. EFI-disabled
5. 不分区, 直接安装 (也就是单纯一个 `C:` 盘)
6. 使用 NTFS 文件系统
7. 激活码: `3FKBQ-32TH7-D3TJB-YBWTQ-D26VQ`

接下来成功进入到 Windows XP 的桌面, 这表明安装过程很顺利.  <br />
现在, 应当把插入到光驱中的虚拟光盘文件移除, 否则下次启动 PC 时又会重装系统.

在桌面上 (或者其它地方, 随便你) 新建一个文件夹 (鼠鼠给文件夹取的名字是 `task`), <br />
然后, 需要将三个文件从你的电脑上移动到虚拟机内部 (主流的模拟器应当提供了这个功能), 分别是:

- `MAIN.ASM`
- `MASM.EXE`
- `LINK.EXE`

总之, 现在你的那个新建文件夹内, 应当只包含上述三个文件.

将虚拟软盘文件 (`main.img`) 插入到虚拟机的软驱中 (你可能需要先关机, 添加一个软驱, 再启动).  <br />
现在, 点开你的虚拟机的“我的电脑”, 会多出一个 `A:` 盘符, 这就是刚刚插进去的软盘.  <br />

你可以选择将 `A:` 格式化, 或者放着不管:

1. 放着不管 (那么刚刚新建的文件夹也可以删了).
    实际上, 这个软盘已经是鼠鼠提前制作好的成品, 你可以选择直接重启虚拟机 (但是要记住, 在模拟器中将软驱设置为启动顺序的第一个);
    然后直接跳到本文的末尾, 去看如何使用这个程序.

2. 选择把它格式化.
    这样, 在完成接下来的步骤之前, 你不应该关闭虚拟机, 否则将无法再次启动 (因为启动顺序的默认的第一项很可能就是软驱, 而软驱中的软盘里什么都没有).

格式化完软盘之后, 就要来制作我们自己的软盘了 (也就是在软盘中写入合适的数据).  <br />
我们将使用 `MAIN.EXE` 这个程序来制作软盘, 鼠鼠已经编写了它的源代码, 也就是新建文件夹中的 `MAIN.ASM` 那个文件.

打开命令行, 进行一番操作:

```bash
# 鼠鼠的新建文件夹是 C:\Documents and Settings\shynur\桌面\task
# 所以, 鼠鼠先进入这个目录

# 输入下面这一行, 但不要回车
cd C:\Documents and Settings\shynur

# 然后按 TAB 键, 直到出现:
cd C:\Documents and Settings\shynur\桌面

# 回车, 再输入下面这行, 再回车
cd task
```

你可以执行 `dir` 命令查看一下当前目录下是不是有之前提到的那三个文件.  <br />
继续:

```bash
# 编译源文件, 输出 object 文件:
# 执行下面这条指令, 然后一路回车
MASM.EXE MAIN.ASM

# 现在目录下应该多出了一个 MAIN.OBJ 文件

# 链接 object 文件, 输出可执行文件
# 同上
LINK.EXE MAIN.OBJ

# 现在目录下应该多出了一个 MAIN.EXE 文件
```

直接用鼠标双击 `MAIN.EXE`, 这时会弹出一个窗口, 然后等它消失就可以了.  <br />
鼠鼠有洁癖, 所以完事之后直接将新建文件夹给删除了.

关闭虚拟机, 在模拟器中将软驱设置为启动顺序的第一个, 再启动虚拟机.  <br />
如果你能看到五行绿字, 那就说明 XP 手术很成功.

## the Program

键入 `1`, `2`, ..., `5`, 以选择不同的子功能.  <br />
键入 `ESC` 退出子功能, 回到主界面.

1. 重启

2. 加载 Windows XP

3. 显示时间.
    按 `F1` 改变时间的字体颜色

4. 设置时间.
    编辑方式就是你想的那样, 输入数字, 删除数字, 回车确认; 你可以只设置年份, 或者只设置年份和月份, etc.
    但是请设置正常一点的日期, 如果设置成了“13月”这种玩意, 可能导致待会儿你选择功能 2 的时候无法进入 Windows XP, 甚至之后要重启两三次.

5. 5

# LICENSE

[MIT License](./LICENSE), 仅针对我编写的 [`COMMENTARY.txt`](./COMMENTARY.txt), [`MAIN.ASM`](./MAIN.ASM), 和 [`README.md`](./README.md).
