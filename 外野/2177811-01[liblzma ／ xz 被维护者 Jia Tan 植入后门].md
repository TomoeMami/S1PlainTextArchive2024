
*****

####  蛋饼  
##### 1#       楼主       发表于 2024-3-30 14:02

 本帖最后由 蛋饼 于 2024-3-30 14:07 编辑 

1. 攻击者 JiaT75 (Jia Tan) 于 2021 年注册了 GitHub 账号，之后积极参与 xz 项目的维护，并逐渐获取信任，获得了直接 commit 代码的权利。

2. JiaT75 在最近几个月的一次 commit 中，悄悄加入了 bad-3-corrupt_lzma2.xz 和 good-large_compressed.lzma 两个看起来人畜无害的测试用二进制数据，然而在编译脚本中，在特定条件下会从这两个文件中读取内容对编译结果进行修改，致使编译结果和公开的源代码不一致。

3. 目前初步的研究显示，注入的代码会使用 glibc 的 IFUNC 去 Hook OpenSSH 的 RSA_public_decrypt 函数，致使攻击者可以通过构造特定的验证数据绕过 RSA 签名验证。（具体细节还在分析中）

4. 只要是同时使用了 liblzma 和 OpenSSH 的程序就会受到影响，最直接的目标就是 sshd，使得攻击者可以构造特定请求，绕过密钥验证远程访问。

5. 受影响的 xz-utils 包已经被并入 Debian testing 中进行测试，攻击者同时也在尝试并入 fedora 和 ubuntu。 

6. 幸运的是，注入的代码似乎存在某种 Bug，导致特定情况下 sshd 的 CPU 占用飙升。被一位安全研究人员注意到了，顺藤摸瓜发现了这个阴谋并报告给 oss-security，致使此事败漏。

如果不是因为这个 Bug，那么这么后门有不低的概率被并入主流发行版的 stable 版本，恐怕会是一件前所未有的重大安全事件。

另外从一些细节能看出来攻击者非常用心：

1. 攻击者抢在 ubuntu beta freeze 的几天前才尝试让新版本并入，以期望减少在测试期间被发现的时间。

2. xz-utils 项目的原维护者 Lasse Collin (Larhzu)，有着定期进行 internet breaks 的习惯，而且最近正在进行，导致这些变动他并没有 review 的机会，即使到现在也没能联系上他本人。这可能也是攻击者选定 xz-utils 项目的原因之一。

更多的细节还在被分析中，目前 GitHub 已经关停了整个 xz 项目。

[https://mp.weixin.qq.com/s/bZHavV6IF_W4QALhcbpwtw](https://mp.weixin.qq.com/s/bZHavV6IF_W4QALhcbpwtw)

*****

####  革萌  
##### 2#       发表于 2024-3-30 14:05

卧槽 这个解压工具可以说是使用极为广泛

*****

####  蛋饼  
##### 3#         楼主| 发表于 2024-3-30 14:10

原帖参考来源：
[https://boehs.org/node/everything-i-know-about-the-xz-backdoor](https://boehs.org/node/everything-i-know-about-the-xz-backdoor)
[https://gist.github.com/thesames ... bc3dce9ee78baad9e27](https://gist.github.com/thesamesam/223949d5a074ebc3dce9ee78baad9e27)

*****

####  kyomu  
##### 4#       发表于 2024-3-30 14:10

怪不得 homebrew 把 xz 降回旧版本

*****

####  小拖  
##### 5#       发表于 2024-3-30 14:16

jia tan是个Chinese吗？

*****

####  geeky_kappa  
##### 6#       发表于 2024-3-30 14:19

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=64427911&amp;ptid=2177811" target="_blank">小拖 发表于 2024-3-30 14:16</a>
jia tan是个Chinese吗？</blockquote>
据称主要活动时间符合东八区

*****

####  芜湖挨宰  
##### 7#       发表于 2024-3-30 14:21

我用macos，运行微信里的检测脚本提示ldd: command no found，要安装后继续检测吗？

*****

####  apefrank  
##### 8#       发表于 2024-3-30 14:23

账号不是二刺螈头像，也许不是国人<img src="https://static.saraba1st.com/image/smiley/face2017/067.png" referrerpolicy="no-referrer">

*****

####  Hieda  
##### 9#       发表于 2024-3-30 14:24

<img src="https://static.saraba1st.com/image/smiley/face2017/119.png" referrerpolicy="no-referrer">arch和msys2都老早就包含中招版本了
好在openssh都没链

*****

####  jkl  
##### 10#       发表于 2024-3-30 14:34

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=64427911&amp;ptid=2177811" target="_blank">小拖 发表于 2024-3-30 14:16</a>
 jia tan是个Chinese吗？</blockquote>
中本聪是日本人吗

*****

####  ruistu  
##### 11#       发表于 2024-3-30 14:59

谭嘉？

*****

####  龙骑士尹志平  
##### 12#       发表于 2024-3-30 14:59

中本冲不是黄人熏吗

*****

####  处男鉴黄师  
##### 13#       发表于 2024-3-30 14:59

这是被发现的，没被发现的不知道有多少

*****

####  coyove  
##### 14#       发表于 2024-3-30 15:23

只能说oss全看贡献者的道德水准

*****

####  weiyang  
##### 15#       发表于 2024-3-30 15:25

6啊，以前就在想有没有类似的操作了

*****

####  Nanachi  
##### 16#       发表于 2024-3-30 15:25

开源软件的依赖链攻击越来越可能了

—— 来自 HUAWEI LNA-AL00, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.5.3-play

*****

####  mp5  
##### 17#       发表于 2024-3-30 15:30

这次是运气好，攻击代码有bug才被发现<img src="https://static.saraba1st.com/image/smiley/face2017/001.png" referrerpolicy="no-referrer">

有未被发现的上游基础包投毒是大概率事件<img src="https://static.saraba1st.com/image/smiley/face2017/125.png" referrerpolicy="no-referrer">

*****

####  mp5  
##### 18#       发表于 2024-3-30 15:33

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=64427911&amp;ptid=2177811" target="_blank">小拖 发表于 2024-3-30 14:16</a>

jia tan是个Chinese吗？</blockquote>
单从帐号名判断是哪国人非常扯

有人在攻击代码里发现 Jia Cheong Tan 这个名字，那现在是不是又可以认为攻击者是韩国人了？

*****

####  子虚乌有  
##### 19#       发表于 2024-3-30 15:35

这种人能抓住吗

*****

####  DTCPSS  
##### 20#       发表于 2024-3-30 15:37

国内宅宅开源贡献者不是人均日文名

—— 来自 [S1Fun](https://s1fun.koalcat.com)

*****

####  Nanachi  
##### 21#       发表于 2024-3-30 15:41

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=64428439&amp;ptid=2177811" target="_blank">子虚乌有 发表于 2024-3-30 15:35</a>
这种人能抓住吗</blockquote>
开源协议大多有免责条款吧，使用者需要自行对使用代码的后果负责

—— 来自 HUAWEI LNA-AL00, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.5.3-play

*****

####  fuckingworld  
##### 22#       发表于 2024-3-30 15:43

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=64428461&amp;ptid=2177811" target="_blank">DTCPSS 发表于 2024-3-30 15:37</a>
国内宅宅开源贡献者不是人均日文名

—— 来自 S1Fun</blockquote>
为什么你们会有“开源者/程序员”都是死宅/二次元这种印象

[论坛助手,iPhone](https://bbs.saraba1st.com/2b/forum.php?mod=viewthread&amp;tid=2029836)

*****

####  bakabaka999  
##### 23#       发表于 2024-3-30 15:44

 本帖最后由 bakabaka999 于 2024-3-30 15:47 编辑 
<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=64427957&amp;ptid=2177811" target="_blank">Hieda 发表于 2024-3-30 14:24</a>

arch和msys2都老早就包含中招版本了

好在openssh都没链</blockquote>
Arch 暂时不受影响。这次只有 tarball 版本的源码被植入了后门，Arch 官方的 PKGBUILD 在三月从 tarball 源码换成了从 git 直接 checkout 逃过一劫。而且本来这个后门是在 m4 里面进行了发行版 check 的，只有 Debian/Ubuntu/Fedora/openSUSE 之类受影响。 <blockquote>目前的证据表明这个后门仅影响部分 Debian/Ubuntu/Fedora/openSUSE 的预发布版本，且均已发布回退更新
目前确定曾受影响的发行版：Debian unstable/testing between 2024-02-26 and 2024-03-29Ubuntu noble-proposed/noble-release between 2024-02-26 and 2024-03-29Fedora 40/41(Rawhide) between 2024-02-27 and 2024-03-29openSUSE Tumbleweed between 2024-03-07 and 2024-03-28</blockquote>

*****

####  coyove  
##### 24#       发表于 2024-3-30 15:45

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=64428461&amp;ptid=2177811" target="_blank">DTCPSS 发表于 2024-3-30 15:37</a>

国内宅宅开源贡献者不是人均日文名

—— 来自 S1Fun</blockquote>
不是我地图炮，一般这种前端、OI选手居多<img src="https://static.saraba1st.com/image/smiley/face2017/033.png" referrerpolicy="no-referrer">

*****

####  芜湖挨宰  
##### 25#       发表于 2024-3-30 16:15

gpt能检测代码中有后门嘛<img src="https://static.saraba1st.com/image/smiley/face2017/066.png" referrerpolicy="no-referrer">

*****

####  hetdff  
##### 26#       发表于 2024-3-30 16:41

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=64428513&amp;ptid=2177811" target="_blank">bakabaka999 发表于 2024-3-30 15:44</a>

Arch 暂时不受影响。这次只有 tarball 版本的源码被植入了后门，Arch 官方的 PKGBUILD 在三月从 tarball  ...</blockquote>
那看来还是滚动发行的openSUSE Tumbleweed影响最大，其他三个都不是稳定版

*****

####  cumbland  
##### 27#       发表于 2024-4-2 22:41

黑客目前有很大可能是东欧假装东八区的，因为中国传统节假日他还在上传源代码，而东欧假期却没有。另外发现他虽然绝大部分的登录显示是东八区，却有几次是东欧的时区。来自: iPhone客户端

*****

####  riczxc  
##### 28#       发表于 2024-4-3 05:42

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=64464836&amp;ptid=2177811" target="_blank">cumbland 发表于 2024-4-2 22:41</a>

黑客目前有很大可能是东欧假装东八区的，因为中国传统节假日他还在上传源代码，而东欧假期却没有。另外发现 ...</blockquote>
时区这个东西也不是不可以改/故意泄漏个假的。工作时间也是。不过在项目合作也有一定的实时性，不是那么容易改的。考虑这个是某个国家的官方行为，那么UTC+2/UTC+3的可能性都有。

据说UTC+2的改动是原作者Lasse帮Jia Tan合并的。真正可能漏马脚的是一个UTC+3的提交。

所以本来因为有UTC+2，大家怀疑东欧的国家。现在只有UTC+3，那就应该是俄罗斯或者以色列（夏令时）这两个常见的嫌疑人了。

*****

####  赤星ビスコ  
##### 29#       发表于 2024-4-3 06:25

我还看到这人为了绕过代码安全检测，注入后门的那次提交故意带了语法错误<img src="https://static.saraba1st.com/image/smiley/face2017/067.png" referrerpolicy="no-referrer">

*****

####  redbuck  
##### 30#       发表于 2024-4-3 08:05

最近国内 boot cdn 也有投毒，嗅探到移动端环境给你页面塞广告，恶意代码特意转义了，变量都更名成 0x，关键 api 也改成索引取值，总之让你人工很难识别。

但是好玩的来了，把恶意代码喂给 chat GPT，它可以识别出代码的意图，甚至可以让他还原成可读的版本。

所以后面应该可以结合 ai，提交前做一次 ai 预检，提高一下投毒门槛

*****

####  perfaceNext  
##### 31#       发表于 2024-4-3 08:24

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=64467126&amp;ptid=2177811" target="_blank">redbuck 发表于 2024-4-3 08:05</a>
最近国内 boot cdn 也有投毒，嗅探到移动端环境给你页面塞广告，恶意代码特意转义了，变量都更名成 0x，关 ...</blockquote>
然后让ai改写一个让ai检测不出来的版本<img src="https://static.saraba1st.com/image/smiley/face2017/049.png" referrerpolicy="no-referrer">，搁这里套娃了

*****

####  redbuck  
##### 32#       发表于 2024-4-3 08:33

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=64467275&amp;ptid=2177811" target="_blank">perfaceNext 发表于 2024-4-3 08:24</a>
然后让ai改写一个让ai检测不出来的版本，搁这里套娃了</blockquote>
不懂能不能别搁这硬凑啊

这个案例里，最大的问题就是 maintainer 没在网，没人 review 才塞进去的。
搞攻击总要调到敏感 api，这些结合上下文是能推导的，而且恰恰是 ai 的强项，人类读起来费劲的它读没有障碍

*****

####  ranocchia  
##### 33#       发表于 2024-4-3 09:24

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=64427933&amp;ptid=2177811" target="_blank">geeky_kappa 发表于 2024-3-30 14:19</a>

据称主要活动时间符合东八区</blockquote><blockquote>分析发现xz后门黑客可能生活在东欧 但试图冒充中国用户发起攻击

冒充东八区用户：

一般来说黑客的工作时间集中在下午或深夜比较合理，毕竟很少有人愿意造成五点就起来干活 (尽管早睡早起也确实是个好习惯)。

Jia Tan 这名字听起来就像是东亚人，而他的 Github 大部分提交都带有 UTC+8 时间戳，也就是东八区用户，东八区用户配合亚洲名字，那么想要冒充谁其实已经很明显。

然而黑客显然不会使用自己的真实名字，所以这招祸水东引本身就存在漏洞，所以每次提交都修改时区为东八区似乎有助于提高可信度。

有几次忘记修改时区：

正如前面提到的每次修改系统时区其实是个很麻烦的事情，毕竟一年提交那么多次代码每次修改会让人无比烦躁。

因此分析就发现在 UTC+2 和 UTC+3 时区分别有过 3 次和 6 次调提交，这与 UTC+8 的 440 次提交来说显得很少，但却是个关键证据。

毕竟如果真是生活在东八区，那为什么有几次要修改成 UTC+2 或者 UTC+3 呢？要么他是去东欧旅游了，顺手在那里写的代码并提交。

那旅游这事河里嘛？也不河里，因为有两次提交时区发生变更，但中途有 11 个小时的时间差，也就是说他在 UTC+3 提交代码后立即飞往 UTC+8，但这两个时区之间的飞机通常要 10~12 个小时的飞行时长，这还是直达的情况下，如果考虑中转时间会更长，因此这看起来并不合理。

还有一次提交时 UTC+3 和 UTC+8 只差几分钟，马斯克的星舰也没这么快，所以必然有一个时区是造假的。

然而谁会在逢年过节还继续干活呢？

在分析中有个很有趣的现象引起 RHEA 的关注，那就是他对比了中国 2023 年的节假日，发现 Jia Tan 竟然在中国农历新年以及中秋节等假期提交代码。

倒不是说不能在法定节假日期间继续干活并提交代码，但 RHEA 发现这名黑客在东欧假期 (UTC+2 和 UTC+3 都包括部分东欧国家) 的时候却没有提交代码。

东欧假期与中国的法定节假日并不重叠，在中国节假日期间提交代码而在东欧节假日却没有提交代码，因此从代码提交时间来看，Jia Tan 的工作安排和假期更适合东欧人，而不是东亚或东南亚地区的人。

另一方面，Jia Tan 的主要工作时间是周二、周三、周四和周五，如果他是个业余爱好者那有自己的工作，不可能工作日还如此活跃的提交代码。

除非他是受雇于人，也就是这就是他的主要工作，所以周六、周日都是休息的，至于周一，想必全世界打工人都一样，刚刚过了周末周一脑袋不够清醒不是很想干活吧。

基于我们可以初步认为 Jia Tan 很有可能是生活在东欧的人，而发起攻击就是他的主要工作，使用东亚名称和修改 UTC+8 就是想要规避追踪，不过打工人偶尔偷懒也是正常的，所以总有几次提交泄露了他所在的真实时区。</blockquote>

*****

####  macos  
##### 34#       发表于 2024-4-3 09:38

靠的不是技术，而是社会工程技巧，虽然
耗时比较久，但是人都可以复刻，但败也败在没技术，写了有bug的功能暴露了

—— 来自 HUAWEI KKG-AN00, Android 10上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.5.4

*****

####  佳丽三千到  
##### 35#       发表于 2024-4-3 10:32

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=64467880&amp;ptid=2177811" target="_blank">ranocchia 发表于 2024-4-3 09:24</a></blockquote>
众所周知黑客有多层跳板的习性。
所以从东八区跳到东欧只是一层，可以再挖一层。

—— 来自 HONOR LSA-AN00, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.5.4

*****

####  小野賢章  
##### 36#       发表于 2024-4-3 10:35

应该强制 GPG 签名，并且维护者线下聚会交换公钥<img src="https://static.saraba1st.com/image/smiley/face2017/037.png" referrerpolicy="no-referrer">

*****

####  想要游戏体验  
##### 37#       发表于 2024-4-3 10:47

嘉痰 指愿意做嘉然的痰 破案了 是管人痴

*****

####  ranocchia  
##### 38#       发表于 2024-4-3 11:08

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=64468780&amp;ptid=2177811" target="_blank">佳丽三千到 发表于 2024-4-3 10:32</a>

众所周知黑客有多层跳板的习性。

所以从东八区跳到东欧只是一层，可以再挖一层。</blockquote>
如果入侵的是什么机密要害部门那多层跳板很正常，这次的事件看起来不像吧，搞不好只是个外包的。

*****

####  gnihton314  
##### 39#       发表于 2024-4-3 11:18

 本帖最后由 gnihton314 于 2024-4-3 11:22 编辑 

Shawn the R0ck 写道：2024年3月29日，一份关于在自由软件社区备受争议的开源项目 xz 软件包被上游源代码中的后门所污染的报告在 oss-security 邮件列表中曝光。这个后门影响到了 liblzma 库，它是 xz 软件包的一部分，在第一份报告发布后有多了很多跟进的研究，内容主要如下，1） 这个后门完整地存在于发布的 xz 源码包中(5.6.0 和 5.6.1 版本)，但上游 git 仓库中存在伪装为测试数据，但并未插入 liblzma 中的载荷，而打包前单独加入源码包中的唤醒代码（它们不存在于 git 仓库中，因此从 git 仓库，或由 github 生成的源码包编译的 liblzma 中不会有后门）会将载荷注入到构建过程中。

2） 注入的代码修改 Makefile 以包含恶意文件，这些文件在构建过程中被执行,导致进一步的有效载荷注入。

3） 这个有效载荷针对的是使用 gcc 和 GNU 链接器的 x86-64 GNU/Linux 系统,并且是 Debian 或 RPM 软件包构建的一部分。

4） 恶意代码针对 OpenSSH 服务器进行劫持以实现远程代码执行，但显著降低了登录速度。它通过劫持和修改 liblzma 库中的某些函数来实现这一点，其载荷是间接加载到 sshd 中的。sshd 实现了对 systemd-notify 的支持，liblzma 被加载是因为它是 libsystemd 的其他部分所依赖的，systemd 的复杂度再次成为了实际上的安全隐患。

5） 建议立即升级任何可能受影响的系统，因为这些被污染的版本还未广泛被 GNU/Linux 发行版集成。

6） 提供了一个脚本来检测系统是否可能受到影响。

7）后门投毒者关闭了 LANDLOCK 沙箱，这个已经被主要维护者修复。

开源社区诸多用户都对于 systemd 饱受争议的复杂性以及其生态渗透到 GNU/Linux 系统之深本有意见，<strong>借愚人节之机</strong>满足读者的阴谋论叙事的诉求：幕后黑手其实是 M$，意在摧毁 GNU/Linux 生态，首先，他们秘密收买了 Lennart Poettering，让他开发了 systemd。Lennart 在 M$ 的授意下,将 systemd 逐步渗透到 GNU/Linux 发行版中,为后续行动铺路，2022年3月，M$ 认为可以执行下一步计划了就排出了 Jia Tan 团队跟 xz-utils 社区进行交涉，Lennart Poettering 的任务也宣告结束，2022年6月，M$ 公开召回（雇佣）Lennart，此后 M$ 筹划了 2023 年开始支持 openssh 的 systemd 生态进而让 Jia TAN 去掌控整个 GNU/Linux 生态，只是没想到被一个执着于性能且追求计算美学的工程师破坏了原本完美的计划，M$立马命令Github关闭了相关的帐号以毁灭证据，幸运的是这个蔚蓝色的星球的赛博网络里有时空穿梭机，这让github的重要信息得以保留。

*****

####  chachi  
##### 40#       发表于 2024-4-3 13:14

ms躺枪

----发送自 [samsung SM-S9180,Android 14](http://stage1.5j4m.com/?1.37)


*****

####  ysys  
##### 41#       发表于 2024-4-3 13:18

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=64427933&amp;ptid=2177811" target="_blank">geeky_kappa 发表于 2024-3-30 14:19</a>

据称主要活动时间符合东八区</blockquote>
有人分析了，有几次提交是东欧的时区，而且时间上隔的很近，不太可能是旅游之类外出的情况

大概率是伪装的东八区

*****

####  ysys  
##### 42#       发表于 2024-4-3 13:20

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=64467126&amp;ptid=2177811" target="_blank">redbuck 发表于 2024-4-3 08:05</a>

最近国内 boot cdn 也有投毒，嗅探到移动端环境给你页面塞广告，恶意代码特意转义了，变量都更名成 0x，关 ...</blockquote>
ai不用全查出来，能滤一部分都是好的

问题是这个ai谁来出……这世界上有信得过的么


*****

####  tonyunreal  
##### 43#       发表于 2024-4-3 13:45

<img src="https://p.sda1.dev/16/9d168e8fff03f2dd5c5ee5be08f5d554/ossattack.jpg" referrerpolicy="no-referrer">

红迪Linux婆罗门做的屌图，汉化了一下


*****

####  qqdragon  
##### 44#       发表于 2024-4-3 13:57

xz 后门作者 JiaT75 (Jia Tan) 使用了拼音名字，但并不意味着他或他们就是华裔，可能不过是一个伪装。在长达三年时间内，Jia Tan 不可能一直不露出任何马脚。他的英文邮件和母语英语者一样出色，Git 时间戳是可以修改的，但他或他们可能会在某个时间忘记修改，导致时间戳出现可疑的变动，比如工作时间从 UTC+08 切换到 UTC+02 和 UTC+03。对其 Git 时间戳的分析显示，Jia Tan 可能生活在东欧。他或他们被发现在中国官方假期如中秋、清明、农历新年期间都工作，但在东欧的假期比如圣诞节和新年期间则从不工作。

Shawn the R0ck 写道：2024年3月29日，一份关于在自由软件社区备受争议的开源项目 xz 软件包被上游源代码中的后门所污染的报告在 oss-security 邮件列表中曝光。这个后门影响到了 liblzma 库，它是 xz 软件包的一部分，在第一份报告发布后有多了很多跟进的研究，内容主要如下，1） 这个后门完整地存在于发布的 xz 源码包中(5.6.0 和 5.6.1 版本)，但上游 git 仓库中存在伪装为测试数据，但并未插入 liblzma 中的载荷，而打包前单独加入源码包中的唤醒代码（它们不存在于 git 仓库中，因此从 git 仓库，或由 github 生成的源码包编译的 liblzma 中不会有后门）会将载荷注入到构建过程中。2） 注入的代码修改 Makefile 以包含恶意文件，这些文件在构建过程中被执行,导致进一步的有效载荷注入。3） 这个有效载荷针对的是使用 gcc 和 GNU 链接器的 x86-64 GNU/Linux 系统,并且是 Debian 或 RPM 软件包构建的一部分。4） 恶意代码针对 OpenSSH 服务器进行劫持以实现远程代码执行，但显著降低了登录速度。它通过劫持和修改 liblzma 库中的某些函数来实现这一点，其载荷是间接加载到 sshd 中的。sshd 实现了对 systemd-notify 的支持，liblzma 被加载是因为它是 libsystemd 的其他部分所依赖的，systemd 的复杂度再次成为了实际上的安全隐患。5） 建议立即升级任何可能受影响的系统，因为这些被污染的版本还未广泛被 GNU/Linux 发行版集成。6） 提供了一个脚本来检测系统是否可能受到影响。7）后门投毒者关闭了 LANDLOCK 沙箱，这个已经被主要维护者修复。开源社区诸多用户都对于 systemd 饱受争议的复杂性以及其生态渗透到 GNU/Linux 系统之深本有意见，借愚人节之机满足读者的阴谋论叙事的诉求：幕后黑手其实是 M$，意在摧毁 GNU/Linux 生态，首先，他们秘密收买了 Lennart Poettering，让他开发了 systemd。Lennart 在 M$ 的授意下,将 systemd 逐步渗透到 GNU/Linux 发行版中,为后续行动铺路，2022年3月，M$ 认为可以执行下一步计划了就排出了 Jia Tan 团队跟 xz-utils 社区进行交涉，Lennart Poettering 的任务也宣告结束，2022年6月，M$ 公开召回（雇佣）Lennart，此后 M$ 筹划了 2023 年开始支持 openssh 的 systemd 生态进而让 Jia TAN 去掌控整个 GNU/Linux 生态，只是没想到被一个执着于性能且追求计算美学的工程师破坏了原本完美的计划，M$立马命令Github关闭了相关的帐号以毁灭证据，幸运的是这个蔚蓝色的星球的赛博网络里有时空穿梭机，这让github的重要信息得以保留。


*****

####  基本农田  
##### 45#       发表于 2024-4-3 14:17

开源软件贡献者原来是可以当全职工作的吗

*****

####  基本农田  
##### 46#       发表于 2024-4-3 14:17

开源软件贡献者原来是可以当全职工作的吗

*****

####  xiaoan2003  
##### 47#       发表于 2024-4-3 14:22

可怜的汉友，又要替波友/乌友/俄友背锅了


*****

####  gnihton314  
##### 48#       发表于 2024-4-3 14:39

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=64471285&amp;ptid=2177811" target="_blank">基本农田 发表于 2024-4-3 14:17</a>

开源软件贡献者原来是可以当全职工作的吗</blockquote>
很难，不过有些大公司和NGO会给开源软件开发者送一点钱，再就靠大家捐赠。


*****

####  michaelz  
##### 49#       发表于 2024-4-3 18:02

5.6.1 版本的都会影响吗 还是只影响 linux那几个特定的发行版  我用的MSYS2 里 就是 5.6.1  


*****

####  heyeshuang  
##### 50#       发表于 2024-4-3 20:09

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=64473866&amp;ptid=2177811" target="_blank">michaelz 发表于 2024-4-3 18:02</a>
5.6.1 版本的都会影响吗 还是只影响 linux那几个特定的发行版  我用的MSYS2 里 就是 5.6.1   ...</blockquote>
不要紧张，Windows没有systemd

—— 来自 OnePlus HD1900, Android 11上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.5.2-play

