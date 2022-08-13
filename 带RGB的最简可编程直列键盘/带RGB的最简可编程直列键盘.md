# **带RGB的最简可编程直列键盘**

> https://oshwhub.com/explore?filter=3f6426c635ff442291209a3384a84102

## 简介：

1、分两块PCB，单独使用是20键小键盘，拼在一起是全功能电脑键盘。 2、开源QMK程序，全键可编程。 3、全部采用1U按键，键帽配备简单便宜，无卫星轴，可不用定位板。 4、配置了RGB等显示层状态。

## 描述：

<img src="\带RGB的最简可编程直列键盘\p1.png">

<img src="\带RGB的最简可编程直列键盘\p2.png">

主板上焊接圆插母，焊孔加大，圆插母贴到主板，PRO MICRO模块元件面朝向主板，模块不采用插针，而直接焊元件脚当插针，将高度降到最低。

<img src="\带RGB的最简可编程直列键盘\p3.png">

模块是micro插座，用导线将模块连接到主板的type c插座；reset采用微动开关，对着底板的位置开一小孔，方便烧录固件。

<img src="\带RGB的最简可编程直列键盘\p4.png">

最下方一行装了RGB灯，不同的颜色对应不同的层。

<img src="\带RGB的最简可编程直列键盘\p5.png">

铜定、铜底

<img src="\带RGB的最简可编程直列键盘\p6.png">

0层：字母+功能键，Fn1进入标点符号层，Fn2进入数字层，Fn3为F功能区、虚拟鼠标、方向键，Fn4为软件快捷键和媒体键。

按Fn1加空格切换中文，输入中文时，拇指按空格选第一个字，Shift选第二个字，输入大写字母左手拇指按Shift，所有操作均无需离开主区域。

<img src="\带RGB的最简可编程直列键盘\p7.png">

1层：所有标点符号按个人习惯和易于记忆布置，如？就是Fa发问的F位置，#就在井号的J位置…… +-×/=和2层的数字键盘一致。

<img src="\带RGB的最简可编程直列键盘\p8.png">

2层 ：右边是完整的数字小键盘，双击Fn2还可以锁定2层，方便大量输入数字时使用。左边是方向键，方便文字编辑时使用，使用时双手手无需做移动。

<img src="\带RGB的最简可编程直列键盘\p9.png">

3层：右手拇指摁在Fn3上，就像用鼠标的手势一样，方便舒服。

直列键盘与常规键盘相比，最大的优势就是方向键、数字小键盘等布局很整齐好用。用来玩游戏，也可以设置专门的一层。

键盘虽小，功能齐全，小白也可享受DIY的乐趣。

键位设置是整个键盘的灵魂，按需设置好，使用将很方便，它很快就成为我唯一的主力键盘。

 

以上为V1.0版的键位设置，经过不停的使用，进入了2.0版的更新，更高效更好用了，不断更新的版本详见附件。

## **小配列键盘如何做到好用？**

精心设计的小配列设置，所有按键均在十指舒服操作范围，小指无需向外按键；

最频繁使用的回车键、退格键就在右手小指下，无需移动即可操作；

切换1、2层的按键及shift、空格键就在两拇指下方，拇指的作用不再只用来按空格，十指利用率有效提高；
左手拇指按Fn1键，左手下面是完整的数字小键盘与运算符号，非常适合左手数字，右手鼠标的操作；【更新】
右手拇指按Fn2键，右手下面是上下左右与Home、End等方向键，手势与拿鼠标相似，自然舒服，在码字时尤其方便移动光标位；【更新】
所有标点符号只需拇指按Fn1键或Fn2键，另一只手的手指按相应按键即可，所有键位均在手指舒适区；
左手拇指按Fn3键，单手按F键简单易用，右手Fn3键，虚拟鼠标……【更新】

 参考资料，感谢各位大牛的贡献！
https://docs.qmk.fm/#/zh-cn/

http://www.keyboard-layout-editor.com/

https://kbfirmware.com/

http://builder.swillkb.com/

https://www.bilibili.com/read/cv10071032/

https://www.zfrontier.com/app/flow/2dq9AoE37KpE

https://post.smzdm.com/p/aekz8pdm/

https://www.zfrontier.com/app/flow/2wqGYOQPMpOQ

https://www.bilibili.com/read/cv5275203/

 

欢迎大家指正或建议。

## **设计图**

### **原理图**

<img src="\带RGB的最简可编程直列键盘\Schematic_RGB键盘_2022-08-13.png">

**PCB（1/3）**

<img src="\带RGB的最简可编程直列键盘\PCB_PCB-ProMicro-IQP40_2022-08-13.png">

<img src="\带RGB的最简可编程直列键盘\PCB_IQP40-BOX002_2022-08-13.png">

<img src="\带RGB的最简可编程直列键盘\PCB_IQP40-BOX001_2022-08-14.png">

## **BOM**

| ID   | Name                                                         | Designator                                                   | Footprint                                                    | Quantity |
| ---- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | -------- |
| 1    | [0.1u](https://lceda.cn/component/24eeb2ceca08480b92b847b6a310acda) | C6,C7,C8,C9                                                  | [C0603](https://lceda.cn/component/f8151fdc728a41ebbc304e11d39e5437) | 4        |
| 2    | [1n4148](https://lceda.cn/component/218e666ab2584477ad4d7dc4daa387b2) | D1,D2,D3,D4,D5,D6,D7,D8,D9,D10,D11,D12,D13,D14,D15,D16,D17,D18,D19,D20 | [LL-34_L3.5-W1.5-RD01](https://lceda.cn/component/c5e105eee5954e659331c857d20e552e) | 20       |
| 3    | [Pro Micro](https://lceda.cn/component/1ca61422cff7477a9984505524577227) | IC1                                                          | [PRO-MICRO](https://lceda.cn/component/b1a204418c6549c1bac9a784252335bb) | 1        |
| 4    | [Key-4P](https://lceda.cn/component/21507fe462954ebb909a348552869f94) | KEY1                                                         | [KEY-TH_4P-L6.0-W6.0-P4.50](https://lceda.cn/component/9096c4e6bc254754b0b895e85df2faca) | 1        |
| 5    | [LED 3.0mm](https://lceda.cn/component/506254561eca4270a007513acd0c2231) | LED1                                                         | [L-T-A](https://lceda.cn/component/02b501f3f3c943148e9656c88d4969a8) | 1        |
| 6    | [1K](https://lceda.cn/component/5d56951fd43d4b5083b0f3cd9bfd5587) | R1                                                           | [R0805](https://lceda.cn/component/b60f399a7a7e41848b2be1eb49c79141) | 1        |
| 7    | [5.1K](https://lceda.cn/component/51396451669a42ceb1d244eb840eec0d) | R2,R6                                                        | [R0805](https://lceda.cn/component/769626f169ec49d9867bc27eb696b6b9) | 2        |
| 8    | [KB01](https://lceda.cn/component/7f7602236a5740a9a981816affcdb7c4) | SW1,SW2,SW3,SW4,SW5,SW6,SW7,SW8,SW9,SW10,SW11,SW12,SW13,SW14,SW15,SW16,SW17,SW18,SW19,SW20 | [KB01B](https://lceda.cn/component/774963096921420a829d2a9d49768ac9) | 20       |
| 9    | [WS2812_N](https://lceda.cn/component/4c98fa304fe44967af736f2906054de3) | U1,U2,U3,U4,U5                                               | [WS2812_1206_FT_N_1](https://lceda.cn/component/8851215fa4194e32aa81508322259b94) | 5        |
| 10   | [TYPE-C16PIN](https://lceda.cn/component/8db579ef59084e01bcdf9ec2f05cfe5d) | USB1                                                         | [USB-C-SMD_TYPE-C16PIN](https://lceda.cn/component/6d4ccf98d88248ecab1247f9e0c9ea9d) | 1        |

