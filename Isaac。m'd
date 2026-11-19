# 以撒 Repentance+ 控制台笔记

窗口标题：`Binding of Isaac: Repentance+ v1.9.7.17`（这台机 hwnd 5180190）
屏幕 2560×1600；GetWindowRect 会返回整屏，裁剪自己按比例算。

## 控制台
- 开关键：反引号 `` ` ``（VK 0xC0），不是 ~
- 输入完回车会执行并自动关窗

## 删/给道具
- `remove` 必须带参数，光敲 `remove` 只回显
- **`remove c<ID>` 最稳**；`remove <名字>` 会匹配不上，别用
- `remove *` 会清空所有被动，绝对不能敲
- 给道具：`giveitem c<ID>`，会直接掉在他脚下，靠近就自动吃
- 主动道具格只有一格：给新的会**顶掉旧的**，比 remove 省事

## 查到自己有的东西
- `listcollectibles` → 输出 `名字:数量` 列表

## 已确认 ID
- Anarchist Cookbook（无政府主义食谱）= 65
- D6 = 105

## 刷东西 / 刷钱
- 语法：`spawn <ID>`，ID 带点，比如 `spawn 5.20.1`（Penny 1 分）
- **`5.20.1` = 硬币（Penny）**，已验证
- 刷出来的会落在脚下，走近自动捡

## 控制台输入：必须走剪贴板
逐个按键注入在这游戏里不可靠，三种坑全踩过：
- 打太快 → 吞字母（`spawn` 整个消失）
- 打太慢 → 字母重复（`spspaawn`）
- 中文输入法在中文态 → 吃键

**稳定做法**（照抄）：
1. PowerShell `Set-Clipboard -Value 'spawn 5.20.1'`
2. 置前窗口 + `sleep(0.9)`，反引号开控制台
3. Ctrl+V（VK 0x11 + 0x56）粘贴 → **截图核对输入行**
4. 核对无误再回车（0x0D）

## keybd_event 映射
字母 `ord(c.upper())`、回车 0x0D、反引号 0xC0、Shift 0x10、退格 0x08、空格 0x20、点 0xBE、Ctrl 0x11、V 0x56

## 实战记录
- 想删左上格的 Anarchist Cookbook：`remove` 裸敲无效 → `remove Anarchist Cookbook` 无效 → `remove c65` 也没顶掉
- 最后用 `giveitem c105` 刷 D6，他捡起来直接把食谱换下来了，格子里变成 D6 ✔
- 刷金币：连挂 6 次（`spawn` 被吞、行首多出 `1`、字母重复……），最后剪贴板粘贴一发成功，地上掉出好几枚 5¢ ✔
