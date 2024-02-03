
*****

####  moeblack  
##### 1#       楼主       发表于 2024-1-22 09:20

 本帖最后由 moeblack 于 2024-1-23 12:09 编辑 

有问题直接回帖问我，看到了就回答。

我现在把服务器迁移到炼丹用的64G内存主机上了哭笑

这游戏太吃内存了16G根本不够

想来我服务器玩的可以私信我
 <blockquote>jammsen/palworld-dedicated-server

docker image</blockquote>
官方教程

 <blockquote>关于“将本地/合作模式存档迁移到服务器”的话题，社区已经有了一套完整的解决方案。这套方案比较复杂，建议有一定程序操作能力的人来执行。

操作步骤：

对于本地/合作模式存档迁移到服务器：

1. 通过 SteamCMD 创建一个专用服务器。

2. 运行服务器一次。

3. 登录服务器，使其创建一个玩家文件夹和 .sav 文件。

- 我的看起来像是 "EE256A5000000000000000000000000.sav"，这是你稍后在脚本中需要的文件名(不包括 .sav)。

4. 停止服务器。

5. 备份所有文件以防万一。

6. 将 C:\Users\domin\AppData\Local\Pal\Saved\SaveGames\Your Steam ID\BUNCH OF LETTERS AND NUMBERS\ 文件夹中的内容复制过来。

7. 确保安装了最新版本的 Python，从 Nul 下载脚本和 UEsave 可执行文件。

8. 用正确的参数运行命令行。

- 例如，对我来说是 "python fix-host-save.py F:\Fixit\uesave.exe F:\Palworld\Server_1\Pal\Saved\SaveGames\0\8A15EB32440279628FB4587AF7718787 EE256A5000000000000000000000000"

9. 稍等片刻，这可能需要一些时间。

10. 复制所有文件和文件夹，覆盖原有文件。

11. 启动服务器。

12. 理论上你现在应该可以开始了。

如果你使用的是云/游戏主机：

- 运行你的新服务器。

- 登录服务器，使其创建一个玩家文件夹和 .sav 文件。

- 停止你的服务器。

- 通过 FTP 连接到你的服务器，并找到保存游戏的目录(这个文件夹包含了所有的存档数据)。

- 将文件下载到你的电脑上，这样你才能运行脚本，因为在主机提供商那里是无法做到的。

= 你也可以通过为 sav 文件创建一个文件夹来使其更加整洁。

- 现在你可以按照上面 #7 提到的其余步骤进行操作。

- 脚本运行完后，你可以将文件上传回服务器，然后启动。

链接：

Nul 的脚本：[https://github.com/xNul/palworld-host-save-fix](https://github.com/xNul/palworld-host-save-fix)

UESave 扩展：[https://github.com/trumank/uesave-rs](https://github.com/trumank/uesave-rs)

Python 下载：[https://www.python.org/downloads/](https://www.python.org/downloads/)

额外选项，如果你想手动将文件从 sav 转换为 json 反之亦然，这些脚本可以帮助你。
[https://gist.github.com/cheahjs/300239464dd84fe6902893b6b9250fd0](https://gist.github.com/cheahjs/300239464dd84fe6902893b6b9250fd0)

[https://gist.github.com/Toakan/3 ... erver-community-faq](https://gist.github.com/Toakan/3c78a577c21a21fcc5fa917f3021d70e#palworld-server-community-faq)

另一种选择：[https://www.reddit.com/r/Palworl ... ile_incl/?rdt=55658](https://www.reddit.com/r/Palworld/comments/19cb8su/complete_guide_to_transfer_a_coop_save_file_incl/?rdt=55658)

附加信息：

加入官方 Discord：
[https://discord.gg/pocketpair](https://discord.gg/pocketpair)</blockquote>
<strong>准备</strong>

一台有Linux或者Windows的服务器：官方推荐是4核CPU 内存16G以上

官方的服务器配置要求原文

CPU4Cores (recommend)RAM16GB
<strong>Recommend over 32GB for stable operation.</strong>

It is possible to start the server with 8 GB, but the further you play, the server will crash due to out of memory.NetworkUDP Port 8211 (Default) Port forwarding required.  

最大的问题是内存问题，拉到主楼最后有暂时的解决方法

SSH终端连接服务器

良好的网络环境
 <blockquote>关于网络

目前几个解决办法

1. 租用云服务器，这是最快捷的，因为没有奸商赞助所以我不推荐，上淘宝和小黄鱼都能搜到组服务器的。建议找给Minecraft开过服务器的商家，他们对这种吃CPU和内存的游戏服务端有经验。

2. 家用电脑开服，有公网IP使用公网iP，在路由器后台设置端口映射，给好朋友分享IP即可。

2.1 使用FRP服务，例如樱花FRP，把自己的电脑端口通过樱花的服务器转发出去，我记得这个是免费10G，够用一周了。</blockquote>
<strong>安装</strong>

以下使用Linux安装，windows服务器可以直接使用steam 下载安装

ssh连接服务器后台：无论使用什么服务器，是自己家里闲置的还是网络上购买的

使用root登入

新建一个账号，名字叫steam，使用这个账号完成下面的工序

[B]注意，一定要使用非root账号来安装使用steamcmd，这就是新建steam用户的原因[/B] <blockquote>sudo useradd -m steam

sudo passwd steam</blockquote>
切换到steam账号
 <blockquote>sudo -u steam -s

cd /home/steam</blockquote>
进入home目录，
 <blockquote>cd ~</blockquote>
安装steamcmd

在Ubuntu上使用
 <blockquote>sudo add-apt-repository multiverse; sudo dpkg --add-architecture i386; sudo apt update 

sudo apt install steamcmd</blockquote>
如果是其他发行版或者windows 查看官方教程

[steamcmd官方安装指南](https://developer.valvesoftware.com/wiki/SteamCMD#Windows)

这个steamcmd同样可以使用docker进行安装
[docker安装steamcmd教程](https://developer.valvesoftware.com/wiki/SteamCMD#Docker)

之后docker和Linux是类似的操作，集体看steamcmd安装的教程

使用steamcmd安装幻兽帕鲁服务端
 <blockquote>steamcmd +login anonymous +app_update 2394010 validate +quit</blockquote>
切换到幻兽帕鲁的目录,执行(目录一般在~/.local/这个文件夹里面)

./PalServer.sh
 <blockquote>-useperfthreads -NoAsyncLoadingThread -UseMultithreadForDS 这几个参数据官方所说可以实现多线程加速，建议加上 更多参数可以查看[官方指南](https://tech.palworldgame.com/dedicated-server-guide)</blockquote>
如果显示
 <blockquote>.steam/sdk64/steamclient.so: cannot open shared object file: No such file or directory</blockquote>
解决方法
 <blockquote>mkdir -p ~/.steam/sdk64/

steamcmd +login anonymous +app_update 1007 +quit

cp <strong>path/to/your</strong>/Steam/steamapps/common/Steamworks\ SDK\ Redist/linux64/steamclient.so ~/.steam/sdk64/</blockquote>
正常启动
 <blockquote>$ ./PalServer.sh

Shutdown handler: initalize.

Increasing per-process limit of core file size to infinity.

dlopen failed trying to load:

steamclient.so

with error:

steamclient.so: cannot open shared object file: No such file or directory

[S_API] SteamAPI_Init(): Loaded '/home/ubuntu/.steam/sdk64/steamclient.so' OK.  (First tried local 'steamclient.so')</blockquote>
输入端口号8211即可连接

记得是自己服务器的ip:端口号

比如本机就是127.0.0.1:8211

如果是其他ip 例如 123.123.123.123

就是123.123.123.123:8211

<img src="http://./mon_202401/20/biQ2t-1o8kK15T3cSyw-k7.webp" referrerpolicy="no-referrer">

<strong>一些问题</strong>

防火墙，linux允许端口通过防火墙的命令是

sudo ufw allow &lt;port&gt;

在执行之前记得安装ufw这个package，当然，你也可以关闭防火墙，如果是在家庭网络中的话，记得在光猫界面把服务器IP的端口映射出去。

光猫 高级 端口映射 光猫密码在光猫背后

需要有IPV4公网IP

关于爆内存

目前看来可以通过把Linux的Swap(Windows上应该叫虚拟内存，但是两者本质不一样)设置更大来解决，我设置了32G的swap，目前一整天没有爆。

或者使用Linux脚本，让服务器一天重启一次即可。

这个服务器爆内存的本质是内存清理没有做好，而不是真的需要这么多内存。

关于服务器指令

Palworld给服务器管理员设置了一系列指令，可以在这个网站查找到

[幻兽帕鲁服务器指令](https://nodecraft.com/support/games/palworld/palworld-server-admin-commands)

在这之前，需要对玩家的管理员资格进行认证 原版教程在这里

[服务器认证教程](https://nodecraft.com/support/games/palworld/how-to-become-an-admin-of-your-palworld-server)

开服之前可以在服务器根目录

DefaultPalWorldSettings.ini 这个文件里，通过修改

AdminPassword=“”

这个参数来设定服务器密码

开服之后，可以通过修改

Pal/Saved/Config/LinuxServer/PalWorldSettings.ini 这个文件来修改服务器配置

将DefaultPalWorldSettings.ini 里的参数粘贴进去即可

之后再服务器聊天框里输入/AdminPassword 你的密码 来认证为管理员

管理员可以用的指令大致如下

Command 命令Description 描述/Shutdown {Seconds} {MessageText}Gracefully shuts down server with an optional timer and/or message to notify players in your server.使用可选的计时器和/或消息正常关闭服务器，以通知服务器中的玩家。/DoExitForcefully shuts down the server immediately. It is not recommended to use this option unless you've got a technical problem or are okay with potentially losing data.立即强制关闭服务器。不建议使用此选项，除非您遇到技术问题或可以接受可能丢失数据的情况。/Broadcast {MessageText}Broadcasts a message to all players in the server.向服务器中的所有玩家广播消息。/KickPlayer {PlayerUID or SteamID}Kicks player from the server. Useful for getting a player's attention with moderation.将玩家踢出服务器。有助于适度地吸引玩家的注意力。/BanPlayer {PlayerUID or SteamID}Bans player from the server. The Player will not be able to rejoin the server until they are unbanned.禁止玩家进入服务器。玩家在解禁之前将无法重新加入服务器。/TeleportToPlayer {PlayerUID or SteamID}INGAME ONLY

Immediately teleport to the target player仅限游戏内

立即传送到目标玩家/TeleportToMe {PlayerUID or SteamID}INGAME ONLY

Immediately teleports target player to you.仅限游戏内

立即将目标玩家传送到您身边。/ShowPlayersShows information on all connected players显示所有已连接玩家的信息/InfoShows server information 显示服务器信息/SaveSave the world data to disk. Useful to ensure your Pal, player, and other data is saved before stopping the server or performing a risky gameplay option.将世界数据保存到磁盘。有助于确保您的好友、玩家和其他数据在停止服务器或执行有风险的游戏选项之前得到保存。

在服务器的设置文件里，还有其他的设置可以调整。<strong>注意，行内不能换行</strong>
设置项中文释义Difficulty难度DayTimeSpeedRate白天时间速率NightTimeSpeedRate夜间时间速率ExpRate经验值率PalCaptureRatePal捕获率PalSpawnNumRatePal出现率PalDamageRateAttackPal攻击伤害倍率PalDamageRateDefense对Pal的防御伤害倍率PlayerDamageRateAttack玩家攻击伤害倍率PlayerDamageRateDefense对玩家的防御伤害倍率PlayerStomachDecreaceRate玩家饥饿消耗率PlayerStaminaDecreaceRate玩家耐力消耗率PlayerAutoHPRegeneRate玩家自动HP恢复率PlayerAutoHpRegeneRateInSleep玩家睡眠HP恢复率PalStomachDecreaceRatePal饥饿消耗率PalStaminaDecreaceRatePal耐力消耗率PalAutoHPRegeneRatePal自动HP恢复率PalAutoHpRegeneRateInSleepPal睡眠HP恢复率(Palbox中)BuildObjectDamageRate建筑物伤害倍率BuildObjectDeteriorationDamageRate建筑物损耗率CollectionDropRate采集物品掉落倍率CollectionObjectHpRate可采集对象HP倍率CollectionObjectRespawnSpeedRate可采集对象重生间隔EnemyDropItemRate敌人掉落物品倍率DeathPenalty死亡惩罚(无：无丢失，物品：不带装备的丢失物品，物品和装备：丢失物品和装备，全部：丢失所有物品、装备、伙伴(库存中))

None : No lost, Item : Lost item without equipment, ItemAndEquipment : Lost item and equipment, All : Lost All item, equipment, pal(in inventory)GuildPlayerMaxNum公会最大玩家数PalEggDefaultHatchingTimePal蛋孵化时间(小时)ServerPlayerMaxNum服务器最大玩家数ServerName服务器名称ServerDescription服务器描述AdminPassword管理员密码ServerPassword设置服务器密码PublicPort公共端口号PublicIP公共IPRCONEnabled启用RCONRCONPortRCON端口号

给开服的坛友推荐用RCON管理后端

<img src="https://img.saraba1st.com/forum/202401/22/092008q25iaaarbia4b323.png" referrerpolicy="no-referrer">

<strong>{8D8ACC0A-49D6-4fb2-B19E-A852CC3156D5}.png</strong> (264.12 KB, 下载次数: 0)

下载附件

2024-1-22 09:20 上传

效果如此，类似于在游戏里输入管理员密码之后控制服务器

可以关闭服务器，T人之类的。

我用的是之前MC开服时候用的RCON控制台。

你们也可以换自己的，地址如下

[https://github.com/zkhssb/NectarRCON](https://github.com/zkhssb/NectarRCON)  <blockquote>丢存档警告<blockquote>我和朋友已经遇上了<blockquote>

<img src="https://img.saraba1st.com/forum/202401/22/110149j2kk1oadu21uvzba.jpg" referrerpolicy="no-referrer">

<strong>636f3772089cd224409ac0e4f2770cf9.jpg</strong> (36.61 KB, 下载次数: 0)

下载附件

2024-1-22 11:01 上传

</blockquote>
</blockquote></blockquote><blockquote>关于存档删除

如上，存档损坏之后需要修复

如果有对应玩家PID，可以进入

PalServer\Pal\Saved\SaveGames\0\&lt;HEX&gt;\Players\

这个文件夹，删除对应的文件

PID=10进制

FileName=16进制

如果没有的话，询问一下玩家最后登录的时间，通过最后存档时间来查询存档。

查到之后删除玩家对应存档 即可新建存档</blockquote><blockquote>玩家PID获取

在RCON后台输入

ShowPlayers

可以查看当前在线玩家Name，PID，SteamID</blockquote>

﹍﹍﹍

评分

 参与人数 3战斗力 +4

|昵称|战斗力|理由|
|----|---|---|
| FUZE| + 2|docker跑的起来吗|
| 丹德里恩| + 1|好评加鹅|
| 河水| + 1||

查看全部评分

*****

####  lvcha3  
##### 2#       发表于 2024-1-22 10:01

不是买了游戏就可以玩的啊？

*****

####  传说中的天才  
##### 3#       发表于 2024-1-22 10:03

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63730857&amp;ptid=2168983" target="_blank">lvcha3 发表于 2024-1-22 10:01</a>

不是买了游戏就可以玩的啊？</blockquote>
一个人玩单机，是。

简单的自己或者朋友开主机联机，是，

（和朋友）加入官方服务器，是，

想和朋友一起享受最佳联机体验，不是。

*****

####  mwj  
##### 4#       发表于 2024-1-22 10:04

<blockquote>lvcha3 发表于 2024-1-22 10:01
不是买了游戏就可以玩的啊？</blockquote>
可以直接开玩，官方也提供了类似mc的私服搭建工具可以搭建服务器后玩。

*****

####  丹德里恩  
##### 5#       发表于 2024-1-22 10:23

<img src="https://static.saraba1st.com/image/smiley/face2017/037.png" referrerpolicy="no-referrer">挺傻瓜式的，分享给傻吊群友了

*****

####  lyt777  
##### 6#       发表于 2024-1-22 10:25

抽空我在公司服务器上整一个，用不着DOCKER，我司ESXI有的是。<img src="https://static.saraba1st.com/image/smiley/face2017/048.png" referrerpolicy="no-referrer">

*****

####  晨曦之下  
##### 7#       发表于 2024-1-22 10:41

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63730857&amp;ptid=2168983" target="_blank">lvcha3 发表于 2024-1-22 10:01</a>

不是买了游戏就可以玩的啊？</blockquote>
你可以翻翻差评 官服卡顿连不上的一堆 还有丢存档的

你也不想和小伙伴一晚上掉十几次吧

*****

####  moeblack  
##### 8#         楼主| 发表于 2024-1-22 11:06

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63731214&amp;ptid=2168983" target="_blank">lyt777 发表于 2024-1-22 10:25</a>

抽空我在公司服务器上整一个，用不着DOCKER，我司ESXI有的是。</blockquote>
我用PVE，LXC容器开的服务器，很稳<img src="https://static.saraba1st.com/image/smiley/face2017/220.png" referrerpolicy="no-referrer">

*****

####  lvcha3  
##### 9#       发表于 2024-1-22 11:11

阿里云我的服务器只有2g内存是不是就不用试了

*****

####  moeblack  
##### 10#         楼主| 发表于 2024-1-22 11:15

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63731844&amp;ptid=2168983" target="_blank">lvcha3 发表于 2024-1-22 11:11</a>

阿里云我的服务器只有2g内存是不是就不用试了</blockquote>
开不起来

*****

####  midearth  
##### 11#       发表于 2024-1-22 11:27

请问下同服务器上限32人是说什么原因吗？这种开放世界游戏非同时在线的玩家数量再多又有什么影响

*****

####  硫磺之火  
##### 12#       发表于 2024-1-22 11:31

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63732075&amp;ptid=2168983" target="_blank">midearth 发表于 2024-1-22 11:27</a>
请问下同服务器上限32人是说什么原因吗？这种开放世界游戏非同时在线的玩家数量再多又有什么影响 ...</blockquote>
内存会爆

—— 来自 Xiaomi 22041216C, Android 13上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.5.2

*****

####  moeblack  
##### 13#         楼主| 发表于 2024-1-22 12:15

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63732075&amp;ptid=2168983" target="_blank">midearth 发表于 2024-1-22 11:27</a>
请问下同服务器上限32人是说什么原因吗？这种开放世界游戏非同时在线的玩家数量再多又有什么影响 ...</blockquote>
同时在线多了内存会爆

—— 来自 HUAWEI ALN-AL80, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.1.2

*****

####  Litccc  
##### 14#       发表于 2024-1-22 12:19

可惜不支持arm的服务器，不然甲骨文薅的服务器就能排上用场了<img src="https://static.saraba1st.com/image/smiley/face2017/067.png" referrerpolicy="no-referrer">

*****

####  今天你提了吗  
##### 15#       发表于 2024-1-22 13:06

没公网ip，能不能图便宜买个最低档有公网ip的小鸡，反代家里电脑，不知道这么搞延迟怎么样

*****

####  蒜苗  
##### 16#       发表于 2024-1-22 13:30

这游戏到底支不支持IPv6，支持的话就不需要愁什么公网IP了

*****

####  qianoooo  
##### 17#       发表于 2024-1-22 14:32

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63733541&amp;ptid=2168983" target="_blank">蒜苗 发表于 2024-1-22 13:30</a>

这游戏到底支不支持IPv6，支持的话就不需要愁什么公网IP了</blockquote>
不支持 discord有人测过

*****

####  tk553521  
##### 18#       发表于 2024-1-22 15:29

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63731844&amp;ptid=2168983" target="_blank">lvcha3 发表于 2024-1-22 11:11</a>

阿里云我的服务器只有2g内存是不是就不用试了</blockquote>
可以试一试，我也是2G阿里云，服务端起了并且玩了一阵子<img src="https://static.saraba1st.com/image/smiley/face2017/067.png" referrerpolicy="no-referrer">

*****

####  sakilin2013  
##### 19#       发表于 2024-1-22 15:39

谁知道我4核8G的能撑住8人一起玩么，<img src="https://static.saraba1st.com/image/smiley/face2017/010.png" referrerpolicy="no-referrer"> 是要定期重启？

[  -- 来自 能手机投票的 Stage1官方 Android客户端](https://www.coolapk.com/apk/140634)

*****

####  赤星ビスコ  
##### 20#       发表于 2024-1-22 15:40

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63733315&amp;ptid=2168983" target="_blank">今天你提了吗 发表于 2024-1-22 13:06</a>
 没公网ip，能不能图便宜买个最低档有公网ip的小鸡，反代家里电脑，不知道这么搞延迟怎么样 ...</blockquote>
我感觉不如直接买个反向代理的服务

*****

####  moeblack  
##### 21#         楼主| 发表于 2024-1-22 15:53

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63735050&amp;ptid=2168983" target="_blank">sakilin2013 发表于 2024-1-22 15:39</a>

谁知道我4核8G的能撑住8人一起玩么， 是要定期重启？

  -- 来自 能手机投票的 Stage1官方 Android ...</blockquote>
可以

不需要定时重启<img src="https://static.saraba1st.com/image/smiley/face2017/053.png" referrerpolicy="no-referrer">

linux swap设置成32G 然后swapiness设置成100

*****

####  MMIno  
##### 22#       发表于 2024-1-22 15:56

我问一下，在启用rcon的情况下，登录rcon的密码是啥？是adminpassword吗？

*****

####  tasuku  
##### 23#       发表于 2024-1-22 15:57

那么理论上nas上也可以架？

*****

####  moeblack  
##### 24#         楼主| 发表于 2024-1-22 16:06

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63735277&amp;ptid=2168983" target="_blank">MMIno 发表于 2024-1-22 15:56</a>

我问一下，在启用rcon的情况下，登录rcon的密码是啥？是adminpassword吗？</blockquote>
是的

*****

####  moeblack  
##### 25#         楼主| 发表于 2024-1-22 16:14

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63735292&amp;ptid=2168983" target="_blank">tasuku 发表于 2024-1-22 15:57</a>

那么理论上nas上也可以架？</blockquote>
可以，NAS可以用docker

让docker使用swap就能保证不崩溃

*****

####  zx09  
##### 26#       发表于 2024-1-22 16:36

我开了服务器 怎么改最大工会可以派驻帕鲁数量 默认是15 最大应该可以到20的 我不知道怎么改

*****

####  moeblack  
##### 27#         楼主| 发表于 2024-1-22 16:40

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63735776&amp;ptid=2168983" target="_blank">zx09 发表于 2024-1-22 16:36</a>
我开了服务器 怎么改最大工会可以派驻帕鲁数量 默认是15 最大应该可以到20的 我不知道怎么改 ...</blockquote>
有些设定是单纯的占位符，并不能修改以后才能改，这是官方服务器专门说了的事情

—— 来自 HUAWEI ALN-AL80, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.1.2

*****

####  鱼肉丸子  
##### 28#       发表于 2024-1-22 16:48

插眼，准备租服务器了

—— 来自 HUAWEI ALT-AL10, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.1.2

*****

####  非典型叶子  
##### 29#       发表于 2024-1-22 16:50

服务器到服务器的存档便宜没有主贴中贴的第三方教程里那么简单，仍有不小的失败可能性。建议非必要不迁移不重启云服务器，等待官方更新

—— 来自 [S1Fun](https://s1fun.koalcat.com)

*****

####  蒜苗  
##### 30#       发表于 2024-1-22 16:51

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63734231&amp;ptid=2168983" target="_blank">qianoooo 发表于 2024-1-22 14:32</a>
不支持 discord有人测过</blockquote>
sad，这就有点难受了


*****

####  干将莫邪  
##### 31#       发表于 2024-1-22 17:15

其实阿里云最便宜的那个2核4G都开的起来（新人优惠一次性机会，3个月30块钱），只是人多了的话就更快到缓存极限导致服务器端关掉。可以写个bat小脚本定时2小时自动重启一下服务端，楼上说的虚拟内存设置大了也许能延长时间。

*****

####  moeblack  
##### 32#         楼主| 发表于 2024-1-22 17:18

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63735978&amp;ptid=2168983" target="_blank">非典型叶子 发表于 2024-1-22 16:50</a>
服务器到服务器的存档便宜没有主贴中贴的第三方教程里那么简单，仍有不小的失败可能性。建议非必要不迁移不 ...</blockquote>
了解

—— 来自 HUAWEI ALN-AL80, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.1.2

*****

####  afer  
##### 33#       发表于 2024-1-22 17:27

<img src="https://static.saraba1st.com/image/smiley/face2017/037.png" referrerpolicy="no-referrer">问下局域网能开么，对，我就是想用蛤蟆吃。

*****

####  moeblack  
##### 34#         楼主| 发表于 2024-1-22 17:28

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63736417&amp;ptid=2168983" target="_blank">afer 发表于 2024-1-22 17:27</a>
问下局域网能开么，对，我就是想用蛤蟆吃。</blockquote>
可以，方法一样，推荐
tailscape

—— 来自 HUAWEI ALN-AL80, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.1.2

*****

####  afer  
##### 35#       发表于 2024-1-22 17:34

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63736434&amp;ptid=2168983" target="_blank">moeblack 发表于 2024-1-22 17:28</a>

可以，方法一样，推荐

tailscape</blockquote>
<img src="https://static.saraba1st.com/image/smiley/face2017/162.png" referrerpolicy="no-referrer">谢谢，公网ip这样就解决了，我考虑是用局域网加笔记本

*****

####  afer  
##### 36#       发表于 2024-1-22 20:01

再问下，现在有没有一般模式迁移到服务器成功的？另外主机之间存档能迁移么？

我现在主机的朋友因为电脑配置爆炸想要换主……<img src="https://static.saraba1st.com/image/smiley/face2017/067.png" referrerpolicy="no-referrer">

*****

####  HSJ1992  
##### 37#       发表于 2024-1-22 21:08

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63738067&amp;ptid=2168983" target="_blank">afer 发表于 2024-1-22 20:01</a>

再问下，现在有没有一般模式迁移到服务器成功的？另外主机之间存档能迁移么？

我现在主机的朋友因为电脑配 ...</blockquote>
单机模式存档迁移到服务器我尝试了一下，有装备没角色，角色会显示需要新建。

*****

####  MMIno  
##### 38#       发表于 2024-1-22 22:50

奇怪，为什么我打不开rconenable的开关？

*****

####  发光的球  
##### 39#       发表于 2024-1-23 00:49

[url=home.php?mod=space&amp;uid=118165]@Echo[/url] off SETLOCAL ENABLEDELAYEDEXPANSION  :: Define the paths to the executables SET "GameServerExecutable=PalServer-Win64-Test-Cmd.exe" SET "RestartServerPath=C:\Program Files\SteamCMD\steamapps\common\PalServer\PalServer.exe"  :: Set the interval for checking the server process (in seconds) SET /A checkInterval=120  :: Set the interval for restarting the server (in seconds) SET /A restartInterval=14400  :: Initialize the timer SET /A timer=0  :loop :: Check if it's time to restart the server IF !timer! GEQ %restartInterval% ( echo Time to restart the server. taskkill /F /IM "%GameServerExecutable%" timeout /t 3 /nobreak &gt; NUL SET /A timer=0 )  :: Check if the game server process is running tasklist /FO "csv" /FI "IMAGENAME eq %GameServerExecutable%" 2&gt;NUL | find /I /N "%GameServerExecutable%"&gt;NUL IF "%ERRORLEVEL%"=="1" ( echo %GameServerExecutable% is not running, starting PalServer.exe... start "" "%RestartServerPath%" SET /A timer=0 )  :: Wait for the specified check interval timeout /t %checkInterval% /nobreak &gt; NUL  :: Increment the timer SET /A timer+=checkInterval  :: Loop back GOTO loop复制代码用gpt帮忙写了个win下自动重启的脚本，现在是四小时重启一次，同时没两分钟检查服务端是否存在，不存在也会自动启动，记得要把RestartServerPath改成自己服务端exe的位置

然后存档备份看b站用的Cobian Backup 11 (Gravity)，感觉还行

不过网站上有个 普京是战犯，Z小鬼和脑残普粉滚粗 的小字

担心作者和n++一样魔怔的人可以再找个别的

*****

####  非典型叶子  
##### 40#       发表于 2024-1-23 02:36

 本帖最后由 非典型叶子 于 2024-1-23 02:38 编辑 

关于“一般模式迁移到服务器”的话题，社区已经有了一套完整的解决方案，比较复杂建议有一点程序能力的人来操作 <blockquote>How to's

For Local/Co-op Save to Server:

```

1  Create a dedicated server via SteamCMD

2  Run the server once

3  Login to the server so it creates a player folder and .sav file.

    - Mine looked like "EE256A5000000000000000000000000.sav" this is what you later need for the script. (without the .sav)

4  Stop the server

5  Make sure to backup everything just in case.

6  Copy your contents of your folder from C:\Users\domin\AppData\Local\Pal\Saved\SaveGames\Your Steam ID\BUNCH OF LETTERS AND NUMBERS\

7  Make sure to have the lastest version of Python installed, download the script from Nul and the UEsave Executable.

8  Run the cmd with the correct parameters. 

    - "python fix-host-save.py C:\Folder\uesave.exe C:\Palworld\Pal\Saved\SaveGames\0\BunchOfLetterAndNumbers" "the file name that has been made from joining it once "

        = For example for me "python fix-host-save.py F:\Fixit\uesave.exe F:\Palworld\Server_1\Pal\Saved\SaveGames\0\8A15EB32440279628FB4587AF7718787 EE256A5000000000000000000000000"

9  Wait a bit, it can take some time. 

10 Copy all the files and folder over and overwrite the files. 

11 Start the server

12 Voila in theory you should be good to go.

```

Extra info for if you are using a **/Cloud/Game Host:

```

-  Run your fresh server

-  Login to the server so it creates a player foler and .sav file. 

-  Stop your Server

-  FTP into your server and find the savegame directory (In this folder has all your save data)

-  Download the files on your own pc, so that you can run your script since this isnt possible with the host provider. 

    = You can also make it a bit more nicer by making a folder for the sav files. 

-  Now you can follow the rest of the stuff from #7 mentioned above. 

-  Once the script is done you can upload the files back to the server and you should be good to go. 

```

Links: 

Nuls script: [https://github.com/xNul/palworld-host-save-fix](https://github.com/xNul/palworld-host-save-fix)

UESave Extension: [https://github.com/trumank/uesave-rs](https://github.com/trumank/uesave-rs)

Python Download: [https://www.python.org/downloads/](https://www.python.org/downloads/)

Extra Options,  if you want to manually convert the files from sav to json and vice versa these script can help you.
[https://gist.github.com/cheahjs/300239464dd84fe6902893b6b9250fd0](https://gist.github.com/cheahjs/300239464dd84fe6902893b6b9250fd0)

Extra General info: [https://gist.github.com/Toakan/3 ... erver-community-faq](https://gist.github.com/Toakan/3c78a577c21a21fcc5fa917f3021d70e#palworld-server-community-faq)

Alternate option: [https://www.reddit.com/r/Palworl ... ile_incl/?rdt=55658](https://www.reddit.com/r/Palworld/comments/19cb8su/complete_guide_to_transfer_a_coop_save_file_incl/?rdt=55658)</blockquote>
来源：官方discord频道，在多位大佬的共同努力下完成

Append:

加入官方discord
[https://discord.gg/pocketpair](https://discord.gg/pocketpair)

可以在此Thread中翻阅讨论内容进一步学习
[https://discord.com/channels/505 ... 1198474488426279054](https://discord.com/channels/505994577942151180/1198474488426279054)

*****

####  非典型叶子  
##### 41#       发表于 2024-1-23 02:39

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63738067&amp;ptid=2168983" target="_blank">afer 发表于 2024-1-22 20:01</a>

再问下，现在有没有一般模式迁移到服务器成功的？另外主机之间存档能迁移么？

我现在主机的朋友因为电脑配 ...</blockquote>
如有需要请参阅上述内容

﹍﹍﹍

评分

 参与人数 1战斗力 +2

|昵称|战斗力|理由|
|----|---|---|
| afer| + 2|感谢|

查看全部评分

*****

####  bypass  
##### 42#       发表于 2024-1-23 08:41

 本帖最后由 bypass 于 2024-1-23 08:43 编辑 

我 8C16T / 64G 的 Home Server + 吃灰两年的腾讯云北京节点在此时发挥了作用。

然而拉不到朋友和我玩，一个人寂寞地抓帕鲁 <img src="https://static.saraba1st.com/image/smiley/face2017/148.png" referrerpolicy="no-referrer">

*****

####  MMIno  
##### 43#       发表于 2024-1-23 08:51

我问一下，我修改了bEnableInvaderEnemy=False和RCONEnabled=True的值，但是在重启之后，这两个的值被还原了，是什么情况

*****

####  蒜苗  
##### 44#       发表于 2024-1-23 09:10

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63740851&amp;ptid=2168983" target="_blank">非典型叶子 发表于 2024-1-23 02:36</a>
关于“一般模式迁移到服务器”的话题，社区已经有了一套完整的解决方案，比较复杂建议有一点程序能力的人来 ...</blockquote>
这个现在还会导致角色等级归零吗？

*****

####  moeblack  
##### 45#         楼主| 发表于 2024-1-23 09:12

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63741460&amp;ptid=2168983" target="_blank">MMIno 发表于 2024-1-23 08:51</a>
我问一下，我修改了bEnableInvaderEnemy=False和RCONEnabled=True的值，但是在重启之后，这两个的值被还原 ...</blockquote>
要关闭之后再修改，修改完之后再启动

—— 来自 HUAWEI ALN-AL80, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.1.2

*****

####  Sissii  
##### 46#       发表于 2024-1-23 09:14

地图上面的野怪，除了改倍率还有什么办法能加快刷新，群里有个小伙伴一直在叫没怪打

*****

####  MMIno  
##### 47#       发表于 2024-1-23 09:35

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63741651&amp;ptid=2168983" target="_blank">moeblack 发表于 2024-1-23 09:12</a>

要关闭之后再修改，修改完之后再启动

—— 来自 HUAWEI ALN-AL80, Android 12上的 S1Next-鹅版 v2.1.2 ...</blockquote>
好了，感谢

*****

####  蒜苗  
##### 48#       发表于 2024-1-23 10:10

自己拿笔记本开了个服务器试了一下，确实不支持IPv6，局域网的都不行<img src="https://static.saraba1st.com/image/smiley/face2017/068.png" referrerpolicy="no-referrer">

看来只能想办法开反代或者云服务器了

*****

####  非典型叶子  
##### 49#       发表于 2024-1-23 10:45

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63741633&amp;ptid=2168983" target="_blank">蒜苗 发表于 2024-1-23 09:10</a>
这个现在还会导致角色等级归零吗？</blockquote>
上述流程就是用来解决角色数据的迁移问题的

[论坛助手,iPhone](https://bbs.saraba1st.com/2b/forum.php?mod=viewthread&amp;tid=2029836)

*****

####  Geyorkias  
##### 50#       发表于 2024-1-23 10:45

我用家里的闲置PC开了一个服务器给群友玩，我自己连服务器的时候可以走内网IP直连么？

*****

####  ds006425  
##### 51#       发表于 2024-1-23 11:08

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63742860&amp;ptid=2168983" target="_blank">Geyorkias 发表于 2024-1-23 10:45</a>

我用家里的闲置PC开了一个服务器给群友玩，我自己连服务器的时候可以走内网IP直连么？ ...</blockquote>
可以，直接连127.0.0.1就行。可以先试试看自己开服务器卡不卡。

昨天我自己搞了个内网穿透给群友玩，群友都说卡卡的

*****

####  sunxpw  
##### 52#       发表于 2024-1-23 11:22

 本帖最后由 sunxpw 于 2024-1-23 11:32 编辑 

问个问题，有关于坏档修复。

就是有人在服务器里出现坏档，黑屏loading进不来，怎么确定players文件夹里的sav文件是对应的谁呢？我看了一下文件名似乎都是十六进制，翻译成十进制以后看起来也没什么规律？---------------------------------------------------------

---------------------------------------------------------

另外我写了个简单的批处理文件来备份帕鲁的存档，自动压缩成当前日期时间为名的rar文件。

最后一行开始的文件路径是调用winrar，填入winrar的运行文件位置，第二个文件路径是存档备份的位置，默认是D:\palsave\内，第三个文件路径是存档位置，根据你实际情况调整。

保存成bat格式的文件，在windows任务计划程序里设置成每小时运行一次就行

@echo off

set "Hour=%time:~0,2%"

set "Minute=%time:~3,2%"

set "Second=%time:~6,2%"

REM 去除可能的前导空格

set "Hour=%Hour: =0%"

set "Minute=%Minute: =0%"

set "Second=%Second: =0%"

REM 整合时间

set Ymd=%date:~,4%%date:~5,2%%date:~8,2%_%Hour%%Minute%%Second%

REM 调用winrar压缩备份

"C:\Program Files\WinRAR\WinRAR.exe" a -ibck -m4 D:\palsave\%Ymd%.rar C:\PROGRA~2\Steam\steamapps\common\PalServer\Pal\Saved

*****

####  upright  
##### 53#       发表于 2024-1-23 11:22

补充个帕鲁服务器信息，我看没人提到，我自己一下午发现处理的case。就是存档迁移后，如果正常开服后1分钟就崩溃，是由于跨服务器或者root权限的问题，需要chmod -R 777存档目录(0/xxxx)即可解决。

*****

####  Gundamslave  
##### 54#       发表于 2024-1-23 11:28

把steam最高层的文件夹777就行了，不这样我也复制不过去。

*****

####  Geyorkias  
##### 55#       发表于 2024-1-23 11:34

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63743205&amp;ptid=2168983" target="_blank">ds006425 发表于 2024-1-23 11:08</a>

可以，直接连127.0.0.1就行。可以先试试看自己开服务器卡不卡。

昨天我自己搞了个内网穿透给群友玩，群友 ...</blockquote>
感谢，我昨天开了几个小时群友表示都还行，基本60ms延迟这样

不过我用的付费的frp

*****

####  moeblack  
##### 56#         楼主| 发表于 2024-1-23 11:37

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63743421&amp;ptid=2168983" target="_blank">sunxpw 发表于 2024-1-23 11:22</a>

问个问题，有关于坏档修复。

就是有人在服务器里出现坏档，黑屏loading进不来，怎么确定players文件夹里的s ...</blockquote>
我正好遇到过这个事情

HEX名字实际上是游戏内PID的16进制版本。

所以在游戏内知道玩家PID之后就可以找到对应的HEX文件名了。
 <blockquote>RCON后台

ShowPlayers

查看游戏内玩家 ID, PID, STEAM ID</blockquote>

我是记下来了玩家的PID所以找到了。

还有一个方法是用过文件最后修改时间来找.sav文件。

两个方法都可以用。

*****

####  sunxpw  
##### 57#       发表于 2024-1-23 11:42

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63743653&amp;ptid=2168983" target="_blank">moeblack 发表于 2024-1-23 11:37</a>

我正好遇到过这个事情

HEX名字实际上是游戏内PID的16进制版本。

所以在游戏内知道玩家PID之后就可以找到 ...</blockquote>
非常感谢！

*****

####  蒜苗  
##### 58#       发表于 2024-1-23 12:07

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63743205&amp;ptid=2168983" target="_blank">ds006425 发表于 2024-1-23 11:08</a>
可以，直接连127.0.0.1就行。可以先试试看自己开服务器卡不卡。

昨天我自己搞了个内网穿透给群友玩，群友 ...</blockquote>
他是闲置PC，不是本机，不能用127，要用192.168

*****

####  蒜苗  
##### 59#       发表于 2024-1-23 12:08

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63742860&amp;ptid=2168983" target="_blank">Geyorkias 发表于 2024-1-23 10:45</a>
我用家里的闲置PC开了一个服务器给群友玩，我自己连服务器的时候可以走内网IP直连么？ ...</blockquote>
自己连直接内网IP就行，不然你绕出去一圈再回来延迟还高了

*****

####  diohanmilton  
##### 60#       发表于 2024-1-23 12:17

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63732822&amp;ptid=2168983" target="_blank">Litccc 发表于 2024-1-22 12:19</a>
可惜不支持arm的服务器，不然甲骨文薅的服务器就能排上用场了</blockquote>
你怎么开到甲骨文的四核arm的？

—— 来自 HONOR PGT-AN10, Android 13上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.5.4


*****

####  Litccc  
##### 61#       发表于 2024-1-23 13:33

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63744133&amp;ptid=2168983" target="_blank">diohanmilton 发表于 2024-1-23 12:17</a>

你怎么开到甲骨文的四核arm的？

—— 来自 HONOR PGT-AN10, Android 13上的 S1Next-鹅版 v2.5.4 ...</blockquote>
很早之前开的，现在热门地区除非升级号应该都没有配额了


*****

####  diohanmilton  
##### 62#       发表于 2024-1-23 13:53

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63744873&amp;ptid=2168983" target="_blank">Litccc 发表于 2024-1-23 13:33</a>
很早之前开的，现在热门地区除非升级号应该都没有配额了</blockquote>
现在免费的只有amd 1核用了，不知道哪个区还能开四核arm。
1核amd性能太低了，上次开了个为知笔记的docker把服务器卡死了，ssh进不去只能删了服务器重建。

—— 来自 HONOR PGT-AN10, Android 13上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.5.4


*****

####  woid1  
##### 63#       发表于 2024-1-23 18:06

我简直傻逼了,..刚刚搭服务器,  结果启动后用ss -nltp查端口 8211一直没有....以为没起来,查了我一个小时...结果突然发现这端口是udp的..

*****

####  Mikumiku831  
##### 64#       发表于 2024-1-23 18:12

炸内存这个写个systemd服务每天定时重启服务端并清理系统缓存是否可行 还是一定要重启服务器？


*****

####  qianoooo  
##### 65#       发表于 2024-1-23 18:24

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63748687&amp;ptid=2168983" target="_blank">Mikumiku831 发表于 2024-1-23 18:12</a>
炸内存这个写个systemd服务每天定时重启服务端并清理系统缓存是否可行 还是一定要重启服务器？ ...</blockquote>
一定要重启服务器端

—— 来自 samsung SM-S9180, Android 14上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.5.2-play

*****

####  DRAGONBLEAPIECE  
##### 66#       发表于 2024-1-23 18:34

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63730332&amp;ptid=2168983" target="_blank">moeblack 发表于 2024-1-22 09:20</a>

有问题直接回帖问我，看到了就回答。</blockquote>
请问按目前经验
10人左右一起玩的话，服务器配置多少才够？谢谢


*****

####  DRAGONBLEAPIECE  
##### 67#       发表于 2024-1-23 18:42

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63743653&amp;ptid=2168983" target="_blank">moeblack 发表于 2024-1-23 11:37</a>
我正好遇到过这个事情

HEX名字实际上是游戏内PID的16进制版本。

所以在游戏内知道玩家PID之后就可以找到 ...</blockquote>
所以请问可以跨服务器且跨世界的移植某个角色存档吗？


*****

####  moeblack  
##### 68#         楼主| 发表于 2024-1-23 19:04

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63748981&amp;ptid=2168983" target="_blank">DRAGONBLEAPIECE 发表于 2024-1-23 18:34</a>
请问按目前经验
10人左右一起玩的话，服务器配置多少才够？谢谢</blockquote>
32G内存吧

我就是16G内存炸了换了64

—— 来自 HUAWEI ALN-AL80, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.1.2

*****

####  moeblack  
##### 69#         楼主| 发表于 2024-1-23 19:05

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63749104&amp;ptid=2168983" target="_blank">DRAGONBLEAPIECE 发表于 2024-1-23 18:42</a>
所以请问可以跨服务器且跨世界的移植某个角色存档吗？</blockquote>
用那个python脚本就能进行存档迁移

—— 来自 HUAWEI ALN-AL80, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.1.2


*****

####  HSJ1992  
##### 70#       发表于 2024-1-23 22:00

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63749366&amp;ptid=2168983" target="_blank">moeblack 发表于 2024-1-23 19:05</a>

用那个python脚本就能进行存档迁移

—— 来自 HUAWEI ALN-AL80, Android 12上的 S1Next-鹅版 v2.1.2 ...</blockquote>
邀请码的P2P联机存档，转LXC 的linux docker服务器，地图能成功，角色数据不行。

不知道接下去咋搞了。。。


*****

####  moeblack  
##### 71#         楼主| 发表于 2024-1-23 23:48

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63751261&amp;ptid=2168983" target="_blank">HSJ1992 发表于 2024-1-23 22:00</a>

邀请码的P2P联机存档，转LXC 的linux docker服务器，地图能成功，角色数据不行。

不知道接下去咋搞了。。 ...</blockquote>
bilibili的视频

[https://www.bilibili.com/video/B ... 28d247272fd4347d79f](https://www.bilibili.com/video/BV1UW4y1F7Vn/?vd_source=cb9821ce4e92428d247272fd4347d79f)

*****

####  Litccc  
##### 72#       发表于 2024-1-23 23:53

arm服务器可以直接拉这个docker镜像：[https://hub.docker.com/r/czy0612/palworld-server](https://hub.docker.com/r/czy0612/palworld-server)

已经集成好server，手动改下配置就可以运行了<img src="https://static.saraba1st.com/image/smiley/face2017/035.png" referrerpolicy="no-referrer">


*****

####  HSJ1992  
##### 73#       发表于 2024-1-24 00:11

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63752568&amp;ptid=2168983" target="_blank">moeblack 发表于 2024-1-23 23:48</a>

bilibili的视频

https://www.bilibili.com/video/BV1UW4y1F7Vn/?vd_source=cb9821ce4e92428d247272fd434 ...</blockquote>
就是按照视频操作的。无效。

是否因为视频里它是用windows版的steamcmd执行的，后面实际使用的服务端也是windows版的服务端，而我是linux版？


*****

####  iccccccccc  
##### 74#       发表于 2024-1-24 06:35

 本帖最后由 iccccccccc 于 2024-1-24 06:42 编辑 
<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63752845&amp;ptid=2168983" target="_blank">HSJ1992 发表于 2024-1-24 00:11</a>

就是按照视频操作的。无效。

是否因为视频里它是用windows版的steamcmd执行的，后面实际使用的服务端也是 ...</blockquote>
[https://tieba.baidu.com/p/8872696062?pid=149664251887&amp;cid=0#149664251887](https://tieba.baidu.com/p/8872696062?pid=149664251887&amp;cid=0#149664251887)

🐟老汉的回复

（作好备份）

他的意思是你登录 steam 后，从 steam 运行服务器。这时候steam会修改你的 saved 文件夹（转而使用 steam账号 加密存档）。就能转移存档了，转移后需要在新的服务器也要安装 steam，还原你的备份，首次通过 steam 运行服务器（可能是多此一举），以后可以直接运行 PalServer，无需登录steam。


*****

####  天地不仁  
##### 75#       发表于 2024-1-24 10:13

问怎么查看自己和朋友开主机联机的延迟，朋友说有点卡和闪回

—— 来自 vivo V2218A, Android 13上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.5.4


*****

####  woblitent  
##### 76#       发表于 2024-1-24 10:32

服务端从一台电脑迁移到另一台电脑，整个saved文件夹复制过去之后，世界还在，但所有玩家都得重建角色该怎么解决，只能一个个对照新老玩家id，手动改玩家存档名字吗<img src="https://static.saraba1st.com/image/smiley/face2017/001.png" referrerpolicy="no-referrer">

—— 来自 Sony XQ-AT52, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.5.2-play


*****

####  moeblack  
##### 77#         楼主| 发表于 2024-1-24 10:35

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63755261&amp;ptid=2168983" target="_blank">天地不仁 发表于 2024-1-24 10:13</a>

请问怎么查看自己和朋友开主机联机的延迟，朋友说有点卡和闪回

—— 来自 vivo V2218A, Android 13上的 S1 ...</blockquote>
朋友esc看RTT，RTT在100以下都没什么闪回

*****

####  万里小路さん  
##### 78#       发表于 2024-1-24 10:36

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63755511&amp;ptid=2168983" target="_blank">woblitent 发表于 2024-1-24 10:32</a>
服务端从一台电脑迁移到另一台电脑，整个saved文件夹复制过去之后，世界还在，但所有玩家都得重建角色该怎 ...</blockquote>
事实上同一台电脑不同用户启动服务器也会这样，不清楚是只跟用户名挂钩还是别的

*****

####  moeblack  
##### 79#         楼主| 发表于 2024-1-24 10:43

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63755511&amp;ptid=2168983" target="_blank">woblitent 发表于 2024-1-24 10:32</a>

服务端从一台电脑迁移到另一台电脑，整个saved文件夹复制过去之后，世界还在，但所有玩家都得重建角色该怎 ...</blockquote>
[https://github.com/xNul/palworld-host-save-fix?tab=readme-ov-file](https://github.com/xNul/palworld-host-save-fix?tab=readme-ov-file)

Github更新了，照着做


*****

####  zero33333  
##### 80#       发表于 2024-1-24 10:46

有无组织啊，我想和人一起玩服务器版


*****

####  HSJ1992  
##### 81#       发表于 2024-1-24 11:02

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63753625&amp;ptid=2168983" target="_blank">iccccccccc 发表于 2024-1-24 06:35</a>
https://tieba.baidu.com/p/8872696062?pid=149664251887&amp;cid=0#149664251887

🐟老汉的回复</blockquote>
我跟视频教程步骤不同的是没本地运行windows版steamcmd服务器端，而是直接用实际linux服务器上的docker服务器端。

我如果想迁移邀请码联机的存档，是要让房主装windows版服务端按视频执行，然后后面的问题就是windows服务端存档如何迁移到linux服务端？


*****

####  iccccccccc  
##### 82#       发表于 2024-1-24 12:34

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63755942&amp;ptid=2168983" target="_blank">HSJ1992 发表于 2024-1-24 11:02</a>

已编辑。

看了新更新的github教程，知道什么问题了。</blockquote>
额，我搞到早上才弄好，找最后一层楼回复的没细看。sorry


*****

####  匿名用户  
##### 83#       发表于 2024-1-24 16:41

咨询一下独立服务器迁间迁移，需要转换存档吗？还是只需要复制 \PalServer\Pal\Saved 里的内容就行？


*****

####  moeblack  
##### 84#         楼主| 发表于 2024-1-24 19:16

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63760131&amp;ptid=2168983" target="_blank">匿名用户 发表于 2024-1-24 16:41</a>

咨询一下独立服务器迁间迁移，需要转换存档吗？还是只需要复制 \PalServer\Pal\Saved 里的内容就行？ ...</blockquote>
都要，参考github帖子，实在不行私信我吧


*****

####  蒜苗  
##### 85#       发表于 2024-1-25 11:46

自建服务器难度有办法调整吗？difficulty那里改设置不起作用啊


*****

####  HSJ1992  
##### 86#       发表于 2024-1-25 17:48

好难啊。。。我连自己尝试新建多人存档然后迁移到当前电脑的windows服务端都一直失败，最后总是要我新建角色。

视频教程里一切顺利，都不知道是哪里出了问题。[https://www.bilibili.com/video/BV18c411x7tq/?p=1&amp;t=19](https://www.bilibili.com/video/BV18c411x7tq/?p=1&amp;t=19)


*****

####  Mikumiku831  
##### 87#       发表于 2024-1-25 18:41

<img src="https://img.saraba1st.com/forum/202401/25/184116ctfebnbeeevtfck8.png" referrerpolicy="no-referrer">

<strong>QQ图片20240125184055.png</strong> (38.73 KB, 下载次数: 0)

下载附件

2024-1-25 18:41 上传

弄了个Linux一键部署+配置修改 等研究完存档迁移再整一个 


*****

####  ahztb  
##### 88#       发表于 2024-1-25 19:24

为什么朋友发邀请码我加他的游戏玩都非常卡
在想是不是去弄个服务器来玩了


*****

####  Gundamslave  
##### 89#       发表于 2024-1-25 21:41

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63774075&amp;ptid=2168983" target="_blank">Mikumiku831 发表于 2024-1-25 18:41</a>
弄了个Linux一键部署+配置修改 等研究完存档迁移再整一个</blockquote>
可以docker吗


*****

####  匿名用户  
##### 90#       发表于 2024-1-26 00:06

5个人，16G 物理内存玩一晚上有几率会爆一次。

设虚拟内存+定时清理内存可以有改善作用吗？


*****

####  moeblack  
##### 91#         楼主| 发表于 2024-1-26 07:22

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63777789&amp;ptid=2168983" target="_blank">匿名用户 发表于 2024-1-26 00:06</a>
5个人，16G 物理内存玩一晚上有几率会爆一次。

设虚拟内存+定时清理内存可以有改善作用吗？ ...</blockquote>
可以
比如6小时关机一次
虚拟内存设置成能多大多大

swap和虚拟内存不是一个东西，但是可以这么理解

—— 来自 HUAWEI ALN-AL80, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.1.2

*****

####  sunzhenfeinan  
##### 92#       发表于 2024-1-26 07:27

steam为什么比学习版帧数低那么多？3060ti都没30帧，什么原因

*****

####  moeblack  
##### 93#         楼主| 发表于 2024-1-26 07:28

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63779470&amp;ptid=2168983" target="_blank">sunzhenfeinan 发表于 2024-1-26 07:27</a>
steam为什么比学习版帧数低那么多？3060ti都没30帧，什么原因</blockquote>
内存炸了进虚拟内存了应该

—— 来自 HUAWEI ALN-AL80, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.1.2

*****

####  sunzhenfeinan  
##### 94#       发表于 2024-1-26 07:30

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63779471&amp;ptid=2168983" target="_blank">moeblack 发表于 2024-1-26 07:28</a>

内存炸了进虚拟内存了应该

—— 来自 HUAWEI ALN-AL80, Android 12上的 S1Next-鹅版 v2.1.2 ...</blockquote>
请问要怎么做？

*****

####  sunzhenfeinan  
##### 95#       发表于 2024-1-26 07:32

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63779471&amp;ptid=2168983" target="_blank">moeblack 发表于 2024-1-26 07:28</a>

内存炸了进虚拟内存了应该

—— 来自 HUAWEI ALN-AL80, Android 12上的 S1Next-鹅版 v2.1.2 ...</blockquote>
为什么学习版不会这样


*****

####  moeblack  
##### 96#         楼主| 发表于 2024-1-26 07:36

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63779481&amp;ptid=2168983" target="_blank">sunzhenfeinan 发表于 2024-1-26 07:32</a>
为什么学习版不会这样</blockquote>
重启游戏就不炸了吧。
配置设置呢

—— 来自 HUAWEI ALN-AL80, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.1.2

*****

####  sunzhenfeinan  
##### 97#       发表于 2024-1-26 07:37

重启了也没用，关键同样设置学习版就很流畅

360截图20240126073629811.jpg
(37.3 KB, 下载次数: 0)

下载附件

2024-1-26 07:37 上传

<img src="https://img.saraba1st.com/forum/202401/26/073743aq7qut7dr59li2xx.jpg" referrerpolicy="no-referrer">

360截图20240126073709541.jpg
(126.42 KB, 下载次数: 0)

下载附件

2024-1-26 07:37 上传

<img src="https://img.saraba1st.com/forum/202401/26/073743dovzc0u0n7jm96uf.jpg" referrerpolicy="no-referrer">

*****

####  sunzhenfeinan  
##### 98#       发表于 2024-1-26 07:38

就是我现在很卡，但是退出直接玩学习版就很流畅，而且设置一样，不理解

*****

####  sunzhenfeinan  
##### 99#       发表于 2024-1-26 07:41

学习版设置，就是想不麻烦以后更新才买的，本来是xgp画质太差。

不太会捣鼓配置

360截图20240126074005671.jpg
(139.64 KB, 下载次数: 0)

下载附件

2024-1-26 07:41 上传

<img src="https://img.saraba1st.com/forum/202401/26/074100isjz2lkm9jjyysj7.jpg" referrerpolicy="no-referrer">


*****

####  moeblack  
##### 100#         楼主| 发表于 2024-1-26 07:44

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63779500&amp;ptid=2168983" target="_blank">sunzhenfeinan 发表于 2024-1-26 07:41</a>
学习版设置，就是想不麻烦以后更新才买的，本来是xgp画质太差。

不太会捣鼓配置 ...</blockquote>
要不你把视距拉倒中吧，我5800X+4090都不敢开最高……

—— 来自 HUAWEI ALN-AL80, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.1.2

*****

####  sunzhenfeinan  
##### 101#       发表于 2024-1-26 07:45

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63779506&amp;ptid=2168983" target="_blank">moeblack 发表于 2024-1-26 07:44</a>

要不你把视距拉倒中吧，我5800X+4090都不敢开最高……

—— 来自 HUAWEI ALN-AL80, Android 12上的 S1Ne ...</blockquote>
我奇怪地是同一台电脑，同样设置，学习版帧数高太多，是不是steam服务器还是什么问题

*****

####  moeblack  
##### 102#         楼主| 发表于 2024-1-26 07:46

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63779508&amp;ptid=2168983" target="_blank">sunzhenfeinan 发表于 2024-1-26 07:45</a>
我奇怪地是同一台电脑，同样设置，学习版帧数高太多，是不是steam服务器还是什么问题 ...</blockquote>
学习版谁知道调了什么……

—— 来自 HUAWEI ALN-AL80, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.1.2

*****

####  sunzhenfeinan  
##### 103#       发表于 2024-1-26 07:47

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63779519&amp;ptid=2168983" target="_blank">moeblack 发表于 2024-1-26 07:46</a>

学习版谁知道调了什么……

—— 来自 HUAWEI ALN-AL80, Android 12上的 S1Next-鹅版 v2.1.2 ...</blockquote>
<img src="https://static.saraba1st.com/image/smiley/face2017/001.png" referrerpolicy="no-referrer">但是观感很好，设置一样，我这个调最低画质帧数都很低，我觉得是平台问题

*****

####  sunzhenfeinan  
##### 104#       发表于 2024-1-26 07:52

<img src="https://img.saraba1st.com/forum/202401/26/075237tkwc0qprphygw9u9.jpg" referrerpolicy="no-referrer">

<strong>360截图20240126075208320.jpg</strong> (137.38 KB, 下载次数: 0)

下载附件

2024-1-26 07:52 上传

这样还是只有10几帧


*****

####  moeblack  
##### 105#         楼主| 发表于 2024-1-26 07:57

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63779533&amp;ptid=2168983" target="_blank">sunzhenfeinan 发表于 2024-1-26 07:52</a>
这样还是只有10几帧</blockquote>
优质答案

我不知道。

—— 来自 HUAWEI ALN-AL80, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.1.2


*****

####  fat  
##### 106#       发表于 2024-1-26 08:04

有人试过用有公网ip的家里pc搭建成功吗？我还是没搞成不知道是不是端口转发有问题


*****

####  moeblack  
##### 107#         楼主| 发表于 2024-1-26 09:13

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63779576&amp;ptid=2168983" target="_blank">fat 发表于 2024-1-26 08:04</a>
有人试过用有公网ip的家里pc搭建成功吗？我还是没搞成不知道是不是端口转发有问题 ...</blockquote>
我就是
openwrt后台开转发，然后先用telnet手机网络看能否通端口
成功之后关闭telnet开服务器

—— 来自 HUAWEI ALN-AL80, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.1.2


*****

####  蒜苗  
##### 108#       发表于 2024-1-27 01:40

今天出了非官方的服务端优化版，楼主有尝试吗


*****

####  moeblack  
##### 109#         楼主| 发表于 2024-1-27 12:21

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63791119&amp;ptid=2168983" target="_blank">蒜苗 发表于 2024-1-27 01:40</a>

今天出了非官方的服务端优化版，楼主有尝试吗</blockquote>
bilibili我发了视频了（）


*****

####  蒜苗  
##### 110#       发表于 2024-1-27 21:01

听说今天的更新优化了内存泄露问题？


*****

####  moeblack  
##### 111#         楼主| 发表于 2024-1-28 07:57

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63798363&amp;ptid=2168983" target="_blank">蒜苗 发表于 2024-1-27 21:01</a>
听说今天的更新优化了内存泄露问题？</blockquote>
修复了应该

—— 来自 HUAWEI ALN-AL80, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.1.2


*****

####  雨中曲  
##### 112#       发表于 2024-1-28 08:09

这菜鸡公司每次更新，都得重新下本体，卧槽里的<img src="https://static.saraba1st.com/image/smiley/face2017/001.png" referrerpolicy="no-referrer">


*****

####  chaoswing  
##### 113#       发表于 2024-1-28 09:02

两个人玩，4g的nas能带动吗


*****

####  蒜苗  
##### 114#       发表于 2024-1-28 10:29

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63801829&amp;ptid=2168983" target="_blank">chaoswing 发表于 2024-1-28 09:02</a>
两个人玩，4g的nas能带动吗</blockquote>
两个人应该可以，就是下地下城可能会爆内存


*****

####  moeblack  
##### 115#         楼主| 发表于 2024-1-28 13:55

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63801829&amp;ptid=2168983" target="_blank">chaoswing 发表于 2024-1-28 09:02</a>

两个人玩，4g的nas能带动吗</blockquote>
2个人玩可以用邀请码开房！

*****

####  moeblack  
##### 116#         楼主| 发表于 2024-1-28 13:56

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63801627&amp;ptid=2168983" target="_blank">雨中曲 发表于 2024-1-28 08:09</a>

这菜鸡公司每次更新，都得重新下本体，卧槽里的</blockquote>
为什么？不是steam直接修补吗


*****

####  Mikumiku831  
##### 117#       发表于 2024-1-29 10:14

有啥方法知道服务端更新了没 想弄个计划任务自动更新

*****

####  moeblack  
##### 118#         楼主| 发表于 2024-1-29 10:16

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63812866&amp;ptid=2168983" target="_blank">Mikumiku831 发表于 2024-1-29 10:14</a>
有啥方法知道服务端更新了没 想弄个计划任务自动更新</blockquote>
启动的时候把你安装服务器使用的命令加在批处理文件里

—— 来自 HUAWEI ALN-AL80, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.1.2


*****

####  qianoooo  
##### 119#       发表于 2024-1-29 11:49

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63812866&amp;ptid=2168983" target="_blank">Mikumiku831 发表于 2024-1-29 10:14</a>
有啥方法知道服务端更新了没 想弄个计划任务自动更新</blockquote>
看steamdb

—— 来自 samsung SM-S9180, Android 14上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.5.2-play


*****

####  Lipshcitsbound  
##### 120#       发表于 2024-1-29 18:33

请问下我用腾讯云搭的服务器，昨晚服务器端莫名崩溃，今天起来发现档变成了两三天前的档（但是这两天解锁的科技还在），这种情况可能是什么原因呢或者说还有救吗<img src="https://static.saraba1st.com/image/smiley/face2017/117.png" referrerpolicy="no-referrer">


*****

####  moeblack  
##### 121#         楼主| 发表于 2024-1-29 19:10

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63819285&amp;ptid=2168983" target="_blank">Lipshcitsbound 发表于 2024-1-29 18:33</a>
请问下我用腾讯云搭的服务器，昨晚服务器端莫名崩溃，今天起来发现档变成了两三天前的档（但是这两天解锁的 ...</blockquote>
没救了，腾讯云超开太多，服务器压力太大崩溃。
给你自动回档到上一个快照了。

—— 来自 HUAWEI ALN-AL80, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.1.2


*****

####  哈迪斯兜帽  
##### 122#       发表于 2024-1-29 20:58

房间转windows服务端
我只替换了自己单机的存档，然后自己替换了单机的地图。
但是之前一起玩的伙计进来就有数据，他说帕鲁也都在，虽然是一个公会的，总不能房间主机也存了会员的数据吧。
等等另一个成员也来了我再问问他。

—— 来自 samsung SM-G9980, Android 13上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.1.2


*****

####  哈迪斯兜帽  
##### 123#       发表于 2024-1-29 21:04

我自己2700x+rx480，自己都跑不到60帧

但是我有公网IP，现在开着服务器自己设置选全低，看看到底能带几个人。<img src="https://static.saraba1st.com/image/smiley/face2017/067.png" referrerpolicy="no-referrer">


*****

####  moeblack  
##### 124#         楼主| 发表于 2024-1-30 07:02

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63820711&amp;ptid=2168983" target="_blank">哈迪斯兜帽 发表于 2024-1-29 20:58</a>
房间转windows服务端

我只替换了自己单机的存档，然后自己替换了单机的地图。

但是之前一起玩的伙计进来就 ...</blockquote>
本来就只需要转换主机的，不需要转换两个好友的存档数据……

Git hub上面有一个那个逆向帕鲁的项目，你可以去看一下，所有人物的存档数据全部在你的地图数据里面！……

—— 来自 HUAWEI ALN-AL80, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.1.2

*****

####  moeblack  
##### 125#         楼主| 发表于 2024-1-30 07:03

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63820803&amp;ptid=2168983" target="_blank">哈迪斯兜帽 发表于 2024-1-29 21:04</a>
我自己2700x+rx480，自己都跑不到60帧

但是我有公网IP，现在开着服务器自己设置选全低，看看到底能带几个人 ...</blockquote>
10个人

—— 来自 HUAWEI ALN-AL80, Android 12上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.1.2


*****

####  狂马王  
##### 126#       发表于 2024-1-30 19:43

请教下怎么修改服务器基地数量和工作帕鲁数量？

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Sayuki1025  
##### 127#       发表于 2024-1-31 12:16

<img src="https://static.saraba1st.com/image/smiley/face2017/018.png" referrerpolicy="no-referrer">大厂哪家服务器最便宜呢

