
*****

####  Machinery  
##### 908#       发表于 2023-10-24 16:03

FreeNoise

通过噪声重新调度实现免调整的更长的视频扩散生成

项目主页:http://haonanqiu.com/projects/FreeNoise.html

github项目主页:https://github.com/arthur-qiu/LongerCrafter

随着大规模视频数据集的可用性和扩散模型的进步，文本驱动的视频生成取得了实质性重大进展，然而，现有的视频生成模型通常在有限数量的帧上进行训练，导致它们无法在推理过程中生成高保真的长视频

此外，这些模型仅支持单文本条件(single-text conditions)，而现实生活场景通常需要多文本条件(multi-text conditions)，因为视频内容随时间变化

为了应对这些挑战，本研究探讨了扩展文本驱动功能以生成基于多个文本条件的更长视频的潜力:
1.首先分析视频扩散模型中初始噪声的影响，然后，基于对噪声的观察，提出了FreeNoise，一种免调整(tuning-free)训练且高效(time-efficient)的范式，可以增强预训练视频扩散模型的生成能力，同时保持内容一致性，具体来说，不是初始化所有帧的噪声，而是为了长程相关重新调度一系列噪声，并通过基于窗口的函数(window-based function)对它们进行时间注意

2.此外，还设计了一种新颖的运动注入方法(motion injection method)来支持根据多个文本提示生成视频

大量的实验验证了本方法在扩展视频扩散模型的生成能力方面的优越性，值得注意的是，与之前最佳性能的方法带来的约255%的额外时间成本相比，本方法仅产生了微不足道的17%的时间成本

<img src="https://img.saraba1st.com/forum/202310/24/160250qyanxdpxzzcdecg5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231024-154931.jpg</strong> (134.95 KB, 下载次数: 0)

下载附件

2023-10-24 16:02 上传

长视频推理的挑战，随机噪声ϵ1和ϵ2具有与模型训练时相同的帧数，所有结果都是在相同的文本提示下生成的：“a man is boating on a lake”

<img src="https://img.saraba1st.com/forum/202310/24/160259grdrljtt9839t39t.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231024-155124.jpg</strong> (280.94 KB, 下载次数: 0)

下载附件

2023-10-24 16:02 上传

时间建模的案例研究，对于(A)和(B)中的“w/o Tconv”结果，与相同初始噪声帧对应的帧用相同的颜色标记

<img src="https://img.saraba1st.com/forum/202310/24/160303xmwzpqkq1k1bpbw3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231024-155300.jpg</strong> (34.91 KB, 下载次数: 0)

下载附件

2023-10-24 16:03 上传

基于局部窗口的注意力融合图，每个窗口的大小为N作为训练视频长度

<img src="https://img.saraba1st.com/forum/202310/24/160308x08eeeeqtncx8ctg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231024-155432__01.jpg</strong> (53.46 KB, 下载次数: 0)

下载附件

2023-10-24 16:03 上传

长视频生成的定量对比

<img src="https://img.saraba1st.com/forum/202310/24/160312cclh9pcncna5dqq6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231024-155432__02.jpg</strong> (242.32 KB, 下载次数: 0)

下载附件

2023-10-24 16:03 上传

长视频生成的定性比较

左侧提示为：“A chihuahua in astronaut suit floating in space, cinematic lighting, glow effect”
右侧提示：“A very happy fuzzy panda dressed as a chef eating pizza in the New York street food truck”

<img src="https://img.saraba1st.com/forum/202310/24/160318jzwnbsqn5in8sosa.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231024-155737.jpg</strong> (44.47 KB, 下载次数: 0)

下载附件

2023-10-24 16:03 上传

用户研究结果，用户需要在内容一致性、视频质量和视频文本对齐方面从提出的FreeNoise与其他基线方法中选择最好的一个

<img src="https://img.saraba1st.com/forum/202310/24/160325laoa8muj92aj3u4m.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231024-155903.jpg</strong> (136.27 KB, 下载次数: 0)

下载附件

2023-10-24 16:03 上传

多提示视频生成的定性比较

左侧的多重提示：“A camel running on the snow field”→“A camel standing on the snow field”
右侧的多重提示：“An astronaut resting on a horse”→“An astronaut riding a horse”

<img src="https://img.saraba1st.com/forum/202310/24/160330ngjxo3ndg83o8308.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231024-160130.jpg</strong> (320.05 KB, 下载次数: 0)

下载附件

2023-10-24 16:03 上传

消融实验结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 909#       发表于 2023-10-24 16:49

Cola

大型语言模型是视觉推理协调者

github项目主页:https://github.com/cliangyu/Cola

视觉推理需要多模态感知和对世界的常识认知，最近，人们提出了多种视觉语言模型(VLM/vision-language models)方法，在各个领域都具有出色的常识推理能力，然而，如何利用这些互补的VLM的集体力量却很少被探讨，像聚合(ensemble)这样的现有方法仍然难以将这些模型与所需的高阶通信(higher-order communication)集合起来

在这项工作中，提出了Cola，一种协调多个VLM进行视觉推理的新颖范式，本文的主要见解是，大型语言模型(LLM)可以通过利用自然语言通信来有效地协调多个VLM从而利用其独特且互补的功能

大量实验表明，指令调整变体Cola-FT在视觉问答(VQA/visual question answering)、外部知识VQA(outside knowledge VQA)、视觉蕴涵(VE/Visual Entailment)和视觉空间推理任务(visual spatial reasoning tasks)上实现了SOTA性能

此外，研究还表明，上下文学习变体Cola-Zero在零样本和少样本设置中表现出了富有竞争力的性能，无需进行微调，通过系统化的消融实验和可视化，验证了LLM协调者确实理解了指令提示以及VLM的单独功能，然后成功协调了它们以实现令人印象深刻的视觉推理能力

<img src="https://img.saraba1st.com/forum/202310/24/164710jt61000t61401sz5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231024-161859.jpg</strong> (161.84 KB, 下载次数: 0)

下载附件

2023-10-24 16:47 上传

提案的Cola协调语言模型进行视觉推理，根据视觉上下文和提供的伪(plausible)答案来协调多个预训练的LLM

<img src="https://img.saraba1st.com/forum/202310/24/164717iej311cooirorcjm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231024-162241.jpg</strong> (203.49 KB, 下载次数: 0)

下载附件

2023-10-24 16:47 上传

LM提示模板，LM被指示协调VLM，每个问题集都定义了视觉上下文、问题(和选择)以及伪答案

<img src="https://img.saraba1st.com/forum/202310/24/164722mpczqzvupppp7v7v.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231024-162553.jpg</strong> (484.64 KB, 下载次数: 0)

下载附件

2023-10-24 16:47 上传

整体表现，Model Spec.表示规范总结了每种方法中采用的详细VLM和LM及其参数，FT和ICT分别表示微调和上下文学习，向下的箭头表示FT和ICT越少，效率越高，不同数据集中的准确度指标略有不同，向上的箭头表示精度越高越好，用粗体字体标记了每个数据集上的最佳性能，用下划线标记次佳性能

<img src="https://img.saraba1st.com/forum/202310/24/164728plswbco7ln000iwc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231024-162850.jpg</strong> (228.54 KB, 下载次数: 0)

下载附件

2023-10-24 16:47 上传

定性例子，正确的选择有下划线

最左边：A-OKVQA的常识题示例；  LLM遵循BLIP的答案
左：A-OKVQA的视觉问题示例；  LLM遵循OFA的答案
右：e-SNLI-VE示例；  LLM协调后选择另一个方案
最右边：VSR的示例；  LLM根据OFA的标题说明和BLIP的答案进行预测

Cola-Zero是在零样本设置中推理出来的，最底行Cola-FT(交换的VLM答案标签)表示LLM根据其各自的功能遵循某些VLM的答案，LLM答案与VLM答案标签的分布相关

<img src="https://img.saraba1st.com/forum/202310/24/164800of4515nqvcvk1fn4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231024-163413.jpg</strong> (105.08 KB, 下载次数: 0)

下载附件

2023-10-24 16:48 上传

使用单个 VLM 的消融研究结果(从顶部开始 #1、#2)、仅VLM的伪答案(无标题说明，#3)、VLM的标题说明(无为答案，#4)、在指令调整时扰动VLM标题说明/答案标签（#5、#6），在评估时交换答案标签(#7)

在#6中，LLM无法学习协调先验，在#7中，LLM可以学习协调先验，但不能在评估时正确应用

FT:指令调整； Eval:评估

<img src="https://img.saraba1st.com/forum/202310/24/164815od280zaw8claf0lz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231024-163927.jpg</strong> (105.74 KB, 下载次数: 0)

下载附件

2023-10-24 16:48 上传

基于三个相同与不同模型的聚合方法的性能

<img src="https://img.saraba1st.com/forum/202310/24/164824lat97gi1y6w9w7zx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231024-164027.jpg</strong> (55.99 KB, 下载次数: 0)

下载附件

2023-10-24 16:48 上传

<img src="https://img.saraba1st.com/forum/202310/24/164824xoqmszciopdti7pi.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231024-164110.jpg</strong> (87.2 KB, 下载次数: 0)

下载附件

2023-10-24 16:48 上传

不同情形下的模型性能研究

<img src="https://img.saraba1st.com/forum/202310/24/164854h57kpu0m5k3v40af.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231024-164839.jpg</strong> (169.66 KB, 下载次数: 0)

下载附件

2023-10-24 16:48 上传

输入Token关联性的可视化，通过特征归因可视化输入Token和输出Token“grass”之间的相关性，较关联的Token在较暗的框中突出显示，Cola-FT重点关注(a)中的问题、选择和VLM的伪答案，而如(b)所示，由于FLAN-T5指令调整，Cola-Zero特别关注指令和VLM标签

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  arb1ters  
##### 910#       发表于 2023-10-24 18:00

<blockquote>Machinery 发表于 2023-10-20 03:53
Fuyu-8B

人工智能代理者的多模态架构</blockquote>
你的这些文章是自己机翻的，还是转载的公众号？有关注哪些公众号呢

[论坛助手,iPhone](https://bbs.saraba1st.com/2b/forum.php?mod=viewthread&amp;tid=2029836)


*****

####  Machinery  
##### 911#       发表于 2023-10-24 18:04

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=62816795&amp;ptid=2126390" target="_blank">arb1ters 发表于 2023-10-24 18:00</a>
你的这些文章是自己机翻的，还是转载的公众号？有关注哪些公众号呢

论坛助手,iPhone ...</blockquote>
那当然全都是我亲手翻和校对的<img src="https://static.saraba1st.com/image/smiley/face2017/068.png" referrerpolicy="no-referrer">

—— 来自 [S1Fun](https://s1fun.koalcat.com)

*****

####  arb1ters  
##### 912#       发表于 2023-10-24 18:05

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=62816837&amp;ptid=2126390" target="_blank">Machinery 发表于 2023-10-24 18:04</a>
那当然全都是我亲手翻和校对的

—— 来自 S1Fun</blockquote>
辛苦了，要不开个公众号和微博收收米吧

[论坛助手,iPhone](https://bbs.saraba1st.com/2b/forum.php?mod=viewthread&amp;tid=2029836)

*****

####  Machinery  
##### 913#       发表于 2023-10-24 18:07

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=62816843&amp;ptid=2126390" target="_blank">arb1ters 发表于 2023-10-24 18:05</a>
辛苦了，要不开个公众号和微博收收米吧

论坛助手,iPhone</blockquote>
那倒不用，这贴更新时间也不一定，主要是开源项目的集合，也方便我自己找项目，算顺手吧<img src="https://static.saraba1st.com/image/smiley/face2017/066.png" referrerpolicy="no-referrer">

—— 来自 [S1Fun](https://s1fun.koalcat.com)

﹍﹍﹍

评分

 参与人数 1战斗力 +1

|昵称|战斗力|理由|
|----|---|---|
| wly5556| + 1|好评加鹅|

查看全部评分


*****

####  Machinery  
##### 914#       发表于 2023-10-25 00:25

 本帖最后由 Machinery 于 2023-10-25 00:27 编辑 

S3Eval

合成、可扩展、系统化评估大型语言模型的套件

github项目主页:https://github.com/lfy79001/SQLEval

大型语言模型(LLM)的快速进步使得诸如推理和长上下文理解等模型能力取得了发展，然而也是因为LLM能够处理的上下文更长，评估这些LLM是否获得了某些能力变得更具挑战性，包括那些可以处理达到100K Token文本长度的模型，这远远超过了人类在合理持续时间内可以可靠评估的长度

在本文中，提议使用更复杂的合成任务作为代理评估方法，提出了S3Eval，一个用于LLM评估的合成、可扩展、系统化的评估套件，作为合成基准，S3Eval可以创建理论上LLM未见的任意数量的评估示例，从而减轻测试集污染问题，S3Eval的综合性质使用户能够完全控制数据集，使之能够通过缩放文本长度和跨不同场景改变任务难度来系统地探索LLM的能力

S3Eval的性能与Big-Bench Hard (BBH)等现实世界基准分数之间的强相关性证明了使用S3Eval评估LLM的合理性，深入分析还揭示了更多见解，包括当答案分布稀疏或位于上下文中间时性能下降，以及模型性能的一些反直觉趋势

<img src="https://img.saraba1st.com/forum/202310/25/002447oqyieldqi9h8xc7m.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231025-001419.jpg</strong> (134.05 KB, 下载次数: 0)

下载附件

2023-10-25 00:24 上传

演示了S3EVAL工作流程的插图，其中通过评估对随机生成的表执行SQL查询的能力来评估LLM的功能

S3Eval是一个用于大型语言模型评估和分析的平台，具有以下特点：
1.推理：SQL包含丰富的语法，其中每个关键字都隐含着不同的推理能力，可以有效测试模型的推理能力
2.长上下文理解：长文本评估的难点在于如何收集有意义的文本和任务，理论上S3Eval可以评估任何LLM上下文窗口长度的任何长上下文能力
3.可控性分析：该平台允许对数据生成进行细粒度控制，比如表的详细属性、生成SQL的细粒度难度控制等等，用户可以灵活地使用进而探索LLM的更多能力
4.动态的无数据泄露：随机构造LLM从未见过的合成数据，极大缓解了LLM评估中的数据泄露问题
5.可定制：用户可以使用自己的xlsx/csv表来生成任意复杂度的SQL

<img src="https://img.saraba1st.com/forum/202310/25/002455mzlpgu6z8z6u6ll6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231025-002324.jpg</strong> (72.15 KB, 下载次数: 0)

下载附件

2023-10-25 00:24 上传

使用精确匹配(EM/exact match)指标作为评估函数，同时也将皮尔逊相关系数(r)和肯德尔等级相关系数(τ)视为相关函数

结果显示S3Eval和BBH之间具有很强的一致性，对于CodeLLM，显示了S3Eval和HumanEval之间的一致性

相关评估结果:

<img src="https://img.saraba1st.com/forum/202310/25/002507ay26uyiv6ckiy0ck.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231025-002353.jpg</strong> (297.34 KB, 下载次数: 0)

下载附件

2023-10-25 00:25 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 915#       发表于 2023-10-25 16:38

 本帖最后由 Machinery 于 2023-10-25 16:41 编辑 

Woodpecker

多模态大语言模型的幻觉纠正

github项目主页:https://github.com/BradyFU/Woodpecker

幻觉(Hallucination)是笼罩在急速发展的多模态大型语言模型(MLLM)上的阴影之一，指的是生成的文本与图像内容不一致的现象，为了减轻幻觉，现有的研究主要采用指令调整的方式，经常需要使用特定的数据重新训练模型

在本文中，开辟了一条不同的道路，引入了一种名为Woodpecker的免训练方法，就像啄木鸟治愈树木一样，它从生成的文本中挑选并纠正幻觉，具体来说，Woodpecker由五个阶段组成：关键概念提取(key concept extraction)、问题表述(question formulation)、视觉知识验证(visual knowledge validation)、视觉声明生成(visual claim generation)和幻觉纠正(hallucination correction)

以生成后补救(post-remedy)的方式施行，Woodpecker可以轻松的为不同的MLLM提供服务，同时可以通过接触这五个阶段的中间输出结果进而获得白盒化的解释

对Woodpecker进行的定量和定性评估，展示了这种新范式的巨大潜力，在POPE基准上，Woodpecker方法比作为基线的MiniGPT-4/mPLUG-Owl的准确度提高了30.66%/24.33%

<img src="https://img.saraba1st.com/forum/202310/25/163647sc6zyy4pvvy4h865.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231025-162157.jpg</strong> (112.94 KB, 下载次数: 0)

下载附件

2023-10-25 16:36 上传

MLLM中幻觉的图示，给定图像，MLLM可能会输出对象级(object-level)和属性级(attribute-level )幻觉的相应响应

<img src="https://img.saraba1st.com/forum/202310/25/163651g829ym5bjz11e591.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231025-162400.jpg</strong> (376.93 KB, 下载次数: 0)

下载附件

2023-10-25 16:36 上传

幻觉矫正框架示例，给定MLLM的响应，Woodpecker会纠正幻觉部分并合并基准信息以用于验证

<img src="https://img.saraba1st.com/forum/202310/25/163733ohi8mi5fhhc4x6ll.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231025-162634__01.jpg</strong> (542.68 KB, 下载次数: 0)

下载附件

2023-10-25 16:37 上传

Woodpecker的框架，给定图像和查询，MLLM输出相应的响应通过关键概念提取、问题表述、视觉知识验证和视觉声明生成这四个步骤，得到了特定于图像和原始响应的视觉知识库，在最后一步中，以边界框作为证据来纠正响应中的幻觉

<img src="https://img.saraba1st.com/forum/202310/25/163741fxh6lrhnm5nv4f46.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231025-162944.jpg</strong> (215.64 KB, 下载次数: 0)

下载附件

2023-10-25 16:37 上传

<img src="https://img.saraba1st.com/forum/202310/25/163741gp2p398iplzt2it7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231025-163114.jpg</strong> (106.94 KB, 下载次数: 0)

下载附件

2023-10-25 16:37 上传

POPE与MME的结果，w/Ours表示由Woodpecker校正的MLLM响应，每个设置中的最佳和次佳性能分别用粗体和下划线表示

<img src="https://img.saraba1st.com/forum/202310/25/163822kdd99fepp9zypdtp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231025-163212.jpg</strong> (94.01 KB, 下载次数: 0)

下载附件

2023-10-25 16:38 上传

<img src="https://img.saraba1st.com/forum/202310/25/163822n5bw59t5e5oap95q.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231025-163807.jpg</strong> (64.37 KB, 下载次数: 0)

下载附件

2023-10-25 16:38 上传

GPT-4V辅助评估图示与结果，准确性和详细度指标的等级为10，分数越高表示性能越好

<img src="https://img.saraba1st.com/forum/202310/25/163826nxzv2y6jdkpfkylb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231025-163356.jpg</strong> (48.91 KB, 下载次数: 0)

下载附件

2023-10-25 16:38 上传

具有不同框架变体的MME的消融结果

“default”是一个总是回答“Yes”的模型，“default w/Detector”引入了用于幻觉纠正的物体检测器，“default w/VQA”引入了VQA模型，而“default w/Woodpecker”是完整框架

<img src="https://img.saraba1st.com/forum/202310/25/164144utb9i9m8ebjriexe.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231025-163526.jpg</strong> (25.68 KB, 下载次数: 0)

下载附件

2023-10-25 16:41 上传

不同纠正结果的比例

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 916#       发表于 2023-10-26 01:01

 This-is-not-a-Dataset

挑战大型语言模型的大型否定基准(A Large Negation Benchmark)

https://github.com/hitz-zentroa/This-is-not-a-Dataset

尽管大型语言模型(LLM)已经获得了一定水平的语法知识和泛化能力，但它们无法诠释否定(negation)，而否定是自然语言处理中的关键步骤，本文试图阐明LLM对于否定为何表现不佳的原因

研究组引入了一个大型的半自动生成数据集，其中包含大约400000个关于常识性知识的描述性句子，这些句子可以是真或假(that can be true or false)，其中否定以不同的形式出现在大约2/3的数据中

以零样本方法使用数据集对最大的可用开源LLM进行测试来判断它们的泛化和推理能力，还微调了一些模型评估是否可以训练模型对否定的理解

研究结果表明，虽然LLM能够熟练地对肯定句进行分类，但却很难处理否定句，并且缺乏对否定的深刻理解，多数依赖于肤浅的关联，尽管对否定句进行模型微调可以改善性能，但在处理否定方面缺乏泛化能力的现象仍然存在，这凸显了LLM在理解和泛化否定方面面临持续的挑战

<img src="https://img.saraba1st.com/forum/202310/26/010031q16ef3s44hc4feoh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231026-004721.jpg</strong> (140.21 KB, 下载次数: 0)

下载附件

2023-10-26 01:00 上传

数据集中的肯定与否定句

<img src="https://img.saraba1st.com/forum/202310/26/010035cx4bx111i1akkwdi.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231026-004825.jpg</strong> (112.33 KB, 下载次数: 0)

下载附件

2023-10-26 01:00 上传

否定的常见类型与分类

<img src="https://img.saraba1st.com/forum/202310/26/010040gddbfdj1jojd3h26.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231026-004849.jpg</strong> (118.41 KB, 下载次数: 0)

下载附件

2023-10-26 01:00 上传

句子的模式分布

<img src="https://img.saraba1st.com/forum/202310/26/010044ddd0p7c1iuc5zcn5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231026-005004.jpg</strong> (61.83 KB, 下载次数: 0)

下载附件

2023-10-26 01:00 上传

对数据集中句子质量的人工评估

<img src="https://img.saraba1st.com/forum/202310/26/010048adrmmo7766rmam6k.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231026-005101.jpg</strong> (127.3 KB, 下载次数: 0)

下载附件

2023-10-26 01:00 上传

本文数据集的各种LLM的零样本表现，最佳结果以粗体突出显示，超过随机基线准确率的分数用下划线表示

<img src="https://img.saraba1st.com/forum/202310/26/010053o3c9nj99x1nrcx4x.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231026-005241.jpg</strong> (99.39 KB, 下载次数: 0)

下载附件

2023-10-26 01:00 上传

Flan-T5-xxl和Vicuna13B在同义词和反义模式中的准确率，在没有干扰的情况下用肯定句和否定句评估模型，超过随机基线的分数用下划线表示

<img src="https://img.saraba1st.com/forum/202310/26/010113wiuvepiivd1hsuvh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231026-005455.jpg</strong> (53.81 KB, 下载次数: 0)

下载附件

2023-10-26 01:01 上传

在使用本文数据集对Vicuna13B和Flan-T5-xxl微调后的性能，最佳结果以粗体突出显示，超过随机基线准确率的分数用下划线表示

<img src="https://img.saraba1st.com/forum/202310/26/010118w6taweetpgbga55b.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231026-005639.jpg</strong> (116.34 KB, 下载次数: 0)

下载附件

2023-10-26 01:01 上传

使用不同类型和数量的负面知识对Vicuna13B微调后的准确度，最佳结果以粗体突出显示，超过随机基线准确率的分数用下划线表示

<img src="https://img.saraba1st.com/forum/202310/26/010122ktk6cmelzketvfkv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231026-005816.jpg</strong> (166.14 KB, 下载次数: 0)

下载附件

2023-10-26 01:01 上传

在一种模式(行)上进行训练同时在其他模式(列)上进行评估时的Vicuna13B的准确率

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 917#       发表于 2023-10-26 19:58

DreamCraft3D

使用引导扩散先验(Bootstrapped Diffusion Prior)进行的分层3D生成(Hierarchical 3D Generation)

项目主页:https://mrtornado24.github.io/DreamCraft3D/

github项目主页:https://github.com/deepseek-ai/DreamCraft3D

DreamCraft3D，一种分层的3D内容生成方法，利用2D参考图像指导几何雕刻(geometry sculpting)和纹理提升(texture boosting)，可以生成高保真且连贯的3D对象

这项工作的中心重点是解决现有作品遇到的一致性问题，为了连贯渲染雕刻的几何形状，通过依赖于视图的扩散模型执行分数蒸馏采样(score distillation sampling)，这样会致使3D先验以及多种训练策略优先考虑几何一致性，损害了纹理的保真度

借由使用引导分数蒸馏(Bootstrapped Score Distillation)来专门增强纹理，在场景的增强渲染上训练个性化Dreambooth扩散模型，为其注入正在优化的场景的3D知识，这种3D感知扩散先验的分数蒸馏为场景提供了视图一致的指导，值得注意的是，通过对扩散先验和3D场景表征的交替优化，实现了相辅相成的改进，优化的3D场景辅助训练特定于场景的扩散模型，从而为3D优化提供越来越一致的视图指导，优化因此被引导并导向了非常显著的纹理效果提升

通过在整个分层生成过程中量身定制的3D先验，DreamCraft3D可以生成具有照片级真实感渲染的连贯3D对象

<img src="https://img.saraba1st.com/forum/202310/26/195750zclup99oxmj999ip.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231026-193808.jpg</strong> (109.56 KB, 下载次数: 0)

下载附件

2023-10-26 19:57 上传

DreamCraft3D利用从文本提示生成的2D图像来指导几何雕刻和纹理提升的阶段，当雕刻几何时，视图条件扩散模型(view-conditioned diffusion model)提供关键的3D指导以确保几何一致性，然后通过进行循环优化来专门提升纹理质量，同时增强了多视图渲染，并使用它们来微调DreamBooth扩散模型，以提供多视图一致的渐变来优化场景，因此将不断先验扩散过程中蒸馏产生的损失(loss)称为引导蒸馏采样(bootstrapped distillation sampling)

<img src="https://img.saraba1st.com/forum/202310/26/195757bzprddmqp8yrl77r.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231026-194718.jpg</strong> (410.92 KB, 下载次数: 0)

下载附件

2023-10-26 19:57 上传

通过将2D图像提升为3D，DreamCraft3D实现了具有丰富细节和整体3D一致性的3D生成效果

<img src="https://img.saraba1st.com/forum/202310/26/195803wtva8aygpgr8vggh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231026-194851.jpg</strong> (174.76 KB, 下载次数: 0)

下载附件

2023-10-26 19:58 上传

与基线的定性对比，本文方法在几何和纹理方面生成了更清晰、更可信的细节，同时在新的视图中生成丰富的纹理细节，消除了之前其他方法遇到的多面Janus问题

<img src="https://img.saraba1st.com/forum/202310/26/195807fze08a08zpqahahn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231026-195034.jpg</strong> (108.96 KB, 下载次数: 0)

下载附件

2023-10-26 19:58 上传

改进了引导过程中的视图一致性和纹理保真度

<img src="https://img.saraba1st.com/forum/202310/26/195812ne1v3xkcu3edtnxx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231026-195107.jpg</strong> (76.07 KB, 下载次数: 0)

下载附件

2023-10-26 19:58 上传

与之前的2D到3D提升方法的定量对比，指标结果是根据300个生成的样本测量获得的

<img src="https://img.saraba1st.com/forum/202310/26/195816v6gyzq0h0mhru0rq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231026-195226.jpg</strong> (64.91 KB, 下载次数: 0)

下载附件

2023-10-26 19:58 上传

3D先验和提案的BSD(Bootstrapped Score Distillation)有效性的消融实验

(a)在几何雕刻阶段没有3D先验
(b)使用SDS损失优化纹理
(c)VSD损失产生了丰富的纹理细节，但也被纹理不一致的情况影响
(d)BSD提高了一轮DreamBooth的纹理一致性
(e)两轮BSD为生成的结果添加了更多细节

<img src="https://img.saraba1st.com/forum/202310/26/195821mtydzqrd33kryvck.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231026-195624.jpg</strong> (102.55 KB, 下载次数: 0)

下载附件

2023-10-26 19:58 上传

通过多阶段持续改进几何和纹理质量

<img src="https://img.saraba1st.com/forum/202310/26/195825m9u9iqce0bcbg0uu.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231026-195701.jpg</strong> (52.95 KB, 下载次数: 0)

下载附件

2023-10-26 19:58 上传

用户研究结果

生成示例:

<img src="https://img.saraba1st.com/forum/202310/26/195839dqnzi7y7ey72hy33.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231026-193753.jpg</strong> (590.11 KB, 下载次数: 0)

下载附件

2023-10-26 19:58 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 918#       发表于 2023-10-27 23:22

CommonCanvas

使用知识共享(CC/Creative-Commons-licensed)图像训练的开放扩散模型

github项目说明页:https://github.com/mosaicml/diffusion/blob/main/assets/common-canvas.md

研究组聚合了一个知识共享图像的数据集，训练了一系列的开源扩散模型，这些模型在质量上可与Stable Diffusion 2竞争

这项任务需要解决两个挑战：
1.高分辨率的知识共享图像缺乏用于训练文本到图像生成模型所需的对应文本对
2.知识共享图像相对稀缺

为了应对这些挑战，通过使用直观的迁移学习技术，生成了一组与精选的知识共享图像所配对的高质量合成说明文本，还开发了一种提高数据和计算效率的训练方案，总计只需要相对于训练现有Stable Diffusion 2模型所需的LAION-2B数据的3%即可，但获得的质量相当，这些结果表明实际上是有足够数量的知识共享图像(约7000万)可用于训练高质量模型，训练方案还实施了各种优化，可实现约3倍的训练加速，从而实现快速模型迭代

通过利用这些方法，本文研究组训练了一系列的高质量文本到图像模型，称其为CommonCanvas系列，虽然这些模型是在比LAION数据集小得多的知识共享数据集上进行训练并使用合成说明文本进行训练的，但其中最大的模型型号在人类评估中实现了与Stable Diffusion 2相当的性能

<img src="https://img.saraba1st.com/forum/202310/27/232159l9yo9gjt5e5q8tqt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231027-230014.jpg</strong> (233.74 KB, 下载次数: 0)

下载附件

2023-10-27 23:21 上传

完全使用知识共享图像和合成说明文本方法，实现了与Stable Diffusion 2(SD2-base)相当的性能

<img src="https://img.saraba1st.com/forum/202310/27/232203u1npsugs12nuiu1u.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231027-230512.jpg</strong> (89.74 KB, 下载次数: 0)

下载附件

2023-10-27 23:22 上传

当输入与迪士尼电影相关的概念提示时，SD2-base会生成可识别的《冰雪奇缘》中艾莎的图像以及带有畸形迪士尼徽标和类似于《狮子王》中的角色的海报式图像，而CommonCanvas则没有

<img src="https://img.saraba1st.com/forum/202310/27/232208p0h54uz54htv6ye8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231027-230851.jpg</strong> (80.97 KB, 下载次数: 0)

下载附件

2023-10-27 23:22 上传

通过BLIP-2从输入图像“有损压缩”到合成说明文本，当使用T2I模型生成带有“有损”的说明文本的图像时(例如CommonCanvas)，生成的图像与原始说明文本图像完全不同

<img src="https://img.saraba1st.com/forum/202310/27/232212zgypex49yi4ea9s4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231027-231107.jpg</strong> (43.61 KB, 下载次数: 0)

下载附件

2023-10-27 23:22 上传

LAION-2B图像的原始说明文本与BLIP-2生成的说明文本，BLIP-2生成的标题更符合人类书写的内容

<img src="https://img.saraba1st.com/forum/202310/27/232216vi7gskm7ygss0gwk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231027-231521.jpg</strong> (44.97 KB, 下载次数: 0)

下载附件

2023-10-27 23:22 上传

CommonCatalog-C包含仅授权用于商业用途的图像；-NC包含-C以及授权用于非商业用途的图像

<img src="https://img.saraba1st.com/forum/202310/27/232220fadgnziqy2d2d2ny.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231027-231701.jpg</strong> (92.55 KB, 下载次数: 0)

下载附件

2023-10-27 23:22 上传

计算效率分析与用户研究调查

<img src="https://img.saraba1st.com/forum/202310/27/232223f2ust22h11hpuuya.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231027-231729.jpg</strong> (255.29 KB, 下载次数: 0)

下载附件

2023-10-27 23:22 上传

相关评估指标结果

<img src="https://img.saraba1st.com/forum/202310/27/232228qyyw3ovp405vv0v3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231027-231850.jpg</strong> (191.05 KB, 下载次数: 0)

下载附件

2023-10-27 23:22 上传

对比了CommonCanvas-SNC与Stable Diffusion 2，本文模型不太可能根据暗示性提示生成标志性角色

<img src="https://img.saraba1st.com/forum/202310/27/232232jrfst2vsd23en3ev.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231027-232019.jpg</strong> (163.35 KB, 下载次数: 0)

下载附件

2023-10-27 23:22 上传

使用CommonCanvas-SNC生成名人，模型在综合个体方面比SD2差，但能够生成一些著名的公众人物

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  okok123  
##### 919#       发表于 2023-10-28 00:24

大佬实在太专业了，伸手党求教下：
1.请问现在llm的3dmark工具或者评测谁更科学？
2.请问能在16g显卡跑的开源llm目前比较好的是哪些？
感谢感谢


*****

####  Machinery  
##### 920#       发表于 2023-10-28 02:34

ChatGLM3

ChatGLM模型第三代

项目主页:https://github.com/THUDM/ChatGLM3

相关介绍:https://www.sohu.com/a/731775848_255153/

github项目说明页:

<img src="https://img.saraba1st.com/forum/202310/28/023439z844gztotssv88s9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231028-023038.jpg</strong> (351.17 KB, 下载次数: 0)

下载附件

2023-10-28 02:34 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)

*****

####  Machinery  
##### 921#       发表于 2023-10-28 02:40

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=62853778&amp;ptid=2126390" target="_blank">okok123 发表于 2023-10-28 00:24</a>
大佬实在太专业了，伸手党求教下：
1.请问现在llm的3dmark工具或者评测谁更科学？
2.请问能在16g显卡跑的开 ...</blockquote>
1.评测分为各种领域与考核方法的(指标)测试与(用户)研究，目前来说没有全知全能与万能的模型，专业领域的深度也决定了不会有这种模型，所以需要按需选择自己想使用的领域与相关的模型前沿，看你的需求是通用还是专用领域了

2.开源llm大致上分为英文预训练与中文预训练模型，之后可以尽量选择最新系列的模型，看看各种指标很容易判断高低，实际上手使用一下，16g跑不了太大的模型，不过一般的开源llm都会提供7b版本，这个是能跑的，可以看看上边的chatglm3

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 922#       发表于 2023-10-28 15:47

 本帖最后由 Machinery 于 2023-10-28 15:52 编辑 

SSD-1B

SSD-1B(Segmind Stable Diffusion 1B)是Stable Diffusion XL(SDXL)蒸馏50%的缩小版本，可以在提供60%的加速的同时保持高质量的文本到图像生成功能

权重下载:https://huggingface.co/segmind/SSD-1B

官方Demo:https://www.segmind.com/models/ssd-1b

hugface演示Demo空间:https://huggingface.co/spaces/segmind/Segmind-Stable-Diffusion

SSD-1B经过各种数据集的训练，包括Grit和Midjourney scrap数据，以增强其根据文本提示创建各种广阔的视觉内容的能力

<img src="https://img.saraba1st.com/forum/202310/28/155218y3fvax95fx5k8t3r.jpg" referrerpolicy="no-referrer">

<strong>a512cd99-43b7-4406-8aa5-8d58c2e956bd.jpg</strong> (305.65 KB, 下载次数: 0)

下载附件

2023-10-28 15:52 上传

该模型采用知识蒸馏策略，连续利用多个专家模型(包括SDXL、ZavyChromaXL和JuggernautXL)的教学，混合它们的优势并产生令人印象深刻的视觉输出
————
模型信息
开发商: Segmind
开发者: Yatharth Gupta and Vishnu Jaddipal.
模型类型: Diffusion-based text-to-image generative model
许可协议: Apache 2.0
从stabilityai/stable-diffusion-xl-base-1.0蒸馏而来
————
模型架构
SSD-1B是1.3B参数模型，从基本的SDXL模型中删除了多个层

<img src="https://img.saraba1st.com/forum/202310/28/154508f1e717nnst0ap17n.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231028-154330.jpg</strong> (90.39 KB, 下载次数: 0)

下载附件

2023-10-28 15:45 上传

————
训练超参数信息

<img src="https://img.saraba1st.com/forum/202310/28/154609oesjepdhfjx8hr99.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231028-154558.jpg</strong> (61.72 KB, 下载次数: 0)

下载附件

2023-10-28 15:46 上传

————
多分辨率比例支持

<img src="https://img.saraba1st.com/forum/202310/28/154623rv0eeqzu1l1ihbh0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231028-154359.jpg</strong> (217.49 KB, 下载次数: 0)

下载附件

2023-10-28 15:46 上传

————
生成速度对比

<img src="https://img.saraba1st.com/forum/202310/28/154640msqgaadaounen62n.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231028-154410.jpg</strong> (134.1 KB, 下载次数: 0)

下载附件

2023-10-28 15:46 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 923#       发表于 2023-10-30 19:45

Skywork-13B

Skywork是由昆仑万维集团·天工团队开发的一系列大型模型

github项目主页:https://github.com/SkyworkAI/Skywork

ModelScope项目主页:https://modelscope.cn/organization/skywork

本次开源的模型有Skywork-13B-Base模型、Skywork-13B-Chat模型、Skywork-13B-Math模型和Skywork-13B-MM模型(介绍如下):

1.【Skywork-13B-Base模型】在高质量清洗过滤的3.2万亿个多语言（主要是中文和英文）和代码数据上进行预训练，它在多种评测和各种基准测试上都展现了同等规模模型的最佳效果

2.【Skywork-13B-Chat模型】具备强大的对话能力，在文创领域进行了进一步的针对性增强，通过构建一万多条高质量指令数据集，在10个文创任务上进行了针对性微调，使模型在文创任务中能够接近ChatGPT的效果，此外，还开源了针对这10个文创任务上的大约500条样本组成的benchmark

3.【Skywork-13B-Math模型】经过专门的数学能力强化训练，在13B规模的模型中，Skywork-13B-Math模型在GSM8K评测上得分第一，同时在MATH数据集以及CMATH上也表现优异，处于13B模型顶尖水平

4.【Skywork-13B-MM多模态模型】支持用户输入图片信息进行问答，对话等任务

5.【Skywork/Skypile-150B数据集】是根据经过精心过滤的数据处理流程从中文网页中筛选出的高质量数据，本次开源的数据集大小约为600GB，总的token数量约为150B，是目前开源最大中文数据集

6.除此之外，还公开了【训练Skywork-13B模型中使用的评估方法、数据配比研究和训练基础设施调优方案等】信息，希望这些开源内容能够进一步启发社区对于大型模型预训练的认知，并推动人工智能通用智能(AGI)的实现

github项目页面介绍:

<img src="https://img.saraba1st.com/forum/202310/30/194531yzvqiqvm421ivuwq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231030-194223.jpg</strong> (279.55 KB, 下载次数: 0)

下载附件

2023-10-30 19:45 上传

<img src="https://img.saraba1st.com/forum/202310/30/194531i1tv288a6t3vfv31.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231030-194236.jpg</strong> (132.59 KB, 下载次数: 0)

下载附件

2023-10-30 19:45 上传

<img src="https://img.saraba1st.com/forum/202310/30/194531tmi811mzkkak91jz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231030-194309.jpg</strong> (543.86 KB, 下载次数: 0)

下载附件

2023-10-30 19:45 上传

<img src="https://img.saraba1st.com/forum/202310/30/194531qmndyxknt58xyaxi.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231030-194344.jpg</strong> (495.91 KB, 下载次数: 0)

下载附件

2023-10-30 19:45 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 924#       发表于 2023-10-30 23:47

 本帖最后由 Machinery 于 2023-10-30 23:52 编辑 

ControlLLM

通过搜索图(Searching on Graphs)工具增强语言模型

github项目主页:https://github.com/OpenGVLab/ControlLLM

ControlLLM，一种新颖的框架，可以使大型语言模型(LLM)利用多模态工具来解决复杂的现实世界任务，尽管LLM表现出色，但由于用户提示常有不明确的歧义、不准确的工具选择，参数化以及工具调度效率低下，目前在工具调用方面依然存在挑战

为了克服这些挑战，框架包含三个关键组件:
1.一个任务分解器(task decomposer)，它将复杂的任务分解为具有明确定义的输入和输出的清晰的子任务
2.Thoughts-on-Graph(ToG)范式，在预先构建的工具图上搜索最优解决方案路径，该图会指定不同工具之间的参数和依赖关系
3.一个具有丰富工具箱的执行引擎(execution engine with a rich toolbox)，它推理解决方案路径并在不同的计算设备上有效地运行工具解决问题

在涉及图像、音频和视频处理的多种任务上评估了本文框架，证明其与现有方法相比具有卓越的准确性、效率和多功能

<img src="https://img.saraba1st.com/forum/202310/30/234928mqj79imizjw1r7c2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231030-232522.jpg</strong> (98.56 KB, 下载次数: 0)

下载附件

2023-10-30 23:49 上传

任务规划的不同范式的对比

(A)思想链(CoT)、具有自我一致性(self-consistency)的CoT
(B)思想树(ToT)、本质上依赖LLM来执行任务规划，边(edge)是在LLM运行时生成的
(C)思维图(ToG)范式是在预先构建的图上搜索解决方案，捕获了工具间的依赖关系，避免了工具调用中的幻觉问题

<img src="https://img.saraba1st.com/forum/202310/30/234702kepqwf4g5xc5xhxp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231030-233131.jpg</strong> (161.12 KB, 下载次数: 0)

下载附件

2023-10-30 23:47 上传

ControlLLM的系统设计，该框架由三个阶段组成，第一阶段是任务分解，将用户输入解析为多个子任务，在第二阶段，ToG利用深度优先搜索算法(depth-first search algorithm)来找到每个子任务的最优解决方案，最后阶段的执行引擎执行解决方案并将输出返回给用户

在这里使用为视频生成网页的示例来说明方法

<img src="https://img.saraba1st.com/forum/202310/30/234711t6l4c4md6r61ltlt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231030-233409.jpg</strong> (123.36 KB, 下载次数: 0)

下载附件

2023-10-30 23:47 上传

详细阐述了任务分解中的输出协议中的每个字段的含义

<img src="https://img.saraba1st.com/forum/202310/30/234719zggxug1x117w1nkn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231030-233517.jpg</strong> (71.22 KB, 下载次数: 0)

下载附件

2023-10-30 23:47 上传

不同方法之间的特征对比，该表显示了本文框架支持更多有利于多模态交互的用户体验的功能，同时表明了框架的高可扩展性

<img src="https://img.saraba1st.com/forum/202310/30/234727blznohwz0sfjn4qj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231030-233637.jpg</strong> (217.56 KB, 下载次数: 0)

下载附件

2023-10-30 23:47 上传

<img src="https://img.saraba1st.com/forum/202310/30/234727znkhfzq6akah6fhf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231030-234111.jpg</strong> (83.73 KB, 下载次数: 0)

下载附件

2023-10-30 23:47 上传

与其他SOTA方法的对比/关于不同LLM之间的任务分解效率效果/不同搜索策略的评估，↓表示越小越好，↑表示越大越好

<img src="https://img.saraba1st.com/forum/202310/30/234739al47or8o89gnss4i.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231030-234211.jpg</strong> (146.85 KB, 下载次数: 0)

下载附件

2023-10-30 23:47 上传

任务规划的对比，用了两个简单的案例来说明两种不同方法在任务规划中的区别，在这里，每个输出节点是由不同的解决路径生成的

<img src="https://img.saraba1st.com/forum/202310/30/235015snna146q3end2ff3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231030-234347.jpg</strong> (425.13 KB, 下载次数: 0)

下载附件

2023-10-30 23:50 上传

<img src="https://img.saraba1st.com/forum/202310/30/235015ff2yfiyxmmmmf21m.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231030-234423.jpg</strong> (353.28 KB, 下载次数: 0)

下载附件

2023-10-30 23:50 上传

<img src="https://img.saraba1st.com/forum/202310/30/235015jv5sqkn9qf295897.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231030-234442.jpg</strong> (421.37 KB, 下载次数: 0)

下载附件

2023-10-30 23:50 上传

<img src="https://img.saraba1st.com/forum/202310/30/235229i5hl7w1lh8pfl2s2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231030-234456.jpg</strong> (399.94 KB, 下载次数: 0)

下载附件

2023-10-30 23:52 上传

<img src="https://img.saraba1st.com/forum/202310/30/235229j5vkw6fjfyhqa1a6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231030-234519.jpg</strong> (550.12 KB, 下载次数: 0)

下载附件

2023-10-30 23:52 上传

<img src="https://img.saraba1st.com/forum/202310/30/235229hvphqz9uq220ddee.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231030-234533.jpg</strong> (422.3 KB, 下载次数: 0)

下载附件

2023-10-30 23:52 上传

不同任务领域的案例研究

—— 来自 [S1Fun](https://s1fun.koalcat.com)

Screenshot_20231030-234456.jpg
(399.94 KB, 下载次数: 0)

下载附件

2023-10-30 23:51 上传

<img src="https://img.saraba1st.com/forum/202310/30/235103a3i1he7e8zffaktw.jpg" referrerpolicy="no-referrer">


*****

####  Machinery  
##### 925#       发表于 2023-10-31 00:35

Wonder3D

使用跨领域(Cross-Domain)扩散将单图像转为3D

项目页面:https://www.xxlong.site/Wonder3D/

github项目仓库:https://github.com/xxlong0/Wonder3D

hugface demo演示:https://huggingface.co/spaces/flamehaze1115/Wonder3D-demo

本文中介绍了Wonder3D，一种从单视图图像高效生成高保真纹理网格的新颖方法

最近基于分数蒸馏采样(SDS/Score Distillation Sampling)的方法已经展现出了从2D扩散先验复原3D几何形状的潜力，但它们经常会受到耗时的预先形状优化和不一致的几何的影响，相比之下，某些作品通过快速的神经网络推理直接产生3D信息，但其结果往往质量较低且缺乏几何细节

为了全面提高图像到3D任务的质量、一致性和效率，提出了一种跨域扩散模型，可以生成多视图的法线贴图和相应的彩色图像，为了确保一致性，通过采用多视图跨域注意力机制(multi-view cross-domain attention mechanism)，促进跨视图和模态的信息交换，最后，还引入了一种几何感知的法线融合算法，该算法可以从多视图2D表征中提取高质量的表面(surfaces)

广泛的评估表明，与之前的工作相比，本文方法实现了高质量的重建结果、稳健的泛化和相当好的效率

<img src="https://img.saraba1st.com/forum/202310/31/003425h17ae8af87rq1227.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231031-002110__01.jpg</strong> (359.24 KB, 下载次数: 0)

下载附件

2023-10-31 00:34 上传

Wonder3D只需2∼3分钟即可从单视图图像重建高度详细的纹理网格

Wonder3D首先通过跨域扩散模型生成一致的多视图法线图和相应的彩色图像，然后利用新颖的法线融合方法实现快速、高质量的重建

<img src="https://img.saraba1st.com/forum/202310/31/003434ut84rplfi8gr68xg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231031-002347.jpg</strong> (72.92 KB, 下载次数: 0)

下载附件

2023-10-31 00:34 上传

Wonder3D概览图，给定单个图像，Wonder3D将输入图像、从CLIP模型生成的文本嵌入、多个视图的相机参数和域切换器作为条件，生成一致的多视图法线贴图和彩色图像，随后Wonder3D采用创新的法线融合算法，从2D表征中稳健地重建高质量3D几何形状，从而生成高保真纹理网格

<img src="https://img.saraba1st.com/forum/202310/31/003500jb868f863zz8fq3g.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231031-002537.jpg</strong> (127.5 KB, 下载次数: 0)

下载附件

2023-10-31 00:35 上传

与合成多视图彩色图像的基线模型进行定性对比

<img src="https://img.saraba1st.com/forum/202310/31/003506kbe4xzhdrxzsfdsn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231031-002653.jpg</strong> (65.12 KB, 下载次数: 0)

下载附件

2023-10-31 00:35 上传

多视图跨域Transformer块的结构图示

<img src="https://img.saraba1st.com/forum/202310/31/003522mysyo86qz1ls2979.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231031-002748__01.jpg</strong> (482.14 KB, 下载次数: 0)

下载附件

2023-10-31 00:35 上传

Wonder3D对各种风格图像的定性结果

<img src="https://img.saraba1st.com/forum/202310/31/003527hhaamsahu2i4m4ue.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231031-002858__01.jpg</strong> (397.11 KB, 下载次数: 0)

下载附件

2023-10-31 00:35 上传

在重建纹理网格方面与GSO数据集上的基线方法进行定性对比

<img src="https://img.saraba1st.com/forum/202310/31/003534q6az38knm2ckkjk1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231031-003004__01.jpg</strong> (373.14 KB, 下载次数: 0)

下载附件

2023-10-31 00:35 上传

不同跨域扩散方案的消融实验

<img src="https://img.saraba1st.com/forum/202310/31/003540r679bmhwbvs655w7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231031-003127__01.jpg</strong> (409.99 KB, 下载次数: 0)

下载附件

2023-10-31 00:35 上传

<img src="https://img.saraba1st.com/forum/202310/31/003540zas17nk3sas4assb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231031-003308.jpg</strong> (181.02 KB, 下载次数: 0)

下载附件

2023-10-31 00:35 上传

不同纹理提取方法的消融实验与指标对比测试结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 926#       发表于 2023-10-31 20:04

LoRAShear

高效的大型语言模型结构化剪枝(Structured Pruning)和知识复原(Knowledge Recovery)

github项目主页:https://github.com/microsoft/lorashear

大型语言模型(LLM)改变了人工智能的格局，而其巨大的尺寸在计算成本方面提出了重大挑战，本文推出LoRAShear，一种对LLM进行结构性剪枝和知识复原的有效新方法

给定一个通常的LLM，LoRAShear首先创建依赖图(dependency graphs)发现最小删除结构(minimally removal structures)并分析知识分布(analyze the knowledge distribution)，然后它对LoRA适配器(LoRA adaptors)进行渐进式结构化修剪，并实现固有知识转移，以更好地保留冗余结构中的信息

为了恢复剪枝过程中丢失的知识，LoRAShear精心研究并设计出了一种带有动态数据适配器(dynamic data adaptors)的动态微调方案(dynamic fine-tuning schemes)，以有效缩小与完整模型的性能差距

数值化结果表明，仅使用一个GPU并在几个GPU天数内，LoRAShear有效的将LLM的占用空间减少了20%，性能仅下降 1.0%，改进显著优于SOTA技术

<img src="https://img.saraba1st.com/forum/202310/31/200354h92uq472sqqcsfvl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231031-195706.jpg</strong> (65.58 KB, 下载次数: 0)

下载附件

2023-10-31 20:03 上传

LoRAShear概览，给定一个通常的LLM，LoRAShear首先发现最小删除结构，随后分析知识分布，将关键结构标记为不可剪枝，之后通过LHSPG对可剪枝结构进行渐进式结构剪枝，最后复原丢失的知识以回顾与完整的LLM的性能差距

<img src="https://img.saraba1st.com/forum/202310/31/200401pjjj45r1hp87lach.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231031-200011.jpg</strong> (212.44 KB, 下载次数: 0)

下载附件

2023-10-31 20:04 上传

LLAMAv1和可训练变量分区中的依赖关系图

<img src="https://img.saraba1st.com/forum/202310/31/200406lzg6gzzdb2dj6g3j.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231031-200101.jpg</strong> (43.96 KB, 下载次数: 0)

下载附件

2023-10-31 20:04 上传

通过测量完整LLAMAv1的困惑度偏差(perplexity deviation)进行知识分布的分析

<img src="https://img.saraba1st.com/forum/202310/31/200410yqs45ebhhhd324b4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231031-200227.jpg</strong> (145.06 KB, 下载次数: 0)

下载附件

2023-10-31 20:04 上传

LoRAhear超越LLAMAv1

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 927#       发表于 2023-11-1 03:48

MM-VID

利用GPT-4V(ision)促进视频理解

项目主页:https://multimodal-vid.github.io/

MM-vid，一个新的集成系统，通过利用GPT-4V的能力，结合视觉、音频和语音方面的专用工具，以促进高级视频理解

MM-vid旨在解决长视频和复杂任务带来的挑战，例如在长达一小时的内容中进行推理以及掌握跨多个剧集的故事情节，MM-vid使用GPT-4V进行视频到剧本(video-to-script)生成，将多模态元素转录为长文本剧本，生成的剧本详细描述了角色的动向、动作、表情和对话，为大型语言模型(LLM)实现视频理解铺平了道路，这使LLM的高级应用发展成为可能，包括音频描述、字符识别以及多模态高阶理解

实验结果证明了MM-vid在处理不同视频长度的不同视频类型方面的有效性，此外，还展示了其应用于交互式环境(例如视频游戏和图形用户界面)时的潜力

<img src="https://img.saraba1st.com/forum/202311/01/034646pqqipb57gfs7zso5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231101-033641.jpg</strong> (331.84 KB, 下载次数: 0)

下载附件

2023-11-1 03:46 上传

MM-Vid包含的任务展示，通过分配专业的视觉、音频、语音专家与GPT-4V(ision)协作来解决具有挑战性的视频理解任务，例如，系统可以关联来自多个上传剧集的信息，并推理所查询角色的故事情节(Multi-Video Episodic Analysis)

<img src="https://img.saraba1st.com/forum/202311/01/034720i59ssj9f9sbpff5p.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231101-033353.jpg</strong> (62.81 KB, 下载次数: 0)

下载附件

2023-11-1 03:47 上传

MM-vid工作流程，系统将视频文件作为输入，并输出描述视频内容的长文本剧本，一共由四个模块组成：(i)多模态预处理，(ii)外部知识收集，(iii)剪辑片段级(Clip-Level)视频描述生成，以及(iv)剧本生成

<img src="https://img.saraba1st.com/forum/202311/01/034728ckg5akgg5akkp1ka.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231101-034106.jpg</strong> (57.89 KB, 下载次数: 0)

下载附件

2023-11-1 03:47 上传

用于流输入的MM-vid，系统可以充当交互环境中的代理者，持续接收和处理流视频帧

<img src="https://img.saraba1st.com/forum/202311/01/034734woo8wz5my5u585md.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231101-034214.jpg</strong> (392.8 KB, 下载次数: 0)

下载附件

2023-11-1 03:47 上传

MM-vid执行流程的示例，给定一个棒球视频，MM-vid提供估计的视频长度，然后调用场景检测和ASR工具，同时收集外部知识，然后使用GPT-4V生成剪辑片段级视频描述，随后GPT-4V以视频帧和文本提示为输入，输出视频描述，最后根据剪辑片段级描述、视频元数据和ASR，使用GPT-4为输入视频生成连贯的剧本

<img src="https://img.saraba1st.com/forum/202311/01/034753pokekduddfqjpwjk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231101-033506__01.jpg</strong> (167.37 KB, 下载次数: 0)

下载附件

2023-11-1 03:47 上传

MM-vid的视频演示(项目页)

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 928#       发表于 2023-11-1 04:20

 本帖最后由 Machinery 于 2023-11-1 04:31 编辑 

VideoCrafter1

用于生成高质量视频的开源扩散模型

项目主页:https://ailab-cvc.github.io/videocrafter/

github项目主页:https://github.com/AILab-CVC/VideoCrafter

discord频道:https://discord.gg/z6veKNgV

视频生成越来越受到学术界和工业界的关注，尽管商业工具已经可以生成似是而非质量不错的视频，但可供研究人员和工程师使用的开源模型数量有限

这项工作中，介绍了两种用于高质量视频生成的扩散模型，即文本到视频(T2V/text-to-video)和图像到视频(I2V/image-to-video)模型，T2V模型根据给定的文本输入合成视频，而I2V模型则包含额外的图像输入

本文提案的T2V模型可以生成分辨率为1024×576的逼真电影质量视频，在质量方面优于其他开源T2V模型，而I2V模型则旨在生成严格遵循所提供的参考图像内容的视频，保留其内容、结构和风格，该模型是第一个开源的I2V基础模型，能够将给定图像转换为视频剪辑片段，同时对内容保持约束，相信这些开源视频生成模型可以为社区技术进步做出重大贡献

<img src="https://img.saraba1st.com/forum/202311/01/041947y5r56hr8lpwr5wwz.jpg" referrerpolicy="no-referrer">

<strong>milestone.jpg</strong> (244.51 KB, 下载次数: 0)

下载附件

2023-11-1 04:19 上传

基于扩散的视频生成基础模型的简洁但不一定全面的里程碑

<img src="https://img.saraba1st.com/forum/202311/01/041954hisi8l881jjl9xoj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231101-040512.jpg</strong> (118.4 KB, 下载次数: 0)

下载附件

2023-11-1 04:19 上传

开源的两种不同生成方式的视频基础模型工作流程

<img src="https://img.saraba1st.com/forum/202311/01/042002mjpeehvtkvhjzjhk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231101-040542.jpg</strong> (74.3 KB, 下载次数: 0)

下载附件

2023-11-1 04:20 上传

VideoCrafter1中视频扩散模型的框架，通过在自动编码器(auto-encoder)的潜在空间中训练视频UNet，以FPS作为控制生成视频运动速度的条件，对于T2V模型，只有文本提示作为交叉注意力输入到空间Transformer中，而对于I2V模型，文本和图像提示都被作为输入

<img src="https://img.saraba1st.com/forum/202311/01/042010d59to5898dcjny58.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231101-041056.jpg</strong> (51.5 KB, 下载次数: 0)

下载附件

2023-11-1 04:20 上传

图像条件分支图，U-Net主干特征Fin通过双交叉注意力层与文本和图像嵌入进行处理，其输出被融合为Fout

<img src="https://img.saraba1st.com/forum/202311/01/042019q4hc0qw1c54sz1d5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231101-041121.jpg</strong> (91.96 KB, 下载次数: 0)

下载附件

2023-11-1 04:20 上传

图像条件文本到视频生成对比

(a)条件图像输入
(b)以全局语义Token为条件的生成
(c)使用完整patch的视觉Tokens作为条件生成，使用的文字提示是“a beautiful girl with colorful hair”

<img src="https://img.saraba1st.com/forum/202311/01/043116en4np194a11wfff9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231101-043103.jpg</strong> (58.95 KB, 下载次数: 0)

下载附件

2023-11-1 04:31 上传

项目页的相关许可
 - 引用：如果您在研究中使用代码、模型和数据，或者受到我们工作的启发，请引用(https://ailab-cvc.github.io/videocrafter/citation.txt)
 - 许可证：代码、模型和数据根据Apache 2.0许可证分发(https://github.com/AILab-CVC/SEED/blob/main/License.txt)

<img src="https://img.saraba1st.com/forum/202311/01/042030kuzhfhyyevko2y42.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231101-041008.jpg</strong> (560.47 KB, 下载次数: 0)

下载附件

2023-11-1 04:20 上传

<img src="https://img.saraba1st.com/forum/202311/01/042030h6ugw4fe5uusiuug.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231101-041652.jpg</strong> (609.41 KB, 下载次数: 0)

下载附件

2023-11-1 04:20 上传

与Gen-2、Pika Labs、I2VGen-XL和Zeroscope-XL的视觉对比

<img src="https://img.saraba1st.com/forum/202311/01/042037id0w434400ccei3x.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231101-041619.jpg</strong> (169.93 KB, 下载次数: 0)

下载附件

2023-11-1 04:20 上传

<img src="https://img.saraba1st.com/forum/202311/01/042037nvztdehmmtetweyr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231101-041640.jpg</strong> (152.15 KB, 下载次数: 0)

下载附件

2023-11-1 04:20 上传

人类偏好对齐结果与用户研究结果

<img src="https://img.saraba1st.com/forum/202311/01/042137anfeo7noan3oin63.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231101-041705__01.jpg</strong> (278.41 KB, 下载次数: 0)

下载附件

2023-11-1 04:21 上传

不同VideoCrafter文本转视频版本之间视觉质量的对比

提示分别是“In Marvel movie style, supercute siamese cat as sushi chef”、“A wise tortoise in a tweed hat and spectacles reads a newspaper, Howard Hodgkin style”和“hand-held camera, a politician giving a speech at a podium”

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  gx19860411  
##### 929#       发表于 2023-11-1 10:59

求楼主给推荐个chatgpt的前端，现在用的chat酱没法上传文件也没法使用4的返图功能。如果支持api2d那就再好不过了。谢谢<img src="https://static.saraba1st.com/image/smiley/face2017/039.png" referrerpolicy="no-referrer">

—— 来自 Xiaomi M2011K2C, Android 13上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.5.4


*****

####  dangoron  
##### 930#       发表于 2023-11-1 11:33

跟了好久的贴了，好奇lz是怎么跟进最新的成果的，是在推特关注了特定的tag吗<img src="https://static.saraba1st.com/image/smiley/face2017/091.png" referrerpolicy="no-referrer">


*****

####  Machinery  
##### 931#       发表于 2023-11-1 17:03

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=62901221&amp;ptid=2126390" target="_blank">gx19860411 发表于 2023-11-1 10:59</a>
求楼主给推荐个chatgpt的前端，现在用的chat酱没法上传文件也没法使用4的返图功能。如果支持api2d那就再好 ...</blockquote>
没怎么用过chatgpt的前端<img src="https://static.saraba1st.com/image/smiley/face2017/068.png" referrerpolicy="no-referrer">这个真不太清楚
不过可以考虑下去github搜下chatgpt然后按most stars排序，挨个看看

<img src="https://img.saraba1st.com/forum/202311/01/170310ledbqj83zobue3b2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231101-170119.jpg</strong> (395.74 KB, 下载次数: 0)

下载附件

2023-11-1 17:03 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)

*****

####  Machinery  
##### 932#       发表于 2023-11-1 17:07

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=62901786&amp;ptid=2126390" target="_blank">dangoron 发表于 2023-11-1 11:33</a>
跟了好久的贴了，好奇lz是怎么跟进最新的成果的，是在推特关注了特定的tag吗 ...</blockquote>
<img src="https://static.saraba1st.com/image/smiley/face2017/068.png" referrerpolicy="no-referrer">有一部分是的，项目组一般都会去推特推广一下自己做的项目，关注多的话确实很容易刷到，其他的，经常看SOTA排名和机器学习社区，相关资讯和论文，都是内容比较丰富的，再慢慢整理，当然也有很多项目至今还是coming soon

—— 来自 [S1Fun](https://s1fun.koalcat.com)

*****

####  dangoron  
##### 933#       发表于 2023-11-1 17:10

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=62905872&amp;ptid=2126390" target="_blank">Machinery 发表于 2023-11-1 17:07</a>

有一部分是的，项目组一般都会去推特推广一下自己做的项目，关注多的话确实很容易刷到，其他的， ...</blockquote>
感谢回复，请问机器学习社区有什么推荐的吗<img src="https://static.saraba1st.com/image/smiley/face2017/033.png" referrerpolicy="no-referrer">


*****

####  Machinery  
##### 934#       发表于 2023-11-1 17:56

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=62905912&amp;ptid=2126390" target="_blank">dangoron 发表于 2023-11-1 17:10</a>
感谢回复，请问机器学习社区有什么推荐的吗还有大佬的推特方便私信一个吗，想关注一下

 ...</blockquote>
我推特都是空的<img src="https://static.saraba1st.com/image/smiley/face2017/037.png" referrerpolicy="no-referrer">

深度学习社区的话倒是有一些，可以看机器之心的总览(https://www.jiqizhixin.com/columns)

—— 来自 [S1Fun](https://s1fun.koalcat.com)

*****

####  Machinery  
##### 935#       发表于 2023-11-1 17:59

jina-embeddings-v2

Jina AI开源的8K长度文本嵌入(text embedding)模型

项目博客:https://jina.ai/news/jina-ai-launches-worlds-first-open-source-8k-text-embedding-rivaling-openai/

相关介绍:https://hub.baai.ac.cn/view/32160

总部位于柏林的人工智能公司Jina AI很高兴地宣布推出第二代开源文本嵌入模型：jina-embeddings-v2
————
与OpenAI的最佳8K模型一起进行基准测试

这一尖端模型现在是唯一支持8K(8192 Token)下文长度的开源产品，在大规模文本嵌入基准(MTEB/Massive Text Embedding Benchmark)排行榜上(相关链接:https://huggingface.co/spaces/mteb/leaderboard?ref=jina-ai-gmbh.ghost.io)，能力与表现方面与OpenAI的专有文本嵌入模型text-embedding-ada-002相当

当直接与OpenAI的8K模型text-embedding-ada-002进行对比时，jina-embeddings-v2展现了它的实力，下图是性能对比表格，突出显示了jina-embeddings-v2特别擅长的领域：

<img src="https://img.saraba1st.com/forum/202311/01/175800mo05ovljvxx05vjj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231101-173035__01.jpg</strong> (46.07 KB, 下载次数: 0)

下载附件

2023-11-1 17:58 上传

可以看出，jina-embedding-v2在分类平均(Classification Average)、重新排名平均(Reranking Average)、检索平均(Retrieval Average)和总结平均(Summarization Average)方面优于OpenAI同类产品
————
特点与优点

1.从草图到成品：jina-embeddings-v2是从零开始构建的，在过去的三个月里，Jina AI团队进行了密集的研究开发、数据收集和微调，其最终成果是一个标志着其相对前身重大飞跃的模型

2.使用8K扩展上下文潜力：jina-embeddings-v2不仅仅是一项技术成就，其8K 上下文长度为新的行业应用打开了大门：

法律分析：确保能够捕获和分析大量法律文本中的每个细节
医学研究：全面嵌入科学论文以进行高级分析和发现
文学分析：深入研究长篇内容，捕捉微妙的主题元素
财务预测：从详细的财务报告中获得卓越的见解
对话智能：改进聊天机器人对复杂用户查询的响应

基准测试显示，在多个数据集中，这种扩展上下文使jina-embeddings-v2的性能优于其他领先的基础嵌入模型，强调了更长上下文能力带来的实际优势

<img src="https://img.saraba1st.com/forum/202311/01/175837k63b54jjsz35ha13.png" referrerpolicy="no-referrer">

<strong>Screenshot-from-2023-10-23-17-41-40.png</strong> (267.17 KB, 下载次数: 0)

下载附件

2023-11-1 17:58 上传

3.作为可用性的体现，两个模型都可以在Huggingface上免费下载：
基础模型(0.27G) - 专为需要更高准确度的重型任务而设计，例如学术研究或商业分析
小型模型(0.07G) - 专为轻量级应用程序而设计，例如移动应用程序或计算资源有限的设备

4.满足不同需求的规模选项：了解 AI 社区的多样化需求，Jina AI提供了两个版本的模型

基础模型相关链接:https://huggingface.co/jinaai/jina-embeddings-v2-base-en?ref=jina-ai-gmbh.ghost.io

小型模型相关链接:https://huggingface.co/jinaai/jina-embeddings-v2-small-en?ref=jina-ai-gmbh.ghost.io
————
对于未来的愿景

Jina AI致力于引领人工智能创新前沿，以下是路线图的下一步：

学术见解：一篇详细介绍jina-embeddings-v2的技术复杂度和基准的学术论文即将发表，让 AI 社区能够获得更深入的见解

API 开发：该团队正在开发类似OpenAI的嵌入API平台的高级阶段，这将使用户能够根据自己的需求轻松扩展嵌入模型

语言扩展：Jina AI将会进军多语言嵌入领域，着眼于推出德语-英语模型，进一步扩展其功能

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  qieqie  
##### 936#       发表于 2023-11-1 18:55

在8k数据集上其它模型的输入是truncated 512? 咋不和分chunk或者摘要的方法做一个对比呢。<img src="https://static.saraba1st.com/image/smiley/face2017/001.png" referrerpolicy="no-referrer">


*****

####  Machinery  
##### 937#       发表于 2023-11-1 19:47

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=62907208&amp;ptid=2126390" target="_blank">qieqie 发表于 2023-11-1 18:55</a>
在8k数据集上其它模型的输入是truncated 512? 咋不和分chunk或者摘要的方法做一个对比呢。 ...</blockquote>
<img src="https://static.saraba1st.com/image/smiley/face2017/068.png" referrerpolicy="no-referrer">我也觉得直接截断是不是不太好，不过目前就这么一个图，之后看看论文上了的话里边会不会有更多对比

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 938#       发表于 2023-11-1 20:08

BlueLM

BlueLM是由vivo AI全球研究院自主研发的大规模预训练语言模型

github项目主页:https://github.com/vivo-ai-lab/BlueLM

本次发布包含7B基础(base)模型和7B对话(chat)模型，同时开源了支持32K的长文本基础(base)模型和对话(chat)模型

github项目说明:

<img src="https://img.saraba1st.com/forum/202311/01/200827doxxe7toey8qrrey.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231101-200632.jpg</strong> (350.55 KB, 下载次数: 0)

下载附件

2023-11-1 20:08 上传

<img src="https://img.saraba1st.com/forum/202311/01/200827qhm4dmqq3yczwz44.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231101-200646.jpg</strong> (109.62 KB, 下载次数: 0)

下载附件

2023-11-1 20:08 上传

<img src="https://img.saraba1st.com/forum/202311/01/200827fuh61hyuzuuh3377.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231101-200659.jpg</strong> (134.92 KB, 下载次数: 0)

下载附件

2023-11-1 20:08 上传

<img src="https://img.saraba1st.com/forum/202311/01/200827baw8hyyr8yd83r1a.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231101-200710.jpg</strong> (167.22 KB, 下载次数: 0)

下载附件

2023-11-1 20:08 上传

<img src="https://img.saraba1st.com/forum/202311/01/200827wyuuxsxxfgvf1e1u.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231101-200730.jpg</strong> (199.04 KB, 下载次数: 0)

下载附件

2023-11-1 20:08 上传

<img src="https://img.saraba1st.com/forum/202311/01/200827imbomm4lxxs3xsk5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231101-200740.jpg</strong> (120.35 KB, 下载次数: 0)

下载附件

2023-11-1 20:08 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 939#       发表于 2023-11-2 19:20

SEINE

用于生成过渡和预测的短到长(Short-to-Long)视频扩散模型

项目主页:https://vchitect.github.io/SEINE-project/

github项目代码仓库:https://github.com/Vchitect/SEINE

最近的视频生成取得了实质性进展，尽管如此，现有的生成视频通常是描述单个场景的非常短的剪辑片段(shot-level)，为了提供连贯的长视频(story-level)，需要在不同的剪辑片段之间生成创造性的过渡和预测效果

本文提出了一种从短到长的视频扩散模型SEINE，专注于生成过渡和预测，最终目标是生成高质量的长视频，在场景和不同长度的shot-level视频之间实现平滑且富有创意的过渡

具体来说，提出了一种随机掩码视频扩散模型(random-mask video diffusion model)，用于根据文本描述自动生成过渡，通过提供不同场景的图像作为输入，并结合基于文本的控制，模型可以生成可确保连贯性和视觉质量的过渡视频

此外，该模型可以轻松扩展到各种任务，例如图像到视频动画和自回归视频预测，为了对这一新的生成任务进行全面评估，还提出了平滑和创造性过渡的三个关键评估标准：时间一致性(temporal consistency)、语义相似性(semantic similarity)和视频文本语义对齐(video-text semantic alignment)

大量的实验验证了本文方法相对于现有的生成过渡和预测方法的有效性，从而能够创建story-level的长视频

<img src="https://img.saraba1st.com/forum/202311/02/191859ue4jnva0fx0f6c8r.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231102-190044.jpg</strong> (163.33 KB, 下载次数: 0)

下载附件

2023-11-2 19:18 上传

生成的样本，提案的S2L(Short-to-long)模型能够通过给出文本描述来合成高清过渡和预测视频

<img src="https://img.saraba1st.com/forum/202311/02/191907uu272dy22jfx92zh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231102-190255.jpg</strong> (143.76 KB, 下载次数: 0)

下载附件

2023-11-2 19:19 上传

S2L的工作流程，S2L视频生成模型可以将不同场景的镜头与转场无缝连接，并通过自回归预测生成不同长度的视频，方便创建story-level视频，红色框代表过渡视频，蓝色框代表通过预测生成的长视频

<img src="https://img.saraba1st.com/forum/202311/02/191913hn3uin6os84isndk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231102-190542.jpg</strong> (94.87 KB, 下载次数: 0)

下载附件

2023-11-2 19:19 上传

生成转换目标的符号和示意图，生成转换表现出每个帧xn与两个场景图像之间的语义相似性； 其中每个帧xn及其相邻帧xn−1和xn+1应该是时间相干( temporal coherence)的； 生成的帧的语义应与提供的文本描述保持一致

<img src="https://img.saraba1st.com/forum/202311/02/191921udy2lssdzjr228yu.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231102-191013.jpg</strong> (122.81 KB, 下载次数: 0)

下载附件

2023-11-2 19:19 上传

提案方法的概览图

<img src="https://img.saraba1st.com/forum/202311/02/191934zexhcv6nrxbhbb1q.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231102-191108.jpg</strong> (261.2 KB, 下载次数: 0)

下载附件

2023-11-2 19:19 上传

与现有方法的定性对比
左: Spiderman becomes into a sand sculpture. 
右: A cat from sitting on the coach transfer to lying on the sand.

<img src="https://img.saraba1st.com/forum/202311/02/191941m57hkz7kfh6fhfhz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231102-191222.jpg</strong> (101.33 KB, 下载次数: 0)

下载附件

2023-11-2 19:19 上传

指标测试结果与人类偏好调查结果

<img src="https://img.saraba1st.com/forum/202311/02/191949u4xjf00qzvx9vvsx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231102-191316.jpg</strong> (369.11 KB, 下载次数: 0)

下载附件

2023-11-2 19:19 上传

派生的过渡结果与文本控制的过渡结果

<img src="https://img.saraba1st.com/forum/202311/02/191956ax347cq7739xrx93.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231102-191456.jpg</strong> (219.02 KB, 下载次数: 0)

下载附件

2023-11-2 19:19 上传

自回归生成结果对比

<img src="https://img.saraba1st.com/forum/202311/02/192002t979ggjfrg7fjz7x.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231102-191638.jpg</strong> (104.7 KB, 下载次数: 0)

下载附件

2023-11-2 19:20 上传

图像动画化结果

<img src="https://img.saraba1st.com/forum/202311/02/192010v72ftee1n1tooyhs.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231102-191715.jpg</strong> (335.17 KB, 下载次数: 0)

下载附件

2023-11-2 19:20 上传

过渡样本

<img src="https://img.saraba1st.com/forum/202311/02/192016ni71hqlyvdqrhjvz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231102-191744.jpg</strong> (281.89 KB, 下载次数: 0)

下载附件

2023-11-2 19:20 上传

图像到视频动画化结果

<img src="https://img.saraba1st.com/forum/202311/02/192022xum5re49ubysusnu.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231102-191812.jpg</strong> (310.84 KB, 下载次数: 0)

下载附件

2023-11-2 19:20 上传

失败案例

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 940#       发表于 2023-11-2 20:52

LLaVA-Interactive

用于图像聊天、分割、生成和编辑的一体化(All-in-One)演示

项目页面:https://llava-vl.github.io/llava-interactive/

github项目主页:https://github.com/LLaVA-VL/LLaVA-Interactive-Demo

演示Demo:https://6dd3-20-163-117-69.ngrok-free.app/

LLaVA-Interactive是多模态人类与人工智能交互的研究原型，该系统可以通过获取多模态用户输入并生成多模态响应来与人类用户进行多轮对话

重要的是，LLaVA-Interactive超越了单纯的语言提示，也可以使用视觉提示在交互中对齐人类意图，LLaVA-Interactive的开发非常具有成本效益，因为该系统结合了预构建AI模型的三种多模态技能，无需额外的模型训练：LLaVA的视觉聊天、SEEM的图像分割以及GLIGEN的图像生成和编辑

提出了一系列不同的应用场景来展示LLaVA-Interactive的前景，希望可以启发多模态交互系统的未来研究
————
大型语言模型(LLM)的快速发展彻底改变了聊天机器人系统，带来了前所未有的智能水平，例如OpenAI的ChatGPT

ChatGPT在语言任务上的成功启发了社区在多模态空间中预期类似的成功范例，其中语言和视觉(LV/language and vision)模态都将参与人机交互以解锁许多新场景，致使越来越多的研究课题目标是构建通用助手，GPT-4V就是这样一个例子，它向前迈出了一步，展示了具有语言图像输入和语言输出的聊天机器人的有趣功能

然而，尽管GPT-4V的性能令人印象深刻，但其局限性在于:
1.它主要是一个大型的语言交互系统，输入图像仅起到为聊天提供额外上下文的作用
2.其训练方法和架构细节仍不清楚，阻碍了该领域的研究和开源创新

为了演示多模态空间中通用助手的新应用场景，本文引入了LLaVA-Interactive，一个开源演示系统，由三个强大的LV模型和易于使用的可扩展框架支持，LLaVA-Interactive的作用在于：
1.视觉交互，除了视觉聊天之外，它还支持视觉提示，允许用户绘制笔画和边界框，以更好地表达视觉创作过程中的人类意图(包括图像分割和生成/编辑)，因此，在遵循人类意图方面，与GPT-4V/LLaVA相比，LLaVA-Interactive展示了更具参与性的人机交互体验
2.开源，公开了演示系统和代码库，以促进社区未来的改进，这篇文章对LLaVA-Interactive的新功能进行了初步评估，并描述了其工作流程和服务的基础设施，同时还邀请社区与在线演示进行互动，以测试这个多模态聊天机器人的功能
————
该图提供了LLaVA-Interactive的工作流程，同时下方描述了一种典型的视觉创作过程:

<img src="https://img.saraba1st.com/forum/202311/02/205150khxqyyl66fllf6ys.png" referrerpolicy="no-referrer">

<strong>llava_interactive_workflow.png</strong> (171.59 KB, 下载次数: 0)

下载附件

2023-11-2 20:51 上传

1.图像输入：首先需要一张图像，用户可以上传图像，或者通过指定其语言标题并为对象的预期空间布局绘制边界框来生成图像，图像准备好后，可以通过应用以下三个步骤之一来处理图像：聊天、分割或编辑
2.视觉聊天：询问有关图像的任何问题，例如如何修改图像的建议，根据编辑建议，可以分别使用步骤3或步骤4删除或添加新对象。
3.交互式分割：可以使用笔画或文本提示来分割对象蒙版(object mask)，如果要删除它，请将蒙版拖出图像，背景将自动填充，或者，可以将蒙版拖到不同的位置，要填充新对象，请提供蒙版的文本提示
4.基准编辑：通过绘制边界框并关联预期的对象的相应概念，可以将新对象直接放置在图像上
5.多轮交互：重复步骤2、3或4，迭代完善视觉创作
————
能力对比
基于仅允许视觉聊天的图像输入的LLaVA，LLaVA-Interactive将其扩展为支持视觉交互，例如用户绘制的笔画和边界框，以及视觉图像生成/编辑，请参阅以下功能比较：

<img src="https://img.saraba1st.com/forum/202311/02/205200p7ka69q6kff9nwhj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231102-204143.jpg</strong> (48.96 KB, 下载次数: 0)

下载附件

2023-11-2 20:52 上传

————
隐藏在幕后的：独立模型
LLaVa-Interactive是一款一体化演示，它在一个交互式会话中连接三个LV模型，用于图像聊天、分割和生成/编辑，它可以比单独的单个模型完成更复杂的任务，作为背景，为对关键技术感兴趣的人简要描述各个模型:
1.LLaVA：大型语言和视觉助手，GPT-4V的第一个开源替代品，它是一种端到端训练的大型多模态模型，结合了CLIP视觉编码器和Vicuna，用于通用视觉理解和推理，模仿GPT-4V的精神，实现了令人印象深刻的聊天功能
2.SEEM：通过多模态提示一次性对所有内容进行分割，SEEM允许用户使用不同类型的提示轻松分割图像，包括视觉提示(点、标记、框、涂鸦)和语言提示，它还可以与任何提示组合一起使用或推广到自定义提示
3.GLIGEN：基准语言到图像生成(Grounded-Language-to-Image Generation)，一种开源模型，它扩展了现有预训练文本到图像扩散模型的功能，使它们能够以视觉提示(例如边界框)为条件
————
发展挑战
 LLaVA-Interactive是一个系统级协同Demo，它利用现有模型检查点来构建通用助理/代理，无需任何额外的模型训练，虽然训练 AI 模型的要求很低，但也带来了一些技术挑战，在开发LLaVA-Interactive时已经解决了如下挑战:
1.面临的一个挑战是GLIGEN重绘模型并不是为处理填充背景空孔洞而设计的 ，相反，使用LAMA进行背景填充
2.另一个挑战是Gradio对用户交互(例如拖放)没有足够的支持，通过实现启用此功能的新Gradio Image组件工具来解决此问题
3.将多个项目和模型集成在一起的复杂性，每个项目和模型都已经很复杂了，通过尝试不同的方法并创建非常干净的UI布局和高效的数据共享方案来克服这个问题
4.最后一个挑战是管理不同的包需求和依赖关系，通过运行不同的模型(例如LAMA)作为单独的Web服务来解决这个问题
————
案例研究

<img src="https://img.saraba1st.com/forum/202311/02/205222q7k49kntsz14q6gs.png" referrerpolicy="no-referrer">

<strong>example_lake_editing.png</strong> (888.03 KB, 下载次数: 0)

下载附件

2023-11-2 20:52 上传

<img src="https://img.saraba1st.com/forum/202311/02/205222kb2w8yee4b0mb0wv.png" referrerpolicy="no-referrer">

<strong>LLaVA_Interactive-13.png</strong> (434.97 KB, 下载次数: 0)

下载附件

2023-11-2 20:52 上传

<img src="https://img.saraba1st.com/forum/202311/02/205222p1i2eibe2yceyoog.png" referrerpolicy="no-referrer">

<strong>LLaVA_Interactive-14.png</strong> (282 KB, 下载次数: 0)

下载附件

2023-11-2 20:52 上传

<img src="https://img.saraba1st.com/forum/202311/02/205222t75eheftk5n7jfek.png" referrerpolicy="no-referrer">

<strong>LLaVA_Interactive-18.png</strong> (442.11 KB, 下载次数: 0)

下载附件

2023-11-2 20:52 上传

<img src="https://img.saraba1st.com/forum/202311/02/205222szgu9y2uc212su92.png" referrerpolicy="no-referrer">

<strong>LLaVA_Interactive-19.png</strong> (278.77 KB, 下载次数: 0)

下载附件

2023-11-2 20:52 上传

<img src="https://img.saraba1st.com/forum/202311/02/205222dcsn3gsa1azlgmpn.png" referrerpolicy="no-referrer">

<strong>LLaVA_Interactive-20.png</strong> (479.17 KB, 下载次数: 0)

下载附件

2023-11-2 20:52 上传

<img src="https://img.saraba1st.com/forum/202311/02/205222npzbqovhoo9o2zov.png" referrerpolicy="no-referrer">

<strong>LLaVA_Interactive-21.png</strong> (335.29 KB, 下载次数: 0)

下载附件

2023-11-2 20:52 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 941#       发表于 2023-11-3 03:11

Distil-Whisper

通过大规模伪标签(Pseudo Labelling)进行稳健的知识蒸馏

github项目代码仓库:https://github.com/huggingface/distil-whisper

随着预训练语音识别模型规模的增加，在低延迟条件下或资源受限的环境中运行这些大型模型变得具有挑战性，在这项工作中，通过利用伪标签聚合了一个大规模的开源数据集，用它来将Whisper模型蒸馏成一个较小的变体，称为Distil-Whisper

使用简单的错误率(WRT/word error rate)启发法，通过仅选择最高质量的伪标签进行训练，蒸馏模型的速度提高了5.8倍，参数减少了51%，同时在零样本迁移设置中对分布外测试数据(out-of-distribution test data)的性能误差在1%以内

Distil-Whisper维持了Whisper模型在困难的声学条件下的稳健性，同时在长格式音频上不易出现幻觉错误，通过使用Distil-Whisper与Whisper配合使用进行推测性解码(speculative decoding)，产生了2倍的加速，同时在数学上确保与原始模型相同的输出

为了促进该领域的进一步研究，研究组公开了训练代码、推理代码和模型

<img src="https://img.saraba1st.com/forum/202311/03/031004m2m2xje420877030.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231103-025436.jpg</strong> (54.2 KB, 下载次数: 0)

下载附件

2023-11-3 03:10 上传

预训练Whisper检查点的模型详细信息

<img src="https://img.saraba1st.com/forum/202311/03/031008h4gs2j1ut3m93c32.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231103-025528.jpg</strong> (127.29 KB, 下载次数: 0)

下载附件

2023-11-3 03:10 上传

用于训练的开源数据集的摘要信息，对于某些数据集，无法可靠地检索说话者的数量，因此将这些条目表示为“unknown”

<img src="https://img.saraba1st.com/forum/202311/03/031014vsd7qj9mqan9w47m.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231103-025630.jpg</strong> (158.77 KB, 下载次数: 0)

下载附件

2023-11-3 03:10 上传

Distil-Whisper模型的架构，编码器(绿色)完全从教师复制到学生并在训练期间冻结，学生的解码器仅由两个解码层组成，参数是从教师的第一个和最后一个解码层初始化的(红色)，教师的所有其他解码层都被丢弃，该模型根据KL散度和PL损失项的加权和进行训练

<img src="https://img.saraba1st.com/forum/202311/03/031018xwbghigfhbvsibvw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231103-025845.jpg</strong> (40.56 KB, 下载次数: 0)

下载附件

2023-11-3 03:10 上传

Distil-Whisper检查点的模型详细信息

<img src="https://img.saraba1st.com/forum/202311/03/031054kf212ag125fdhzn2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231103-025913.jpg</strong> (124.22 KB, 下载次数: 0)

下载附件

2023-11-3 03:10 上传

用于短期和长期评估的OOD数据集摘要信息

<img src="https://img.saraba1st.com/forum/202311/03/031103rwutgsegw24q4sru.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231103-030035.jpg</strong> (78.53 KB, 下载次数: 0)

下载附件

2023-11-3 03:11 上传

Distil-Whisper维持了Whisper模型的WER性能，但推理速度更快，图为四个OOD短式测试集和4个OOD长式测试集的平均WER结果，相对延迟是相对于Large-v2检查点的推理时间，对于短式评估，批大小(batch size)设置为1，对于长格式评估，使用分块(chunked)长式转录算法，批大小为16

<img src="https://img.saraba1st.com/forum/202311/03/031108lccx1j0685qxah3j.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231103-030303.jpg</strong> (47.93 KB, 下载次数: 0)

下载附件

2023-11-3 03:11 上传

跨越各种数据集的有效稳健性，一个ID参考数据集和四个OOD数据集的WER结果，相对错误率(RER)显示在右侧，给出了每个数据集的有效稳健性分数，宏观平均结果显示在底行中

<img src="https://img.saraba1st.com/forum/202311/03/031125yp74nse2ui2m7u84.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231103-030312.jpg</strong> (32.77 KB, 下载次数: 0)

下载附件

2023-11-3 03:11 上传

长式转录算法的对比，顺序和分块长式算法的四个OOD长式测试集的平均WER结果，相对延迟是相对于具有顺序长式解码的Large-v2模型的推理时间，使用批大小16报告分块转录结果

<img src="https://img.saraba1st.com/forum/202311/03/031136nz3t0048p04ay3ou.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231103-030714.jpg</strong> (188.42 KB, 下载次数: 0)

下载附件

2023-11-3 03:11 上传

噪声对WER性能的影响

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 942#       发表于 2023-11-3 04:05

dediffusion

去扩散(De-Diffusion)使文本成为强大的跨模态交互界面(interface)

项目主页:https://dediffusion.github.io/

Code:[coming soon!]

将文本作为强大的跨模态交互界面，相对于那些依靠深度嵌入来连接图像和语言作为交互界面表征的方法，本文方法是将图像表示为文本，从中可以享受自然语言固有的可解释性和灵活性

通过采用自动编码器(autoencoder)，该编码器使用预训练的文本到图像扩散模型进行解码，编码器经过训练将输入图像转换为文本，然后将其作为输入送入固定的文本到图像扩散解码器中用以重建原始输入，进行称之为去扩散的过程

实验验证了去扩散文本表征图像的精度和全面性，这样它就可以很容易地被现成的文本到图像工具和LLM用于各种多模态任务，例如，单个去扩散模型可以泛化为不同的文本到图像工具提供可转移的提示，并且还可以通过简单地用很少的提示来提示大型语言模型，从而在开放式视觉语言任务上实现新的SOTA

<img src="https://img.saraba1st.com/forum/202311/03/040247cbpizitztbobha83.jpg" referrerpolicy="no-referrer">

<strong>7e296b27-e971-4b07-90fe-884dabfe1eef.jpg</strong> (164.69 KB, 下载次数: 0)

下载附件

2023-11-3 04:02 上传

去扩散是一种自动编码器，其解码器是预训练的文本到图像扩散模型，它将输入图像编码为一段信息丰富的文本，其中混合了图像中存在的全面的语义概念，形成了“​​乱序字幕说明(scrambled caption)”

为了便于说明，已经按颜色对语义进行了分组，去扩散文本可以充当不同模态之间的灵活接口，例如，支持多种视觉语言应用程序，其中包括：为不同的文本到图像工具提供可转移的提示;支持纯文本聊天机器人(例如Bard);进行多模态对话;通过少样本示例将图像上下文注入现成的大型语言模型(例如PaLM2)以执行开放式视觉问答

<img src="https://img.saraba1st.com/forum/202311/03/040259onxd0n5z904194yu.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231103-034018.jpg</strong> (56.81 KB, 下载次数: 0)

下载附件

2023-11-3 04:02 上传

去扩散的构架，整体结构是一个自动编码器，预训练的文本到图像扩散模型作为解码器，文本作为潜在表示，以及由图像主干和注意力池组成的图像到文本编码器，锁定和解锁分别表示冻结权重和可学习权重，使用了Gumbel-softmax来处理离散的文本Token

<img src="https://img.saraba1st.com/forum/202311/03/040338owh5xtww3jqewxqj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231103-034540.jpg</strong> (47.21 KB, 下载次数: 0)

下载附件

2023-11-3 04:03 上传

通过文本到图像重建评估了不同的字幕说明方法，文本到图像模型是预先训练的Stable Diffusion v2基础模型

报告了30K MS-COCO(2014)验证分割的256×256图像的FID(↓)，去扩散比人工标注的字幕、BLIP-2(在MS-COCO上微调)和PaLI-X(多任务字幕说明模型)获得了更好的FID

<img src="https://img.saraba1st.com/forum/202311/03/040358zphp6bqkhhhr6aqb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231103-034851.jpg</strong> (269.02 KB, 下载次数: 0)

下载附件

2023-11-3 04:03 上传

视觉语言少样本学习，报告了VQAv2开放式设置和OKVQA视觉问答的VQA准确性，以及MS-COCO图像字幕说明的CIDEr，粗体表示最佳性能，下划线表示每列中第二好的性能，ID域内COCO图像被用于训练

<img src="https://img.saraba1st.com/forum/202311/03/040406qcrcu3bvmc1uk4rv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231103-035131.jpg</strong> (181.33 KB, 下载次数: 0)

下载附件

2023-11-3 04:04 上传

使用现成的LLM进行VQA，其中参考图像的去扩散文本插入到LLM提示中的“图像上下文”之后，然后LLM完成提示以回答视觉问题，去扩散文本提供了丰富的视觉细节，例如A中的泰迪熊和B中火车的红色外表，使用了PaLM 2-L作为LLM，样本来自OKVQA

<img src="https://img.saraba1st.com/forum/202311/03/040422qrdd2wfn1rr288rj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231103-035417.jpg</strong> (70.29 KB, 下载次数: 0)

下载附件

2023-11-3 04:04 上传

与VQAv2和OKVQA的val分割上的其他字幕说明进行对比，BLIP-2代表顶级字幕模型，人工字幕来自MS-COCO标注，使用了PaLM 2-L

<img src="https://img.saraba1st.com/forum/202311/03/040427s0riln1o0ru7r2lj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231103-035602.jpg</strong> (78.83 KB, 下载次数: 0)

下载附件

2023-11-3 04:04 上传

与现成的纯文本聊天机器人进行多模态对话，其中去扩散文本插入在ChatGPT-3.5和Bard的文本提示中的“图像上下文”之后

<img src="https://img.saraba1st.com/forum/202311/03/040433g00ux0q0qppbmbrg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231103-035746.jpg</strong> (170.39 KB, 下载次数: 0)

下载附件

2023-11-3 04:04 上传

miniImageNet上的开放式单样本分类，其中只有LLM预测的确切类名才被认为是正确的，任务归纳是解释分类任务并在提示开头提供预期类名的介绍性文本，以前的封闭形式的最佳成绩不再强调

<img src="https://img.saraba1st.com/forum/202311/03/040439eh8bpbylhh93wwb8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231103-040018.jpg</strong> (104.62 KB, 下载次数: 0)

下载附件

2023-11-3 04:04 上传

<img src="https://img.saraba1st.com/forum/202311/03/040439j80bbet09zc2y2c2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231103-040032.jpg</strong> (76.33 KB, 下载次数: 0)

下载附件

2023-11-3 04:04 上传

消融实验

<img src="https://img.saraba1st.com/forum/202311/03/040454ltk3k711ikhhh75h.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231103-040100.jpg</strong> (551.71 KB, 下载次数: 0)

下载附件

2023-11-3 04:04 上传

<img src="https://img.saraba1st.com/forum/202311/03/040454zh4ssxhzctth2wqt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231103-040141.jpg</strong> (492.16 KB, 下载次数: 0)

下载附件

2023-11-3 04:04 上传

<img src="https://img.saraba1st.com/forum/202311/03/040454civn3ljr332ozlp3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231103-040149.jpg</strong> (600.15 KB, 下载次数: 0)

下载附件

2023-11-3 04:04 上传

<img src="https://img.saraba1st.com/forum/202311/03/040454h5u7cz3xi5vemuee.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231103-040200.jpg</strong> (545.39 KB, 下载次数: 0)

下载附件

2023-11-3 04:04 上传

使用例

—— 来自 [S1Fun](https://s1fun.koalcat.com)

*****

####  miraclePTSD  
##### 943#       发表于 2023-11-3 04:09

 本帖最后由 miraclePTSD 于 2023-11-3 04:11 编辑 

大佬们，字符串拆分命名实体识别有没有好用的库哇，尤其是地名一类的 简中


*****

####  Machinery  
##### 944#       发表于 2023-11-3 04:13

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=62920889&amp;ptid=2126390" target="_blank">miraclePTSD 发表于 2023-11-3 04:09</a>
大佬们，字符串拆分命名实体识别有没有好用的库哇，尤其是地名一类的 简中 ...</blockquote>
可以考虑用LLM做少样本示例之后json格式输出之类的，比如，hugface那一堆演示或者gpt4或者bard和claude之流，本地LLM也行

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 945#       发表于 2023-11-4 01:43

 本帖最后由 Machinery 于 2023-11-4 01:45 编辑 

LingoWhale-8B

LingoWhale-8B是由深言科技推出的语鲸系列大模型中首个开源的中英双语大语言模型

github项目主页:https://github.com/DeepLangAI/LingoWhale-8B

hugface权重仓库:https://huggingface.co/deeplang-ai/LingoWhale-8B

LingoWhale-8B模型在数万亿token的高质量中英数据上进行预训练，具有强大的基础能力，在多个公开评测基准上均达到领先效果，在预训练阶段，模型使用8K的上下文长度进行训练，能够完成更长上下文的理解和生成任务

LingoWhale-8B模型对学术研究完全开放，使用方通过邮件申请并获得官方商用许可后，即可免费商用

在开源模型权重的同时，也提供了符合用户习惯的Huggingface推理接口以及LoRA等参数高效微调示例，便于开发者快速使用LingoWhale-8B模型

受模型参数量影响，大模型固有的幻觉问题、数学计算能力相对较弱等问题在LingoWhale-8B模型中仍然存在，请大家在使用前了解这些问题，评估可能存在的风险，后续版本的LingoWhale模型将会针对此类问题进行重点优化

github项目说明:

<img src="https://img.saraba1st.com/forum/202311/04/014314zsq3skqkr88u93u8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231104-013959.jpg</strong> (380.63 KB, 下载次数: 0)

下载附件

2023-11-4 01:43 上传

<img src="https://img.saraba1st.com/forum/202311/04/014314i2d0jlzxp2pi9xdx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231104-014023.jpg</strong> (345.69 KB, 下载次数: 0)

下载附件

2023-11-4 01:43 上传

<img src="https://img.saraba1st.com/forum/202311/04/014314qmp1ikzwmksusooa.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231104-014034.jpg</strong> (83.49 KB, 下载次数: 0)

下载附件

2023-11-4 01:43 上传

<img src="https://img.saraba1st.com/forum/202311/04/014314ssy9zbmr69900i09.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231104-014123.jpg</strong> (282.88 KB, 下载次数: 0)

下载附件

2023-11-4 01:43 上传

<img src="https://img.saraba1st.com/forum/202311/04/014459wgd79qqv090l3qdv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231104-014443.jpg</strong> (29.33 KB, 下载次数: 0)

下载附件

2023-11-4 01:44 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 946#       发表于 2023-11-4 02:07

 本帖最后由 Machinery 于 2023-11-4 02:10 编辑 

Yi-6B/34B

Yi系列模型是由01.AI的开发人员从头开始训练的大型语言模型系列

github项目主页:https://github.com/01-ai/Yi

hugface权重:https://huggingface.co/01-ai

Yi系列模型第一个公开版本包含两个双语(英文/中文)基础模型，参数大小分别为6B和34B，两个模型都4K序列长度进行训练，并且在推理期间可以扩展到32K长度

————
模型评测说明

在对开源模型进行基准测试时，观察到本文的评估工作流程(pipeline)生成的结果与公共来源(例如OpenCompass)中报告的结果之间存在差异，在对这种差异进行更深入的调查后，发现各种模型可能采用了不同的提示(different prompts)、后处理策略(post-processing strategies)和采样技术(sampling techniques)，可能导致结果出现显著变化

本系列模型的提示和后处理策略与原始基准保持一致，并且在评估过程中采用贪婪解码(greedy decoding)，且不对生成的内容进行任何后处理，对于原作者未报告的分数(包括使用不同设置报告的分数)，尝试了通过本文的评估工作流程获取结果

为了广泛评估模型的能力，采用了Llama2中概述的方法，具体来说

使用包括PIQA、SIQA、HellaSwag、WinoGrande、ARC、OBQA和CSQA基准评估常识推理

使用SquAD、QuAC和BoolQ评估阅读理解能力，其中CSQA专门使用7样本(7-shot)设置进行测试，而所有其他测试均使用0样本(0-shot)配置进行

此外，还在“数学与代码”类别下报告了GSM8K(8-shot@1)、MATH(4-shot@1)、HumanEval(0-shot@1)和MBPP(3-shot@1)

由于技术限制，没有在QuAC和OBQA上测试Falcon-180，分数是通过剩余任务的平均分数得出的，由于这两项任务的得分普遍低于平均水平，因此可以相信Falcon-180B的表现并没有被低估
————
授权许可

此存储库中的源代码已根据Apache 2.0许可证获得许可，Yi系列模型全面开放供学术研究和免费商业使用，所有使用都必须遵守示范许可协议，如需申请官方商业许可，请联系(yi@01.ai)
————
github项目说明:

<img src="https://img.saraba1st.com/forum/202311/04/020658qq2swhnplmhsp2l2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231104-015433.jpg</strong> (298.1 KB, 下载次数: 0)

下载附件

2023-11-4 02:06 上传

<img src="https://img.saraba1st.com/forum/202311/04/020658ac814foh1wmogogz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231104-015445.jpg</strong> (219.35 KB, 下载次数: 0)

下载附件

2023-11-4 02:06 上传

<img src="https://img.saraba1st.com/forum/202311/04/020658oaxz4jj73g6777xa.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231104-015453.jpg</strong> (89.71 KB, 下载次数: 0)

下载附件

2023-11-4 02:06 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 947#       发表于 2023-11-4 02:54

 本帖最后由 Machinery 于 2023-11-4 03:01 编辑 

Recognize-Any-Regions

识别任何区域

github项目仓库(待整理):https://github.com/Surrey-UPLab/Recognize-Any-Regions

在例如开放世界的对象检测等任务中，理解无约束图像中各个区​​域(regions)或区块(patches)的语义，是计算机视觉中一项关键但具有挑战性的任务

基于CLIP等强大的图像级视觉语言(ViL)基础模型的成功，最近的方法试图通过使用广泛收集的大量区域标签对(region-label pairs)重新训练对比模型(contrastive model)或对齐具有区域提案的图像级表征的检测模型输出来利用其功能，尽管取得了显著的进展，但这些方法仍受制于计算密集型的训练需求、对数据噪声的敏感性以及上下文信息缺乏的困扰

为了解决这些限制，通过探索现成的基础模型的协同潜力，利用它们在定位和语义方面各自的优势，引入了一种新颖、通用且高效的区域识别架构，名为RegionSpot，旨在将来自定位基础模型(例如SAM)的位置感知(position-aware)定位知识与从ViL模型(例如CLIP)提取的语义信息集成

为了充分利用预训练的知识，同时最大限度地减少训练开销，研究组冻结了两个基础模型，将优化工作仅集中在轻量的基于注意力的知识集成模块(lightweight attention-based knowledge integration module)上

通过在开放世界对象识别背景下的大量实验，RegionSpot展示了比之前的替代方案更显著的性能改进，同时还提供了大量的计算资源节省，例如，使用8个V100 GPU就可以在一天内使用300万数据训练本文模型，同时模型在平均精度(mAP)方面也比GLIP高出了6.5%，对于更具挑战性和稀有的类别，其优势甚至高达14.8%

<img src="https://img.saraba1st.com/forum/202311/04/025330yr3rkxzhffl9tyeq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231104-023815__01.jpg</strong> (82.39 KB, 下载次数: 0)

下载附件

2023-11-4 02:53 上传

经典的区域级视觉理解架构的图示

(a)通过从裁剪区域中提取图像级ViL表征并将其合并到检测模型中来学习区域识别模型
(b)使用大量区域标签对数据集完全微调视觉和文本模型
(c)本文提案的方法，集成了预训练(冻结)定位和ViL模型，强调学习它们的表征关联

<img src="https://img.saraba1st.com/forum/202311/04/025336t90i9d399a3982hp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231104-024253.jpg</strong> (113.99 KB, 下载次数: 0)

下载附件

2023-11-4 02:53 上传

提案的RegionSpot的概览图

(a)将来自定位模型(例如SAM)的位置感知Token与ViL模型(例如CLIP)中提取的图像级特征图(image-level feature maps)集成，这种集成可以产生区域级语义Token，然后对其进行区域文本对齐
(b)基于注意力机制的跨模态特征交互设计

<img src="https://img.saraba1st.com/forum/202311/04/025342cj66qrhr5ehe69ui.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231104-024612.jpg</strong> (203.03 KB, 下载次数: 0)

下载附件

2023-11-4 02:53 上传

在LVIS数据集上使用基准答案(GT/ground-truth)框、RPN框和GLIP框设置下的开放世界零样本目标识别结果

<img src="https://img.saraba1st.com/forum/202311/04/025351gmg00d0ilit5yigy.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231104-024748.jpg</strong> (46.75 KB, 下载次数: 0)

下载附件

2023-11-4 02:53 上传

训练效率的对比

<img src="https://img.saraba1st.com/forum/202311/04/025357splriq6mrfk16m6c.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231104-024812.jpg</strong> (41.97 KB, 下载次数: 0)

下载附件

2023-11-4 02:53 上传

增加检测训练数据的效果

<img src="https://img.saraba1st.com/forum/202311/04/025404ifa3g3bx3dvrjjgj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231104-024842.jpg</strong> (47.39 KB, 下载次数: 0)

下载附件

2023-11-4 02:54 上传

LVIS上的消融实验
(a)CLIP视觉编码器的有效性
(b)位置感知Token选择
(c)RegionSpot的深度

<img src="https://img.saraba1st.com/forum/202311/04/025407k4mmlvim79kppv7q.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231104-024954.jpg</strong> (35.3 KB, 下载次数: 0)

下载附件

2023-11-4 02:54 上传

提示工程的消融实验

<img src="https://img.saraba1st.com/forum/202311/04/025412imo3606s66pdzmz6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231104-025026.jpg</strong> (238.7 KB, 下载次数: 0)

下载附件

2023-11-4 02:54 上传

GLIP-T和RegionSpot的LVIS数据集的定性预测结果，RegionSpot可以更准确地识别物体

<img src="https://img.saraba1st.com/forum/202311/04/025418qe33ebsqu0p23uc5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231104-025154.jpg</strong> (128.08 KB, 下载次数: 0)

下载附件

2023-11-4 02:54 上传

RegionSpot的交叉注意力图，这些图表明位置感知Token与整个图像的语义特征图有效对齐，在每一行中，蓝色和红色框分别对应于左图和右图

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 948#       发表于 2023-11-6 16:46

 本帖最后由 Machinery 于 2023-11-6 16:50 编辑 

XVERSE-65B

XVERSE-65B是由深圳元象科技自主研发的支持多语言的大语言模型(Large Language Model)，参数规模为650亿

hugface权重下载:https://huggingface.co/xverse/XVERSE-65B

相关介绍文章:https://www.jiqizhixin.com/articles/2023-11-06-10

本次开源的模型为底座模型 XVERSE-65B，主要特点如下:
1.模型结构：XVERSE-65B使用主流Decoder-only的标准Transformer网络结构，支持16K的上下文长度(Context Length)，能满足更长的多轮对话、知识问答与摘要等需求，模型应用场景更广泛
2.训练数据：构建了2.6万亿token的高质量、多样化的数据对模型进行充分训练，包含中、英、俄、西等40多种语言，通过精细化设置不同类型数据的采样比例，使得中英两种语言表现优异，也能兼顾其他语言效果
3.分词：基于BPE(Byte-Pair Encoding)算法，使用上百GB语料训练了一个词表大小为100,534的分词器，能够同时支持多语言，而无需额外扩展词表
4.训练框架：训练中采用FlashAttention2加速计算，3D并行基础上采用虚拟流水线(virtual pipeline)技术，降低较长流水线和16k上下文窗口产生的过高气泡率，在千卡集群的峰值算力利用率达到业界前列，同时通过集群基础设施运营、资源调度、训练框架和调度平台协同等持续优化，打造出高稳定、低中断、强容错的训练系统，将每周有效训练率提升至 98.6%

权重说明页:

<img src="https://img.saraba1st.com/forum/202311/06/164611o7kn7epkenkf5zfn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231106-164220.jpg</strong> (120.22 KB, 下载次数: 0)

下载附件

2023-11-6 16:46 上传

<img src="https://img.saraba1st.com/forum/202311/06/164611tbu6ct6a2mzo6pb8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231106-164232.jpg</strong> (161.19 KB, 下载次数: 0)

下载附件

2023-11-6 16:46 上传

<img src="https://img.saraba1st.com/forum/202311/06/164611cm4t10hmyitiihtr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231106-164244.jpg</strong> (25.32 KB, 下载次数: 0)

下载附件

2023-11-6 16:46 上传

<img src="https://img.saraba1st.com/forum/202311/06/164611ttdt4ul4k87h84ut.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231106-164308.jpg</strong> (67.24 KB, 下载次数: 0)

下载附件

2023-11-6 16:46 上传

<img src="https://img.saraba1st.com/forum/202311/06/164611kai8uk8zbi3yy989.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231106-164314.jpg</strong> (34.85 KB, 下载次数: 0)

下载附件

2023-11-6 16:46 上传

相关介绍:

<img src="https://img.saraba1st.com/forum/202311/06/164623njc7jd17fao77ygc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231106-164420.jpg</strong> (307.95 KB, 下载次数: 0)

下载附件

2023-11-6 16:46 上传

<img src="https://img.saraba1st.com/forum/202311/06/164623w14hdsa7xa4axxzx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231106-164520.jpg</strong> (522.92 KB, 下载次数: 0)

下载附件

2023-11-6 16:46 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 949#       发表于 2023-11-6 23:24

PPTC

通过完成PPT任务( PowerPoint Task)评估大型语言模型

github项目主页:https://github.com/gydpku/PPTC

最近对大型语言模型(LLM)的评估集中围绕于测试其针对基本自然语言任务的零样本/少样本能力以及将指令转换为工具API的能力

然而，尚未对LLM利用复杂工具在复杂的多模态环境中完成多轮、多模态指令的相关评估进行研究调查，为了弥补这方面的缺失，本文引入了PowerPoint任务完成(PPTC/PowerPoint Task Completion)基准来评估LLM们根据用户指令创建和编辑PPT文件的能力

PPTC包含279个涵盖不同主题的多回合会话和数百条涉及多模态操作的说明，还提出了PPTX-Match评估系统，该系统根据预测文件而不是标签API序列来评估LLM是否完成指令，因此它支持各种LLM生成的API序列

通过测试3个封闭式LLM和6个开源LLM，结果表明，GPT-4在单轮对话测试中以75.1%的准确率优于其他LLM，但在完成整个会话方面遇到了挑战，最终仅实现了6%的会话准确率

在基准测试中发现了三个主要错误原因：多轮会话的错误累积、长PPT模板处理和多模态感知，这些问题都对未来的LLM和代理者系统提出了巨大的挑战

<img src="https://img.saraba1st.com/forum/202311/06/232309fl4l4isvsl4lvll4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231106-230349.jpg</strong> (204.66 KB, 下载次数: 0)

下载附件

2023-11-6 23:23 上传

在基准测试中，模拟了人类和LLM之间的多轮对话场景，以评估LLM的PPT任务完成表现

<img src="https://img.saraba1st.com/forum/202311/06/232314tm2aah12lwwl71sb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231106-230509.jpg</strong> (272.78 KB, 下载次数: 0)

下载附件

2023-11-6 23:23 上传

说明图展示了LLM如何在会话中完成一轮任务:
(A)为了提示LLM，向其提供当前指令、之前的指令(对话历史)、PPT文件内容和API参考文件
“PPT阅读器”是将PPT文件转换为文本格式作为PPT文件内容的功能
(B)LLM生成API序列并执行它以获得预测的PPT文件
(C)评估预测文件中的属性和位置关系

<img src="https://img.saraba1st.com/forum/202311/06/232320ar3ck5yf1qprqq3r.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231106-230907__01.jpg</strong> (118.24 KB, 下载次数: 0)

下载附件

2023-11-6 23:23 上传

PPTC的统计信息
(A)会话轮数分布
(B)指令API数量分配(Token)
(C)涉及图表、表格、图片和位置的指令的分发

涉及“位置”的指令需要系统基于对空间信息的理解来进行与位置相关的操作，一项指令可能涉及多种不同的模式

<img src="https://img.saraba1st.com/forum/202311/06/232408c8hiwvmpspdp88zv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231106-231249.jpg</strong> (450.91 KB, 下载次数: 0)

下载附件

2023-11-6 23:24 上传

在基于回合和基于整个会话的评估设置中使用的推理提示

在基于回合的评估中，评估LLM当前回合的表现，并假设LLM已正确完成之前的回合，然后使用前几轮的可行API序列作为对话历史中的AI响应，并将前几轮的标签文件解析为PPT文件内容

在基于会话的评估中，评估整个会话的完成情况，并且不假设LLM已正确完成之前的轮次，使用LLM生成的API序列作为响应，并将LLM预测文件解析为PPT文件内容

<img src="https://img.saraba1st.com/forum/202311/06/232414l11ylllu1su9llv3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231106-231701.jpg</strong> (226.31 KB, 下载次数: 0)

下载附件

2023-11-6 23:24 上传

评估成绩

<img src="https://img.saraba1st.com/forum/202311/06/232421ibat5c9umbkm2mg5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231106-231731__01.jpg</strong> (112.1 KB, 下载次数: 0)

下载附件

2023-11-6 23:24 上传

举例说明了创建新PPT文件任务(任务1)和编辑PPT模板任务(任务2)的分析结果

在(A)中，报告了涉及图表、表格、图片、位置和纯文本的指令的平均回合精度，没有绘制任务2的准确度，因为该任务中没有图表说明

在(B)中，报告了GPT-4所犯的四种常见错误的比率

在(C)中，报告了依据模型大小的准确性，没有绘制任务2基于会话的准确性，因为它为零

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 950#       发表于 2023-11-7 02:22

ComVint

什么是优秀的视觉指示？ 合成复杂的视觉推理指令以进行视觉指令调整

github项目主页:https://github.com/RUCAIBox/ComVint

视觉指令调整是改进多模态大型语言模型(MLLM/Multi-modal Large Language Models)零样本泛化能力的重要方法，近期涌现出了大量不同关注焦点和特质的视觉指令数据集，使MLLM在评估基准上取得了令人惊喜的成果

为了开发更强大的MLLM，在本文中，研究了一个重要的基础问题：“什么才是优秀的视觉指令？”

通过进行全面的实证研究，发现专注于复杂视觉推理任务(complex visual reasoning tasks)的指令对于提高MLLM在评估基准上的性能特别有效

基于这一发现，设计了一种系统化方法来自动创建高质量的复杂视觉推理指令，方法采用合成-复杂化-重构范式，利用多阶段逐渐增加指令的复杂度的同时保证质量，基于这种方法，构造了由32K个示例组成的合成视觉推理指令数据集ComVint，并在其上微调了四个MLLM

实验结果表明，ComVint一致的增强了所有用于对比的MLLM的性能，例如MiniGPT-4和BLIP-2，分别在MME-Cognition上的性能提高了32.6%和28.8%

<img src="https://img.saraba1st.com/forum/202311/07/022137urehaeqwvmo6qjlq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-020615.jpg</strong> (73.94 KB, 下载次数: 0)

下载附件

2023-11-7 02:21 上传

现有的合成视觉指令数据集的对比，“Cap”为Caption的缩写，“Rea”为Reasoning的缩写

*通过将LLaVA中的多轮对话分解成单轮的问题，获得了256K VQA指令

<img src="https://img.saraba1st.com/forum/202311/07/022149e0sslknf80ss1k0w.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-020836.jpg</strong> (116.87 KB, 下载次数: 0)

下载附件

2023-11-7 02:21 上传

使用不同指令集微调MiniGPT-4和BLIP-2后在Seed-Bench和MME上的评估结果，MME-P和MME-C分别是MME-Perception和MME-Cognition的缩写，橙色阴影的单元格表示微调增强了原始MLLM的性能，蓝色表示性能下降

<img src="https://img.saraba1st.com/forum/202311/07/022154wl9jlc927awk47ot.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-021032__01.jpg</strong> (383.51 KB, 下载次数: 0)

下载附件

2023-11-7 02:21 上传

合成复杂视觉推理指令的方法，包括合成跨模态和外部知识推理指令(synthesize cross-modal and outside-knowledge reasoning instructions)、迭代复杂化和验证(iteratively complicate and verify)以及重制定指令格式(reformulate instruction formats)三个阶段

<img src="https://img.saraba1st.com/forum/202311/07/022206gtyj6avc0j9b6nz3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-021334.jpg</strong> (144.42 KB, 下载次数: 0)

下载附件

2023-11-7 02:22 上传

不同模型在不同的指令集上进行微调的性能，MME-P和MME-C分别是MME-Perception和MME-Cognition的缩写，最好的性能和第二好的性能分别用粗体和下划线字体表示，橙色阴影的单元格表示微调增强了原始MLLM性能，蓝色表示性能下降

<img src="https://img.saraba1st.com/forum/202311/07/022220y76n66r83m1uqy2s.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-021533.jpg</strong> (68.36 KB, 下载次数: 0)

下载附件

2023-11-7 02:22 上传

指令类型的消融实验，其中“C-M推理”和“O-K推理”分别代表跨模态推理指令和外部知识推理指令，“Both”代表它们的组合

<img src="https://img.saraba1st.com/forum/202311/07/022225cqk7jq2dbm927jan.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-021629.jpg</strong> (148.7 KB, 下载次数: 0)

下载附件

2023-11-7 02:22 上传

本文数据集中的两个合成指令示例以及来自五个MLLM的相应响应，这表明指令的复杂度，因为这些MLLM大多都无法正确回答问题

<img src="https://img.saraba1st.com/forum/202311/07/022230f33xjyj6xyex8yxl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-021756.jpg</strong> (184.55 KB, 下载次数: 0)

下载附件

2023-11-7 02:22 上传

性能对比，关于不同复杂度级别的指令，其中“D0”代表主指令，“D1”和“D2”分别代表第一轮复杂度和第二轮复杂度之后的指令

<img src="https://img.saraba1st.com/forum/202311/07/022235hwg5p5pniw93kwkh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-022005.jpg</strong> (68.38 KB, 下载次数: 0)

下载附件

2023-11-7 02:22 上传

指令格式的消融实验，其中“Mixer”代表三种指令格式的组合， “Avg”是“Average”的缩写

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 951#       发表于 2023-11-7 18:28

PASTA

告诉你的模型应该注意何处：LLM的事后注意力引导(Post-hoc Attention Steering)

github项目主页:https://github.com/QingruZhang/PASTA

在人类创作的文章中，经常会利用一些文本风格的微妙之处，例如粗体和斜体，来引导读者的注意力，这些文本重点对于传达的信息至关重要，当与大型语言模型(LLM)交互时，有通过类似的方法，实现需求到引导(need-steering)，使模型更加关注用户指定的信息，例如指令

然而，现有的仅限于处理纯文本的方法并不支持这种机制，这促使本文引入了事后注意力引导方法(PASTA/Post-hoc Attention STeering Approach)，这种方法允许LLM阅读用户指定标记的强调文本，为此，PASTA识别了注意力头的一小部分(a small subset of attention head)，并对它们应用了精确的注意力重新加权，将模型注意力引导到用户指定的部分，与提示一样，PASTA应用于推理时，且不需要更改任何模型参数

实验表明，PASTA可以显著增强LLM遵循用户指令或集成来自用户输入的新知识的能力，从而提高各种任务的性能(例如LLAMA-7B的平均准确度提高22%)

<img src="https://img.saraba1st.com/forum/202311/07/182657iwqipmnp4l114npp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-175403__01.jpg</strong> (105.31 KB, 下载次数: 0)

下载附件

2023-11-7 18:26 上传

PASTA使用用户指定的输入部分来引导模型生成与用户意图保持一致，通过增强(emphasizing)用户指定的上下文部分相对应的Token位置生成的分数，PASTA修改推理过程中生成的注意力分数

<img src="https://img.saraba1st.com/forum/202311/07/182714p0rzswla6z6gizas.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-180456.jpg</strong> (99.81 KB, 下载次数: 0)

下载附件

2023-11-7 18:27 上传

<img src="https://img.saraba1st.com/forum/202311/07/182714r6f8c82j9c8x2czn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-180507.jpg</strong> (98.05 KB, 下载次数: 0)

下载附件

2023-11-7 18:27 上传

LLAMA-7B和GPT-J的主要实验结果都证明了PASTA可以增强模型能力：(i)遵循用户指令(JSON格式和代词更改)；(ii)解释上下文信息(BiasBios)；(iii)解决知识冲突(CounterFact)，对于所有的分数，结果越高越好，最好的结果以粗体显示

<img src="https://img.saraba1st.com/forum/202311/07/182725vsg92i2woa91i9gx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-180909.jpg</strong> (140.74 KB, 下载次数: 0)

下载附件

2023-11-7 18:27 上传

LLAMA-7B生成的JSON格式和代词更改任务上的示例

<img src="https://img.saraba1st.com/forum/202311/07/182733y9blzvcuteazfacv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-181053.jpg</strong> (105.43 KB, 下载次数: 0)

下载附件

2023-11-7 18:27 上传

对于JSON格式化任务中提示改写的敏感性的结果，通过在提示模板中给出重新改写的指令，PASTA可以提高所有提示的零样本性能

<img src="https://img.saraba1st.com/forum/202311/07/182803mc9vb9hh0zv9umh4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-181337.jpg</strong> (55.92 KB, 下载次数: 0)

下载附件

2023-11-7 18:28 上传

LLAMA-7B在JSON格式化任务上的性能；  引导(i)所有注意力头(绿色)时;(ii)整层(黄色);(iii)层内的单个头部(蓝色提琴符)，跨层和跨注意力头的性能差异很大

<img src="https://img.saraba1st.com/forum/202311/07/182812acmt210411qpp353.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-181839.jpg</strong> (105.86 KB, 下载次数: 0)

下载附件

2023-11-7 18:28 上传

在top任务特定头之间改变头选择策略时、跨多个任务的并集以及交集结果(PASTA中使用的默认值)

<img src="https://img.saraba1st.com/forum/202311/07/182817axx3g76r2cg3zgn2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-182149.jpg</strong> (74.11 KB, 下载次数: 0)

下载附件

2023-11-7 18:28 上传

|将PASTA应用于LLAMA-7B在JSON格式和代词更改任务时的性能，改变引导头数量|H|;同时改变缩放系数α|

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 952#       发表于 2023-11-7 19:49

GLaMM

像素基准的大型多模态模型

项目主页:https://mbzuai-oryx.github.io/groundingLMM

github项目仓库:https://github.com/mbzuai-oryx/groundingLMM

数据集下载:https://mbzuai-oryx.github.io/groundingLMM/#grand-dataset

大型多模态模型(LMM/Large Multimodal Models)将大型语言模型扩展到了视觉领域，最初的LMM使用整体图像和文本提示来生成无基准(ungrounded)根据的文本响应，近期的区域级LMM则已被用来生成基于视觉基准的响应，然而，它们同时在单次仅限于引用单个对象类别，获取用户指定输入中的区域，无法提供密集的像素注意的对象基准(dense pixel-wise object grounding)

在这项工作中，提出了Grounding LMM (GLaMM)，这是第一个可以生成与自然语言相对应的无缝交织的对象分割掩码的模型，GLaMM不仅可以与对话中出现的基准对象交互，而且足够灵活，还可以接受文本和可选的视觉提示(感兴趣的区域)作为输入，这使用户能够在文本和视觉领域的各种粒度级别与模型进行交互

由于缺乏用于生成视觉基准详细对话的基准测试新设置，通过精心标注的基准对话引入了全面的评估协议，提出了基准对话生成(GCC/Grounded Conversation Generation)任务，这需要大规模自然场景中的密集基准概念，为此，还使用了提出的自动标注工作流程，创造了一个密集标注的Grounding-anything数据集(GranD)，包含750万个独特的概念，这些概念基于总共8.1亿个可用分割掩码的区域

除了GCG之外，GLaMM还可以在多个下游任务上有效执行例如引用表达分割(referring expression segmentation)、图像和区域级字幕说明(image and region-level captioning)以及视觉语言对话(vision-language conversations)等任务

<img src="https://img.saraba1st.com/forum/202311/07/194753lj61h0ejjw6jpjfo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-190219.jpg</strong> (277.89 KB, 下载次数: 0)

下载附件

2023-11-7 19:47 上传

使用GLaMM进行基准对话生成，本文的多模态对话模型可以提供基于输入图像像素级的自然语言响应，输出基准中描述了不同级别的粒度，例如事物(建筑物，树)，东西(草，天空，人行道)和对象部分(屋顶作为建筑物的子部分)以及对象属性( 白色的房子、红色的屋顶、修剪整齐的草坪)和物体关系(延伸到人行道的草、建筑物上空的天空)

现有的LMM，无论是开源的(例如 LLaVa、miniGPT4、Shikra、Kosmos-2)还是闭源的(例如GPT4-V、Bard)，都不提供像素级的基准对话功能

<img src="https://img.saraba1st.com/forum/202311/07/194804vygg13cgw3mmz1ym.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-190856.jpg</strong> (157.61 KB, 下载次数: 0)

下载附件

2023-11-7 19:48 上传

最新大型多模态模型(LMM)的对比，强调了它们的区域级理解能力，Input表示可以处理用户通过边界框定义的区域的模型，Multi-Region表示可以处理多个此类区域的模型，Output代表能够提供基准响应的模型，虽然一些方法采用外部视觉模块来理解区域，但其他方法仅依赖于LMM，这可能会略微导致定位不精确

然而，如Region Enc./Dec.所示，有一些集成了专门的视觉模块和 LMM，End-End Model将利用LMM进行区域理解的模型与使用外部模块的模型区分开来，Pixel-wise Grounding突出显示可以使用分段掩码进行响应的模型，而Multi-turn Conversation则表示可以与用户进行交互式对话的模型，其中本文提出的GLaMM因其提供全面的区域理解、像素级基准的响应、对话功能和端到端训练方法而脱颖而出

<img src="https://img.saraba1st.com/forum/202311/07/194817czrtknotdvaz1lpt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-192007.jpg</strong> (141.82 KB, 下载次数: 0)

下载附件

2023-11-7 19:48 上传

GLaMM的架构，该图说明了模型架构，展示了其提供场景级理解、区域级解释和像素级基准的能力

上图:GLaMM的核心组件，包括全局图像编码器、区域编码器、LLM、基准图像编码器和像素解码器，针对跨越不同粒度的视觉语言任务进行了紧密结合的定制，视觉到语言(V-L/vision-to-language)投影层有效地将图像特征映射到语言域，像素解码器利用语言到提示(L-P/language-to-prompt)投影层，将与分割(segmentation)相关的文本嵌入转换到解码器空间，GLaMM的一个主要功能是它能够执行我们新引入的基准对话生成(GCG)任务，这凸显了模型将特定短语锚定到图像中相应分割掩码的能力

底部:GLaMM的多种下游应用，包括引用表达分割、区域级字幕说明、图像级字幕说明和短句基准

<img src="https://img.saraba1st.com/forum/202311/07/194850l9rlvl0hgcyicgsd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-192702.jpg</strong> (122.08 KB, 下载次数: 0)

下载附件

2023-11-7 19:48 上传

GLaMM在基准对话生成(GCG)上的定性结果，给定用户查询，LMM不仅生成文本响应，还使用像素级掩码为对象、对象部分、属性和短语提供基准，显示了其详细理解能力

<img src="https://img.saraba1st.com/forum/202311/07/194857c97d8i2ixoc8xzfd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-193142.jpg</strong> (227.2 KB, 下载次数: 0)

下载附件

2023-11-7 19:48 上传

Grounding-anything数据集(GranD)的自动标注工作流程，该流程由四个级别组成，在生成基于8.1亿个区域的750万个独特概念方面发挥着关键作用

级别1详细说明了对象和属性，级别2包括简短的字幕说明和关系标记，级别3构建场景图，分层组织早期级别的信息使LLM可以进行基准的密集字幕说明生成，级别4提供额外的历史和社会背景，以丰富的视觉理解的信息

<img src="https://img.saraba1st.com/forum/202311/07/194903cjytu4jpt93s2htj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-193542.jpg</strong> (250.3 KB, 下载次数: 0)

下载附件

2023-11-7 19:49 上传

来自Grand数据集的数据集样本，自动标注工作流程为对象提供了多个语义标签和属性以及属于对象分割掩码，密集的字幕说明彻底描述了视觉场景，部分基准文本与相应的物体相关，额外的上下文提供了对场景的更深入的理解，超出了观察到的范围

<img src="https://img.saraba1st.com/forum/202311/07/194909yq938yg0l706oypu.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-194035.jpg</strong> (147.72 KB, 下载次数: 0)

下载附件

2023-11-7 19:49 上传

GranD与可用的图像和图像文本数据集的对比，GranD数据集独特地为每个图像提供了三个基准字幕说明，并包括每个标注区域的分割掩码，请注意，AS-1B数据集以灰色阴影表示它是并行工作，并且截至本发布时数据集尚未公开访问

<img src="https://img.saraba1st.com/forum/202311/07/194914gsz407fp4yc7pyce.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-194316.jpg</strong> (296.61 KB, 下载次数: 0)

下载附件

2023-11-7 19:49 上传

<img src="https://img.saraba1st.com/forum/202311/07/194914ol69rzp066rn666v.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-194412__01__01.jpg</strong> (337.4 KB, 下载次数: 0)

下载附件

2023-11-7 19:49 上传

性能对比结果

<img src="https://img.saraba1st.com/forum/202311/07/194919jq9tu1ukc4511n87.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231107-194546.jpg</strong> (263.33 KB, 下载次数: 0)

下载附件

2023-11-7 19:49 上传

GLaMM促进的多模态对话交互，该图展示了GLaMM进行多轮对话、提供详细描述、解决特定区域的询问并呈现基准对话的能力，这有效地凸显了其在复杂的视觉语言交互中的适应性，并有力地保留了LLM固有的推理能力

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 953#       发表于 2023-11-8 00:58

Ziya2

以数据为中心的学习就是LLM所需要的

hugface权重下载:https://huggingface.co/IDEA-CCNL/Ziya2-13B-Base

modelscope介绍页:https://modelscope.cn/models/Fengshenbang/Ziya2-13B-Base/summary

近年来，包括闭源和开源模型在内的各种大型语言模型(LLM)被提出，不断在多个基准上创造新的记录，然而，LLMs的发展仍然面临着一些问题，例如从头开始训练模型的成本过于高昂，持续预训练会导致灾难性遗忘等等

尽管许多此类问题在对LLMs的研究中得到了解决，但一个重要但是实际的问题仍然存在，许多研究过度追求扩大模型规模，而没有全面分析和优化学习过程中预训练数据的使用，以及在更具有成本效益的环境下于LLM训练中适当组织和利用这些数据

在这项工作中，提出了Ziya2，一个具有130亿参数的模型，采用LLaMA2作为基础模型，并在7000亿Token上进一步进行预训练，通过专注于预训练技术并使用以数据为中心的优化来增强学习过程，提高Ziya2在不同阶段的表现

实验表明，与代表性的开源模型相比，Ziya2在多个基准测试中显著优于其他模型

<img src="https://img.saraba1st.com/forum/202311/08/005801aoalbpnzt9nz9zzj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231108-003903.jpg</strong> (179.4 KB, 下载次数: 0)

下载附件

2023-11-8 00:58 上传

Ziya2的整体以数据为中心的学习过程，其中获取高质量数据的工作流程、训练策略和三阶段训练过程分别呈现在图的底部、中间和顶部，其中通过对比数据分布来说明了不同阶段的训练策略

<img src="https://img.saraba1st.com/forum/202311/08/005808a1qfiqj2zu2f2vwz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231108-004241.jpg</strong> (41.49 KB, 下载次数: 0)

下载附件

2023-11-8 00:58 上传

Ziya2中提出的以数据为中心的学习方法的概览，该方法包括五个组件：数据预处理(DP/data preprocessing)、自动评分(AS/automatic scoring)、基于规则的过滤(RF/rule-based filtering)、内容去重(CF/content de-duplication)和数据评估(DE/data evaluation)

灰色和彩色块分别表示相对于原始数据集过滤掉和保留的数据的比例

<img src="https://img.saraba1st.com/forum/202311/08/005813axgeoeps3ygbbusc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231108-004602.jpg</strong> (192.13 KB, 下载次数: 0)

下载附件

2023-11-8 00:58 上传

用于评估数据质量的指标，Method表示检测方法，Re Matching表示涉及正则表达式进行计数的方法，LM表示利用语言模型来预测相关指标，Counts表示使用统计方法来直接计数指标，Human Check是指由人工进行的手动抽查，Level表示对各个指标应用的严格程度，如果不超过千分之一，就认为其是合规的

<img src="https://img.saraba1st.com/forum/202311/08/005818ppeefpzf4rrfdrop.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231108-004836.jpg</strong> (107.9 KB, 下载次数: 0)

下载附件

2023-11-8 00:58 上传

用于训练Ziya2的高质量预训练数据集信息，“pre-training stage”说明了使用数据集的阶段；  “en”、“zh”、“multi”分别表示数据集的语言为英语、汉语、多语种；  “Sampling”是指从原始数据集中采样数据的比例

<img src="https://img.saraba1st.com/forum/202311/08/005822gh8ejgbyecygooj3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231108-005016.jpg</strong> (96.4 KB, 下载次数: 0)

下载附件

2023-11-8 00:58 上传

构建无监督和监督预训练数据的过程分为三个阶段

<img src="https://img.saraba1st.com/forum/202311/08/005826uba8d7mgv387x63y.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231108-005117.jpg</strong> (62.81 KB, 下载次数: 0)

下载附件

2023-11-8 00:58 上传

BF16和FP16浮点数表示的图示以及Ziya2-13B和Ziya-13B相对于训练步数的预训练损失

<img src="https://img.saraba1st.com/forum/202311/08/005830upww4v41wzeddp64.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231108-005338.jpg</strong> (136.83 KB, 下载次数: 0)

下载附件

2023-11-8 00:58 上传

Ziya2与其他闭源和开源LLM于六个用于LLM评估的基准数据集上的对比结果，其中粗体表示在所有开源LLM中表现最好的结果

<img src="https://img.saraba1st.com/forum/202311/08/005836p5hauwz9aqfhqhjf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231108-005524.jpg</strong> (165 KB, 下载次数: 0)

下载附件

2023-11-8 00:58 上传

Ziya2在三个训练阶段时于六个基准数据集上的性能，不同阶段的训练过程由特定训练步骤中用于训练Ziya2的token数量表示，LLaMA2在数据集上的性能用虚线表示以供参考

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 954#       发表于 2023-11-8 01:30

MFTCoder

通过多任务微调(Multitask Fine-Tuning)提升代码LLM

github项目主页:https://github.com/codefuse-ai/MFTCOder

代码大型语言模型(LLM)已成为一个专门的研究领域，其研究致力于通过对预训练模型进行微调来增强模型的编码能力，以前的微调方法通常是针对特定的下游任务或场景进行量身定制的，这意味着每个任务都需要单独进行微调，这需要大量的训练资源，并且在部署和维护方面提出了挑战

此外，这些方法并未能利用不同的代码相关任务之间固有的相互关联性，为了克服这些限制，本文提出了一个多任务微调框架MFTcoder，可以对多个任务进行同步和并行微调，通过结合各种损失函数，有效地解决了多任务学习中的常见挑战，例如数据不平衡、不同的难度级别和不一致的收敛速度

大量的实验最终证明多任务微调方法优于对单个任务的单独微调和对混合任务集合的微调，此外，MFTcoder提供高效的训练能力，包括高效的数据分词化模式(tokenization modes)和前缀微调(PEFT fine-tuning)，与传统微调方法相比，速度显著提高

MFTcoder可以与CodeLLama、Qwen等几种主流的开源LLM无缝集成，通过利用CodeLLama作为基础模型，本文提出的MFTcoder微调模型CodeFuse-CodeLLama-34B在HumaneEval基准测试中取得了令人印象深刻的74.4%的pass@1成绩，超越了GPT-4的67%的零样本性能

github项目页截图:

<img src="https://img.saraba1st.com/forum/202311/08/013011v0a577cgc7j1c11o.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231108-012914.jpg</strong> (222.85 KB, 下载次数: 0)

下载附件

2023-11-8 01:30 上传

<img src="https://img.saraba1st.com/forum/202311/08/013011c7obo9z8ob171a1b.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231108-012928.jpg</strong> (257.18 KB, 下载次数: 0)

下载附件

2023-11-8 01:30 上传

<img src="https://img.saraba1st.com/forum/202311/08/013011p2n36jjgg660202z.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231108-012937.jpg</strong> (170.68 KB, 下载次数: 0)

下载附件

2023-11-8 01:30 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 955#       发表于 2023-11-8 02:38

CoVLM

通过沟通解码(Communicative Decoding)在大型语言模型中组合视觉实体和关系(Visual Entities and Relationships)

项目页面:https://vis-www.cs.umass.edu/CoVLM

github项目代码仓库:https://github.com/UMass-Foundation-Model/CoVLM

人类的一项非凡能力在于组合式推理(compositional reasoning)，即“无限的使用有限含义(infinite use of finite means)”的能力，然而，当前的大型视觉语言基础模型(VLM/vision-language foundation models)由于其“词袋(bag-of-words)”行为且无法构建正确表示视觉实体和实体之间关系的单词，因此缺乏这种组合能力

为此，本文提出了CoVLM，它可以指导LLM显式地组合文本之间的视觉实体和关系，并与视觉编码器和检测网络动态沟通，以实现视觉语言沟通解码

具体来说，首先为LLM设计了一组新颖的沟通Token，用于视觉检测系统和语言系统之间的动态沟通，LLM根据视觉实体或关系生成沟通Token，以通知检测网络提案与目前生成的句子相关的区域，然后将提议的感兴趣区域(ROI/regions-of-interests)反馈到LLM中用以根据相关区域更好地生成语言

因此，LLM能够通过沟通Token组合视觉实体和关系，视觉到语言和语言到视觉的交流不断迭代，直到生成整个句子，本文的框架无缝地弥合了视觉感知和LLM之间的差距，并且在组合推理基准上大幅优于之前的VLM(例如，在HICO-DET mAP上的改进约为20%，在Cola top-1上的改进14%，在ARO top-1上的改进约3%)，在传统视觉语言任务上也实现了SOTA表现，例如指代表达理解和视觉问答

<img src="https://img.saraba1st.com/forum/202311/08/023811swwwpe0jech6wq4t.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231108-022033.jpg</strong> (86.1 KB, 下载次数: 0)

下载附件

2023-11-8 02:38 上传

与现有VLM的对比，以前的模型将整张图像作为输入，损害了VLM的组合性，CoVLM将语言到视觉和视觉到语言通信后的视觉实体/关系Token插入到LLM中，在很大程度上提高了组合性

<img src="https://img.saraba1st.com/forum/202311/08/023824wzpgp2jim6m6w59z.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231108-022452.jpg</strong> (89.79 KB, 下载次数: 0)

下载附件

2023-11-8 02:38 上传

CoVLM框架概览，视觉模块由一个用于对图像进行编码的CLIP编码器和一个对象检测器组成，该对象检测器接收图像和语言输入以生成相关区域

对于语言建模，将一组沟通Token插入到LLM中，这些Token可以出现在带有&lt;visual&gt;Token的视觉实体之后，或者出现在带有&lt;previsual&gt;Token的关系之后，之后LLM的最后一个隐藏层被发送到对象检测器，以提案与迄今为止的语言输入相关的区域，这被称为自上而下的语言到视觉的沟通(top down language-to-vision communication)，接下来，在视觉到语言的通信中，建议区域的特征通过&lt;box&gt;或&lt;prebox&gt;令牌反馈给LLM以进一步生成语言

<img src="https://img.saraba1st.com/forum/202311/08/023835v9yfm6mnmivfry99.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231108-022937.jpg</strong> (107.35 KB, 下载次数: 0)

下载附件

2023-11-8 02:38 上传

三个数据集上的视觉语言对齐模型和生成模型的组合推理能力对比

<img src="https://img.saraba1st.com/forum/202311/08/023843chfzzh4qeg5e4351.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231108-023050.jpg</strong> (115.73 KB, 下载次数: 0)

下载附件

2023-11-8 02:38 上传

与HICO-DET上任务特定方法的对比

<img src="https://img.saraba1st.com/forum/202311/08/023848qqifz9qp9rf7fk6s.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231108-023130.jpg</strong> (51.85 KB, 下载次数: 0)

下载附件

2023-11-8 02:38 上传

与Cola上任务特定的监督学习方法的对比

<img src="https://img.saraba1st.com/forum/202311/08/023852yi9t4u4k936ly0t0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231108-023552.jpg</strong> (71.47 KB, 下载次数: 0)

下载附件

2023-11-8 02:38 上传

三个数据集上的引用表达理解的对比

<img src="https://img.saraba1st.com/forum/202311/08/023857o2k88yb3uybuv23u.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231108-023625.jpg</strong> (124.02 KB, 下载次数: 0)

下载附件

2023-11-8 02:38 上传

VQAv2的test-dev结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 956#       发表于 2023-11-9 02:24

 本帖最后由 Machinery 于 2023-11-9 02:27 编辑 

OtterHD/MagnifierBench

高分辨率多模态模型/MagnifierBench评估框架

github项目主页:https://github.com/Luodian/Otter

MagnifierBench评估框架:https://huggingface.co/datasets/Otter-AI/MagnifierBench

OtterHD-8B，一种从Fuyu-8B演变来的创新多模态模型，专注用于以粒度精度理解高分辨率视觉输入，与受固定尺寸视觉编码器限制的传统模型不同，OtterHD-8B拥有灵活处理输入尺寸的能力，确保其在各种推理要求中的多功能性

除了该模型之外，还引入了MagnifierBench，一个新颖的评估框架，旨在检查模型辨别小物体的微小细节和空间关系的能力，对比分析表明，虽然当前领先的模型在此基准上表现不佳，但OtterHD-8B，特别是在直接处理高分辨率输入时，其性能大幅优于同类产品

研究结果阐明了不同模型之间视觉信息处理的结构差异，以及视觉编码器的预训练分辨率差异对此类基准中模型有效性的影响，研究强调了灵活性和高分辨率输入能力在大型多模态模型中的关键作用，并举例说明了Fuyu架构在处理复杂视觉数据的简单性方面所固有的潜力

<img src="https://img.saraba1st.com/forum/202311/09/022337rrz5qjitw0rote6d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-012554.jpg</strong> (171.91 KB, 下载次数: 0)

下载附件

2023-11-9 02:23 上传

OtterHD-8B的感知与识别演示，该图为宋代国画《清明上河图》整个作品的一部分，分辨率为2466×1766

<img src="https://img.saraba1st.com/forum/202311/09/022343fhh3ph6770qj0t1h.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-012613.jpg</strong> (136.38 KB, 下载次数: 0)

下载附件

2023-11-9 02:23 上传

OtterHD-8B与著名开源LMM的性能对比，详细说明了指令/响应数据对、训练和评估分辨率

“Dynamic”指的是具有不同分辨率的训练，“Original”表示使用每个图像的原始分辨率进行评估，而不进行任何调整大小操作，其他模型多数将图像大小调整为一致的方形分辨率进行评估，如Eval Res所示

<img src="https://img.saraba1st.com/forum/202311/09/022355ctbihbfyqheqzatb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-014700.jpg</strong> (51.18 KB, 下载次数: 0)

下载附件

2023-11-9 02:23 上传

不同模型的吞吐量对比评估，训练吞吐量指标(表示每个GPU每秒的Token数)，通过记录每个批次的值并计算随后30分钟时间的平均值确定，Token包括图像Token和文本Token

<img src="https://img.saraba1st.com/forum/202311/09/022400d8n4n4n1qwwhwa1t.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-014705.jpg</strong> (142.79 KB, 下载次数: 0)

下载附件

2023-11-9 02:24 上传

MagnifierBench中三种问题类型的示例，其中每个问题都与两种类型的问题和答案相关，左右图像的分辨率均为1080×1920，而中央图像的分辨率为640×480

<img src="https://img.saraba1st.com/forum/202311/09/022406jpow61h40tbpnkzp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-021519.jpg</strong> (72.78 KB, 下载次数: 0)

下载附件

2023-11-9 02:24 上传

OtterHD在不同分辨率下的评估性能对比

<img src="https://img.saraba1st.com/forum/202311/09/022411owzhwesrru25fuw6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-021606.jpg</strong> (41.41 KB, 下载次数: 0)

下载附件

2023-11-9 02:24 上传

不同分辨率下的图像和文本Token计数

<img src="https://img.saraba1st.com/forum/202311/09/022720tmmtll07lhqqhllm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-021644__01.jpg</strong> (175.27 KB, 下载次数: 0)

下载附件

2023-11-9 02:27 上传

LMM之间的对象计数和详细场景文本理解能力对比，不正确的部分已注明

<img src="https://img.saraba1st.com/forum/202311/09/022422i16ns6nz99y6mtdz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-021739.jpg</strong> (226.82 KB, 下载次数: 0)

下载附件

2023-11-9 02:24 上传

LMM之间的桌面级(desktop)理解能力对比，不正确的部分已注明

<img src="https://img.saraba1st.com/forum/202311/09/022428q2j7t0st57m55s2m.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-021937.jpg</strong> (181.31 KB, 下载次数: 0)

下载附件

2023-11-9 02:24 上传

<img src="https://img.saraba1st.com/forum/202311/09/022428vfbo4mbo5hhmmb4f.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-021946.jpg</strong> (227.32 KB, 下载次数: 0)

下载附件

2023-11-9 02:24 上传

LMM之间的详细场景文本(桌面指导)理解和推理能力对比，不正确的部分已注明

<img src="https://img.saraba1st.com/forum/202311/09/022635cyysmsdydkfdlxls.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-022622.jpg</strong> (474.46 KB, 下载次数: 0)

下载附件

2023-11-9 02:26 上传

比较不同LLM在MagnifierBench上对两类问题的回答，正确答案有下划线

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 957#       发表于 2023-11-9 06:18

I2VGen-XL

通过级联扩散模型(Cascaded Diffusion Models)进行高质量图像到视频合成

项目主页:https://i2vgen-xl.github.io/

github项目仓库:https://github.com/damo-vilab/i2vgen-xl

随着扩散模型的快速发展，视频合成最近取得了明显的进步，然而这些方法在语义准确性、清晰度和时空连续性(spatio-temporal continuity)方面仍然需要接受挑战，源于缺乏良好对齐的文本视频数据以及视频复杂的固有结构的原因，使得模型很难同时确保语义和质量的效果

在本文中，提出了一种级联I2VGen-XL方法，该方法通过解耦这两个因素来增强模型的性能，同时通过利用静态图像作为关键指导的形式来确保与输入数据的对齐

I2VGen-XL由两个阶段组成：i)基础阶段，通过使用两个分层编码器保证关联语义并保留输入图像的内容，ii)细化阶段，通过合并额外的简短文本来增强视频的细节，并将分辨率提高到1280×720

为了提高多样性，研究组收集了大约3500万个单镜头(single-shot)文本视频对和60亿个文本图像对来优化模型，通过这种方式，I2VGen-XL可以同时增强生成视频的语义准确性(semantic accuracy)、细节的连续性(continuity of details)和清晰度(clarity)

通过广泛实验，研究了I2VGen-XL的基本原理，并将其与当前的顶级方法进行了对比，这证明了其在多种数据上的有效性

<img src="https://img.saraba1st.com/forum/202311/09/061757yp6nghnexgtp1ghe.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-060434.jpg</strong> (320.76 KB, 下载次数: 0)

下载附件

2023-11-9 06:17 上传

生成的视频的示例，I2VGen-XL能够生成各种类别的高质量视频，例如艺术、人类、动物、技术等，生成的视频具有高清、高分辨率、流畅、美观等优点，适合更广泛的视频内容创作

<img src="https://img.saraba1st.com/forum/202311/09/061800qpnh3aayjscn66yb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-060552.jpg</strong> (65.87 KB, 下载次数: 0)

下载附件

2023-11-9 06:18 上传

I2VGen-XL的框架总览，在基础阶段，两个分层编码器同时捕获输入图像的高级语义和低级细节，确保更真实的动态，同时保留图像的内容和结构，在细化阶段，利用独立的扩散模型来增强分辨率，并通过细化细节显著增强视频的时间连续性，“D.Enc” 和“G.Enc”分别表示细节编码器和全局编码器

<img src="https://img.saraba1st.com/forum/202311/09/061804xkaas86pzmmxkkmm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-060914.jpg</strong> (147.05 KB, 下载次数: 0)

下载附件

2023-11-9 06:18 上传

全局编码器的架构，“C”代表Conv2D，相应的参数分别为input dimension，output dimension，kernel size，stride,以及padding，“A.A.P”是2D Adaptive平均池化操作

<img src="https://img.saraba1st.com/forum/202311/09/061808cqa3og4497d3a89e.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-061341.jpg</strong> (204.79 KB, 下载次数: 0)

下载附件

2023-11-9 06:18 上传

细化模型的结果，显然，细化模型有效地复原了视频细节并保证了时间连续性，从而证明了其效果

<img src="https://img.saraba1st.com/forum/202311/09/061813d0bb201021h0hjf4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-061455.jpg</strong> (467.45 KB, 下载次数: 0)

下载附件

2023-11-9 06:18 上传

与Gen-2和Pika Labs的对比

<img src="https://img.saraba1st.com/forum/202311/09/061817sq1xx7kqw8xeiu2e.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-061524.jpg</strong> (621.42 KB, 下载次数: 0)

下载附件

2023-11-9 06:18 上传

根据输入的文本提示生成的视频

<img src="https://img.saraba1st.com/forum/202311/09/061822rguup59ww256rp1g.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-061602.jpg</strong> (160.4 KB, 下载次数: 0)

下载附件

2023-11-9 06:18 上传

细化模型的频谱分析与I2VGen-XL生成人类躯体视频

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 958#       发表于 2023-11-9 07:23

VIM(Video Instance Matting)

视频实例抠图/去背景(Matting)

github项目主页:https://github.com/SHI-Labs/VIM

传统的视频抠图为视频帧中出现的所有实例输出一个alpha遮罩，从而无法区分各个实例，虽然视频实例分割提供了具有时间一致性的实例掩码，由于应用了二值化(binarization)，其结果对于抠图应用程序来说并不令人满意

为了弥补这一缺陷，本文提出了视频实例抠图(VIM/Video Instance Matting)，对于视频序列的每一帧的每个实例都输出估计的alpha遮罩，为了解决这个挑战性的问题，提出了MSG-VIM，一种掩码序列引导的视频实例抠图神经网络(Mask Sequence Guided Video Instance Matting neural network)，作为VIM的新基线模型

MSG-VIM使用掩码增强的混合让不准确和不一致的掩码指导预测具有稳健性，结合了时间掩码和时间特征指导提高alpha遮罩预测的时间一致性

此外，还为VIM构建了一个新的基准测试，称为VIM50，其中包含50个视频剪辑片段，在前景对象中有多个人体实例，用于评估VIM任务的性能，还引入了一个合适的指标，称为视频实例感知抠图质量(VIMQ/Video Instance-aware Matting Quality)，本文提出的模型MSG-VIM在VIM50基准上设定了强有力的基线，并且远远优于现有的其他方法

<img src="https://img.saraba1st.com/forum/202311/09/072304hegk5pgpkwrgtw68.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-071125.jpg</strong> (304.23 KB, 下载次数: 0)

下载附件

2023-11-9 07:23 上传

视频实例抠图与相关任务的对比，图中描绘了VIM50基准测试的三个框架，视频抠图(Video Matting)、视频实例分割(Video Instance Segmentation)和视频实例抠图(Video Instance Matting)，结果分别从RVM、SeqFormer和MSG-VIM获得，视频实例抠图是识别和跟踪每个前景实例的任务，并估计视频序列每帧对应实例的alpha遮罩

<img src="https://img.saraba1st.com/forum/202311/09/072320n78ztllfpl8p7qgg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-071509.jpg</strong> (40.15 KB, 下载次数: 0)

下载附件

2023-11-9 07:23 上传

视频实例抠图以及相关任务之间的高级对比

<img src="https://img.saraba1st.com/forum/202311/09/072326mtibeoezx9ktdndo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-071615.jpg</strong> (178.68 KB, 下载次数: 0)

下载附件

2023-11-9 07:23 上传

MSG-VIM的架构，使用VIS方法来获取目标的掩码序列和参考实例，掩码引导序列与视频帧连接，作为遮罩网络的输入，之后输出目标实例和参考实例的精细alpha遮罩预测

<img src="https://img.saraba1st.com/forum/202311/09/072348w5qd11d3zqkmk2kk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-072018.jpg</strong> (175.83 KB, 下载次数: 0)

下载附件

2023-11-9 07:23 上传

<img src="https://img.saraba1st.com/forum/202311/09/072348tyjhihmyjqyqmurm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-072052.jpg</strong> (220.5 KB, 下载次数: 0)

下载附件

2023-11-9 07:23 上传

相关消融实验与指标测试对比等

<img src="https://img.saraba1st.com/forum/202311/09/072353ftmt1rypy9wrr8hm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-072136.jpg</strong> (234.63 KB, 下载次数: 0)

下载附件

2023-11-9 07:23 上传

<img src="https://img.saraba1st.com/forum/202311/09/072353xbbcbiy942b27b34.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-072149.jpg</strong> (284.43 KB, 下载次数: 0)

下载附件

2023-11-9 07:23 上传

定性对比结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 959#       发表于 2023-11-9 07:36

DevOps-Model/DevOpsEval

DevOps-Model是一系列业界首个开源的中文开发运维大模型，主要致力于在DevOps(software development (dev) and operations (ops))领域发挥实际价值

DevOpsEval是DevOps领域专属的评测基准，用来更好的评测DevOps领域模型的效果

DevOps-Model github项目主页:https://github.com/codefuse-ai/CodeFuse-DevOps-Model

DevOpsEval github项目主页:https://github.com/codefuse-ai/codefuse-devops-eval

相关页面说明:

<img src="https://img.saraba1st.com/forum/202311/09/073646wm111a1z4brsm33d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-073221.jpg</strong> (261.89 KB, 下载次数: 0)

下载附件

2023-11-9 07:36 上传

<img src="https://img.saraba1st.com/forum/202311/09/073646einl3ey4nw44pnxn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-073233.jpg</strong> (183.41 KB, 下载次数: 0)

下载附件

2023-11-9 07:36 上传

<img src="https://img.saraba1st.com/forum/202311/09/073646rc1c2pqjlvql5nbz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-073245.jpg</strong> (164.87 KB, 下载次数: 0)

下载附件

2023-11-9 07:36 上传

<img src="https://img.saraba1st.com/forum/202311/09/073646i5dosd1o6o61x1hd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-073253.jpg</strong> (214.67 KB, 下载次数: 0)

下载附件

2023-11-9 07:36 上传

<img src="https://img.saraba1st.com/forum/202311/09/073646rigbovox70e212iy.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-073322.jpg</strong> (79.43 KB, 下载次数: 0)

下载附件

2023-11-9 07:36 上传

<img src="https://img.saraba1st.com/forum/202311/09/073647re74gg7mdefgvafp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-073540.jpg</strong> (242.21 KB, 下载次数: 0)

下载附件

2023-11-9 07:36 上传

<img src="https://img.saraba1st.com/forum/202311/09/073647b413xxyue477xxq4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231109-073600.jpg</strong> (484.98 KB, 下载次数: 0)

下载附件

2023-11-9 07:36 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 960#       发表于 2023-11-10 02:19

LRM

单图像转3D的大型重建模型(Large Reconstruction Model)

项目主页:https://yiconghong.me/LRM/

本文提出了第一个大型重建模型(LRM/Large Reconstruction Model)，可以在仅仅5秒内从单张输入图像预测对象的3D模型

与许多在小规模数据集(例如ShapeNet)上以特定类别方式进行训练的方法相比，LRM采用高度可扩展的基于Transformer的架构，具有5亿可学习的参数，可以直接从输入图像预测神经辐射场(NeRF/neural radiance field)

通过在包含大约100万个对象的海量多视图数据上以端到端的方式训练模型，使用包括来自Objaverse的合成渲染和来自MVImgNet的真实捕获图，大型模型和大规模训练数据的结合使模型具有高通用性，并且可以根据各种测试输入(如真实世界的自然场景捕获和生成模型的图像)生成高质量的3D重建

<img src="https://img.saraba1st.com/forum/202311/10/021835he0l44ciyzdvbkml.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-020236.jpg</strong> (157.21 KB, 下载次数: 0)

下载附件

2023-11-10 02:18 上传

LRM的整体架构，一个基于完全可微(fully-differentiable)的Transformer的编码器-解码器框架，用于单图像到NeRF重建

LRM应用预先训练的视觉模型(DINO)对输入图像进行编码，其中图像特征通过大型Transformer解码器的交叉注意力投影为3D三平面表征， 随后多层感知器(multi-layer perceptron)用来预测体积渲染(volumetric rendering)的点颜色(point color)和密度(density)，整个网络在大约一百万个3D数据上进行端到端训练，并具有简单的图像重建损失(reconstruction losses)

<img src="https://img.saraba1st.com/forum/202311/10/021931u61zm06dyd1o01mp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-020821.jpg</strong> (396.83 KB, 下载次数: 0)

下载附件

2023-11-10 02:19 上传

LRM从单张图像重建形状的新视图(RGB和深度)，在训练期间模型不会观察到任何图像，生成的图像是使用Adob​​e Firefly创建的，最后两行将本模型的结果与Objaverse对象(GT/基准答案)的基准渲染结果图像进行对比

<img src="https://img.saraba1st.com/forum/202311/10/021855oehb1f8oo6ok1by0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-021258.jpg</strong> (151.29 KB, 下载次数: 0)

下载附件

2023-11-10 02:18 上传

与One-2-3-45的对比，为了避免挑选结果(cherry picking)，前三行中的输入图像是从One-2-3-45的论文或演示页面中提供的示例中选择的，模型在训练期间没有观察到任何图像

<img src="https://img.saraba1st.com/forum/202311/10/021850gw8gqlptrrot8prg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-021429.jpg</strong> (45.39 KB, 下载次数: 0)

下载附件

2023-11-10 02:18 上传

本方法的失败案例，所有三个示例都在遮挡区域显示了模糊纹理，通常是由于相机参数的估计在很大程度上不准确而导致的失真

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 961#       发表于 2023-11-10 02:20

Awesome-Text-to-3D

文本到3D生成方法总览

引导页:https://github.com/StellarCheng/Awesome-Text-to-3D

相关说明截图:

<img src="https://img.saraba1st.com/forum/202311/10/022024zi3va2el0wkkxvz7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-021648.jpg</strong> (563.03 KB, 下载次数: 0)

下载附件

2023-11-10 02:20 上传

<img src="https://img.saraba1st.com/forum/202311/10/022024vhu0de3bz3o0ro3z.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-021655.jpg</strong> (190.17 KB, 下载次数: 0)

下载附件

2023-11-10 02:20 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 962#       发表于 2023-11-10 03:43

mPLUG-Owl2

通过多模态协力(Collaboration)革新多模态大型语言模型

github项目页面:https://github.com/X-PLUG/mPLUG-Owl/tree/main/mPLUG-Owl2

多模态大型语言模型(MLLM/Multi-modal Large Language Models)在多种开放式任务中表现出了令人印象深刻的指令能力，然而，之前的方法主要侧重于增强多模态能力，在本文中，引入了一种多功能的多模态大语言模型mPLUG-Owl2，能够有效地利用模态协力来同时提高文本和多模态任务的性能

mPLUG-Owl2采用模块化网络设计，语言解码器作为管理者控制不同模态的通用交互接口，具体来说，mPLUG-Owl2合并了共享的功能模块以促进模态协力，并引入了模态适配模块(modality-adaptive module)来保留局限于特定模态的功能

大量实验表明，mPLUG-Owl2能够泛化文本任务和多模态任务，并通过单个通用模型实现SOTA性能，更值得注意的是，mPLUG-Owl2是第一个在纯文本和多模态场景中展示模态协力现象的MLLM模型，这为未来多模态基础模型的开发开辟了开创性道路

<img src="https://img.saraba1st.com/forum/202311/10/033815ll57ja118uqq1lqe.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-031309.jpg</strong> (272.63 KB, 下载次数: 0)

下载附件

2023-11-10 03:38 上传

mPLUG-Owl2与已有的MLLM之间的性能对比总览以及已有的MLLM与本文提出的模型之间的差异
(a)以前的方法利用标准语言解码器(即LLM)来管理不同类型的指令，导致模态干扰和性能下降
(b)本文方法引入了mPLUG-Owl2，通过使用模态适配语言解码器来处理不同模块内的不同模态，同时共享一些用于模态协力的参数，这种方法减轻了模态互相干扰的问题

<img src="https://img.saraba1st.com/forum/202311/10/033822u7goh9gzo9l9lbb7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-031846.jpg</strong> (125.73 KB, 下载次数: 0)

下载附件

2023-11-10 03:38 上传

所提案的mPLUG-Owl2及其训练范式的图示
(a) mPLUG-Owl2概览，它由视觉编码器、视觉抽象器(visual abstractor)、文本嵌入层和语言解码器组成
(b)所提出的模态适配模块的详细信息，该模块采用多模态输入并采用不同的参数将各种模态投影到共享语义空间中以进行关系学习，同时保留模态特定的特征，从而实现模态协力
(c)mPLUG-Owl2的训练范式，首先涉及视觉相关模块的预训练，包括视觉编码器和视觉抽象器，同时，语言解码器中新添加的参数也在预训练阶段被学习，在指令调整阶段，同时使用语言指令和多模态指令来联合训练整个模型

<img src="https://img.saraba1st.com/forum/202311/10/033836lv88vvnq1f6y3d8y.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-032212.jpg</strong> (108.72 KB, 下载次数: 0)

下载附件

2023-11-10 03:38 上传

图像字幕说明和视觉问答的性能对比，对于图像字幕说明，报告CIDEr指标进行评估，VQA则报告准确率，请注意有的方法会对模型进行独立数据集微调

†表示使用了OCR输入，‡表示模型已在数据集上进行训练，将那些在数据集上专门微调的专家方法以及通用的微调结果显示为灰色

<img src="https://img.saraba1st.com/forum/202311/10/034106u8c66nnmmnnc05m6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-034057.jpg</strong> (118.27 KB, 下载次数: 0)

下载附件

2023-11-10 03:41 上传

对多模态基准测试进行零样本多模态评估，MME、MMBench、MM-Vet、SEED-Bench和Q-Bench，报告总分以供评估

<img src="https://img.saraba1st.com/forum/202311/10/034217kujm00ijqh0x7ufx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-034204.jpg</strong> (59.04 KB, 下载次数: 0)

下载附件

2023-11-10 03:42 上传

mPLUG-Owl2与LLaMA-2 (7B)系列变体在纯文本基准测试中的性能对比，对MMLU采用5-shot，对BBH、AGIEval和ARC采用0-shot

<img src="https://img.saraba1st.com/forum/202311/10/034238nz5h45ixbpi4xnpu.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-033204.jpg</strong> (108.08 KB, 下载次数: 0)

下载附件

2023-11-10 03:42 上传

视频问答的零样本评估，报告准确性和相关性分数

<img src="https://img.saraba1st.com/forum/202311/10/034250qrc05hvbrery5qvc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-033243.jpg</strong> (72.94 KB, 下载次数: 0)

下载附件

2023-11-10 03:42 上传

模态协力下跨越多种功能的文本基准测试性能

<img src="https://img.saraba1st.com/forum/202311/10/034255iqc4n4sn4s5tlpts.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-033401.jpg</strong> (211.87 KB, 下载次数: 0)

下载附件

2023-11-10 03:42 上传

其他相关评估结果

<img src="https://img.saraba1st.com/forum/202311/10/034303eopza73k3no83omc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-033455.jpg</strong> (60.33 KB, 下载次数: 0)

下载附件

2023-11-10 03:43 上传

不同输入图像分辨率的影响

<img src="https://img.saraba1st.com/forum/202311/10/034307s5fsllykz1w5599b.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-033521.jpg</strong> (224.5 KB, 下载次数: 0)

下载附件

2023-11-10 03:43 上传

使用和不使用模态适配模块的注意力图的可视化，展示了第0、15和31层的注意力图，其中视觉Token的范围由橙色表示，文本Token的范围由蓝色表示

<img src="https://img.saraba1st.com/forum/202311/10/034311nzxpz2x2xzpxp2fl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-033705.jpg</strong> (310.32 KB, 下载次数: 0)

下载附件

2023-11-10 03:43 上传

使用和不使用模态适配模块的注意力图的可视化，展示了每层注意力图的平均值

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 963#       发表于 2023-11-10 04:14

NExT-Chat

用于聊天、检测和分割(Chat, Detection and Segmentation)的LMM

项目主页:https://next-chatv.github.io/

github项目仓库:https://github.com/NExT-ChatV/NExT-Chat

7B演示Demo:https://20d12192149d0748e2.gradio.live/

大型语言模型(LLM/large language models)的发展极大地提升了多模态理解领域，并发展出了大型多模态模型(LMM/large multimodal models)，为了提高视觉理解水平，最近的研究通过将对象边界框坐标表征为一系列文本序列(pixel2seq)，为LMM装备了区域级理解能力(region-level understanding capabilities)

在本文中，介绍了一种称为Pixel2emb的对象位置建模(object location modeling)的新范式方法，通过要求LMM输出位置嵌入(location embeddings)，然后由不同的解码器进行解码，这种范式允许在多模态对话中使用不同的位置格式(例如边界框和掩码)，此外，这种基于嵌入的位置建模使之能够利用定位任务中的现有实践方法，例如检测和分割

在资源有限的场景中的公平比较下，Pixel2emb在位置输入和输出任务中都表现出了比现有的SOTA方法更强大的性能，利用所提出的Pixel2emb方法，还训练了一个名为NExT-Chat的LMM，并展示了其处理视觉基准(visual grounding)、区域字幕说明(region caption)和基准推理(grounded reasoning)等多项任务的能力

<img src="https://img.saraba1st.com/forum/202311/10/041339f25v1l2kip11pib2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-040309.jpg</strong> (64.31 KB, 下载次数: 0)

下载附件

2023-11-10 04:13 上传

通过使用基于嵌入的位置建模方法，LMM可以将边界框作为输入和输出文本、多模态对话中的边界框和掩码

<img src="https://img.saraba1st.com/forum/202311/10/041344wzjh1jd99m9zud9u.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-040234.jpg</strong> (63.61 KB, 下载次数: 0)

下载附件

2023-11-10 04:13 上传

NExT-Chat的整体框架，图像和给定的边界框分别由图像和框编码器编码，随后&lt;trigger&gt;的隐藏状态被输入框解码器和掩码解码器，从而实现对象检测和分割

<img src="https://img.saraba1st.com/forum/202311/10/041351bmwzbgmcvv0ew0c8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-040534.jpg</strong> (60.36 KB, 下载次数: 0)

下载附件

2023-11-10 04:13 上传

Pemb和现有的位置建模方法之间的对比，Dec.Type是解码坐标的方式，Format是边界框格式，ToB代表单个边界框的Token数量，请注意，“[” and “]”也需要两个Token，Vocab.是添加到位置数据建模词汇表中的新Token的数量，Rep.代表模型是给定位置建模方法的代表性模型

<img src="https://img.saraba1st.com/forum/202311/10/041358kztxr3vrxc1ehh1d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-040849.jpg</strong> (41.15 KB, 下载次数: 0)

下载附件

2023-11-10 04:13 上传

循环损失(Cycle loss)用于绑定框编码器和解码器的训练

<img src="https://img.saraba1st.com/forum/202311/10/041408z11ze9hn1ojn9921.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-040955.jpg</strong> (79.91 KB, 下载次数: 0)

下载附件

2023-11-10 04:14 上传

<img src="https://img.saraba1st.com/forum/202311/10/041408c7vwcwridycwd7yq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-041030.jpg</strong> (23.75 KB, 下载次数: 0)

下载附件

2023-11-10 04:14 上传

Pemb和其他基线在位置输出与输入任务上的对比

<img src="https://img.saraba1st.com/forum/202311/10/041413eyj8ni9n9nu9un1w.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-041136.jpg</strong> (156.12 KB, 下载次数: 0)

下载附件

2023-11-10 04:14 上传

NExT-Chat与当前SOTA模型在POPE目标幻觉诊断基准上的比较

<img src="https://img.saraba1st.com/forum/202311/10/041428dxttn2idnd88zd7z.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-041225.jpg</strong> (337.85 KB, 下载次数: 0)

下载附件

2023-11-10 04:14 上传

<img src="https://img.saraba1st.com/forum/202311/10/041428vjm2o0zm1z583tfo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-041235.jpg</strong> (145.93 KB, 下载次数: 0)

下载附件

2023-11-10 04:14 上传

<img src="https://img.saraba1st.com/forum/202311/10/041428klevs3z1aeg8svl9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-041242.jpg</strong> (225.12 KB, 下载次数: 0)

下载附件

2023-11-10 04:14 上传

<img src="https://img.saraba1st.com/forum/202311/10/041428nkyg9vkvo993fkgg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231110-041250.jpg</strong> (201 KB, 下载次数: 0)

下载附件

2023-11-10 04:14 上传

相关任务实例

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 964#       发表于 2023-11-12 03:18

 本帖最后由 Machinery 于 2023-11-12 03:21 编辑 

LooGLE

长上下文语言模型可以理解长上下文吗？

github数据集主页:https://github.com/bigai-nlco/LooGLE

尽管大型语言模型在多种语言任务中表现出色，但这通常仅限于处理上下文窗口大小内的文本，这一限制促使人们进行了大量的研究工作，使用诸如高质量的长序列基准测试来增强LLM的长上下文理解

然而之前的数据集在某些方面存在一些短处，例如，与现代LLM的上下文窗口相比，基准测试的上下文长度依然较短；文档过时，存在数据泄露问题； 以及过于强调短程依赖任务而不是长程依赖任务

在本文中，提出了LooGLE，一种用于LLM长上下文理解的长上下文通用语言评估基准，LooGLE集成了2022年之后相对较新的文档，每个文档包含超过24000个Token，以及跨越不同领域的6000个新生成的问题，同时人工标注者精心制作了1100多个高质量问答对，以满足长程依赖测试要求

通过对这些问答对进行了彻底的交叉验证，对LLM的长程依赖能力进行了最精确的评估，以及对LooGLE上八个SOTA LLM的评估揭示了以下主要发现:(i)商业模型优于开源模型；(ii)LLM在短程依赖任务(如简短问答和完形填空任务)方面表现出色，但在更复杂的长程依赖任务上表现不佳；(iii)上下文学习和CoT只能带来边际收益；(iv)基于检索的技术显示出对短问答的巨大好处，而延长上下文窗口长度的策略对长上下文理解的影响有限

因此，LooGLE不仅为长上下文LLM提供了系统、全面的评估模式，而且还为未来发展“真正的长上下文理解”增强模型提供了灵感

<img src="https://img.saraba1st.com/forum/202311/12/031506hl52jgp8zpp4lm94.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231112-030555.jpg</strong> (124.78 KB, 下载次数: 0)

下载附件

2023-11-12 03:15 上传

用于长上下文理解的LooGLE基准

<img src="https://img.saraba1st.com/forum/202311/12/031514qh1hocccnwdzd000.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231112-030631.jpg</strong> (57.14 KB, 下载次数: 0)

下载附件

2023-11-12 03:15 上传

与其他长上下文基准的对比

<img src="https://img.saraba1st.com/forum/202311/12/031531u555ue21555u5jxz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231112-030700.jpg</strong> (95.32 KB, 下载次数: 0)

下载附件

2023-11-12 03:15 上传

LooGLE的统计数据

<img src="https://img.saraba1st.com/forum/202311/12/031544nrk4tphr44u8ualt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231112-030725__01.jpg</strong> (317.47 KB, 下载次数: 0)

下载附件

2023-11-12 03:15 上传

长程依赖QA任务

<img src="https://img.saraba1st.com/forum/202311/12/031551y1pcrqc3607ice1y.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231112-030817__01.jpg</strong> (209.8 KB, 下载次数: 0)

下载附件

2023-11-12 03:15 上传

LLM们在LooGLE上的长上下文理解表现总览

<img src="https://img.saraba1st.com/forum/202311/12/031558e22zlknv3wrdk3r9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231112-030954.jpg</strong> (252.59 KB, 下载次数: 0)

下载附件

2023-11-12 03:15 上传

短程依赖与长程依赖的表现性能

<img src="https://img.saraba1st.com/forum/202311/12/031604lejnr3n11fhwirkj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231112-031023.jpg</strong> (127.72 KB, 下载次数: 0)

下载附件

2023-11-12 03:16 上传

输入长度对长程依赖任务的影响

<img src="https://img.saraba1st.com/forum/202311/12/031851whpmaz1kaskk1qoh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231112-031102.jpg</strong> (169.81 KB, 下载次数: 0)

下载附件

2023-11-12 03:18 上传

使用LlamaIndex的长程依赖QA任务的性能与GPT 4评估的四种长程依赖WAs的独立结果

<img src="https://img.saraba1st.com/forum/202311/12/031705t1ch31mlsg133hkk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231112-031147.jpg</strong> (99.94 KB, 下载次数: 0)

下载附件

2023-11-12 03:17 上传

时间线重排序的性能表现

<img src="https://img.saraba1st.com/forum/202311/12/031710v0sy48spgdxdxss8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231112-031221.jpg</strong> (78.18 KB, 下载次数: 0)

下载附件

2023-11-12 03:17 上传

不同分段的表现与没有CoT的长程依赖性QA任务表现

<img src="https://img.saraba1st.com/forum/202311/12/031715n23r3tl9fdelvlee.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231112-031232.jpg</strong> (65.72 KB, 下载次数: 0)

下载附件

2023-11-12 03:17 上传

QA任务的输出分布

<img src="https://img.saraba1st.com/forum/202311/12/031720uu8rran8jaan75j4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231112-031253.jpg</strong> (120.35 KB, 下载次数: 0)

下载附件

2023-11-12 03:17 上传

长程依赖QA的错误案例研究

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 965#       发表于 2023-11-12 03:52

helm

文本到图像模型的整体评估

github项目主页:https://github.com/stanford-crfm/helm

具有完全透明度的生成图像和人工评估结果:https://crfm.stanford.edu/heim/v1.1.0

最近的文本到图像模型以令人惊叹的质量改进引起了广泛的关注和部署，然而缺乏对其能力和风险的全面定量了解，为了填补这一空白，本文引入了一个新的基准：文本到图像模型的整体评估(HEIM/Holistic Evaluation of Text-to-Image Models)

虽然之前的评估主要关注文本图像对齐和图像质量，但细粒度不足，因此确定了新的12个方面，包括文本图像对齐、图像质量、美学、原创性、推理、知识、偏见、毒性、公平性、稳健性、多语言性和效率(text-image alignment, image quality, aesthetics, originality, reasoning, knowledge, bias, toxicity, fairness, robustness, multilinguality, and efficiency)

策划了涵盖这些方面的62个场景，并在此基准测试上评估了26个SOTA文本到图像模型，结果表明，没有一个模型在所有方面都表现出色，不同的模型表现出不同的优势

<img src="https://img.saraba1st.com/forum/202311/12/035217dne01nyo1i8snuun.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231112-033437.jpg</strong> (140.94 KB, 下载次数: 0)

下载附件

2023-11-12 03:52 上传

文本到图像模型的整体评估概览，虽然现有的基准测试侧重于有限的方面，例如图像质量和与文本的对齐，依赖于可能无法准确反映人类判断的自动化指标，同时仅评估有限的模型，而HEIM则采取了一种整体方法，通过在62个提示场景(“提示”列)中评估了图像生成的12个关键方面(“方面”列)，此外，还采用现实的、基于人的评估指标(“指标”列中的蓝色字体)与自动化指标(黑色字体)相结合，对26个不同的模型进行了标准化评估

<img src="https://img.saraba1st.com/forum/202311/12/035223tlid5vpy81av7gpd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231112-034020__01.jpg</strong> (406.59 KB, 下载次数: 0)

下载附件

2023-11-12 03:52 上传

标准化评价，在HEIM之前的评估基准，对图像生成模型的评估并不全面：12个核心方面中有6个没有在现有模型上进行评估，并且只研究了总评估空间的11％(矩阵中✓的百分比)

<img src="https://img.saraba1st.com/forum/202311/12/035227jspvdj03s5w6gzhr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231112-034218.jpg</strong> (29.51 KB, 下载次数: 0)

下载附件

2023-11-12 03:52 上传

评估组件，每次评估运行都包含一个方面(评估维度)、一个场景(特定用例)、一个具有适配过程的模型(模型如何运行)以及一个或多个指标(捕获模型的好坏程度)

<img src="https://img.saraba1st.com/forum/202311/12/035231xtz2ifapirptlwet.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231112-034451.jpg</strong> (384.42 KB, 下载次数: 0)

下载附件

2023-11-12 03:52 上传

文本到图像生成模型的当前情况，在这里展示了精选的几个文本到图像模型的示例，以从不同方面(不包括效率)提供各种提示，基准测试强调了模型的优点和缺点，例如DALL-E 2对于英文和中文提示都显示出不错的文本图像对齐，但具有明显的性别和肤色偏差，仅生成具有相似肤色的女性图像(最右一列)

<img src="https://img.saraba1st.com/forum/202311/12/035236vg0fy0o31gofgnyi.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231112-034646.jpg</strong> (142.67 KB, 下载次数: 0)

下载附件

2023-11-12 03:52 上传

文本到图像模型的评估方面

<img src="https://img.saraba1st.com/forum/202311/12/035241vf9p9n4nvtnyv4ed.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231112-034718.jpg</strong> (324.13 KB, 下载次数: 0)

下载附件

2023-11-12 03:52 上传

用于评估图像生成模型的12个方面的场景

<img src="https://img.saraba1st.com/forum/202311/12/035245sqhhj2g3k3qzc3he.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231112-034759.jpg</strong> (307.06 KB, 下载次数: 0)

下载附件

2023-11-12 03:52 上传

用于评估图像生成模型12个方面的指标，使用了现实的人工指标以及自动化且常用的现有指标

评估的相关模型

用于评估各个方面的模型的结果摘要，对于每个方面，展示每个模型的胜率

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 966#       发表于 2023-11-14 03:29

EmotiVoice

EmotiVoice易魔声:多音色提示控制TTS

github项目主页:https://github.com/netease-youdao/EmotiVoice

EmotiVoice是一个强大的开源TTS引擎，支持中英文双语，包含2000多种不同的音色，以及特色的情感合成功能，支持合成包含快乐、兴奋、悲伤、愤怒等广泛情感的语音

EmotiVoice提供一个易于使用的web界面，还有用于批量生成结果的脚本接口

github说明页:

<img src="https://img.saraba1st.com/forum/202311/14/032902wvcivyncyyemcmns.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231114-032820.jpg</strong> (224.96 KB, 下载次数: 0)

下载附件

2023-11-14 03:29 上传

<img src="https://img.saraba1st.com/forum/202311/14/032902jsu9mhps1kkzh1ur.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231114-032830.jpg</strong> (50.65 KB, 下载次数: 0)

下载附件

2023-11-14 03:29 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 967#       发表于 2023-11-14 03:49

LanguageBind

通过基于语言的语义对齐(Language-based Semantic Alignment)将视频语言预训练(Video-Language Pretraining)扩展到N(个)模态

github项目主页:https://github.com/PKU-YuanGroup/LanguageBind

相关介绍:https://www.qbitai.com/2023/11/97554.html

视频语言(VL/video-language)预训练在多种下游任务中取得了优秀的改进，然而，当前的VL预训练框架很难扩展到除了视觉和语言之外的其他多种模态(N模态，其中N&gt;=3)

因此，本文提出了LanguageBind，语言模态已经被充分探索并且包含丰富的语义，因此将语言作为不同模态之间的锚定，具体来说，首先通过冻结VL预训练权重获得语言编码器，然后通过对比学习来训练其他模态的编码器，最后所有模态都可以映射到共享特征空间，实现多模态语义对齐

虽然LanguageBind可以将VL模态扩展到N个模态，但还需要一个高质量的包含以语言为中心的对齐数据对的数据集，因此，本文还带来了了具有视频、红外、深度、音频以及对应语言(Video, Infrared, Depth, Audio and their corresponding Language)的VIDAL-10M数据集

在VIDAL-10M中，所有视频都来自具有完整语义的短视频平台的视频，而不是那些从长视频中截断的片段，并且所有视频、深度、红外和音频模态都与其文本描述保持一致

在使用VIDAL-10M进行预训练后，在MSR-VTT数据集上的零样本视频文本检索任务R@1性能优于ImageBind 5.8% ，而且是参数仅为其15%的情况下

除此之外，LanguageBind在零样本视频、音频、深度和红外理解任务方面也有了很大的改进，例如，LanguageBind在MSR-VTT上超越InterVideo 1.9%，在MSVD上超越InterVideo 8.8%，在DiDeMo上超越InterVideo 6.3%，在ActivityNet上超越InterVideo 4.4%

在LLVIP和 NYU-D数据集上，LanguageBind的top-1准确率分别优于ImageBind 23.8%和11.1%

github说明页:

<img src="https://img.saraba1st.com/forum/202311/14/034901jmo16gw9n8n39jp3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231114-034759.jpg</strong> (260.68 KB, 下载次数: 0)

下载附件

2023-11-14 03:49 上传

<img src="https://img.saraba1st.com/forum/202311/14/034901wzdijx7rxsut7mgd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231114-034811.jpg</strong> (432.53 KB, 下载次数: 0)

下载附件

2023-11-14 03:49 上传

<img src="https://img.saraba1st.com/forum/202311/14/034901egt2daarq0z35m0g.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231114-034824.jpg</strong> (309.31 KB, 下载次数: 0)

下载附件

2023-11-14 03:49 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 968#       发表于 2023-11-14 19:45

 本帖最后由 Machinery 于 2023-11-14 19:50 编辑 

JARVIS-1

具有记忆增强的多模态语言模型的开放世界多任务代理者

项目页面:https://craftjarvis-jarvis1.github.io/

github代码仓库:https://github.com/CraftJarvis/JARVIS-1

在开放世界中通过多模态观察实现类人规划以及控制能力是功能更强大的通用代理者们(generalist agents)的一个重要里程碑，现有的方法可以处理开放世界中的某些长远任务，然而当开放世界任务的数量逼近无限时，因为缺乏随着游戏时间的进展逐步提高任务完成度的能力，这些方法依然会陷入困境

本文推出了JARVIS-1，一种开放世界代理者，它可以感知多模态输入(视觉观察和人类指令)、生成复杂的规划并执行具身控制(embodied control)，所有这些都在流行但具有挑战性的开放世界Minecraft宇宙中进行

具体来说，通过在预训练的顶尖多模态语言模型之上开发JARVIS-1，该模型将视觉观察和文本指令映射到规划，这些规划将被发送给目标条件控制器(goal-conditioned controllers)

通过为JARVIS-1配备多模态记忆，这有助于利用预训练的知识及其自己实际的游戏生存经验进行规划，在实验中，JARVIS-1在Minecraft宇宙基准测试(Minecraft Universe Benchmark)中的200多个不同任务中表现出了接近完美的性能

JARVIS-1在长远钻石镐任务(long-horizon diamond pickaxe task)中取得了12.5%的完成率，与之前的记录相比，这增加了5倍，此外，由于多模态记忆的存在，JARVIS-1还能够遵循终身学习范式并进行自我改进，这激发更通用的智力并提高了自主性

<img src="https://img.saraba1st.com/forum/202311/14/194345be6xnxxu6qxqiugw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231114-191154__01.jpg</strong> (384.39 KB, 下载次数: 0)

下载附件

2023-11-14 19:43 上传

关于JARVIS-1如何解锁Minecraft宇宙的技术树，JARVIS-1可以持续获得Minecraft主世界主要科技树上的高级物品，例如钻石、红石和黄金物品，这需要收集10多种不同的中级物品，JARVIS-1不仅在钻石镐方面优于之前最先进的VPT(6% vs. 2.5%可靠性)，而且还可以制作主世界中几乎所有的钻石物品，包括钻石胸甲

<img src="https://img.saraba1st.com/forum/202311/14/194352v0jee7r4e7suj9yr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231114-191502.jpg</strong> (53.68 KB, 下载次数: 0)

下载附件

2023-11-14 19:43 上传

开放世界环境中的挑战以及JARVIS-1如何应对这些挑战

(左)为与没有情境感知规划(situation-aware planning)的基线(GPT)进行的对比，JARVIS-1显著提高了具有挑战性的获取钻石(GettingDiamond)任务的成功率
注：由于资源限制，只能提供10分钟的人工游戏结果

(中)随着任务复杂度的增加石头→铁→钻石(STONE→IRON→DIAMOND)，JARVIS-1凭借交互式规划(interactive planning)展现出更显著的优势

(右)在给定从多模态记忆检索的其他任务(y轴)的上下文经验的情况下，选定任务(x轴)的成功率增益(由颜色深度表示)，凭借终身学习和记忆，JARVIS-1可以利用相关任务的先前经验来更好地进行规划

<img src="https://img.saraba1st.com/forum/202311/14/194400q6gswssg2gmmtgkm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231114-192049.jpg</strong> (106.14 KB, 下载次数: 0)

下载附件

2023-11-14 19:44 上传

JARVIS-1的架构及其自我改进机制
(a)JARVIS-1包含一个生成规划的记忆增强多模态语言模型(MLM)和一个低级动作控制器(low-level action controller)，JARVIS-1还利用多模态记忆来存储和获取经验作为规划的参考

(b)JARVIS-1可以通过探索自己提出的任务(自我指导/self-instruct)和不断增长的记忆来增强自己的规划技能，这有助于更好地规划之前(部分/partially)访问过的任务

<img src="https://img.saraba1st.com/forum/202311/14/194409kxxovcnwn622f6nx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231114-192404.jpg</strong> (139.78 KB, 下载次数: 0)

下载附件

2023-11-14 19:44 上传

JARVIS-1中的交互式规划，在收到当前任务指令和观察后，JARVIS-1将产生一个初始规划，该规划将通过自我检查来修复可能的错误(标记为红色)，此外，如果在执行细化规划的过程中出现任何错误(也用红色标记)，JARVIS-1将尝试通过自我解释从环境反馈中推理出下一步行动，交错的自我检查和自我解释显著提高了JARVIS-1规划的正确性和稳健性

<img src="https://img.saraba1st.com/forum/202311/14/194420fyfae0herayllh9d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231114-192647.jpg</strong> (164.84 KB, 下载次数: 0)

下载附件

2023-11-14 19:44 上传

JARVIS-1中的查询生成(Query generation)，给定一个最近的观察和任务，JARVIS-1将首先进行逆向思考并找出所需的中间子目标，推理将受到有限深度的限制，记忆中存在的子目标将加入当前的视觉观察以形成最终查询，与文本查询匹配的条目将根据其状态到obs查询的感知距离进行排名，并且仅检索每个子目标的top条目

<img src="https://img.saraba1st.com/forum/202311/14/194429kzo9zg9qll4baulq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231114-193047.jpg</strong> (132.24 KB, 下载次数: 0)

下载附件

2023-11-14 19:44 上传

11个任务组的特质，涵盖200多个Minecraft任务

<img src="https://img.saraba1st.com/forum/202311/14/194438ihklbodgkolbig7u.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231114-193146.jpg</strong> (276.96 KB, 下载次数: 0)

下载附件

2023-11-14 19:44 上传

JARVIS-1的结果和其他的Minecraft基线

<img src="https://img.saraba1st.com/forum/202311/14/194444gvz91xnqeqvypqqv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231114-193252.jpg</strong> (76.95 KB, 下载次数: 0)

下载附件

2023-11-14 19:44 上传

不同物品的记忆尺寸的成功率，通过测量Minecraft技术树上关键项目完成的成功率(% Episodes)来评估JARVIS-1在不同记忆大小(代表不同学习阶段)下的性能，随着学习的进展，观察到所有项目的完成率都有所提高，记忆中包含的成功轨迹也越来越多，经过4个epoch的学习，JARVIS-1的记忆中总共积累了425条成功轨迹

<img src="https://img.saraba1st.com/forum/202311/14/194452rhjniirnggxk2gk6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231114-193300.jpg</strong> (71.84 KB, 下载次数: 0)

下载附件

2023-11-14 19:44 上传

不同LLM在 Minecraft任务上的成功率，PT和FT代表预训练和微调的LLaMA2

<img src="https://img.saraba1st.com/forum/202311/14/194458adi1ow4t128ujizj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231114-193318.jpg</strong> (47.56 KB, 下载次数: 0)

下载附件

2023-11-14 19:44 上传

Minecraft任务中记忆消融的成功率，R是推理过程，T和M分别表示文本嵌入和多模态嵌入的检索

<img src="https://img.saraba1st.com/forum/202311/14/194502j718y1vfg000hn2j.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231114-193343.jpg</strong> (81.24 KB, 下载次数: 0)

下载附件

2023-11-14 19:45 上传

(左)不同模型在“ObtainDiamondPickaxe”挑战中相对于游戏时间的成功率，VPT RL在VPT早期游戏的基础上进行了微调，强化学习了超过140万episodes，JARVIS-1代理者及其变体已在任务池中的所有任务上与Minecraft进行了超过4个episodes的交互，通常技术人员需要超过20分钟(24000 步)才能获得钻石镐

(右)JARVIS-1钻石镐合成过程中获得重要中间物品的成功率，该任务已在不同种子上进行了300多次评估，这些曲线表明，随着游戏的进行，获得所有中间物品的成功率都在增加，这表明JARVIS-1正在不断提高自己的技能

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 969#       发表于 2023-11-15 05:18

 本帖最后由 Machinery 于 2023-11-15 05:20 编辑 

Lumos

具有统一数据、模块化设计和开源LLM集成的学习代理者(Learning Agents)

项目主页:https://allenai.github.io/lumos/

github项目代码仓库:https://github.com/allenai/lumos

hugface模型权重:https://huggingface.co/models?sort=trending&amp;search=ai2lumos

数据集下载:https://huggingface.co/datasets?sort=trending&amp;search=ai2lumos

Lumos，一种用于训练语言代理者的新颖框架，采用了统一的数据格式(unified data format)和基于开源大型语言模型(LLM)的模块化架构

Lumos由三个不同的模块组成：规划(planning)、基准(grounding)和执行(execution)，规划模块将任务分解为一系列与工具无关的高级子目标，然后由基准模块通过一组低级操作(low-level actions)将其具体化，这些操作随后由执行模块利用一系列现成的工具和API执行

为了有效地训练这些模块，收集了高质量的子目标和操作的标注用于微调LLM对于复杂问答、网络任务和数学问题等各种任务，利用这种统一的数据和模块化设计，Lumos不仅实现了与当前的SOTA代理者相当甚至更好的性能，而且还展现了其他几个关键优势:
(1)Lumos在复杂问答和网络任务方面超越了基于GPT-4/3.5的代理者的同时还在数学任务上与更大的LLM代理者的表现相当
(2)Lumos的性能优于通过传统训练方法和使用思想链训练创建的开源代理者
(3)Lumos能够有效地泛化到未见的交互任务，超越基于LLM的大型代理者，甚至超过专用的代理者的性能

<img src="https://img.saraba1st.com/forum/202311/15/051829cvvm4r4d31d3h4sv.png" referrerpolicy="no-referrer">

<strong>lumos_architecture.png</strong> (253.96 KB, 下载次数: 0)

下载附件

2023-11-15 05:18 上传

Lumos由以下模块组成：
规划模块：
将复杂的任务分解为一系列用自然语言编写的高级子目标
基准模块：
将规划模块生成的高级子目标转换为低级可执行操作
执行模块：
将动作解析为一系列外部工具，包括 API、小型神经网络模型以及与相关工具和外部环境交互的虚拟模拟器

<img src="https://img.saraba1st.com/forum/202311/15/051836g7bpn777iwjxbb6z.png" referrerpolicy="no-referrer">

<strong>lumos_formulation.png</strong> (291.42 KB, 下载次数: 0)

下载附件

2023-11-15 05:18 上传

尝试了以下两种Lumos构想：
Lumos-Iterative (Lumos-I/迭代):
根据外部环境和先验记忆，在每次迭代中生成一个子目标及其对应的可执行动作，当生成当前第t个子目标时，规划模块需要获取先前规划的子目标以及基准动作的执行结果
Lumos-Onetime (Lumos-O/同时)：
 一个有效的构想，可以同时生成所有子目标和基准行动

<img src="https://img.saraba1st.com/forum/202311/15/051843xs3p3z76wpqq206x.png" referrerpolicy="no-referrer">

<strong>lumos_annotation_example.png</strong> (493.24 KB, 下载次数: 0)

下载附件

2023-11-15 05:18 上传

作为自我指导(Self-Instruct)方法的替代，使用LLM将基准答案的中间推理步骤转换为与提出的构想一致的预期高质量标注，最后能够生成约40K标注来训练Lumos规划和基准模块(语言代理者微调的最大资源之一)，标注源涵盖网络、复杂QA和数学任务类型

评测结果:

<img src="https://img.saraba1st.com/forum/202311/15/051848dxh29e5pvcq2fxev.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231115-051717.jpg</strong> (460.22 KB, 下载次数: 0)

下载附件

2023-11-15 05:18 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 970#       发表于 2023-11-15 07:11

Q-Instruct

改进多模态基础模型的低层级视觉能力

项目主页:https://q-future.github.io/Q-Instruct

hugface数据集下载:https://huggingface.co/datasets/teowu/Q-Instruct

模型园(Model Zoo):https://github.com/Q-Future/Q-Instruct/tree/main/model_zoo

hugface演示:https://huggingface.co/spaces/teowu/Q-Instruct-on-mPLUG-Owl-2

以GPT-4V等模型为代表的多模态基础模型为低级视觉感知和理解任务带来了新的范式，可以响应模型中广泛的自然人类输入的指令，虽然现有的基础模型在低层级视觉任务上显示出了令人兴奋的潜力，但它们的相关能力仍处于初步阶段，需要改进

为了增强这些模型，通过进行的大规模主观实验收集了大量真实的人类对低层级视觉的反馈，每个反馈都遵循一条路径，从对低层级视觉外观(*例如图像的清晰度、颜色、亮度*)的详细描述开始，到总体结论结束，平均长度为45个单词。构建的Q-Pathway数据集包括18973张具有不同低层级外观的图像的58K详细人类反馈

此外，为了使基础模型能够稳健地响应不同类型的问题，还设计了一个GPT参与的转换过程，将这些反馈处理为不同格式的200K指令响应对

实验结果表明，Q-Instruct始终如一地提高了多个基础模型的低层级感知和理解能力，预计数据集可以为通用智能可以感知的未来铺平道路 ，能够了解低层级视觉外观并像人类一样评估视觉质量

<img src="https://img.saraba1st.com/forum/202311/15/071016nx8yku8clayxelq2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231115-064909__01.jpg</strong> (463.64 KB, 下载次数: 0)

下载附件

2023-11-15 07:10 上传

与基线版本相比，经过Q-Instruct调整的LLaVA-v1.5-7B在各种低层级视觉任务上的能力

<img src="https://img.saraba1st.com/forum/202311/15/071021q4jd4jj04r4vrr0f.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231115-065128.jpg</strong> (175.97 KB, 下载次数: 0)

下载附件

2023-11-15 07:10 上传

数据构造工作流程管道，首先，收集了58K条关于低层级视觉方面的人类反馈(the Q-pathway，a/b)，然后将它们转换为200K的指令响应对(Q-Instruct，c)，用于(d)低层级视觉指令调整

<img src="https://img.saraba1st.com/forum/202311/15/071026pj17a12w4j717y1y.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231115-065446.jpg</strong> (122.75 KB, 下载次数: 0)

下载附件

2023-11-15 07:10 上传

Q-Pathway与其来源的对比，对源图像进行子采样，以减少其MOS分布的偏差，使采样的分布更为平衡

<img src="https://img.saraba1st.com/forum/202311/15/071035p0bi9cmjrbllttj9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231115-065635__01.jpg</strong> (557.84 KB, 下载次数: 0)

下载附件

2023-11-15 07:10 上传

路径反馈的示例，每个反馈都包含详细描述，然后是总体评估，并包含上下文

(b)路径反馈长度的分布
(c)Q-Pathway的文字云
(d)与低层级视力相关的高频词

<img src="https://img.saraba1st.com/forum/202311/15/071044bbedax9409d4e909.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231115-065857__01.jpg</strong> (631.1 KB, 下载次数: 0)

下载附件

2023-11-15 07:10 上传

Q-Instruct数据集的组成，其中200K 指令响应对包括:
(a)58K路径推理
(b)视觉问答，其中76K是什么/如何问题和57K平衡的是或否问题
(c)12K扩展对话

<img src="https://img.saraba1st.com/forum/202311/15/071053uh84ccl4thppzcdk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231115-070151__01.jpg</strong> (157.9 KB, 下载次数: 0)

下载附件

2023-11-15 07:10 上传

研究中评估了低层级视觉指令调整的训练策略，包括:
(a)将Q-Instruct与高层级视觉指令调整数据集混合
(b)在高层级视觉指令调整之后仅使用Q-Instruct进行进一步的低层级调整阶段

<img src="https://img.saraba1st.com/forum/202311/15/071100kg6v3vmohv36zd7o.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231115-070151__02.jpg</strong> (87.23 KB, 下载次数: 0)

下载附件

2023-11-15 07:11 上传

用于低层级视觉指令调整的基线MLLM

相关评估数据:

<img src="https://img.saraba1st.com/forum/202311/15/071132e0p0c7ulhuhvlg7u.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231115-070507__01.jpg</strong> (730.17 KB, 下载次数: 0)

下载附件

2023-11-15 07:11 上传

<img src="https://img.saraba1st.com/forum/202311/15/071132m0ff37zx1smfs7v8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231115-070518__01.jpg</strong> (182.93 KB, 下载次数: 0)

下载附件

2023-11-15 07:11 上传

<img src="https://img.saraba1st.com/forum/202311/15/071132lvs7d5n61ecqeenb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231115-070518__02.jpg</strong> (126.4 KB, 下载次数: 0)

下载附件

2023-11-15 07:11 上传

<img src="https://img.saraba1st.com/forum/202311/15/071132vb2j4t8e3wrz79vr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231115-070534__01.jpg</strong> (635.52 KB, 下载次数: 0)

下载附件

2023-11-15 07:11 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 971#       发表于 2023-11-15 07:51

ChatAnything

与LLM增强(LLM-Enhanced)角色进行面对面聊天(Facetime Chat)

项目主页:https://chatanything.github.io/

github项目主页:https://github.com/zhoudaquan/ChatAnything

hugface模型下载:https://huggingface.co/ermu2001/ChatAnything

演示Demo:https://26fed97b4a7706bed0.gradio.live/

在这份技术报告中的目标是以在线方式为基于LLM的角色生成拟人化的角色，包括视觉外观(visual appearance)、性格(personality)和音调(tones)，而且仅使用文本描述

为了实现这一目标，首先通过精心设计的一系列系统提示(system prompts)，利用LLM的上下文学习能力来生成性格，还提出了两个新颖的概念:声音混合(MoV/mixture of voices)和扩散混合(MoD/mixture of diffusers)，用于生成不同的声音和外观

对于MoV，利用具有各种预定义音调的文本转语音(TTS)算法，并根据用户提供的文本描述自动选择最匹配的一种

对于MoD，结合了最近流行的文本到图像生成技术和说话头部算法(talking head algorithms)来简化生成说话对象的过程

整个框架称为ChatAnything，有了它，用户只需输入几个文本即可为具有任何拟人角色的任何内容制作动画，然而，还观察到当前生成模型生成的拟人对象通常无法被预先训练的人脸特征点检测器(face landmark detectors)检测到，从而导致人脸运动生成失败，即使这些人脸具有类似人类的外观，为了解决这个问题，通过在图像生成阶段采用像素级指导来注入人脸标志

为了对这些指标进行基准测试，构建了一个评估数据集，基于此验证了人脸特征点的检测率从57.0%显著提高到了92.5%，从而允许为基于生成的语音内容自动进行人脸动画化

<img src="https://img.saraba1st.com/forum/202311/15/074842ovochbthoc1201z2.jpg" referrerpolicy="no-referrer">

<strong>e672023c-2f06-42df-817c-a742f3871f55.jpg</strong> (112.14 KB, 下载次数: 0)

下载附件

2023-11-15 07:48 上传

ChatAnything的整体工作流程，框架包括四个关键组件：
1.头像生成组件，基于LLM的控制模块，用于初始化用户的文本描述角色的个性，它还用于管理系统操作并根据与用户的交互调用应用程序
2.个性生成组件，为人物角色生成参考图像的头像初始值设定项，它包括微调扩散模型(MoD)以及LoRA模块(如果应用)的组合，每个模型都专门生成特定风格的图像，根据LLM角色的用户文本描述自动调用最匹配的模型
3.一个语音生成组件，文本转语音模块(MoV)的混合体，可以将角色输入的文本转换为具有自定义音调的语音信号，该选择是LLM根据用户文本描述自动完成的
4.面部驱动组件，运动生成模块，接收语音信号并驱动生成的图像

为了增强用户定义能力，还提出了两个新颖的概念:声音混合(MoV/mixture of voices)和扩散混合(MoD/mixture of diffusers)，可以根据用户文字描述进行定制，用于生成不同的声音和外观

<img src="https://img.saraba1st.com/forum/202311/15/074850xuk1phuc7mffc2a1.jpg" referrerpolicy="no-referrer">

<strong>14cb94fa-432d-4516-ae33-b1d6d7e55e14.jpg</strong> (126.61 KB, 下载次数: 0)

下载附件

2023-11-15 07:48 上传

扩散过程中特征点引导的影响，如第一行所示，直接应用SD1.5进行人像生成往往会产生抽象的人脸图像，这些图像在说话头部模型的训练过程中很少看到，因此不能用作面部表情生成的输入，不同的是，在应用ChatAnything中提出的技术(包括面部标志引导、提示工程和LoRA微调以提高美观性)后，模型倾向于生成更多具有高视觉质量的拟人图像，而且这些图像可以用作预训练的说话头部模型的输入

<img src="https://img.saraba1st.com/forum/202311/15/074856yn5f4018l8j8jlnc.jpg" referrerpolicy="no-referrer">

<strong>88538b79-10cb-43f5-9fb4-aa76b2ceeb56.jpg</strong> (294.33 KB, 下载次数: 0)

下载附件

2023-11-15 07:48 上传

强大的语言模型选择了多种图像生成模型和多种TTS语音，选择的预训练生成模型来生成初始帧，在这之后，对于生成的帧，开源动画模块根据另一个选定的TTS语音的音频输出来渲染视频，这里是由工作流程生成的动画的面部网格，显示了想象中的说话面部的平均期望

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 972#       发表于 2023-11-16 03:06

Cappy

使用小型评分器(Small Scorer)超越并提升大型多任务语言模型

github项目主页:https://github.com/tanyuqian/cappy

hugface权重下载:https://huggingface.co/btan2/cappy-large

类似T0、FLAN和OPT-IML之类的大型语言模型(LLM)在统一的指令跟随范式下运行，擅长执行多任务，并且对未见的任务也表现出了卓越的泛化能力，尽管它们的性能令人印象深刻，但这些LLM的参数大小从数十亿到数千亿不等，需要大量的计算资源，使得它们的训练和推理成本高昂且效率低下，此外，由于微调对硬件的广泛要求，使这些模型适应下游应用程序，特别是复杂的任务，通常是不可行的，即使使用提示调整等参数效率的方法也是如此

最强大的多任务LLM系列(例如OPT-IML-175B和FLAN-PaLM-540B)无法公开访问，这严重限制了它们的潜在定制能力方面，为了应对这些挑战，本文引入了预训练的小型评分器，Cappy，旨在提高多任务LLM的性能和效率

Cappy仅具有3.6亿参数，既可以独立的执行分类任务，也可以作为LLM的辅助组件提高其性能，此外Cappy还能够有效地集成下游任务监督，无需LLM微调的同时做到了无需访问其参数

实验表明，当独立完成PromptSource的11种语言理解任务时，Cappy的表现比LLM高出几个数量级，此外，在BIG-Bench的45个复杂任务上，Cappy大幅提升了高级多任务LLM FLAN-T5的性能，Cappy还可以灵活地与其他LLM变体进行合作，包括微调和上下文学习，提供额外的性能增强

<img src="https://img.saraba1st.com/forum/202311/16/030555okm9m2uyrdurbyky.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-024530.jpg</strong> (73.56 KB, 下载次数: 0)

下载附件

2023-11-16 03:05 上传

左图:Cappy的表现优于多任务LLM，总体准确率超过了PromptSource的11项测试任务的平均值，图中每条虚线连接到同一型号模型的不同参数规模版本，更靠近左上方的线条表示效率更高且性能更优越的模型

右图:Cappy提升了多任务LLM在BIG-Bench中超过45个复杂任务的平均Rouge-L分数，图中每条虚线代表一种适用于各种参数规模的LLM的方法，自我评分是指利用LLM的交叉熵来选择响应

<img src="https://img.saraba1st.com/forum/202311/16/030600fxxpp5w52mtkw8m5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-024955.jpg</strong> (84.77 KB, 下载次数: 0)

下载附件

2023-11-16 03:06 上传

左图:Cappy的建模方法

右图:说明Cappy在增强多任务LLM方面的应用，以及通过Cappy进行的下游适应与其他依赖LLM参数的方法(例如微调和提示调整)之间的对比

<img src="https://img.saraba1st.com/forum/202311/16/030606nxigmx7gcvanx5n8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-025221.jpg</strong> (64.14 KB, 下载次数: 0)

下载附件

2023-11-16 03:06 上传

使用多任务LLM进行数据增强，为Cappy的预训练和微调构建弱监督回归数据集

<img src="https://img.saraba1st.com/forum/202311/16/030614qv1m7ai7v1za17io.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-025339.jpg</strong> (101.99 KB, 下载次数: 0)

下载附件

2023-11-16 03:06 上传

Cappy和多任务LLM在各种测试数据集上的性能，一系列的虚线用于连接同一模型型号的不同参数规模版本，例如OPT-30B与OPT-175B，位于图表左上角的线或点表示模型更高效且性能更优越，每个图对应一个特定的测试任务，但ANLI除外，它代表三个不同的任务(ANLI-R1/R2/R3)

<img src="https://img.saraba1st.com/forum/202311/16/030621zxn9equip1xiknpn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-025622.jpg</strong> (154.53 KB, 下载次数: 0)

下载附件

2023-11-16 03:06 上传

左图:图中总体准确度是PromptSource零样本设置下的11项保留测试任务的平均值，“RLHF-RM”指4.1节中提到的RLHF奖励模型

右图:45个BIG-Bench任务的平均Rouge-L得分，其中主干FLAN-T5模型已被冻结，“ICL”指的是上下文学习，即在指令的前缀中附加训练示例

<img src="https://img.saraba1st.com/forum/202311/16/030628at705eq0cqrkyds9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-025952__01.jpg</strong> (199.37 KB, 下载次数: 0)

下载附件

2023-11-16 03:06 上传

在45个BIG-Bench任务上，Cappy评分优于FLAN-T5-XXL的自我评分方法，x轴是任务的名称

<img src="https://img.saraba1st.com/forum/202311/16/030638b00prz422c33p3zj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-030101.jpg</strong> (123.96 KB, 下载次数: 0)

下载附件

2023-11-16 03:06 上传

当主干FLAN-T5模型也经过微调时，BIG-Bench任务的平均Rouge-L得分

<img src="https://img.saraba1st.com/forum/202311/16/030642rctr10dt4r0u1bcc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-030156.jpg</strong> (178.66 KB, 下载次数: 0)

下载附件

2023-11-16 03:06 上传

Cappy评分与FLAN-T5-XXL自我评分方法相比明显处于劣势的任务

<img src="https://img.saraba1st.com/forum/202311/16/030646fpye3zcvglyexu43.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-030238.jpg</strong> (37.15 KB, 下载次数: 0)

下载附件

2023-11-16 03:06 上传

BIG-Bench适配(adaptation)在具有不同数量样本的冻结FLAN-T5-XXL上的性能

<img src="https://img.saraba1st.com/forum/202311/16/030650ibzpbn11rbzb18h9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-030425.jpg</strong> (54.53 KB, 下载次数: 0)

下载附件

2023-11-16 03:06 上传

BIG-Bench适配的性能，在使用LLM消融Cappy预训练和数据增强之后，括号中的数字是性能下降

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 973#       发表于 2023-11-16 03:42

LayoutPrompter

唤醒大型语言模型的设计能力

项目主页:https://github.com/microsoft/LayoutGeneration/tree/main/LayoutPrompter

条件图形布局生成(Conditional graphic layout generation)可以自动将用户约束映射成高质量的布局，如今已引起广泛关注，尽管最近的研究工作取得了有希望的进展，但缺乏通用性和数据效率阻碍了它们的实际应用

在这项工作中，提出了LayoutPrompter，通过利用大型语言模型(LLM)的上下文学习来解决上述问题，LayoutPrompter由三个关键组件组成:输入输出序列化(input-output serialization)、动态示例选择(dynamic exemplar selection)和布局排名(layout ranking)

具体来说，输入输出序列化组件为每个布局生成任务精心设计的输入和输出格式，动态示例选择负责为给定输入选择最有帮助的提示样本，布局排名器用于从LLM的多个输出中挑选最高质量的布局

通过使用四个公共数据集对所有现有布局生成任务进行实验，尽管方法很简单，但实验结果表明，在这些任务上，LayoutPrompter可以与SOTA方法竞争甚至超越，而无需任何模型训练或微调，这证明了这种方法的通用性且无需训练的有效性

此外，消融实验还表明，在低数据情况(low-data regime)下，LayoutPrompter显著优于基于训练的基线，进一步表明了LayoutPrompter的数据效率

<img src="https://img.saraba1st.com/forum/202311/16/034101kmsb65fm6hvarssh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-032841.jpg</strong> (110.07 KB, 下载次数: 0)

下载附件

2023-11-16 03:41 上传

LayoutPrompter是一种通用的图形布局生成方法，能够解决一系列布局域(如右侧所示)的各种条件布局生成任务(如左侧所示)，而无需任何模型训练或微调

<img src="https://img.saraba1st.com/forum/202311/16/034107x6rem70hfljmlj8x.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-033010.jpg</strong> (44.27 KB, 下载次数: 0)

下载附件

2023-11-16 03:41 上传

现有条件布局生成方法与Layout Prompter的对比

<img src="https://img.saraba1st.com/forum/202311/16/034117ithc0wmlk6zl0xh7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-033108.jpg</strong> (117.3 KB, 下载次数: 0)

下载附件

2023-11-16 03:41 上传

LayoutPrompter的概览图，完整的提示由特定于任务的前言、N个上下文示例和一个测试输入组成，根据测试输入从训练集中动态检索样本，随后，将提示输入LLM以生成L个不同的布局，最后使用布局排名器来选择最好的一种作为最终输出

<img src="https://img.saraba1st.com/forum/202311/16/034121h393h8uoshh98167.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-033347.jpg</strong> (66.56 KB, 下载次数: 0)

下载附件

2023-11-16 03:41 上传

输入画布被转换为显著图(saliency map)

<img src="https://img.saraba1st.com/forum/202311/16/034126b0rwgip2m2kvrarz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-033513.jpg</strong> (142.61 KB, 下载次数: 0)

下载附件

2023-11-16 03:41 上传

与约束显式布局生成任务的基线进行定量对比，↑表示数值越大越好，↓表示数值越小越好

<img src="https://img.saraba1st.com/forum/202311/16/034130ixmm2u0ox5njwk5m.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-033605.jpg</strong> (54.21 KB, 下载次数: 0)

下载附件

2023-11-16 03:41 上传

数据集统计，请注意，这些数据集仅用于特定任务

<img src="https://img.saraba1st.com/forum/202311/16/034134edde3g2gy7gd79d0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-033636.jpg</strong> (174.69 KB, 下载次数: 0)

下载附件

2023-11-16 03:41 上传

LayoutPrompter与SOTA基线Layout-Former++在约束显式布局生成任务上的定性对比

<img src="https://img.saraba1st.com/forum/202311/16/034138wbdbna0v3ib0gxd0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-033731.jpg</strong> (40.46 KB, 下载次数: 0)

下载附件

2023-11-16 03:41 上传

在内容感知布局生成任务上与基线的定量对比

<img src="https://img.saraba1st.com/forum/202311/16/034142h6mjicf6pfkifavu.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-033815.jpg</strong> (155.82 KB, 下载次数: 0)

下载附件

2023-11-16 03:41 上传

DS-GAN与LayoutPrompter在内容感知布局生成方面生成的定性对比结果，元素类型分为三种，包括logo(红)、文本(绿)和底层(黄色)

<img src="https://img.saraba1st.com/forum/202311/16/034151lxx5vf8htff3t9zp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-034001.jpg</strong> (229.96 KB, 下载次数: 0)

下载附件

2023-11-16 03:41 上传

其他性能对比

<img src="https://img.saraba1st.com/forum/202311/16/034159yt1gu77le70eyg7g.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-034010.jpg</strong> (227.97 KB, 下载次数: 0)

下载附件

2023-11-16 03:41 上传

消融实验

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 974#       发表于 2023-11-16 05:30

Instant3D

即时文本到3D生成(Text-to-3D generation)

项目主页:https://ming1993li.github.io/Instant3DProj/

code:coming soon

文本到3D生成任务旨在根据文本提示合成栩栩如生的3D对象，这引起了计算机视觉社区的广泛关注，现有的一些工作已经在这项任务上取得了令人印象深刻的结果，但它们主要依赖于耗时的优化(time-consuming optimization)范式，具体来说，这些方法每次都针对文本提示从头优化神经场(neural field)，这大约需要一小时甚至更长时间才能生成一个对象，这种繁重且重复的训练成本阻碍了它们的实际部署

在本文中，提出了一种快速的文本到3D生成新框架，称之为Instant3D，在经过训练后，Instant3D能够仅通过一次前馈网络过程，即可在不到一秒的时间内为未见的各种文本提示创建3D对象，通过设计一种新的网络最终实现了这种惊人的速度，该网络可以根据文本提示直接构建3D三平面(3D triplane)，Instant3D的核心创新在于探索了有效地将文本条件注入网络的策略

此外，还提出了一种简单而有效的激活函数，scaled-sigmoid，来代替原本的sigmoid函数，将训练收敛速度加快了十倍以上，最后，为了解决过去方法在3D生成中遇到的Janus多头问题，还提出了一种自适应Perp-Neg算法，该算法可以在训练过程中根据Janus问题的严重程度动态调整其概念否定尺度(concept negation scales)，有效减少了多头效应 

对各种基准数据集的大量实验表明，所提出的算法在定性和定量上都优于SOTA方法，同时实现了更高的效率

<img src="https://img.saraba1st.com/forum/202311/16/052936xafqhfyjqv45cfaf.png" referrerpolicy="no-referrer">

<strong>rabbit.png</strong> (794.6 KB, 下载次数: 0)

下载附件

2023-11-16 05:29 上传

现有的SOTA方法与本文提案的对比

现有方法针对每个文本提示从头开始优化随机初始化的NeRF，这通常需要超过10000次迭代和数小时才能收敛，相比之下，本文方法旨在学习文本条件的NeRF，其训练计算成本要少得多，并且对新提示具有很强的泛化能力，同时它能够在前馈网络的仅一次传递中即可为未见的文本提示生成3D对象的条件3D表征(三平面)，仅需25毫秒

<img src="https://img.saraba1st.com/forum/202311/16/052942sicbvt6tcghtfbz4.jpg" referrerpolicy="no-referrer">

<strong>overview.jpg</strong> (130.78 KB, 下载次数: 0)

下载附件

2023-11-16 05:29 上传

Instant3D的概览图，通过应用条件解码器网络将文本提示映射到相应的三平面，这个过程中，交叉注意力、风格注入和 token 到平面转换三种条件机制无缝结合，连接了文本和3D，解决了SDS弱监督的问题

在给定随机相机姿态，通过基于坐标的特征采样、点密度和反照率预测(albedo prediction)以及可微的体积渲染，从条件三平面直接渲染2D图像

对于反照率激活(albedo activation)，还提出了一个缩放的sigmoid函数，有效地加速了训练收敛，在训练过程中，视图图像(view image)首先通过添加随机噪声进行扩散，然后输入到以文本提示为条件的预训练UNet中进行去噪，从而提供SDS损失的梯度

最后，提出了一种自适应Perp-Neg算法，用以更好地解决框架中的Janus问题，在推理过程中，Instant3D可以在不到一秒的时间内从未见的各种文本提示中泛化推断出可置信的3D对象

样例:

<img src="https://img.saraba1st.com/forum/202311/16/052958bmedq8jckpe8idke.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-052848.jpg</strong> (335.89 KB, 下载次数: 0)

下载附件

2023-11-16 05:29 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 975#       发表于 2023-11-16 05:52

 本帖最后由 Machinery 于 2023-11-16 05:53 编辑 

One-2-3-45++

通过一致的多视图生成与3D扩散快速将单图像转换为3D对象

项目主页:https://sudo-ai-3d.github.io/One2345plus_page

github项目仓库:https://github.com/SUDO-AI-3D/One2345plus

演示Demo:https://www.sudo.ai/3dgen

最近关于开放世界3D对象生成领域的进展非常显著，图像转3D方法比文本转3D方法提供了更细粒度的控制，然而，大多数现有模型无法同时提供快速的生成速度和输入图像的高保真度——但这两个功能对于实际应用至关重要

在本文中，提出了One-2-3-45++，一种创新方法，可以在大约一分钟内将单个图像转换为详细的3D纹理网格，本方法旨在充分利用2D扩散模型中嵌入的广泛知识以及来自价值有限的3D数据的先验知识，这是通过首先微调2D扩散模型生成一致的多视图图像，然后借助多视图条件3D原生扩散模型将这些图像提升为3D对象实现的

广泛的实验评估表明，本文方法可以生成高度反映原始输入图像的高质量、多样化的3D资源

<img src="https://img.saraba1st.com/forum/202311/16/055150ebu4fp4e5mcm5pf5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-054544.jpg</strong> (184.96 KB, 下载次数: 0)

下载附件

2023-11-16 05:51 上传

One-2-3-45++能够在一分钟内将任何对象的单个RGB图像转换为高保真纹理网格，生成的网格紧密地映射了原始输入图像的网格，只需8张A100 GPU即可训练One-2-3-45++

<img src="https://img.saraba1st.com/forum/202311/16/055200jrtwwrzp19bf9txi.png" referrerpolicy="no-referrer">

<strong>method.png</strong> (994.36 KB, 下载次数: 0)

下载附件

2023-11-16 05:52 上传

从单个图像作为输入开始，最初通过微调2D扩散模型来生成一致的多视图图像，然后，这些多视图图像通过一对(a pair)3D原生扩散网络提升为3D，在整个3D扩散过程中，生成的多视图图像充当必要的指导条件，从去噪的体积中提取3D网格后，再通过采用多视图图像作为监督的轻量级优化来进一步增强纹理，One-2-3-45++能够在20秒内生成初始纹理网格，并在大约一分钟内提供精致的网格

<img src="https://img.saraba1st.com/forum/202311/16/055205pi4tt11ji4igg0j4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-054919.jpg</strong> (85.81 KB, 下载次数: 0)

下载附件

2023-11-16 05:52 上传

涉及53名参与者的用户研究结果，其中每个单元格显示一种方法(行)优于另一种方法(列)的概率或偏好率

<img src="https://img.saraba1st.com/forum/202311/16/055211welc0osto7alesee.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-055017.jpg</strong> (233.87 KB, 下载次数: 0)

下载附件

2023-11-16 05:52 上传

One-2-3-45++可以显著提高3D游戏艺术家的效率和创造力，视频中的每个3D资源都是由本方法的AI创建的(可前往项目主页查看视频)

其他数据集的生成样例:

<img src="https://img.saraba1st.com/forum/202311/16/055226k8rqnnm1zd1nl8ih.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-054856.jpg</strong> (205.57 KB, 下载次数: 0)

下载附件

2023-11-16 05:52 上传

<img src="https://img.saraba1st.com/forum/202311/16/055226azakmkvdxp7bamvm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-054906.jpg</strong> (224.92 KB, 下载次数: 0)

下载附件

2023-11-16 05:52 上传

<img src="https://img.saraba1st.com/forum/202311/16/055226ei76pi8v78m64x48.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-054913.jpg</strong> (119.94 KB, 下载次数: 0)

下载附件

2023-11-16 05:52 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 976#       发表于 2023-11-16 19:04

IFEval

大型语言模型的指令跟随评估

github项目主页:https://github.com/google-research/google-research/tree/master/instruction_following_eval

现代大型语言模型(LLM)的一项核心功能是遵循自然语言指令，然而，对此类能力的评估并不标准化：人工评估昂贵、缓慢且不客观，难以再现，而基于LLM的自动评估可能潜在的存在偏见或受到评估LLM能力的限制

为了克服这些问题，本文为大型语言模型引入了指令跟随评估(IFEval/Instruction-Following Eval)，IFEval是一个简单且易于复制的评估基准，它侧重于一套“可验证的指令(verifiable instructions)”，例如“写400字以上”和“至少提及AI的关键字3次”

IFEval确定了25种可验证指令，并构建了大约500个提示，每个提示都包含一个或多个可验证指令，展示了当前两种广泛使用的LLM的评估结果

<img src="https://img.saraba1st.com/forum/202311/16/190413dg6d5zs0qps051dl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-185714__01.jpg</strong> (158.75 KB, 下载次数: 0)

下载附件

2023-11-16 19:04 上传

诸如“写至少25个句子”之类的指令可以被自动、客观地验证，研究组构建了一组带有可验证指令的提示，用于评估大型语言模型的指令跟随能力

<img src="https://img.saraba1st.com/forum/202311/16/190437dpmdoadpcd5rkdp6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-185828.jpg</strong> (518.96 KB, 下载次数: 0)

下载附件

2023-11-16 19:04 上传

25个可验证指令的列表，并附有简要说明，之所以使用这些指令是因为它们很容易验证或者在实际应用中很常见。该列表可以轻松扩展，例如，可以添加“语言 - 响应中混合两种语言”和“可检测格式 - XML格式”等

<img src="https://img.saraba1st.com/forum/202311/16/190442l7xcqsq9c37cc3a9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-190020.jpg</strong> (226.16 KB, 下载次数: 0)

下载附件

2023-11-16 19:04 上传

带有可验证说明的提示示例(斜体内容)

<img src="https://img.saraba1st.com/forum/202311/16/190446rneocuou4cdoetlh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-190131.jpg</strong> (39.73 KB, 下载次数: 0)

下载附件

2023-11-16 19:04 上传

依据IFEval测试的总体指令遵循精度，由于参数数量差异较大，两个模型不具有直接可比性

<img src="https://img.saraba1st.com/forum/202311/16/190451hz0r177t5665e7pp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-190240.jpg</strong> (62.5 KB, 下载次数: 0)

下载附件

2023-11-16 19:04 上传

每个模型的指令级严格精度(Instruction-level strict-accuracy)，按每个指令的类别分开

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  穷人也是人  
##### 977#       发表于 2023-11-16 19:16

强烈马克


*****

####  Machinery  
##### 978#       发表于 2023-11-16 19:54

 本帖最后由 Machinery 于 2023-11-16 19:55 编辑 

Qwen-Audio

通过统一的大规模音频语言模型(Large-Scale Audio-Language Models)促进通用音频理解

项目主页:https://qwen-audio.github.io/Qwen-Audio/

github项目主页:https://github.com/QwenLM/Qwen-Audio

最近，能够跟随指令的音频语言模型在与人类的音频交互中受到了广泛的关注，然而，缺乏能够处理不同音频类型和任务的预训练音频模型导致了阻碍该领域的进展，大多数现有作品只能支持有限范围的交互能力

在本文中，研究组开发了Qwen-Audio模型，并通过扩展音频语言预训练来解决这一限制，用以涵盖30多种任务和多种音频类型，例如人类语音、自然声音、音乐和歌曲，以促进通用音频理解能力，然而，直接协同训练(co-training)所有的任务和数据集可能会导致干扰问题，取决于不同的任务焦点、语言、标注粒度和文本结构的差异，不同数据集相关的文本标签可能会表现出相当大的变化

为了克服一对多干扰，精心设计了一个多任务训练框架，以对解码器的一系列分层标签作为条件(conditioning on a sequence of hierarchical tags)，分别通过共享标签和指定标签来鼓励知识共享并避免干扰

Qwen-Audio在各种基准测试任务中都取得了令人印象深刻的性能，无需任何特定于任务的微调，超越了同类产品，在Qwen-Audio的基础上，还进一步开发了Qwen-Audio-Chat，它允许以各种音频和文本作为输入，实现多轮对话并支持多种以音频中心的场景

<img src="https://img.saraba1st.com/forum/202311/16/195334ex5hqnncj5j7gzqx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-194238.jpg</strong> (105.43 KB, 下载次数: 0)

下载附件

2023-11-16 19:53 上传

Qwen-Audio和之前来自多任务音频文本学习模型的顶级性能对比，例如SpeechT5、SpeechNet、SpeechLLaMA、SpeechLLaMA、SALMONN和Pengi

<img src="https://img.saraba1st.com/forum/202311/16/195339spkpkewhk82wdwce.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-194800.jpg</strong> (362.2 KB, 下载次数: 0)

下载附件

2023-11-16 19:53 上传

展示了12个数据集的测试集结果，涵盖自动语音识别(ASR/Automatic Speech Recognition)、语音到文本翻译(S2TT/Speech-to-Text Translation)、自动音频字幕说明(AAC/Automatic Audio Captioning)、声学场景分类 (ASC/Acoustic Scene Classification)、语音情感识别(SER/Speech Emotion Recognition) 、音频问答(AQA/Audio Question and Answering)、语音分类(VSC/Vocal Sound Classification)和音乐音符分析(MNA/Music Note Analysis)

<img src="https://img.saraba1st.com/forum/202311/16/195347dhugqahhbld45jqw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-194946.jpg</strong> (165.64 KB, 下载次数: 0)

下载附件

2023-11-16 19:53 上传

Qwen-Audio的示例展示了其感知和理解各种类型音频的能力，Qwen-Audio还支持多音频分析、声音理解和推理、音乐欣赏以及语音编辑工具的使用

<img src="https://img.saraba1st.com/forum/202311/16/195358ebbr6rsqll33r97l.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-195050.jpg</strong> (260.01 KB, 下载次数: 0)

下载附件

2023-11-16 19:53 上传

Qwen-Audio架构和多任务预训练概览图

<img src="https://img.saraba1st.com/forum/202311/16/195403jl0r3t8z3t8rthys.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-195121.jpg</strong> (102.08 KB, 下载次数: 0)

下载附件

2023-11-16 19:54 上传

多任务预训练数据集

<img src="https://img.saraba1st.com/forum/202311/16/195408gegpgizrmzprlgep.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-195210.jpg</strong> (306.17 KB, 下载次数: 0)

下载附件

2023-11-16 19:54 上传

Qwen-Audio评估基准的摘要

相关评估结果:

<img src="https://img.saraba1st.com/forum/202311/16/195419i2llmvvmu9ddd9az.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-195257.jpg</strong> (422.16 KB, 下载次数: 0)

下载附件

2023-11-16 19:54 上传

<img src="https://img.saraba1st.com/forum/202311/16/195419cgkpvzr8vgkpcrr0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231116-195305.jpg</strong> (95.26 KB, 下载次数: 0)

下载附件

2023-11-16 19:54 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 979#       发表于 2023-11-18 03:41

 本帖最后由 Machinery 于 2023-11-18 03:44 编辑 

RED-DOT

通过相关证据检测进行多模态事实检查(Multimodal Fact-checking)

github项目仓库:https://github.com/stevejpapad/relevant-evidence-detection

在线的错误信息通常是多模态的，且通常是由文本和随附(accompanying)的图像之间的误导性关联引起的，为了进行事实核查过程，研究人员最近一直在开发自动多模态的方法，用于收集和分析与所检查的图像文本对相关的外部信息、证据

然而，之前的研究假设所有收集到的证据都是相关(relevant)的，在本研究中，引入了“相关证据检测”(RED/Relevant Evidence Detection)模块来辨别每个证据是否相关，以支持或否定该主张

具体来说，开发了“相关证据检测指向Transformer”(RED-DOT/Relevant Evidence Detection Directed Transformer)并探索了多种架构变体(例如单阶段或双阶段)和机制，例如“引导注意力”(guided attention)

广泛的消融和对比实验表明，RED-DOT在VERITE基准上比SOTA技术显著提高了28.5%，此外，重排序(re-ranking)和元素注意的模态融合(element-wise modality fusion)可以使RED-DOT在NewsCLIPings+上实现了具有竞争力的改进性能，而无需大量证据或多个骨干编码器

最后，定性分析表明，所提出的“引导注意力”模块有可能增强架构的可解释性

<img src="https://img.saraba1st.com/forum/202311/18/034059galqweeuf6keeklk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231118-031905__01.jpg</strong> (375.94 KB, 下载次数: 0)

下载附件

2023-11-18 03:40 上传

图像文本对正在与从网络收集的外部证据(图像和文本)一起进行验证，本文所提案的框架检索证据并重排序，同时RED-DOT确定哪些信息与图像文本对最相关(支持或反对)，然后使用这些信息来确定该图像文本对的真实性

<img src="https://img.saraba1st.com/forum/202311/18/034104j9aa4j94pgpj9g4b.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231118-032448.jpg</strong> (54.59 KB, 下载次数: 0)

下载附件

2023-11-18 03:41 上传

方程2的可视化，用于检索“不相关”证据的困难负采样

<img src="https://img.saraba1st.com/forum/202311/18/034110a90dnixnnyfzism9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231118-032529.jpg</strong> (68.54 KB, 下载次数: 0)

下载附件

2023-11-18 03:41 上传

所提案的RED-DOT中的Transformer D(·)的概览，应用于“模态融合”

<img src="https://img.saraba1st.com/forum/202311/18/034115ysjhtdz5ztpp2jss.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231118-032805.jpg</strong> (43.7 KB, 下载次数: 0)

下载附件

2023-11-18 03:41 上传

单阶段和双阶段RED-DOT变体的高层次概览图，虚线代表DSL的第二阶段

<img src="https://img.saraba1st.com/forum/202311/18/034123keoo4otsdlhl0waw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231118-033500__01__01.jpg</strong> (124.98 KB, 下载次数: 0)

下载附件

2023-11-18 03:41 上传

与SOTA进行对比，所有方法均在NewsCLIPings+(简称“News”)上进行了训练，†表示“R-NESt + CHASMA-D + NC-t2t”，在这里，M、K+和M、K-分别表示作为模型输入提供的相关和不相关证据的数量

<img src="https://img.saraba1st.com/forum/202311/18/034127b4txl66wrzxiysr6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231118-033740__01.jpg</strong> (408.74 KB, 下载次数: 0)

下载附件

2023-11-18 03:41 上传

通过RED-DOT变体进行推理：基于NewsCLIPings+样本的DSL和DSL+GA，报告了每种方法分配的注意力分数，为了简单起见，[T e−, I e−, T e+, I e+]的“相关性基准答案”设置分别为[0, 0, 1, 1]

<img src="https://img.saraba1st.com/forum/202311/18/034131mibbtqz4ae8kzeky.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231118-033957.jpg</strong> (35.84 KB, 下载次数: 0)

下载附件

2023-11-18 03:41 上传

DSL和DSL+GA根据“相关”和“不相关”证据分配的注意力分数分布

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 980#       发表于 2023-11-18 04:16

ML-Bench

让大型语言模型利用开源库(Open-source Libraries)完成机器学习任务

项目主页:https://ml-bench.github.io/

github项目仓库:https://github.com/gersteinlab/ML-bench

数据集下载:https://drive.google.com/drive/folders/1e86FhLjxXK837SgR8a29cztx9UfxPQzS?usp=drive_link

大型语言模型在代码生成基准测试(code generation benchmarks)中表现出了良好的性能，然而，这些基准测试成绩与其实际使用方面之间存在相当大的区别，这主要归就于真实世界的编程含有对预先存在的库(pre-existing libraries)的依赖

这项工作的目的不是评估LLM从头编码的能力，而是提出一种新的评估设置，其中需要LLM使用开源库来完成机器学习任务(machine learning tasks)

因此，本文提出了ML-Bench，一个广泛的基准，旨在评估LLM利用开源库中现有功能的有效性，包含10044个样本，涵盖14个著名机器学习GitHub存储库中的130个任务，在此设置中，给定特定的机器学习任务指令和代码库中随附的自述文件(README)，LLM的任务是生成代码来完成该任务，这需要理解很长的语言代码交错文档，以及复杂的跨文件代码结构，从而为测试引入了新的挑战

值得注意的是，虽然GPT-4比其他LLM表现出了更显著的进步，但它依然只完成了39.73%的任务，留下了巨大的改进空间，研究组通过提出ML-Agent来应对这些挑战，该代理者旨在有效地导航代码库、定位文档、检索代码和生成可执行代码，实验结果表明，基于GPT-4构建的ML-Agent可以带来更进一步的改进

<img src="https://img.saraba1st.com/forum/202311/18/041547xqppzovnjqnc6d7u.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231118-035711.jpg</strong> (157.99 KB, 下载次数: 0)

下载附件

2023-11-18 04:15 上传

ML-Bench通过三个步骤的工作流程从14个机器学习GitHub存储库收集数据：提取自述信息、自动生成指令并形成标准化输出，此外，还引入了ML-Agent来完成所提出的任务，并在ML-Bench上针对当前高度稳健的语言模型进行评估

<img src="https://img.saraba1st.com/forum/202311/18/041605wwykwv34kz5l0n5s.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231118-035952.jpg</strong> (136.07 KB, 下载次数: 0)

下载附件

2023-11-18 04:16 上传

ML-Bench的数据构建，来源包含14个著名的GitHub存储库，聚合了总共10040个样本

<img src="https://img.saraba1st.com/forum/202311/18/041610uhb5zl9tlc6cmfr4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231118-040117.jpg</strong> (229.68 KB, 下载次数: 0)

下载附件

2023-11-18 04:16 上传

ML-Bench的构造工作流程
步骤1：在存储库中找到实现特定任务的readme文件
步骤2：识别与任务相关的基本信息
步骤3：从任务中提取需求参数
步骤4：利用从自述文件中提取的详细信息，制定多种参数组合
步骤5：为每个参数组合创建指令
步骤6：替换自述文件中的代码或脚本，作为ML-Bench的基准答案(ground truth)代码

<img src="https://img.saraba1st.com/forum/202311/18/041619kzjjzmvqyqerrojq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231118-040439.jpg</strong> (68.43 KB, 下载次数: 0)

下载附件

2023-11-18 04:16 上传

跨越三种设置的README文件的平均Token长度和最大Token长度：训练、分布外(OOD)训练和ML-Bench中的训练测试设置

<img src="https://img.saraba1st.com/forum/202311/18/041629eg783gayrki9g7g7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231118-040625.jpg</strong> (57.05 KB, 下载次数: 0)

下载附件

2023-11-18 04:16 上传

ML-Bench的统计信息

<img src="https://img.saraba1st.com/forum/202311/18/041634ua022x8osbzz7z1m.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231118-040718.jpg</strong> (223.73 KB, 下载次数: 0)

下载附件

2023-11-18 04:16 上传

输入输出对、黄金输出和执行结果的说明性集合，并附有精度指标：Pass@1=0、Pass@2=0和Pass@5=1，其中不同颜色表示不同指示的不同的参数

<img src="https://img.saraba1st.com/forum/202311/18/041638vlewwdzewwoz2msd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231118-040953.jpg</strong> (111.05 KB, 下载次数: 0)

下载附件

2023-11-18 04:16 上传

第3节中的Pass@K(%)实验结果，原始自述文件、BM25检索中报告了模型的Pass@1、Pass@2和Pass@5分数

<img src="https://img.saraba1st.com/forum/202311/18/041649ci179kr11kt9ky21.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231118-041132.jpg</strong> (170.23 KB, 下载次数: 0)

下载附件

2023-11-18 04:16 上传

<img src="https://img.saraba1st.com/forum/202311/18/041649koqczcdfbsosqpae.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231118-041145.jpg</strong> (130.31 KB, 下载次数: 0)

下载附件

2023-11-18 04:16 上传

其他指标测试结果

<img src="https://img.saraba1st.com/forum/202311/18/041653fw88llb2rz39lw92.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231118-041201.jpg</strong> (45.7 KB, 下载次数: 0)

下载附件

2023-11-18 04:16 上传

人工标注进行的错误分析，分析了GPT 3.5的240个错误和Claude 2的220个错误

<img src="https://img.saraba1st.com/forum/202311/18/041657p4zjmg9gjjj2ttx0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231118-041313__01.jpg</strong> (226.45 KB, 下载次数: 0)

下载附件

2023-11-18 04:16 上传

ML-Agent的结构，在收到人类指令后遵循四个步骤： 
步骤 1：从指令中提取关键字并在GitHub上进行搜索以识别五个最相关的存储库
步骤2：对检索到的GitHub数据进行排序
步骤3：评估每个检索到的存储库以确定其辅助完成任务的能力
步骤4：编写实现任务所需的脚本或代码

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 981#       发表于 2023-11-21 03:17

AQUATK

音频质量评估工具包(Audio Quality Assessment Toolkit)

github项目主页:https://github.com/Ashvala/AQUA-Tk

神经音频合成(NAS/Neural Audio Synthesis)的最新进展已经超过了标准化评估方法和工具的发展速度，为了弥补这一差距，本文引入了AquaTk，一个开源Python库，专门设计用于简化和标准化NAS系统的评估

AquaTk提供一系列音频质量指标，包括基本PEAQ算法的独特Python实现，并以多种模式运行以满足各种用户需求

<img src="https://img.saraba1st.com/forum/202311/21/031725ehmmzv3haimv3yyv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-031520.jpg</strong> (48.16 KB, 下载次数: 0)

下载附件

2023-11-21 03:17 上传

AquaTK的图形界面

github说明页:

<img src="https://img.saraba1st.com/forum/202311/21/031729ypxjraxssps6ssyr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-031635.jpg</strong> (266.19 KB, 下载次数: 0)

下载附件

2023-11-21 03:17 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 982#       发表于 2023-11-21 04:54

VideoCon

通过对比字幕说明(Contrast Captions)实现稳健的视频语言对齐

github项目主页:https://github.com/Hritikbansal/videocon

尽管经过了大量数据的(预)训练，SOTA视频语言对齐模型依然对于视频字幕说明中语义上合理的对比变化并不稳健，本文通过识别广泛的多种对比错位类型(contrast misalignments)解决这个问题，例如替换实体(replacing entities)、动作(actions)和翻转事件顺序(flipping event order)等，这些对齐模型应当对此具有稳健性

为此，引入了VideoCon，一个由大型语言模型构建的视频语言对齐数据集，可生成合理的对比视频字幕说明(contrast video captions)以及原始视频字幕说明和对比视频字幕说明之间具有的差异解释

通过使用VideoCon对生成视频语言模型进行微调，以评估视频语言蕴涵(entailment)并生成解释(explanations)，基于VideoCon的对齐模型显著优于当前模型，对于人工构造的对比字幕说明(human-generated contrast captions)的视频语言对齐任务(video-language alignment task)，AUC提高了12点

最后，本文模型在时间延长(temporally-extensive)的视频语言任务设置中达成了新的SOTA零样本性能，例如SSv2-Temporal上的文本到视频检索(text-to-video retrieval)和ATP-Hard上的视频问答(video question answering)，此外，模型还在新颖的视频和人工制作的字幕说明和解释上表现出了卓越的性能

<img src="https://img.saraba1st.com/forum/202311/21/045255mexr89zrrc9xrie3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-043710__01.jpg</strong> (223.21 KB, 下载次数: 0)

下载附件

2023-11-21 04:52 上传

VideoCon方法概览，首先，过滤对齐的视频语言对以保留时间上具有挑战性的实例，随后LLM生成对比字幕说明和自然语言解释(NLE/natural language explanations)，以创建VideoCon数据集，之后使用VideoCon在对齐和NLE任务上对视频语言对齐模型进行微调，最后根据基线模型评估微调模型，结果表明，它的性能优于基线，在下游任务上实现了SOTA结果

<img src="https://img.saraba1st.com/forum/202311/21/045302fnpaee7jbv3qv3pm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-044059__01.jpg</strong> (413.69 KB, 下载次数: 0)

下载附件

2023-11-21 04:53 上传

从上到下的VideoCon数据生成过程，具体来说，首先使用基于视频的原始字幕说明以及对比字幕中预期的未对齐类型来提示大型语言模型(PaLM-2)，考虑了七种错位类型，包含物体、动作、属性、计数、空间关系、幻觉和事件顺序翻转，也为每种错位类型提供生成的对比字幕说明和相应的自然语言解释

<img src="https://img.saraba1st.com/forum/202311/21/045308i2cusdun31z9tn6u.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-044422.jpg</strong> (39.94 KB, 下载次数: 0)

下载附件

2023-11-21 04:53 上传

VideoCon数据集的对比字幕说明内的未对齐类型的分布，观察到该数据集对8.8%到24.2%范围内的各种错位具有良好的代表性

<img src="https://img.saraba1st.com/forum/202311/21/045313hatxzx5a19x8thw6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-044616.jpg</strong> (82.66 KB, 下载次数: 0)

下载附件

2023-11-21 04:53 上传

VideoCon中VLE和NLE任务的统计信息

<img src="https://img.saraba1st.com/forum/202311/21/045320gprt81889tr7ffs0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-044710.jpg</strong> (166.72 KB, 下载次数: 0)

下载附件

2023-11-21 04:53 上传

微调的蕴含任务与NLE任务的提示

<img src="https://img.saraba1st.com/forum/202311/21/045348lnmz70hjcm7m8env.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-044926__01.jpg</strong> (355.7 KB, 下载次数: 0)

下载附件

2023-11-21 04:53 上传

本文模型的成功(绿色)和失败(红色)模式的定性示例，在每个示例中，按照从上到下的时间顺序呈现一些视频帧、其相关字幕说明、对比字幕说明、数据集中的基准答案NLE

此外，还展示了模型预测的NLE，标题单元格末尾的小框表示模型是否认为该字幕说明是基于视频的，E和C表示模型预测字幕说明分别与视频相关和矛盾，E-GT和C-GT分别表示预测的NLE与基准答案(GT)NLE相矛盾

<img src="https://img.saraba1st.com/forum/202311/21/045358v1htvdp9td1yx1kf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-044809.jpg</strong> (111.49 KB, 下载次数: 0)

下载附件

2023-11-21 04:53 上传

<img src="https://img.saraba1st.com/forum/202311/21/045358cmif223kihmmrhkd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-044821.jpg</strong> (113.31 KB, 下载次数: 0)

下载附件

2023-11-21 04:53 上传

<img src="https://img.saraba1st.com/forum/202311/21/045358uzahmvzqzdajzdcq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-044840.jpg</strong> (96.38 KB, 下载次数: 0)

下载附件

2023-11-21 04:53 上传

<img src="https://img.saraba1st.com/forum/202311/21/045358d1bdb2o0jvj2d25j.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-044852.jpg</strong> (103.79 KB, 下载次数: 0)

下载附件

2023-11-21 04:53 上传

相关评估指标与结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 983#       发表于 2023-11-21 05:44

 本帖最后由 Machinery 于 2023-11-21 05:45 编辑 

Video-LLaVA

通过投影前对齐(Alignment Before Projection)学习联合视觉表征(United Visual Representation)

github项目主页:https://github.com/PKU-YuanGroup/Video-LLaVA

大型视觉语言模型(LVLM/Large Vision-Language Model)增强了视觉语言理解中多种下游任务的性能，其中大多数现有方法将图像和视频编码到分离的特征空间中，然后将其作为大型语言模型的输入，然而，由于图像和视频缺乏统一的分词化(tokenization)，导致投影前的未对齐(misalignment)，大型语言模型(LLM)从一些贫弱的投影层中学习多模态交互将变得具有挑战性

在这项工作中，为了将视觉表征统一到语言特征空间中，推进基础LLM走向统一的LVLM，建立了一个简单但强大的LVLM基线，名为Video-LLaVA，可以从图像和视频的混合数据集中学习，相互增强

Video-LLaVA在跨越5个图像问答数据集和4个图像基准工具包的9个图像基准测试中实现了卓越的性能，此外，Video-LLaVA在MSRVTT、MSVD、TGIF和ActivityNet上的性能也分别优于Video-ChatGPT5.8%、9.9%、18.6%和10.1%，大量实验表明Video-LLaVA在统一的视觉表征中使图像和视频互惠互利，其性能优于专门为图像或视频设计的模型

<img src="https://img.saraba1st.com/forum/202311/21/054349e41o7hfzwfvfw936.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-051841.jpg</strong> (147.08 KB, 下载次数: 0)

下载附件

2023-11-21 05:43 上传

对比不同的LVLM范式，Video-LLaVA通过在投影前对齐图像和视频，使LLM能够从统一的视觉表征中学习，并赋予LLM同时理解图像和视频的能力

<img src="https://img.saraba1st.com/forum/202311/21/054354yz7g87obe7qtpct3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-052906.jpg</strong> (104.06 KB, 下载次数: 0)

下载附件

2023-11-21 05:43 上传

不同大型视觉语言模型之间的对比，对于将LLM作为调度器的那些方法，它们不需要预对齐和联合训练

<img src="https://img.saraba1st.com/forum/202311/21/054359rvb5ayha6h525rra.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-053032.jpg</strong> (668.95 KB, 下载次数: 0)

下载附件

2023-11-21 05:43 上传

训练框架和性能
(a)Video-LLaVA框架演示了一个根据输入指令生成相应响应的数据流
(b)Video-LLaVA在跨越图像和视频的15个数据集上实现了卓越的性能

<img src="https://img.saraba1st.com/forum/202311/21/054403wv2ddhghffodj8mh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-053219.jpg</strong> (85.09 KB, 下载次数: 0)

下载附件

2023-11-21 05:44 上传

用于训练Video-LLaVA的数据组合，第一阶段的数据集由单轮对话组成，侧重于简洁的视觉描述，第二阶段，数据集包含多轮对话，强调复杂的视觉推理能力

<img src="https://img.saraba1st.com/forum/202311/21/054407vgfo9g68nnggnnx5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-053318__01.jpg</strong> (249.06 KB, 下载次数: 0)

下载附件

2023-11-21 05:44 上传

不同LVLM在图像理解基准上的对比，Res.表示输入图像的分辨率，由于页面限制，基准名称被缩写

VQA-v2;GQA;VisWiz;SQAI : ScienceQA-IMG;VQAT TextVQA;POPE;MMB: MMBench;LLaVAW: LLaVA-Bench(In-the-Wild);MM-Vet.*表明训练数据存在一些重叠

<img src="https://img.saraba1st.com/forum/202311/21/054413j5w2dvb6w6ksml5m.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-053650.jpg</strong> (82.34 KB, 下载次数: 0)

下载附件

2023-11-21 05:44 上传

不同LVLM在视频推理基准上的对比，使用ChatGPT-Assistant来评估Video-ChatGPT的性能，ChatGPT的版本是“gpt-3.5-turbo”

<img src="https://img.saraba1st.com/forum/202311/21/054418xnttkrgtlg38v0yk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-053658.jpg</strong> (323.2 KB, 下载次数: 0)

下载附件

2023-11-21 05:44 上传

Video-LLaVA多模态理解能力的示例，展示了模型根据给定的指令输入生成相应响应的能力:
(a)Video-LLaVA在图像理解和图像推理方面的样本
(b)视频理解方面中的Video-LLaVA样本
(c)联合视觉理解中的Video-LLaVA样本

<img src="https://img.saraba1st.com/forum/202311/21/054432i8uj4ejbs4etwre8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-054019.jpg</strong> (96.62 KB, 下载次数: 0)

下载附件

2023-11-21 05:44 上传

<img src="https://img.saraba1st.com/forum/202311/21/054432ctk8b2gyugky282y.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-054238.jpg</strong> (79.18 KB, 下载次数: 0)

下载附件

2023-11-21 05:44 上传

<img src="https://img.saraba1st.com/forum/202311/21/054432tdshoxronzhnswmo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-054249.jpg</strong> (88.69 KB, 下载次数: 0)

下载附件

2023-11-21 05:44 上传

<img src="https://img.saraba1st.com/forum/202311/21/054432nb5a8az58xqbl8xl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-054258.jpg</strong> (114.24 KB, 下载次数: 0)

下载附件

2023-11-21 05:44 上传

消融实验的结果
“United”是指统一的视觉表征，“Separated”是指分离的视觉表征

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 984#       发表于 2023-11-21 21:01

FastBERT

指数级加快语言建模速度

github项目主页:https://github.com/pbelcak/FastBERT

语言模型实际上只需要使用其神经元的指数的一部分来进行单独推理，作为证明，本文提出了FastBERT，一种BERT变体，在推理过程中使用了0.3%的神经元，同时性能与类似的BERT模型相当

FastBERT仅选择性地使用4095个神经元中的12个进行每层推理(each layer inference)，这是通过用快速前馈网络(FFFs/fast feedforward networks)替换前馈网络(FFNs/feedforward networks)来实现的

虽然目前还没有真正有效的实现来释放条件神经元运算(conditional neural execution)的完全加速潜力，但本文提供的高层级CPU代码比优化的基线前馈实现相比达到了78倍的加速，而PyTorch实现比同等的批量前馈推理实现了40倍的加速，同时发布了训练代码、基准测试设置和模型权重

<img src="https://img.saraba1st.com/forum/202311/21/210121t1za96x07lun9994.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-205630.jpg</strong> (277.36 KB, 下载次数: 0)

下载附件

2023-11-21 21:01 上传

 各种语言模型在GLUE-dev测试集的结果

NT表示可用于训练的神经元数量，NI/NT表示用于单次推理的神经元比例，“Avg”表示该栏左侧所有任务结果的平均分

<img src="https://img.saraba1st.com/forum/202311/21/210125szknenxussxnfee2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231121-210017.jpg</strong> (69.05 KB, 下载次数: 0)

下载附件

2023-11-21 21:01 上传

推理加速评估结果，重点强调最佳的“公平对比”表现

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 985#       发表于 2023-11-22 07:53

Orca 2

教授小型语言模型如何推理

Orca 2-7b权重:https://huggingface.co/microsoft/Orca-2-7b

Orca 2-13b权重:https://huggingface.co/microsoft/Orca-2-13b

Orca 1从丰富的信号，例如解释轨迹(explanation traces)中学习，使其能够在BigBench Hard和AGIEval等基准测试中超越传统的指令调整模型，在Orca 2中，继续探索了改进的训练信号如何增强小型语言模型(LM)的推理能力，训练小型LM的研究通常依赖于模仿学习来复制能力更强的模型的输出，研究组认为，过度强调模仿可能会限制较小模型的潜力

通过试图教导小型LM针对不同的任务采用不同的解决策略，这些策略可能与较大模型使用的潜在策略不同，例如，虽然较大的模型可能可以为复杂任务直接提供答案，但较小的模型可能不具有相同的容量，在Orca 2中，教授了模型各种推理技术(逐步推理/step-by-step,回忆后生成/recall then generate,回忆-推理-生成/recall-reason-generate,直接回答/direct answer等)，其中最重要的目标是帮助模型学习确定每项任务最有效的解决策略

通过使用一套全面的15个不同基准(对应于大约100个任务和超过36000个独特提示)评估了Orca 2，在零样本设置下测试高级推理能力的复杂任务上进行的评估，结果表明Orca 2显著超越了类似尺寸的模型，并达到了与5-10倍大的模型相似或更好的性能水平

<img src="https://img.saraba1st.com/forum/202311/22/075246dxhajcwih82xo8bq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231122-073408.jpg</strong> (61.17 KB, 下载次数: 0)

下载附件

2023-11-22 07:52 上传

在各种基准(零样本设置)上对比了Orca 2(7B和13B)与LLaMA-2-Chat(13B和70B)和WizardLM(13B和70B)的结果，范围涵盖语言理解、常识推理、多步推理，解决数学问题等，Orca 2模型匹配或超越所有其他模型，包括比其大5-10倍的模型，请注意，所有型号均使用相应尺寸的相同LLaMA-2基础模型

<img src="https://img.saraba1st.com/forum/202311/22/075252o1xznnxn3nza8ono.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231122-073711.jpg</strong> (407.46 KB, 下载次数: 0)

下载附件

2023-11-22 07:52 上传

Orca 2、其基本模型LLaMA-2、LLaMA-2-Chat和ChatGPT(GPT-3.5-Turbo)对推理问题响应的示例，分别使replicate.com/meta/llama-2-13b和chat.lmsys.org生成LLaMA-2和LLaMA-2-Chat模型响应，LLaMA和Orca 2模型调用使用temperature=0和top_p=1作为参数，ChatGPT的响应是通过chat.openai.com获得的

<img src="https://img.saraba1st.com/forum/202311/22/075257c02yfmmwiimgo0oj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231122-073935.jpg</strong> (470.89 KB, 下载次数: 0)

下载附件

2023-11-22 07:52 上传

来自Flan-CoT Collection的演示示例

<img src="https://img.saraba1st.com/forum/202311/22/075302mbywbm13umphl7wm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231122-074023.jpg</strong> (72.56 KB, 下载次数: 0)

下载附件

2023-11-22 07:53 上传

不同模型在推理基准上的宏观平均性能

<img src="https://img.saraba1st.com/forum/202311/22/075307kdq9aqfqyqqabdap.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231122-074130.jpg</strong> (131.87 KB, 下载次数: 0)

下载附件

2023-11-22 07:53 上传

推理基准上不同模型的零样本性能对比

<img src="https://img.saraba1st.com/forum/202311/22/075313tqq1aqw4s4ezjaj3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231122-074302.jpg</strong> (84.01 KB, 下载次数: 0)

下载附件

2023-11-22 07:53 上传

MMLU、ARC Easy和ARC Challenge上不同模型的零样本性能对比，System Message表示系统消息是“empty”还是“cautious”

<img src="https://img.saraba1st.com/forum/202311/22/075318vo381oemkle1whul.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231122-074453.jpg</strong> (91.68 KB, 下载次数: 0)

下载附件

2023-11-22 07:53 上传

零样本设置下不同模型在文本完成测试集上的性能

<img src="https://img.saraba1st.com/forum/202311/22/075323q2obkuookfuezt91.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231122-074543.jpg</strong> (130.76 KB, 下载次数: 0)

下载附件

2023-11-22 07:53 上传

MT-Bench每轮得分和平均得分

<img src="https://img.saraba1st.com/forum/202311/22/075327fx3sls8ewz0lze50.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231122-074629.jpg</strong> (63.55 KB, 下载次数: 0)

下载附件

2023-11-22 07:53 上传

使用GPT-4作为鉴别器评估的幻觉率在，在三个抽象概括基准上进行的平均性能(越低越好)

<img src="https://img.saraba1st.com/forum/202311/22/075332txe2inht3rxdrv2r.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231122-074744.jpg</strong> (50.34 KB, 下载次数: 0)

下载附件

2023-11-22 07:53 上传

<img src="https://img.saraba1st.com/forum/202311/22/075332pndzm20r0fumlpjr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231122-074752.jpg</strong> (53.21 KB, 下载次数: 0)

下载附件

2023-11-22 07:53 上传

ToxiGen毒性声明分类与中性陈述分类的评估结果，结果是所有13个类别的平均值

<img src="https://img.saraba1st.com/forum/202311/22/075337rwme8iepp5imk5zi.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231122-074927.jpg</strong> (62.35 KB, 下载次数: 0)

下载附件

2023-11-22 07:53 上传

不同模型在TruthfulQA基准上的表现，准确性为模型给定的多项选择问题生成正确答案的次数的百分比

<img src="https://img.saraba1st.com/forum/202311/22/075346k23zkg6k5l236u0k.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231122-075048.jpg</strong> (75.93 KB, 下载次数: 0)

下载附件

2023-11-22 07:53 上传

HHH数据集的评估结

<img src="https://img.saraba1st.com/forum/202311/22/075351j2ob2wuhe2n4enbe.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231122-075116.jpg</strong> (137.07 KB, 下载次数: 0)

下载附件

2023-11-22 07:53 上传

安全性评估结果

<img src="https://img.saraba1st.com/forum/202311/22/075355sn1jl7gykflvdttd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231122-075143.jpg</strong> (232.31 KB, 下载次数: 0)

下载附件

2023-11-22 07:53 上传

其他评估对比成绩

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 986#       发表于 2023-11-22 08:53

SVD/SVD-XT

Stability开源的视频生成模型系列

介绍博客:https://stability.ai/news/stable-video-diffusion-open-ai-video-model

hugface SVD权重:https://huggingface.co/stabilityai/stable-video-diffusion-img2vid

hugface SVD-XT权重:https://huggingface.co/stabilityai/stable-video-diffusion-img2vid-xt

出于研究目的发布了稳定视频扩散(Stable Video Diffusion)，一种图像到视频生成模型：

SVD：该模型经过训练，可以在给定相同大小的上下文帧的情况下生成分辨率为576x1024的14帧视频，使用SD 2.1中的标准图像编码器，但用时间感知去闪烁解码器(temporally-aware deflickering decoder)替换解码器(decoder)

 SVD-XT：与SVD架构相同，但针对25帧视频生成进行了微调，提供了一个streamlit演示脚本/demo/video_sampling.py，以及一个独立的python脚本scripts/sampling/simple_video_sample.py用于两个模型的推理

除了模型之外，还发布了一份技术报告(相关链接:https://stability.ai/research/stable-video-diffusion-scaling-latent-video-diffusion-models-to-large-datasets)

性能对比:

<img src="https://img.saraba1st.com/forum/202311/22/085256iy0nguquvapgb8dx.jpg" referrerpolicy="no-referrer">

<strong>Graph+SVD+v+Competition0.jpg</strong> (36.27 KB, 下载次数: 0)

下载附件

2023-11-22 08:52 上传

论文内容待更新

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 987#       发表于 2023-11-23 22:24

 本帖最后由 Machinery 于 2023-11-23 22:26 编辑 

HierSpeech++

通过分层变分推理(Hierarchical Variational Inference)来缩小语音的语义和声学表征(Semantic and Acoustic Representation)之间的差距进行零样本语音合成(Zero-shot Speech Synthesis)

github项目主页:https://github.com/sh-lee-prml/HierSpeechpp

基于大型语言模型(LLM)的语音合成已广泛应用于零样本语音合成中，然而，它们需要大量数据，并且具有与以前的自回归语音模型相同的局限性，包括推理速度慢和缺乏稳健性

本文提出了HierSpeech++，一种快速、强大的零样本语音合成器，用于文本到语音(TTS/text-to-speech)和声音转换(VC/voice conversion)，验证了分层语音合成框架(hierarchical speech synthesis frameworks)可以显著提高合成语音的稳健性与表现力

此外，在零样本语音合成场景中，也提高了合成语音的自然度和说话人相似度，对于文本到语音，采用了文本到向量框架，该框架根据文本表征和韵律提示(prosody prompts)生成自监督语音表征和F0表征，然后HierSpeech++根据生成的向量、F0和语音提示生成语音

还进一步研究了从16 kHz到48 kHz的高效语音超分辨率框架(high-efficient speech super-resolution framework)，实验结果表明，分层变分自动编码器可以成为强大的零样本语音合成器，还优于基于LLM和基于扩散的模型，此外，还第一个实现了人类水平质量的零样本语音合成

<img src="https://img.saraba1st.com/forum/202311/23/222128fyy00qwyu2i72mr2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-214504__01.jpg</strong> (200.58 KB, 下载次数: 0)

下载附件

2023-11-23 22:21 上传

HierSpeech++的分层语音合成工作流程
(a)对于语音到语义建模，使用MMS，它是从具有1406种语言语音数据的预训练的Wav2Vec 2.0
(b)分层语音合成器根据语义表征和语音提示生成16 kHz波形音频
(c)SpeechSR将16 kHz波形音频上采样至48 kHz
(d)对于TTS，文本转向量系统根据文本序列和韵律提示生成语义表征

<img src="https://img.saraba1st.com/forum/202311/23/222135p7jgddykdkdo9oq0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-214518__01.jpg</strong> (211.47 KB, 下载次数: 0)

下载附件

2023-11-23 22:21 上传

HierSpeech++的分层语音合成器，左为训练，右为推理

<img src="https://img.saraba1st.com/forum/202311/23/222249w4en2lgl2ssf29gv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-214525__01.jpg</strong> (243.46 KB, 下载次数: 0)

下载附件

2023-11-23 22:22 上传

分层语音合成器的架构细节，为了进行推理，可以根据语义表征、F0和语音提示生成波形，从源语音中提取语义表征和F0进行语音转换，并且可以通过TTV用于文本转语音生成

<img src="https://img.saraba1st.com/forum/202311/23/222254fsice1lsser4pwiz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-214530__01.jpg</strong> (51.36 KB, 下载次数: 0)

下载附件

2023-11-23 22:22 上传

文本到向量

<img src="https://img.saraba1st.com/forum/202311/23/222302uyobcycd5wd6t605.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-214530__02.jpg</strong> (75.69 KB, 下载次数: 0)

下载附件

2023-11-23 22:23 上传

语音超分辨率

<img src="https://img.saraba1st.com/forum/202311/23/222307k38d2d8jt3z2mxda.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-214535__01.jpg</strong> (141.17 KB, 下载次数: 0)

下载附件

2023-11-23 22:23 上传

语音转换和文本转语音的推理场景

<img src="https://img.saraba1st.com/forum/202311/23/222322brqo1qozqc12cac1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-214540__01.jpg</strong> (39.06 KB, 下载次数: 0)

下载附件

2023-11-23 22:23 上传

风格提示复制

<img src="https://img.saraba1st.com/forum/202311/23/222326nnsxddinngh5kh3i.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-214544__01.jpg</strong> (69.82 KB, 下载次数: 0)

下载附件

2023-11-23 22:23 上传

训练数据集，利用公共可用的语音数据集来训练模型，对于TTV，仅使用LibriTTS数据集

<img src="https://img.saraba1st.com/forum/202311/23/222333jko8rl92fsxapkmb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-214558__01.jpg</strong> (109.22 KB, 下载次数: 0)

下载附件

2023-11-23 22:23 上传

消融实验的重建结果，LT-460表示LibriTTS train-clean-100和360子集，LT-960还使用LT-460的train-other-500子集，ALL表示模型使用 5.1 节中的所有数据集进行训练

<img src="https://img.saraba1st.com/forum/202311/23/222339tx1vfc7od2ahzrdz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-214558__02.jpg</strong> (105.29 KB, 下载次数: 0)

下载附件

2023-11-23 22:23 上传

消融实验的重合成结果

<img src="https://img.saraba1st.com/forum/202311/23/222345a247b2227ha99ap7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-214558__03.jpg</strong> (98.27 KB, 下载次数: 0)

下载附件

2023-11-23 22:23 上传

消融实验的语音转换结果，Params.表示模型参数的数量

<img src="https://img.saraba1st.com/forum/202311/23/222355xbi952fnmffwiad9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-214606__01.jpg</strong> (153.93 KB, 下载次数: 0)

下载附件

2023-11-23 22:23 上传

VCTK数据集中未见的说话者的零样本VC结果，DiffVC♠表示来自使用LibriTTS训练的官方实现预训练模型，YourTTS♣表示来自官方实现预训练模型，但使用LibriTTS、VCTK等进行训练，因此YourTTS的结果不是零样本VC结果

<img src="https://img.saraba1st.com/forum/202311/23/222401r636dw3zcpihcdwo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-214610__01.jpg</strong> (126.99 KB, 下载次数: 0)

下载附件

2023-11-23 22:24 上传

Temperature参数搜索，对于TTS，有两个可控Temperature，TTV的Tttv和分层语音合成器的Th，使用经过LT-960训练的HierSpeech++进行此实验并固定随机种子，发现低Temperature可以提高合成语音在CER和WER的稳健性，但是，如果您希望生成多样化且富有表现力的语音，则可以选择高Temperature，基准答案(ground-truth)的CER和WER分别为2.31和4.13，UTMOS以标准差表示

<img src="https://img.saraba1st.com/forum/202311/23/222407vkpie3uu4qrqfp3v.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-214614__01.jpg</strong> (132.65 KB, 下载次数: 0)

下载附件

2023-11-23 22:24 上传

零样本TTS结果，对LibriTTS的测试干净子集中未见的扬声器发出噪音提示，合成了子集的所有句子(4837个样本)，对于HierSpeech++，仅使用LibriTTS train-960中的文本序列

<img src="https://img.saraba1st.com/forum/202311/23/222411by1yasrrsyidt61z.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-214614__02.jpg</strong> (132.55 KB, 下载次数: 0)

下载附件

2023-11-23 22:24 上传

零样本TTS结果，在来自LibriTTS的其他测试子集的未见扬声器上出现了非常嘈杂的提示，综合了测试其他子集的所有句子(5120个样本)

<img src="https://img.saraba1st.com/forum/202311/23/222426uci8hpepil7ddizh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-214619__01.jpg</strong> (58.52 KB, 下载次数: 0)

下载附件

2023-11-23 22:24 上传

不同长度语音提示的结果，利用LibriTTS的干净测试子集(1002个样本)中所有超过10秒的句子，SPR表示风格提示复制，通过将一个简短的提示复制五次以实现稳健的风格转移，由于对语音进行随机切片，没有考虑语音/非语音部分，因此1s提示的结果低于其他提示，UTMOS以标准差表示

<img src="https://img.saraba1st.com/forum/202311/23/222430s018i0rake003bwi.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-214629__01.jpg</strong> (183.79 KB, 下载次数: 0)

下载附件

2023-11-23 22:24 上传

使用AudioSR和SpeechSR(our)获得的基准答案和语音超分辨率结果的频谱图

<img src="https://img.saraba1st.com/forum/202311/23/222436yjj82n8k2ug6jdik.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-214634__01.jpg</strong> (69.43 KB, 下载次数: 0)

下载附件

2023-11-23 22:24 上传

VCTK数据集上的语音超分辨率结果

<img src="https://img.saraba1st.com/forum/202311/23/222440fxx46g98fgcp8rf8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-214634__02.jpg</strong> (52.41 KB, 下载次数: 0)

下载附件

2023-11-23 22:24 上传

SpeechSR的ABX偏好测试

<img src="https://img.saraba1st.com/forum/202311/23/222444zok42ar24aak91ix.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-214634__03.jpg</strong> (62.21 KB, 下载次数: 0)

下载附件

2023-11-23 22:24 上传

与VALL-E、NaturalSpeech2和StyleTTS 2的对比，因为只比较了NaturalSpeech 2和StyleTTS 2演示页面中的四个样本，所以这个实验仅供参考

<img src="https://img.saraba1st.com/forum/202311/23/222448qnqfn77nn8yw4hf3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-214639__01.jpg</strong> (121.38 KB, 下载次数: 0)

下载附件

2023-11-23 22:24 上传

带噪声抑制的语音提示结果，HierSpeech++♠表示Hierspeech++语音合成后的级联去噪结果，仅利用去噪音频作为风格编码器的语音提示来提取去噪风格表征

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 988#       发表于 2023-11-24 00:05

 本帖最后由 Machinery 于 2023-11-24 00:06 编辑 

PhysGaussian

用于生成动态(Generative Dynamics)的物理学集成的3D高斯(Physics-Integrated 3D Gaussians)

项目主页:https://xpandora.github.io/PhysGaussian/

github项目代码仓库:https://github.com/XPandora/PhysGaussian

PhysGaussian，一种新方法，可将基于物理学的牛顿动力学无缝集成到3D高斯中，以实现高质量的新颖运动合成，方法采用定制的质点方法(MPM/custom Material Point Method)，通过具有物理意义的运动形变(kinematic deformation)和机械应力属性(mechanical stress attributes)丰富3D高斯核(3D Gaussian kernels)，所有这些都符合连续介质力学原理(continuum mechanics principles)

方法的一个决定性特征是物理模拟和视觉渲染之间的无缝集成：两个组件都使用相同的3D高斯核作为其离散表征，这消除了三角形/四面体网格(triangle/tetrahedron meshing)、行进立方体(marching cubes)、“笼式网格(cage meshes)”或任何其他几何嵌入的必要性，突出了“所见即所模拟/what you see is what you simulate(WS2)”的原则

本方法在各种材料(包括弹性实体、金属、非牛顿流体和粒状材料)中展示了卓越的多功能性，展示了其通过新颖的观点和运动创建多样化视觉内容的强大能力

<img src="https://img.saraba1st.com/forum/202311/24/000402nwzkqrwqaawzomi1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-234319__01.jpg</strong> (507.92 KB, 下载次数: 0)

下载附件

2023-11-24 00:04 上传

PhysGaussian是一个统一的模拟渲染工作流程，其中3D高斯可以通过新颖的运动和视图无缝模拟和渲染

<img src="https://img.saraba1st.com/forum/202311/24/000428xh404m5ehjl4fyuf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-234327__01.jpg</strong> (369.39 KB, 下载次数: 0)

下载附件

2023-11-24 00:04 上传

方法概览图，PhysGaussian是一个统一的模拟渲染工作流程，它结合了3D高斯溅射(3D Gaussian splatting)表征和连续介质力学，可以同时无缝地生成基于物理的动态运动和照片级真实感渲染

<img src="https://img.saraba1st.com/forum/202311/24/000434euccaymu0ajwizyw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-234350__01.jpg</strong> (423 KB, 下载次数: 0)

下载附件

2023-11-24 00:04 上传

材料的多功能性，在各种示例中展示了本方法的卓越多功能性：狐狸/弹性实体、飞机/金属、吐司/断裂、废墟/颗粒材料、果酱/粘塑性材料和沙发套件/碰撞

<img src="https://img.saraba1st.com/forum/202311/24/000439gzy6qz5kurrvl36b.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-234359__01.jpg</strong> (141.04 KB, 下载次数: 0)

下载附件

2023-11-24 00:04 上传

对比，对于每个基准案例，选择了一个测试视图并可视化所有对比，放大了一些区域，以强调本方法在变形后保持高保真渲染质量的能力，同时使用黑色背景来避免背景的干扰

<img src="https://img.saraba1st.com/forum/202311/24/000444gi9zfw19aq27oiao.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-234359__02.jpg</strong> (30.95 KB, 下载次数: 0)

下载附件

2023-11-24 00:04 上传

消融实验，不可扩展的高斯可能会在形变过程中导致严重的视觉伪影，虽然直接渲染形变高斯核已经可以获得良好的结果，但球谐函数(spherical harmonics)的额外旋转可以提高渲染质量

<img src="https://img.saraba1st.com/forum/202311/24/000448trvjsn3siij4y6ia.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-234410__01.jpg</strong> (87.27 KB, 下载次数: 0)

下载附件

2023-11-24 00:04 上传

合成了格栅(lattice)形变基准数据集以与基线进行对比并进行消融实验验证设计选择，报告了PSNR分数(越高越好)，本方法在所有情况下都优于其他方法

<img src="https://img.saraba1st.com/forum/202311/24/000451pez3cebssxp5bpeg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-234410__02.jpg</strong> (62.7 KB, 下载次数: 0)

下载附件

2023-11-24 00:04 上传

内部填充(Internal filling)还可实现更真实的模拟结果，本方法还支持通过材料参数灵活控制，其中杨氏模量(Young’s modulus)E越大，刚度越高，而泊松比ν(poission ratio ν)越大，体积保持越好

<img src="https://img.saraba1st.com/forum/202311/24/000456hoehmqe2q2eo9fdv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-234410__03.jpg</strong> (29.37 KB, 下载次数: 0)

下载附件

2023-11-24 00:04 上传

与基于几何的编辑方法相比，基于物理的方法能够捕获体积行为，从而产生更真实的动态

<img src="https://img.saraba1st.com/forum/202311/24/000637fzdtxzfc22dakzcf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231123-234410__04.jpg</strong> (46.54 KB, 下载次数: 0)

下载附件

2023-11-24 00:06 上传

各向异性正则化器(Anisotropy Regularizer)，为高斯核引入了各向异性约束，有效增强了动态条件下基于高斯表征的保真度

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 989#       发表于 2023-11-24 01:22

Concept Sliders

用于扩散模型中精确控制的LoRA适配器

https://sliders.baulab.info/

https://github.com/rohitgandikota/sliders

已经训练的Concept Sliders:https://sliders.baulab.info/weights/xl_sliders/

本文提出了一种创造可解释概念滑块(Concept Sliders)的方法，可以精确控制扩散模型生成图像中的属性，本方法识别与一个概念相对应的低秩参数方向，同时最大限度地减少对其他属性的干扰，滑块是使用一小组提示或示例图像创造的，因此，可以为文本或视觉概念创建滑块方向

概念滑块是即插即用的，它们可以有效组合并连续调制(continuously modulated)，从而能够精确控制图像生成，在定量实验中，与以前的编辑技术相比，滑块表现出更强的针对性编辑和更低的干扰

展示了天气、年龄、风格和表达的滑块，以及滑块组合，展示了滑块如何从StyleGAN传输潜变量，以直观地编辑文本描述困难的视觉概念。同时还发现，本方法可以帮助解决Stable Diffusion XL中持续存在的质量问题，例如修复对象变形和扭曲的手
————
如何精确控制扩散模型中的概念？

 艺术家花费大量时间制作提示并寻找适合的seed，以使用文本到图像模型生成所需的图像，然而，当他们需要对生成图像中的属性强度(如眼睛大小或光照)进行更细致、更细粒度的控制时，修改提示会破坏整体结构，艺术家需要能够保持连贯性的表达控制方法

为了在不改变结构的情况下实现精确编辑，提出了概念滑块，它们是应用在预训练模型之上的即插即用的低秩适配器(low rank adaptors)，通过使用简单的文本描述或一小组配对图像，可以训练概念滑块来表示所需属性的方向，在生成时，这些滑块可用于控制图像中概念的强度，从而实现细微的调整

<img src="https://img.saraba1st.com/forum/202311/24/011817thy7i7wu2hie9uky.jpg" referrerpolicy="no-referrer">

<strong>19804e49-e8fa-4845-97bc-1ba6aef5471c.jpg</strong> (127.85 KB, 下载次数: 0)

下载附件

2023-11-24 01:18 上传

概念滑块可以在文本提示、图像对或 StyleGAN 样式空间神经元上进行训练，以识别扩散模型中的目标概念方向，从而实现精确的属性控制
————
为什么需要扩散模型中的概念控制？

在图像生成和编辑过程中精确调节语义概念的能力为利用文本到图像扩散模型的艺术家开启了创意表达的新领域。 正如艺术界最近的讨论所证明的那样，概念控制的局限性阻碍了创作者通过这些生成技术充分体现其愿景的能力，也有人认为，这些模型会生成模糊、扭曲的图像

修改提示往往会极大地改变图像结构，从而很难根据艺术偏好进行微调，例如，艺术家可能会花费数小时精心制作提示来生成引人注目的场景，但缺乏软调整较轻的概念(例如对象的精确年龄或风暴的氛围)来实现其创作目标的能力，对文本和视觉属性的更直观、更细粒度的控制将使艺术家能够调整生成以进行细微的改进，相比之下，概念滑块通过识别与特定概念相关的可解释的潜在方向，可以对视觉属性进行细致的、连续的编辑，通过简单地调整滑块，艺术家可以对生成过程进行更细粒度的控制，并可以更好地塑造输出以符合他们的艺术意图
————
如何控制模型中的概念？

提出了两种类型的训练，单独使用文本提示与使用图像对，对于难以用文本描述的概念或模型无法理解的概念，建议使用图像对训练，首先讨论文本概念滑块的训练
————
文本概念滑块

这个想法很简单但功能强大：预训练模型 Pθ*(x)具有一些预先存在的概率分布来生成概念t，因此我们的目标是学习模型各层的一些低秩更新，从而形成一个 新模型Pθ(x)根据原始预训练模型，在以t为条件时，通过降低图像中属性c-的概率并提高属性c+的概率来重塑其分布：

<img src="https://img.saraba1st.com/forum/202311/24/011835qmn88cjm9mvcvqrq.png" referrerpolicy="no-referrer">

<strong>prob.png</strong> (46.02 KB, 下载次数: 0)

下载附件

2023-11-24 01:18 上传

这类似于基于能量的组合模型背后的动机，在扩散中，它导致了一种直接了当的简单微调方案，该方案通过减去一个组件并添加一个以目标概念为条件的组件来修改噪声预测模型：

<img src="https://img.saraba1st.com/forum/202311/24/011853whef17j887jez7p8.png" referrerpolicy="no-referrer">

<strong>score.png</strong> (29.14 KB, 下载次数: 0)

下载附件

2023-11-24 01:18 上传

概念滑块使用从原始冻结Stable Diffusion模型获得的条件分数对低秩适配器进行微调，以引导输出从一个属性转向另一个正在编辑的目标概念

查询冻结的预训练模型来预测给定目标提示的噪声，并控制属性提示，然后使用训练时的无分类器引导而不是推理的思想来训练编辑后的模型以相反的方向引导它，同时发现以此目标微调的滑块权重非常有效，生成了一个即插即用的适配器，可以直接控制目标概念的属性

在实践中，注意到这些概念是相互纠缠的，例如，当试图控制一个人的年龄属性时，他们的种族在推理过程中会发生变化，为了避免这种不必要的干扰，建议使用一小组保留提示来寻找方向，而不是单独用一对单词来定义属性，通过使用多个文本组合来定义它，找到一个改变目标属性的方向，同时保持其他要保留的属性不变

<img src="https://img.saraba1st.com/forum/202311/24/011913c3jwc8cp39aw7873.png" referrerpolicy="no-referrer">

<strong>disent-score.png</strong> (39.1 KB, 下载次数: 0)

下载附件

2023-11-24 01:19 上传

为了避免对编辑的不必要干扰并允许精确控制，建议寻找保留一组受保护概念的方向，不是寻找从“年轻人”到“老年人”的方向，而是通过特别提及要保留的一组受保护属性来找到保留种族的方向，例如“亚洲年轻人”到“亚洲老人”

<img src="https://img.saraba1st.com/forum/202311/24/011922yfjdjdfbj7zfy0yt.png" referrerpolicy="no-referrer">

<strong>directions.png</strong> (126.5 KB, 下载次数: 0)

下载附件

2023-11-24 01:19 上传

红色箭头是仅使用“老”和“年轻”提示训练的原始年龄方向，然而，这个方向与种族纠缠在一起，相反，通过使用多个提示构建一个新的解缠结方向(蓝色)，以使新向量在这些方向上保持不变，例如，“亚洲老人”和“亚洲年轻人”，通过在所有种族中都这样做，以消除种族纠缠
————
视觉概念滑块

<img src="https://img.saraba1st.com/forum/202311/24/011933xqruk30hkl9r23u0.png" referrerpolicy="no-referrer">

<strong>image-score.png</strong> (21.24 KB, 下载次数: 0)

下载附件

2023-11-24 01:19 上传

 为了训练无法仅用文本提示描述的概念滑块，提出了基于图像对的训练，其中特别根据梯度差来训练图像，滑块通过学习图像对(xA , xB)之间的对比来捕捉视觉概念，训练过程优化了LORA在正向和负向方向上的应用，对于正向LoRA的应用，必须写εθ+，对于负案例，必须写εθ-，然后最小化以下损失：
————
为什么概念滑块低秩且分开？

向滑块引入低秩约束有两个主要原因，首先，为了提高参数计数和计算的效率，其次，以更好的泛化来精确捕捉编辑方向，分开的公式有助于将编辑与不需要的属性隔离开来，展示了一项消融实验，以更好地理解我们工作的这两个主要组成部分的作用

<img src="https://img.saraba1st.com/forum/202311/24/012032qqihiow0h025gv5w.jpg" referrerpolicy="no-referrer">

<strong>9dafcc1e-d812-4ee3-a5f8-0d9cc8930ad0.jpg</strong> (230.62 KB, 下载次数: 0)

下载附件

2023-11-24 01:20 上传

解开目标有助于避免不必要的属性更改，例如编辑年龄时种族或性别的变化，低秩约束对于实现精确编辑也至关重要
————
用于提高图像质量的滑块

像Stable Diffusion XL这样的大规模生成模型最有趣的方面之一是，尽管它们的图像输出经常会受到扭曲或模糊物体等失真的影响，但模型的参数包含生成高质量输出生成模型的潜在能力，概念滑块可以通过识别修复常见扭曲的低秩参数方向来解锁这些能力，与默认情况下相比，输出质量更高，失真更少

<img src="https://img.saraba1st.com/forum/202311/24/012053v0omrf45f2oo0744.jpg" referrerpolicy="no-referrer">

<strong>54ba20e2-1a04-41c5-a7ca-32686f21a645.jpg</strong> (113.37 KB, 下载次数: 0)

下载附件

2023-11-24 01:20 上传

修复滑块使模型能够生成更真实且不失真的图像，该滑块控制下的参数可帮助模型纠正生成输出中的一些缺陷，例如(A/B)中扭曲的人类和宠物，(B/C/D)中的不自然物体以及(B/C)中模糊的自然图像

<img src="https://img.saraba1st.com/forum/202311/24/012102hgam5zidmgvxlqku.jpg" referrerpolicy="no-referrer">

<strong>c271e402-2e94-41ea-909a-5089ee70d5f7.jpg</strong> (217.09 KB, 下载次数: 0)

下载附件

2023-11-24 01:21 上传

演示了“修复”滑块对细节的效果：它改善了密集排列对象的渲染，拉直了建筑线条，并避免了复杂形状边缘的模糊和扭曲

<img src="https://img.saraba1st.com/forum/202311/24/012112fsvwz9w3z5zem9yh.jpg" referrerpolicy="no-referrer">

<strong>fc0a675f-8f21-422e-a068-4ad18d15db0d.jpg</strong> (102.72 KB, 下载次数: 0)

下载附件

2023-11-24 01:21 上传

演示了一个用于在Stable Diffusion中修复手的滑块，找到了一个方向，让双手变得更加真实，远离“画得不好的手”
————
控制文本概念

研究文本概念滑块； 论文对以前的图像编辑方法和基于文本的提示编辑方法进行了更多的定量分析

<img src="https://img.saraba1st.com/forum/202311/24/012126eszller4srl3qo4d.jpg" referrerpolicy="no-referrer">

<strong>85156a9c-c404-46ba-9057-7910a4f2f9c9.jpg</strong> (190.27 KB, 下载次数: 0)

下载附件

2023-11-24 01:21 上传

通过使用一小组要控制的属性的文本描述，可以训练概念滑块以允许在推理过程中对生成的图像进行细粒度控制，通过缩放滑块的系数，用户可以控制编辑的强度

<img src="https://img.saraba1st.com/forum/202311/24/012141wd6hvmkrrmnmdmwd.jpg" referrerpolicy="no-referrer">

<strong>517280b0-90cb-46cf-afc6-e84d6fa54389.jpg</strong> (173.07 KB, 下载次数: 0)

下载附件

2023-11-24 01:21 上传

展示了如何使用不同的滑块控制图像的多个属性，可以注意到，由于低秩公式，参数权重轻，易于共享和作为插件

<img src="https://img.saraba1st.com/forum/202311/24/012154dlhg315rll1m8g0z.jpg" referrerpolicy="no-referrer">

<strong>17f45ded-e13a-4550-a5c9-2a33072ec107.jpg</strong> (238.34 KB, 下载次数: 0)

下载附件

2023-11-24 01:21 上传

展示了“宜人”、“黑暗”、“热带”和“冬季”的天气滑块，为了令人愉快，注意到模型有时会使天气明亮或添加节日装饰，对于热带地区，它添加了热带植物和树木，最后，在冬天，它增加了雪

<img src="https://img.saraba1st.com/forum/202311/24/012158yjgiwgrjdg6d6gdz.jpg" referrerpolicy="no-referrer">

<strong>0da2362d-42d4-4307-b9ce-846cb76e823f.jpg</strong> (133.19 KB, 下载次数: 0)

下载附件

2023-11-24 01:21 上传

展示了“皮克斯”、“真实细节”、“粘土”和“雕塑”的风格滑块
————
控制视觉概念

可以使用视觉滑块来控制微妙的视觉概念； 论文展示了与定制方法的比较和一些定量评估

<img src="https://img.saraba1st.com/forum/202311/24/012209tdwouj44yx943g2z.jpg" referrerpolicy="no-referrer">

<strong>086a04a8-6ae6-4cb2-9ff7-4486f0ea52c8.jpg</strong> (111.75 KB, 下载次数: 0)

下载附件

2023-11-24 01:22 上传

可以为无法用语言描述的概念创建滑块，这些滑块由艺术家使用6-8对图像创建

StyleGAN潜变量，尤其是stylespace潜变量，可以转移到稳定扩散，从styleGAN收集图像并在这些图像上训练滑块，发现扩散模型可以学习解开的样式空间神经元行为，使艺术家能够控制styleGAN中存在的细微差别属性

<img src="https://img.saraba1st.com/forum/202311/24/012219zqjhq34u54pup3rl.jpg" referrerpolicy="no-referrer">

<strong>d7a191cf-ae05-4467-9607-80bbe983f7e4.jpg</strong> (123.49 KB, 下载次数: 0)

下载附件

2023-11-24 01:22 上传

Stylespace潜变量可以从styleGAN转移到Stable Diffusion XL
————
组合多个滑块

低秩滑块方向的一个关键优势是可组合性，用户可以组合多个滑块进行细致的控制，而不是一次仅限于一个概念，通过下载有趣的滑块集，用户可以同时调整多个旋钮来引导复杂的生成

<img src="https://img.saraba1st.com/forum/202311/24/012233ptwwh8z3w0tbwbmu.jpg" referrerpolicy="no-referrer">

<strong>1cc26662-c197-4a4d-a44e-e5c5de4a33a5.jpg</strong> (411.05 KB, 下载次数: 0)

下载附件

2023-11-24 01:22 上传

展示了混合“熟食”和“精致餐饮”的食物滑块来穿越这个2D概念空间，最有趣的是，该模型如何缩小“精致餐饮”的份量

<img src="https://img.saraba1st.com/forum/202311/24/012238rl7w3pc33h6d7fuh.jpg" referrerpolicy="no-referrer">

<strong>08a8cb4c-ddc7-42bb-a57f-4a1f11011259.jpg</strong> (119.2 KB, 下载次数: 0)

下载附件

2023-11-24 01:22 上传

定性地展示了逐步组合多个滑块直至一次最多50个滑块的效果，通过使用远远超过77个令牌(SDXL当前的上下文限制)来创建这50个滑块，这展示了本方法的强大功能，它允许进行超出仅通过基于提示的方法所能实现的控制

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 990#       发表于 2023-11-24 02:26

MagicDance

通过动作和面部表情转换生成逼真的人类舞蹈视频

项目主页:https://boese0601.github.io/magicdance/

github项目代码仓库:https://github.com/Boese0601/MagicDance

在这项工作中，提出了MagicDance，一种基于扩散的模型，用于在具有挑战性的人类舞蹈视频上进行2D人体运动和面部表情转换

具体来说，研究的目标是生成由新颖的姿态序列驱动的任何目标身份的人类舞蹈视频，同时保持人物不变，为此，提出了一种两阶段训练策略来解耦人类动作和外观(例如面部表情、肤色和着装)，包括外观控制块的预训练和在同一数据集的人类舞蹈姿态上对外观姿态联合控制块的微调

新的设计能够实现强大的外观控制，上身、面部属性甚至背景在时间上保持一致，该模型还可以很好地泛化未见的人类身份和复杂的运动序列，而无需利用图像扩散模型的先验知识对具有不同人类属性的附加数据进行任何微调

此外，所提出的模型易于使用，可以被视为Stable Diffusion的插件模块/扩展，还展示了该模型零样本2D动画生成的能力，不仅能够实现从一个身份到另一个身份的外观转移，而且还允许仅在给定姿态输入的情况下实现类似卡通的风格化，大量实验证明了本方法在TikTok数据集上的卓越性能
————

<img src="https://img.saraba1st.com/forum/202311/24/022252ndjdmwk2gxd8jsg2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-022236.jpg</strong> (132.88 KB, 下载次数: 0)

下载附件

2023-11-24 02:22 上传

提出了MagicDance，一种新颖有效的方法，可以提供逼真的人类视频生成，从而实现生动的运动和面部表情转换，以及一致的真实自然场景的零样本生成，无需任何微调

MagicDance可以精确地生成外观一致的结果，而原始的文本到图像模型(例如Stable Diffusion和ControlNet)很难准确地保持主体的身份信息，此外，提出的模块可以被视为原始文本到图像模型的扩展/插件，而无需修改其预训练的权重
————

<img src="https://img.saraba1st.com/forum/202311/24/022312gjof6l27lfk3l9jn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-022301.jpg</strong> (103.1 KB, 下载次数: 0)

下载附件

2023-11-24 02:23 上传

MagicDance的工作流程总览图，用于通过动作和面部表情转换生成可控的人类舞蹈视频，外观控制模型是整个Stable Diffusion的UNet副本，使用相同的权重进行初始化，UNet在整个训练过程中都处于冻结状态

(A)外观控制预训练期间，训练外观控制模型及其多源自注意力模块(Multi-Source Self-Attention Module)
(B)外观姿态解耦控制期间，联合微调权重从A初始化的外观控制模型和姿势Controlnet，在这些步骤之后，冻结所有先前训练的模块并微调从AnimateDiff初始化的运动模块
————
1.人体运动和面部表情转换

<img src="https://img.saraba1st.com/forum/202311/24/022333d860z66w58v0wjjg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-022323.jpg</strong> (422.73 KB, 下载次数: 0)

下载附件

2023-11-24 02:23 上传

<img src="https://img.saraba1st.com/forum/202311/24/022354cghezhq2ezsmxqum.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-022344.jpg</strong> (250.57 KB, 下载次数: 0)

下载附件

2023-11-24 02:23 上传

人体运动和面部表情转换的可视化，MagicDance能够在多种姿势骨架和人脸landmark输入的情况下生成生动逼真的动作和表情，同时准确地保持来自输入的参考图像的身份信息

<img src="https://img.saraba1st.com/forum/202311/24/022424xwtnx6zkmfv93v6o.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-022400__01.jpg</strong> (216 KB, 下载次数: 0)

下载附件

2023-11-24 02:24 上传

视频结果(项目主页动图)
————
2.零样本动画化

<img src="https://img.saraba1st.com/forum/202311/24/022501xkvbiavk6z6vrvyu.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-022430.jpg</strong> (451.14 KB, 下载次数: 0)

下载附件

2023-11-24 02:25 上传

<img src="https://img.saraba1st.com/forum/202311/24/022506rz4gziu4imllk8ai.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-022438.jpg</strong> (152.07 KB, 下载次数: 0)

下载附件

2023-11-24 02:25 上传

零样本2D动画生成的可视化，MagicDance在接受真人舞蹈视频训练后，无需进一步微调，就可以从卡通风格的图像中提供精确身份信息的生成

<img src="https://img.saraba1st.com/forum/202311/24/022512sthuucyc75pp5c5i.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-022450.jpg</strong> (205.76 KB, 下载次数: 0)

下载附件

2023-11-24 02:25 上传

视频结果(项目主页动图)
————
与近期作品的定性对比

<img src="https://img.saraba1st.com/forum/202311/24/022543ch8bjy7v8b8j8vbr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-022518.jpg</strong> (195.81 KB, 下载次数: 0)

下载附件

2023-11-24 02:25 上传

TPS、Disco和MagicDance之间的人类视频生成定性对比，以前的方法显然存在面部表情和人体姿势身份不一致的问题

<img src="https://img.saraba1st.com/forum/202311/24/022549n4vz2j4d2rv77hm7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-022526.jpg</strong> (184.07 KB, 下载次数: 0)

下载附件

2023-11-24 02:25 上传

视频对比
————
与近期作品的定量对比

<img src="https://img.saraba1st.com/forum/202311/24/022634t07o2jej09o08z4d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-022625.jpg</strong> (94.47 KB, 下载次数: 0)

下载附件

2023-11-24 02:26 上传

MagicDance与最近的SOTA方法DreamPose和Disco的定量对比，↓表示越低越好，反之亦然，带*的方法直接使用目标图像作为输入，与OpenPose相比包含更多信息，†表示Disco在其他数据集上的预训练多于MagicDance，后者仅使用TikTok数据集中的335个视频序列进行预训练和微调，Face-Cos表示生成图像和基准真实图像之间面部区域的余弦相似度

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 991#       发表于 2023-11-24 03:00

GAIA

通用人工智能助手的基准测试

hugface排行榜:https://huggingface.co/gaia-benchmark

hugface数据集:https://huggingface.co/gaia-benchmark

GAIA，一个通用人工智能助理的基准测试，如果AI能够解决这个基准测试集，将代表人工智能研究的一个里程碑

GAIA提出了需要一系列基本能力的现实世界问题，例如推理、多模态处理、网页浏览和熟练使用一般工具，GAIA问题在概念上对于人类来说很简单，但对于大多数先进的人工智能来说却具有挑战性：研究表明，人类受访者的得分为92%，而对于配备插件的GPT-4的得分仅为15%

这种显著的表现差异与最近LLM在需要专业技能(例如法律或化学)的任务上优于多数人类的趋势形成鲜明对比，GAIA的理念背离了当前人工智能基准测试的趋势，即针对对人类来说更加困难的任务，研究组认为，通用人工智能(AGI)的出现取决于系统在此类问题上表现出与普通人相似的稳健性的能力

使用GAIA方法，设计了466个问题及其答案，同时发布了这些问题的一部分，保留了其中300个问题的答案，以支持进行排行榜排名测试

<img src="https://img.saraba1st.com/forum/202311/24/025933zg6me8qc86q0pzvt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-024611__01.jpg</strong> (442.91 KB, 下载次数: 0)

下载附件

2023-11-24 02:59 上传

GAIA问题示例，完成任务需要推理、多模态处理或工具使用熟练程度等基本能力，基准的答案是明确的，并且按照设计，不可能在训练数据的纯文本中找到答案，有些问题带有额外的证据，例如图像，反映真实的用例并允许更好地控制问题

<img src="https://img.saraba1st.com/forum/202311/24/025942gxk2p2usxq0tccko.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-024755__01.jpg</strong> (274.59 KB, 下载次数: 0)

下载附件

2023-11-24 02:59 上传

为了回答GAIA，GPT4(这里配备了代码解释器)等人工智能助手需要完成几个步骤，可能需要使用工具或读取文件

<img src="https://img.saraba1st.com/forum/202311/24/025956gkzzn2t0t0tn0dnq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-024802__01.jpg</strong> (109.28 KB, 下载次数: 0)

下载附件

2023-11-24 02:59 上传

左：每种能力至少需要几种能力才能解决问题的数量
右：每个点对应一个GAIA问题，在给定位置，点的大小与问题数量成正比，并且仅显示问题数量最多的级别以方便阅读

这两个图表都是基于人类标注者在回答问题时报告的信息，人工智能系统的处理方式可能会有所不同

<img src="https://img.saraba1st.com/forum/202311/24/030003c1cv6dvm6ua317d1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-024809__01.jpg</strong> (125.04 KB, 下载次数: 0)

下载附件

2023-11-24 03:00 上传

每种方法和级别的分数和回答时间，正如正文中所述，GPT4+插件分数应该被视为预言机，因为其插件是根据问题人工手动选择的，而人工分数则是指标注者在验证问题时获得的分数

<img src="https://img.saraba1st.com/forum/202311/24/030009punqz6tfu2yqul2q.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-024815__01.jpg</strong> (64.21 KB, 下载次数: 0)

下载附件

2023-11-24 03:00 上传

多种LLM达到1级时的每种能力分数

“多样化文件类型读取”和“多模态”的非工具模型的非零分是因为任务的解决方式与标注者的方式不同，用于网页浏览的非工具模型的非零分主要是由于正确记忆了完成中间步骤所需的信息

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 992#       发表于 2023-11-24 20:03

Kandinsky Video

文本到视频生成工作流程的高效架构方向

项目主页:https://ai-forever.github.io/kandinsky-video/

github项目主页:https://github.com/ai-forever/KandinskyVideo

多媒体生成方法在人工智能研究中占据着重要的地位，其中文本到图像模型在过去几年中取得了高质量的结果，然而，现在的视频合成方法也在日渐发展，本文提出了一种基于文本到图像扩散模型的两阶段潜在扩散文本到视频生成架构(two-stage latent diffusion text-to-video generation architecture based on the text-to-image diffusion model)

第一阶段涉及关键帧合成以描绘视频的故事情节，而第二阶段则致力于生成插值中间帧以使场景和对象的运动更平滑，比较了几种关键帧生成的时间调节方法，结果表明，在反映视频生成质量方面和人类偏好指标方面，使用时间层上的分离时间块更具有优势

与其他掩码帧插值方法相比，本文插值模型的设计显著降低了计算成本，此外，还评估了基于MoVQ的视频解码方案的不同配置，以提高一致性并获得更高的PSNR、SSIM、MSE与LPIPS分数

最后，将本文方法与现有的解决方案进行了对比，并在总体得分中获得了top-2，在开源解决方案中获得了top-1，CLIPSIM分数0.2976和FVD分数433.054
————

<img src="https://img.saraba1st.com/forum/202311/24/200106s73xje37hs660988.jpeg" referrerpolicy="no-referrer">" src="https://static.saraba1st.com/image/common/none.gif" referrerpolicy="no-referrer">

<strong>title.jpeg</strong> (329.23 KB, 下载次数: 0)

下载附件

2023-11-24 20:01 上传

Kandinsky Video是一种文本到视频生成模型，基于FusionFrames架构，由两个主要阶段组成，关键帧生成和插值，本方法的时间调节方案使之能够生成具有高质量外观、平滑而动态的视频
————
工作流程总览

<img src="https://img.saraba1st.com/forum/202311/24/200119kkk55655xws5h5dt.jpg" referrerpolicy="no-referrer">

<strong>pipeline.jpg</strong> (150.01 KB, 下载次数: 0)

下载附件

2023-11-24 20:01 上传

编码后的文本提示进入带有时间层或块的U-Net关键帧生成模型，然后将采样的潜在关键帧发送到潜在插值模型，以预测两个关键帧之间的三个插值帧，使用时间MoVQ-GAN解码器来获得最终的视频结果
————
通过时间调节生成关键帧

<img src="https://img.saraba1st.com/forum/202311/24/200132edd9zw69weagwgze.jpg" referrerpolicy="no-referrer">

<strong>temporal_layers_blocks.jpg</strong> (405.22 KB, 下载次数: 0)

下载附件

2023-11-24 20:01 上传

研究检查了T2I U-Net预训练架构中使用的以下两种时间组件方法

左图:将空间层和时间层混合在一个块中的传统方法
中间:分配分离时间块的方法

所有以灰色表示的层均未在T2V架构中进行过训练，而是使用T2I模型的权重进行初始化，所有层左上角的NA和N分别对应于有激活和无激活的预归一化层的存在

对于不同类型的块，实现了不同类型的时间注意力和时间卷积层(左图)，还实现了不同类型的时间调节，其中之一是当像素在类型的不同时刻(1D层)中仅看到其自身值时的简单调节，在3D层中，像素也可以在不同时刻看到其邻近的值(右图)
————
视频帧插值

<img src="https://img.saraba1st.com/forum/202311/24/200201vtz02i9rhunzhon0.jpg" referrerpolicy="no-referrer">

<strong>interpolation_ours.jpg</strong> (311.29 KB, 下载次数: 0)

下载附件

2023-11-24 20:02 上传

T2I架构的主要变化包括:
(i)输入卷积现在接受三个噪声潜在输入(插值帧)和两个条件潜在输入(关键帧)
(ii)输出卷积预测三个去噪潜变量
(iii)在每个空间卷积之后引入了时间卷积
————
时间调节的结果

<img src="https://img.saraba1st.com/forum/202311/24/200215n4ujv4v4cvpmub8v.jpg" referrerpolicy="no-referrer">

<strong>panda_generations.jpg</strong> (431.31 KB, 下载次数: 0)

下载附件

2023-11-24 20:02 上传

提出了基于分离时间块的时间调节方法，将之与之前作品中常用的三种时间块与时间层进行了比较，并在帧质量、文本对齐和时间一致性方面获得了优势
————
对比结果

<img src="https://img.saraba1st.com/forum/202311/24/200247ctpotmou393q6qpm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-200235.jpg</strong> (149.92 KB, 下载次数: 0)

下载附件

2023-11-24 20:02 上传

————
其他结果

<img src="https://img.saraba1st.com/forum/202311/24/200314ezncegsm9qevqbue.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-200302.jpg</strong> (446.84 KB, 下载次数: 0)

下载附件

2023-11-24 20:03 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 993#       发表于 2023-11-24 21:16

DINOv

视觉上下文提示(Visual In-Context Prompting)

github项目主页:https://github.com/UX-Decoder/DINOv

大型语言模型(LLM)中的上下文提示已成为提高其零样本能力的流行方法，但这种思路在视觉领域的探索较少，现有的视觉提示方法侧重于引用分割(referring segmentation)来分割最相关的对象，无法解决许多通用视觉任务，例如开放集分割和检测

在本文中，为这两项任务引入了一个通用的视觉上下文提示框架，特别是，通过建立在编码器-解码器架构之上，开发了一种多功能提示编码器来支持各种提示，如笔划、框和点，进一步增强了它以将任意数量的参考图像分割作为上下文

广泛的实验探索表明，所提出的视觉上下文提示引发了非凡的引用和通用分割能力以支持引用和检测，为封闭集域内数据集(close-set in-domain datasets)带来了有竞争力的性能，并在许多开放集分割数据集上显示出了有效的结果，通过在COCO和SA-1B上联合训练，模型在COCO上达到57.7 PQ，在ADE20K上达到23.2PQ

<img src="https://img.saraba1st.com/forum/202311/24/211210ebxhpiglm7gbsppe.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-203319__01.jpg</strong> (657.87 KB, 下载次数: 0)

下载附件

2023-11-24 21:12 上传

DINOv支持通用和引用分割，可以将多个或单个对象与用户输入的视觉提示相关联，用户可以输入一个或多个上下文视觉提示(涂鸦、掩码、框等)以提高分割性能

<img src="https://img.saraba1st.com/forum/202311/24/211216ekcgykk76hqhgwjx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-203326__01.jpg</strong> (164.09 KB, 下载次数: 0)

下载附件

2023-11-24 21:12 上传

与相关作品的对比

通用(Generic):分割与用户提示匹配的相同语义概念的所有对象…
参考(Refer):根据用户输入的视觉提示分割特定对象
图像提示(Image prompt)：根据提示裁剪图像区域
(单)视觉提示(single Visual prompt):一个用于分割的图像提示示例
上下文提示(In- context prompt):一个或多个图像提示示例，可以执行单图像和跨图像视觉提示任务，并支持引用和通用分割

<img src="https://img.saraba1st.com/forum/202311/24/211227rngh4i0zr6rud29k.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-203331__01.jpg</strong> (283.38 KB, 下载次数: 0)

下载附件

2023-11-24 21:12 上传

DINOv是一个通用分割框架，可以进行通用分割和参考图像分割，视觉编码器用于提取图像特征，(B)为视觉通用分割损失的图示，在示例中，有6个视觉提示，是从3个类别的6个掩码中采样的，来自同一类实例的视觉提示被平均作为类嵌入，匹配矩阵的每一列都是一个3维one-hot向量，它是实例的one-hot类标签，(C)为视觉参考分割损失的图示，每个视觉提示都被分类为6个实例之一

<img src="https://img.saraba1st.com/forum/202311/24/211235uzhi7khsfll7hdff.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-203338__01.jpg</strong> (184.19 KB, 下载次数: 0)

下载附件

2023-11-24 21:12 上传

通用和引用分割任务的DINOv查询形式

<img src="https://img.saraba1st.com/forum/202311/24/211243mga6sjsuaadwjdd5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-203343__01.jpg</strong> (44.41 KB, 下载次数: 0)

下载附件

2023-11-24 21:12 上传

提示编码器对参考图像的视觉提示进行编码，使用从视觉编码器小特征图到大特征图的三个屏蔽交叉注意力(three masked cross-attention)

<img src="https://img.saraba1st.com/forum/202311/24/211255n6mul6lj3uzrhe5p.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-203353__01.jpg</strong> (259.71 KB, 下载次数: 0)

下载附件

2023-11-24 21:12 上传

一套权重，用于多个数据集上的通用视觉上下文分割，模型在COCO和SA-1B数据集上进行训练

“-”表示模型没有报告的数字或不具备执行特定任务的能力
⋆表示是测试集结果
†表示FC-CLIP采用冻结的CLIP进行开放集(文本)，通过提示带有CLIP视觉特征的FC-CLIP来模拟视觉推广(visual promoting)
#代表FC-CLIP和ODISE依赖于冻结的CLIP和Stable Diffusion知识
Mask DINO是进行对比的基准

<img src="https://img.saraba1st.com/forum/202311/24/211400wxvkgavzoaknxpoy.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-211343.jpg</strong> (62.32 KB, 下载次数: 0)

下载附件

2023-11-24 21:14 上传

OdinW基准上的一套权重，为简单起见，报告了35个数据集的平均AP和中值AP

<img src="https://img.saraba1st.com/forum/202311/24/211448pbykel9l2ttqqorn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-211433.jpg</strong> (151.05 KB, 下载次数: 0)

下载附件

2023-11-24 21:14 上传

零样本视频对象分割，无需使用视频或成对图像数据进行训练，本文方法就能够以零样本的方式进行视频对象分割

<img src="https://img.saraba1st.com/forum/202311/24/211530ci6z016o6ddm15sc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-203416__01.jpg</strong> (55.99 KB, 下载次数: 0)

下载附件

2023-11-24 21:15 上传

使用差异查询来进行上下文引用和通用分割的消融实验，默认情况下，同时使用通用查询和交互式查询，通过一次删除一种类型的查询以降低其有效性

<img src="https://img.saraba1st.com/forum/202311/24/211540izpkppdmypxuinup.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-203416__02.jpg</strong> (45.35 KB, 下载次数: 0)

下载附件

2023-11-24 21:15 上传

在Swin-T模型上使用不同方式对视觉提示进行编码的消融实验，在相同的设置下，通过更改提示编码方法，并使用预先训练的CLIP对图像中的提示对象进行裁剪和编码

<img src="https://img.saraba1st.com/forum/202311/24/211601evvjkkbznd6kjgjb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-203421__01.jpg</strong> (49.3 KB, 下载次数: 0)

下载附件

2023-11-24 21:16 上传

统一任务和数据的有效性的消融实验

<img src="https://img.saraba1st.com/forum/202311/24/211609sve1on1l6bn1enql.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-203416__03.jpg</strong> (70.27 KB, 下载次数: 0)

下载附件

2023-11-24 21:16 上传

训练中图像批大小采样参数的消融实验

<img src="https://img.saraba1st.com/forum/202311/24/211615rq8eigiv85fz8f85.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-203428__01.jpg</strong> (360.12 KB, 下载次数: 0)

下载附件

2023-11-24 21:16 上传

DINOv可以通过给出视觉提示来进行开放集分割

<img src="https://img.saraba1st.com/forum/202311/24/211620n5o8e05yujtekwum.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231124-203431__01.jpg</strong> (75.24 KB, 下载次数: 0)

下载附件

2023-11-24 21:16 上传

不同任务的DINOv查询形式

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 994#       发表于 2023-11-26 01:15

Nanbeige 16B

Nanbeige-16B（南北阁-16B）是南北阁大模型实验室研发的160亿参数规模的大语言模型

github项目主页:https://github.com/Nanbeige/Nanbeige

项目权重:https://huggingface.co/Nanbeige

Nanbeige-16B（南北阁-16B）是南北阁大模型实验室研发的160亿参数规模的大语言模型，采用了2.5T Tokens进行预训练，数据包含大量互联网高质量语料、各类书籍、代码等领域脱敏文本，在各个权威测评数据集上都取得了不错的效果。本次发布包含有 Base、Chat 以及扩展上下文长度的 Base-32k、Chat-32k 版本

Base-32k 版本基于Nanbeige-16B-Base模型，采用YaRN插值方法对位置编码进行修改，并以32k为最大长度进行了20B Tokens的中文、英文、代码语料的全参数增量预训练

Chat 版本和 Chat-32k 版本分别基于Nanbeige-16B-Base模型和Nanbeige-16B-Base-32k模型，经过了大量人类对齐训练，能够更好、更安全地回复用户的问题

github说明页:

<img src="https://img.saraba1st.com/forum/202311/26/011537vddufqzxxyvp07xd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231126-011407.jpg</strong> (573.68 KB, 下载次数: 0)

下载附件

2023-11-26 01:15 上传

<img src="https://img.saraba1st.com/forum/202311/26/011537uqzqk5ykxeascl33.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231126-011421.jpg</strong> (328.09 KB, 下载次数: 0)

下载附件

2023-11-26 01:15 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 995#       发表于 2023-11-27 12:59

SEGIC

解放上下文分割(In-Context Segmentation)的新兴对应关系(Emergent Correspondence)

github项目主页:https://github.com/MengLcool/SEGIC

上下文分割的目标旨在使用一些标记(labeled)的示例图像(称为“上下文示例”)来分割新图像，并探索示例与目标之间的内容相似性，由此构建的模型可以无缝转移推广到新的分割任务上，与传统的流程​​相比，显著降低了标签和训练成本

然而，由于其元学习(meta-learning)的性质，上下文分割比经典分割方法更具有挑战性，要求模型能够学习基于少数样本的分割规则，而不仅仅只是分割

与之前的专案或者非端到端设计工作不同，本文提出了SEGIC，这是一种基于单一视觉基础模型(VFM/vision foundation model)构建的端到端上下文框架，特别是SEGIC能够利用VFM中的新兴对应关系来捕获目标图像和上下文样本之间的密集关联，因此，来自上下文样本的信息随后被提取为三种类型的指令，即几何指令(geometric instructions)、视觉指令(visual instructions)和元指令(meta instructions)，作为最终掩码预测的显式条件

SEGIC是一种简单而有效的方法，可以在单样本分割基准上达到SOTA性能，而且值得注意的是，SEGIC还可以轻松的推广到多种不同的任务上，包括视频对象分割和开放词汇分割

<img src="https://img.saraba1st.com/forum/202311/27/125842yts5e5ws224n182d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231127-123822__01.jpg</strong> (532.61 KB, 下载次数: 0)

下载附件

2023-11-27 12:58 上传

SEGIC的定性结果，其可以根据一些标记好的示例图像来分割目标图像，这被称之为“上下文分割”，SEGIC通过不同类型的上下文样本来统一各种分割任务，包括每个样本用一个掩码标注的样本(单样本分割)、每个样本用几个掩码标注的样本(视频对象分割)以及标注样本的组合(语义分割)

<img src="https://img.saraba1st.com/forum/202311/27/125846yqhm2j2jdkh2w7hw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231127-123843__01.jpg</strong> (296.76 KB, 下载次数: 0)

下载附件

2023-11-27 12:58 上传

架构概览图，SEGIC构建在冻结的视觉基础模型之上，总共由四个阶段组成:1.特征提取，2.关联发现，3.上下文指令提取，4.掩码解码

<img src="https://img.saraba1st.com/forum/202311/27/125850jffoa6z1yqjf4iyb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231127-123854__01.jpg</strong> (377.92 KB, 下载次数: 0)

下载附件

2023-11-27 12:58 上传

几个分割基准测试的主要结果

†表示冻结的图像编码器，‡表示免训练方法并使用SAM，*表示需要额外的微调，#表示图像中的类在推理过程中是已知的，n/a表示模型不具备执行该任务的能力，-表示没有能报告的数字

<img src="https://img.saraba1st.com/forum/202311/27/125855c3chcok6z8bx7dix.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231127-123900__01.jpg</strong> (71.56 KB, 下载次数: 0)

下载附件

2023-11-27 12:58 上传

与单样本COCO-20i的对比，‡表示该模型是在排除COCO的数据集上联合训练的

<img src="https://img.saraba1st.com/forum/202311/27/125900otnqn7afl9syyqaq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231127-123905__01.jpg</strong> (70.14 KB, 下载次数: 0)

下载附件

2023-11-27 12:59 上传

语义对应和分割的关联表现，直接使用密集对应进行零样本PCK

<img src="https://img.saraba1st.com/forum/202311/27/125904c94h6jsqf4eh60t4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231127-123911__01.jpg</strong> (400.93 KB, 下载次数: 0)

下载附件

2023-11-27 12:59 上传

消融实验

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 996#       发表于 2023-11-27 20:53

charting-new-territories

绘制新领域：探索多模态LLM的地理和地理空间能力

https://github.com/jonathan-roberts1/charting-new-territories

多模态大语言模型(MLLM)在广泛的任务中表现出了卓越的能力，但它们在地理和地理空间领域方面的知识和能力仍有待探索，取决于它们对于导航(navigation)、环境研究(environmental research)、城市发展(urban development)和灾难响应(disaster response)以及其他领域的多种任务都具有的潜在益处，进行了一系列实验探索MLLM在这些领域内的各种视觉能力，其中特别关注了前沿模型GPT-4V，并将其性能与开源模型进行对比基准测试

本文使用了由一系列的多种视觉任务组成的小规模地理基准测试来挑战这些模型，包含各种复杂范围内的能力，该分析不仅揭示了这些模型的优点(包括它们超越人类的应用实例)，还揭示了它们的不足之处，从而对它们在地理领域的能力提供了平衡的看法，为了能够对未来模型进行对比和评估，本文的基准测试将公开发布

为了探测MLLM的知识，进行了一系列视觉实验，将每个图像与给定的提示一起传递给MLLM作为定位，正如其响应所强调的那样，发现GPT-4V能够提取和推理此类图像中的细粒度细节，同时GPT-4V在测试国家的基准上也取得了令人鼓舞的准确性，它优于其他强大的MLLM基线

<img src="https://img.saraba1st.com/forum/202311/27/205113lp0hbpyg7hzph4hh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231127-201720__01.jpg</strong> (56.51 KB, 下载次数: 0)

下载附件

2023-11-27 20:51 上传

SATIN子集上的零样本卫星图像分类，对于LLaVA-1.5，报告了5个子集的µ±σ

<img src="https://img.saraba1st.com/forum/202311/27/205125xed0ttedt6ky03y5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231127-201720__02.jpg</strong> (101.5 KB, 下载次数: 0)

下载附件

2023-11-27 20:51 上传

定位:地图→现实世界
平均距离误差是在每个裁剪洲地图的10个点上计算的

<img src="https://img.saraba1st.com/forum/202311/27/205133iv2h6ts22oxxkhon.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231127-201730__01.jpg</strong> (492.72 KB, 下载次数: 0)

下载附件

2023-11-27 20:51 上传

卫星图像变化检测，测试了GPT-4V中的四季图像时间序列中季节变化的能力，在此示例中，模型能够通过获取农作物颜色和雪的存在等次要细节，以正确估计季节

<img src="https://img.saraba1st.com/forum/202311/27/205140rc41224ga1g5z152.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231127-201737__01.jpg</strong> (159.02 KB, 下载次数: 0)

下载附件

2023-11-27 20:51 上传

使用GPT-4V进行分割，定性展示了LoveDA卫星图像的分割和定位能力，边界框适用于城市地区(红色)和道路(绿色)

<img src="https://img.saraba1st.com/forum/202311/27/205146plzz2736lx7z7wch.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231127-201745__01.jpg</strong> (221.06 KB, 下载次数: 0)

下载附件

2023-11-27 20:51 上传

城市地区(红色)、道路(黄色)和水体(蓝色)的边界框

<img src="https://img.saraba1st.com/forum/202311/27/205210pmc140yq9mscm1l4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231127-201745__02.jpg</strong> (201.79 KB, 下载次数: 0)

下载附件

2023-11-27 20:52 上传

计算小物体非常具有挑战性

<img src="https://img.saraba1st.com/forum/202311/27/205259vw0vhthvztqtcvcb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231127-201752__01.jpg</strong> (219.79 KB, 下载次数: 0)

下载附件

2023-11-27 20:52 上传

左方：所有三个识别任务的定量结果
右方：为每个任务选择的示例，表明各个模型的成功和失败(来自OpenStreetMap的地图数据)

<img src="https://img.saraba1st.com/forum/202311/27/205304dl3cbcgi04il4cuh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231127-201759__01.jpg</strong> (194.28 KB, 下载次数: 0)

下载附件

2023-11-27 20:53 上传

定位：地图→现实世界
预测的纬度和经度位置，[左]欧洲(Miller)，[右]非洲(PlateCarree)

<img src="https://img.saraba1st.com/forum/202311/27/205308t8utp8ti3ip1m8fa.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231127-201759__02.jpg</strong> (112.06 KB, 下载次数: 0)

下载附件

2023-11-27 20:53 上传

在常规地图上识别多个状态是很困难的，并且翻转地图后会有非常明显的失败案例

<img src="https://img.saraba1st.com/forum/202311/27/205316tgz8eoz418xhqafa.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231127-201811__01.jpg</strong> (596.89 KB, 下载次数: 0)

下载附件

2023-11-27 20:53 上传

定位：现实世界→地图
使用GPT-4V在覆盖有网格的地图上标注欧洲首都
有两种设置：图像[左]，其中地图网格传递给模型；无图像[右]，仅传递地图的简短描述

<img src="https://img.saraba1st.com/forum/202311/27/205320yu3330os4x4p54o0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231127-201823__01.jpg</strong> (230.66 KB, 下载次数: 0)

下载附件

2023-11-27 20:53 上传

国旗识别
(a)展示了在完整网格用例下用于旗帜识别的结构化输入，以及GPT-4V的响应，其中旗帜下方的国家名称添加到后面并进行颜色编码以指示正确和不正确的识别
(b)描述了不同模型识别旗帜的准确性，以人类平均值作为参考，人类表现数据来自Sporcle，可能无法反映精确的准确性

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 997#       发表于 2023-11-28 05:03

GaussianEditor

快捷且可控的Gaussian Splatting 3D内容编辑

项目主页:https://buaacyw.github.io/gaussian-editor/

github项目代码仓库:https://github.com/buaacyw/GaussianEditor

3D内容编辑在诸如游戏和虚拟现实等许多领域发挥着至关重要的作用，传统的3D编辑方法依赖于网格和点云等表示形式，并且通常无法真实地描绘复杂的场景，另一方面，基于隐式3D表征的方法，例如神经辐射场(NeRF)可以有效渲染复杂场景，但目前处理速度慢且对特定场景区域的控制有限

为了应对这些挑战，本文提出了GaussianEditor，一种基于高斯泼溅(GS/Gaussian Splatting/一种新颖的3D表示形式)的创新且高效的3D编辑算法

GaussianEditor通过提出的高斯语义跟踪(Gaussian semantic tracing)增强了编辑的精度和控制程度，该跟踪在整个训练过程中跟踪需要编辑的目标，此外，还提出了分层高斯泼溅(HGS/Hierarchical Gaussian splatting)，以在二维扩散模型的随机生成指导下实现稳定且精细的结果，还开发了有效的对象移除和集成(object removal and integration)编辑策略，这些对现有方法来说都是具有挑战性的任务

综合实验证明了GaussianEditor卓越的控制能力、效果和快速性能，标志着3D编辑领域的重大进步

<img src="https://img.saraba1st.com/forum/202311/28/050142k4obbbxox2tgmgne.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-035949__01.jpg</strong> (791.46 KB, 下载次数: 0)

下载附件

2023-11-28 05:01 上传

GaussianEditor的结果，本方法可以提供快速、可控且多功能的3D编辑，一次编辑仅需5-10分钟，请注意图中的精确编辑控制，仅修改所需的部分，以图中第一行的“Make the grass on fire”为例，场景中的其他物体(例如长凳和树)则不受影响

<img src="https://img.saraba1st.com/forum/202311/28/050151ell6kuvznujuwukn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-035959__01.jpg</strong> (106.53 KB, 下载次数: 0)

下载附件

2023-11-28 05:01 上传

高斯语义追踪的插图，右图中的红色掩码代表目标高斯的投影，值得注意的是，该预测在整个训练过程中动态变化，确保其在整个训练期间的有效性

<img src="https://img.saraba1st.com/forum/202311/28/050155foac6av29v79to5a.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-035959__02.jpg</strong> (366.62 KB, 下载次数: 0)

下载附件

2023-11-28 05:01 上传

用于对象合并的3D重绘，GaussianEditor能够在场景中的指定位置添加对象，给定2D重绘掩码(mask)和来自单个视图的文本提示，整个过程仅需五分钟

<img src="https://img.saraba1st.com/forum/202311/28/050159qu99gkuu0lym3vug.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-040009__01.jpg</strong> (335.41 KB, 下载次数: 0)

下载附件

2023-11-28 05:01 上传

用于移除物体的3D重绘，通常，基于高斯语义掩码去除目标对象会在目标对象和场景之间的界面处产生伪影，为了解决这个问题，可以使用2D重绘方法生成修复图像，采用平均方误差(MSE/Mean Squared Error)损失进行监督，整个过程仅需两分钟

<img src="https://img.saraba1st.com/forum/202311/28/050205jrfp81zim44qie1r.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-040021__01.jpg</strong> (758.91 KB, 下载次数: 0)

下载附件

2023-11-28 05:02 上传

定性对比，最重要的是要注对编辑区域(人的整个身体)保持控制的程度，与整​​个场景发生变化的Instruct-Nerf2Nerf相比，背景和其他非目标区域基本上不受影响，GaussianEditor-DDS和GaussianEditor-iN2N表示分别用delta去噪分数和Instruct-Nerf2Nerf作为编辑指导

<img src="https://img.saraba1st.com/forum/202311/28/050331eckzh98trmmtmdc9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-040038__01.jpg</strong> (477.65 KB, 下载次数: 0)

下载附件

2023-11-28 05:03 上传

GaussianEditor的广泛应用结果，本方法能够执行多种编辑任务，包括面部和场景编辑，在面部编辑中，使用高斯语义追踪将编辑区域限制在面部，确保其他不需要的区域保持不变，最左边的列显示原始视图，而右边的三列为编辑后的图像

<img src="https://img.saraba1st.com/forum/202311/28/050225fhdcvv0hhn3w6g3k.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-040055__01.jpg</strong> (475.42 KB, 下载次数: 0)

下载附件

2023-11-28 05:02 上传

分层高斯泼溅的消融实验，提示文本为：Make the grass on fire
即使通过提示指定编辑区域，像Instruct-Pix2Pix这样的生成方法也倾向于编辑整个2D图像，如果没有HGS，高斯模型往往会通过在整个场景中扩散和致密来遵循这种整体图像编辑，从而导致图像无法控制的致密和模糊，然而，有了 HGS，这种扩散就能被有效地抑制

<img src="https://img.saraba1st.com/forum/202311/28/050219pn4kn7z708zchk38.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-040103__01.jpg</strong> (38.06 KB, 下载次数: 0)

下载附件

2023-11-28 05:02 上传

定量对比，Gaussian Editor-iN2N在用户研究评估和CLIP定向相似性(CLIP Directional Similarity metrics)指标方面均表现出色

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 998#       发表于 2023-11-28 18:50

ParaDiffusion

使用信息增强(Information-Enriched)的扩散模型进行段落到图像(Paragraph-to-Image)生成

项目主页:https://weijiawu.github.io/ParaDiffusionPage/

github项目主页:https://github.com/weijiawu/ParaDiffusion

文本到图像(T2I/Text-to-image)模型最近经历了急速的发展，在保真度和文本对齐能力方面取得了惊人的性能，然而，对于很长的段落(最多可至512个单词)，这些生成模型仍然难以实现和文本强对齐，并且无法生成描述复杂的场景图像

在本文中，介绍了一种用于段落到图像生成任务的信息增强的扩散模型，称为ParaDiffusion，它深入研究了大型语言模型的广泛语义理解能力到图像生成任务的迁移，具体来说，其核心是使用大型语言模型(例如Llama V2)对长式文本(long-form)进行编码，然后使用LORA进行微调，以对齐生成任务中的文本图像特征空间

为了促进长文本语义对齐的训练，还策划构造了一个高质量的段落图像对数据集，即ParaImage，该数据集包含少量的高质量、精心标注的数据，以及使用视觉语言模型生成的包含长文本描述的大规模合成数据集

实验表明，ParaDiffusion在ViLG-300和ParaPrompts上的表现优于SOTA系列模型(SD XL、DeepFloyd IF等)，在视觉吸引力和文本忠实度方面分别实现了高达15%和45%的人类投票率提升，该代码和数据集将被发布，以促进研究社区对长文本对齐的研究

<img src="https://img.saraba1st.com/forum/202311/28/184838zgg5ylgcyefwpzt5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-181512__01.jpg</strong> (816.98 KB, 下载次数: 0)

下载附件

2023-11-28 18:48 上传

ParaDiffusion中的段落图像对齐示例，凭借LLM强大的语义理解能力，ParaDiffusion能够生成高度美观且复杂的图像，同时很好的与长文本内容对齐

<img src="https://img.saraba1st.com/forum/202311/28/184844m1xgo1mzfrykrmyx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-181632__01.jpg</strong> (278.24 KB, 下载次数: 0)

下载附件

2023-11-28 18:48 上传

本方法的工作流程，ParaDiffusion的训练流程主要包括三个阶段:
1.预训练基于3亿个样本，以获取通用的文本图像知识
2.使用数百万数据同时微调LLM以及进行扩散模型的段落图像对齐
3.使用精选的高质量标注数据(即ParaImage-Small)进行质量调整

<img src="https://img.saraba1st.com/forum/202311/28/184851s8eeycl4l84rchke.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-181639__01.jpg</strong> (640.79 KB, 下载次数: 0)

下载附件

2023-11-28 18:48 上传

所提案的ParaImage数据集的示例:
a.带有合成字幕说明(generative captions)的高质量图像(ParaImage-Big)主要用于第二阶段的段落图像对齐学习
b.带有手动标注长描述的美学图像(ParaImage-Small)主要用于第3阶段的质量调整

<img src="https://img.saraba1st.com/forum/202311/28/184857iodtmu9oii9dfoxl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-181650__01.jpg</strong> (45.98 KB, 下载次数: 0)

下载附件

2023-11-28 18:48 上传

数据统计对比

<img src="https://img.saraba1st.com/forum/202311/28/184904anktoboon96g9k9c.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-181650__02.jpg</strong> (119.91 KB, 下载次数: 0)

下载附件

2023-11-28 18:49 上传

字幕说明长度的分布，所提出的数据集(ParaImage)的文本描述长度远远超过了当前可用的公共数据集的文本描述

<img src="https://img.saraba1st.com/forum/202311/28/184909f1mz0tzxt3m4km0z.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-181650__03.jpg</strong> (85.13 KB, 下载次数: 0)

下载附件

2023-11-28 18:49 上传

不同评估数据集的字幕说明长度分布， ParaPrompts数据集提供了大量的长文本描述

<img src="https://img.saraba1st.com/forum/202311/28/184914jx0oluuuaq5c055a.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-181650__04.jpg</strong> (59.21 KB, 下载次数: 0)

下载附件

2023-11-28 18:49 上传

ParaPrompts概念的分布，其中提示涵盖了人类相关活动中的常见概念

<img src="https://img.saraba1st.com/forum/202311/28/184919btc71aty7rwo373w.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-181659__01.jpg</strong> (139.56 KB, 下载次数: 0)

下载附件

2023-11-28 18:49 上传

使用零样本FID-30K在MS-COCO 256 × 256数据集上的性能对比
‘#Params’指的是Unet的参数

<img src="https://img.saraba1st.com/forum/202311/28/184930ph2bxn15nw5zzhkr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-181659__02.jpg</strong> (76.53 KB, 下载次数: 0)

下载附件

2023-11-28 18:49 上传

ViLG-300的300条提示的用户研究，“Tie”表示四个模型的图像质量相似

<img src="https://img.saraba1st.com/forum/202311/28/184934e039i95nhxz9zo79.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-181659__03.jpg</strong> (71.63 KB, 下载次数: 0)

下载附件

2023-11-28 18:49 上传

ParaPrompts的400个提示的用户研究，当闭源模型的结果不可用或API调用失败时，只选择开源模型进行对比

<img src="https://img.saraba1st.com/forum/202311/28/184940h1o516yg7j5licwt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-181709__01.jpg</strong> (759.23 KB, 下载次数: 0)

下载附件

2023-11-28 18:49 上传

可视化对比，ParaDiffusion在长文本对齐方面表现出非凡的优越性

<img src="https://img.saraba1st.com/forum/202311/28/184947kpt4luujx0pux1up.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-181715__01.jpg</strong> (174.1 KB, 下载次数: 0)

下载附件

2023-11-28 18:49 上传

消融实验

<img src="https://img.saraba1st.com/forum/202311/28/184952rbonbbubi43gzny8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-181730__01.jpg</strong> (650.63 KB, 下载次数: 0)

下载附件

2023-11-28 18:49 上传

来自ParaDiffusion的更多以人为中心的可视化

<img src="https://img.saraba1st.com/forum/202311/28/184956aob0soc71p7qfbha.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-181819__01.jpg</strong> (673.16 KB, 下载次数: 0)

下载附件

2023-11-28 18:49 上传

来自ParaDiffusion的更多以风景为中心的可视化

<img src="https://img.saraba1st.com/forum/202311/28/185004j3lzvhljo400xccg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-181837__01.jpg</strong> (155.69 KB, 下载次数: 0)

下载附件

2023-11-28 18:50 上传

ParaDiffusion的糟糕案例，ParaDiffusion仍然有针对进行优化的区域

<img src="https://img.saraba1st.com/forum/202311/28/185021p87883s333llu7l8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-181837__02.jpg</strong> (30.54 KB, 下载次数: 0)

下载附件

2023-11-28 18:50 上传

PartiPrompts的1600个提示的用户研究

<img src="https://img.saraba1st.com/forum/202311/28/185025g9l5hs2zly9y2m7y.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-181845__01.jpg</strong> (516.92 KB, 下载次数: 0)

下载附件

2023-11-28 18:50 上传

ParaPrompts-400上的可视化对比，ParaDiffusion在长文本对齐方面展示了显著的优势

<img src="https://img.saraba1st.com/forum/202311/28/185030ltcptanz6ct681yc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-181903__01.jpg</strong> (227.22 KB, 下载次数: 0)

下载附件

2023-11-28 18:50 上传

视觉吸引力和文本忠实度之间存在冲突的风险，包含以下两个见解:
1.仅仅扩展当前模型(SD XL、DeepFloyd-IF)的令牌数量并不能产生令人满意的性能
2.随着输入token数量的增加，所有模型的视觉吸引力都会出现一定程度的下降

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 999#       发表于 2023-11-28 21:59

 本帖最后由 Machinery 于 2023-11-28 22:02 编辑 

PromptSR

使用文本提示扩散进行图像超分辨率

github项目主页:https://github.com/zhengchen1999/PromptSR

通常的图像超分辨率(SR/Image super-resolution)方法一般是对退化(degradation)进行建模，以提高复杂和未知退化场景中的重建精度，然而，从低分辨率图像中提取退化信息非常具有挑战性，这限制了模型的性能

为了提高图像超分辨率性能，一种可行的方法是引入额外的先验(introduce additional priors)，受到多模态方法和文本提示图像处理进步的启发，可以将文本提示引入图像超分辨率以提供退化先验

具体来说，首先设计一个文本图像生成工作流程，通过文本退化表征和退化模型将文本集成到超分辨率数据集中，文本表征采用基于数据装箱法(binning method)离散化地抽象描述退化，这种表征方法还可以保持语言的灵活性，同时，提出了PromptSR来实现文本提示超分辨率，PromptSR采用扩散模型和预训练语言模型(例如T5和CLIP)，在生成的文本图像数据集上训练模型

大量实验表明，将文本提示引入图像超分辨率后，可以在合成图像和真实图像上产生出色的超分辨率效果

<img src="https://img.saraba1st.com/forum/202311/28/215700zuu6vzflesqfy4yz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-203034.jpg</strong> (129.7 KB, 下载次数: 0)

下载附件

2023-11-28 21:57 上传

视觉对比(×4)，LR图像会经历复杂且未知的退化(例如模糊、噪声和下采样)，通过在SR任务中引入文本提示来提供退化先验，可以有效提高重建质量

<img src="https://img.saraba1st.com/forum/202311/28/215709cl33v7q39z6qv8ke.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-203124__01.jpg</strong> (364.08 KB, 下载次数: 0)

下载附件

2023-11-28 21:57 上传

文本图像生成工作流程的插图
(a)工作流程由两部分组成:退化模型(顶部)和文本表征(底部)，退化模型包括五个步骤，其中“Comp”表示压缩操作，文本表征通过基于数据装箱技术的离散化方式描述每个降级操作(例如，噪声操作的[medium noise])，整体文本表征是所有描述的组合
(b)文本图像数据集的示例

<img src="https://img.saraba1st.com/forum/202311/28/215718pj2fsy831y3b893i.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-203150__01.jpg</strong> (330.6 KB, 下载次数: 0)

下载附件

2023-11-28 21:57 上传

PromptSR的整体架构，包括一个去噪网络(DN/denoising network)和一个预训练的文本编码器，文本编码器的权重在训练期间被冻结，首先通过双三次插值(bicubic interpolation)将LR图像x上采样到目标HR分辨率，然后与噪声图像yt (t ∈[1, T])连接作为DN的输入，文本提示c由文本编码器转换为嵌入，嵌入通过交叉注意力(CA/cross-attention)模块注入到DN中，在CA模块中，DN的中间特征被转换为查询(Q/Query)矩阵，而文本嵌入被转换为键(K/Key)和值(V/Value)矩阵

<img src="https://img.saraba1st.com/forum/202311/28/215724kvu4rp7v3vrmt3uj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-203203__01__01.jpg</strong> (84.77 KB, 下载次数: 0)

下载附件

2023-11-28 21:57 上传

对文本提示的消融实验，在ControlNet和PromptSR上进行了实验，用以估计消除特定网络设计的影响，对于没有文本提示的模型，应用空字符串作为输入提示

<img src="https://img.saraba1st.com/forum/202311/28/215832rl9u1l5dh4yuglgl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-203203__01.jpg</strong> (134.43 KB, 下载次数: 0)

下载附件

2023-11-28 21:58 上传

不同提示的视觉对比，模板提示为:[light blur, unchange, light noise, light compression, downsample]，下划线部分表示被替换的内容

<img src="https://img.saraba1st.com/forum/202311/28/215835dw7laqa0dllad74g.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-203203__02.jpg</strong> (72.4 KB, 下载次数: 0)

下载附件

2023-11-28 21:58 上传

对于文本内容的消融实验
Caption：由BLIP生成的整体图像内容的描述…
Degradation(本文)：退化过程的描述
Both：两种描述的组合，格式为 [Caption: content description; Degradation: degradation description]

<img src="https://img.saraba1st.com/forum/202311/28/215857h3u78juvdrrcub6l.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-203203__03.jpg</strong> (72.08 KB, 下载次数: 0)

下载附件

2023-11-28 21:58 上传

对于预训练文本编码器的消融实验，在PromptSR中采用不同的预训练语言模型作为文本编码器，Params:每个文本编码器的参数

<img src="https://img.saraba1st.com/forum/202311/28/215904igdsc2k1jkgkks29.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-203215__01.jpg</strong> (438.01 KB, 下载次数: 0)

下载附件

2023-11-28 21:59 上传

合成数据集的定量对比(×4)，最好和第二好的结果用红色和蓝色着色

<img src="https://img.saraba1st.com/forum/202311/28/215909vhjp7zvdzpb9ck7v.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-203221__01.jpg</strong> (409.08 KB, 下载次数: 0)

下载附件

2023-11-28 21:59 上传

合成数据集的视觉对比(×4)，本文方法可以以高真实和保真度恢复图像

<img src="https://img.saraba1st.com/forum/202311/28/215913kecnznkzcn1zcvyl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-203234__01.jpg</strong> (98.93 KB, 下载次数: 0)

下载附件

2023-11-28 21:59 上传

真实世界数据集的定量对比(×4)

<img src="https://img.saraba1st.com/forum/202311/28/215917qfw6cmscmd006w68.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231128-203234__02.jpg</strong> (316.91 KB, 下载次数: 0)

下载附件

2023-11-28 21:59 上传

真实世界数据集的视觉对比(×4)，本文方法可以生成更真实的图像

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1000#       发表于 2023-11-29 02:28

YUAN 2.0

具有基于局部过滤的注意力(Localized Filtering-based Attention)的大型语言模型

github项目主页:https://github.com/IEIT-Yuan/Yuan-2.0

在这项工作中，引入了基于局部过滤的注意力(LFA/Localized Filtering-based Attention)，将自然语言局部依赖性的先验知识纳入到注意力中，基于LFA，开发并发布了参数范围从21亿到1026亿的大型语言模型Yuan 2.0系列

提出了一种数据过滤和生成方法来构建高质量的预训练和微调数据集，提出了非均衡并行工作流程(non-uniform pipeline parallel)、数据并行(data parallel)、优化器并行(optimizer parallel)的分布式训练方法，成功降低了节点内通信的带宽需求，在大规模分布式训练中取得了良好的性能

与现有模型相比，Yuan 2.0模型在代码生成、数学问题解决和聊天方面显示出令人印象深刻的能力，最新版本的YUAN 2.0，包括模型权重和源代码等，可在Github上获取

github项目说明页:

<img src="https://img.saraba1st.com/forum/202311/29/022850issf1qgaumfyfkmj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231129-022717.jpg</strong> (152.58 KB, 下载次数: 0)

下载附件

2023-11-29 02:28 上传

<img src="https://img.saraba1st.com/forum/202311/29/022850rg36h57sknrt5hg1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231129-022727.jpg</strong> (213.67 KB, 下载次数: 0)

下载附件

2023-11-29 02:28 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1001#       发表于 2023-11-29 12:52

SDXL Turbo

实时文本到图像生成模型

介绍博客:https://stability.ai/news/stability-ai-sdxl-turbo

项目权重:https://huggingface.co/stabilityai/sdxl-turbo

演示Demo:http://clipdrop.co/stable-diffusion-turbo

<img src="https://img.saraba1st.com/forum/202311/29/125135suqtqtu9hzooyejh.jpg" referrerpolicy="no-referrer">

<strong>adversarial_diffusion+(1)-1+1.jpg</strong> (133.42 KB, 下载次数: 0)

下载附件

2023-11-29 12:51 上传

SDXL Turbo通过新的蒸馏技术实现了SOTA性能，能够以前所未有的质量生成单步图像，将所需的步骤数从50减少到只有1步

请参阅研究论文，了解有关该模型的新蒸馏技术的具体技术细节，该技术利用对抗性训练(adversarial training)和分数蒸馏(score distillation)的组合

在Hugging Face上下载模型权重和代码，目前是在允许个人、非商业用途的非商业研究许可证下发布的

在Stability AI的图像编辑平台Clipdrop上可以测试SDXL Turbo，并进行实时文本到图像生成功能的Beta演示
————
SDXL Turbo，一种新的文本到图像模式，SDXL Turbo基于一种称为对抗扩散蒸馏(ADD)的新颖蒸馏技术，该技术使模型能够一步合成图像输出并生成实时文本到图像输出，同时保持高采样保真度。 对于对技术细节感兴趣的研究人员和爱好者，可以在此处获取研究论文(相关链接:https://stability.ai/research/adversarial-diffusion-distillation)
————
对抗扩散蒸馏的优点

SDXL Turbo 在扩散模型技术方面取得了新进展，在SDXL 1.0的基础上进行迭代，并为文本到图像模型实现了一种新的蒸馏技术：对抗扩散蒸馏，通过整合 ADD，SDXL Turbo获得了与GAN(生成对抗网络)共有的许多优势，例如单步图像输出，同时避免了其他蒸馏方法中常见的伪影或模糊
————
与其他扩散模型相比的性能优势

<img src="https://img.saraba1st.com/forum/202311/29/125153v2o55dqdq2qqtzdq.jpg" referrerpolicy="no-referrer">

<strong>turbo_comparing.jpg</strong> (84.02 KB, 下载次数: 0)

下载附件

2023-11-29 12:51 上传

为了评估SDXL Turbo的效果，通过使用相同的提示生成输出来比较多个不同的模型变体(StyleGAN-T++、OpenMUSE、IF-XL、SDXL 和 LCM-XL)，然后人类评估者会随机看到两个输出，并被要求选择最符合提示方向的输出，接下来，用相同的方法完成图像质量的附加测试，在这些盲测中，SDXL Turbo能够以1步击败LCM-XL的4步配置，并且仅用4步击败SDXL的50步配置，通过这些结果，可以看到SDXL Turbo的性能优于最先进的多步模型，其计算要求也显著降低，而无需牺牲图像质量

此外，SDXL Turbo还显著提高了推理速度，在A100上，SDXL Turbo在207毫秒内生成512x512图像(提示编码+单个去噪步骤+解码，fp16)，其中单个UNet在前向评估中只占用了67毫秒
————
使用Clipdrop探索SDXL Turbo

要测试这一新模型的功能，请访问Stability AI的图像编辑平台Clipdrop，以获取SDXL Turbo的实时图像生成的测试版演示，它与大多数浏览器兼容，且目前可以免费试用
————
商业应用

 如果您想将此模型用于您的商业产品或目的，请联系Stability以了解更多信息
————

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  jojog  
##### 1002#       发表于 2023-11-29 13:10

<img src="https://static.saraba1st.com/image/smiley/face2017/029.png" referrerpolicy="no-referrer">1step这个有点离谱，实际上是怎么实现的?


*****

####  Machinery  
##### 1003#       发表于 2023-11-29 13:21

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63170045&amp;ptid=2126390" target="_blank">jojog 发表于 2023-11-29 13:10</a>
1step这个有点离谱，实际上是怎么实现的?</blockquote>
更完了<img src="https://static.saraba1st.com/image/smiley/face2017/037.png" referrerpolicy="no-referrer">鉴别器gan那套

—— 来自 [S1Fun](https://s1fun.koalcat.com)

*****

####  jojog  
##### 1004#       发表于 2023-11-29 13:22

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63170158&amp;ptid=2126390" target="_blank">Machinery 发表于 2023-11-29 13:21</a>

更完了鉴别器gan那套

—— 来自 S1Fun</blockquote>
<img src="https://static.saraba1st.com/image/smiley/face2017/001.png" referrerpolicy="no-referrer">这个真的要拿来收费吗


*****

####  Machinery  
##### 1005#       发表于 2023-11-29 13:26

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63170175&amp;ptid=2126390" target="_blank">jojog 发表于 2023-11-29 13:22</a>
这个真的要拿来收费吗</blockquote>
权重本身是开源的，商业化考量就不清楚了，不过原理公开了只要有算力的应该都能复刻这个蒸馏方法…目前来说这就是个实验演示Demo，其他模型还要从头蒸馏一遍<img src="https://static.saraba1st.com/image/smiley/face2017/037.png" referrerpolicy="no-referrer">对于大公司降低生成成本和实时合成比较重要

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1006#       发表于 2023-11-30 00:29

LLaMA-VID

在大型语言模型中一张图像值2个Token

项目主页:https://llama-vid.github.io/

github项目主页:https://github.com/dvlab-research/LLaMA-VID

hugface权重主页:https://huggingface.co/YanweiLi

数据集下载:https://huggingface.co/datasets/YanweiLi/LLaMA-VID-Data

在这项工作中，提出了一种新颖的方法解决视频和图像理解的视觉语言模型(VLM/Vision Language Models)中的Token生成挑战，称之为LLaMA-VID

当前的VLM虽然精通图像字幕说明和视觉问答等任务，但在处理长视频时由于视觉Token过多会面临计算负担，LLaMA-VID通过用两个不同的Token(即上下文Token和内容Token)表示每个帧来解决此问题

上下文Token根据用户输入对整个图像上下文进行编码，而内容Token则封装每个帧中的视觉提示，这种双Token策略(dual-token strategy)显著减少了长视频的过载，同时保留了关键信息，一般来说，LLaMA-VID使现有的框架能够支持长达一小时的视频，并通过额外的上下文Token来推动其上限

实验证明，它在大多数基于视频或图像的基准测试中超越了以前的方法

<img src="https://img.saraba1st.com/forum/202311/30/002817h0r316883uzehnv1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231129-231547__01.jpg</strong> (245.57 KB, 下载次数: 0)

下载附件

2023-11-30 00:28 上传

所提案的LLaMA-VID在大多数7B LLM基准测试中都取得了领先性能，基于视频和基于图像的基准分别以蓝色和紫色表示

<img src="https://img.saraba1st.com/forum/202311/30/002822ybrt4zgx4tdh8863.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-001606__01.jpg</strong> (208.38 KB, 下载次数: 0)

下载附件

2023-11-30 00:28 上传

LLaMA-VID的框架，根据用户指示，LLaMA-VID将单个图像或视频帧作为输入进行操作，并从LLM生成响应，视觉编码器将输入帧转换为视觉嵌入

文本解码器根据用户输入生成文本查询，在上下文注意力中，文本查询从视觉嵌入中聚合与文本相关的视觉提示(text-related visual cues)，为了提升效率，提供了一个选项将视觉嵌入下采样为多种Token大小，比如单个Token

之后使用线性投影器来表示文本引导的上下文Token和视觉信息丰富的内容Token，以表示时间t的每个帧，最后LLM将用户指示和所有视觉Token作为输入并给出响应

<img src="https://img.saraba1st.com/forum/202311/30/002829pzv0goxueu8gpigo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-001620__01.jpg</strong> (112.45 KB, 下载次数: 0)

下载附件

2023-11-30 00:28 上传

各阶段模型训练的多模态数据分布和指令格式，&lt;image&gt;和&lt;image-i&gt;分别表示单个图像和第i个视频帧的Token

<img src="https://img.saraba1st.com/forum/202311/30/002834p9mhon9ugkmufhhm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-001620__02.jpg</strong> (264.26 KB, 下载次数: 0)

下载附件

2023-11-30 00:28 上传

为电影泰坦尼克号构建指令对的示例，给定电影概要和剧本，利用GPT-4和Claude-2等开发的LLM来生成电影摘要、情节相关的QA对和一般推理QA对

<img src="https://img.saraba1st.com/forum/202311/30/002840gj92mjs8gkzubk7k.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-001627__01.jpg</strong> (159.66 KB, 下载次数: 0)

下载附件

2023-11-30 00:28 上传

与4个零样本视频QA数据集上的领先方法进行对比，报告每帧2个Token的结果，为了公平比较，模型只使用第1阶段和第2阶段的数据(多模态对齐/指令微调)进行训练，没有进行长视频微调，Res表示图像分辨率

<img src="https://img.saraba1st.com/forum/202311/30/002847tp61ot42oapop6jf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-001633__01.jpg</strong> (137.21 KB, 下载次数: 0)

下载附件

2023-11-30 00:28 上传

与基于视频的生成性能基准测试的领先方法进行对比，报告每帧2个Token的结果，为了公平比较，模型只使用第1阶段和第2阶段的数据(多模态对齐/指令微调)进行训练，没有进行长视频微调，Res表示图像分辨率，Correctness, Detail, Context, Temporal, and Consistency分别表示信息正确性、细节方向、上下文理解、时间理解和一致性的评价指标

<img src="https://img.saraba1st.com/forum/202311/30/002853yhdp35h3fc8p3n33.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-001637__01.jpg</strong> (245 KB, 下载次数: 0)

下载附件

2023-11-30 00:28 上传

在8个基准测试上与领先方法进行对比，在这里，使用与LLaVA-1.5中相同的训练和指令微调数据，用1个上下文Token和n个内容Token报告结果，其中n与LLaVA-1.5保持相同，即n=(336/14)的平方=576，为了公平比较，模型只使用第1阶段和第2阶段的数据(多模态对齐/指令微调)进行训练，没有进行长视频微调，Res表示输入图像分辨率，*和†分别表示训练子集包含在训练中，并且数据不公开

<img src="https://img.saraba1st.com/forum/202311/30/002910dsfbvbqhw7v74bhs.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-001652__01.jpg</strong> (422.02 KB, 下载次数: 0)

下载附件

2023-11-30 00:29 上传

使用基于Vicuna-7B的模型的LLaMA-VID示例，分别为单图像、短视频和小时长度的视频

<img src="https://img.saraba1st.com/forum/202311/30/002915qrexjqdcl9i3czcx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-001657__01.jpg</strong> (30.74 KB, 下载次数: 0)

下载附件

2023-11-30 00:29 上传

不同Token类型的对比，使用1个上下文Token(如果存在)和1个内容Token报告结果

<img src="https://img.saraba1st.com/forum/202311/30/002930moao2qw6w3peovpi.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-001702__02.jpg</strong> (31.71 KB, 下载次数: 0)

下载附件

2023-11-30 00:29 上传

不同文本编码器的对比，使用1个上下文Token(如果存在)和1个内容Token报告结果

<img src="https://img.saraba1st.com/forum/202311/30/002933ysgz11v0c8ojs099.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-001702__03.jpg</strong> (135.96 KB, 下载次数: 0)

下载附件

2023-11-30 00:29 上传

对等式1中的输入问题得分最高的高响应区，在Qt中展示前两个查询的响应，图像是从VQA V2测试开发集中随机采样的

<img src="https://img.saraba1st.com/forum/202311/30/002938v5phqptcyv0vbrve.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-001706__01.jpg</strong> (71.72 KB, 下载次数: 0)

下载附件

2023-11-30 00:29 上传

LLaMA-VID的训练设置

<img src="https://img.saraba1st.com/forum/202311/30/002942axldhmmuh9qdmddp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-001745__01.jpg</strong> (495 KB, 下载次数: 0)

下载附件

2023-11-30 00:29 上传

为电影泰坦尼克号构建指令对的详细信息

<img src="https://img.saraba1st.com/forum/202311/30/002947a1p2p0wq1a27021e.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-001835__01.jpg</strong> (583.63 KB, 下载次数: 0)

下载附件

2023-11-30 00:29 上传

使用基于Vicuna-7B模型的长达小时级别的电影的LLaMA-VIDEO示例

<img src="https://img.saraba1st.com/forum/202311/30/002952sdzkm2r5ma0dpamq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-001959__01.jpg</strong> (443.08 KB, 下载次数: 0)

下载附件

2023-11-30 00:29 上传

在相同问题下与LLaMA 2和LongLoRA进行对比

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1007#       发表于 2023-11-30 04:58

RankingGPT

通过渐进式学习增强大型语言模型的文本排名(Text Ranking)能力

github项目主页:https://github.com/Alibaba-NLP/RankingGPT

文本排序是各种信息检索应用中的一项关键任务，最近大型语言模型(LLM)在自然语言处理方面的成功引发了人们对其在文本排序中的应用的兴趣

这些方法主要涉及查询(query)和候选文档(candidate documents)的组合，并利用提示学习(prompt learning)使用特定Token让LLM输出概率或直接生成候选文档的排序列表来确定查询文档的相关性，尽管这些方法卓有成果，但LLM的建模训练目标(通常是以预测下一个Token为中心)与评估查询文档相关性的训练目标之间存在值得注意的差异

为了解决这一差距并充分利用LLM在文本排名任务中的潜力，本文提出了一种渐进式的多阶段训练策略。 首先引入了一个大规模的弱监督的关联文本(relevance texts)数据集，使LLM能够在不改变其原始训练目标的情况下获得预测相关标记的能力，随后结合监督训练，进一步提升LLM的排序能力

在多个基准上的实验结果表明，与以前的竞争方法相比，本文提出的方法在ID(in-domain)和OOD(out-of-domain)场景中都具有优越的性能

<img src="https://img.saraba1st.com/forum/202311/30/045711bxnynhiph0p4xzzq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-045330.jpg</strong> (91.01 KB, 下载次数: 0)

下载附件

2023-11-30 04:57 上传

基准答案和LLM生成查询(LLaMA)的对比，示例来自MS MARCO数据集

<img src="https://img.saraba1st.com/forum/202311/30/045715oawxdzko11naadi2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-045351.jpg</strong> (95.13 KB, 下载次数: 0)

下载附件

2023-11-30 04:57 上传

两阶段训练范式:持续预训练和监督微调

<img src="https://img.saraba1st.com/forum/202311/30/045719skcvichnjzcanznb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-045405.jpg</strong> (66.34 KB, 下载次数: 0)

下载附件

2023-11-30 04:57 上传

维持持续预训练收益的三种SFT策略

<img src="https://img.saraba1st.com/forum/202311/30/045724pzawjboejbzbofwz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-045425.jpg</strong> (128.76 KB, 下载次数: 0)

下载附件

2023-11-30 04:57 上传

各种模型的ID结果

<img src="https://img.saraba1st.com/forum/202311/30/045729khciy1hbysccrzcq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-045438.jpg</strong> (168.22 KB, 下载次数: 0)

下载附件

2023-11-30 04:57 上传

220M-3B参数模型的OOD结果，“Best on”表示模型表现最佳的数据集数量

<img src="https://img.saraba1st.com/forum/202311/30/045733tg34vxgug5443axl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-045455.jpg</strong> (162.44 KB, 下载次数: 0)

下载附件

2023-11-30 04:57 上传

7B模型的OOD结果，“BLO.”, “LLa.”以及“Bai.”分别代表BLOOM，LLaMA，Baichuan模型

<img src="https://img.saraba1st.com/forum/202311/30/045740emogzgsoebm2vrg3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-045523.jpg</strong> (122.74 KB, 下载次数: 0)

下载附件

2023-11-30 04:57 上传

BLOOM-560m和1b在ID和OOD场景的消融结果

<img src="https://img.saraba1st.com/forum/202311/30/045744ys9erhanoeihi1hp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-045542.jpg</strong> (60.36 KB, 下载次数: 0)

下载附件

2023-11-30 04:57 上传

具有不同可训练层的BLOOM-1B结果

<img src="https://img.saraba1st.com/forum/202311/30/045748mt5l6b00fvoftbfv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-045602.jpg</strong> (50.49 KB, 下载次数: 0)

下载附件

2023-11-30 04:57 上传

对比BLOOM-1B与不同负面样本大小的性能

<img src="https://img.saraba1st.com/forum/202311/30/045752c7057a49cev53l30.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-045611.jpg</strong> (100.31 KB, 下载次数: 0)

下载附件

2023-11-30 04:57 上传

不同模型的PPL结果，RankLLaMA和LLaMA-Only排序的PPL分布与其他模型有很大不同，因此，我们只在图中展示了它们的近似位置，并用虚线表示了两个模型

<img src="https://img.saraba1st.com/forum/202311/30/045757cfbkvavkjarg7wra.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-045627.jpg</strong> (91.95 KB, 下载次数: 0)

下载附件

2023-11-30 04:57 上传

RankingGPT和无监督排序方法在BM25 top-100上的排序结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1008#       发表于 2023-11-30 05:44

 本帖最后由 Machinery 于 2023-11-30 05:48 编辑 

CoSeR

桥接图像和语言以实现认知超分辨率(Cognitive Super-Resolution)

项目主页:https://coser-main.github.io/

github项目代码仓库:https://github.com/VINHYU/CoSeR

现有的超分辨率(SR/super-resolution)模型主要侧重于恢复局部的纹理细节，往往忽略了场景内的全局语义信息，这种疏忽可能会导致在恢复过程中遗漏关键的语义细节或引入不准确的纹理

在本工作中，引入了认知超分辨率(CoSeR/Cognitive Super-Resolution)框架，使SR模型能够理解低分辨率图像，这是通过将图像外观和语言理解结合起来生成认知嵌入(cognitive embedding)实现的，这不仅激活大型文本到图像扩散模型的先验信息，而且还有助于生成高质量参考图像以优化SR过程

为了进一步提高图像保真度，还提出了一种称为“All-in-Attention”的新颖条件注入方案(condition injection scheme)，将所有条件信息整合到单个模块中

因此，本方法成功地重建了正确的语义和逼真的细节，在多个基准测试中展示了最新的SOTA性能
————

<img src="https://img.saraba1st.com/forum/202311/30/054323bllk57ual7admd95.jpg" referrerpolicy="no-referrer">

<strong>833b1ccc-65d4-453b-8641-59b4994f8623.jpg</strong> (178.84 KB, 下载次数: 0)

下载附件

2023-11-30 05:43 上传

<img src="https://img.saraba1st.com/forum/202311/30/054323b545755l5boci4if.jpg" referrerpolicy="no-referrer">

<strong>fe3cc81f-3c3a-452f-9bf5-bafb679ff830.jpg</strong> (165.9 KB, 下载次数: 0)

下载附件

2023-11-30 05:43 上传

<img src="https://img.saraba1st.com/forum/202311/30/054323f84lx1qqxqgj855r.jpg" referrerpolicy="no-referrer">

<strong>779db557-054f-4fd2-9d59-0aab05bb8f07.jpg</strong> (120.34 KB, 下载次数: 0)

下载附件

2023-11-30 05:43 上传

<img src="https://img.saraba1st.com/forum/202311/30/054323olo2ttjrtf0t9lts.jpg" referrerpolicy="no-referrer">

<strong>ee5ba05d-651a-4d31-b633-d5304b6a4f2c.jpg</strong> (183.43 KB, 下载次数: 0)

下载附件

2023-11-30 05:43 上传

CoSeR 能够从低分辨率(LR/low-resolution)图像中提取认知特征，并生成在语义和纹理方面与LR图像紧密匹配的高质量参考图像，通过将生成的参考图像与认知特征结合起来可以显著提高SR性能
————
动机

<img src="https://img.saraba1st.com/forum/202311/30/054334e49w4a4t645mu6sd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-054136.jpg</strong> (204.71 KB, 下载次数: 0)

下载附件

2023-11-30 05:43 上传

本文的动机基于以下观察:
现有的SR方法在泛化方面面临局限性，特别是当遇到偏离训练集的退化分布时(上图第一行)，通常，增强SR性能需要根据从特定传感器获取的特定于场景的数据来训练模型，这对于这些场景效果很好，但在不同的场景中效果不佳

当前的SR方法缺乏对图像内容的全面理解，这些方法很擅长从数据中学习退化模式，但在LR图像的语义理解方面却遇到了困难，这影响了对象结构和纹理恢复(上图第二行)
————
概述

<img src="https://img.saraba1st.com/forum/202311/30/054350i9unzyuiynf6yana.jpg" referrerpolicy="no-referrer">

<strong>009f798c-b2f0-49fa-813d-4039ce80a917.jpg</strong> (113.62 KB, 下载次数: 0)

下载附件

2023-11-30 05:43 上传

本文方法可以从LR输入图像中提取认知嵌入，全面掌握整个场景内容，然后利用这种认知嵌入来生成能够保持语义一致性的高分辨率参考图像，最后使用认知嵌入来激活恢复网络中的扩散先验，同时使用生成的参考图像作为附加先验来指导SR过程，在本文模型中使用了Stable Diffusion 2.1-base
————
对比

<img src="https://img.saraba1st.com/forum/202311/30/054630cejcmum7bvrrr22v.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-054611.jpg</strong> (392.54 KB, 下载次数: 0)

下载附件

2023-11-30 05:46 上传

凭借对场景信息的全面理解，CoSeR擅长增强高质量纹理细节，正如第一行和第二行所示，实验结果显示，动物的皮毛和面部特征明显更清晰、更真实，同样，在第三行和第四行中，本方法也熟练地恢复了真实的纹理，例如海葵触手和肉质的叶子，这是其他方法无法比拟的成就，模型的认知能力能够恢复在低分辨率输入中几乎全部丢失的语义细节，值得注意的是，在第一行中，只有本文模型成功地重建了野狗的眼睛，而在第五行中，只有本文方法可以重建沙漏内的沙子

<img src="https://img.saraba1st.com/forum/202311/30/054407g5aouxian4iaq4pd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-054210.jpg</strong> (145.98 KB, 下载次数: 0)

下载附件

2023-11-30 05:44 上传

合成图像的更多对比

<img src="https://img.saraba1st.com/forum/202311/30/054410cgfkfclfhllrktr8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-054224.jpg</strong> (114.75 KB, 下载次数: 0)

下载附件

2023-11-30 05:44 上传

对现实世界或未知退化类型图像的更多对比
————
方法

<img src="https://img.saraba1st.com/forum/202311/30/054416az1676rb5z1grwr7.jpg" referrerpolicy="no-referrer">

<strong>2a35d680-1d58-4adf-afe7-e0b4badacc65.jpg</strong> (111.79 KB, 下载次数: 0)

下载附件

2023-11-30 05:44 上传

CoSeR采用双阶段过程(dual-stage process)来恢复LR图像，最初，研究组开发了一个认知编码器来对图像内容进行彻底分析，将认知嵌入传递给扩散模型，这使得能够激活预训练的Stable Diffusion模型中存在的图像先验，从而促进复杂细节的恢复，此外，本文方法利用认知理解来生成与输入语义紧密一致的高保真参考图像，这些参考图像作为辅助信息，有助于增强超分辨率结果，最终，模型同时将三个条件控制应用于预训练的Stable Diffusion模型：LR图像、认知嵌入和参考图像
————
使用认知嵌入的解释

<img src="https://img.saraba1st.com/forum/202311/30/054809q888ststst3a8tzp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-054710.jpg</strong> (152.58 KB, 下载次数: 0)

下载附件

2023-11-30 05:48 上传

出于几个可以理解的原因，只选择了利用特征嵌入进行认知过程，而不是直接从LR图像生成字幕说明，首先，尽管以语言嵌入为指导，但认知嵌入依然保留了细粒度的图像特征，在生成高语义相似度的参考图像方面具有优势，在上图的第一行中，显示了从LR图像生成的BLIP2字幕说明，但是这并不能识别动物的精确分类、颜色和纹理，导致这与认知适配器(cognitive adapter)相比，生成结果不理想，其次，由于输入分布的差异，预训练的图像描述模型可能会为LR图像生成不准确的描述，相比之下，认知适配器对于LR图像更加稳健，如上图第二行所示，第三，采用预训练的图像描述模型需要大量参数，可能达到7B。 相比之下，认知适配器要轻得多，只有3%的参数，从而产生了良好的效率

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1009#       发表于 2023-11-30 16:38

Character Animation

用于角色动画化(Character Animation)的一致且可控的图像到视频合成(Image-to-Video Synthesis)

项目主页:https://humanaigc.github.io/animate-anyone/

github项目代码仓库:https://github.com/HumanAIGC/AnimateAnyone

角色动画化旨在通过驱动信号(driving signals)从静止图像生成角色的视频，目前，扩散模型因其强大的生成能力已经成为了视觉生成研究的主流，然而，当前的图像到视频领域仍然存在挑战，特别是在角色动画化中，想要保持与角色详细信息的一致性仍然是一个艰巨的问题

在本文中，通过利用扩散模型的力量，提出了一个为角色动画化量身定制的新颖框架，为了保持参考图像中复杂外观特征的一致性，专门设计了ReferenceNet，并使用空间注意力来合并细节特征，为了确保可控性和连续性，还引入了有效的姿态引导器来指导角色的运动，并采用有效的时间建模方法来确保视频帧之间平滑的过渡

通过扩展训练数据，本方法可以对任意角色进行动画化处理，相比其他图像到视频方法相比，本文方法在角色动画化方面产生了更好的结果，此外，还根据时尚视频与人类舞蹈合成的基准测试评估了本文方法，并取得了SOTA结果

<img src="https://img.saraba1st.com/forum/202311/30/163741dkks6kkkmoo60hpx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-163147__01.jpg</strong> (467.49 KB, 下载次数: 0)

下载附件

2023-11-30 16:37 上传

给定参考图像(每组图像中最左边的图片)即可获得一致且可控的角色动画化结果，本文方法能够对任意角色进行动画化处理，生成清晰且时间稳定的视频结果，同时保持与参考角色的外观细节的一致性

<img src="https://img.saraba1st.com/forum/202311/30/163747y66gngk333g3anhw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-163156__01.jpg</strong> (254.07 KB, 下载次数: 0)

下载附件

2023-11-30 16:37 上传

方法概览图，姿态序列(pose sequence)使用Pose Guider进行编码，并与多帧噪声(multi-frame noise)融合，然后由Denoising UNet进行视频生成的去噪过程，Denoising UNet的计算模块由空间注意力(Spatial-Attention)、交叉注意力(Cross-Attention)和时间注意力(Temporal-Attention)组成，如右侧虚线框所示，参考图像的集成涉及两个方面，首先，通过ReferenceNet提取详细特征并应用于空间注意力，其次，通过CLIP图像编码器提取语义特征以应用于交叉注意，而时间注意力在时间维度上运作，最后VAE解码器将结果解码为视频片段

<img src="https://img.saraba1st.com/forum/202311/30/163753uj2sk42t2he22z3e.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-163228__01.jpg</strong> (358.21 KB, 下载次数: 0)

下载附件

2023-11-30 16:37 上传

定性结果，给定参考图像(最左边的图片)，本文方法展示了对不同角色进行动画化处理的能力，包括全身人物、半身肖像、卡通人物和人形人物，该插图展示了清晰、一致的细节和连续运动的生成结果

<img src="https://img.saraba1st.com/forum/202311/30/163800fdk6ingk77qqqdcd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-163259__01.jpg</strong> (74.22 KB, 下载次数: 0)

下载附件

2023-11-30 16:38 上传

合成时尚视频合成的定性对比，DreamPose和BDMM在保留服装的精细纹理细节方面存在缺陷，而本文方法在保留特殊的细节特征方面表现出色

<img src="https://img.saraba1st.com/forum/202311/30/163804l92lf0evc0vo0kwz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-163259__02.jpg</strong> (49.7 KB, 下载次数: 0)

下载附件

2023-11-30 16:38 上传

时尚视频合成的定量对比，“Dreampose*”表示没有使用样本微调的结果

<img src="https://img.saraba1st.com/forum/202311/30/163808cbembmggaf02muqg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-163259__03.jpg</strong> (86.21 KB, 下载次数: 0)

下载附件

2023-11-30 16:38 上传

DisCo和本文方法之间的定性对比，DisCo在生成的结果中出现了姿态控制错误、颜色不准确和细节不一致等问题，相比之下，本文方法在解决这些问题方面表现出了显着的改进

<img src="https://img.saraba1st.com/forum/202311/30/163814dededad75dseasff.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-163259__04.jpg</strong> (45.78 KB, 下载次数: 0)

下载附件

2023-11-30 16:38 上传

人类舞蹈生成的定量对比

<img src="https://img.saraba1st.com/forum/202311/30/163819hv44ioiz38bbddot.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-163307__01.jpg</strong> (93.98 KB, 下载次数: 0)

下载附件

2023-11-30 16:38 上传

与图像到视频方法的定性对比，当前的图像到视频方法很难生成大量的角色动作，并且在保持与角色图像特征的长期一致性方面面临挑战

<img src="https://img.saraba1st.com/forum/202311/30/163824rrrsl9yzlz99ss9b.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-163307__02.jpg</strong> (72.49 KB, 下载次数: 0)

下载附件

2023-11-30 16:38 上传

不同设计的消融实验，只有ReferenceNet才能保留角色外观细节的一致

<img src="https://img.saraba1st.com/forum/202311/30/163829evfapf103p88lba3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-163307__03.jpg</strong> (39.52 KB, 下载次数: 0)

下载附件

2023-11-30 16:38 上传

消融实验的定量对比

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1010#       发表于 2023-11-30 19:07

visual anagrams

错视排列:使用扩散模型生成多视图视错图

项目主页:https://dangeng.github.io/visual_anagrams/

github代码仓库:https://github.com/dangeng/visual_anagrams

colab体验:https://colab.research.google.com/drive/1hCvJR5GsQrhH1ceDjdbzLG8y6m2UdJ6l?usp=sharing

<img src="https://img.saraba1st.com/forum/202311/30/190814ocuh6itxvochu03x.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-183906__01.jpg</strong> (308.56 KB, 下载次数: 0)

下载附件

2023-11-30 19:08 上传

<img src="https://img.saraba1st.com/forum/202311/30/190814ui6264sy0y4ii4y9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-183915__01.jpg</strong> (312 KB, 下载次数: 0)

下载附件

2023-11-30 19:08 上传

本文解决了合成多视图视错图的问题：在变换(例如翻转或旋转)时会感觉外观改变的图像

提出了一种简单的零样本方法，用于从现成的文本到图像扩散模型中获得这些错视图:在反向扩散过程中，从噪声图像的不同视图估计噪声，然后将这些噪声估计(noise estimate)结合在一起并对图像进行去噪

理论分析表明，该方法恰好适用于可以写成正交变换(orthogonal transformations)的视图，其中的排列是正交变换的子集，这就引出了错视图的想法——在像素重新排列的情况下会改变外观的图像，包括旋转和翻转，还包括更奇特的像素排列，例如拼图重排列(jigsaw rearrangement)，本方法也可以自然地扩展到具有两个以上视图的错视

提供了定性和定量结果，证明了方法的有效性和灵活性
————

<img src="https://img.saraba1st.com/forum/202311/30/190718aeni7rzny4hssnos.jpg" referrerpolicy="no-referrer">

<strong>method.jpg</strong> (302.27 KB, 下载次数: 0)

下载附件

2023-11-30 19:07 上传

这个方法在概念上很简单，通过采用现成的扩散模型，并用它来估计不同视图或变换中的图像v_i的噪声，然后通过应用反转视图(inverse view)来对齐噪声估计v_i^{-1}并一起平均，然后该平均噪声估计被用来进行扩散步骤

并不是每个视图函数都适用于上述方法。 当然v_i必须是可逆的，但这里可以讨论两个额外的约束

<img src="https://img.saraba1st.com/forum/202311/30/190725dmxdr9agdgub11iu.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231130-190053.jpg</strong> (180.12 KB, 下载次数: 0)

下载附件

2023-11-30 19:07 上传

————
正交变换

大多数图像的正交变换在视觉上是没有意义的，例如，用随机采样的正交矩阵变换下面的图像

<img src="https://img.saraba1st.com/forum/202311/30/190733sbdc1z2gd76xbcib.jpeg" referrerpolicy="no-referrer">" src="https://static.saraba1st.com/image/common/none.gif" referrerpolicy="no-referrer">

<strong>orthogonal.jpeg</strong> (307.19 KB, 下载次数: 0)

下载附件

2023-11-30 19:07 上传

然而，排列矩阵是正交矩阵的子集，并且非常容易解释，它们只是图像中像素的重排列，这就是错视排列(visual anagram)的想法由来，这里的大多数错觉都可以这样解释——作为像素的特定重新排列——例如旋转、翻转、倾斜、“内旋转”、拼图重排列和块(patch)排列，最后，颜色反转不是排列，而是正交的，因为它们是像素值的否定(negation)

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1011#       发表于 2023-12-1 04:46

TimeBench

大型语言模型的时间推理(Temporal Reasoning)能力综合评估

github项目主页:https://github.com/zchuz/TimeBench

理解时间是人类认知能力的一个关键方面，这对于理解世界的复杂程度的更广泛框架至关重要，之前的研究通常关注时间的特定方面，缺乏全面的时间推理基准测试

为了解决这个问题，本文提出了TimeBench，一个全面的分级时间推理基准测试(hierarchical temporal reasoning benchmark)，涵盖了广泛的时间推理现象，为研究大型语言模型的时间推理能力提供了全面的评估

通过对流行的LLM(例如GPT-4、LLaMA2和Mistral模型)进行的广泛的实验，并结合了思维链(CoT)提示，实验结果表明，SOTA LLM与人类之间依然存在显著的性能差距，这证明了在时间推理方面仍有相当多的挑战需要克服，希望TimeBench能够成为一个综合基准，促进LLM的时间推理研究

<img src="https://img.saraba1st.com/forum/202312/01/044529p4mhxmk2q04hgvnw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-044159.jpg</strong> (124.32 KB, 下载次数: 0)

下载附件

2023-12-1 04:45 上传

人类和LLM在TimeBench上的表现的简要概览图，其中人类分数有对应标注

<img src="https://img.saraba1st.com/forum/202312/01/044534htvtd7i1tvdxbvi7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-044214.jpg</strong> (134.74 KB, 下载次数: 0)

下载附件

2023-12-1 04:45 上传

TimeBench中类别、任务和子任务的分布，度数表示数据的比例

<img src="https://img.saraba1st.com/forum/202312/01/044548jydjxuq90x5exq0e.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-044226.jpg</strong> (87.57 KB, 下载次数: 0)

下载附件

2023-12-1 04:45 上传

符号时间推理的示例

<img src="https://img.saraba1st.com/forum/202312/01/044555rwwyhu9bw75y4qzc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-044244.jpg</strong> (194.13 KB, 下载次数: 0)

下载附件

2023-12-1 04:45 上传

常识性时间推理的示例

<img src="https://img.saraba1st.com/forum/202312/01/044601dwgzw627352c6xs7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-044258.jpg</strong> (252.48 KB, 下载次数: 0)

下载附件

2023-12-1 04:46 上传

事件时间推理的示例，C=上下文，Q=问题，A=答案

<img src="https://img.saraba1st.com/forum/202312/01/044606cioni144sczhinfc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-044349__01.jpg</strong> (746.13 KB, 下载次数: 0)

下载附件

2023-12-1 04:46 上传

TimeBench的主要结果，默认情况下，对齐的模型处于零样本设置下，带†的方法是没有对齐的基本模型，在少样本设置下，因此与其他方法无法对比，省略了部分F1成绩，每组中的最佳结果以粗体显示，top-3结果用下划线显示

<img src="https://img.saraba1st.com/forum/202312/01/044611fa6m8nuhk8ikkiqh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-044404.jpg</strong> (87.52 KB, 下载次数: 0)

下载附件

2023-12-1 04:46 上传

基础模型和对齐模型之间的性能差异，Baichuan2和LLaMA2使用了SFT和RLHF对齐，Vicuna、Mistral和ChatGLM3仅使用SFT对齐

<img src="https://img.saraba1st.com/forum/202312/01/044617bsrrxwyzx4qrpr9s.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-044416.jpg</strong> (79.52 KB, 下载次数: 0)

下载附件

2023-12-1 04:46 上传

有和没有CoT提示的性能差距，结果值是GPT-4、GPT-3.5、Baichuan2、LLaMA2/Vicuna-1.5和Mistral的平均值

<img src="https://img.saraba1st.com/forum/202312/01/044622vr6yylg6gn1tunsu.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-044428.jpg</strong> (127.65 KB, 下载次数: 0)

下载附件

2023-12-1 04:46 上传

Δ思维链提示和直接I-O提示之间的得分
上:零样本设置，下:少样本设置，左:每个任务的变化，右:符号、常识、事件和整体任务的平均变化

<img src="https://img.saraba1st.com/forum/202312/01/044628gm6w83vm4z3ejz3d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-044437.jpg</strong> (92.32 KB, 下载次数: 0)

下载附件

2023-12-1 04:46 上传

在少样本设置下得出的每个时间常识方面的结果，带†的型号是基本模型，红色↓和绿色↑代表成绩低于或高于平均水平

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1012#       发表于 2023-12-1 21:40

Grad-CAM

影子不会撒谎，线条不会弯曲！生成模型(暂时还)不知道射影几何(Projective Geometry)

项目主页:https://projective-geometry.github.io/

生成模型可以生成令人印象深刻的逼真图像，本文证明了这些生成的图像具有与真实图像不同的几何特征，通过构建了一组生成图像的集合，清洗(prequalified)这些图像惊人的简单，并且可以欺骗基于信号的简单分类器，使其相信它们是真实的

随之而来的是，通过仅查看几何属性的分类器可以可靠地识别这些经过清洗的生成图像，使用三个这样的分类器，所有的三个分类器都被拒绝访问图像的具体像素，并且仅查看图像衍生的几何特征

第一个分类器着眼于图像的透视场(perspective field)，第二个分类器着眼于图像中的线条检测(lines detected)，第三个分类器着眼于检测到的对象和阴影(detected objects and shadows)之间的关系，对于来自多个不同生成器的图像，本文程序比基于SOTA局部信号的检测器可以更可靠地检测生成的图像

显著图(Saliency maps)表明分类器可以可靠地识别几何问题，得出的结论是，当前的生成器无法可靠地再现真实图像的几何特性
————

<img src="https://img.saraba1st.com/forum/202312/01/213919b28xkzpkl1am7enk.jpg" referrerpolicy="no-referrer">

<strong>teaser.jpg</strong> (765.28 KB, 下载次数: 0)

下载附件

2023-12-1 21:39 上传

人工智能生成的图像虽然在视觉上很有吸引力，但在阴影对齐和消失点(vanishing point)精度方面经常存在错误，本文模型可以有效地检测到这些系统不一致之处，有助于识别此类图像
————
对应工作流程一览

<img src="https://img.saraba1st.com/forum/202312/01/213948kxtayia6tfzcaaac.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-213726.jpg</strong> (46.71 KB, 下载次数: 0)

下载附件

2023-12-1 21:39 上传

<img src="https://img.saraba1st.com/forum/202312/01/213948x2z2l6r2vtmlm876.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-213751.jpg</strong> (68.76 KB, 下载次数: 0)

下载附件

2023-12-1 21:39 上传

<img src="https://img.saraba1st.com/forum/202312/01/213948gttggmqc7rg1mcgr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-213807.jpg</strong> (71.6 KB, 下载次数: 0)

下载附件

2023-12-1 21:39 上传

————
图像分析

<img src="https://img.saraba1st.com/forum/202312/01/213955c8z6x6ba18v6xtzh.jpg" referrerpolicy="no-referrer">

<strong>bae694a4-58e2-4c60-8ebe-abbc05f927fb.jpg</strong> (176.08 KB, 下载次数: 0)

下载附件

2023-12-1 21:39 上传

室内:
对Stable Diffusion-XL室内场景的Grad-CAM分析暴露了几何缺陷:原始图像的对象阴影不匹配，而Grad-CAM突出显示了合成指标，例如家具的误导阴影，此外，它还可以识别透视场中的异常情况，例如未对齐的线条和橱柜顶部的差异，从而证实了模型在检测人工智能生成的图像错误方面的准确性

<img src="https://img.saraba1st.com/forum/202312/01/214002a59v95691m9gmgmf.jpg" referrerpolicy="no-referrer">

<strong>2336bfd1-48f8-4e10-a6a2-23e1587e8026.jpg</strong> (182.71 KB, 下载次数: 0)

下载附件

2023-12-1 21:40 上传

室外:
Grad-CAM揭示了Stable Diffusion-XL图像中的关键错误:车辆中不同的阴影方向以及消失点附近的结构扭曲，突出了其在检测AI生成内容中的几何不一致方面的精度

<img src="https://img.saraba1st.com/forum/202312/01/214008fqe904j40p9fapj9.jpg" referrerpolicy="no-referrer">

<strong>b43**1-c0f0-465c-b234-ca3286875040.jpg</strong> (261.55 KB, 下载次数: 0)

下载附件

2023-12-1 21:40 上传

DALL-E 3:
DALL-E 3生成内部场景分析，使用对象阴影和透视场线索进行的GradCam可视化分析，对象阴影GradCam可以识别不匹配的阴影方向和长度，而透视场GradCam可以揭示房间几何形状中线对齐和消失点的不准确情况

<img src="https://img.saraba1st.com/forum/202312/01/214014syvgqpp8xxvhlg9c.jpg" referrerpolicy="no-referrer">

<strong>aa1b5193-62d4-4db6-981b-62d838b4598c.jpg</strong> (324.25 KB, 下载次数: 0)

下载附件

2023-12-1 21:40 上传

Adobe Firefly:
Adobe Firefly的街道场景揭示了投影几何的不一致，并使用对象阴影和透视场进行了分析，对象阴影GradCam突出显示不匹配的阴影方向和长度，而透视场GradCam检测到了消失点附近和场景深度中的线条不一致，特别是在道路标记和建筑物外墙中
————
性能结果

<img src="https://img.saraba1st.com/forum/202312/01/214026j3eg8mz43ufrpqu6.png" referrerpolicy="no-referrer">

<strong>results.png</strong> (282.54 KB, 下载次数: 0)

下载附件

2023-12-1 21:40 上传

通过ROC曲线评估Stable Diffusion XL的AI生成图像中的投影几何线索

<img src="https://img.saraba1st.com/forum/202312/01/214032fkh7lvydddi8dmmo.png" referrerpolicy="no-referrer">

<strong>mixed_plot_outdoor.png</strong> (273.04 KB, 下载次数: 0)

下载附件

2023-12-1 21:40 上传

通过ROC曲线评估DeepFloyd, Firefly, Kandinsky, PixArt-alpha, DALL-E 3的AI生成图像中的投影几何线索

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1013#       发表于 2023-12-1 23:07

ILoRA(intrinsic lora)

生成模型们知道什么？ 他们知道事情吗？ 让我们来看看吧！

项目主页:https://intrinsic-lora.github.io/

生成模型已被证明能够合成高度详细且逼真的图像，人们很自然地怀疑它们已经隐式学习了对某些图像内在特征(例如表面法线、深度或阴影)进行建模

在本文中，提出了令人信服的证据，证明生成模型确实在内部产生了高质量的场景内在特征(intrinsic)图，从而引入了Intrinsic lora(ILoRA)，一种通用的即插即用方法，可以将任何生成模型转换为场景内在特征预测器，能够直接从原始生成器网络中提取场景内在特征图，无需额外的解码器或完全微调原来的模型

本文方法采用了关键特征图的低秩适应(LoRA)，新学习的参数只占生成模型中总参数的0.6%不到，通过一小组标记(labeled)图像进行了优化，这种模型无关(model-agnostic)方法适用于各种生成架构，包括扩散模型、GAN和自回归模型

实验表明，本文方法生成的场景内在特征映射图可以与领先的监督技术生成的场景内在特征映射图相比，甚至在某些用例下超过了这些方法

<img src="https://img.saraba1st.com/forum/202312/01/230157l3nrz3r6jr2jj3bk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-225306__01.jpg</strong> (473.5 KB, 下载次数: 0)

下载附件

2023-12-1 23:01 上传

引入了intrinsic lora(I-LORA)，它揭示了各种生成模型中的隐藏能力，包括VQGAN(a)、StyleGAN-XL(b)、StyleGAN-v2(c)和Stable Diffusion(d)

本方法使用了lora来调制关键特征图，其中包括VQGAN中的注意力层以及StyleGAN中的Stable Diffusion和affine层，这种调制使模型能够揭示图像中的法线、深度、反照率和阴影等固有属性

I-LORA有效地使用了现有的解码器进行内在特征图像提取，该解码器之前用于RGB图像生成，在不需要新的层就能做到这一点可以看出这些模型对复杂场景内在特征的深刻、内在的理解

<img src="https://img.saraba1st.com/forum/202312/01/230215gnz5myrfsmds57nn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-225322__01.jpg</strong> (95.05 KB, 下载次数: 0)

下载附件

2023-12-1 23:02 上传

在不改变生成器头(generator head)的情况下跨越不同生成模型的场景内在特征提取能力的总结
✓:可以高质量地提取内在特征
∼:无法高质量提取内在特征
×:无法提取内在特征

<img src="https://img.saraba1st.com/forum/202312/01/230224fbpwz665pnbb5bbe.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-225336__01.jpg</strong> (498.14 KB, 下载次数: 0)

下载附件

2023-12-1 23:02 上传

来自不同生成器(VQGAN、StyleGAN-v2和StyleGAN-XL)的场景内在特征，在FFHQ数据集上进行训练：第一列显示每个模型生成的原始合成图像，随后的列显示了与表面法线、深度、反照率和阴影相对应的场景内在特征，由SOTA非生成模型和本文方法(I-LORA)提取

对于表面法线(surface normals)，图像突出了模型推断表面方向和轮廓的能力，深度图(depth maps)展示了图像内的感知距离，较暖的颜色表示较近的物体，较冷的颜色表示较远的物体，反照图(Albedo maps)则隔离了拍摄对象的固有颜色，消除了光照和阴影的影响，最后，着色贴图(shading maps)捕捉了光线和表面的相互作用，显示光线如何影响不同面部特征的外观

有趣的是，生成图像的保真度和提取的表面法线的准确性之间似乎存在相关性，这表明模型的图像生成能力越复杂，它就越能精确地在其场景本质中复制与现实世界物理的细微差别

<img src="https://img.saraba1st.com/forum/202312/01/230235ils0n02ts7znp2ps.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-225347__01.jpg</strong> (229.62 KB, 下载次数: 0)

下载附件

2023-12-1 23:02 上传

应用于单步扩散模型的INTINSIC LORA概览图，微调了与关键特征图对应的低秩矩阵(特别是注意力矩阵)，以引出场景内在特征，不同的低阶适配器，由颜色编码的θ表示(例如，紫色表示表面法线)，通过利用一组有限的标记示例来使生成模型能够使用原始解码器中直接提取场景内在特征，针对每个内在特征进行了优化，从而避免了需求专门的解码器或重新全面训练模型的需求

<img src="https://img.saraba1st.com/forum/202312/01/230301ro7zvpvxvw5vn8nx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-225402__01__01.jpg</strong> (177.83 KB, 下载次数: 0)

下载附件

2023-12-1 23:03 上传

从在LSUN卧室图像上训练的Stylegan2中提取场景内在特征

<img src="https://img.saraba1st.com/forum/202312/01/230321l562560ssx06j8l0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-225402__02.jpg</strong> (151.87 KB, 下载次数: 0)

下载附件

2023-12-1 23:03 上传

在ImageNet上训练的StyleGAN-XL
上方:平底锅
下方:笔记本电脑

旁边有相应的场景内在特征(伪基准答案和提取)，表面法线和深度图虽然捕捉了基本形状和体积，但缺乏精确的细节并表现出伪影，反照图无法始终如一地将纹理与照明分开，着色贴图无法完全捕捉光线和表面的微妙相互作用，这些困难与生成的图像整体较差的真实感相关

<img src="https://img.saraba1st.com/forum/202312/01/230336w5gg80u58kofztgx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-225412__01.jpg</strong> (154.7 KB, 下载次数: 0)

下载附件

2023-12-1 23:03 上传

生成图像的场景内在特征提取性能的定量分析，将表面法线与Omnidata-v2的伪基准答案进行对比，将深度与ZoeDepth进行对比，将反照和着色与Paradigms进行对比

指标包括平均角度误差、中值角度误差和表面法线的L1误差；对于深度使用rms和δ&lt;1.25；反照和着色使用rms，还包括SD UNet和AUGUNET在1000个合成图像上的结果，并带有各种完整提示(prompt)

<img src="https://img.saraba1st.com/forum/202312/01/230421vehm17ymeyg8cy84.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-225420__01.jpg</strong> (111.89 KB, 下载次数: 0)

下载附件

2023-12-1 23:04 上传

在真实图像上对不同模型的场景内在提取性能进行的定量分析

<img src="https://img.saraba1st.com/forum/202312/01/230451ec53cdql5dld35gl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-225420__02.jpg</strong> (129.66 KB, 下载次数: 0)

下载附件

2023-12-1 23:04 上传

使用单步SD UNet对训练样本数量进行消融实验，用表面法线预测来说明，(c)列是我们用于训练的Omnidata-v2伪标签，(e)至(i)列下方的数字是训练期间使用的样​​本数量，结果表明，即使使用包含数百张图像的有限数据集，预训练的Stable Diffusion模型也可以辨别大量的表面法线细节

值得注意的是，在数据集大小仅为4000个样本的情况下，本文方法可以准确捕获具有挑战性的区域，例如(a)中左上角的远处墙壁，选择了SD v1-5和LoRA rank=8开始测试

<img src="https://img.saraba1st.com/forum/202312/01/230458vl1upl821st1581e.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-225426__01.jpg</strong> (250.98 KB, 下载次数: 0)

下载附件

2023-12-1 23:04 上传

消融实验——LoRA的Rank，(e)至(i)栏下的数字是LoRA的Rank，设为8时实现了不错的显存效率并给出了良好的结果，所有模型均使用SD v1-5和4000个样本进行训练

<img src="https://img.saraba1st.com/forum/202312/01/230646lp2bab2errie2apr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-225436__01.jpg</strong> (341.18 KB, 下载次数: 0)

下载附件

2023-12-1 23:06 上传

使用改进的扩散技术从AUGUNET模型中提取详细的场景内在特征:展示了从生成模型导出的场景内在特征以及受监督的对应模型

AUGUNET1.5与AUGUNET相同，只是使用SD1.5并且不使用零信噪比策略(Zero SNR strategy)，AUGUNET1.5呈出了更清晰的细节，尤其是在复杂区域-例如灯架和汽车等轻薄结构，另一方面AUGUNET展示了在减少色彩偏移方面的显著改进，同时保持了细节清晰度，就如与最后一行中的基准答案(GT)数据的的对比所示

<img src="https://img.saraba1st.com/forum/202312/01/230722j7cyccyg9dazcdim.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-225456__01.jpg</strong> (377.94 KB, 下载次数: 0)

下载附件

2023-12-1 23:07 上传

AUGUNET模型的结果应用于训练未见的1024x1024合成图像，对于每组，从左到右分别是:图像、表面法线、深度、反照和阴影

第一行包含来自I-LORA的结果，第二行包含来自现有SOTA方法的对应伪基准答案

<img src="https://img.saraba1st.com/forum/202312/01/230734uoc3rnkrocpnkn0l.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-225506__01.jpg</strong> (124.32 KB, 下载次数: 0)

下载附件

2023-12-1 23:07 上传

通过使用单步方法对各种Stable Diffusion版本进行消融实验，观察到生成模型的质量与提取的场景内在特征的准确性之间的相关性，分析包括Stable Diffusion的1.1、1.2和1.5版本，每个版本都展示了图像生成功能的显著增强，从而提高了场景内在特征提取的保真度

<img src="https://img.saraba1st.com/forum/202312/01/230742aqq8tyibbqty1blj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-225506__02.jpg</strong> (93.2 KB, 下载次数: 0)

下载附件

2023-12-1 23:07 上传

单步扩散(SD UNet)产生了令人满意的结果，但多个扩散步骤会导致提取的内在特征未对齐，如SD1.5(多步)列中所示，最后一栏，AUGUNET，展示了使用本文图像条件方法成功纠正这些错位，从而获得对齐良好且连贯的场景内在特征提取

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1014#       发表于 2023-12-1 23:41

WarAgent

战争与和平:基于大型语言模型模拟的世界大战多智能体系统

github项目主页:https://github.com/agiresearch/WarAgenthttps://github.com/agiresearch/WarAgent
我们能否在历史的十字路口避免战争？ 整个人类历史上的个人、学者、政策制定者和组织一直在追寻这个问题，在这项研究中，试图根据人工智能(AI)和大型语言模型(LLM)的最新进展来回答这个问题

本文提出了WarAgent，一个由LLM驱动的多智能体人工智能系统，用于模拟历史性国际冲突中的参与国、他们的决策和后果，包括第一次世界大战(WWI)、第二次世界大战(WWII)和中国古代的战国时期(Warring States Period)

通过评估模拟效果，研究了尖端人工智能系统在研究复杂的人类集体行为(例如不同环境下的国际冲突)方面的能力的进步和局限性，在这些模拟中，代理人之间的新兴互动也为检查导致战争的触发因素和条件提供了一个新颖的视角，研究结果提供了数据驱动的人工智能的增强见解，可以重新定义解决冲突和维持和平战略的方式，这些影响超越了历史分析，为利用人工智能理解人类历史并可能预防未来的国际冲突提供了蓝图

github说明页:

<img src="https://img.saraba1st.com/forum/202312/01/234124icmziidofi2dfwib.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-234036.jpg</strong> (491.03 KB, 下载次数: 0)

下载附件

2023-12-1 23:41 上传

<img src="https://img.saraba1st.com/forum/202312/01/234124joozhim0xzpsl80i.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231201-234043.jpg</strong> (131.28 KB, 下载次数: 0)

下载附件

2023-12-1 23:41 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1015#       发表于 2023-12-2 05:01

HandRefiner

通过基于扩散的条件重绘(Conditional Inpainting)来修复生成图像中畸形手部(Malformed Hands)

github项目仓库:https://github.com/wenquanlu/HandRefiner

扩散模型在生成逼真的图像方面取得了显着的成功，但在生成准确的人手方面依然存在问题，经常出现例如手指数量不正确或手部形状不规则等问题，这一困难源于从训练图像中学习手的物理结构和姿态问题，其中涉及广泛的变形和遮挡，导致了学习难度的增加

为了正确生成手部，本文介绍了一种名为HandRefiner的轻量级后处理(post-processing)解决方案，HandRefiner采用条件重绘方法来纠正畸形的手，同时保持图像的其他部分不变，通过利用手部网格(hand mesh)重建模型，该模型能够始终遵循正确的手指数量和手部形状，同时还能够在生成的图像中拟合所需的手部姿态

给予一个因手部畸形而生成的失败图像，利用ControlNet模块重新注入此类正确的手部信息，此外，当改变控制强度时，还发现了ControlNet中的相转换现象(phase transition phenomenon)，这使之能够利用更容易获得的合成数据，而不会受到现实和合成手之间的领域差距的影响，实验表明，HandRefiner可以显着改进相关图片生成质量

<img src="https://img.saraba1st.com/forum/202312/02/050007o6c4zfp2j6v2ivvj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231202-045318__01.jpg</strong> (598.81 KB, 下载次数: 0)

下载附件

2023-12-2 05:00 上传

Stable Diffusion(前两行)和SDXL(最后一行)所生成的畸形的手(每对图像左侧)，例如手指数量不正确或形状不规则等，可以通过HandRefiner修正(每对图像右侧)

<img src="https://img.saraba1st.com/forum/202312/02/050012lnn8hfn2436d82vz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231202-045337__01.jpg</strong> (257.37 KB, 下载次数: 0)

下载附件

2023-12-2 05:00 上传

HandRefiner概览图，在推理过程中，手部网格重建模型拟合的深度图通过ControlNet注入到重绘推理过程中，在微调时，合成数据用于训练基于深度的ControlNet，以按照重绘工作流程重建手部，HandRefiner简单而有效，**提高了生成的手质量

<img src="https://img.saraba1st.com/forum/202312/02/050019uxdx4qxxxquvq7o7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231202-045342__01.jpg</strong> (185.04 KB, 下载次数: 0)

下载附件

2023-12-2 05:00 上传

通过在HandRefiner工作流程中使用预先训练的深度ControlNet生成手部

<img src="https://img.saraba1st.com/forum/202312/02/050023t8khvmrkns3m138h.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231202-045342__02.jpg</strong> (170.1 KB, 下载次数: 0)

下载附件

2023-12-2 05:00 上传

RHD数据集中的手部示例，缺乏真实纹理

<img src="https://img.saraba1st.com/forum/202312/02/050028ii2mpq21ac6mzhj6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231202-045351__01.jpg</strong> (405.28 KB, 下载次数: 0)

下载附件

2023-12-2 05:00 上传

相转换的图示，当施加的控制强度较小时，手部形状和姿势会发生变化以匹配深度图，而在高控制强度下，手部皱纹和纹理会消失

<img src="https://img.saraba1st.com/forum/202312/02/050033xxo2z1ooeochoq5x.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231202-045358__01.jpg</strong> (88.27 KB, 下载次数: 0)

下载附件

2023-12-2 05:00 上传

使用HAGRID作为参考，原始图像和校正图像之间的图像级FID和 KID指标对比

<img src="https://img.saraba1st.com/forum/202312/02/050038bz2z291obo9op9po.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231202-045416__01.jpg</strong> (468.53 KB, 下载次数: 0)

下载附件

2023-12-2 05:00 上传

HAGRID数据集上的可视化结果

<img src="https://img.saraba1st.com/forum/202312/02/050041j7ubg58egh660v7g.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231202-045423__01.jpg</strong> (48.52 KB, 下载次数: 0)

下载附件

2023-12-2 05:00 上传

以FreiHAND为参考，原始图像与校正图像之间的图像手部分FID和KID指标对比

<img src="https://img.saraba1st.com/forum/202312/02/050046v9977hazva7zvkaa.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231202-045423__02.jpg</strong> (56.76 KB, 下载次数: 0)

下载附件

2023-12-2 05:00 上传

用户研究结果，颜色代表50名参与者的积极投票数

<img src="https://img.saraba1st.com/forum/202312/02/050049xw0tgt0ytevq0ebn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231202-045436__01.jpg</strong> (95.11 KB, 下载次数: 0)

下载附件

2023-12-2 05:00 上传

HandRefiner设计选择的消融实验

<img src="https://img.saraba1st.com/forum/202312/02/050054okhg5fc4mf31cdgg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231202-045545__01.jpg</strong> (282.27 KB, 下载次数: 0)

下载附件

2023-12-2 05:00 上传

ControlNet中的相转换以不同的控制信号为条件，所有模型仅使用合成数据进行训练

<img src="https://img.saraba1st.com/forum/202312/02/050057d4a477aal7lkl661.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231202-045551__01.jpg</strong> (331.12 KB, 下载次数: 0)

下载附件

2023-12-2 05:00 上传

重绘2k HAGIRD图像的不同方法的对比

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1016#       发表于 2023-12-3 23:27

VIDiff

通过具有扩散模型的多模态指令转换视频

项目主页:https://chenhsing.github.io/VIDiff

github项目主页:https://github.com/ChenHsing/VIDiff

扩散模型在图像和视频生成领域取得了巨大的成功，这激发了人们对视频编辑任务的兴趣，比如根据提供的文本描述来编辑视频，然而，现有的大多数方法仅关注较短片段的视频编辑，并且依赖于耗时的微调或推理

本文是第一个提出视频指令扩散(VIDiff/Video Instruction Diffusio)的，这是一种专为广泛的视频任务设计的统一基础模型，这些任务包括理解任务(例如语言引导的视频对象分割)和生成任务(视频编辑和增强)，模型可以根据用户指令在几秒钟内编辑和转换所需的结果

此外，还设计了一种迭代自回归方法(iterative auto-regressive method)来确保编辑和增强的长视频的一致性

实验结果证明，本文方法为不同的输入视频和指令都提供了令人信服的生成结果，无论是定性还是定量方面

<img src="https://img.saraba1st.com/forum/202312/03/232630g0a4xfbuguh03wfr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231203-232010__01.jpg</strong> (594.39 KB, 下载次数: 0)

下载附件

2023-12-3 23:26 上传

VIDiff，一种用于视频转换任务的通用模型，给定输入视频和人类指令，统一模型可以有效地完成视频重上色、模糊、去模糊、编辑、重绘和对象分割等任务

<img src="https://img.saraba1st.com/forum/202312/03/232635yftutet8mex0thyd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231203-232021__01.jpg</strong> (124.39 KB, 下载次数: 0)

下载附件

2023-12-3 23:26 上传

训练阶段概览图，展示了如何将T2I模型迁移到V2V转换任务
(a)文本到图像阶段
(b)文本到视频阶段
(c)视频到视频阶段

<img src="https://img.saraba1st.com/forum/202312/03/232646zdcadfxdcs3ppdts.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231203-232021__02.jpg</strong> (75.73 KB, 下载次数: 0)

下载附件

2023-12-3 23:26 上传

多模态条件方法的概览图，在训练阶段，冻结CLIP-Text和CLIP-Vision编码器，仅微调MLP的参数

<img src="https://img.saraba1st.com/forum/202312/03/232650kp8roqodkoe8tkz6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231203-232049__01.jpg</strong> (488.67 KB, 下载次数: 0)

下载附件

2023-12-3 23:26 上传

VIDiff转换框架的工作流程，利用Stable Diffusion中的预训练自动编码器来获得潜在表征
(a)在训练过程中，随机决定使用前几帧作为条件
(b)第一个视频片段的推理
(c)以视频的最后一帧为条件，可以迭代转换长视频

<img src="https://img.saraba1st.com/forum/202312/03/232656xezn9g9qzjq0g90i.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231203-232056__01.jpg</strong> (245.56 KB, 下载次数: 0)

下载附件

2023-12-3 23:26 上传

不同文本驱动视频编辑方法的属性，对比了模型类型、附加控制、微调时间和应用范围

<img src="https://img.saraba1st.com/forum/202312/03/232703tau7pqk6173osg7t.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231203-232056__02.jpg</strong> (157.04 KB, 下载次数: 0)

下载附件

2023-12-3 23:27 上传

与开源评估基线的定量对比，报告了定量和用户研究结果
“Tuning”是指优化的过程，“Inference”时间包括反演和去噪时间

<img src="https://img.saraba1st.com/forum/202312/03/232707vrbuuiw3933g5wbf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231203-232112__01.jpg</strong> (444.07 KB, 下载次数: 0)

下载附件

2023-12-3 23:27 上传

两个条件输入的无分类器指导权重，sV控制与输入视频的相似度，而sT控制与编辑指令的一致性

<img src="https://img.saraba1st.com/forum/202312/03/232710yodsojoq77yofj87.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231203-232119__01.jpg</strong> (136.22 KB, 下载次数: 0)

下载附件

2023-12-3 23:27 上传

不同方法的评估数据集的定量结果，最佳项目和次佳项目分别以粗体和下划线突出显出

<img src="https://img.saraba1st.com/forum/202312/03/232714a7qmvgvb466tcp73.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231203-232132__01.jpg</strong> (150.76 KB, 下载次数: 0)

下载附件

2023-12-3 23:27 上传

视频增强的定量结果，还报告了通过使用VAE重建基准答案图像获得的上限基线，这表示了使用VAE模型可实现的性能上限

<img src="https://img.saraba1st.com/forum/202312/03/232718taccofmcbokb4fry.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231203-232132__02.jpg</strong> (521.72 KB, 下载次数: 0)

下载附件

2023-12-3 23:27 上传

自回归长视频转换的消融实验，VIDiff可以保持不同视频剪辑片段之间的时间一致性

<img src="https://img.saraba1st.com/forum/202312/03/232722fgt7ezjgzebbkml7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231203-232140__01.jpg</strong> (63.08 KB, 下载次数: 0)

下载附件

2023-12-3 23:27 上传

多任务训练和多阶段迁移方法的消融实验，在四项任务上评估了本文模型，它表明联合的多任务训练和多阶段迁移显著提高了每个任务的性能

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1017#       发表于 2023-12-3 23:55

InstructSeq

将视觉任务与指令条件多模态序列生成(Instruction-conditioned Multi-modal Sequence Generation)统一

github项目主页:https://github.com/rongyaofang/InstructSeq

使模型能够动态地完成用户通过自然语言指令指定的任务，这是一条通向更强大、更通用的人工智能的有希望的道路，在这项工作中，引入了InstructSeq，一种指令条件多模态建模框架，它通过灵活的自然语言控制以及视觉和文本数据的处理来统一不同的视觉任务

InstructSeq采用多模态Transformer架构，涵盖视觉、语言和序列建模，利用视觉编码器来提取图像特征，并利用文本编码器来编码指令，自回归Transformer融合表征并生成序列的任务输出

通过使用LLM生成的自然语言指令进行训练，InstructSeq获得了对用于指定视觉任务的自由格式指令的强大理解能力，这提供了一个直观的界面，可以使用灵活的自然指令来指导模型

无需任何特定于任务的调整，InstructSeq在语义分割、引用表达分割/理解和图像字幕说明方面实现了引人注目的性能，灵活的控制和多任务统一将使模型更具有接近人类的通用性和计算机视觉的泛化能力

<img src="https://img.saraba1st.com/forum/202312/03/235520l7fmth8kx7kntt34.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231203-235014__01.jpg</strong> (231.57 KB, 下载次数: 0)

下载附件

2023-12-3 23:55 上传

InstructSeq包含视觉编码器、冻结的指令编码器和自回归Transformer，视觉编码器提取图像特征，而指令编码器对自由格式的文本指令进行编码，这些表征形式被输入到生成离散Token序列的Transformer，该架构允许模型生成各种输出类型，用以基于自然语言指令完成不同的视觉任务

<img src="https://img.saraba1st.com/forum/202312/03/235524hqit8hbt6t4btif7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231203-235123__01.jpg</strong> (24.09 KB, 下载次数: 0)

下载附件

2023-12-3 23:55 上传

在 FSS-1000基准上评估InstructSeq的分割能力

<img src="https://img.saraba1st.com/forum/202312/03/235529n8118a4f6pm4hzac.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231203-235128__01.jpg</strong> (213.7 KB, 下载次数: 0)

下载附件

2023-12-3 23:55 上传

InstructSeq与专用模型和其他通用模型的性能对比
灰色单元格表示模型无法处理该任务
*表示模型能够完成该任务，但未在基准测试中进行评估

<img src="https://img.saraba1st.com/forum/202312/03/235533skkh12k12ha11zbk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231203-235132__01.jpg</strong> (124.25 KB, 下载次数: 0)

下载附件

2023-12-3 23:55 上传

使用关于RefCOCO参考分割任务的新构造指令评估InstructSeq模型，InstructSeq-Template模型使用每个任务的固定指令模板进行训练，而基本设置InstructSeq-Full使用LLM扩展指令集进行训练，新的构造指令不包含在两个模型的训练集中

<img src="https://img.saraba1st.com/forum/202312/03/235541dp5rll5fbfv7vuvp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231203-235144__01.jpg</strong> (600.51 KB, 下载次数: 0)

下载附件

2023-12-3 23:55 上传

InstructSeq在跨越所有视觉任务中的定性结果

<img src="https://img.saraba1st.com/forum/202312/03/235545gdldgxx7ff14dq74.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231203-235149__01.jpg</strong> (78.52 KB, 下载次数: 0)

下载附件

2023-12-3 23:55 上传

InstructSeq在评估的每个任务期间对多个数字进行采样的结果

<img src="https://img.saraba1st.com/forum/202312/03/235549ff8uobsbfw9b2b9u.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231203-235149__02.jpg</strong> (91.44 KB, 下载次数: 0)

下载附件

2023-12-3 23:55 上传

左:从InstructSeq模型生成的语义分割图
右:Instruct-Seq token采样期间获得的置信图，黄色区域表示低置信度区域，紫色区域表示高置信度区域

<img src="https://img.saraba1st.com/forum/202312/03/235553j7p98njv7o6czo96.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231203-235153__01.jpg</strong> (119.92 KB, 下载次数: 0)

下载附件

2023-12-3 23:55 上传

InstructSeq 与专用模型和其他通用模型的性能对比

<img src="https://img.saraba1st.com/forum/202312/03/235557ndlbdm3ildi7gldz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231203-235153__02.jpg</strong> (49.29 KB, 下载次数: 0)

下载附件

2023-12-3 23:55 上传

对包含所有任务的InstructSeq BASE训练和仅包含图像输出任务的训练进行的消融实验

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1018#       发表于 2023-12-4 02:35

 本帖最后由 Machinery 于 2023-12-4 02:42 编辑 

ElasticDiffusion

免训练任意尺寸图像生成

github项目主页:https://github.com/MoayedHajiAli/ElasticDiffusion-official

近年来，扩散模型彻底改变了图像生成，但目前为止依然仅限于少数的尺寸和长宽比，本文提出了ElasticDiffusion，一种新颖的免训练解码方法，可以使预训练的文本到图像扩散模型能够生成各种尺寸的图像

ElasticDiffusion尝试将预训练模型的生成轨迹解耦为局部(local)和全局(global)信号，局部信号控制低层级像素信息，同时可以在局部区块(local patches)上进行估计(estimated)，而全局信号用于保持整体结构一致性，并使用参考图像进行估计

在CelebA-HQ(面部)和LAION-COCO(物体/室内/室外场景)上测试了方法，实验和定性结果表明，MultiDiffusion与Stable Diffusion的标准解码策略相比，在纵横比上具有更卓越的图像一致性质量

<img src="https://img.saraba1st.com/forum/202312/04/023317c9ooogqtx0o63nx8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231204-022712__01.jpg</strong> (844.45 KB, 下载次数: 0)

下载附件

2023-12-4 02:33 上传

ElasticDiffusion使用在单图像大小上训练的预训练扩散模型生成任意大小的高质量图像，同时具有等效的显存占用且无需进一步训练，上图这些结果基于Stable Diffusion1.4，该模型经过训练原本只能生成512×512图像，而这些图中显示的示例未经过任何图像裁剪、拉伸或后处理策略

<img src="https://img.saraba1st.com/forum/202312/04/023322lrssaqpqbzpp6b0q.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231204-022721__01.jpg</strong> (334.19 KB, 下载次数: 0)

下载附件

2023-12-4 02:33 上传

计算局部区块上扩散模型得分的各种策略的对比
1.相邻区块(A)之间没有重叠会导致边界不连续
2.策略(B)和(C)明确地重叠附近的区块，但需要大量重叠才能有效
3.本文的隐式重叠方法(D)获得了与(B)类似的对于计算需求的优异结果

<img src="https://img.saraba1st.com/forum/202312/04/023328t4574n7bnxag3nin.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231204-022728__01.jpg</strong> (263.21 KB, 下载次数: 0)

下载附件

2023-12-4 02:33 上传

降低分辨率指导(RRG/Reduced-Resolution Guidance)的影响，以增加的权重的方式应用RRG可以有效消除新出现的伪影，尽管代价是输出稍微模糊，在δ=200时达成了很好的平衡

<img src="https://img.saraba1st.com/forum/202312/04/023333kr6u36nb83p8hr48.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231204-022728__02.jpg</strong> (158.56 KB, 下载次数: 0)

下载附件

2023-12-4 02:33 上传

重采样的影响，应用更多的重采样步骤可以显著增强生成图像的细节

<img src="https://img.saraba1st.com/forum/202312/04/023337jn517g72o1odfx55.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231204-022737__01.jpg</strong> (724.43 KB, 下载次数: 0)

下载附件

2023-12-4 02:33 上传

CelebAHQ面部在不同分辨率下的定性对比，ElasticDiffusion在所有分辨率下都能一致地生成连贯图像，Stable Diffusion和MultiDiffusion会在高分辨率生成重复的身体部位，而StableDiffusion-XL则无法在较低分辨率下保持其质量，导致256×256的输出结果出现噪声，同时排除了256×256的MultiDiffusion结果，因为它不是为在较低的分辨率下生成图像而设计的

<img src="https://img.saraba1st.com/forum/202312/04/023341wjpfxcfco0bhtxbl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231204-022755__01.jpg</strong> (327.71 KB, 下载次数: 0)

下载附件

2023-12-4 02:33 上传

各种纵横比的定性对比，ElasticDiffusion可以有效地处理各种纵横比，相比之下，SD和MultiDiffusion会生成不真实的图像，而SDXL的输出则会表现出可以感知的质量下降

<img src="https://img.saraba1st.com/forum/202312/04/023346ap9x899p08s3cppv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231204-022755__02.jpg</strong> (184.95 KB, 下载次数: 0)

下载附件

2023-12-4 02:33 上传

CelebA-HQ和LAION-COCO在不同分辨率下的定量对比，用粗体表示最佳表现，用下划线表示次佳表现，#Calls表示每个解码步骤所需的扩散模型调用的数量

<img src="https://img.saraba1st.com/forum/202312/04/023350z0i94zi0nwl099i9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231204-022812__01.jpg</strong> (147.72 KB, 下载次数: 0)

下载附件

2023-12-4 02:33 上传

不同纵横比(A)和分辨率(R)下LAION-COCO数据集的定量对比，用粗体表示最好的表现，用下划线表示次佳表现，Portrait意味着分辨率从H:W转换为W:H

<img src="https://img.saraba1st.com/forum/202312/04/023516hni5ntt0tuucuttu.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231204-022817__01.jpg</strong> (30.19 KB, 下载次数: 0)

下载附件

2023-12-4 02:35 上传

对ElasticDiffusion进行的500张图像的消融实验

<img src="https://img.saraba1st.com/forum/202312/04/023446fsuut5t3n5nkzdo6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231204-022812__02.jpg</strong> (105.22 KB, 下载次数: 0)

下载附件

2023-12-4 02:34 上传

全高清结果，本方法使SDXL能够生成连贯的全高清图像(1920×1080)，与产生重复纹理和元素的标准流程相反，ElasticDiffusion在较低分辨率应用全局指导来强制执行全局结构

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1019#       发表于 2023-12-4 18:42

LVM

序列建模(Sequential Modeling)以支持大型视觉模型(Large Vision Models)的可扩展学习(Scalable Learning)

项目主页:https://yutongbai.com/lvm.html

github项目仓库:https://github.com/ytongbai/LVM

本文引入了一种新颖的序列建模方法，该方法可以在不使用任何语言数据的情况下进行大型视觉模型(LVM/Large Vision Models)学习，并为此定义了一种通用格式，“视觉句子(visual sentences)”，其中可以表示原始图像和视频以及带标注的数据源，在例如语义分割和深度重建等任务中，不需要除了像素之外的任何元知识(meta-knowledge)

一旦将如此广泛的视觉数据(包含约4200亿个Token)表示为序列，就可以训练模型最小化下一个Token预测的交叉熵损失，通过跨越不同规模的模型架构和数据多样性进行训练，提供了经验证据，证明本文模型可以有效地扩展，通过在测试时设计合适的视觉提示可以解决许多不同的视觉任务
————
Visual Sentence启用了统一的视觉数据格式

<img src="https://img.saraba1st.com/forum/202312/04/184039drt3ofqhtnskqzra.jpg" referrerpolicy="no-referrer">

<strong>9686299f-712a-4a37-aa67-865b6b84534b.jpg</strong> (246.19 KB, 下载次数: 0)

下载附件

2023-12-4 18:40 上传

Visual Sentence允许将不同的视觉数据格式统一为图像序列结构
————
LVM展示了跨越模型和数据大小的可扩展性

<img src="https://img.saraba1st.com/forum/202312/04/184053x4dua6fyap1jjcfn.jpg" referrerpolicy="no-referrer">

<strong>training_loss_plot.jpg</strong> (288.69 KB, 下载次数: 0)

下载附件

2023-12-4 18:40 上传

300M、600M、1B和3B模型的训练损失，所有模型均在420B Token上进行训练，这些Token对应总共1.64B的图像，训练的缩放可以很好地拓展到不同模型大小

<img src="https://img.saraba1st.com/forum/202312/04/184104vjum8z32jpmddj9m.jpg" referrerpolicy="no-referrer">

<strong>semantic_segmentation_plot.jpg</strong> (248.34 KB, 下载次数: 0)

下载附件

2023-12-4 18:41 上传

<img src="https://img.saraba1st.com/forum/202312/04/184104sall14l646w5newe.jpg" referrerpolicy="no-referrer">

<strong>depth_estimation_plot.jpg</strong> (233.56 KB, 下载次数: 0)

下载附件

2023-12-4 18:41 上传

<img src="https://img.saraba1st.com/forum/202312/04/184104jad4c66o27c7xdfm.jpg" referrerpolicy="no-referrer">

<strong>Surface_Normal_plot.jpg</strong> (236.52 KB, 下载次数: 0)

下载附件

2023-12-4 18:41 上传

<img src="https://img.saraba1st.com/forum/202312/04/184104hlchfjl24kj2c2df.jpg" referrerpolicy="no-referrer">

<strong>Edge_Detection_plot.jpg</strong> (259.17 KB, 下载次数: 0)

下载附件

2023-12-4 18:41 上传

更大的LVM在下游任务上表现更好，按照ImageNet验证集上的5样本设置，在4个不同的下游任务上评估了不同大小的LVM，并报告了困惑度，可以发现，所有任务中的模型越大，困惑度就越低，这表明其具有很强的可扩展性

<img src="https://img.saraba1st.com/forum/202312/04/184117u667vp5vg717b151.jpg" referrerpolicy="no-referrer">

<strong>dataset_ablation.jpg</strong> (200.11 KB, 下载次数: 0)

下载附件

2023-12-4 18:41 上传

使用ImageNet验证集评估了在数据集的不同子组成(sub-components)上训练的4个模型在任务上的困惑度，所有模型均为3B参数，所有评估均在5样本设置下进行，可以看到该模型受益于每个图像、视频和标注，这证明了训练数据集多样性的重要性
————
结果，一切尽在提示(prompt)

<img src="https://img.saraba1st.com/forum/202312/04/184128zc66yz5dixc7drgd.jpg" referrerpolicy="no-referrer">

<strong>videos.jpg</strong> (783.66 KB, 下载次数: 0)

下载附件

2023-12-4 18:41 上传

框架预测，LVM按照提示依据先前的视频帧来预测下一帧(以红色标记)，结果表明，LVM可以在考虑动态对象和摄像机运动的情况下预测视频帧

<img src="https://img.saraba1st.com/forum/202312/04/184137x801by8r6h2kyky9.jpg" referrerpolicy="no-referrer">

<strong>3fb0c959-dd50-4d13-9c4a-f6a36fe35f69.jpg</strong> (303.03 KB, 下载次数: 0)

下载附件

2023-12-4 18:41 上传

进出(In and out)分布提示的示例，每一行都是一个提示，其中包含一系列与标注交错的图像，并附加一个查询，最后一张图像是由模型预测的(以红色标记)，最后5行显示了查询图像对于其训练任务来说超出分布(out of distribution)的示例(绘画、草图等)

<img src="https://img.saraba1st.com/forum/202312/04/184142kjfjzziujstcsdjr.jpg" referrerpolicy="no-referrer">

<strong>complex_task_3.jpg</strong> (710.89 KB, 下载次数: 0)

下载附件

2023-12-4 18:41 上传

组合&amp;新任务，在一个提示中将多个任务组合在一起，在这里演示了旋转任务和新颖的关键点对应任务，并要求模型继续预测该模式
————
各种提示，猜猜接下来会发生什么？

<img src="https://img.saraba1st.com/forum/202312/04/184155gyldh57s3h3ehayd.jpg" referrerpolicy="no-referrer">

<strong>Guess_2.jpg</strong> (459.03 KB, 下载次数: 0)

下载附件

2023-12-4 18:41 上传

并不总是可以轻易用语言描述的任务

<img src="https://img.saraba1st.com/forum/202312/04/184200mjxyzxaz78jf8d7z.jpg" referrerpolicy="no-referrer">

<strong>raven_2.jpg</strong> (262.78 KB, 下载次数: 0)

下载附件

2023-12-4 18:42 上传

非语言的智商测试

<img src="https://img.saraba1st.com/forum/202312/04/184204evz4lfl1fyur1ri1.jpg" referrerpolicy="no-referrer">

<strong>misc.jpg</strong> (416.84 KB, 下载次数: 0)

下载附件

2023-12-4 18:42 上传

各种简单的视觉任务，例如对象复制(上方)、重新照明(中间)和放大(下方)，都可以通过适当选择的Visual Sentence提示来简单地指定并将任务表达给LVM

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1020#       发表于 2023-12-4 19:56

 本帖最后由 Machinery 于 2023-12-4 19:59 编辑 

vip-llava

让大型多模态模型理解任意视觉提示(Arbitrary Visual Prompts)

项目主页:https://vip-llava.github.io/

演示Demo:https://pages.cs.wisc.edu/~mucai/vip-llava.html

github项目代码仓库:https://github.com/mu-cai/vip-llava

系列模型权重下载:https://github.com/mu-cai/ViP-LLaVA/blob/main/docs/MODEL_ZOO.md

现有的大型视觉语言多模态模型专注于整张的图像理解，这也致使在实现特定区域的理解方面存在显著的差距，当前方法使用的诸如文本坐标或空间编码的方法通常无法为用户提供友好的视觉提示交互

为了应对这一挑战，本文引入了一种新颖的多模态模型，能够解码任意视觉提示，这允许用户直观地标记图像并使用“红色边界框(red bounding box)”或“尖箭头(pointed arrow)”等自然提示与模型交互

通过直接将视觉标记覆盖到RGB图像上这样的简单设计，无需复杂的区域编码，在Visual7W、PointQA和Visual Commonsense Reasoning基准测试等区域理解任务上实现了SOTA性能

此外，还推出了ViP-Bench，一个综合基准测试，用于评估模型在多个维度理解视觉提示的能力，从而促进该领域的未来研究
————
ViP-LLaVA直接将视觉提示与原始图像叠加，然后将图像输入多模态模型，这个方法有几个好处:

简单的设计:不需要特定区域编码模块
可以推广到任意视觉提示:用户可以绘制任意的视觉提示，如涂鸦、圆圈和点

<img src="https://img.saraba1st.com/forum/202312/04/195423a6h9x399brrh34in.jpg" referrerpolicy="no-referrer">

<strong>b2f81964-e66e-405f-bce2-54a42fd2bfab.jpg</strong> (142.26 KB, 下载次数: 0)

下载附件

2023-12-4 19:54 上传

在训练过程中使用了8种不同的视觉提示，包括蒙版轮廓、椭圆、边界框、三角形、涂鸦、点、箭头和蒙版(mask contour, ellipse, bounding box, triangle, scribble, point, arrow, and mask)，注意，各种提示不仅具有不同的形状，而且还具有不同的颜色、透明度值、宽度、大小和方向

<img src="https://img.saraba1st.com/forum/202312/04/195443v13nj55iq8356n83.jpg" referrerpolicy="no-referrer">

<strong>acfaf39a-d099-4e4e-b3b6-65dd456ca606.jpg</strong> (118.36 KB, 下载次数: 0)

下载附件

2023-12-4 19:54 上传

————
表现

传统的区域级基准测试：ViP-LLaVa实现了SOTA性能

<img src="https://img.saraba1st.com/forum/202312/04/195506fcuvye7yenucw1ed.png" referrerpolicy="no-referrer">

<strong>visual7w_pointqa_results.png</strong> (299.46 KB, 下载次数: 0)

下载附件

2023-12-4 19:55 上传

ViP-Bench:开源模型中的SOTA

ViP-Bench是第一个零样本区域级基准测试，全面评估多模态模型理解视觉提示的能力，ViP-Bench由303个样本组成，评估识别、OCR、知识、数学、对象关系推理和语言生成等6项能力
ViP-Bench有两种格式:(1)边界框格式，(2)人工标注的任意视觉提示

<img src="https://img.saraba1st.com/forum/202312/04/195527cyx1x1z43cy1o65b.jpg" referrerpolicy="no-referrer">

<strong>01cc796e-3c25-48c9-bac9-de25bfb952e5.jpg</strong> (115.36 KB, 下载次数: 0)

下载附件

2023-12-4 19:55 上传

GPT-4V仍然是零样本视觉提示理解中最强的多模态模型，ViP-LLaVA在ViP-Bench上显示出令人印象深刻的性能，大多数的特定区域多模态模型(例如Kosmos-2)甚至表现出比图像级多模态模型更低的性能

<img src="https://img.saraba1st.com/forum/202312/04/195609ahl6prb2tldjlhw9.png" referrerpolicy="no-referrer">

<strong>vip-bench-results.png</strong> (443 KB, 下载次数: 0)

下载附件

2023-12-4 19:56 上传

————
视觉提示理解示例

<img src="https://img.saraba1st.com/forum/202312/04/195643z2n8lhh2o622n885.png" referrerpolicy="no-referrer">

<strong>vip-example.png</strong> (1001.66 KB, 下载次数: 0)

下载附件

2023-12-4 19:56 上传

这里关注了一些GPT-4V无法识别的视觉提示，而ViP-LLaVA则成功的情况，然而在大多数用例下，GPT-4V在视觉提示理解方面表现出了稳健和强大的性能

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1021#       发表于 2023-12-4 22:07

VideoBooth

带有图像提示(Image Prompts)的基于扩散的视频生成

项目主页:https://vchitect.github.io/VideoBooth-project/

github项目仓库:https://github.com/Vchitect/VideoBooth

当前，文本驱动的视频生成得到了快速进步，然而，仅使用文本提示不足以准确描述符合用户意图的所需主题外观(subject appearance)，尤其是对于定制内容创造而言

在本文中，研究了带有图像提示的视频生成任务，这提供了超越文本提示的更准确和直接的内容控制，具体来说，提出了一个前馈框架(feed-forward framework)VideoBooth，包含两个专用设计:

1.以从粗到细的方式嵌入图像提示，来自图像编码器的粗略视觉嵌入(Coarse visual embeddings)提供了图像提示的高层级(high-level)编码，而来自所提出的注意注入模块(attention injection module)的精细视觉嵌入提供了图像提示的多尺度和详细信息编码，这两个互补的嵌入可以忠实地捕捉所需的外观

2.在精细级别(fine level)的注意力注入模块中，多尺度图像提示被作为附加键(keys)和值(values)输入到不同的跨帧注意力层中，这种额外的空间信息细化了第一帧中的细节，然后传播(propagated)到剩下的其他帧中，从而保持了时间一致性

大量实验表明，VideoBooth在生成具有图像提示中指定主题的定制高质量视频方面实现了SOTA性能，VideoBooth还是一个通用框架，其中单个模型适用于具有前馈传递的各种图像提示

<img src="https://img.saraba1st.com/forum/202312/04/220654uqt3118trjs9j3qq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231204-220209__01.jpg</strong> (622.81 KB, 下载次数: 0)

下载附件

2023-12-4 22:06 上传

通过图像提示合成的视频，VideoBooth可以生成具有图像提示中指定主题的视频

<img src="https://img.saraba1st.com/forum/202312/04/220737jh5ohjbuql7l57tl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231204-220218__01.jpg</strong> (395.57 KB, 下载次数: 0)

下载附件

2023-12-4 22:07 上传

图像提示的使用，使用不同类型的提示生成了三个视频剪辑片段：简单文本提示、长文本提示和图像提示，使用LLaVa模型生成具有描述图像提示外观的文本提示，单独使用文字提示并不能完全捕捉图像提示的视觉特征

<img src="https://img.saraba1st.com/forum/202312/04/220635strl29kr2qsaz1a1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231204-220232__01.jpg</strong> (401.54 KB, 下载次数: 0)

下载附件

2023-12-4 22:06 上传

VideoBooth概览图，首先，以图像提示I和文本提示T作为输入来生成视频，图像提示被输入CLIP图像编码器，然后是MLP层，之后将获得的粗略视觉嵌入fI插入到文本嵌入中，组合的嵌入则作为交叉注意力的输入，编码器提取的嵌入提供了图像提示的视觉外观的粗略编码，为了进一步细化生成视频中的细节，在精细级别上，将图像提示的潜在表征作为附加的键和值附加到跨帧注意力中，不同的跨框帧注意力层接收不同尺度的潜在表征，具有空间细节的多尺度特征细化了合成细节

<img src="https://img.saraba1st.com/forum/202312/04/220848p99sn0ny2ajza7en.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231204-220244__01.jpg</strong> (214.67 KB, 下载次数: 0)

下载附件

2023-12-4 22:08 上传

精细的视觉嵌入细化，将图像提示的潜在表征(这里使用图像用于说明目的)直接注入到跨帧注意力模块中，首先使用图像提示中的键和值来更新第一帧的值然后，第一帧的更新值用于更新其余帧，在跨帧注意力中注入图像提示有助于将图像提示的详细视觉特征转移到合成帧中，通过在不同尺度的不同交叉注意力层中进行细化

<img src="https://img.saraba1st.com/forum/202312/04/220631q78n1mhozi8tm9bh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231204-220301__01.jpg</strong> (739.97 KB, 下载次数: 0)

下载附件

2023-12-4 22:06 上传

定性对比，Video Booth有效保留了图像提示的保真度，实现了更好的视觉质量

<img src="https://img.saraba1st.com/forum/202312/04/220625myz1u8uu8z1s663t.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231204-220306__01.jpg</strong> (82.69 KB, 下载次数: 0)

下载附件

2023-12-4 22:06 上传

定量对比，VideoBooth实现了最佳的图像对齐和可比的文本对齐性能

<img src="https://img.saraba1st.com/forum/202312/04/220621qwk86obnarr4637b.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231204-220306__02.jpg</strong> (62.7 KB, 下载次数: 0)

下载附件

2023-12-4 22:06 上传

用户研究，VideoBooth在所有三个维度上都实现了最高的用户偏好比

<img src="https://img.saraba1st.com/forum/202312/04/220617hp4pplaf201qie55.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231204-220324__01.jpg</strong> (266.18 KB, 下载次数: 0)

下载附件

2023-12-4 22:06 上传

消融实验
(A)仅使用图像编码器的粗略嵌入，狗的身体生成的图案与图像提示不同
(B)由于注意力注入仅具有精细嵌入，因此缺乏用于注意力注入模块进行细化的狗的粗略编码，生成的狗在之后的合成帧中会扭曲
(C)统一训练降低了图像编码器的能力，因此狗也被扭曲了
(D)完整模型更好地保留了图像提示的所有视觉细节

<img src="https://img.saraba1st.com/forum/202312/04/220611vsui0usy7vr7u700.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231204-220324__02.jpg</strong> (54.39 KB, 下载次数: 0)

下载附件

2023-12-4 22:06 上传

消融实验，完整模型得分最高

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1022#       发表于 2023-12-5 03:05

 本帖最后由 Machinery 于 2023-12-5 03:06 编辑 

Merlin

以远见卓识增强多模态LLM

项目主页:https://ahnsun.github.io/merlin/

github项目代码仓库:https://github.com/Ahnsun/merlin

人类拥有根据当前的观察在一定程度上预见未来(foresee the future)的非凡能力，这被称之为远见思维(foresight minds)，然而，这种能力在现有的多模态大型语言模型(MLLM)中仍处于探索之中，这阻碍了它们学习事物如何运作的基本原理(fundamental principles of how things operate)以及观察隐藏在对象背后的意图的能力(intentions behind the observed subjects)

为了解决这个问题，通过将未来建模(future modeling)整合到MLLM现有的学习框架中，利用主题轨迹(subject trajectory)，一种连续帧序列(consecutive frame sequence)的高度结构化表征(highly structured representation)作为学习目标，目的是弥补过去与未来之间的差距

提出了两种创新方法来增强MLLM的远见思维，即远见预训练(FPT/Foresight Pre-Training)和远见指令调整(FIT/Foresight Instruction-Tuning)，其灵感来自于LLM的现代学习范式

具体来说，FPT联合训练多种以轨迹为中心的任务，使MLLM能够学习如何根据给定的初始观察来关注和预测整个轨迹，然后，FIT要求MLLM首先预测相关对象的轨迹，然后根据它们推理潜在的未来事件，在FPT和FIT的帮助下，构建了一个新颖且统一的MLLM，名为Merlin，它支持多图像输入和分析多个对象的潜在动作，以供未来推理

实验结果表明，Merlin具有强大的远见思维，在未来推理和视觉理解任务上都有令人印象深刻的表现

<img src="https://img.saraba1st.com/forum/202312/05/025930tzh474307h3p4ap7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-025058__01.jpg</strong> (658.79 KB, 下载次数: 0)

下载附件

2023-12-5 02:59 上传

Merlin的Demo演示案例，这里展示了Merlin的几个主要能力，值得注意的是，在对话中，用颜色标记的单词对应于图像中目标的轨迹输出，为了节省空间，使用相同的颜色突出显示它们

<img src="https://img.saraba1st.com/forum/202312/05/025951w87xrlx8xr4u9y98.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-025108__01.jpg</strong> (292.64 KB, 下载次数: 0)

下载附件

2023-12-5 02:59 上传

关于GPT-4V的未来推理失败案例

<img src="https://img.saraba1st.com/forum/202312/05/025957hbcydcdcd5pdfzkz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-025122__01.jpg</strong> (436.96 KB, 下载次数: 0)

下载附件

2023-12-5 02:59 上传

Merlin的整体工作流程，架构主要由三个组件组成:
(1)图像编码器
(2)大型语言模型
(3)模态对齐的投影器(modality-align projector)

上方:模型响应，包括预测轨迹和特征推理
下方:支持多图像上下文、初始观察和特定用户提示的多样化输入格式

<img src="https://img.saraba1st.com/forum/202312/05/030004dzhi8w5rqcmiziww.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-025131__01.jpg</strong> (232.38 KB, 下载次数: 0)

下载附件

2023-12-5 03:00 上传

用一个例子来说明多模态预训练数据集，顶部展示了提供的上下文，包括多个图像上下文和关于主题的初始观察(框、外观和动作)用以提示LLM，底部显示包括问题和答案的对话

<img src="https://img.saraba1st.com/forum/202312/05/030014g7mwrx38wg0x3s0x.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-025142__01.jpg</strong> (402.23 KB, 下载次数: 0)

下载附件

2023-12-5 03:00 上传

未来推理的有效性，从MMBench开发和测试集中分别选择5个指标，包括OL：对象定位、PPR：物理属性推理、FR：功能推理、IR：身份推理、FP：未来预测

最好和第二好的表现分别以粗体和下划线显示

<img src="https://img.saraba1st.com/forum/202312/05/030022tzu7qts3f09u7utl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-025147__01.jpg</strong> (127.08 KB, 下载次数: 0)

下载附件

2023-12-5 03:00 上传

Merlin与可用追踪方法的对比，值得注意的是，Merlin仅使用了相关跟踪数据集中的一小部分样本数据进行训练，而不是完整数据

<img src="https://img.saraba1st.com/forum/202312/05/030050t313nrrrish5rrnp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-025157__01.jpg</strong> (273.83 KB, 下载次数: 0)

下载附件

2023-12-5 03:00 上传

COCO验证集上的零样本物体幻觉评估，“yes”代表模型输出的正面答案的比例

<img src="https://img.saraba1st.com/forum/202312/05/030058mydqyimsws9essj2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-025203__01.jpg</strong> (148.35 KB, 下载次数: 0)

下载附件

2023-12-5 03:00 上传

在主要的MLLM基准测试上与SOTA方法进行对比，对于VQA任务，主要选择GQA和VisWiz来评估模型； 对于通常评估，主要选择MMBench和MM-Vet

†为使用不可公开访问的内部数据

<img src="https://img.saraba1st.com/forum/202312/05/030343p9utofucsuuza6tu.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-025210__01.jpg</strong> (267.41 KB, 下载次数: 0)

下载附件

2023-12-5 03:03 上传

注意力图可视化，为了便于观察，将注意力映射到了每帧的框响应和视觉Token之间以进行可视化

<img src="https://img.saraba1st.com/forum/202312/05/030458jcrpje661jbuferc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-025216__01.jpg</strong> (80.12 KB, 下载次数: 0)

下载附件

2023-12-5 03:04 上传

关于Merlin中提出的策略的消融实验
(ITP：图像文本对数据，ITD：指令调整数据)，主要报告GOT10k的AO分数和未来推理的平均分数

<img src="https://img.saraba1st.com/forum/202312/05/030503qhw92ubdiwdjjz7d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-025227__01.jpg</strong> (256.2 KB, 下载次数: 0)

下载附件

2023-12-5 03:05 上传

所有训练数据

Cap.:Captioning、Ref.:Referring(包含REC、REG和Referring Tracking)、Det.: Detection、Track:Tracking(包括单对象跟踪/SOT和多对象跟踪/MOT)、Rea.:Reasoning ，Dia.:Dialogue

*表示该数据仅在SFT阶段使用

<img src="https://img.saraba1st.com/forum/202312/05/030511d4ccxqcq1syzix1m.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-025241__01.jpg</strong> (506.77 KB, 下载次数: 0)

下载附件

2023-12-5 03:05 上传

数据格式可视化，在训练中，使用了涉及多个任务的数据集，为了说明这些数据集的结构，从每个数据集中选择了一个示例，值得一提的是，所有关于框的信息都已调整为1000的标准范围，在示例中，问题以黑色文本显示，答案以蓝色文本显示，负样本以红色文本显示

<img src="https://img.saraba1st.com/forum/202312/05/030520txx2zoooz1noiq3i.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-025252__01.jpg</strong> (110.96 KB, 下载次数: 0)

下载附件

2023-12-5 03:05 上传

Merlin的训练超参数，位于中间的超参数表示该超参数在两个阶段中都使用

<img src="https://img.saraba1st.com/forum/202312/05/030525rccc7onnogty9yby.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-025403__01.jpg</strong> (22.1 KB, 下载次数: 0)

下载附件

2023-12-5 03:05 上传

具有(w)和不具有(w/o)精确任务描述的Merlin之间的对比，主要报告了GOT10K的AO分数和未来推理的平均分数

<img src="https://img.saraba1st.com/forum/202312/05/030531oxev2ep4y8kguz4f.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-025412__01.jpg</strong> (299.34 KB, 下载次数: 0)

下载附件

2023-12-5 03:05 上传

在图像级任务中使用Merlin进行更多对话可视化，展示了Merlin熟练处理各种图像级任务的其他示例，包括通常检测、开放词汇检测(OV-Detection)、指称表达理解(REC)、指称表达生成(REG)和关系推理

<img src="https://img.saraba1st.com/forum/202312/05/030539uz0qkajzzwqjqqa1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-025423__01.jpg</strong> (308.57 KB, 下载次数: 0)

下载附件

2023-12-5 03:05 上传

在视频级任务中使用Merlin进行更多对话可视化，展示了Merlin熟练处理各种视频级任务的其他示例，包括通常追踪、视频引用表达理解(Video REC)和视频引用表达生成(Video REG)

<img src="https://img.saraba1st.com/forum/202312/05/030544ah5dp60pi15elq0d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-025430__01.jpg</strong> (288.03 KB, 下载次数: 0)

下载附件

2023-12-5 03:05 上传

使用Merlin进行更多未来推理对话可视化

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1023#       发表于 2023-12-5 13:44

 本帖最后由 Machinery 于 2023-12-5 13:45 编辑 

Mamba

选择性状态空间的线性时间(Linear-Time)序列建模方法

github项目代码仓库:https://github.com/state-spaces/mamba

相关介绍文章:https://mp.weixin.qq.com/s?__biz=MzI3MTA0MTk1MA==&amp;mid=2652414828&amp;idx=1&amp;sn=401e5e7adcf037a2c1b4167e8b616d5b

基础模型现在已经成为深度学习中大多数令人兴奋的应用程序的核心支持组件，同时几乎普遍基于Transformer架构及其核心的注意力模块，许多的次二次时间(subquadratic-time)架构，例如线性注意力(linear attention)、门控卷积(gated convolution)和循环模型(recurrent models)以及结构化状态空间模型(SSM/structured state space models)已被开发出来，用以解决Transformer在长序列上的计算效率低下问题，但它们在重要模态下，例如语言的关注不足

此类模型的一个关键弱点是它们无法执行基于内容的推理，并进行了一些改进，首先，简单地让SSM参数作为输入的函数，可以解决其离散模态的弱点，允许模型根据当前Token选择性地沿序列长度维度传播或遗忘信息，其次，尽管这种变化阻止了高效卷积的使用，但通过在循环模式(recurrent mode)下设计了一种硬件感知的并行算法，将这些选择性SSM集成到简化的端到端神经网络架构中，无需注意力机制，甚至不需要MLP模块，Mamba拥有快速推理(吞吐量比Transformer高5倍)和序列长度线性缩放，并且其性能可以在高达百万长度序列的实际数据上继续得到提高

作为通用序列模型骨干，Mamba在语言、音频和基因等多种模态上实现了SOTA性能，在语言建模方面，Mamba-3B模型在预训练和下游评估方面都优于相同大小的Transformer，并且可以与两倍大小的Transformer性能相匹配

github说明页:

<img src="https://img.saraba1st.com/forum/202312/05/134429w75ugd5dpdxcyccr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-134109.jpg</strong> (162.99 KB, 下载次数: 0)

下载附件

2023-12-5 13:44 上传

<img src="https://img.saraba1st.com/forum/202312/05/134429fdaz69eshqbbzsvb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-134130.jpg</strong> (114.19 KB, 下载次数: 0)

下载附件

2023-12-5 13:44 上传

<img src="https://img.saraba1st.com/forum/202312/05/134429u8vzvxcwr6n1n11n.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-134138.jpg</strong> (263.76 KB, 下载次数: 0)

下载附件

2023-12-5 13:44 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1024#       发表于 2023-12-5 19:36

 本帖最后由 Machinery 于 2023-12-5 19:38 编辑 

StyleCrafter

使用样式适配器(Style Adapter)增强风格化的文本到视频的生成

项目主页:https://gongyeliu.github.io/StyleCrafter.github.io/

github项目仓库:https://github.com/GongyeLiu/StyleCrafter

文本到视频(T2V/Text-to-video)模型在生成多样化视频方面表现出了卓越的能力，然而，由于(i)文本固有的不足，很难表达特定风格以及(ii)风格保真度的普遍下降，致使用户很难制作渴望的风格化视频

为了应对这些挑战，本文引入了StyleCrafter，一种通用方法，可以通过风格控制适配器增强预训练的T2V模型，通过提供参考图像来生成任何风格的视频

考虑到风格化视频数据集的稀缺性，首先使用风格丰富的图像数据集训练风格控制适配器(style control adapter)，然后通过定制的微调范式将学习到的风格化能力转移到视频生成，为了促进内容与风格的解耦，还从文本提示中删除了风格描述，并使用解耦学习策略(decoupling learning strategy)仅从参考图像中提取风格信息

此外，设计了一个尺度自适应的融合模块来平衡基于文本的内容特征和基于图像的风格特征的影响，这有助于泛化各种文本和风格组合，StyleCrafter有效生成了高质量的风格化视频，这些视频与文本内容一致并类似于参考图像的风格

实验表明，本文方法比现有的其他竞争方法更加灵活和高效

<img src="https://img.saraba1st.com/forum/202312/05/193137qugaygcustdbywba.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-192454__01.jpg</strong> (416.96 KB, 下载次数: 0)

下载附件

2023-12-5 19:31 上传

将样式适配器添加到T2V模型的效果
(a)和(b)分别是Stable Diffusion和VideoCrafter的结果
(c)是配备风格适配器的VideoCrafter的结果，内容文字提示为“A knight riding a horse through the field”
对于(a)和(b)，风格提示是使用GPT4V从风格图像生成的

<img src="https://img.saraba1st.com/forum/202312/05/193144jqfcj6fqc26g24q4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-192508__01.jpg</strong> (241.86 KB, 下载次数: 0)

下载附件

2023-12-5 19:31 上传

提案的风格适配器的概览图，它由三个组件组成，即风格特征提取器(style feature extractor)、双交叉注意力模块(dual cross-attention module)和上下文感知的缩放系数预测器(context-aware scale factor predictor)

<img src="https://img.saraba1st.com/forum/202312/05/193150r1qzdygmmuvygjpc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-192521__01.jpg</strong> (166.25 KB, 下载次数: 0)

下载附件

2023-12-5 19:31 上传

跨越多个输入对(input pairs)的内容风格融合缩放系数的图示，随机选择4个提示id ∈ [0, 3]的短提示(小于5个单词)和4个提示id ∈ [4, 7]的长提示(大于8个单词)，结果表明，较短的提示和具有丰富样式语义的图像往往具有相对较高的缩放系数

<img src="https://img.saraba1st.com/forum/202312/05/193321egnbbxqv4244xvq3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-192536__01__01__01__01.jpg</strong> (540.95 KB, 下载次数: 0)

下载附件

2023-12-5 19:33 上传

<img src="https://img.saraba1st.com/forum/202312/05/193321axwh34fqpco3fppq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-192536__01__01__01__02.jpg</strong> (574.8 KB, 下载次数: 0)

下载附件

2023-12-5 19:33 上传

风格引导的T2I生成的视觉对比
所有方法都使用四种风格和三种内容文本进行测试:(i) A person jogging along a scenic trail; (ii) A colorful butterfly resting on a flower; (iii) An ancient temple surrounded by lush vegetation.

<img src="https://img.saraba1st.com/forum/202312/05/193331d4bov42o9zfof49r.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-192546__01.jpg</strong> (48.58 KB, 下载次数: 0)

下载附件

2023-12-5 19:33 上传

单参考风格引导的T2I生成的定量对比，在400对测试集上评估了文本对齐(Text)和风格一致性(Style)的CLIP分数，粗体是最好的结果

<img src="https://img.saraba1st.com/forum/202312/05/193340r57965li22li67rl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-192554__01.jpg</strong> (809.45 KB, 下载次数: 0)

下载附件

2023-12-5 19:33 上传

对风格样式和文本提示的单参考风格引导T2V生成结果进行定性比较

<img src="https://img.saraba1st.com/forum/202312/05/193345fprw7fwopuugcb2d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-192602__01__01.jpg</strong> (70.6 KB, 下载次数: 0)

下载附件

2023-12-5 19:33 上传

风格引导的T2V生成的定量对比，在240对测试集上评估了图像文本对齐(Text)、样式一致性(Style)和时间质量(Temporal)的CLIP分数和用户偏好，粗体是最好的结果
Vid.Com.: VideoComposer, Vid.Craf.: VideoCrafter

<img src="https://img.saraba1st.com/forum/202312/05/193352jhf0n5mehmf5e00o.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-192612__01.jpg</strong> (774.23 KB, 下载次数: 0)

下载附件

2023-12-5 19:33 上传

多参考风格引导的T2V生成在各种风格和文本提示上的定性对比

<img src="https://img.saraba1st.com/forum/202312/05/193358c114zg0gm6gm1u85.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-192619__01.jpg</strong> (83.87 KB, 下载次数: 0)

下载附件

2023-12-5 19:33 上传

多参考风格引导的T2V生成的定量对比，在60对测试集上评估了图像文本对齐(Text)、风格一致性(Style)和时间质量(Temporal)的CLIP分数和用户偏好，粗体是最好的结果
S-R:单参考了/Single-Reference，M-R:多参考/Multi-Reference

<img src="https://img.saraba1st.com/forum/202312/05/193846lge1x2952s2bo2g4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-193749.jpg</strong> (59.14 KB, 下载次数: 0)

下载附件

2023-12-5 19:38 上传

风格调制设计的消融实验，性能是根据风格引导的T2I生成进行评估的

<img src="https://img.saraba1st.com/forum/202312/05/193516l35jn13q1ojj36h4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-192640__01.jpg</strong> (179.13 KB, 下载次数: 0)

下载附件

2023-12-5 19:35 上传

双交叉注意力和数据增强效果的视觉对比，消除双交叉注意力往往会融合参考图像中的内容，而不使用数据增强则无法捕获“3D render”风格特征

<img src="https://img.saraba1st.com/forum/202312/05/193545r3nv0pqpvnaguzj0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-192644__01.jpg</strong> (199.16 KB, 下载次数: 0)

下载附件

2023-12-5 19:35 上传

适配内容风格融合的视觉检查效果，它在泛化方面表现出对极端用例输入情况的优越性，例如长文本描述，使用两个文本提示:(i) A little girl; (ii) A little girl reading a book in the park, with a telescope nearby pointed at the sky.

<img src="https://img.saraba1st.com/forum/202312/05/193600ubg8gtcgwxwhcycg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-192640__02.jpg</strong> (48.18 KB, 下载次数: 0)

下载附件

2023-12-5 19:36 上传

两阶段训练计划的消融实验

<img src="https://img.saraba1st.com/forum/202312/05/193613t8dqe3ed7ns8srrt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231205-192640__03.jpg</strong> (233.76 KB, 下载次数: 0)

下载附件

2023-12-5 19:36 上传

不同训练方案的效果对比  

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  2624135228  
##### 1025#       发表于 2023-12-5 23:14

wat


*****

####  Machinery  
##### 1026#       发表于 2023-12-6 03:26

Magicoder

源代码就是您所需要的

github项目主页:https://github.com/ise-uiuc/magicoder

Magicoder，一系列的完全开源(代码、权重和数据)代码大型语言模型(LLM)，可显著缩小与顶级代码模型的差距，同时参数不超过7B

Magicoder模型使用OSS-Instruct在75K合成指令数据上进行训练，这是一种利用开源代码片段(open-source code snippets)启发LLM以生成高质量代码指令数据的新方法，主要动机是通过为LLM提供丰富的开源参考资料来生成更多样化、更真实、更可控的数据，从而减轻LLM生成的合成数据的固有偏差

OSS-Instruct和其他数据生成方法(如Evol-Instruct)的正交性(orthogonality)使之能够进一步构建增强的MagicoderS，Magicoder和MagicoderS在各种编码基准测试(包括Python文本到代码生成、多语言编码和数据科学编程代码完成)上都远远优于相似甚至更大尺寸的SOTA代码模型

值得注意的是，基于CodeLlama的MagicoderS-CL-7B甚至超过了HumanEval+上著名的ChatGPT(pass@1准确率66.5对比65.9)，总体而言，OSS-Instruct利用丰富的开源参考为低偏差的高质量指令调整开辟了新方向

<img src="https://img.saraba1st.com/forum/202312/06/032523tp5gf5cmpm5uggzk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-032037__01.jpg</strong> (425.81 KB, 下载次数: 0)

下载附件

2023-12-6 03:25 上传

OSS-INSTRUCT概览，以及其他不同LLM在HumanEval(+)上的pass@1结果

<img src="https://img.saraba1st.com/forum/202312/06/032527j1n0xnnwf09xxqwf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-032045__01.jpg</strong> (346.6 KB, 下载次数: 0)

下载附件

2023-12-6 03:25 上传

OSS-INSTRUCT的详细提示设计

<img src="https://img.saraba1st.com/forum/202312/06/032532k5zmwugmyhm55ygu.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-032110__01.jpg</strong> (262.9 KB, 下载次数: 0)

下载附件

2023-12-6 03:25 上传

展示了OSS-INSTRUCT如何从种子代码片段生成问题和解决方案的示例，为了简洁起见，省略了完整的问题要求、完整的实现和解释等细节

<img src="https://img.saraba1st.com/forum/202312/06/032537jlwz8hhawqap22ut.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-032118__01.jpg</strong> (116.96 KB, 下载次数: 0)

下载附件

2023-12-6 03:25 上传

OSS-INSTRUCT的类别构成

<img src="https://img.saraba1st.com/forum/202312/06/032542bb18ha4mmh3hgb1u.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-032118__02.jpg</strong> (53.68 KB, 下载次数: 0)

下载附件

2023-12-6 03:25 上传

OSS-INSTRUCT生成的问题和解决方案的Token计数分布

<img src="https://img.saraba1st.com/forum/202312/06/032550orufsjnczd95unnw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-032118__03.jpg</strong> (70.56 KB, 下载次数: 0)

下载附件

2023-12-6 03:25 上传

HumanEval与不同数据生成方法之间的余弦相似度对比

<img src="https://img.saraba1st.com/forum/202312/06/032554hbb8744l4l86dl4l.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-032132__01.jpg</strong> (404.58 KB, 下载次数: 0)

下载附件

2023-12-6 03:25 上传

通过贪婪解码计算的HumanEval(+)和MBPP(+)数据集上不同LLM的Pass@1百分比结果，缩写“CL”和“SC”分别指代基本模型CODELLAMA-PYTHON和StarCoder，报告的结果与EvalPlus排行榜一致

<img src="https://img.saraba1st.com/forum/202312/06/032558qc5iifriiejr77o5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-032140__01.jpg</strong> (239.75 KB, 下载次数: 0)

下载附件

2023-12-6 03:25 上传

按照WizardCoder论文相同的超参数设置，在MultiPL-E上评估的不同LLM的Pass@1结果：temperature=0.2，top_p=0.95，max_length=512，num_samples=50，使用bigcode-evaluation-harness评估了所有的7B模型，并报告了WizardCoder论文中的其他结果

<img src="https://img.saraba1st.com/forum/202312/06/032602qhomqo9j9gc5azkq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-032148__01.jpg</strong> (239.26 KB, 下载次数: 0)

下载附件

2023-12-6 03:26 上传

DS-1000上的Pass@1结果(补完格式)，temperature=0.2、top_p=0.5、max_length=1024、num_samples=40，遵循WizardCoder论文中使用的相同超参数设置，使用其首选的提示格式评估所有的7B模型，并报告了WizardCoder的其他结果

<img src="https://img.saraba1st.com/forum/202312/06/032607s66mjsjrdyxq4qij.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-032152__01.jpg</strong> (187.99 KB, 下载次数: 0)

下载附件

2023-12-6 03:26 上传

Magicoder和DeepSeek-Coder在HumanEval(+)和MBPP(+)上的Pass@1(贪婪解码)对比，DeepSeek-Coder结果由EvalPlus排行榜报告

<img src="https://img.saraba1st.com/forum/202312/06/032611xettrmwhootpbra8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-032159__01.jpg</strong> (98.98 KB, 下载次数: 0)

下载附件

2023-12-6 03:26 上传

使用不同编程语言作为训练数据的消融实验，展示了Python的HumanEval+上的Pass@1结果以及表2中使用的同一组编程语言的MultiPL-E上的平均Pass@1结果(即Java、JavaScript、C++、PHP、Swift和Rust)，所有变体都经过2个epoch的微调，并通过贪婪解码进行评估

<img src="https://img.saraba1st.com/forum/202312/06/032616ioyowkoowtg6gox5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-032159__02.jpg</strong> (59.9 KB, 下载次数: 0)

下载附件

2023-12-6 03:26 上传

以CODELLAMA-PYTHON-7B为基础模型的情况下的OSS-INSTRUCT与直接对comment-function对(pairs)进行微调的对比

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1027#       发表于 2023-12-6 04:08

RLHF-V

从细粒度的矫正人类反馈(Fine-grained Correctional Human Feedback)进行行为对齐(Behavior Alignment)从而迈向值得信赖的MLLM

项目主页:https://rlhf-v.github.io

github项目主页:https://github.com/RLHF-V/RLHF-V

多模态大语言模型(MLLM)最近在多模态理解、推理和交互方面表现出了令人印象深刻的能力，然而，现有的MLLM普遍存在严重的幻觉问题，生成的文本实际上并不基于相关图像，这个问题使得现有的MLLM并不值得信任，因此在现实世界(尤其是高风险)应用的想法不切实际

为了应对这一挑战，本文提出了RLHF-V，它通过细粒度的矫正人类反馈的行为对齐来增强MLLM的可信度，具体来说，RLHF-V以对幻觉进行分段级校正(segment-level corrections)的形式收集人类偏好，并对人类反馈进行密集的直接偏好优化(direct preference optimization)

对自动和人工评估中的五个基准测试的综合实验表明，RLHF-V可以实现更值得信赖的MLLM行为，并具有良好的数据和计算效率，值得注意的是，在只使用1.4k个带标注的数据样本的情况下，RLHF-V将基础MLLM的幻觉率显著降低了34.8%，优于在10k个带标注数据上训练的并发LLaVA-RLHF，其最终模型在开源MLLM中的可信度方面达到了SOTA性能，并且在防止过度泛化引起的幻觉方面表现出了比GPT-4V更好的稳健性

<img src="https://img.saraba1st.com/forum/202312/06/040808zky21yp3c48m5r31.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-040529__01.jpg</strong> (361.42 KB, 下载次数: 0)

下载附件

2023-12-6 04:08 上传

用于根据人类反馈调整MLLM行为的RLHF-V框架
(1)给定输入图像和提示，从MLLM获得输出，并从幻觉的细粒度分段级校正的形式收集人类反馈
(2)在人类偏好学习过程中，对细粒度的矫正人类反馈进行密集的直接偏好优化

<img src="https://img.saraba1st.com/forum/202312/06/040812cbzc7szunh72hnzw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-040544__01.jpg</strong> (279.68 KB, 下载次数: 0)

下载附件

2023-12-6 04:08 上传

关于幻觉的主要实验结果，报告了不同粒度的幻觉率，包括响应级/response-level(Resp.)和提及级/mention-level(Mention)，以及不同类型的响应级/response-level幻觉率，还展示了信息/informativeness(Info.)、多模态对话/multimodal conversation(Conv.)、详细描述/detailed description(Detail)和复杂推理/complex reasoning(Comp.)方面的分数
*表示VQAv2.2上的零样本结果，最好和第二好的开源结果分别以粗体和下划线显示

<img src="https://img.saraba1st.com/forum/202312/06/040816opcp8es0cazsd5x5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-040555__01.jpg</strong> (201.46 KB, 下载次数: 0)

下载附件

2023-12-6 04:08 上传

Object HalBench上的过度泛化产生幻觉的实验结果，对于每个场景，报告了在完整基准测试(Ha)和场景下(Hs)的top-10常见物体的平均幻觉率，为了简洁起见，为每个场景列出了最常见的6个对象
Δ:幻觉率差异，Δ:跨越场景的平均差异

<img src="https://img.saraba1st.com/forum/202312/06/040820ethwjgwzuwl9bu6h.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-040559__01.jpg</strong> (111.89 KB, 下载次数: 0)

下载附件

2023-12-6 04:08 上传

MHumanEval(所有类型)上的相对于偏好数据量的幻觉率和数量，报告了在不同RLHF数据上训练的不同模型的结果

<img src="https://img.saraba1st.com/forum/202312/06/040825xr0y300gba0aakg2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-040604__01.jpg</strong> (84.69 KB, 下载次数: 0)

下载附件

2023-12-6 04:08 上传

不同组件的消融实验，MHB:MMHal-Bench，IT-VQA:VQAv2上的指令调整，untrust aug.:不可信的数据增强

<img src="https://img.saraba1st.com/forum/202312/06/040841ng53shddrzxd63gy.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-040616__01.jpg</strong> (680.97 KB, 下载次数: 0)

下载附件

2023-12-6 04:08 上传

不同模型在短式QA和长式QA上的定性结果，正确答案、不能推理的延伸和幻觉分别用颜色突出显示

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1028#       发表于 2023-12-6 04:44

re-align

基础LLM的解锁咒语：通过上下文学习重新思考对齐

项目主页:https://allenai.github.io/re-align/

github项目仓库:https://github.com/Re-Align/urial

just eval项目主页:https://github.com/Re-Align/just-eval

数据集下载:https://huggingface.co/datasets/re-align/just-eval-instruct

大型语言模型(LLM)的对齐调整过程通常涉及通过监督微调(SFT)进行指令学习以及通过人类反馈强化学习(RLHF)进行偏好调整，最近的一项研究LIMA表明，仅使用1K个示例进行SFT也可以实现显著的对齐性能，这表明对齐调整的效果可能是“浅显的(superficial)”，这引发了关于对齐调整如何准确地转换基础LLM的问题

通过检查基础LLM以及对应的对齐版本之间的Token分布转移来分析了对齐调整的效果，研究结果表明，基础LLM及其对齐调整版本在大多数Token位置的解码中表现几乎相同，而大多数分布转移都与风格化Token(stylistic tokens)有关，这些直接证据有力地支持了LIMA提出的表面对齐假说(Superficial Alignment Hypothesis)

基于这些发现，通过提出研究问题来重新思考LLM的调整:在没有SFT或RLHF的情况下，我们该如何有效地调整基础LLM？ 

为了解决这个问题，引入了一种简单的、免调整的对齐方法，名为URIAL，URIAL通过纯粹的与基础LLM的上下文学习 (ICL/in-context learning)实现有效的协调，只需要三个恒定的风格化示例(three constant stylistic examples)和一个系统提示(system prompt)

对一组不同的示例进行细粒度且可解释的评估，使用名为JUST-EVAL-INSTRUCT的评估结果表明，基于URIAL的基础LLM可以匹配甚至超过使用SFT或SFT+RLHF的LLM的表现，这表明，通过策略提示和ICL，可以显著缩小免调整和基于调整的对齐方法之间的差距

对齐调整的表面性质的发现以及URIAL的结果表明，对对齐的更深入分析和理论理解对于未来的LLM研究至关重要

<img src="https://img.saraba1st.com/forum/202312/06/044410ajesf4fvf7k23vke.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-044054__01.jpg</strong> (193.49 KB, 下载次数: 0)

下载附件

2023-12-6 04:44 上传

不同方面的对齐性能对比

<img src="https://img.saraba1st.com/forum/202312/06/044417k156v6dnz8gy46wd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-044107__01.jpg</strong> (554.18 KB, 下载次数: 0)

下载附件

2023-12-6 04:44 上传

分析与Token分布转移的对齐，对齐的LLM(llama-2-chat)接收查询q并输出响应o，为了分析对齐调整的效果，在每个位置t处解码未调整的版本(llama-2-base)，接下来，根据ot在基本LLM概率排序Token列表中的排名，将o中的所有标记分为三组，平均而言，77.7%的Token也在基础LLM排名top-1(未转移位置)，92.2%位于top-3(+边缘)，移动位置上的常见Token显示在右上角，并且大多是风格化的构成话语Token，相比之下，知识密集型Token主要出现在未移动的位置

<img src="https://img.saraba1st.com/forum/202312/06/044422qs4wzhsww9xhdhjd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-044117__01.jpg</strong> (449.89 KB, 下载次数: 0)

下载附件

2023-12-6 04:44 上传

三对基础VS对齐的LLM的Token分布变化，未转移、边缘和转移Token的比率用彩色表示(%)

<img src="https://img.saraba1st.com/forum/202312/06/044427hs2satpap1s2w21v.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-044142__01.jpg</strong> (340.3 KB, 下载次数: 0)

下载附件

2023-12-6 04:44 上传

在解码过程中，Token分布变化随着时间的推移而减少

<img src="https://img.saraba1st.com/forum/202312/06/044435bznfnulvl7nks3kk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-044152__01.jpg</strong> (759.74 KB, 下载次数: 0)

下载附件

2023-12-6 04:44 上传

免调整对齐方法，零样本提示使用模板化前缀从基础LLM中引出答案，原生(Vanilla)上下文学习(ICL)在提示中采用了一些指令输出示例，基于检索的ICL从外部数据集中检索相似的示例，因此该方法的提示会针对每个推理用例动态更改，URIAL像原生ICL一样使用静态提示，但添加了系统级提示并重新设计了上下文示例的输出部分

<img src="https://img.saraba1st.com/forum/202312/06/044439xboc1obb9zehzxl6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-044205__01.jpg</strong> (228.52 KB, 下载次数: 0)

下载附件

2023-12-6 04:44 上传

8个just-eval-instruct数据的统计，(a)显示了9个子集中的示例分布，(b)和(c)分别显示了任务类型和主题的类别分布

<img src="https://img.saraba1st.com/forum/202312/06/044444g3d33t23uetd5wdi.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-044214__01.jpg</strong> (558.54 KB, 下载次数: 0)

下载附件

2023-12-6 04:44 上传

对8个just-eval-instruct的对齐方法进行多方面评分评估，分数的范围为1-5，长度根据单词数计算，图标实心表示模型已通过SFT或RLHF进行调整，而空心表示模型未调整

<img src="https://img.saraba1st.com/forum/202312/06/044450uugkg50htbdgwtut.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-044222__01.jpg</strong> (364.13 KB, 下载次数: 0)

下载附件

2023-12-6 04:44 上传

对不同任务和主题的对齐进行分类性能分析

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1029#       发表于 2023-12-6 05:20

segment caption anything

分割与字幕说明任何东西(Segment and Caption Anything)

项目主页:https://xk-huang.github.io/segment-caption-anything/

github项目主页:https://github.com/xk-huang/segment-caption-anything

演示Demo:https://github.com/xk-huang/segment-caption-anything/blob/main/docs/DEMO.md

提出了一种有效地为SAM模型(Segment Anything Model)配备生成区域级字幕说明能力的方法，SAM具有很强的通用性，可以对任何事物进行分割，但对于语义理解来说却有短处

通过引入轻量级的基于查询的特征混合器(lightweight query-based feature mixer)，将特定于区域的特征与语言模型的嵌入空间对齐以供之后的字幕说明生成使用，由于可训练参数的数量很少(通常为数千万)，因此计算成本、显存使用量和通信带宽都较少，从而实现了快速且可扩展的训练

为了解决区域字幕数据的稀缺问题，首先在对象检测和分割任务上预训练了本文模型，将此步骤称为弱监督预训练(weak supervision pretraining)，因为预训练数据仅包含类别名称而不是完整的句子描述，弱监督预训练使之能够利用许多公开可用的对象检测和分割数据集

进行的大量的实验证明了本文方法的优越性并验证了每个设计选择，这项工作是扩大区域字幕说明数据的垫脚石，并有助于探索利用区域语义增强SAM的有效方法

<img src="https://img.saraba1st.com/forum/202312/06/051941j957knhsk71km3s7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-051719__01.jpg</strong> (222.55 KB, 下载次数: 0)

下载附件

2023-12-6 05:19 上传

SCA(b)是SAM(a)的轻量级增强，能够生成区域字幕，通过在SAM架构之上添加了一个预训练的冻结语言模型和一个轻量级的混合特征混合器，尽管可训练参数数量较少，但通过学习特定区域的特征以与语言模型的嵌入空间保持对齐从而进行区域字幕生成

<img src="https://img.saraba1st.com/forum/202312/06/051945w9sk9ylyv8s9yr9y.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-051729__01.jpg</strong> (272.92 KB, 下载次数: 0)

下载附件

2023-12-6 05:19 上传

模型架构，该模型由三部分组成，包括图像编码器、特征混合器和用于掩码或文本的解码器头，该模型的关键组成部分是文本特征混合器，它是一个轻量级的双向Transformer，将其堆叠在SAM的Token之上并重用其令牌，通过单独优化附加混合器，将特定于区域的特征与语言模型的嵌入空间对齐，由于可优化参数数量有限，训练既快速又可扩展

<img src="https://img.saraba1st.com/forum/202312/06/051951qg365sff4z5lya8g.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-051748__01.jpg</strong> (515.85 KB, 下载次数: 0)

下载附件

2023-12-6 05:19 上传

与基线对比

“C”:CIDEr-D、“M”:METEOR、“S”:SPICE、“B”:BLEU、“R”:ROUGE、“F”:Fuzzy

对于所有指标来说，数值越高越好，最好、第二、第三好成绩分别标记为红色、橙色、黄色

*:[86]中使用的字幕说明
†:对模型进行了100K步的预训练，然后在VG上对其进行100K步的微调
‡:当不应用任何预训练时，在VG上训练模型200K步，因此他们的训练成本相似

<img src="https://img.saraba1st.com/forum/202312/06/052003gvejapjjaekjj7aj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-051809__01.jpg</strong> (658.62 KB, 下载次数: 0)

下载附件

2023-12-6 05:20 上传

定性结果，SCA同时预测掩码(红色轮廓)和标题，从上到下，字幕说明来自：SAM+Captioner {GIT-large、BLIP-large、BLIP2-OPT-2.7B}、GRIT、SCA {GPT2-large+VG、LLAMA-3B+VG，GPT2-large+Pretrain+VG}，以及基准答案，边界框(红色)用于提示(prompt)模型

<img src="https://img.saraba1st.com/forum/202312/06/052013pd0aim1ykhp91ak0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-051614.jpg</strong> (204.7 KB, 下载次数: 0)

下载附件

2023-12-6 05:20 上传

<img src="https://img.saraba1st.com/forum/202312/06/052013iac995sc4zxr4v5f.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-051640.jpg</strong> (129.39 KB, 下载次数: 0)

下载附件

2023-12-6 05:20 上传

消融实验

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1030#       发表于 2023-12-6 06:06

DiffiT

用于图像生成的扩散视觉Transformers

github项目主页:https://github.com/NVlabs/DiffiT

扩散模型以其强大的表现力和高样本质量，在各个领域实现了许多新的应用程序和用例，对于样本生成，这些模型通常依赖于通过迭代去噪生成图像的去噪神经网络(denoising neural network)，然而，去噪网络架构的作用尚未得到充分研究，其中大多数工作都依赖于卷积残差U-Net(convolutional residual U-Nets)

在本文中，研究了视觉Transformer在基于扩散的生成学习中的有效性，具体来说，提出了一种新模型，称为扩散视觉Transformer(DiffiT/Diffusion Vision Transformers)，它由带有U形编码器和解码器(U-shaped encoder and decoder)的混合分层架构组成(hybrid hierarchical architecture)

还引入了一种新颖的时间相关自注意力模块(time-dependent self-attention module)，该模块允许注意力层以有效的方式在去噪过程中的不同阶段调整其行为

还引入了潜在DiffiT(latent DiffiT)，它由带有所提出的自注意力层的Transformer模型组成，用于高分辨率图像生成

结果表明，DiffiT在生成高保真图像方面出奇地有效，并且它在各种分类条件(class-conditional)和无条件合成(unconditional synthesis tasks)任务上实现了SOTA基准，在潜在空间中，DiffiT在ImageNet-256数据集上取得了新的SOTA FID分数(1.73)

<img src="https://img.saraba1st.com/forum/202312/06/060511c7hp44bhfbblf9bl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-055945__01.jpg</strong> (669.14 KB, 下载次数: 0)

下载附件

2023-12-6 06:05 上传

由潜在DiffiT在ImageNet数据集上生成的未整理的图像

<img src="https://img.saraba1st.com/forum/202312/06/060520j79a6e16iz46i3ht.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-055953__01.jpg</strong> (259.76 KB, 下载次数: 0)

下载附件

2023-12-6 06:05 上传

图像空间DiffiT模型概览图，Downsample和Upsample分别表示卷积下采样和上采样层

<img src="https://img.saraba1st.com/forum/202312/06/060529pibbn0ei8x110ece.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-060000__01.jpg</strong> (70.27 KB, 下载次数: 0)

下载附件

2023-12-6 06:05 上传

DiffiT Transformer Block将它们组合在一起形成每个Token的查询、键和值向量，再对空间和时间嵌入Token应用线性投影，然后使用这些向量来计算多头自注意力激活(multi-head self-attention activations)，然后是两个线性层

<img src="https://img.saraba1st.com/forum/202312/06/060534b4qrzxmirqyrnsq1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-060014__01.jpg</strong> (89.42 KB, 下载次数: 0)

下载附件

2023-12-6 06:05 上传

潜在DiffiT框架概览图

<img src="https://img.saraba1st.com/forum/202312/06/060540q1hvh8gnp1qg3vsq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-060014__02.jpg</strong> (167.85 KB, 下载次数: 0)

下载附件

2023-12-6 06:05 上传

在CIFAR10、FFHQ-64数据集上与各种生成方法进行FID性能对比，VP和VE分别表示Variance Preserving和Variance Exploding，DiffiT的性能优于竞争方法，有时更是大幅领先

<img src="https://img.saraba1st.com/forum/202312/06/060546j9tqt88kvvjycuyu.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-060035__01.jpg</strong> (459.83 KB, 下载次数: 0)

下载附件

2023-12-6 06:05 上传

FFHQ-64数据集的未整理生成图像的可视化

<img src="https://img.saraba1st.com/forum/202312/06/060551pffto8hbx9hcbcx7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-060041__01.jpg</strong> (336.2 KB, 下载次数: 0)

下载附件

2023-12-6 06:05 上传

在ImageNet-256和ImageNet-512数据集上将图像生成性能与最先进的模型进行对比，潜在DiffiT模型在ImageNet-256数据集上的FID分数实现了SOTA性能

<img src="https://img.saraba1st.com/forum/202312/06/060556bto2yohouvu2nxc5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-060047__01.jpg</strong> (52.92 KB, 下载次数: 0)

下载附件

2023-12-6 06:05 上传

时间和特征维度有效性的消融实验

<img src="https://img.saraba1st.com/forum/202312/06/060600ab3g4em3db6pw4wp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-060102__01.jpg</strong> (594.02 KB, 下载次数: 0)

下载附件

2023-12-6 06:06 上传

通过潜在DiffiT模型在ImageNet-256和ImageNet-512数据集上可视化未整理的生成图像

<img src="https://img.saraba1st.com/forum/202312/06/060605m1xirx2mljjx5ay8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-060107__01.jpg</strong> (58.58 KB, 下载次数: 0)

下载附件

2023-12-6 06:06 上传

编码器和解码器架构有效性的消融实验

<img src="https://img.saraba1st.com/forum/202312/06/060609aokri73ksbskicop.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-060107__02.jpg</strong> (38.53 KB, 下载次数: 0)

下载附件

2023-12-6 06:06 上传

TMSA作为其他去噪网络中的独立模块的影响

<img src="https://img.saraba1st.com/forum/202312/06/060714d4ygd09ydc1d0101.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-060117__01.jpg</strong> (24.98 KB, 下载次数: 0)

下载附件

2023-12-6 06:07 上传

TMSA设计选择对FID分数的影响

<img src="https://img.saraba1st.com/forum/202312/06/060623mpnynoybejynbzxe.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-060117__02.jpg</strong> (226.45 KB, 下载次数: 0)

下载附件

2023-12-6 06:06 上传

具有和不具有TMSA的模型在去噪过程中的注意力图的并排定性对比，去噪过程从顶行开始

<img src="https://img.saraba1st.com/forum/202312/06/060627qtn4dfk0rzlkl3r8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-060117__03.jpg</strong> (56.93 KB, 下载次数: 0)

下载附件

2023-12-6 06:06 上传

对使用潜在DiffiT模型的ImageNet-256和ImageNet-512实验的FID分数的无分类器引导缩放(scale)的影响

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1031#       发表于 2023-12-6 07:11

style aligned

通过共享注意力(Shared Attention)生成风格一致的图像

项目主页:http://style-aligned-gen.github.io/

github项目代码仓库:https://github.com/google/style-aligned/

大规模文本到图像(T2I)模型在创意领域迅速获得了关注，其能够通过文本提示生成视觉上引人注目的输出，然而，控制这些模型以确保风格一致仍然具有挑战性，现有方法需要微调和手动干预来理清内容和风格

在本文中，介绍了StyleAligned，一种用于在一系列生成的图像之间建立风格对齐的新技术，通过在扩散过程中采用最少的“注意力共享”，本文方法保证了T2I模型中图像之间的风格一致性

这种方法允许通过简单的反转操作使用参考风格创建风格一致的图像，本文方法对不同风格和文本提示的评估展现了高质量的合成结果和保真度，强调了其在跨越各种输入时实现一致风格的效果
————
问题陈述

在生成与任何文本描述一致的高质量图像时，最先进的文本到图像模型通常会创造对相同的风格化描述存在显著差异的图像，给定“minimal origami”的风格描述，标准文本到图像生成(左方)的输出具有显著的不同风格图像，而本文方法可以使模型生成的风格持续化(右方)
————
风格一致的生成

生成与左侧参考图像风格对齐的图像，在每个扩散去噪步骤中，除了参考图像，其他的所有图像都与参考图像执行共享的自注意力

目标图像通过使用参考查询和键(reference queries and keys)在其查询和键上(their queries and keys)应用AdaIN处理参考图像，然后应用共享注意力，其中目标特征由目标值Vt和参考值Vr更新
————
结果

本文方法可以使用不同的提示生成风格一致的内容，而无需进行微调

本文方法还可以很好地适应真实参考图像的风格迁移，同时不需要训练或模型个性化

————
与其他方法集成

StyleAligned可以轻松地与其他方法结合使用

DreamBooth+StyleAligned

MultiDiffusion+StyleAligned
————


*****

####  Machinery  
##### 1032#       发表于 2023-12-6 19:32

style aligned

通过共享注意力(Shared Attention)生成风格一致的图像

项目主页:http://style-aligned-gen.github.io/

github项目代码仓库:https://github.com/google/style-aligned/

大规模文本到图像(T2I)模型在创意领域迅速获得了关注，其能够通过文本提示生成视觉上引人注目的输出，然而，控制这些模型以确保风格一致仍然具有挑战性，现有方法需要微调和手动干预来理清内容和风格

在本文中，介绍了StyleAligned，一种用于在一系列生成的图像之间建立风格对齐的新技术，通过在扩散过程中采用最少的“注意力共享”，本文方法保证了T2I模型中图像之间的风格一致性

这种方法允许通过简单的反转操作使用参考风格创建风格一致的图像，本文方法对不同风格和文本提示的评估展现了高质量的合成结果和保真度，强调了其在跨越各种输入时实现一致风格的效果
————
问题陈述

在生成与任何文本描述一致的高质量图像时，最先进的文本到图像模型通常会创造对相同的风格化描述存在显著差异的图像，给定“minimal origami”的风格描述，标准文本到图像生成(左方)的输出具有显著的不同风格图像，而本文方法可以使模型生成的风格持续化(右方)
————
风格一致的生成

生成与左侧参考图像风格对齐的图像，在每个扩散去噪步骤中，除了参考图像，其他的所有图像都与参考图像执行共享的自注意力

目标图像通过使用参考查询和键(reference queries and keys)在其查询和键上(their queries and keys)应用AdaIN处理参考图像，然后应用共享注意力，其中目标特征由目标值Vt和参考值Vr更新
————
结果

本文方法可以使用不同的提示生成风格一致的内容，而无需进行微调

本文方法还可以很好地适应真实参考图像的风格迁移，同时不需要训练或模型个性化

————
与其他方法集成

StyleAligned可以轻松地与其他方法结合使用

DreamBooth+StyleAligned

MultiDiffusion+StyleAligned
————
SegAnyGAussians

分割任何3D高斯(Segment Any 3D Gaussians)

项目主页:https://jumpat.github.io/SAGA

github项目仓库:https://github.com/Jumpat/SegAnyGAussians

辐射场(radiance fields)中的交互式3D分割是一项有吸引力的任务，因为这在3D场景理解和操作中非常重要，然而，现有方法面临着实现细粒度、多粒度分割(multi-granularity segmentation)或需求大量计算开销、以及非实时交互的挑战

在本文中，介绍了Segment Any 3D GAussians(SAGA)，这是一种新颖的3D交互式分割方法，它将2D分割基础模型与3D Gaussian Splatting(3DGS)无缝集成，这是辐射场的最新突破

SAGA通过精心设计的对比训练(contrastive training)，将2D分割基础模型(2D segmentation foundation model)生成的多粒度2D分割结果有效地嵌入到3D高斯点特征(3D Gaussian point features)中

对现有基准的评估表明，SAGA可以通过SOTA方法实现具有竞争力的性能，此外，SAGA还实现了多粒度分割并适应各种提示(prompt)，包括点、涂鸦和2D掩码(points,scribbles,2D masks)

值得注意的是，SAGA可以在几毫秒内完成3D分割，与之前的SOTA相比实现了近1000倍的加速

<img src="https://img.saraba1st.com/forum/202312/06/193150ua571fric5v7t1r6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-192743__01.jpg</strong> (356.37 KB, 下载次数: 0)

下载附件

2023-12-6 19:31 上传

SAGA是一种新颖的交互式3D分割方法，可以在几毫秒内提供精确的3D分割，每个分割结果的下方都显示了计算时间(以秒为单位)，这代表从用户输入提示到获取分割结果之间的持续时间

<img src="https://img.saraba1st.com/forum/202312/06/193155y5kmk2uampkmkatw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-192753__01.jpg</strong> (317.95 KB, 下载次数: 0)

下载附件

2023-12-6 19:31 上传

SAGA的整体工作流程，给定预训练的3DGS模型及其训练集，将低维3D特征(low-dimensional 3D feature)附加到模型中的每个高斯(Gaussian)，对于训练集中的每个图像，使用SAM来提取2D特征和一组掩码，然后通过可微分光栅化(differentiable rasterization)渲染2D特征图

用两个损失(loss)训练附加特征(比如SAM引导损失/SAM-guidance loss和对应损失/correspondence loss)，前者采用SAM特征来引导3D特征，从模糊的2D掩码中学习3D分割，而后者提取从掩码导出的逐点对应(point-wise correspondence)关系以增强特征的紧凑性

<img src="https://img.saraba1st.com/forum/202312/06/193203eds4m4aazm4sukfg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-192805__01.jpg</strong> (78.07 KB, 下载次数: 0)

下载附件

2023-12-6 19:32 上传

NVOS上的定量结果

<img src="https://img.saraba1st.com/forum/202312/06/193208exxxujuj5v8yx53e.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-192805__02.jpg</strong> (72.72 KB, 下载次数: 0)

下载附件

2023-12-6 19:32 上传

SPIn-NeRF数据集的定量结果，“Singe view”表示简单的将2D分割结果投影到3D，因此省略了其时间消耗

<img src="https://img.saraba1st.com/forum/202312/06/193213v22v8rjqyq7r77js.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-192805__03.jpg</strong> (45.29 KB, 下载次数: 0)

下载附件

2023-12-6 19:32 上传

与 LERF-figurines上的SA3D进行对比，由于标注是由SA3D生成的，因此省略了其mIoU指标

<img src="https://img.saraba1st.com/forum/202312/06/193218ljdyybyjjjq35oaq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-192813__01.jpg</strong> (523.83 KB, 下载次数: 0)

下载附件

2023-12-6 19:32 上传

SAGA的定性结果，与SA3D相比，SAGA可以在千分之一的时间内达到类似的性能，与ISRF相比，SAGA可以区分具有相似语义的对象并实现物体部分分割，此外，得益于高效的3D高斯表征，分割对象的渲染质量优于之前的SOTA方法SA3D和ISRF

<img src="https://img.saraba1st.com/forum/202312/06/193223v9fpxex444ezopk4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-192829__01.jpg</strong> (372.69 KB, 下载次数: 0)

下载附件

2023-12-6 19:32 上传

SAGA的其中一个失败案例，右上部分展示了分割结果，下方部分展示了3DGS模型的高斯均值，失败的原因是3DGS学习到的高斯的几何结构不正确

<img src="https://img.saraba1st.com/forum/202312/06/193228xeh8077jj0ewyzp8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-192849__01.jpg</strong> (90.05 KB, 下载次数: 0)

下载附件

2023-12-6 19:32 上传

不同loss对于NVOS数据集的影响，“Corr.” 代表对应loss，“S-guidance”代表SAM-guidance loss，由于训练目标的复杂性，缺少SAM引导loss会导致分割性能显著下降

<img src="https://img.saraba1st.com/forum/202312/06/193232fyz467qpiiys50od.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-192849__02.jpg</strong> (85.87 KB, 下载次数: 0)

下载附件

2023-12-6 19:32 上传

对应loss影响的消融实验，点提示和掩码提示被标注在原始图像上，如果没有这个loss，学习到的特征就不够紧凑，这极大地阻碍了基于点提示的分割和基于掩模提示的分割

<img src="https://img.saraba1st.com/forum/202312/06/193236edj881evhsiz58o8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-192849__03.jpg</strong> (62.44 KB, 下载次数: 0)

下载附件

2023-12-6 19:32 上传

对后处理(post-processing)影响的消融，分割目标突出显示，如果不进行后处理，分割结果就会充满噪声且不完整

<img src="https://img.saraba1st.com/forum/202312/06/193240ewm999v0wnmn98w0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-192849__04.jpg</strong> (39.79 KB, 下载次数: 0)

下载附件

2023-12-6 19:32 上传

消耗的计算量分析，高斯数表示场景的尺度以及对应的分割目标，SAGA的计算可以分为三个阶段：高斯检索、后处理(filtering)和后处理(growing)

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1033#       发表于 2023-12-6 19:53

nxtp

使用下一个Token预测(Next Token Prediction)范式的对象识别(Object Recognition)

github项目主页:https://github.com/kaiyuyue/nxtp

本文提出了一种将对象识别作为下一个Token预测的方法，这个想法的核心在于应用一个语言解码器(language decoder)，从图像嵌入(image embeddings)中自回归的预测文本Token(auto-regressively predicts the text tokens)以形成标签(labels)

为了使这种预测过程基于自回归，为解码器定制了一个非因果注意力掩码(non-causal attention mask)，其中包含两个关键特征:将来自不同标签的Token建模为独立的，并将图像Token视为前缀(prefix)

这种遮蔽(Mask)机制激发了一种有效的方法，单样本采样(one-shot sampling)，同时并行采样多个标签的Token，并在推理过程中根据生成的标签的概率对生成的标签进行排序

为了进一步提高效率，还提出了一种简单的策略，通过简单地丢弃预训练语言模型的中间块(intermediate blocks)来构建紧凑的解码器，这种方法产生的解码器与完整模型的性能相匹配，但效率显著提高

<img src="https://img.saraba1st.com/forum/202312/06/195245ta3ipefsaff8yrii.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-195108__01.jpg</strong> (129.06 KB, 下载次数: 0)

下载附件

2023-12-6 19:52 上传

作为下一个Token预测的对象识别，使用生成解码器(例如基于Transformer的语言模型)来自回归的预测对象标签

<img src="https://img.saraba1st.com/forum/202312/06/195249z617i6gilo0xh511.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-195125__01.jpg</strong> (113.1 KB, 下载次数: 0)

下载附件

2023-12-6 19:52 上传

非因果注意力掩码，用于为图像Token Xv加上前缀，并将不同标签Lk的Token解耦，使其在[SEP] Token上独立

<img src="https://img.saraba1st.com/forum/202312/06/195254rot47rpsp3pr47fo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-195130__01.jpg</strong> (112.86 KB, 下载次数: 0)

下载附件

2023-12-6 19:52 上传

用于并行生成top-k标签Token的单样本采样，一旦模型对[SEP] Token进行采样，标签就完成了，否则，模型将继续处理未完成的标签

<img src="https://img.saraba1st.com/forum/202312/06/195259oawagu3mwau3qawa.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231206-195145__01.jpg</strong> (693.85 KB, 下载次数: 0)

下载附件

2023-12-6 19:52 上传

不同方法与top-10预测的对比，粗体数字为最佳结果，下划线数字为次佳结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1034#       发表于 2023-12-7 01:57

 本帖最后由 Machinery 于 2023-12-7 01:59 编辑 

X-Adapter

为升级的扩散模型添加通用插件兼容性

项目主页:https://showlab.github.io/X-Adapter/

github项目代码仓库:https://github.com/showlab/X-Adapter

X-Adapter，一种通用的升级模型兼容方法，可以在无需进一步重新训练的情况下，使预训练的模块化插件方法(例如ControlNet、LoRA等)能够直接在升级后的文本到图像扩散模型使用(例如SDXL)

这是通过训练一个额外的网络来使用新的文本图像数据对(text-image data pairs)控制冻结的升级模型来实现这一目标的，具体来说，X-Adapter保留了旧模型的冻结副本，用以作为不同插件的连接器

此外，X-Adapter还添加了可训练的映射层，将不同版本模型的解码器桥接起来，以进行特征重新映射，重新映射的特征将用作升级后的模型的指导，为了增强X-Adapter的指导能力，对升级后的模型采用了无文本(null-text)训练策略，训练后，还引入了两阶段去噪策略对齐X-Adapter的初始潜在和升级后的模型

通过这些策略，X-Adapter展示了对各种插件的通用兼容性，并且还使得不同版本的插件能够协同工作，从而扩展了扩散社区的能力，为了验证所提出方法的有效性，进行了大量的实验，结果表明X-Adapter可以促进升级后的基础扩散模型的更广泛应用
————

<img src="https://img.saraba1st.com/forum/202312/07/015616njei23wmz5ee21e3.jpg" referrerpolicy="no-referrer">

<strong>xadapter_teaser.jpg</strong> (946.17 KB, 下载次数: 0)

下载附件

2023-12-7 01:56 上传

给定基础扩散模型(例如Stable Diffusion 1.5)的预训练模块插件(例如ControlNet、LoRA)，所提出的X-Adapter可以普遍地升级这些插件，使它们能够直接与升级后的模型一起使用(例如SDXL)而无需进一步重新训练
————

<img src="https://img.saraba1st.com/forum/202312/07/015707pbikb5vjo5iadt15.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-015655.jpg</strong> (110.05 KB, 下载次数: 0)

下载附件

2023-12-7 01:57 上传

任务定义，与之前单独训练每个插件的方法不同，本方法只需要训练单个X-Adapter，即可应用到所有固定的下游插件中
——

<img src="https://img.saraba1st.com/forum/202312/07/015722p1ksol7zp9ff7yq1.png" referrerpolicy="no-referrer">

<strong>xadapter_pipeline_v5.png</strong> (363.11 KB, 下载次数: 0)

下载附件

2023-12-7 01:57 上传

方法概览图，在训练中，在升级的基础模型和X-Adapter的潜在空间中添加不同的噪声，通过将升级模型的提示设置为空并训练映射层，X-Adapter学习如何引导升级后的模型，在测试中
(a)可以直接在升级模型上应用X-Adapter的插件
(b)引入两阶段流方案来提高图像质量
——

<img src="https://img.saraba1st.com/forum/202312/07/015733njyqnbq7hpcyv8yc.jpg" referrerpolicy="no-referrer">

<strong>1f5dcfa7-b40f-440e-aa93-4c1e9f864207.jpg</strong> (408.89 KB, 下载次数: 0)

下载附件

2023-12-7 01:57 上传

<img src="https://img.saraba1st.com/forum/202312/07/015733m6bouc49h6do7x6i.jpg" referrerpolicy="no-referrer">

<strong>56218d4e-91dc-4a96-aeee-f139c8b39849.jpg</strong> (401.26 KB, 下载次数: 0)

下载附件

2023-12-7 01:57 上传

提案的X-Adapter和预训练SD 1.5插件，展示了SDXL和SD 2.1上的不同结果，X-Adapter展现了对不同插件和基础模型的广泛支持

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1035#       发表于 2023-12-7 03:21

ImageDream

用于3D生成的图像提示多视图(Image-Prompt Multi-view)扩散

项目主页:https://image-dream.github.io/

github项目主页:https://github.com/ImageDream-byte/ImageDream

ImageDream，一种用于生成3D对象的创新图像提示、多视图扩散模型，与现有SOTA图像条件方法相比，ImageDream能够生成更高质量的3D模型

本文方法利用图像中的对象的规范相机坐标，提高了视觉几何精度，该模型根据输入图像在扩散模型内的每个模块上设计了不同级别的控制，其中全局控制塑造整体对象布局，局部控制微调图像细节

通过大量使用标准提示列表进行的广泛评估证明了ImageDream的有效性
————

<img src="https://img.saraba1st.com/forum/202312/07/032134fdevj4dliwe21mdn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-031536.jpg</strong> (65.7 KB, 下载次数: 0)

下载附件

2023-12-7 03:21 上传

阐明了ImageDream的多级图像提示控制器在UNet扩散模型架构中的集成方法，补充了MVDream中部署的原始文本嵌入(original text embedding)和四视图相机嵌入(four-view camera embedding)
——
图像提示分数蒸馏

<img src="https://img.saraba1st.com/forum/202312/07/032139zulbir8ce886rc9r.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-031529.jpg</strong> (60.92 KB, 下载次数: 0)

下载附件

2023-12-7 03:21 上传

图像提示多视图扩散模型可以轻松地与分数蒸馏相结合，其中仅执行单阶段SDS融合
——
合成视图和 3D 对象

<img src="https://img.saraba1st.com/forum/202312/07/032145zmzm7390zdyaz7dy.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-031822.jpg</strong> (128.11 KB, 下载次数: 0)

下载附件

2023-12-7 03:21 上传

ImageDream 以多视图一致的方式生成对象和场景
——
对比结果

<img src="https://img.saraba1st.com/forum/202312/07/032150qa5lefapzjla3wwt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-032046.jpg</strong> (259.22 KB, 下载次数: 0)

下载附件

2023-12-7 03:21 上传

采用了MVDream中的39个提示并使用SDXL生成图像来与其他图像转3D方法进行对比，所有提示均使用固定的默认配置，无需使用Threestudio进行超参数调整，ImageDream-G表示仅使用CLIP特征的结果，ImageDream-P表示同时具有这两种特征的结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1036#       发表于 2023-12-7 04:17

LivePhoto

具有文本引导运动控制(Text-guided Motion Control)的真实图像动画化(Real Image Animation)

项目主页:https://xavierchen34.github.io/LivePhoto-Page/

github项目仓库:https://github.com/XavierCHEN34/LivePhoto

尽管最近文本到视频生成领域取得了进展，但现有的研究通常忽视了这样一个问题：在合成视频中经常只有空间内容而时间运动则不受文本控制

针对这样的挑战，这项工作提出了名为LivePhoto的系统，允许用户通过文本描述将他们感兴趣的图像动画化，具体来说，首先建立一个强大的基线，帮助熟练的文本到图像生成器(即Stable Diffusion)将图像作为进一步的输入，然后，为改进的生成器配备了用于时间建模的运动模块，并提出了精心设计的训练工作流程以更好地链接文本和运动，特别是，考虑到以下事实:
1.文本只能粗略地描述运动(无论移动速度如何)
2.文本可能同时包含内容和运动描述

引入了运动强度估计模块(motion intensity estimation module)和文本重加权模块(text re-weighting module)以减少文本到运动映射的模糊性，经验性的证据表明，本文方法能够很好地将与运动相关的文本指令解码为视频，例如动作、摄像机移动，甚至凭空变出新内容(例如将水倒入空玻璃杯中)，最有趣的是，由于所提出的强度学习机制，LivePhoto除了用于视频定制的文本之外，还为用户提供了额外的控制信号(即运动强度)
————

<img src="https://img.saraba1st.com/forum/202312/07/041659m6i1b7brxmermnd1.png" referrerpolicy="no-referrer">

<strong>pipeline.png</strong> (709.99 KB, 下载次数: 0)

下载附件

2023-12-7 04:16 上传

LivePhoto的整体工作流程如上所示，除了以参考图像和文本作为输入外，LivePhoto还利用运动强度作为补充条件，图像和运动强度(从1级到10级)是在训练期间从基准真实(ground truth)视频中获得的，并在推理过程中由用户定制

首先，提取参考潜变量作为局部内容指导，然后将其与潜变量噪声、帧嵌入和强度嵌入连接起来，这个10-channel张量被送入UNet中进行去噪

在推理过程中，使用参考潜变量的反转而不是纯高斯(pure Gaussian)提供内容先验，在上方，内容编码器提取视觉Token以提供全局内容指导，在下方，引入了文本重加权，它学习强调文本嵌入的运动相关部分，以实现更好的文本运动映射，视觉和文本Token通过交叉注意力注入到UNet中，对于UNet，冻结预训练的Stable Diffusion并插入运动模块来捕获帧间关系

火焰和雪花的符号分别表示可训练和冻结的参数
————
带有文本指令的运动控制

<img src="https://img.saraba1st.com/forum/202312/07/041711bb337qv99zv0h970.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-041511.jpg</strong> (151.99 KB, 下载次数: 0)

下载附件

2023-12-7 04:17 上传

LivePhoto的独特功能是通过文本指令进行精确的运动控制，此外，用户还可以通过设置不同的“运动强度”来定制这些运动
————
与现有替代方案的对比

<img src="https://img.saraba1st.com/forum/202312/07/041718cwt8gav6njt066e7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-041328.jpg</strong> (575.33 KB, 下载次数: 0)

下载附件

2023-12-7 04:17 上传

 对LivePhoto和GEN-2以及Pikalabs进行了分析对比，使用了截至2023年11月的版本，生成的视频从左到右按顺序呈现，分别源自GEN-2、Pikalabs和LivePhoto，值得注意的是，LivePhoto在文本引导运动控制方面表现出了卓越的性能
————
视频演示(请看原项目页面)

<img src="https://img.saraba1st.com/forum/202312/07/041739xyawvc8yg3ahshcx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-041312.jpg</strong> (78.81 KB, 下载次数: 0)

下载附件

2023-12-7 04:17 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  RandomDictator  
##### 1037#       发表于 2023-12-7 04:55

Deepmind的Gemini出了，据称超过gpt4，不知道实际咋样


*****

####  Machinery  
##### 1038#       发表于 2023-12-7 05:47

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63247472&amp;ptid=2126390" target="_blank">RandomDictator 发表于 2023-12-7 04:55</a>
Deepmind的Gemini出了，据称超过gpt4，不知道实际咋样</blockquote>
英文版bard已经用上了，想用的话现在就可以体验<img src="https://static.saraba1st.com/image/smiley/face2017/037.png" referrerpolicy="no-referrer">

—— 来自 [S1Fun](https://s1fun.koalcat.com)

*****

####  RandomDictator  
##### 1039#       发表于 2023-12-7 05:51

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63247499&amp;ptid=2126390" target="_blank">Machinery 发表于 2023-12-7 05:47</a>

英文版bard已经用上了，想用的话现在就可以体验

—— 来自 S1Fun</blockquote>
bard上是pro不是ultra，看metrics有没有3.5水平都还不好说，还没有多模态，ultra还要等明年发<img src="https://static.saraba1st.com/image/smiley/face2017/001.png" referrerpolicy="no-referrer">


*****

####  Machinery  
##### 1040#       发表于 2023-12-7 06:03

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63247507&amp;ptid=2126390" target="_blank">RandomDictator 发表于 2023-12-7 05:51</a>
bard上是pro不是ultra，看metrics有没有3.5水平都还不好说，还没有多模态，ultra还要等明年发 ...</blockquote>
单从指标看ultra的话感觉和gpt4伯仲之间吧，甚至感觉还取了点巧，对比4主要强在原生多模态预训练，虽然输出还是图片和文本，而且连微调都做了，感觉没多少提升空间了，最乐的是只说了nano版参数，堪比closeai般的保密<img src="https://static.saraba1st.com/image/smiley/face2017/037.png" referrerpolicy="no-referrer">

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  RandomDictator  
##### 1041#       发表于 2023-12-7 06:38

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63247513&amp;ptid=2126390" target="_blank">Machinery 发表于 2023-12-7 06:03</a>

单从指标看ultra的话感觉和gpt4伯仲之间吧，甚至感觉还取了点巧，对比4主要强在原生多模态预训练，虽然输 ...</blockquote>
能和gpt4打平就已经很强了吧，市面上其他最多都是接近3.5的水平，给够closeai足够动力干活了

sunder最好希望别在ultra release之前gpt就又升级了<img src="https://static.saraba1st.com/image/smiley/face2017/067.png" referrerpolicy="no-referrer">


*****

####  darktide  
##### 1042#       发表于 2023-12-7 08:38

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63236994&amp;ptid=2126390" target="_blank">Machinery 发表于 2023-12-6 07:11</a>

style aligned

通过共享注意力(Shared Attention)生成风格一致的图像</blockquote>
感觉这个比较有实用性


*****

####  Machinery  
##### 1043#       发表于 2023-12-7 20:09

 本帖最后由 Machinery 于 2023-12-7 20:10 编辑 

OneLLM

一个框架将所有模态对齐到语言

github项目主页:https://github.com/csuhan/OneLLM

多模态大型语言模型(MLLM)由于其强大的多模态理解能力而受到广泛关注，然而，现有的部分研究工作严重依赖于特定模态的编码器，这些编码器通常在架构上有所不同，并且仅限于常见的模态

在本文中，提出了OneLLM，这是一种使用统一框架将八种模态与语言对齐的MLLM，这是通过统一的多模态编码器(unified multimodal encoder)和渐进式多模态对齐工作流程(progressive multimodal alignment pipeline)实现的

具体来说，首先训练了一个图像投影模块，将视觉编码器与LLM连接起来，然后通过混合多个图像投影模块和动态路由来构建通用投影模块(UPM/universal projection module)，最后，逐步将更多模态通过UPM与LLM对齐

为了充分发挥OneLLM在后续指令中的潜力，还策划构造了一个全面的多模态指令数据集，其中包括来自图像、音频、视频、点云、深度/法线贴图、IMU和fMRI大脑活动的200万个项目

根据25个不同的基准测试评估了OneLLM，诸如多模态字幕说明、问题回答和推理等任务，在这些任务中它提供了出色的性能表现

<img src="https://img.saraba1st.com/forum/202312/07/200713alzjszsqqtbrks2b.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-195746__01.jpg</strong> (171.8 KB, 下载次数: 0)

下载附件

2023-12-7 20:07 上传

不同多模态LLM的对比，OneLLM将支持的模态从三种扩展至八种

Vision LLM:一个图像编码器和投影模块
Multimodal(MM)LLM:特定模态的编码器和投影模块
OneLLM:通用编码器、通用投影模块和用于在模态之间切换的模态Token {modal}

<img src="https://img.saraba1st.com/forum/202312/07/200723rdz2wxdojvaundwj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-195756__01.jpg</strong> (233.88 KB, 下载次数: 0)

下载附件

2023-12-7 20:07 上传

OneLLM的架构，OneLLM由模态分词器(tokenizers)、通用编码器、通用投影模块(UPM)和LLM组成

模态分词器是一个2D/1D卷积层，用于将输入信号转换为Token序列，为了简单起见，省略了视频、深度/法线贴图分词器，通用编码器是一种冻结的视觉语言模型(即CLIP)，用于提取高维特征，UPM由多个投影专家和模态路由器组成，用于使输入信号与语言保持一致

对于对齐阶段，训练模态分词器和UPM，并保持LLM冻结，对于指令调整阶段，只训练LLM，其他模型保持冻结，在UPM的前向传递中，将输入和模态Token连接起来作为输入，然后只将模态Token作为输入信号的总结，并将其输入LLM进行多模态理解

<img src="https://img.saraba1st.com/forum/202312/07/200736x6nli63ulqfwz68n.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-195812__01.jpg</strong> (406.61 KB, 下载次数: 0)

下载附件

2023-12-7 20:07 上传

对12个图像文本基准测试进行评估，包括6个VQA任务，2个图像字幕说明任务和4个多模态基准

LLM分别是是Chinchilla、Vicuna、Qwen、LLaMA和LLaMA2，VQA和字幕说明任务的评估指标分别是准确率和CIDEr，粗体和下划线标出的结果分别是最好的和次好的结果，-代表未报告结果

<img src="https://img.saraba1st.com/forum/202312/07/200743abmkobd1fnbkz48k.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-195822__01.jpg</strong> (87.44 KB, 下载次数: 0)

下载附件

2023-12-7 20:07 上传

视频文本任务评估，包括视频问答和视频字幕说明任务，Acc代表准确率

<img src="https://img.saraba1st.com/forum/202312/07/200748jto3o86jt1xvj3cg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-195822__02.jpg</strong> (74.79 KB, 下载次数: 0)

下载附件

2023-12-7 20:07 上传

对音频文本任务的评估，包括Clotho Caption上的音频字幕说明和Clotho AQA上的音频问答任务

<img src="https://img.saraba1st.com/forum/202312/07/200753yn9rkzirkp69iop4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-195914__01.jpg</strong> (228.99 KB, 下载次数: 0)

下载附件

2023-12-7 20:07 上传

对音频-视频-文本任务的评估，包括MUSIC-AVQA上的视听问答和 VALOR-32K上的视听字幕说明以及AVSD上的对话完成(dialog completion)任务

<img src="https://img.saraba1st.com/forum/202312/07/200759ftx8tc7686c0tmn3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-195822__04__01.jpg</strong> (72.16 KB, 下载次数: 0)

下载附件

2023-12-7 20:07 上传

点云文本任务评估，评估数据集来自Objaverse，遵循PointLLM中的数据分割，InstructBLIP以单视图图像作为输入，而PointLLM和OneLLM以点云作为输入
GPT4- Acc.代表使用GPT4作为准确率评估者

<img src="https://img.saraba1st.com/forum/202312/07/200803pauwhdsyhbyhb2ba.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-195839__01.jpg</strong> (91.55 KB, 下载次数: 0)

下载附件

2023-12-7 20:08 上传

使用深度/法线贴图评估场景分类任务，请注意，NYUv2和SUN RGB-D仅具有深度图，通过应用预训练的DPT模型来生成法线贴图

OneLLM-N/D:具有深度/法线贴图输入的OneLLM
*:CLIP的输入是深度渲染的灰度图像，ImageBind在SUN RGB-D的图像深度对(image-depth pairs)上进行了训练，因此不是零样本的

<img src="https://img.saraba1st.com/forum/202312/07/200810shaamjm8ziiccp1p.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-195839__02.jpg</strong> (205.82 KB, 下载次数: 0)

下载附件

2023-12-7 20:08 上传

消融实验，选择了三种模态(图像、音频、视频)和四个数据集(NoCaps、VQAv2、ClothoQA和MSVDQA)进行评估，灰色背景的行是默认设置

<img src="https://img.saraba1st.com/forum/202312/07/200817ietx4utpxt74uwgt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-195852__01.jpg</strong> (652 KB, 下载次数: 0)

下载附件

2023-12-7 20:08 上传

八种模态的定性结果，所有演示输入均来自网络或对应模态的测试集

<img src="https://img.saraba1st.com/forum/202312/07/200823n94rkcr6l03krjlb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-195902__01.jpg</strong> (69.34 KB, 下载次数: 0)

下载附件

2023-12-7 20:08 上传

通用编码器的消融实验

<img src="https://img.saraba1st.com/forum/202312/07/200828z8d6kr0aefxaneg5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-195914__01.jpg</strong> (228.99 KB, 下载次数: 0)

下载附件

2023-12-7 20:08 上传

训练数据集

<img src="https://img.saraba1st.com/forum/202312/07/200833exb5048rxp8j4ba8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-195922__01.jpg</strong> (259.36 KB, 下载次数: 0)

下载附件

2023-12-7 20:08 上传

训练的提示格式

<img src="https://img.saraba1st.com/forum/202312/07/200838sbjwjfi6ckqwtqq0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-195937__01.jpg</strong> (230.17 KB, 下载次数: 0)

下载附件

2023-12-7 20:08 上传

评估的提示格式

<img src="https://img.saraba1st.com/forum/202312/07/200843ucoo11n4k5e4q93c.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-195943__01.jpg</strong> (121.13 KB, 下载次数: 0)

下载附件

2023-12-7 20:08 上传

不同多模态LLM的对比

<img src="https://img.saraba1st.com/forum/202312/07/200850r4u0u2x0gjxc4pax.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-200003.jpg</strong> (503.86 KB, 下载次数: 0)

下载附件

2023-12-7 20:08 上传

附加的定性图像演示

<img src="https://img.saraba1st.com/forum/202312/07/200856ogmjtka1ce9sjmzh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-200018.jpg</strong> (487.93 KB, 下载次数: 0)

下载附件

2023-12-7 20:08 上传

附加的定性视频、音频和点云演示

<img src="https://img.saraba1st.com/forum/202312/07/200904bntgo76toaagro8x.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231207-200035.jpg</strong> (401.68 KB, 下载次数: 0)

下载附件

2023-12-7 20:09 上传

附加的定性深度/法线贴图、IMU和fMRI演示

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1044#       发表于 2023-12-8 02:20

Kandinsky 3.0

文本到图像生成模型Kandinsky 3.0版本

项目主页:https://ai-forever.github.io/Kandinsky-3

github项目仓库:https://github.com/ai-forever/Kandinsky-3

Kandinsky 3.0，一种基于潜在扩散的大规模文本到图像生成模型，延续了Kandinsky文本到图像模型系列，反映了在实现更高质量和真实感的图像生成方面取得的进展

与以前版本的Kandinsky 2.x相比，Kandinsky 3.0进一步利用了两倍大的U-Net骨干、十倍大的文本编码器，并删除了扩散映射

本文描述了模型的架构、数据收集过程、训练技术和用户交互的生产系统，其中重点关注了关键组件，正如通过大量实验确定的那样，与其他模型相比，这些组件对提高模型质量具有最显著的影响

通过并排对比，Kandinsky3.0不仅在文本理解方面变得更好，并且在特定领域也表现得更好
————

<img src="https://img.saraba1st.com/forum/202312/08/021943zzzsnk5988ycpvn1.jpeg" referrerpolicy="no-referrer">" src="https://static.saraba1st.com/image/common/none.gif" referrerpolicy="no-referrer">

<strong>K3_full_pipline.jpeg</strong> (182.94 KB, 下载次数: 0)

下载附件

2023-12-8 02:19 上传

Kandinsky 3.0是一个潜在扩散模型，其完整流程包括用于处理用户提示的文本编码器、用于在去噪(反向)过程中预测噪声的U-Net以及用于从生成的潜在重建图像的解码器模型，在U-Net训练期间，文本编码器和图像解码器完全冻结，整个模型包含约119亿参数
————

<img src="https://img.saraba1st.com/forum/202312/08/021951nom6sbouxumbgoi7.jpg" referrerpolicy="no-referrer">

<strong>kandinsky.jpg</strong> (233.19 KB, 下载次数: 0)

下载附件

2023-12-8 02:19 上传

架构由三部分组成:
Text encoder Flan-UL2 (encoder part) - 8.6B
Latent Diffusion U-Net - 3B
MoVQ encoder/decoder - 267M
————
发布了两个模型:
 base:基础文本到图像扩散模型，该模型在400个A100上训练了超过200万步
Inpainting:模型的重绘版本，该模型从base模型的最终检查点进行初始化，并在300个A100上训练了25万步
————
重绘

<img src="https://img.saraba1st.com/forum/202312/08/022000m02ro0ls0rwcw200.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231208-021830.jpg</strong> (314.62 KB, 下载次数: 0)

下载附件

2023-12-8 02:20 上传

通过训练基础文本到图像模型，还发布了附加的重绘版本，从基本模型开始训练，然后在包含随机掩码的多样化数据集上对其进行微调，该模型展现了其根据文本查询智能填充图像缺失区域并将其与周围视觉内容无缝融合的能力
————
外绘

<img src="https://img.saraba1st.com/forum/202312/08/022006dct0rrm34rlmlx73.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231208-021841.jpg</strong> (280.75 KB, 下载次数: 0)

下载附件

2023-12-8 02:20 上传

此外，模型还能够解决图像补全问题，根据文本自然地填充图像的缺失区域，并使其与视觉上下文保持一致
————
Deforum

<img src="https://img.saraba1st.com/forum/202312/08/022010riqz6x17oood1h4d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231208-021851.jpg</strong> (376.49 KB, 下载次数: 0)

下载附件

2023-12-8 02:20 上传

Kandinsky-3通过与Deforum集成，允许在不同模式下生成高质量的动画视频

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1045#       发表于 2023-12-8 03:33

 本帖最后由 Machinery 于 2023-12-8 03:39 编辑 

playground-v2-1024px-aesthetic

从头预训练的SDXL构架模型

相关博客:https://blog.playgroundai.com/playground-v2/

hugface项目权重下载:https://huggingface.co/playgroundai/playground-v2-1024px-aesthetic

<img src="https://img.saraba1st.com/forum/202312/08/033301azvwryv10qwfvvd0.jpg" referrerpolicy="no-referrer">

<strong>Group-3.jpg</strong> (124.27 KB, 下载次数: 0)

下载附件

2023-12-8 03:33 上传

<img src="https://img.saraba1st.com/forum/202312/08/033301ck74m7mpbuum19bm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231208-032421.jpg</strong> (232.92 KB, 下载次数: 0)

下载附件

2023-12-8 03:33 上传

Playground v2是一种基于扩散的文本到图像生成模型，该模型由Playground的研究团队从头开始训练，根据Playground的用户研究，Playground v2生成的图像比Stable Diffusion XL生成的图像受欢迎程度高2.5倍

团队很高兴向社区发布不同训练阶段的中间检查点，包括评估指标，希望这能鼓励对图像生成基础模型的进一步研究，最后引入了一个新的基准MJHQ-30K，用于自动评估模型的美学质量
————
基准测试

早期基准测试表明，Playground v2的受欢迎程度是Stable Diffusion XL的2.5 倍，在数千个提示中，通过向数千名用户展示每个模型的图像来询问他们更喜欢哪张图像，下面展示了每个模型的结果

<img src="https://img.saraba1st.com/forum/202312/08/033309eztcg6jkjkggsenr.png" referrerpolicy="no-referrer">

<strong>Wizard-data--1-.png</strong> (10.78 KB, 下载次数: 0)

下载附件

2023-12-8 03:33 上传

Parti提示:

<img src="https://img.saraba1st.com/forum/202312/08/033319giffofme24cmynso.png" referrerpolicy="no-referrer">

<strong>PartiPrompt--1-.png</strong> (9.75 KB, 下载次数: 0)

下载附件

2023-12-8 03:33 上传

————
FID

引入了一个新的基准MJHQ-30K，用于自动评估模型的美学质量，该基准测试在高质量数据集上计算FID，以衡量美学质量，整理了来自Midjourney的高质量数据集，包含10个常见类别，每个类别有3K样本，依照惯例，使用美学评分和CLIP评分来确保高图像质量和高图文对齐，此外，还特别注意了使每个类别中的数据更多样化

<img src="https://img.saraba1st.com/forum/202312/08/033341uq66qzgkquqz8g4j.png" referrerpolicy="no-referrer">

<strong>MJHQ-30K-Per-Category-Benchmark.png</strong> (36.22 KB, 下载次数: 0)

下载附件

2023-12-8 03:33 上传

下面是选择的提示的对比表格，用以提供高质量、对齐和美观的感觉:

<img src="https://img.saraba1st.com/forum/202312/08/033347ldozdtfoozedoou6.jpg" referrerpolicy="no-referrer">

<strong>Group-1--1--2.jpg</strong> (71.28 KB, 下载次数: 0)

下载附件

2023-12-8 03:33 上传

————
不求回报，传递下去(Paying it forward)

同时还发布了预训练权重，以推动在算力往往受限的环境中的研究领域，HuggingFace上提供了256px(相关链接:https://huggingface.co/playgroundai/playground-v2-256px-base?ref=blog.playgroundai.com)和512px(相关链接:https://huggingface.co/playgroundai/playground-v2-512px-base?ref=blog.playgroundai.com)阶段的基本模型权重

如果您创造了任何东西，研究团队将很乐意听到
— Playground Research Team
————
模型说明
开发者:Playground
模型类型:基于扩散的文本到图像生成模型
许可证:Playground v2 Community License
总结：该模型根据文本提示生成图像，它是一个潜在扩散模型，使用两个固定的、预训练的文本编码器(OpenCLIP-ViT/G和CLIP-ViT/L)，遵循与Stable Diffusion XL相同的架构
————
MJHQ-30K基准测试

相关链接:https://huggingface.co/playgroundai/playground-v2-1024px-aesthetic#mjhq-30k-benchmark

<img src="https://img.saraba1st.com/forum/202312/08/033839kpw0k0nyewsnife0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231208-033757.jpg</strong> (112.86 KB, 下载次数: 0)

下载附件

2023-12-8 03:38 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1046#       发表于 2023-12-8 04:40

Gaussian Head Avatar

通过动态高斯(Dynamic Gaussians)实现超高保真度的化身头像(Ultra High-fidelity Head Avatar)

项目主页:https://yuelangx.github.io/gaussianheadavatar/

github项目代码仓库:https://github.com/YuelangX/Gaussian-Head-Avatar

创建高保真3D化身头像一直是研究中的热点，但在轻量级稀疏视图设置下仍然存在巨大挑战，在本文中，提出了以可控3D高斯为代表的高斯化身头像，用于高保真的头像建模

通过优化神经3D高斯和完全学习的基于MLP的变形场来捕获复杂的表情，这两部分相辅相成，因此本文方法可以在保证表情准确性的同时对细粒度的动态细节进行建模

此外，还基于隐式SDF(implicit SDF)和DMTet(Deep Marching Tetrahedra)设计了一种有效的几何引导初始化策略，以确保训练过程的稳定性和收敛

实验表明，本文方法优于其他SOTA稀疏视图方法，即使在夸张的表情下，也能在2K分辨率实现超高保真渲染质量

<img src="https://img.saraba1st.com/forum/202312/08/043753zjuv6fkszjgjogjo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231208-043348__01.jpg</strong> (403.35 KB, 下载次数: 0)

下载附件

2023-12-8 04:37 上传

Gaussian Head Avatar在2K分辨率下实现了表情可控的超高保真图像合成，上方展示了合成头像的不同视图，下方展示了相同表情的不同身份的动画化， 训练期间使用了16个视图

<img src="https://img.saraba1st.com/forum/202312/08/043759h0zkpspkfkkrfprf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231208-043412__01.jpg</strong> (278.47 KB, 下载次数: 0)

下载附件

2023-12-8 04:37 上传

Gaussian Head Avatar渲染和重建概览图，首先在初始阶段优化引导模型(包括神经网格、变形MLP和颜色MLP)，然后，使用它们来初始化神经高斯和动态生成器，最后，通过可微渲染和超分辨率网络合成2K RGB图像，Gaussian Head Avatar在多视图RGB视频的监督下进行训练

<img src="https://img.saraba1st.com/forum/202312/08/043803tesxnnmn6yuinmqs.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231208-043435__01.jpg</strong> (273.88 KB, 下载次数: 0)

下载附件

2023-12-8 04:38 上传

不同方法在自重现(self reenactment task)任务上的定性对比

从左到右分别是:NeRFBlendShape、NeRFace、HAvatar和本文方法，本文方法可以高质量地重建胡须、牙齿等细节

<img src="https://img.saraba1st.com/forum/202312/08/043810xouacmhbtwt4xejw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231208-043452__01.jpg</strong> (384.56 KB, 下载次数: 0)

下载附件

2023-12-8 04:38 上传

不同方法在跨越身份的重现任务上的定性对比

从左到右分别是:NeRFBlendShape、NeRFace、HAvatar和本文方法，本文方法可以合成高保真图像，同时确保表情迁移的准确性

<img src="https://img.saraba1st.com/forum/202312/08/043815qt8y3lwm0wtnbabm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231208-043501__01.jpg</strong> (151.03 KB, 下载次数: 0)

下载附件

2023-12-8 04:38 上传

NeRFBlendShape、NeRFace、HAvatar和本文方法的无超分版本以及完全版本对比

<img src="https://img.saraba1st.com/forum/202312/08/043947drvuv2misj719zoo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231208-043518__01__01.jpg</strong> (182.85 KB, 下载次数: 0)

下载附件

2023-12-8 04:39 上传

初始化策略的消融实验:FLAME-初始化和本文几何引导初始化，本文策略成功确保远离头部的发丝得到良好的重建

<img src="https://img.saraba1st.com/forum/202312/08/044019wvzn0oj04d0oh6o9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231208-043523__01.jpg</strong> (62.38 KB, 下载次数: 0)

下载附件

2023-12-8 04:40 上传

其他两个消融基线和本文方法的定量评估结果

<img src="https://img.saraba1st.com/forum/202312/08/044001tu24lzirmgugb92k.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231208-043518__01__02.jpg</strong> (152.88 KB, 下载次数: 0)

下载附件

2023-12-8 04:40 上传

变形建模方法的消融实验:基于网格LBS的变形和本文的完全学习变形，本文方法可以学习复杂且夸张的表情

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1047#       发表于 2023-12-8 05:28

 本帖最后由 Machinery 于 2023-12-8 05:30 编辑 

DreamComposer

通过多视图条件生成可控的3D对象

项目主页:https://yhyang-myron.github.io/DreamComposer/

github项目仓库:https://github.com/yhyang-myron/DreamComposer

<img src="https://img.saraba1st.com/forum/202312/08/052656ypszascsvy44kqvy.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231208-052535.jpg</strong> (129.71 KB, 下载次数: 0)

下载附件

2023-12-8 05:26 上传

利用预训练的2D大规模生成模型，最近的研究工作能够从单个真实自然图像中生成高质量的新视图，然而，由于缺乏来自多个视图的信息，这些作品在生成可控的新视图方面遇到了困难

在本文中，提出了DreamComposer，这是一个灵活且可扩展的框架，可以通过注入多视图条件(injecting multi-view conditions)来增强现有的视图感知(view-aware)扩散模型

具体来说，DreamComposer首先使用视图感知3D提升模块(view-aware 3D lifting module )从多个视图获取对象的3D表征，然后使用多视图特征融合模块(multi-view feature fusion module)从3D表征中渲染目标视图的潜在特征，最后，从多视图输入中提取的目标视图特征被注入到预训练的扩散模型中

实验表明，DreamComposer与SOTA零样本新视图合成扩散模型完全兼容，可以进一步增强它们以生成具有多视图条件的高保真新视图图像，为可控的3D对象重建和各种其他多种应用程序做好了准备
————

<img src="https://img.saraba1st.com/forum/202312/08/052717i72qogi6tj66rits.png" referrerpolicy="no-referrer">

<strong>pipeline.png</strong> (374.55 KB, 下载次数: 0)

下载附件

2023-12-8 05:27 上传

给定来自不同视图的多个输入图像，DreamComposer提取它们的2D潜在特征并使用3D提升模块生成三平面3D表征，然后将从3D表征获得的多视图条件渲染注入到预训练的扩散模型中，以提供目标视图辅助信息
————
Google扫描物体数据集的结果

<img src="https://img.saraba1st.com/forum/202312/08/052729pol114qz82bz8zsq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231208-052552.jpg</strong> (74.16 KB, 下载次数: 0)

下载附件

2023-12-8 05:27 上传

在Google扫描物体数据集上对SyncDreamer(“SyncD.”)和DC-SyncDreamer(“SyncD.+Ours”)的3D重建结果进行定性对比，其中附加的额外的后视图输入图像(用□标记)是通过Zero-1-to-3生成的
————
Objaverse数据集的结果

<img src="https://img.saraba1st.com/forum/202312/08/052751rz6zx6guigghsqay.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231208-052603.jpg</strong> (64.91 KB, 下载次数: 0)

下载附件

2023-12-8 05:27 上传

Objaverse数据集上SyncDreamer(“SyncD.”)和DC-SyncDreamer(“SyncD.+Ours”)的3D重建结果的定性对比
————
输入的视图数量的消融实验

<img src="https://img.saraba1st.com/forum/202312/08/052756ipgqmkxgehxfezqm.png" referrerpolicy="no-referrer">

<strong>ablation.png</strong> (807.49 KB, 下载次数: 0)

下载附件

2023-12-8 05:27 上传

DreamComposer可以处理任意数量的输入视图，并且其可控性随着输入视图数量的增加而增强
————
应用:可控3D编辑

<img src="https://img.saraba1st.com/forum/202312/08/052810mhi11ekkpi7pzrns.jpg" referrerpolicy="no-referrer">

<strong>3d65018c-3f94-4f42-aaa0-f41d6b9816d9.jpg</strong> (80.42 KB, 下载次数: 0)

下载附件

2023-12-8 05:28 上传

展示了(a)使用InstructPix2Pix进行个性化编辑的结果；(b)使用DragGAN、DragDiffusion进行拖动编辑；(c)颜色编辑
————
应用:3D角色建模

<img src="https://img.saraba1st.com/forum/202312/08/052816q7cni4nnti5nhcz8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231208-052622.jpg</strong> (47.25 KB, 下载次数: 0)

下载附件

2023-12-8 05:28 上传

展示了一些多视图2D绘画中的复杂3D角色的新视图合成和重建结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1048#       发表于 2023-12-8 20:02

Alpha-CLIP

专注于您关注的任何地方的CLIP模型

项目主页:https://aleafy.github.io/alpha-clip/

github项目代码仓库:https://github.com/SunzeY/AlphaCLIP

对比语言图像预训练(CLIP/Contrastive Language-Image Pre-training)在从不同任务的图像中提取有价值的内容信息方面发挥着至关重要的作用，以对齐文本和视觉方式来理解整张图像，包括所有细节，甚至是那些与特定任务无关的细节

然而，为了更好地理解和控制图像编辑过程，关注特定的感兴趣区域变得至关重要，这些区域可以由人类或感知模型用点、掩码或框进行表示

为了满足这些要求，引入了Alpha-CLIP，这是CLIP的增强版本，带有辅助alpha通道推荐关注区域，并使用构建的数百万个RGBA区域文本对(RGBA region-text pairs)进行了微调

Alpha-CLIP不仅保留了CLIP的视觉识别能力，还可以通过精确控制强调图像内容，它展示了在各种任务中的有效性，包括但不限于开放世界识别、多模态大语言模型和条件2D/3D生成，拥有作为图像相关任务的多功能工具的强大潜力
————
1.图像识别中的Alpha-CLIP，通过关注指定的基准答案区域可以使零样本ImageNet分类任务的top-1准确率提高4.1%，这种增强的基于区域的识别对于引用表达理解 (REC/Referring Expression Comprehension)等任务非常有价值，并且可以作为开放词汇检测任务(OVD/Open Vocabulary Detection)的数据引擎

2.作用MLLM的视觉骨干，与大型语言模型相结合，Alpha-CLIP能够在MLLM框架(例如BLIP-2、LLaVA)上提升区域级字幕说明和VQA，这种集成显著减少了幻觉的发生并减少了模型偏差，同时还支持以区域为焦点的新任务

3.2D生成中的Alpha-CLIP，当与扩散模型集成时，Alpha-CLIP增强了BLIP-Diffusion 在图像变种任务(image variation tasks)中的可控性，此外，它还能够从复杂图像中提取主题以进行主题驱动生成，克服了在BLIP-Diffusion中部署原始CLIP时遇到的障碍，后者仅支持简单图像中的单个主题

4.3D生成中的Alpha-CLIP，除了2D生成能力外，Alpha-CLIP还展现了3D生成能力，可以与Point-E等扩散模型结合进行有效部署，以提高3D对象生成的质量，此外，它还可以与NeRF(例如PureCLIPNeRF)结合使用，以优化高级3D对象的创造
————
Alpha-CLIP工作流程

<img src="https://img.saraba1st.com/forum/202312/08/200253fzdsy6sp4080nkc6.png" referrerpolicy="no-referrer">

<strong>pipeline.png</strong> (988.82 KB, 下载次数: 0)

下载附件

2023-12-8 20:02 上传

数据生成方法和模型架构的工作流程
(a)生成数百万个RGBA区域文本对
(b)Alpha-CLIP修改了CLIP图像编码器以获取额外的Alpha通道以及 RGB，首先从基础和分类数据集中生成数百万个RGBA区域文本数据，然后使用生成的数据，在额外的Alpha通道输入训练Alpha-CLIP
————
Alpha-CLIP用法

Alpha-CLIP可以在广泛的下游任务中增强CLIP，通过应用渗透到不同领域的插件方法，涵盖2D和3D应用中的，从感知到生成的各个领域，在下面的图表中展示了Alpha-CLIP的下游任务及其相对于原始CLIP的优势

<img src="https://img.saraba1st.com/forum/202312/08/195905nrxi8sq878flcrvx.jpg" referrerpolicy="no-referrer">

<strong>8e1090f4-2a6d-4599-888f-6c8b1b20274c.jpg</strong> (181.94 KB, 下载次数: 0)

下载附件

2023-12-8 19:59 上传

<img src="https://img.saraba1st.com/forum/202312/08/195904naiasw42wcbdw0cv.png" referrerpolicy="no-referrer">

<strong>usage_table1.png</strong> (95.46 KB, 下载次数: 0)

下载附件

2023-12-8 19:59 上传

————
图像识别中的Alpha-CLIP

Alpha-CLIP增强了原始CLIP的区域识别能力，可以根据感兴趣的区域将alpha通道输入设置为全1，获取复杂图像中精确的对象类别，图示如下

<img src="https://img.saraba1st.com/forum/202312/08/195919kifij2jwki2ees2i.png" referrerpolicy="no-referrer">

<strong>recog_demo.png</strong> (207.7 KB, 下载次数: 0)

下载附件

2023-12-8 19:59 上传

在ImageNet上使用不同的alpha-map级别测试原始CLIP和Alpha-CLIP的识别能力，结果如下

<img src="https://img.saraba1st.com/forum/202312/08/195927xuvvbbyq11b307gb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231208-195808.jpg</strong> (33.07 KB, 下载次数: 0)

下载附件

2023-12-8 19:59 上传

ImageNet-S上具有不同alpha map级别的零样本分类，当前景掩码不可用时，Alpha-CLIP与原始CLIP相当，并通过矩形框或掩码alpha map进一步提升了性能
————
MLLM中的Alpha-CLIP

用Alpha-CLIP替换了BLIP-2和LLaVA-1.5中使用的 CLIP，使MLLM能够直接关注视觉语言任务中的用户定义区域，例如区域级字幕说明和VQA，这里显示的所有用例都是简单地用插件Alpha-CLIP替换BLIP2或LLaVA-1.5的原始CLIP，无需进一步微调

<img src="https://img.saraba1st.com/forum/202312/08/200010dzaaiv6o1ai7uple.jpg" referrerpolicy="no-referrer">

<strong>12ce1ec7-e08d-40c3-81c1-5fd9725636f6.jpg</strong> (423.55 KB, 下载次数: 0)

下载附件

2023-12-8 20:00 上传

除了定性结果之外，还提供了Alpha-CLIP在LLaVA-1.5上的Visual Genome和RefCOCOg数据集的定量区域字幕说明结果

<img src="https://img.saraba1st.com/forum/202312/08/200018chhvhbsb9lvyllyh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231208-195952.jpg</strong> (48.29 KB, 下载次数: 0)

下载附件

2023-12-8 20:00 上传

Alpha-CLIP在区域级字幕说明中的性能:报告了在Visual Genome和refCOCOg数据集上的METEOR和CIDEr指标，展示了竞争性的性能结果
————
图像变种中的Alpha-CLIP

Alpha-CLIP可用于大多数使用CLIP图像编码器的图像变种模型，例如，BLIP-Diffusion将CLIP和stable-diffusion与Q-former结合起来，以生成和编辑由文本控制的2D图像，通过引入Alpha-CLIP，可以添加一组额外的视觉提示，使模型能够专注于指定区域进行2D生成，从而实现复杂图像中的主题驱动生成，每三行的第一行是原始BLIP-Diffusion生成的图像，其他行则代表Alpha-CLIP的指定掩码生成结果，其中突出显示为红色

<img src="https://img.saraba1st.com/forum/202312/08/200056n449crc94sf4ercr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231208-200037.jpg</strong> (572.63 KB, 下载次数: 0)

下载附件

2023-12-8 20:00 上传

————
3D对象生成中的Alpha-CLIP

 Point-E的Alpha-CLIP
证明Alpha-CLIP在两种情况下很有帮助:
1.当Point-E生成的点云有部分缺失时，用户可以在条件图像中突出显示缺失部分，以提醒扩散模型更加关注该部分并修复此缺失部分问题
2.用户可以在2D图像上强调需要的部分

<img src="https://img.saraba1st.com/forum/202312/08/200149bb3mp5cfdggbpmhy.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231208-200107.jpg</strong> (96.61 KB, 下载次数: 0)

下载附件

2023-12-8 20:01 上传

PureCLIPNeRF中的Alpha-CLIP
在PureCLIPNeRF中用Alpha-CLIP替换了CLIP模型来生成3D对象，并在有和没有背景增强的情况下进行了测试，如下图所示，使用Alpha-CLIP，PureCLIPNeRF生成的对象在形状和颜色方面与提供的文本提示(尤其是粗体文本)紧密一致，此外，生成的对象的整体连贯性也得到了增强，并且具有显著的美学质量

<img src="https://img.saraba1st.com/forum/202312/08/200159ncxn06q1zxn101s1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231208-200120.jpg</strong> (190.78 KB, 下载次数: 0)

下载附件

2023-12-8 20:01 上传

————
Alpha-CLIP注意力图可视化

 检查了视觉编码器中最后一个Transformer块中[CLS]Token的注意力图，每四行的第一行来自原始CLIP，其他三行来自Alpha-CLIP，其中用户定义的焦点区域标记为红色，该可视化验证了Alpha-CLIP更关注要关注的区域，更重要的是，没有损坏原始CLIP的特征位置中保留的2D位置信息

<img src="https://img.saraba1st.com/forum/202312/08/200239zokvio684uo6eze2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231208-200225.jpg</strong> (400.11 KB, 下载次数: 0)

下载附件

2023-12-8 20:02 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1049#       发表于 2023-12-9 06:34

 本帖最后由 Machinery 于 2023-12-9 06:42 编辑 

StripedHyena-7B

为高效架构铺平道路的开源模型，一睹Transformer之外的世界

相关博客:https://www.together.ai/blog/stripedhyena-7b

hugface基础模型StripedHyena-Hessian-7B (SH 7B)权重下载:https://huggingface.co/togethercomputer/StripedHyena-Hessian-7B

hugface聊天模型StripedHyena-Nous-7B (SH-N 7B)权重下载:https://huggingface.co/togethercomputer/StripedHyena-Nous-7B

在Together Playground上与模型一起玩耍:https://api.together.xyz/playground/chat/togethercomputer/StripedHyena-Nous-7B

<img src="https://img.saraba1st.com/forum/202312/09/063025zzg440rg04go49vq.jpg" referrerpolicy="no-referrer">

<strong>16faa83e-534b-43ec-836f-e03275af0585.jpg</strong> (128.96 KB, 下载次数: 0)

下载附件

2023-12-9 06:30 上传

Together Research的研究重点领域之一是针对Transformer架构的长上下文、改进的训练和推理性能的新架构，源于研究团队和学术合作者的一项研究项目，受到植根于信号处理启发的序列模型，很高兴推出StripedHyena模型，此版本包括基本模型StripedHyena-Hessian-7B (SH 7B)和聊天模型StripedHyena-Nous-7B (SH-N 7B)，StripedHyena借鉴了过去一年中设计高效序列建模架构的许多经验教训:H3、Hyena、HyenaDNA和Monarch Mixer

<img src="https://img.saraba1st.com/forum/202312/09/063047hnl9hscmmhmspcel.jpg" referrerpolicy="no-referrer">

<strong>afa154b1-9bf3-4db4-92cb-087fa3746312.jpg</strong> (21.67 KB, 下载次数: 0)

下载附件

2023-12-9 06:30 上传

————
1.StripedHyena是第一个在短上下文和长上下文评估中与最佳开源Transformer竞争的替代模型，相同的基础模型在OpenLLM排行榜任务上实现了与Llama-2、Yi和Mistral 7B相当的性能，而在长上下文摘要方面表现甚至优于这些模型

2.对于长序列训练、微调和生成，StripedHyena速度更快、显存效率更高，除了注意力之外，高效推理的一个核心计算原型是状态空间模型(SSM/state-space model)层，它建立在S4等开创性工作的基础上，能够将卷积层转换为递归，利用基于门控卷积的快速内核(FlashFFTConv)和高效Hyena推理的最新研究，StripedHyena在长度为32k、64k 和 128k的序列上的端到端训练中速度提高了&gt;30%、&gt;50%和&gt;100%，与使用FlashAttention v2和自定义内核优化的Transformer基线相比，用于自回归生成的StripedHyena缓存比使用分组查询注意力的同等大小的Transformer小50%以上

3.StripedHyena的设计利用了对高效构架缩放定律的最新研究，特别是，StripedHyena是Hyena算子中注意力和门控卷积的混合体，通过计算最佳缩放协议，确定了几种在架构级别改进Transformers(Chinchilla)基线缩放法则的方法，例如混合化(hybridization)，通过这些技术，能够在每个训练计算预算下获得比Transformer更高质量的模型，并在推理时获得额外的好处

4.StripedHyena使用一组新的模型移植技术进行了优化，使之能够在训练期间更改模型架构，StripedHyena是通过移植Transformers和Hyena的架构组件获得的，并在RedPajama数据集的混合上进行训练，并用更长的上下文数据进行了增强

期待能够进一步突破模型架构的边界，以实现快速训练和推理，从而使我们能够改进现有的缩放法则，并在每个计算预算下获得更高质量的基础模型
————
适用于短期和长期上下文任务的单一架构‍

在过去的一年里，Together AI团队和Hazy Research的合作者一直致力于为语言和其他领域设计新的序列模型，这些架构取代了注意力，成为负责混合嵌入序列的主要算子，并用计算成本更低的替代方案替换它们，还开发了几种模型(H3、Hyena)，用隐式门控卷积(implicit gated convolutions)和门控SSMs取代了注意力，并训练了一些在语言上与Transformer相媲美的第一个替代架构
————
评估

通过一系列基准测试来评估StripedHyena，以确定短上下文任务的性能，并测试其处理长提示的能力

首先，在古腾堡计划的一部分书籍(a subset of books from Project Gutenberg)上测试了困惑度缩放，计算了每个样本的最后2048个Token的困惑度，并通过在StripedHyena的提示中包含越来越长的前缀来重复实验，根据样本的结构，观察到不同的行为；困惑度要么在32k处饱和(在训练的最后阶段看到的输入长度)，要么在超过32k时持续减少，这表明该模型能够合并来自较长提示的一些信息

<img src="https://img.saraba1st.com/forum/202312/09/063118rekeix0toznynon1.png" referrerpolicy="no-referrer">

<strong>65732f121802735f813cafb9_PastedGraphic-5.png</strong> (727.38 KB, 下载次数: 0)

下载附件

2023-12-9 06:31 上传

从古腾堡收藏中采样的书籍的上下文长度缩放，当模型通过更长的提示输入额外的上下文时，损失会减少

较长上下文的质量使StripedHyena成为了一种高效的基线通用模型，在摘要和较长上下文任务方面可与Mistral 7B竞争:

<img src="https://img.saraba1st.com/forum/202312/09/063204uosqz1lspopjjzmp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231209-063142.jpg</strong> (43.2 KB, 下载次数: 0)

下载附件

2023-12-9 06:32 上传

在ZeroScrolls的零样本、长上下文任务上对StripedHyena-Hessian-7B (SH 7B)和Mistral 7B进行基准测试

StripedHyena是第一个可与相同大小或更大规模的强大Transformer基础模型竞争的替代架构，在短上下文任务(包括OpenLLM排行榜任务)上，StripedHyena的表现优于Llama-2 7B、Yi 7B和最强的Transformer替代品(例如RWKV 14B)注:这里使用的是RWKV Raven 14B

<img src="https://img.saraba1st.com/forum/202312/09/063224siuumqff4fukfbmo.jpg" referrerpolicy="no-referrer">

<strong>f071b45c-0c6e-4680-bf43-1061a154d31d.jpg</strong> (58.72 KB, 下载次数: 0)

下载附件

2023-12-9 06:32 上传

标准短上下文的平均值，基准:“arc-challenge”、“mmlu”、“boolq”、“winogrande”、“hellaswag”、“truthfulqa”，使用OpenLLM排行榜中的少样本配置，SH 7B是第一个替代模型，其性能可与相同尺寸或​​更大尺寸的最佳Transformer基线相媲美

很高兴与Nous Research的合作者一起发布StripedHyena-Nous- 7B(SH-N 7B)，这是一个聊天模型，采用针对StripedHyena架构量身定制的新微调配方构建
————
了解架构设计空间：改善缩放的多种方法

混合化

在扩展实验的早期，注意到一个一致的趋势:在给定的计算预算的情况下，由不同关键层的混合构建的构架总是优于同质构架，这些观察结果与各种论文中描述的结果相呼应:H3、MEGA(其他等)，并发现了与GPT-3(来自Sparse Transformers)和GPTNeo的混合全局局部注意力设计更早的联系

为了了解这一现象，以及缩放系数的改进(例如，预算中每次浮点运算(FLOP)的预期损失减少)，通过对一类架构进行了广泛的计算优化缩放分析，发现由多头注意力、门控MLPs和门控卷积组成的混合体在计算预算上优于强大的Transformer架构(例如Llama)，并确定了在顺序和数量上混合这些组件的最佳方法

<img src="https://img.saraba1st.com/forum/202312/09/063303br2350fmjwcxqpw0.png" referrerpolicy="no-referrer">

<strong>65734be22ed8d1eca69a9876_graph23.png</strong> (164.76 KB, 下载次数: 0)

下载附件

2023-12-9 06:33 上传

[左]不同架构的困惑度缩放，作为计算预算的函数
[右]每个计算预算下计算最佳模型的最佳混合比例

上图中的所有点，每个点代表一个训练设置(模型大小、架构和Token总数)，都是计算最优的

<img src="https://img.saraba1st.com/forum/202312/09/063319f94w37fo49tgnbyz.png" referrerpolicy="no-referrer">

<strong>65734b5af10b77767f02d895_graph22.png</strong> (227.7 KB, 下载次数: 0)

下载附件

2023-12-9 06:33 上传

困惑度缩放分析，遵循计算最优协议，并为基础架构和混合架构确定了每个FLOP组(每个组通过不同颜色表示)的最佳模型大小，为了最大限度地减少超参数对不同架构的影响，从优化实验的子集中推导出超参数缩放定律，混合化提高了在计算最优边界之外执行的训练的扩展性和稳健性

与我们的学术合作伙伴一起开发理论和综合任务，以了解这种情况如何以及为何发生，已经确定了各种机制，其中各层专门处理序列建模的特定子任务，为进一步的架构优化提供有价值的信号，这延续了在机制设计方面的一般工作路线，其中涉及精心构建的小规模的综合任务，以对架构功能进行压力测试
————
多头门控卷积

提高Transformer速率的另一种方法是以门控卷积中的多头形式引入额外的计算，这种设计受到线性注意力的启发，已在H3和MultiHyena等架构中得到验证，并且在编码的关联回忆回路方面被证明更有效

<img src="https://img.saraba1st.com/forum/202312/09/063344ddqq2dch2docovch.png" referrerpolicy="no-referrer">

<strong>6573717223a903c3f413a3bd_white lines.png</strong> (67.6 KB, 下载次数: 0)

下载附件

2023-12-9 06:33 上传

通过计算优化缩放来验证各种架构改进
 ‍
这些是可以改善Transformer扩展性的众多架构设计技术中的两种，对于StripedHyena，特别关注了注意力和门控卷积之间的协同作用
————
语言模型计算占用的转变:更便宜的微调，更快的推理

优化基于不同架构构建的模型需要重新考虑训练、微调和推理的计算权衡，对于这些新架构，出现了一组不同的计算瓶颈，很自豪能够开发出支持这些模型的关键技术，例如FlashFFTConv及其前身

对于长序列上的训练和微调工作负载，SH 7B始终比优化的Transformer更快(比FlashAttention v2处理长度为32k、64k和128k的序列的端到端快&gt;10%、&gt;20%和&gt;50%， 在批大小1的情况下) ，随着序列更长和批大小更大，加速比会变得更迅猛，StripedHyena模型是长上下文任务微调的最佳候选者，对于长度为128k的任务，在相同预算的情况下，SH 7B可以微调两倍于Transformer的Token

<img src="https://img.saraba1st.com/forum/202312/09/063414w9ox0z9bqav2q788.png" referrerpolicy="no-referrer">

<strong>65732f3e6bb6da558f966bb8_PastedGraphic-4.png</strong> (737.65 KB, 下载次数: 0)

下载附件

2023-12-9 06:34 上传

与SH 7B相比，优化的Transformer 7B(FlashAttention v2和自定义内核)的端到端批大小1延迟

这些改进是由混合架构中不同的渐近缩放和各层计算配置文件驱动的，期待更快的模型以及精细的混合比例和层数
————
减少推理显存

与Transformer(具有分组查询注意力)相比，SH 7B的另一项优势是在自回归生成过程中显存占用减少了50%以上，在Transformers中，每层的键和值在预填充阶段都会被缓存，以避免重新计算并加速增量解码，门控卷积层在推理过程中引入了更多的自由度，因为有多种方法可以表示和优化计算，在最近关于Hyena卷积的蒸馏和表征的研究中探索了这些权衡，这些新技术已在SH 7B中使用，通过识别和修剪冗余状态来进一步减少显存占用

<img src="https://img.saraba1st.com/forum/202312/09/063439izc5cz4x6zvv43m3.png" referrerpolicy="no-referrer">

<strong>65732f59425c945fc9fbfe71_PastedGraphic-6.png</strong> (864.49 KB, 下载次数: 0)

下载附件

2023-12-9 06:34 上传

GQA Transformer和StripedHyena的推理缓存的显存占用，包括键值缓存和卷积状态(FIR和IIR)
————
从信号处理到语言模型
 ‍
StripedHyena的灵活性是线性系统(卷积、模态、规范)的多重等效表示和参数化存在的直接结果，每种形式都更适合特定的训练和推理工作负载

借用经典信号处理过程的术语，SH卷积过滤器可以广泛地视为有限(FIR)或无限(IIR)，卷积的FIR缓存类似于注意力机制中的标准键值缓存(kv缓存)，尤其是滑动窗口类型，并且显存占用会不断增长(直到达到最大值)

另一方面，IIR过滤器可以通过缓存恒定大小的状态来应用，然后在解码期间通过循环步骤进行更新，IIR表征本身可以自我定制(itself be customized)，与kv缓存相比，固定大小状态在推理堆栈级(inference stack level)开启了几个关键优化，简化了连续批处理和推测解码(speculative decoding)等技术
————
未来会发生什么

使用StripedHyena模型的主要目标是将架构设计的前沿推向Transformer之外，StripedHyena 仅触及了通过机制设计和缩放法则进行了仔细架构设计以及混合化、隐式卷积和状态缓存等思想的一部分结果，希望这些模型能够激励开源社区探索具有不同架构的新的令人兴奋的构建

在未来的版本中，还将探索:

具有更长上下文的更大模型
多模态支持
进一步的性能优化
将StripedHyena集成到检索工作流程中，以充分利用更长的上下文
————
致谢

如果没有HazyResearch、Hessian.AI、Nous Research、MILA、HuggingFace、DFKI的合作者，这项工作就不可能完成

感谢Hessian.AI创新实验室和hessian.AISC服务中心的合作和共同使的AI超级计算机forty-two，还要特别感谢德国人工智能中心(DFKI)

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  naiveyan  
##### 1050#       发表于 2023-12-9 12:03

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=62177923&amp;ptid=2126390" target="_blank">Machinery 发表于 2023-8-26 23:50</a>

评测榜单一直是不太全的，更多的属于是给人一个大致印象的模型能力，更何况llama2出的比较晚，算是近期的 ...</blockquote>
[https://opencompass.org.cn/model-detail/RWKV-5-3B](https://opencompass.org.cn/model-detail/RWKV-5-3B)

rwkv也开始打榜了，不过3b版本的成绩并不突出<img src="https://static.saraba1st.com/image/smiley/face2017/068.png" referrerpolicy="no-referrer">


*****

####  Machinery  
##### 1051#       发表于 2023-12-9 12:05

 本帖最后由 Machinery 于 2023-12-9 12:10 编辑 
<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63271970&amp;ptid=2126390" target="_blank">naiveyan 发表于 2023-12-9 12:03</a>
https://opencompass.org.cn/model-detail/RWKV-5-3B

rwkv也开始打榜了，不过3b版本的成绩并不突出[f:068 ...</blockquote>
<img src="https://static.saraba1st.com/image/smiley/face2017/037.png" referrerpolicy="no-referrer">V5在打，V6在练，V7在研究，前途光明

<img src="https://img.saraba1st.com/forum/202312/09/121000a3oqnnu0qlqdq34o.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231209-120929.jpg</strong> (113.04 KB, 下载次数: 0)

下载附件

2023-12-9 12:10 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1052#       发表于 2023-12-10 05:01

AnimateZero

视频扩散模型是零样本图像动画师

项目主页:https://vvictoryuki.github.io/animatezero.github.io/

github项目仓库:https://github.com/vvictoryuki/AnimateZero

近年来大型文本到视频(T2V/text-to-video)扩散模型在视觉质量、运动和时间一致性方面取得了巨大进步，然而，生成过程仍然是一个黑箱，所有属性(例如外观、运动)都是联合学习和生成的，除了粗略的文本描述之外，没有任何精确的控制能力

受图像动画化将视频作为一种特定外观与相应运动解耦的启发，提出了AnimateZero，揭示了预训练的文本到视频扩散模型，例如AnimateDiff，为其提供更精确的外观和运动控制的能力

对于外观控制，借用了文本到图像(T2I)生成中的中间潜在(intermediate latents)及其特征，以确保生成的第一帧等于给定的生成图像

对于时间控制，用提案的位置校正窗口注意力(positional-corrected window attention)替换了原始T2V模型的全局时间注意力(global temporal attention)，以确保其他帧能与第一帧很好地对齐

借助所提出的方法，AnimateZero在无需进一步训练的情况下即可成功控制生成进度，作为给定图像的零样本图像动画师，AnimateZero还支持多种新应用，包括交互式视频生成和真实图像动画化，详细的实验证明了该方法在T2V和相关应用中的有效性

<img src="https://img.saraba1st.com/forum/202312/10/050015e5n0c0tcl0qt5att.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231210-045549__01.jpg</strong> (578.18 KB, 下载次数: 0)

下载附件

2023-12-10 05:00 上传

提出的AnimateZero修改了文本到视频扩散模型AnimateDiff的构架，以实现更可控(例如，使用预先训练的文本到图像模型生成的图像控制外观)的视频生成，而无需进一步训练 ，上述结果证明了AnimateZero在从生成图像的完全相同的域生成动画与视频方面的有效性，这些个性化图像领域包括动画风格、素描风格、像素艺术风格和写实风格等

<img src="https://img.saraba1st.com/forum/202312/10/050021k9u9l97uajluu6xx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231210-045600__01.jpg</strong> (83.4 KB, 下载次数: 0)

下载附件

2023-12-10 05:00 上传

AnimateDiff中扩散UNet的构架，它将视频扩散模型解耦为两种模块：空间模块负责生成外观，运动模块负责生成运动

<img src="https://img.saraba1st.com/forum/202312/10/050026y2pr5q8ji55i40bz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231210-045610__01.jpg</strong> (429.75 KB, 下载次数: 0)

下载附件

2023-12-10 05:00 上传

提案的AnimateZero的整体流程，给定来自预训练T2I模型的空间模块及其相应的运动模块，首先使用T2I模型生成单张图像I1，然后根据该图像生成动画化视频

左侧部分显示了具有中间潜在和提出的空间外观控制的图像生成过程，空间外观控制对空间模块进行修改，包括用于确保第一帧等于I1的潜在插入，以及在其他帧之间共享第一帧的空间自注意力的键和值，以对齐语义和风格

右侧部分是时间一致性控制，对AnimateDiff中的原始自注意力进行了修改，这是一个全局注意力，如(a)所示，修改包括三个关键点(如b所示):
(1)将全局注意力替换为窗口注意力，它仅使用前面的i帧来计算第i个输出Token
(2)重复使用第一个Token计算的相似度，以强调第一帧I1的重要性
(3)纠正添加到输入Token中的位置嵌入(在q和k的上标中标记为红色，qkv的计算由式2描述)以获得更好的结果

<img src="https://img.saraba1st.com/forum/202312/10/050032beyqetsenywbyeyw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231210-045622__01.jpg</strong> (733.17 KB, 下载次数: 0)

下载附件

2023-12-10 05:00 上传

AnimateDiff和提案的AnimateZero之间的定性对比结果

如图(a)、(b)和(c)所示，AnimateDiff生成的视频与生成的图像不在同一域中，相比之下，AnimateZero能够保持与原始T2I域的一致性

在(a)、(c)和(d) 中，证明AnimateDiff可能会遇到提供的文本和生成的帧(以红色突出显示)之间不一致的问题，而AnimateZero在这个问题上表现更好

<img src="https://img.saraba1st.com/forum/202312/10/050037wkm4rku94kqzu44b.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231210-045629__01.jpg</strong> (57.98 KB, 下载次数: 0)

下载附件

2023-12-10 05:00 上传

AnimateDiff和AnimateZero之间的定量对比结果，AnimateZero与文本和原始T2I域表现出更高的相似性

<img src="https://img.saraba1st.com/forum/202312/10/050042cq2aqo5i51arqis1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231210-045640__01.jpg</strong> (628.18 KB, 下载次数: 0)

下载附件

2023-12-10 05:00 上传

公开可用的图像到视频工具与提案的AnimateZero之间的定性对比结果

<img src="https://img.saraba1st.com/forum/202312/10/050047s8ccwp2ap89ovb44.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231210-045645__01.jpg</strong> (228.9 KB, 下载次数: 0)

下载附件

2023-12-10 05:00 上传

公开的图像到视频工具和提案的AnimateZero之间的定量对比结果，提出的AnimateZero在多个指标中展示了最佳性能，或者在其他指标中取得了与最佳方法相当的结果，性能最佳方法的指标以红色突出显示，而次佳方法的指标以蓝色突出显示

<img src="https://img.saraba1st.com/forum/202312/10/050052a5w5gwuw50cwspd5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231210-045653__01.jpg</strong> (870.23 KB, 下载次数: 0)

下载附件

2023-12-10 05:00 上传

消融实验演示:
(a)AnimateDiff生成的视频
(b)+插入生成的给定图像的中间潜在
(c)+共享给定的生成图像的键和值
(d)+无位置校正的时间一致性控制(TCC w/o PC)
(e)+带位置校正的时间一致性控制(TCC w/ PC)

<img src="https://img.saraba1st.com/forum/202312/10/050057iuylvvxbz27iv1hl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231210-045701__01.jpg</strong> (121.23 KB, 下载次数: 0)

下载附件

2023-12-10 05:00 上传

AnimateZero受到Animate-Diff运动先验的限制，并且两者在复杂运动中都表现不佳

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1053#       发表于 2023-12-10 05:46

 本帖最后由 Machinery 于 2023-12-10 05:48 编辑 

HyperDreamer

从单张图像生成和编辑超真实3D内容

项目主页:https://ys-imtech.github.io/HyperDreamer/

github项目仓库:https://github.com/wutong16/HyperDreamer

从单张图像创造3D内容是一项长久存在但非常令人渴望的任务，最近的进展通过引入了2D扩散先验，产生了合理的结果，然而，现有方法对于生成后的使用来说并不足够真实，因为用户无法全方位查看、渲染和编辑生成的3D内容

为了应对这些挑战，推出了具有几个关键设计和非常有吸引力的HyperDreamer:
1.可查看:具有高分辨率纹理的360度网格建模可以通过全方位的观察创造视觉上引人注目的3D模型
2.可渲染:细粒度语义分割和数据驱动先验被纳入指导，以学习材料的合理反照率(albedo)、粗糙度(roughness)和镜面反射(specular properties)，从而实现语义感知的任意材质估计(semantic-aware arbitrary material estimation)
3.可编辑:对于生成的模型或自己的数据，用户可以通过几次点击交互式选择任何区域，并通过基于文本的指导有效地编辑纹理

大量实验证明了HyperDreamer在使用高分辨率纹理对区域感知材质进行建模并实现用户友好的编辑方面的有效性，相信HyperDreamer有望推动3D内容的创造并在各个领域得到应用

<img src="https://img.saraba1st.com/forum/202312/10/054340j9u6v98xese6at9p.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231210-053651__01.jpg</strong> (333.71 KB, 下载次数: 0)

下载附件

2023-12-10 05:43 上传

概览图，给定单个RGB图像，可以生成具有丰富细节的逼真3D模型，同时全方位可视、可渲染和可编辑

<img src="https://img.saraba1st.com/forum/202312/10/054347ln77n2lx26x3jz5l.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231210-053702__01.jpg</strong> (469.81 KB, 下载次数: 0)

下载附件

2023-12-10 05:43 上传

3D生成与编辑工作流程概览图，将扩散先验、语义先验和去渲染先验引入到这个高度约束下的问题中，以在生成后通过材质建模和交互式编辑来实现高分辨率纹理

<img src="https://img.saraba1st.com/forum/202312/10/054453zmhm88zei5inzppv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231210-053715__01.jpg</strong> (77.56 KB, 下载次数: 0)

下载附件

2023-12-10 05:44 上传

处于生成阶段的SAM，与原始SAM结果相比，有效地聚类了简洁的语义组

<img src="https://img.saraba1st.com/forum/202312/10/054501f7s7ir131v6hhhos.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231210-053715__02.jpg</strong> (167.47 KB, 下载次数: 0)

下载附件

2023-12-10 05:45 上传

扩散偏置，d中的2D扩散偏置导致b中的3D生成失败，这可以通过c中的反照率正则化来缓解

<img src="https://img.saraba1st.com/forum/202312/10/054508bbtljjl4elyf06lz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231210-054024__01.jpg</strong> (206.54 KB, 下载次数: 0)

下载附件

2023-12-10 05:45 上传

交互式编辑过程，用户可以选择感兴趣的区域，然后本文方法将目标区域的纹理掩码输出到纹理合成工作流程以进行文本引导编辑

<img src="https://img.saraba1st.com/forum/202312/10/054520u4izq1uoipsq0p08.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231210-053739__01.jpg</strong> (396.08 KB, 下载次数: 0)

下载附件

2023-12-10 05:45 上传

定性对比，HyperDreamer生成高保真的参考视图，并在新视图上生成更加真实合理的结果

<img src="https://img.saraba1st.com/forum/202312/10/054603mlleftcey188l07a.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231210-053744__01__01.jpg</strong> (56.81 KB, 下载次数: 0)

下载附件

2023-12-10 05:46 上传

本文方法数据的定量结果

<img src="https://img.saraba1st.com/forum/202312/10/054530v34fa41eo9ia9dda.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231210-053744__02.jpg</strong> (52.43 KB, 下载次数: 0)

下载附件

2023-12-10 05:45 上传

DTU数据集的定量结果

<img src="https://img.saraba1st.com/forum/202312/10/054608ol6468amownwmwmt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231210-053759__01.jpg</strong> (169.52 KB, 下载次数: 0)

下载附件

2023-12-10 05:46 上传

超分辨率(SR)模块上的消融，纹理上的高频细节是在SR监督下生成的

<img src="https://img.saraba1st.com/forum/202312/10/054637ruiurrirjmexulii.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231210-053805__01.jpg</strong> (159.96 KB, 下载次数: 0)

下载附件

2023-12-10 05:46 上传

材质建模分析，在a中展示了输出粗糙度和镜面反射贴图的示例，以及Blender中的渲染结果，展示了参考视图中的反照率损失如何帮助减轻b中的反照率纹理的阴影和反射学习

<img src="https://img.saraba1st.com/forum/202312/10/054645piu60qv0gmuubcxt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231210-053759__02.jpg</strong> (165.05 KB, 下载次数: 0)

下载附件

2023-12-10 05:46 上传

分析了网格分割方案，本文方法具有更好的处理复杂情况的能力

<img src="https://img.saraba1st.com/forum/202312/10/054649gti88ztyytar88dy.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231210-053840__01.jpg</strong> (327.65 KB, 下载次数: 0)

下载附件

2023-12-10 05:46 上传

HyperDreamer提供的其他结果以及更多视图，最后一列中的图像分别是镜面反射图和粗糙度图

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1054#       发表于 2023-12-12 02:10

 本帖最后由 Machinery 于 2023-12-12 02:12 编辑 

DreaMoving

基于扩散模型的人类舞蹈视频生成框架

项目主页:https://dreamoving.github.io/dreamoving/

github项目仓库:https://github.com/dreamoving/dreamoving-project

在本文中，提出了DreaMoving，一种基于扩散的可控视频生成框架，用于生成高质量的定制人类舞蹈视频，具体来说，给定目标身份和姿态序列的情况下，DreaMoving可以生成以目标身份在姿态序列驱动下在任何地方跳舞的视频，为此，提出了一个用于运动控制的视频ControlNet和一个用于身份保留的内容指导者，所提出的模型易于使用，并且可以适应大多数风格化的扩散模型以生成不同的结果

<img src="https://img.saraba1st.com/forum/202312/12/021016pfv2l7bgyy8fygz7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231212-020712__01.jpg</strong> (365.82 KB, 下载次数: 0)

下载附件

2023-12-12 02:10 上传

DreamMoving概览图，视频ControlNet是在每个U-Net块之后注入运动块(motion blocks)的图像ControlNet，视频ControlNet将控制序列(姿态或深度)处理为额外的时间残差(temporal residuals)，去噪U-Net是Stable Diffusion U-Net派生的，具有用于视频生成的运动块，内容指导者将输入文本提示和外观表情，例如人脸(衣服是可选项)，转换到内容嵌入以进行交叉注意力

<img src="https://img.saraba1st.com/forum/202312/12/021021uzs3ywesiz73337z.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231212-020722__01.jpg</strong> (850.62 KB, 下载次数: 0)

下载附件

2023-12-12 02:10 上传

以文本提示作为输入的DreaMoving结果

<img src="https://img.saraba1st.com/forum/202312/12/021025aesy42ejyj3xoz6d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231212-020735__01.jpg</strong> (577.12 KB, 下载次数: 0)

下载附件

2023-12-12 02:10 上传

以文字提示和人脸图像作为输入的DreaMoving结果

<img src="https://img.saraba1st.com/forum/202312/12/021030md0p54ppkojz9sr5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231212-020746__01.jpg</strong> (694.74 KB, 下载次数: 0)

下载附件

2023-12-12 02:10 上传

以面部和衣服图像作为输入的DreaMoving结果

<img src="https://img.saraba1st.com/forum/202312/12/021034v4h6s4gpsut6r4tp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231212-020800__01.jpg</strong> (498.24 KB, 下载次数: 0)

下载附件

2023-12-12 02:10 上传

以风格化图像作为输入的DreaMoving结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1055#       发表于 2023-12-12 04:18

lskd

视觉常识模型(Visual Commonsense Models)的区域化符号知识蒸馏(Localized Symbolic Knowledge Distillation)

github项目主页:https://github.com/jamespark3922/lskd

指令跟随视觉语言(VL/Instruction following vision-language)模型提供灵活的接口以零样本的方式支持广泛的多模态任务，然而，对完整图像进行操作的交互并不能直接使用户能够“指向”并确认图像内的特定区域，此功能不仅对于支持基于参考的VL基准测试很重要，而且对于需要精确的图像内推理的实际应用也很重要

通过构建局部化的视觉常识模型，允许用户指定(多个)区域作为输入，从大型语言模型(LLM)中采样了局部常识知识来训练本文模型

具体来说，通过在给定一组VL模型自动生成的全局文字图像描述和局部文字区域描述的情况下提示LLM收集常识知识，使用单独训练的批判模型(critic model)选择高质量的样本，可以成功地从现有的VL模型中蒸馏局部区域常识语料库以进行训练支持使用参考作为输入

零样本设置中的经验结果和人类评估表明，与将生成的引用表达传递给LLM的基线相比，本文的蒸馏方法可以产生更精确的VL推理模型

<img src="https://img.saraba1st.com/forum/202312/12/041708ejmijxj7k8x9lojx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231212-041307__01.jpg</strong> (645.87 KB, 下载次数: 0)

下载附件

2023-12-12 04:17 上传

LSKD框架的流程
1.使用不同的视觉语言描述来描述图像
2.LLM利用全局和局部描述来生成具有基准的常识知识
3.标注了一小部分数据来监督训练批判模型，该模型可以过滤显示不正确的视觉细节或不连贯的推理实例，批判模型过滤其余生成的语句以确定最终数据池
4.在合成数据上对多模态模型进行微调，以零样本方式支持局部视觉常识推理

<img src="https://img.saraba1st.com/forum/202312/12/041714fd3t8xd9cttbzoww.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231212-041322__01.jpg</strong> (47.86 KB, 下载次数: 0)

下载附件

2023-12-12 04:17 上传

基于BLIP-2的批判模型分析，可以看到添加多类回归损失后可以进一步提高批判模型的性能

<img src="https://img.saraba1st.com/forum/202312/12/041719yvz5d86378e0mvsr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231212-041322__02.jpg</strong> (50.06 KB, 下载次数: 0)

下载附件

2023-12-12 04:17 上传

使用不同阈值过滤语料库大小的批判模型的精度，通过使用监督批判模型来过滤语料库，精度显著提高

<img src="https://img.saraba1st.com/forum/202312/12/041724o2269hi2aq9an7za.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231212-041330__01.jpg</strong> (77.31 KB, 下载次数: 0)

下载附件

2023-12-12 04:17 上传

对于描述的消融实验，当调用ChatGPT生成语料库时，从完整描述中删除其中一个描述，并计算平均批判分数来对各种生成进行评分(越高越好)

<img src="https://img.saraba1st.com/forum/202312/12/041730uuqk05060zqknakn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231212-041330__02.jpg</strong> (56.5 KB, 下载次数: 0)

下载附件

2023-12-12 04:17 上传

人类对有和没有过滤的语料库的判断，从三位人工标注者处获得了李克特量表(Likert scale/从1到3)的平均评分

<img src="https://img.saraba1st.com/forum/202312/12/041736muivrc1tbec101mg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231212-041341__01.jpg</strong> (208.13 KB, 下载次数: 0)

下载附件

2023-12-12 04:17 上传

局部和非局部视觉推理任务的零样本结果

<img src="https://img.saraba1st.com/forum/202312/12/041740ukptfepdlzphi1xx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231212-041347__01.jpg</strong> (129.22 KB, 下载次数: 0)

下载附件

2023-12-12 04:17 上传

过滤阈值控制的数据质量对不同数据集的影响，x轴显示过滤阈值，y轴是以百分比表示的准确度指标，对比了在LLaVA-instruct数据集(红色)和本文模型(蓝色)上训练的模型

<img src="https://img.saraba1st.com/forum/202312/12/041747hqk3xmym2g2gxqz4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231212-041354__01.jpg</strong> (201.17 KB, 下载次数: 0)

下载附件

2023-12-12 04:17 上传

关于BLIP-2 ViT-G训练的消融，使用由人类和机器标注的不同来源的视觉知识语料库进行训练，将视觉推理任务分为需要局部推理和不需要局部推理的视觉推理任务，批判过滤被应用于LSKD语料库(本文的)

<img src="https://img.saraba1st.com/forum/202312/12/041751j0i5a4sc2s2shc6e.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231212-041400__01.jpg</strong> (138.92 KB, 下载次数: 0)

下载附件

2023-12-12 04:17 上传

使用LSKD vs Chat-GPT，对生成模型的描述进行人类评估，如果具有相同的品质，人类会被要求选择更好的生成之一或平局

<img src="https://img.saraba1st.com/forum/202312/12/041756icdqlhnfddf1lqsp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231212-041414__01.jpg</strong> (594.08 KB, 下载次数: 0)

下载附件

2023-12-12 04:17 上传

ChatGPT(教师模型)、针对复杂视觉推理训练的LLAVA和本文模型定性示例对比，问题中提到的每个人都被分配了一个带有边界框的唯一编号，并且提及他们相应的颜色标记，生成结果中的任何错误都会以红色显示

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1056#       发表于 2023-12-13 02:10

LLM360

迈向完全透明的开源LLMs

项目主页:https://www.llm360.ai/

最近开源大型语言模型(LLM)的激增，例如LLaMA、Falcon和Mistral，为人工智能从业者和研究人员提供了多样化的选择，然而，大多数LLM仅发布了部分文件，例如最终模型权重或推理代码，并且技术报告越来越将其范围限制为高层级的设计选择和表面的统计结果，这些选择降低了LLM训练的透明度，并迫使团队需要重新发现训练过程中的许多细节，从而阻碍了该领域的进步

本文提出了LLM360，这是一项完全开源的LLM计划，倡导向社区提供所有的训练代码和数据、模型检查点和中间结果。  LLM360的目标是通过使端到端LLM训练过程透明且可供每个人复制来支持开放和协作的人工智能研究

作为LLM360的第一步，发布了两个从头预训练的7B参数LLM:Amber和CrystalCoder，包括它们的训练代码、数据、中间检查点和分析，通过致力于这项开源工作不断突破LLM的界限，更大规模、更强的型号正在研发中，并将在未来发布

项目截图:

<img src="https://img.saraba1st.com/forum/202312/13/021023ljnf89fdrzn05108.jpg" referrerpolicy="no-referrer">

<strong>DH_upload_刚刚.jpg</strong> (366.07 KB, 下载次数: 0)

下载附件

2023-12-13 02:10 上传


*****

####  Machinery  
##### 1057#       发表于 2023-12-13 06:24

Sherpa3D

通过粗略(Coarse)3D先验提升(Boosting)高保真文本到3D的生成

项目主页:[https://liuff19.github.io/Sherpa3D/](https://liuff19.github.io/Sherpa3D/)

github项目代码仓库:[https://github.com/liuff19/Sherpa3D](https://github.com/liuff19/Sherpa3D)

最近，通过利用2D和3D扩散模型，从文本提示创造3D内容已取得重大进展，虽然3D扩散模型可以保证良好的多视图一致性，但有限的3D数据阻碍了其生成高质量和多样化3D资产的能力

相比之下，2D扩散模型找到了一种蒸馏方法，可以在无需任何3D数据的情况下实现出色的泛化和丰富的细节，然而2D扬升方法(2D lifting methods)存在固有的与视图无关的模糊性，从而导致严重的多面Janus问题，其中文本提示无法提供足够的指导来学习生成连贯的3D结果

相比重新训练成本高昂的视点感知模型，本文研究了如何充分利用易于访问的粗略3D知识来增强提示并指导2D扬升优化以实现细化，在本文中，提出了Sherpa3D，一种新的文本转3D框架，可同时实现高保真度、通用性和几何一致性

具体来说，设计了一对源自3D扩散模型生成的粗略3D先验的指导策略:用于几何保真度(geometric fidelity)的结构指导(structural guidance)和用于3D一致性(3D coherence)的语义指导(semantic guidance)，利用这两种引导，2D扩散模型以多样化和高质量的结果丰富了3D内容

大量实验表明，Sherpa3D在质量和3D一致性方面优于之前的SOTA文本转3D方法

<img src="https://img.saraba1st.com/forum/202312/13/062231jckgtfgz5plc1gpp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231213-061835__01.jpg</strong> (295.2 KB, 下载次数: 0)

下载附件

2023-12-13 06:22 上传

Sherpa3D图库:各种来自Sherpa3D生成的纹理网格的Blender渲染，其能够通过输入文本提示生成高保真、多样化、多视图一致的3D内容，本文方法也与流行的图形引擎兼容

<img src="https://img.saraba1st.com/forum/202312/13/062248zg6z5lldz6dhtggj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231213-061855__01.jpg</strong> (203.22 KB, 下载次数: 0)

下载附件

2023-12-13 06:22 上传

Sherpa3D的工作流程，给定文本作为输入，首先提示3D扩散来构建在几何模型(例如DMTet)中编码的粗略3D先验M，接下来在DMTet中渲染提取的网格的法线贴图，并从M中导出两种指导策略

(a)结构指导:利用结构描述(structural descriptor)来计算显然(salient)的几何特征，以保证几何保真度(解决诸如坑洞脸部的问题/pockmarked face problem)

(b)语义指导:利用语义编码器(例如CLIP)来提取高层级信息以保证3D一致性(解决诸如多面问题/multi-face issues)，在2D扬升过程中应用两种指导，使用法线贴图作为2D扩散模型的形状编码，并释放其力量来生成具有3D连贯性的高质量和多样化的结果

然后，通过外观建模进行真实感渲染，获得最终的3D结果(整个过程犹如那句著名谚语“Everest’s summit eludes many without Sherpa.”)

<img src="https://img.saraba1st.com/forum/202312/13/062314tt5cq5c20zt8fqfs.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231213-061906__01.jpg</strong> (220.32 KB, 下载次数: 0)

下载附件

2023-12-13 06:23 上传

与不同视图(0和180°)的基线方法进行定性对比，可以观察到基线方法存在严重的多面问题，而Sherpa3D可以实现更好的质量和3D连贯性

<img src="https://img.saraba1st.com/forum/202312/13/062331m6rt2rde11oq6yqt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231213-061923__01.jpg</strong> (191.08 KB, 下载次数: 0)

下载附件

2023-12-13 06:23 上传

与不同视图(−30°和150°)的基线方法进行的定性对比

<img src="https://img.saraba1st.com/forum/202312/13/062343ewcwqtcosulsvcpz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231213-061933__01.jpg</strong> (61.37 KB, 下载次数: 0)

下载附件

2023-12-13 06:23 上传

使用不同CLIP检索模型对带有文本提示的生成效果图进行了定量对比，与基准答案图像、Shap-E、Dreamfusion、Magic3D进行了对比，并在以对象为中心的COCO数据集上进行了评估

<img src="https://img.saraba1st.com/forum/202312/13/062353dy8f5fs53iffmszn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231213-061945__01.jpg</strong> (216.61 KB, 下载次数: 0)

下载附件

2023-12-13 06:23 上传

本文方法的消融实验，生成基于文字提示“a head of the Terracotta Army”，在实验中消融了结构指导、语义指导和逐步退火(step annealing)技术的设计选择

<img src="https://img.saraba1st.com/forum/202312/13/062404u3uvbvr3tr9azqaz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231213-061951__01.jpg</strong> (51.94 KB, 下载次数: 0)

下载附件

2023-12-13 06:24 上传

多视图一致性和总体生成质量分数的用户研究定量对比，评分范围为1-10，分数越高表示性能越好

<img src="https://img.saraba1st.com/forum/202312/13/062412sdaz0jdvwvcwdwu2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231213-061951__02.jpg</strong> (61.54 KB, 下载次数: 0)

下载附件

2023-12-13 06:24 上传

与Zero123的对比，使用生成的3D模型的前视图作为拥有开放词汇文本提示的Zero123的输入


*****

####  Machinery  
##### 1058#       发表于 2023-12-13 07:22

Vary

扩**型视觉语言模型的视觉词汇量

项目主页:[https://varybase.github.io/](https://varybase.github.io/)

github项目仓库:[https://github.com/Ucas-HaoranWei/Vary](https://github.com/Ucas-HaoranWei/Vary)

demo演示:[http://region-31.seetacloud.com:22701/](http://region-31.seetacloud.com:22701/)

现代大型视觉语言模型(LVLM)使用相同的视觉词汇——CLIP，可以涵盖大多数常见的视觉任务，然而，对于一些需要密集和细粒度视觉感知的特殊视觉任务，例如文档级OCR或图表理解，特别是在非英语场景中，CLIP式词汇可能会遇到视觉知识标记化效率低下的问题，甚至会遇到超出固有词汇外的问题

因此，本文提出了Vary，一种高效又有效的方法来扩大LVLM的视觉词汇量，Vary的处理过程被自然的分为两个部分:新视觉词汇的生成和整合

在第一阶段，设计了一个词汇网络(vocabulary network)，拥有一个小型的仅解码器Transformer(tiny decoder-only transformer)，以通过自回归生成所需的词汇，接下来，将新的视觉词汇与原始的视觉词汇(CLIP)合并来扩展普通视觉词汇，使LVLM能够快速获得新特性

与流行的BLIP-2、MiniGPT4和LLaVA相比，Vary可以保持其通用能力，同时享受更优秀的细粒度感知和理解能力，具体来说，Vary能够胜任新文档内容解析(OCR或Markdown转换)，同时在DocVQA中实现78.2%的ANLS，在MMVet中实现了36.2%的成绩

<img src="https://img.saraba1st.com/forum/202312/13/072002lq8sz0orr6kn0q0s.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231213-071431__01.jpg</strong> (141.11 KB, 下载次数: 0)

下载附件

2023-12-13 07:20 上传

先前的方法 vs. Vary:与其他使用现成视觉词汇的模型不同，Vary的过程可以分为两个阶段:视觉词汇的生成和融合，在第一阶段，使用“词汇网络”的一个小型的仅解码器网络，通过自回归产生强力的新视觉词汇，在第二阶段，将视觉词汇与原始词汇融合，以有效地为LVLM提供新特性

<img src="https://img.saraba1st.com/forum/202312/13/072017fgcehakaaiinz022.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231213-071441__01.jpg</strong> (188.66 KB, 下载次数: 0)

下载附件

2023-12-13 07:20 上传

Vary的概览图，有两种类型的形式Vary:Vary-tiny和Vary-base，Vary-tiny主要专注于生成新的视觉词汇表，而Vary-base是新的LVLM，旨在基于新的视觉词汇表处理各种视觉任务

<img src="https://img.saraba1st.com/forum/202312/13/072033exizoq0qxq6xfzqo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231213-071451__01.jpg</strong> (34.14 KB, 下载次数: 0)

下载附件

2023-12-13 07:20 上传

新视觉词汇网络的结构，添加了两个卷积层将输出转换为类似CLIP

<img src="https://img.saraba1st.com/forum/202312/13/072047uzpjtjpkjb30up67.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231213-071507__01.jpg</strong> (154.46 KB, 下载次数: 0)

下载附件

2023-12-13 07:20 上传

合成数据的可视化，使用pdflatex渲染文档，并使用pyecharts/matplotlib渲染图表

文档数据获取中/英文文本、公式、表格

图表数据包括中/英文条形、折线、饼图、复合样式

<img src="https://img.saraba1st.com/forum/202312/13/072058c8ykqoo4i44y5oih.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231213-071524__01.jpg</strong> (108.86 KB, 下载次数: 0)

下载附件

2023-12-13 07:20 上传

与Nougat相比更细粒度的文本感知，Vary-tiny是基于OPT-125M生成视觉词汇的模型，具有纯OCR能力，包括中文和英文，Vary-base是在Qwen-Chat 7B的基础上扩大视觉词汇量后的模型，通过提示控制，兼具纯文档OCR和Markdown格式对话能力

<img src="https://img.saraba1st.com/forum/202312/13/072114y232zrovji3s4jbj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231213-071533__01.jpg</strong> (94.14 KB, 下载次数: 0)

下载附件

2023-12-13 07:21 上传

在DocVQA和ChartQA上与流行方法的对比，80k表示SFT数据为LLaVA-80k，665k表示LLaVA-CC 665k，DocVQA的指标是ANLS，而ChartQA则遵循其原生论文的宽松准确性

<img src="https://img.saraba1st.com/forum/202312/13/072125psze0shzg59hegf1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231213-071537__01.jpg</strong> (140.25 KB, 下载次数: 0)

下载附件

2023-12-13 07:21 上传

与MMVet上的流行方法的对比

Rec: Recognition; Know: Knowledge; Gen: Language generation; Spat: Spatial awareness

<img src="https://img.saraba1st.com/forum/202312/13/072135rztt80ba8gxq2nx1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231213-071554__01.jpg</strong> (167.87 KB, 下载次数: 0)

下载附件

2023-12-13 07:21 上传

Vary-base 的指令跟随能力优于Markdown转换或纯OCR，Vary-base可以根据用户的提示控制输入的文档图像的输出格式

<img src="https://img.saraba1st.com/forum/202312/13/072149m6sjloo2lcyz6v66.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231213-071604__01.jpg</strong> (224.46 KB, 下载次数: 0)

下载附件

2023-12-13 07:21 上传

Vary-base对英文文档密集OCR的细粒度视觉感知能力

<img src="https://img.saraba1st.com/forum/202312/13/072159pr1rpbzzd7rhlddz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231213-071604__02.jpg</strong> (104.4 KB, 下载次数: 0)

下载附件

2023-12-13 07:21 上传

Vary-base对中文书籍密集OCR的细粒度视觉感知能力，输入图片来自互联网

<img src="https://img.saraba1st.com/forum/202312/13/072209z8zhhmehmmzy201z.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231213-071608__01.jpg</strong> (53.72 KB, 下载次数: 0)

下载附件

2023-12-13 07:22 上传

Vary-base的Markdown/Latex格式转换能力(数学公式)，输入图片来自互联网

<img src="https://img.saraba1st.com/forum/202312/13/072220kdn5x55x6djrryal.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231213-071608__02.jpg</strong> (88.9 KB, 下载次数: 0)

下载附件

2023-12-13 07:22 上传

Vary-base的Markdown/Latex格式转换能力(表格)，输入图片来自互联网

<img src="https://img.saraba1st.com/forum/202312/13/072233u6jfxe2bkxrke8ff.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231213-071614__01.jpg</strong> (80.89 KB, 下载次数: 0)

下载附件

2023-12-13 07:22 上传

Vary-base的图表理解(中文)，输入图片来自互联网

<img src="https://img.saraba1st.com/forum/202312/13/072242wlxeyi8eqxjzd1nz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231213-071614__02.jpg</strong> (138.57 KB, 下载次数: 0)

下载附件

2023-12-13 07:22 上传

Vary-base的通用性，这些图像来自LLaVA样本


*****

####  Machinery  
##### 1059#       发表于 2023-12-14 03:40

Phi-2

小型语言模型的惊人力量

相关博客文章:[https://www.microsoft.com/en-us/ ... ll-language-models/](https://www.microsoft.com/en-us/research/blog/phi-2-the-surprising-power-of-small-language-models/)

Azure AI Studio的phi2:[https://ml.azure.com/registries/ ... ls/microsoft-phi-2/](https://ml.azure.com/registries/azureml-msr/models/microsoft-phi-2/)

<img src="https://img.saraba1st.com/forum/202312/14/033817h8l2wa9ukb8av8v4.jpg" referrerpolicy="no-referrer">

<strong>Phi2-BlogHeroFeature-1400x788-1-1066x600.jpg</strong> (47.67 KB, 下载次数: 0)

下载附件

2023-12-14 03:38 上传

Satya Nadella在Microsoft Ignite 2023上宣布Phi-2

在过去的几个月中，微软研究院的机器学习基础团队发布了一套名为“Phi”的小型语言模型(SLM/small language models)，在各种基准测试中取得了卓越的性能，其中第一个模型，13亿参数的Phi-1，在现有SLM中的Python编码方面实现了SOTA性能(特别是在HumanEval和MBPP基准测试上)，然后，通过将重点扩展到常识推理和语言理解上，并创建了一个新的13亿参数模型，名为Phi-1.5，其性能表现甚至可以与比其大5倍的模型相媲美

现在发布的Phi-2，是一个27亿参数的语言模型，展示了出色的推理和语言理解能力，其在参数少于130亿的系列基础语言模型中达成了SOTA性能，而在复杂的基准测试中，得益于模型扩展和训练数据管理方面的创新，Phi-2的性能可与比其大25倍的模型相匹配或超越

凭借其紧凑的尺寸大小，Phi-2可以成为研究人员的实验创意游乐场，包括探索机制的可解释性、安全性改进或对各种任务的微调实验，已在Azure AI Studio模型目录中提供Phi-2，以促进语言模型的研究和开发

————

Phi-2 背后的关键见解

语言模型的规模大幅增加到数千亿个参数，这释放了许多新兴能力，重新定义了自然语言处理的领域格局，然而其中一个问题是，是否可以使用训练策略选择(例如数据选择)在较小的模型规模上实现这种新兴能力

对Phi模型的研究旨在通过训练SLM来回答这个问题，这些SLM的性能可与更大规模的模型相媲美(但距离前沿模型还很远)，对于使用Phi-2打破传统语言模型缩放定律的主要见解有两个:

首先，训练数据质量对模型性能起着至关重要的作用，几十年来人们都知道这一点，但继之前的工作“Textbooks Are All You Need”之后，通过关注“教科书质量(textbook-quality)”的数据，将这一见解发挥到了极致，训练数据混合了专门创建的合成数据集，用于教育模型常用场景推理和通用常识，包括科学、日常活动和心理理论与其他等(science, daily activities, and theory of mind, among others.)，通过精心挑选的网络数据进一步扩充了训练语料库，这些数据根据教育价值和内容质量进行了过滤

其次，使用了创新技术进行扩展，从13亿参数模型Phi-1.5开始，并将其知识嵌入到27亿参数Phi-2中，这种规模化的知识转移不仅加速了训练收敛，而且显著提高了Phi-2的基准分数

<img src="https://img.saraba1st.com/forum/202312/14/033902yfkd2j7pukd3bwfb.png" referrerpolicy="no-referrer">

<strong>figure2_phi_comp-1024x237.png</strong> (30.65 KB, 下载次数: 0)

下载附件

2023-12-14 03:39 上传

Phi-2 (2.7B) 和Phi-1.5(1.3B)模型之间的对比，除了BBH和MMLU分别使用3-shot CoT和5-shot评估之外，其他所有任务均使用0-shot进行评估

————

训练细节

Phi-2是一个基于Transformer的模型，以下一个单词预测为建模目标，在用于NLP和编码的合成数据集和Web数据集的混合上多次传递的1.4T Token上进行训练，Phi-2的训练在96个A100 GPU上花费了14天，Phi-2是一个基础模型，没有通过人类反馈强化学习(RLHF)进行对齐，也没有进行指令微调，尽管如此，与经过调整的现有开源模型相比，观察到在毒性和偏置方面有更好的表现，由于定制的数据管理技术，这与在Phi-1.5中看到的情况一致

<img src="https://img.saraba1st.com/forum/202312/14/033923ch0sf14czwvv041w.png" referrerpolicy="no-referrer">

<strong>figure3_safety_scores-1024x498.png</strong> (55.21 KB, 下载次数: 0)

下载附件

2023-12-14 03:39 上传

从ToxiGen根据13人口统计数据计算出的安全评分，选择了6541个句子的子集，并根据困惑度和句子毒性进行0到1之间的评分，较高的分数表明与benign ones相比，模型产生有毒句子的可能性更小

————

Phi-2评估

总结了Phi-2在学术基准上与流行语言模型的性能对比，基准测试涵盖多个类别，包括Big Bench Hard (BBH) (3 shot with CoT), commonsense reasoning (PIQA, WinoGrande, ARC easy and challenge, SIQA), language understanding (HellaSwag, OpenBookQA, MMLU (5-shot), SQuADv2 (2-shot), BoolQ), math (GSM8k (8 shot)), and coding (HumanEval, MBPP (3-shot))

Phi-2仅拥有27亿参数，在各种聚合基准上超越了Mistral和Llama-2模型的7B和13B参数的性能，值得注意的是，与大25倍的Llama-2-70B模型相比，它在多步推理任务(即编码和数学)上实现了更好的性能，此外，尽管尺寸更小，但Phi-2的性能可与最近发布的Google Gemini Nano 2相媲美或优于

当然也需要承认当前模型评估面临的挑战，并且许多公共基准可能会泄漏到训练数据中，对于第一个模型Phi-1，进行了广泛的净化研究以排除这种可能性，这可以在第一份报告“Textbooks Are All You Need”中找到，最终，可以相信判断语言模型的最佳方法是在具体用例上对其进行测试，遵循这种精神，还使用多个Microsoft内部的专有数据集和任务评估了Phi-2，并再次将其与Mistral和Llama-2进行了比较，观察到类似的趋势，即平均而言，Phi-2优于Mistral-7B，而后者优于Llama-2模型(7B、13B和70B)

<img src="https://img.saraba1st.com/forum/202312/14/033956upealui9e06pn060.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231214-033647.jpg</strong> (47.31 KB, 下载次数: 0)

下载附件

2023-12-14 03:39 上传

与流行的开源SLM相比，分组基准的平均性能表现

<img src="https://img.saraba1st.com/forum/202312/14/034019jcmyyglxg7lmecz1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231214-033657.jpg</strong> (22.85 KB, 下载次数: 0)

下载附件

2023-12-14 03:40 上传

Phi-2和Gemini Nano 2模型在Gemini报告的基准测试上的对比

除了这些基准之外，还对研究社区的常用提示进行了广泛的测试，观察到的行为与给出的基准结果的预期一致，例如，测试了一个用于探测模型解决物理问题的能力的提示，其最近用于评估Gemini Ultra模型的能力，并取得了以下结果:

<img src="https://img.saraba1st.com/forum/202312/14/034037qyyqzmnu98jp2yzn.png" referrerpolicy="no-referrer">

<strong>Seb_Fig4.png</strong> (125.09 KB, 下载次数: 0)

下载附件

2023-12-14 03:40 上传

Phi-2对一个简单物理问题的输出，其中包括近似正确的平方根计算

<img src="https://img.saraba1st.com/forum/202312/14/034049hxd7wddowa81w7iw.png" referrerpolicy="no-referrer">

<strong>Seb_Fig5.png</strong> (101.23 KB, 下载次数: 0)

下载附件

2023-12-14 03:40 上传

与Gemini的测试类似，还进一步向Phi-2询问了学生的错误答案，看看Phi-2是否能够识别出错误所在(确实如此，尽管Phi-2没有针对聊天或遵循指令进行过微调)，然而，注意到，这并是与Gemini报告中描述的Gemini Ultra输出的完全同类的对比，特别是在后一种情况下，学生的答案是作为带有手写文本的图像给出的，而不是在此例子中使用原始文本


*****

####  Machinery  
##### 1060#       发表于 2023-12-14 07:21

FreeControl

任意条件下任意文本到图像扩散模型的免训练空间控制

项目主页:[https://genforce.github.io/freecontrol/](https://genforce.github.io/freecontrol/)

github项目代码仓库:[https://github.com/genforce/freecontrol](https://github.com/genforce/freecontrol)

最近的方法，例如ControlNet等，为用户提供了对文本到图像(T2I)扩散模型的细粒度空间控制，然而，辅助模块必须针对每种类型的空间条件、模型架构和检查点(checkpoints)进行训练，这使得它们与人类设计师在内容创造过程中想要传达给人工智能模型的不同意图和偏好相矛盾

在这项工作中，提出了FreeControl，这是一种无需训练的可控T2I生成方法，同时支持多种条件、架构和检查点，FreeControl设计结构引导以促进结构与引导图像对齐，并设计外观引导以实现使用同一种子生成的图像之间的外观共享

广泛的定性和定量实验证明了FreeControl在各种预训练T2I模型中的卓越性能，特别是，FreeControl有助于对许多不同的架构和检查点进行方便的免训练控制，这可以完成在大多数现有免训练方法失败的场合的挑战性的输入条件，并通过基于训练的方法实现了有竞争力的合成质量

<img src="https://img.saraba1st.com/forum/202312/14/071857z14h01wfvmg01g0d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231214-071106__01.jpg</strong> (347.24 KB, 下载次数: 0)

下载附件

2023-12-14 07:18 上传

稳定扩散的免训练条件控制

(a)FreeControl能够在给定任何模态的输入条件图像的情况下对预训练的文本到图像扩散模型进行零样本控制

(b)与ControlNet相比，当面临引导图像和文本描述之间的冲突时，FreeControl在空间和图像文本对齐之间实现了良好的平衡，此外，它还支持难以构建训练对(training pairs)的条件类型（例如，引入行中的点云和网格的2D投影)

<img src="https://img.saraba1st.com/forum/202312/14/071915rvxxex3yozyymgio.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231214-071121__01.jpg</strong> (137.54 KB, 下载次数: 0)

下载附件

2023-12-14 07:19 上传

PCA给出的特征子空间的可视化，U-Net解码器中第一个自注意力的键(key)是通过DDIM反演获得的，针对不同风格和模态的五张图像(上方:人物；下方:卧室)，随后使用PCA，三个主要部分的RGB中的伪彩色(pseudo-colored)提供了语义成分的清晰分离

<img src="https://img.saraba1st.com/forum/202312/14/071927zszerk5i4iigz4si.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231214-071141__01.jpg</strong> (219.49 KB, 下载次数: 0)

下载附件

2023-12-14 07:19 上传

方法概览图

(a)在分析阶段，FreeControl使用预训练的扩散模型生成目标概念(例如人)的种子图像(seed images)，并对它们的扩散特征执行PCA 以获得线性子空间作为基础语义

(b)在合成阶段，FreeControl在该子空间中采用结构引导来强制结构与输入条件对齐，同时应用外观指导来利用没有条件控制的相同种子生成的兄弟图像(sibling image)进行外观迁移

<img src="https://img.saraba1st.com/forum/202312/14/071939vkufkztcdwed3cws.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231214-071153__01.jpg</strong> (408.44 KB, 下载次数: 0)

下载附件

2023-12-14 07:19 上传

可控T2I扩散的定性对比，FreeControl支持一整套控制信号和Stable Diffusion的三个主要版本，生成的图像紧密遵循文本提示，同时与输入图像表现出健壮的空间对齐

<img src="https://img.saraba1st.com/forum/202312/14/071953z7cbykfc78kkkz7c.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231214-071219__01.jpg</strong> (302.08 KB, 下载次数: 0)

下载附件

2023-12-14 07:19 上传

更多控制条件的定性结果，FreeControl支持基于训练的方法无法实现的具有挑战性的控制条件，其中包括常见图形原型的2D投影(第1行和第2行)、特定领域的形状模型(第3行和第4行)、图形软件视端(第5行)和模拟驾驶环境(第6行)

<img src="https://img.saraba1st.com/forum/202312/14/072014l9p6l6dqx4m9mmnm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231214-071230__01.jpg</strong> (431.03 KB, 下载次数: 0)

下载附件

2023-12-14 07:20 上传

可控T2I扩散的定性对比，与基于训练的方法相比，FreeControl实现了有竞争力的空间控制和卓越的图像文本对齐，它还避免了免训练基线方法所表现出的外观泄漏问题(appearance leakage problem)，生成内容丰富且外观忠实于文本提示的高质量图像

<img src="https://img.saraba1st.com/forum/202312/14/072024efaz2mx77tb3pk12.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231214-071239__01.jpg</strong> (163.08 KB, 下载次数: 0)

下载附件

2023-12-14 07:20 上传

可控T2I扩散的定量结果，通过自相似距离(Self-similarity distance)、CLIP分数和LPIPS距离指标衡量，FreeControl在结构保留(structure preservation)、图像文本对齐(image-text alignment)和外观多样性(appearance diversity)方面始终优于所有的免训练基线，它通过基于训练的基线实现了有竞争力的结构和外观分数，同时展示了更强的图像文本对齐

<img src="https://img.saraba1st.com/forum/202312/14/072037zbaexthlahh4ulzh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231214-071307__01.jpg</strong> (274.07 KB, 下载次数: 0)

下载附件

2023-12-14 07:20 上传

可控的T2I定制概念生成，FreeControl与主要的定制化技术兼容，并且可以轻松支持定制概念的可控生成，而无需空间对齐的条件图像，相比之下，ControlNet无法在给定冲突条件的情况下保留自定义概念，而T2I-Adapter则拒绝遵守条件图像和文本提示

<img src="https://img.saraba1st.com/forum/202312/14/072049bto1jtw2tb11w2op.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231214-071323__01.jpg</strong> (255.14 KB, 下载次数: 0)

下载附件

2023-12-14 07:20 上传

文本引导图像到图像转换的定性和定量对比，FreeControl通过引导掩码M和随机种子(左)灵活控制图像组成和风格，与基线相比(右，越右下代表成绩越好)，它在结构保留(自相似距离)和图像文本对齐(CLIP分数)之间取得了良好的平衡

<img src="https://img.saraba1st.com/forum/202312/14/072104qv3qph0whwy30g1h.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231214-071323__02.jpg</strong> (71.49 KB, 下载次数: 0)

下载附件

2023-12-14 07:21 上传

语义基础Nb的大小相关消融实验，图像是使用提示“a Lego man giving a lecture”生成的，它们说明了结构和外观质量之间固有的权衡，Nb’s在中间范围内可以实现良好的平衡

<img src="https://img.saraba1st.com/forum/202312/14/072113vt4v4gtv4e214zz4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231214-071337__01.jpg</strong> (78.03 KB, 下载次数: 0)

下载附件

2023-12-14 07:21 上传

对引导效果的影响的消融实验，gs和ga分别代表结构和外观指导，上方: “leather shoes”; 下方: “cat, in the desert”

<img src="https://img.saraba1st.com/forum/202312/14/072122ee9jyrkqrrjjy9r7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231214-071348__01.jpg</strong> (149.39 KB, 下载次数: 0)

下载附件

2023-12-14 07:21 上传

特征选择上的消融实验，U-Net解码器中up block.1的自注意力的键(key)展现了最强的可控能力，插图中显示了特征的PCA可视化

<img src="https://img.saraba1st.com/forum/202312/14/072130pvzo3k5ob5zk3l0t.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231214-071352__01.jpg</strong> (170.43 KB, 下载次数: 0)

下载附件

2023-12-14 07:21 上传

种子图像数量Ns的消融实验，较大的N会带来结构对齐的微小改进

上方: “wooden sculpture of a man”; 下方: “dog, in the snow”.


*****

####  Machinery  
##### 1061#       发表于 2023-12-14 07:43

 本帖最后由 Machinery 于 2023-12-14 07:44 编辑 

FreeInit

弥合视频扩散模型中的初始差距

项目主页:[https://tianxingwu.github.io/pages/FreeInit/](https://tianxingwu.github.io/pages/FreeInit/)

github项目仓库:[https://github.com/TianxingWu/FreeInit](https://github.com/TianxingWu/FreeInit)

尽管基于扩散的视频生成取得了快速发展，但现有模型的推理结果仍然表现出不那么令人满意的时间一致性和不自然的动态性，在本文中，深入研究了视频扩散模型的噪声初始化(noise initialization)，并发现了隐含的训练到推理差距，该问题导致了推理质量不佳

本文关键发现是:

1.推理时的初始潜在(initial latent)的时空频率分布(spatial-temporal frequency distribution)与训练时的时空频率分布存在本质上不同

2.去噪过程中的生成结果是受到初始噪声(initial noise)的低频部分(low-frequency components)的显著影响的

受这些观察的启发，提出了一种简洁而有效的推理采样策略FreeInit，显著提高了扩散模型生成的视频的时间一致性，通过在推理时迭代细化初始潜在的时空低频部分，FreeInit能够对训练和推理之间的初始差距进行补偿，从而有效提高生成结果的主题外观和时间一致性

大量实验表明，FreeInit能够持续增强各种文本到视频生成模型的生成结果质量而无需额外训练

————

生成对比演示(请查看项目页面)

<img src="https://img.saraba1st.com/forum/202312/14/074227agcfzgrricsr11ff.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231214-074123.jpg</strong> (54.04 KB, 下载次数: 0)

下载附件

2023-12-14 07:42 上传

————

<img src="https://img.saraba1st.com/forum/202312/14/074308c5a35a3qkza9kbgv.png" referrerpolicy="no-referrer">

<strong>pipeline.png</strong> (319.35 KB, 下载次数: 0)

下载附件

2023-12-14 07:43 上传

提出了FreeInit来弥合视频扩散模型的训练和推理之间的初始差距，FreeInit以迭代细化的方式推理初始噪声，通过DDIM采样、DDPM前向和噪声重初始化(Noise Reinitialization)，初始噪声的低频成分逐渐细化，持续增强时间一致性和主题外观

————

不同模型的生成结果演示

<img src="https://img.saraba1st.com/forum/202312/14/074342xmg6zq1cashsbq6v.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231214-074107.jpg</strong> (232.7 KB, 下载次数: 0)

下载附件

2023-12-14 07:43 上传


*****

####  Machinery  
##### 1062#       发表于 2023-12-14 19:38

 本帖最后由 Machinery 于 2023-12-14 19:41 编辑 

Mixtral 8x7B

混合专家系列模型Mixtral 8x7B

相关博客:[https://mistral.ai/news/mixtral-of-experts/](https://mistral.ai/news/mixtral-of-experts/)

hugface基础模型权重:[https://huggingface.co/mistralai/Mixtral-8x7B-v0.1](https://huggingface.co/mistralai/Mixtral-8x7B-v0.1)

hugface指令模型权重:[https://huggingface.co/mistralai/Mixtral-8x7B-v0.1](https://huggingface.co/mistralai/Mixtral-8x7B-v0.1)

————

Mistral AI继续履行为开发者社区提供最佳开放模型的使命，人工智能的发展需要采取新的技术变革，而不仅仅是重用众所周知的架构和训练范式，最重要的是，它需要使社区从原始模型中受益，以促进新的发明和用途

今天，该团队很自豪地发布Mixtral 8x7B，开源权重的高质量稀疏专家混合模型(SMoE/sparse mixture of experts model)，依据Apache 2.0进行授权许可，Mixtral在大多数基准测试中都优于Llama 2 70B，推理速度提高了6倍，也是最强大的开源权重模型，具有宽松的许可证，同时也是成本/性能权衡方面的最佳模型，特别是，它在大多数标准基准测试中可以匹配或优于GPT3.5的性能

 Mixtral具有以下能力:

1.它可以优雅地处理 32k Token的上下文

2.它可以处理英语、法语、意大利语、德语和西班牙语

3.它在代码生成方面表现出了强大的性能

4.它可以微调为指令跟随模型，同时在MT-Bench上获得8.3的分数

————

通过稀疏架构推动开放模型的前沿

Mixtral是一个稀疏的专家混合网络，一个仅解码器模型，其中前馈块从一组8个不同的参数组中进行选择，在每一层，对于每个Token，路由网络选择其中的组中两个(“专家”)来处理Token并相加地组合它们的输出

该技术增加了模型的参数数量，同时控制了成本和延迟，因为该模型仅使用每个Token总参数集合的一小部分，具体来说，Mixtral共有46.7B个参数，但每个Token仅使用12.9B个参数， 因此它可以以与12.9B模型相同的速度和相同的成本处理输入并生成输出

Mixtral根据从开放互联网中提取的数据进行了预训练，同时训练专家和路由网络

————

性能

将Mixtral与Llama 2系列和GPT3.5基础模型进行了对比，Mixtral在大多数基准测试中均匹配或优于Llama 2 70B以及GPT3.5

<img src="https://img.saraba1st.com/forum/202312/14/194104eqqc81cz1tkoai1g.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231214-193909.jpg</strong> (73.03 KB, 下载次数: 0)

下载附件

2023-12-14 19:41 上传

在下图中，衡量了质量与推理预算的权衡，与Llama 2型号相比，Mistral 7B和Mixtral 8x7B均属于高效型号系列

<img src="https://img.saraba1st.com/forum/202312/14/193751p83fgt38b293ub32.png" referrerpolicy="no-referrer">

<strong>scaling.png</strong> (173.95 KB, 下载次数: 0)

下载附件

2023-12-14 19:37 上传

下表给出了上图的详细结果

<img src="https://img.saraba1st.com/forum/202312/14/193804hdtg0ytdazvktcma.png" referrerpolicy="no-referrer">

<strong>open_models.png</strong> (226.51 KB, 下载次数: 0)

下载附件

2023-12-14 19:38 上传

幻觉和偏见，为了识别可能的缺陷，通过微调/偏好建模来纠正，在TruthfulQA/BBQ/BOLD上测量了基本模型的性能

<img src="https://img.saraba1st.com/forum/202312/14/194115pm5ftckxx5f5mh6x.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231214-193938.jpg</strong> (76.04 KB, 下载次数: 0)

下载附件

2023-12-14 19:41 上传

与Llama 2相比，Mixtral更真实可信(在TruthfulQA基准上为73.9% vs 50.2%)，并且在BBQ基准上呈现出了更少的偏差，总体而言，Mixtral在BOLD上比Llama 2展现出了更正向的情绪，每个维度内的差异相似

 语言，Mixtral 8x7B精通法语、德语、西班牙语、意大利语和英语

<img src="https://img.saraba1st.com/forum/202312/14/193842c1ilfhz1tattaijc.png" referrerpolicy="no-referrer">

<strong>multilingual.png</strong> (148.82 KB, 下载次数: 0)

下载附件

2023-12-14 19:38 上传

————

指令模型

与Mixtral 8x7B一起发布了Mixtral 8x7B Instruct，该模型已通过监督微调和直接偏好优化(DPO)进行了优化，以便仔细遵循指令，在MT-Bench上，它达到了8.30的分数，使其成为最好的开源模型，性能可与GPT3.5相媲美

注意：可以优雅地通过提示Mixtral使构建在其之上的应用禁止某些需要严格审核的某些输出，如此处所示，适当的偏好调整也可以达到此目的，请记住，如果没有这样的提示，模型将仅遵循给出的任何指示

————

使用开源部署堆栈部署 Mixtral

为了使社区能够使用完全开源的堆栈运行Mixtral，已提交了对vLLM项目的更改，该项目集成了Megablocks CUDA内核以实现高效推理

 Skypilot允许在云端的任何实例上部署vLLM端点


*****

####  Machinery  
##### 1063#       发表于 2023-12-15 01:05

alignment-for-honesty

对齐至诚之道(Alignment for Honesty)

github项目主页:[https://github.com/GAIR-NLP/alignment-for-honesty](https://github.com/GAIR-NLP/alignment-for-honesty)

最近的研究在应用对齐技术来根据人类意图增强大型语言模型(LLM)的帮助性和无害性方面取得了重大进展，在本文中，主张了诚信对齐的重要性，这可以确保LLM在缺乏知识时主动拒绝回答问题，同时又不至于过于保守

然而，对齐诚信的一个关键方面涉及辨别LLM知识的局限性，这并非直截了当能够判断，这一挑战需要在指标开发(metric development)、基准创建(benchmark creation)和训练方法论(training methodologies)方面提供全面的解决方案

在本文中，建立了精确的问题定义，并根据论语(Analects of Confucius)的启发定义了“至诚之道”来应对这些挑战，这是制定指标的基石，有效把握了LLM在后对齐(post-alignment)过程中的诚信度量化

此外，还引入了一个灵活的训练框架，该框架通过几种高效的微调技术进一步实例化，这些技术强调诚信而不牺牲其他任务的性能

广泛的实验表明，这些对齐的模型显示出诚信度的显著提高，正如提出的指标所示，开源了大量资源，以促进未来的研究，包括诚信对齐模型、诚信对齐训练和评估数据集、概念术语表以及所有相关源代码

<img src="https://img.saraba1st.com/forum/202312/15/010301px3edmxfd5usf4et.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-005653__01.jpg</strong> (122.48 KB, 下载次数: 0)

下载附件

2023-12-15 01:03 上传

诚信对齐的说明图，给定一个知识密集型问题，一个对齐模型应该能够在了解问题的情况下提供正确答案，或者选择拒绝回答该问题

<img src="https://img.saraba1st.com/forum/202312/15/010320fo7mym33mmewpj7o.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-005704__01.jpg</strong> (88.96 KB, 下载次数: 0)

下载附件

2023-12-15 01:03 上传

(a)迭代对齐的示意图，大型语言模型M通过迭代演化，以更好地与给定的人类价值观进行对齐

(b)“无害(harmless)” 的决策边界，通常由人类定义

(c)“已知(known)” 的决策边界，通常由模型决定

<img src="https://img.saraba1st.com/forum/202312/15/010335jiubssshs8ruouri.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-005711__01.jpg</strong> (38.1 KB, 下载次数: 0)

下载附件

2023-12-15 01:03 上传

在对齐诚信之后(t+1)，以及之前(t)的模型的回应出现类型变化，以“⑦”回应为例:模型Mt能够正确回答问题，但是模型Mt+1却选择不这样做，这意味着对齐后的模型可能会呈现出过度谨慎

<img src="https://img.saraba1st.com/forum/202312/15/010344ip6vamf6fxa6bv4p.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-005720__01.jpg</strong> (216.31 KB, 下载次数: 0)

下载附件

2023-12-15 01:03 上传

提案的以诚信为导向(honesty-oriented)的微调方法概览图，“预期准确率=0.3”表示在抽样的10个回答中，有3个正确回答和7个错误回答，用不同的颜色分别表示错误回答，正确回答，以及不知道(idk)的回答

<img src="https://img.saraba1st.com/forum/202312/15/010356f4zwwbju6be8x0w6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-005726__01.jpg</strong> (49.53 KB, 下载次数: 0)

下载附件

2023-12-15 01:03 上传

输入的提示

<img src="https://img.saraba1st.com/forum/202312/15/010413iihbhgu6b69rhdit.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-005732__01.jpg</strong> (131.14 KB, 下载次数: 0)

下载附件

2023-12-15 01:04 上传

CONFIDENCE-NUM的输出

<img src="https://img.saraba1st.com/forum/202312/15/010427v7yjaajeaauyajws.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-005737__01.jpg</strong> (110.04 KB, 下载次数: 0)

下载附件

2023-12-15 01:04 上传

OCONFIDENCE-VERB的输出

<img src="https://img.saraba1st.com/forum/202312/15/010442pzr9zi9apxxz5xza.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-005746__01.jpg</strong> (64.95 KB, 下载次数: 0)

下载附件

2023-12-15 01:04 上传

TriviaQA评估集上的主要结果，UNALIGNED表示UNALIGNED基线，FINE-TUNED表示FINE-TUNED基线，而PROMPT-BASED表示只采用提示的免训练方法，ABSOLUTE采用m=10和τ=0.1，最佳诚信度分数以粗体显示，第二高的准确度以下划线表示

<img src="https://img.saraba1st.com/forum/202312/15/010458x1181swrzujjswbp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-005746__02.jpg</strong> (30.6 KB, 下载次数: 0)

下载附件

2023-12-15 01:04 上传

拒绝阈值τ的效果

<img src="https://img.saraba1st.com/forum/202312/15/010508ienuca02v0cnt0e3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-005753__01.jpg</strong> (84.83 KB, 下载次数: 0)

下载附件

2023-12-15 01:05 上传

不同模型规模在TriviaQA评估集上的结果

<img src="https://img.saraba1st.com/forum/202312/15/010523g4wa1ybf13yjpejj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-005802__01.jpg</strong> (150.43 KB, 下载次数: 0)

下载附件

2023-12-15 01:05 上传

三个自由形式问答数据集的OOD表现，考虑到最后两个数据集的不同特点，提供了PUQA的谨慎(prudence)分数以及PKQA的过度保守(over-consv.)分数和准确率，具体而言，对于PUQA，重点在于评估对齐模型是否能够拒绝明显未知的问题，相反，对于PKQA，关注点则转移到评估对齐模型是否过于谨慎，并且能否保持对于明确已知问题的准确回答

<img src="https://img.saraba1st.com/forum/202312/15/010545r6lm1bqpbqwg7udw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-005811__01.jpg</strong> (112.53 KB, 下载次数: 0)

下载附件

2023-12-15 01:05 上传

在MMLU上的结果，灰色行表示进行了数据增强的结果

<img src="https://img.saraba1st.com/forum/202312/15/010553eal45ugxsafdldox.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-005811__02.jpg</strong> (35.38 KB, 下载次数: 0)

下载附件

2023-12-15 01:05 上传

根据来自Eval-P-的帮助性数据的结果


*****

####  Machinery  
##### 1064#       发表于 2023-12-15 01:31

 本帖最后由 Machinery 于 2023-12-15 01:32 编辑 

Stable Zero123

从单张图像生成高质量3D对象

hugface模型权重下载:[https://huggingface.co/stabilityai/stable-zero123](https://huggingface.co/stabilityai/stable-zero123)

————

关键要点

Stable Zero123可以生成对象物体的新视图，展现了从各个角度对物体外观的3D理解，由于训练数据集和高度(elevation)条件的改进，质量比Zero1-to-3或Zero123-XL显著提高

 该模型基于Stable Diffusion1.5，消耗与SD1.5相同数量的VRAM来生成1个新视图，使用Stable Zero123生成3D对象需要更多时间和显存(建议使用 24GB VRAM)

该模型在非商业和研究用途的授权情况下发布(相关链接:[https://huggingface.co/stability ... 23/raw/main/LICENSE](https://huggingface.co/stabilityai/stable-zero123/raw/main/LICENSE))

<img src="https://img.saraba1st.com/forum/202312/15/013105prdwwb5shcy7reqq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-012905.jpg</strong> (79.51 KB, 下载次数: 0)

下载附件

2023-12-15 01:31 上传

Stable Zero123使用分数蒸馏重建的示例3D模型

————

Stable Zero123是内部训练的用于条件视图图像生成的模型，与之前的SOTA模型Zero123-XL相比，Stable Zero123达成了明显的改进效果，这是通过以下三个关键创新实现的:

1. 改进的训练数据集，从Objaverse经过严格筛选，仅保留高质量的3D物体，并且使用比以前的方法更加真实的方式进行渲染

2. 在训练和推理过程中，为模型提供了估计的摄像机角度，这种高度条件使其能够做出更明智、更高质量的预测

3.预计算的数据集(预计算的潜变量)和改进的数据加载器支持更大的批大小，结合第一项创新，使得训练效率相比Zero123-XL提高了40倍

已在Hugging Face上发布了该模型，以便研究人员和非商业用户可以下载并进行实验

<img src="https://img.saraba1st.com/forum/202312/15/013116y4mmmspkqps2bkf3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-012918.jpg</strong> (48.78 KB, 下载次数: 0)

下载附件

2023-12-15 01:31 上传

对比来自右上方显示的输入图像样本的Stable Zero123和Zero123-XL跨越不同视角的预测

————

使用Stable Zero123创建3D对象

为了促进3D对象生成的开放研究，改进了threestudio的开源代码以支持Zero123和Stable Zero123，这个简化版的Stable 3D过程目前处于私人预览阶段，从技术角度来说，它使用分数蒸馏采样(SDS)来优化Stable Zero123模型的NeRF，然后根据这个创建一个带纹理的3D网格，这个过程可以通过首先使用SDXL生成单个图像，然后使用Stable Zero123生成3D对象来进行文本到3D生成

<img src="https://img.saraba1st.com/forum/202312/15/013123xwq15q4up578bqhd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-012932.jpg</strong> (63 KB, 下载次数: 0)

下载附件

2023-12-15 01:31 上传

Stable Zero123 (Stability AI)和Zero123-XL模型的3D对象对比


*****

####  Machinery  
##### 1065#       发表于 2023-12-15 02:45

 本帖最后由 Machinery 于 2023-12-15 02:50 编辑 

CLIP as RNN

无需训练即可分割无数视觉概念

项目主页:[https://torrvision.com/clip_as_rnn/](https://torrvision.com/clip_as_rnn/)

github项目仓库:[https://github.com/kevin-ssy/CLIP_as_RNN](https://github.com/kevin-ssy/CLIP_as_RNN)

现有的开放词汇图像分割方法需要在掩码标注或图像文本数据集上进行微调步骤，掩码标签需要大量人力，这限制了分割数据集中类别的数量，因此，预训练的视觉语言模型(VLM)的开放词汇能力在经过微调后严重受限，然而，如果没有进行微调，仅在弱图像文本监督下训练的VLM，在那些图像中不存在的概念的文本查询时，往往会产生次优的掩码预测结果

为了缓解这些问题，本文引入了一种新颖的循环框架(recurrent framework)，通过逐渐过滤掉不相关的文本并改善掩码质量，无需进行训练即可实现，循环单元(recurrent unit)是一个基于冻结权重的VLM构建的两阶段分割器，因此，本文模型保留了VLM的广泛词汇空间，并增强了其分割能力

实验结果表明，本文方法不仅优于无训练的对应方法，还优于使用数百万额外数据样本进行微调的方法，并在零样本语义分割和指代图像分割任务(referring image segmentation tasks)上创下了新的最优记录

具体而言，在Pascal VOC、COCO Object和Pascal Context数据集上，将当前记录的mIoU分别提高了28.8、16.0和6.9

<img src="https://img.saraba1st.com/forum/202312/15/024240oruykqkiiukzppkr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-023748__01.jpg</strong> (277.33 KB, 下载次数: 0)

下载附件

2023-12-15 02:42 上传

提出了CaR来对广泛的词汇进行概念分割，包括虚拟角色、地标、品牌、日常物品和指称表达，图片展示了定性结果

<img src="https://img.saraba1st.com/forum/202312/15/024252k7b7zm4azhx7qfha.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-023754__01.jpg</strong> (97.67 KB, 下载次数: 0)

下载附件

2023-12-15 02:42 上传

CaR可以完全继承CLIP的广泛词汇空间，通过直接使用预训练的视觉语言模型CLIP的特征，而无需进行任何微调，尽管图像中的场景很简单，但在分割数据集上经过微调的SOTA方法无法正确地分割和识别百事可乐和可口可乐

<img src="https://img.saraba1st.com/forum/202312/15/024303kpmg4ggbgg61m6mx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-023807__01.jpg</strong> (272.68 KB, 下载次数: 0)

下载附件

2023-12-15 02:43 上传

CaR的总体框架

(a)、(b):给定一张图片，用户提供一组他们感兴趣的文本查询用于进行分割，这个初始集合用h0表示，可能包含图片中不存在的概念，例如Arsenal和Arsenal，在t-th个时间步骤中，冻结的分割器评估每个掩码与先前时间步骤的文本查询ht−1之间的对齐程度，然后使用函数σ消除置信度较低的查询

(c) 描述了两阶段分割器的详细构架，它包括一个掩码生成器f(·, ·)，和一个掩码分类器g(·, ·)，用于评估每个掩码文本对的对齐程度

<img src="https://img.saraba1st.com/forum/202312/15/024315l9ueqxcgxtu9ttdk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-023815__01.jpg</strong> (60.54 KB, 下载次数: 0)

下载附件

2023-12-15 02:43 上传

给定the man wearing the jersey of Manchester United掩码的视觉提示的示例

<img src="https://img.saraba1st.com/forum/202312/15/024429vfrifdycynkjyknr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-023839__01.jpg</strong> (307.22 KB, 下载次数: 0)

下载附件

2023-12-15 02:44 上传

与现有的零样本语义分割方法进行对比，用✓表示VLM的视觉编码器或文本编码器是否经过预训练，从表格可以看出，本文方法不仅在没有微调的情况下表现出色，而且在对数百万个数据样本进行微调的方法上也表现出色，为了公平比较，将使用CLIP作为骨干网络的方法进行了对比

<img src="https://img.saraba1st.com/forum/202312/15/024443rj28129mp0j8qvg5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-023847__01.jpg</strong> (31.83 KB, 下载次数: 0)

下载附件

2023-12-15 02:44 上传

应用循环架构和不同的CAM方法的效果，循环在提高性能方面起着至关重要的作用

<img src="https://img.saraba1st.com/forum/202312/15/024455ypkvc4555jvvj65c.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-023859__01.jpg</strong> (45.8 KB, 下载次数: 0)

下载附件

2023-12-15 02:44 上传

CLIP骨干网络的效果，在Pascal VOC和COCO Object上比较了各种CLIP骨干网络，结果显示，通过扩大掩码分类器，可以提高性能

<img src="https://img.saraba1st.com/forum/202312/15/024507l92rb1mmcbmkxz99.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-023905__01.jpg</strong> (45.19 KB, 下载次数: 0)

下载附件

2023-12-15 02:45 上传

不同视觉提示的效果，当多个视觉提示被选中时，将同时将所有选中的视觉提示应用于一张图像上，实验在Pascal VOC上进行

<img src="https://img.saraba1st.com/forum/202312/15/024516xiliy8sropn3o1i8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-023917__01.jpg</strong> (50.5 KB, 下载次数: 0)

下载附件

2023-12-15 02:45 上传

不同超参数的影响:将掩码二值化提案的阈值(η)，移除文本查询的阈值(θ)以及CLIP-ES的参数(λ)，在Pascal VOC和COCO Object上进行了实验

<img src="https://img.saraba1st.com/forum/202312/15/024532vxp6pvs1kipxpyjs.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-023917__02.jpg</strong> (38.39 KB, 下载次数: 0)

下载附件

2023-12-15 02:45 上传

背景查询对Pascal VOC的影响，将背景查询分为:Terrestrial, Aquatic,Atmospheric, and Man-Made，在第一行的结果中使用“None”作为背景查询

<img src="https://img.saraba1st.com/forum/202312/15/024542zq3gr8m7tw74z2m0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-023917__03.jpg</strong> (49.7 KB, 下载次数: 0)

下载附件

2023-12-15 02:45 上传

在指代图像分割的mIoU方面，与SOTA方法进行了对比，CaR在三个基准测试的所有拆分中都优于所有比较方法

<img src="https://img.saraba1st.com/forum/202312/15/024553syhfohnzcycoc6nf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-023925__01.jpg</strong> (7.51 KB, 下载次数: 0)

下载附件

2023-12-15 02:45 上传

在Ref-DAVIS 2017上的结果


*****

####  Machinery  
##### 1066#       发表于 2023-12-15 17:54

 本帖最后由 Machinery 于 2023-12-15 17:58 编辑 

Weak-to-strong

从弱到强的泛化

相关博客:[https://openai.com/research/weak-to-strong-generalization](https://openai.com/research/weak-to-strong-generalization)

相关论文:[https://cdn.openai.com/papers/weak-to-strong-generalization.pdf](https://cdn.openai.com/papers/weak-to-strong-generalization.pdf)

github相关仓库:[https://github.com/openai/weak-to-strong](https://github.com/openai/weak-to-strong)

提出了一个新的超对齐研究方向，以及有希望的初步结果:我们能否利用深度学习的泛化特点来控制强模型与弱监督者的关系

————

对于超人工智能系统(超对齐)的核心挑战之一是，人类能监督比他们更聪明的AI系统吗？本文研究了一个简单的类比:小模型能够监督大模型吗？展示了使用一个类似GPT-2的模型来调用GPT-4的大部分能力，接近于GPT-3.5的性能水平，甚至在小模型失败的困难问题上也能正确泛化，这开辟了一条新的研究方向，使我们能够直接应对未来超人类模型对齐的核心挑战，同时在当今取得迭代的经验性进展

————

超对齐问题

相信在未来十年内，会出现远远智能于人类的超智能人工智能，然而，我们仍然不知道如何可靠地引导和控制超人类人工智能系统，解决这个问题对于确保未来最先进的人工智能系统仍然安全和有益于人类至关重要

今年早些时候，openai成立了超对齐团队来解决超智能对齐的问题，而今天，发布了该团队的第一篇论文，介绍了一种新的通过经验对齐超人类模型的研究方向

当前的对齐方法，比如基于人类反馈的强化学习(RLHF)，依赖于人类的监督，然而，未来的人工智能系统将能够展现极其复杂和创造性的行为，这将使得人类难以可靠地监督它们，例如，超人类模型可能能够编写数百万行新颖(具有潜在危险)的计算机代码，即使对于专家人类来说，理解起来也非常困难

相对于超人类的AI模型，人类将成为“弱监督者”，这是人工通用智能对齐的一个核心挑战:弱监督者如何能够信任和控制实质上更强大的模型？

————

实验设置

为了在这个核心挑战上取得进展，提出一个在今天可以进行实证研究的类比:能否使用一个较小(能力较弱)模型来监督一个较大(能力较强)的模型？

<img src="https://img.saraba1st.com/forum/202312/15/175438t512p8zeg8y82251.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-175422.jpg</strong> (41.3 KB, 下载次数: 0)

下载附件

2023-12-15 17:54 上传

一个对于超对齐的简单类比:在传统的机器学习中，人类监督相比他们自己能力较弱的AI系统(左图)，为了实现超智能的对齐，人类将需要监督比他们自己更聪明的AI系统(中图)，虽然现在无法直接研究这个问题，但可以研究一个简单的类比:较小的模型是否可以监督较大的模型(右图)

天真地说，我们可能不会期望一个强大的模型比提供训练信号的弱监督者表现更好，它可能只是学会模仿弱监督者所犯的所有错误，另一方面，强大的预训练模型具有出色的原始能力，从而不需要从头开始教它们新任务，只需要引出它们潜在的知识

关键问题是:强大的模型是否会根据弱监督者的潜在意图进行泛化，利用其全部能力来解决即使在弱监督者只能提供不完整或有缺陷的训练标签的困难问题？

————

研究结果

<img src="https://img.saraba1st.com/forum/202312/15/175451ai6p75mt5g26iti6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-175356.jpg</strong> (20.4 KB, 下载次数: 0)

下载附件

2023-12-15 17:54 上传

典型的自然语言处理基准(NLP benchmarks)上的从弱到强的泛化:使用一个GPT-2级别的模型作为弱监督者，来对GPT-4进行微调

可以在许多设置中显著提高泛化能力，使用一种简单的方法，鼓励强模型更加自信，包括在必要时坚定地不同意弱监督者，当我们使用这种方法用GPT-2级模型监督GPT-4在自然语言处理任务上时，得到的模型通常表现在GPT-3和GPT-3.5之间，这意味着能够通过较弱的监督来恢复大部分GPT-4的能力

这种方法是一个概念验证，有一些重要的限制；例如，它仍然不能在ChatGPT偏好数据上工作，然而，还发现其他方法，比如优化的早期停止(optimal early stopping)和从小到中再到大的模型的自举提升(bootstrapping)，也有迹象表明它们是有效的

综上所述，研究结果表明:(1)简单的人类监督，比如通过人类反馈进行强化学习(RLHF)，可能在没有进一步工作的情况下很难扩展到超人模型，但(2)在弱到强泛化方面是可行的

————

研究机会

当前的经验设置与解决超级智能模型对齐的最终问题之间仍然存在重要的不同之处，例如，未来的模型可能更容易模仿弱人类的错误，而当前的强模型要模仿当前的弱模型错误可能更困难，这可能使得未来的泛化更加困难

尽管如此，相信本文也捕捉到了解决未来超级智能模型对齐问题的一些关键困难，使我们能够从今天开始在这个问题上取得实证进展，未来工作有许多有希望的方向，包括修复设置中的不同之处，开发更好的可扩展方法，并推进对何时以及如何期望从弱到强泛化能力的良好科学理解

Openai团队今日发布了开源代码，以便于开始进行弱到强泛化实验，同时推出了一项1000万美元的资助计划，面向研究生、学者和其他研究人员，广泛开展超人级AI对齐的工作，特别期待支持与弱到强泛化相关的研究

弄清楚如何将未来的超人级AI系统对齐以确保安全性从未如此重要，现在在这个问题上进行经验上的进展比以往任何时候都更容易，并对研究人员能够发现什么突破感到兴奋

————

<img src="https://img.saraba1st.com/forum/202312/15/175754jyjq60jjgla4111h.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231215-175721.jpg</strong> (272.04 KB, 下载次数: 0)

下载附件

2023-12-15 17:57 上传


*****

####  Machinery  
##### 1067#       发表于 2023-12-16 03:38

CogAgent

用于GUI代理者(GUI Agents)的视觉语言模型

项目综合主页:[https://github.com/THUDM/CogVLM](https://github.com/THUDM/CogVLM)

人们花费了大量的时间在数字设备的图形用户界面(GUI)上，例如计算机或智能手机屏幕等，诸如ChatGPT这样的大型语言模型(LLM)可以帮助人们完成写邮件之类的任务，但在理解和与GUI交互方面依然存在困难，这限制了它们在自动化水平方面继续提高的潜力

在本文中，介绍了CogAgent，一个具有180亿参数的视觉语言模型(VLM)，专门用于GUI的理解和导航，通过同时利用低分辨率和高分辨率图像编码器，CogAgent支持1120*1120分辨率的输入，使其能够识别微小的页面元素和文本

作为一个通用的视觉语言模型，CogAgent在五个富文本和四个通用的VQA基准测试(包括VQAv2、OK-VQA、Text-VQA、ST-VQA、ChartQA、infoVQA、DocVQA、MM-Vet和POPE)中达成了SOTA水平

CogAgent仅使用屏幕截图作为输入，在PC和Android GUI导航任务中优于消耗提取的HTML文本的LLM方法(Mind2Web和AITW)，推动了技术的发展

<img src="https://img.saraba1st.com/forum/202312/16/033615vrugyuhxh3uxaeau.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-033048__01.jpg</strong> (315.47 KB, 下载次数: 0)

下载附件

2023-12-16 03:36 上传

CogAgent生成的视觉代理者样本

<img src="https://img.saraba1st.com/forum/202312/16/033631ccnjjb4501c2452j.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-033106__01.jpg</strong> (176.85 KB, 下载次数: 0)

下载附件

2023-12-16 03:36 上传

CogAgent的模型构架，采用CogVLM作为原始的VLM

<img src="https://img.saraba1st.com/forum/202312/16/033643e5zouo7rsu75zyqb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-033124__01.jpg</strong> (133.24 KB, 下载次数: 0)

下载附件

2023-12-16 03:36 上传

在视觉问答基准测试中的表现，粗体表示通用类别中的最佳得分，而下划线文字表示通用类别和特定任务类别中的最佳得分

<img src="https://img.saraba1st.com/forum/202312/16/033652enn1aanaavgf4ob3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-033201__01.jpg</strong> (92.55 KB, 下载次数: 0)

下载附件

2023-12-16 03:36 上传

CogAgent在对话式问答和幻觉评测上的评估，关于POPE数据集，在评估中使用了其对抗子集(adversarial subset)

<img src="https://img.saraba1st.com/forum/202312/16/033703i4eu4u6uyxuoxm2u.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-033209__01.jpg</strong> (94.08 KB, 下载次数: 0)

下载附件

2023-12-16 03:37 上传

在Mind2Web任务上的表现。†表示从top-10元素候选项中选择，其他来自top-50

<img src="https://img.saraba1st.com/forum/202312/16/033732hx56gx5rhedt4dt4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-033209__02.jpg</strong> (84.35 KB, 下载次数: 0)

下载附件

2023-12-16 03:37 上传

在Android in the Wild(AITW)数据集上的表现，†表示在每个子集上进行独立微调的模型，而其他模型是跨越所有子集的统一模型

<img src="https://img.saraba1st.com/forum/202312/16/033750crra7kr7grorga3f.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-033221__01.jpg</strong> (48.78 KB, 下载次数: 0)

下载附件

2023-12-16 03:37 上传

不同模型构架和分辨率在前向传播过程中的FLOPs对比

<img src="https://img.saraba1st.com/forum/202312/16/033759fpffhaayp3haazoe.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-033221__02.jpg</strong> (56.42 KB, 下载次数: 0)

下载附件

2023-12-16 03:37 上传

模型架构的消融研究，训练时间是在批大小为8的A800上评估的，模型使用字幕说明+OCR数据进行预训练

<img src="https://img.saraba1st.com/forum/202312/16/033806lwvvhtbwz6s54l26.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-033221__03.jpg</strong> (51.67 KB, 下载次数: 0)

下载附件

2023-12-16 03:38 上传

预训练数据的消融实验，包括逐步添加图像字幕说明、OCR和其他预训练数据的实验

*****

####  Machinery  
##### 1068#       发表于 2023-12-16 03:41

StemGen

一种基于聆听的音乐生成模型

项目主页:[https://julian-parker.github.io/stemgen/](https://julian-parker.github.io/stemgen/)

最近，使用深度学习技术对音乐音频进行端到端生成的研究引发了热潮，然而，大多数模型专注于根据抽象的条件信息生成完全混合的音乐(fully mixed music)

在这项工作中，提出了一种可替代的范式，可以根据音乐上下文进行聆听与回应的音乐生成模型，本文描述了如何使用非自回归的基于Transformer的模型构架构建这样的模型，并提出了一些新颖的构架和采样改进方法

使用开源数据集和专有数据集对所描述的架构进行了训练，同时使用标准的质量指标和基于音乐信息检索描述符(music information retrieval descriptors)的新方法对生成的模型进行了评估，结果表明，所得模型在音频质量上达到了基于文本条件的模型水平的SOTA成绩，并且具有强大的与其上下文关联的音乐连贯表现

相关截图:

<img src="https://img.saraba1st.com/forum/202312/16/034105gbcuxo0xawiskfwz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-022109__01.jpg</strong> (78.5 KB, 下载次数: 0)

下载附件

2023-12-16 03:41 上传

<img src="https://img.saraba1st.com/forum/202312/16/034114n064xsddf440505i.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-022321.jpg</strong> (45.24 KB, 下载次数: 0)

下载附件

2023-12-16 03:41 上传


*****

####  Machinery  
##### 1069#       发表于 2023-12-16 04:28

 本帖最后由 Machinery 于 2023-12-16 04:29 编辑 

DCI

一张图片的价值超过 77 个文本Token:评估密集字幕说明上的CLIP样式模型

github项目仓库:[https://github.com/facebookresearch/DCI](https://github.com/facebookresearch/DCI)

大规模的视觉语言数据集的标注方法需要在数据集的大小和质量之间进行权衡筛选，然而，即使是最高质量的可用标注字幕说明，也远远无法捕捉到一幅图像中丰富的视觉细节

为了展示密集且高度对齐的图像文本对的价值，研究构造了密集字幕说明图像(DCI/Densely Captioned Images)数据集，其中包含8012张自然图像，每张图像都用人工标注的掩码对齐描述，平均每个描述超过1000个单词

通过将精确可靠的字幕与图像的特定部分关联起来，可以使用一项新任务评估视觉语言模型(VLM)对图像内容的理解程度，该任务要求将每个字幕说明与其相应的子裁切图进行匹配，由于当前的模型通常限制为77个文本Token，因此还引入了一个摘要版本(sDCI/summarized Densely Captioned Images)，其中每个字幕的长度有所限制

展示了在标准基准测试上取得进展的现代技术，在基于sDCI的基准上并没有显著改善，最后，使用sDCI对CLIP进行微调，并显示出与基线相比的显著改进，尽管训练集很小，通过发布第一个人工标注的密集图像字幕数据集，希望为下一代VLM的开发提供新的基准或微调方法

<img src="https://img.saraba1st.com/forum/202312/16/042647v3wjvr8qrqoxcvjo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-042400__01.jpg</strong> (287.95 KB, 下载次数: 0)

下载附件

2023-12-16 04:26 上传

DCI数据集中的一个例子，只显示了子掩码层次结构的部分

<img src="https://img.saraba1st.com/forum/202312/16/042710xpaayt2xtppqzh0e.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-042427__01.jpg</strong> (241.38 KB, 下载次数: 0)

下载附件

2023-12-16 04:27 上传

为图像的掩码编写描述的标注视图，为了清晰起见，掩码区域会高亮显示

<img src="https://img.saraba1st.com/forum/202312/16/042720ko4nzx11zizmnoe4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-042437__01.jpg</strong> (455.76 KB, 下载次数: 0)

下载附件

2023-12-16 04:27 上传

Llama2生成的sDCI摘要和负面的示例，每个图像和子掩码都有多个摘要和负面，还对比了DAC和DCI之间的字幕说明质量，与依赖于人工标注的DCI不同，DAC使用了基于LLM的自动工作流程进行字幕说明编写，正如在这个例子中观察到的，DAC的字幕可能会出现幻觉，并且错过照片的重要元素，在这项工作中认为，虽然改进自动工作流程是一个重要的研究方向，但目前提案的自动字幕说明还不足以可靠地用于评估模型的能力

<img src="https://img.saraba1st.com/forum/202312/16/042734vnd7xot2rrxv6riv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-042445__01.jpg</strong> (81.96 KB, 下载次数: 0)

下载附件

2023-12-16 04:27 上传

DCI数据集的统计数据与其他数据集的对比，重点关注了每个图像或字幕说明的平均CLIP Token数，请注意，DCI与之前最长的标注数据集Localized Narratives(LN)之间存在26倍的差异，sub表示包括子掩码及其描述作为示例，sDCI是指将DCI的字幕总结为77个Token的LLM版本，而LNCOCO&lt;77则代表简单地删除了超过77个标记的示例(约10.8%)

<img src="https://img.saraba1st.com/forum/202312/16/042758zopz8vcu4awyoz4v.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-042452__01.jpg</strong> (138.78 KB, 下载次数: 0)

下载附件

2023-12-16 04:27 上传

sDCI测试结果：在子裁切字幕说明匹配(SCM/Subcrop-Caption Matching)和负面测试中对比了现有的基线模型，注意到，在第5节中对sDCI进行微调的最佳模型在All SCM和All SCM Pick5的保留测试(held-out test)中分别达到了64.02%和31.60%，为模型性能设定了一个上限

<img src="https://img.saraba1st.com/forum/202312/16/042808rii63xs3464wdaa3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-042500__01.jpg</strong> (224.52 KB, 下载次数: 0)

下载附件

2023-12-16 04:28 上传

使用sDCI对CLIP进行微调，在ARO和VL-Checklist基准上测试，将使用DAC字幕进行微调的模型与使用sDCI进行微调的模型进行了对比，由于DAC数据集包含3百万张图像，而sDCI只包含8012张图像，因此对DAC数据集中使用的训练图像数量进行了消融实验

在这个例子中，DACLLM10000是指只使用DAC中的1万张图像对CLIP进行微调，绘制了5个不同随机种子的平均值，并在标准差超过1%准确率时显示出来，观察到，相比于使用DAC进行训练，使用sDCI进行训练在相似数量的样本上显著改进了性能


*****

####  Machinery  
##### 1070#       发表于 2023-12-16 04:56

Fine ControlNet

通过空间对齐文本控制注入带来的精细文本控制进行图像生成

项目主页:[https://samsunglabs.github.io/FineControlNet-project-page/](https://samsunglabs.github.io/FineControlNet-project-page/)

github项目主页(待整理):[https://github.com/SamsungLabs/FineControlNet](https://github.com/SamsungLabs/FineControlNet)

最近引入的ControlNet具有使用几何输入(geometric input)，如人体2D姿势或边缘特征等，来驱动基于文本的图像生成过程的能力，虽然ControlNet可以控制生成图像中实例的几何形状，但它缺乏控制每个实例的视觉外观的能力

为了在保持精确的姿态控制能力的同时对每个实例的外观进行精细控制，提出了FineControlNet，具体而言，通过人体姿态图像实现了几何控制，并使用实例级文本提示实现外观控制，在潜在空间中实例特定的文本提示和2D姿态的空间对齐使得FineControlNet具有精细控制能力

通过与基于姿态条件的SOTA文本到图像扩散模型进行严格对比来评估FineControlNet的性能，与现有方法相比，FineControlNet在生成遵循用户提供的实例特定文本提示和姿态的图像方面表现出卓越的性能

————

FineControlNet方法概览图

<img src="https://img.saraba1st.com/forum/202312/16/045544n0hble30seb51hqb.png" referrerpolicy="no-referrer">

<strong>method_overview.png</strong> (238.38 KB, 下载次数: 0)

下载附件

2023-12-16 04:55 上传

FineControlNet接受一个文本提示和一个空间条件图像作为输入，然后文本提示被解析，为每个条件实例分配一个独立的提示，之后将每个提示、草图、掩码和噪声图传递给模型，通过将每个独立提示信息空间注入到图像的不同区域，可以生成符合输入提示的高质量图像

————

定性结果

<img src="https://img.saraba1st.com/forum/202312/16/045615yhn4tdt9ft3n9a7d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-045602.jpg</strong> (346.03 KB, 下载次数: 0)

下载附件

2023-12-16 04:56 上传

将本文方法与6种SOTA基线方法进行了定性与定量对比，下面是本文方法生成的图像与基线方法的一些示例对比，有关完整的分析，请参阅论文

————

其他模态

<img src="https://img.saraba1st.com/forum/202312/16/045635k2jwsoe2tqlspejc.png" referrerpolicy="no-referrer">

<strong>other_modalities.png</strong> (272.22 KB, 下载次数: 0)

下载附件

2023-12-16 04:56 上传

本文方法还具有以除了人体姿态之外的其他模态作为条件能力，包括了其他模态条件的定性结果，例如Canny边缘、M-LSD、软边缘和草图输入作为本文方法可以处理的其他空间条件的示例


*****

####  Machinery  
##### 1071#       发表于 2023-12-16 05:33

 本帖最后由 Machinery 于 2023-12-16 05:36 编辑 

VL-GPT

用于视觉和语言理解和生成的生成式预训练Transformer(Generative Pre-trained Transformer)

github项目主页:[https://github.com/AILab-CVC/VL-GPT](https://github.com/AILab-CVC/VL-GPT)

在这项工作中，介绍了视觉语言生成式预训练Transformer(VL-GPT/Vision-Language Generative Pre-trained Transformer)，这是一个可以同时感知和生成视觉和语言数据的Transformer模型

VL-GPT通过采用直接的自回归目标来实现图像和文本两种模态的统一预训练方法，从而使模型能够像处理文本一样无缝处理图像和文本，为了实现这一目标，首先提出了一种新颖的图像分词-去词化器框架(image tokenizer-detokenizer framework)，专门设计用于将原始图像转换为连续嵌入序列，并进行相应的重建，结合现有的文本分词器和去分词化器(text tokenizer and detokenizer)，这个框架允许将交错的图像文本数据编码为多模态序列，随后可以将序列输入到Transformer模型中

因此，VL-GPT可以利用统一的自回归目标(即下一个Token预测)对多模态语料库进行大规模预训练，在预训练完成后，VL-GPT在各种视觉和语言理解和生成任务中展现出了非常出色的零样本和少样本性能，包括图像字幕说明生成、视觉问答、文本到图像生成等

此外，当给定多模态提示时，预训练模型可以进行上下文学习，进一步在VL-GPT上进行了指令调整，突出了它在多模态辅助方面的出色潜力，源代码和模型权重将会公开发布

<img src="https://img.saraba1st.com/forum/202312/16/053214t3mlsgdmniaqmm6u.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-052813__01.jpg</strong> (184.64 KB, 下载次数: 0)

下载附件

2023-12-16 05:32 上传

提出的方法概览图，上方部分描述了图像分词器-去分词器框架，用于将图像编码为连续的视觉嵌入，并在像素空间中重构图像，下方部分展示了VL-GPT的实现，其中交错的图像文本数据使用图像和文本分词器编码为多模态序列，随后由Transformer模型自回归式地处理，图像和文本去分词器用于生成相应的输出

<img src="https://img.saraba1st.com/forum/202312/16/053224ph6m2hiyb8mhh3bq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-052825__01.jpg</strong> (110.51 KB, 下载次数: 0)

下载附件

2023-12-16 05:32 上传

图像分词器-去分词器框架的训练方案是由预训练图像扩散模型的冻结图像和文本编码器进行监督的，只有分词器中的因果Transformer和去分词器中的Transformer解码器需要进行训练，而去分词器中的扩散解码器在训练过程中未被使用

<img src="https://img.saraba1st.com/forum/202312/16/053232cjl2618i2l4d6dk2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-052834__01.jpg</strong> (249.16 KB, 下载次数: 0)

下载附件

2023-12-16 05:32 上传

图像分词器-去分词器框架利用图像条件嵌入zv，文本条件嵌入zt或两种类型的条件嵌入zv+zt来重建图像

<img src="https://img.saraba1st.com/forum/202312/16/053244z67kgf0oglggjawf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-052844__01.jpg</strong> (54.68 KB, 下载次数: 0)

下载附件

2023-12-16 05:32 上传

使用CLIP相似性评估图像重建

<img src="https://img.saraba1st.com/forum/202312/16/053305jj3kmmchh4x6bxpk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-052855__01.jpg</strong> (249.22 KB, 下载次数: 0)

下载附件

2023-12-16 05:33 上传

使用VL-GPT模型与其他模型之间进行了评估对比，†表示零样本提示是通过采样两个特定任务的示例，并删除它们的相关图像来构建的，§表示用于指令调整的数据集是私有的

<img src="https://img.saraba1st.com/forum/202312/16/053315txn11xmu1rxgzacg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-052944__01.jpg</strong> (220.4 KB, 下载次数: 0)

下载附件

2023-12-16 05:33 上传

VL-GPT在各种视觉和语言理解与生成任务中的示例样本，这些任务包括:(1)-(2)图像描字幕说明，(3)视觉问答，(4)-(8)文本到图像生成，(9)-(10)多模态上下文生成，以及(11)-(12)多模态对话

示例(1)-(10)是由预训练的VL-GPT生成的，而(11)-(12)是由调整过的VL-GPT生成的，蓝色框表示多模态输入，黄色框表示VL-GPT输出

<img src="https://img.saraba1st.com/forum/202312/16/053323qsav95gbm93ncv59.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-052956__01.jpg</strong> (42.64 KB, 下载次数: 0)

下载附件

2023-12-16 05:33 上传

视觉问答方面的少样本表现

<img src="https://img.saraba1st.com/forum/202312/16/053348qeks4aaod1gome0k.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-052956__02.jpg</strong> (36.4 KB, 下载次数: 0)

下载附件

2023-12-16 05:33 上传

进行了条件嵌入类型的消融实验，使用文本嵌入et、图像嵌入ev或它们的组合et+ev来指导分词器-去分词器框架的训练，评估了在采用不同的图像分词器和去分词器时重建图像的效果和VL-GPT的性能


*****

####  Machinery  
##### 1072#       发表于 2023-12-16 06:41

PixelLLM

像素对齐的语言模型(Pixel Aligned Language Models)

项目主页:[https://jerryxu.net/PixelLLM](https://jerryxu.net/PixelLLM)

代码:coming soon

近年来，大型语言模型在自然语言处理领域取得了巨大成功，视觉领域的变体也同样如此，现有的视觉语言模型可以用自然语言描述图像，回答与视觉相关的问题，或者对图像进行复杂的推理，然而，目前尚不清楚如何使用大型语言模型执行定位任务(localization tasks)，例如词语基准(word grounding)或指代定位(referring localization)等任务

在这项工作中，旨在开发一种视觉语言模型，可以将位置(例如一组点或框)作为输入或输出，当将位置作为输入时，该模型执行基于位置条件的字幕说明生成(location-conditioned captioning)，为指定的对象或区域生成字幕说明，当生成位置作为输出时，本文模型通过语言模型生成的每个输出词的像素坐标进行回归，从而执行密集的词基准(dense word grounding)，本文模型在定位叙事数据集上进行了预训练，该数据集包含了人类注意力下的像素词语对齐(pixel-word-aligned)

展示了本文模型可以应用于各种位置感知的视觉语言任务，包括指代定位、基于位置条件的字幕说明生成和密集对象字幕说明生成，在RefCOCO和Visual Genome上达到了SOTA性能

————

<img src="https://img.saraba1st.com/forum/202312/16/064017thk6kqwhta6jhs66.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-060507.jpg</strong> (52.46 KB, 下载次数: 0)

下载附件

2023-12-16 06:40 上传

<img src="https://img.saraba1st.com/forum/202312/16/064026kkzzg92ssqwp9bqs.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-063607.jpg</strong> (103.13 KB, 下载次数: 0)

下载附件

2023-12-16 06:40 上传

每个由PixelLLM预测的词都与一个像素位置对齐

————

问题概览

<img src="https://img.saraba1st.com/forum/202312/16/064036oe822z5ekm28qlyb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-062524.jpg</strong> (49.41 KB, 下载次数: 0)

下载附件

2023-12-16 06:40 上传

提出了像素对齐语言模型(PixelLLM)，为大型语言模型提供定位能力，该模型在定位图像字幕说明数据上进行预训练，其中每个词都标有一个像素位置，以学习单词与图像像素之间的对齐关系，PixelLLM可以应用于各种定位任务，例如，在输入位置时进行位置条件字幕说明生成，以及在生成位置输出时进行指代定位

————

用于像素对齐字幕说明的PixelLLM架构

<img src="https://img.saraba1st.com/forum/202312/16/064052qwblte24drbwrhkl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-063634.jpg</strong> (39.97 KB, 下载次数: 0)

下载附件

2023-12-16 06:40 上传

PixelLLM架构，用于像素对齐的字幕说明生成，首先分别使用提示编码器P和图像编码器V对输入的位置提示(在这个用例中是全局框提示)和输入图像进行编码，然后将提示特征l和图像特征f输入到提示特征提取器中，以提取特定位置的视觉特征fl，大型语言模型L根据先前的文本Token和视觉特征，自回归地预测下一个文本Token，在LLM的词汇映射层(vocabulary mapping layer)之前，对Token特征应用一个简单的MLP层，预测每个文本Token的坐标，字幕说明与追踪之间的对齐由颜色渐变表示

————

定性结果展示

<img src="https://img.saraba1st.com/forum/202312/16/064114qamfpi6uwiajkp4m.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-063714.jpg</strong> (526.67 KB, 下载次数: 0)

下载附件

2023-12-16 06:41 上传

————

指代定位与分割

<img src="https://img.saraba1st.com/forum/202312/16/064124htltrheq22e50ror.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-063740.jpg</strong> (376.86 KB, 下载次数: 0)

下载附件

2023-12-16 06:41 上传

————

稠密对象字幕说明

<img src="https://img.saraba1st.com/forum/202312/16/064137t657qw5vaz5sym5a.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-063844.jpg</strong> (227.57 KB, 下载次数: 0)

下载附件

2023-12-16 06:41 上传


*****

####  Machinery  
##### 1073#       发表于 2023-12-16 07:01

TigerBot

开源多语言多任务LLM(Multilingual Multitask LLM)

github项目主页:[https://github.com/TigerResearch/TigerBot](https://github.com/TigerResearch/TigerBot)

本文发布并介绍了TigerBot系列的大型语言模型(LLM)，包括基础模型和聊天模型，参数大小分别为70亿、130亿、700亿和1800亿，通过从Llama-2和BLOOM开始开发模型，并在数据、训练算法、基础设施和应用工具方面推动了发展界限

本文模型在SOTA系列开源模型(例如Llama-2)的基础上进一步取得了有意义的性能提升，英文效果提升6%，中文效果提升了20%，TigerBot模型系列在主要的学术和工业基准测试和排行榜中也取得了领先的性能，相信TigerBot只是LLM开源社区中迅猛发展的一个缩影

因此，研究组非常高兴通过公开发布模型并报告，特别强调了以自由化的方式构建SOTA LLM，并使LLM在真实世界的应用中发挥作用

项目说明页截图:

<img src="https://img.saraba1st.com/forum/202312/16/070120dn7vx8qa5u0pvvvw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-065840.jpg</strong> (86.18 KB, 下载次数: 0)

下载附件

2023-12-16 07:01 上传

<img src="https://img.saraba1st.com/forum/202312/16/070128bo6jdrfkh6vkbko5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-065918.jpg</strong> (198.79 KB, 下载次数: 0)

下载附件

2023-12-16 07:01 上传


*****

####  Machinery  
##### 1074#       发表于 2023-12-16 20:53

 本帖最后由 Machinery 于 2023-12-16 20:56 编辑 

GLEE

大规模图像和视频的通用对象基础模型

项目主页:[https://glee-vision.github.io/](https://glee-vision.github.io/)

github项目仓库:[https://github.com/FoundationVision/GLEE](https://github.com/FoundationVision/GLEE)

hugface演示demo:[https://huggingface.co/spaces/Junfeng5/GLEE_demo](https://huggingface.co/spaces/Junfeng5/GLEE_demo)

在这项工作中，提出了GLEE，这是一个用于在图像和视频中定位和识别对象的对象级基础模型(object-level foundation model)，通过统一的框架，GLEE可以在各种对象感知任务的开放世界场景中完成检测、分割、追踪、基准和识别任意对象

通过采用一个连贯的学习策略，GLEE从不同的数据源中获取知识，并通过不同的监督级别(varying supervision levels)来形成通用的对象表征，在零样本迁移到新数据和任务时同样表现出色

具体而言，使用图像编码器、文本编码器和视觉提示器来处理多模态输入，能够同时解决多种以对象为中心的下游任务，并保持SOTA性能

通过在来自不同基准测试集的五百万张图像上进行广泛训练，GLEE展现出了卓越的多功能性和改进的泛化性能，可以在无需适配的情况下高效地处理下游任务，通过整合大量自动标注的数据，进一步提升了它的零样本泛化能力

此外，GLEE还可以集成到大型语言模型中，作为一个基础模型为多模态任务提供通用的对象级信息，希望本文方法的多功能性和普适性可以为AGI系统的高效视觉基础模型的发展迈出重要一步

<img src="https://img.saraba1st.com/forum/202312/16/205135bbmqswdxcbbqxak0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-204640__01.jpg</strong> (117.43 KB, 下载次数: 0)

下载附件

2023-12-16 20:51 上传

在广泛的对象级任务上使用GLEE与现有模型进行了对比

<img src="https://img.saraba1st.com/forum/202312/16/205146vm11v03v97xgq0sw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-204700__01.jpg</strong> (392.71 KB, 下载次数: 0)

下载附件

2023-12-16 20:51 上传

一个具有说明性的例子，展示了来自不同数据集的不同粒度的标注，以及使用到的数据规模，在多个来源的数据集上进行训练赋予了模型更通用的表征能力

<img src="https://img.saraba1st.com/forum/202312/16/205156coen29d55p4fljrj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-204710__01.jpg</strong> (312.62 KB, 下载次数: 0)

下载附件

2023-12-16 20:51 上传

GLEE的框架，文本编码器接受来自不同数据源的多种形式的文本描述，包括对象类别(object categories)、名称(names)、字幕说明(captions)和指代表达(referring expressions)，视觉提示器将点、边界框或涂鸦转换为相应的视觉表征，对象解码器使用它们和图像特征来预测图像中的对象

(b)图部分说明了GLEE在为不同语言描述和视觉提示量身定制的图像任务中的应用

(c)演示了在各种对象级视频任务中的应用

<img src="https://img.saraba1st.com/forum/202312/16/205209kxa7rzclq3qaax1x.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-204728__01.jpg</strong> (257.37 KB, 下载次数: 0)

下载附件

2023-12-16 20:52 上传

使用GLEE与最近的专用模型和通用模型在在对象级图像任务上进行了对比，对于REC和RES任务，报告了Precision@0.5和整体IoU(oIoU)，对于开放世界实例分割任务，报告了在UVO上的100个掩码提案的平均召回率(AR@100)

<img src="https://img.saraba1st.com/forum/202312/16/205220x5f3jzgkmp5assw8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-204738__01.jpg</strong> (238.43 KB, 下载次数: 0)

下载附件

2023-12-16 20:52 上传

使用GLEE与最近的专用模型和通用模型在对象级视频任务上以零样本的方式进行了对比，对于BURST评估指标，分别报告了“常见”、“不常见”和“所有”类别，mAP在追踪级别计算掩码IoU，HOTA是每帧检测准确率(DetA/detection accuracy)和时间关联准确率(AssA/association accuracy)的平均，而TETA将检测分解为定位和分类组件，LV-VIS中的AP、APb和APn表示整体类别、基本类别和新颖类别(overall categories, base categories, and novel categories)的平均精度，†表示不使用视频进行训练，Pro在LV-VIS上相对于Plus的表现不佳是因为Pro使用了更大的训练和推理分辨率，证明了对于这个特定的数据集来说是次优的

<img src="https://img.saraba1st.com/forum/202312/16/205233tfh8eppj13vvcgb3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-204745__01.jpg</strong> (154.42 KB, 下载次数: 0)

下载附件

2023-12-16 20:52 上传

13个OdinW数据集上的零样本性能

<img src="https://img.saraba1st.com/forum/202312/16/205245abuba4urrn4f4f7b.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-204752__01.jpg</strong> (170.14 KB, 下载次数: 0)

下载附件

2023-12-16 20:52 上传

使用GLEE在视频实例分割任务上进行了性能对比

<img src="https://img.saraba1st.com/forum/202312/16/205303aas6k0g3jm1fayvw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-204802__01.jpg</strong> (63.36 KB, 下载次数: 0)

下载附件

2023-12-16 20:53 上传

在将SAM替换为GLEE的情况下，对LISA中的表现进行了性能对比，结果显示GLEE在提取对象方面达到了与SAM相同的效果

<img src="https://img.saraba1st.com/forum/202312/16/205310sqgog7opqzciaii0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-204811__01.jpg</strong> (53.74 KB, 下载次数: 0)

下载附件

2023-12-16 20:53 上传

数据缩放，在TAO、BURST、OVIS、YTVIS19上分别使用10%、20%、50%、100%的总数据进行训练后，GLEE-Pro的性能表现，训练数据规模的增加后在各种下游任务中的零样本性能得到提升

<img src="https://img.saraba1st.com/forum/202312/16/205321aqgw66hdmzt90ms5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231216-204819__01.jpg</strong> (147.08 KB, 下载次数: 0)

下载附件

2023-12-16 20:53 上传

在OmniLabel基准测试上的评估结果，最终的AP值是类别(AP-categ)和自由形式描述(AP-descr)之间的几何平均值(geometric mean)


*****

####  Machinery  
##### 1075#       发表于 2023-12-17 03:19

 本帖最后由 Machinery 于 2023-12-17 03:20 编辑 

SceneWiz3D

迈向文本引导的3D场景合成

项目主页:[https://zqh0253.github.io/SceneWiz3D/](https://zqh0253.github.io/SceneWiz3D/)

github项目代码仓库(待整理):[https://github.com/zqh0253/SceneWiz3D](https://github.com/zqh0253/SceneWiz3D)

我们正在见证从文本生成3D对象的技术取得的重大突破，现有的方法要么利用大型文本到图像模型来优化3D表征，要么在以对象物体为中心的数据集上训练3D生成器，因此，生成整个场景仍然非常具有挑战性，因为一个场景包含了多个3D对象，而且这些对象是多样且分散的

在这项工作中，引入了一种新方法，SceneWiz3D，用于从文本合成具有高保真度的3D场景，通过引入混合的3D表征(hybrid 3D representation)方法，将对象的局部性与场景的整体性相结合:3D对象的表征是显式的，而场景是隐式的，值得注意的是，具有明确表示的对象可以通过传统的文本到3D方法生成，也可以由用户提供

为了配置场景的布局并自动放置对象，在优化过程中应用了粒子群优化技术(Particle Swarm Optimization technique)，此外，对于场景难以确认的某些部分(例如角落、遮挡)，很难获得多视图监督，从而导致几何质量较差的问题，通过引入了一种RGBD全景扩散模型(RGBD panorama diffusion model)来减轻这个问题，从而获得高质量的几何形状，广泛的评估支持了本文方法在质量上优于之前的方法，且能够生成细节丰富视角一致的3D场景

<img src="https://img.saraba1st.com/forum/202312/17/031504qii0wfm2xwmzywz3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231217-030838__01.jpg</strong> (387.48 KB, 下载次数: 0)

下载附件

2023-12-17 03:15 上传

本文方法可以合成多样化的3D场景，如图所示，可以将从文本提示自动生成的对象(在左上角和右上角，标记为机器人头部图标)或由用户提供的对象(在右中部标记为人类头像图标)整合进来，本文方法适用于不同类型和风格的场景，并支持对场景的操作，如移动或删除对象(下方)

<img src="https://img.saraba1st.com/forum/202312/17/031515l6r6ux90ymw0kkxu.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231217-030850__01.jpg</strong> (244.42 KB, 下载次数: 0)

下载附件

2023-12-17 03:15 上传

SceneWiz3D概览图，为了建模3D场景，采用了包含显式和隐式组件的混合表征:对于感兴趣的物体(OOIs/objects of interest)使用DMTets，对于环境则采用NeRF，在给定文本提示后，首先识别场景的OOIs，并初始化它们的DMTets，之后基于CLIP相似度使用粒子群优化来更新OOIs的配置，并使用文本到图像扩散模型、全景RGBD扩散模型和深度正则化器来更新OOIs和环境的分数蒸馏

<img src="https://img.saraba1st.com/forum/202312/17/031527sq3fs3ibf31331i3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231217-030916__01.jpg</strong> (196.69 KB, 下载次数: 0)

下载附件

2023-12-17 03:15 上传

发现场景配置对于2D(上方)和3D(下方)来说都是非常重要的，简单的基于梯度的优化方法在低维和非凸优化空间中容易陷入局部最小值，导致出现不太可能的配置(物体重叠或放置错误)，相比之下，粒子群优化能够正确地识别出合理的配置

<img src="https://img.saraba1st.com/forum/202312/17/031537nb8j321b8ljlbbbl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231217-030934__01.jpg</strong> (238.94 KB, 下载次数: 0)

下载附件

2023-12-17 03:15 上传

与基线的定性对比，提示为“a bedroom, realistic detailed photo”

<img src="https://img.saraba1st.com/forum/202312/17/031548gn70xfzmbmcfnovo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231217-030944__01.jpg</strong> (71.16 KB, 下载次数: 0)

下载附件

2023-12-17 03:15 上传

与基线的定量对比

<img src="https://img.saraba1st.com/forum/202312/17/031559dt18kgv8rgv3zxxt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231217-030950__01.jpg</strong> (90.84 KB, 下载次数: 0)

下载附件

2023-12-17 03:15 上传

定量消融实验

<img src="https://img.saraba1st.com/forum/202312/17/031612w5lxh2rtztkx8t3k.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231217-031001__01.jpg</strong> (261.66 KB, 下载次数: 0)

下载附件

2023-12-17 03:16 上传

定性消融实验，提示为“a washing room,realistic detailed photo”

<img src="https://img.saraba1st.com/forum/202312/17/031624jcn3ocz3c7c6i65s.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231217-031019__01.jpg</strong> (323.78 KB, 下载次数: 0)

下载附件

2023-12-17 03:16 上传

在场景合成中，Janus问题被表达为同一物体类别的多个实例，可以通过混合表征来缓解，每个边界框颜色代表一个唯一的身份

<img src="https://img.saraba1st.com/forum/202312/17/031646jk4vqzs7kdzqk3ii.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231217-031038__01.jpg</strong> (634.78 KB, 下载次数: 0)

下载附件

2023-12-17 03:16 上传

由SceneWiz3D生成的各种不同场景，展示了本文方法成功地泛化到不同类型的场景(室内、室外)，并且能够适应不同的风格(逼真、卡通、绘画)和感兴趣的对象类别(人物、物体)

<img src="https://img.saraba1st.com/forum/202312/17/031925mzkz235jtpdaaxpa.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231217-031049__01.jpg</strong> (521.82 KB, 下载次数: 0)

下载附件

2023-12-17 03:19 上传

由SceneWiz3D生成的多样化的艺术卧室场景，SceneWiz3D能够成功地泛化到广泛的多种场景特征，涵盖了各种艺术风格和风景，通过提出的混合表征方法，可以同时保持前景对象的多视图一致性，并合成具有不同结构的背景(从摩天大楼、日落、银河系到从燃烧的房屋烟雾扩散)


*****

####  Machinery  
##### 1076#       发表于 2023-12-18 20:03

Amphion

开源音频、音乐和语音生成工具包

github项目主页:https://github.com/open-mmlab/Amphion

Amphion是一个用于音频、音乐和语音生成的工具包，它的目的是支持可重现的研究，并帮助初级研究人员和工程师在音频、音乐和语音生成研究和开发领域入门

Amphion提供了一个独特的特点:经典模型或架构的可视化，相信这些可视化对于那些希望更好地理解模型的初级研究人员和工程师更有益，Amphion的北极星目标(North-Star objective for North Star Approach)是提供一个平台，用于研究将任何输入转换为通用音频

Amphion旨在支持独立生成任务，除了特定的生成任务之外，Amphion还包括几个声码器(vocoders)和评估指标(evaluation metrics)，声码器是产出高质量音频信号的重要模块，而评估指标对于确保生成任务中的一致性至关重要

<img src="https://img.saraba1st.com/forum/202312/18/200228ggmhbf797gp4mff1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231218-195802__01.jpg</strong> (53.81 KB, 下载次数: 0)

下载附件

2023-12-18 20:02 上传

Amphion工具包的北极星目标

<img src="https://img.saraba1st.com/forum/202312/18/200236jdd3r12rtdqhv42h.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231218-195812__01.jpg</strong> (253.7 KB, 下载次数: 0)

下载附件

2023-12-18 20:02 上传

目前开源社区中与音频、音乐和语音生成相关的开源工具包一览

<img src="https://img.saraba1st.com/forum/202312/18/200311jni75ywq27228rzc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231218-195816__01.jpg</strong> (83.62 KB, 下载次数: 0)

下载附件

2023-12-18 20:03 上传

Amphion的系统架构设计，从底层开始:

(1)将数据处理(数据集、特征和数据加载器)、通用模块(模块)和优化算法(优化器、调度器和训练器)统一为所有音频生成任务的基础设施

(2)对于每个特定的生成任务，统一其数据/特征使用(任务加载器)、模型框架(任务框架)和训练工作流程(任务训练器)

(3)在每个生成任务中，为每个特定的基线指定架构(模型架构)和训练工作流程(模型训练器)

(4)最后，为用户提供每个模型的指导(配方)，统一了所有模型的配方格式，并尽可能使其自独立(self-contained)且适合新手使用

<img src="https://img.saraba1st.com/forum/202312/18/200321odjwtt1uq7w6q0q5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231218-195821__01.jpg</strong> (32.06 KB, 下载次数: 0)

下载附件

2023-12-18 20:03 上传

Amphion文本到语音生成的工作流程

<img src="https://img.saraba1st.com/forum/202312/18/200328ce7z51q6ei9o6oo0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231218-195827__01.jpg</strong> (48.17 KB, 下载次数: 0)

下载附件

2023-12-18 20:03 上传

Amphion歌声转换的工作流程

<img src="https://img.saraba1st.com/forum/202312/18/200334wscpdceqpdezoeer.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231218-195834__01.jpg</strong> (41.8 KB, 下载次数: 0)

下载附件

2023-12-18 20:03 上传

Amphion文本到音频生成的工作流程

<img src="https://img.saraba1st.com/forum/202312/18/200339kq3xgxhmkddzdmlm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231218-195840__01.jpg</strong> (29.09 KB, 下载次数: 0)

下载附件

2023-12-18 20:03 上传

Amphion神经声码器的工作流程

<img src="https://img.saraba1st.com/forum/202312/18/200344x11dlsu444mhu1wc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231218-195849__01.jpg</strong> (315.81 KB, 下载次数: 0)

下载附件

2023-12-18 20:03 上传

基于扩散的SVC模型的可视化

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1077#       发表于 2023-12-18 22:04

 本帖最后由 Machinery 于 2023-12-18 22:06 编辑 

DreamTalk

当富有表现力的对话头像(Talking Head)生成遇到扩散概率模型

项目主页:https://dreamtalk-project.github.io/

github综合项目仓库:https://github.com/damo-vilab/i2vgen-xl

扩散模型在各种下游生成任务中展现出了非凡的成功，但在重要且具有挑战性的表情丰富的对话头像生成领域仍然鲜有探索，在这项工作中，提出了一个名为DreamTalk的框架来填补这一空白，通过应用精心的设计来发挥扩散模型在生成表情丰富的对话头像方面的潜力

具体而言，DreamTalk由三个关键组件组成:去噪网络、风格感知的唇部专家(a style-aware lip expert)和风格预测器(style predictor)

基于扩散的去噪网络能够持续合成高质量的包含多种表情的由音频驱动的面部动作，为了增强唇部动作的表现力和准确性，引入了一个风格感知的唇部专家，可以在注意说话风格的同时引导嘴唇同步，为了消除对表情参考视频或文本的需求，还使用了一个额外的基于扩散的风格预测器直接从音频中预测目标表情，通过这种方式，DreamTalk可以利用强大的扩散模型有效生成表情丰富的面部，并减少对昂贵的风格参考的依赖

实验结果表明，DreamTalk能够生成具有照片级真实度的多种说话风格的对话头像，并实现准确的唇部动作，超越现有的SOTA方法

<img src="https://img.saraba1st.com/forum/202312/18/220304zp5bogrpgepe54pr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231218-215409__01.jpg</strong> (91.1 KB, 下载次数: 0)

下载附件

2023-12-18 22:03 上传

借助强大的扩散模型，DreamTalk能够生成具有高度表达力的各种说话风格的说话头像，此外，DreamTalk还能够直接从输入音频中提取个性化的说话风格，从而省去了额外的风格参考的需要

<img src="https://img.saraba1st.com/forum/202312/18/220312xo0z7lebji6le2ht.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231218-215423__01.jpg</strong> (349.43 KB, 下载次数: 0)

下载附件

2023-12-18 22:03 上传

DreamTalk的图示

首先训练了一个在给定说话风格的情况下对唇部音频同步概率(lip-audio synchronous probability)进行评估的风格感知唇部专家(b)，为去噪网络(a)提供唇部运动指导

然后，训练去噪网络以将音频、风格参考视频和嘈杂的面部运动作为输入，并预测无噪声的面部运动

接下来，训练了一个风格预测器(c)，用于预测从视频中提取的风格编码，以音频和视频中的说话者作为输入

在推理过程中(d)，可以使用从视频中提取或从音频中衍生的风格代码来指定说话风格

<img src="https://img.saraba1st.com/forum/202312/18/220320lffll6gmg7xh7g6f.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231218-215436__01.jpg</strong> (397.58 KB, 下载次数: 0)

下载附件

2023-12-18 22:03 上传

MEAD、HDTF和Voxceleb2上的定量对比，由于仅收到了MEAD和HDTF上的GC-AVT样本，因此未在Voxceleb2上评估GC-AVT

<img src="https://img.saraba1st.com/forum/202312/18/220333lwll7tm2e4ezr26p.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231218-215459__01.jpg</strong> (372.22 KB, 下载次数: 0)

下载附件

2023-12-18 22:03 上传

与之前的方法进行定性对比

<img src="https://img.saraba1st.com/forum/202312/18/220340bontiis5gbgty2xt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231218-215517__01.jpg</strong> (147.88 KB, 下载次数: 0)

下载附件

2023-12-18 22:03 上传

在StyleTalk的输出中观察到面部扭曲

<img src="https://img.saraba1st.com/forum/202312/18/220346fmqmb8nbxq8wbqw8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231218-215517__02.jpg</strong> (123.38 KB, 下载次数: 0)

下载附件

2023-12-18 22:03 上传

与DiffTalk进行对比

<img src="https://img.saraba1st.com/forum/202312/18/220351bfx7u0cfxc7ii0f0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231218-215517__03.jpg</strong> (187.19 KB, 下载次数: 0)

下载附件

2023-12-18 22:03 上传

使用域外(out-of-domain)头像生成的结果

<img src="https://img.saraba1st.com/forum/202312/18/220357ffq4ctmuzlllt7ft.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231218-215733__01.jpg</strong> (178.35 KB, 下载次数: 0)

下载附件

2023-12-18 22:03 上传

说话风格预测结果，第四列展现了应用预测风格后的生成的相同头像的样本，以便进行更清晰的对比

<img src="https://img.saraba1st.com/forum/202312/18/220402luxb74xm7mr7kx4z.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231218-215733__02.jpg</strong> (58.06 KB, 下载次数: 0)

下载附件

2023-12-18 22:04 上传

消融实验结果

<img src="https://img.saraba1st.com/forum/202312/18/220407p7sqllcsc1kslq9s.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231218-215744__01.jpg</strong> (60.04 KB, 下载次数: 0)

下载附件

2023-12-18 22:04 上传

在MEAD上进行的DreamTalk的消融实验结果，由于在CPBD指标上各个变体之间没有显著差异，省略了CPBD分数

<img src="https://img.saraba1st.com/forum/202312/18/220413gy6rechu5o6o785k.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231218-215744__02.jpg</strong> (31.81 KB, 下载次数: 0)

下载附件

2023-12-18 22:04 上传

15个说话者的风格代码的t-SNE可视化，每种颜色都代表来自对应同一说话者的风格代码

<img src="https://img.saraba1st.com/forum/202312/18/220421sn2hnorz9b5zuoxx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231218-215750__01.jpg</strong> (71.81 KB, 下载次数: 0)

下载附件

2023-12-18 22:04 上传

通过调整无分类器引导的尺度ω来控制输入风格的效果

<img src="https://img.saraba1st.com/forum/202312/18/220432acrrbnx3cbaqi83d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231218-215750__02.jpg</strong> (112.74 KB, 下载次数: 0)

下载附件

2023-12-18 22:04 上传

说话风格插值(speaking style interpolation)的结果

<img src="https://img.saraba1st.com/forum/202312/18/220438vds8wpfhfw6dashd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231218-215750__03.jpg</strong> (162.02 KB, 下载次数: 0)

下载附件

2023-12-18 22:04 上传

用户研究结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  chaosliu  
##### 1078#       发表于 2023-12-18 23:21

刚开始学，想借楼问下有s1群吗？我想整一个不怎么吃显存的本地模型<img src="https://static.saraba1st.com/image/smiley/face2017/068.png" referrerpolicy="no-referrer">，手上显卡就一张3070


*****

####  Machinery  
##### 1079#       发表于 2023-12-18 23:34

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63370206&amp;ptid=2126390" target="_blank">chaosliu 发表于 2023-12-18 23:21</a>
刚开始学，想借楼问下有s1群吗？我想整一个不怎么吃显存的本地模型，手上显卡就一张3070 ...</blockquote>
请看888楼

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  诚司  
##### 1080#       发表于 2023-12-19 01:34

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63370206&amp;ptid=2126390" target="_blank">chaosliu 发表于 2023-12-18 23:21</a>

刚开始学，想借楼问下有s1群吗？我想整一个不怎么吃显存的本地模型，手上显卡就一张3070 ...</blockquote>
8G显存的话，如果用pytorch（sd webui或者hf的transformers库），stable Diffusion和 7b量级的int4量化大语言模型都勉强够部署，再多一点都不行了（比如7b的langchain-chatchat就不行）但如果是cuda编译的stable diffusion.cpp和llama.cpp的话，显存绰绰有余，速度也很快

跑demo，sd不带lora大概占2.7G显存，20 steps半分钟出图

qwen 7b int4用llama.cpp，显存只占2g，大概7b不量化也跑的起来，不过我没试过，但是14b int4是跑不起来的（当然cpu给力的话，14b int4只用cpu跑的起来）

7b级别的大模型的话，int4和float16感觉差很多，特别是指令遵从度上。7b float16到14b这个量级才能大致有点生产力


*****

####  Machinery  
##### 1081#       发表于 2023-12-19 02:53

SPC

使用大型语言模型进行可信的角色(Persona-based)对话数据集生成

github项目仓库:https://github.com/google-research-datasets/Synthetic-Persona-Chat

高质量的对话数据集对于开发能够与用户进行交流的AI模型至关重要，其中一种方法是通过角色扮演促进聊天机器人与用户之间更深入的互动，用户的个性视角可以提供更深入的对于他们的性格，动机和行为的洞察，在多样化和全面的基于角色扮演的数据集上训练自然语言处理(NLP)模型可以创建出与用户建立更深层次联系并保持参与度的对话模型

在这篇论文中，通过利用大型语言模型(LLMs)的能力，从种子数据集(seed dataset)创建出一个大型高质量的对话数据集，提出了一个生成器-评判者架构框架(Generator-Critic architecture framework)来扩展初始数据集，并改善对话质量

生成器是一个被提示输出对话的LLM，评判者则由一系列混合专家LLM(mixture of expert LLM)组成，用以控制生成的对话质量，这些专家选择最佳的生成对话，然后用它们来改进生成器

发布了一个名为Synthetic-Persona-Chat的数据集，其中包含从Persona-Chat中种子化的20000个对话，通过广泛的实验评估了Synthetic-Persona-Chat和本文的生成框架在不同维度上的质量，观察到在三次迭代过程中，Synthetic-Persona-Chat相对于Persona-Chat在图灵测试中的失败率从17.2%降低到了8.8%

<img src="https://img.saraba1st.com/forum/202312/19/025306tu8iat8uazbsu7aq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-024942.jpg</strong> (96.71 KB, 下载次数: 0)

下载附件

2023-12-19 02:53 上传

不可信的对话(左):热爱牛排与“I am a vegetarian”这一人设属性呈负相关

可信的对话(右):它没有引入任何与用户个人资料相矛盾或减弱的信息

<img src="https://img.saraba1st.com/forum/202312/19/025311l33pp4nxpp87za74.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-025002.jpg</strong> (59.85 KB, 下载次数: 0)

下载附件

2023-12-19 02:53 上传

数据集增强工作流程

<img src="https://img.saraba1st.com/forum/202312/19/025316mxcf2xyjc9c9lbfp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-025021.jpg</strong> (157.42 KB, 下载次数: 0)

下载附件

2023-12-19 02:53 上传

查询归纳步骤

<img src="https://img.saraba1st.com/forum/202312/19/025323l9um5118v9391583.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-025034.jpg</strong> (109.38 KB, 下载次数: 0)

下载附件

2023-12-19 02:53 上传

基于查询的角色引导自举过程

<img src="https://img.saraba1st.com/forum/202312/19/025327xgg9jptgcs2898g8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-025102.jpg</strong> (60.93 KB, 下载次数: 0)

下载附件

2023-12-19 02:53 上传

用于对话生成的生成器-评判者架构

<img src="https://img.saraba1st.com/forum/202312/19/025333ysejs35m8bmtx1fh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-025120.jpg</strong> (52 KB, 下载次数: 0)

下载附件

2023-12-19 02:53 上传

对扩展角色集的评估，带有∗的数字表示新生成的角色属性的指标值，用于与初始集进行对比

<img src="https://img.saraba1st.com/forum/202312/19/025337jxya8oabb6carrav.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-025147__01.jpg</strong> (270.71 KB, 下载次数: 0)

下载附件

2023-12-19 02:53 上传

实验的下一句发言(utterance)预测结果，训练模型在Persona-Chat测试分割上的性能由表中的数字表示，而括号中的数字表示在Synthetic-Persona-Chat测试分割上的结果

<img src="https://img.saraba1st.com/forum/202312/19/025343kadgr3zxxv3c88qx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-025216.jpg</strong> (78.73 KB, 下载次数: 0)

下载附件

2023-12-19 02:53 上传

每次迭代，使用200个生成的对话进行图灵测试，Synthetic-Persona-Chat在对抗中超越了Persona-Chat

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1082#       发表于 2023-12-19 03:46

Point Transformer V3

更简单、更快、更强大

项目主页:https://github.com/Pointcept/PointTransformerV3

这篇论文并没有以创新的动机来探索注意力机制内部的创新，相反，它专注于克服点云处理中准确性和效率之间的现有权衡，充分利用规模的力量，从最近在3D大规模表征学习方面的进展中获取的灵感，使我们认识到，模型性能更多地受到规模的影响，而不是复杂的设计

因此，本文提出了Point Transformer V3(PTv3)，它优先考虑简单性和效率，而不是某些机制的准确率，这些机制对扩展后的整体性能影响较小，例如用高效的序列邻映射(efficient serialized neighbor mapping)代替精确的KNN邻搜索(precise neighbor search by KNN)，以特定的模式组织点云

这个原则实现了显著的扩展，将感受野(receptive field)从16个点扩展到1024个点，同时保持了高效，与前身PTv2相比，处理速度提高了3倍，显存效率提高了10倍

PTv3在涵盖室内外场景的20多个下游任务上取得了SOTA结果，通过多数据集联合训练进一步增强了PTv3的结果，将其推向了更高的水平

<img src="https://img.saraba1st.com/forum/202312/19/034603mlix110w3ilnqxii.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-034233__01.jpg</strong> (321.73 KB, 下载次数: 0)

下载附件

2023-12-19 03:46 上传

PTv3是Point Transformer V3的缩写，相较于其前身PTv2，在以下几个方面表现出了更卓越的性能:
1.更强的性能，PTv3在各种室内外3D感知任务中取得了SOTA结果
2.更广阔的感受野，得益于简单高效的设计，PTv3将感受野从16个点扩展到1024个点
3.更快的速度，PTv3显著提高了处理速度，使其适用于对延迟敏感的应用
4.更低的显存消耗，PTv3减少了显存使用，提升了在更广泛情景中的可用性

<img src="https://img.saraba1st.com/forum/202312/19/034611j5ea584ia4vnjlez.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-034250__01.jpg</strong> (209.93 KB, 下载次数: 0)

下载附件

2023-12-19 03:46 上传

模型效率，使用不同尺度的感受野基准测试主干网络的训练和推理效率，批大小固定为1，/后面的数字表示稀疏卷积的核大小和注意力的区块大小(patch size1)

<img src="https://img.saraba1st.com/forum/202312/19/034621gufwv7i2zg7pp3v2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-034252__01.jpg</strong> (81.68 KB, 下载次数: 0)

下载附件

2023-12-19 03:46 上传

PTv2的每个组件的延迟树状图(Latency treemap)，对PTv2每个组件的前向时间进行了基准测试和可视化比例，KNN查询和RPE占据了全部前向时间的54%

<img src="https://img.saraba1st.com/forum/202312/19/034626ttxf5bfapw3sfb75.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-034300__01.jpg</strong> (428.2 KB, 下载次数: 0)

下载附件

2023-12-19 03:46 上传

点云序列化，通过三元组可视化展示了四种序列化模式，对于每个三元组，展示了序列化的空间填充曲线(左)，点云序列化在空间填充曲线内的排列顺序(中)，以及序列化点云的分组区块以进行局部注意力(右)，在四种序列化模式之间进行切换使得注意机制能够捕捉到不同的空间关系和上下文，从而提高模型的准确性和泛化能力

<img src="https://img.saraba1st.com/forum/202312/19/034631m3k1bkiiqzh3x74i.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-034309__01.jpg</strong> (118.98 KB, 下载次数: 0)

下载附件

2023-12-19 03:46 上传

区块分组

(a)根据特定的序列化模式重新排序点云
(b)通过从邻区块中借用点来填充点云序列，以确保其可被指定的区块大小切割

<img src="https://img.saraba1st.com/forum/202312/19/034636t4bieqpq8oqqkejq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-034309__02.jpg</strong> (190.45 KB, 下载次数: 0)

下载附件

2023-12-19 03:46 上传

区块交互

(a)标准的区块分组，具有规则的非平移排列
(b)平移膨胀，将点以规则间隔分组，创建一种膨胀效果
(c)平移区块，应用类似于平移窗口方法的平移机制
(d)平移顺序，不同的序列化模式被循环分配给连续的注意力层
(d)混洗顺序，在馈送到注意力层之前，序列化模式的顺序被随机化

<img src="https://img.saraba1st.com/forum/202312/19/034643pok0xbl4tbto2btb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-034316__01.jpg</strong> (108.67 KB, 下载次数: 0)

下载附件

2023-12-19 03:46 上传

总体构架

<img src="https://img.saraba1st.com/forum/202312/19/034648lyuu3yu1kdquqyza.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-034108__01.jpg</strong> (301.77 KB, 下载次数: 0)

下载附件

2023-12-19 03:46 上传

<img src="https://img.saraba1st.com/forum/202312/19/034648obbcwcgjb6j7qbw2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-034130__01.jpg</strong> (272.81 KB, 下载次数: 0)

下载附件

2023-12-19 03:46 上传

相关测试结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1083#       发表于 2023-12-19 04:54

Marathon

一场穿越长上下文范围的大型语言模型竞赛

hugface数据集下载:https://huggingface.co/datasets/Lemoncoke/Marathon

在线评估网站:https://openbenchmark.online/marathon

尽管目前有许多用于评估大型语言模型的长文本理解和推理能力的基准，但随着这些模型中上下文窗口的扩展，现有的长文本基准已不足以评估大型语言模型的长文本理解和推理能力

在本文中，开发了一个全新的长文本评估基准，名为Marathon，受到MMLU等基准的启发，采用多项选择题的形式，快速、准确、客观地评估大型语言模型的长文本理解能力

在基准上评估了几种最新和最流行的大型语言模型，以及三种最近有效的长文本优化方法，这展示了这些大型语言模型的长文本推理和理解能力，并验证了这些优化方法的有效性

<img src="https://img.saraba1st.com/forum/202312/19/045411mcnv190b1nvntr99.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-045009__01.jpg</strong> (469 KB, 下载次数: 0)

下载附件

2023-12-19 04:54 上传

基准测试中的测试用例的其中一些示例，出于文章显示需求，上下文已被截断

<img src="https://img.saraba1st.com/forum/202312/19/045417gfsgmwzgzzgsd56w.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-045017__01.jpg</strong> (106.04 KB, 下载次数: 0)

下载附件

2023-12-19 04:54 上传

Marathon的统计信息

<img src="https://img.saraba1st.com/forum/202312/19/045423p8nyplz8tqtnslpb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-045025__01.jpg</strong> (183.3 KB, 下载次数: 0)

下载附件

2023-12-19 04:54 上传

Marathon中的上下文长度的分布

<img src="https://img.saraba1st.com/forum/202312/19/045428dougn2aajhqzsy6q.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-045046__01.jpg</strong> (605.83 KB, 下载次数: 0)

下载附件

2023-12-19 04:54 上传

模型在Marathon基准测试中的评估结果:C&amp;R代表理解和推理任务；MIR代表多信息检索任务；TR代表时间线重排序任务；Com.代表计算任务；PR代表段落检索任务；SDQA代表短依赖问答任务；Avg.表示所有任务的平均准确率

<img src="https://img.saraba1st.com/forum/202312/19/045435s3v4ks3433i8khfk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-045053__01.jpg</strong> (221.01 KB, 下载次数: 0)

下载附件

2023-12-19 04:54 上传

大型语言模型在Marathon指令跟随基准上的评估结果

<img src="https://img.saraba1st.com/forum/202312/19/045441kr47zqgjpha3oohq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-045101__01.jpg</strong> (172.18 KB, 下载次数: 0)

下载附件

2023-12-19 04:54 上传

<img src="https://img.saraba1st.com/forum/202312/19/045441ceoio5iftmddrh0x.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-045109__01.jpg</strong> (154.07 KB, 下载次数: 0)

下载附件

2023-12-19 04:54 上传

<img src="https://img.saraba1st.com/forum/202312/19/045441ftq7tztiyyi2k6gq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-045115__01.jpg</strong> (184.34 KB, 下载次数: 0)

下载附件

2023-12-19 04:54 上传

具体表现

<img src="https://img.saraba1st.com/forum/202312/19/045448rcvcgfggxgkjnjcz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-045120__01.jpg</strong> (115.35 KB, 下载次数: 0)

下载附件

2023-12-19 04:54 上传

提示的示例，出于文章显示需求，上下文已被截断

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1084#       发表于 2023-12-19 20:57

G-LLaVA

多模态大型语言模型解决几何问题(Geometric Problem)

项目主页:https://github.com/pipilurj/G-LLaVA

大型语言模型(LLM)展现出了卓越的人类级别的推理和生成能力，这鼓励了对它们在数学问题求解中的应用进行广泛的研究，然而，目前的工作主要着眼于基于文本的数学问题(text-based mathematical problems)上，对涉及几何信息(geometric information)的问题的研究还相对有限

为了弥补这一空白，通过理解图像输入，使LLM能够解决几何问题，首先分析了当前多模态大型语言模型(MLLM)在这个领域的局限性:它们难以准确地理解基本的几何元素(basic geometric elements)及其关系

为了克服这些挑战，通过利用几何问题的独特特性(如独特的几何逻辑形式和几何可扩展性)以及文本LLM的能力，基于现有数据构建了一个丰富的多模态几何数据集，增强的数据集Geo170K包含了超过170K个几何图像-字幕说明(170K geometric image-caption)和问题-答案对(question-answer pairs)

利用构建的Geo170K数据集，开发了G-LLaVA，在MathVista基准测试中，以仅有7B参数的情况下展现出了出色的几何问题解决能力，同时成绩明显优于GPT-4V

<img src="https://img.saraba1st.com/forum/202312/19/205301h8t1ke9kt691d938.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-204619__01.jpg</strong> (515.23 KB, 下载次数: 0)

下载附件

2023-12-19 20:53 上传

SOTA MLLMs在几何图形方面存在严重的幻觉问题，这严重影响了它们在解决几何问题方面的能力，另一方面，G-LLaVA在与策划构造的数据集进行对齐后，其推理几何图形的能力得到了显著提升

<img src="https://img.saraba1st.com/forum/202312/19/205306zj1pu1j4jhh4rbbx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-204637__01.jpg</strong> (444.22 KB, 下载次数: 0)

下载附件

2023-12-19 20:53 上传

通过利用几何问题的特性生成多模态几何数据的框架

<img src="https://img.saraba1st.com/forum/202312/19/205313nrqdrs17dcdljm77.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-204644__01.jpg</strong> (177.87 KB, 下载次数: 0)

下载附件

2023-12-19 20:53 上传

通过逆向信息恢复(inverse information recovery)实现了完整几何图形描述的生成，该描述是基于文本问答对生成的，上半部分展示了用于指导纯文本ChatGPT的问答对，而下半部分(蓝色)展示了ChatGPT生成的回答

<img src="https://img.saraba1st.com/forum/202312/19/205319wvfvnh7334hfjn7h.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-204707__01.jpg</strong> (277.45 KB, 下载次数: 0)

下载附件

2023-12-19 20:53 上传

几何图像描述和对比问答对(contrastive QA pairs)用于理解基本元素，生成过程分为两个阶段:
1.将人工标注的逻辑形式翻译为详细的信息项和图表描述的总结
2.根据提供的信息和总结生成对比问答对，蓝色部分显示ChatGPT生成的回答

<img src="https://img.saraba1st.com/forum/202312/19/205401wky31ygm6d9itugo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-204713__01__01.jpg</strong> (91.98 KB, 下载次数: 0)

下载附件

2023-12-19 20:54 上传

原始样本

<img src="https://img.saraba1st.com/forum/202312/19/205407gq95wqqg9gpvcnwe.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-204713__01__02.jpg</strong> (91.67 KB, 下载次数: 0)

下载附件

2023-12-19 20:54 上传

通过值拓展(value scaling)生成的合成样本

<img src="https://img.saraba1st.com/forum/202312/19/205422h5tz2ivv18iw63ep.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-204724__01.jpg</strong> (285.13 KB, 下载次数: 0)

下载附件

2023-12-19 20:54 上传

通过将值替换为未知变量并求解方程的合成示例

<img src="https://img.saraba1st.com/forum/202312/19/205443fuhaevlppercvxzx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-204724__02.jpg</strong> (89.85 KB, 下载次数: 0)

下载附件

2023-12-19 20:54 上传

通过将条件重新表述为未知的合成示例

<img src="https://img.saraba1st.com/forum/202312/19/205448fz8ogqrcx3p88680.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-204724__03.jpg</strong> (77.28 KB, 下载次数: 0)

下载附件

2023-12-19 20:54 上传

通过句子解析的合成示例

<img src="https://img.saraba1st.com/forum/202312/19/205455fznxngoi1daviwq6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-204735__01.jpg</strong> (385.68 KB, 下载次数: 0)

下载附件

2023-12-19 20:54 上传

在MathVista基准测试的迷你测试集上对比模型在几何问题解决(GPS/geometry problem solving)方面的性能，对于输入，Q代表问题，I代表图像，Ic代表由Bard生成的图像字幕说明，而It代表图像中检测到的OCR文本，基线结果来自Lu et al. (2023)，人类表现和超越人类表现的结果以灰色突出显示，本文结果以蓝色突出显示

<img src="https://img.saraba1st.com/forum/202312/19/205620sueh4fcr4x3ifgch.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-204746__01__01.jpg</strong> (22.93 KB, 下载次数: 0)

下载附件

2023-12-19 20:56 上传

GeoQA和GeoQA+的数据拆分

<img src="https://img.saraba1st.com/forum/202312/19/205644x5b75kpk755447oo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-204746__01__02.jpg</strong> (64.48 KB, 下载次数: 0)

下载附件

2023-12-19 20:56 上传

在GeoQA上与传统方法的模型性能进行对比

<img src="https://img.saraba1st.com/forum/202312/19/205701e2pnitppipihbkcx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-204746__02.jpg</strong> (25.68 KB, 下载次数: 0)

下载附件

2023-12-19 20:57 上传

GeoQA上的不同难度问题

<img src="https://img.saraba1st.com/forum/202312/19/205714peqrb7e29orc2022.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-204746__03.jpg</strong> (33.18 KB, 下载次数: 0)

下载附件

2023-12-19 20:57 上传

GeoQA上不同类型的问题的表现

<img src="https://img.saraba1st.com/forum/202312/19/205719i5ka3ryqour3rvqw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-204746__04.jpg</strong> (38.65 KB, 下载次数: 0)

下载附件

2023-12-19 20:57 上传

预训练阶段对齐的有效性，报告了Top-1准确率

<img src="https://img.saraba1st.com/forum/202312/19/205725wqqnq5fgypqu55wk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-204802__01.jpg</strong> (445.99 KB, 下载次数: 0)

下载附件

2023-12-19 20:57 上传

分别使用GPT-4-V和G-LLaVA演示解决几何问题

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1085#       发表于 2023-12-19 22:05

MagicScroll

通过多层语义感知去噪(Multi-Layered Semantic-Aware Denoising)生成用于视觉故事叙述(Visual Storytelling)的非典型纵横比的图像(Nontypical Aspect-Ratio Image)

项目主页:https://magicscroll.github.io/

code:coming soon

视觉叙事常常使用非典型的纵横比图像，比如卷轴画、连环画和全景图(scroll paintings, comic strips, and panoramas)，以创造富有表现力和吸引力的叙事效果

虽然生成式人工智能取得了巨大的成功，并展示了重塑创意产业的潜力，但生成具有任意大小和可控风格、概念以及布局的连贯且引人入胜的内容仍然是一个挑战，这些要素对于视觉叙事至关重要

为了克服以往方法的缺点，包括重复内容、风格不一致和缺乏可控性，本文提出了MagicScroll，一个基于多层的、渐进式扩散的图像生成框架，具有新颖的语义感知去噪过程(semantic-aware denoising process)，该模型可以在对象、场景和背景层面上对生成的图像进行细粒度控制，并结合文本、图像和布局条件控制

还为用于故事叙述的非典型纵横比图像生成建立了首个基准测试，包括绘画、漫画和电影全景等媒介，并设计了定制的评估指标进行系统化评估，通过对比和消融实验，MagicScroll展示了与叙事文本的对齐、改进了视觉连贯性和吸引观众方面的有希望的结果

研究组计划发布代码和基准，希望能够促进人工智能研究人员与视觉故事创作者之间更好的合作

<img src="https://img.saraba1st.com/forum/202312/19/220406sygsyyxpjnww68dg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-220006__01.jpg</strong> (732.47 KB, 下载次数: 0)

下载附件

2023-12-19 22:04 上传

使用MagicScroll生成的示例结果，框架旨在从故事文本中生成连贯、可控和吸引人的非典型纵横比图像，支持对风格、内容和布局进行多层次、精细化的控制，包括预测的掩码、参考图像和风格概念

<img src="https://img.saraba1st.com/forum/202312/19/220411vy6vyy5mrg8fjhyp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-220025__01.jpg</strong> (460.95 KB, 下载次数: 0)

下载附件

2023-12-19 22:04 上传

方法的工作流程，MagicScroll主要包括基于GPT的布局预测、语义感知的去噪以及基于文本和图像的风格控制

布局预测模块从故事文本中提取场景和物体的边界框，风格控制模块通过对文本提示和参考图像进行编码来确定风格化属性(stylistic attributes)，语义感知的去噪模块包括潜在混合(latent blending)和平滑(smoothing)处理，生成可控、连贯、吸引人的非典型纵横比图像

<img src="https://img.saraba1st.com/forum/202312/19/220417ogq4xdcbxggoggd6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-220038__01.jpg</strong> (80.94 KB, 下载次数: 0)

下载附件

2023-12-19 22:04 上传

端到端评估结果，表格提供了绘画数据集上内容丰富度和保真度的对比统计数据，CSGT代表与基准答案相比的CLIP相似度

<img src="https://img.saraba1st.com/forum/202312/19/220421qvz5iz9q7ct8s5ki.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-220046__01.jpg</strong> (45.27 KB, 下载次数: 0)

下载附件

2023-12-19 22:04 上传

与GLIGEN的对比，GLIGEN和本文方法都支持布局控制，本文方法生成的图像具有更好的连贯性和更高的文本图像相似度

<img src="https://img.saraba1st.com/forum/202312/19/220517h2so9ls9112v1z19.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-220456.jpg</strong> (333.33 KB, 下载次数: 0)

下载附件

2023-12-19 22:05 上传

使用本文方法与其他基线方法进行了定性对比，结果表明了MagicScroll的高度灵活性和核心优势

(a)特定历史背景下的风格模仿
(b)语义布局规划和控制
(c)内容丰富性和多样性

在不同的情景中，本文框架可以实现更有效和吸引人的视觉叙事效果

<img src="https://img.saraba1st.com/forum/202312/19/220523kqon1nvtaq17yfax.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-220124__01.jpg</strong> (440.4 KB, 下载次数: 0)

下载附件

2023-12-19 22:05 上传

消融实验的示例结果，红色框表示出现了伪影(artifacts)，在这些模块中，(b)基于文本的风格控制和(c)基于图像的风格控制主要影响整体风格和颜色，(d)潜在平滑可以提高视觉连贯性，(e)物体掩码和(f)场景掩码不仅影响图像布局，还显著影响前景和中景之间的一致性

<img src="https://img.saraba1st.com/forum/202312/19/220531fkxxlmijmm5k5ffe.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-220128__01.jpg</strong> (116.32 KB, 下载次数: 0)

下载附件

2023-12-19 22:05 上传

消融实验结果，表格列出了在绘画数据集上进行的消融实验的统计数据，CLIP:全局CLIP分数，TBSC:基于文本的风格控制，IBSC:基于图像的风格控制，SM:场景掩码，OM:物体掩码，LS:潜在平滑

<img src="https://img.saraba1st.com/forum/202312/19/220538elwvzj6wujl3ciki.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-220144__01.jpg</strong> (669.88 KB, 下载次数: 0)

下载附件

2023-12-19 22:05 上传

MagicScroll生成的更多示例结果，通过在所有前景、中景和背景层面上提供对风格、概念和布局的控制，本文框架可以满足各种场景中关于视觉叙事内容生成的需求

<img src="https://img.saraba1st.com/forum/202312/19/220543p667qq4qr663o31l.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231219-220149__01.jpg</strong> (78.52 KB, 下载次数: 0)

下载附件

2023-12-19 22:05 上传

用户研究结果，在文本图像一致性、连贯性和故事叙述吸引力方面对比了不同模型生成的图像，结果显示，本文框架在这三个方面都优于其他替代的方法

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1086#       发表于 2023-12-20 00:40

M3DBench

通过多模态3D提示(Multi-modal 3D Prompts)指导大型模型

github项目主页:https://github.com/OpenM3D/M3DBench/

最近，3D理解能力在促进自主代理者(autonomous agents)进行进一步决策方面变得流行起来，然而，现有的3D数据集和方法往往局限于特定任务，另一方面，大型语言模型(LLMs)和多模态语言模型(MLLMs)在通用语言和图像任务上取得了非凡的性能表现，因此，将MLM的潜力解锁到更广泛的3D任务是很有前途的目标，然而，由于缺乏大规模的3D指令跟随数据集，目前的MLM研究在3D任务上的关注较少

在这项工作中，介绍了一个全面的3D指令跟随数据集，名为M3DBench，具有以下特点:
1.支持文本、图像、3D对象和其他视觉提示交错在一起的通用多模态指令
2.统一了区域和场景级别的多样化3D任务，涵盖了真实世界3D环境中的各种基本能力
3.它是一个具有超过320k指令-响应对的大规模3D指令跟随数据集

此外，还建立了一个新的基准测试，用于评估大型模型在理解多模态3D提示方面的性能，广泛的实验证明了数据集和基线的有效性，同时支持常见的以3D为中心的任务，这可以激发未来的研究进展

<img src="https://img.saraba1st.com/forum/202312/20/003944zh9gez6nr8h2ug2q.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-003621__01.jpg</strong> (525.73 KB, 下载次数: 0)

下载附件

2023-12-20 00:39 上传

M3DBench示例，涵盖各种以3D为中心的任务，该数据集支持将文本与视觉提示交错在一起的多模态指令，并涵盖了现实世界3D环境中的各种基础能力，如视觉感知、场景理解、空间推理、导航和规划

<img src="https://img.saraba1st.com/forum/202312/20/003951uqdhh088mp0a0ajj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-003637__01.jpg</strong> (150.26 KB, 下载次数: 0)

下载附件

2023-12-20 00:39 上传

将M3DBench与其他3D VL数据集以及3D指令数据集进行了对比，M3DBench具有以下特点:
1.为3D场景量身定制的综合指令跟随数据集
2.支持交错文本、坐标、图像、3D对象的多模态指令
3.涵盖了多样化的以3D视觉为中心的任务，包括现实世界3D环境中的各种基础能力，如视觉感知、场景理解、空间推理、导航和规划

<img src="https://img.saraba1st.com/forum/202312/20/003956jfk77k44zxtm9rz7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-003649__01.jpg</strong> (237.66 KB, 下载次数: 0)

下载附件

2023-12-20 00:39 上传

M3DBench的统计数据

(a)基于第一个单词的指令分布，图中的内圆表示第一个单词出现的频率，而外圆显示了对应于该第一个单词的指令中动词和名词的出现频率
(b)回答的词云
(c)指令长度的分布
(d)回答长度的分布

<img src="https://img.saraba1st.com/forum/202312/20/004001epillpncl2kpzlvi.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-003657__01.jpg</strong> (263.1 KB, 下载次数: 0)

下载附件

2023-12-20 00:40 上传

基线模型的概览图，使用场景感知器从3D视觉输入中提取场景Token，多模态指令通过各自的编码器转换为相应的指令Token，然后将场景Token和多模态指令Token连接起来，输入到一个冻结的LLM中，随后生成相应的回复。在训练过程中，只更新投影器(projectors)

<img src="https://img.saraba1st.com/forum/202312/20/004005rochcozkoobm26r6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-003711__01.jpg</strong> (541.44 KB, 下载次数: 0)

下载附件

2023-12-20 00:40 上传

多任务的基准测试:密集字幕说明(DC/Dense Caption)，视觉问答(VQA/Visual Question Answering)，具身问答(EQA/Embodied Question Answering)，多区域推理(MR/Multi-region Reasoning)和具身规划(EP/Embodied Planning)，展示了基线方法在评估数据集上的性能，↑表示数值越大越好

<img src="https://img.saraba1st.com/forum/202312/20/004010bm906a5e02951t15.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-003717__01.jpg</strong> (70.05 KB, 下载次数: 0)

下载附件

2023-12-20 00:40 上传

基准测试的详细信息，在实践中，随机选择了39个场景，并为每个场景生成了由GPT-4生成的详细描述，然后评估了不同变体所达到的相对得分，变体模型生成的响应和GPT-4的描述被反馈到GPT-4中进行对比分析和评分，同时提供每个变体答案的相关解释，实验表明，基于Vicuna-7B-V1.5的模型表现出了优越的性能

<img src="https://img.saraba1st.com/forum/202312/20/004015dx3kswzbdkwxwknk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-003746__01.jpg</strong> (392.69 KB, 下载次数: 0)

下载附件

2023-12-20 00:40 上传

定性结果，在不同的3D环境中提供了各种以3D中心的任务可视化结果，橙色突出显示了错误的答案

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1087#       发表于 2023-12-20 02:23

SCEdit

通过跳过连接编辑进行高效且可控的图像扩散生成

项目主页:https://scedit.github.io/

code:coming soon

在最近的研究中，图像扩散模型被广泛用于各种任务，比如文本到图像生成和可控图像合成，最近的研究引入了微调方法，对原始模型进行微小调整(subtle adjustments)，在基础生成扩散模型的特定改进中取得了有希望的结果

相比修改扩散模型的主要骨干，本文深入研究了U-Net中跳跃连接(skip connection)的作用，并揭示了在编码器和解码器中跨越长距离对信息进行层次特征聚合，这对图像生成的内容和质量产生了重大影响

基于这一观察，本文提出了一种高效的生成微调框架(efficient generative tuning framework)，称为SCEdit，通过使用一个轻量级微调模块SC-Tuner来集成和编辑跳跃连接，此外，所提出的框架通过使用可控的SC-Tuner注入不同条件输入实现了可控图像合成的直接拓展，达成了简单又统一的多条件输入的网络设计

SCEdit通过使用轻量级的微调器极大的减少了训练参数、显存使用和计算开销，只将反向传播传递给解码器块，在文本到图像生成和可控图像合成任务上进行的大量实验表明，本文方法在效率和性能方面达成了优秀的成绩

<img src="https://img.saraba1st.com/forum/202312/20/022225cg5q8sna3psovp2v.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-021313__01.jpg</strong> (738.29 KB, 下载次数: 0)

下载附件

2023-12-20 02:22 上传

由SCEdit生成的图片，SCEdit仅使用少量可训练参数和低显存占用，就能够高效地在特定数据集上进行微调(左上)，并支持使用少样本进行迁移学习(右上)，此外，它采用各种条件作为输入，可以实现高效的可控生成(中间)，同时独立的条件学习模型能够轻松组合，提供了无限的组合可能性(下方)

<img src="https://img.saraba1st.com/forum/202312/20/022230btvikg6kcftyyfcv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-021322__01.jpg</strong> (112.79 KB, 下载次数: 0)

下载附件

2023-12-20 02:22 上传

对于文本到图像生成(圆标)和可控图像合成(五角标)任务，进行了性能和效率对比，标记区域反映了参数的相对数量

<img src="https://img.saraba1st.com/forum/202312/20/022235ylkkyzk9muttojdx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-021335__01.jpg</strong> (268.58 KB, 下载次数: 0)

下载附件

2023-12-20 02:22 上传

预训练的U-Net的输出分布(左)和特征图(右)，从不同层删除跳跃连接明显影响了整个网络的输出

<img src="https://img.saraba1st.com/forum/202312/20/022240ukf0fohuhhfohnzo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-021348__01.jpg</strong> (331.59 KB, 下载次数: 0)

下载附件

2023-12-20 02:22 上传

SCEdit框架的示意图，本文方法通过编辑跳跃连接上的特征来实现高效微调，同时证明这具有丰富的结构信息，利用(a)SC-Tuner来进行文本到图像生成调整，借助(b)CSC-Tuner和(c)级联密集卷积(Cascade Dense Convolution)的帮助，实现可控的图像合成

<img src="https://img.saraba1st.com/forum/202312/20/022246fm6v4vtbwkpzmm4k.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-021404__01.jpg</strong> (394.58 KB, 下载次数: 0)

下载附件

2023-12-20 02:22 上传

使用相同提示对原始SD v1.5、现有调整策略和SCEdit进行定性对比

<img src="https://img.saraba1st.com/forum/202312/20/022251ju74nvv0zbeow0yr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-021414__01.jpg</strong> (126.42 KB, 下载次数: 0)

下载附件

2023-12-20 02:22 上传

使用COCO2017数据集生成文本到图像的FID和效率对比，对于FID分数，遵循SD v1.5的默认设置，在效率方面，从参数效率、显存效率和训练时间效率方面进行了对比，比较了LoRA和本文方法在两种不同参数设置下的性能

<img src="https://img.saraba1st.com/forum/202312/20/022256dq6d6jjj0gqq60os.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-021423__01.jpg</strong> (600.28 KB, 下载次数: 0)

下载附件

2023-12-20 02:22 上传

对各种自定义风格化数据集的少样本迁移学习对比，与LoRA调整相比，SCEdit实现了更精确的风格特征学习并生成了更高质量的图像

<img src="https://img.saraba1st.com/forum/202312/20/022300zis9d9i6t53zwii7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-021433__01.jpg</strong> (149.07 KB, 下载次数: 0)

下载附件

2023-12-20 02:23 上传

使用LAION数据集对可控图像合成的FID和效率进行对比，“k”表示条件模型的卷积核大小，较大的大小在FID分数上表现更好，尽管参数会适度增加

<img src="https://img.saraba1st.com/forum/202312/20/022305h1uh4h0fl8jn334h.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-021445__01.jpg</strong> (665.6 KB, 下载次数: 0)

下载附件

2023-12-20 02:23 上传

各种条件下的可控图像合成，奇数行表示输入条件，而偶数行对应于生成的结果，SCEdit能够根据输入条件生成精确的高质量图像

<img src="https://img.saraba1st.com/forum/202312/20/022311b631lm5382phz2hf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-021455__01.jpg</strong> (668.61 KB, 下载次数: 0)

下载附件

2023-12-20 02:23 上传

与基于精细边缘(canny edge)和语义分割条件的SOTA可控图像合成方法进行定性对比

<img src="https://img.saraba1st.com/forum/202312/20/022319jff5bf6oig6vfyky.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-021504__01.jpg</strong> (554.49 KB, 下载次数: 0)

下载附件

2023-12-20 02:23 上传

可组合的生成，多种条件的组合提供了更多的组合可能性

<img src="https://img.saraba1st.com/forum/202312/20/022323r1d1g2cgg160k1gc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-021509__01.jpg</strong> (88.77 KB, 下载次数: 0)

下载附件

2023-12-20 02:23 上传

控制泛化

学习的边缘条件模型能够完成草图到图像的任务，重绘条件模型可以控制重绘生成

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1088#       发表于 2023-12-20 02:52

VidToMe

用于零样本视频编辑的视频Token合并(Video Token Merging)

项目主页:https://vidtome-diffusion.github.io/

github项目仓库:https://github.com/lixirui142/VidToMe

扩散模型在生成高质量图像方面取得了显著进展，但由于时间运动的复杂性，它们在视频生成方面的应用仍然具有挑战性，零样本视频编辑通过利用预训练的图像扩散模型将源视频转换为新视频，提供了其中一种解决方案，然而，现有方法在保持严格的时间一致性和高效的显存消耗方面存在困难

在这项工作中，提出了一种新方法，通过合并跨帧的自注意力Token(merging self-attention tokens across frames)来增强生成视频的时间一致性，通过对视频帧之间的时间冗余Token进行对齐和压缩，本文方法改善了时间连贯性的同时减少了自注意力计算中的显存消耗

该合并策略根据帧之间的时间对应关系匹配和对齐Token，促进了生成视频帧的自然时间一致性，为了管理视频处理流程中的复杂性，通过将视频分成块(divide videos into chunks)，并开发了块内(inter-chunk)局部Token合并和块内(inter-chunk)全局Token合并，确保了短期的视频连续性和长期内容的一致性

本文的视频编辑方法将图像编辑方面的进展无缝地扩展到视频编辑领域，相对于SOTA方法，在时间一致性方面呈现出了更好的结果
————

<img src="https://img.saraba1st.com/forum/202312/20/025139jpnr5ip26b5prn5s.png" referrerpolicy="no-referrer">

<strong>pipeline.png</strong> (616.91 KB, 下载次数: 0)

下载附件

2023-12-20 02:51 上传

给定一个输入的源视频和文本提示，VidToMe系统使用预训练的文本到图像扩散模型遵循提示生成一个编辑视频，其关键思想是在自注意模块中跨越多个帧合并相似的Token，以实现生成视频的时间一致性

上方:VidToMe工作流程，从DDIM反转噪声潜在开始，使用扩散模型结合现有的控制方法对视频帧进行去噪处理，在自注意力块之前应用视频Token合并

下方:视频Token合并，给定自注意输入Token，首先在视频块中合并Token(局部Token合并)，然后，将全局Token集被混合起来，实现块间Token共享(全局Token合并)，在合并Token集上进行联合自注意力后，通过反转合并过程将输出Token恢复为其原始大小
————

<img src="https://img.saraba1st.com/forum/202312/20/025145frllrpf333lb3lcv.png" referrerpolicy="no-referrer">

<strong>efficiency.png</strong> (35.79 KB, 下载次数: 0)

下载附件

2023-12-20 02:51 上传

合并多帧Token减少了视频帧中的时间冗余，从而提高了显存和计算效率，因此，与基线方法相比，VidToMe在快速生成视频的同时消耗更少的显存
————
视频编辑结果

<img src="https://img.saraba1st.com/forum/202312/20/025200d1ggb5p6xpljbuub.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-024937.jpg</strong> (390.93 KB, 下载次数: 0)

下载附件

2023-12-20 02:52 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1089#       发表于 2023-12-20 05:11

adaptive-diffusion

您的学生比预期的更好:文本条件扩散模型的自适应师生协作(Adaptive Teacher-Student Collaboration)

github项目主页:https://github.com/yandex-research/adaptive-diffusion

最近，知识蒸馏方法(Knowledge distillation methods)已经展现出在加速大型扩散模型合成速度方面的潜力，只需要少量的推理步骤即可加快合成速度，虽然最近提出了几种强大的蒸馏方法，但学生样本的整体质量与教师样本相比通常较低，这妨碍了它们在实际中应用

在这项工作中，调查了教师文本到图像扩散模型及其蒸馏的学生版本产生的样本的相对质量，作为主要的实证发现，尽管学生的特性是“近似(approximate)”的，但有相当一部分学生样本在保真度上优于教师样本，基于这一发现，提出了学生和教师扩散模型之间的自适应协作，以实现有效的文本到图像合成

具体而言，蒸馏模型生成初始样本，然后一个预示机(oracle)决定是否需要通过慢速教师模型进行进一步改进

广泛的实验表明，这种设计的工作流程在人类偏好方面，在各种推理预算上超过了SOTA文本到图像替代方案，此外，所提出的方法可以自然地应用于流行的应用，如文本引导的图像编辑和可控生成

<img src="https://img.saraba1st.com/forum/202312/20/050630j4eimiex4xretqel.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-050248__01.jpg</strong> (447.79 KB, 下载次数: 0)

下载附件

2023-12-20 05:06 上传

左:所提案方法的概览图
右:SDv1.5和SDXL与其几个步骤的精炼版本的并排对比

对于相同的文本提示和初始噪声，蒸馏后的模型在大量样本中超过了原始模型

<img src="https://img.saraba1st.com/forum/202312/20/050636tewgbggi6zrqr6wg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-050300__01.jpg</strong> (576.35 KB, 下载次数: 0)

下载附件

2023-12-20 05:06 上传

学生的表现优于教师(SD1.5)

左:文本条件图像合成
右:文本引导图像编辑(SDEdit)

 每对内的图像是使用相同的初始噪声样本生成的

<img src="https://img.saraba1st.com/forum/202312/20/050645m52ua4v29x12ifza.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-050321__01.jpg</strong> (394.69 KB, 下载次数: 0)

下载附件

2023-12-20 05:06 上传

(a)相似(左)和不相似(右)的师生样本的视觉示例
(b)学生和教师样本之间的相似度与样本质量差异之间的关系，差异较大的样本往往具有不同的质量
(c)学生和教师样本之间不同距离范围内的人类投票分布，学生胜利大多发生在学生与教师有分歧的情况下

<img src="https://img.saraba1st.com/forum/202312/20/050650g38zu5s839o2ggw7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-050330__01.jpg</strong> (115.87 KB, 下载次数: 0)

下载附件

2023-12-20 05:06 上传

图像复杂度的影响

(a)学生和教师样本越相似，图像越简单，反之亦然
(b)学生和教师在复杂的教师样本上图像质量有很大的差异，值得注意的是，学生在这些样本上通常表现优于教师

<img src="https://img.saraba1st.com/forum/202312/20/050654mrrkxrz7j8xk04px.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-050557.jpg</strong> (86.19 KB, 下载次数: 0)

下载附件

2023-12-20 05:06 上传

文本提示的影响

(a)较短的提示通常会导致学生和教师样本更相似
(b)当学生在很大程度上更依赖于文本提示时，学生和教师往往会生成更相似的图像

<img src="https://img.saraba1st.com/forum/202312/20/050721rmsqxifnfqnzkfbm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-050704.jpg</strong> (78 KB, 下载次数: 0)

下载附件

2023-12-20 05:07 上传

教师轨迹弯曲的影响

(a)学生样本在轨迹弯曲较小的情况下与教师样本相似
(b)更直的轨迹通常对应于更简单的教师图像

<img src="https://img.saraba1st.com/forum/202312/20/050728pm4mhbqi1s4cqa4c.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-050710.jpg</strong> (62.67 KB, 下载次数: 0)

下载附件

2023-12-20 05:07 上传

全参考(full-reference) VS 不参考(no-reference)决策，可以找到ImageReward分数的第k个百分位，提供与人类投票的相关性，类似于全参考对比，但不观察教师的样本

<img src="https://img.saraba1st.com/forum/202312/20/050753sji4j4699v957c6z.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-050400__01.jpg</strong> (774.83 KB, 下载次数: 0)

下载附件

2023-12-20 05:07 上传

本文的自适应细化方法与SD1.5教师模型的定性对比

<img src="https://img.saraba1st.com/forum/202312/20/050830bawucr91rh9ru4sh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-050408__01.jpg</strong> (300.31 KB, 下载次数: 0)

下载附件

2023-12-20 05:08 上传

用户偏好研究(SD1.5)

(a)将本文方法与最佳的教师配置进行对比
(b)将其与使用DPM-Solver的教师模型在相同步数下进行对比
(c)将其与没有自适应步骤的改进策略在相同步数下进行对比

上方行:LAION-美学文本提示
下方行:COCO2014文本提示

对于本文的自适应方法，使用细化策略(R)

<img src="https://img.saraba1st.com/forum/202312/20/050929y9kxaxok3kktvlql.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-050425__01.jpg</strong> (114.08 KB, 下载次数: 0)

下载附件

2023-12-20 05:09 上传

自动评估(SD1.5)，对来自COCO2014的5K个文本提示进行不同采样步骤的FID、CLIP和ImageReward分数对比，所提出的协作方法优于所有基线方法，具有重生成策略(G)的自适应流程展现了更高的文本对齐度(CLIP分数)，而细化策略(R)提高了图像保真度(FID)

<img src="https://img.saraba1st.com/forum/202312/20/050934xus9le9b9oths22b.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-050430__01.jpg</strong> (60.64 KB, 下载次数: 0)

下载附件

2023-12-20 05:09 上传

用户偏好研究(SDXL)

左图:将自适应方法与CD-SDXL以及表现最佳的教师设置进行对比
右图:将自适应方法与相同采样步骤的ADD-XL以及ADD-XL进行对比

<img src="https://img.saraba1st.com/forum/202312/20/050940xr6p2lvv6v6rq622.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-050425__02.jpg</strong> (81.55 KB, 下载次数: 0)

下载附件

2023-12-20 05:09 上传

用户对样本估计器的不同准确率水平的偏好，当前状态表示使用ImageReward估计器的结果，其他结果展示了如果未来估计器性能提高而可能获得的潜在收益

<img src="https://img.saraba1st.com/forum/202312/20/051013itlmuvz1vrtlime0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-050442__01.jpg</strong> (108.12 KB, 下载次数: 0)

下载附件

2023-12-20 05:10 上传

通过不同方法收集的多样性人类分数

<img src="https://img.saraba1st.com/forum/202312/20/051017neuoeomcc2cd8uno.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-050442__02.jpg</strong> (75.77 KB, 下载次数: 0)

下载附件

2023-12-20 05:10 上传

CD-SD1.5和SD1.5样本的图像复杂度，使用ICNet进行采样

左图:箱线图表示两个模型的复杂度分位数
右图:独立复杂度值的分布，每个点对应于为相同提示和初始噪声生成的一对样本

蒸馏模型仅略微简化了教师分布

<img src="https://img.saraba1st.com/forum/202312/20/051107ki4954mn5m2ibnmi.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-050447__01.jpg</strong> (122.37 KB, 下载次数: 0)

下载附件

2023-12-20 05:11 上传

使用不同方法的SDEdit在参考留存DINOv2和编辑质量(ImageReward)方面的对比，强度为0.6

<img src="https://img.saraba1st.com/forum/202312/20/051113iknfri1k944in45s.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-050503__01.jpg</strong> (772.51 KB, 下载次数: 0)

下载附件

2023-12-20 05:11 上传

使用本文方法和性能最佳的教师(SD1.5)配置生成的视觉示例
顶部:使用SDEdit进行文本引导的图像编辑
底部:使用ControlNet进行精确边缘和语义分割掩码的可控图像生成

<img src="https://img.saraba1st.com/forum/202312/20/051118r2ard20g2a5rri0d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-050506__01.jpg</strong> (53.13 KB, 下载次数: 0)

下载附件

2023-12-20 05:11 上传

SDEdit在参考留存(DINOv2)和编辑质量(IR)方面针对不同强度值的性能

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1090#       发表于 2023-12-20 05:27

Catwalk

多数据集的统一语言模型评估框架

github项目主页:https://github.com/allenai/catwalk

大型语言模型的成功已经改变了自然语言处理(NLP)中的评估范式，社区的兴趣转向了在许多任务、领域和数据集上对比NLP模型，这通常是在极大的规模下进行的，同时这这带来了新的工程挑战:构建数据集和模型的工作被分散进行，它们的格式和接口并不兼容，因此，要进行公平和可控的大规模评估往往需要进行大量的重新实现工作

Catwalk旨在解决这些问题，Catwalk为广泛的现有NLP数据集和模型提供了统一的交互接口，包括经典的监督训练和微调，以及更现代的诸如上下文学习的范式，它精心设计的抽象层允许轻松扩展到其他许多领域，Catwalk极大的降低了进行大规模可控实验的门槛，例如，可以使用一个命令对超过86个数据集上的64个模型进行了微调和评估，而无需编写任何代码

Catwalk由艾伦人工智能研究所(AI2)的AllenNLP团队维护，是一个持续的开源项目

<img src="https://img.saraba1st.com/forum/202312/20/052653aukiy8n5ik8cf4yc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-052508.jpg</strong> (334.96 KB, 下载次数: 0)

下载附件

2023-12-20 05:26 上传

Catwalk的工作流程

<img src="https://img.saraba1st.com/forum/202312/20/052658mao9rs33oagyh3v3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-052616.jpg</strong> (56.89 KB, 下载次数: 0)

下载附件

2023-12-20 05:26 上传

Catwalk中的模型样式和支持的功能特性

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1091#       发表于 2023-12-20 06:28

 本帖最后由 Machinery 于 2023-12-20 06:29 编辑 

Silkie

大型视觉语言模型的偏好蒸馏

项目主页:https://vlf-silkie.github.io/

github项目仓库:https://github.com/vlf-silkie/VLFeedback

hugface模型权重下载:https://huggingface.co/MMInstruction/Silkie

这篇论文探讨了针对大型视觉语言模型(LVLMs)的偏好蒸馏，以提高其生成有帮助且可信的视觉上下文回复的能力，首先利用AI标注构建了一个视觉语言反馈(VLFeedback)数据集，具体而言，响应是以来自各种数据集的多模式指令为条件，从​​12个LVLM模型生成的

通过采用GPT-4V来评估了生成的输出的有关帮助性、视觉可信度和道德伦理(regarding helpfulness, visual faithfulness, and ethical considerations)方面，此外，通过直接偏好优化(DPO)方法，将偏好监督压缩到了Qwen-VL-Chat中，由此得到的模型Silkie，在感知和认知能力方面，相对于MME基准，分别取得了6.9%和9.5%的相对改进

Silkie还通过在MMHal-Bench基准上达成了一个新的SOTA得分3.02以证明减少了幻觉，进一步的分析显示，使用VLFeedback数据集的DPO主要提升了LVLM的细粒度感知和复杂认知能力，相比于人工标注的偏好数据集，带来了更全面的改进

<img src="https://img.saraba1st.com/forum/202312/20/062725y88qgq8qzfdfz5x5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-062333__01.jpg</strong> (378.63 KB, 下载次数: 0)

下载附件

2023-12-20 06:27 上传

视觉语言反馈(VLFeedback)数据集的标注框架如图，从各种来源收集指令，并使用来自LVLM池(LVLM pool)的4个模型解码相应的回应，GPT-4V模型评估这些回应的三个方面，并为分数提供评级和理由

<img src="https://img.saraba1st.com/forum/202312/20/062730f20q9avg82nupwar.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-062339__01.jpg</strong> (315.83 KB, 下载次数: 0)

下载附件

2023-12-20 06:27 上传

VLFeedback数据集中多模态指令的描述和统计

<img src="https://img.saraba1st.com/forum/202312/20/062736kuafjrta13tf83f8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-062352__01.jpg</strong> (431.28 KB, 下载次数: 0)

下载附件

2023-12-20 06:27 上传

GPT-4V模型的视觉可信度评估标注指导

<img src="https://img.saraba1st.com/forum/202312/20/062740kdv9bsuba7vs6bea.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-062359__01.jpg</strong> (101.17 KB, 下载次数: 0)

下载附件

2023-12-20 06:27 上传

不同方面的评分分布，帮助性和视觉可信度具有相似的分数分布，大多数解码的响应在没有道德考虑的情况下进行评估

<img src="https://img.saraba1st.com/forum/202312/20/062744nx22285hxte55cm7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-062405__01.jpg</strong> (217.96 KB, 下载次数: 0)

下载附件

2023-12-20 06:27 上传

GPT-4V在三个方面的平均得分和整体表现上显示出明显优势，这促使本文选择GPT-4V作为人类标注者的代行者

<img src="https://img.saraba1st.com/forum/202312/20/062754uzg4jppjdccpg7cg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-062411__01.jpg</strong> (107.53 KB, 下载次数: 0)

下载附件

2023-12-20 06:27 上传

GPT-4V和Qwen-VL-Chat之间的分数分布对比

<img src="https://img.saraba1st.com/forum/202312/20/062759cc47rr0iiznmgmwm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-062417__01.jpg</strong> (194.83 KB, 下载次数: 0)

下载附件

2023-12-20 06:27 上传

多模态基准的性能评估，最佳结果以粗体显示，第二名的结果以下划线显示

<img src="https://img.saraba1st.com/forum/202312/20/062803a0wpd3iuxjd4puxd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-062425__01.jpg</strong> (156.28 KB, 下载次数: 0)

下载附件

2023-12-20 06:28 上传

(左图)对性能改进的MME基准进行了深入分析，VLFeedback数据集在OCR识别和代码推理任务中带来了更明显的收益
(右图)通过对RLHF-V偏好数据和VLFeedback数据集的子集执行DPO来实现相对性能改进，GPT-4V的标注偏好数据集在四个基准测试中带来了更一致的改进

<img src="https://img.saraba1st.com/forum/202312/20/062808sh8uy8fyv3uovhay.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-062432__01.jpg</strong> (418.68 KB, 下载次数: 0)

下载附件

2023-12-20 06:28 上传

MMHal-Bench(左)和MM-Vet(右)的评估样本的案例研究，Silkie能够准确地找到带有红花的木凳子，而不会提供误导性的断言，并且能够正确回答与科学相关的问题

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1092#       发表于 2023-12-20 23:34

 本帖最后由 Machinery 于 2023-12-20 23:35 编辑 

StarVector

从图像生成可扩展的矢量图形代码(Vector Graphics Code)

github项目主页:https://github.com/joanrod/star-vector

可拓展矢量图形(SVG/Scalable Vector Graphics)已经成为现代图像渲染应用中不可或缺的一部分，因为它们在分辨率上具有无限可扩展性、具备广泛的使用范围和可编辑性，其中，SVG在网页开发和图形设计领域特别受欢迎，现有的方法通常使用深度学习对SVG进行建模，常常难以生成复杂的SVG，在局限于简单SVG的同时，还需要大量的处理流程和简化

本文介绍了StarVector，一种多模态SVG生成模型，它有效地将代码生成大型语言模型(CodeLLMs)和视觉模型进行了整合，利用CLIP图像编码器从基于像素的图像中提取视觉表征，然后通过适配器模块(adapter module)将其转换为视觉Token，这些视觉Token被预置(pre-pended)到SVG Token嵌入中，随后这些序列由StarCoder模型进行建模，使用下一个Token预测目标，有效地学习了如何对齐视觉和代码Token，这使得StarVector能够生成准确表示像素图像的无限制SVG

为了评估StarVector的性能，提出了SVG-Bench，一个用于评估SVG方法的全面基准测试，涵盖多个数据集和相关指标，在这个基准中，引入了包括SVG-Stack在内的新数据集(一个大规模的真实世界SVG示例数据集)，并将其用于预训练StarVector，使之作为SVG的大型基础模型

结果表明，与当前方法相比，本文方法在视觉质量和复杂性处理方面取得了显著的改进，这成为了SVG生成技术的显著进步标志之一

<img src="https://img.saraba1st.com/forum/202312/20/233049jts87prr8k6zrt5p.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-232422__01.jpg</strong> (287.47 KB, 下载次数: 0)

下载附件

2023-12-20 23:30 上传

图像到SVG生成任务:给定一个输入图像，生成对应的SVG代码，在左侧，展示了来自SVG-Emoji和SVG-Stack数据集的复杂SVG的测试示例，StarVector对图像进行编码，并以多模态语言建模的方式处理它们，以生成类似输入图像的可执行SVG代码，这里展示了由StarVector模型生成的真实代码和光栅化图像，展现了生成吸引人的SVG设计和使用复杂语法的能力

<img src="https://img.saraba1st.com/forum/202312/20/233056khm43zh14sst14zk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-232433__01.jpg</strong> (246.28 KB, 下载次数: 0)

下载附件

2023-12-20 23:30 上传

StarVector架构:像素空间中的图像使用CLIP编码为一组2D嵌入，Adapter对图像嵌入进行非线性变换，使其与Code-LLM空间对齐获得视觉Token，StarCoder使用图像嵌入作为上下文生成SVG，在训练过程中，通过SVG Token的下一个Token预测来监督该任务，在推理过程中，模型使用输入图像的视觉Token自回归地预测SVG代码

<img src="https://img.saraba1st.com/forum/202312/20/233104k27rlclax3c33rvo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-232448__01.jpg</strong> (186.04 KB, 下载次数: 0)

下载附件

2023-12-20 23:31 上传

SVG-Bench中的数据集，展示了每个分割(split)内的样本数量，还有一个由简化的SVG组成的降低后的测试集，提供了数据集获取的来源，并提供了SVG代码长度的统计信息，考虑了由StarCoder训练的分词器(tokenizer)，最后，展示了数据集中使用的SVG基元(primitives)的类型

<img src="https://img.saraba1st.com/forum/202312/20/233110phz7yiun0qiq770o.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-232448__02.jpg</strong> (175.84 KB, 下载次数: 0)

下载附件

2023-12-20 23:31 上传

基线对比，虽然之前的工作只考虑了3个简单的命令-M(Move)、L(Line)和C(Curve)，但模型原则上可以处理所有类型的复杂SVG命令

<img src="https://img.saraba1st.com/forum/202312/20/233115eolf32z7y2qau8b2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-232504__01.jpg</strong> (64.92 KB, 下载次数: 0)

下载附件

2023-12-20 23:31 上传

简化SVG-Icons和SVG-Fonts的测试结果

<img src="https://img.saraba1st.com/forum/202312/20/233122guz02me13wzkz0ii.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-232504__02.jpg</strong> (62.56 KB, 下载次数: 0)

下载附件

2023-12-20 23:31 上传

SVG-Icons测试集的结果

<img src="https://img.saraba1st.com/forum/202312/20/233150ap8q88cq0j6jjzzu.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-232608__01.jpg</strong> (257.28 KB, 下载次数: 0)

下载附件

2023-12-20 23:31 上传

针对SVGBench中不同方法的图像到SVG转换任务的简化(sim)数据集的结果，粗体代表最佳模型，下划线代表第二名

<img src="https://img.saraba1st.com/forum/202312/20/233155xuggf63nggxunfrg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-232608__02.jpg</strong> (226.21 KB, 下载次数: 0)

下载附件

2023-12-20 23:31 上传

图像到SVG转换任务的完整数据集的结果，指标是在SVG-Bench的完整测试集上计算的，DeepSVG不包括在内，因为它不支持复杂的SVG图像

<img src="https://img.saraba1st.com/forum/202312/20/233202vusxdd7pxy55u7dn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-232623__01.jpg</strong> (143.48 KB, 下载次数: 0)

下载附件

2023-12-20 23:32 上传

SVG-Emoji测试集的结果

<img src="https://img.saraba1st.com/forum/202312/20/233207x83gfuhg8zqyy6bo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-232623__02.jpg</strong> (111.15 KB, 下载次数: 0)

下载附件

2023-12-20 23:32 上传

SVG-Stack测试集的结果

<img src="https://img.saraba1st.com/forum/202312/20/233220lqk3njf8fd3z66i9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-232721__01.jpg</strong> (265.38 KB, 下载次数: 0)

下载附件

2023-12-20 23:32 上传

使用不同的图像编码器进行消融实验，同时保持架构的其余部分相同，CLIP作为骨干的视觉模型在相似的参数设置下表现最好

<img src="https://img.saraba1st.com/forum/202312/20/233225lwwwuesvpvz6czhc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-232721__02.jpg</strong> (228.81 KB, 下载次数: 0)

下载附件

2023-12-20 23:32 上传

SVG数据增强的结果，本实验评估了容易发生过度拟合的较小数据集，“+”表示还包括之前的行

<img src="https://img.saraba1st.com/forum/202312/20/233230jdd9992sg9dvs99d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-232648__01.jpg</strong> (132.95 KB, 下载次数: 0)

下载附件

2023-12-20 23:32 上传

使用不同的视觉编码器在SVG-emoji上进行消融实验

<img src="https://img.saraba1st.com/forum/202312/20/233234wpu5ewp1xxtbsexx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231220-232648__02.jpg</strong> (98.46 KB, 下载次数: 0)

下载附件

2023-12-20 23:32 上传

使用不同的视觉编码器在SVG-Stack上进行消融实验

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1093#       发表于 2023-12-21 00:25

 本帖最后由 Machinery 于 2023-12-21 00:26 编辑 

VistaLLM

万事通，多才多艺(Jack of All Tasks, Master of Many)，设计通用从粗到细(Coarse-to-Fine)的视觉语言模型

项目主页:https://shramanpramanick.github.io/VistaLLM/

<img src="https://img.saraba1st.com/forum/202312/21/002421bpbx7fz6qt7g77r7.png" referrerpolicy="no-referrer">

<strong>radar.png</strong> (82.04 KB, 下载次数: 0)

下载附件

2023-12-21 00:24 上传

————
本文的主要贡献

VistaLLM:推出了VistaLLM，这是一个功能强大的通用视觉系统，它将单个和多个输入图像上的粗粒度和细粒度视觉语言推理以及基础任务集成到一个统一的框架中

新颖的采样算法:为了有效地将分割掩码转换为序列，提出了一种梯度感知适配轮廓采样方案(gradient-aware adaptive contour sampling scheme)，该方案在不同的分割基准测试上相比以前使用的均匀采样(uniform sampling)提高了3-4mIoU分数

CoinIt数据集:为了在多种形式的视觉和语言任务上训练VistaLLM，提出了从粗到细的指令调整数据集，其中包含680万个样本，涵盖四大类任务——单图像粗粒级、单图像区域级、多图像粗粒级和多图像区域级(single-image coarse-level, single-image region-level, multi-image coarse-level, and multi-image region-level)

新任务:提出一项新任务“Attribute-level Co-Segmentation”来解决缺乏公开可用的多图像区域级数据集的问题，该任务旨在识别具有共同属性的输入图像(形状、颜色、大小、 位置)，并对这些对象进行分割，AttCoSeg包含685k训练样本，帮助VistaLLM在多个输入图像上获得了显著的通用推理能力和基准(grounding)能力改进
————
VistaLLM构架

<img src="https://img.saraba1st.com/forum/202312/21/002626kxurvruv0vvwhlt0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-002608.jpg</strong> (117.79 KB, 下载次数: 0)

下载附件

2023-12-21 00:26 上传

提出的VistaLLM的概览图，将单图像和多图像的粗粒度和细粒度的视觉语言任务集成到统一的通用框架中，VistaLLM包含三个关键的设计模块

(i)图像编码器，用于提取全局图像嵌入

(ii)指令指导的图像分词器(tokenizer)，利用任务指令对全局图像嵌入进行细化和压缩，使模型能够过滤当前任务所需的必要视觉信息

(iii)LLM(Vicuna)，基于LLM的解码器，可以联合处理图像和语言特征，并生成所需的输出，VistaLLM使用一种梯度感知的适配采样技术，将分割掩码有效地表示为点序列(point sequence)

除图像编码器外，所有参数在第一阶段进行训练，而只有图像分词器在第二阶段进行微调
————
适配采样

<img src="https://img.saraba1st.com/forum/202312/21/002442f25dcgk1hkdg1hzo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-002242__01.jpg</strong> (284.33 KB, 下载次数: 0)

下载附件

2023-12-21 00:24 上传

均匀采样和适配采样策略的可视化，(左图)采样点的示意图和用于对比的聚合曲线，(右)采样点的示意图和聚合的掩码对比，通过提出一种梯度感知的适配轮廓采样方案，将二值化掩码高效地转换为点序列，从而显著改善了先前用于序列到序列分割任务的简单均匀采样技术
————
相关评估结果

<img src="https://img.saraba1st.com/forum/202312/21/002457kicdio3wc9zdx0dq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-001807__01.jpg</strong> (285.43 KB, 下载次数: 0)

下载附件

2023-12-21 00:24 上传

<img src="https://img.saraba1st.com/forum/202312/21/002457ykgd7996f5579dfk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-001814__01.jpg</strong> (209.87 KB, 下载次数: 0)

下载附件

2023-12-21 00:24 上传

<img src="https://img.saraba1st.com/forum/202312/21/002457ukhh1ddtqd4zd11x.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-001820__01.jpg</strong> (159.91 KB, 下载次数: 0)

下载附件

2023-12-21 00:24 上传

————
示例演示

<img src="https://img.saraba1st.com/forum/202312/21/002520y6okbp6honvdl7z9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-002121.jpg</strong> (751.94 KB, 下载次数: 0)

下载附件

2023-12-21 00:25 上传

<img src="https://img.saraba1st.com/forum/202312/21/002521y3vvc1jpz26cwp36.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-002138.jpg</strong> (615.78 KB, 下载次数: 0)

下载附件

2023-12-21 00:25 上传

<img src="https://img.saraba1st.com/forum/202312/21/002521cjduqf5fni0uf5zj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-002206.jpg</strong> (529.09 KB, 下载次数: 0)

下载附件

2023-12-21 00:25 上传

<img src="https://img.saraba1st.com/forum/202312/21/002521k8el3xxhi6jd6jf0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-002214.jpg</strong> (206.9 KB, 下载次数: 0)

下载附件

2023-12-21 00:25 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1094#       发表于 2023-12-21 01:40

 本帖最后由 Machinery 于 2023-12-21 01:42 编辑 

3D-LFM

3D提升(Lifting)基础模型

项目主页:https://3dlfm.github.io/

github项目仓库:https://github.com/mosamdabhi/3dlfm

将3D结构和摄影机从2D标记点中提升出来是整个计算机视觉的核心基石，传统方法局限于特定的刚性物体，比如透视n点(PnP/Perspective-n-Point)问题中的物体，但深度学习扩展了重建广泛的物体类别(如C3PDO和PAUL)的能力，这些模型具有对弹性噪声、遮挡和透视变形的稳健性

然而，所有这些技术都受限于建立3D训练数据之间对应关系的基本需求，如果仅拥有大量“非对应”3D数据时，这将限制这些应用的实用性，本文方法利用Transformer内部的排列恒等性(permutation equivariance)来处理每个3D数据实例中的点数量变化，抵抗遮挡，并泛化到未见的类别

在2D-3D提升任务基准测试中展示了SOTA性能，由于本文方法可以在如此广泛的结构类别上进行训练，因此将其简称为3D提升基础模型(3D-LFM)——这是首个相关的基础模型
————

<img src="https://img.saraba1st.com/forum/202312/21/014016twoz0bok01qpb6k1.png" referrerpolicy="no-referrer">

<strong>approach.png</strong> (136.25 KB, 下载次数: 0)

下载附件

2023-12-21 01:40 上传

3D-LFM模型的架构图:系统通过TPE对2D关键点进行编码，通过Transformer层对其进行处理，并使用MLP解码为规范的3D形状，使用Procrustean方法将形状与基准答案对齐，确保以效率的计算捕获局部和全局上下文
————
3D-LFM是一种通用的2D-3D提升模型，无需特定类别的知识即可处理不同的对象，它使用Transformer的排列恒等性和几何一致性来处理摄影机旋转，并标准化规范帧中的形状表征

<img src="https://img.saraba1st.com/forum/202312/21/014022nqq00lvc622nssqr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-013920.jpg</strong> (150.71 KB, 下载次数: 0)

下载附件

2023-12-21 01:40 上传

3D-LFM 可扩展到多个类别(在实验中为30多个类别)，通过建议的架构更改可以管理不同的标记配置，图中红色代表基准答案，蓝色代表预测
————
OOD泛化

<img src="https://img.saraba1st.com/forum/202312/21/014030xxefv2tfejls0n2v.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-013938.jpg</strong> (50.15 KB, 下载次数: 0)

下载附件

2023-12-21 01:40 上传

3D-LFM能够识别和重建许多在训练阶段从未遇到过的标记数量的物体配置，模型在训练中从未见过上述对象类别

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1095#       发表于 2023-12-21 05:51

tao-amodal

追踪任何对象的非模态(Tracking Any Object Amodally)

注:非模态感知(Amodal perception)是当只有部分物理结构影响感觉受体时对整个物理结构的感知，例如，即使视线中只有桌子的一部分投射到视网膜上，那些看不到的部分也会被视为完整的体积结构，尽管只有表面暴露在视线中，但它依然具有内部体积和隐藏的背面

项目主页:https://tao-amodal.github.io/

非模态感知是一种基本技能，甚至连婴儿都具备，其重要性延伸到了自动驾驶等应用领域，其中，对于严重遮挡物体的清晰理解至关重要，然而现代的检测和追踪算法经常忽略这一关键能力，可能是因为大多数的数据集主要关注可见物体的标注

为了解决缺乏非模态数据的问题，引入了TAO-Amodal基准测试，其中包含880个不同类别的物体以及成千上万个视频序列，数据集包括了非模态和模态边界框，以用于可见和遮挡物体，包括部分超出画面的物体

为了增强非模态追踪的物体的持久性，通过利用一个轻量级的插件模块，即非模态扩展器(amodal expander)，在数百个带有数据增强的视频序列上进行微调，将标准的模态追踪器转化为非模态追踪器

在TAO-Amodal上的检测和追踪遮挡物体的准确率分别提高了3.3%和1.6%，在人类评估方面，相比于SOTA模态基线，本方法取得了惊人的2倍显著改进
————

<img src="https://img.saraba1st.com/forum/202312/21/055125e9dllz09md12zhhl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-054755.jpg</strong> (100.03 KB, 下载次数: 0)

下载附件

2023-12-21 05:51 上传

TAO-Amodal数据集具有多种(880种)标注，同时包含传统追踪(上)和非模态追踪(下)
————
传统l vs. 非模态追踪

<img src="https://img.saraba1st.com/forum/202312/21/055130qllx2wexatztw7dj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-054845.jpg</strong> (142.93 KB, 下载次数: 0)

下载附件

2023-12-21 05:51 上传

传统感知(上)集中于识别可见部分，因此，当它们面临着特殊输出时，例如在遮挡场景下边界框消失或框尺寸很小时，非模态感知(下)可以通过推断完整的对象边界，即使某些部分被遮挡，效果也超越了传统方法
————
TAO-Amodal数据集

<img src="https://img.saraba1st.com/forum/202312/21/055148cuig6798td4liulw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-054910.jpg</strong> (69.81 KB, 下载次数: 0)

下载附件

2023-12-21 05:51 上传

数据集通过非模态边界框标注增强了TAO数据集，其中涵盖了880个类别中完全不可见、框外和遮挡的对象，请注意，这意味着TAO-Amodal还包括模态分割掩码
————
非模态拓展器

<img src="https://img.saraba1st.com/forum/202312/21/055154c8ghypjugwwpwjho.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-055032.jpg</strong> (104.98 KB, 下载次数: 0)

下载附件

2023-12-21 05:51 上传

作为一个插件模块，可以使用有限的(非模态)训练数据“非模态化”任何现有的探测器或追踪器，在这里，提供了来自非模态扩展器的模态(上方)和非模态(下方)预测的定性结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1096#       发表于 2023-12-21 06:36

Customize-It-3D

使用特定于主题的知识先验从单张图像创造高质量3D

项目主页:https://nnanhuang.github.io/projects/customize-it-3d/

github项目仓库:https://github.com/nnanhuang/Customize-it-3D

在本文中，提出了一种新颖的两阶段方法，充分利用了参考图像提供的信息为图像到3D生成建立了个性化的知识先验，之前的方法主要依赖于通用的扩散先验，但往往无法产生与参考图像一致的结果

为此，本文提出了一种主题特定的多模态扩散模型，该模型不仅通过考虑改进几何结构的着色模式来帮助NeRF进行优化，还通过从粗略结果中增强纹理来实现更好的细化效果，这两个方面都有助于将3D内容与主题可信的对齐

大量的实验证明了Customize-It-3D方法的优越性，其结果明显优于之前的方法，它可以产生可信的360度的重建结果，具有令人印象深刻的视觉质量，非常适用于包括文本到3D创造在内的各种应用场景

<img src="https://img.saraba1st.com/forum/202312/21/063548k0wz2fl9jcw01b86.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-063017__01.jpg</strong> (388.03 KB, 下载次数: 0)

下载附件

2023-12-21 06:35 上传

 Customize-It-3D具有从单个图像中生成高保真3D内容的能力，为普通物体呈现了法线贴图和新视图渲染，突出了在新视图下纹理和几何的一致性，质量十分出色

<img src="https://img.saraba1st.com/forum/202312/21/063554uue68cz0ha6ctj30.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-063036__01.jpg</strong> (445.28 KB, 下载次数: 0)

下载附件

2023-12-21 06:35 上传

提出了一个两阶段的框架，用于根据主题特定的扩散先验依据参考图像进行高质量的3D创造，在粗略阶段，在着色感知的方式下通过优化NeRF来重建参考图像的几何形状，进一步从粗略阶段构建具有增强纹理的点云，并联合优化不可见点处的纹理以及可学习的延迟渲染器，以生成逼真且视角一致的纹理

<img src="https://img.saraba1st.com/forum/202312/21/063602ngllzzmlzuwr9qs6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-063050__01.jpg</strong> (108.02 KB, 下载次数: 0)

下载附件

2023-12-21 06:36 上传

所提出的着色模式感知引导极大地增强了粗略阶段的3D几何形状

<img src="https://img.saraba1st.com/forum/202312/21/063608jqt9oojj98wwe9wd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-063050__02.jpg</strong> (83.88 KB, 下载次数: 0)

下载附件

2023-12-21 06:36 上传

从深度图像和本文方法说明不同的点云构建方法

<img src="https://img.saraba1st.com/forum/202312/21/063613nwrr3wwzswvm513n.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-063121__01.jpg</strong> (111.9 KB, 下载次数: 0)

下载附件

2023-12-21 06:36 上传

使用多模态DreamBooth极大增强了粗略渲染的纹理细节

<img src="https://img.saraba1st.com/forum/202312/21/063619o6ezjtfileqwk5ng.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-063334.jpg</strong> (181.49 KB, 下载次数: 0)

下载附件

2023-12-21 06:36 上传

纹理点云的构造，增强新视图的纹理和掩码，并迭代地将纹理投影到点云

<img src="https://img.saraba1st.com/forum/202312/21/063623phvolbthklkbbgbw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-063128__01.jpg</strong> (80.43 KB, 下载次数: 0)

下载附件

2023-12-21 06:36 上传

RealFusion15上的定量对比，计算参考视图下的LPIPS和PSNR，以及新视图下的CLIP

<img src="https://img.saraba1st.com/forum/202312/21/063629wrr9zsfi55s8o5ep.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-063143__01.jpg</strong> (416.06 KB, 下载次数: 0)

下载附件

2023-12-21 06:36 上传

图像到3D生成的定性对比，将Customize-It-3D与RealFusion、Make-it-3D和Magic123进行了对比，以从单张无姿态图像(最左边的列)创造3D对象

<img src="https://img.saraba1st.com/forum/202312/21/063637tsbflflgdeaa5whg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-063158__01.jpg</strong> (134.1 KB, 下载次数: 0)

下载附件

2023-12-21 06:36 上传

Multimodal DreamBooth的效果，在几何和纹理方面都表现出了一致的改进

<img src="https://img.saraba1st.com/forum/202312/21/063642n9axv934ae9bran9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-063158__02.jpg</strong> (172.16 KB, 下载次数: 0)

下载附件

2023-12-21 06:36 上传

多模态DreamBooth与单RGB，在几何形状方面展示出了明显的改进

<img src="https://img.saraba1st.com/forum/202312/21/063649sbux6mbl4xp1mw4l.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-063204__01.jpg</strong> (109.58 KB, 下载次数: 0)

下载附件

2023-12-21 06:36 上传

高保真文本到3D生成的说明

<img src="https://img.saraba1st.com/forum/202312/21/063654foc4wcvc58vdkfcf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-063204__02.jpg</strong> (131.93 KB, 下载次数: 0)

下载附件

2023-12-21 06:36 上传

展示真实场景的高保真3D创造

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1097#       发表于 2023-12-21 08:49

HAAR

基于3D股丝(strand)的人类发型文本条件生成模型

项目主页:https://haar.is.tue.mpg.de/

code:to be released

本文提出了一种名为HAAR的，基于股丝的新型生成模型，可用于生成3D人体发型，具体而言，基于文本输入，HAAR可以生成用于现代计算机图形引擎中的生产资产级别的3D发型

当前基于人工智能的生成模型利用强大的2D先验知识来重建3D内容，以点云、网格或体积函数的形式，然而，通过使用2D先验知识，它们只能固有地恢复可见部分，这些方法无法重建高度遮挡的发型结构，并且仅对“外壳(outer shell)”进行建模，因此无法直接用于基于物理的渲染或仿真工作流程

相比之下，本文提出了首个文本引导的生成方法，使用3D头发股丝作为底层表征，通过利用2D VQA系统，使用自动标注从一小组由艺术家创造的发型中生成合成发型模型，这使之能够训练一个在常见发型UV空间(common hairstyle UV space)中操作的潜在扩散模型

通过定性和定量研究，展示了该模型的能力，并将其与现有的发型生成方法进行了对比

<img src="https://img.saraba1st.com/forum/202312/21/084420sduyutm6dzz4dcj5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-083934__01.jpg</strong> (614.05 KB, 下载次数: 0)

下载附件

2023-12-21 08:44 上传

给定一个文本描述，本文方法能够生成逼真的人类发型，由于使用了基于3D股丝的几何表征，使其能够轻松地融入现有的计算机图形工作流程中进行模拟和渲染

<img src="https://img.saraba1st.com/forum/202312/21/084425dll34y43isaj74iz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-083944__01.jpg</strong> (257.42 KB, 下载次数: 0)

下载附件

2023-12-21 08:44 上传

概览图，提出了一种新的文本引导和基于股丝的发型生成方法，对于训练集中的每个发型H，使用现成的VQA系统和定制的标注工作流程生成潜在的头发映射图Z，并使用文本标题P进行标注，然后训练一个条件扩散模型D在这个潜在空间中生成引导股丝，并使用潜在上采样过程来根据文本描述重建包含多达十万条股丝的密集发型，最后，使用现成的计算机图形技术来渲染生成的发型

<img src="https://img.saraba1st.com/forum/202312/21/084430gs89qxhwqwqqch8q.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-083951__01.jpg</strong> (170.14 KB, 下载次数: 0)

下载附件

2023-12-21 08:44 上传

数据集收集，通过将渲染的正面和背面视图的发型以及预定义的问题集合Q送入VQA，获得发型描述，然后使用冻结的文本编码器网络对其进行进一步编码

<img src="https://img.saraba1st.com/forum/202312/21/084434y7kava675vbgmakb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-084007__01.jpg</strong> (523.32 KB, 下载次数: 0)

下载附件

2023-12-21 08:44 上传

无条件扩散模型的对比，本文方法生成的样本质量和多样性更好

<img src="https://img.saraba1st.com/forum/202312/21/084822tfanuv4fzj4km4v4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-084007__01.jpg</strong> (523.32 KB, 下载次数: 0)

下载附件

2023-12-21 08:48 上传

对条件生成模型的定性对比，展示了TECA和本文模型的几个生成结果，对于本文结果，可视化了在上采样之前(以伪彩色/pseudocolor显示)和上采样之后得到的几何形状，本文模型生成了更多样化、质量更高的发型样本，值得注意的是，在某些情况下，TECA并没有很好地遵循输入描述，生成了短发而不是长发

<img src="https://img.saraba1st.com/forum/202312/21/084852kbb3a2hmn33z2xnb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-084020__01.jpg</strong> (531.94 KB, 下载次数: 0)

下载附件

2023-12-21 08:48 上传

上采样，在引导股丝之间进行插值对比不同的上采样方案(以深色表示)，为了展示效果，这里使用了约15000股毛发，在Blender中，插值是在3D空间中进行的，而本文方法是在潜在空间中计算的

在这两种变体中，使用最近邻(Nearest Neighbour)的方法可以更准确地根据引导股丝的几何形状(以深色表示)，但会导致整体外观不真实，双线性方案会导致发型平均股丝穿透和原始引导股丝结构的消失，将这两种方法结合起来可以解决提出的问题，并得到逼真的渲染结果

在潜在空间中添加额外的噪声可以进一步增加逼真度，并有助于消除网格结构

<img src="https://img.saraba1st.com/forum/202312/21/084857osmq3qw3worn2swr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-084025__01.jpg</strong> (37.64 KB, 下载次数: 0)

下载附件

2023-12-21 08:48 上传

条件化，对不同的条件化方案进行了消融实验，使用BLIP文本编码器，得到了比CLIP和可训练的Transformer网络更好的条件化效果

<img src="https://img.saraba1st.com/forum/202312/21/084906h0lio0j0jvxvl0l0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-084036__01.jpg</strong> (506.65 KB, 下载次数: 0)

下载附件

2023-12-21 08:49 上传

发型编辑，类似于Imagic，使用文本提示来编辑输入图像，提供了没有额外调整的扩散模型的编辑结果(前两行)，以及有额外调整的结果(后两行)，微调扩散模型可以实现更平滑的编辑，并更好地保留输入的发型

<img src="https://img.saraba1st.com/forum/202312/21/084911b2129caaianc1zyo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-084041__01.jpg</strong> (128.43 KB, 下载次数: 0)

下载附件

2023-12-21 08:49 上传

有关局限，失败案例包括对头皮区域的穿透(左)，原则上可以通过后处理步骤来解决，此外，对于非洲发型(右)，需要增加股丝的卷曲程度

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1098#       发表于 2023-12-21 20:08

 本帖最后由 Machinery 于 2023-12-21 20:09 编辑 

MixRT

用于实时NeRF渲染的混合神经表征

项目主页:https://licj15.github.io/MixRT/

神经辐射场(NeRF)作为一种主流的新视图合成技术，以其令人印象深刻的逼真重建和渲染能力而令人印象深刻，然而，在大规模场景中进行实时NeRF渲染一直存在挑战，通常来说，方法需要采用复杂的大量烘焙网格表示或资源密集的烘焙表示中的光线行进

通过对这些传统方法提出了质疑，观察到高质量的几何形状，由大量三角形组成的网格表示，并不是实现逼真渲染质量所必需的，因此本文提出了MixRT，一种新颖的NeRF表征方法，包括低质量的网格、视图相关的位移映射和压缩的NeRF模型，这种设计有效地利用了现有图形硬件的能力，从而在边缘设备上实现了实时的NeRF渲染效果

通过利用高度优化的基于WebGL的渲染框架，提出的MixRT在边缘设备上实现了实时渲染速度(在MacBook M1 Pro笔记本上以1280 x 720的分辨率达到30 FPS以上)，具有更好的渲染质量(在Unbounded-360数据集的室内场景中比其他SOTA方法高出0.2 PSNR)，以及更小的存储空间(与现有方法相比减少了80%)
————
MixRT渲染工作流程概览

<img src="https://img.saraba1st.com/forum/202312/21/200821lrbeabhaubssuhbb.jpg" referrerpolicy="no-referrer">

<strong>104ba700-d646-4cc1-a7c4-203ab640d9d6.jpg</strong> (94.13 KB, 下载次数: 0)

下载附件

2023-12-21 20:08 上传

MixRT整合了三个核心组件：低质量网格、视图相关的位移映射和压缩成哈希表的NeRF模型，这种组合旨在最大程度地利用各种硬件资源，为了渲染图像像素:

1.使用光栅化硬件执行网格光栅化，确定光线与网格的交点p
2.利用纹理映射单元，使用纹理坐标访问包含球谐函数(spherical harmonics)系数和尺度的映射，计算校准点pcali
3.最后，通过SIMD单元对pcali进行处理，从以哈希表形式存储的3D网格中检索其最近的八个顶点的嵌入，然后一个小型MLP网络将这些插值嵌入转换为最终的渲染颜色
————
相关效果:

<img src="https://img.saraba1st.com/forum/202312/21/200831yeenjr2xfwovmu2t.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-200538__01.jpg</strong> (121.12 KB, 下载次数: 0)

下载附件

2023-12-21 20:08 上传

<img src="https://img.saraba1st.com/forum/202312/21/200831jbnwnaz5yhdndmyd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-200546__01.jpg</strong> (128.65 KB, 下载次数: 0)

下载附件

2023-12-21 20:08 上传

<img src="https://img.saraba1st.com/forum/202312/21/200831nni5v5frwyroigwn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-200552__01.jpg</strong> (123.73 KB, 下载次数: 0)

下载附件

2023-12-21 20:08 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1099#       发表于 2023-12-21 21:03

 本帖最后由 Machinery 于 2023-12-21 21:05 编辑 

Emu2

生成式多模态模型是上下文学习者

项目主页:https://baaivision.github.io/emu2

演示Demo:http://218.91.113.230:9002/

github综合项目主页:https://github.com/baaivision/Emu

hugface演示:https://huggingface.co/spaces/BAAI/Emu2

hugface模型权重下载:https://huggingface.co/BAAI/Emu2

当前的多模态系统很难模仿人类在上下文中轻松解决多模态任务的能力(即仅需少量演示或简单指令)，在这项工作中，展示了通过有效扩展(effective scaling-up)，可以显著增强大型多模态模型在任务无关的上下文中学习的能力(task-agnostic in-context learning capabilities)

本文介绍了Emu2，一个具有370亿参数的生成式多模态模型，通过统一的自回归目标在大规模多模态序列上进行训练，Emu2展现了强大的多模态上下文学习能力，甚至能够解决需要即时推理的任务，如视觉提示和基于对象的生成(object-grounded generation)

该模型在多种少样本设置下的多模态理解任务上创下了新纪录，当调整为遵循特定指令时，Emu2在具有挑战性的任务上进一步实现了SOTA水平，例如大规模多模态模型的问答基准测试和开放式主题驱动生成，这些成就表明Emu2足以作为基础模型和广泛应用于各种多模态任务的通用接口，为了促进未来的研究，代码和模型已开源
————
强大的多模态少样本学习者

<img src="https://img.saraba1st.com/forum/202312/21/210228byo54z2llwvfwh96.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-205928.jpg</strong> (55.83 KB, 下载次数: 0)

下载附件

2023-12-21 21:02 上传

令人印象深刻的多模态全才

<img src="https://img.saraba1st.com/forum/202312/21/210236ke2hhm4qqkfmqk2a.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-205938.jpg</strong> (75.36 KB, 下载次数: 0)

下载附件

2023-12-21 21:02 上传

熟练的画家

<img src="https://img.saraba1st.com/forum/202312/21/210241hvaa1gamesmz3kpa.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-205955.jpg</strong> (42.19 KB, 下载次数: 0)

下载附件

2023-12-21 21:02 上传

多模态上下文学习

<img src="https://img.saraba1st.com/forum/202312/21/210251v8jgoxbqg6jkmsjx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-210022.jpg</strong> (192.06 KB, 下载次数: 0)

下载附件

2023-12-21 21:02 上传

强大的多模态理解

<img src="https://img.saraba1st.com/forum/202312/21/210303dhjnhixeneyyhxh4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-210030.jpg</strong> (322.55 KB, 下载次数: 0)

下载附件

2023-12-21 21:03 上传

从任何提示序列生成图像

<img src="https://img.saraba1st.com/forum/202312/21/210309gvezc8cw441h8bpb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-210128.jpg</strong> (80.49 KB, 下载次数: 0)

下载附件

2023-12-21 21:03 上传

<img src="https://img.saraba1st.com/forum/202312/21/210315m8mst93smltm9ayt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-210140.jpg</strong> (95.58 KB, 下载次数: 0)

下载附件

2023-12-21 21:03 上传

从任何提示序列生成视频

<img src="https://img.saraba1st.com/forum/202312/21/210325j50dbwn070w06e9n.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231221-210200.jpg</strong> (211.05 KB, 下载次数: 0)

下载附件

2023-12-21 21:03 上传

————
方法

<img src="https://img.saraba1st.com/forum/202312/21/210337tjmxzqlkjq3xqkej.png" referrerpolicy="no-referrer">

<strong>emu2_method.png</strong> (828.29 KB, 下载次数: 0)

下载附件

2023-12-21 21:03 上传

Emu2以预测下一个元素(predict-the-next-element)为目标进行多模态学习，多模态序列中的每张图像都会经由视觉编码器进行分词处理(tokenized)转为嵌入，然后与文本Token交错以进行自回归建模，通过回归得到的视觉嵌入将由视觉解码器解码成图像或视频，与Emu1相比，Emu2采用了更简单的框架、更好的视觉解码器，并且参数规模扩大到了370亿

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1100#       发表于 2023-12-22 01:08

Repaint123

通过渐进式可控2D重绘，快速高质量地将单图像生成为3D

github项目仓库:https://github.com/junwuzhang19/repaint123

最近，一些将单图像转换为3D的方法普遍采用了分数蒸馏采样(Score Distillation Sampling)，尽管结果令人印象深刻，但存在多个不足之处，包括多视图不一致、过饱和以及过于平滑的纹理，生成速度慢等

为了解决这些不足，本文提出了Repaint123，以缓解多视角偏差、纹理退化并加快生成过程，其核心思想是结合2D扩散模型的强大图像生成能力和重绘策略的纹理对齐能力，生成具有一致性的高质量多视图图像

进一步提出了重叠区域处的可见度感知的适配重绘强度(visibility-aware adaptive repainting strength)，以增强重绘过程中的生成图像质量，生成的高质量和多视图一致的图像使之可以使用简单的平均方误差(MSE)损失进行快速的3D内容生成

大量实验证明，本文方法能够在2分钟内从头开始生成具有多视图一致性和精细纹理的高质量3D内容

<img src="https://img.saraba1st.com/forum/202312/22/010801lasag4bd39nxfa4g.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-010349__01.jpg</strong> (341.92 KB, 下载次数: 0)

下载附件

2023-12-22 01:08 上传

Repaint123仅需一张图像即可在短短2分钟内生成高质量的具有详细纹理的3D内容，Repaint123在粗略阶段使用高斯泼溅技术，然后利用2D可控扩散模型和重绘策略生成视觉一致的高质量图像，这样即可通过简单的平均方误差损失快速而高质量地细化提取的网格纹理

<img src="https://img.saraba1st.com/forum/202312/22/010808sfe6x81dygqip66q.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-010402__01.jpg</strong> (340.13 KB, 下载次数: 0)

下载附件

2023-12-22 01:08 上传

提出工作流程的动机，当前的方法采用SDS损失，导致纹理不一致且质量较差，因此想法是将可控的2D扩散模型的强大图像生成能力与重绘策略的纹理对齐能力相结合，生成高质量的多视图一致图像，重绘的图像可以使用简单的平均方误差损失快速生成3D内容

<img src="https://img.saraba1st.com/forum/202312/22/010814kjj9gf9od6sju826.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-010419__01.jpg</strong> (353.15 KB, 下载次数: 0)

下载附件

2023-12-22 01:08 上传

可控重绘方案，采用DDIM反演从粗略图像中生成决定性的噪声潜在，随后由深度引导几何(depth-guided geometry)、参考图像语义(reference image semantics)和注意力驱动的参考纹理(attention-driven reference texture)控制的扩散模型进行细化，时间步感知的二值化操作(timestep-aware binarization operation)将可见映射(visibility map)二值化为重叠掩码(overlap mask)，在每个去噪步骤中，选择性地对重叠区域进行重绘，从而得到高质量的细化新视图图像

<img src="https://img.saraba1st.com/forum/202312/22/010820nxr2d83k8rx3r223.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-010430__01.jpg</strong> (293.73 KB, 下载次数: 0)

下载附件

2023-12-22 01:08 上传

图像到3D生成工作流程，在粗略阶段，在新视图中使用SDS损失对高斯泼溅表征进行优化，在细化阶段，导出网格表征(Mesh representation)，并双向和逐步采样新视图以进行可控的渐进重绘，新视图的细化图像将与输入的新视图图像一起计算MSE损失，以实现高效的生成，红色的摄影机是用于获取可见映射的双向邻近摄影机(bidirectional neighbor cameras)

<img src="https://img.saraba1st.com/forum/202312/22/010826g0xile32l2xvtdy2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-010436__01.jpg</strong> (192.59 KB, 下载次数: 0)

下载附件

2023-12-22 01:08 上传

摄影机视图和细化强度的相关关系，红框内的区域是从不同视图获取的相同区域

<img src="https://img.saraba1st.com/forum/202312/22/010832sa3m3kxam7m7mmqu.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-010453__01.jpg</strong> (358.99 KB, 下载次数: 0)

下载附件

2023-12-22 01:08 上传

图像到3D生成的定性对比

<img src="https://img.saraba1st.com/forum/202312/22/010838h0b300nmh12mw03b.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-010507__01.jpg</strong> (287.92 KB, 下载次数: 0)

下载附件

2023-12-22 01:08 上传

展示了定量结果，在RealFusion15和test-alpha数据集上，加粗代表所有方法中最好的结果，下划线表示基于高斯泼溅的方法中最好的结果，*表示Zero123-XL添加了网格微调阶段以进一步提高质量，文本反转(textual inversion)所需的时间用括号表示

<img src="https://img.saraba1st.com/forum/202312/22/010843jxrq9hu9p009ka09.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-010527__01.jpg</strong> (99.35 KB, 下载次数: 0)

下载附件

2023-12-22 01:08 上传

Test-alpha数据集的定量消融实验

<img src="https://img.saraba1st.com/forum/202312/22/010848fu8z52ymu2a8n8mn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-010527__02.jpg</strong> (209.82 KB, 下载次数: 0)

下载附件

2023-12-22 01:08 上传

定性消融实验，红色框内为伪影

<img src="https://img.saraba1st.com/forum/202312/22/010853s33kopp8yfo0p5o0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-010539__01.jpg</strong> (79.18 KB, 下载次数: 0)

下载附件

2023-12-22 01:08 上传

在Test-alpha数据集上Repaint123中相邻视点所选角度对结果的影响

<img src="https://img.saraba1st.com/forum/202312/22/010857i7qa6aqjlneariva.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-010545__01.jpg</strong> (107.53 KB, 下载次数: 0)

下载附件

2023-12-22 01:08 上传

当选择40°和60°作为角度间隔时，进行可视化对比，红色框显示了出现的多面问题

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1101#       发表于 2023-12-22 02:09

StreamDiffusion

实时交互生成的流程级解决方案

github项目主页:https://github.com/cumulo-autumn/StreamDiffusion

StreamDiffusion，一个专为交互式图像生成设计的实时扩散工作流程，现有的扩散模型在根据文本或图像提示生成图像方面表现出色，但在实时交互方面往往存在局限性，这种限制在涉及连续输入的场景中尤为明显，比如Metaverse、实时直播视频流和广播等，这些场景中高吞吐量至关重要

为了解决这个问题，提出了一种新颖的方法，将原始的顺序去噪转化为批量去噪过程，Stream Batch消除了传统的等待和交互方法，实现了流畅且高吞吐量的流式处理，为了处理数据输入和模型吞吐量之间的频率差异，设计了一种新颖的输入输出队列，以并行化流式处理过程，此外，现有的扩散工作流程使用了无分类器引导(CFG)，需要额外的U-Net计算，为了减少冗余计算，提出了一种新颖的残差无分类器引导(RCFG)算法，将负条件去噪步骤(negative conditional denoising steps)的数量减少到仅为一步甚至零步，此外还引入了一种随机相似性过滤器(SSF/stochastic similarity filter)来优化功耗

与顺序去噪方法相比，Stream Batch在不同的去噪级别下实现了约1.5倍的加速，所提出的RCFG的速度比传统的CFG高出了2.05倍，结合所提出的策略和现有的成熟加速工具，使得图像到图像生成在RTX4090上达到了最高91.07fps的吞吐量，比Diffusers开发的AutoPipline的吞吐量提高了59.56倍，此外，所提出的StreamDiffusion还显著降低了能耗，分别在RTX3060和RTX4090上达到了2.39倍和1.99倍的降低

项目说明截图:

<img src="https://img.saraba1st.com/forum/202312/22/020955vm5exxgpephpd5c9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-020743.jpg</strong> (509.93 KB, 下载次数: 0)

下载附件

2023-12-22 02:09 上传

<img src="https://img.saraba1st.com/forum/202312/22/020955klfsxcxxxuxaavou.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-020756.jpg</strong> (145.46 KB, 下载次数: 0)

下载附件

2023-12-22 02:09 上传

<img src="https://img.saraba1st.com/forum/202312/22/020955gpigx2o0b5i4bpgb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-020816.jpg</strong> (461.76 KB, 下载次数: 0)

下载附件

2023-12-22 02:09 上传

<img src="https://img.saraba1st.com/forum/202312/22/020955wzlzzxlh2t9nsav5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-020842.jpg</strong> (695.79 KB, 下载次数: 0)

下载附件

2023-12-22 02:09 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1102#       发表于 2023-12-22 19:28

 本帖最后由 Machinery 于 2023-12-22 19:31 编辑 

InstructVideo

人类反馈的指导视频扩散模型

项目主页:https://instructvideo.github.io/

github模型与项目仓库:https://github.com/damo-vilab/i2vgen-xl/blob/main/doc/InstructVideo.md

在视频生成方面，扩散模型已成为事实上的范式，然而，由于依赖于质量各异的大规模网络数据，这些模型往往会产生在视觉上不够吸引人，与文本提示也不一致的结果

为了解决这个问题，本文提出了InstructVideo，通过奖励微调使用人类反馈来指导文本到视频扩散模型，InstructVideo有两个关键要素:

1.为了减少通过完整的DDIM采样链生成视频所需的奖励微调成本，将奖励微调定义为编辑(editing)，通过利用扩散过程来破坏采样视频，InstructVideo仅需要对DDIM采样链的部分进行推理，从而降低了微调成本，同时提高了微调效率

2.为了满足缺乏的专门针对人类偏好的视频奖励模型，通过重新利用已有的图像奖励模型，例如HPSv2，提出了分段视频奖励(Segmental Video Reward)，这个机制基于分段稀疏采样提供奖励信号，以及时间衰减奖励，这个方法在微调过程中缓解了时间建模的退化(degradation)

大量的定性和定量实验证实了InstructVideo中使用图像奖励模型的实用性和有效性，显著提高了生成视频的视觉质量，同时并未降低泛化能力

<img src="https://img.saraba1st.com/forum/202312/22/192735u0l9fwa9xwnwl75f.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-192326__01.jpg</strong> (176.31 KB, 下载次数: 0)

下载附件

2023-12-22 19:27 上传

InstructVideo框架概览图，为了在采样的视频文本对上进行高效微调，使用了图像奖励模型中的人类偏好

<img src="https://img.saraba1st.com/forum/202312/22/192740l37r97777bvqe2pz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-192340__01.jpg</strong> (398.61 KB, 下载次数: 0)

下载附件

2023-12-22 19:27 上传

InstructVideo的奖励微调框架，在微调过程中，对视频文本对进行采样，并应用扩散过程将视频损坏到噪声水平τ，随后，对DDIM采样链进行部分推理，获得人类偏好的编辑视频，通过利用SegVR和TAR，可以利用图像奖励模型对视频生成进行奖励微调，为了清晰起见，VQGAN编码器和解码器被省略，在这个例子中，通过人类偏好来编辑模糊的视频z，产生了一个突显花从的活力和结构的结果

<img src="https://img.saraba1st.com/forum/202312/22/192751i4kgzfyz74oa4gma.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-192355__01.jpg</strong> (897.42 KB, 下载次数: 0)

下载附件

2023-12-22 19:27 上传

InstructVideo与基本模型ModelScope T2V的对比，ModelScope T2V使用了20和50的DDIM步骤

<img src="https://img.saraba1st.com/forum/202312/22/192758ojmb99l9l33buv3u.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-192403__01.jpg</strong> (713.1 KB, 下载次数: 0)

下载附件

2023-12-22 19:27 上传

InstructVideo与其他奖励微调方法的对比，为所有方法设置D=20

<img src="https://img.saraba1st.com/forum/202312/22/192803ug71g4zj18kv8vu1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-192409__01.jpg</strong> (188.09 KB, 下载次数: 0)

下载附件

2023-12-22 19:28 上传

(a)与其他奖励微调方法的对比
(b)不同的噪声水平τ的影响，垂直虚线表示τ=0.6时的20k优化步骤
(c)改变λtar的影响

<img src="https://img.saraba1st.com/forum/202312/22/192809y69qrisy4igay78v.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-192421__01.jpg</strong> (836.47 KB, 下载次数: 0)

下载附件

2023-12-22 19:28 上传

InstructVideo的泛化能力与其他方法的对比，为所有方法设置D=20

<img src="https://img.saraba1st.com/forum/202312/22/192813wt1azim89kta3imm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-192437__01.jpg</strong> (131.41 KB, 下载次数: 0)

下载附件

2023-12-22 19:28 上传

未见的文本提示的泛化效果，†表示模型采用D=50，而其他模型采用D=20，“in-domain”表示来自评估数据的域内动物文本提示

<img src="https://img.saraba1st.com/forum/202312/22/192820erhoqor8clorty88.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-192437__02.jpg</strong> (71.07 KB, 下载次数: 0)

下载附件

2023-12-22 19:28 上传

用户研究结果，“Tie”表示标注者认为两个视频质量相当的情况，“Quality”和“Alignment”代表视频质量和视频文本对齐

<img src="https://img.saraba1st.com/forum/202312/22/192825gquuy3387uvub7vb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-192451__01.jpg</strong> (234.2 KB, 下载次数: 0)

下载附件

2023-12-22 19:28 上传

SegVR和TAR的消融实验，该视频展示了一只白色犬在公园缓步行走

<img src="https://img.saraba1st.com/forum/202312/22/192831dnpr6t8p26p0033p.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-192500__01.jpg</strong> (319.98 KB, 下载次数: 0)

下载附件

2023-12-22 19:28 上传

微调期间生成的视频变化，展示了一只短尾犬在散步

<img src="https://img.saraba1st.com/forum/202312/22/192837jjjxzbfqa334cf4s.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-192500__02.jpg</strong> (81.21 KB, 下载次数: 0)

下载附件

2023-12-22 19:28 上传

不同的微调数据的效果，彩色水平虚线表示不同的微调数据的奖励分数，与相应曲线的颜色匹配

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1103#       发表于 2023-12-22 21:21

AppAgent

作为智能手机用户的多模态代理

项目主页:https://appagent-official.github.io/

github项目仓库:https://github.com/mnotgod96/AppAgent

最近大型语言模型(LLM)的最新进展使得我们可以创建出能够执行复杂任务的智能代理者，本文介绍了一种新颖的基于LLM的多模态代理框架，旨在操作智能手机应用程序，框架通过简化的操作空间使代理者能够操作智能手机应用程序，模拟人类的点击和滑动等类人交互方式

这种新颖的方法绕过了对系统后端访问的需求，从而增加了其适用性，可以应用于各种不同的应用程序，代理者的核心功能是其创新的学习方法，代理者通过自主探索或观察人类演示学习导航和使用新的应用程序，在这个过程中生成了一个知识库(knowledge base)，使之能够在解决在不同应用程序上的不同复杂任务时进行参考

为了证明本文代理者的实用性，在10个不同的应用程序中进行了50个任务的广泛测试，包括社交媒体、电子邮件、地图、购物和复杂的图像编辑工具，结果证实了代理者在处理多样化的高水平任务方面的熟练程度

<img src="https://img.saraba1st.com/forum/202312/22/212050dah3xnhuk9otmn59.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-211754__01.jpg</strong> (365.82 KB, 下载次数: 0)

下载附件

2023-12-22 21:20 上传

多模态代理框架在智能手机应用程序操作中的多种应用方法，在10个不同的应用程序中评估了代理者模型在50个任务上的有效性，突出了它在真实环境中的适应能力和有效性

<img src="https://img.saraba1st.com/forum/202312/22/212059vcv081ucdowfv1b4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-211812__01.jpg</strong> (328.62 KB, 下载次数: 0)

下载附件

2023-12-22 21:20 上传

设计的多模态代理框架用于操作智能手机应用程序的概览图，该图展示了框架的两阶段方法，在探索阶段，代理者与智能手机应用程序进行交互，并从结果中学习，用以创造一个全面的参考文档，在部署阶段，代理者利用编制的这个文档中的信息来有效地操作和导航应用程序

<img src="https://img.saraba1st.com/forum/202312/22/212105zy0xy6llbmvpm08z.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-211834__01.jpg</strong> (472.36 KB, 下载次数: 0)

下载附件

2023-12-22 21:21 上传

<img src="https://img.saraba1st.com/forum/202312/22/212105wxsl1ztjl8jfmzfg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-211845__01.jpg</strong> (287.89 KB, 下载次数: 0)

下载附件

2023-12-22 21:21 上传

三个应用的定性任务评估，该图展示了在Google地图、Gmail和Lightroom上进行的三个不同任务的定性结果，同时展示了AppAgent在准确感知、推理和执行任务方面的能力，证明了在各种应用场景中的能力，由于空间限制，描述中省略了一些不太重要的细节
—

<img src="https://img.saraba1st.com/forum/202312/22/212110xh9ww4d7h5ee75e5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-211850__01.jpg</strong> (138.81 KB, 下载次数: 0)

下载附件

2023-12-22 21:21 上传

评估AppAgent设计选择中的性能表现，该表对AppAgent的不同设计要素进行了对比，其中关键发现包括:自定义开发的操作空间在效率上超过了原始的操作空间；探索阶段，结合自主互动和观察人类示范，显著提高了代理者的性能；自动生成的文档与手工制作的文档产生的结果相当

<img src="https://img.saraba1st.com/forum/202312/22/212116og02cjh8mbcu8szh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231222-211850__02.jpg</strong> (94.23 KB, 下载次数: 0)

下载附件

2023-12-22 21:21 上传

使用Lightroom应用进行图像编辑任务的案例研究，进行了用户研究，对不同方法的图像编辑结果进行排序，本文代理者比GPT-4基线产生了更好的结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1104#       发表于 2023-12-23 02:41

 本帖最后由 Machinery 于 2023-12-23 02:42 编辑 

lm-weights-encode-time

将时间编码在微调语言模型的权重中

github项目主页:https://github.com/KaiNylund/lm-weights-encode-time

本文提出了时间向量，一种使语言模型适应新时间段(new time periods)的简单工具，时间向量是通过在一段时间内(例如一年或一个月)的数据上微调预训练语言模型，并减去原始预训练模型的权重而创建的

这个向量在权重空间中指定了一个方向，正如本文实验所显示的那样，它可以改善该时间段的文本性能，专门用于邻近时间段的时间向量似乎在流形(manifold)中更接近，利用这种结构，可以在时间向量之间进行插值，从而创建在介入时以及未来时间段上表现更好的新模型，而无需进行额外的训练

在不同任务、领域、模型大小和时间尺度上展示了发现的一致性，结果表明，时间可以被编码在微调模型的权重空间中

<img src="https://img.saraba1st.com/forum/202312/23/023907pmzm8z0ps35fr0a1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-023430__01.jpg</strong> (133.79 KB, 下载次数: 0)

下载附件

2023-12-23 02:39 上传

提出了时间向量(τi)，这是一种简单的工具，可以将语言模型定制到新的时间段(i)，时间向量在权重空间中指定了一个方向，可以提高时间段的文本上的性能，它们是通过从预训练的权重(θpre)中减去针对目标时间段微调的权重(θi)来计算的

通过在时间向量之间进行插值并将结果添加到预训练模型中(中间图)，可以将模型行为定制到新的时间段(例如中间的几个月或几年)，还可以通过类推算法(analogy arithmetic)将模型推广到未来的时间段(j)，这涉及将任务特定的时间向量与从微调的语言模型(τLMj)中得到的类推时间向量相结合

<img src="https://img.saraba1st.com/forum/202312/23/023914i9b9a6ldsbl0mg0h.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-023508__01.jpg</strong> (271.83 KB, 下载次数: 0)

下载附件

2023-12-23 02:39 上传

模型性能呈逐年线性下降趋势，评估了语言模型困惑度(WMT)，ROUGE-L(新闻摘要)和macro F1(政策倾向分类)，每个单元格表示T5-3B在该任务的一年中进行微调和评估的月度性能，报告了每年相对于平均性能的百分比差异，并发现无论是何任务，随着微调和评估年份的错位，性能呈线性退化趋势，在T5-small和medium中发现了类似的趋势

<img src="https://img.saraba1st.com/forum/202312/23/023918iohkfnx7k02vc05j.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-023523__01.jpg</strong> (151.38 KB, 下载次数: 0)

下载附件

2023-12-23 02:39 上传

月度时间退化具有季节模式，每个单元格都表示了对T5-small微调并在WMT数据集的其中一个月上进行评估的月度性能，报告了相对于所有微调的T5-small模型在评估月份上的平均测试困惑度的百分比差异(较暗表示较好)，对角线表示每个模型在其微调月份上表现最好，模型在其他年份的同一月份上也相对较好，可以从每12个月从对角线辐射出的条纹可见

<img src="https://img.saraba1st.com/forum/202312/23/023923aywjn5rc2nh5dhaz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-023537__01.jpg</strong> (51.7 KB, 下载次数: 0)

下载附件

2023-12-23 02:39 上传

时间向量在流形中的组织反应了随时间变化的情形，每个点都是在单个WMT月份上微调的T5-small时间向量的最后前馈层的UMAP投影，相邻月份之间的点和边按年份着色，时间向量权重之间的距离与时间错位相关

<img src="https://img.saraba1st.com/forum/202312/23/023931yttqat8inzadhwnz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-023550__01.jpg</strong> (72.62 KB, 下载次数: 0)

下载附件

2023-12-23 02:39 上传

与时间向量相关的时间退化之间的相似性

年度时间向量的余弦相似度与每个评估时间段内所有年度模型平均性能的退化%之间的皮尔逊相关系数(Pearson correlation)

所有p值均＜8×10^-4

<img src="https://img.saraba1st.com/forum/202312/23/024239zvexxvg7nnw06m0h.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-024221.jpg</strong> (88.66 KB, 下载次数: 0)

下载附件

2023-12-23 02:42 上传

起始年份和结束年份之间的插值减少了微调模型中间年份的时间错位，T5-3b在起始年份和结束年份之间的每年平均表现(不包括起始和结束年份)，“Best interpolations”使用每年最佳的α值

<img src="https://img.saraba1st.com/forum/202312/23/024108pu2g8ur8rbookjjk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-023649__01.jpg</strong> (262.84 KB, 下载次数: 0)

下载附件

2023-12-23 02:41 上传

在两个年份向量之间进行插值可以提高它们之间年份的性能，这些性能改进遵循直观的结构，例如，在2012年和2016年之间进行插值时，在2013年出现最佳结果相比2012年发生百分比更高，2015年则反之亦然，插值导致的改进在不同设置下有所不同

<img src="https://img.saraba1st.com/forum/202312/23/024054vt4cg1ti0wxnbwcg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-023658__01.jpg</strong> (405.8 KB, 下载次数: 0)

下载附件

2023-12-23 02:40 上传

在两个月向量之间进行插值可以提高它们之间月份的性能，在1月和12月的月份向量之间进行插值，并在微调的同一年的所有其他月份进行评估，与年度尺度一样，早期的月份在使用更高比例的1月模型时效果更好，反之亦然，而中间的月份在两个模型之间以50%的比例表现最佳，上图中的星星对应于每个评估月份中表现最好的插值结果；这些最佳结果在下面的线图中得到了体现

<img src="https://img.saraba1st.com/forum/202312/23/024036gm62ly28fllb9s8o.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-024017.jpg</strong> (136.69 KB, 下载次数: 0)

下载附件

2023-12-23 02:40 上传

任务类推可以在没有目标时间的标记数据的情况下抵消下游时间错位，报告了使用WMT LM和Twitter LM向量更新的NewsSum和PoliAff T5模型在每个目标评估时间上的性能，还报告了对于所有模型尺寸的最佳更新模型相对于2012年NewsSum和2015年PoliAff模型在每个目标时间上的性能改进百分比

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1105#       发表于 2023-12-23 04:03

Paint3D

使用无光照纹理扩散模型(Lighting-Less Texture Diffusion Models)绘制任何3D

github项目主页:https://github.com/OpenTexture/Paint3D

Paint3D，一种新颖的从粗到细(coarse-to-fine)的生成框架，能够在给定文本或图像输入的情况下为无纹理的3D网格生成高分辨率、无光照和多样化的2K UV纹理映射

本文方法的关键挑战是在不嵌入光照信息的情况下生成高质量的纹理，使得纹理可以在现代图形工作流程中重新照明或编辑，为了实现这一目标，本文方法首先利用预训练的深度感知2D扩散模型(pre-trained depth-aware 2D diffusion model)生成视图条件图像(view-conditional images)，并进行多视图纹理融合(multi-view texture fusion)，以生成初始的粗略纹理映射(initial coarse texture map)

然而，由于2D模型无法完全表示3D形状并禁用了光照效果，粗糙纹理映射会出现不完整的区域(incomplete areas)和光照伪影(illumination artifacts)，为了解决这个问题，分别训练了UV重绘(UV Inpainting)和UVHD扩散模型(UVHD diffusion models)专门用于形状感知的细化不完整区域和去除光照伪影，通过这个从粗到细的过程，Paint3D可以生成高质量的2K UV纹理，保持语义一致性，同时无需光照，显著推动了纹理化3D对象的SOTA水平

<img src="https://img.saraba1st.com/forum/202312/23/040209df0mj75wodzjd08o.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-035704__01.jpg</strong> (608.01 KB, 下载次数: 0)

下载附件

2023-12-23 04:02 上传

Paint3D生成的纹理结果画廊，本文方法能够在跨越各种类别的不同物体上生成无光照的高质量、高保真的纹理

<img src="https://img.saraba1st.com/forum/202312/23/040216ed1m1h4d7dzmghyy.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-035720__01.jpg</strong> (123.36 KB, 下载次数: 0)

下载附件

2023-12-23 04:02 上传

预照明问题的示意图，具有自由照明的纹理映射与传统渲染流程兼容，而在预照明纹理上应用重新照明时会出现不适当的阴影

<img src="https://img.saraba1st.com/forum/202312/23/040225sjdrng6osrnnjg16.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-035743__01.jpg</strong> (491.33 KB, 下载次数: 0)

下载附件

2023-12-23 04:02 上传

从粗到细的框架概览图，粗略阶段从预训练的2D图像扩散模型中采样多视图图像，然后将这些图像反投影到网格表面上，创建初始纹理映射，细化阶段在UV空间中依照位置映射和粗略纹理映射条件使用扩散模型生成高质量纹理

<img src="https://img.saraba1st.com/forum/202312/23/040232v9ej4v9v6jbjvjlz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-035805__01.jpg</strong> (603.64 KB, 下载次数: 0)

下载附件

2023-12-23 04:02 上传

基于文本提示的条件纹理生成定性对比，将本文的纹理网格与Latent-Paint、TEXTure和Text2Tex进行了对比，与基线相比，本文方法生成了自由光照的纹理映射，以及更精美的纹理细节

<img src="https://img.saraba1st.com/forum/202312/23/040239sti6ikl22lwbbbkb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-035819__01.jpg</strong> (67.96 KB, 下载次数: 0)

下载附件

2023-12-23 04:02 上传

文本到纹理任务的定量对比，本文方法在FID和KID方面均优于其他方法

<img src="https://img.saraba1st.com/forum/202312/23/040245f40ivzqs03e3u4wq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-035828__01.jpg</strong> (258.75 KB, 下载次数: 0)

下载附件

2023-12-23 04:02 上传

以图像提示为条件的纹理生成的定性对比，与TEXTure相比，本文方法可以更好地表示图像条件中包含的纹理细节

<img src="https://img.saraba1st.com/forum/202312/23/040251vpxhgxxmmpmhxm4y.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-035828__02.jpg</strong> (49.52 KB, 下载次数: 0)

下载附件

2023-12-23 04:02 上传

图像到纹理任务的定量对比，本文方法在基线上取得了更显著的改进

<img src="https://img.saraba1st.com/forum/202312/23/040256i98qwugdw3829dlz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-035834__01.jpg</strong> (68.11 KB, 下载次数: 0)

下载附件

2023-12-23 04:02 上传

Paint3D框架中模块的评估，展示了每个组件的有效性，包括粗略阶段、UV重绘和UVHD，通过在粗略阶段整合生成先验和在细化阶段整合无光照先验，本文的完整方法实现了最佳结果

<img src="https://img.saraba1st.com/forum/202312/23/040303lebj986tc6ejz3e7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-040040.jpg</strong> (119.26 KB, 下载次数: 0)

下载附件

2023-12-23 04:03 上传

粗略阶段效果的图示，粗略阶段的缺失可能会导致纹理中的语义混乱

<img src="https://img.saraba1st.com/forum/202312/23/040309qxv8b0wbfv8i2pf3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-035834__02.jpg</strong> (130.96 KB, 下载次数: 0)

下载附件

2023-12-23 04:03 上传

细化阶段效果的可视化，通过细化阶段，生成的纹理是光照自由的

<img src="https://img.saraba1st.com/forum/202312/23/040315xcvfoolbyb7bdb2v.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-035846__01.jpg</strong> (146.31 KB, 下载次数: 0)

下载附件

2023-12-23 04:03 上传

UV重绘效果的示意图，UV重绘可以有效地填补位于投影盲点(例如褶皱裙子的内侧)的纹理空洞

<img src="https://img.saraba1st.com/forum/202312/23/040320fj8rr40i4eyarbjy.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-035846__02.jpg</strong> (127.32 KB, 下载次数: 0)

下载附件

2023-12-23 04:03 上传

UVHD模块的效果图，展示了UVHD增强现有纹理细节的能力，甚至可以在单色区域生成新纹理

<img src="https://img.saraba1st.com/forum/202312/23/040324qi022znznikyz0cq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-035851__01.jpg</strong> (66.59 KB, 下载次数: 0)

下载附件

2023-12-23 04:03 上传

粗略阶段视点数量的评估，视点数量并不是越多越好，因为预训练的2D图像扩散模型可能会产生光照伪影

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1106#       发表于 2023-12-23 19:31

HD-Painter

使用扩散模型进行高分辨率且快速可信的文本引导图像重绘

github项目主页:https://github.com/Picsart-AI-Research/HD-Painter

最近的研究在文本引导的图像重绘方面取得了显著进展，基于文本到图像扩散模型的空前成功，实现了异常逼真和视觉上合理的结果，然而，当前的文本到图像重绘模型仍然有很大的潜在改进空间，特别是在更好地与用户提示对齐和进行高分辨率重绘方面

因此，在本文中，介绍了HD-Painter，一种完全无需训练的方法，可以准确地遵循提示并一致地扩展到高分辨率图像重绘，为此设计了提示注意的内在注意力层(PAIntA/Prompt-Aware Introverted Attention layer)，通过提示信息增强自注意力得分，从而产生更好的文本对齐生成结果

为了进一步提高提示一致性，还引入了重调制权重的注意力分数引导(RASG/Reweighting Attention Score Guidance)机制，将事后比较采样策略(post-hoc sampling strategy)无缝整合到DDIM的通常形式中，以防止分布之外的潜在偏移，此外，HD-Painter还通过引入一种针对重绘的专用超分辨率技术，实现了更大尺度的扩展，可以完成高达2K分辨率的图像中缺失区域的重绘

实验证明，HD-Painter在定性和定量方面都超过了现有的SOTA方法，生成准确度改进达到了61.4％ vs 51.9％(之前的方法)

github项目说明页截图:

<img src="https://img.saraba1st.com/forum/202312/23/193050bg4icxlz9sasa333.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-192951.jpg</strong> (422.96 KB, 下载次数: 0)

下载附件

2023-12-23 19:30 上传

<img src="https://img.saraba1st.com/forum/202312/23/193051e1zgg71ffkz3n0km.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231223-193002.jpg</strong> (755.63 KB, 下载次数: 0)

下载附件

2023-12-23 19:30 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1107#       发表于 2023-12-24 02:53

 本帖最后由 Machinery 于 2023-12-24 02:55 编辑 

PIA

通过文本到图像模型中的插件模块实现您的个性化图像动画器

项目主页:https://pi-animator.github.io/

github项目仓库:https://github.com/open-mmlab/PIA

演示Demo:https://openxlab.org.cn/apps/detail/zhangyiming/PiaPia/

b站视频:https://www.bilibili.com/video/BV12a4y1z7V8

最近的个性化文本到图像(T2I)模型取得了相当大的进展，彻底改变了内容创作的方式，使非专业用户也能够生成具有独特风格的惊人图像，虽然前景良好，但是通过文本将逼真的动作添加到这些个性化图像中，在保留独特风格、高保真细节和实现文本动作控制方面面临着重大挑战

在本文中，提出了PIA，一种个性化图像动画化生成器，它在与条件图像对齐、通过文本实现动作控制以及在没有微调的情况下与各种个性化T2I模型的兼容性方面表现出色

为了实现这些目标，PIA基于一个经过训练有素的基础T2I模型，通过时间对齐层(temporal alignment layers)，可以将任何个性化T2I模型无缝转换为图像动画化模型，PIA的其中一个关键组成部件，条件模块，该模块利用条件帧和帧间相似性(affinity)作为输入，在潜在空间中根据相似性提示(affinity hints)传递外观信息，用于单帧合成，这种设计缓解了与外观相关的图像对齐的挑战，同时允许更加关注与运动相关的指导保持对齐

<img src="https://img.saraba1st.com/forum/202312/24/025220obe7zwtieig4t495.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231224-024728__01.jpg</strong> (553.39 KB, 下载次数: 0)

下载附件

2023-12-24 02:52 上传

给定个性化文本到图像模型生成的详细图像，本文提案的个性化图像动画器(PIA/Personalized Image Animator)根据不同的文本提示以逼真的动作进行动画化，同时保留原本的独特风格和高保真细节

<img src="https://img.saraba1st.com/forum/202312/24/025226bhyg48hmsz38sh3a.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231224-024745__01.jpg</strong> (348.18 KB, 下载次数: 0)

下载附件

2023-12-24 02:52 上传

个性化图像动画器，如(a)所示，PIA由文本到图像模型、经过训练的时间对齐层和负责编码条件图像以及帧间近似的新条件模块(new condition module)组成，具体来说，T2I模型由U-Net块组成，如(b)所示，包括一个Resblock，一个自注意力层和一个交叉注意力层，在训练过程中，条件模块学习利用近似提示(affinity hints)，从条件图像中利用外观信息，促进图像对齐并更加强调与运动相关的对齐

<img src="https://img.saraba1st.com/forum/202312/24/025231wqmcfim2ffzpkf00.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231224-024759__01.jpg</strong> (155.13 KB, 下载次数: 0)

下载附件

2023-12-24 02:52 上传

条件模块的示意图，传统的个性化T2V模型(a)需要同时对齐单帧的外观和运动，带有CM的PIA模型(b)可以借用条件图像的外观信息和近似提示，从而减轻同时对齐外观和运动的挑战，使用颜色和条纹分别表示外观和运动

<img src="https://img.saraba1st.com/forum/202312/24/025237ezbaootbba4j40aj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231224-024806__01.jpg</strong> (95.04 KB, 下载次数: 0)

下载附件

2023-12-24 02:52 上传

AnimateBench的示例，AnimateBench中的图像是通过一组收集的个性化文本到图像模型精心制作而成的，每张图像都有三个精心设计的提示，描述了图像可能在一个短片段内可能发生的动作

<img src="https://img.saraba1st.com/forum/202312/24/025243lm9me0jo6q7emzoo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231224-024819__01.jpg</strong> (660.31 KB, 下载次数: 0)

下载附件

2023-12-24 02:52 上传

<img src="https://img.saraba1st.com/forum/202312/24/025247uv2uvv9v8hb92qch.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231224-024833__01.jpg</strong> (542.83 KB, 下载次数: 0)

下载附件

2023-12-24 02:52 上传

与SOTA方法进行的定性对比，与其他方法相比，PIA展现出了出色的运动可控性和强大的图像对齐能力，具体而言，在第一个用例中，PIA为玩具熊(脚步)生成了“行走”动作，而其他方法只能维持静态帧，显示出运动可控性不足，在第二个用例中，PIA添加了一个新的元素，即火焰，具有逼真的运动效果

<img src="https://img.saraba1st.com/forum/202312/24/025253wl09t4b40iq4qllx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231224-024858__01.jpg</strong> (92.21 KB, 下载次数: 0)

下载附件

2023-12-24 02:52 上传

AnimateBench的定量对比

<img src="https://img.saraba1st.com/forum/202312/24/025257xazj797hr4bdcer5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231224-024910__01.jpg</strong> (333.19 KB, 下载次数: 0)

下载附件

2023-12-24 02:52 上传

文本提示下的运动控制，PIA能够有效地捕捉到文本提示中与运动相关的指导，并在结果中添加逼真的相关运动

<img src="https://img.saraba1st.com/forum/202312/24/025302ngyu35hz4zvxq64s.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231224-024910__02.jpg</strong> (269.81 KB, 下载次数: 0)

下载附件

2023-12-24 02:53 上传

运动幅度可控性，PIA能够让用户通过设置输入的近似信息为不同的值，调整运动的幅度，轻微、中等或大幅度

<img src="https://img.saraba1st.com/forum/202312/24/025307xgevtetnjewvpexe.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231224-024920__01.jpg</strong> (163.41 KB, 下载次数: 0)

下载附件

2023-12-24 02:53 上传

风格转换，PIA能够通过将个性化的文本到图像模型应用于给定的图像，实现生成视频中的风格转换

<img src="https://img.saraba1st.com/forum/202312/24/025312pebbpepzphugppw6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231224-024931__01.jpg</strong> (125.63 KB, 下载次数: 0)

下载附件

2023-12-24 02:53 上传

帧近似的有效性，借助帧近似，PIA能够生成具有更强图像对齐的视频

<img src="https://img.saraba1st.com/forum/202312/24/025318wxqtz2p24r24xvp7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231224-024931__02.jpg</strong> (124.27 KB, 下载次数: 0)

下载附件

2023-12-24 02:53 上传

局限性，当输入图像远离训练数据集域时，PIA很容易生成色彩发生显著变化的视频

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1108#       发表于 2023-12-26 04:19

BrainVis

通过图像重建探索大脑与视觉信号之间的通路

 项目主页:https://brainvis-projectpage.github.io/

github项目仓库:https://github.com/RomGai/BrainVis

分析和重建脑信号中的视觉刺激能够有效推进对人类视觉系统的理解，然而，脑电图信号(EEG signals)是复杂的，包含大量噪音，这导致现有的从脑电图中重建视觉刺激的研究存在重大局限，例如难以将脑电图嵌入与细粒度语义信息对齐，以及严重依赖额外的大型自采集数据集以用于训练

为了应对这些挑战，本文提出了一种新颖的方法，称为BrainVis，首先，将脑电图信号分成各种单元(various units)，并应用自监督方法(self-supervised approach)，以获取脑电图的时域特征(EEG time-domain features)，减轻训练的困难度

此外，还提出了利用频域特征(frequency-domain features)增强脑电图表征(EEG representations)，随后，在CLIP空间中将脑电图的时频嵌入与粗粒度和细粒度语义的插值同时对齐，以突出主要的视觉组成部分(primary visual components)并减少跨模态对齐的难度，最后，采用级联扩散模型(cascaded diffusion models)来重建图像

BrainVis在语义保真重建和生成质量方面优于现有的SOTA水平，另外值得注意的是，本文方法还将训练数据的需求量减小到先前工作的10%
————
框架

<img src="https://img.saraba1st.com/forum/202312/26/041902lxbpkgnn3ox7xgbg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-041805.jpg</strong> (105.28 KB, 下载次数: 0)

下载附件

2023-12-26 04:19 上传

首先，获取给定的脑电信号的时间和频率特征，其中时间编码器利用自监督预训练方法，采用掩码分割(masking segmentation)和潜在重构(latent reconstruction)来获取特征，而频率编码器则利用LSTM与快速傅里叶变换(FFT/Fast Fourier Transform)来提取特征

然后时间和频率编码器与脑电分类器(EEG classifier)同时进行微调，以获取时间-频率双嵌入(time-frequency dual embedding)，接下来，一个对齐网络将脑电时间-频率双嵌入与CLIP空间中的来自于视觉刺激图像的细粒度语义进行对齐(视觉刺激图像标签和其字幕说明的语义插值)

最后，对齐的脑电细粒度嵌入，以及分类结果的粗粒度嵌入，作为级联扩散模型的条件，以用于多级语义视觉重建(multi-level semantic visual reconstruction)
————
结果

以下是视觉刺激重建结果(部分)和基准答案图像(ground truth)，本文方法不仅能够正确地重建类型，而且在一定程度上能够捕捉到其细粒度的语义信息，例如显著的数字、颜色、环境或行为特征

<img src="https://img.saraba1st.com/forum/202312/26/041915rwtz33j3wt3l6yyd.jpg" referrerpolicy="no-referrer">

<strong>ce0f00e7-a5b0-4a7d-b94c-02b53d378daa.jpg</strong> (290.5 KB, 下载次数: 0)

下载附件

2023-12-26 04:19 上传

下面是本文方法和之前的工作之间重建的图像质量对比

<img src="https://img.saraba1st.com/forum/202312/26/041921u9xkf898zvwqviep.jpg" referrerpolicy="no-referrer">

<strong>pic4.jpg</strong> (820.29 KB, 下载次数: 0)

下载附件

2023-12-26 04:19 上传

下面是重建图像与先前工作在同一GT图像上的对比

<img src="https://img.saraba1st.com/forum/202312/26/041933n7araaaawnjjnwi1.jpg" referrerpolicy="no-referrer">

<strong>pic5.jpg</strong> (667.94 KB, 下载次数: 0)

下载附件

2023-12-26 04:19 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1109#       发表于 2023-12-26 04:33

 本帖最后由 Machinery 于 2023-12-26 04:38 编辑 

YAYI2-30B

YAYI 2是中科闻歌研发的新一代开源大型语言模型系列

相关论文:https://arxiv.org/abs/2312.14862

相关博客:https://www.wenge.com/content/details_53_4626.html

github项目仓库:https://github.com/wenge-research/YAYI2

hugface模型权重下载:https://huggingface.co/wenge-research/yayi2-30b

YAYI 2是中科闻歌研发的开源大语言模型，包括Base和Chat版本，参数规模为30B，YAYI2-30B是基于Transformer的大语言模型，采用了2.65万亿Tokens的高质量、多语言语料进行预训练，针对通用和特定领域的应用场景，采用了百万级指令进行微调，同时借助人类反馈强化学习方法，以更好地使模型与人类价值观对齐，本次开源的模型为YAYI2-30B Base模型

相关说明截图:

<img src="https://img.saraba1st.com/forum/202312/26/043305mahm86smu8kk06mm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-043153.jpg</strong> (199.49 KB, 下载次数: 0)

下载附件

2023-12-26 04:33 上传

<img src="https://img.saraba1st.com/forum/202312/26/043305fkgkb3m1ps1z9koq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-043205.jpg</strong> (317.89 KB, 下载次数: 0)

下载附件

2023-12-26 04:33 上传

<img src="https://img.saraba1st.com/forum/202312/26/043305bgtzghexnx3ghkih.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-043226.jpg</strong> (58.13 KB, 下载次数: 0)

下载附件

2023-12-26 04:33 上传

<img src="https://img.saraba1st.com/forum/202312/26/043305jd1efeqrtqe8fjjt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-043236.jpg</strong> (287.51 KB, 下载次数: 0)

下载附件

2023-12-26 04:33 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1110#       发表于 2023-12-26 05:21

meta-prompts

使用元提示(Meta Prompts)驾驭扩散模型解决视觉感知(Visual Perception)任务

github项目主页:https://github.com/fudan-zvg/meta-prompts

视觉模型的生成式预训练问题一直是一个长期存在的难题，目前，文本到图像(T2I)扩散模型展示了在生成与文本输入相匹配的高清晰度图像方面的非凡能力，这一成就得益于它在大规模图像-文本对上进行的预训练

这引发了一个自然的问题:扩散模型能否用于解决视觉感知任务？在本文中，提出了一个简单而有效的方案，利用扩散模型进行视觉感知任务

其中一个关键洞察是引入可学习的嵌入(learnable embeddings/meta-prompts)到预训练的扩散模型中，以提取适合感知任务的特征，元提示的效果有两个方面，首先，作为T2I模型中文本嵌入的直接替代，它可以在特征提取过程中激活与任务相关的特征，其次，它将被用于重新排列提取的特征，以确保模型专注于任务中最相关的特征

此外，还设计了一种循环细化训练策略(recurrent refinement training strategy)，充分利用了扩散模型的特性，从而产生更强大的视觉特征

对各种基准测试的大量实验证明了本文方法的有效性，其中，在NYU depth V2和KITTI的深度估计任务以及CityScapes的语义分割任务上实现了新记录，同时，所提出的方法在ADE20K的语义分割和COCO数据集的姿态估计方面取得了与SOTA方法可竞争的性能，进一步证明了其稳健性和多功能性

<img src="https://img.saraba1st.com/forum/202312/26/052106q3w74ei7g1647ll7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-051718.jpg</strong> (145.83 KB, 下载次数: 0)

下载附件

2023-12-26 05:21 上传

不同提示方法的对比，本文提出的元提示具有简洁的工作流程，不需要额外的标签或预训练模型，并且能够自适应地学习当前感知任务所需的关注区域，以生成相应的激活

<img src="https://img.saraba1st.com/forum/202312/26/052128n3ouoioq847thy04.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-051748__01.jpg</strong> (153.97 KB, 下载次数: 0)

下载附件

2023-12-26 05:21 上传

左侧为总体工作流程，VQVAE编码器Eψ将输入图像编码为潜在空间Z0，Z0的分辨率是原始分辨率的1/8，在t个步骤中对图像特征进行细化，在不同的细化步骤中，去噪UNet共享相同的参数，符号⊙表示点积(点积)

右侧为通过提示引导的特征重排，以一个尺度的特征图为例

<img src="https://img.saraba1st.com/forum/202312/26/052134g78qqzk0da94oj7o.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-051833.jpg</strong> (166.26 KB, 下载次数: 0)

下载附件

2023-12-26 05:21 上传

Cityscapes验证集和测试集的结果，*City表示CityScapes数据集，Mapi表示Mapillary Vistas数据集

<img src="https://img.saraba1st.com/forum/202312/26/052138djulc3jrul3qz7e7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-051850.jpg</strong> (142.75 KB, 下载次数: 0)

下载附件

2023-12-26 05:21 上传

ADE20K验证集的结果

<img src="https://img.saraba1st.com/forum/202312/26/052143yw10prkoee0apvep.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-051911.jpg</strong> (153.43 KB, 下载次数: 0)

下载附件

2023-12-26 05:21 上传

在NYU depth V2和KITTI Eigen分割数据集上进行的深度估计结果，RMSE代表均方根误差(root mean square error)，REL代表绝对相对误差(absolute relative error)，准确度指标为(δi&lt;1.25i，其中i∈1, 2, 3)

<img src="https://img.saraba1st.com/forum/202312/26/052154zcmwcgfuv4ge4fi3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-051925.jpg</strong> (140.33 KB, 下载次数: 0)

下载附件

2023-12-26 05:21 上传

MS-COCO验证集的结果

<img src="https://img.saraba1st.com/forum/202312/26/052202rzcttr3rkt2cm7op.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-051938__01.jpg</strong> (340.27 KB, 下载次数: 0)

下载附件

2023-12-26 05:22 上传

CityScapes语义分割数据集和NYU Deep V2深度估计数据集的消融实验，报告了交并比平均值(mIoU/mean of intersection over union)和均方根误差(RMSE/root mean square error)，默认设置以灰色标记

<img src="https://img.saraba1st.com/forum/202312/26/052207rq9xas8hv1a68kzs.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-051947.jpg</strong> (214.76 KB, 下载次数: 0)

下载附件

2023-12-26 05:22 上传

第一行:语义分割任务中同一图像上不同提示的热图(Heatmaps)，第二行:深度估计任务的不同图像上相同提示的热图

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1111#       发表于 2023-12-26 05:45

Aurora

通过指令调整(Instruction-Tuning)激活Mistral-8x7B稀疏专家混合(Mixture-of-Experts)的中文聊天能力(Chinese chat capability)

项目主页:https://github.com/WangRongsheng/Aurora

现有研究证明，通过利用机器生成的指令跟随数据可以对大型语言模型(LLMs)进行细化，使得这些模型能够展示出令人印象深刻的零样本能力，而无需人工编写指令

在本文中，系统地研究、预处理和整合了三个中文指令跟随数据集以提升Mixtral-8x7B稀疏专家混合模型的中文对话能力，通过在经过精心处理的数据集上进行指令微调，成功构建了新的Mixtral-8x7B稀疏专家混合模型，命名为“Aurora”

为了评估Aurora的性能，使用了三个广泛认可的基准测试:C-Eval、MMLU和CMMLU，实证研究验证了将指令微调应用于Mixtral-8x7B稀疏专家混合模型的有效性，这项工作在对稀疏专家混合模型执行指令微调方面具有开创性，标志着提升该模型架构能力的重大突破

相关模型说明页:

<img src="https://img.saraba1st.com/forum/202312/26/054519sesqkkibq0l0lzim.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-054210.jpg</strong> (343.36 KB, 下载次数: 0)

下载附件

2023-12-26 05:45 上传

<img src="https://img.saraba1st.com/forum/202312/26/054519h2s0f48xfprvopix.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-054226.jpg</strong> (273.37 KB, 下载次数: 0)

下载附件

2023-12-26 05:45 上传

<img src="https://img.saraba1st.com/forum/202312/26/054519uxz3sx22hff9y4y6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-054257.jpg</strong> (99.24 KB, 下载次数: 0)

下载附件

2023-12-26 05:45 上传

<img src="https://img.saraba1st.com/forum/202312/26/054519sz813h3cziehzqh3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-054314.jpg</strong> (476.33 KB, 下载次数: 0)

下载附件

2023-12-26 05:45 上传

<img src="https://img.saraba1st.com/forum/202312/26/054519pl24sysu8822u882.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-054322.jpg</strong> (546.08 KB, 下载次数: 0)

下载附件

2023-12-26 05:45 上传

<img src="https://img.saraba1st.com/forum/202312/26/054519w8knrxwbtmb98a9r.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-054335.jpg</strong> (566.5 KB, 下载次数: 0)

下载附件

2023-12-26 05:45 上传

<img src="https://img.saraba1st.com/forum/202312/26/054519ahydymaqqmkktvky.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-054347.jpg</strong> (227.78 KB, 下载次数: 0)

下载附件

2023-12-26 05:45 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1112#       发表于 2023-12-26 06:03

InternVL

拓展视觉基础模型并对齐通用视觉语言任务

相关论文:https://arxiv.org/abs/2312.14238

github项目主页:https://github.com/OpenGVLab/InternVL

大语言模型(LLMs)的指数增长为多模态AGI系统开辟了许多可能性，然而，视觉和视觉语言基础模型的进展，并没有跟上LLMs的步伐，而这些模型也是多模态AGI的关键要素之一

在这项工作中，设计了一个大规模的视觉语言基础模型(InternVL)，将视觉基础模型的参数规模扩大到60亿，并逐步与大型语言模型进行对齐，使用来自各种来源的网络大规模图像文本数据，该模型可以广泛应用并达成SOTA级视觉感知任务(如图像级别或像素级别识别)、视觉语言任务(如零样本图像/视频分类、零样本图像/视频-文本检索)以及链接到LLMs中，从而创建多模态对话系统

希望本文的研究能为多模态大模型的发展做出贡献

相关项目说明页截图:

<img src="https://img.saraba1st.com/forum/202312/26/060340smyt4kmjzjbukeya.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-060231.jpg</strong> (297.79 KB, 下载次数: 0)

下载附件

2023-12-26 06:03 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1113#       发表于 2023-12-26 07:55

 本帖最后由 Machinery 于 2023-12-26 07:57 编辑 

ZeroShape

基于回归(Regression-based)的零样本形状重建(Zero-shot Shape Reconstruction)

项目主页:https://zixuanh.com/projects/zeroshape.html

github项目主页:https://github.com/zxhuang1698/ZeroShape

本文专注于研究单图像零样本3D形状重建的问题，最近的研究工作通过3D资产的生成式建模学习零样本形状重建，但这些模型在训练和推理时计算成本高昂，相比之下，传统方法解决这个问题是基于回归的，即训练确定性模型(deterministic models)直接回归物体形状(directly regress the object shape)，这种回归方法比生成方法具有更高的计算效率

这引发了一个自然的问题:对于高性能，生成式建模是否是必须的，或者相反，基于回归的方法仍然具备竞争力？为了回答这个问题，设计了一种强大的基于回归的模型，称为ZeroShape

基于该领域的集中(converging)发现以及新颖的见解，还策划构造了一个大型的真实世界评估基准测试，其中包含来自三个不同真实世界3D数据集的对象，这个评估基准比之前的研究使用的量化评估模型更加多样化和数量级更大，旨在减少领域的评估方差，展示了ZeroShape不仅在性能上超越了SOTA方法，而且在计算和数据效率上也表现出显著优势

<img src="https://img.saraba1st.com/forum/202312/26/075434ceguifzfzpfi77g1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-075030__01.jpg</strong> (92.29 KB, 下载次数: 0)

下载附件

2023-12-26 07:54 上传

在零样本3D形状重建方面表现优于现有方法，同时推理时间更快且所需训练数据更少，圆的大小表示用于训练的3D资产数量，最大的圆代表320万，阈值0.05的F-Score是基于Octroc3D、Pix3D、OmniObject3D的平均值

<img src="https://img.saraba1st.com/forum/202312/26/075443p8zifnxqqxqxih8i.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-075049__01.jpg</strong> (284.98 KB, 下载次数: 0)

下载附件

2023-12-26 07:54 上传

根据真实自然场景图像进行ZeroShape重建，本文方法从一组不同对象上的单视图图像生成了详细而准确的对象重建

<img src="https://img.saraba1st.com/forum/202312/26/075448pvhfowgg6uvz0wta.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-075104__01.jpg</strong> (199.59 KB, 下载次数: 0)

下载附件

2023-12-26 07:54 上传

模型的概览图，由三个模块组成:深度和摄影机估计器(depth and camera estimator)、几何反投影单元(geometric unprojection unit)和投影引导形状重建器(projection-guided shape reconstructor)

深度和摄影机估计器使用DPT骨干从输入图像中预测深度和摄影机内参(intrinsics)，几何反投影单元将深度和内参估计转换为规范的3D可见表面，并通过三通道投影映射(three-channel projection map)进行参数化，形状重建器最终通过跨注意力机制从投影映射中提取局部信息，重建完整的占用场(full occupancy field)

<img src="https://img.saraba1st.com/forum/202312/26/075453mx80mamx90mxe99p.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-075127__01.jpg</strong> (111.03 KB, 下载次数: 0)

下载附件

2023-12-26 07:54 上传

内参的影响，将精确的深度图反投影到具有错误内参的3D表面会导致具有错误3D纵横比的倾斜形状

<img src="https://img.saraba1st.com/forum/202312/26/075506wjsjf77sytt1tm79.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-075139__01.jpg</strong> (296.12 KB, 下载次数: 0)

下载附件

2023-12-26 07:55 上传

定性结果，将ZeroShape与其他SOTA方法在本文的标注基准测试上进行了对比(前三列来自Ocrtoc3D，后三列来自OmniObject3D)，本文方法的重建不仅更好地与图像中的可见表面对齐，还能恢复重建对象的可信全局结构

<img src="https://img.saraba1st.com/forum/202312/26/075501bj1zgdb767vvilg3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-075148__01.jpg</strong> (420.18 KB, 下载次数: 0)

下载附件

2023-12-26 07:55 上传

定量对比

<img src="https://img.saraba1st.com/forum/202312/26/075511gitzt9nf2tzhh627.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-075158__01.jpg</strong> (96.7 KB, 下载次数: 0)

下载附件

2023-12-26 07:55 上传

对OmniObject3D进行消融实验，对架构设计选择进行定量分析予以证明:强制性的显式几何推理以及通过估计深度和内参实现反投影是至关重要的

<img src="https://img.saraba1st.com/forum/202312/26/075516rssdn8jv03k3oyzi.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-075203__01.jpg</strong> (173.48 KB, 下载次数: 0)

下载附件

2023-12-26 07:55 上传

内参学习的好处，展示了两个真实图像输入的重建可见表面，可见表面是从估计的深度中反投影得到的，其中使用了固定内参或预测内参，使用固定内参会导致可见物体表面的3D纵横比出现非真实变形(例如，物体看起来被压缩了)

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1114#       发表于 2023-12-26 08:39

DreamDistribution

文本到图像扩散模型的提示分布学习(Prompt Distribution Learning)

项目主页:https://briannlongzhao.github.io/DreamDistribution

github项目仓库:https://github.com/briannlongzhao/DreamDistribution

文本到图像(T2I)扩散模型的普及使得从文本描述中生成高质量的图像成为可能，然而，生成具有参考视觉属性(reference visual attributes)的多样化定制图像仍然具有挑战性

本研究专注于在更抽象的概念(more abstract concept)或分类级别(category level)上个性化T2I扩散模型，通过从一组参考图像中调整共性并创建具有充足变化的新实例，提出了一种解决方案，允许预训练的T2I扩散模型学习一组软提示(soft prompts)，通过从学习的分布中采样提示来生成新的图像，这些提示提供了文本引导的编辑能力，并在控制变化和混合多个分布时提供额外的灵活性

展示了学习到的提示分布对其他任务(如文本到3D)的适应性，最后，通过包含自动评估和人工评估在内的定量分析证明了本文方法的有效性
————
演示

<img src="https://img.saraba1st.com/forum/202312/26/083431xq2ffikzf0mb2ffe.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-083152.jpg</strong> (201.1 KB, 下载次数: 0)

下载附件

2023-12-26 08:34 上传

<img src="https://img.saraba1st.com/forum/202312/26/083431gu2z11ipq2epfpd0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-083228.jpg</strong> (110.55 KB, 下载次数: 0)

下载附件

2023-12-26 08:34 上传

DreamDistribution能够找到参考图像的提示分布，之后便可用于生成新的2D/3D实例，以及进行文本引导编辑等任务
————
方法

<img src="https://img.saraba1st.com/forum/202312/26/083437xccwytcwwzhhae5q.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-083307.jpg</strong> (84.43 KB, 下载次数: 0)

下载附件

2023-12-26 08:34 上传

保留了一组可学习的K个软提示，并在CLIP文本编码器特征空间中建模它们的分布，其中只有提示是可学习的，CLIP编码器和T2I扩散模型都是固定的

使用重参数化技巧(reparameterization trick)从提示分布中进行采样，并通过反向传播更新可学习的提示，训练目标是使生成的图像与参考图像对齐，还引入了一个额外的正交损失(orthogonal loss)，以促进可学习的提示之间的差异化(differentiation)，对于推理，类似地，从文本特征空间中的提示分布中进行采样，以指导预训练的T2I模型生成

对比其他方法

<img src="https://img.saraba1st.com/forum/202312/26/083450gk0w3pqq97a4ma8q.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-083330.jpg</strong> (403.93 KB, 下载次数: 0)

下载附件

2023-12-26 08:34 上传

给定一组训练图像(通常为5-20个，在这里只显示4个)，将生成结果与其他现有方法进行对立，对所有方法都使用Stable Diffusion 2.1 版本，从下方行可以看出，本文方法能够生成更加多样化和连贯的图像
————
多样化的分布内2D生成

<img src="https://img.saraba1st.com/forum/202312/26/083642dm9f69j2699yqdx3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-083500.jpg</strong> (454.01 KB, 下载次数: 0)

下载附件

2023-12-26 08:36 上传

使用参考图像生成图像的更多结果，左列中的图像是参考图像，右列中的图像是生成图像
————
文本引导的分布内2D生成

<img src="https://img.saraba1st.com/forum/202312/26/083713lyczynkozvjomjvl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-083653.jpg</strong> (493.24 KB, 下载次数: 0)

下载附件

2023-12-26 08:37 上传

本文方法的文本可编辑性结果，左栏展示了参考图像的样本，右栏展示了生成的结果以及对应的提示
————
文本转3D生成的应用

<img src="https://img.saraba1st.com/forum/202312/26/083719r1mg6d633mc4ii10.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-083702.jpg</strong> (151.39 KB, 下载次数: 0)

下载附件

2023-12-26 08:37 上传

通过学习参考图像上的提示分布，然后使用MVDream进行推理(无需额外控制的文本)的3D生成结果
————
文本引导编辑的文本转3D生成应用

<img src="https://img.saraba1st.com/forum/202312/26/083738kg4sp979xg15dbyd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-083727.jpg</strong> (145.19 KB, 下载次数: 0)

下载附件

2023-12-26 08:37 上传

通过学习参考图像上的提示分布，然后使用MVDream进行文本引导编辑推理的3D生成结果
————
 提示分布的组合

<img src="https://img.saraba1st.com/forum/202312/26/083759euusvz3kuu3qv4ku.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-083746.jpg</strong> (822.81 KB, 下载次数: 0)

下载附件

2023-12-26 08:37 上传

在两组图像之间进行线性插值来组合提示分布，混合比从左到右线性变化，中间的列显示两组的混合结果
————
提示分布的缩放变化

<img src="https://img.saraba1st.com/forum/202312/26/083855rooqon1ponqoxsn6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-083813__01.jpg</strong> (759.33 KB, 下载次数: 0)

下载附件

2023-12-26 08:38 上传

<img src="https://img.saraba1st.com/forum/202312/26/083855c58txx597gi77t5f.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-083813__02.jpg</strong> (308.06 KB, 下载次数: 0)

下载附件

2023-12-26 08:38 上传

缩放学习提示分布的变量效果，通过将变量乘以标量γ来缩放，图像多样性随着缩放系数γ的增加而增加
————
合成ImageNet

<img src="https://img.saraba1st.com/forum/202312/26/083930u5fl8nl0zll1zodl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-083918.jpg</strong> (676.61 KB, 下载次数: 0)

下载附件

2023-12-26 08:39 上传

使用本文方法生成的训练图像与仅使用类名称作为文本提示生成的图像之间的对比，对于每组有两行，上方行展示本文方法生成的训练图像的样本，下方行显示使用类名称作为文本提示生成的训练图像

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1115#       发表于 2023-12-26 09:42

CLIP-Parrot-Bias

Parrot字幕说明会教受CLIP定位文本，CLIP分数天生具有缺陷

项目主页:https://linyq17.github.io/CLIP-Parrot-Bias/

OpenDataLab数据集:https://openxlab.org.cn/datasets/opendatalab-linyiqi/LAION-text-debiased-100M

github项目主页:https://github.com/opendatalab/CLIP-Parrot-Bias

尽管CLIP在大量视觉语言应用中是基础模型，但CLIP存在严重的文本定位偏差，这种偏差会导致CLIP模型“鹦鹉学舌”般的学习嵌入在图像中的视觉文本，而忽略真实的视觉语义

在最流行的图像文本数据集LAION-2B中，字幕说明也在被密集地“鹦鹉学舌”，嵌入在图像中的文本拼写分析显示，约有50％的图像嵌入了视觉文本内容，而90％的字幕说明或多或少地包括了视觉文本

基于这样的观察，彻底检查了不同版本的CLIP模型，并验证了视觉文本是否是衡量这些模型中LAION风格图像文本相似性的主要因素，为了检查这些鹦鹉学舌的字幕说明是否塑造了文本定位偏差，使用不同于鹦鹉学舌字幕说明为导向的标准，策划构造了一系列基于LAION子集的CLIP模型进行训练

结果表明，使用鹦鹉学舌字幕说明进行训练很容易塑造这种偏差，这会损害CLIP模型中预期的视觉语言表征学习，这表明迫切需要重新审视CLIP-like模型的设计，或者基于CLIP评分重新过滤构建现有图像文本数据集的策划流程
————

<img src="https://img.saraba1st.com/forum/202312/26/093916qithtf424jejcfte.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-090605__01.jpg</strong> (287.47 KB, 下载次数: 0)

下载附件

2023-12-26 09:39 上传

<img src="https://img.saraba1st.com/forum/202312/26/093916vll0019llz7gf4oz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-091251__01.jpg</strong> (158.96 KB, 下载次数: 0)

下载附件

2023-12-26 09:39 上传

<img src="https://img.saraba1st.com/forum/202312/26/093916i95f5t753mm5t8b7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-091138__01.jpg</strong> (118.72 KB, 下载次数: 0)

下载附件

2023-12-26 09:39 上传

————
相关详情

<img src="https://img.saraba1st.com/forum/202312/26/094056c3kkqw8rzjlukqok.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-094020.jpg</strong> (476.17 KB, 下载次数: 0)

下载附件

2023-12-26 09:40 上传

<img src="https://img.saraba1st.com/forum/202312/26/094056mbvu262y22lbjsbs.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-094033.jpg</strong> (287.99 KB, 下载次数: 0)

下载附件

2023-12-26 09:40 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  革萌  
##### 1116#       发表于 2023-12-26 20:46

求问一下有没有什么抽出网页主要内容的大模型

就门户网站的html进去，抽出标题和文章文本的内容出来

*****

####  Machinery  
##### 1117#       发表于 2023-12-26 20:49

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63448895&amp;ptid=2126390" target="_blank">革萌 发表于 2023-12-26 20:46</a>
求问一下有没有什么抽出网页主要内容的大模型

就门户网站的html进去，抽出标题和文章文本的内容出来 ...</blockquote>
这个一般的LLM都能做，不过有的网页比较长的话可能得选长上下文LLM

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1118#       发表于 2023-12-26 20:53

VCoder

多模态大型语言模型的泛用(Versatile Vision Encoders)视觉编码器

github项目主页:https://github.com/SHI-Labs/VCoder

人类具有视觉感知的非凡技能，即看到并理解所见的能力，得以帮助他们理解视觉世界并进行推理，多模态大语言模型(MLLM)最近在视觉语言任务上取得了令人印象深刻的表现，从视觉问答、图像字幕说明、到视觉推理和图像生成

然而，当要求MLLM系统在给定图像中识别或计数(感知)实体时，现有系统存在失败的情况，为了迈向准确的用于感知和推理MLLM系统，提出了为多模态LLMs所用的泛用视觉编码器(VCoder/Versatile vision enCoders)作为感知的眼睛

首先，通过向VCoder提供感知模态(如分割或深度图)，提高了MLLM的感知能力，其次，利用COCO中的图像和现成的视觉感知模型的输出，创造了用于在对象感知任务上训练和评估MLLM上的COCO分割文本(COST/COCO Segmentation Text)数据集，第三，引入了一些评估MLLM对象感知能力的指标，这些指标在COST数据集上进行评估，最后，提供了大量的实验证据，证明了VCoder在对象级别感知能力上相较于现有的多模态LLMs(包括GPT-4V)的改进，数据集、代码和模型将开源以促进研究

<img src="https://img.saraba1st.com/forum/202312/26/204931npppro737v1l1y7x.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-204409__01.jpg</strong> (430.16 KB, 下载次数: 0)

下载附件

2023-12-26 20:49 上传

当提示GPT-4V描述复杂视觉场景时，其能够给出令人印象深刻的回答，但是，它在同一场景中进行简单的计数任务时却失败了，与之相比，VCoder则能够准确地计算出人数

<img src="https://img.saraba1st.com/forum/202312/26/204936sn1lwmz62uuzwqou.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-204430__01.jpg</strong> (576.62 KB, 下载次数: 0)

下载附件

2023-12-26 20:49 上传

MLLMs对物体进行计数和识别

如第一列所示，GPT-4V和LLaVA-1.5在计数人数方面都失败了，此外，LLaVA-1.5错过了背景实体，比如窗户、墙壁等，并且产生了手提包在场的幻觉，除了椅子外，VCoder可以准确预测人数和其他背景实体，类似地，在第二列中，GPT-4V和LLaVA-1.5在计数椅子方面也失败了，而VCoder则与Oracle(预示)的性能相匹配，值得注意的是，所有MLLMs在第三列中对于非杂乱图像的物体感知都很准确，只有LLaVA-1.5在计数领带方面失败了，如第四列所示，VCoder也可以准确执行一般的问答任务，将OneFormer视为物体感知的Oracle

红色文本表示计数错误；粉色文本表示幻觉；蓝色文本表示正确的物体感知

<img src="https://img.saraba1st.com/forum/202312/26/204945hz1ssfyk1y3hhzdq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-204444__01.jpg</strong> (572.74 KB, 下载次数: 0)

下载附件

2023-12-26 20:49 上传

组织COST数据集的方式，将来自COCO数据集的图像、来自GPT-4的问题以及来自OneFormer的分割输出以问答形式结合起来，用于训练和评估在物体识别任务上的多模态语言模型，还通过加入来自DINOv2和DPT的深度图输出，将COST扩展到了物体顺序感知任务，通过类似地加入其他模态(例如关键点图等)，COST可以进一步扩展到更多的物体级任务中

<img src="https://img.saraba1st.com/forum/202312/26/205053s8jhhgbrnmvm2prv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-204456__01.jpg</strong> (313.44 KB, 下载次数: 0)

下载附件

2023-12-26 20:50 上传

使用VCoder对多模态LLMs进行准确物体感知的适配调整

(a)将VCoder作为适配器添加到LLaVA-1.5中，并将感知模态作为额外的控制输入用于提高物体感知性能，在训练过程中，冻结LLaVA-1.5的组件(ImCoder、MLP和LLM)，以保留原始的推理性能

(b)使用深度图和分割图作为VCoder的控制输入，用于物体顺序感知任务

<img src="https://img.saraba1st.com/forum/202312/26/205325q1yfpzlyzer11kb7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-204508__01.jpg</strong> (178.01 KB, 下载次数: 0)

下载附件

2023-12-26 20:53 上传

目标识别的评估指标，将基准答案和预测中的目标数量进行比较，以计算计数分数(count score)和幻觉分数(hallucination score)

<img src="https://img.saraba1st.com/forum/202312/26/205330b5z4bapowzymbc6l.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-204521__01.jpg</strong> (435.41 KB, 下载次数: 0)

下载附件

2023-12-26 20:53 上传

在对象识别的COST验证数据集上与基线多模态LLM进行了对比

将VCoder与现有的现成基线MLLM进行了对比:包含MiniGPT-4、InstructBLIP、LLaVA-1.5和CogVLM

还在COST数据集上训练了三种不同的LLaVA-1.5变体: COST IT将COST训练数据与指令微调数据混合; Soft-Prompted使用一组可学习的Token; 而ImCoder使用RGB图像作为控制输入

VCoder适配的LLaVA-1.5在所有三个对象感知任务中表现最好，⟨·⟩表示输入Token给LLM，seg表示分割图，img表示RGB图像，prompt表示可学习提示，query表示用户问题

还使用OpenAI发布的公开付费API评估了GPT-4V在COST数据集上的性能，VCoder适配的LLaVA-1.5在所有MLLM中表现出了最佳的对象识别性能

<img src="https://img.saraba1st.com/forum/202312/26/205336hl1s9didiqiujqsb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-204533__01.jpg</strong> (70.96 KB, 下载次数: 0)

下载附件

2023-12-26 20:53 上传

物体顺序感知性能，VCoder LLaVA-1.5在控制输入的使用和在COST数据集上的训练上明显优于LLaVA-1.5

<img src="https://img.saraba1st.com/forum/202312/26/205343khnlxrbblhru2yq1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231226-204542__01.jpg</strong> (436.15 KB, 下载次数: 0)

下载附件

2023-12-26 20:53 上传

失败案例，当输入的分割掩码(控制输入)不准确时，VCoder返回了不准确的错误响应

—— 来自 [S1Fun](https://s1fun.koalcat.com)

*****

####  革萌  
##### 1119#       发表于 2023-12-26 20:59

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63448924&amp;ptid=2126390" target="_blank">Machinery 发表于 2023-12-26 20:49</a>

这个一般的LLM都能做，不过有的网页比较长的话可能得选长上下文LLM

—— 来自 S1Fun ...</blockquote>
类似我对着gpt写个prompt这样就行么？

*****

####  Machinery  
##### 1120#       发表于 2023-12-26 21:00

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63449029&amp;ptid=2126390" target="_blank">革萌 发表于 2023-12-26 20:59</a>
类似我对着gpt写个prompt这样就行么？</blockquote>
是的，算是非常简单的任务<img src="https://static.saraba1st.com/image/smiley/face2017/037.png" referrerpolicy="no-referrer">

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  革萌  
##### 1121#       发表于 2023-12-26 21:25

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63449038&amp;ptid=2126390" target="_blank">Machinery 发表于 2023-12-26 21:00</a>

是的，算是非常简单的任务

—— 来自 S1Fun</blockquote>
看了一下光是当前的s1页面的html代码就几万个token了

这个有什么本地的能联网的LLM可以做这个吗？

*****

####  Machinery  
##### 1122#       发表于 2023-12-26 21:26

 本帖最后由 Machinery 于 2023-12-26 21:29 编辑 
<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63449245&amp;ptid=2126390" target="_blank">革萌 发表于 2023-12-26 21:25</a>
看了一下光是当前的s1页面的html代码就几万个token了

这个有什么本地的能联网的LLM可以做这个吗？ ...</blockquote>
这个长度需求就算有跑起来大概率显存也不够用<img src="https://static.saraba1st.com/image/smiley/face2017/001.png" referrerpolicy="no-referrer">除非你愿意截断，或者换个方法，用1058楼的vary直接做图像截图重建

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  革萌  
##### 1123#       发表于 2023-12-26 21:41

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63449263&amp;ptid=2126390" target="_blank">Machinery 发表于 2023-12-26 21:26</a>

这个长度需求就算有跑起来大概率显存也不够用除非你愿意截断，或者换个方法，用1058楼的vary直接 ...</blockquote>
图像重建有点抽象了。但是可以在网页上复制文字内容，然后拿给gpt就可以了


*****

####  诚司  
##### 1124#       发表于 2023-12-26 21:46

 本帖最后由 诚司 于 2023-12-26 21:48 编辑 
<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63449245&amp;ptid=2126390" target="_blank">革萌 发表于 2023-12-26 21:25</a>

看了一下光是当前的s1页面的html代码就几万个token了

这个有什么本地的能联网的LLM可以做这个吗？ ...</blockquote>
我做的类似的事，最后是用浏览器打印成pdf（可以复制文字的那种pdf），然后用paddleocr的pdf版面恢复（paddleocr里设置ocr=false，通过pdf解析而不是ocr进行版面恢复），在大致保持版面的情况下提出文字，加点版面标记再喂给大模型。当然这不一定符合你需求，因为网页打印pdf，最终版面还是和原来有挺大差别……

解决方案不一定有用，但是我知道哪些东西没用：

1.打印成图片，然后用paddleocr直接恢复版面（而不是用可以复制文字的pdf通过paddleocr进行解析）不怎么好使，比如英文第一句话是for example，paddleocr开启ocr模式可能直接识别成or example

2.直接几万token喂给大模型，虽然Baichuan有192K的，Qwen也能支持32K，但是长文档本身不靠谱，html这种树结构的长文档更不靠谱

3.多模态大模型直接喂图片最不靠谱，比上面两个都不靠谱，中文用的QwenVL，他论文里就有ocr示例，本来我想让QwenVL直接识别pdf页眉页脚，然后去掉水印和页眉页脚再ocr，结果确实可以无视水印去掉页眉页脚，但是ocr本身性能不咋地，中文缺字<img src="https://static.saraba1st.com/image/smiley/face2017/067.png" referrerpolicy="no-referrer">

目前看下来我的需求也就是打印成可解析的pdf然后版面恢复最靠谱


*****

####  Machinery  
##### 1125#       发表于 2023-12-26 22:02

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63449384&amp;ptid=2126390" target="_blank">革萌 发表于 2023-12-26 21:41</a>
图像重建有点抽象了。但是可以在网页上复制文字内容，然后拿给gpt就可以了 ...</blockquote>
上边那个打印成pdf的方法确实不错，ocr则取决于精度，不是专用大模型效果确实不行，说白了还是html直接喂太糙了，如果预处理一下会好很多<img src="https://static.saraba1st.com/image/smiley/face2017/053.png" referrerpolicy="no-referrer">

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  诚司  
##### 1126#       发表于 2023-12-27 20:54

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63449384&amp;ptid=2126390" target="_blank">革萌 发表于 2023-12-26 21:41</a>

图像重建有点抽象了。但是可以在网页上复制文字内容，然后拿给gpt就可以了 ...</blockquote>
啊，我今天又试了试，发现我对Qwen-VL的拉胯印象是建立在我在单位离线部署的开源Qwen-VL-Chat版本上的……

试了试web版的Qwen VL plus，现在的能力已经完全堪用了，我用“请输出图片中的正文部分，并去掉页眉页脚等信息”，这样的prompt，大部分pdf截的图都没有太大的问题……

但是没开源…………


*****

####  Machinery  
##### 1127#       发表于 2023-12-28 00:55

SOLAR 10.7B

通过简单而有效的深度扩展(Depth Up-Scaling)来扩展大型语言模型

hugface权重下载:https://huggingface.co/upstage/SOLAR-10.7B-v1.0

hugface指令微调权重下载:https://huggingface.co/upstage/SOLAR-10.7B-Instruct-v1.0

本文介绍了一种称为深度拓展(DUS/Depth Up-Scaling)新技术，以一种简单而高效的方式对基本大型语言模型(LLMs)进行拓展，与专家混合(MoE/mixture-of-experts)不同，DUS不需要复杂的训练和推理改进，通过使用DUS，构建了一个具有107亿参数的大型语言模型，名为SOLAR 10.7B，在各种自然语言处理(NLP)任务中展示了优越的性能

对比评估显示，SOLAR 10.7B优于现有的开源预训练LLMs，例如Llama 2和Mistral 7B，还提供了经过精心微调以适应指令跟随能力的SOLAR 10.7B-Instruct变体版本，超越了Mixtral-8x7B，SOLAR 10.7B在Apache 2.0许可下授权公开使用，促进了LLM领域的广泛可访问和应用

<img src="https://img.saraba1st.com/forum/202312/28/005448xhuujstpqe07bjue.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-005336__01.jpg</strong> (104.27 KB, 下载次数: 0)

下载附件

2023-12-28 00:54 上传

使用具有32层的基础模型进行深度拓展，虽然本文使用了Llama2架构，但其他Transformer架构也能兼容深度拓展技术，在基础模型的32层中使用了24层的预训练权重，这致使深度拓展模型的所有48层都具有预训练权重

<img src="https://img.saraba1st.com/forum/202312/28/005453auq4o8joqpwpnej8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-005354__01.jpg</strong> (137.98 KB, 下载次数: 0)

下载附件

2023-12-28 00:54 上传

分别用于指令和对齐调整阶段的训练数据集，对于指令调整过程，使用了Alpaca-GPT4、OpenOrca和Synth. Math-Instruct数据集，而对于对齐调整，使用了Orca DPO Pairs、Ultrafeedback Cleaned和Synth. Math-Alignment数据集

“Total # Samples”表示整个数据集中的样本总数
“Maximum # Samples Used”表示实际使用于训练的样本的最大数量，可能低于给定数据集中的样本总数
“Open Source”表示数据集是否开源

<img src="https://img.saraba1st.com/forum/202312/28/005458az6oecx6r6vs5cop.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-005401__01.jpg</strong> (362.59 KB, 下载次数: 0)

下载附件

2023-12-28 00:54 上传

SOLAR 10.7B和SOLAR 10.7B-Instruct以及其他top-performing模型的评估结果

报告了提到的六个任务的分数，以及H6分数(六个任务的平均值)，还报告了模型的大小，以十亿参数为单位，类型表示模型的训练阶段(预训练，指导调整，对齐调整)

基于SOLAR 10.7B的模型以紫色标示，H6和各个任务的最佳分数以粗体显示

<img src="https://img.saraba1st.com/forum/202312/28/005508cj2b5djdkopjg1qd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-005211.jpg</strong> (263.13 KB, 下载次数: 0)

下载附件

2023-12-28 00:55 上传

<img src="https://img.saraba1st.com/forum/202312/28/005508fl69qvqx7x07yv5z.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-005232.jpg</strong> (164.14 KB, 下载次数: 0)

下载附件

2023-12-28 00:55 上传

消融实验与结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1128#       发表于 2023-12-28 01:32

Mach

在数分钟内生成高质量的文本到3D角色

项目主页:https://human3daigc.github.io/MACH/

github项目仓库:https://github.com/Human3DAIGC/Make-A-Character

随着AI代理者和Metaverse的出现，定制化的富有表现力的3D角色需求日益增长，但使用传统计算机图形工具创造3D角色是一项复杂而耗时的任务

为了解决这些挑战，本文提出了名为Make-A-Character(Mach)的用户友好框架，以用于根据文本描述创造逼真的3D化身，该框架利用大型语言和视觉模型的能力进行文本意图理解和中间图像生成，然后通过一系列以人类导向的视觉感知和3D生成模块

本系统为用户提供了一种直观的方法，可以在2分钟内创造可控、逼真、完整的3D角色，以满足用户的期望，同时还可以与现有的CG工作流程轻松集成，实现动态表现力

<img src="https://img.saraba1st.com/forum/202312/28/013035sg7g0qqpycgcgpqo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-012500__01.jpg</strong> (375.61 KB, 下载次数: 0)

下载附件

2023-12-28 01:30 上传

Mach系统可以根据文本提示创造高度详细和多样化的3D化身，展示这些角色的多样性，以及通过各种面部表情来表达动态能力

<img src="https://img.saraba1st.com/forum/202312/28/013041be9vsvoyoooy6yoz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-012513__01.jpg</strong> (175.38 KB, 下载次数: 0)

下载附件

2023-12-28 01:30 上传

该框架利用大型语言模型提取各种面部属性(例如脸型、眼睛形状、嘴巴形状、发型和颜色、眼镜类型等)，然后将这些语义属性映射到对应的视觉线索(visual clues)，从而指导Stable Diffusion和ControlNet生成参考肖像，再通过一系列2D面部解析和3D生成模块，生成的目标面部的网格和纹理，与其他匹配的配饰一起组合，参数化表征使生成的3D化身更容易动画化

<img src="https://img.saraba1st.com/forum/202312/28/013046a8drsltlqlz3sirq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-012524__01.jpg</strong> (91.12 KB, 下载次数: 0)

下载附件

2023-12-28 01:30 上传

发现仅仅通过文本提示使用Stable Diffusion模型生成相应的详细面部属性是具有挑战性的，这是因为缺乏全面的面部标注和对应的图像对，为了解决这个问题，首先利用大型语言模型来提取属性，并将它们与低级视觉线索(如姿态和边缘图)进行对齐，然后这些视觉线索通过控ControlNet引导文本到图像生成过程，增强模型准确渲染面部细节的能力

<img src="https://img.saraba1st.com/forum/202312/28/013052exzfn1i4uppt3un0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-012534__01.jpg</strong> (352.92 KB, 下载次数: 0)

下载附件

2023-12-28 01:30 上传

本文所用到的多视图光台设备，专为捕获头部和身体的高分辨率3D扫描设计

<img src="https://img.saraba1st.com/forum/202312/28/013057e82832onitttnm86.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-012534__02.jpg</strong> (50.61 KB, 下载次数: 0)

下载附件

2023-12-28 01:30 上传

FaceScape数据集上的重投影错误

<img src="https://img.saraba1st.com/forum/202312/28/013102ionpk73przje33cp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-012544__01.jpg</strong> (179.42 KB, 下载次数: 0)

下载附件

2023-12-28 01:31 上传

传统的68个landmarks、98个landmarks、以及本文用到的431个landmarks，传统的landmarks在表面上是稀疏的，相比之下，本文的431个landmark密集的覆盖整个头部

<img src="https://img.saraba1st.com/forum/202312/28/013107fy1xdcc184q11q98.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-012554__01.jpg</strong> (240.14 KB, 下载次数: 0)

下载附件

2023-12-28 01:31 上传

在几何生成的过程中，在密集的面部landmarks和参考图像的指导下优化摄影机参数和三平面映射，每个顶点的位置根据其对应的UV坐标被编码到三平面映射中

<img src="https://img.saraba1st.com/forum/202312/28/013116cl4fvn7iulxlzd6l.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-012607__01.jpg</strong> (95.62 KB, 下载次数: 0)

下载附件

2023-12-28 01:31 上传

应用了多分辨率策略，利用可微渲染方法，获得了详细且连贯的纹理贴图，分辨率层次结构定义如下:[32, 128, 512, 1024]

<img src="https://img.saraba1st.com/forum/202312/28/013222jiu8u4xusfhfku74.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-012626__01__01.jpg</strong> (150.81 KB, 下载次数: 0)

下载附件

2023-12-28 01:32 上传

数据采集​​和处理工作流程

<img src="https://img.saraba1st.com/forum/202312/28/013229ekhhk9enynn5d33f.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-012626__01__02.jpg</strong> (56.06 KB, 下载次数: 0)

下载附件

2023-12-28 01:32 上传

提案的纹理校正和补完工作流程

<img src="https://img.saraba1st.com/forum/202312/28/013236udrhcckl8l9cr2l2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-012636__01.jpg</strong> (76.09 KB, 下载次数: 0)

下载附件

2023-12-28 01:32 上传

发型生成工作流程

<img src="https://img.saraba1st.com/forum/202312/28/013240x7tkwj4jnozk4wkk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-012643__01.jpg</strong> (207.5 KB, 下载次数: 0)

下载附件

2023-12-28 01:32 上传

基于股丝的发型生成，使用SD模型生成的发型图像引导

<img src="https://img.saraba1st.com/forum/202312/28/013245li2rmicrp5mv72f6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-012956__01.jpg</strong> (149.02 KB, 下载次数: 0)

下载附件

2023-12-28 01:32 上传

采用面部控制系统进行动态表情

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1129#       发表于 2023-12-28 02:17

RoleEval

大型语言模型的双语角色评估基准(Bilingual Role Evaluation Benchmark)

github项目主页:https://github.com/Magnetic2014/RoleEval

大型语言模型(LLM)的快速演变需要有效的基准测试来评估其角色(role)知识，这对于与现实世界建立连接和提供更沉浸式的互动至关重要

本文介绍了RoleEval，一个用于评估角色知识的双语基准测试，旨在评估其记忆、利用和推理的能力，RoleEval包括RoleEval-Global(包括国际知名角色)和RoleEval-Chinese(包括中国受欢迎的角色)两种分类，提供了6000个中英文平行的多项选择题，涵盖了来自名人、动画、漫画、电影、电视剧、游戏和小说等各个领域的300个富有影响力的真实人物和虚构角色

这些问题涵盖了基本知识(basic knowledge)和多跳推理能力(multi-hop reasoning)，旨在系统地探索角色的个人信息、关系、能力和经历等各个方面，为了保持严格标准，采用了自动和人工验证相结合的混合质量检查过程，确保问题多样、具有挑战性和判别性

在各种开源和专有的大型语言模型上对RoleEval进行了广泛评估，包括零样本和少样本设置，揭示了富有灼见的发现，值得注意的是，虽然GPT-4在RoleEval-Global上表现优于其他模型，但中文LLM在RoleEval-Chinese上表现出色，突显了显著的知识分布差异，在此期望RoleEval能够有效凸显在各种语言和文化环境中评估基础模型的角色知识的重要性

<img src="https://img.saraba1st.com/forum/202312/28/021711f76gfs6r66173777.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-021325__01.jpg</strong> (212.04 KB, 下载次数: 0)

下载附件

2023-12-28 02:17 上传

RoleEval包括不同类型的角色、知识、推理、问题形式、影响和语言

<img src="https://img.saraba1st.com/forum/202312/28/021717lszm6ljhhmztbw0m.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-021338__01.jpg</strong> (69.97 KB, 下载次数: 0)

下载附件

2023-12-28 02:17 上传

RoleEval的统计信息

<img src="https://img.saraba1st.com/forum/202312/28/021747ql32r2hu58uluulr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-021354__01.jpg</strong> (185.27 KB, 下载次数: 0)

下载附件

2023-12-28 02:17 上传

RoleEval的少样本提示示例，为了清晰起见，英文翻译位于相应的中文文本之后

<img src="https://img.saraba1st.com/forum/202312/28/021754c3ziqqwdyj60iqzg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-021411__01.jpg</strong> (173.57 KB, 下载次数: 0)

下载附件

2023-12-28 02:17 上传

在实验中评估的模型细节，为了简单起见，只列出了“模型大小”栏中评估模型的大小

<img src="https://img.saraba1st.com/forum/202312/28/021759ag47ulpug7pgpriv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-021435__01.jpg</strong> (402.81 KB, 下载次数: 0)

下载附件

2023-12-28 02:17 上传

在RoleEval (zh)上的五种类别的五样本结果:celebrities (CE), anime and comics (AC), movie and TV series (MT), games (GA), and fiction (FI)

<img src="https://img.saraba1st.com/forum/202312/28/021805cnjjjr7np1iih0p0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-021444__01.jpg</strong> (402.47 KB, 下载次数: 0)

下载附件

2023-12-28 02:18 上传

在RoleEval (en)上的五种类别的五样本结果:celebrities (CE), anime and comics (AC), movie and TV series (MT), games (GA), and fiction (FI)

<img src="https://img.saraba1st.com/forum/202312/28/021809pye5bidvel2zb2db.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-021452__01.jpg</strong> (112.05 KB, 下载次数: 0)

下载附件

2023-12-28 02:18 上传

RoleEval-Global上的参数缩放法则

<img src="https://img.saraba1st.com/forum/202312/28/021814wn444nljzubn4x44.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-021500__01.jpg</strong> (111.89 KB, 下载次数: 0)

下载附件

2023-12-28 02:18 上传

RoleEval-Global上的Token缩放法则

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1130#       发表于 2023-12-28 03:09

 本帖最后由 Machinery 于 2023-12-28 03:10 编辑 

MultiRankIt

使用物理世界搜索引擎识别日常物体的排列学习方法(Learning-To-Rank Approach)

github项目主页:https://github.com/keio-smilab23/MultiRankIt

家庭服务机器人为满足日常护理和支援需求提供了解决方案，一种将自动化和操作者介入相结合的人在回路的方法被认为是在社会中使用它们的现实方法，因此，本文关注的是在人在回路设置中从用户的开放词汇指令中检索目标物体的任务，并将其定义为学习排列物理物体(LTRPO/learning-to-rank physical objects)任务

例如，给定指令“Please go to the dining room which has a round table. Pick up the bottle on it”，模型需要输出一个排序列表，操作者/用户可以从中选择目标物体

在本文中，提出了一种名为MultiRankIt的新方法，用于LTRPO任务，MultiRankIt引入了跨模态名词短语编码器(Crossmodal Noun Phrase Encoder)，以建模包含指代表达的短语与目标边界框之间的关系，以及跨模态区域特征编码器(Crossmodal Region Feature Encoder)，以建模目标物体与其周围多个图像的关系

此外，还为LTRPO任务构建了一个新的数据集，其中包含伴随着各种目标物体的复杂指代表达指令和真实室内环境图像，在数据集上验证了本文模型，并在平均倒数排名(mean reciprocal rank)和recall@k(recall@k)方面优于基线方法

此外，还在标准化的家庭环境中进行了物理实验，其中家庭服务机器人根据用户的指令在人在回路设置中检索日常物品，实验结果表明，物体检索的成功率达到了80%

<img src="https://img.saraba1st.com/forum/202312/28/030853oa884l8fh8ieh888.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-030446__01.jpg</strong> (165.23 KB, 下载次数: 0)

下载附件

2023-12-28 03:08 上传

LTRPO任务的典型场景，输入是指令，输出是目标对象的排序列表

<img src="https://img.saraba1st.com/forum/202312/28/030859btj6dprt2m0llxmh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-030515__01.jpg</strong> (517.97 KB, 下载次数: 0)

下载附件

2023-12-28 03:08 上传

提出的方法框架，MultiRankIt由跨模态名词短语编码器和跨模态区域特征编码器组成，“FFN”和“Sim”分别表示前馈网络和余弦相似度

<img src="https://img.saraba1st.com/forum/202312/28/030903ihxa6hz6xa9lh90z.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-030529__01.jpg</strong> (399.23 KB, 下载次数: 0)

下载附件

2023-12-28 03:09 上传

验证集的定量对比，最好的分数以粗体显示

<img src="https://img.saraba1st.com/forum/202312/28/030907nss6p4gs74a7llvw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-030546__01.jpg</strong> (419.1 KB, 下载次数: 0)

下载附件

2023-12-28 03:09 上传

定性结果，最上面的图像显示了基准答案图像，其他图像显示了top-3的图像，黄色边框区域和绿色虚线区域分别代表xt和除xt之外的上下文对象

<img src="https://img.saraba1st.com/forum/202312/28/030913wnefae6tg4ckwgg7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-030546__02.jpg</strong> (79.23 KB, 下载次数: 0)

下载附件

2023-12-28 03:09 上传

失败的样本，最左边的图像显示了基准答案目标图像，其他图像显示了top-3的图像，该模型未能成功检索位于一本打开的书附近的画像

<img src="https://img.saraba1st.com/forum/202312/28/030917gjz6ob9al9bbtjjv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-030554__01.jpg</strong> (224.21 KB, 下载次数: 0)

下载附件

2023-12-28 03:09 上传

错误分析与，(a)实验环境中的DSR平台和(b)物理实验中使用的YCB物体

<img src="https://img.saraba1st.com/forum/202312/28/030921ic6d09sxh194c494.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-030559__01.jpg</strong> (29.46 KB, 下载次数: 0)

下载附件

2023-12-28 03:09 上传

物理实验中的任务成功率

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1131#       发表于 2023-12-28 03:30

YAYI-UIE

雅意信息抽取统一大模型 (YAYI-UIE)

github项目主页:https://github.com/wenge-research/YAYI-UIE

雅意信息抽取统一大模型(YAYI-UIE)在百万级人工构造的高质量信息抽取数据上进行指令微调，统一训练信息抽取任务包括命名实体识别(NER)，关系抽取(RE)和事件抽取(EE)，实现通用、安全、金融、生物、医疗、商业、个人、车辆、电影、工业、餐厅、科学等场景下结构化抽取

信息抽取任务的困难在于处理任务特定的标签方案(task-specific label schemas)和异构的数据结构，最近的研究提出了基于大型语言模型的方法，以统一建模不同的信息抽取任务，然而，这些现有方法在处理英语以外的中文语言的信息抽取能力方面存在不足

在本文中，提出了一种用于通用信息抽取的端到端聊天增强指令调整框架(YAYI-UIE)，以同时支持中文和英文，具体而言，利用对话数据和信息抽取数据联合增强信息抽取性能

实验结果表明，提出的框架在中文数据集上实现了SOTA性能，同时在监督设置和零样本设置下，在英文数据集上也实现了可比的性能

相关项目说明截图:

<img src="https://img.saraba1st.com/forum/202312/28/033034zk0mqiziviiks1x6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-032936.jpg</strong> (209.28 KB, 下载次数: 0)

下载附件

2023-12-28 03:30 上传

<img src="https://img.saraba1st.com/forum/202312/28/033034jiiazioppopclxfa.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-032944.jpg</strong> (196.51 KB, 下载次数: 0)

下载附件

2023-12-28 03:30 上传

<img src="https://img.saraba1st.com/forum/202312/28/033034yeahyru46u2yehzb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-032956.jpg</strong> (267.76 KB, 下载次数: 0)

下载附件

2023-12-28 03:30 上传

<img src="https://img.saraba1st.com/forum/202312/28/033034wvh9tkrxt96xs9fy.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231228-033006.jpg</strong> (145.83 KB, 下载次数: 0)

下载附件

2023-12-28 03:30 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1132#       发表于 2023-12-29 15:19

TinyGPT-V

通过小型骨干网络运行高效的多模态大型语言模型

github项目主页:https://github.com/DLYuanGod/TinyGPT-V

hugface权重下载:https://huggingface.co/Tyrannosaurus/TinyGPT-V

在长足发展的多模态学习时代中，如GPT-4V等多模态大型语言模型(MLLMs)在连接语言和视觉元素方面取得了显著进展，然而，闭源性质和较大的计算需求对于普遍的使用和修改而言存在挑战，这就是为何开源MLLMs，如LLaVA和MiniGPT-4相关模型到来的原因，它们在各种任务上取得了突破性的成就，尽管取得了这些成就，计算效率仍然是一个暂未解决的问题，像LLaVA-v1.5-13B这样的模型，依然需要大量的资源

为了解决这些问题，本文引入了TinyGPT-V，一种将出色性能与普世的计算容量相结合的新型模型，它的训练仅需要一个24G的GPU，同时推理只需要一个8G的GPU或CPU，TinyGPT-V基于Phi-2构建，将一个有效的语言骨干与来自BLIP-2或CLIP的预训练视觉模块相结合，TinyGPT-V的2.8B参数可以经历独特的量化过程，以适用于在各种8G设备上进行本地部署和推理任务

本文工作促进了更多成本效益、高效和高性能MLLMs的设计，扩大了它们在大量实际场景中的适用性，此外，本文还提出了通过小型骨干构建多模态大型语言模型的新范式

<img src="https://img.saraba1st.com/forum/202312/29/151840of5ttebhptletja8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231229-151504__01.jpg</strong> (225.17 KB, 下载次数: 0)

下载附件

2023-12-29 15:18 上传

与其他通用MLLM相比，TinyGPT-V在多种视觉语言任务中实现了与13B或7B模型相同的性能

<img src="https://img.saraba1st.com/forum/202312/29/151844eyrxso50bnyt8wby.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231229-151528__01.jpg</strong> (211.85 KB, 下载次数: 0)

下载附件

2023-12-29 15:18 上传

TinyGPT-V的训练过程，第一阶段是预热训练，第二阶段是预训练，第三阶段是指令微调，第四阶段是多任务学习

<img src="https://img.saraba1st.com/forum/202312/29/151850s9hx591002j1c233.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231229-151556__01.jpg</strong> (265.74 KB, 下载次数: 0)

下载附件

2023-12-29 15:18 上传

(a)表示LoRA的结构
(b)表示LoRA如何在自然语言处理中高效地微调大型语言模型
(c)表示TinyGPT-V的LLM结构
(d)表示QK归一化(Normalization)的结构

<img src="https://img.saraba1st.com/forum/202312/29/151857jyyryod0gxgrggg4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231229-151608__01.jpg</strong> (231.26 KB, 下载次数: 0)

下载附件

2023-12-29 15:18 上传

TinyGPT-V在训练期间使用的数据集的完整列表

<img src="https://img.saraba1st.com/forum/202312/29/151903h0ucgjqh753ooooo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231229-151636__01.jpg</strong> (264.46 KB, 下载次数: 0)

下载附件

2023-12-29 15:19 上传

TinyGPT-V训练阶段的学习率变化

<img src="https://img.saraba1st.com/forum/202312/29/151908oykxaygagzggpsgb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231229-151651__01.jpg</strong> (94.97 KB, 下载次数: 0)

下载附件

2023-12-29 15:19 上传

TinyGPT-V训练阶段的loss变化

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1133#       发表于 2023-12-29 15:41

MobileVLM

适用于移动设备的快速、可重现且强大的视觉语言助手

github项目主页:https://github.com/Meituan-AutoML/MobileVLM

MobileVLM，一种专为移动设备设计的多模态视觉语言模型(MMVLM/mobile multimodal vision language model)，融合了许多面向移动设备的架构设计和技术，通过从零开始训练一个规模为14亿和27亿参数的语言模型集合，一个以CLIP方式预训练的多模态视觉模型，以及通过高效投影器实现的跨模态交互

在几个经典的VLM基准测试上评估了MobileVLM，模型表现与一些更大的模型相当，更重要的是，同时在高通骁龙888 CPU和NVIDIA Jeston Orin GPU上测量了推理速度，分别达到了每秒21.5个Token和65.3个Token的SOTA性能

<img src="https://img.saraba1st.com/forum/202312/29/154055wddgnue4djl7ieud.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231229-153904.jpg</strong> (184.99 KB, 下载次数: 0)

下载附件

2023-12-29 15:40 上传

开源VLM架构及其相关训练语料库的对比
*表示BLIP采用了多模态编码器/解码器

<img src="https://img.saraba1st.com/forum/202312/29/154058s3b3rfm0rs21lc4r.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231229-153920.jpg</strong> (47.27 KB, 下载次数: 0)

下载附件

2023-12-29 15:40 上传

本文语言模型的详细设置

<img src="https://img.saraba1st.com/forum/202312/29/154103rtgwzbddttmjwc5m.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231229-153941.jpg</strong> (108.22 KB, 下载次数: 0)

下载附件

2023-12-29 15:41 上传

MobileVLM架构(右)使用MobileLLaMA作为其语言模型，分别将图像Xv和语言指令Xq作为输入，并给出语言响应Ya作为输出，LDP指的是轻量级下采样投影器(左)

<img src="https://img.saraba1st.com/forum/202312/29/154111bz631u9i99ls9594.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231229-153959.jpg</strong> (93.23 KB, 下载次数: 0)

下载附件

2023-12-29 15:41 上传

MobileVLM训练策略图示

<img src="https://img.saraba1st.com/forum/202312/29/154116dx87ucuo8c7ph7x7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231229-154018.jpg</strong> (151.39 KB, 下载次数: 0)

下载附件

2023-12-29 15:41 上传

与主流语言基准测试上的SOTA移动规模语言模型进行对比

<img src="https://img.saraba1st.com/forum/202312/29/154120hfjqepna4rtuauaz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231229-154033.jpg</strong> (61.36 KB, 下载次数: 0)

下载附件

2023-12-29 15:41 上传

在RedPajama数据的1.3T Token上训练Mobile LLaMA 1.4B和2.7B的loss曲线

<img src="https://img.saraba1st.com/forum/202312/29/154126k00bbof7oz7ajg6j.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231229-154042.jpg</strong> (87.39 KB, 下载次数: 0)

下载附件

2023-12-29 15:41 上传

MobileLLaMA 1.4B和2.7B的SFT loss曲线

<img src="https://img.saraba1st.com/forum/202312/29/154140lnatuataiytyy0aa.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231229-153623.jpg</strong> (238.66 KB, 下载次数: 0)

下载附件

2023-12-29 15:41 上传

<img src="https://img.saraba1st.com/forum/202312/29/154140mreggt93wwoiser9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231229-153635.jpg</strong> (246.23 KB, 下载次数: 0)

下载附件

2023-12-29 15:41 上传

<img src="https://img.saraba1st.com/forum/202312/29/154140bma10a2yx1bb1n6x.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231229-153649.jpg</strong> (192.82 KB, 下载次数: 0)

下载附件

2023-12-29 15:41 上传

<img src="https://img.saraba1st.com/forum/202312/29/154140dedfp6p4t7l5atfz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231229-153658.jpg</strong> (315.19 KB, 下载次数: 0)

下载附件

2023-12-29 15:41 上传

<img src="https://img.saraba1st.com/forum/202312/29/154140g6j6vjrqzl8xjlxj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231229-153720.jpg</strong> (222.1 KB, 下载次数: 0)

下载附件

2023-12-29 15:41 上传

<img src="https://img.saraba1st.com/forum/202312/29/154140kgkwnuwzguuppgww.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231229-153733.jpg</strong> (56.22 KB, 下载次数: 0)

下载附件

2023-12-29 15:41 上传

相关性能与延迟测试以及其他测试结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1134#       发表于 2023-12-29 16:05

 本帖最后由 Machinery 于 2023-12-29 16:06 编辑 

Generative AI for Math

第一部分——MathPile:十亿Token规模的数学预训练语料库

github项目主页:https://github.com/GAIR-NLP/MathPile/

高质量、大规模的语料库是构建基础模型的基石，在这项工作中，介绍了MathPile，一个包含约95亿 Token的多样化且高质量的以数学为中心的语料库

在创建过程中，坚持了“少即是多”的原则，坚信数据质量比数量在预训练阶段更重要，进行了细致入微的数据收集和处理工作，包括复杂的预处理、预过滤、语言识别、清洗、过滤和去重，确保了语料库的高质量

此外，还对下游基准测试集进行了数据污染检测，以消除重复数据，希望MathPile能够帮助提升语言模型的数学推理能力，同时计划开源不同版本的MathPile以及用于处理的脚本，以促进该领域的未来发展
————
介绍

<img src="https://img.saraba1st.com/forum/202312/29/160518qw00fhafohw0j3r9.png" referrerpolicy="no-referrer">

<strong>mathpile-features.png</strong> (54.39 KB, 下载次数: 0)

下载附件

2023-12-29 16:05 上传

以数学为中心:MathPile独特地迎合了数学领域的需求，这与Pile和RedPajama等以通用领域为中心的语料库不同，也与ROOTS和The Stack等以多语言为中心的语料库不同，虽然现在也存在以数学为中心的语料库，但它们通常要么是闭源的，例如Google的Minerva和OpenAI的MathMix，又或者要么缺乏多样性，例如ProofPile和OpenWebMath

多样性:MathPile的资料来源广泛:其中包含教科书(含讲稿)、arXiv、Wikipedia、ProofWiki、StackExchange和网页，它包含适合K-12、大学、研究生水平和数学竞赛的数学内容，这种多样性是其首创的，尤其是，还发布了大量高质量教科书内容(约0.19b Token)

高质量:坚持了少即是多的原则，坚信数据质量高于数量，即使在预训练阶段也是如此，细致的数据收集和处理工作包括一套复杂的预处理、预过滤、清理、过滤和重复数据删除，确保了语料库的高质量

<img src="https://img.saraba1st.com/forum/202312/29/160526iv7mpumjdmam91ug.png" referrerpolicy="no-referrer">

<strong>mathpile-overview.png</strong> (152.21 KB, 下载次数: 0)

下载附件

2023-12-29 16:05 上传

数据文档:为了提高透明度，广泛记录了MathPile，这包括数据集表和网络来源文档的质量标注，例如语言识别分数和符号与单词的比率，这使用户可以灵活地根据自己的需求定制数据，还执行了数据污染检测，以消除MATH和MMLU-STEM等基准测试集中的重复项

希望MathPile能够帮助增强语言模型的数学推理能力，请参阅论文了解更多技术细节
————
限制

在数据收集和处理阶段做出的决策可能并不总是最优的

MathPile中的某些文档可能并不总是具有最高质量，同时研究组致力于不断完善和优化这个语料库
————
声明

这些宝贵的语料库是人类智慧的顶峰，应该被用来改善人类，帮助改善人类生活，强烈呼吁所有用户不要利用本语料库进行任何可能危害国家安全、社会安全或违法的活动

研究组已尽最大努力确保数据的高质量和合法使用，然而，不可预见的问题仍然可能出现，包括但不限于数据安全问题以及因滥用而产生的任何风险或问题，研究组对任何此类问题不承担任何责任

如果MathPile的源数据受到比CC BY-NC-SA 4.0更严格的许可证管理，则MathPile应该遵守该更严格的许可，在所有其他情况下，它都在CC BY-NC-SA 4.0许可证下运行，同时已计划发布该数据集的商业可用版本

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1135#       发表于 2023-12-29 23:44

 本帖最后由 Machinery 于 2023-12-29 23:47 编辑 

DL3DV-10K

用于3D深度视觉学习的大规模场景数据集

项目主页:https://dl3dv-10k.github.io/DL3DV-10K/

github数据集下载:https://github.com/DL3DV-10K/Dataset

最近，基于深度学习的3D视觉领域取得了重大进展，从基于神经辐射场(NeRF)的3D表征学习到新视图合成(NVS)方面的普遍应用，然而，现有的基于深度学习的3D视觉场景级数据集，无论是合成环境还是真实世界场景的选择都非常有限，这不仅阻碍了对现有方法的全面评估，也限制了在基于深度学习的3D分析中可能的探索

为了解决这一关键问题，本文提出了DL3DV-10K，一个大规模场景数据集，包含了来自10510个视频的5120万帧，这些视频是从65种兴趣点(POI /point-of-interest)位拍摄的，同时涵盖了有界和无界场景，并具有不同水平的反射、透明和光照

在DL3DV-10K上对最近的NVS方法进行了全面的评估，揭示了未来NVS研究可能存在的有价值的见解，此外，在DL3DV-10K上进行学习的可泛化NeRF的试验研究中取得了令人鼓舞的结果，这充分表明了建立场景级大规模数据集是迈向3D表征学习的基础模型所必须的道路，DL3DV-10K数据集经过了详尽的基准测试，为学习3D表征的基础模型铺平了道路
————
A.10510个视频，具有一致的采集标准
B.全面的新视图综合基准
C.每个视频都有人工创建的与场景POI和复杂性(光线、表面材料等)相关的标签
D.每个视频都有校准的摄像机姿态、NeRF估计深度、点云和3D网格
————
统计数据

<img src="https://img.saraba1st.com/forum/202312/29/234422skqbekk949bt8w5y.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231229-232707.jpg</strong> (78.83 KB, 下载次数: 0)

下载附件

2023-12-29 23:44 上传

<img src="https://img.saraba1st.com/forum/202312/29/234422zp5sd077q4w0200i.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231229-232825.jpg</strong> (246.62 KB, 下载次数: 0)

下载附件

2023-12-29 23:44 上传

图1.按POI类别的场景分布
每个类的角度表示其数据比例
Interior(室内):主要的POI类别
Exterior(室外):次要的POI类别

<img src="https://img.saraba1st.com/forum/202312/29/234429bkq8yxxwts2tz6a5.png" referrerpolicy="no-referrer">

<strong>Scene_Category_by_secondary_POI.png</strong> (501.94 KB, 下载次数: 0)

下载附件

2023-12-29 23:44 上传

图2.次要的POI类别内的场景数量
图例包含主要和次要POI类别之间的映射，观察到学校大学和住宅区是DL3DV-10K数据集中的主要场景，相比之下，诸如政府和市政服务设施(例如邮局、警察局、法院和市政厅)等地点的拍摄频率较低，因为进入这些区域进行详细视频记录存在困难

<img src="https://img.saraba1st.com/forum/202312/29/234434g88bbng10qbq84n1.png" referrerpolicy="no-referrer">

<strong>Scene_complexity_primary-POI.png</strong> (314.81 KB, 下载次数: 0)

下载附件

2023-12-29 23:44 上传

图3.按复杂性指数显示了场景类别(主要的POI地点)的分布
包括环境设置、光照条件、反射表面和透明材料，光照条件下的属性包括:自然光(nlight)、人造光(alight)以及两者的组合(mlight)，反射类包括更多、中等、更少和无，透明度同反射类

<img src="https://img.saraba1st.com/forum/202312/29/234440y9l4u7q79d3iqlzi.png" referrerpolicy="no-referrer">

<strong>duration_frequency_distribution.png</strong> (117.09 KB, 下载次数: 0)

下载附件

2023-12-29 23:44 上传

 图4.展示了10510 个视频的视频时长和频率指标的分布
使用消费类移动设备进行视频拍摄的最短时长设置为60秒，而对于无人机摄像机来说，则至少为45秒，在数据集中，视频时长中位数为69.5秒，此外，通过平均图像强度确定的频率指标的中位数值为2.6e-06，基于这个中位数值，将场景分为高频率和低频率两类

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1136#       发表于 2023-12-30 01:39

Unified-IO 2

通过视觉、语言、音频和动作(Vision, Language, Audio, and Action)扩展自回归多模态模型

项目主页:https://unified-io-2.allenai.org/

github项目代码仓库:https://github.com/allenai/unified-io-2

Unified-IO 2，这是第一个能够理解和生成图像、文本、音频和动作的自回归多模态模型，为了统一不同的模态，通过将输入和输出(图像、文本、音频、动作、边界框等)进行分词化(tokenize)，进入一个共享的语义空间，然后使用单一的编码-解码Transformer模型进行处理，由于使用如此多样化的模态进行训练具有挑战性，提出了各种架构改进来稳定模型训练

通过从头开始在一个大型的多模态预训练语料库上训练模型，该语料库来自各种来源，结合了多模态混合的去噪目标(multimodal mixture of denoisers objective)，为了学习一系列广泛的技能，例如遵循多模态指令，构建了一个聚合了120个数据集、提示和增强方法的集合，并对其进行微调

通过单一的统一模型，Unified-IO 2 在GRIT基准测试中达到了SOTA性能，并在超过35个基准测试中取得了强大的结果，其中包括图像生成和理解、自然语言理解、视频和音频理解以及机器操作(robotic manipulation)

<img src="https://img.saraba1st.com/forum/202312/30/013827cc9v3yh7icbj96iv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-013202__01.jpg</strong> (429.41 KB, 下载次数: 0)

下载附件

2023-12-30 01:38 上传

UNIFIED-IO 2是一种具有广泛能力和支持模态的指令跟随模型，它可以生成图像(红框)，进行包括图像编辑、图像生成、深度估计、表面法线估计和未来帧预测等任务，它还可以生成文本(蓝框)，其中包括对查询的长式回答、关键点估计、视觉音频定位、预测机器操作等，也可以从图像或文本生成音频(绿框)

<img src="https://img.saraba1st.com/forum/202312/30/013841dd9y7ltgyllytlsy.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-013217__01.jpg</strong> (322.55 KB, 下载次数: 0)

下载附件

2023-12-30 01:38 上传

UNIFIED-IO 2架构，输入的文本、图像、音频或图像/音频历史被编码成嵌入序列，这些序列被连接起来并作为编码器-解码器Transformer模型的输入，Transformer输出离散的Token，可以解码成文本、图像或音频片段

<img src="https://img.saraba1st.com/forum/202312/30/013847lhwz36l0omgl3512.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-013225__01.jpg</strong> (154.93 KB, 下载次数: 0)

下载附件

2023-12-30 01:38 上传

左:不同模态混合的训练loss(a)和梯度范数/gradient norms(b)
右:UIO-2XXL在所有模态上的训练loss(c)和下一个Token预测准确度 (d)

在应用提案的构架改进之前获得了结果

<img src="https://img.saraba1st.com/forum/202312/30/013855ahxzpntx9b9jhb9t.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-013225__02.jpg</strong> (87.24 KB, 下载次数: 0)

下载附件

2023-12-30 01:38 上传

三个模型的训练loss曲线，使用动态封装(dynamic packing)和512的批大小进行预训练

<img src="https://img.saraba1st.com/forum/202312/30/013905p68f6wnx9n3qxd3e.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-013225__03.jpg</strong> (106.35 KB, 下载次数: 0)

下载附件

2023-12-30 01:39 上传

掩码图像建模中的不同训练范式:
(a)自回归
(b)掩码自编码(mask auto-encoder)
(c)动态掩码的自回归

提出的范式可以在避免解码器信息泄露的同时保持因果生成

<img src="https://img.saraba1st.com/forum/202312/30/013914not8o3v552hmh88m.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-013246__01.jpg</strong> (219.57 KB, 下载次数: 0)

下载附件

2023-12-30 01:39 上传

预训练和指令调整数据的分布，分割与采样率成正比，内部部分展示了目标模态，外部部分显示数据类型

<img src="https://img.saraba1st.com/forum/202312/30/013919cety00v9ztgwwxjy.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-013306__01.jpg</strong> (57.47 KB, 下载次数: 0)

下载附件

2023-12-30 01:39 上传

UNIFIED-IO 2的不同变体

<img src="https://img.saraba1st.com/forum/202312/30/013926kj1ea1v7jn9jdhdy.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-013355__01.jpg</strong> (237 KB, 下载次数: 0)

下载附件

2023-12-30 01:39 上传

从视频数据中构建模型的输入与目标的训练样本，给定视频，首先提取视频帧以及相应的音频谱图和转录文本，然后，数据经过随机选择过程确定目标模态、输入模态、训练目标、输入掩码等，模型的最终输入和目标在右上方

<img src="https://img.saraba1st.com/forum/202312/30/013936hxwo3n4d2qxf6xw8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-013409__01.jpg</strong> (593.95 KB, 下载次数: 0)

下载附件

2023-12-30 01:39 上传

可以执行多种多模态任务的统一模型:对图像进行字幕说明，遵循自由形式的指令，图像编辑，物体检测，语义分割，表面法线和基于图像的音频生成等等，在这里，展示了模型对各种提示的输出

<img src="https://img.saraba1st.com/forum/202312/30/013942krpbbiwrdzzdixq9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-013422__01.jpg</strong> (432.3 KB, 下载次数: 0)

下载附件

2023-12-30 01:39 上传

<img src="https://img.saraba1st.com/forum/202312/30/013942sk9ho9k99oz3ui7n.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-013436__01.jpg</strong> (411.88 KB, 下载次数: 0)

下载附件

2023-12-30 01:39 上传

<img src="https://img.saraba1st.com/forum/202312/30/013942m8gzvw3e8fx7e3yo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-013454__01.jpg</strong> (249.66 KB, 下载次数: 0)

下载附件

2023-12-30 01:39 上传

<img src="https://img.saraba1st.com/forum/202312/30/013942e64uxbdd3e3qonq7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-013504__01.jpg</strong> (83.21 KB, 下载次数: 0)

下载附件

2023-12-30 01:39 上传

相关评估结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1137#       发表于 2023-12-30 19:18

 本帖最后由 Machinery 于 2023-12-30 19:20 编辑 

City-on-Web

网上的大型场景实时神经渲染

项目主页:https://ustc3dv.github.io/City-on-Web/

NeRF已经显著推进了3D场景重建任务，可以在各种环境中捕捉复杂的细节，现有的方法已经成功地利用辐射场烘焙技术(radiance field baking)来实现对小场景的实时渲染，然而，当应用于大规模场景时，这些技术面临着重大挑战，由于计算、显存和带宽资源有限，很难提供无缝浏览的实时体验

在本文中，提出了City-on-Web，通过将整个场景划分为可管理的块(manageable blocks)，并为每个块分配适当的细节级别(Level-of-Detail)，以确保高保真度、高效的显存管理和快速渲染，与此同时，仔细设计了训练和推理过程，以确保网上的最终渲染结果与训练一致，得益于新颖的表征方式和精心设计的训练/推理过程，本文方法率先在资源有限的环境中实现了大规模场景的实时渲染

大量的实验结果表明，本文方法有助于网络平台上实时渲染大规模场景，在1080P分辨率下，使用RTX 3060 GPU，在Web平台上实现了32FPS的实时渲染，并同时实现了与SOTA方法接近的质量
————
渲染效果(请前往项目页面查看)

<img src="https://img.saraba1st.com/forum/202312/30/191725t0pw5padzfpjjhxj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-190910__01.jpg</strong> (584.14 KB, 下载次数: 0)

下载附件

2023-12-30 19:17 上传

<img src="https://img.saraba1st.com/forum/202312/30/191745nd8t8fjffo383757.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-190915__01.jpg</strong> (563.53 KB, 下载次数: 0)

下载附件

2023-12-30 19:17 上传

City-on-Web，根据已知信息，这是第一个能够使用笔记本电脑GPU通过网络对大规模场景进行实时神经渲染的系统，上图为在1920x1080分辨率的NVIDIA RTX 3060笔记本电脑GPU上的测试结果
————
训练工作流程

<img src="https://img.saraba1st.com/forum/202312/30/191753uiazeqzzui3ieac9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-190831.jpg</strong> (185.96 KB, 下载次数: 0)

下载附件

2023-12-30 19:17 上传

首先根据地平面将整个场景划分为不重叠的不同块，对于光线通过的块，相应的着色器渲染每个块的颜色和不透明度，对光线经过的块进行深度排序，然后通过保持3D一致性的Alpha混合渲染最终的结果
——
LOD生成

1.由于采用了非重叠的分割策略，因此可以直接对网格进行下采样，并合并多个块以生成LOD
2.对于合并的块，首先冻结属性查询函数的训练(training of attribute query function)，然后重新训练一个新的延迟MLP(new deferred MLP)
3.在训练完延迟MLP后，继续同时训练延迟MLP和下采样模型

<img src="https://img.saraba1st.com/forum/202312/30/191813erwvwy5qbbbf39sp.jpg" referrerpolicy="no-referrer">

<strong>09f5c666-e114-41ce-b622-27b36989c9a6.jpg</strong> (156.43 KB, 下载次数: 0)

下载附件

2023-12-30 19:18 上传

——
与SOTA方法对比

本文方法擅长恢复更精细的细节，并且在不同的尺度和环境中实现了更高质量的重建

<img src="https://img.saraba1st.com/forum/202312/30/191854ncey888debfhyrco.jpg" referrerpolicy="no-referrer">

<strong>e57dafcb-348f-4fec-8488-520676a7dd41.jpg</strong> (284.84 KB, 下载次数: 0)

下载附件

2023-12-30 19:18 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1138#       发表于 2023-12-30 19:52

DreamGaussian4D

4D高斯泼溅生成

项目主页:https://jiawei-ren.github.io/projects/dreamgaussian4d

github项目代码仓库:https://github.com/jiawei-ren/dreamgaussian4d

最近4D内容生成取得了显著进展，然而现有方法存在优化时间长、缺乏运动可控性和细节部分表现不好的问题，在本文中，介绍了DreamGaussian4D，一种基于4D高斯泼溅表征的高效4D生成框架

本文主要见解是，与隐式表征相比，高斯泼溅中的空间变换(spatial transformations)使显式建模更适合4D生成

DreamGaussian4D将优化时间从几个小时缩短到几分钟，同时允许灵活的控制生成的3D运动，并且可以生成能够在3D引擎中高效渲染的动画化网格

<img src="https://img.saraba1st.com/forum/202312/30/195124yzdgszmgdz1d1d41.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-194620__01.jpg</strong> (388.02 KB, 下载次数: 0)

下载附件

2023-12-30 19:51 上传

DreamGaussian4D利用4D高斯泼溅可以在几分钟内生成4D内容，导出的网格可以在3D引擎中高效地合成和渲染

<img src="https://img.saraba1st.com/forum/202312/30/195129ioluleluo06oyeoy.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-194642__01.jpg</strong> (126.98 KB, 下载次数: 0)

下载附件

2023-12-30 19:51 上传

速度对比，DreamGaussian 4D将优化时间从几个小时缩短到几分钟

<img src="https://img.saraba1st.com/forum/202312/30/195134ml9g45mrtrd1xzm1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-194658__01.jpg</strong> (364.3 KB, 下载次数: 0)

下载附件

2023-12-30 19:51 上传

DreamGaussian4D框架，首先使用DreamGaussianHD获取静态3D GS模型，并使用图像到视频扩散模型得到一个驱动视频，随后，通过优化一个变形网络，学习在不同时间戳下如何变形静态3D GS，使用MSE损失和SDS损失对驱动视频进行监督，最后，可以导出逐帧网格，并且可以使用视频到视频工作流程对纹理映射进行细化

<img src="https://img.saraba1st.com/forum/202312/30/195152zihmwgr6fg6b6gb6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-194731__01.jpg</strong> (255.21 KB, 下载次数: 0)

下载附件

2023-12-30 19:51 上传

定性结果，渲染图像显示了渐变的时间戳和视角

<img src="https://img.saraba1st.com/forum/202312/30/195205wpu1duzhb0mai1b2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-194740__01.jpg</strong> (212.62 KB, 下载次数: 0)

下载附件

2023-12-30 19:52 上传

与Animate124的对比，本文模型达成了对输入图像更好的忠实度、更大的运动范围和更高的细节级别

<img src="https://img.saraba1st.com/forum/202312/30/195211s6633hfhsens41qz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-194740__02.jpg</strong> (73.3 KB, 下载次数: 0)

下载附件

2023-12-30 19:52 上传

组合场景，4D GS可以导出为可以在Blender中高效合成和渲染的网格

<img src="https://img.saraba1st.com/forum/202312/30/195215e2msrzhfss2ffrst.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-194740__03.jpg</strong> (97.46 KB, 下载次数: 0)

下载附件

2023-12-30 19:52 上传

对DreamGaussianHD的消融实验，现有的DreamGaussian在新视图下存在严重的模糊问题，多视图优化显著改善了纹理和几何形状，修复背景颜色进一步提高了细节级别

<img src="https://img.saraba1st.com/forum/202312/30/195220ss1efgzae7sdgvsg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-194747__01.jpg</strong> (33.43 KB, 下载次数: 0)

下载附件

2023-12-30 19:52 上传

对零初始化(zero-initialization)的消融实验，非零初始化会导致静态模型发生变化，成为次优的模型，例如熊猫的背面变成全黑等，而零初始化可以防止漂变

<img src="https://img.saraba1st.com/forum/202312/30/195225hg7uvz1s1scduyvp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-194747__02.jpg</strong> (36.88 KB, 下载次数: 0)

下载附件

2023-12-30 19:52 上传

可控运动，DreamGaussian4D可以轻松控制生成的运动，还可以从不同的驱动视频中为同一输入图像生成不同的3D运动

<img src="https://img.saraba1st.com/forum/202312/30/195230tbtho9z5khomk51m.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-194747__03.jpg</strong> (32.48 KB, 下载次数: 0)

下载附件

2023-12-30 19:52 上传

对纹理细化的消融实验，类似DreamGaussian的图像到图像(I2I)优化会导致相邻帧之间的时间一致性差和闪烁问题，而视频到视频(V2V)优化缓解了这个问题

<img src="https://img.saraba1st.com/forum/202312/30/195236xfq3dfegfdgmrqdm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231230-194747__04.jpg</strong> (15.73 KB, 下载次数: 0)

下载附件

2023-12-30 19:52 上传

定量结果
†：基于Zhao et al. (2023)提供的8个示例计算的结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1139#       发表于 2023-12-31 02:38

SpacetimeGaussians

用于实时动态视图合成的时空高斯特征泼溅(Spacetime Gaussian Feature Splatting)

项目主页:[https://oppo-us-research.github.io/SpacetimeGaussians-website/](https://oppo-us-research.github.io/SpacetimeGaussians-website/)

github项目仓库:[https://github.com/oppo-us-research/SpacetimeGaussians](https://github.com/oppo-us-research/SpacetimeGaussians)

动态场景的新视图合成一直是一个引人注目但具有挑战性的问题，尽管最近取得了一些进展，但同时实现高分辨率逼真的结果、以及实时渲染和紧凑的存储方案仍然是一项艰巨的任务

为了解决这些挑战，提出了一种新颖的动态场景表征方法——时空高斯特征泼溅(Spacetime Gaussian Feature Splatting)，它由三个关键组件组成

首先，通过增强3D高斯的时间不透明度和参数化运动/旋转，提出了富有表现力的时空高斯特征泼溅(Spacetime Gaussian Feature Splatting)，这使得时空高斯能够捕捉到场景中的静态、动态和瞬态内容

其次，引入了泼溅特征渲染，用神经特征取代了球谐函数(spherical harmonics)，这些特征有助于对视图和时间依赖的外观进行建模，同时保持小尺寸

第三，利用训练误差(training error)和粗略深度(coarse depth)的指导，在现有工作流程难以收敛的区域采样新的高斯

对几个已建立的真实世界数据集进行的实验证明，本文方法在保持紧凑存储的同时，实现了SOTA渲染质量和速度，在8K分辨率下，本文方法的轻量版本模型可以在Nvidia RTX 4090 GPU上以60帧每秒的速度渲染

<img src="https://img.saraba1st.com/forum/202312/31/023658s9flmszr1i4n3xin.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231231-023310__01.jpg</strong> (226.61 KB, 下载次数: 0)

下载附件

2023-12-31 02:36 上传

本文方法的动态场景表征实现了逼真的质量、实时的高分辨率渲染和紧凑的模型大小

(a)轻量版本模型可以在Nvidia RTX 4090 GPU上以66 FPS的速度渲染8K 6-DoF视频

(b)一个具有挑战性场景的新视角渲染示例

(c)在神经3D视频数据集上与先前的研究在渲染质量、速度和模型大小方面的定量对比

<img src="https://img.saraba1st.com/forum/202312/31/023707ewha2x0balmkfl22.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231231-023325__01.jpg</strong> (167.98 KB, 下载次数: 0)

下载附件

2023-12-31 02:37 上传

时空高斯和特征渲染概览

(a)本文方法利用一组时空高斯(STG)来表示动态场景，在3D高斯的基础上，每个STG还进一步配备了时间不透明度、多项式运动/旋转和时间依赖特征

(b)将绘制的特征可视化为映射，通过MLP将其转换为彩色图像

<img src="https://img.saraba1st.com/forum/202312/31/023717ehppn3333nnn8g3p.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231231-023337__01.jpg</strong> (282.09 KB, 下载次数: 0)

下载附件

2023-12-31 02:37 上传

高斯引导采样策略的图示，通过利用训练误差和粗略深度的指导，沿光线对新高斯进行采样

<img src="https://img.saraba1st.com/forum/202312/31/023733ctcl8kfgl7k9o5t8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231231-023353__01.jpg</strong> (107.62 KB, 下载次数: 0)

下载附件

2023-12-31 02:37 上传

在Neural 3D视频数据集上进行定量对比

“FPS”以1352×1014分辨率进行测量，“Size”是300帧的总模型大小，其中一些方法只报告了部分场景，为了公平起见，还根据他们的设置报告了本文方法的结果

1只包括Flame Salmon场景，2排除了Coffee Martini场景

<img src="https://img.saraba1st.com/forum/202312/31/023745jzfr3rr0bfb37zbt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231231-023406__01.jpg</strong> (379.9 KB, 下载次数: 0)

下载附件

2023-12-31 02:37 上传

神经3D视频数据集的定性对比

<img src="https://img.saraba1st.com/forum/202312/31/023756k6ia2msu06re00ri.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231231-023414__01.jpg</strong> (339.73 KB, 下载次数: 0)

下载附件

2023-12-31 02:37 上传

Google Immersive数据集的定性对比

<img src="https://img.saraba1st.com/forum/202312/31/023807ktqt2yyo1dzqqyd5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231231-023424__01.jpg</strong> (216.5 KB, 下载次数: 0)

下载附件

2023-12-31 02:38 上传

<img src="https://img.saraba1st.com/forum/202312/31/023813l5cyrk6trp5cgc9p.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231231-023432__01.jpg</strong> (79.27 KB, 下载次数: 0)

下载附件

2023-12-31 02:38 上传

其他定性对比与消融实验


*****

####  Machinery  
##### 1140#       发表于 2023-12-31 02:56

<img src="https://img.saraba1st.com/forum/202312/31/025510dmjbeeebjbadbxec.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231231-025432.jpg</strong> (51.6 KB, 下载次数: 0)

下载附件

2023-12-31 02:55 上传

这篇卡了四次，老哥们可以去项目页自己看，就不发了<img src="https://static.saraba1st.com/image/smiley/face2017/068.png" referrerpolicy="no-referrer">

项目主页:[https://ssr-encoder.github.io/](https://ssr-encoder.github.io/)


*****

####  Machinery  
##### 1141#       发表于 2023-12-31 03:51

 本帖最后由 Machinery 于 2023-12-31 03:57 编辑 

DiffusionGAN3D

通过结合3D GANs和扩散先验提升文本引导的3D生成和领域自适应(Domain Adaption)

项目主页:https://younglbw.github.io/DiffusionGAN3D-homepage/

github项目代码仓库:https://github.com/youngLBW/DiffusionGAN3D

文本引导的领域自适应，以及，生成具有3D注意的肖像(3D-aware portraits)，在各个领域中都可以找到应用前景，然而由于缺乏训练数据和处理高度多样的几何和外观的挑战，现有的方法在这些任务中存在各种问题，如不灵活、不稳定和低保真度(inflexibility, instability, and low fidelit)

在本文中，提出了一种新颖的框架，DiffusionGAN3D，通过结合3D GAN和扩散先验来提升(boosts)文本引导的3D领域自适应和生成，具体而言，整合了预训练的3D生成模型(例如EG3D)和文本到图像扩散模型，前者为从文本生成稳定且高质量的化身提供了坚实的基础，而扩散模型则提供了强大的先验知识，并通过信息指导(informative direction)引导3D生成器进行灵活而高效的文本引导领域自适应的微调

为了增强领域自适应中的多样性和文本到化身的生成能力，分别引入了相对距离损失(relative distance loss)和用例特定的可学习三平面(case-specific learnable triplane)，此外，还设计了一个渐进式纹理细化模块(progressive texture refinement module)，以提高上述两个任务的纹理质量

大量实验证明，所提出的框架在领域自适应和文本到化身任务中取得了出色的结果，在生成质量和效率方面优于现有方法

<img src="https://img.saraba1st.com/forum/202312/31/034931errqotzbsvepzrxm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231231-034421__01.jpg</strong> (678.15 KB, 下载次数: 0)

下载附件

2023-12-31 03:49 上传

所提出的DiffusionGAN3D在不同任务上的一些生成结果

<img src="https://img.saraba1st.com/forum/202312/31/034938n766jjcnucck7c26.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231231-034431__01.jpg</strong> (424.64 KB, 下载次数: 0)

下载附件

2023-12-31 03:49 上传

所提出的两阶段DiffusionGAN3D框架的概览图

<img src="https://img.saraba1st.com/forum/202312/31/034943sdjumis7lxq0pg6i.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231231-034446__01.jpg</strong> (104.73 KB, 下载次数: 0)

下载附件

2023-12-31 03:49 上传

相对距离损失的图示

<img src="https://img.saraba1st.com/forum/202312/31/034947ym11kknggwdwujkz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231231-034504__01.jpg</strong> (70.72 KB, 下载次数: 0)

下载附件

2023-12-31 03:49 上传

给定文本“a man with green hair”，不同噪声级别下的SDS损失梯度响应的可视化

<img src="https://img.saraba1st.com/forum/202312/31/034955untnhu1bbo03ybt4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231231-034509__01.jpg</strong> (71.16 KB, 下载次数: 0)

下载附件

2023-12-31 03:49 上传

所提出的自适应混合模块的细节

<img src="https://img.saraba1st.com/forum/202312/31/035441cext25llmgw52w85.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231231-034534__01__02.jpg</strong> (194 KB, 下载次数: 0)

下载附件

2023-12-31 03:54 上传

3D领域自适应的定性对比(在EG3D-FFHQ上应用)

<img src="https://img.saraba1st.com/forum/202312/31/035449wyw2gygxfy1euvul.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231231-034534__01__01.jpg</strong> (187.5 KB, 下载次数: 0)

下载附件

2023-12-31 03:54 上传

文本到化身任务的视觉对比，前两行是“head”的结果，其余的则是“body”的结果

<img src="https://img.saraba1st.com/forum/202312/31/035537dj0s4me8edje3v6j.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231231-034556__01.jpg</strong> (64.79 KB, 下载次数: 0)

下载附件

2023-12-31 03:55 上传

3D领域自适应任务的定量对比

<img src="https://img.saraba1st.com/forum/202312/31/035106hg586owiv5jjj555.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231231-035043.jpg</strong> (44.5 KB, 下载次数: 0)

下载附件

2023-12-31 03:51 上传

对文本到化身生成的用户偏好

<img src="https://img.saraba1st.com/forum/202312/31/035020evn83ct87zzumux3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231231-034609__01.jpg</strong> (132.47 KB, 下载次数: 0)

下载附件

2023-12-31 03:50 上传

纹理细化的消融实验

<img src="https://img.saraba1st.com/forum/202312/31/035123wa1mrn2n6may66mi.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231231-034609__02.jpg</strong> (227.17 KB, 下载次数: 0)

下载附件

2023-12-31 03:51 上传

相对距离损失的消融实验

<img src="https://img.saraba1st.com/forum/202312/31/035128dm3q9e9iaupmpiey.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231231-034615__01.jpg</strong> (96.98 KB, 下载次数: 0)

下载附件

2023-12-31 03:51 上传

扩散引导重建损失的消融实验，EG3D中的ToRGB模块与Gtrain一起训练，输入文本是“a close-up of a woman with green hair”

<img src="https://img.saraba1st.com/forum/202312/31/035132tsyoi336eiq344y1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20231231-034615__02.jpg</strong> (207.58 KB, 下载次数: 0)

下载附件

2023-12-31 03:51 上传

用例特定的可学习三平面和多尺度总变分损失(multi-scale total variation loss)的消融实验

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1142#       发表于 2024-1-2 03:20

SynCLR

从模型中学习视觉可以与从数据中学习视觉相媲美

github项目主页:https://github.com/google-research/syn-rep-learn

SynCLR，一种可以从合成图像和合成字幕说明中学习视觉表征的新方法，不需要任何真实数据，通过使用大型语言模型合成了大量的图像字幕说明数据集，然后利用现成的文本到图像模型为每个合成字幕说明生成多个图像

通过对这些合成图像进行对比学习(contrastive learning)来进行视觉表征学习，将具有相同字幕说明的图像视为正样本对(positive pairs)，最终得到的表征在许多下游任务上都有很好的迁移性能，在图像分类任务上则可以与其他通用视觉表征学习方法(如CLIP和DINO v2)相媲美

此外，在语义分割等密集预测任务中，SynCLR的性能大幅优于先前的自监督方法，例如在ADE20k数据集上，对于ViT-B/16模型，相比MAE和iBOT，mIoU提高了6.2和4.3个百分点

<img src="https://img.saraba1st.com/forum/202401/02/031633bpl7m5du1epy941k.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-031102__01.jpg</strong> (163.81 KB, 下载次数: 0)

下载附件

2024-1-2 03:16 上传

视觉表征学习的三种范式

上方:传统方法，例如CLIP，仅从真实数据中学习
中间:最近的方法，例如StableRep，从真实文本和生成图像中学习
下方:本文方法，SynCLR，从合成文本与合成图像中学习，尽管没有直接观察过任何真实数据，但在ImageNet上可以与CLIP的线性性迁移性能相媲美

<img src="https://img.saraba1st.com/forum/202401/02/031640w42wp28yyqiztyqm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-031116__01.jpg</strong> (258.42 KB, 下载次数: 0)

下载附件

2024-1-2 03:16 上传

不同的学习目标对待分类粒度也有不同

这些图片是通过两个提示生成的:“a golden retriever, wearing sunglasses and a beach hat, rides a bike”和“a cute golden retriever sits in a house made of sushi”

SimCLR把每个图片都视为一个类别，而监督的交叉熵把它们都视为同一个“golden retrieval”类别，前者不考虑图片之间的共享语义，后者粒度粗略，忽略了主体/背景之间的动作或关系，而本文方法SynCLR，通过句子来定义视觉类别

<img src="https://img.saraba1st.com/forum/202401/02/031650nn2coil2imuxjjxx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-031132__01.jpg</strong> (470.35 KB, 下载次数: 0)

下载附件

2024-1-2 03:16 上传

展示了三个合成模板的示例，这些示例被用作Llama-2进行上下文学习任务的演示，总共有176个这样的示例，其中大部分是通过提示GPT-4生成的，而少数其他的是人为生成的(在一项1000万级的合成字幕说明试验中，没有关注到包括或排除人类生成示例之间的显著差异)

<img src="https://img.saraba1st.com/forum/202401/02/031656t1dwjzmyiwakjdmd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-031150__01.jpg</strong> (93.68 KB, 下载次数: 0)

下载附件

2024-1-2 03:16 上传

使用 Llama-2生成上下文字幕说明，其中，为每个推理r随机抽取三个上下文中的示例

<img src="https://img.saraba1st.com/forum/202401/02/031703vejzo6omsmsotm90.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-031209__01.jpg</strong> (1018.69 KB, 下载次数: 0)

下载附件

2024-1-2 03:17 上传

SynCLER工作流程中生成的合成字幕和图像的随机示例，每个字幕说明配有4张图像

<img src="https://img.saraba1st.com/forum/202401/02/031708p7e7pez70p575pkp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-031229__01.jpg</strong> (85.82 KB, 下载次数: 0)

下载附件

2024-1-2 03:17 上传

不同字幕说明合成策略的对比，报告了ImageNet线性评估的top-1准确率和9个细粒度数据集的平均准确率，每个项目包括10M个字幕说明和每个字幕说明的4张图片

<img src="https://img.saraba1st.com/forum/202401/02/031713ntjkzwe5l7t0ctew.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-031229__02.jpg</strong> (18.97 KB, 下载次数: 0)

下载附件

2024-1-2 03:17 上传

无分类引导尺度(CFG/Classifier-free guidance scale)，对比损失更偏好较小的CFG，但对其并不敏感

<img src="https://img.saraba1st.com/forum/202401/02/031741oa4nnaaqppjajiub.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-031240__01.jpg</strong> (63.82 KB, 下载次数: 0)

下载附件

2024-1-2 03:17 上传

模型的重要组件，ViT-B/16模型经过85000次迭代(iterations)，研究了影响ImageNet线性评估、细粒度分类(平均)和ADE20k分割的模块

<img src="https://img.saraba1st.com/forum/202401/02/031747r8g2i8ms0cpgbvzb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-031240__02.jpg</strong> (37.75 KB, 下载次数: 0)

下载附件

2024-1-2 03:17 上传

不同学习目标的对比，这些目标假设了不同级别的分类粒度，本文方法的建模方式，也即是，将字幕说明定义为类别，优于其他两种

<img src="https://img.saraba1st.com/forum/202401/02/031809nv25ocmazrzfoom2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-031257__01.jpg</strong> (372.87 KB, 下载次数: 0)

下载附件

2024-1-2 03:18 上传

在ImageNet线性评估和细粒度分类上的对比，尽管只使用了合成数据，SynCLR在性能上与OpenAI的CLIP和DINO v2模型相当

*表示DINO v2模型是从ViT-g模型中蒸馏出来的，因此在这个对比中具有优势
†表示重新运行时仅使用cls标记，而不是在原始DINO v2论文中提出的多层级连接(concatenating multiple layers)

<img src="https://img.saraba1st.com/forum/202401/02/031814gekc80yoe13zcycq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-031310__01.jpg</strong> (132.79 KB, 下载次数: 0)

下载附件

2024-1-2 03:18 上传

使用UperNet进行ADE20K语义分割(mIoU)，采用单尺度的512x512分辨率
†表示使用14x14的区块尺寸，因此可以适应518x518的分辨率

<img src="https://img.saraba1st.com/forum/202401/02/031820leq8j48tg9t9ffp9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-031310__02.jpg</strong> (156.51 KB, 下载次数: 0)

下载附件

2024-1-2 03:18 上传

在ImageNet上进行微调评估的Top-1准确率，模型在224x224的分辨率下进行微调
†表示使用14x14的区块尺寸

<img src="https://img.saraba1st.com/forum/202401/02/031929hfa33df05drmaarw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-031317__01.jpg</strong> (126.31 KB, 下载次数: 0)

下载附件

2024-1-2 03:19 上传

对于DINO v2和SynCLR未见过的概念的泛化能力，SynCLR优于DINO v2，CLIP取得了最佳准确率，可能是因为其训练数据包括与这些数据集相似的概念

<img src="https://img.saraba1st.com/forum/202401/02/031939yllwjifigw747i47.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-031317__02.jpg</strong> (47.28 KB, 下载次数: 0)

下载附件

2024-1-2 03:19 上传

在相同的合成数据上对比SynCLR和CLIP，观察到:
1.SynCLR优于CLIP
2.在相同设置中，即每个字幕说明生成4张图像，对于SynCLR和CLIP而言，SynCaps-150M都提供了更好的表征能力

<img src="https://img.saraba1st.com/forum/202401/02/031957o8dcm53p5p59889d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-031334__01.jpg</strong> (420.39 KB, 下载次数: 0)

下载附件

2024-1-2 03:19 上传

PCA可视化，根据DINO v2的方法，在同一组图像的区块之间进行PCA分析，并着色它们的前3部分，与DINO v2相比，SynCLR对汽车的映射更准确，但对狗略差一些，对两种方法都使用了ViT-L/14，在图像被输入网络之前，将图像调整为336x448的分辨率，得到24x32的可视化网格

<img src="https://img.saraba1st.com/forum/202401/02/032004gz4riccpvzzpqure.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-031346__01.jpg</strong> (51.08 KB, 下载次数: 0)

下载附件

2024-1-2 03:20 上传

不同训练尺度下的ImageNet的线性准确率

<img src="https://img.saraba1st.com/forum/202401/02/032009c89df05po8peeneo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-031346__02.jpg</strong> (53.67 KB, 下载次数: 0)

下载附件

2024-1-2 03:20 上传

不同训练尺度下的细粒度分类

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1143#       发表于 2024-1-2 03:49

LARP

用于开放世界游戏的语言代理者角色扮演(Language-Agent Role Play for Open-World Games)

项目主页:https://miao-ai-lab.github.io/LARP/

github项目代码仓库:https://github.com/MiAO-AI-Lab/LARP

语言代理者在定义明确的设置中以及简短的时间线内展现了令人印象深刻的问题解决能力，然而，随着开放世界模拟中不断演化的复杂性，迫切需要一种能够灵活适应复杂环境并始终维持长期记忆以确保一致的行动

为了弥合语言代理者与开放世界游戏之间的差距，引入了基于角色扮演的语言代理者(LARP/Language Agent for Role-Playing)，其中包括一个涵盖记忆处理和决策辅助的认知架构，一个带有反馈驱动可学习行动空间(feedback-driven learnable action space)的环境交互模块(environment interaction module)和一个促进各种人格对齐(alignment of various personalities)的后处理方法(post-processing method)

LARP框架改进了用户和代理者之间的交互，预先定义了独特的背景和人格，最终增强了在开放世界环境中的游戏体验，此外，它还突显了语言模型在娱乐、教育和各种模拟场景等领域的多样化应用

<img src="https://img.saraba1st.com/forum/202401/02/034855hizlziitv9tmmu43.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-034721__01.jpg</strong> (469.96 KB, 下载次数: 0)

下载附件

2024-1-2 03:48 上传

LARP的认知架构概览图

<img src="https://img.saraba1st.com/forum/202401/02/034859jmobbegdesqyve1j.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-034731__01.jpg</strong> (259.94 KB, 下载次数: 0)

下载附件

2024-1-2 03:48 上传

LARP的认知工作流程，这代表一个循环:从长期记忆和观察中获取的信息被记忆处理模块处理，并传输到工作记忆模块，工作记忆模块中的信息与观察到的信息一起输入到决策辅助模块中，最终生成一个决策或对话

记忆处理有三个主要阶段:编码、存储和回忆

编码是将信息转化为可以存储在记忆中的形式的过程，存储是在记忆中维持信息的过程，回忆是从记忆中检索信息的过程

<img src="https://img.saraba1st.com/forum/202401/02/034907eymrth6clrmcyses.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-034740__01.jpg</strong> (189.7 KB, 下载次数: 0)

下载附件

2024-1-2 03:49 上传

回忆心理过程的详细控制流程，首先对观察进行自询问(self-asking)，获取自询问问题(self-ask questions)，将自询问问题作为查询(queries)，采用不同的检索方法

1. 基于查询生成逻辑编程语言(logic programming language)和概率编程语言(probabilistic programming language)用于预测逻辑陈述(predicate logic statements)
2. 从查询中提取关键词后进行向量相似度搜索
3. 基于查询与问题-答案对(question-answer pairs)中的问题之间的语句相似度搜索问题-答案对

Qself-ask表示用作查询的自询问问题，Qlogic表示预测的逻辑查询陈述，Qkey表示提取的关键词，Q'A表示问题-答案对

<img src="https://img.saraba1st.com/forum/202401/02/034925lwz5q6ox5nlslubs.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-034749__01.jpg</strong> (212.57 KB, 下载次数: 0)

下载附件

2024-1-2 03:49 上传

环境互动

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1144#       发表于 2024-1-2 04:08

zeroshot-classifier

通过自然语言推理构建高效的通用分类器

相关论文:https://arxiv.org/abs/2312.17543

github项目主页:https://github.com/MoritzLaurer/zeroshot-classifier

hugface主页:https://huggingface.co/MoritzLaurer

生成式大型语言模型(LLMs)由于文本生成的普适性，在少样本(fewshot)和零样本(zeroshot)学习中已成为主流选择，然而，许多用户并不需要生成式LLMs的广泛能力，当他们只想自动化一个分类任务时，较小的类BERT的模型也可以学习通用任务，使它们能够在不需要微调(零样本分类)的情况下完成任何文本分类任务，或者仅通过少量示例学习新任务(少样本分类)，同时比生成式LLMs更高效

本文(1)解释了如何将自然语言推理(NLI/Natural Language Inference)用作遵循类似生成式LLMs指令微调原则的通用分类任务，(2)还提供了一个逐步指南和可重复使用的Jupyter笔记本，用于构建通用分类器，(3)共享了训练于33个数据集、包含389个不同类别的通用分类器的结果

共享的部分代码已被用于训练早期的旧零样本分类器，同时截至2023年12月，在Hugging Face Hub下载次数超过5500万次，而新分类器则提高了9.4%的零样本性能

<img src="https://img.saraba1st.com/forum/202401/02/040839z4l2klljtjyjocsk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-040358.jpg</strong> (166.64 KB, 下载次数: 0)

下载附件

2024-1-2 04:08 上传

<img src="https://img.saraba1st.com/forum/202401/02/040839implj0jnev3p9jh9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-040450.jpg</strong> (71.12 KB, 下载次数: 0)

下载附件

2024-1-2 04:08 上传

<img src="https://img.saraba1st.com/forum/202401/02/040839gh79j496e7k6je30.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-040631.jpg</strong> (362.69 KB, 下载次数: 0)

下载附件

2024-1-2 04:08 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  不热爱讨论  
##### 1145#       发表于 2024-1-2 05:13

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=62608771&amp;ptid=2126390" target="_blank">Machinery 发表于 2023-10-4 01:03</a>
Mistral 7B

由Mistral AI团队发布，迄今为止最强大的语言模型系列之一</blockquote>
玩了下，这个还真不错，关键是比他强的协议都没他好


*****

####  Machinery  
##### 1146#       发表于 2024-1-2 19:18

GeoGalacica

地球科学(Geoscience)中的科学大型语言模型

相关技术报告:https://arxiv.org/abs/2401.00434

github项目主页:https://github.com/geobrain-ai/geogalactica

大型语言模型(LLM)凭借其通用的知识和解决广泛范围内的各种自然语言处理(NLP)任务的能力取得了巨大成功，由于其令人印象深刻的能力，通过利用LLM促进人工智能进行科学领域((AI4S/AI for science))的交叉学科(inter-discipline)应用提供了新的可能性，同时，在地球科学研究和实践中利用NLP技术是宽广而复杂的，其中需要从知识提取和文档分类到问题回答以及知识发现等各方面的贡献

在这项工作中， 通过利用LLM来进行科学研究迈出了最初的一步，使用了一种相当简单有效的方法，将LLM转换为了地球科学方面的专家，首先，使用大量的地球科学文本对模型进行了进一步的预训练，并使用研究组自己收集的指令调整数据集进行了监督微调(SFT)，这些努力产生了一个包含300亿参数的模型，GeoGalactica，据目前所知，这是地球科学领域最大的语言模型

更具体地说，GeoGalactica是基于Galactica进一步预训练得到的，使用了一个包含650亿 Token的地球科学相关文本语料库对GeoGalactica进行训练，这些文本来自大型科学项目Deep-time Digital Earth(DDE)的广泛数据源，是迄今为止最大的地球科学特定文本语料库，然后使用100万对指令调整数据对模型进行微调，其中包含需要专业地球科学知识才能回答的问题

在这份技术报告中，详细介绍了GeoGalactica的所有方面，包括数据收集、数据清洗、基础模型选择、预训练、SFT和评估，同时将开源数据标注工具以及GeoGalactica在前3/4的预训练过程中的检查点

<img src="https://img.saraba1st.com/forum/202401/02/191801n18qf4jxl3gvq5dq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-191233__01.jpg</strong> (430.29 KB, 下载次数: 0)

下载附件

2024-1-2 19:18 上传

GEOGALACTICA的处理、构造、组件和应用概览图

<img src="https://img.saraba1st.com/forum/202401/02/191808v2ssf3gzgm83s3yr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-191245__01.jpg</strong> (167.83 KB, 下载次数: 0)

下载附件

2024-1-2 19:18 上传

尖端人工智能技术用于进行地球科学研究的进展示意图，淡绿色的文本框显示了来自计算机科学领域的技术，淡黄色的文本框显示了可能是地球科学家首次使用这些技术的研究

<img src="https://img.saraba1st.com/forum/202401/02/191813a7d7fb2zd2722fb9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-191251__01.jpg</strong> (235.68 KB, 下载次数: 0)

下载附件

2024-1-2 19:18 上传

本技术报告用到的词汇

<img src="https://img.saraba1st.com/forum/202401/02/191817ikcok7mefakkaznf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-191304__01.jpg</strong> (140.57 KB, 下载次数: 0)

下载附件

2024-1-2 19:18 上传

用于训练GEOGALACTICA的语料库的数据分布

<img src="https://img.saraba1st.com/forum/202401/02/191821cf8bqrrxq573rzqk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-191336__01.jpg</strong> (244.4 KB, 下载次数: 0)

下载附件

2024-1-2 19:18 上传

分词化(Tokenization)处理后的文本
A.展示了一个图表标记的例子，只选择保留标题；
B.展示了一个表格标记的例子，将表格转换为Markdown格式；
C.展示了引用标记的分词化处理，将引用数字替换为引用论文的标题，以保持文本语料的可读性；
D.展示了公式的特殊Token的例子

<img src="https://img.saraba1st.com/forum/202401/02/191829idshvjhdtr7drpl6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-191354__01.jpg</strong> (224.39 KB, 下载次数: 0)

下载附件

2024-1-2 19:18 上传

对GeoSignal贡献最大的四个平台

<img src="https://img.saraba1st.com/forum/202401/02/191834gbeeterir226twea.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-191406__01.jpg</strong> (276.38 KB, 下载次数: 0)

下载附件

2024-1-2 19:18 上传

知识密集数据源

<img src="https://img.saraba1st.com/forum/202401/02/191839eh7dd5gh2cephz53.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-191421__01.jpg</strong> (251.25 KB, 下载次数: 0)

下载附件

2024-1-2 19:18 上传

用于说明构造知识密集型指令数据的重构示例

<img src="https://img.saraba1st.com/forum/202401/02/191843qewuudnixizbqfiv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-191438__01.jpg</strong> (285.87 KB, 下载次数: 0)

下载附件

2024-1-2 19:18 上传

GeoSignal统计表格

<img src="https://img.saraba1st.com/forum/202401/02/191934fhdrvs3hhs2d937r.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-191914.jpg</strong> (113.13 KB, 下载次数: 0)

下载附件

2024-1-2 19:19 上传

相关资源链接
—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1147#       发表于 2024-1-2 20:14

COSMO

具有交错预训练(Interleaved Pre-Training)的对比精简型多模态模型(COntrastive Streamlined MultimOdal Model)

项目主页:http://fingerrec.github.io/cosmo

github项目跳转介绍主页:https://github.com/showlab/cosmo

CosMo2.1B预训练权重下载:https://huggingface.co/Awiny/cosmo2.1b/tree/main

CosMo3.4B预训练权重下载:https://huggingface.co/Awiny/cosmo3.4b/tree/main

CosMo8.1B:预训练权重下载https://huggingface.co/Awiny/cosmo8.1b/tree/main

在视觉语言预训练的演变中，从短文本理解转向包含扩展的文本上下文是至关重要的，最近的自回归视觉语言模型(例如flamingo，palme等)利用大型语言模型的长上下文能力，在少样本文本生成任务中表现出色，但在对齐任务中面临挑战

为了解决这一差距，本文通过将对比损失(contrastive loss)引入到文本生成模型中，提出了对比精简型多模态框架(COSMO/COntrastive-Streamlined MultimOdal framework)，将语言模型分为专用的单模态文本处理和熟练的多模态数据处理组件

统一框架COSMO融合了单模态和多模态元素，提高了模型在涉及文本和视觉数据的任务中的性能，同时显著减少了可学习的参数，然而，这些模型仍然需要大量的长文本数据集，但高质量的长文本视频数据集的可用性仍然有限，为了弥补这一差距，本文介绍了Howto-Interlink7M，一个首次交错的视频文本数据集，具有全面的字幕说明，标志着向前迈出的重要一步

通过展示其影响，说明了Howto-Interlink7M如何提高图像-文本任务中的模型性能，仅使用了可用数据的72%和可学习参数的34%，本文模型就表现出了比OpenFlamingo更显著的优越性能，在4-shot flickr实例字幕任务中，性能从57.2%显著提高到65%

COSMO和Howto-Interlink7M的贡献得到了14个不同的下游数据集的显著性能增益的支持，这些数据集涵盖了各种图像文本和视频文本任务

<img src="https://img.saraba1st.com/forum/202401/02/201240vdkpzmbxmdwxdz4e.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-200715__01.jpg</strong> (126.82 KB, 下载次数: 0)

下载附件

2024-1-2 20:12 上传

视觉语言预训练(VLP)的进展已经转向了适应长篇文本输入
(a)早期的研究强调短的图像/视频文本相关性，例如CLIP和GiT等作品
(b)现在的研究强调上下文学习策略，如Flamingo和Palm-E，LLMs出色的文本处理能力使得轻松集成长篇文档成为可能，展示了强大的少样本学习能力，无需大量的微调，模态学习范式具有显著的优势

<img src="https://img.saraba1st.com/forum/202401/02/201246xfvlrf6rkdk5vk8d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-200734__01.jpg</strong> (338.01 KB, 下载次数: 0)

下载附件

2024-1-2 20:12 上传

将传统的视频文本数据集与Howto-Interlink7M进行对比
左侧:传统的视频文本数据集通常包含描述视频的简短ASR字幕
右侧:在Howto-Interlink7M中，为了包含更多细节和改进视频的连贯性，视频被分割为镜头，随后，使用GPT-4模型根据历史上下文对每个镜头进行标注，并包括ASR、字幕说明和密集字幕说明，强调了物体标签以及视频片段之间的连接

<img src="https://img.saraba1st.com/forum/202401/02/201251dl5rsr5frks5t553.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-200751__01.jpg</strong> (51.27 KB, 下载次数: 0)

下载附件

2024-1-2 20:12 上传

Howto-Interlink7M的数据统计，最后两列分别是每个视频片段的平均Token长度和CLIP图像文本相似性分数

<img src="https://img.saraba1st.com/forum/202401/02/201326vrrislysqjjqqil6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-200757__01.jpg</strong> (77.85 KB, 下载次数: 0)

下载附件

2024-1-2 20:13 上传

CosMo的架构细节
#CE是交叉注意力层的数量的简写

<img src="https://img.saraba1st.com/forum/202401/02/201332z2d4i8hm4yu8y811.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-200806__01.jpg</strong> (169.73 KB, 下载次数: 0)

下载附件

2024-1-2 20:13 上传

CosMo的介绍:该模型同时处理图像/视频文本对和不同级别的图像/视频文本对，大型语言模型被分为两部分，用于计算对比损失和语言建模损失

<img src="https://img.saraba1st.com/forum/202401/02/201342snj0ai0uwkxownrt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-200813__01.jpg</strong> (29.71 KB, 下载次数: 0)

下载附件

2024-1-2 20:13 上传

低相似度图像的实例:在像MMC4这样的数据集中，基于原始网站内容，通常存在与相应文本不一致的图像，导致训练不稳定

<img src="https://img.saraba1st.com/forum/202401/02/201350qbl6dyvb3o5c65ov.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-200821__01.jpg</strong> (88.89 KB, 下载次数: 0)

下载附件

2024-1-2 20:13 上传

预训练数据集的统计信息:通过聚类和过滤从完整数据集中提取了一个子集

<img src="https://img.saraba1st.com/forum/202401/02/201355w0166qq3qfqqt9qj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-200829__01.jpg</strong> (215.88 KB, 下载次数: 0)

下载附件

2024-1-2 20:13 上传

LAION400M和类似的大型数据集通常存在冗余问题，聚类和基于统一的基于距离的采样有助于缓解这个问题

<img src="https://img.saraba1st.com/forum/202401/02/201406wmbpxvx5lczqv8lc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-200850__01.jpg</strong> (425.47 KB, 下载次数: 0)

下载附件

2024-1-2 20:14 上传

在一个1800万子集上的CosMo消融实验，主要关注对比了8-shot结果，将基线结果放在第一行。我们突出显示了可学习参数和全部参数之间的区别，对于字幕说明评估，报告了CIDER，'Iter.'是Iteration的缩写，靛蓝色文字表示默认设置

<img src="https://img.saraba1st.com/forum/202401/02/201420sbqtm6wem38btymm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-200903__01.jpg</strong> (451.51 KB, 下载次数: 0)

下载附件

2024-1-2 20:14 上传

不同规模的对比，通过仅使用128个Token进行预训练，本文模型的计算成本与相关方法相比显著降低，'ILLength'缩写为Interlevel Token Length，值得注意的是，CosMo-3.4B和Open-Flamingo(4B)使用相同的LLM(RedPajama-3B)和视觉编码器(Clip ViT-L/14)，带有颜色的行表示本文方法

<img src="https://img.saraba1st.com/forum/202401/02/201439a3g18llw33w3lh1l.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-200912__01.jpg</strong> (181.28 KB, 下载次数: 0)

下载附件

2024-1-2 20:14 上传

视频文本任务的对比，使用开放式生成评估这些数据集，括号表示使用语言模型进行文本相似度匹配进行评估，除了YouCook2之外，每个视频只使用3帧

<img src="https://img.saraba1st.com/forum/202401/02/201444u0ejiee2nzinjox7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-200932__01.jpg</strong> (70.78 KB, 下载次数: 0)

下载附件

2024-1-2 20:14 上传

MMC4的clip图像到文本相似度得分分布，左边是所有对(all pairs)，右边是匹配对(matched pairs)

<img src="https://img.saraba1st.com/forum/202401/02/201450bilacbmsj60a0n4c.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-200942__01.jpg</strong> (79.45 KB, 下载次数: 0)

下载附件

2024-1-2 20:14 上传

交错相似度阈值的分数选择会影响结果，N/A表示模型出现梯度爆炸，第二行表示用预训练的CosMo生成的字幕说明替换了嘈杂的数据

<img src="https://img.saraba1st.com/forum/202401/02/201457zrqqqq0ip33l30aq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240102-200942__02.jpg</strong> (61.2 KB, 下载次数: 0)

下载附件

2024-1-2 20:14 上传

数据质量极大地影响多样本能力

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1148#       发表于 2024-1-3 06:08

ToolEyes

关于现实世界中大型语言模型工具学习能力的细粒度评估

github项目主页:https://github.com/Junjie-Ye/ToolEyes

现有的工具学习评估主要集中在验证大型语言模型(LLMs)预先选择的工具与预期结果之间的对齐，然而，这些方法依赖于一组有限的可以预先确定答案的场景，与真实需求有所偏离，此外，仅关注结果忽视了LLMs有效利用工具所必需的复杂能力

为了解决这个问题，提出了ToolEyes，这是一个细粒度化的系统，专门设计用于评估LLMs在真实场景中的工具学习能力，该系统细粒度地考察了七个真实世界场景，分析了对于LLMs而言在工具学习中至关重要的五个维度：格式对齐(format alignment)、意图理解(intent comprehension)、行为规划(behavior planning)、工具选择(tool selection)和答案组织(answer organization)，此外，ToolEyes还包括一个工具库，拥有大约600个工具，可以作为LLMs与物理世界之间的中间介质

在涉及三个类别的十个LLMs的评估结果表明，在工具学习中存在对特定场景的偏好和有限的认知能力，有趣的是，拓展模型大小甚至加剧了对工具学习的阻碍。这些发现提供了有指导意义的见解，旨在推动工具学习领域的发展

<img src="https://img.saraba1st.com/forum/202401/03/060652pe223orelww5zhrs.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-060127__01.jpg</strong> (101.33 KB, 下载次数: 0)

下载附件

2024-1-3 06:06 上传

工具学习过程的示意图，在收到用户请求后，LLM会仔细审查用户的需求，提示获取足够的信息，选择适当的工具，并以指定的格式输入所需参数

随后，该工具与环境进行交互，向LLM提供反馈，然后，LLM根据最初的请求进行逻辑推理，按步骤中进行迭代思考直到得出确定的答案

<img src="https://img.saraba1st.com/forum/202401/03/060702xonn8ha2thn9tia9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-060140__01.jpg</strong> (394.12 KB, 下载次数: 0)

下载附件

2024-1-3 06:07 上传

ToolEyes的框架，ToolEyes提出了七个不同的真实场景，每个场景都包含了一系列相关的工具，LLMs 可以利用这些工具与物理世界进行交互，满足用户的实际需求，通过评估LLMs在五个维度上的能力，该系统能够高效地监督整个工具学习过程

<img src="https://img.saraba1st.com/forum/202401/03/060708bdwvw3wzvd3wb06r.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-060152__01.jpg</strong> (69.05 KB, 下载次数: 0)

下载附件

2024-1-3 06:07 上传

每个场景数据的统计信息

# Cat表示工具类别的数量，# Subcat表示工具子类别的数量，# Tool表示工具的数量，# Query表示用户查询(user queries)的数量

<img src="https://img.saraba1st.com/forum/202401/03/060714igao01g9sg069iax.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-060152__02.jpg</strong> (110.26 KB, 下载次数: 0)

下载附件

2024-1-3 06:07 上传

每个场景都有不同的工具类别

<img src="https://img.saraba1st.com/forum/202401/03/060719l4oqh4otq4qqkr04.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-060207__01.jpg</strong> (400.55 KB, 下载次数: 0)

下载附件

2024-1-3 06:07 上传

在每个场景下不同模型的性能表现，以百分比表示，“ALL”表示在所有场景下的得分，每个场景中最好的结果以粗体展示

<img src="https://img.saraba1st.com/forum/202401/03/060725nb86esuo8hob8obn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-060222__01.jpg</strong> (158.94 KB, 下载次数: 0)

下载附件

2024-1-3 06:07 上传

通过Welch's ANOVA测试(Welch’s ANOVA test)检查七种场景下各种LLM的总分，p值小于0.05表示数据之间存在显著差异

<img src="https://img.saraba1st.com/forum/202401/03/060734o5exq2qef2qa9zf5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-060242__01.jpg</strong> (96.4 KB, 下载次数: 0)

下载附件

2024-1-3 06:07 上传

对比了Vicuna-1.5-7B和Text-davinci-003在每种场景下的性能

<img src="https://img.saraba1st.com/forum/202401/03/060738r911z1k0z1jvsvq0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-060251__01.jpg</strong> (143.4 KB, 下载次数: 0)

下载附件

2024-1-3 06:07 上传

每个LLM与环境交互的轮数的概率密度分布

<img src="https://img.saraba1st.com/forum/202401/03/060742uo20y0t0jt005j5y.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-060306__01.jpg</strong> (227.64 KB, 下载次数: 0)

下载附件

2024-1-3 06:07 上传

所有场景中各种LLM在每个能力维度上的性能

<img src="https://img.saraba1st.com/forum/202401/03/060747s3djfxpmmznhbhp1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-060319__01.jpg</strong> (107.29 KB, 下载次数: 0)

下载附件

2024-1-3 06:07 上传

LLM的各种能力维度之间的皮尔逊相关系数(Pearson correlation coefficients)

<img src="https://img.saraba1st.com/forum/202401/03/060753mq7uuq5iq2uw7nq5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-060338__01.jpg</strong> (375.78 KB, 下载次数: 0)

下载附件

2024-1-3 06:07 上传

不同错误类型的一些示例，其中的错误已经标记为红色

<img src="https://img.saraba1st.com/forum/202401/03/060758ckybhmbbjjkxibbp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-060356__01.jpg</strong> (70.76 KB, 下载次数: 0)

下载附件

2024-1-3 06:07 上传

LLM的输出中缺少关键字的轮次和带有冗余句子的轮次

<img src="https://img.saraba1st.com/forum/202401/03/060802zoo7ivyzuecujzce.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-060401__01.jpg</strong> (45.76 KB, 下载次数: 0)

下载附件

2024-1-3 06:08 上传

Vicuna-1.5的st−realty和st−match(%)

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1149#       发表于 2024-1-3 06:45

 本帖最后由 Machinery 于 2024-1-3 06:46 编辑 

ReasoningLM

在预训练模型中启用结构子图推理以进行知识图谱问答(Enabling Structural Subgraph Reasoning in Pre-trained Language Models for Question Answering over Knowledge Graph)

github项目代码仓库(待整理):https://github.com/RUCAIBox/ReasoningLM

知识图谱问答(KGQA/Question Answering over Knowledge Graph)旨在从大规模知识图谱(KG)中寻找自然语言问题的答案实体，为了更好地对KG进行推理，最近的研究通常采用预训练语言模型(PLM)对问题进行建模，并采用基于图神经网络(GNN)的模块对KG进行多跳推理(multi-hop reasoning)，尽管这种方法卓有成效，但由于模型架构的差异，PLM和GNN并没有紧密集成，这限制了知识共享和细粒度的特征交互

为了解决这个问题，本文目标是简化上述的两个模块方法，并开发一个更强大的PLM，可以直接支持KGQA的子图推理，即ReasoningLM

在本文方法中，提出了一个子图感知的自注意机制(subgraph-aware self-attention mechanism)，以模拟GNN进行结构化推理，并采用自适应调整策略来调整具有20000个合成问题的子图的模型的参数

调整后，PLM可以在下游任务上进行参数高效的微调，实验证明，ReasoningLM在性能上大幅超过了现有的SOTA模型，即使是在更新的参数与训练数据同样少的情况下

<img src="https://img.saraba1st.com/forum/202401/03/064444bytp7y0yzqrtetr0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-064201__01.jpg</strong> (316.77 KB, 下载次数: 0)

下载附件

2024-1-3 06:44 上传

根据问题使用提出的子图序列化(subgraph serialization)和子图感知自注意力(subgraph-aware self-attention)，在子图上执行答案实体推理的示意图

<img src="https://img.saraba1st.com/forum/202401/03/064448du9yx7xmtm5nyz8y.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-064217__01.jpg</strong> (436.96 KB, 下载次数: 0)

下载附件

2024-1-3 06:44 上传

知识图谱问答的不同方法的性能对比(以百分比表示的Hits@1和F1)，粗体和下划线分别表示最佳和次佳方法，FPT和PET分别表示全参数调整和参数高效调整，Rule-SYN和LLM-SYN分别代表使用基于规则和基于LLM的策略合成问题

<img src="https://img.saraba1st.com/forum/202401/03/064452s48fk6wq2qq1q6t6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-064224__01.jpg</strong> (100.88 KB, 下载次数: 0)

下载附件

2024-1-3 06:44 上传

实验数据集的统计信息

<img src="https://img.saraba1st.com/forum/202401/03/064457xr92we6tq9ev6oq2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-064237__01.jpg</strong> (66.15 KB, 下载次数: 0)

下载附件

2024-1-3 06:44 上传

子图感知自注意力机制(SA)和自适应调整(AT)的消融实验

<img src="https://img.saraba1st.com/forum/202401/03/064503zt9r1pp9dt9pir4m.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-064237__02.jpg</strong> (58.78 KB, 下载次数: 0)

下载附件

2024-1-3 06:45 上传

使用不同的PLM在CWQ上的ReasoningLM性能

<img src="https://img.saraba1st.com/forum/202401/03/064507v47xsgjjl827im3s.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-064246__01.jpg</strong> (100.25 KB, 下载次数: 0)

下载附件

2024-1-3 06:45 上传

在使用不同数量样本进行自适应调整后，ReasoningLM在WebQSP和CWQ上的Hits@1分数(左边)，以及ReasoningLM在CWQ上与两个强基线(NSM和UniKGQA)进行微调时不同数量样本的Hits@1分数(右边)

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1150#       发表于 2024-1-3 23:10

Boundary Attention

学习在任何分辨率下寻找微弱边界(Faint Boundaries)

项目主页:https://boundaryattention.github.io/

code:coming soon

本文提出了一个可微模型(differentiable model)，通过一种称之为边界注意力(boundary attention)的新机制，可以显式地建模边界，包括轮廓、拐角和连接点(boundaries -- including contours, corners and junctions)

即使边界信号非常弱，又或者被噪声淹没，本文模型也能准确的提供精确的结果，与以前用于发现微弱边界的经典方法相比，本文模型具有可微分性、可扩展以适应更大的图像，还能够自动适应图像每个部分的适宜几何细节层次

与先前通过端到端训练来发现边界的深度方法相比，本文模型可以提供亚像素精度(sub-pixel precision)、更能抗噪声，还能够以原生分辨率以及纵横比处理任何图像
————
总览

<img src="https://img.saraba1st.com/forum/202401/03/230700dt9rqq6qzeq65l5s.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-230643.jpg</strong> (234.9 KB, 下载次数: 0)

下载附件

2024-1-3 23:07 上传

介绍了一种轻量级的自下而上模型(bottom-up model)，能够以高精度推理基于颜色(color-based)的边界，输出的边界由像素分辨率的向量场(pixel-resolution vector fields)表征，该向量场编码了图像中每个步幅为1(every stride-1 patch in an image)的区块(patch)的三分法(three-way partitions)和相关的窗口函数，这种输出可以表达各种边界元素，包括轮廓、细条、拐角、T形连接点和Y形连接点，因为它们是在没有进行光栅化的情况下进行表达的，因此没有分辨率限制

图像的底行滚动展示了这些输出，每个区块的分区都通过边界和分割颜色进行了可视化，这些重叠区块的各种“折叠(foldings)”导向了图像顶行的像素分辨率输出映射图:输入颜色的边界感知平滑、全局边界映射图(表示为无符号距离函数)以及每个像素与所有邻近之间的空间近似(spatial affinities)

本文模型的核心是一种特殊形式的邻近自注意力(neighborhood self-attention)，称为边界注意力，研究发现，可以使用非常简单的合成图像将其训练到一个可用的状态，这表明它对边界具有归纳偏差(inductive bias)，此外，由于它的所有操作都是局部和自下而上的，因此可以在小图像上训练它，然后可以在任何图像尺寸以及纵横比上应用它
————
模型的实现细节

<img src="https://img.saraba1st.com/forum/202401/03/230708tkbob6ebc3ubzhnu.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-230154.jpg</strong> (429.4 KB, 下载次数: 0)

下载附件

2024-1-3 23:07 上传

————
模型的涌现性质

<img src="https://img.saraba1st.com/forum/202401/03/230928obbaiqz1ja4at67y.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-230238__01__01.jpg</strong> (333.23 KB, 下载次数: 0)

下载附件

2024-1-3 23:09 上传

<img src="https://img.saraba1st.com/forum/202401/03/230928bfo7hbra8rfzuerq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-230238__01__02.jpg</strong> (697.49 KB, 下载次数: 0)

下载附件

2024-1-3 23:09 上传

<img src="https://img.saraba1st.com/forum/202401/03/230928awii3smwimou5ma8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-230238__02__01.jpg</strong> (509.29 KB, 下载次数: 0)

下载附件

2024-1-3 23:09 上传

<img src="https://img.saraba1st.com/forum/202401/03/230928id9hdhahtyh2r9m2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240103-230238__02__02.jpg</strong> (279.73 KB, 下载次数: 0)

下载附件

2024-1-3 23:09 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1151#       发表于 2024-1-4 01:40

TrailBlazer

基于扩散的视频生成过程中的轨迹控制(Trajectory Control)

项目主页:https://hohonu-vicml.github.io/Trailblazer.Page/

github项目代码仓库:https://github.com/hohonu-vicml/Trailblazer

在最近的文本到视频(T2V)生成方法中，实现合成视频的可控性常常面临挑战，通常，这个问题可以通过提供低级别的每帧指导(low-level per-frame guidance)解决，比如边缘图、深度图或已有的需要修改的视频，然而，获取这样的指导信息的过程中可能面临大量人力的消耗，本文旨在通过使用简单的边界框来增强视频合成的可控性，而无需神经网络训练、微调、推理时的优化或使用预先存在的视频

TrailBlazer算法，基于一个预训练的T2V模型构建，易于实现，通过提出的空间和时间注意力图编辑，使用边界框来指导主题(subject)的运动，此外，还引入了关键帧的概念，允许通过移动的边界框和相应的提示来指导主题的轨迹和整体外观，而无需提供详细的掩码(Mask)

该方法非常高效，与底层预训练模型相比，额外的计算量可以忽略不计，尽管边界框指导非常简单，但运动结果的效果令人惊讶地自然，这其中还包括随着边界框尺寸的增加，透视效果和朝向虚拟摄像机的运动结果的效果也同步增强
————
总览

<img src="https://img.saraba1st.com/forum/202401/04/013928srvrrqrsrsvhzvqf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240104-013638.jpg</strong> (182.5 KB, 下载次数: 0)

下载附件

2024-1-4 01:39 上传

TrailBlazer使用预训练模型进行文本到视频扩散的视频编辑，无需进一步的模型训练、微调或在线优化，支持各种所描述的用户体验
————
核心方法

<img src="https://img.saraba1st.com/forum/202401/04/013939l5c9915a9i95w79q.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240104-013724.jpg</strong> (89.33 KB, 下载次数: 0)

下载附件

2024-1-4 01:39 上传

突出显示了TrailBlazer的空间跨注意力编辑的中心组件(左侧，金色部分)和时间跨帧注意力编辑(右侧，蓝色部分)，这个操作仅在早期的去噪过程中应用，目标是在用户指定的边界框(bbox)内改变注意力图
————
场景合成

<img src="https://img.saraba1st.com/forum/202401/04/013946u8c7arg7aggrrx1h.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240104-013801.jpg</strong> (110.59 KB, 下载次数: 0)

下载附件

2024-1-4 01:39 上传

场景合成允许同时控制多个主题的运动，该算法首先对每个主题单独进行初始去噪步骤的计算，第一张图展示了“a white cat”和“a yellow dog”分别合成的结果，作为对主题质量的合理性检查

<img src="https://img.saraba1st.com/forum/202401/04/013957jidz83mvzhz993qq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240104-013821.jpg</strong> (158.18 KB, 下载次数: 0)

下载附件

2024-1-4 01:39 上传

然后，每个主题的中间结果被合成并在一个完整的提示(例如“a white cat and a yellow dog”)的控制下进行全局去噪处理，其中包括对环境的描述(例如“...on the moon”)，请注意，背景与主题之间的交互看起来是合理的，就像所有样本中的一致阴影一样
————
关键帧

<img src="https://img.saraba1st.com/forum/202401/04/014002xlccuk3lcqv3n37q.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240104-013838.jpg</strong> (37.25 KB, 下载次数: 0)

下载附件

2024-1-4 01:40 上传

通过关键帧，可以对边界框和提示进行动画化处理，使用户能够沿着时间轴改变主题的轨迹和粗略行为，生成的主题与指定的环境无缝衔接，为一般用户提供了一个可行的视频故事创作流程

<img src="https://img.saraba1st.com/forum/202401/04/014008d2rc2v0whbn0bort.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240104-013855.jpg</strong> (160.61 KB, 下载次数: 0)

下载附件

2024-1-4 01:40 上传

TrailBlazer提供了一种新颖的方法，通过bbox关键帧来引导合成主题的运动，例如，用户可以将动画化的鱼游泳动态地拖向摄影机，然后再游开，又或者，用户可以通过关键帧控制猫的奔跑速度，TrailBlazer的关键帧功能非常强大，例如，只需增加和减小bbox的尺寸，就可以简单地做出让鱼游向摄影机然后游开的动画
————
局限性

TrailBlazer承继了底层预训练模型(ZeroScope)的限制，这些限制包括动物的肢体数量不正确以及一些其他扩散式T2I和T2V方法的常见问题

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1152#       发表于 2024-1-4 02:36

Q-Refine

用于AI生成图像的质量感知优化器

github项目主页:https://github.com/Q-Future/Q-Refine

近年来，随着文本到图像(T2I)模型的急速发展，其生成结果的不尽人意已经成为一个需要解决的挑战，然而，对于不同质量的人工智能生成图像(AIGIs/AI-Generated Images)进行统一的优化，不仅限制了对低质量AIGIs的优化能力，还对高质量AIGIs带来了负面的优化效果

为了解决这个问题，本文提出了一种称为Q-Refine的质量奖励细化器(quality-award refiner)，基于人类视觉系统(HVS/Human Visual System)的偏好，Q-Refine首次使用图像质量评估(IQA/Image Quality Assessment)指标来引导细化过程，并通过三个适配工作流程修改不同质量的图像

实验证明，对于主流的T2I模型，Q-Refine能够对不同质量的AIGIs进行有效优化，还能作为一个通用细化器，从保真度和美学质量两个方面优化AIGIs，从而拓展了T2I生成模型的应用范围

<img src="https://img.saraba1st.com/forum/202401/04/023533wpipm5qewwqfp5rw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240104-023308__01.jpg</strong> (668.91 KB, 下载次数: 0)

下载附件

2024-1-4 02:35 上传

来自AGIQA-3K的原始AIGIs，经过传统细化器和本文提出的Q-Refine优化，作为一种质量感知指标，Q-Refine可以在模糊部分添加细节，以更好地优化低质量区域(1)(2)；提高中等质量区域(3)(4)的清晰度而不改变整个图像；并避免降低高质量区域(5)(6)的质量

<img src="https://img.saraba1st.com/forum/202401/04/023537jp7qd4cgtwy3rrwg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240104-023321__01.jpg</strong> (430.55 KB, 下载次数: 0)

下载附件

2024-1-4 02:35 上传

Q-Refine的框架，包括质量预处理模块(quality pre-prossess module)和用于低/中/高质量(LQ/MQ/HQ)区域的三个细化工作流程，每个工作流程的细化机制接受预测质量的指示

<img src="https://img.saraba1st.com/forum/202401/04/023543l45j44il8uh66zil.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240104-023329__01.jpg</strong> (128.53 KB, 下载次数: 0)

下载附件

2024-1-4 02:35 上传

仅使用SDXL的降噪/添加噪声+降噪的细化结果，添加噪声会降低质量，但在降噪之前可以为全局最优结果奠定基础

<img src="https://img.saraba1st.com/forum/202401/04/023547wn5dn0n7x17x50gd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240104-023329__02.jpg</strong> (116.97 KB, 下载次数: 0)

下载附件

2024-1-4 02:35 上传

使用原始区块质量图/展平图(flattened map)来引导重绘，(a)受到块影响并产生意外伪影，而(b)则具有平滑自然的结果

<img src="https://img.saraba1st.com/forum/202401/04/023553i9f34fjff94gzsdv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240104-023335__01.jpg</strong> (89.19 KB, 下载次数: 0)

下载附件

2024-1-4 02:35 上传

使用盲增强器(blind enhancer)或提示引导增强器(prompt-guided enhancer)来提升AGIQA-3K中不同质量组的图像，盲增强器在低质量组中显示出更好的提升结果，但会对高质量组造成负面优化效果

<img src="https://img.saraba1st.com/forum/202401/04/023559zipidlr6w1i4ic56.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240104-023349__01.jpg</strong> (546.96 KB, 下载次数: 0)

下载附件

2024-1-4 02:35 上传

相关性能评估

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1153#       发表于 2024-1-4 21:07

 本帖最后由 Machinery 于 2024-1-4 21:09 编辑 

En3D

从2D合成数据雕刻3D人体的增强生成式模型

项目主页:https://menyifang.github.io/projects/En3D/index.html

github项目仓库:https://github.com/menyifang/En3D

En3D，一种增强的生成方案，用于雕刻高质量的3D人类化身，与之前依赖稀缺的3D数据集或具有不平衡观察视角和不准确的姿态先验的有限2D数据的方法不同，本方法旨在开发一种零样本3D生成方案，能够在不依赖现有3D或2D资源的情况下生成视觉逼真、几何准确的，以及内容多样的3D人类

为了解决这个挑战，引入了一个精心设计的工作流程，通过准确的物理建模从合成的2D数据中学习增强3D生成模型，在推理过程中，整合了优化模块，以弥补逼真外观和粗略3D形状之间的差距

具体而言，En3D包括三个模块:
1.3D生成器，可以准确地从合成的平衡、多样和结构化的人类图像中建模出具有逼真外观的可普遍适用的3D人类
2.几何雕刻器，利用多视图法线约束来增强形状质量，用于复杂的人体肢体
3.纹理模块，利用语义UV分化(semantical UV partitioning)和可微光栅化器(differentiable rasterizer)来解耦显式的纹理映射，实现纹理的保真度和可编辑性

实验结果表明，本文方法在图像质量、几何准确率以及内容多样性方面明显优于先前的方法，还展示了本文方法生成的角色在动画化和编辑方面的可用性，以及在内容风格自由适应方面的可扩展性

<img src="https://img.saraba1st.com/forum/202401/04/210659amcq2mfmw5j2yrz2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240104-210220__01.jpg</strong> (307.27 KB, 下载次数: 0)

下载附件

2024-1-4 21:06 上传

给定随机噪声或引导文本，本文的生成方案可以合成逼真且几何精确的高保真3D人体化身，这些化身可以随之进行动画化和编辑，本文模型是在2D合成数据上进行训练的，而不依赖于任何现有的3D或2D集合

<img src="https://img.saraba1st.com/forum/202401/04/210717rocpccfo2pp09e9p.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240104-210227__01.jpg</strong> (278.18 KB, 下载次数: 0)

下载附件

2024-1-4 21:07 上传

所提出方案的概览图，包括三个模块:3D生成建模(3D generative modeling/3DGM)，几何雕刻(GS/geometric sculpting)和显式纹理(ET/explicit texturing)

3DGM使用合成的多样化、平衡和结构化的人体图像，并通过准确的摄影机φ来学习具有三面体架构(triplane-based architecture)的可普遍适用的3D人体，GS作为优化模块进行整合，利用多视图法线约束来细化和雕刻几何细节，ET利用UV分化和可微光栅化器来解耦显式的UV纹理映射，不仅可以获得多视图渲染结果，还可以获得逼真的3D模型

<img src="https://img.saraba1st.com/forum/202401/04/210723ybc21frdsgg4obpd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240104-210236__01.jpg</strong> (92.92 KB, 下载次数: 0)

下载附件

2024-1-4 21:07 上传

本文方法的可视化流程图，从输入的噪声、文本或图像中合成带纹理的3D人体化身

<img src="https://img.saraba1st.com/forum/202401/04/210728hi6258fon56ufdm6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240104-210252__01.jpg</strong> (315.57 KB, 下载次数: 0)

下载附件

2024-1-4 21:07 上传

合成的512x512分辨率的3D人体化身的结果

<img src="https://img.saraba1st.com/forum/202401/04/210732q7t7wt0e07ya60ay.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240104-210302__01.jpg</strong> (319.87 KB, 下载次数: 0)

下载附件

2024-1-4 21:07 上传

与三种SOTA方法(EVA3D，AG3D和EG3D)的定性对比

<img src="https://img.saraba1st.com/forum/202401/04/210736jyy6zh2hq0ng6p2a.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240104-210307__01.jpg</strong> (47.61 KB, 下载次数: 0)

下载附件

2024-1-4 21:07 上传

使用FID、IS-360、法线准确率(Normal)和身份一致性(ID)进行定量评估

<img src="https://img.saraba1st.com/forum/202401/04/210740z06oo32np9p3jpjp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240104-210307__02.jpg</strong> (28.89 KB, 下载次数: 0)

下载附件

2024-1-4 21:07 上传

使用估计的物理参数(w/o SYN-P)替换训练模型或移除区块合成渲染(w/o PCR)的结果

<img src="https://img.saraba1st.com/forum/202401/04/210745n1dhkq7sb647ss36.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240104-210316__01.jpg</strong> (80.28 KB, 下载次数: 0)

下载附件

2024-1-4 21:07 上传

GS模块对细粒度表面的雕刻效果

<img src="https://img.saraba1st.com/forum/202401/04/210750dpt20gtlqpcq0pjq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240104-210316__02.jpg</strong> (100.28 KB, 下载次数: 0)

下载附件

2024-1-4 21:07 上传

ET模块对于引导合成的效果

<img src="https://img.saraba1st.com/forum/202401/04/210754pc1rulcpclgwupy1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240104-210316__03.jpg</strong> (113.37 KB, 下载次数: 0)

下载附件

2024-1-4 21:07 上传

将本文方法适用于各种风格(例如卡通角色)或内容(例如肖像头像)的合成结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1154#       发表于 2024-1-5 01:41

 本帖最后由 Machinery 于 2024-1-5 01:42 编辑 

aMUSEd

开源MUSE模型实现

256*256模型权重下载:https://huggingface.co/amused/amused-256

512*512模型权重下载:https://huggingface.co/amused/amused-512

关于MUSE构架的介绍:https://www.51cto.com/article/744895.html

aMUSEd，这是一个基于MUSE架构的开源、轻量级的掩码图像模型(MIM/masked image model)，用于文本到图像的生成，相比于MUSE，aMUSEd只使用了前者10%的参数，并专注于实现快速图像生成

相较于目前潜在扩散的发展，在MIM文本到图像生成领域方面还未得到充分的探索，与潜在扩散相比，MIM需要的推理步骤更少，而且更具有可解释性(more interpretable)，此外，MIM可以通过仅使用单张图像进行微调来学习额外的风格

希望通过展现MIM在大规模文本到图像生成上的有效性，并发布可复现的训练代码，来进一步的鼓励对于MIM的探索，还发布了两个模型的检查点，这些模型可以直接生成256x256和512x512分辨率的图像
————

<img src="https://img.saraba1st.com/forum/202401/05/014040d7q8q7r7r3q77zdi.jpg" referrerpolicy="no-referrer">

<strong>202c6deb-8a01-4973-8c87-756f8a551b25.jpg</strong> (231.46 KB, 下载次数: 0)

下载附件

2024-1-5 01:40 上传

aMUSEd是一个基于MUSE架构的轻量级文本到图像模型，aMUSEd在需要轻量级且快速的应用中(例如一次性快速的生成许多图像)非常有用

<img src="https://img.saraba1st.com/forum/202401/05/014046ahedi7uvf37wpddz.jpg" referrerpolicy="no-referrer">

<strong>190c7d19-56c3-40b2-95f5-7e6e0d0c8b14.jpg</strong> (105.25 KB, 下载次数: 0)

下载附件

2024-1-5 01:40 上传

该图展示了aMUSEd的训练和推理的工作流程

aMUSEd由三个分别训练的组件组成:预训练的CLIP-L/14文本编码器、VQ-GAN和U-ViT

在训练过程中，VQ-GAN编码器将图像映射到小16倍的潜在分辨率，掩码潜在Token的比例是从余弦掩码方案中采样的，例如cos(r · π 2 ) with r ∼ Uniform(0, 1)

模型通过交叉熵损失(cross-entropy loss)进行训练，以预测被遮蔽的Token，在对256x256图像进行训练之后，添加了下采样和上采样层，并继续在512x512图像上进行训练

在推理过程中，U-ViT以文本编码器的隐藏状态(hidden states)作为条件，为所有被遮蔽的Token迭代式的预测值(values)，余弦掩码方案决定了每次迭代后要固定的最可信Token(most confident token)预测的百分比，经过12次迭代，所有Token都被预测并由VQ-GAN解码回图像像素
————
性能

aMUSEd继承了原始MUSE的性能优势

<img src="https://img.saraba1st.com/forum/202401/05/014106hjzjj61ywao02wrj.png" referrerpolicy="no-referrer">

<strong>PEVklboNHZ1dgrco8Mu_-.png</strong> (137.7 KB, 下载次数: 0)

下载附件

2024-1-5 01:41 上传

1.并行解码:该模型遵循去噪方案，在每个去噪步骤中揭示一定百分比的Token，在每个步骤中，预测所有被遮蔽的Token，并揭示一些网络最有信心的Token，由于同时预测多个标记，可以在大约12个步骤内生成完整的256x256或512x512图像，相比之下，自回归模型必须一次预测一个Token，请注意，使用16倍下采样VAE的MUSE的256x256图像将有256个Token

2.更少的采样步骤:与许多扩散模型相比，MUSE需要的采样更少

此外，与MUSE相比，aMUSEd使用更小的CLIP作为其文本编码器，而不是T5，与最大的3B参数MUSE模型相比，aMUSEd更小，大约只有600M参数，同时请注意，由于尺寸较小，aMUSEd可能会产生相对较低质量的结果

<img src="https://img.saraba1st.com/forum/202401/05/014126wu4ovoyhzkbh8xun.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-014115.jpg</strong> (40.72 KB, 下载次数: 0)

下载附件

2024-1-5 01:41 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1155#       发表于 2024-1-5 06:29

 本帖最后由 Machinery 于 2024-1-5 06:31 编辑 

Image Sculpting

通过3D几何控制(3D Geometry Control)进行精准的对象编辑

项目主页:https://image-sculpting.github.io/

github项目代码仓库:https://github.com/vision-x-nyu/image-sculpting

<img src="https://img.saraba1st.com/forum/202401/05/062655phenhbbhtuxutpcb.png" referrerpolicy="no-referrer">

<strong>teaser3.png</strong> (976.46 KB, 下载次数: 0)

下载附件

2024-1-5 06:26 上传

本文提出了一种名为Image Sculpting的新框架，可以通过3D几何和图形学以及对应的工具来编辑2D图像，这种方法与现有方法有着显著区别，现有方法受限于2D空间，并且通常依赖于文本指令，导致了分歧和受限的控制能力

Image Sculpting将2D对象转换为3D，使之能够直接与转换后的3D几何进行交互，在编辑后，这些对象被重新渲染为2D图像，并与原始图像合并，通过粗到细的增强过程产生高保真度的结果

本文框架支持精确、可量化的和物理上拟似的编辑选项(precise, quantifiable, and physically-plausible editing options)，如姿态编辑、旋转、转换、3D组合、雕刻和连续添加，这是将生成模型的创意自由与图形工作流程的精准相结合的初步尝试
————
部分演示结果(请前往项目页面查看)

<img src="https://img.saraba1st.com/forum/202401/05/062727o40axeh7qxmaa4s4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-052927.jpg</strong> (115.91 KB, 下载次数: 0)

下载附件

2024-1-5 06:27 上传

<img src="https://img.saraba1st.com/forum/202401/05/062727jsfsrrtztlbve42r.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-053011.jpg</strong> (109.68 KB, 下载次数: 0)

下载附件

2024-1-5 06:27 上传

<img src="https://img.saraba1st.com/forum/202401/05/062727wfgcoc5puhcpods8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-053234.jpg</strong> (128.43 KB, 下载次数: 0)

下载附件

2024-1-5 06:27 上传

<img src="https://img.saraba1st.com/forum/202401/05/062727qu8hfug8zz4qjiiq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-053246.jpg</strong> (138.8 KB, 下载次数: 0)

下载附件

2024-1-5 06:27 上传

<img src="https://img.saraba1st.com/forum/202401/05/062727hqobqdqqqbyf343o.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-053305.jpg</strong> (158.17 KB, 下载次数: 0)

下载附件

2024-1-5 06:27 上传

<img src="https://img.saraba1st.com/forum/202401/05/062728cudy56idhp6b699m.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-053321.jpg</strong> (125.3 KB, 下载次数: 0)

下载附件

2024-1-5 06:27 上传

————
框架

所提出的图像雕刻框架，形象地来说类似于在3D空间中对2D图像进行灵活和精确的雕刻，集成了三个关键组件:
1.单视图3D重建
2.在3D空间中操作物体
3.从粗到细的生成增强过程

具体而言，2D对象被转换为3D模型，使用户能够直接操作和编辑3D几何体，从而实现精确的编辑，然后，修改过的对象随后无缝地重新融入其原始或新的2D背景中，保持视觉上的一致性和保真度

(1) 单视图3D重建

<img src="https://img.saraba1st.com/forum/202401/05/062752wmywqnmmmmw8cu0r.jpg" referrerpolicy="no-referrer">

<strong>reconstruct.jpg</strong> (562.59 KB, 下载次数: 0)

下载附件

2024-1-5 06:27 上传

该过程始于将输入图像通过逆渲染(de-rendering)过程转换为纹理3D模型，给定一个物体的图像，目标是进行3D重建，以获得3D模型

图像到三3D模型的转换的初始步骤涉及从输入的图像中使用SAM分割出所选的物体，在此基础上，使用Zero-1-to-3和分数蒸馏采样(SDS)对NeRF模型进行训练，然后使用等值立方搜寻算法(Marching cubes)和纹理将NeRF体积(NeRF volume)转换为纹理网格

(2) 3D形变

<img src="https://img.saraba1st.com/forum/202401/05/062803xlerrfirhrlhra4d.jpg" referrerpolicy="no-referrer">

<strong>deformation.jpg</strong> (658.61 KB, 下载次数: 0)

下载附件

2024-1-5 06:28 上传

然后，将3D模型预备为可交互的形变状态(interactive deformation)，方法是创建一个骨架并计算蒙皮权重(skinning weights)，用户可以修改骨架以对3D模型进行形变，从而得到一个初始的粗略图像

在获得3D模型之后，用户可以手动构建骨架并通过旋转骨骼进行交互操作，以实现目标姿态，网格形变会影响物体的顶点位置(vertex positions)，但不会影响用于纹理映射的UV坐标；因此，该过程会随着物体的形变而扭曲纹理映射在物体上的贴图

然而，最终的图像质量取决于3D重建的准确性，在本文用例中，重建结果粗略并且无法满足预期的视觉效果，因此，还依赖于图像增强流程将粗略渲染转换为高质量输出

(3) 从粗到细的生成式增强
这一部分的重点是将一幅粗略渲染的图像与其原始背景混合在一起，目标是在保持编辑后的几何形状完好无损的同时恢复纹理细节，图像恢复和增强通常被视为图像到图像的转换任务，利用源图像和目标图像之间的强关联性，然而，本文的挑战还呈现了一种独特的情形:尽管输入图像和期望输出之间在外观和纹理上有整体相似之处，但在用户对几何进行编辑后，输入对象的几何形状有时变化会很大

<img src="https://img.saraba1st.com/forum/202401/05/062815ddbz70daprpc00r6.jpg" referrerpolicy="no-referrer">

<strong>dreambooth.jpg</strong> (335.77 KB, 下载次数: 0)

下载附件

2024-1-5 06:28 上传

为了在保留纹理和几何结构之间取得平衡，本文方法首先通过“个性化(personalizing)”，一个预训练的文本到图像扩散模型来进行处理，为了捕捉物体的关键特征，使用一张输入参考图像通过DreamBooth对扩散模型进行微调，为了维持几何结构，还采用了特征和注意力注入技术，该技术最初是为了语义布局控制而设计的。此外，还通过ControlNet将3D模型的对应深度数据整合进来，最终确定这种整合对于在增强过程中减少不确定性非常重要

单样本的DreamBooth
使用少量图像对预训练的扩散模型进行微调，以进行主题驱动(subject-driven)的生成，原始的DreamBooth论文已经展示了它利用语义类别先验来生成给定图像的新视图的能力，仅需要给出了该主题的一些正面图像，在本文场景中，这一方面特别有用，因为处理的粗略渲染缺乏明确的视点信息，在实际应用中，只使用单个样本(即输入图像)来训练DreamBooth，值得注意的是，DreamBooth的这种单样本方法还有效地捕捉了详细的纹理，从而填充了粗略渲染中存在的纹理缺失

深度控制
使用了深度ControlNet来保留用户编辑的几何信息，深度图直接从形变的3D模型中渲染，无需进行任何单目深度估计，对于背景区域，不使用深度图，深度图可以作为空间控制信号，指导最终编辑图像中的几何生成，然而，仅仅依靠深度控制是不够的-尽管它可以在一定程度上保留几何结构，但在局部的、更微妙的编辑中仍然存在困难

<img src="https://img.saraba1st.com/forum/202401/05/062837jgs53bgav8vavfez.jpg" referrerpolicy="no-referrer">

<strong>enhancement.jpg</strong> (363.74 KB, 下载次数: 0)

下载附件

2024-1-5 06:28 上传

为了细化这张编辑过的图像，将粗略的渲染反转为噪声，然后将自注意力图和特征图从初始图像的去噪过程中注入到增强图像的去噪步骤中，这种技术有助于保留修改对象的几何形状，并恢复编辑图像的视觉质量，DDIM+代表使用经过DreamBooth微调和深度控制模型的DDIM技术

特征注入
为了更好地保留几何结构，使用了特征注入，这一步骤从粗略渲染图像的DDIM反演开始(使用DreamBooth微调的、深度控制扩散模型)，以获取反转的潜在，在每个去噪步骤中，对粗略渲染的反转潜变量以及细化图像的潜在进行去噪，提取它们各自的特征图(从残差块中)和自注意图(从Transformer块中)，PnP的论文中已经证明了特征图中携带着语义信息，而自注意图包含生成图像的几何和布局信息，通过在增强图像的去噪步骤中使用来自粗略版本的特征和自注意图覆盖特征和自注意图，可以确保增强图像的几何结构能够正确反映粗略渲染的几何结构
————
对比

本文方法通过精确的3D几何控制引入了新的编辑功能，这是现有方法中不存在的功能，将本文方法与SOTA对象编辑技术进行了对比以进行全面分析

<img src="https://img.saraba1st.com/forum/202401/05/062852nyf6d8zydw2qlffd.jpg" referrerpolicy="no-referrer">

<strong>7ebc8ffa-6c59-4a02-b178-8993623257cf.jpg</strong> (176.56 KB, 下载次数: 0)

下载附件

2024-1-5 06:28 上传

与OBJect-3DIT的对比，关于对象转换、旋转和组合

在这个图示中，展示了3DIT，它是为了通过语言指令进行3D感知编辑而设计的，但是当应用于真实的、复杂的图像时，它面临着问题，这主要是因为它的训练是基于合成数据集的

<img src="https://img.saraba1st.com/forum/202401/05/062908jkcr8ougu0it8u0v.jpg" referrerpolicy="no-referrer">

<strong>a2875de2-9acf-4d73-a01d-c7b76adfc774.jpg</strong> (227.21 KB, 下载次数: 0)

下载附件

2024-1-5 06:29 上传

与DragDiffusion和ControlNet在姿态编辑方面进行对比，这些技术在处理复杂的姿态修改时面临困难

<img src="https://img.saraba1st.com/forum/202401/05/062923eh1ftpptja66jpis.jpg" referrerpolicy="no-referrer">

<strong>e338ec99-06ca-45f5-93f1-268eea0895e3.jpg</strong> (198.89 KB, 下载次数: 0)

下载附件

2024-1-5 06:29 上传

与InstructPix2Pix和DALL·E 3在连续添加任务上的对比，这些基于文本的编辑方法无法按照精确和可量化的指令进行操作

此外，还展示了像InstructPix2Pix和DALL·E 3这样的基于文本的编辑方法在处理精确和可量化的指令时遇到的困难

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1156#       发表于 2024-1-5 07:57

PLLaMa

植物科学的开源大型语言模型

github项目仓库:https://github.com/Xianjun-Yang/PLLaMa

hugface 7b基础模型:https://huggingface.co/Xianjun/PLLaMa-7b-base

hugface 13b基础模型:https://huggingface.co/Xianjun/PLLaMa-13b-base

大型语言模型(LLMs)在各个领域展示出了对自然语言的卓越理解和交互能力，然而，在植物科学等需要高准确性的专业领域，它们的效果受限，这主要是缺乏领域的特定专业知识所导致的

本文介绍了PLLaMa，一个从LLaMa-2演化而来的开源语言模型，通过一个包含150多万篇植物科学学术文章的全面数据库进行了增强，这成功丰富了PLLaMa在植物和农业科学方面的知识和能力

进行了涉及与植物和农业相关的特定数据集的初步测试，结果展现了PLLaMa在理解植物科学相关主题方面的显著提高，此外，还组建了一个国际专业人员小组，包括植物科学家、农业工程师和植物育种学家，团队在验证PLLaMa对各种学术问题的回答准确性方面起着关键作用，确保了其在实际应用中的有效性和可靠性

为了支持进一步的研究和发展，已经将该模型的检查点和源代码开源

<img src="https://img.saraba1st.com/forum/202401/05/075700acc7lw2vyy2ueqqj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-075339.jpg</strong> (83.78 KB, 下载次数: 0)

下载附件

2024-1-5 07:56 上传

PLLaMa的训练流程

<img src="https://img.saraba1st.com/forum/202401/05/075704fcdc4fshd4of7ie1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-075559.jpg</strong> (598.58 KB, 下载次数: 0)

下载附件

2024-1-5 07:57 上传

PLLaMa-13B-Chat生成的问题和解答

<img src="https://img.saraba1st.com/forum/202401/05/075708thfftzvy2mhyhfth.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-075611.jpg</strong> (718.97 KB, 下载次数: 0)

下载附件

2024-1-5 07:57 上传

由 LLaMa-13B-Chat生成的问题和答案预测

<img src="https://img.saraba1st.com/forum/202401/05/075713f4unlok70a54ndi4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-075618.jpg</strong> (112.68 KB, 下载次数: 0)

下载附件

2024-1-5 07:57 上传

预训练损失曲线

<img src="https://img.saraba1st.com/forum/202401/05/075717e5umaqbbrruzm18a.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-075626.jpg</strong> (68.16 KB, 下载次数: 0)

下载附件

2024-1-5 07:57 上传

指令微调损失曲线

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1157#       发表于 2024-1-5 18:58

TinyLlama

开源小型语言模型

github项目主页:https://github.com/jzhang38/TinyLlama

TinyLlama，一个紧凑的1.1B参数语言模型，在大约1万亿个Token上进行了预训练，训练时间约为3个epochs，在Llama 2的架构和分词器的基础上，TinyLlama利用了开源社区贡献的各种新技术(例如FlashAttention)，实现了更好的计算效率，尽管参数规模相对较小，但TinyLlama在一系列下游任务中展现出了卓越的性能，它在可相比较大小的现有开源语言模型中表现出色，模型的检查点和代码可以在GitHub上公开获取

github项目说明页截图:

<img src="https://img.saraba1st.com/forum/202401/05/185813vht4gxn6nx4t9t4x.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-185702.jpg</strong> (224.31 KB, 下载次数: 0)

下载附件

2024-1-5 18:58 上传

<img src="https://img.saraba1st.com/forum/202401/05/185813x09sgh0bqbgqgwwq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-185711.jpg</strong> (298.72 KB, 下载次数: 0)

下载附件

2024-1-5 18:58 上传

<img src="https://img.saraba1st.com/forum/202401/05/185813j1117yxe5e1xqb7q.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-185721.jpg</strong> (108.48 KB, 下载次数: 0)

下载附件

2024-1-5 18:58 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1158#       发表于 2024-1-5 21:34

 本帖最后由 Machinery 于 2024-1-5 21:37 编辑 

LLaMA Pro

具有块扩展(Block Expansion)的渐进式LLaMA

github项目主页:https://github.com/TencentARC/LLaMA-Pro

人类通常会在学习新技能的同时保持对旧技能的掌握，但是对于大型语言模型(LLMs)来说情况恰恰相反，例如，将LLaMA调整成CodeLLaMA

为此，本文提出了一种新的LLM后预训练处理方法(post-pretraining method)，通过扩展Transformer blocks，只使用新语料库来调整扩展的blocks，有效而效率的提升模型的知识，同时避免灾难性遗忘

在本文中，于代码和数学语料库上进行了实验，得到了LLaMA Pro-8.3B，一个多功能的基础模型，从LLaMA2-7B初始化而来，在通用任务、编程和数学方面表现出色

LLaMA Pro及其遵循指令的对应模型(LLaMA Pro-Instruct)在各种基准测试中取得了领先性能，证明了其在LLaMA家族中的现有开放模型之上的优越性，以及作为智能代理者在推理和解决多样任务方面的巨大潜力

本文的研究结果为将自然语言和编程语言整合提供了有价值的见解，为开发在各种环境中有效运作的高级语言代理者奠定了坚实基础

<img src="https://img.saraba1st.com/forum/202401/05/213308pzend555x5g0o011.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-212940.jpg</strong> (131.63 KB, 下载次数: 0)

下载附件

2024-1-5 21:33 上传

LLaMA Pro-Instruct在广泛的各种任务中展现出的SOTA性能，从通用语言到特定领域，优于LLaMA系列的现有模型

<img src="https://img.saraba1st.com/forum/202401/05/213315udvrk9crd9ekfe5z.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-212954.jpg</strong> (144.72 KB, 下载次数: 0)

下载附件

2024-1-5 21:33 上传

(a)从大型语言模型开始，该模型在一个庞大的未标记语料库上进行预训练，从而获得强大的通用能力，这里选择了现成的LLaMA2模型以便于使用

(b)在保留从基础模型继承的冻结的blocks的同时，拓展骨干并使用相关语料库微调扩展的身份blocks(backbone expansion and fine-tune the expanded identity blocks)，后预训练(post-pretraining)的模型可以像通常一样进行指令调整

<img src="https://img.saraba1st.com/forum/202401/05/213323xjgdherq9lddmmjg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-213026.jpg</strong> (207.97 KB, 下载次数: 0)

下载附件

2024-1-5 21:33 上传

(a)LLaMA块的概述，包括MHSA机制与之后带有SwiGLU激活的FFN

(b)经过身份复制之后的LLaMA身份blocks，通过将输出线性矩阵初始化为零，以保留基础模型的输出

<img src="https://img.saraba1st.com/forum/202401/05/213329rh2d8ab83o9t2bgd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-213037.jpg</strong> (80.63 KB, 下载次数: 0)

下载附件

2024-1-5 21:33 上传

预训练数据源，Token以及在训练过程中每个组成部分的混合权重

<img src="https://img.saraba1st.com/forum/202401/05/213335gobh1olbynr1rmlz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-213052.jpg</strong> (74.73 KB, 下载次数: 0)

下载附件

2024-1-5 21:33 上传

本研究调查的指令数据集，报告了平均回合数(N¯ rounds)，平均提示长度(L¯ prompt)，平均完成长度(L¯ completion)

<img src="https://img.saraba1st.com/forum/202401/05/213349yp0nuhu667s0cn6u.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-213108.jpg</strong> (158.07 KB, 下载次数: 0)

下载附件

2024-1-5 21:33 上传

一系列优秀的代码和语言模型的评估对比结果

<img src="https://img.saraba1st.com/forum/202401/05/213359pqejjp2q2ze2pe22.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-213120.jpg</strong> (84.82 KB, 下载次数: 0)

下载附件

2024-1-5 21:33 上传

将LLAMA PRO的整体和代码性能与一组在同一时间训练的模型进行了对比，包括通用LLM和面向代码的LLM，图中的斑点大小与训练的Token数量成正例，由于Mistral-7B的论文中没有报告Token数量，因此没有在此包括它

<img src="https://img.saraba1st.com/forum/202401/05/213405w23uf02fgyabrbfx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-213129.jpg</strong> (66.72 KB, 下载次数: 0)

下载附件

2024-1-5 21:34 上传

GPT-4对Chatbot模型进行的自动评估，LLaMA Pro-Instruct在广泛使用的LLaMA社区聊天机器人中表现优异

<img src="https://img.saraba1st.com/forum/202401/05/213409xs5j7ncuzngsuhcq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-213146.jpg</strong> (92.47 KB, 下载次数: 0)

下载附件

2024-1-5 21:34 上传

在工具增强的推理测试中，评估了模型在将工具集成到推理工作流程中的熟练程度，模型的有效性通过其在各个交互阶段的成功率来衡量

<img src="https://img.saraba1st.com/forum/202401/05/213415ljop6kkjooskcp4k.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-213159.jpg</strong> (40.9 KB, 下载次数: 0)

下载附件

2024-1-5 21:34 上传

在使用LLaMA2-7B进行连续学习阶段后，各种训练策略在TRACE基准测试中的性能对比，该表格展示了每种策略的总体性能(OP)和逆向迁移(BWT)的得分，展示了所提出的blocks扩展训练方法的出色适应性

<img src="https://img.saraba1st.com/forum/202401/05/213420ldf21j2ff1bdffj4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-213208.jpg</strong> (102.05 KB, 下载次数: 0)

下载附件

2024-1-5 21:34 上传

训练损失随着增加的blocks数和专家混合(MoE)扩展而变化

<img src="https://img.saraba1st.com/forum/202401/05/213427nbbpux8422lu8zp3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-213221.jpg</strong> (126.47 KB, 下载次数: 0)

下载附件

2024-1-5 21:34 上传

对比了几个优秀的代码和语言模型的评估结果，最后一列表示语言任务平均和代码任务平均的平均值

<img src="https://img.saraba1st.com/forum/202401/05/213432fogbbv9pgoj7bbbk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-213227.jpg</strong> (32.93 KB, 下载次数: 0)

下载附件

2024-1-5 21:34 上传

通过使用相同的指令数据集对LLaMA2-7B和LLAMA PRO进行微调，LLAMA PRO在所有任务中始终优于LLaMA2-7B，这个结果突显了本文方法的有效性，因为这证明了LLAMA PRO在预训练过程中成功地编码了更多的领域知识

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1159#       发表于 2024-1-5 22:38

LLaVA-phi

使用小型语言模型作为高效的多模态助手

github项目仓库:https://github.com/zhuyiche/llava-phi

LLaVA-ϕ(LLaVA-Phi)，一种高效的多模态助手，通过利用最近出现的先进小型语言模型Phi-2的力量来促进多模态对话的发展，在紧凑的多模态模型领域中取得了显著的进步，它表明，即使只是参数只有27亿的小型的语言模型，只要经过高质量的语料库训练，就可以有效地进行融合了文本和视觉元素的复杂对话

LLaVA-Phi在公开可用的评估数据集上展现出了令人称赞的性能，其中包括视觉理解、推理和基于知识的感知，除了在多模态对话任务中表现出卓越的性能外，本文模型还为在时间需求型的环境和实时交互系统(如具身代理者)中的应用开辟了新的途径，它突显了小型语言模型在实现复杂水平的理解和互动方面的潜力，同时保证了更高的资源效率

<img src="https://img.saraba1st.com/forum/202401/05/223746t6xxcb4859bif0fn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-223625.jpg</strong> (392.16 KB, 下载次数: 0)

下载附件

2024-1-5 22:37 上传

LLaVA-Phi擅长通过共情推理识别和回答复杂问题

<img src="https://img.saraba1st.com/forum/202401/05/223751x7xssys7icudcccj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-223645.jpg</strong> (258.49 KB, 下载次数: 0)

下载附件

2024-1-5 22:37 上传

LLaVA-Phi可以根据视觉输入和命令生成有用的代码

<img src="https://img.saraba1st.com/forum/202401/05/223755lree7e70qy5w4ykq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-223701.jpg</strong> (158.23 KB, 下载次数: 0)

下载附件

2024-1-5 22:37 上传

多模态基准测试的多模态评估，由于空间限制，基准名称被缩写

<img src="https://img.saraba1st.com/forum/202401/05/223759nqm9dznggug8atfj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240105-223713.jpg</strong> (149.33 KB, 下载次数: 0)

下载附件

2024-1-5 22:37 上传

LLaVA-Phi能够对数学方程进行精确的OCR并相应地进行求解

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1160#       发表于 2024-1-8 01:39

 本帖最后由 Machinery 于 2024-1-8 01:41 编辑 

OpenVoice

多功能即时语音克隆

相关研究博客:https://research.myshell.ai/open-voice

github项目主页:https://github.com/myshell-ai/OpenVoice

演示demo:https://huggingface.co/spaces/myshell-ai/OpenVoice

模型权重下载:
1.https://myshell-public-repo-hosting.s3.amazonaws.com/checkpoints_1226.zip
2.https://huggingface.co/myshell-ai/OpenVoice

OpenVoice，一种多功能的语音克隆(voice cloning)方法，只需要参考说话者的一个较短的音频片段，就可以复制相关声音并生成多种语言的语音

OpenVoice在以下领域的开放挑战中取得了重大进展:
1.灵活的语音风格控制，OpenVoice可以对语音风格进行粒度控制，包括情感、口音、节奏、停顿和语调(emotion, accent, rhythm, pauses, and intonation)，还可以复制参考的说话者的音色，这些语音风格不是直接从参考说话者那里复制并受限制的，先前的方法在克隆之后缺乏灵活操纵语音风格的能力

2.零样本跨语言语音克隆，OpenVoice实现了对未包含在大规模说话者训练集中的语言进行零样本跨语言语音克隆，与先前的方法不同，那些方法通常需要包含所有语言的大规模说话者多语言(MSML/massive-speaker multi-lingual)数据集，而OpenVoice可以在没有任何用于该语言的大规模说话者训练数据的情况下将声音克隆到新的语言中

OpenVoice的计算效率也很高，成本比性能更差的商用API低数十倍，为了促进该领域的进一步研究，已经公开了源代码和训练模型，还在演示网站上提供了定性结果

在公开发布之前，本文内部版本的OpenVoice作为MyShell的后端在2023年5月至10月期间已经被全球用户使用了数千万次

<img src="https://img.saraba1st.com/forum/202401/08/013901kt3cqk3332ta3vj3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240108-013239.jpg</strong> (58.44 KB, 下载次数: 0)

下载附件

2024-1-8 01:39 上传

OpenVoice框架的插图，使用了基本说话人模型来控制风格和语言，并使用转换器将参考说话人的音色体现到语音中

<img src="https://img.saraba1st.com/forum/202401/08/014113dt63e29o93ejz6v7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240108-014049.jpg</strong> (302.17 KB, 下载次数: 0)

下载附件

2024-1-8 01:41 上传

hugface权重语言声明:这个版本的权重只支持英文和中文，OpenVoice可以适应任何其他语言，只要提供一个基础说话人，有关多语言和跨语言的示例，请参考这个jupyter笔记本(相关链接:https://github.com/myshell-ai/OpenVoice/blob/main/demo_part2.ipynb)

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1161#       发表于 2024-1-8 19:03

 本帖最后由 Machinery 于 2024-1-8 19:07 编辑 

DeepSeek LLM

以长期主义的理念扩展开源语言模型

github项目主页:https://github.com/deepseek-ai/deepseek-LLM

hugface权重下载

deepseek-llm-7b-base:https://huggingface.co/deepseek-ai/deepseek-llm-7b-base

deepseek-llm-7b-chat:https://huggingface.co/deepseek-ai/deepseek-llm-7b-chat

deepseek-llm-67b-base:https://huggingface.co/deepseek-ai/deepseek-llm-67b-base

deepseek-llm-67b-chat:https://huggingface.co/deepseek-ai/deepseek-llm-67b-chat

开源大型语言模型快速发展，然而，之前的论文中描述的缩放法则(scaling law)各自含有不同的结论与观点，这给LLM的发展带来了阴云，通过深入研究了缩放法则，本文提出了独特的发现，这有助于在两种常用的开源配置(7B和67B)中扩展大型语言模型

同时，在缩放法则的指导下，推出了DeepSeek LLM项目，致力于以长期主义的理念推进开源语言模型的发展，为了支持预训练阶段，构建了一个数据集，目前包含2万亿Token，且仍然在不断拓展中，还对DeepSeek LLM基础模型进行了监督微调(SFT)和直接偏好优化(DPO/Direct Preference Optimization)，从而创造了DeepSeek Chat系列模型

评估结果表明，DeepSeek LLM 67B在各种基准测试中超过了LLaMA-2 70B，尤其是代码、数学和推理，此外，开放式评估表明，与GPT-3.5相比，DeepSeek LLM 67B Chat表现出更优异的性能

<img src="https://img.saraba1st.com/forum/202401/08/190203i5ks1ko61f9s9rfs.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240108-185440__01.jpg</strong> (503.69 KB, 下载次数: 0)

下载附件

2024-1-8 19:02 上传

1e17和1e20 FLOPs情况下，批大小和学习率的训练损失

<img src="https://img.saraba1st.com/forum/202401/08/190210if7fffxdjhxv5bf5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240108-185459__01.jpg</strong> (174.95 KB, 下载次数: 0)

下载附件

2024-1-8 19:02 上传

批大小和学习率的缩放曲线，灰色圆圈表示模型的泛化误差最多超出最小值0.25%，虚线表示适用于较小模型的最强缩放拟合线，蓝色星星表示DeepSeek LLM 7B和67B模型

<img src="https://img.saraba1st.com/forum/202401/08/190216n62ay5s20sa82amm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240108-185507__01.jpg</strong> (148.23 KB, 下载次数: 0)

下载附件

2024-1-8 19:02 上传

非嵌入参数𝑁1和完整参数𝑁2的分化相对于FLOPs/token 𝑀的模型缩放规模表示的差异

<img src="https://img.saraba1st.com/forum/202401/08/190227gx7k6n7snxsxt5s5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240108-185513__01.jpg</strong> (162.95 KB, 下载次数: 0)

下载附件

2024-1-8 19:02 上传

IsoFLOP曲线和最优模型/数据分配，在IsoFLOP曲线中，指标是验证集上的每字节比特数(bits-per-byte)，最佳模型/数据缩放曲线中的虚线表示拟合较小模型(灰色圆圈)的最强缩放拟合线

<img src="https://img.saraba1st.com/forum/202401/08/190236a9dmb9t41uugaugt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240108-185520__01.jpg</strong> (66.97 KB, 下载次数: 0)

下载附件

2024-1-8 19:02 上传

性能缩放曲线，指标是验证集上的每字节比特数，虚线表示拟合较小模型(灰色圆圈)的最强缩放拟合线，蓝色星星代表DeepSeek LLM 7B和67B，它们的性能很好地符合了缩放曲线的预测

<img src="https://img.saraba1st.com/forum/202401/08/190243ycjv3t3utavv2tuu.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240108-185527__01.jpg</strong> (117.09 KB, 下载次数: 0)

下载附件

2024-1-8 19:02 上传

模型缩放和数据缩放的系数随训练数据分布的不同而变化

<img src="https://img.saraba1st.com/forum/202401/08/190249t2hiivxvx0pgp2tm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240108-185604__01.jpg</strong> (279.68 KB, 下载次数: 0)

下载附件

2024-1-8 19:02 上传

主要评估结果，本文报告的评估结果基于内部评估框架，粗体数字表示4个模型中的最佳结果，对于Pile-test，报告BPB/bits-per-byte，对于DROP，报告F1分数，对于其他任务，报告准确率

请注意，测试样本(test-shots)是最大值，由于上下文长度有限或可用的少样本示例(few-shot)有限等情况，在阅读理解任务(例如RACE)中，可能会应用较少的提示样本

<img src="https://img.saraba1st.com/forum/202401/08/190258u2l7hhpl8r9rdflj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240108-185617__01.jpg</strong> (286.82 KB, 下载次数: 0)

下载附件

2024-1-8 19:02 上传

基础模型和对话模型之间的对比，对于对话模型，进行了零样本评估，评估指标包括MMLU、GSM8K、MATH、C-Eval和CMMLU，而基础模型的结果仍然是在少样本设置下获得的

<img src="https://img.saraba1st.com/forum/202401/08/190304skfrsggwgzeisw5g.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240108-185625__01.jpg</strong> (396.2 KB, 下载次数: 0)

下载附件

2024-1-8 19:03 上传

使用gpt-4-0613评估的AlignBench排行榜，模型按照总分从高到低排列，带有*的结果是基于官方AlignBench存储库的评估结果，而其他所有结果都来自AlignBench论文，Deepseek-67B-Chat模型结果中明显的超越了ChatGPT和其他基线模型，这表明在基础中文语言任务和高级中文推理任务方面本文模型具有卓越的性能，此外，还发现DPO过程在几乎所有领域都带来了改进

<img src="https://img.saraba1st.com/forum/202401/08/190314b2kt7j22d4cm4tbj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240108-185632__01.jpg</strong> (152.3 KB, 下载次数: 0)

下载附件

2024-1-8 19:03 上传

MT-Bench评估结果

<img src="https://img.saraba1st.com/forum/202401/08/190322d6jy3ee6348yj66y.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240108-185638__01.jpg</strong> (76.72 KB, 下载次数: 0)

下载附件

2024-1-8 19:03 上传

使用保留数据集进行的评估

<img src="https://img.saraba1st.com/forum/202401/08/190326pidwwrdcgrge2295.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240108-185646__01.jpg</strong> (256.79 KB, 下载次数: 0)

下载附件

2024-1-8 19:03 上传

安全评估分类，每个类别的测试用例总数以及本文模型DeepSeek-67B-Chat提供的安全答案数量列在表格的最右侧列中，测试问题的标注和生成结果的评估都由专业人员团队进行，可以观察到，本文模型在各种类型的安全测试集中展现出强大的安全性

<img src="https://img.saraba1st.com/forum/202401/08/190331jp6cuvwoj0vpwwcj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240108-185651__01.jpg</strong> (54.22 KB, 下载次数: 0)

下载附件

2024-1-8 19:03 上传

“Do-Not-Answer Score(Wang et al., 2023)”是一项评估模型安全性的指标，得分越高表示模型的安全性越高，带有*的结果是基于官方仓库的评估结果，而其他所有结果都来自原始论文，可以发现，本文模型的安全得分比ChatGPT和GPT-4都要高，在最安全的模型中排名较高

<img src="https://img.saraba1st.com/forum/202401/08/190337iokoh3rkt89939zv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240108-185705__01.jpg</strong> (64.17 KB, 下载次数: 0)

下载附件

2024-1-8 19:03 上传

两阶段微调结果，重复比(repetition ratio)是在温度(temperature)为0时计算的，重复比越低越好，IFEval的结果是提示级的宽松准确率(prompt-level loose accuracy)

<img src="https://img.saraba1st.com/forum/202401/08/190342whzpfa1jhzkjhaap.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240108-185705__01.jpg</strong> (64.17 KB, 下载次数: 0)

下载附件

2024-1-8 19:03 上传

添加多项选择题数据的影响

<img src="https://img.saraba1st.com/forum/202401/08/190346pmtybfiticjb4mmv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240108-185705__02.jpg</strong> (66.99 KB, 下载次数: 0)

下载附件

2024-1-8 19:03 上传

添加系统提示(system prompt)的影响

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1162#       发表于 2024-1-8 19:25

Segmind Stable Diffusion/Segmind-Vega

使用层级损失(Layer Level Loss)对Stable Diffusion XL进行渐进式蒸馏

hugface SSD-1B模型权重:https://huggingface.co/segmind/SSD-1B

hugface Segmind-Vega模型权重:https://huggingface.co/segmind/Segmind-Vega

SDXL因其多功能性和顶尖的图像质量已成为最好的开源文本到图像模型之一，高效地解决SDXL模型的计算需求对于扩大其覆盖范围和适用性至关重要

在这项工作中，引入了两个缩小版本，Segmind Stable Diffusion(SSD-1B)和Segmind-Vega，分别应用了1.3B和0.74B参数的UNet，通过使用层级损失进行渐进性剪枝，重点在于减小模型的大小同时保持生成质量

本文方法包括从SDXL的U-Net结构中消除残差网络(residual networks)和Transformer块(transformer blocks)，从而显著减少参数和延迟

紧凑的模型通过利用转移的知识有效地模仿了原始的SDXL，与更大的数十亿参数的SDXL相比取得了竞争性的结果，本文工作强调了知识蒸馏和层级损失在减小模型大小同时保持SDXL高质量生成能力方面的有效性，从而使之在资源受限环境中更容易部署

<img src="https://img.saraba1st.com/forum/202401/08/192451cgmdnmgtlf8d3cng.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240108-192206__01.jpg</strong> (227.96 KB, 下载次数: 0)

下载附件

2024-1-8 19:24 上传

上图分别为SDXL U-Net、 SSD-1B U-Net、Vega U-Net的结构

<img src="https://img.saraba1st.com/forum/202401/08/192457u9c6z959bm0e9rtb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240108-192214__01.jpg</strong> (47.07 KB, 下载次数: 0)

下载附件

2024-1-8 19:24 上传

推理延迟测试

<img src="https://img.saraba1st.com/forum/202401/08/192502dwovnw3npvn3dvuq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240108-192230__01.jpg</strong> (445.8 KB, 下载次数: 0)

下载附件

2024-1-8 19:25 上传

<img src="https://img.saraba1st.com/forum/202401/08/192502db2cfaa7012z2wfo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240108-192248__01.jpg</strong> (417.84 KB, 下载次数: 0)

下载附件

2024-1-8 19:25 上传

生成结果对比

<img src="https://img.saraba1st.com/forum/202401/08/192507m8p775317gy5z128.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240108-192254__01.jpg</strong> (19.08 KB, 下载次数: 0)

下载附件

2024-1-8 19:25 上传

用户偏好研究

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1163#       发表于 2024-1-9 02:56

DenoisingViT

去噪视觉Transformer

项目主页:https://jiawei-yang.github.io/DenoisingViT/

github项目仓库:https://github.com/Jiawei-Yang/Denoising-ViT

本文深入探讨了视觉Transformer(ViT)中一个固有但微妙而重要的挑战:这些模型的特征图(feature maps)展现出了网格状的伪影(grid-like artifacts)，这严重损害了ViT在下游任务中的性能，这个问题的根本可以追溯到输入阶段的位置嵌入

为了解决这个问题，提出了一种新颖的噪声模型(noise model)，适用于所有的ViT，具体而言，该噪声模型将ViT的输出分解为三个部分:一个不受噪声伪影影响的语义项，以及以像素位置为条件的两个与伪像相关的项，通过基于每个图像的神经场强制实现了跨视图特征一致性，实现了这种分解，这种基于每张图像的优化过程从原始的ViT输出中提取出无伪影的特征，为离线应用提供干净的特征

为了扩展解决方案以支持在线功能，引入了一个可学习的去噪器(denoiser)，直接从未经处理的ViT输出中预测无伪影的特征，这展现出了对新数据的显著泛化能力，而无需进行基于每张图像的优化

本文的两阶段方法，称为去噪视觉Transformer(DVT/Denoising Vision Transformers)，不需要重新训练现有的预训练ViT，并且可以立即应用于任何基于Transformer的架构

在各种代表性的ViT(DINO、MAE、DeiT-III、EVA02、CLIP、DINOv2、DINOv2-reg)上评估了本文方法，广泛的评估表明，DVT提升了现有的SOTA通用模型在多个数据集上的语义和几何任务中的性能(+3.84 mIoU)，希望本文研究能够促使重新评估ViT的设计，特别是关于对位置嵌入的简单应用

<img src="https://img.saraba1st.com/forum/202401/09/025604no9e9eh3fvfukt93.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240109-025159__01.jpg</strong> (722.31 KB, 下载次数: 0)

下载附件

2024-1-9 02:56 上传

DVT消除了几乎所有视觉Transformer(ViTs)中存在的视觉特征噪音伪影，使用一组代表性的ViTs作为示例，包括监督(例如DeiT-III，Auto-aug ViT)，重构(EVA-02)，自蒸馏(DINOv2，DINOv2-reg)和多模态(CLIP)算法

上图: 每个图像三元组展示了一张输入图像，其对应的原始特征可视化图和经过DVT去噪的清晰特征图

下图: 这些三元组依次显示了一个特征图，一个K-Means聚类图和中心区块(红色虚线)与图像中其他块的相似性图…

观察噪点如何对聚类准确性和相似性产生对应负面影响，以及DVT如何有效解决这些问题，可视化图中的特征颜色是使用主成分分析(PCA/principle component analysis)生成的

<img src="https://img.saraba1st.com/forum/202401/09/025611zrntw37ixfynudy7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240109-025215__01.jpg</strong> (496.36 KB, 下载次数: 0)

下载附件

2024-1-9 02:56 上传

ViTs中的位置编码影响

(a)DINOv2 ViTs以及训练时使用和不使用位置编码的对比(“ViT”对比“ViT∗”)，展示了以下特征图:
(1)标准的ViT处理
(2)仅使用位置编码(PE)作为输入的ViT，强调了伪影的出现
(3)不使用位置编码的ViT∗处理，显示了这些伪影的明显缺失
在图中，“Patch”表示区块嵌入，“PE”表示位置嵌入

(b)描述了ViT如何保留和传播位置编码

(c) 尽管各个帧的上下文存在显著差异，伪影在图像中保持相对位置的一致性(中间行)，DVT有效去噪了这些伪影，如最后一行所示

<img src="https://img.saraba1st.com/forum/202401/09/025618wb477wqowovjj0oj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240109-025238__01.jpg</strong> (578.38 KB, 下载次数: 0)

下载附件

2024-1-9 02:56 上传

DVT由一个两阶段的降噪工作流程组成

在第一阶段，本文方法将一个裁剪图像的噪声特征分解为无噪声的语义项F，与输入无关且与位置相关的伪影项G，以及额外的残差项∆(左图)

第二阶段，使用这些经过独立优化的干净特征训练一个具有泛化能力的降噪器(右图)

<img src="https://img.saraba1st.com/forum/202401/09/025623tafhuqftqfsqhtit.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240109-025255__01.jpg</strong> (630.31 KB, 下载次数: 0)

下载附件

2024-1-9 02:56 上传

ViT输出特征和去噪特征的视觉分析

(a)使用空白图像和猫图像作为输入，对DINOv2 ViT-base模型的所有层的特征图进行可视化，猫的特征图中的伪影与空白输入的特征图有很强的视觉相关性

(b)对DINOv2 ViTs在不同层次上的分解伪影、原始特征和去噪特征进行可视化，观察到不同大小的ViTs中存在相似的模式

(c)K-Means聚类结果和中心区块(红点)与其他区块的余弦相似度的可视化

请注意，在去噪之后，特征图中的伪影减少，语义清晰度增强，从而改善了聚类结果和相似性对应关系

<img src="https://img.saraba1st.com/forum/202401/09/025630n4mnwy4xhmxqwm3v.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240109-025303__01.jpg</strong> (44.54 KB, 下载次数: 0)

下载附件

2024-1-9 02:56 上传

特征与空间位置相关性的对比，报告了网格特征与归一化区块坐标之间的最大信息系数(MIC/maximal information coefficient)

<img src="https://img.saraba1st.com/forum/202401/09/025635bpg6t2sm2gxstwpg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240109-025313__01.jpg</strong> (322.68 KB, 下载次数: 0)

下载附件

2024-1-9 02:56 上传

DVT的定性表现，DVT改进了针对密集预测任务的不同预训练 ViT，报告了语义分割(VOC2012、ADE20K)与深度预测NYUd)任务上的性能最好的结果以粗体显示

<img src="https://img.saraba1st.com/forum/202401/09/025645sgydr9p58hp48shq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240109-025327__01.jpg</strong> (692.15 KB, 下载次数: 0)

下载附件

2024-1-9 02:56 上传

涌现的物体发现能力

展示了DVT学习的去噪器输出的定性结果，使用PCA和L2特征范数对特征进行可视化，比较了原始的ViT特征与去噪后的特征在不同算法下的差异，显而易见，DVT去噪后的特征在感兴趣的物体上显示出更高的特征范数，并减少了高范数(a、b)和低范数伪影(c、d)

<img src="https://img.saraba1st.com/forum/202401/09/025650osaaevaas9fj276b.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240109-025333__01.jpg</strong> (174.27 KB, 下载次数: 0)

下载附件

2024-1-9 02:56 上传

消融实验

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1164#       发表于 2024-1-9 03:18

pheme

高效的对话型语音生成

项目主页:https://polyai-ldn.github.io/pheme/

github项目代码仓库:https://github.com/PolyAI-LDN/pheme

近年来，语音生成取得了显著进步，现在已经实现了单样本生成能力，且几乎无法与真实的人类声音区分开来。将这样的语音生成技术与大型语言模型结合起来，可以获得更广阔的应用空间

然而，某些应用，如辅助对话系统，需要自然而流畅的语音生成工具，同时还需要能够实时高效地运行，目前的SOTA模型(如VALL-E和SoundStorm等)，由分层神经音频编解码器驱动，需要大型神经组件和大量训练数据才能发挥良好的效果，相比之下，MQTTS旨在构建更紧凑的对话式TTS模型，同时仅利用较小规模的真实对话语音数据，然而由于其自回归性质，推理延迟较高，从而限制了其实时使用

为了减轻目前的SOTA TTS模型的局限性，同时利用它们的优势，在本文中，引入了Pheme模型系列，它具备以下特点:
1.提供紧凑但高性能的模型
2.允许并行生成自然对话语音
3.自然的对话型语音
4.可以在较小规模的对话数据上高效训练，数据需求减少10倍以上，但仍能与自回归TTS模型的质量相匹配

本文还证明，通过简单的师生蒸馏，可以在预训练的Pheme检查点上显著改善单说话者设置的音质，其完全依赖于更大的师生模型生成的合成语音

github项目页说明截图:

<img src="https://img.saraba1st.com/forum/202401/09/031841pztf7aacrftoefrl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240109-031739.jpg</strong> (257.78 KB, 下载次数: 0)

下载附件

2024-1-9 03:18 上传

<img src="https://img.saraba1st.com/forum/202401/09/031841u1y1hem9hdmd9g1n.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240109-031758.jpg</strong> (239.06 KB, 下载次数: 0)

下载附件

2024-1-9 03:18 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1165#       发表于 2024-1-9 03:47

 本帖最后由 Machinery 于 2024-1-9 03:48 编辑 

Open-Vocabulary SAM

交互式分割和识别2万个类别

项目主页:https://www.mmlab-ntu.com/project/ovsam/

github项目仓库:https://github.com/HarborYuan/ovsam

hugface演示demo:https://huggingface.co/spaces/HarborYuan/ovsam

CLIP和Segment Anything(SAM)模型是非常出色的视觉基础模型(VFM)，SAM在跨越各种领域的分割任务中表现出色，而CLIP则以其零样本识别能力而闻名

本文介绍了将这两个模型整合为一个统一框架的深入探索，具体而言，本文引入了Open-Vocabulary SAM，这是一个受SAM启发的模型，旨在实现同时交互分割和识别，并利用两个独特的知识迁移模块:SAM2CLIP和CLIP2SAM，前者通过蒸馏和可学习的Transformer适配器将SAM的知识迁移到CLIP中，而后者则将CLIP的知识迁移到SAM中，增强其识别能力

在各种数据集和检测器上进行了大量实验证明了Open-Vocabulary SAM在分割和识别任务中的有效性，显著优于简单组合SAM和CLIP的普通基线，此外，辅以图像分类数据训练，本文方法可以对大约22000个类别进行分割和识别

<img src="https://img.saraba1st.com/forum/202401/09/034711zpszpzwq7yu7gsqw.jpg" referrerpolicy="no-referrer">

<strong>51b52c39-f088-425c-8036-a1752cf6b5e4.jpg</strong> (140.74 KB, 下载次数: 0)

下载附件

2024-1-9 03:47 上传

Open-Vocabulary SAM通过类CLIP的真实世界识别拓展了SAM的分割能力，并大幅降低了计算成本，在COCO开放词汇基准测试中，它在物体识别的表现优于SAM和CLIP方法的组合

<img src="https://img.saraba1st.com/forum/202401/09/034721kxptxxreft68euvs.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240109-034613.jpg</strong> (91.93 KB, 下载次数: 0)

下载附件

2024-1-9 03:47 上传

Open-Vocabulary SAM融合了SAM和CLIP的知识，形成了一个统一架构，这个架构是通过SAM2CLIP实现的，SAM2CLIP将SAM的知识蒸馏迁移到CLIP中，而CLIP2SAM则利用CLIP的知识，与SAM的掩码解码器结合用于识别

在训练过程中，SAM编码器作为教师网络，而SAM2CLIP则扮演学生网络的角色，将SAM的知识与CLIP对齐，CLIP2SAM将CLIP的知识迁移到SAM解码器，并在封闭和开放词汇设置中进行联合分割和分类

演示demo

<img src="https://img.saraba1st.com/forum/202401/09/034733dh3luq39e3zc2ciz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240109-034557.jpg</strong> (133.6 KB, 下载次数: 0)

下载附件

2024-1-9 03:47 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1166#       发表于 2024-1-10 02:54

Activation Beacon

从4K飙升到400K:使用激活信标(Activation Beacon)拓展LLM的上下文

项目综合主页:https://github.com/FlagOpen/FlagEmbedding

对于大型语言模型来说，应用长上下文而言是一个巨大的挑战，因为它们的上下文窗口长度(context window lengt)有限，虽然可以通过微调来扩展上下文窗口，但这会在训练和推理时产生相当大的成本，并对语言模型的原始能力产生不利影响

在这项工作中，提出了激活信标(Activation Beacon)，它将语言模型的原始激活值(LLM's raw activations)压缩成更紧凑的形式(more compact forms)，使其能够在有限的上下文窗口内感知更长的上下文

激活信标被引入为语言模型的插件模块(plug-and-play module)，它在处理短上下文时完全保留了语言模型的原始能力，同时扩展了处理长上下文的能力，此外，它使用短滑动窗口(short sliding windows)来处理长上下文，在训练和推理中实现了有竞争力的显存和时间效率

激活信标通过在多种压缩比例的信标混合条件下进行自回归任务学习，多亏这种方式，它可以仅通过短序列数据进行高效训练，仅需1万步，以及不到9小时，就可以在一台单独的8xA800 GPU机器上完成

实验研究表明，激活信标能够将Llama-2-7B的上下文长度扩展100倍(4K到400K)，同时在长上下文生成和理解任务上取得了优异的结果

<img src="https://img.saraba1st.com/forum/202401/10/025256uk2qpwqzb2iucpqz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-024810__01.jpg</strong> (182.53 KB, 下载次数: 0)

下载附件

2024-1-10 02:52 上传

激活信标与其他上下文扩展方法的对比，包括
1.位置插值
2.NTK感知的缩放RoPE
3.LongLlama

激活信标在长上下文生成质量和运行效率(显存、时间)方面表现更好，困惑度通过在PG19测试集上使用滑动窗口进行测量

<img src="https://img.saraba1st.com/forum/202401/10/025302igqvjj2qih4pqqqk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-024816__01.jpg</strong> (283.68 KB, 下载次数: 0)

下载附件

2024-1-10 02:53 上传

(A)信标用于将激活值压缩成更紧凑的形式
(B)压缩后的激活值通过一个短滑动窗口进行自回归流处理

<img src="https://img.saraba1st.com/forum/202401/10/025308z0nnkthektzczevo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-024846__01.jpg</strong> (196.38 KB, 下载次数: 0)

下载附件

2024-1-10 02:53 上传

激活信标的工作机制(I)和信标的注意力方案(II)

<img src="https://img.saraba1st.com/forum/202401/10/025324dtglli5vxippv3ta.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-024858__01.jpg</strong> (45.68 KB, 下载次数: 0)

下载附件

2024-1-10 02:53 上传

训练数据的长度分布，所有训练数据的平均长度为3180

<img src="https://img.saraba1st.com/forum/202401/10/025330vc39zb7y7i9yw3i7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-024907__01.jpg</strong> (299.73 KB, 下载次数: 0)

下载附件

2024-1-10 02:53 上传

不同上下文窗口扩展方法在PG19、Proof-Pile和CodeParrot上的滑动窗口困惑度，激活信标成功将Llama-2-7B模型的上下文窗口扩展到比训练时见到的序列更长的长度

<img src="https://img.saraba1st.com/forum/202401/10/025335fdyyeyvvtanc8fcv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-024915__01.jpg</strong> (214.81 KB, 下载次数: 0)

下载附件

2024-1-10 02:53 上传

在LongBench上评估不同方法，激活信标的性能与经过微调的完全注意力基线相当

<img src="https://img.saraba1st.com/forum/202401/10/025339qylnsqnndt8qlzqn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-024921__01.jpg</strong> (219.7 KB, 下载次数: 0)

下载附件

2024-1-10 02:53 上传

推理时间和GPU显存使用率的评估，这两个指标是通过100次前向传递的平均值计算的(LongChat启用了FlashAttention-2)

<img src="https://img.saraba1st.com/forum/202401/10/025344bxq4yaa466kgpsz4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-024927__01.jpg</strong> (210.04 KB, 下载次数: 0)

下载附件

2024-1-10 02:53 上传

在不同上下文长度中的主题检索准确率(topic retrieval accuracy)的评估，Activation Beacon的表现与经过微调的方法(如LongChat-32K和LongAlpaca-16K)相似

<img src="https://img.saraba1st.com/forum/202401/10/025353ipwl3zonmee3p59e.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-024931__01.jpg</strong> (46.59 KB, 下载次数: 0)

下载附件

2024-1-10 02:53 上传

LongAlpaca-16K(8个A100 GPU)和Activation Beacon(8个A800 GPU)的训练时间和GPU显存成本对比

<img src="https://img.saraba1st.com/forum/202401/10/025359yeaxitavdwjr80ll.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-024936__01.jpg</strong> (211.72 KB, 下载次数: 0)

下载附件

2024-1-10 02:53 上传

不同技术因素的影响，包括信标的注意力方案、压缩比率和训练数据的组成，默认设置用*标记

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1167#       发表于 2024-1-10 03:54

AST-T5

用于代码生成和理解的结构感知预训练(Structure-Aware Pretraining)

github项目代码仓库:https://github.com/gonglinyuan/ast_t5

大型语言模型(LLMs)在与代码相关的任务中取得了重大进步，但许多LLMs依然将代码视为简单的序列(simple sequences)，忽视了其结构化的本质

本文引入了AST-T5，一种新颖的预训练范式，利用抽象语法树(AST/Abstract Syntax Tree)增强了代码生成、转换(transpilation)和理解能力，通过动态规划(dynamic programming)，AST感知分割的保留代码结构，而AST感知跨度损坏目标(AST-Aware Span Corruption objective)使模型能够重构各种代码结构，与其他模型不同，AST-T5避免了复杂的程序分析或架构改变，因此可以与任何编码器-解码器Transformer无缝集成

评估结果显示，AST-T5在各种与代码相关的任务中始终优于相同规模的LLMs，结构感知使AST-T5在代码到代码相关任务中特别强大，在Bugs2Fix任务的精确匹配分数上超过CodeT5 2个点，在CodeXGLUE的Java-C#转换任务上的精确匹配分数上超过CodeT5 3个点

<img src="https://img.saraba1st.com/forum/202401/10/035422a4org1rsurmbrreg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-035220.jpg</strong> (112.11 KB, 下载次数: 0)

下载附件

2024-1-10 03:54 上传

使用Python的阶乘函数对比了AST-Aware子树损坏(Subtree Corruption)和原生(Vanilla)T5两种方法

这两种方法都用哨点(sentinel)Token(添加到词汇表中的特殊Token，在图中表示为[X]，[Y]和[Z])替换了被遮蔽(Mask)的片段，并且输出序列包含原始的遮蔽Token，输入和目标以字节对编码(BPE/byte-pair encoding)显示，例如，“factorial”被编码为“fact”和“##orial”，与随机遮蔽代码并且与结构无关的Vanilla T5不同，本文方法专门针对与AST子树对齐的片段，如表达式和语句(expressions and statements)

<img src="https://img.saraba1st.com/forum/202401/10/035427g0a1cluygy3ayghh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-035245.jpg</strong> (128.35 KB, 下载次数: 0)

下载附件

2024-1-10 03:54 上传

贪婪分割和AST感知分割的对比:

对于一个112个Token的代码示例，最大长度设置为48，贪婪分割将前48个标记放在块1中，接下来的48个标记放在块2中，剩下的放在块3中，破坏了代码的结构完整性

相比之下，AST-Aware分割使用动态规划算法智能地对代码进行分割，与成员函数或主要函数分支的边界对齐，从而保留了代码的结构

为了清晰起见，附带的AST对一些层级进行了修剪，证实了这些分割确实与关键子树的分界线相吻合

<img src="https://img.saraba1st.com/forum/202401/10/035432yt2367341mb1f133.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-035314.jpg</strong> (85.72 KB, 下载次数: 0)

下载附件

2024-1-10 03:54 上传

各种预训练配置在下游任务中的性能对比，每一行表示对前一行模型应用顺序性修改，指标包括HumanEval的“Pass@1”，CONCODE的“Exact Match”，Bugs2Fix(“Small”和“Medium”代码长度分割)，以及Java-C#转换(包括Java到C#和C#到Java)，复制检测(Clone Detection)使用F1分数，缺陷检测(Defect Detection)使用准确率，与先前的研究一致

<img src="https://img.saraba1st.com/forum/202401/10/035436pd7dic6bbdpd5qii.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-035325.jpg</strong> (95.36 KB, 下载次数: 0)

下载附件

2024-1-10 03:54 上传

AST-T5在下游任务中的结果与已构建的语言模型的报告结果对比，评估指标与表1中的指标一致，主要关注与AST-T5相似规模的模型，特别是“Base”型号(110M到230M参数)，由于某些模型为仅编码器或仅解码器(encoder-only or decoder-only)，因此不适用于某些任务，这些结果在本表中标有“N/A”，因为它们在文献中不可用

<img src="https://img.saraba1st.com/forum/202401/10/035441prhzxqt1huubh5hl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-035335.jpg</strong> (60.33 KB, 下载次数: 0)

下载附件

2024-1-10 03:54 上传

将AST-T5在HumanEval上的性能与超过230M参数的模型进行对比，散点图上的每个点表示一个模型，x轴以对数刻度显示参数数量，y轴以对数刻度显示HumanEval的Pass@1，模型的开源状态以颜色编码:蓝色表示开源，红色表示专有

<img src="https://img.saraba1st.com/forum/202401/10/035445v3db7u37sob5d5s3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-035340.jpg</strong> (61.49 KB, 下载次数: 0)

下载附件

2024-1-10 03:54 上传

将AST-T5在MBPP上的性能与其他模型进行对比，散点图上的每个点表示一个模型

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1168#       发表于 2024-1-10 04:25

TIER

用于AIGC图像质量评估的基于文本和图像编码器的回归

项目代码仓库:https://github.com/jiquan123/TIER

最近，AIGC图像质量评估(AIGCIQA/AIGC image quality assessment)作为计算机视觉中的一个新课题出现，旨在从人类感知的角度评估AI生成图像的质量，与常见的图像质量评估任务不同，这些任务中的图像是由生成模型使用文本提示生成的，而不是通过噪声、模糊和压缩来扭曲原始图像

在过去几年中已经做出了相当大的努力来推进AIGCIQA，然而，大多数现有的AIGCIQA方法直接从单张独立的生成的图像中回归预测的分数，忽视了这些图像的文本提示中包含的信息，这个疏忽在一定程度上限制了这些AIGCIQA方法的性能

为了解决这个问题，本提出了一种基于文本和图像编码器的回归(TIER/text and image encoder-based regression)框架，具体来说，将生成的图像及其相应的文本提示作为输入，利用文本编码器和图像编码器分别从这些文本提示和生成的图像中提取特征

为了证明提出的TIER方法的有效性，在几个主流的AIGCIQA数据库上进行了大量实验，包括AGIQA-1K、AGIQA-3K和AIGCIQA2023，实验结果表明，本文提出的TIER方法在大多数用例中都表现出了优于基线的性能

<img src="https://img.saraba1st.com/forum/202401/10/042536kqm3bopsgtb4sp3b.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-042336.jpg</strong> (49.98 KB, 下载次数: 0)

下载附件

2024-1-10 04:25 上传

(a)在常见的图像质量评估任务中，图像是由受到噪声、模糊和压缩等影响而变形的原始图像派生而来的

(b)在AIGCIQA任务中，图像通常是通过使用文本提示生成模型生成的

<img src="https://img.saraba1st.com/forum/202401/10/042540sh49c4czk3njcbpp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-042350.jpg</strong> (58.77 KB, 下载次数: 0)

下载附件

2024-1-10 04:25 上传

本文提出的TIER框架的工作流程，分别将生成的图像和对应的文本提示作为输入，利用文本编码器和图像编码器从这些文本提示和生成的图像中提取特征，文本编码器使用在自然语言处理(NLP)中常用的文本Transformer模型，而图像编码器可以是卷积神经网络或视觉Transformer，然后，将提取的文本和图像特征进行拼接(concatenated)，并输入到回归网络中预测得分

<img src="https://img.saraba1st.com/forum/202401/10/042546g44ji3ul8mk8gmgs.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-042419__01.jpg</strong> (310.99 KB, 下载次数: 0)

下载附件

2024-1-10 04:25 上传

与使用不同文本编码器和图像编码器的TIER方法与基线方法在三个主流AIGCIQA数据库上进行对比

<img src="https://img.saraba1st.com/forum/202401/10/042551vf6llrcllpcc1zcc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-042433__01.jpg</strong> (413.18 KB, 下载次数: 0)

下载附件

2024-1-10 04:25 上传

TIER方法与基线方法在三个主流AIGCIQA数据库上的性能比较，↑表示TIER方法相比基线方法表现出了更好的性能

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1169#       发表于 2024-1-10 05:04

Grimoire

魔法书(Grimoire)就是增强大型语言模型您所需要的

github项目主页:https://github.com/IAAR-Shanghai/Grimoire

上下文学习(ICL/In-context learning)是提高大型语言模型在特定任务上性能的关键方法之一，它通过提供一组少量的问题和答案示例来实现，然而，不同类型的模型在ICL能力上显示出显著的差异，这通常是由于模型架构、数据学习量以及参数的大小等因素所导致的，通常情况下，模型的参数大小越大，学习数据越丰富，其ICL能力就越强

在本文中，提出了一种名为强LLM增强上下文学习(SLEICL/Strong LLM Enhanced ICL)的方法，它涉及使用强大的语言模型从示例中学习，然后将这些学到的技能进行摘要和转移(summarizing and transferring)，提供给弱小语言模型进行推理和应用，这确保了ICL的稳定性和有效性，与直接让弱语言模型从提示示例中学习相比，SLEICL减少了这些模型进行ICL的难度

在多达八个数据集以及五种语言模型上进行的实验证明，使用SLEICL方法，弱语言模型在其自身的零样本或少样本能力上取得了一致改进，一些弱语言模型甚至在SLEICL的帮助下超过了GPT4-1106-preview(零样本)的性能水平

<img src="https://img.saraba1st.com/forum/202401/10/050349vkzcfkkc3ac06ab0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-045849__01.jpg</strong> (305.21 KB, 下载次数: 0)

下载附件

2024-1-10 05:03 上传

与直接让语言模型进行常规上下文学习(Regular ICL)相比，强LLM增强上下文学习(SLEICL)的方法是让一个强大的语言模型最初学习和总结基于代表性样本的技术，随后，生成的技术(魔法书/grimoire)作为提示的一部分被纳入到弱语言模型的回答中，以指导它们的回应

<img src="https://img.saraba1st.com/forum/202401/10/050354wbnjtnssndz9diis.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-045925__01.jpg</strong> (337.34 KB, 下载次数: 0)

下载附件

2024-1-10 05:03 上传

所提出的SLEICL方法的框架，首先，使用不同的样本选择方法(KCS，HCS，HSS，RSS)获得多组代表性样本，每组采样样本都根据标签进行分层管理，随后，根据每个样本集生成相应的深度魔法书(PG/profound grimoires)和简单魔法书(SG/simple grimoires)，此外，还包括不使用样本生成的零样本深度魔法书(zero-shot-PG)和零样本简单魔法书(zero-shot-SG)，最后，根据给定的测试样本对所有的魔法书进行排名，并将最佳魔法书交给弱LLM进行回答

<img src="https://img.saraba1st.com/forum/202401/10/050359oeobbduohu86e1bo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-045943__01.jpg</strong> (328.34 KB, 下载次数: 0)

下载附件

2024-1-10 05:03 上传

魔法书生成的工作流程

<img src="https://img.saraba1st.com/forum/202401/10/050403ded2omohlazaz2ve.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-050108__01.jpg</strong> (526.57 KB, 下载次数: 0)

下载附件

2024-1-10 05:04 上传

魔法书增强的GPT3.5-Turbo的详细评估结果

注意:-表示该超参数在当前测试中无效，n-shot表示每个预测将提供n个样本，k-shot表示在每个标签下提供k个样本以生成魔法书，r表示困难样本的采样比例，每列中的最佳性能将以粗体显示，第二佳性能将以下划线显示

<img src="https://img.saraba1st.com/forum/202401/10/050428a7x57885yr54k04o.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-050134__01__01.jpg</strong> (673.28 KB, 下载次数: 0)

下载附件

2024-1-10 05:04 上传

魔法书方法相对于基线的预测精度差异

注意:Max(Single Grimoire)表示在所有的单个魔法书方法(among all Single Grimoire methods)中的最佳性能，正差异将以绿色突出显示，较深的颜色表示差异更大：&lt;5%、5%∼10%、10%∼20%、20%∼30%、&gt;30%，负差异将以红色突出显示，差异越小，颜色越深:&gt;-5%、-5%∼-10%、&lt;-10%，NaN表示有效实验数据数量过小，无法给出可靠的准确率

<img src="https://img.saraba1st.com/forum/202401/10/050434oyhetgueasatsmug.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-050149__01.jpg</strong> (115.42 KB, 下载次数: 0)

下载附件

2024-1-10 05:04 上传

雷达图对比了GPT-4在零样本提示下与其他模型在Max(Single Grimoire)设置中的结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1170#       发表于 2024-1-10 06:39

UMIE

指令调整的统一多模态信息提取

github项目主页:https://github.com/ZUCC-AI/UMIE

多模态信息提取(MIE/Multimodal information extraction)在多模态内容的流行度增加时引起了广泛关注，然而，当前的MIE方法通常采用特定于任务的模型结构，导致在不同任务之间的泛化能力有限，并且未充分利用MIE任务之间的共享知识

为了解决这些问题，本文提出了UMIE，一种统一的多模态信息提取器，使用指令调整将三个MIE任务统一为生成问题，能够有效地提取文本和视觉线索

大量实验证明，本文的UMIE在跨越三个任务的六个MIE数据集上优于各种SOTA方法，此外，深入分析表明UMIE在零样本设置下具有很强的泛化能力，对指令变体具有稳健性，并且可解释性强

本文研究为统一的MIE模型迈出了第一步，并在MIE领域内探索了指令调整和大型语言模型

<img src="https://img.saraba1st.com/forum/202401/10/063912qp6v18q68f6z81qr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-063431.jpg</strong> (187.8 KB, 下载次数: 0)

下载附件

2024-1-10 06:39 上传

将三个关键的MIE任务统一在一个多模态模型中，给定任务指导(task instructor)，UMIE通过提取文本和视觉线索(MNER和MEE)或推断两个给定线索之间的关系(MRE)来执行相应的任务，O1、O2和O3是视觉对象

<img src="https://img.saraba1st.com/forum/202401/10/063919p3u3ytv6700dzdt0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-063455.jpg</strong> (187.38 KB, 下载次数: 0)

下载附件

2024-1-10 06:39 上传

UMIE模型的示意图，视觉编码器将图像和对象编码为特征，这些特征在门控注意力模块(gated attention module)中与文本特征动态集成，文本解码器自回归式地生成信息提取结果

<img src="https://img.saraba1st.com/forum/202401/10/063925rrm4vczjjvfvxo3h.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-063519__01.jpg</strong> (337.1 KB, 下载次数: 0)

下载附件

2024-1-10 06:39 上传

任务指导的描述，如表中的最后一行所示，MEAE的具体指令将由MED检测到的事件类型确定

<img src="https://img.saraba1st.com/forum/202401/10/063931cwm5m6hhgzgwrmz6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-063528__01.jpg</strong> (63.25 KB, 下载次数: 0)

下载附件

2024-1-10 06:39 上传

门控注意力模块的示意图

<img src="https://img.saraba1st.com/forum/202401/10/063940hfhmuywatw9fn7yw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-063601__01.jpg</strong> (394.21 KB, 下载次数: 0)

下载附件

2024-1-10 06:39 上传

三个任务的输入和输出格式，特别是，MEE任务将被作为两个级联任务，即MED和MEAE，具有相同的输入示例进行

<img src="https://img.saraba1st.com/forum/202401/10/063946orc3y5k0y2djcd3d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-063607__01.jpg</strong> (93.18 KB, 下载次数: 0)

下载附件

2024-1-10 06:39 上传

六个MIE数据集的统计信息

<img src="https://img.saraba1st.com/forum/202401/10/063951m06i60uwmb6ffpai.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-063746.jpg</strong> (282.61 KB, 下载次数: 0)

下载附件

2024-1-10 06:39 上传

<img src="https://img.saraba1st.com/forum/202401/10/063951l105o5zs7xezk70s.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240110-063802.jpg</strong> (162.62 KB, 下载次数: 0)

下载附件

2024-1-10 06:39 上传

相关性能评估与对比

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1171#       发表于 2024-1-11 04:14

 本帖最后由 Machinery 于 2024-1-11 04:19 编辑 

animagine-xl

动漫图像生成

hugface权重下载:https://huggingface.co/cagliostrolab/animagine-xl-3.0

演示demo:https://huggingface.co/spaces/Linaqruf/animagine-xl

相关博客:https://cagliostrolab.net/posts/animagine-xl-v3-release

————
两个月前，Animagine XL 2.0公开发布，今天，很高兴向您介绍Animagine XL 3.0，这是基于Stable Diffusion XL的开源动漫文本到图像模型的下一代版本，在上一代版本的基础上，V3经过了开发和改进，以成为最好的开源动漫图像生成模型

与上一代版本相比，它具备更好的知识、更好的概念和更好的提示理解能力，它还可以生成更好的手部结构
————
在Animagine XL 2.0的基础之上进行微调

在一番尝试和错误之后，Animagine XL 2.0可以成为Animagine XL 3.0预训练过程的基础模型，这个模型不仅建立在SDXL之上(迄今为止世界上最好的开源图像生成模型)，而且Animagine XL 2.0已经比原始版本更好地学习了动漫概念，这使得持续训练变得简单高效

为了训练Animagine XL 3.0，只在Runpod上使用了2个A100 80GB，其中一半的积分来自研究组宝贵的朋友，其余的则来自自掏腰包，这个模型在12月份训练了21天，大约使用了500个GPU小时，使用了稍微修改过的kohya-ss/sd-scripts作为训练脚本，添加了一些类似于keep_tokens_separator的内容，以动态的保持标签不被打乱

然而，Animagine XL 3.0的训练配置可能会与Animagine XL 2.0略有不同，希望模型能够适应这种变化
————
标签排序

NovelAI去年宣布了他们的动漫文本到图像模型的第三次迭代，NovelAI Diffusion V3，声称NAID V3经过独特的标签排序训练，这意味着标签排序对于获得我们想要的东西至关重要，值得庆幸的是，他们在文档中分享了他们的发现(相关链接:https://docs.novelai.net/image/tags.html#tag-ordering)

基于这些信息，通过尝试构建数据集并进行类似于NovelAI Diffusion V3的训练来重现标签排序，到目前为止，对结果感到非常满意，因此提议使用下文提示模板来对本文V3模型进行推理

1boy/1girl, what character, from which series, everything else in random order*

everything else in random order*可以是一切，从一般标签到质量标签

<img src="https://img.saraba1st.com/forum/202401/11/041257y25e2s885w12tw19.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240111-041015.jpg</strong> (127.06 KB, 下载次数: 0)

下载附件

2024-1-11 04:12 上传

————
更好的手

相信V3可以相对于上一版本可以生成更好的手势，研究组一直在测试一些手势标签，比如waving, double v, v, pointing at viewer, hands up, rabbit pose, 以及 shushing等，到目前为止，对效果感到十分满意

<img src="https://img.saraba1st.com/forum/202401/11/041305cooa3j818pzumipj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240111-041024.jpg</strong> (171.97 KB, 下载次数: 0)

下载附件

2024-1-11 04:13 上传

————
更简单的提示，更好的知识

导致需要训练这个模型的另一个原因是LoRA的开发不可控且低效，假设我们需要2800个LoRA来处理2800个角色，每个LoRA的平均大小为50 MB(8 dim, 8 alpha, 8 conv dim, 4 alpha)，那么我们需要分配大约140 GB的存储空间来保存LoRA，不仅如此，还必须加载所有LoRA，验证它们是否损坏，打开network选项卡，选择LoRA，并在生成之前调整LoRA适配器的权重

我们需要通过训练更好的基础模型来让LoRA更加有效和高效，这样我们只需要针对模型缺乏的概念和艺术风格来训练LoRA，使用此模型，您只需使用提示即可生成许多知名角色，甚至不需要解释大多数角色的特征就可以得到您想要的，如果您输入“Hoshimachi Suisei”，您将得到“Hoshimachi Suisei”，如果您输入“Arima Kana”，您将得到Arima Kana，就这么简单！

<img src="https://img.saraba1st.com/forum/202401/11/041317xhf7bohzuros2hrs.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240111-041032.jpg</strong> (340.14 KB, 下载次数: 0)

下载附件

2024-1-11 04:13 上传

————
CFG更低，采样步骤更少

根据研究发现，建议使用5-7左右的较低的无分类器指导，采样步骤低于30，并使用Euler Ancestral (Euler A)作为采样器，此设置可优化性能而不影响结果质量

<img src="https://img.saraba1st.com/forum/202401/11/041325aqq0569q9587jmz9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240111-041043.jpg</strong> (212.65 KB, 下载次数: 0)

下载附件

2024-1-11 04:13 上传

————
无法控制

说完好事之后，现在开始解释发生的坏事，如果用户使用masterpiece, best quality，可能会遇到更多NSFW结果，因为许多高分数据集都是NSFW，最好将NSFW, rating: sensitive添加到负面提示，并将rating: general添加到正面提示

在训练结束之后，我们才意识到训练脚本有问题，它存在分布式数据并行问题，因为使用了多个GPU，所以梯度未同步，这意味着模型可能训练不足，因为它可能只接收部分update
————
特殊标签

与之前的迭代一样，该模型使用一些特殊标签进行训练，以将结果引导至质量和年份标签，没有这些特殊标签，模型仍然可以完成工作，但如果我们想让模型更容易发挥效果，建议使用它们

质量标签

为了使用户更容易从SD 1.5迁移到SDXL，选择了保持质量标签相同，其中根据数据集得分来衡量质量标签，以下为列表，从最好到最差:
masterpiece
best quality
high quality
normal quality
low quality
worst quality

<img src="https://img.saraba1st.com/forum/202401/11/041337bilddcwcdcvpwphq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240111-041055.jpg</strong> (205.25 KB, 下载次数: 0)

下载附件

2024-1-11 04:13 上传

————
年份标签

还引入了年份标签，但与NovelAI Diffusion V3不同，其中基于一系列图片发布的年份而不是单独的帖子年份进行训练，它应该是另一个质量标签，引导结果走向动漫艺术风格的现代性，年份标签使用起来不是很有效，但是，如果我们特别想要获得2014年代的艺术风格，它们应该特别有效，以下是列表，从最新到最旧:
newest
late
mid
early
oldest

<img src="https://img.saraba1st.com/forum/202401/11/041413e79097relb9bln7r.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240111-041104.jpg</strong> (278.08 KB, 下载次数: 0)

下载附件

2024-1-11 04:14 上传

————
发布与相关许可

<img src="https://img.saraba1st.com/forum/202401/11/041418nfdfg5udgn5f2ye3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240111-041114.jpg</strong> (382.07 KB, 下载次数: 0)

下载附件

2024-1-11 04:14 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  squallx  
##### 1172#       发表于 2024-1-11 04:54

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63610401&amp;ptid=2126390" target="_blank">Machinery 发表于 2024-1-11 04:14</a>

animagine-xl

动漫图像生成</blockquote>
<img src="https://static.saraba1st.com/image/smiley/face2017/048.png" referrerpolicy="no-referrer">开源社区向NAI3霸权开出的第一炮

虽然这霸权还没到两个月

*****

####  Machinery  
##### 1173#       发表于 2024-1-11 04:59

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63610425&amp;ptid=2126390" target="_blank">squallx 发表于 2024-1-11 04:54</a>
开源社区向NAI3霸权开出的第一炮

虽然这霸权还没到两个月</blockquote>
虽然是nai3自己发的，这开源程度已经完全超越了一系列大厂<img src="https://static.saraba1st.com/image/smiley/face2017/068.png" referrerpolicy="no-referrer">

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1174#       发表于 2024-1-12 06:26

 本帖最后由 Machinery 于 2024-1-12 06:27 编辑 

PIXART-δ

使用潜在一致性模型进行快速且可控的图像生成

项目主页:https://pixart-alpha.github.io/

github项目代码仓库:https://github.com/PixArt-alpha/PixArt-alpha

演示demo:https://huggingface.co/spaces/PixArt-alpha/PixArt-LCM

PIXART-δ，一种文本到图像合成框架，将潜在一致性模型(LCM/Latent Consistency Model)和ControlNet集成到了先进的PIXART-α模型中，同时以其高效的训练过程生成1024px分辨率的高质量图像能力而闻名

在PIXART-δ中集成LCM显著加快了推理速度，使之仅需2-4步即可生成高质量图像，同时，PIXART-δ在生成1024×1024像素图像方面取得了突破性进展，仅需0.5秒，相比PIXART-α快了近7倍，此外，PIXART-δ的设计使其可以通过仅在单张32GB V100 GPU上花费一天即可高效训练

通过8位(8-bit)推理能力，PIXART-δ可以在8GB GPU显存限制下合成1024px图像，极大地提高了其可用性和易用性，此外，引入的类ControlNet模块使得对文本到图像扩散模型进行精细控制成为可能

通过引入一种专为Transformer量身定制的ControlNet-Transformer架构，实现了显式可控性的高质量图像生成，作为一种SOTA开源图像生成模型，PIXART-δ为Stable Diffusion模型系列提供了有希望的替代方案，并在文本到图像合成领域做出了重大贡献

<img src="https://img.saraba1st.com/forum/202401/12/062459vc98z599oaxuutbx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-061927__01.jpg</strong> (313.39 KB, 下载次数: 0)

下载附件

2024-1-12 06:24 上传

PIXART-δ的训练流程，图的上半部分提供了训练过程的高级概述，描述了在特定ODE轨迹上的噪声采样和去噪的连续阶段，映射线上标有序列号，以清楚地排序这些步骤的顺序

下半部分深入研究了预训练(教师)模型和学生模型的复杂作用，揭示了它们在上半部分的训练过程中各自的功能，并标记了相应的序列号，以便于轻松交叉引用

<img src="https://img.saraba1st.com/forum/202401/12/062509ytypz9thbb0p8sph.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-061941__01.jpg</strong> (285.8 KB, 下载次数: 0)

下载附件

2024-1-12 06:25 上传

对各种无分类器引导尺度(ω)策略进行的FID和CLIP分数消融实验，以及它们对训练中对蒸馏收敛性的影响

<img src="https://img.saraba1st.com/forum/202401/12/062516t1ar1ayn0npp1ree.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-061958__01.jpg</strong> (184.46 KB, 下载次数: 0)

下载附件

2024-1-12 06:25 上传

PIXART-δ和LCM之间的βt实例化、噪声调度功能以及相应的logSNR

<img src="https://img.saraba1st.com/forum/202401/12/062524jmzbilirr0yzhayz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-062009__01.jpg</strong> (111 KB, 下载次数: 0)

下载附件

2024-1-12 06:25 上传

在PIXART-δ和Stable Diffusion模型之间的LCM训练设置示意图
(*表示Stable Diffusion Dreamshaper-v7微调版本)

<img src="https://img.saraba1st.com/forum/202401/12/062529gde6eggi2hlke7nr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-062009__02.jpg</strong> (104.9 KB, 下载次数: 0)

下载附件

2024-1-12 06:25 上传

在各种设备上实现的生成速度示例，这些测试都基于1024×1024分辨率，所有情况下批大小都为1

<img src="https://img.saraba1st.com/forum/202401/12/062538mcyudhjkzcj1isxa.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-062023__01.jpg</strong> (297.88 KB, 下载次数: 0)

下载附件

2024-1-12 06:25 上传

PIXART-δ集成了ControlNet

(b)ControlNet-UNet，基本blocks被分为“编码器”和“解码器”阶段(“encoder” and “decoder” stages)，ControlNet结构被应用于PIXART-δ的每个编码器层次，并通过skip-connections将输出连接到解码器阶段

(c):ControlNet-Transformer，ControlNet被应用于前几个blocks，每个blocks的输出添加到相应的冻结blocks的输出中，作为下一个冻结blocks的输入

<img src="https://img.saraba1st.com/forum/202401/12/062544ylv60ez833lvrv0t.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-062035__01.jpg</strong> (806.14 KB, 下载次数: 0)

下载附件

2024-1-12 06:25 上传

ControlNet-UNet和ControlNet-Transformer的消融实验，ControlNet-Transformer产生的结果比ControlNet-UNet好得多，ControlNet-Transformer的可控性随着复制blocks数量的增加而增加

<img src="https://img.saraba1st.com/forum/202401/12/062552fepj1qggfevfx39g.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-062057__01.jpg</strong> (436.32 KB, 下载次数: 0)

下载附件

2024-1-12 06:25 上传

PixArt-ControlNet训练中的“突然收敛(Sudden Converge)”示例，经验性地观察到这在1000次迭代之前发生

<img src="https://img.saraba1st.com/forum/202401/12/062558klduca2zrb1uduuj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-062120__01.jpg</strong> (489.66 KB, 下载次数: 0)

下载附件

2024-1-12 06:25 上传

生成输出的示例，在上半部分，对比的是PIXART-δ和SDXL-LCM，采样步骤为4步，在下半部分，对比了PIXART-δ和PIXART-α(教师模型，使用14步的DPM-Solver)

<img src="https://img.saraba1st.com/forum/202401/12/062616cqz76cccttkmljm7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-062138__01.jpg</strong> (404.29 KB, 下载次数: 0)

下载附件

2024-1-12 06:26 上传

由PIXART-δ生成的4步推理样本，在使用全部批大小(total batch size)为24的2个V100 GPU上展示了LCD训练的快速收敛能力，值得注意的是，完整的微调过程仅需要不到24GB的GPU内存，在大多数当代的消费级GPU上可行

<img src="https://img.saraba1st.com/forum/202401/12/062621zf6xe3kxquhh3lfw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-062148__01.jpg</strong> (617.66 KB, 下载次数: 0)

下载附件

2024-1-12 06:26 上传

高分辨率和细粒度的可控图像生成

使用提示“the map of the final fantasy game’s main island, in the style of hirohiko araki, raymond swanland, monumental murals, mosaics, naturalistic rendering, vorticism, use of earth tones.”生成

<img src="https://img.saraba1st.com/forum/202401/12/062627f88fflgw69llw7vs.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-062155__01.jpg</strong> (471.68 KB, 下载次数: 0)

下载附件

2024-1-12 06:26 上传

高分辨率和细粒度的可控图像生成

输出使用提示“Multicultural beauty. Women of different ethnicity - Caucasian, African, Asian and Indian.”生成

<img src="https://img.saraba1st.com/forum/202401/12/062632y0gqobnqqnnibaio.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-062202__01.jpg</strong> (721.55 KB, 下载次数: 0)

下载附件

2024-1-12 06:26 上传

PixArt-ControlNet生成的更多图像示例

<img src="https://img.saraba1st.com/forum/202401/12/062637v6qtoczkbcksppcf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-062216__01.jpg</strong> (645.34 KB, 下载次数: 0)

下载附件

2024-1-12 06:26 上传

训练步骤的影响，快速收敛，随着训练步骤的增加，细节逐渐改善，并与HED边缘图更加吻合

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1175#       发表于 2024-1-12 07:22

ANIM-400K

用于视频自动端到端配音(Automated End-To-End Dubbing)的大规模数据集

github项目主页:https://github.com/davidmchan/Anim400K

互联网作为巨大的内容宝库，其中高达60%的内容是用英语发布的，与全球人口相比形成了鲜明对比，其中全球只有18.8%的人口会说英语，而仅有5.1%的人口将其视为母语，这导致了在线信息获取的严重分化

不幸的是，视频配音的自动化过程，将视频的音轨替换为翻译后的音轨，仍然是一项复杂而具有挑战性的任务，因为需要精确的时间控制(precise timing)、面部动作同步(facial movement synchronization)和韵律匹配(prosody matching)，虽然端到端的配音提供了一种解决方案，但数据稀缺持续阻碍着端到端和基于工作流程的方法相关进展

在这项工作中，介绍了Anim-400K，一个包含超过425000个对齐的日语和英语动画视频片段的综合数据集，支持各种与视频相关的任务，包括自动配音、同声翻译、指导式视频摘要和类型/主题/风格分类(automated dubbing, simultaneous translation, guided video summarization, and genre/theme/style classification)，数据集已公开提供，以供研究目的使用

Anim-400K，被设计为旨在用于视频自动配音，并支持从同声翻译与引导视频摘要到流派/主题/风格分类等多种范围的次要视频任务的新数据集

与自动配音相关的数据集概览

Anim-400K中包含的季/节目、剧集和片段级别的信息概览

Heroes和Anim-400K数据集之间一些自然语言分布差异的概览

Anim-400K数据集中存在的流派和主题

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1176#       发表于 2024-1-12 08:35

 本帖最后由 Machinery 于 2024-1-12 08:36 编辑 

AutoAct

通过自规划(Self-Planning)从零进行自动化代理者学习(Automatic Agent Learning)

github项目主页:https://github.com/zjunlp/AutoAct

语言代理者们在各种复杂任务上取得了相当不错的表现，尽管当前的研究对这个领域进行了大量探索，但现有的语言代理者系统仍然面临着昂贵且难以重用的数据依赖性，并且面临将单一模型应用于多个功能的挑战

为此，本文介绍了AutoAct，一个自动化代理者学习框架，且不依赖于大规模标注数据和来自闭源模型(例如GPT-4)的合成轨迹，在仅拥有有限的工具库数据的情况下，AutoAct首先自动合成规划轨迹，而且无需人类或强大闭源模型的任何帮助，然后，AutoAct利用分工(division-of-labor)策略根据目标任务信息和合成轨迹进行自动区分(automatically differentiate)，生成一个子代理者组(sub-agent group)完成任务

对多个LLM进行了全面实验，结果表明，与各种强大基线相比，AutoAct能够获得更好或相当的性能，在这其中注意到，当使用Llama-2-13b模型时，AutoAct可以达到与GPT-3.5-Turbo代理者相当的性能

<img src="https://img.saraba1st.com/forum/202401/12/083441exx9nna42nhj8njb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-083038__01.jpg</strong> (137.12 KB, 下载次数: 0)

下载附件

2024-1-12 08:34 上传

AUTOACT的基本框架，通过仅使用一个工具库，元代理者(META-AGENT)可以根据目标任务信息进行自动区分，并产生一个子代理者组，协同完成任务

<img src="https://img.saraba1st.com/forum/202401/12/083447v07ns9um0494gza1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-083101__01.jpg</strong> (330.96 KB, 下载次数: 0)

下载附件

2024-1-12 08:34 上传

相关工作的对比

数据和轨迹获取(Data and Trajectory Acquisitions)是指获取训练数据和轨迹的方法

规划(Planning)表示规划的方式，根据每个步骤的动作是全局还是迭代(globally or iteratively)进行划分

多代理者(Multi-Agent)表示框架是否包含多代理者

微调(Fine-Tuning)表示方法是否是基于微调的智能体学习框架

普适性(Generality)表示方法是否适用于各种任务

反思(Reflection)表示规划过程是否包含反思

<img src="https://img.saraba1st.com/forum/202401/12/083454pj3z9ffjq4r3vvyv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-083118__01.jpg</strong> (537.95 KB, 下载次数: 0)

下载附件

2024-1-12 08:34 上传

提出的AUTOACT框架概览图，首先进行自指导(self-instruct)，从零开始扩展任务数据库，然后应用自规划进行自动化代理者学习，包括自动工具选择、轨迹合成、自区分(self-differentiation)和群体规划，其中，自区分是一个参数高效的微调过程，以实现轻量级和低消耗

<img src="https://img.saraba1st.com/forum/202401/12/083459gp15ygpdccfq0f1u.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-083147__01.jpg</strong> (301.91 KB, 下载次数: 0)

下载附件

2024-1-12 08:34 上传

在HotpotQA和ScienceQA上使用AUTOACT和各种基线相进行对比

<img src="https://img.saraba1st.com/forum/202401/12/083504zl0s3vg3bs66jljo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-083157__01.jpg</strong> (98 KB, 下载次数: 0)

下载附件

2024-1-12 08:35 上传

AUTOACT的方法消融

- 反思(reflection)表示在AUTOACT中删除反思代理者
- 多(multi)代表将所有区分数据送入一个模型进行微调
- 微调(fine-tuning)表示使用AUTOACT中定义的三个代理者进行零样本提示规划
- 过滤(filtering)表示没有过滤错误用例的情况下在零样本规划中的所有轨迹生成上进行自区分

<img src="https://img.saraba1st.com/forum/202401/12/083510tzw9cgwk22wg2c2v.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-083211__01.jpg</strong> (472.54 KB, 下载次数: 0)

下载附件

2024-1-12 08:35 上传

AUTOACT在不同训练数据规模上的性能

(a-c)表示在自合成轨迹上训练的模型结果
(d-f)表示在由更强的模型合成的轨迹上训练的模型结果

其中虚线是在自合成轨迹上进行的基线训练(baseline trained on self-synthesized trajectories)

<img src="https://img.saraba1st.com/forum/202401/12/083519kzobnyj94oj4nbao.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-083220__01.jpg</strong> (129.77 KB, 下载次数: 0)

下载附件

2024-1-12 08:35 上传

基于不同程度分工的AUTOACT性能

1(one)代表用所有区分数据训练单个模型
3(three)代表将差异化分为三个代理者:规划、工具和反思
工具指定(Tool Specified)表示进一步将工具代理者区分为一个工具、一个代理者

<img src="https://img.saraba1st.com/forum/202401/12/083525s9hheu7222udjouo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-083233__01.jpg</strong> (718.65 KB, 下载次数: 0)

下载附件

2024-1-12 08:35 上传

案例研究

AUTOACT(b)通过采用更科学的工具组合和更准确的工具调用成功解决了REACT(a)中的失败，通过更多的规划轮次，AUTOACT(c)可以通过继续更多轮的自我验证来验证其内部答案，虽然这也可能导致上下文更长，逐渐偏离原始问题的AUTOACT(d)

<img src="https://img.saraba1st.com/forum/202401/12/083531o4e3l0nsks0gc53k.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-083245__01.jpg</strong> (161.78 KB, 下载次数: 0)

下载附件

2024-1-12 08:35 上传

对Llama-2-70b-chat在HotpotQA上生成的轨迹进行了人工评估，对比了规划轮次的数量、思考的逻辑正确性、动作类型、动作参数以及每个轨迹的整体连贯性

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1177#       发表于 2024-1-12 18:23

Telechat

星辰语义大模型TeleChat是由中电信人工智能科技有限公司研发训练的大型语言模型系列

github项目主页:https://github.com/Tele-AI/Telechat

hugface Telechat 7B模型权重下载:https://huggingface.co/Tele-AI/Telechat-7B

hugface数据集下载地址:https://huggingface.co/datasets/Tele-AI/TeleChat-PTD

天翼云盘下载地址:https://cloud.189.cn/t/ia2QbaVzYf6z
(访问码：pkg8)

星辰语义大模型TeleChat是由中电信人工智能科技有限公司研发训练的大语言模型，采用1.5万亿 Tokens中英文高质量语料进行训练，本次开源了对话模型TeleChat-7B-bot，以及其huggingface格式的权重文件，此外，还开源了7B模型的int8和int4量化版本，2024.1月底开源12B版本模型（待开放）

TeleChat-PTD 是由电信星辰大模型TeleChat预训练语料中抽取出的的综合性大规模中文数据集，数据主要来源于网页、书籍、官方媒体等，使用规则+模型的方式进行了相关的过滤，并对数据进行了相似性去重，尽可能地提取出高质量地数据

TeleChat-PTD 数据集大约公开了2.7亿条数据，数据由纯中文文本构成，原始大小约1TB,压缩后480G，共189个文件，数据集中已经去除了其它冗余信息

github项目说明截图:

<img src="https://img.saraba1st.com/forum/202401/12/182227bvpwj8ffj2i1y221.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-182005.jpg</strong> (249.13 KB, 下载次数: 0)

下载附件

2024-1-12 18:22 上传

<img src="https://img.saraba1st.com/forum/202401/12/182227b2l2mc6k7se6xgxr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-182017.jpg</strong> (112.8 KB, 下载次数: 0)

下载附件

2024-1-12 18:22 上传

<img src="https://img.saraba1st.com/forum/202401/12/182227ezl4l2662bqwxn68.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-182029.jpg</strong> (354.53 KB, 下载次数: 0)

下载附件

2024-1-12 18:22 上传

<img src="https://img.saraba1st.com/forum/202401/12/182227cqi36v6ph66pxuac.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-182040.jpg</strong> (165.72 KB, 下载次数: 0)

下载附件

2024-1-12 18:22 上传

<img src="https://img.saraba1st.com/forum/202401/12/182227t42hq46l2f622xfg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-182048.jpg</strong> (289.94 KB, 下载次数: 0)

下载附件

2024-1-12 18:22 上传

<img src="https://img.saraba1st.com/forum/202401/12/182227gw3aovowvhtf43wk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-182059.jpg</strong> (410.29 KB, 下载次数: 0)

下载附件

2024-1-12 18:22 上传

<img src="https://img.saraba1st.com/forum/202401/12/182227vfd8t62almfy2ta2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240112-182135.jpg</strong> (338.58 KB, 下载次数: 0)

下载附件

2024-1-12 18:22 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1178#       发表于 2024-1-14 23:40

DeepSeekMoE

推动混合专家(MoE/Mixture-of-Experts)语言模型迈向终极的专业特化

github项目主页:https://github.com/deepseek-ai/DeepSeek-MoE

在大型语言模型时代，混合专家(Mixture-of-Experts)是一种有前景的架构，用于在扩大模型参数规模时管理计算成本，然而传统的MoE架构(如GShard)在确保专家的专业特化方面面临挑战，因为每次只激活𝑁个专家中的top-𝐾个专家，这使得每个专家都需要获得非重叠且专注的知识

为此，本文提出了DeepSeekMoE架构，以实现终极的专家特化，它包含两个主要策略:
1.精密地将专家细分为𝑚𝑁个，并从中激活𝑚𝐾个，从而实现对于激活专家而言更灵活的组合
2.将𝐾𝑠个专家独立为共享专家，旨在捕捉共同知识并减少路由专家中的冗余

从一个适度规模的2B参数开始，实验证明DeepSeekMoE 2B与GShard 2.9B的性能相当，而后者具有1.5倍的专家参数和计算量，此外，DeepSeekMoE 2B几乎接近具有相同总参数数量的密集对应模型的性能，这为MoE模型设定了边界上限，随后，通过将DeepSeekMoE扩展到16B参数，展现出了与LLaMA2 7B相当的性能，且仅需约40%的计算量

此外，还初步尝试将DeepSeekMoE扩展到145B参数，并始终验证了其相对于GShard架构的实质性优势，并展示其性能与DeepSeek 67B相当，且仅使用了28.5%(甚至是18.2%)的计算量

<img src="https://img.saraba1st.com/forum/202401/14/233847fl8mt7i1tmt8sh8h.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240114-233411__01.jpg</strong> (115.8 KB, 下载次数: 0)

下载附件

2024-1-14 23:38 上传

DeepSeekMoE 16B与开源模型在Open LLM排行榜上的对比，红色虚线是通过将除了DeepSeekMoE 16B以外的所有模型的数据点进行线性拟合得到的，DeepSeekMoE 16B始终以较大的优势击败了具有相似数量激活参数的模型，并且相对于比其大了约2.5倍激活参数的LLaMA2 7B实现了可竞争的性能

<img src="https://img.saraba1st.com/forum/202401/14/233855s58usou85l58ouuo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240114-233429__01.jpg</strong> (299.11 KB, 下载次数: 0)

下载附件

2024-1-14 23:38 上传

DeepSeekMoE的示意图

子图(a)展示了传统的top-2路由策略的MoE层
子图(b)说明了更细粒度的专家分割策略
子图(c)展示了共享专家独立整合的策略

这构成了完整的DeepSeekMoE架构，值得注意的是，在这三种架构中，专家参数和计算成本保持恒定

<img src="https://img.saraba1st.com/forum/202401/14/233903ezlgh6jtjth2ll9q.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240114-233456__01.jpg</strong> (432.09 KB, 下载次数: 0)

下载附件

2024-1-14 23:39 上传

验证实验的评估结果，粗体表示最佳结果，相比其他MoE架构，DeepSeekMoE展现出了明显的性能优势

<img src="https://img.saraba1st.com/forum/202401/14/233908q7875pcbrnpi4pb5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240114-233552__01.jpg</strong> (342.24 KB, 下载次数: 0)

下载附件

2024-1-14 23:39 上传

DeepSeekMoE、更大的GShard模型和更大的密集模型的对比

在“# Experts”一行中，𝑎+𝑏表示𝑎个共享专家和𝑏个路由专家
在“# Activated Experts”一行中，𝑎+𝑏表示𝑎个激活的共享专家和𝑏个激活的路由专家

DeepSeekMoE实现了与包含1.5倍专家参数和计算量的GShard模型相当的性能，此外，DeepSeekMoE几乎接近具有16倍FFN参数的密集模型的性能，这为MoE模型的模型容量设定了边界上限

<img src="https://img.saraba1st.com/forum/202401/14/233923tpc7ztfhroj7dxrj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240114-233559__01.jpg</strong> (200.1 KB, 下载次数: 0)

下载附件

2024-1-14 23:39 上传

DeepSeekMoE的消融实验，为了表达清晰，性能已经标准化为最佳性能，所有对比的模型具有相同数量的参数和激活参数，可以发现，细粒度的专家分割和共享的专家独立都对整体性能有所贡献

<img src="https://img.saraba1st.com/forum/202401/14/233931boc8p6jocgsl7lj5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240114-233607__01.jpg</strong> (130.96 KB, 下载次数: 0)

下载附件

2024-1-14 23:39 上传

禁用不同比例的top路由专家的Pile损失，值得注意的是，DeepSeekMoE对禁用top路由专家的比例更敏感，这表明DeepSeekMoE中的路由专家之间的冗余较低

<img src="https://img.saraba1st.com/forum/202401/14/233939jeeme4bcmxl614ss.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240114-233614__01.jpg</strong> (144.32 KB, 下载次数: 0)

下载附件

2024-1-14 23:39 上传

DeepSeekMoE中不同数量的激活路由专家的Pile损失，仅需4个激活的路由专家，DeepSeekMoE就能达到与GShard相当的Pile损失

<img src="https://img.saraba1st.com/forum/202401/14/234000v0qqs4vvdk3dj8kd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240114-233627__01.jpg</strong> (184.15 KB, 下载次数: 0)

下载附件

2024-1-14 23:40 上传

GShard和DeepSeekMoE(从头开始训练)激活专家数量减半的对比，在总专家参数相同且只有一半激活专家参数的情况下，DeepSeekMoE仍然优于GShard

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1179#       发表于 2024-1-15 01:19

LEGO

语言增强的多模态基准(Grounding)模型

github项目主页:https://github.com/lzw-lzw/LEGO

多模态大型语言模型在各种模态的多种任务中都展示了令人印象深刻的性能，然而，现有的多模态模型主要侧重于捕捉每个模态内的全局信息，而忽视了跨模态感知局部信息的重要性，因此，这些模型缺乏有效理解输入数据的细粒度细节的能力，这限制了它们在需要更细致理解的任务中的性能，为了解决这个限制，有必要开发能够在多个模态之间实现细粒度理解的模型，从而增强它们在广泛任务中的适用性

在本文中，提出了一种名为LEGO的语言增强多模态基准模型，除了捕捉像其他多模态模型一样的全局信息外，提出的模型在需要对输入中的局部信息进行详细理解的任务中表现出色，能够精确识别和定位图像中的特定区域或视频中的特定时刻

为了实现这个目标，设计了一个多样化的数据集构建流程，构建了一个用于模型训练的多模态、多粒度(multi-modal,multi-granularity)数据集

<img src="https://img.saraba1st.com/forum/202401/15/011915qmj8lqiysjgii8d8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-011640__01.jpg</strong> (476.7 KB, 下载次数: 0)

下载附件

2024-1-15 01:19 上传

LEGO是一个统一的端到端多模态基准模型，展示了LEGO在一系列多模态任务上的性能，包括:图像基准，视频基准，声音基准，多模态理解

<img src="https://img.saraba1st.com/forum/202401/15/011920mbrea2496eec9xza.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-011654__01.jpg</strong> (285.59 KB, 下载次数: 0)

下载附件

2024-1-15 01:19 上传

LEGO的整体结构包括每种模态(视频、图像、音频等)的独立编码器(separate encoders)和适配器(adapters)，每种模态的输入经过其独立的编码器和适配器处理后获得模态嵌入(modality embeddings)，图中展示了使用视频和图像模态的两个示例，蓝色框表示视频输入，黄色框表示图像输入

<img src="https://img.saraba1st.com/forum/202401/15/011927c77zi10ly18gvvid.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-011712__01.jpg</strong> (389.91 KB, 下载次数: 0)

下载附件

2024-1-15 01:19 上传

两阶段数据集构建流程和三阶段训练的数据集示例，第一和第二阶段的训练数据通过数据集转换获得，第三阶段的数据通过指令调整数据集生成

<img src="https://img.saraba1st.com/forum/202401/15/011931mfr99vfwr9w5f8rw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-011720__01.jpg</strong> (325.93 KB, 下载次数: 0)

下载附件

2024-1-15 01:19 上传

在指代表达理解(REC/referring expression comprehension)任务上的性能对比，模型名称后面的括号中的数字代表输入图像的分辨率，"*"表示模型使用了额外的图像区域感知模块

<img src="https://img.saraba1st.com/forum/202401/15/011936gr2y9k7yeo245ovk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-011726__01.jpg</strong> (73.68 KB, 下载次数: 0)

下载附件

2024-1-15 01:19 上传

在时间基准任务上的性能对比

<img src="https://img.saraba1st.com/forum/202401/15/011940iy3psjp3rh4zssyl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-011733__01.jpg</strong> (77.91 KB, 下载次数: 0)

下载附件

2024-1-15 01:19 上传

在Chardes-STA数据集上不同视频帧数量的结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1180#       发表于 2024-1-15 01:54

video-instruction-tuning

从数百万个视频中蒸馏视觉语言模型

github项目主页(stay tuned):https://github.com/zhaoyue-zephyrus/video-instruction-tuning

视觉语言模型近期的发展主要归功于丰富的图像文本数据，本文的目标是为视频语言模型复制这一成功，但实际上可用的人工标注视频文本数据并不足够，因此，通过应用强大的图像语言基线模型获取合成的指令数据进行微调，获得了一个视频语言模型，再利用这个视频语言模型，对数百万个视频进行自动标注，生成高质量的字幕说明

展示了适应后的视频语言模型在多个视频语言基准测试中表现良好，例如，在开放式的NExT-QA基准上超过了之前最好的结果2.8%，此外，本文模型可以为先前未见的视频生成了详细的描述，这提供了比现有方法更好的文本监督

实验表明，在这些自动生成的字幕说明上对比训练的视频语言双编码(dual-encoder)模型比那些仅利用视觉语言模型的最强基线模型提高了3.8%，本文的最佳模型在MSR-VTT零样本文本视频检索上超过了SOTA方法6%
————
总览

视频语言模型以视频和任何形式的指令作为输入，并根据指令生成文本，它可以生成多个粒度的文本描述，包括静态外观、一般行为和详细的身体动作

<img src="https://img.saraba1st.com/forum/202401/15/015416h1z8o4464owz8786.png" referrerpolicy="no-referrer">

<strong>overview.png</strong> (564.96 KB, 下载次数: 0)

下载附件

2024-1-15 01:54 上传

————
将基于图像的视觉语言模型适配到视频

将基于图像的视觉语言模型(例如PaLI-3)主要分为两个阶段进行视频领域的适应

阶段1.视觉适应，在这个阶段冻结语言部分，而用较大规模的带有简短字幕说明的视频数据集(例如Spoken Moments-in-Times)对视觉部分进行微调

阶段2.语言适应，在这个阶段冻结视觉部分，而用带有详细标题的较小规模的视频数据集对语言部分进行指令微调，在实验中，通过提示PaLM-2从视频定位叙述(Video-Localized-Narratives)中生成指令回答对

<img src="https://img.saraba1st.com/forum/202401/15/015427c158u3uss82vxzx8.png" referrerpolicy="no-referrer">

<strong>method.png</strong> (304.87 KB, 下载次数: 0)

下载附件

2024-1-15 01:54 上传

————
评估视频语言模型

将经过适配的视频语言模型与基线模型PaLI-3和之前的SOTA进行对比评估，其中重点关注零样本性能，并在没有任何微调的情况下将模型应用于下游任务的测试数据集

<img src="https://img.saraba1st.com/forum/202401/15/015433rg0k5hktzqhknt6k.png" referrerpolicy="no-referrer">

<strong>vlm_zeroshot.png</strong> (25.94 KB, 下载次数: 0)

下载附件

2024-1-15 01:54 上传

————
利用经过蒸馏的伪字幕说明(Pseudo-Captions)

通过在伪字幕说明上进行预训练来展示模型的零样本视频理解性能，这是伪字幕说明质量的一个可靠指标

<img src="https://img.saraba1st.com/forum/202401/15/015440qu8d8r844dudrb0d.png" referrerpolicy="no-referrer">

<strong>dualencoder_internvid.png</strong> (20.54 KB, 下载次数: 0)

下载附件

2024-1-15 01:54 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1181#       发表于 2024-1-15 03:26

知识翻译

一种模型压缩的新途径

github项目主页:https://github.com/zju-SWJ/KT

近年来，深度学习取得了令人瞩目的进展，但这也使得模型训练、推理和存储的开销不断增加，虽然现有的模型压缩方法致力于在保持高准确性的同时减少模型参数的数量，但它们不可避免地需要重新训练压缩模型或施加架构限制

为了克服这些限制，本文提出了一种新的框架，称为“知识翻译(KT/Knowledge Translation)”，其中，训练了一个“翻译”模型，该模型接收较大模型的参数并生成压缩的参数

KT的概念借鉴了语言翻译，它有效地利用神经网络将不同的语言转换成具有完全相同意义的形式，因此，本文探索了神经网络将不同大小的模型转换为功能相同的模型的潜力，提出了一个全面的KT框架，引入了数据增强策略以增强模型的性能，尽管训练数据受限，但成功地在MNIST数据集上证明了KT的可行性

<img src="https://img.saraba1st.com/forum/202401/15/032504oaqeqaqqtak6b216.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-032115.jpg</strong> (44.58 KB, 下载次数: 0)

下载附件

2024-1-15 03:25 上传

模型压缩方法的对比

<img src="https://img.saraba1st.com/forum/202401/15/032510c2f2junjjufftu42.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-032129.jpg</strong> (87.33 KB, 下载次数: 0)

下载附件

2024-1-15 03:25 上传

语言和知识翻译的示意图对比

<img src="https://img.saraba1st.com/forum/202401/15/032514teg25ugbycbzmm03.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-032144.jpg</strong> (119.2 KB, 下载次数: 0)

下载附件

2024-1-15 03:25 上传

知识翻译的概览图

<img src="https://img.saraba1st.com/forum/202401/15/032519r11varjjrojyno9v.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-032154.jpg</strong> (42.35 KB, 下载次数: 0)

下载附件

2024-1-15 03:25 上传

知识翻译的块架构示例

<img src="https://img.saraba1st.com/forum/202401/15/032524py963p2d2fd3dt4u.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-032210.jpg</strong> (52.55 KB, 下载次数: 0)

下载附件

2024-1-15 03:25 上传

不同架构的拟合能力评估

<img src="https://img.saraba1st.com/forum/202401/15/032528fzvve5c3s8oi3omi.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-032221.jpg</strong> (67.24 KB, 下载次数: 0)

下载附件

2024-1-15 03:25 上传

模型架构的详细信息

<img src="https://img.saraba1st.com/forum/202401/15/032554w9hxxzgxbat9tnus.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-032235.jpg</strong> (81.37 KB, 下载次数: 0)

下载附件

2024-1-15 03:25 上传

使用不同的模型架构进行参数分配和知识翻译的准确率%对比，粗体数值表示最佳结果

<img src="https://img.saraba1st.com/forum/202401/15/032559un6qfofheftd2trf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-032252.jpg</strong> (90.32 KB, 下载次数: 0)

下载附件

2024-1-15 03:25 上传

使用不同方法获得的特征可视化，基础模型训练了300个epoch以用于知识翻译

<img src="https://img.saraba1st.com/forum/202401/15/032603kxsmiofummedm6su.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-032303.jpg</strong> (60.18 KB, 下载次数: 0)

下载附件

2024-1-15 03:26 上传

使用更长的训练epoch时的准确率%和改进%的对比，粗体数值表示最佳结果，改进是当前模型的最佳准确率与表3中对应模型的最佳准确率之间的差异

<img src="https://img.saraba1st.com/forum/202401/15/032616f99zegs572ggo7kg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-032318.jpg</strong> (73.27 KB, 下载次数: 0)

下载附件

2024-1-15 03:26 上传

Small和Wide模型的训练损失和评估准确率%

<img src="https://img.saraba1st.com/forum/202401/15/032620r2l232lxuhf3x3ui.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-032338.jpg</strong> (47.56 KB, 下载次数: 0)

下载附件

2024-1-15 03:26 上传

随机初始化(左)和知识翻译的评估准确率分布，x轴上的准确率%表示评估准确率在[a-5%, a]范围内

<img src="https://img.saraba1st.com/forum/202401/15/032626e81qcl7tz7zzbggq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-032347.jpg</strong> (40.34 KB, 下载次数: 0)

下载附件

2024-1-15 03:26 上传

使用不同增强方法的准确率%对比，所有结果都来自大型语言模型，粗体数值表示最佳结果

<img src="https://img.saraba1st.com/forum/202401/15/032632lpm44xaqzq4kxmx6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-032409.jpg</strong> (32.18 KB, 下载次数: 0)

下载附件

2024-1-15 03:26 上传

将卷积转化为不同架构时的准确率%差异

<img src="https://img.saraba1st.com/forum/202401/15/032637eaky2lcyamt4l1ml.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-032432.jpg</strong> (30.85 KB, 下载次数: 0)

下载附件

2024-1-15 03:26 上传

知识翻译和随机初始化在不同训练数据%下的准确率差异%，使用训练了1000个epoch的大模型，对于每个百分比，使用100组模型参数进行评估

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1182#       发表于 2024-1-15 22:12

Mind Your Format

改进上下文学习从而迈向一致的评估

github项目主页:https://github.com/yandex-research/mind-your-format

大型语言模型展现出了从少数例子中学习解决新任务的非凡能力，然而，提示模板(prompt template)或者说输入示例的格式化(formatted)为提示的方式，是上下文学习中一个重要但常常被忽视的方面

在这项工作中，全面研究了模板格式对上下文学习性能的影响，评估了模板格式对各种模型(从770M到70B个参数)和4个标准分类数据集的影响，结果发现，选择不当的模板会将最强大的模型和推理方法的性能降低到随机猜测的级别(random guess level)，更重要的是，其中最好的模板在不同设置中，甚至是同一系列的模型之间也不能迁移

研究结果表明，当前流行的评估方法忽视了模板选择，可能会因为不同研究工作中的不同模板而导致误导性的结果，作为缓解这个问题的第一步，本文提出了模板聚合(Template Ensembles)，通过聚合多个模板的模型预测，这种简单的测试时增强(simple test-time augmentation)可以提高平均性能，并且对于随机选择的模板集具有稳健性

<img src="https://img.saraba1st.com/forum/202401/15/221201zbxoe70fc07bcccs.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-220740__01.jpg</strong> (199.92 KB, 下载次数: 0)

下载附件

2024-1-15 22:12 上传

两个演示的示例模板转换(example template transformation)，不同的提示格式会导致模型和ICL方法的不同排序，对于某个方法最佳的模板对于其他方法则可能是次优的

<img src="https://img.saraba1st.com/forum/202401/15/221206xwqj6wjsn7vus62q.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-220807.jpg</strong> (151.75 KB, 下载次数: 0)

下载附件

2024-1-15 22:12 上传

本文研究工作中使用的语言模型

<img src="https://img.saraba1st.com/forum/202401/15/221210d3we2pmps3e23mw4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-220823__01.jpg</strong> (177.53 KB, 下载次数: 0)

下载附件

2024-1-15 22:12 上传

本文研究工作中模板的所有成分的可能选择

<img src="https://img.saraba1st.com/forum/202401/15/221215piscimjq8026xujj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-220924.jpg</strong> (114.9 KB, 下载次数: 0)

下载附件

2024-1-15 22:12 上传

在基线设置下2个LLMs系列的分类准确率，30次运行中(3组演示的10个模板)的标准差在下标中表示

<img src="https://img.saraba1st.com/forum/202401/15/221221pu15rxfnv1131aff.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-221004.jpg</strong> (73.39 KB, 下载次数: 0)

下载附件

2024-1-15 22:12 上传

在2-shot设置中，上下文学习预测方法的对比

<img src="https://img.saraba1st.com/forum/202401/15/221226eoft8tswskicfefk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-221016.jpg</strong> (77.39 KB, 下载次数: 0)

下载附件

2024-1-15 22:12 上传

在直接(DIRECT)4-shot设置中选择方法的对比

<img src="https://img.saraba1st.com/forum/202401/15/221231w4x8z74uunztln4n.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-221032.jpg</strong> (186.09 KB, 下载次数: 0)

下载附件

2024-1-15 22:12 上传

在DBPedia数据集上，使用直接预测方法在随机(RANDOM)2-shot设置中，所有模型的top-10模板的IoU(Intersection-over-Union)

<img src="https://img.saraba1st.com/forum/202401/15/221236k30vttb03i0oiidi.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-221039.jpg</strong> (79.65 KB, 下载次数: 0)

下载附件

2024-1-15 22:12 上传

对随机2-shot设置下，通过不同解码方法获得的19个模型的结果进行平均IoU

<img src="https://img.saraba1st.com/forum/202401/15/221241nzaihi5uzhxaax23.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-221051.jpg</strong> (62.52 KB, 下载次数: 0)

下载附件

2024-1-15 22:12 上传

在AG News数据集上，每种示例选择方法的top-10最佳模板的IoU，METHOD-N表示使用METHOD选择了N个示例

<img src="https://img.saraba1st.com/forum/202401/15/221245iz1aavkdt5o1ok3s.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-221107.jpg</strong> (104.63 KB, 下载次数: 0)

下载附件

2024-1-15 22:12 上传

使用聚合的5个模板和单个模板对SST-2数据集的2-shot学习性能进行对比，最终结果是在5个随机种子(random seeds)上进行平均的

<img src="https://img.saraba1st.com/forum/202401/15/221251y2alwco0lqpbv0zv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-221125.jpg</strong> (50.88 KB, 下载次数: 0)

下载附件

2024-1-15 22:12 上传

对SST-2数据集上Falcon 40B的2-shot学习性能进行聚合尺寸的消融实验

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1183#       发表于 2024-1-15 22:58

 本帖最后由 Machinery 于 2024-1-15 23:01 编辑 

MCSD

多候选推测解码(Multi-Candidate Speculative Decoding)

github项目主页:https://github.com/NJUNLP/MCSD

大型语言模型在各种自然语言处理任务中展现出了惊人的能力，但是它们自回归式生成文本的过程非常耗时，为了加快生成速度，一种可行方法是采用推测解码，即从一个快速的草稿模型中生成候选片段(一系列的标记Token)，然后由目标模型并行验证这些片段

然而，候选Token的接受率(acceptance rates)受到多个因素的限制，例如模型、数据集和解码设置，本文提出了从草稿模型中采样多个候选片段，并组织它们进而批量进行验证的方法，研究组设计了高效的多候选验证算法，同时保证了目标模型的分布

本文方法在多个数据集和模型上都显示出了显著的接受率提升，始终优于标准的推测解码方法

<img src="https://img.saraba1st.com/forum/202401/15/225313obtsk0u96lybi9ai.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-223917.jpg</strong> (372.44 KB, 下载次数: 0)

下载附件

2024-1-15 22:53 上传

标准SD(a)和MCSD(b)的过程

<img src="https://img.saraba1st.com/forum/202401/15/225318p6pnkd9e51nh8213.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-224013.jpg</strong> (136.77 KB, 下载次数: 0)

下载附件

2024-1-15 22:53 上传

基于树注意力(Tree Attention)在单个序列中同时处理多个候选项，其中包含一个注意力掩码，仅允许每个Token访问其祖先(ancestors)

<img src="https://img.saraba1st.com/forum/202401/15/225417qzqyq8dq8irf8z1j.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-225020__01.jpg</strong> (270.96 KB, 下载次数: 0)

下载附件

2024-1-15 22:54 上传

使用LLaMA-68M作为草稿模型，给予不同k值的接受率(α)曲线

<img src="https://img.saraba1st.com/forum/202401/15/225524lu223l8x692k92k1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-225027__02.jpg</strong> (212.78 KB, 下载次数: 0)

下载附件

2024-1-15 22:55 上传

使用LLaMA-68M和LLaMA-160M作为草稿模型，LLaMA-33B和Vicuna-33B作为目标模型，在Alpaca和WMT数据集上的接受率(α)

<img src="https://img.saraba1st.com/forum/202401/15/225628t2y66wggy868nlcg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-225110.jpg</strong> (151.61 KB, 下载次数: 0)

下载附件

2024-1-15 22:56 上传

使用LLaMA-68M作为草稿模型，LLaMA-33B和Vicuna-33B作为目标模型，在Alpaca和WMT数据集上的每种方法的性能

<img src="https://img.saraba1st.com/forum/202401/15/225654j2c34cy3t5e4tx2c.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-225126.jpg</strong> (145.61 KB, 下载次数: 0)

下载附件

2024-1-15 22:56 上传

使用LLaMA-160M作为草稿模型，LLaMA-33B和Vicuna-33B作为目标模型，在Alpaca和WMT数据集上的每种方法的性能

<img src="https://img.saraba1st.com/forum/202401/15/225737r05elg9f51l5gfm3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-225200__01.jpg</strong> (256.17 KB, 下载次数: 0)

下载附件

2024-1-15 22:57 上传

不同k配置下的加速比和block效率(τ)，其中数据集为Alpaca，使用LLaMA-68M作为草稿模型

<img src="https://img.saraba1st.com/forum/202401/15/225757myyhabj8fkozhzoa.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-225206__01.jpg</strong> (201.68 KB, 下载次数: 0)

下载附件

2024-1-15 22:57 上传

树注意力和不同验证算法进行的消融实验，其中数据集为Alpaca，草稿模型为LLaMA-68M，temp=1(标准采样)

<img src="https://img.saraba1st.com/forum/202401/15/225803tnyrrvv2le303ee0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240115-225234.jpg</strong> (252.94 KB, 下载次数: 0)

下载附件

2024-1-15 22:58 上传

使用不同的草稿模型和目标模型，在Alpaca数据集上从k=1到k=4的接受率(α)改进

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1184#       发表于 2024-1-16 02:11

prometheus-vision

使用视觉语言模型作为细粒度评估的评判者

github项目主页:https://github.com/kaistAI/prometheus-vision

评估由视觉语言模型(VLM/Vision-Language Models)生成的长篇回答非常具有挑战性，这不仅需要检查VLM是否遵循给定的指令，还需要验证文本输出是否适当地基于给定的图像

受最近使用语言模型评估语言模型的方法的启发，在这项工作中，提出了使用VLM评估VLM的方法，为此，构造了一个名为Perception Collection的新反馈数据集，其中包含15K个用户在评估过程中可能关心的自定义评分标准

使用Perception Collection，训练了Prometheus-Vision，这是第一个能够在评估过程中理解用户定义的评分标准的开源VLM评估模型

Prometheus-Vision在与人类评估者和GPT-4V之间的皮尔逊相关系数(Pearson correlation)中表现出最高的水平，展示了其对VLM的透明和可访问评估的有效性

<img src="https://img.saraba1st.com/forum/202401/16/021035djcccc4nqsjo4cjk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240116-020722.jpg</strong> (311.98 KB, 下载次数: 0)

下载附件

2024-1-16 02:10 上传

传统的度量指标衡量回答与基准答案之间的相似性，表达能力不足，此外也无法准确指出回答在评估标准上的不足之处，相比之下，VLM作为评判者的工作流程不仅具有遵循任意评估标准的灵活性，还提供了指出具体不足之处的详细语言反馈

<img src="https://img.saraba1st.com/forum/202401/16/021043cfl5p33zzl84zkk7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240116-020736.jpg</strong> (251.28 KB, 下载次数: 0)

下载附件

2024-1-16 02:10 上传

以往的自动评估指标无法捕捉到VLM回答是否意识到美学和谐(aesthetic harmony)，通过PROMETHEUS-VISION，用户可以基于自定义的评分标准，而不是根据粗粒度的准则，如帮助性、相关性、准确性和全面性等进行评估

每个PERCEPTION COLLECTION的组件都由5个输入组成:指令、真实世界图像、待评估的回答、自定义评分标准和参考答案

基于此，PROMETHEUS-VISION被训练生成语言反馈和评分决策

<img src="https://img.saraba1st.com/forum/202401/16/021051w3k3yyn3hhvyums4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240116-020752.jpg</strong> (77.64 KB, 下载次数: 0)

下载附件

2024-1-16 02:10 上传

PERCEPTION COLLECTION中包含的每个组件的数量，请注意，反馈和评分是均匀分布的，1-5评分之间每个评分有30K个实例

<img src="https://img.saraba1st.com/forum/202401/16/021057h2haehtt27d7aqdq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240116-020812.jpg</strong> (65.75 KB, 下载次数: 0)

下载附件

2024-1-16 02:10 上传

在第5.1节中评估设置中包含的实例数量和评分标准，从每个基准中随机抽取15个实例，并手工制定了一个实例级细粒度评分标准，每个实例原本只包含一张图片和一条指令

<img src="https://img.saraba1st.com/forum/202401/16/021104nqpsbbprsbqwbzlo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240116-020819.jpg</strong> (122.16 KB, 下载次数: 0)

下载附件

2024-1-16 02:11 上传

在第5.2节的评估设置中包含的实例数量和评分标准，除了LLaVA-Bench外，从每个基准中随机抽取500个实例，每个实例原本只包含一张图片和一条指令，另外通过提示GPT-4V来添加了细粒度的评分标准和参考答案

<img src="https://img.saraba1st.com/forum/202401/16/021116jmzrkrmk6wrk96zq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240116-020837.jpg</strong> (157.37 KB, 下载次数: 0)

下载附件

2024-1-16 02:11 上传

人工评估的评分决策与GPT-4V、GPT-4、GPT-3.5-TURBO、PROMETHEUS-13B和PROMETHEUS-VISION-13B的评分决策在来自LLAVA-BENCH、VISIT-BENCH和PERCEPTION-BENCH的45个定制评分标准的实例之间的皮尔逊相关系数

PROMETHEUS-VISION与人工评估的相关性较高，特别是在包含真实世界图像的实例上

<img src="https://img.saraba1st.com/forum/202401/16/021121vvpvpmsimvmg48g4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240116-020844.jpg</strong> (96.87 KB, 下载次数: 0)

下载附件

2024-1-16 02:11 上传

GPT-4V、GPT-4和PROMETHEUS-VISION-13B生成的语言反馈质量的两两对比，结果显示，PROMETHEUS-VISION的反馈质量在57.78%的情况下与GPT-4V的反馈质量一致或优于后者

<img src="https://img.saraba1st.com/forum/202401/16/021127viirzh9rrzl0hzjh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240116-020907.jpg</strong> (160.82 KB, 下载次数: 0)

下载附件

2024-1-16 02:11 上传

通过从GPT-4V中采样跨越3个视觉指令跟随基准测试推理的分数测量了Pearson、Kendall-Tau和Spearman相关性，需要注意的是，为了测量自我一致性(self-consistency)，总共对GPT-4V进行了6次采样

在基线测试中以粗体显示最佳可比统计数据，次佳则以下划线标注，通过将GPT-4V作为参考，展示了其在多次推理中的自我一致性

<img src="https://img.saraba1st.com/forum/202401/16/021133naor4daiqxkn4ohr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240116-020914.jpg</strong> (142.56 KB, 下载次数: 0)

下载附件

2024-1-16 02:11 上传

通过从GPT-4V中采样跨越3个视觉问答基准测试推理的分数测量了Pearson、Kendall-Tau和Spearman相关性，需要注意的是，为了测量自我一致性(self-consistency)，总共对GPT-4V进行了6次采样

在基线测试中以粗体显示最佳可比统计数据，次佳则以下划线标注，通过将GPT-4V作为参考，展示了其在多次推理中的自我一致性，对于所有问题，为评估器VLM提供了细粒度的评分标准

<img src="https://img.saraba1st.com/forum/202401/16/021141m2h6fm007652d6vv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240116-020930.jpg</strong> (157.02 KB, 下载次数: 0)

下载附件

2024-1-16 02:11 上传

通过从GPT-4V中采样跨越3个字幕说明基准测试推理的分数测量了Pearson、Kendall-Tau和Spearman相关性，需要注意的是，为了测量自我一致性(self-consistency)，总共对GPT-4V进行了6次采样

在基线测试中以粗体显示最佳可比统计数据，次佳则以下划线标注，通过将GPT-4V作为参考，展示了其在多次推理中的自我一致性，对于所有问题，为评估器VLM提供了细粒度的评分标准

<img src="https://img.saraba1st.com/forum/202401/16/021149ygdjjubd0h8huzxp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240116-020944.jpg</strong> (120.3 KB, 下载次数: 0)

下载附件

2024-1-16 02:11 上传

GPT-4V在所有测试集中，根据GPT-4V和PROMETHEUS-VISION 13B的评估，不同分数的回答长度分布，x轴上的每个分数类别都标注了从每个评估器VLM接收到该特定分数的回答数量

<img src="https://img.saraba1st.com/forum/202401/16/021154uuhin3fw3fwp5g43.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240116-020956.jpg</strong> (137.34 KB, 下载次数: 0)

下载附件

2024-1-16 02:11 上传

使用PROMETHEUS-VISION或GPT-4V作为评估器VLM，对LLaVA-Bench和PERCEPTION-BENCH上的5个VLM进行评估，趋势显示PROMETHEUS-VISION可以很好地模拟GPT-4V的评估，此外，PROMETHEUS-VISION的开源性为那些开发SOTAVLM的人提供了可访问和透明的评估

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1185#       发表于 2024-1-17 21:39

AIM

大型自回归图像模型的可拓展预训练

github项目主页:https://github.com/apple/ml-aim

AIM，一组通过自回归目标进行预训练的视觉模型，这些模型受到了文本相关模型的启发，即大型语言模型(LLM)，并且具有类似的可扩展性质

具体来说，本文强调了两个关键发现:
1.视觉特征的性能与模型容量和数据数量成比例增长
2.目标函数的价值与模型在下游任务上的性能相关

通过在冻结的主干上使用70亿参数的AIM上对20亿张图像进行预训练，在ImageNet-1k上实现了84.0%的准确率，有趣的是，即使在这个规模下，依然观察到性能没有饱和的迹象，这表明AIM有可能代表大规模视觉模型的训练新领域，AIM的预训练类似于LLMs的预训练，并且不需要任何特定于图像的策略来稳定大规模训练

<img src="https://img.saraba1st.com/forum/202401/17/213748btdbrdck1rkys1k1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-212812__01.jpg</strong> (145.78 KB, 下载次数: 0)

下载附件

2024-1-17 21:37 上传

(左图)AIM的扩展倾向，随着AIM容量的扩展，观察到预训练目标的性能得到了改进，这与下游任务的性能提升直接相关

(右图)使用更大规模的非筛选网络数据集进行训练的AIM在下游任务中展现出更强的性能，下游任务的性能是基于15个图像识别基准测试中的平均注意力探针Top-1准确率计算得出的

所有模型在相同的更新次数下进行训练

<img src="https://img.saraba1st.com/forum/202401/17/213755kinnns7qf76ads8d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-212830__01.jpg</strong> (156.86 KB, 下载次数: 0)

下载附件

2024-1-17 21:37 上传

AIM预训练概览图，输入图像被分割成不重叠的图像区块，并按照Doso-vitskiy等人的方法进行线性嵌入(embedded linearly)，图像区块的特征被馈送到一个transformer模型中，其中的自注意力操作被因果遮蔽(causally masked)以防止与前面的位置发生关联，接着，一个高度参数化的MLP独立地处理每个图像区块的特征，并将其投影到像素空间，目标是将对应的输入序列向左移动一个位置，要求模型预测下一个图像区块的光栅顺序(raster order)

<img src="https://img.saraba1st.com/forum/202401/17/213807h99ejpf7hel29575.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-212846__01.jpg</strong> (128.43 KB, 下载次数: 0)

下载附件

2024-1-17 21:38 上传

前缀因果注意力(Prefix causal attention)，在预训练阶段均匀地采样一个前缀长度S，前S个图像区块的注意力被设定为双向的(bidirectional)，并且只对剩余的图像区块计算损失，在适配下游任务(adaptation to downstream tasks)时，这允许去除注意力的因果遮蔽，从而提高下游任务的性能

<img src="https://img.saraba1st.com/forum/202401/17/213814h6xe19c94r69c69r.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-212846__02.jpg</strong> (69.35 KB, 下载次数: 0)

下载附件

2024-1-17 21:38 上传

模型规格，提供了所有AIM变体的嵌入维度、层数和参数数量，还提供了预训练期间的学习率和批大小，对于参数为10亿及以上的AIM模型，预训练过程包括120万次迭代，相当于预训练期间看到1.2万亿个图像区块或50亿张图像

<img src="https://img.saraba1st.com/forum/202401/17/213822mcurieayam7kzode.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-212901__01.jpg</strong> (212.63 KB, 下载次数: 0)

下载附件

2024-1-17 21:38 上传

AIM预训练在不同模型规模下的表现，观察到随着AIM容量的增加，预训练目标的性能的明显提高，此外，随着容量更大的模型和更长的预训练时间，下游性能(IN-1k top-1)也呈单调改善(monotonically improving)，即使在500k次迭代之后，也没有观察到预训练过程中出现明显的趋于稳定的信号(clear signs of plateauing)，这表明AIM可以从更长的预训练历程中受益，需要注意的是，在训练的最后阶段，由于余弦衰减策略使得学习率有效地变为零，导致损失函数出现饱和

<img src="https://img.saraba1st.com/forum/202401/17/213854o2afkn2rzfrsklmt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-212912__01.jpg</strong> (86.83 KB, 下载次数: 0)

下载附件

2024-1-17 21:38 上传

数据集对预训练性能的影响，一方面，使用IN-1k进行预训练会导致过拟合，即使对于AIM-0.6B规模模型也是如此，另一方面，使用未经筛选的DFN-2B数据集进行预训练可以避免过拟合，但由于分布转变(distributional shift)，会收敛到同一个类似的点，通过在DFN-2B+(该数据集主要由DFN-2B样本组成，同时还包含少量IN-1k样本)上进行预训练，可以获得最佳性能

<img src="https://img.saraba1st.com/forum/202401/17/213900kzzws1w1syg5euyl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-212912__02.jpg</strong> (25.96 KB, 下载次数: 0)

下载附件

2024-1-17 21:39 上传

数据集对下游性能的影响(15个基准测试)，在下游任务中观察到与上图类似，使用DFN-2B和IN-1k的混合数据集可以获得最佳性能

<img src="https://img.saraba1st.com/forum/202401/17/213905q2qfflkla3hdl3ko.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-212918__01.jpg</strong> (66.96 KB, 下载次数: 0)

下载附件

2024-1-17 21:39 上传

FLOPs的规模关系，训练过程中的FLOPs总和与最终的验证损失相关，这表明存在类似于Hoffmann等人提出的计算驱动的缩放法则(scaling law)

<img src="https://img.saraba1st.com/forum/202401/17/213909hqlppdq6i8uewta7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-212930__01.jpg</strong> (247.34 KB, 下载次数: 0)

下载附件

2024-1-17 21:39 上传

消融提出的AIM的各种设计选择的实验，使用了一个预训练的AIM-0.6B模型和用于评估的IN-1k，报告了线性和注意力探针的结果，默认设置的AIM的主要结果以灰色突出显示

<img src="https://img.saraba1st.com/forum/202401/17/213922ywkkskbrhu3qkafb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-212940__01.jpg</strong> (89.42 KB, 下载次数: 0)

下载附件

2024-1-17 21:39 上传

自回归模式，探索了一些用于图像自回归遍历的模式，图像区块集被分成相等大小的块(equal-sized chunks)，并计算每个块的验证损失，观察到任务难度的分布随着模式在块间出现非常大的变化

<img src="https://img.saraba1st.com/forum/202401/17/213936rzg6g8g0o3egfooa.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-213417__01.jpg</strong> (51.46 KB, 下载次数: 0)

下载附件

2024-1-17 21:39 上传

MLP设计，通过改变MLP块的数量(即深度)或嵌入大小(即宽度)来改变MLP head的容量，增加容量的宽度或深度都可以改善下游性能，但深度的影响更大

<img src="https://img.saraba1st.com/forum/202401/17/213947p2fj7vfjfqfwnvnf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-213417__02.jpg</strong> (31.85 KB, 下载次数: 0)

下载附件

2024-1-17 21:39 上传

Autoregressive vs. Masking，评估了AIM的自回归目标在IN-1k上的性能，与掩码目标进行对比，保持了所有其他架构和优化组件的固定，观察到在相同的预训练设置下，自回归目标的冻结主干性能优于掩码的

<img src="https://img.saraba1st.com/forum/202401/17/213956o5bnz4zga1nmj9n4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-213438__01.jpg</strong> (438.88 KB, 下载次数: 0)

下载附件

2024-1-17 21:39 上传

冻结主干的下游评估，通过15个不同的图像识别基准测试数据集进行评估，判断AIM特征的质量

使用了冻结主干的注意力探针方法评估AIM和基线方法，AIM模型在所有基准测试上都表现出了很强的性能，尤其是AIM-7B，AIM在联合嵌入或生成方法方面优于所有其他方法，除了DINOv2使用更高分辨率图像之外，因为这可以在ImageNet上提高1-1.5%的性能

†:通过替代最后层(32nd)而从20层提取的额外特征

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1186#       发表于 2024-1-17 22:35

MultiPLY

3D世界中以多感官为目标中心的具身大型语言模型

项目主页:https://vis-www.cs.umass.edu/multiply/

github项目仓库:https://github.com/UMass-Foundation-Model/MultiPLY

人类拥有以多感官获取的多种混杂信息线索对3D世界进行主动探索和互动的能力，然而，目前的多模态大型语言模型只能被动地接收感知数据作为输入，缺乏主动与3D环境中的物体进行互动并动态地收集它们的多感官信息的能力

为了推动这一领域的研究，本文提出了MultiPLY，一种多感官具身大型语言模型(a multisensory embodied large language model)，可以将相应的视觉、声音、触觉和热度信息(visual, audio, tactile, and thermal information)等多感官交互数据纳入大型语言模型，从而建立单词、动作和感知之间的关联

为此，专门收集了一个大规模的多感官交互数据集，名为Multisensory Universe，首先使用了一个以LLM增强的具身代理者在3D环境中进行互动，收集了50万条数据，用以在生成的数据上对预训练LLM进行指令调整

首先将3D场景编码为抽象的以目标为中心的表征，然后引入表示代理者在环境中采取特定动作的动作Token，以及表示代理者在每个时间步的多感官状态观察的状态Token，在推理阶段，MultiPLY可以生成动作Token，指示代理者在环境中采取动作并获取下一个多感官状态观察，然后，观察结果通过状态Token附加回LLM，以生成后续文本或操作Token

通过一系列多样化的具身任务(包括对象检索、工具使用、多感官字幕说明和任务分解)的实验结果表明，MultiPLY相比基线模型取得了显著的性能提升

<img src="https://img.saraba1st.com/forum/202401/17/223445rp69ft9k6zqk90f5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-223041__01.jpg</strong> (600.99 KB, 下载次数: 0)

下载附件

2024-1-17 22:34 上传

提出的MultiPLY，一种多感官具身LLM，通过对以目标为中心的多感官表示(如视觉、声音、触觉和热度)进行编码，部署一个具身代理者与3D环境互动，MultiPLY在多个任务中表现出色，包括多感官字幕说明、问题回答、对话、操作、导航、工具使用、任务分解等

<img src="https://img.saraba1st.com/forum/202401/17/223451ns5455l8tbf8v855.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-223057__01.jpg</strong> (379.11 KB, 下载次数: 0)

下载附件

2024-1-17 22:34 上传

Multisensory Universe生成流程，首先在具身环境中添加一组新的可交互目标，然后提示ChatGPT生成关于环境的多样化任务，具身代理者与目标进行交互，检索多感官信息并构建交互数据

<img src="https://img.saraba1st.com/forum/202401/17/223456dc071bh01mz8wywn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-223124__01.jpg</strong> (540.63 KB, 下载次数: 0)

下载附件

2024-1-17 22:34 上传

MultiPLY概览图，首先将场景编码为一个抽象的以目标为中心的表征，而物体的多感官细节只有当代理者执行动作并与之互动时才能揭示出来，设计了一组表示代理者与环境互动动作的动作Token，交互结果则通过状态Token追加回LLM

<img src="https://img.saraba1st.com/forum/202401/17/223500xv1xilzhhhn1c17l.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-223143__01.jpg</strong> (163.45 KB, 下载次数: 0)

下载附件

2024-1-17 22:35 上传

物体检索的实验结果，-I表示模型利用预言的动作Token与环境进行交互，(Finetuned)表示在Multisensory Universe数据集上进行了微调

<img src="https://img.saraba1st.com/forum/202401/17/223505hkajzracla0j0s2r.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-223207__01.jpg</strong> (158.54 KB, 下载次数: 0)

下载附件

2024-1-17 22:35 上传

工具使用的实验结果

<img src="https://img.saraba1st.com/forum/202401/17/223623o9mf2547a5c2njp5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-223604.jpg</strong> (92.89 KB, 下载次数: 0)

下载附件

2024-1-17 22:36 上传

多感官字幕说明的实验结果

<img src="https://img.saraba1st.com/forum/202401/17/223522as21s4x1qsy2y1x6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-223237__01.jpg</strong> (684.27 KB, 下载次数: 0)

下载附件

2024-1-17 22:35 上传

MultiPLY的定性示例，MultiPLY可以与具身环境中的物体进行交互并收集多感官信息

<img src="https://img.saraba1st.com/forum/202401/17/223527jhmgkipk9a44vduh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-223248__01.jpg</strong> (84.2 KB, 下载次数: 0)

下载附件

2024-1-17 22:35 上传

多感官字幕说明的实验结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1187#       发表于 2024-1-17 23:48

PlayMyData

多平台视频游戏的精选数据集

数据集下载:https://zenodo.org/records/10262075

数十年来，电子游戏一直在数字娱乐领域占据主导地位，直到最近，软件工程(SE)社区才将其视为有价值的软件艺术品，这种认可揭示了一些研究契机，涵盖了从经验研究到应用AI技术进行分类任务等范围，在这方面，已经公开了几个经过筛选的游戏数据集供研究使用，尽管收集到的数据不足以支持高级模型的应用或进行跨学科研究，此外，其中大多数仅限于PC游戏，因此排除了著名的游戏平台，如PlayStation、Xbox和Nintendo等

在本文中，提出了PlayMyData，一个由IGDB网站收集的99864个多平台游戏的精选数据集，通过利用专用API，收集了每个游戏的相关元数据，例如描述、类型、评级、游戏视频URL和截图，此外，还通过挖掘HLT网站，为PlayMyData添加了完成每个游戏所需的时间

据目前所知，这是领域内最全面的数据集，可用于支持软件工程中不同的自动化任务，更重要的是，PlayMyData还可以用于基于所提供的多媒体数据进行跨领域调查

<img src="https://img.saraba1st.com/forum/202401/17/234749ngqvgg1t1smzm4td.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-234509.jpg</strong> (59.57 KB, 下载次数: 0)

下载附件

2024-1-17 23:47 上传

PlayMyData数据收集过程

<img src="https://img.saraba1st.com/forum/202401/17/234755xus4sw4aszsaslak.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-234521.jpg</strong> (146.6 KB, 下载次数: 0)

下载附件

2024-1-17 23:47 上传

PlayMyData数据建模

<img src="https://img.saraba1st.com/forum/202401/17/234800u8nlqsqrqzmp0lll.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-234547.jpg</strong> (231.12 KB, 下载次数: 0)

下载附件

2024-1-17 23:48 上传

按平台分组的最流行的游戏流派

<img src="https://img.saraba1st.com/forum/202401/17/234806lde2pw9wieq2edtd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240117-234604.jpg</strong> (163.75 KB, 下载次数: 0)

下载附件

2024-1-17 23:48 上传

随时间推移演变的游戏完成情况

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1188#       发表于 2024-1-18 01:08

 本帖最后由 Machinery 于 2024-1-18 01:09 编辑 

InstantID

在几秒之内进行零样本身份保留(Identity-Preserving)的生成

github项目主页:https://github.com/InstantID/InstantID

例如Textual Inversion/DreamBooth/LoRA之类的方法，在个性化图像合成方面取得了重大进步，然而，它们在实际应用中存在存储需求高、微调过程冗长和需要多个参考图像等问题，相反，现有的基于ID嵌入(ID embedding-based)的方法虽然只需要单次前向推理，但依然面临如下挑战:要么需要对多个模型的参数进行繁琐的微调，要么与社区预训练模型不兼容，要么无法保持高面部保真度

为了解决这些限制，本文引入了InstantID，一个强大的基于扩散模型的解决方案，只需单张面部图像，插件模块就能够灵活处理各种风格的图像个性化，同时确保高保真度

为了实现这一目标，设计了一个新颖的身份网络(IdentityNet)，通过施加强大的语义和弱空间条件，将面部和landmark图像与文本提示集成起来以引导图像生成，InstantID展示了出色的性能和效率，在重视身份保留的实际应用中具有极大的益处，此外，本文的工作还可以与流行的预训练文本到图像扩散模型(如SD1.5和SDXL)无缝集成，作为一个强大的适配插件

<img src="https://img.saraba1st.com/forum/202401/18/010711f2jf9j2neayy4lgz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-010456.jpg</strong> (367.35 KB, 下载次数: 0)

下载附件

2024-1-18 01:07 上传

InstantID的炫酷团队，按照作者的顺序使用InstantID生成

<img src="https://img.saraba1st.com/forum/202401/18/010716phwf4fxyhdc5zfxv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-010520.jpg</strong> (117.21 KB, 下载次数: 0)

下载附件

2024-1-18 01:07 上传

本文提出的InstantID的整体流程图，模型由三个部分组成，以保持高面部保真度

首先，应用面部编码器代替CLIP来提取语义面部特征，并使用可训练的投影层将它们投影到文本特征空间中，将投影特征作为面部嵌入

然后，引入了一个轻量级的自适应模块，其中包含解耦的交叉注意力，以支持将图像作为提示

最后，提出了IdentityNet，用于对参考的面部图像的复杂特征进行编码，并具有额外的弱空间控制

在IdentityNet中，生成过程完全由面部嵌入引导，没有任何文本信息，只有新增的模块被更新，而预训练的文本到图像模型保持冻结，以确保灵活性，训练完成后，用户可以自由生成任何风格的身份保留的高保真度图像

<img src="https://img.saraba1st.com/forum/202401/18/010804un8vaupqkb6wg5v3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-010532.jpg</strong> (302.21 KB, 下载次数: 0)

下载附件

2024-1-18 01:08 上传

InstantID的稳健性、可编辑性和兼容性示例

第1列显示了仅图像结果，在推理过程中将提示设置为空
第2-4列通过文本提示展示了可编辑性
第5-9列展示了与现有的ControlNets(canny&amp;depth)的兼容性

<img src="https://img.saraba1st.com/forum/202401/18/010810wzllfyf2cg8lqfl8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-010543.jpg</strong> (183.92 KB, 下载次数: 0)

下载附件

2024-1-18 01:08 上传

参考图像数量的影响，对于多个参考图像，将ID嵌入的平均值作为图像提示，即使只有一张参考图像，InstantID也能够取得良好的结果

<img src="https://img.saraba1st.com/forum/202401/18/010822itlyv3zhvyyuii38.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-010609.jpg</strong> (301.17 KB, 下载次数: 0)

下载附件

2024-1-18 01:08 上传

InstantID与其他方法在不同角色和风格条件下的对比

从左到右分别是IP-Adapter-SDXL，IP-Adapter-SDXL-FaceID(*表示实验版本)，IP-Adapter-SD1.5-FaceID，IP-Adapter-SD1.5-FaceID-Plus

如图所示，可以发现依赖于CLIP嵌入的IP-Adapter无法实现面部保真度，并且会导致提示控制的生成风格退化(degradation)，IP-Adapter-FaceID引入了面部嵌入，改善了面部的保真度，但仍仍然无法实现高度保真，IP-Adapter-FaceID-Plus结合了面部嵌入和CLIP，可以实现良好的面部保真度，但依然存在风格退化问题，导致面部无法融入背景风格中，相比之下，本文提出的InstantID在保持高度保真度的同时，与各种风格兼容

<img src="https://img.saraba1st.com/forum/202401/18/010828ar59rb5f3zlrrc3f.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-010617.jpg</strong> (181.79 KB, 下载次数: 0)

下载附件

2024-1-18 01:08 上传

InstantID与预训练角色LoRAs的对比，本文方法可以在没有任何训练的情况下取得有竞争力的结果

<img src="https://img.saraba1st.com/forum/202401/18/010836hesnpmk414m9k9pe.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-010634.jpg</strong> (124.87 KB, 下载次数: 0)

下载附件

2024-1-18 01:08 上传

InstantID与InsightFace Swapper的对比，在非真实风格下，本文工作在面部和背景整合上更加灵活

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1189#       发表于 2024-1-18 01:55

T2VScore

迈向更好的文本到视频生成指标

github项目主页:https://showlab.github.io/T2VScore/

github项目代码仓库:https://github.com/showlab/T2VScore

<img src="https://img.saraba1st.com/forum/202401/18/015352cj2scvhyjgppdvvj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-015156.jpg</strong> (156.47 KB, 下载次数: 0)

下载附件

2024-1-18 01:53 上传

生成模型已经展现出在合成高质量的文本、图像和视频方面的卓越能力，对于视频生成，当代的文本到视频模型展示出了令人印象深刻的能力，创作出了视觉上令人惊艳的视频，尽管如此，评估这样的视频方面存在着重大挑战，当前的研究主要采用自动化指标，如FVD、IS和CLIP分数，然而这些指标在视频内容的时间评估方面提供的分析是不完整的，因此它们不能可靠地代表真实的视频质量，此外，虽然用户研究(user studies)有潜力准确反映人类感知，但它们的时间消耗大、费力且结果往往受到主观偏见的影响

在本文中，调查了现有指标的固有限制，并引入了一种新的评估流程，即文本到视频评分(T2VScore/Text-to-Video Score)，这个指标集成了两个关键标准:
1.文本视频对齐，检查视频在表示给定文本描述方面的保真度
2.视频质量，用专家的混合评估来评估视频的整体制作水平

此外，为了评估所提出的指标并促进对它们的未来改进，提供了TVGE数据集，收集了对2543个文本到视频生成的视频在这两个标准上的人类判断，在TVGE数据集上的实验证明了所提出的T2VScore在提供更好的文本到视频生成指标方面的优势
————
文本视频对齐

视频与文字提示的匹配程度如何？

<img src="https://img.saraba1st.com/forum/202401/18/015405w513hh7ll43rl3dh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-015219.jpg</strong> (281.61 KB, 下载次数: 0)

下载附件

2024-1-18 01:54 上传

T2VScore-A:首先将文本提示输入大型语言模型(LLM)以生成问题和答案，利用CoTracker，提取辅助轨迹(auxiliary trajectory)，将其与输入视频一起输入到多模态LLM中进行视觉问答(VQA)，最终的T2VScore-A是根据VQA的准确性来衡量的
————
视频质量

合成视频的质量如何？

<img src="https://img.saraba1st.com/forum/202401/18/015424b22wrurtyurfxzzl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-015229.jpg</strong> (215.05 KB, 下载次数: 0)

下载附件

2024-1-18 01:54 上传

T2VScore-Q:选择两名具有不同偏见的评估者作为技术和语义专家，并融合他们的判断以提高视频质量评估的泛化能力
————
文本到视频生成评估(TVGE/Text-to-Video Generation Evaluation)数据集

<img src="https://img.saraba1st.com/forum/202401/18/015444jh8zc2h0maxskkj9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-015251.jpg</strong> (314.41 KB, 下载次数: 0)

下载附件

2024-1-18 01:54 上传

研究的一个不可分割的部分是评估所提出的指标在文本条件生成视频上的可靠性和稳健性，为此，提出了文本到视频生成评估(TVGE)数据集，收集了关于T2V分数研究的两个方面(对齐和质量)的丰富人类意见

<img src="https://img.saraba1st.com/forum/202401/18/015454ltnfazrp71lpsb8r.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-015310.jpg</strong> (180.52 KB, 下载次数: 0)

下载附件

2024-1-18 01:54 上传

与自然视频的领域差距，生成视频(例如在TVGE数据集中)的常见失真在空间和时间上都与自然视频中的失真不同

<img src="https://img.saraba1st.com/forum/202401/18/015502bv7wgdfla9fllltv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-015321.jpg</strong> (119.6 KB, 下载次数: 0)

下载附件

2024-1-18 01:55 上传

TVGE中的分数分布，一般来说，生成的视频在两个方面的评分都低于平均的人类评价，这表明需要不断改进这些方法以最终生成合理的视频，尽管如此，特定模型也证明了在单一维度上的良好熟练程度，例如Pika的视频质量平均得分为3.45，注意到这两个方面之间的相关性非常低(Spearman的ρ为0.223，Kendall的φ为0.152)，证明这两个维度是不同的，应该分别独立考虑

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1190#       发表于 2024-1-18 03:15

ALMA

对比偏好优化:突破机器翻译LLM性能的边界

github项目主页:https://github.com/fe1ixxu/ALMA

中等规模(Moderate-sized)的大型语言模型(LLM)——具有70亿或130亿参数的模型——在机器翻译(MT/Machine Translation)方面的性能表现出了很大的潜力，然而，即使是表现最佳的130亿参数LLM翻译模型，如ALMA，也无法与SOTA传统编码器-解码器翻译模型或更大规模的LLM(如GPT-4)相媲美

在这项研究中，弥补了这一性能差距，首先评估了LLM在MT任务中监督微调的缺点，强调了参考数据中存在的质量问题，尽管这些数据是由人类生成的，然后，与模仿参考翻译(mimics reference translations)的SFT相反，引入了对比偏好优化(CPO/Contrastive Preference Optimization)，这是一种新颖的方法，用于训练模型避免生成仅仅是足够但不完美的翻译

将CPO应用于仅有22K个平行句子和1200万参数的ALMA模型可以显著提高性能，因此而产生的模型，称为ALMA-R，在WMT'21、WMT'22和WMT'23的测试数据集上能够达到或超过WMT比赛的获胜者以及GPT-4的性能水平

<img src="https://img.saraba1st.com/forum/202401/18/031451pfprfx96xpxv3lxv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-031153.jpg</strong> (87.34 KB, 下载次数: 0)

下载附件

2024-1-18 03:14 上传

性能对比

展示了提出的ALMA-13B-R模型与其他最近发布的基于130亿参数的LLM模型以及顶级翻译系统(如GPT-4、WMT获胜者、Google翻译和NLLB-200)之间的对比

评估涵盖8个方向的WMT’22测试数据，涉及德语、捷克语、中文和俄语到英语以及逆向翻译，分数根据三个无参考模型(wmt23-cometkiwi-da-xxl、XCOMET-XXL和wmt22-cometkiwi-da)的评估进行了平均，也在所有方向上进行了平均

本文模型ALMA-13B-R是通过使用CPO方法进一步训练ALMA-13B-LoRA开发的，能够与SOTA翻译模型相匹配或超越它们，有效缩小了中等规模LLM翻译器与SOTA翻译系统之间的性能差距

<img src="https://img.saraba1st.com/forum/202401/18/031504iocsmtxcjzzsz8vi.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-031209.jpg</strong> (79.07 KB, 下载次数: 0)

下载附件

2024-1-18 03:15 上传

一个示例，展示了人工编写的黄金参考翻译可能并不总是完美无瑕的，甚至也可能被先进的翻译模型的翻译所超越，在这种情况下，参考翻译保留了“CEP”的缩写，但未提供其完整名称，模型生成的翻译中高亮显示的短语展示了黄金参考翻译中省略的部分

<img src="https://img.saraba1st.com/forum/202401/18/031510hhnw0hu44ugq35gw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-031222.jpg</strong> (96.4 KB, 下载次数: 0)

下载附件

2024-1-18 03:15 上传

通过两个与人类偏好最相关的10亿参数大小的无参考评估模型对黄金参考翻译和先进翻译模型的输出进行性能对比，结果表明，这些强大的翻译模型的平均性能甚至可能超过黄金参考翻译，在击败参考翻译方面取得了高成功率

<img src="https://img.saraba1st.com/forum/202401/18/031514ptet59f0iztbfn0y.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-031239.jpg</strong> (120.88 KB, 下载次数: 0)

下载附件

2024-1-18 03:15 上传

一组三元组翻译，从模型生成或从参考中衍生的，相伴着分别由无参考模型评估的分数，对于给定的源句子，得分最高的翻译被指定为偏好翻译，得分最低的被视为不偏好的翻译，得分居中的翻译被忽略

<img src="https://img.saraba1st.com/forum/202401/18/031519z3gcrz19zrco9117.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-031259__01.jpg</strong> (448.9 KB, 下载次数: 0)

下载附件

2024-1-18 03:15 上传

在WNT'21和WMT'22上en→xx方向的整体结果，将CPO方法应用于ALMA-13B-LoRA模型的微调显著提高了性能，达到或超过了WMT比赛的获胜者以及GPT-4的水平，粗体表示所有系统中的最高得分，深绿色框突出显示在使用偏好数据进行微调后的ALMA模型中改进超过1分的情况，而不到1分的较小增益显示在浅绿色框中，性能下降用红色框标记

<img src="https://img.saraba1st.com/forum/202401/18/031523urrwm4r234mhr8rl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-031326__01.jpg</strong> (460.58 KB, 下载次数: 0)

下载附件

2024-1-18 03:15 上传

在WMT'21和WMT'22上xx→en方向上的整体结果，其余同上

<img src="https://img.saraba1st.com/forum/202401/18/031537pnus8jdydynyszs1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-031400.jpg</strong> (79.17 KB, 下载次数: 0)

下载附件

2024-1-18 03:15 上传

在WMT'23所有六个方向上的平均性能

<img src="https://img.saraba1st.com/forum/202401/18/031542x1pckicwcrcplkik.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-031104.jpg</strong> (324.61 KB, 下载次数: 0)

下载附件

2024-1-18 03:15 上传

相关消融实验与检查

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1191#       发表于 2024-1-18 04:10

self-imagine

使用自想象(Self-Imagination)的多模态模型进行有效的单模态推理(Unimodal Reasoning)

github项目主页:https://github.com/snat1505027/self-imagine

视觉语言模型(VLMs)的潜力在处理复杂的基于文本的问题时通常被低估，特别是当这些问题可以从视觉表征中受益时，与人类通过(1)从问题中创建可视化图表和(2)推断解决问题所需的步骤的能力相呼应，本文提出了Self-Imagine

通过利用单个的视觉语言模型(VLM)生成问题的HTML结构化，然后将HTML渲染为图像，并最后使用相同的VLM，使用问题和图像来回答问题，本文方法不需要任何额外的训练数据或训练过程

使用SOTA VLM在三个数学任务和九个通用推理任务进行评估，本文方法提高了VLM在所有数学任务(gsm:+4.62％；asdiv:+4.49％；svamp:+9.30％)和大多数通用推理任务的性能(0.4％到13.20％)，同时在其他任务中达到了可比性的性能

<img src="https://img.saraba1st.com/forum/202401/18/041012n3dp1yke4czdq352.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-040727.jpg</strong> (110.18 KB, 下载次数: 0)

下载附件

2024-1-18 04:10 上传

通过单个VLM，生成关于问题的HTML图像

<img src="https://img.saraba1st.com/forum/202401/18/041017n0uc3y85uk5q5qq9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-040740.jpg</strong> (74.92 KB, 下载次数: 0)

下载附件

2024-1-18 04:10 上传

[左]不使用SELF-IMAGINE的VLM进行推理:给定一个问题(0)，VLM生成一个答案(1)

[右]使用SELF-IMAGINE的VLM进行推理:给定一个问题(0)，VLM使用HTML生成问题的结构化表征(1)，将HTML渲染为图像(2)，然后与问题一起传递给VLM(3)，最后，VLM通过结合视觉和语言模态生成答案(4)

<img src="https://img.saraba1st.com/forum/202401/18/041023sz3gngnez838uedn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-040753.jpg</strong> (134.12 KB, 下载次数: 0)

下载附件

2024-1-18 04:10 上传

SELF-IMAGINE的主要结果:SELF-IMAGINE在各种数学和符号推理任务中提高了准确率

<img src="https://img.saraba1st.com/forum/202401/18/041028i024gyuwqrgzy7qk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-040826.jpg</strong> (132.12 KB, 下载次数: 0)

下载附件

2024-1-18 04:10 上传

使用SELF-IMAGINE生成的图像在各种推理任务中与进行“仅问题”和“问题+图像”的准确率对比

<img src="https://img.saraba1st.com/forum/202401/18/041032yu01501fhu1hlq9h.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-040851.jpg</strong> (86.11 KB, 下载次数: 0)

下载附件

2024-1-18 04:10 上传

math world problem任务的示例

<img src="https://img.saraba1st.com/forum/202401/18/041038i11brgy311i3g5bp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-040905.jpg</strong> (203.51 KB, 下载次数: 0)

下载附件

2024-1-18 04:10 上传

图像在GSM8K任务中提高了推理能力的示例

<img src="https://img.saraba1st.com/forum/202401/18/041045lr8chr0i3gqrr7sw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-040919.jpg</strong> (208.43 KB, 下载次数: 0)

下载附件

2024-1-18 04:10 上传

一些BIG-Bench Hard子任务的示例

<img src="https://img.saraba1st.com/forum/202401/18/041051hchqbqfpcpgppe9p.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-040931.jpg</strong> (94.93 KB, 下载次数: 0)

下载附件

2024-1-18 04:10 上传

受图像影响的每个子任务实例的数量，在这里，“Image Hurts”表示没有图像正确回答的实例，在有图像的情况下回答错误，类似地，“Image Improves”显示了在有图像的情况下得到正确答案，并在没有图像的情况下得到错误答案的数据点

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1192#       发表于 2024-1-18 04:32

SciGLM

通过自反思指令标注和调整(Self-Reflective Instruction Annotation and Tuning)训练科学(Scientific)语言模型

github项目主页:https://github.com/THUDM/SciGLM

大型语言模型在协助科学发现方面展现出了有前景的未来，然而，最近的应用受到大型语言模型在理解复杂科学概念、推导符号方程和解决高级数值计算方面的不足的限制

为了弥合这些差距，本文引入了SciGLM，这是一个能够进行学院级别科学推理的科学语言模型套件，本文方法的核心是一个新颖的自反思指令标注框架(self-reflective instruction annotation framework)，用于解决科学领域中数据稀缺的挑战

该框架利用现有的大型语言模型为未标记的科学问题生成逐步推理，然后进行自反思的评判和修订(self-reflective critic-and-revise)过程，通过应用这个框架，创建了SciInstruct，一个包含数学、物理、化学和形式证明的多样化的高质量数据集

通过使用SciInstruct对ChatGLM系列语言模型进行了微调，提升了它们在科学和数学推理方面的能力，值得注意的是，SciGLM持续改进了基础模型(ChatGLM3-6B-Base)和更大规模的模型(12B和32B)而不会牺牲基础模型的语言理解能力，这使得SciGLM可以成为一个适合促进多样化科学发现任务的基础模型，为了使更广泛的研究社区受益，发布了SciInstruct和SciGLM

github项目说明页截图:

<img src="https://img.saraba1st.com/forum/202401/18/043223k3si3gggjxyzkxdd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-043107.jpg</strong> (359.22 KB, 下载次数: 0)

下载附件

2024-1-18 04:32 上传

<img src="https://img.saraba1st.com/forum/202401/18/043223p2bz1c8rrc82kc85.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-043116__01.jpg</strong> (92.99 KB, 下载次数: 0)

下载附件

2024-1-18 04:32 上传

<img src="https://img.saraba1st.com/forum/202401/18/043224zzize9103g14t341.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-043142.jpg</strong> (415.94 KB, 下载次数: 0)

下载附件

2024-1-18 04:32 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1193#       发表于 2024-1-18 06:06

 本帖最后由 Machinery 于 2024-1-18 06:07 编辑 

JumpCoder

通过即时修改超越自回归编码器

github项目主页:https://github.com/Keytoyze/JumpCoder

<img src="https://img.saraba1st.com/forum/202401/18/060523v5ocv1r6o6ikv6bn.gif" referrerpolicy="no-referrer">

<strong>code-demo.gif</strong> (514.13 KB, 下载次数: 0)

下载附件

2024-1-18 06:05 上传

现有的编码大型语言模型(Code LLMs)在代码生成方面展现了惊人的能力，但它们自回归式的顺序生成本质上缺乏可逆性(reversibility)，这个限制阻碍了它们像人类一样及时纠正之前缺失的语句，在编码过程中经常导致错误传播和次优的性能

本文引入了JumpCoder，一个新颖的模型无关框架(modelagnostic framework)，可以实现即时修改和非顺序生成，以增强代码LLMs的能力，JumpCoder的关键思想是在生成代码时，在必要的情况下插入新的代码，这是通过辅助的填充模型(auxiliary infilling model)与代码LLMs协同工作来实现的

由于事先确定最佳填充位置是困难的，采用了先填充后判断(infill-first, judge-later)的策略，即在生成每行代码后尝试在k个最关键的位置进行填充，并使用抽象语法树(AST/Abstract Syntax Tree)解析器和生成模型评分来有效判断每个潜在填充的有效性

通过对多个基准测试进行的广泛实验一致表明，使用六种SOTA代码LLMs，JumpCoder在所有基准测试中都取得了显著的改进，值得注意的是，在多语言HumanEval基准测试中，JumpCoder帮助代码LLMs实现了Python Pass@1改进3.6%，Java改进6.3%，C++改进3.7%

<img src="https://img.saraba1st.com/forum/202401/18/060529zeh28l0mz9y8zen9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-060017__01.jpg</strong> (417.6 KB, 下载次数: 0)

下载附件

2024-1-18 06:05 上传

展示了人类和LLM之间的区别的说明性例子，当需要一个新的变量时，人类可以跳回到前面的部分来定义它，对于LLM而言，受限于自回归性质，只能继续生成并导致错误传播

<img src="https://img.saraba1st.com/forum/202401/18/060534vjy6jjisywiub1s0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-060032__01.jpg</strong> (138.33 KB, 下载次数: 0)

下载附件

2024-1-18 06:05 上传

传统自回归编码器和提出的JUMPCODER的示意图，代码行由生成模型(蓝色)和填充模型(黑色)生成

<img src="https://img.saraba1st.com/forum/202401/18/060538xjvvz0vnl3vnnw0v.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-060046__01.jpg</strong> (293.32 KB, 下载次数: 0)

下载附件

2024-1-18 06:05 上传

JUMPCODER框架，迭代的代码更新过程包括三个重要阶段:混合生成、判断和组合(Hybrid generation, Judging and Combination)，每次迭代插入一行新的代码

<img src="https://img.saraba1st.com/forum/202401/18/060544jt1kkqiqqyhie1ie.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-060100__01.jpg</strong> (307.43 KB, 下载次数: 0)

下载附件

2024-1-18 06:05 上传

在HumanEval和MBPP上使用贪婪解码生成的Pass@1(%)结果
V=Vanilla(原生)
F=Filtered(过滤)
O=Oracle(喻示/性能上限边界)

†代表结果取自Roziere等人

<img src="https://img.saraba1st.com/forum/202401/18/060551w55ontxtl5xluxx2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-060111__01.jpg</strong> (158.46 KB, 下载次数: 0)

下载附件

2024-1-18 06:05 上传

在MultiPL-E上使用贪婪解码生成的Pass@1结果
V=Vanilla(原生)
O=Oracle(喻示/性能上限边界)

<img src="https://img.saraba1st.com/forum/202401/18/060556c2jrr0hurudd8yro.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-060126__01.jpg</strong> (170.32 KB, 下载次数: 0)

下载附件

2024-1-18 06:05 上传

JUMPCODER与各种基线的对比分析

<img src="https://img.saraba1st.com/forum/202401/18/060601sbbhfyp45uu5zfsk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-060126__02.jpg</strong> (97.22 KB, 下载次数: 0)

下载附件

2024-1-18 06:06 上传

(A)在判断阶段移除AST解析器和生成模型评分的消融实验
(B)JUMPCODER解决的不同类型的错误，“Name Error”表示未定义的标识符错误
(C)不同语言的未定义标识符错误数量

CL-I/P = CODELLAMA-INSTRUCT/PYTHON

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1194#       发表于 2024-1-18 07:29

AlphaGeometry

奥林匹克级的几何AI系统

相关博客:https://deepmind.google/discover/blog/alphageometry-an-olympiad-level-ai-system-for-geometry/

github项目主页:https://github.com/google-deepmind/alphageometry

————

<img src="https://img.saraba1st.com/forum/202401/18/072831h6tjf76jt0umzz3u.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-072809.jpg</strong> (159.3 KB, 下载次数: 0)

下载附件

2024-1-18 07:28 上传

本文AI系统在几何问题(geometry problems)上超越了SOTA方法，推动了数学推理中的AI发展

反映古希腊奥林匹克精神的国际数学奥林匹克是世界上最聪明的高中数学家的现代竞技场。这项比赛不仅展示了年轻的才华，而且已经成为了测试数学和推理方面的先进AI系统的试验场

在今天发表在《自然》杂志上的一篇论文中，介绍了AlphaGeometry，一个能够解决复杂几何问题的AI系统，其表现接近于一位奥林匹克金牌得主水平，这是AI性能的一次突破，在对30个奥林匹克几何问题的基准测试中，AlphaGeometry在奥林匹克标准时间限制内解决了25个问题，相比之下，先前的SOTA系统解决了10个几何问题，而人类金牌得主平均解决了25.9个问题

<img src="https://img.saraba1st.com/forum/202401/18/072837rhz3gqzj63qz33wg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-072819.jpg</strong> (58.9 KB, 下载次数: 0)

下载附件

2024-1-18 07:28 上传

在基准测试中，使用了30道奥林匹克几何题目(IMO-AG-30)，这些题目来自2000年至2022年的奥林匹克竞赛，AlphaGeometry在竞赛时间限制内解决了25道问题。这已经接近了人类金牌得主在这些问题上的平均得分，而之前的SOTA方法只解决了10道题

由于缺乏推理能力和训练数据，人工智能系统在几何和数学方面的复杂问题上往往存在困难，AlphaGeometry系统结合了神经语言模型的预测能力和基于规则边界的演绎引擎，二者协同工作以找到解决方案，通过开发一种生成大量合成训练数据的方法，生成了1亿个独特示例，可以在没有人类示范的情况下训练AlphaGeometry，避免了数据瓶颈

通过AlphaGeometry，展示了人工智能在逻辑推理方面日益增长的能力，以及发现和验证新知识的能力，解决奥林匹克级别的几何问题是发展深层次数学推理、迈向更高级和通用人工智能系统的重要里程碑，将开源AlphaGeometry的代码和模型，并希望与合成数据生成和训练中的其他工具和方法一起，能够在数学、科学和人工智能领域开辟新的可能性
————
AlphaGeometry应用了神经符号方法

AlphaGeometry是一个神经符号系统，由神经语言模型和符号演绎引擎组成，它们共同工作以找到复杂几何定理的证明，类似于“快思考与慢思考”的理念，一个系统提供快速、直观的想法，而另一个系统更加深思熟虑，做出理性的决策

由于语言模型在一般模式和数据关系方面表现出色，它们可以快速预测出潜在有用的结构，但往往缺乏严谨推理或解释决策的能力，而符号推理引擎则基于形式逻辑，使用清晰的规则得出结论，它们是理性且可解释的，但在独自处理大型复杂问题时往往“慢”且不灵活

AlphaGeometry的语言模型引导其符号演绎引擎寻找几何问题的可能解决方案，奥林匹克几何问题通常基于需要添加新的几何构造才能解决的图表，例如点、线或圆，AlphaGeometry的语言模型预测应该添加哪些新的构造最有用，从无限可能性中选择。这些线索有助于填补差距，并让符号引擎对图表进行进一步推断，并逐渐接近解决方案

<img src="https://img.saraba1st.com/forum/202401/18/072927jtxxs6z6twu9mfvp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-072904.jpg</strong> (54.49 KB, 下载次数: 0)

下载附件

2024-1-18 07:29 上传

AlphaGeometry解决一个简单的问题:给定问题图及其定理前提(左)，AlphaGeometry(中)首先使用其符号引擎推导有关图的新陈述，直到找到解决方案或用尽新陈述，如果找不到解决方案，AlphaGeometry的语言模型会添加一种可能有用的构造(蓝色)，为符号引擎开辟新的演绎路径。，这个循环一直持续到找到解决方案为止(右)，在此示例中，仅需要一种构造

<img src="https://img.saraba1st.com/forum/202401/18/072932iz0zpc2aqd2c323q.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-072912.jpg</strong> (104.04 KB, 下载次数: 0)

下载附件

2024-1-18 07:29 上传

AlphaGeometry解决奥林匹克竞赛问题:这是2015年国际数学奥林匹克竞赛的第三题(左)，以及AlphaGeometry解决方案的简化版本(右图)，蓝色的元素是添加的构造，AlphaGeometry的解决方案包含109个逻辑步骤(全部步骤解决方案:https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/alphageometry-an-olympiad-level-ai-system-for-geometry%20/AlphaGeometry%20solution.pdf)
————
生成1亿个合成数据示例

几何学依赖于对空间、距离、形状和相对位置的理解，是艺术、建筑、工程和许多其他领域的基础。人类可以使用纸和笔来学习几何学，通过检查图表和利用现有知识来发现新的更复杂的几何特性和关系，本文的合成数据生成方法大规模模拟这种知识构建过程，使之能够从零开始训练AlphaGeometry，而不需要任何人类示范

通过高度并行化的计算，系统开始生成十亿个几何对象的随机图表，并详尽地推导出每个图表中点和线之间的所有关系，AlphaGeometry找到了每个图表中包含的所有证明，并倒推出为了得到这些证明是否需要额外的构造，这个过程被称之为为“符号的演绎和回溯(symbolic deduction and traceback)”

<img src="https://img.saraba1st.com/forum/202401/18/072950ofpee241eap21ern.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-072939.jpg</strong> (69.68 KB, 下载次数: 0)

下载附件

2024-1-18 07:29 上传

AlphaGeometry生成的合成数据的可视化

对这个巨大的数据池进行了过滤，排除了相似的示例，最终得到了一个包含1亿个不同难度的训练数据集，其中900万个示例包含了额外的构造，由于有这么多关于这些构造如何导向证明的示例，AlphaGeometry的语言模型能够在面对奥林匹克几何问题时提出很好的建议
————
开创性地利用人工智能进行数学推理

每一个奥林匹克问题的解决方案都由AlphaGeometry经过计算机的检查和验证，还将其结果与先前的AI方法以及奥林匹克竞赛中人类的表现进行了对比。此外，数学教练和前奥林匹克金牌得主Evan Chen还评估了AlphaGeometry的一系列解决方案

陈说：“AlphaGeometry的输出令人印象深刻，因为它既可验证又干净，过去的AI解决方案在面向证明的竞赛问题上有时命中有时失(输出有时候是正确的，但需要人工检查)，AlphaGeometry没有这个弱点:它的解决方案具有机器可验证的结构，然而，尽管如此，它的输出仍然可读。人们可以想象一个通过蛮力坐标系解决几何问题的计算机程序:想象一下漫长而乏味的代数计算，AlphaGeometry并不是这样，它像学生一样使用经典的几何规则，例如角度和相似三角形”

由于每个奥林匹克竞赛只有六个问题，其中只有两个通常是关于几何的，因此AlphaGeometry只能应用于给定奥林匹克竞赛的三分之一的问题，尽管如此，仅凭其几何能力，它已成为世界上第一个能够达到国际数学奥林匹克(IMO)2000年和2015年铜牌门槛的AI模型

在几何学中，本文系统达到了国际数学奥林匹克金牌得主的水平，但目标是更大的奖项:推动下一代AI系统的推理能力，考虑到使用大规模合成数据从头开始训练AI系统的更广泛潜力，这种方法可能塑造未来AI系统发现新知识的方式，源于数学并超越数学

AlphaGeometry基于Google DeepMind和Google Research’s work的工作，开创性的使用AI进行数学推理的先河-从探索纯数学的美到使用语言模型解决数学和科学问题，最近还引入了FunSearch，利用大型语言模型在数学科学中首次发现了开放问题的答案

本研究的长期目标仍然是构建能够在数学领域进行泛化的AI系统，发展出精湛的问题解决和推理能力，这将是通用AI系统所依赖的，同时推动人类知识的边界

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1195#       发表于 2024-1-18 21:41

garfield

用辐射场对一切进行分组(Group Anything)

项目主页:https://www.garfield.studio/

github项目代码仓库:https://github.com/chungmin99/garfield

由于可以分解场景的多个粒度级别，分组在本质上是不明确的——挖掘机的轮子应该被视为独立的还是整体的一部分？ 

本文提出了使用辐射场对任何事物进行分组(GARField/Group Anything with Radiance Fields)，这是一种将3D场景从姿态图像输入分解为具有语义意义上的分组层次结构的方法，可以通过物理尺度(physical scale)来接受群体模糊性(group ambiguity):通过优化以尺度为条件的3D近似特征场(scale-conditioned 3D affinity feature field)，世界上的任何一个点都可以属于不同大小的不同组

通过Segment Anything(SAM)提供的一组2D掩码，以从粗到细的层次结构(coarse-to-fine hierarchy)的原则优化场(field)，使用尺度来一致地融合源于不同视点的冲突掩码，从场中可以通过自动树构建(automatic tree construction)或用户交互(user interaction)导出可能的分组层次结构

在各种真实自然场景中评估了GARField，发现它可以有效地提取多个级别的组:对象聚合、对象和各种子部分(clusters of objects, objects, and various subparts)，GARField本质上代表多视图一致的分组，可以产生比输入的SAM掩码更高保真度的分组，GARField的分层分组具有令人兴奋的下游应用，例如3D资产提取或动态场景理解等

<img src="https://img.saraba1st.com/forum/202401/18/213950jnvc3ce3icsnemwe.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-213519__01.jpg</strong> (517.86 KB, 下载次数: 0)

下载附件

2024-1-18 21:39 上传

GARField，它将表示为掩码的多级组提炼到NeRF中，以创建以尺度为条件的3D近似场(左上)，一旦训练完成，近似场就可以在不同的尺度上进行聚类，将场景分解为不同粒度的层次，例如将挖掘机分解为其子部件(底部)，可以通过自动提取场景中的每个组或通过用户点击来从这个层次结构中提取3D资产，如图所示(右上)

<img src="https://img.saraba1st.com/forum/202401/18/213955gjuj2kk3yj3a1q9c.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-213527__01.jpg</strong> (68.87 KB, 下载次数: 0)

下载附件

2024-1-18 21:39 上传

尺度的重要性，分组时，一个点可能属于多个组，GARField使用尺度作为条件来将这些冲突的信号统一到一个近似场中

<img src="https://img.saraba1st.com/forum/202401/18/214000a1mptmk1t5w7wpwt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-213535__01.jpg</strong> (295.17 KB, 下载次数: 0)

下载附件

2024-1-18 21:40 上传

GARField方法:(左)给定一个输入图像集，通过密集查询SAM提取一系列候选组，并通过从NeRF中反投影深度(deprojecting depth from the NeRF)分配每个物理尺度，这些尺度用于训练一个与尺度相关的近似场(右)

在训练过程中，如果采样的光线对(pairs of sampled rays)位于不同的掩码中，则将它们推开；如果它们在同一个掩码中，则拉近它们，近似(Affinity)仅在每个掩码的尺度上监督，这有助于解决它们之间的冲突

<img src="https://img.saraba1st.com/forum/202401/18/214008truz3rxrx0nkrvsf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-213549__01.jpg</strong> (148.29 KB, 下载次数: 0)

下载附件

2024-1-18 21:40 上传

密集尺度监督(Densified Scale Supervision):考虑一个聚类中的两个葡萄，如果只是简单的使用尺度进行对比损失(contrastive loss)只能在葡萄和葡萄架(grape trio)的层次上监督近似，留下了整个区间没有监督，在GARField中，通过以下方式密集增强了监督:
1.在掩码的欧几里得尺度之间增强尺度
2.对包含的更大尺度施加了辅助损失

<img src="https://img.saraba1st.com/forum/202401/18/214016vpkms9uugpze98h3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-213549__02.jpg</strong> (183.02 KB, 下载次数: 0)

下载附件

2024-1-18 21:40 上传

通过交互选择进行3D资产提取:用户可以使用点击和单尺度来交互选择与视角一致的3D组

<img src="https://img.saraba1st.com/forum/202401/18/214022tgc7ewgfof58a4a4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-213557__01.jpg</strong> (247.38 KB, 下载次数: 0)

下载附件

2024-1-18 21:40 上传

3D分解:GARField可以递归式的递减尺度查询，将场景聚类成对象及其子部分

<img src="https://img.saraba1st.com/forum/202401/18/214028bz8uz4hphii7f3cf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-213623__01.jpg</strong> (377.11 KB, 下载次数: 0)

下载附件

2024-1-18 21:40 上传

结果:从GARField中可以通过选择的top聚类从全局场景中提取对象，然后在递减的尺度上可视化它们的局部聚类，GARField可以生成完整的3D对象掩码，并根据输入的掩码将这些对象分解为有意义的子部分，通过使用高斯泼溅在3D中生成了可视化效果

<img src="https://img.saraba1st.com/forum/202401/18/214037lvsdsh8pd1w11dhg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-213649__01.jpg</strong> (185.52 KB, 下载次数: 0)

下载附件

2024-1-18 21:40 上传

Segment-Anything vs. GARField:SAM的自动掩码生成器可能会在从给定视点中回忆起所有掩码时遇到困难，特别是当存在小掩码的聚类并且摄影机距离物体较远时，相比之下，GARField的尺度条件近似场结合了来自3D的多个视点的掩码

<img src="https://img.saraba1st.com/forum/202401/18/214043pfk505mz8k3kfk9c.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-213658__01.jpg</strong> (138.3 KB, 下载次数: 0)

下载附件

2024-1-18 21:40 上传

消融实验:在没有密集层次监督的情况下，点可能在不同尺度上出现不一致的近似，可能存在以下情况:
1.在无监督尺度上出现虚假的大近似
2.在较大尺度上近似意外丢失

<img src="https://img.saraba1st.com/forum/202401/18/214050f7bve48eeawd9amw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-213709__01.jpg</strong> (111.95 KB, 下载次数: 0)

下载附件

2024-1-18 21:40 上传

3D完整性，报告了单个点与多达三个层次的层次结构的场景标注的mIOU，相比GARField，SAM在产生视图一致的良好细分组方面存在困难

<img src="https://img.saraba1st.com/forum/202401/18/214056hcf9cm9gtrc9fr8c.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-213709__02.jpg</strong> (92.04 KB, 下载次数: 0)

下载附件

2024-1-18 21:40 上传

层次分组召回(Hierarchical Grouping Recall):报告了相对于人类的不同对象的多尺度组的mIOU

<img src="https://img.saraba1st.com/forum/202401/18/214102zop370t1okv0vc4p.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240118-213717__01.jpg</strong> (186.65 KB, 下载次数: 0)

下载附件

2024-1-18 21:41 上传

从图7中选择的场景的全场景聚类可视化

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1196#       发表于 2024-1-19 05:04

scene-verse

拓展3D视觉语言学习以实现基准场景理解

项目主页;https://scene-verse.github.io/

github项目主页;https://github.com/scene-verse/sceneverse

数据集:coming soon

3D视觉语言基准(grounding)，旨在将语言与3D物理环境对齐，是发展具身代理者(embodied agents)的代表性基石，与2D领域的最新进展相比，将语言基准于3D场景面临着几个重要挑战:
1.由于不同的对象配置、丰富的属性和复杂关系，3D场景所固有的内在复杂性
2.缺乏用于基准学习的成对的3D视觉语言数据
3.缺乏统一的从基准3D数据中蒸馏知识的学习框架

在这项工作中，旨在通过系统化的提升室内环境(indoor environments)中的3D视觉语言学习潜力来解决这三个主要挑战，构造了第一个百万级的3D视觉语言数据集，SceneVerse，其中包括约68K个3D室内场景，以及由人工标注和可扩展的基于场景图的生成方法得到的250万个视觉语言对，这种扩展允许进行统一的预训练框架，既基准场景预训练(GPS/Grounded Pre-training for Scenes)

通过大量实验，在所有的现有3D基准视觉测试集上实现了SOTA性能，展示了GPS的有效性，通过在具有挑战性的3D视觉语言任务中进行的零样本转换实验，SceneVerse和GPS的巨大潜力得到了展现

<img src="https://img.saraba1st.com/forum/202401/19/050352beeag3171xc7aa68.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240119-045929__01.jpg</strong> (584.36 KB, 下载次数: 0)

下载附件

2024-1-19 05:03 上传

SCENEVERSE概览图，这是一个包含超过68000个不同室内场景和来自场景字幕说明、物体字幕说明和物体引用的250万个对齐的场景语言对的百万级3D视觉语言数据集

<img src="https://img.saraba1st.com/forum/202401/19/050359wo195fpcx8p5pfl4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240119-045957__01.jpg</strong> (154.4 KB, 下载次数: 0)

下载附件

2024-1-19 05:03 上传

SCENEVERSE与现有3D视觉语言数据集的对比，SCENEVERSE将之前的工作的数据规模扩大了一个数量级

Anno.人工标注，Syn.模板或LLM生成的描述

<img src="https://img.saraba1st.com/forum/202401/19/050405a2ldiz3mbrr5824l.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240119-050013__01.jpg</strong> (683.58 KB, 下载次数: 0)

下载附件

2024-1-19 05:04 上传

SCENEVERSE数据集的收集和统计信息，给定一个3D场景(a)，自动化流程(c)生成三种类型的描述，包括场景字幕说明、物体字幕说明和物体引用，图(b)为不同的语言来源和数据组合的对比

<img src="https://img.saraba1st.com/forum/202401/19/050410dstsz84rgxg3fagg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240119-050030__01.jpg</strong> (180.03 KB, 下载次数: 0)

下载附件

2024-1-19 05:04 上传

提出的GPS模型概览图，利用三个级别的对比对齐(Lobj、Lscene和Lref)作为LMLM的掩码语言建模目标进行模型学习

<img src="https://img.saraba1st.com/forum/202401/19/050421rv9kbzptljcokpc5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240119-050046__01.jpg</strong> (535.87 KB, 下载次数: 0)

下载附件

2024-1-19 05:04 上传

在Nr3D、Sr3D和ScanRefer上的3D视觉基准结果，使用“direct”表示在SCENEVERSE上训练的模型，没有额外的微调head，“fine-tune”表示在特定数据上进行了微调的模型，用粗体显示最佳结果

<img src="https://img.saraba1st.com/forum/202401/19/050428k9ppgg9r9jahddrj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240119-050104__01.jpg</strong> (93.58 KB, 下载次数: 0)

下载附件

2024-1-19 05:04 上传

在已建立的基准测试上的零样本迁移结果

<img src="https://img.saraba1st.com/forum/202401/19/050433k0qn7xxbxzqnzgzx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240119-050114__01.jpg</strong> (113.15 KB, 下载次数: 0)

下载附件

2024-1-19 05:04 上传

在SCENEVERSE-val上的零样本迁移结果，遵循Nr3D/Sr3D的设置使用GT(Ground Truth)物体提案评估结果

<img src="https://img.saraba1st.com/forum/202401/19/050438zhzwrzik1ehkwi2i.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240119-050123__01.jpg</strong> (85.12 KB, 下载次数: 0)

下载附件

2024-1-19 05:04 上传

模型性能与数据规模的关系，模型在ScanRefer和SCENEVERSE-val上的数据拓展致使预训练和零样本迁移设置中都有持续改进

<img src="https://img.saraba1st.com/forum/202401/19/050443ken6809dlleop8gh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240119-050130__01.jpg</strong> (52.64 KB, 下载次数: 0)

下载附件

2024-1-19 05:04 上传

在训练中对不同的场景文本对类型进行的消融实验，报告了在ScanRefer上没有额外微调的模型结果

<img src="https://img.saraba1st.com/forum/202401/19/050449grpxjprmrirmimxr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240119-050130__02.jpg</strong> (52.59 KB, 下载次数: 0)

下载附件

2024-1-19 05:04 上传

在真实或合成数据集中学习的模型在跨域迁移上的结果，"S3D"代表Structured3D

—— 来自 [S1Fun](https://s1fun.koalcat.com)

*****

####  Machinery  
##### 1197#       发表于 2024-1-19 06:19

Consolidated3D

通过确定性采样先验(Deterministic Sampling Prior)实现一致的高保真文本到3D生成

github项目主页(待整理):https://github.com/sail-sg/Consistent3D

分数蒸馏采样(SDS/Score distillation sampling)及其变体极大地推进了文本到3D生成的发展，但容易遇到几何崩溃和质量较差的纹理，为了解决这个问题，首先对SDS进行了深入分析，发现其蒸馏采样过程实际上对应于随机微分方程(SDE/stochastic differential equation)的轨迹采样:SDS沿着SDE轨迹进行采样，得到一个更少噪声的样本，然后将其作为优化3D模型的指导，然而，SDE采样中的随机性常常导致多样性和不可预测性的样本，这意味着并不总是会成为更少噪声的样本，因此不能始终正确的指导，这解释了SDS的脆弱性

对于任何SDE，总是存在一个常微分方程(ODE/ordinary differential equation)，其轨迹采样可以确定性地、一致地收敛到所需的目标点作为SDE，本文因此提出了一种新颖而有效的方法，名为Consistent3D，用于探索文本到3D生成中的ODE确定性采样先验(ODE deterministic sampling prior)

具体而言，在每个训练迭代中，给定一个由3D模型渲染的图像，首先通过预训练的2D扩散模型估计其期望的3D得分函数，并构建一个用于轨迹采样的ODE，接下来，设计了一种一致性蒸馏采样损失(consistency distillation sampling loss)，沿着ODE轨迹进行采样，生成两个相近的样本，并使用更少噪声的样本来指导另一个更嘈杂的样本，以将确定性先验提取到3D模型中

实验结果显示，Consistent3D在生成高保真度和多样化的3D对象和大规模场景方面具有很好的效果

<img src="https://img.saraba1st.com/forum/202401/19/061926moyff91n2e3s8yyz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240119-061538__01.jpg</strong> (572.46 KB, 下载次数: 0)

下载附件

2024-1-19 06:19 上传

Consistent3D生成的示例，本文方法可以根据广泛范围的文本提示生成详细、多样的3D物体和大规模场景

<img src="https://img.saraba1st.com/forum/202401/19/061930ifn7bmhnbonuwyfa.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240119-061557__01.jpg</strong> (171 KB, 下载次数: 0)

下载附件

2024-1-19 06:19 上传

随机微分方程(SDE)和常微分方程(ODE)中(反向)轨迹采样的对比

<img src="https://img.saraba1st.com/forum/202401/19/061934kzt5tx5x95xxbxjt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240119-061609__01.jpg</strong> (85.57 KB, 下载次数: 0)

下载附件

2024-1-19 06:19 上传

CDS概览图，在每个训练迭代中，渲染图像被固定噪声扰动，然后作为确定性流(deterministic flow)的起点用于计算CDS损失

<img src="https://img.saraba1st.com/forum/202401/19/061938fzbdt3tfq4wfnfdm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240119-061630__01.jpg</strong> (470.64 KB, 下载次数: 0)

下载附件

2024-1-19 06:19 上传

Consistent3D可以生成与给定文本提示高度相关的多样且高保真度的物体或大规模场景

<img src="https://img.saraba1st.com/forum/202401/19/061943pvo0vzponrc5zjpi.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240119-061646__01.jpg</strong> (361.82 KB, 下载次数: 0)

下载附件

2024-1-19 06:19 上传

文本到3D生成的定性对比，本文方法产生了更加真实且更稳健的几何结果

<img src="https://img.saraba1st.com/forum/202401/19/061948pulejytp7vftlfyx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240119-061715__01.jpg</strong> (462.98 KB, 下载次数: 0)

下载附件

2024-1-19 06:19 上传

Consistent3D各组件贡献的消融实验:
(a)随机时间步计划
(b)预定时间步计划
(c)每次迭代中的随机噪声
(d)本文提出的配置

<img src="https://img.saraba1st.com/forum/202401/19/061953irddh5z1dnl1zqcl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240119-061719__01.jpg</strong> (77.03 KB, 下载次数: 0)

下载附件

2024-1-19 06:19 上传

CLIP R-Precision的定量对比，分数是从DreamFusion画廊的40个提示中平均计算得出的

—— 来自 [S1Fun](https://s1fun.koalcat.com)

*****

####  巨魔型美羽  
##### 1198#       发表于 2024-1-19 11:03

请教一下，图像多标签分类现在有什么离线部署的解决方案吗，想要识别一些遥感图像是否有云、过曝、条纹等情况。训练集已有，自己炼模型的方案和能微调的现成模型有什么推荐的吗<img src="https://static.saraba1st.com/image/smiley/face2017/068.png" referrerpolicy="no-referrer">


*****

####  Machinery  
##### 1199#       发表于 2024-1-20 00:51

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=63698955&amp;ptid=2126390" target="_blank">巨魔型美羽 发表于 2024-1-19 11:03</a>
请教一下，图像多标签分类现在有什么离线部署的解决方案吗，想要识别一些遥感图像是否有云、过曝、条纹等情 ...</blockquote>
感觉arxiv里很多相关领域的文章，微调或者训练分类模型都行吧，甚至vlm直接练进去图像特征也行…找个深度学习社区，飞桨/modelscope/kaggle/arxiv/github/hugface之类的搜搜关键字

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1200#       发表于 2024-1-20 03:50

OMG-Seg

一种模型足以适用于所有分割任务吗？

项目主页:https://lxtgh.github.io/project/omg_seg/

github项目代码仓库:https://github.com/lxtGH/OMG-Seg

在本文中，尝试统一解决各种不同分割任务，而传统方法上每种任务都由不同或部分统一的模型处理，本文提出了OMG-Seg，一种足以高效且有效地处理所有分割任务的模型，包括图像语义分割、实例分割、全景分割以及所对应的视频任务、开放词汇设置、基于提示的交互式分割(例如SAM)和视频对象分割

据本文所知，这是第一个可以在一个模型中处理所有这些任务并取得令人满意的性能的模型，OMG-Seg，一种基于Transformer的编码器-解码器架构，具有特定于任务的查询和输出，可以支持数十个不同的分割任务，并在各种任务和数据集上显著减少计算和参数开销，在协同训练(co-training)过程中严格评估了任务之间的相互影响和相关性

<img src="https://img.saraba1st.com/forum/202401/20/034924v4d4biq4gmazb8yc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-034314__01.jpg</strong> (538.48 KB, 下载次数: 0)

下载附件

2024-1-20 03:49 上传

OMG-Seg可以在一个框架中处理十多种不同的分割任务，包括图像级和视频级分割任务，交互式分割和开放式词汇分割，据目前所知，这是第一个统一这四个方向的模型

<img src="https://img.saraba1st.com/forum/202401/20/034929iwplxr3f6ouxrfof.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-034324__01.jpg</strong> (215.31 KB, 下载次数: 0)

下载附件

2024-1-20 03:49 上传

不同模型的设置对比，在这里列出了几种代表性的方法，而本文提出的OMG-Seg可以在一个模型中执行各种分割任务

<img src="https://img.saraba1st.com/forum/202401/20/034935gnnzsmlc7c77a2jl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-034330__01.jpg</strong> (276.53 KB, 下载次数: 0)

下载附件

2024-1-20 03:49 上传

OMG-Seg的元架构

(a)OMG-Seg遵循Mask2Former的架构，包括一个主干网络(CLIP视觉编码器)，一个像素解码器，一个掩码解码器，不同的部分包括用于图像和视频分割的共享掩码解码器和一个视觉提示编码器，使用两种类型的掩码查询(比如语义查询)，用于实例/语义掩码或掩码管(mask tubes)，以及位置查询(location queries)的编码框或点提示

(b)掩码解码器中的一个解码器层，位置查询跳过了自注意力操作，因为它们只与图像内容和位置提示有关

(c)OMG-Seg在训练和推理中的前向传递过程，使用CLIP的文本编码器来表示类别名称，并通过计算掩码特征和文本嵌入之间的余弦相似度来对掩码进行分类

<img src="https://img.saraba1st.com/forum/202401/20/034956nbwvw89ly87tbq8k.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-034341__01.jpg</strong> (323.39 KB, 下载次数: 0)

下载附件

2024-1-20 03:49 上传

OMG-Seg在图像、视频、开放词汇和类似SAM的设置上的实验结果

*表示模型在Object365数据集上进行了预训练，由于页面限制，只列出了一些代表性的方法，其结果是五个不同实验的平均结果

<img src="https://img.saraba1st.com/forum/202401/20/035005mjwe66ybmtze0eel.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-034345__01.jpg</strong> (160.12 KB, 下载次数: 0)

下载附件

2024-1-20 03:50 上传

OMG-Seg在多个数据集设置上的实验结果，使用五个不同的数据集进行了12个epoch的平衡的联合协同训练，还在同一代码库中实现了对比基准

<img src="https://img.saraba1st.com/forum/202401/20/035015iulb6l3bllblrluy.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-034356__01.jpg</strong> (329.04 KB, 下载次数: 0)

下载附件

2024-1-20 03:50 上传

<img src="https://img.saraba1st.com/forum/202401/20/035015tob7l9ooohsj0l93.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-034423__01.jpg</strong> (225.16 KB, 下载次数: 0)

下载附件

2024-1-20 03:50 上传

消融实验

<img src="https://img.saraba1st.com/forum/202401/20/035020kpmepjzn47xx477n.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-034412__01.jpg</strong> (553.13 KB, 下载次数: 0)

下载附件

2024-1-20 03:50 上传

OMG-Seg模型的功能可视化，列举了来自四个数据集的五个不同任务作为示例，本文方法在一个共享模式中实现了高质量的分割、追踪和交互式分割

<img src="https://img.saraba1st.com/forum/202401/20/035028kp3vmknpo4oamovo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-034435__01.jpg</strong> (354.73 KB, 下载次数: 0)

下载附件

2024-1-20 03:50 上传

对OMG-Seg模型的更多功能可视化，除了主要论文中提到的五个不同任务外，还对ADE-20k数据集上的开放词汇分割结果进行了可视化，以及ImageNet 1k数据集上的开放词汇交互分割结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1201#       发表于 2024-1-20 04:16

LGVI

通过多模态大型语言模型实现语言驱动的视频重绘(Language-Driven Video Inpainting)

项目主页:https://jianzongwu.github.io/projects/rovi/

github项目代码仓库(待整理):https://github.com/jianzongwu/Language-Driven-Video-Inpainting

<img src="https://img.saraba1st.com/forum/202401/20/041534mzzebuidoiferez5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-041422.jpg</strong> (155.91 KB, 下载次数: 0)

下载附件

2024-1-20 04:15 上传

本文引入了一项新任务——基于语言的视频重绘，通过使用自然语言指令来指导重绘过程，这种方法克服了传统视频重绘方法的局限性，传统方法一般依赖于手动标记的二值化掩码(binary masks)，这一过程通常繁琐乏味且需要密集劳动

提出了ROVI(Remove Objects from Videos by Instructions)数据集，其中包含5650个视频的9091个重绘结果，用于支持该任务的训练和评估

还提出了一种新颖的基于扩散的语言驱动视频重绘框架，这是该任务的首个端到端基准模型，整合了多模态大型语言模型有效的理解和执行基于语言的复杂重绘请求

全面的实验结果展示了数据集的多样性以及模型在各种语言指导的重绘场景中的有效性
————
LGVI框架

<img src="https://img.saraba1st.com/forum/202401/20/041545kknz15lli9p9c9r2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-041433.jpg</strong> (142.08 KB, 下载次数: 0)

下载附件

2024-1-20 04:15 上传

提出的LGVI和LGVI-I框架，通过增加一个时间维度来扩展U-Net以支持视频输入，为了确保生成的视频在时间上的一致性，在交叉注意力和FFN层之间引入了一个时间注意力模块

此外，还提出了一个掩码解码器模块，用于在重绘任务中提供显式指导，通过MLLM联合训练来增强LGVI以用于交互式视频重绘，从而得到了基线模型LGVI-I，MLLM的输出包括一组提示Token，这些Token被输入到U-Net的交叉注意力中
————
ROVI数据集

<img src="https://img.saraba1st.com/forum/202401/20/041549fzkjg6s2zlfniww2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-041440.jpg</strong> (157.41 KB, 下载次数: 0)

下载附件

2024-1-20 04:15 上传

所提出的ROVI数据集的统计数据，ROVI数据集是第一个用于语言引导视频重绘(LVI/language guided video inpainting)和交互式视频重绘(IVI/interactive video inpainting)任务的数据集
————
视觉结果

<img src="https://img.saraba1st.com/forum/202401/20/041554jl8flflfzj5kul7l.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-041447.jpg</strong> (152.1 KB, 下载次数: 0)

下载附件

2024-1-20 04:15 上传

LGVI与参考视频重绘的基线模型进行的对比

<img src="https://img.saraba1st.com/forum/202401/20/041559qypdpmdcmvrh4w9v.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-041453.jpg</strong> (133.25 KB, 下载次数: 0)

下载附件

2024-1-20 04:15 上传

更多有关参考视频重绘结果

<img src="https://img.saraba1st.com/forum/202401/20/041603fgcdodl1ldw1i1gt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-041501.jpg</strong> (301.96 KB, 下载次数: 0)

下载附件

2024-1-20 04:16 上传

LGVI-I的交互式视频重绘结果

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1202#       发表于 2024-1-20 06:17

The Manga Whisperer

自动从漫画中生成转录对话

github项目主页:https://github.com/ragavsachdeva/magi

在过去的几十年中，漫画已经超越了文化和语言的界限，成为了一种真正的全球热潮，然而，漫画对于视觉障碍的人来说很难接触，因为它严重依赖于视觉线索和插图，在这项工作中，尝试解决这个重大障碍，确保每个人都能欣赏和积极参与漫画

具体而言，本文解决的问题是对话记录，即以完全自动的方式生成谁在何时说了什么的文字转录，为此做出了如下贡献:
(1)提出了一个统一的模型Magi，能够(a)检测面板、文字框和角色框，(b)通过身份对角色进行聚类(不需要预先知道聚类的数目)，以及(c)将对话与说话者关联起来
(2)提出了一种新颖的方法，能够按阅读顺序对检测到的文字框进行排序并生成对话转录
(3)使用公开可用的[英文]漫画页，为这个任务标注了一个评估基准

<img src="https://img.saraba1st.com/forum/202401/20/061524aand6gpapf9djaca.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-061159__01.jpg</strong> (692.05 KB, 下载次数: 0)

下载附件

2024-1-20 06:15 上传

给定一个漫画页，本文模型可以:
(a)检测面板、文本块和角色框
(b)按照角色身份对角色框进行聚类
(c)将文本与说话者关联起来
(d)按正确的阅读顺序生成对话转录

这里展示了在Yoshihiro Togashi的《猎人×猎人》漫画页面上预测的面板(绿)、文本块(红)和角色(蓝)，通过连接角色框中心的线来显示预测的角色身份关联，为了视觉清晰，没有明确显示文本与说话者的关联，但提供了生成的转录

<img src="https://img.saraba1st.com/forum/202401/20/061537j67ik4quim7zw6wh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-061208__01.jpg</strong> (292.91 KB, 下载次数: 0)

下载附件

2024-1-20 06:15 上传

Magi架构:
给定一个漫画页作为输入，本文的模型预测面板、文本块和角色的边界框，并关联检测到的角色-角色(character-character)和文本-角色(text-character)对

模型将高分辨率漫画页作为输入送入CNN主干网络，然后通过Transformer编码器-解码器生成N×[OBJ]+[C2C]+[T2C]个Token，[OBJ] Token由检测头(框和类)处理，以获得边界框及其分类，检测到的对象对应的[OBJ] Token与[C2C]和[T2C]一起处理成对，通过角色匹配模块和说话者关联模块进行处理，从而得到角色聚类和对话记录

<img src="https://img.saraba1st.com/forum/202401/20/061547hwitqq3pzi4tcfak.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-061222__01.jpg</strong> (618.77 KB, 下载次数: 0)

下载附件

2024-1-20 06:15 上传

面板排序方法，右方为本文的排序方法，图像来源Prism Heart ©Mai Asatsuki

<img src="https://img.saraba1st.com/forum/202401/20/061553uerqebe0ri7qz2da.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-061228__01.jpg</strong> (219.44 KB, 下载次数: 0)

下载附件

2024-1-20 06:15 上传

训练和评估数据集，在列中，提供了每个任务的标注数量

P=面板，T=文本，C=角色，C2C=角色-角色正样本对，T2C=文本-角色对

†自动化生成
‡仅适用于8488张图像
††使用启发式动态挖掘(mined using heuristics dynamically)

<img src="https://img.saraba1st.com/forum/202401/20/061657ycec3eg818uq081p.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-061244__01__02.jpg</strong> (547.08 KB, 下载次数: 0)

下载附件

2024-1-20 06:16 上传

<img src="https://img.saraba1st.com/forum/202401/20/061657vd2d68kgs63y23ff.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-061244__01__01.jpg</strong> (522.43 KB, 下载次数: 0)

下载附件

2024-1-20 06:16 上传

Magi模型确定的角色、文本块和面板的边界框预测，以及聚类预测(作为节点和边)，为了可视化，删除了已经建立连接的角色之间的冗余的连接

请注意，尽管已经产生了:遮挡/部分可见性(girl: A4, hand: B1)，视点变化(boy: A5, girl: A2)，和变化的保真度(girl: A1, boy: B2)，该模型仍然成功匹配了角色，该模型还可以检测非人类角色(dog-like creatures: A1, octopus-like creature: B3)

还展示了一个失败案例，模型错误地匹配了两个不同的角色(one is wearing checked scarf, while the other is wearing checked coat, they are brothers and look similar)

<img src="https://img.saraba1st.com/forum/202401/20/061708v3wdg089h0hia8cv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-061254__01.jpg</strong> (799.01 KB, 下载次数: 0)

下载附件

2024-1-20 06:17 上传

Magi模型生成的文本到说话者的预测，每个预测的文本框都通过一条线连接到一个预测的角色框，线的不透明度反映了模型的置信度，线越暗，模型的置信度越高，每个预测的角色框中心有一个基于聚类预测的数字

还展示了最终生成的转录，请注意，所有的对话都按照正确的阅读顺序排列，对于置信度较低(&lt;0.4)的文本到说话者预测，在生成的转录中用⟨?⟩替换预测的说话者，并让读者从上下文中推理

<img src="https://img.saraba1st.com/forum/202401/20/061714dopvommnakc3n5pn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-061310__01.jpg</strong> (67.77 KB, 下载次数: 0)

下载附件

2024-1-20 06:17 上传

检测结果，报告的平均精度结果边界上限为1.0

<img src="https://img.saraba1st.com/forum/202401/20/061718t274u4e82ryeu45i.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-061310__02.jpg</strong> (427.71 KB, 下载次数: 0)

下载附件

2024-1-20 06:17 上传

角色聚类结果，使用几个不同指标报告结果，它们的边界上限均为1.0

<img src="https://img.saraba1st.com/forum/202401/20/061723iw14vsiw4lqws6o0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-061310__03.jpg</strong> (36.92 KB, 下载次数: 0)

下载附件

2024-1-20 06:17 上传

说话者关联结果，报告的Recall@#text结果边界上限为1.0

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1203#       发表于 2024-1-20 08:43

 本帖最后由 Machinery 于 2024-1-20 08:45 编辑 

Edit One for All

交互式批量图像编辑

项目主页:https://thaoshibe.github.io/edit-one-for-all/

github项目代码仓库:https://github.com/thaoshibe/edit-one-for-all

近年来，图像编辑取得了显著的进步，借助增加的人类控制，现在可以利用多种方式编辑图像，从在文本中指定我们想要修改的内容，到直接以交互式进行编辑(例如基于点的方式拖动图像的内容)，然而，大多数研究仍集中在一次编辑单张图像，是否能够同时大量编辑图像，以及如何做到这一点，仍然是一个未被充分研究的问题

本文旨在最大程度减少编辑过程中的人类监督，提出了一种使用StyleGAN作为媒介的交互式批量图像编辑的新方法，给定用户在示例图像中指定的编辑(例如使面部朝向正面），本文方法可以自动将该编辑转移到其他测试图像上，无论它们的初始状态(姿势)如何，都可以达到相同的最终状态(例如，面部都面朝正前方)

大量实验证明，本文方法进行的编辑具有与现有的单图像编辑方法相似的视觉质量，同时具有更高的视觉一致性，并节省了大量时间和人力
————

<img src="https://img.saraba1st.com/forum/202401/20/084301tpe9xghpzg95p3uz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-084101__01.jpg</strong> (367.78 KB, 下载次数: 0)

下载附件

2024-1-20 08:43 上传

单张图像编辑与批量图像编辑之间的区别在于:
(a)以往的研究主要集中在单张图像编辑上
(b)本文则专注于批量图像编辑，即用户对一张图像的编辑会自动传递到新的图像上，使得它们最终都达到相同的状态，而不用考虑它们的初始状态
————
交互式批量图像编辑

<img src="https://img.saraba1st.com/forum/202401/20/084311ki8u0u16u4zau1ue.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-084108.jpg</strong> (273.71 KB, 下载次数: 0)

下载附件

2024-1-20 08:43 上传

当用户调整示例图像(顶部)中的编辑强度时，所有测试图像将自动更新(红色边框表示根据拖拽点进行移动)
————
框架

<img src="https://img.saraba1st.com/forum/202401/20/084318ig0u56no8ldzrazo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-084140__01.jpg</strong> (217.28 KB, 下载次数: 0)

下载附件

2024-1-20 08:43 上传

a.设定
b.简单方法:对于一个示例有效的编辑方向可能无法很好地推广到测试图像
c.优化编辑方向:优化对于示例和测试图像都有效的全局一致方向
d.调整编辑强度:确保一致的最终状态需要调整每个测试图像的编辑强度
————
多次编辑

<img src="https://img.saraba1st.com/forum/202401/20/084339dgv2vlg2gksmx2vb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-084146.jpg</strong> (145.92 KB, 下载次数: 0)

下载附件

2024-1-20 08:43 上传

在传递到测试图像之前，可以对示例图像应用多次编辑
————
限制

<img src="https://img.saraba1st.com/forum/202401/20/084345tcnrzu0q7qyyzew6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-084158.jpg</strong> (174.78 KB, 下载次数: 0)

下载附件

2024-1-20 08:43 上传

a.失败案例:本文方法可能在捕捉细节方面遇到困难(卷曲的象鼻)
b.示例-测试图像相似性:为了获得最佳结果，示例和测试图像应属于相同的语义领域(都具有长发)，以确保正确传递编辑
c-d.有趣的用例:编辑可能会被错误解释，导致意外的结果，例如错误的眨眼方位，或者无意中翻转的马(d)

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1204#       发表于 2024-1-20 21:16

MM-Interleaved

通过多模态特征同步器(Multi-modal Feature Synchronizer)进行交错的图像文本生成建模

github项目主页:https://github.com/OpenGVLab/MM-Interleaved

为交错的图像文本数据开发生成模型同时具有研究价值与实际价值，它要求模型理解交错的序列，并随后生成图像和文本，然而，现有的尝试受到了固定数量的视觉Token无法高效捕捉图像细节问题的限制，这在多图像场景中尤为严重

为了解决这个问题，本文提出了MM-Interleaved，一种用于交错图像文本数据的端到端生成模型，它引入了一个多尺度和多图像特征的同步器模块(a multi-scale and multi-image feature synchronizer module)，允许在生成过程中直接访问先前上下文中的细粒度图像特征，MM-Interleaved在配对数据和交错的图像文本语料库上进行了端到端的预训练，并通过监督微调阶段进一步增强，改善了模型遵循复杂多模态指令的能力

实验证明了MM-Interleaved遵循多模态指令认知视觉细节和生成符合文本和视觉条件的一致图像方面的多功能性

<img src="https://img.saraba1st.com/forum/202401/20/211424oh5x27l7ccj532wj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-210528.jpg</strong> (150.34 KB, 下载次数: 0)

下载附件

2024-1-20 21:14 上传

多模态特征同步器的示意图

在自回归生成交错的图像文本序列时，除了使用自注意力与低分辨率图像Token进行交互外，MM-Interleaved中的Token还可以使用多模态特征同步器来跨越多尺度对高分辨率图像特征进行交叉关注(cross-attend)，多模态特征同步器可以确保交叉注意力在图像和文本Token之间具有精确的相同因果关系(causal relation)

<img src="https://img.saraba1st.com/forum/202401/20/211432k6se7hbzenuzjqlf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-210545.jpg</strong> (96.67 KB, 下载次数: 0)

下载附件

2024-1-20 21:14 上传

不同类型的图像文本生成建模的对比

(a)和(b)只能生成文本，(c)和(d)可以生成图像和文本，除(d)之外的所有类型都受到了上下文不敏感(context-insensitive)的重采样提取所导致的固定数量的视觉Token的限制，最终无法有效捕捉图像细节，并在多图像场景中出现问题

<img src="https://img.saraba1st.com/forum/202401/20/211440wok6i7xsx0m676s7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-210603.jpg</strong> (631.62 KB, 下载次数: 0)

下载附件

2024-1-20 21:14 上传

所提出的MM-Interleaved模型的架构，红线表示如何生成和利用多尺度图像特征，MM-Interleaved结合了图像编码器，既能提取高分辨率的多尺度图像特征，又能将每个图像映射到固定数量的低分辨率视觉Token中

这些视觉Token伴随文本Token一起输入到多模态LLM中，LLM使用特征同步模块(feature synchronization module)提取高分辨率图像细节，并自回归式生成文本Token，之后基于DM的图像解码器根据来自LLM的先前上下文的特征和特征同步模块的多尺度图像特征生成下一张图像

<img src="https://img.saraba1st.com/forum/202401/20/211445l0ittswwqgaqmwgg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-210631.jpg</strong> (147.44 KB, 下载次数: 0)

下载附件

2024-1-20 21:14 上传

MMFS模块的架构，查询特征(query feature)通过线性层传递，并添加到图像索引嵌入(image index embedding)中，通过使用两个线性层分别预测每个图像的采样偏移(sampling offsets)和非归一化的注意力权重(unnormalized attention weights)，采样偏移与查询的参考点(query’s reference point)相加，形成相应的采样位置(sampling locations)，这些位置在相同图像的所有特征图中共享和重新缩放(rescaled)，输出特征是从这些点采样的空间特征的加权和

<img src="https://img.saraba1st.com/forum/202401/20/211451jaf5q7ykybf0bylg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-210650__01.jpg</strong> (422.81 KB, 下载次数: 0)

下载附件

2024-1-20 21:14 上传

多模态理解评估

“H”表示使用内部数据，“I”表示训练中包含了某些基准的训练图像，“A”表示训练中某些基准的训练标注是可见的

<img src="https://img.saraba1st.com/forum/202401/20/211457vt3h22h22pooio6l.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-210718.jpg</strong> (115.25 KB, 下载次数: 0)

下载附件

2024-1-20 21:14 上传

在指代表达理解任务上的监督微调结果，"*"表示使用额外的自构建的基准数据集，并使用大于224的图像分辨率进行训练

<img src="https://img.saraba1st.com/forum/202401/20/211520w9gf9fmfzpfg94om.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-210730.jpg</strong> (226.01 KB, 下载次数: 0)

下载附件

2024-1-20 21:15 上传

在MS-COCO和LN-COCO上的零样本文本到图像生成结果，报告了FID

<img src="https://img.saraba1st.com/forum/202401/20/211527egvmlpd5z8decwmp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-210750__01.jpg</strong> (183.76 KB, 下载次数: 0)

下载附件

2024-1-20 21:15 上传

MM-Interleaved的图像生成能力的对比分析

<img src="https://img.saraba1st.com/forum/202401/20/211538nw761nwdn21xdl2v.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-210812.jpg</strong> (215.31 KB, 下载次数: 0)

下载附件

2024-1-20 21:15 上传

评估基准的总结，包括图像字幕说明、视觉问答、指代表达理解和图像生成

<img src="https://img.saraba1st.com/forum/202401/20/211543pcgr4nu62r2skwuv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-210826.jpg</strong> (190.4 KB, 下载次数: 0)

下载附件

2024-1-20 21:15 上传

用于文本生成的提示模板

<img src="https://img.saraba1st.com/forum/202401/20/211547h2kjn9ifjsfh4rse.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-211020.jpg</strong> (154.6 KB, 下载次数: 0)

下载附件

2024-1-20 21:15 上传

TextVQA的定性结果，每个示例由用户查询、带有MMFS的MM-Interleaved给出的答案以及不带MMFS的MM-Interleaved给出的答案组成，图像形状被归一化以便可视化

<img src="https://img.saraba1st.com/forum/202401/20/211552wjjqkckggf2in7nf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-211036.jpg</strong> (149.8 KB, 下载次数: 0)

下载附件

2024-1-20 21:15 上传

在RefCOCOg上的指代表达理解，每个示例包括用户查询、使用MMFS预测的框和不使用MMFS预测的框，图像形状已经归一化以便可视化

<img src="https://img.saraba1st.com/forum/202401/20/211601t3uzkp33h2uq35hp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-211056.jpg</strong> (439.25 KB, 下载次数: 0)

下载附件

2024-1-20 21:16 上传

在ADE20k上的分割到图像生成(Segmentation-to-Image Generation)，每行都是一个示例，包括四个图像，分别是输入分割图、基准答案图像、使用MMFS生成的图像和不使用MMFS生成的图像，基准图像和分割图的形状已经归一化以便可视化，当没有使用MMFS时，生成的结果与输入的分割图缺乏空间对齐

<img src="https://img.saraba1st.com/forum/202401/20/211610utkjejktkjkssxjv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-211115.jpg</strong> (440.55 KB, 下载次数: 0)

下载附件

2024-1-20 21:16 上传

在PororoSV和FlintstonesSV上的多图像生成，每个示例包括四行，第一行是第一帧图像和所有相应的字幕说明，第二行是包含随后帧的基准答案图像；第三行是使用MMFS生成的结果；最后一行是没有使用MMFS生成的结果，当没有使用MMFS时，生成的多个图像在角色、背景、物体等方面缺乏内容一致性

<img src="https://img.saraba1st.com/forum/202401/20/211615wra5zmbfgm9z8cr3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240120-211133.jpg</strong> (527.45 KB, 下载次数: 0)

下载附件

2024-1-20 21:16 上传

在PororoSV和FlintstonesSV上的交错图像文本生成，每个示例包括三列，第一列是所有帧的基准答案图像和字幕说明；第二列是使用MMFS生成的结果；最后一列是没有使用MMFS生成的结果

在生成时只给定了第一帧的字幕说明和图像作为生成时的条件

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1205#       发表于 2024-1-21 04:43

RoleCraft-GLM

促进大型语言模型中的个性化角色扮演

github项目主页:https://github.com/tml2002/RoleCraft

RoleCraft-GLM，一个创新性框架，旨在通过大型语言模型(LLMs)提升个性化角色扮演能力，RoleCraft-GLM解决了对话型人工智能中缺乏个性化互动的关键问题，并通过详细而情感细腻的角色描绘提供了解决方案

本文贡献了一个独特的对话数据集，从传统的以知名角色为中心的角色数据集，转变为了多样化的非知名角色，从而提高了语言建模互动的真实度和复杂性

此外，本文方法还包括细致的角色开发(character development)，确保对话既真实又能在情感上产生共鸣，通过各种用例研究验证了RoleCraft-GLM的有效性，突显了其在不同场景中的多功能性和能力

本文框架在生成对话方面表现出色，能准确反映角色的个性特征和情感，从而提高用户参与度，在个性化人工智能互动方面迈出了重要一步，并通过更加细腻和情感丰富的对话，为更真实、沉浸式的人工智能辅助的角色扮演体验铺平了道路

<img src="https://img.saraba1st.com/forum/202401/21/044219em6cqb0iuemuclux.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240121-043621__01.jpg</strong> (210.16 KB, 下载次数: 0)

下载附件

2024-1-21 04:42 上传

RoleCraft-GLM框架概览图:
1.情感标注的对话数据集在创建反映特定情感特质的角色配置文件方面扮演着关键作用
2.基于上下文和已知角色特征生成的问答对，确保了对话与角色配置文件一致
3.使用通用和角色特定指令的混合方法训练GLM以适应各种对话场景

<img src="https://img.saraba1st.com/forum/202401/21/044224seaqd3yaen9cnpei.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240121-043648__01.jpg</strong> (479.08 KB, 下载次数: 0)

下载附件

2024-1-21 04:42 上传

生成详细角色描述的示例，利用角色描述模板和情感标注的对话数据集，可以根据提示生成详细的角色描述

<img src="https://img.saraba1st.com/forum/202401/21/044228dyfg5s9fkyazwifp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240121-043706__01.jpg</strong> (233.53 KB, 下载次数: 0)

下载附件

2024-1-21 04:42 上传

指令的动词-名词结构(Verb-noun structure)，内圈表示前20个动词，外圈列出直接的名词对象

<img src="https://img.saraba1st.com/forum/202401/21/044233xoyzwy3ofsrruywa.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240121-043706__02.jpg</strong> (48.93 KB, 下载次数: 0)

下载附件

2024-1-21 04:42 上传

对话中的情感数据分布

<img src="https://img.saraba1st.com/forum/202401/21/044242uh03a63wn7uat33r.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240121-043715__01.jpg</strong> (204.84 KB, 下载次数: 0)

下载附件

2024-1-21 04:42 上传

数据集的统计数据

<img src="https://img.saraba1st.com/forum/202401/21/044246nofe9lo4f7lxeejl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240121-043715__02.jpg</strong> (142.46 KB, 下载次数: 0)

下载附件

2024-1-21 04:42 上传

词云表示数据集中的中文角色的个性特征的可视化分布，越大的单词表示相关特质的频率越高

<img src="https://img.saraba1st.com/forum/202401/21/044251dxgko9d1e1yccefg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240121-043723__01.jpg</strong> (371.38 KB, 下载次数: 0)

下载附件

2024-1-21 04:42 上传

本文模型和基线模型对角色特定介绍生成的响应的示例

<img src="https://img.saraba1st.com/forum/202401/21/044255ssumwesfjdsx62j2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240121-043730__01.jpg</strong> (277.81 KB, 下载次数: 0)

下载附件

2024-1-21 04:42 上传

各种指标评估结果

<img src="https://img.saraba1st.com/forum/202401/21/044300r7skvk1b77y795kt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240121-043735__01.jpg</strong> (41.21 KB, 下载次数: 0)

下载附件

2024-1-21 04:43 上传

情感标注和未标注的数据的消融实验结果对比

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1206#       发表于 2024-1-22 01:34

GPT-SoVITS/Webui

强大的少样本语音转换与语音合成/Web用户界面

github项目主页:https://github.com/RVC-Boss/GPT-SoVITS

bilibili演示视频:https://www.bilibili.com/video/BV12g4y1m7Uw/

特点:
1.零样本 TTS:输入5秒语音样本并体验即时文本到语音转换

2.少样本 TTS:仅用1分钟的训练数据即可微调模型，改进语音相似度和真实感

3.跨语言支持:可以推理与训练数据集不同的语言，目前支持英语、日语和中文

4.WebUI工具:集成工具包括语音伴奏分离、自动训练集分割、中文ASR和文本标注，帮助初学者创建训练数据集和GPT/SoVITS模型

github项目说明截图:

<img src="https://img.saraba1st.com/forum/202401/22/013413qxro9p9ak5ht69pp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240122-012906.jpg</strong> (261.21 KB, 下载次数: 0)

下载附件

2024-1-22 01:34 上传

<img src="https://img.saraba1st.com/forum/202401/22/013413grkvqnrnw5qrrzv8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240122-012925.jpg</strong> (83.27 KB, 下载次数: 0)

下载附件

2024-1-22 01:34 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1207#       发表于 2024-1-22 22:29

LangBridge

不需要多语言监督(Multilingual Supervision)的多语言推理(Multilingual Reasoning)

github项目主页(待整理):https://github.com/kaistAI/LangBridge

LangBridge是一种零样本方法，用于在不需要多语言监督的情况下自适应多语言推理任务，LangBridge通过桥接两个专注于不同方面的模型来运作:
1.一个专注于理解多语言的模型(例如mT5编码器)
2.一个专注于推理的模型(例如Orca 2)

LangBridge通过在两个模型之间引入最少的可训练参数(minimal trainable parameters)来连接它们，尽管只使用英语数据进行训练，但LangBridge在数学推理、编码和逻辑推理等低资源语言(low-resource languages)的模型性能方面有相当显著的提升，分析表明，LangBridge的有效性源于多语言表征(multilingual representations)的语言无关特性(language-agnostic characteristics)

<img src="https://img.saraba1st.com/forum/202401/22/222746ofliatyms66ii45n.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240122-222435.jpg</strong> (111.24 KB, 下载次数: 0)

下载附件

2024-1-22 22:27 上传

MetaMath模型以及通过LANGBRIDGE(LB)对齐的mT5-XL编码器(2B)的MGSM准确率(%)

除了附加的平均准确率(AVG)外，还报告了由Shi等人(2023)对高资源语言(HRL/highresource languages和少数语言(URL/under-represented languages)进行分类的平均准确率

<img src="https://img.saraba1st.com/forum/202401/22/222753nui09zdg9ug2qgiu.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240122-222457__01.jpg</strong> (178.54 KB, 下载次数: 0)

下载附件

2024-1-22 22:27 上传

LANGBRIDGE的概览图

左:一个多语言编码器，具有附加的线性层，通过使用英语数据与语言模型对齐，保持语言模型冻结，而线性层可训练，当适配预训练语言模型时，多语言编码器是可训练的，而适配微调的语言模型时，多语言编码器是冻结的

右:在测试时，LANGBRIDGE模型可以有效地解决多语言推理任务

<img src="https://img.saraba1st.com/forum/202401/22/222850n66mtpyjuyjuuuza.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240122-222531__01.jpg</strong> (547.48 KB, 下载次数: 0)

下载附件

2024-1-22 22:28 上传

MGSM准确率(%)

除了附加的平均准确率(AVG)外，还报告了由Shi等人(2023)对高资源语言(HRL/highresource languages和少数语言(URL/under-represented languages)进行分类的平均准确率

包括使用Llama 2的语言分布作为参考，对于预训练的模型(顶部)，使用8-shot跨语言CoT推理示例进行提示，除了PaLM-540B，参考Shi等人(2023)报告的6-shot跨语言CoT性能

对于微调的模型(底部)，进行零样本评估，PP2和MM后缀分别代表在Proof-Pile-2和MetaMath上训练的模型，通过将LANGBRIDGE模型(LB)与它们的原始检查点进行了对比，用粗体显示了最佳性能

<img src="https://img.saraba1st.com/forum/202401/22/222859jrxo2pb1z2tvzzrj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240122-222541__01.jpg</strong> (186.68 KB, 下载次数: 0)

下载附件

2024-1-22 22:28 上传

HumanEval和HumanEval-MT上的Pass@1分数

使用贪婪解码对模型进行零样本代码补全评估，通过将LANGBRIDGE(LB)模型与它们的原始检查点进行了对比，用粗体显示最佳性能

<img src="https://img.saraba1st.com/forum/202401/22/222906y0vvyit442lvyz29.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240122-222623__01.jpg</strong> (100.58 KB, 下载次数: 0)

下载附件

2024-1-22 22:29 上传

BBH(英语)和BBH-BN(孟加拉语)的准确率(%)，报告所选的14个子任务平均准确率，通过将LANGBRIDGE(LB)模型与它们的原始检查点进行了对比，用粗体显示最佳性能

<img src="https://img.saraba1st.com/forum/202401/22/222920axv9g1xp3jbxgarx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240122-222631__01.jpg</strong> (160.1 KB, 下载次数: 0)

下载附件

2024-1-22 22:29 上传

使用FLORES获得的汇总表示的前两个主成分(principle components)，请注意，两个子图的尺度有所不同

<img src="https://img.saraba1st.com/forum/202401/22/222926zeuff7xxv1xvuxxb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240122-222639__01.jpg</strong> (392.4 KB, 下载次数: 0)

下载附件

2024-1-22 22:29 上传

Orca 2-LANGBRIDGE模型使用BBH-BN的SNARK子集作为提示的意外翻译(accidental translation)示例，为简洁起见，输入提示的部分和输出中的几个合理步骤被截断(对应翻译在蓝色括号内)

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1208#       发表于 2024-1-22 23:17

MixNet

有效且高效率的超高清低亮度图像增强方法

github项目主页:https://github.com/zzr-idam/MixNet

随着成像设备(imaging devices)的不断进步，超高清(UHD/Ultra-High-Definition)图像的普及度也在增加，尽管许多图像复原方法(image restoration methods)取得了令人满意的结果，但由于UHD图像固有的高计算复杂性，它们不能直接应用于计算资源有限的设备上的UHD图像

在本文中，专注于低亮度图像增强(LLIE/low-light image enhancement)任务，并提出了一种名为MixNet的新LLIE方法，专为UHD图像设计

为了捕捉特征的远程依赖关系而不引入过多的计算复杂性，提出了全局特征调制层(GFML/Global Feature Modulation Layer)，GFML通过对特征图进行排列，将不同视图的特征关联起来，实现了对远程依赖关系的高效建模，此外还设计了局部特征调制层(LFML/Local Feature Modulation Layer)和前馈层(FFL/Feed-forward Layer)，用于捕捉局部特征并将特征转化为紧凑的表征

通过这种方式，MixNet在模型参数少、计算复杂度低的情况下实现了有效的LLIE，在合成和真实数据集上进行的大量实验，综合结果表明本文提出的方法超过了当前的SOTA性能

<img src="https://img.saraba1st.com/forum/202401/22/231611um2e2ty24rb4m4y2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240122-230729__01.jpg</strong> (77.11 KB, 下载次数: 0)

下载附件

2024-1-22 23:16 上传

本文提出的MixNet与其他LLIE方法在UHD-LOL4K数据集上的模型复杂度和性能对比，由于大多数方法无法直接处理UHD图像，FLOPs的计算是基于1024×1024图像尺寸进行的(这些算法在单个GPU上能处理的最大分辨率)，本文的MixNet在模型复杂度和性能之间取得了更好的平衡

<img src="https://img.saraba1st.com/forum/202401/22/231616zzmbv3eknkmf8mfc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240122-230747__01.jpg</strong> (264.94 KB, 下载次数: 0)

下载附件

2024-1-22 23:16 上传

提出的MixNet的整体架构，MixNet首先使用下采样器(DownSampler)将输入的低亮度图像转换为特征空间，然后使用一系列的特征混合块(FMB/Feature Mixing Blocks)进行特征提取，最后使用上采样器(UpSampler)对这些提取的特征进行重建，FMB主要包含全局特征调制层(GFML)、局部特征调制层(LFML)和前馈层(FFL)

<img src="https://img.saraba1st.com/forum/202401/22/231621fzifzvxpqrr1e1fx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240122-230753__01.jpg</strong> (90.67 KB, 下载次数: 0)

下载附件

2024-1-22 23:16 上传

提出的整体架构中的(a)全局特征调制层，(b)局部特征调制层和(c)前馈层

<img src="https://img.saraba1st.com/forum/202401/22/231626s48u4xujri44v1aj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240122-230758__01.jpg</strong> (263.92 KB, 下载次数: 0)

下载附件

2024-1-22 23:16 上传

维度转换操作的可视化，通过使用简单的维度转换操作，MixNet能够以较少的参数捕捉特征的长程依赖

<img src="https://img.saraba1st.com/forum/202401/22/231632heee4q3ecof7cucn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240122-230807__01.jpg</strong> (387.24 KB, 下载次数: 0)

下载附件

2024-1-22 23:16 上传

视觉质量对比，最后一行显示了图像的色彩直方图(color histogram)，本文方法与GT图像的颜色最接近

<img src="https://img.saraba1st.com/forum/202401/22/231636gljt6zpozrllueu2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240122-230813__01.jpg</strong> (359.95 KB, 下载次数: 0)

下载附件

2024-1-22 23:16 上传

在UHD-LOL4K和UHD-LL数据集上的定量对比结果，最佳和次佳结果分别用粗体和下划线表示

<img src="https://img.saraba1st.com/forum/202401/22/231641c6g6tqatj2a8taza.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240122-230825__01.jpg</strong> (798.22 KB, 下载次数: 0)

下载附件

2024-1-22 23:16 上传

视觉质量对比，本文方法可以有效去除噪声并重建曝光良好的图像细节

<img src="https://img.saraba1st.com/forum/202401/22/231646ri520tg0s5augiau.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240122-230831__01.jpg</strong> (164.95 KB, 下载次数: 0)

下载附件

2024-1-22 23:16 上传

LOL数据集上定量结果对比，最佳和次佳结果分别用粗体和下划线表示

<img src="https://img.saraba1st.com/forum/202401/22/231650lcjnvcmmrwng5gmj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240122-230845__01.jpg</strong> (194.04 KB, 下载次数: 0)

下载附件

2024-1-22 23:16 上传

O-Haze数据集上定量结果对比，最佳和次佳结果分别用粗体和下划线表示

<img src="https://img.saraba1st.com/forum/202401/22/231654q9lchkc336s0jpgp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240122-230850__01.jpg</strong> (111.75 KB, 下载次数: 0)

下载附件

2024-1-22 23:16 上传

所提出的块(block)的消融实验，为了确保参数大小的一致性，通过逐步用参数相近的残差模块替换所提出的模块

<img src="https://img.saraba1st.com/forum/202401/22/231659blr5ttztww9tbror.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240122-230850__02.jpg</strong> (129.21 KB, 下载次数: 0)

下载附件

2024-1-22 23:16 上传

上采样器之前的特征图可视化，此处使用的图像是图6中显示的低亮度图像，本文方法重建了纹理更清晰的特征图

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1209#       发表于 2024-1-23 00:14

CivRealm

决策代理者(Decision-Making Agents)在文明中的学习和推理之旅

github项目主页:https://github.com/bigai-ai/civrealm

决策代理者的泛化包括两个基本要素:从过去的经验中学习和在新环境中进行推理，然而，在大多数交互环境中主要强调的是学习，通常以牺牲推理的复杂性为代价

在本文中，介绍了CivRealm，一个受到文明游戏(Civilization game)启发的环境，文明与人类历史和社会的深刻对齐需要复杂的学习，而其不断变化的情景则要求强大的推理能力来进行推广，特别是，CivRealm建立了一个不完全信息的非零和游戏，参与者数量不断变化，它提供了丰富的复杂特征，挑战代理者处理外交和谈判技巧能力的开放性随机环境

在CivRealm中，提供了两种典型的代理者类型接口:基于张量的代理者专注于学习，而基于语言的代理者则强调推理，为了促进进一步的研究，对这两种范式都提供了初步结果，经典的基于强化学习的代理者在小游戏中表现出了合理的性能，但是，无论是基于强化学习还是LLM的代理者，都很难在完整游戏中取得实质性的进展，总体而言，CivRealm是一个独特的学习和推理游戏，适合决策代理者挑战

<img src="https://img.saraba1st.com/forum/202401/23/001319yyryjyrg5p3xfhy5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-000920__01.jpg</strong> (514.01 KB, 下载次数: 0)

下载附件

2024-1-23 00:13 上传

CivRealm游戏玩法需要深入推理，涉及长期的战略规划和精细的战术控制，图中描述了一个类似于历史情景的假设情况，罗马人需要在对抗迦太基的同时保护西西里岛，并与衰落的埃及保持友好的外交关系，这个决策是在一个高度复杂的背景下做出的:玩家需要认真考虑在给定的地理和外交情况下的长期发展战略，如技术、军事和外交，他们还需要进行细致的控制行动，例如边境探索、船只建造和道路建设

<img src="https://img.saraba1st.com/forum/202401/23/001347rm2m15z8m2rm123r.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-000940__01.jpg</strong> (239.03 KB, 下载次数: 0)

下载附件

2024-1-23 00:13 上传

与现有环境的对比，CivRealm具有以下用于学习和推理的特点:
信息不完全(Imperfect info):完整状态只能部分观察到
随机性(Stochastic):动态环境是非确定性的
多目标(Multi-goal)游戏中有多个胜利条件
动态空间(Dynamic space):单个玩家的状态和行动空间在游戏中动态变化
多代理者(Multi-agent):游戏中有多个相互互动的玩家
正和(General-sum):这是一个混合动机游戏，合作与竞争共存
改变的玩家(Changing players):在一个游戏中玩家的数量可以增加或减少
通信(Comm):玩家可以在游戏中明确地进行通信
张量和语言(Tensor &amp; Lang):环境提供张量和语言API

<img src="https://img.saraba1st.com/forum/202401/23/001354ad8d84vx75rzmk1r.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-000949__01.jpg</strong> (530.61 KB, 下载次数: 0)

下载附件

2024-1-23 00:13 上传

随着游戏的展开，文明发展，潜在的状态和行动空间也变得非常庞大，这个图集中展示了8个时代中的4个，其中技术进步解锁了更多的建筑和单位，在游戏过程中，状态可以从10^15增长到10^650，行动空间可以从10^4扩展到10^166，图例只展示了一些示例元素:完整的游戏包括87种技术、68种建筑、52种单位、6种管理类型和5种外交状态，所有这些都受到使用的规则集的限制且可定制

<img src="https://img.saraba1st.com/forum/202401/23/001401npwou6oj7yms60w7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-001003__01.jpg</strong> (664.47 KB, 下载次数: 0)

下载附件

2024-1-23 00:14 上传

设计的不同类型的迷你游戏示例

<img src="https://img.saraba1st.com/forum/202401/23/001406ir3bk2es2srwfbke.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-001015__01.jpg</strong> (304.66 KB, 下载次数: 0)

下载附件

2024-1-23 00:14 上传

生成的迷你游戏多样且平衡
(a)地形和资源分布以及相应的联合食物/生产/贸易指标
(b)单位数量和强度:单位数量的玩家之间比率
(c)技术数量和价值:玩家之间的差异分布

<img src="https://img.saraba1st.com/forum/202401/23/001419yopeveyvx9tm9ntp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-001027__01.jpg</strong> (363.71 KB, 下载次数: 0)

下载附件

2024-1-23 00:14 上传

基于LLM的方法架构
左:BaseLang
右:Mastaba

<img src="https://img.saraba1st.com/forum/202401/23/001425wod0ax4y7xvk1dv1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-001040__01.jpg</strong> (264.97 KB, 下载次数: 0)

下载附件

2024-1-23 00:14 上传

在三个迷你任务上进行训练的RL方法的性能；不同的迷你任务表现出不同程度的随机性和复杂性，导致了不同的成功率，在“SettlerBuildCity”任务中，RL方法在困难级别上表现出了捷径学习(shortcut learning)效果

<img src="https://img.saraba1st.com/forum/202401/23/001430o761cb1n7c7nc0b6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-001045__01.jpg</strong> (201.21 KB, 下载次数: 0)

下载附件

2024-1-23 00:14 上传

RL方法在全游戏训练过程中的得分，CivRealm提供了不同的指标来衡量模型的性能，从不同的角度提供进一步的见解，这些指标也反映了环境的多目标性质

<img src="https://img.saraba1st.com/forum/202401/23/001436k9kyms4k5mjjjszj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-001108__01.jpg</strong> (263.52 KB, 下载次数: 0)

下载附件

2024-1-23 00:14 上传

文明的演化
上方:BaseLang
下方:Mastaba

从左到右，图中展示了文明进展到各个阶段

<img src="https://img.saraba1st.com/forum/202401/23/001441y17plpwpmdpzv7nd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-001113__01.jpg</strong> (201.45 KB, 下载次数: 0)

下载附件

2024-1-23 00:14 上传

基于LLM的代理根据游戏回合的指标统计数据，每个游戏统计50次

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1210#       发表于 2024-1-23 01:33

Mementos

使用图像序列作为多模态大语言模型推理的综合基准测试

github项目主页:https://github.com/umd-huang-lab/Mementos

多模态大语言模型(MLLMs)已经展现了熟练处理各种视觉语言任务的能力，然而，目前的MLLM基准主要被设计用于评估基于单张图像的静态信息推理能力，而现代的MLLM从图像序列中推断的能力，对于理解不断变化的世界至关重要，但研究较少

为了解决这个挑战，本文引入了Mementos，这是一个新的基准，旨在评估MLLM的序列图像推理能力。Mementos包含4761个不同长度的多样化图像序列，还采用了GPT-4辅助方法来评估MLLM的推理性能

通过对包括GPT-4V和Gemini在内的九个近期的MLLM，在Mementos上进行仔细评估，发现它们在准确描述给定图像序列的动态信息方面存在困难，经常在对象及其对应行为方面产生幻觉/错误表达

定量分析和案例研究确定了影响MLLM的序列图像推理的三个关键因素:对象和行为幻觉之间的相关性，共同行为的影响以及行为幻觉的复合影响

<img src="https://img.saraba1st.com/forum/202401/23/013202kcnnc7mnvmruwvw0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-012643__01.jpg</strong> (500.5 KB, 下载次数: 0)

下载附件

2024-1-23 01:32 上传

在Mementos上三个领域中GPT-4产生的幻觉示例，红框展示了GPT-4V基于给定提示生成的描述，蓝框内是人工标注的描述，黄色高亮部分是GPT-4V生成的幻觉内容，这说明即使是GPT-4V，在图像序列推理时也会出现严重的幻觉

<img src="https://img.saraba1st.com/forum/202401/23/013210suj3p0c31jppgpz0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-012704__01.jpg</strong> (52.64 KB, 下载次数: 0)

下载附件

2024-1-23 01:32 上传

Mementos中不同类别的图像序列数量

<img src="https://img.saraba1st.com/forum/202401/23/013215ezr3rhcm11l707zc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-012713__01.jpg</strong> (109.21 KB, 下载次数: 0)

下载附件

2024-1-23 01:32 上传

Mementos验证集中图像序列长度的分布

<img src="https://img.saraba1st.com/forum/202401/23/013219j1q7uqfug8jlu0ab.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-012713__02.jpg</strong> (85.81 KB, 下载次数: 0)

下载附件

2024-1-23 01:32 上传

Mementos验证集中片段长度的分布

<img src="https://img.saraba1st.com/forum/202401/23/013224jf3tf478zf7f185w.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-012724__01.jpg</strong> (111.86 KB, 下载次数: 0)

下载附件

2024-1-23 01:32 上传

GPT-4辅助评估过程，使用“O-”和“B-”分别表示对象和行为

<img src="https://img.saraba1st.com/forum/202401/23/013229f6ujopu2jff7fjue.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-012739__01.jpg</strong> (214.41 KB, 下载次数: 0)

下载附件

2024-1-23 01:32 上传

不同MLLM在Mementos上的六个指标对比

<img src="https://img.saraba1st.com/forum/202401/23/013233tj20njcwsqqw0v03.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-012803__01__01__01.jpg</strong> (390 KB, 下载次数: 0)

下载附件

2024-1-23 01:32 上传

在Mementos上对不同MLLM进行评估

<img src="https://img.saraba1st.com/forum/202401/23/013240bp97pxxux2dc89mx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-012817__01.jpg</strong> (341.28 KB, 下载次数: 0)

下载附件

2024-1-23 01:32 上传

日常生活领域失败推理案例的示例，失败原因是物体幻觉、物体幻觉和行为幻觉之间的关联以及共同发生的行为，在网球场的物体幻觉之后，LVLM随后表现出持有网球拍的行为幻觉(物体幻觉和行为幻觉之间的关联)，并且看起来在打网球(共同发生的行为)

<img src="https://img.saraba1st.com/forum/202401/23/013258oq7fhcwr5ioivfdv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-012826__01.jpg</strong> (367.7 KB, 下载次数: 0)

下载附件

2024-1-23 01:32 上传

Mementos上不同MLLM之间的行为幻觉和物体幻觉之间的相关系数

<img src="https://img.saraba1st.com/forum/202401/23/013302j8l5jlx3nv35w6a6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-012841__01.jpg</strong> (84.06 KB, 下载次数: 0)

下载附件

2024-1-23 01:33 上传

随着图像序列的片段长度增长，GPT-4V和LLaVA-1.5在日常生活领域中物体和行为召回的变化趋势

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1211#       发表于 2024-1-23 02:11

KCA

通过知识一致对齐减轻大型语言模型的幻觉

github项目主页:https://github.com/fanqiwan/KCA

尽管大型语言模型(LLM)在经过对齐后在各种任务上都表现超常，但它们仍然可能会产生与上下文或世界知识相矛盾的回复，这种现象被称为“幻觉”

在本文中，展示了通过减少训练数据中所包含的外部知识与预训练语料库中所继承的内在知识之间的不一致性，可以减轻幻觉在对齐后的出现

具体而言，引入了一种新颖的知识一致对齐(KCA/knowledge consistent alignment)方法，该方法涉及基于外部知识自动制定检查来评估LLM的理解能力，对于包含的知识不一致的数据，KCA采用了几种简单而高效的处理策略

通过使用不同基础架构和规模的LLM在六个基准测试中展示了所提出的KCA方法在减轻幻觉方面的卓越性能，此外，确认了知识不一致性与幻觉之间的相关性，表明了减少知识不一致性在减轻幻觉方面的有效性

<img src="https://img.saraba1st.com/forum/202401/23/021046iu55n6rlj55fk5f5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-020718__01.jpg</strong> (165.67 KB, 下载次数: 0)

下载附件

2024-1-23 02:10 上传

预训练语料库和对齐训练数据之间的不一致性，这使得语言模型倾向于在对齐后产生有说服力但幻觉的回复

<img src="https://img.saraba1st.com/forum/202401/23/021055k45z5e4ioz54igqe.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-020738__01.jpg</strong> (134.7 KB, 下载次数: 0)

下载附件

2024-1-23 02:10 上传

在各种基准测试中，经过指令调整的7B基础语言模型(Pythia，Llama-2和Mistral)在不同的知识不一致百分比下的幻觉率(y轴)

<img src="https://img.saraba1st.com/forum/202401/23/021100awvvm73c6rd6gt7w.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-020800__01.jpg</strong> (561.59 KB, 下载次数: 0)

下载附件

2024-1-23 02:11 上传

提出的KCA方法通过知识一致对齐来减轻幻觉，首先通过制定检查方法(左侧)检测知识不一致，然后使用开卷式、丢弃式和拒绝式调整(open-book, discarding, and refusal tuning)(右侧)处理包含不一致性的训练数据

<img src="https://img.saraba1st.com/forum/202401/23/021107r76kzlul5kbnt5kb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-020807__01.jpg</strong> (192.52 KB, 下载次数: 0)

下载附件

2024-1-23 02:11 上传

不同基础语言模型在不同训练和评估数据集上的一致子集Dc和不一致子集Di的百分比，对于7B规模的基础语言模型，Pythia在Di的百分比上高于Llama-2和Mistral，Llama-2 13B相比Llama-2 7B，Di百分比降低

<img src="https://img.saraba1st.com/forum/202401/23/021117juxaua9sikgeuuru.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-020818__01.jpg</strong> (496.93 KB, 下载次数: 0)

下载附件

2024-1-23 02:11 上传

使用GPT-4测量不同基础语言模型、调整方法和基准测试上的幻觉率以进行对比，更低的比率代表更好的性能，将包括开卷式调整、丢弃式调整和拒绝式调整在内的KCA方法与标准调整基线进行对比，请注意，对于拒绝式调整，只对非拒绝的回复进行评估

<img src="https://img.saraba1st.com/forum/202401/23/021122h9p9292p1tnpihsh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-020825__01.jpg</strong> (184.44 KB, 下载次数: 0)

下载附件

2024-1-23 02:11 上传

在拒绝式调整下，拒绝回复和非拒绝回复的指令的平均幻觉率，为了衡量拒绝回复的指令的幻觉率，使用标准调整基线在不同基础语言模型和基准测试上生成回复，具有拒绝式回复的指令显示出相比具有非拒绝回复的指令更高的幻觉率

<img src="https://img.saraba1st.com/forum/202401/23/021131h0z4d69qqddv2hwl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-020842__01.jpg</strong> (471.1 KB, 下载次数: 0)

下载附件

2024-1-23 02:11 上传

使用ROUGE-1、ROUGE-2和ROUGE-L对生成的输出和参考答案进行对比，将包括开卷式调整、丢弃式调整和拒绝式调整在内的KCA方法与标准调整基线进行对比，请注意，对于拒绝式调整，只对非拒绝的回复进行评估

<img src="https://img.saraba1st.com/forum/202401/23/021143utdlrzt3f8rdue99.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-020847__01.jpg</strong> (423.33 KB, 下载次数: 0)

下载附件

2024-1-23 02:11 上传

使用GPT-4测量的有帮助性分数，区间在1(最差)到10(最好)之间，对比了不同基础语言模型、调整方法和基准测试，将包括开卷式调整、丢弃式调整和拒绝式调整在内的KCA方法与标准调整基线进行对比

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1212#       发表于 2024-1-23 02:28

FuseLLM

大型语言模型的知识融合(Knowledge Fusion)

github项目地址:https://github.com/fanqiwan/FuseLLM

通过从头开始训练大型语言模型(LLM)，可以构建具有独特功能和优势的模型，但这会付出巨大的成本，且有可能导致冗余的能力，相反，一种高效且瞩目的方法是将现有的预训练LLM合并成一个更强大的模型

然而，由于这些LLM的架构不同，直接混合它们的权重是不可行的，在本文中，引入了LLM的知识融合概念，旨在将现有LLM的能力结合起来，并将其转移到单个LLM中，通过利用源LLM的生成分布，外化了它们的集体知识和独特优势，从而提升目标模型的能力，并超越任何单个的源LLM的能力

使用具有不同架构的三种流行LLM(Llama-2、MPT和OpenLLaMA)在各种基准和任务中验证了本文方法，研究结果表明，LLM的融合可以提高目标模型在推理、常识和代码生成等多个能力方面的性能

github项目页说明截图:

<img src="https://img.saraba1st.com/forum/202401/23/022821bw13bmxfxluyfh00.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-022719.jpg</strong> (239.78 KB, 下载次数: 0)

下载附件

2024-1-23 02:28 上传

<img src="https://img.saraba1st.com/forum/202401/23/022821vzxapzwapt3qxun1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-022741.jpg</strong> (670.6 KB, 下载次数: 0)

下载附件

2024-1-23 02:28 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1213#       发表于 2024-1-24 00:05

S-Seg

探索简单的开放词汇语义分割(Open-Vocabulary Semantic Segmentation)

github项目主页:https://github.com/zlai0/S-Seg

开放词汇的语义分割模型旨在从一组任意的开放词汇文本(a set of arbitrary open-vocabulary texts)中为图像中的每个像素精准地分配语义标签(semantic label)

为了学习这种像素级(pixel-level)的对齐，当前的方法通常依赖于以下组合:
(i)图像级(image-level)的视觉语言模型(例如CLIP)
(ii)人工标注的基准掩码答案
(iii)使用定制编码器进行分组

在本文中，引入了一种新颖的模型，S-Seg，可以在不依赖以上任何元素的情况下取得令人惊讶的强大性能，S-Seg利用伪掩码(pseudo-mask)和语言训练MaskFormer，并且可以从公开可用的图像文本数据集中进行简单训练

与先前的工作相反，本文模型直接训练像素级特征并与语言对齐，一旦训练完成，S-Seg可以很好的在多个测试数据集上泛化，而无需进行微调，此外，S-Seg在使用数据进行缩放以及与自训练相结合时，拥有可以持续改进的额外好处，可以相信，本文简单而有效的方法将为未来的研究提供一个坚实的基线

<img src="https://img.saraba1st.com/forum/202401/24/000336y27vxvwzza7cvhld.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-235614__01.jpg</strong> (53.98 KB, 下载次数: 0)

下载附件

2024-1-24 00:03 上传

对网络图像分割的S-Seg结果，目标是对所有物体进行分割，包括虚构角色(例如minions)

<img src="https://img.saraba1st.com/forum/202401/24/000343s6reu6ijgipvhkhr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-235614__02.jpg</strong> (76.2 KB, 下载次数: 0)

下载附件

2024-1-24 00:03 上传

S-Seg框架利用伪掩码和语言来训练MaskFormer，展示了本文方法直接训练像素级特征和语言对齐，也能产生优秀的结果

<img src="https://img.saraba1st.com/forum/202401/24/000350k78pyd8yc9c3fdgk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-235638__01.jpg</strong> (456.13 KB, 下载次数: 0)

下载附件

2024-1-24 00:03 上传

使用所有的数据集类别作为查询进行评估的S-Seg的定性结果，本文模型能够应对挑战性情况，例如重叠物体和小物体，还能够处理“stuff”类别，比如水和地板，此外，本文的S-Seg+模型能够纠正S-Seg方法中的小错误

最后，即使在COCO数据集中，本文模型仍能在预测中保持高准确率，即使该数据集包含更多的物体

<img src="https://img.saraba1st.com/forum/202401/24/000401k1v0csmcb6s77c2c.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-235651__01.jpg</strong> (178.05 KB, 下载次数: 0)

下载附件

2024-1-24 00:04 上传

使用图像文本对训练S-Seg的伪代码(Pseudocode)

<img src="https://img.saraba1st.com/forum/202401/24/000408a3qmhk9ktirjipsp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-235708__01.jpg</strong> (223.49 KB, 下载次数: 0)

下载附件

2024-1-24 00:04 上传

S-Seg的概览图，一个MaskFormer模型从图像输入中计算掩码和掩码特征，一个伪掩码生成器(pseudo-mask generator)产生用于监督掩码预测的分割图，而描述图像的文本通过语言模型编码并与MaskFormer一起训练，使用图像文本对比损失(image-text contrastive loss)来提供对掩码特征的监督

<img src="https://img.saraba1st.com/forum/202401/24/000419uxx22g3jk2cza3zx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-235725__01.jpg</strong> (67.2 KB, 下载次数: 0)

下载附件

2024-1-24 00:04 上传

在S-Seg上进行测试，在推理过程中，S-Seg通过利用文本中的候选类别(a list of candidate classes in text)生成的语言特征(language features)来推广到新的类别(new categories)

<img src="https://img.saraba1st.com/forum/202401/24/000426z3ibr8sgs5tygbr5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-235725__02.jpg</strong> (45.86 KB, 下载次数: 0)

下载附件

2024-1-24 00:04 上传

伪掩码生成器在训练过程中生成伪掩码来监督预测的掩码，该模块以图像作为输入，使用经过DINO预训练的ViT提取其特征，然后应用K-means聚类将像素分组成分割(segments)

<img src="https://img.saraba1st.com/forum/202401/24/000432yhs0kddhavi4z22z.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-235725__03.jpg</strong> (85.16 KB, 下载次数: 0)

下载附件

2024-1-24 00:04 上传

伪掩码生成器迅速实现了出色的预示(oracle)性能，使其成为理想的掩码监督，报告了在一个批次中的128个样本上的分期的运行时间，模拟训练时的场景

*以H/8 × W/8分辨率处理降采样的图像，以获得合理的运行时间

<img src="https://img.saraba1st.com/forum/202401/24/000438ja5zxaeruozug161.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-235734__01.jpg</strong> (151.1 KB, 下载次数: 0)

下载附件

2024-1-24 00:04 上传

伪掩码示例，伪掩码生成器能够生成高质量的人工掩码，当提供预示标签时，这些掩码与基准答案标注之间有很高的重叠度

<img src="https://img.saraba1st.com/forum/202401/24/000453gz9lsjri99i21tlr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-235756__01.jpg</strong> (491.73 KB, 下载次数: 0)

下载附件

2024-1-24 00:04 上传

与现有方法的定性对比，CLIP主要用于分类，在分割方面表现不佳，而MaskCLIP将CLIP用于分割，但会产生噪声预测，并且不能处理背景类别，GroupViT是一个强有力的竞争对手，但在挑战性的场景中会遇到困难

<img src="https://img.saraba1st.com/forum/202401/24/000458nnnn3r3sjlv333c6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-235801__01.jpg</strong> (59.95 KB, 下载次数: 0)

下载附件

2024-1-24 00:04 上传

用于开放词汇语义分割的简单基线，所有模型都在CC12M上进行过训练，数值越高效果越好，即使使用了本文的伪掩码和更多的训练数据，两个简单的基线也无法获得令人满意的结果

<img src="https://img.saraba1st.com/forum/202401/24/000503g7ics8riyatmzb9y.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-235813__01.jpg</strong> (231.92 KB, 下载次数: 0)

下载附件

2024-1-24 00:05 上传

开放词汇语义分割结果(评估中包括背景像素)，在Pascal VOC (P. VOC)，Pascal Context (P. Context)和COCO上进行评估，按照无标注掩码的开放词汇模型的标准评估协议进行评估

本文方法得到了第二好的平均表现，并且在所有数据集上都比GroupViT更好

†表示重新计算的结果，数值越高越好

<img src="https://img.saraba1st.com/forum/202401/24/000516o47f5o6gx551w5y4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-235819__01.jpg</strong> (280.58 KB, 下载次数: 0)

下载附件

2024-1-24 00:05 上传

开放词汇语义分割结果(评估中排除了背景像素)，按照使用标注掩码的开放词汇模型的标准协议进行评估，与之前的方法相比，S-Seg在此设置下实现了有竞争力的性能

†表示重新计算的结果，*COCO用于训练，数值越高越好

<img src="https://img.saraba1st.com/forum/202401/24/000523adpwijvww86xz7bj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-235838__01.jpg</strong> (193.73 KB, 下载次数: 0)

下载附件

2024-1-24 00:05 上传

自训练的改进，在图上展示了相对改进的平均值，观察到，在所有的训练和测试数据设置中，自训练始终显著提高了S-Seg的性能

<img src="https://img.saraba1st.com/forum/202401/24/000528vo55ap5qrzaijqiq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-235846__01.jpg</strong> (58.2 KB, 下载次数: 0)

下载附件

2024-1-24 00:05 上传

自训练效果可视化，自训练的S-Seg+模型展示了在S-Seg忽略的区域准确预测的能力，如彩色矩形所示

<img src="https://img.saraba1st.com/forum/202401/24/000535n3bovv73k3vovso3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-235846__02.jpg</strong> (123.66 KB, 下载次数: 0)

下载附件

2024-1-24 00:05 上传

扩大训练数据规模可以提高性能，无论是否进行自训练，使用不同规模的数据进行模型训练:CC12M(12M)、CC12M+CC3M(15M)和CC12M+CC3M+RedCaps(26M)，注意到，随着数据规模的增加，性能稳步提高

<img src="https://img.saraba1st.com/forum/202401/24/000542w66rrr6xwst6vyrr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240123-235854__01.jpg</strong> (237.08 KB, 下载次数: 0)

下载附件

2024-1-24 00:05 上传

网络图像的定性结果，右侧显示了查询类别名称

第一行:S-Seg能够分割动画场景中的虚构角色
第二行:虽然进行了泥浴，但仍然能轻松识别和分割老虎
第三行:S-Seg能够识别特定的地标

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1214#       发表于 2024-1-24 04:59

 本帖最后由 Machinery 于 2024-1-24 05:01 编辑 

mllm-nvar

多模态大型语言模型的非言语抽象推理(Nonverbal Abstract Reasoning)的奇怪案例

github项目主页:https://github.com/kahrabian/mllm-nvar

尽管大型语言模型(LLMs)仍然不断应用于新的领域并在新应用中发挥作用，但当前依然在经历新一代基础模型的不断涌入，即多模态大型语言模型(MLLMs)，这些模型整合了语言和视觉信息，为这两种模态的交错点上的更复杂的推理能力开辟了新的可能性

然而，尽管MLLMs非常具有前景，但目前对它们的推理能力的理解还很有限，在这项研究中，使用变种Raven的渐进矩阵式(Raven's Progressive Matrices)评估了开源和闭源MLLMs的非言语抽象推理能力

实验揭示了解决这类问题的困难，同时展现了开源和闭源模型之间的巨大差距，还揭示了个别视觉和文本模块的关键缺陷，使模型的性能受到限制，最后，为了提高MLLMs的性能，尝试了各种方法，如CoT提示等，在性能上取得了显著的提升

<img src="https://img.saraba1st.com/forum/202401/24/045828u8fjnljr8je7phlj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-045325__01.jpg</strong> (292.74 KB, 下载次数: 0)

下载附件

2024-1-24 04:58 上传

在IQ50数据集的示例上的模型对样本的预测结果，给定一个带有视觉难题(visual puzzle)的提示(顶部)，模型生成一个包含所选选项的推理响应

<img src="https://img.saraba1st.com/forum/202401/24/045833qffff55findllfox.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-045337__01.jpg</strong> (403.12 KB, 下载次数: 0)

下载附件

2024-1-24 04:58 上传

使用广泛的下一个Token得分方法在IQ50、RAVEN-S和Marvel数据集上的零样本准确率，对于每个数据集，MLLMs的最佳性能以粗体显示，第二好的性能以下划线显示

T→运行一周后超时
∗→使用半精度(例如bfloat16)运行以适应GPU显存
‡→性能优于随机基线

<img src="https://img.saraba1st.com/forum/202401/24/045841asla20t2kve1a2cd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-045403__01.jpg</strong> (377.89 KB, 下载次数: 0)

下载附件

2024-1-24 04:58 上传

使用广泛的下一个Token得分方法对相关参数数量进行零样本准确率对比，模型按照从最小到最大排序，同一族类的模型颜色相同，红色虚线表示随机基线

<img src="https://img.saraba1st.com/forum/202401/24/045848hkju766zwlllx7d3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-045416__01.jpg</strong> (105.02 KB, 下载次数: 0)

下载附件

2024-1-24 04:58 上传

使用一一对比(one by one)和广泛的下一个Token得分方法在IQ50数据集上的零样本准确率对比

带有†标记的结果来自于Zhao等人(2023)的研究，  取决于运行错误，无法复制它们(无论是Huggingface还是GitHub版本)，红色虚线表示随机基线

<img src="https://img.saraba1st.com/forum/202401/24/045859zfbn76oawfvyoy9o.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-045425__01.jpg</strong> (103.3 KB, 下载次数: 0)

下载附件

2024-1-24 04:58 上传

通过人工检查评估在IQ50上进行指令调整的模型的推理正确性表现，答案和推理分别用A和R表示，最佳性能以粗体显示，第二好的性能以下划线显示

<img src="https://img.saraba1st.com/forum/202401/24/045905yk0e4yk4sk49dukt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-045432__01.jpg</strong> (57.63 KB, 下载次数: 0)

下载附件

2024-1-24 04:59 上传

在IQ50上使用仅文本提示的零样本CoT准确率

<img src="https://img.saraba1st.com/forum/202401/24/045909o1nlyyb4fuy1ln0a.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-045445__01.jpg</strong> (146.59 KB, 下载次数: 0)

下载附件

2024-1-24 04:59 上传

在IQ50的子集上的视觉感知问题表现

<img src="https://img.saraba1st.com/forum/202401/24/045915jqkvt7jqtgxdq07z.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-045451__01.jpg</strong> (66.59 KB, 下载次数: 0)

下载附件

2024-1-24 04:59 上传

在IQ50上使用不同类型提醒(hints)的gpt-4v和gemini-pro-vision的引导提示表现

 Z-S → Zero-shot
Gen → General

Sam → Sample-specific
Cor → Corrective

<img src="https://img.saraba1st.com/forum/202401/24/045925v3gs1133554h54p5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-045507__01.jpg</strong> (215.16 KB, 下载次数: 0)

下载附件

2024-1-24 04:59 上传

在IQ50上的零样本和对称少样本准确率

在(a)分布内(In-Distribution)，演示取自IQ50，而在(b)超出分布(Out-of-Distribution)中，演示取自RAVEN-S，每个变体都使用不同的种子执行了五次，以减少随机抽样的影响，红色虚线表示随机基线

<img src="https://img.saraba1st.com/forum/202401/24/045936jp5fhvv5y305ydvv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-045515__01.jpg</strong> (48.2 KB, 下载次数: 0)

下载附件

2024-1-24 04:59 上传

在IQ50上的对称少样本CoT准确率

<img src="https://img.saraba1st.com/forum/202401/24/045940sf1b0iibvybafo2i.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-045520__01.jpg</strong> (45.99 KB, 下载次数: 0)

下载附件

2024-1-24 04:59 上传

在IQ50上的非对称少样本CoT准确率

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1215#       发表于 2024-1-24 05:55

CMMMU

中文大规模多学科多模态理解基准测试

项目主页:https://cmmmu-benchmark.github.io/

github项目仓库:https://github.com/CMMMU-Benchmark/CMMMU

排行榜:https://cmmmu-benchmark.github.io/#leaderboard

数据集:https://huggingface.co/datasets/m-a-p/CMMMU

随着大型多模态模型模型(LMM)能力的持续进步，评估LMM的性能成为一种日益增长的需求，此外，评估LMM在诸如中文等非英语环境中的高级知识和推理能力方面存在着很大的差距

本文介绍了CMMMU，一个全新的中文大规模多学科多模态理解基准测试，旨在评估LMM在中文环境中需要的大学级学科知识和深思熟虑推理方面的能力，CMMMU受到MMMU的启发，并严格遵循其标注和分析模式

CMMMU包含从大学考试、测验和教科书中手动收集的1.2万个多模态问题，涵盖六个核心学科：艺术与设计、商业、科学、健康与医学、人文社科、技术与工程，与其伙伴MMMU相同，这些问题涵盖30个学科，包括39种高度异构的图像类型，如图表、图示、地图、表格、乐谱和化学结构

CMMMU关注的是在中文环境中具有特定领域知识的复杂感知和推理能力，评估了11个开源LMM和一个专有的GPT-4V(ision)，即使是GPT-4V，准确率也只有42%，这表明还有很大的改进空间

CMMMU将推动社区构建面向专家人工智能的下一代LMM，并通过提供多样的语言环境促进LMM的广泛使用

<img src="https://img.saraba1st.com/forum/202401/24/055454i00u0naiqff0blgd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-055155.jpg</strong> (128.31 KB, 下载次数: 0)

下载附件

2024-1-24 05:54 上传

CMMMU中的学科

<img src="https://img.saraba1st.com/forum/202401/24/055500s88fiuah8m2ay2on.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-055224__01.jpg</strong> (488.13 KB, 下载次数: 0)

下载附件

2024-1-24 05:55 上传

从每个学科中抽样的CMMMU示例，这些图片包括乐谱、表格、化学结构、曲线、电路图和其他类型的图片，高难度的问题需要专家级的知识来理解和推理

<img src="https://img.saraba1st.com/forum/202401/24/055505ncrv5jvzrprewz8j.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-055229__01.jpg</strong> (564.67 KB, 下载次数: 0)

下载附件

2024-1-24 05:55 上传

CMMMU中6个学科和30个主题的比例，30个主题中的多模态样本均均匀地涵盖了相关的专家级领域知识

<img src="https://img.saraba1st.com/forum/202401/24/055509kxxllywn5sl45ld1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-055302.jpg</strong> (172.01 KB, 下载次数: 0)

下载附件

2024-1-24 05:55 上传

与其他多模态基准测试的对比

<img src="https://img.saraba1st.com/forum/202401/24/055513g9qfqq0gq99fqk88.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-055314.jpg</strong> (282.29 KB, 下载次数: 0)

下载附件

2024-1-24 05:55 上传

CMMMU的统计数据

<img src="https://img.saraba1st.com/forum/202401/24/055517bz5j34233bufene6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-055334.jpg</strong> (186.44 KB, 下载次数: 0)

下载附件

2024-1-24 05:55 上传

图像类型及其对应数量

<img src="https://img.saraba1st.com/forum/202401/24/055521vnz40z4v7mhq2mov.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-055350.jpg</strong> (222.6 KB, 下载次数: 0)

下载附件

2024-1-24 05:55 上传

开源和闭源模型在CMMMU验证和测试集上的整体结果，粗体结果表示所有模型中的最佳结果，蓝色结果表示开源模型中的最佳结果

<img src="https://img.saraba1st.com/forum/202401/24/055526vp8hpuo20uk0uu7y.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-055359.jpg</strong> (75.38 KB, 下载次数: 0)

下载附件

2024-1-24 05:55 上传

按问题类型分解的结果

<img src="https://img.saraba1st.com/forum/202401/24/055530kiav9a6br91im60a.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-055411.jpg</strong> (101.67 KB, 下载次数: 0)

下载附件

2024-1-24 05:55 上传

按问题难度级别分解的结果，粗体结果表示所有模型中的最佳结果，蓝色结果表示开源模型中的最佳结果

<img src="https://img.saraba1st.com/forum/202401/24/055536rz47348yflku22zm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-055425.jpg</strong> (61.67 KB, 下载次数: 0)

下载附件

2024-1-24 05:55 上传

GPT-4V的错误响应的类型分布

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1216#       发表于 2024-1-24 06:46

RPG-DiffusionMaster

掌控文本到图像扩散:使用多模态LLM进行重述、规划和生成(Recaptioning, Planning, and Generating)

github项目主页:https://github.com/YangLing0818/RPG-DiffusionMaster

扩散模型在文本到图像生成和编辑方面表现出色，然而，现有方法经常在处理涉及多个对象、多个属性和关系的复杂文本提示时面临挑战

在本文中，提出了一种全新的无需训练的文本到图像生成/编辑框架，名为Recaption，Plan and Generate(RPG)，利用多模态LLM的强大思维链推理能力来增强文本到图像扩散模型的组合性

本文方法将MLLM作为全局规划器，将生成复杂图像的过程分解为子区域内的多个更简单的生成任务，提出了区域互补扩散(complementary regional diffusion)，以实现区域感知的组合式生成，此外，通过以闭环的方式将文本引导的图像生成和编辑集成到提出的RPG中，增强了泛化能力

大量实验证明了RPG在多类别对象组合和文本图像语义对齐方面优于SOTA文本到图像扩散模型，包括DALL-E 3和SDXL，值得注意的是，RPG框架与各种MLLM架构(如MiniGPT-4)和扩散骨干模型(如ControlNet)具有广泛的兼容性

<img src="https://img.saraba1st.com/forum/202401/24/064500pogdcscgl9c5y9y9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-063747__01.jpg</strong> (124.65 KB, 下载次数: 0)

下载附件

2024-1-24 06:45 上传

(a)文本条件扩散模型、(b)布局/基于注意力的扩散模型、(c) LLM基准扩散模型和(d)RPG之间的架构对比

<img src="https://img.saraba1st.com/forum/202401/24/064505h7i979gilnbzgdl3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-063800__01.jpg</strong> (765.1 KB, 下载次数: 0)

下载附件

2024-1-24 06:45 上传

与SDXL和DALL-E 3相比，本文提出的RPG在表达生成图像中复杂和组合的文本提示方面具有更强的能力(彩色文本表示关键部分)

<img src="https://img.saraba1st.com/forum/202401/24/064511fv2mv7vq3ddidlro.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-063817__01.jpg</strong> (475.25 KB, 下载次数: 0)

下载附件

2024-1-24 06:45 上传

RPG框架可以通过利用ControlNet来扩展文本到图像生成的更多条件(例如姿态、深度和边缘)，与原始的ControlNet相比，RPG通过将"用户输入"分解为基本提示和子提示的组合，显著改善了其提示理解，并通过执行区域感知的扩散生成进一步增强了生成图像的组合语义对齐

<img src="https://img.saraba1st.com/forum/202401/24/064520bigq5h5gim5lcnk5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-063840__01.jpg</strong> (181.75 KB, 下载次数: 0)

下载附件

2024-1-24 06:45 上传

RPG框架用于文本到图像生成的概览图

<img src="https://img.saraba1st.com/forum/202401/24/064524v5g2pxpgjhgxzp2k.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-063854__01.jpg</strong> (110.83 KB, 下载次数: 0)

下载附件

2024-1-24 06:45 上传

区域划分的示例说明

<img src="https://img.saraba1st.com/forum/202401/24/064530rackigcu48uccaml.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-063905__01.jpg</strong> (471.97 KB, 下载次数: 0)

下载附件

2024-1-24 06:45 上传

区域互补扩散中的每个采样步骤的演示

<img src="https://img.saraba1st.com/forum/202401/24/064534qokjshj6xwcaoktt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-063918__01.jpg</strong> (473 KB, 下载次数: 0)

下载附件

2024-1-24 06:45 上传

RPG以闭环的方式整合了文本引导的图像生成和编辑

<img src="https://img.saraba1st.com/forum/202401/24/064540gbvz9xo66svz9eaf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-063929__01.jpg</strong> (761.54 KB, 下载次数: 0)

下载附件

2024-1-24 06:45 上传

RPG与SOTA文本到图像模型SDXL和DALL-E 3以及LLM基准扩散模型LMD+之间的定性对比

<img src="https://img.saraba1st.com/forum/202401/24/064545p1bp9z4u9x1xhqup.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-063935__01__01.jpg</strong> (288.03 KB, 下载次数: 0)

下载附件

2024-1-24 06:45 上传

在T2I-CompBench上的评估结果，RPG在属性绑定、对象关系和复杂组合方面始终表现出最佳性能，用蓝色表示最佳得分，绿色表示次佳得分，基线数据引用自Chen等人(2023a)

<img src="https://img.saraba1st.com/forum/202401/24/064550h8gn4ad2ifv22aya.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-063951__01.jpg</strong> (649.77 KB, 下载次数: 0)

下载附件

2024-1-24 06:45 上传

分层区域扩散的演示，具有更多层次的扩散可以产生更令人满意的结果

<img src="https://img.saraba1st.com/forum/202401/24/064554i1jf0jj2mjm1ay12.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-064000__01.jpg</strong> (797.64 KB, 下载次数: 0)

下载附件

2024-1-24 06:45 上传

将RPG推广到不同的扩散骨干网络，包括稳定扩散v2.1和最新的SOTA扩散模型ConPreDiff

<img src="https://img.saraba1st.com/forum/202401/24/064558innzoss1r1s4ssgn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-064008__01.jpg</strong> (453.63 KB, 下载次数: 0)

下载附件

2024-1-24 06:45 上传

在文本引导的图像编辑方面进行的定性对比，本文方法的表现优于以前的各种方法，包括Prompt2Prompt、InstructPix2Pix和MasaCtrl等

<img src="https://img.saraba1st.com/forum/202401/24/064603hxpnnr6pksyxtp9k.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-064023__01.jpg</strong> (534.23 KB, 下载次数: 0)

下载附件

2024-1-24 06:46 上传

使用RPG框架进行多轮文本引导的图像编辑

<img src="https://img.saraba1st.com/forum/202401/24/064608a3f9fhsmfsz5ms95.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-064029__01.jpg</strong> (783.07 KB, 下载次数: 0)

下载附件

2024-1-24 06:46 上传

RPG中关于重述的消融实验

<img src="https://img.saraba1st.com/forum/202401/24/064612h3o11w1goo1devoz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-064040__01.jpg</strong> (475.79 KB, 下载次数: 0)

下载附件

2024-1-24 06:46 上传

RPG中CoT规划的消融实验

<img src="https://img.saraba1st.com/forum/202401/24/064616xqudvqn99cddr9rq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240124-064049__01.jpg</strong> (320.72 KB, 下载次数: 0)

下载附件

2024-1-24 06:46 上传

区域互补扩散中基本提示的消融实验

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1217#       发表于 2024-1-25 04:15

Vary-toy

小型语言模型结合强化视觉词汇(Reinforced Vision Vocabulary)

项目主页:https://varytoy.github.io/

github项目代码仓库:https://github.com/Ucas-HaoranWei/Vary-toy

演示demo:https://vary.xiaomy.net/

当前时代，在AI社区中使用大规模视觉语言模型(LVLMs)已经成为一种潮流，然而流行的LVLMs通常拥有相对较多的参数(超过70亿)，这使得在消费级GPU上进行训练和部署变得困难，并让许多资源有限的研究人员望而却步，想象一下，如果能在唯一拥有的游戏卡(个人用户)GTX1080ti上体验当前LVLMs的所有功能是多么酷！

因此，在这份报告中介绍了Vary-toy，它是一个小型的Vary模型，使用Qwen-1.8B作为基础的“大型”语言模型，在Vary-toy中，引入了一个改进的视觉词汇表，使模型不仅具备Vary的所有特性，还能够具备更多的通用性

具体而言，在生成视觉词汇表的过程中，通过使用目标检测驱动的正样本数据(positive sample)替换了自然图像的负样本(negative samples of natural images)，更充分地利用了词汇网络的容量，并使其能够高效地编码与自然对象相对应的视觉信息

在实验中，Vary-toy在DocVQA上可以达到65.6%的ANLS，ChartQA准确率为59.1%，RefCOCO准确率为88.1%，MMVet准确率为29%

<img src="https://img.saraba1st.com/forum/202401/25/041505ac2dqd2szploebxs.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-041146__01.jpg</strong> (524.78 KB, 下载次数: 0)

下载附件

2024-1-25 04:15 上传

Vary-toy的特点，基于一个18亿参数的语言模型，Vary-toy可以实现原生Vary-base的所有功能，包括文档OCR、图像字幕说明、VQA、一般对话等等，此外，还为Vary-toy引入了自然物体(位置)感知能力，最重要的是，只需要一块单独的GTX1080ti GPU，您就可以体验到上述所有功能

<img src="https://img.saraba1st.com/forum/202401/25/041514y0xe4knpppbay4o9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-041157__01.jpg</strong> (296.69 KB, 下载次数: 0)

下载附件

2024-1-25 04:15 上传

Vary-toy的架构，通过利用Vary-tiny+工作流程生成Vary-toy的新视觉词汇表，这种视觉词汇表可以有效地将密集文本和自然物体位置信息编码成Token，基于改进后的词汇表，Vary-toy不仅具备了之前所有的功能(文档OCR)，还能很好地处理对象检测任务

<img src="https://img.saraba1st.com/forum/202401/25/041519pmlmhbbrtmmmtrcc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-041216__01.jpg</strong> (851.62 KB, 下载次数: 0)

下载附件

2024-1-25 04:15 上传

Vary-tiny+使用的图像文本对可视化，对于PDF图像文本对，只有一个提示，而对于对象检测任务，使用了图中右半部分显示的两种类型的提示，因为一些图像可能会有太多对象，以至于超过OPT125M的最大Token长度(4096)

<img src="https://img.saraba1st.com/forum/202401/25/041524w0k2bqufrz2q2xsn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-041225__01.jpg</strong> (357.67 KB, 下载次数: 0)

下载附件

2024-1-25 04:15 上传

多任务训练数据，在预训练阶段引入了5种类型的数据，包括弱监督数据对、PDF图像文本数据对、检测数据、纯文本自回归数据和VQA数据，所有数据标注都被重新组织成对话格式

<img src="https://img.saraba1st.com/forum/202401/25/041529raamhvnhxjn0jjnj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-041232__01.jpg</strong> (149.36 KB, 下载次数: 0)

下载附件

2024-1-25 04:15 上传

在DocVQA和ChartQA上与流行方法的性能对比，Vary-toy在DocVQA上可以达到65.6%的ANLS，与7B的Qwen-VL-chat相当，并且在ChartQA上可以达到59.1%的准确率，高于7B规模的mPLUG-DocOwl

<img src="https://img.saraba1st.com/forum/202401/25/041533djpoqzb9bymbbozf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-041238__01.jpg</strong> (202.14 KB, 下载次数: 0)

下载附件

2024-1-25 04:15 上传

在RefCOCO上与流行方法的对比，由于新视觉词汇表的帮助，Vary-toy在RefCOCO val上可以达到88.1%的准确率，与7B的Qwen-VL-chat相当

<img src="https://img.saraba1st.com/forum/202401/25/041538chbaassaej0shszs.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-041242__01.jpg</strong> (190.67 KB, 下载次数: 0)

下载附件

2024-1-25 04:15 上传

在MMVet上与流行的LVLM方法对比，只需要一个18亿参数的语言模型，Vary-toy就能够获得29.0%的准确率

Rec：识别；Know：知识；Gen：语言生成；Spat：空间意识

<img src="https://img.saraba1st.com/forum/202401/25/041543ay7hyj9yymg8cstl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-041256__01.jpg</strong> (543.78 KB, 下载次数: 0)

下载附件

2024-1-25 04:15 上传

本文模型在四个常用领域的高质量可视化结果，可以看到，Vary-toy具有令人满意的通用能力，并且具备强大的文本和物体感知能力

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1218#       发表于 2024-1-25 04:56

 本帖最后由 Machinery 于 2024-1-25 05:00 编辑 

Ditto

大语言模型是所有角色的叠加:通过自对齐(Self-Alignment)实现任意角色扮演(Arbitrary Role-play)

github项目仓库:https://github.com/OFA-Sys/Ditto

社区对于开源大型语言模型(LLM)进行角色扮演能力增强方面付出了大量努力，这些模型试图通过模仿对应的专有模型进行增强，然而，本文认为LLM原生具有角色扮演能力，这是由于其广阔训练语料库中已经蕴含了角色知识和广泛的潜在对话能力

因此，在这项研究中引入了Ditto，一种用于角色扮演的自对齐方法，Ditto充分利用了角色知识，鼓励一个遵循指令的LLM模拟角色扮演对话，作为阅读理解的一种变体

该方法创建了一个包含4000个角色的角色扮演训练集，相对于当前可用数据集的角色，数量增加了十倍，随后使用这个自动生成的数据集对LLM进行微调，以增强其角色扮演能力

在评估精心构建且可复现的角色扮演基准和MT-Bench的角色扮演子集时，Ditto在各种参数规模下始终维持了一致的角色身份，并在多轮角色扮演对话中提供了准确的角色特定知识，值得注意的是，它超越了所有开源角色扮演基线，展现了可与高级专有聊天机器人相媲美的性能水平

此外，还展现了在角色扮演领域的首个全面的交叉监督对齐实验(cross-supervision alignment experiment)，揭示了LLM的内在能力限制了角色扮演中的知识，与此同时，角色扮演风格可以在较小模型的指导下轻松获得

<img src="https://img.saraba1st.com/forum/202401/25/045516zvunj7uueiobzcf6.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-045218.jpg</strong> (120.01 KB, 下载次数: 0)

下载附件

2024-1-25 04:55 上传

DITTO通过自对齐提升了LLMs的角色扮演能力，在各种角色文档和对话中进行了预训练

<img src="https://img.saraba1st.com/forum/202401/25/045521zu5vvelyfeu8pn7n.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-045235__01.jpg</strong> (433.04 KB, 下载次数: 0)

下载附件

2024-1-25 04:55 上传

DITTO示意图，DITTO由三阶段组成以进行角色扮演的自对齐

首先，DITTO从知识库中收集角色文档，如上部分所示，然后使用现成的聊天机器人生成角色特定和对比性的问题，接着通过知识增强的自回应(knowledge-augmented self-response)构建角色扮演监督数据集(对话模拟)，最后，DITTO在监督模型上微调数据集，增强角色扮演能力

<img src="https://img.saraba1st.com/forum/202401/25/045533xywhwf7wo47foow0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-045305__01.jpg</strong> (586.82 KB, 下载次数: 0)

下载附件

2024-1-25 04:55 上传

LLM角色扮演的客观评估，提出了三个度量标准

<img src="https://img.saraba1st.com/forum/202401/25/045537b0gpv9fgfdq29911.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-045325.jpg</strong> (64.85 KB, 下载次数: 0)

下载附件

2024-1-25 04:55 上传

数据集统计，将WIKIROLE与现有的开源角色扮演数据集进行了对比，WIKIROLE训练集中的查询由种子LLM生成，而测试集由GPT-4生成

<img src="https://img.saraba1st.com/forum/202401/25/045541qcczlkd8dzl1kixz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-045342.jpg</strong> (279 KB, 下载次数: 0)

下载附件

2024-1-25 04:55 上传

DITTO的主要结果

Cons.、Know.和Rej.分别代表一致的角色身份、准确的角色相关知识和未知问题拒绝，“En”代表英文，“Zh”代表中文，“All”列显示双语测试样本的聚合得分

报告了一致性和拒绝评估的准确率，以及知识的1-10分，较深的背景颜色表示更好的性能，封闭源LLMs的参数数量未知，因此省略

<img src="https://img.saraba1st.com/forum/202401/25/045548mae83aaaswe44e3e.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-045358.jpg</strong> (71.75 KB, 下载次数: 0)

下载附件

2024-1-25 04:55 上传

查询模拟质量的人工标注

<img src="https://img.saraba1st.com/forum/202401/25/045554g0tde7jwedjj3jzg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-045417__01.jpg</strong> (200.23 KB, 下载次数: 0)

下载附件

2024-1-25 04:55 上传

不同监督和种子LLMs之间的泛化分析，监督性能表示在DITTO模拟配方下进行角色扮演的性能，包括知识增强，模仿性能是指种子LLM在某些监督LLM的模拟上进行微调时的性能

<img src="https://img.saraba1st.com/forum/202401/25/045604i5r4ru365pktpkcr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-045440.jpg</strong> (48.32 KB, 下载次数: 0)

下载附件

2024-1-25 04:56 上传

对话模拟中知识注入的有效性，报告了Qwen-1.8B-Chat在测试集上具有和不具有角色知识注入的对话模拟性能

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1219#       发表于 2024-1-25 05:12

Orion-14B

开源多语言大型语言模型

github项目主页:https://github.com/OrionStarAI/Orion

技术报告:https://arxiv.org/abs/2401.12246

Orion-14B-Base是一个具有140亿参数的多语种大模型，该模型在一个包含2.5万亿token的多样化数据集上进行了训练，涵盖了中文、英语、日语、韩语等多种语言，在多语言环境下的一系列任务中展现出卓越的性能，在主流的公开基准评测中，Orion-14B系列模型表现优异，多项指标显著超越同等参数基本的其他模型，具体技术细节请参考技术报告

github项目页说明截图:

<img src="https://img.saraba1st.com/forum/202401/25/051213ymbfrnmb8xznbnql.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-050942.jpg</strong> (339.92 KB, 下载次数: 0)

下载附件

2024-1-25 05:12 上传

<img src="https://img.saraba1st.com/forum/202401/25/051213t0uu00brpm0rp3p3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-051007.jpg</strong> (313.92 KB, 下载次数: 0)

下载附件

2024-1-25 05:12 上传

<img src="https://img.saraba1st.com/forum/202401/25/051213epnp2vp9rjnkznpu.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-051020.jpg</strong> (250.9 KB, 下载次数: 0)

下载附件

2024-1-25 05:12 上传

<img src="https://img.saraba1st.com/forum/202401/25/051213sus4imcu71c514zc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-051051.jpg</strong> (139.29 KB, 下载次数: 0)

下载附件

2024-1-25 05:12 上传

<img src="https://img.saraba1st.com/forum/202401/25/051213atvt8s00uj77b8f7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-051111.jpg</strong> (411.59 KB, 下载次数: 0)

下载附件

2024-1-25 05:12 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1220#       发表于 2024-1-25 06:02

Yi-VL 6B/34B

Yi Vision Language(Yi-VL)多模态语言大模型

Yi-VL项目主页:https://github.com/01-ai/Yi/tree/main/VL

Yi-VL 6B模型权重:https://huggingface.co/01-ai/Yi-VL-6B

Yi-VL 34B模型权重https://huggingface.co/01-ai/Yi-VL-34B

机器之心相关介绍:https://www.jiqizhixin.com/articles/2024-01-22-10

量子位相关介绍:https://www.qbitai.com/2024/01/115765.html

构架信息

<img src="https://img.saraba1st.com/forum/202401/25/060212j2qs7d372smfds7c.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-060053.jpg</strong> (94.76 KB, 下载次数: 0)

下载附件

2024-1-25 06:02 上传

相关英文与中文基准测试结果

<img src="https://img.saraba1st.com/forum/202401/25/060230oq6rxt7u4f1ftxrq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-060107.jpg</strong> (107.65 KB, 下载次数: 0)

下载附件

2024-1-25 06:02 上传

<img src="https://img.saraba1st.com/forum/202401/25/060230rz1gbzrhogbp0rzb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-060115.jpg</strong> (139.07 KB, 下载次数: 0)

下载附件

2024-1-25 06:02 上传

实际用例

<img src="https://img.saraba1st.com/forum/202401/25/060243pzki6qtnikzy6546.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240125-060134.jpg</strong> (396.4 KB, 下载次数: 0)

下载附件

2024-1-25 06:02 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1221#       发表于 2024-1-26 10:23

Say-I-Dont-Know

人工智能助理能否了解他们自身不知道什么

github项目仓库:https://github.com/OpenMOSS/Say-I-Dont-Know

最近，基于大型语言模型(LLMs)的AI助手在许多任务中展现出惊人的性能，比如对话、解决数学问题、编写代码与使用工具，虽然LLMs具有丰富的世界知识，但在面对一些知识密集型任务(如开放域问答)时，它们仍然会出现事实错误，这些不真实的回应可能会在实际应用中带来重大风险

因此，可以认为AI助手拒绝回答它不知道的问题是减少幻觉和保持助手真实性的关键方法，在本文中提出了一个问题:“AI助手能否知道自己不知道什么，并用自然语言表达出来？”

为了回答这个问题，针对一个助手构建了一个特定于模型的“我不知道”(Idk)数据集，其中包含它所知道和不知道的问题，基于现有的开放域问答数据集，然后将助手与相应的Idk数据集进行对齐，观察在对齐后它是否能够拒绝回答自己不知道的问题

实验结果显示，在与Idk数据集对齐后，助手可以拒绝回答大多数未知问题，而对于它们尝试回答的问题，准确率显著提高

<img src="https://img.saraba1st.com/forum/202401/26/102247lomoymyznoxqxhmo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-102011.jpg</strong> (103.89 KB, 下载次数: 0)

下载附件

2024-1-26 10:22 上传

AI助手的知识象限图

“Unknowns”表示AI实际上不知道的内容
“Knowns”表示AI实际上知道的内容
“Known”表示AI认为自己知道的内容
“Unknown”表示AI认为自己不知道的内容

<img src="https://img.saraba1st.com/forum/202401/26/102253mbfucc6trivr9uuf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-102040.jpg</strong> (79.63 KB, 下载次数: 0)

下载附件

2024-1-26 10:22 上传

基于Idk数据集的AI助手的知识象限图(Ik阈值=1.0)

IK-IK表示AI正确回答了问题
IDK-IK表示AI知道答案但拒绝回答问题
IDK-IDK表示AI错误回答了问题
IK-IDK表示AI不知道答案并拒绝回答问题

w/Idk-Prompting:使用提示可以将某些IDK-IDK问题转化为IK-IDK问题
w/Idk-SFT:Idk-SFT允许模型拒绝回答更多它不知道的问题，但这也往往会使模型更加保守，导致错误地拒绝回答一些实际上它知道的问题
w/Idk-DPO:使用偏好感知优化(如DPO)可以减轻模型的过度保守，并减少IDK-IK问题的数量

<img src="https://img.saraba1st.com/forum/202401/26/102258nkmawfvg67a2wmf8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-102101.jpg</strong> (162.48 KB, 下载次数: 0)

下载附件

2024-1-26 10:22 上传

上方:Idk数据集的构建过程
下方:偏好对构建过程，绿色回答表示正确答案，红色回答表示错误答案，“I don’t know”表示拒绝回答的模板

<img src="https://img.saraba1st.com/forum/202401/26/102305zyxfg0z7j70yx7qq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-102116.jpg</strong> (111.64 KB, 下载次数: 0)

下载附件

2024-1-26 10:23 上传

基于TriviaQA和分布外(OOD)测试集构建的Idk数据集的测试集整体结果

<img src="https://img.saraba1st.com/forum/202401/26/102310oqe9010mo0ax1qkf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-102137.jpg</strong> (96.25 KB, 下载次数: 0)

下载附件

2024-1-26 10:23 上传

在不同规模的模型上的Idk-SFT实验结果

<img src="https://img.saraba1st.com/forum/202401/26/102316bkhhfwmzt3qc24q4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-102210.jpg</strong> (86.73 KB, 下载次数: 0)

下载附件

2024-1-26 10:23 上传

左侧:根据不同Ik阈值构建的Idk数据集中Ik和Idk问题的比例变化
右侧:在不同Idk数据集上进行Idk-SFT后，IK-IK比率、IK-IDK比率和TRUTHFUL比率的变化

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1222#       发表于 2024-1-26 21:18

 本帖最后由 Machinery 于 2024-1-26 21:20 编辑 

MaLA-500

大型语言模型的大规模语言适配

hugface权重下载:https://huggingface.co/MaLA-LM/mala-500

大型语言模型在自然语言处理方面取得了领先地位，然而，它们主要被设计用于英语或一组有限的语言，这导致了对于资源稀缺的语言而言，它们的效果存在较大的差距

为了弥补这一差距，本文推出了MaLA-500，一个新颖的大型语言模型，旨在覆盖广泛的534种语言，为了训练MaLA-500，采用了词汇扩展和在LLaMA上使用Glot500-c进行持续预训练的方法

在SIB-200上的实验表明，MaLA-500取得了SOTA上下文学习结果

<img src="https://img.saraba1st.com/forum/202401/26/211843km8k8moq3iq14s33.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-210309.jpg</strong> (64.71 KB, 下载次数: 0)

下载附件

2024-1-26 21:18 上传

使用不同LLM在SIB-200上的3-shot上下文学习宏平均(macro-average)准确率(%)的结果，mGPT没有约70亿参数的模型版本，因此选择了参数130亿的更大模型

<img src="https://img.saraba1st.com/forum/202401/26/211848b2ttl9k7vv57lzok.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-210333.jpg</strong> (70.91 KB, 下载次数: 0)

下载附件

2024-1-26 21:18 上传

在SIB-200上的3-shot上下文学习详细结果
X轴:不同准确率范围内的语言数量(%)

<img src="https://img.saraba1st.com/forum/202401/26/211852lir0paqo5y5siqrc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-210347.jpg</strong> (69 KB, 下载次数: 0)

下载附件

2024-1-26 21:18 上传

MaLA-500在SIB-200上不同样本数量的上下文学习宏平均准确率(%)

<img src="https://img.saraba1st.com/forum/202401/26/211856hpba7ojxwhmohav1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-210400.jpg</strong> (92.85 KB, 下载次数: 0)

下载附件

2024-1-26 21:18 上传

使用MaLA-500在SIB-200上进行上下文学习的详细结果
X轴:不同准确率范围内的语言数量(%)
Y轴:样本数量

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1223#       发表于 2024-1-26 22:12

SpeechGPT-Gen

拓展信息链(Chain-of-Information)语音生成

github项目主页:https://github.com/0nutation/SpeechGPT

得益于有效的语音建模，当前的语音大型语言模型(SLLMs/Speech Large Language Models)在上下文语音生成和对未见的说话者(unseen speakers)方面展现了高效泛化的卓越能力，然而，当前的信息建模过程存在某些冗余，导致语音生成效率低下

本文提出了信息链生成(CoIG/Chain-of-Information Generation)的方法，用于在大规模语音生成中解耦语义和感知信息(perceptual information)，在此基础上开发了SpeechGPT-Gen，一个8亿参数的SLLM，能够高效地建模语义和感知信息，它包括一个基于LLM的用于语义信息建模的自回归模型，以及一个采用流匹配(flow matching)进行感知信息建模的非自回归模型，此外，还引入了将语义信息注入先验分布以增强流匹配效率的新方法

广泛的实验结果表明，SpeechGPT-Gen在零样本文本转语音(zero-shot text-to-speech)、零样本声音转换(zero-shot voice conversion)和语音到语音对话(speech-to-speech dialogue)方面表现出色，展现了CoIG在捕捉和建模语音语义和感知维度方面的卓越能力

<img src="https://img.saraba1st.com/forum/202401/26/221138p1gcn4qrz0lkn5gk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-220855.jpg</strong> (102.48 KB, 下载次数: 0)

下载附件

2024-1-26 22:11 上传

三种语音生成方法的示意图，整合建模(Integrated modeling)表示同时进行语义建模和感知建模

(a)整合生成
(b)语义解耦生成
(c)信息链生成

<img src="https://img.saraba1st.com/forum/202401/26/221154lmqdredqlygq8r9q.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-220913.jpg</strong> (94.62 KB, 下载次数: 0)

下载附件

2024-1-26 22:11 上传

SpeechGPT-Gen的概览图，解码器代表SpeechTokenizer解码器，不同颜色的块代表包含不同信息的表征

<img src="https://img.saraba1st.com/forum/202401/26/221158npa9y5f5t3t45y4i.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-220940.jpg</strong> (101.82 KB, 下载次数: 0)

下载附件

2024-1-26 22:11 上传

零样本文本到语音和声音转换的结果

<img src="https://img.saraba1st.com/forum/202401/26/221202pd75ymbzfr7bpjwm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-220948.jpg</strong> (47.03 KB, 下载次数: 0)

下载附件

2024-1-26 22:12 上传

语音到语音对话的结果

<img src="https://img.saraba1st.com/forum/202401/26/221207geiuu9s1s6wu39uw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-221019.jpg</strong> (94.71 KB, 下载次数: 0)

下载附件

2024-1-26 22:12 上传

AR(自回归)建模和NAR(非自回归)建模的整合生成、语义解耦生成和信息链生成的训练损失

<img src="https://img.saraba1st.com/forum/202401/26/221211pukrahnua6u5u6rv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-221026.jpg</strong> (105.09 KB, 下载次数: 0)

下载附件

2024-1-26 22:12 上传

整合生成、语义解耦生成和信息链生成相关的零样本TTS的单词错误率和说话者相似度

<img src="https://img.saraba1st.com/forum/202401/26/221217cfaz3kne8gk6kfe7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-221043.jpg</strong> (76.97 KB, 下载次数: 0)

下载附件

2024-1-26 22:12 上传

使用标准高斯先验和语义先验进行流匹配的零样本语音转换的单词错误率和说话者相似度

<img src="https://img.saraba1st.com/forum/202401/26/221223gaxfuuxleoo25fkf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-221050.jpg</strong> (67.15 KB, 下载次数: 0)

下载附件

2024-1-26 22:12 上传

不同大小的流匹配模型的训练损失和零样本语音转换的单词错误率和说话者相似度

<img src="https://img.saraba1st.com/forum/202401/26/221229la5r33rm3aqmg083.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-221108.jpg</strong> (45.29 KB, 下载次数: 0)

下载附件

2024-1-26 22:12 上传

离散感知建模和连续感知建模的零样本语音转换的单词错误率和说话者相似度

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1224#       发表于 2024-1-26 22:57

InstructDoc

通过指令进行视觉文档理解的零样本泛化数据集

github项目代码仓库:https://github.com/nttmdlab-nlp/InstructDoc

本文研究了如何通过人工编写的指令完成各种视觉文档理解(VDU/visual document understanding)任务，例如问答和信息提取等

为此，本文提出了InstructDoc，这是第一个包含30个公开可用的VDU数据集的大规模集合，每个数据集都采用统一的格式包含多样化的指令，涵盖了12种不同的任务，包括各种开放的文档类型/格式

此外，为了提高VDU任务的泛化性能，还设计了一种新的基于指令的文档阅读和理解模型，称为InstructDr，它通过可训练的桥接模块(trainable bridging module)连接文档图像、图像编码器和大型语言模型

实验证明，InstructDr能够通过给定的指令有效地适应新的VDU数据集、任务和领域，并且在没有特定训练的情况下优于现有的多模态LLMs和ChatGPT

<img src="https://img.saraba1st.com/forum/202401/26/225555ud1gxgdx5kgh7ggw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-225150__01.jpg</strong> (360.86 KB, 下载次数: 0)

下载附件

2024-1-26 22:55 上传

InstructDoc数据集的示例，输入定义了意图(蓝色)、查询和选项(绿色)和答案风格(红色)

查询和选项以及输出来自原始数据集，只对意图和答案风格组成的或仅意图组成的指令进行了标注

<img src="https://img.saraba1st.com/forum/202401/26/225601s9nnqpdr6up55nnd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-225158__01.jpg</strong> (363.53 KB, 下载次数: 0)

下载附件

2024-1-26 22:56 上传

InstructDoc使用的数据集，涵盖了各种VDU任务和文档类型和格式

<img src="https://img.saraba1st.com/forum/202401/26/225608hmais7kna7e3ewx3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-225207__01.jpg</strong> (316 KB, 下载次数: 0)

下载附件

2024-1-26 22:56 上传

InstructDr模型，在训练过程中，只更新Document-former的参数和投影FFN层的参数

<img src="https://img.saraba1st.com/forum/202401/26/225614tnnnf5kgrj5qj67k.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-225213__01.jpg</strong> (154.04 KB, 下载次数: 0)

下载附件

2024-1-26 22:56 上传

InstructDoc和其他VDU指令调整数据集的统计数据，排除了DocOwl中除了VDU任务之外的数据，IT代表指令模板(instruction templates)

<img src="https://img.saraba1st.com/forum/202401/26/225622bfmzmmc6r6tcom66.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-225223__01.jpg</strong> (423.98 KB, 下载次数: 0)

下载附件

2024-1-26 22:56 上传

InstructDr和MLLMs在VDU任务上的零样本性能
“T/L/V”表示文档的“text/layout/visual”模态
#TuP/#ToP表示调整/总参数的数量
最高的零样本性能以粗体标记
†表示原论文中报告的监督性能，因为它并不公开可用
IDoc表示InstructDoc

<img src="https://img.saraba1st.com/forum/202401/26/225631l3gkxofxx3rz8bf8.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-225230__01.jpg</strong> (248.38 KB, 下载次数: 0)

下载附件

2024-1-26 22:56 上传

InstructDr和监督SOTA模型以及强大的基于文本的LLMs在VDU任务上的零样本性能

*表示使用不同的拆分进行评估，因为它们在排行榜上进行评估，无法使用F1进行评估

<img src="https://img.saraba1st.com/forum/202401/26/225636gr1lbz1cgnykiizn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-225242__01.jpg</strong> (158.69 KB, 下载次数: 0)

下载附件

2024-1-26 22:56 上传

架构和指令的消融实验，报告了可以进行消融的得分

<img src="https://img.saraba1st.com/forum/202401/26/225640fohonvvacknvcqq9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-225249__01.jpg</strong> (86.45 KB, 下载次数: 0)

下载附件

2024-1-26 22:56 上传

在DUDE上五个不同指令的零样本性能对比
w/o Multiple instructions表示本文模型在每个数据集上使用单指令进行训练

<img src="https://img.saraba1st.com/forum/202401/26/225647o55up39gg93ujjkr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-225249__02.jpg</strong> (90.05 KB, 下载次数: 0)

下载附件

2024-1-26 22:56 上传

模型性能随训练中使用的任务聚类数量变化，(·)表示任务数量

<img src="https://img.saraba1st.com/forum/202401/26/225653hlxo7oh16wfh6k3c.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-225306__01.jpg</strong> (488.45 KB, 下载次数: 0)

下载附件

2024-1-26 22:56 上传

定性示例，输出是正确/充分(绿色)和不正确/不充分(红色)的答案，(...)表示省略号

<img src="https://img.saraba1st.com/forum/202401/26/225658djf1ttll83iakpek.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-225311__01.jpg</strong> (84.85 KB, 下载次数: 0)

下载附件

2024-1-26 22:56 上传

在测试集上进行的held-in(VisualMRC)和held-out(DUDE/SlideVQA)任务的微调性能

<img src="https://img.saraba1st.com/forum/202401/26/225703c6nptptn6w8ptazz.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240126-225311__02.jpg</strong> (91.9 KB, 下载次数: 0)

下载附件

2024-1-26 22:57 上传

场景文本VQA任务的零样本性能

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1225#       发表于 2024-1-27 01:08

ConTextual

评估大型多模态模型上下文相关的富文本(Context-Sensitive Text-Rich )视觉推理

项目主页:https://con-textual.github.io/

github项目代码仓库:https://github.com/rohan598/ConTextual

hugface数据集下载:https://huggingface.co/datasets/ucla-contextual/contextual_all

评估排行榜:https://con-textual.github.io/#leaderboard

最近的人工智能发展引领了大型多模态模型(LMMs)的进步，这些模型能够处理涉及文本和图像内容的复杂任务(例如在公共场所中导航地图)

本文介绍了ConTextual，一个新颖的基准测试，其中包含专门设计用于评估LMMs在执行上下文相关的富文本视觉推理能力方面的指令，ConTextual强调多样化的现实场景(例如，读时钟、导航、购物等)，要求更深入地理解文本和视觉元素之间的交互

研究发现，最佳的LMM，即GPT-4V(ision)，与人类评估的人类能力相比存在30.8%的性能差距，这表明在上下文相关的富文本视觉推理方面还有很大的改进空间，值得注意的是，虽然GPT-4V在抽象类别(如表情包和引用解释)方面表现出色，但其整体性能仍落后于人类，除了人类评估，还使用了GPT-4进行了自动评估指标，发现了类似的性能差距趋势，通过对不同的视觉环境进行细致的评估，并提供了定性分析，为LMM设计的未来发展提供了一个强大的框架

<img src="https://img.saraba1st.com/forum/202401/27/010620wwpabhzkwdhhww6h.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240127-010036__01.jpg</strong> (284.7 KB, 下载次数: 0)

下载附件

2024-1-27 01:06 上传

GPT-4V、Gemini-Pro-Vision、ShareGPT-4V-7B和人类在CONTEXTUAL数据集上的表现

(a)人类评估和基于GPT-4的自动评估的响应正确性
(b)使用基于GPT-4的评估在视觉上下文变化中的细粒度性能

<img src="https://img.saraba1st.com/forum/202401/27/010628cz69oozo0k9rjr22.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240127-010054__01.jpg</strong> (400.87 KB, 下载次数: 0)

下载附件

2024-1-27 01:06 上传

现有数据集(如ESTVQA)和CONTEXTUAL数据集在富文本视觉推理方面的特性对比

(a)之前的数据集主要测试LMM的阅读能力，因此，它们的问题可以通过对准确的OCR检测结果进行纯文本推理来解决，然而，本文希望评估现代模型在更具挑战性的场景中的能力，因为它们已经展现出了增强的视觉感知和推理能力
(b)CONTEXTUAL的实例构造成可以测试模型捕捉图像中文本和视觉内容交互的上下文能力，在这里，仅仅依靠检测到的OCR进行纯文本推理是不够的

<img src="https://img.saraba1st.com/forum/202401/27/010649mej3brra4y4ienb4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240127-010115__01.jpg</strong> (231.1 KB, 下载次数: 0)

下载附件

2024-1-27 01:06 上传

用于评估大型多模态模型在富文本视觉推理方面的相关工作的对比，将上下文相关缩写为Consens.，生成缩写为Gen

<img src="https://img.saraba1st.com/forum/202401/27/010713yjous89o8j3c8l9o.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240127-010124__01.jpg</strong> (542.05 KB, 下载次数: 0)

下载附件

2024-1-27 01:07 上传

CONTEXTUAL中的8种视觉上下文示例各取其一，大型多模态模型应该能够遵循

<img src="https://img.saraba1st.com/forum/202401/27/010727p3hhyq9z9qhnicv1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240127-010131__01.jpg</strong> (233.76 KB, 下载次数: 0)

下载附件

2024-1-27 01:07 上传

数据收集工作流程:
(1)短列表图像，利用手动和自动方法从源数据集中筛选出要进行标注的图像
(2)指令与响应创建，将作者分为两个独立的组(绿色表示第一组，紫色表示第二组)，分配给每个组对应四个类别的图像进行标注
(3)数据样本验证，仔细检查在前一阶段标注的&lt;图像，指令，响应&gt;三元组，其中一组交叉验证另一组所做的标注

<img src="https://img.saraba1st.com/forum/202401/27/010741os54u28ssj85x5sw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240127-010141__01.jpg</strong> (192.66 KB, 下载次数: 0)

下载附件

2024-1-27 01:07 上传

CONTEXTUAL的关键统计数据

<img src="https://img.saraba1st.com/forum/202401/27/010747ts9jq5v2qhhz8968.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240127-010141__02.jpg</strong> (369.29 KB, 下载次数: 0)

下载附件

2024-1-27 01:07 上传

指令中出现的最频繁的前40个发生动词(内圈)和它们的前4个直接名词(外圈)

<img src="https://img.saraba1st.com/forum/202401/27/010810dhjhqhqmvexet4j2.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240127-010207__01.jpg</strong> (158.14 KB, 下载次数: 0)

下载附件

2024-1-27 01:08 上传

在CONTEXTUAL数据集上对比各种基础模型(增强LLM和LMMs)和人类的性能，使用人工评估、自动GPT-4和基于GPT-4V的评估来报告响应接受率，此外，还报告了标准的文本生成质量评估指标，包括BLEURT、Rouge-L和BERTScore

可以发现人类在数据集上表现优于所有现有模型，而最好的LMM GPT-4V与人类性能相差30%

<img src="https://img.saraba1st.com/forum/202401/27/010817jkwvx5v1te5ett8f.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240127-010214__01.jpg</strong> (77.72 KB, 下载次数: 0)

下载附件

2024-1-27 01:08 上传

使用ROC-AUC和spearman相关性对比人工和自动评估指标，基于GPT-4和GPT-4V的评估在两种方法中与人类相关性最高

<img src="https://img.saraba1st.com/forum/202401/27/010823szgm6gmj1zm0me91.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240127-010228__01.jpg</strong> (94.6 KB, 下载次数: 0)

下载附件

2024-1-27 01:08 上传

CONTEXTUAL数据集上的少样本性能

<img src="https://img.saraba1st.com/forum/202401/27/010830vwxxcw6wktz1zzcx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240127-010234__01.jpg</strong> (469.24 KB, 下载次数: 0)

下载附件

2024-1-27 01:08 上传

基于GPT-4评估，对CONTEXTUAL数据集上的基础模型(增强LLM和LMMs)和人类的性能进行细粒度对比

平均响应接受率缩写为Avg.，购物为Shop.，导航为Nav.，摘要为Abs.，应用使用为App.，网络使用为Web，信息图为Info.，其他自然场景为NS

GPT-4V在大多数类别上优于所有模型基线，而Gemini-Pro-Vision在网络使用和自然场景方面表现最好

<img src="https://img.saraba1st.com/forum/202401/27/010842irh6omqwehmeormn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240127-010250__01.jpg</strong> (275.11 KB, 下载次数: 0)

下载附件

2024-1-27 01:08 上传

在这个例子中，尽管具有逻辑推理能力，GPT-4V对指令提供了一个错误的回答，绿色表示与参考答案匹配的回答，红色突出显示回答中的错误，此外，还提供了总结推理来概述GPT-4V得出答案所使用的基本原理

<img src="https://img.saraba1st.com/forum/202401/27/010854sjuhuwbc0uzudvf0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240127-010250__02.jpg</strong> (203.41 KB, 下载次数: 0)

下载附件

2024-1-27 01:08 上传

在这个例子中，GPT-4V对指令作出了正确的回答，然而，ShareGPT-4V-7B(表现最佳的开源LMM)和带有布局感知的OCR+字幕说明的GPT-4(增强LLM)给出了错误的回答，因为它们缺乏对文本和图像的联合推理能力

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1226#       发表于 2024-1-27 04:58

 本帖最后由 Machinery 于 2024-1-27 05:01 编辑 

ChatterBox

多轮多模态指代和基准(Referring and Grounding)

github项目主页:https://github.com/sunsmarterjie/ChatterBox

在这项研究中，为一项名为多模态多轮指代与基准(MRG/multimodal multi-round referring and grounding)的新任务建立了一个新基线，为实例级多模态对话开辟了一个有前景的方向，为此，构造了一个新的基准测试集CB-300K，以及一个高效的视觉语言模型ChatterBox，CB-300K基准测试集涵盖多轮对话、多个实例之间的复杂空间关系、一致的推理等挑战，超越了现有基准测试集

提出的模型名为ChatterBox，采用了一个双分支(two-branch)架构来协同处理视觉和语言任务，通过对实例区域进行分词化(tokenizing)，语言分支获得了感知指代信息的能力，同时，ChatterBox将视觉分支中的查询嵌入馈送给一个Token接收器进行视觉基准，还设计了一个两阶段的优化策略，利用CB-300K和辅助外部数据来改进模型在实例级理解方面的稳定性和能力

实验证明，ChatterBox在MRG方面，定量和定性实验中都优于现有模型，为复杂而精确的多模态对话场景铺就了一条新的道路

<img src="https://img.saraba1st.com/forum/202401/27/045558b2m3niilzuiu1zvf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240127-045048__01.jpg</strong> (612.78 KB, 下载次数: 0)

下载附件

2024-1-27 04:55 上传

多轮指代和视觉基准(MRG)任务的示例，在对话过程中，机器人可以收到用于指代表达的[REF] Token或用于视觉基准的[GND] Token，如果没有这些Token，任务就变成了通常的视觉问答

所有的答案都是由ChatterBox代理者生成的，展示了它在视觉识别方面的强大能力，特别是，ChatterBox可以理解逻辑相关的问题，并结合上下文信息提供答案，例如，在右边的对话中，问题“‘Where is the other one?”需要识别“one”指代的是一个人，然后定位“另一个”与之前提到的那个人所不同的人物

<img src="https://img.saraba1st.com/forum/202401/27/045616rtj1o87t4d1t7v1o.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240127-045055__01.jpg</strong> (134.68 KB, 下载次数: 0)

下载附件

2024-1-27 04:56 上传

ChatterBox与最近的研究方法在进行多轮对话(包括区域级指代和视觉基准)方面的能力、提出的新数据(†表示需要生成新的对话数据而不仅仅是重新组织现有数据)，训练成本方面的差异，N/R表示未报告

<img src="https://img.saraba1st.com/forum/202401/27/045633up04osh5ybmsaw68.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240127-045108__01.jpg</strong> (697.62 KB, 下载次数: 0)

下载附件

2024-1-27 04:56 上传

CB-300K数据集包含了四个不同目的的子集

图像和元数据(物体位置和描述)来自Visual Genome，同一张图片可以出现在不同的子集中，前两个子集CB-MRG和CB-LC是通过提示GPT-4阅读元数据并生成问题和答案来获得的，后两个子集CB-REF和CB-GND是使用手动设计的规则生成的，并经由GPT-3.5修订

<img src="https://img.saraba1st.com/forum/202401/27/045659aablmci9i5ii8w5v.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240127-045118__01.jpg</strong> (68.05 KB, 下载次数: 0)

下载附件

2024-1-27 04:56 上传

每个独立子集和整个基准测试的关联列数量和问题答案对数量

<img src="https://img.saraba1st.com/forum/202401/27/045721csa64245ltsscczk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240127-045129__01.jpg</strong> (328.04 KB, 下载次数: 0)

下载附件

2024-1-27 04:57 上传

ChatterBox模型的架构，它接收图像和当前问题以及对话历史作为输入，并生成语言输出和必要时的视觉输出(即视觉基准结果)，放大了位置解码器说明查询Token和视觉特征之间的互动

<img src="https://img.saraba1st.com/forum/202401/27/045733fdhxk6sdykkca3fa.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240127-045140__01.jpg</strong> (148.6 KB, 下载次数: 0)

下载附件

2024-1-27 04:57 上传

ChatterBox与之前的工作之间的基于MRG指标的定量对比

<img src="https://img.saraba1st.com/forum/202401/27/045745jb3uuyujk38uoluw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240127-045148__01.jpg</strong> (586.1 KB, 下载次数: 0)

下载附件

2024-1-27 04:57 上传

LISA，Kosmos-2和ChatterBox之间多轮对话的定性对比，本文模型在理解多轮对话和进行推理方面展现了卓越的能力，值得强调的是，更强的视觉识别能力是由明确的视觉模块带来的

<img src="https://img.saraba1st.com/forum/202401/27/045805nmqeumjldzwyq0ss.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240127-045155__01.jpg</strong> (52.52 KB, 下载次数: 0)

下载附件

2024-1-27 04:58 上传

在RefCOCOg数据集上针对单轮指代表达进行定量对比

<img src="https://img.saraba1st.com/forum/202401/27/045810px43dfdryhxvwf9r.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240127-045155__02.jpg</strong> (52.76 KB, 下载次数: 0)

下载附件

2024-1-27 04:58 上传

在COCO 2017测试集上针对单轮视觉基准进行定量对比

<img src="https://img.saraba1st.com/forum/202401/27/045814ztcw3kje2j9q3zkk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240127-045200__01.jpg</strong> (77.63 KB, 下载次数: 0)

下载附件

2024-1-27 04:58 上传

以BERT得分和T得分为指标的诊断结果

CB-300K:是否使用CB-300K进行训练
Ref. Words:在推理阶段是否使用指代表达
注意:第三行不是一个公平的对比，因为它比MRG更容易

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1227#       发表于 2024-1-28 06:06

Multimodal Pathway

通过其他模态的交错数据改进Transformers

github项目主页:https://github.com/AILab-CVC/M2PT

本文提出了利用其他模态的无关数据来改进特定模态的transformers，例如，使用音频或点云数据集(audio or point cloud datasets)来改进ImageNet模型，值得强调的是，目标模态的数据样本与其他模态无关，这与其他利用不同模态的配对数据(例如CLIP)或交错数据的方法有所区别

提出了一种名为Multimodal Pathway的方法，给定一个目标模态和为其设计的transformer，使用经过另一模态数据训练的辅助transformer，并构建路径来连接两个模型的组件，这样目标模态的数据就可以被两个模型处理，通过这种方式，利用从两个模态获得的transformer通用序列到序列建模能力

作为具体实现，通常使用模态特定的分词器(tokenizer)和任务特定的head，但通过一种名为跨模态重参数化(Cross-Modal Re-parameterization)的方法，可以利用辅助模型的transformer blocks而不产生任何推理成本

在图像、点云、视频和音频识别任务中，观察到通过来自其他模态的无关数据，获得了显著且一致的性能改进

<img src="https://img.saraba1st.com/forum/202401/28/060524zaq45eqjo4z9e6sp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240128-055817__01.jpg</strong> (364.51 KB, 下载次数: 0)

下载附件

2024-1-28 06:05 上传

与使用对齐良好的多模态数据的已知范式相比，本文关注的是利用来自多个模态但是无关的场景的数据样本，这是目前待解决的开放问题

<img src="https://img.saraba1st.com/forum/202401/28/060529jdzd5dhtb51btwdb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240128-055826__01.jpg</strong> (298.07 KB, 下载次数: 0)

下载附件

2024-1-28 06:05 上传

(左)M2PT(Multimodal Pathway Transformer)的框架，以点云和图像模态为例子

与transformer的常见做法遵循相同的流程:
1.使用分词器将输入数据转换为序列
2.使用transformer block处理序列
3.使用head解码序列

通过在不同模态的组件之间建立路径来更新序列到序列的建模，因此处理特定模态的token可以利用另一个模态训练的transformer block

(中间)M2PT的概念设计，其中路径是通过让目标模型中的线性层(包括注意力block中的Query/Key/Value/投影层和FFN block中的层)与辅助模型中的对应层进行合作来实现的

(右边)跨模态重参数化通过使用辅助模型的参数重新参数化目标模型的权重来高效实现M2PT，引入了边际训练成本，但完全没有推理成本

<img src="https://img.saraba1st.com/forum/202401/28/060547pfrof8tcpfv6rtcj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240128-055836__01.jpg</strong> (83.73 KB, 下载次数: 0)

下载附件

2024-1-28 06:05 上传

M2PT在图像、视频、点云和音频四个模态的每对之间都带来了一致改进，指标分别为ImageNet-1K准确率、Kinetics-400准确率、Part-Net mIoU和AudioSet准确率

这些数字表示M2PT模型相对于分别在四种模态上使用MAE式方法进行预训练的基线模型性能的改进百分比

<img src="https://img.saraba1st.com/forum/202401/28/060554ho9nhhqx88y9ohhq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240128-055845__01.jpg</strong> (225.37 KB, 下载次数: 0)

下载附件

2024-1-28 06:05 上传

在图像识别任务上的实验结果

在ImageNet上，报告了线性层微调(tune acc)或固定(fix acc)的transformer block结果

∗:结果是通过原版代码得出的，每个模型的架构都是ViT-B，相对于基线模型的改进显示为绿色

<img src="https://img.saraba1st.com/forum/202401/28/060601gsgb2bdgqelmmsqm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240128-055854__01.jpg</strong> (164.69 KB, 下载次数: 0)

下载附件

2024-1-28 06:06 上传

在点云数据集上的实验结果，报告了ShapeNet-Part上的类别mIoU(mIoUC)和实例mIoUI以及PartNet上的mIoU，相对于基线模型的改进显示为绿色

<img src="https://img.saraba1st.com/forum/202401/28/060605hekhd4tsetej4zg4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240128-055854__02.jpg</strong> (124.12 KB, 下载次数: 0)

下载附件

2024-1-28 06:06 上传

在AudioSet-2k上的实验结果，绿色同上

<img src="https://img.saraba1st.com/forum/202401/28/060610qwacxz77mzo5b110.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240128-055901__01.jpg</strong> (101.63 KB, 下载次数: 0)

下载附件

2024-1-28 06:06 上传

在Kinetics-400上的实验结果，绿色同上

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1228#       发表于 2024-1-28 06:40

DeepSeek-Coder

当大型语言模型遇上编程——代码智能的崛起

github项目主页:https://github.com/deepseek-ai/DeepSeek-Coder

大型语言模型的急速发展已经在软件开发中彻底改变了代码智能化，然而，闭源模型的主导地位限制了广泛的研究和开发，为了解决这个问题，本文介绍了DeepSeek-Coder系列，这是一系列的开源代码模型，大小从1.3B到33B不等，在2万亿Token上从头开始训练，这些模型在一个高质量的项目级代码语料库上进行了预训练，并采用了一个16K窗口的fill-in-the-blank任务来增强代码生成和填充能力

进行的广泛评估表明，DeepSeek-Coder不仅在多个基准测试中取得了开源代码模型SOTA性能，还超过了现有的闭源模型，如Codex和GPT-3.5等，此外，DeepSeek-Coder模型采用宽松的许可证，允许同时进行研究和无限制的商业使用

<img src="https://img.saraba1st.com/forum/202401/28/063933g63kf66uw2ko2ehm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240128-063410__01.jpg</strong> (346.35 KB, 下载次数: 0)

下载附件

2024-1-28 06:39 上传

DeepSeek-Coder的性能

<img src="https://img.saraba1st.com/forum/202401/28/063937mgmhmgwhwgjr21gy.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240128-063418__01.jpg</strong> (67.77 KB, 下载次数: 0)

下载附件

2024-1-28 06:39 上传

数据集创建过程

<img src="https://img.saraba1st.com/forum/202401/28/063943tmok8zotm3mjfmcm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240128-063439__01.jpg</strong> (315.82 KB, 下载次数: 0)

下载附件

2024-1-28 06:39 上传

选择的编程语言的清洁训练数据总结

<img src="https://img.saraba1st.com/forum/202401/28/063950eq4l36z6qxux0iue.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240128-063453__01.jpg</strong> (193.59 KB, 下载次数: 0)

下载附件

2024-1-28 06:39 上传

使用FIM作为目标的效果

<img src="https://img.saraba1st.com/forum/202401/28/063954gpdgkgk6hrdjugrw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240128-063503__01.jpg</strong> (242.46 KB, 下载次数: 0)

下载附件

2024-1-28 06:39 上传

DeepSeek-Coder的超参数

<img src="https://img.saraba1st.com/forum/202401/28/064000witdht9nvkvqxdkj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240128-063514__01.jpg</strong> (298.51 KB, 下载次数: 0)

下载附件

2024-1-28 06:40 上传

在多轮对话环境中，DeepSeek-Coder-Instruct 33B的响应示例

<img src="https://img.saraba1st.com/forum/202401/28/064004ki3dat6eeze6isee.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240128-063522__01.jpg</strong> (496.94 KB, 下载次数: 0)

下载附件

2024-1-28 06:40 上传

在多语言HumanEval和MBPP基准上的方法性能

<img src="https://img.saraba1st.com/forum/202401/28/064009a88w53z8l5lwfw9w.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240128-063528__01.jpg</strong> (256.71 KB, 下载次数: 0)

下载附件

2024-1-28 06:40 上传

在DS-1000-Tasks上的不同方法性能

<img src="https://img.saraba1st.com/forum/202401/28/064013cp3bvbvucosypylx.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240128-063532__01.jpg</strong> (330.99 KB, 下载次数: 0)

下载附件

2024-1-28 06:40 上传

在LeetCode Contest基准上的不同模型性能

<img src="https://img.saraba1st.com/forum/202401/28/064017nocq3qoykyq9sddq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240128-063538__01.jpg</strong> (190.68 KB, 下载次数: 0)

下载附件

2024-1-28 06:40 上传

在FIM-Tasks上的不同方法的性能

<img src="https://img.saraba1st.com/forum/202401/28/064022d3btj58gw9f8cvtt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240128-063544__01.jpg</strong> (327.78 KB, 下载次数: 0)

下载附件

2024-1-28 06:40 上传

在跨文件代码补全上的不同模型性能

<img src="https://img.saraba1st.com/forum/202401/28/064026cuj3b7dd74rxzff3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240128-063550__01.jpg</strong> (325.34 KB, 下载次数: 0)

下载附件

2024-1-28 06:40 上传

在程序辅助的数学推理任务上的不同方法性能

<img src="https://img.saraba1st.com/forum/202401/28/064032lwydflfxdf5n7dst.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240128-063555__01.jpg</strong> (121.31 KB, 下载次数: 0)

下载附件

2024-1-28 06:40 上传

DeepSeek-Coder-v1.5 7B预训练数据来源

<img src="https://img.saraba1st.com/forum/202401/28/064037yvlb2v7rucrr353y.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240128-063600__01.jpg</strong> (212.5 KB, 下载次数: 0)

下载附件

2024-1-28 06:40 上传

通过编程解决数学任务对DeepSeek-Coder-Base和DeepSeek-Coder-Base-v1.5性能进行对比分析

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1229#       发表于 2024-1-29 19:27

pix2gestalt

通过合成整体进行非模态切割(Amodal Segmentation)

项目主页:https://gestalt.cs.columbia.edu/

github项目代码仓库:https://github.com/cvlab-columbia/pix2gestalt

pix2gestalt，一个零样本非模态分割框架，通过学习估计在遮挡后仅部分可见的整个对象的形状和外观，利用扩散模型将它们的表征迁移到这个任务中，学习了一个条件扩散模型用于在具有挑战性的零样本用例中重建整个物体，甚至在违背自然和物理先验的艺术作品示例中也能适用，作为训练数据，使用了一个构造的合成数据集，其中包含带有遮挡物的物体与它们的完整对应物

实验证明，本文方法在基准测试中优于监督基线，此外，在存在遮挡的情况下，本文模型还可以显著提高现有的目标识别和3D重建方法的性能

<img src="https://img.saraba1st.com/forum/202401/29/192527dkbdkblc3b5lc6zw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240129-191802__01.jpg</strong> (355.73 KB, 下载次数: 0)

下载附件

2024-1-29 19:25 上传

通过合成实现的非模态分割和重建，pix2gestalt方法可以从部分可见的对象中合成整个对象，实现非模态分割、识别、新视图合成和遮挡对象的3D重建

<img src="https://img.saraba1st.com/forum/202401/29/192533c3dfh93frkdd79df.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240129-191836__01.jpg</strong> (119.57 KB, 下载次数: 0)

下载附件

2024-1-29 19:25 上传

预训练的扩散模型能够生成整个对象，展示了以类别为条件生成的Stable Diffusion样本，通过利用这种合成能力可以进行零样本非模态重建和分割

<img src="https://img.saraba1st.com/forum/202401/29/192540ecz7c25o79y97a8y.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240129-191849__01.jpg</strong> (403.35 KB, 下载次数: 0)

下载附件

2024-1-29 19:25 上传

pix2gestalt是一种使用潜在扩散架构的非模态补全模型，在输入遮挡图像和感兴趣区域的条件下，合成整体(非模态)形式，从而允许进行其他视觉任务

<img src="https://img.saraba1st.com/forum/202401/29/192545o2k2ezert9x3itfe.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240129-191901__01.jpg</strong> (577.54 KB, 下载次数: 0)

下载附件

2024-1-29 19:25 上传

构建训练数据，为了确保只遮挡整个物体，使用一种启发式方法，即比相邻物体更靠近摄像机的物体更可能是整个物体，物体周围的绿色轮廓显示估计的深度比背景更靠近摄像机的位置(红色则相反)

<img src="https://img.saraba1st.com/forum/202401/29/192550c8ohdt7pybyiy9t7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240129-191911__01.jpg</strong> (651.81 KB, 下载次数: 0)

下载附件

2024-1-29 19:25 上传

 真实自然场景的非模态补全和分割，pix2gestalt能够在新状况下合成整个对象，包括艺术作品、iPhone拍摄的图像和错觉图像

<img src="https://img.saraba1st.com/forum/202401/29/192555iigeiudejymjk6us.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240129-191916__01.jpg</strong> (100.71 KB, 下载次数: 0)

下载附件

2024-1-29 19:25 上传

非模态分割结果，报告了在非模态COCO和非模态伯克利分割数据集上的mIoU(%)↑

∗PCNet-Sup使用来自COCO-Amodal的非模态基准答案掩码进行训练

<img src="https://img.saraba1st.com/forum/202401/29/192613qn3nl688r0nuudjd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240129-191948__01.jpg</strong> (352.91 KB, 下载次数: 0)

下载附件

2024-1-29 19:26 上传

在非模态COCO上的非模态补全和分割定性结果，在蓝色圆圈中，展示了PCNet基线中存在纹理扭曲的补全区域，而本文结果则是正确的纹理

<img src="https://img.saraba1st.com/forum/202401/29/192621zjjvhdv58giwjgwj.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240129-192009__01.jpg</strong> (518.44 KB, 下载次数: 0)

下载附件

2024-1-29 19:26 上传

非模态伯克利分割数据集的定性结果，本文方法提供了准确、完整的遮挡物体重建

<img src="https://img.saraba1st.com/forum/202401/29/192626a92ncfwcshz92dsy.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240129-192033__01.jpg</strong> (105.48 KB, 下载次数: 0)

下载附件

2024-1-29 19:26 上传

样本的多样性，非模补全具有固有的不确定性，通过扩散过程中的多次采样，该方法合成了多个可能与输入观察一致的整体物体

<img src="https://img.saraba1st.com/forum/202401/29/192631g5ijirlhzlr0np6n.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240129-192033__02.jpg</strong> (109.12 KB, 下载次数: 0)

下载附件

2024-1-29 19:26 上传

遮挡物体识别，在遮挡和分离COCO数据集上报告了零样本分类准确率，简单的基线方法无法在更具挑战性的分离COCO场景中提高CLIP性能，本文方法则始终以较大的优势提高了识别准确性

<img src="https://img.saraba1st.com/forum/202401/29/192635w27m5orzo4d4cj5n.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240129-192041__01.jpg</strong> (127.24 KB, 下载次数: 0)

下载附件

2024-1-29 19:26 上传

常识和物理错误

左图:重建结果中汽车朝着错误的方向行驶
右图:重建结果违反物理，未能捕捉到手必须拿着甜甜圈盒子的情况

<img src="https://img.saraba1st.com/forum/202401/29/192641fid1nrx1mz9dz1g7.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240129-192057__01.jpg</strong> (431.84 KB, 下载次数: 0)

下载附件

2024-1-29 19:26 上传

非模态3D重建的定性结果，其中感兴趣的物体由黄色点提示指定，将pix2gestalt作为现有SOTA 3D重建模型的插件，能够更轻松的解决用例中具有挑战性的多样化遮挡场景

<img src="https://img.saraba1st.com/forum/202401/29/192647h5e5w1tdcmmz4aff.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240129-192103__01.jpg</strong> (93.32 KB, 下载次数: 0)

下载附件

2024-1-29 19:26 上传

单视图3D重建，报告了Scanned Objects的Chamfer距离和体积IoU

<img src="https://img.saraba1st.com/forum/202401/29/192652gnkppgbpa4zmbplm.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240129-192103__02.jpg</strong> (112.97 KB, 下载次数: 0)

下载附件

2024-1-29 19:26 上传

从单张图像中合成新视图，报告了在Scanned Objects上的结果，请注意SSIM衡量的是图像质量，而不是新视图的准确率

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1230#       发表于 2024-1-30 03:07

SliceGPT

通过删除行和列(Rows and Columns)来压缩大型语言模型

github项目主页:https://github.com/microsoft/TransformerCompression

大型语言模型已成为自然语言处理的基石，但在计算和显存资源等方面付出了巨大代价，稀疏化(Sparsification)提供了一种减轻这些资源限制的解决方案，最近的研究表明，训练好的模型可以在训练后期进行稀疏化处理，现有的稀疏化技术面临挑战，因为它们需要额外的数据结构，并且在当前硬件上的加速程度有限

在本文中，提出了SliceGPT，一种全新的训练后稀疏方案，它用较小的密集矩阵替代了每个权重矩阵，从而减小了网络的嵌入维度，通过广泛的实验，SliceGPT可以在保持LLAMA2-70B、OPT 66B和Phi-2模型零样本任务性能分别为99%、99%和90%的情况下，删除多达25%的模型参数(包括嵌入)

SliceGPT可以在较少的GPU上运行更快，而且无需额外的代码优化:在24GB的消费级GPU上，可以将LLAMA2-70B的推理计算总量减少到稠密模型的64%；在40GB的A100 GPU上，可以将其减少到66%

本文提供了一个新的见解，即Transformer网络中的计算不变性，这使SliceGPT成为可能，希望本文能够激发更多促进未来减少预训练模型的显存和计算需求的方法

github项目说明页截图:

<img src="https://img.saraba1st.com/forum/202401/30/030720bfhemsfodo6c81os.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240130-030431.jpg</strong> (161.74 KB, 下载次数: 0)

下载附件

2024-1-30 03:07 上传

<img src="https://img.saraba1st.com/forum/202401/30/030720tcbc7cdc1ejeh6cs.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240130-030441.jpg</strong> (361.14 KB, 下载次数: 0)

下载附件

2024-1-30 03:07 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1231#       发表于 2024-1-30 04:24

Taiyi-Diffusion-XL

通过大型视觉语言模型支持从而促进双语文本到图像生成发展

hugface权重下载:https://huggingface.co/IDEA-CCNL/Taiyi-Stable-Diffusion-XL-3.5B

Tech Report 技术报告:https://arxiv.org/abs/2401.14688

Demo 体验地址:https://huggingface.co/spaces/IDEA-CCNL/Taiyi-Stable-Diffusion-XL-3.5B

Deployment Webui 推理部署:https://github.com/IDEA-CCNL/Fooocus-Taiyi-XL

最近文本到图像模型的进展显著增强了图像生成能力，但在双语或中文语言支持方面仍存在明显的开源模型缺口，为了解决这个需求，本文提出了Taiyi-Diffusion-XL，这是一个新的中英双语文本到图像模型，通过对CLIP和Stable-Diffusion-XL进行双语连续预训练开发，其中包括将常用汉字整合到CLIP的分词器和嵌入层中，以及绝对位置编码的扩展，从而实现词汇的高效扩充

此外，通过大型视觉语言模型丰富了文本提示，从而产生更好的图像字幕说明并具有更高的视觉质量，这些增强策略随后应用于下游的文本到图像模型，实证结果表明，所开发的CLIP模型在双语图像文本检索方面表现出色，此外，Taiyi-Diffusion-XL的双语图像生成能力超过了先前的模型，Taiyi-Diffusion-XL模型的开发和开源，代表了图像生成领域的一个显著进展，特别适用于中文应用，这一贡献在多模态研究中为更多语言支持的需求迈出了一步

hugface项目说明截图:

<img src="https://img.saraba1st.com/forum/202401/30/042454b8vfmlln8ovu8lll.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240130-042136__01.jpg</strong> (784.9 KB, 下载次数: 0)

下载附件

2024-1-30 04:24 上传

<img src="https://img.saraba1st.com/forum/202401/30/042454nrdmilw1n6re6mbv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240130-042136__02.jpg</strong> (237.68 KB, 下载次数: 0)

下载附件

2024-1-30 04:24 上传

<img src="https://img.saraba1st.com/forum/202401/30/042454qoqlweveeqp4nc4f.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240130-042136__03.jpg</strong> (953.97 KB, 下载次数: 0)

下载附件

2024-1-30 04:24 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1232#       发表于 2024-1-31 06:33

InternLM-XComposer2

掌握大型视觉语言模型中的自由形式文本图像组合与理解

github项目主页:https://github.com/InternLM/InternLM-XComposer

InternLM-XComposer2，在自由形式的文本图像组合与理解方面表现出色的尖端视觉语言模型，该模型超越了传统的视觉语言理解，从多样的输入中，如轮廓、详细的文本规范和参考图像(outlines, detailed textual specifications, and reference images)中巧妙地构建交替的文本图像内容，实现高度可定制的内容创作

InternLM-XComposer2提出了一种部分LoRA(PLoRA/Partial LoRA)方法，将额外的LoRA参数仅应用于图像Token，以保留预训练语言知识的完整性，在精确的视觉理解和具有文学才艺的文本构成之间取得平衡

实验结果表明，基于InternLM2-7B的InternLM-XComposer2在生成高质量的长文本多模态内容方面具有显著优势，在各种基准测试中展现了卓越的视觉语言理解性能，它不仅显著优于现有的多模态模型，还在某些评估中与GPT-4V和Gemini Pro相匹敌甚至超越，这凸显了它在多模态理解领域的能力

github中文项目说明页截图:

<img src="https://img.saraba1st.com/forum/202401/31/063300rsez4gcpz473z6up.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-063128.jpg</strong> (318.39 KB, 下载次数: 0)

下载附件

2024-1-31 06:33 上传

<img src="https://img.saraba1st.com/forum/202401/31/063300aekhhlz6v2a2nwa0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-063159.jpg</strong> (266.28 KB, 下载次数: 0)

下载附件

2024-1-31 06:33 上传

<img src="https://img.saraba1st.com/forum/202401/31/063300lpo45jjowpwfoehf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-063211.jpg</strong> (268.05 KB, 下载次数: 0)

下载附件

2024-1-31 06:33 上传

<img src="https://img.saraba1st.com/forum/202401/31/063300gstip8xs6el7l63t.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-063227.jpg</strong> (169.93 KB, 下载次数: 0)

下载附件

2024-1-31 06:33 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1233#       发表于 2024-1-31 10:12

Diffutoon

通过扩散模型进行高分辨率可编辑卡通着色(Shading)

项目主页:https://ecnu-cilab.github.io/DiffutoonProjectPage/

github DiffSynth-Studio综合主页:https://github.com/Artiprocher/DiffSynth-Studio

卡通渲染(Toon shading)是一种非照片真实渲染任务的动画化技术，主要目的是以扁平和风格化的外观渲染物体，随着扩散模型在图像合成方法中的崛起，本文探讨了一种基于扩散模型的创新化卡通渲染方法，旨在将逼真的视频直接渲染成动画风格，当前的视频风格化方法面临着持续挑战，尤其是在保持一致性和实现高视觉质量

在本文中，将卡通渲染问题建模为四个子问题:风格化、一致性增强、结构引导和色彩着色(stylization, consistency enhancement, structure guidance, and colorization)

为了解决视频风格化的挑战，提出了一种有效的卡通渲染方法，称为Diffutoon，Diffutoon能够以动画风格渲染出极其详细、高分辨率的长期视频，它还可以通过额外分支根据提示(prompts)编辑内容

通过定量指标和人类评估，测试了Diffutoon的有效性，实验结果表明，Diffutoon同时超过了开源和闭源基线

Diffutoon的整体架构，上方是主要的卡通渲染工作流程，下方是编辑分支，编辑分支可以为主要的卡通渲染工作流程生成色彩视频帧的编辑信号

各种方法的定量结果

人类评估研究中的用户偏好

与其他方法的视觉对比，用于编辑的提示为“best quality, perfect anime illustration, a girl is dancing, smile, solo, orange dress , black hair , white shoes , blue sky”

Diffutoon的中间结果，在主要的卡通渲染流程中，依据轮廓视频和色彩视频合成视频，当启用编辑分支时，生成的色彩视频包含编辑信号

没有轮廓信息渲染的视频

没有色彩信息渲染的视频

使用Animate-Diff作为编辑分支渲染的视频

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1234#       发表于 2024-1-31 22:28

Mobile-Agent

具有视觉感知的自主多模态移动设备代理者(Agent)

github项目代码仓库:https://github.com/X-PLUG/MobileAgent

基于多模态大型语言模型(MLLM)的移动设备代理者正成为流行应用，在本文中，介绍了Mobile-Agent，一种自主多模态移动设备代理者

Mobile-Agent首先利用视觉感知工具准确识别和定位应用前端界面中的视觉和文本元素，根据感知到的视觉内容，它自主规划和分解复杂的操作任务，并通过逐步操作导航移动应用程序，与之前依赖于应用程序的XML文件或移动系统元数据的解决方案不同，Mobile-Agent以视觉为中心的方式在各种移动操作环境中具有更高的适应性，从而消除了对系统进行特定定制的必要性

为了评估Mobile-Agent的性能，引入了Mobile-Eval，用于评估移动设备操作的基准测试，基于Mobile-Eval，对Mobile-Agent进行了全面的评估

实验结果表明，Mobile-Agent实现了显著的准确性和完成率，即使在具有挑战性的指令(例如多应用程序操作)下，Mobile-Agent依然能够完成要求

<img src="https://img.saraba1st.com/forum/202401/31/222655utgnbnfbh4jif3tr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-221959__01.jpg</strong> (358.73 KB, 下载次数: 0)

下载附件

2024-1-31 22:26 上传

移动代理者是用于操作移动设备的自主代理者，基于用户指令，移动代理者可以规划一系列操作来完成需求

<img src="https://img.saraba1st.com/forum/202401/31/222700pa3rfaf433j7arzr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222020__01.jpg</strong> (331.72 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

移动代理者的框架

<img src="https://img.saraba1st.com/forum/202401/31/222705x4m10sitttdphih4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222039__01.jpg</strong> (370.05 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

Mobile-Eval中使用的应用程序和指令

<img src="https://img.saraba1st.com/forum/202401/31/222710brar66rat57gw6gs.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222045__01.jpg</strong> (205.35 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

Mobile-Agent在Mobile-Eval上取得的整体评估结果，其中RE的两个值分别代表Mobile-Agent和人类花费的步骤数

<img src="https://img.saraba1st.com/forum/202401/31/222716mknslrdsf9mm94m1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222058__01.jpg</strong> (599.76 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

指令理解和执行规划的用例

<img src="https://img.saraba1st.com/forum/202401/31/222722hf99pv2syrb6c8gg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222106__01.jpg</strong> (539.22 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

进行无效操作后的自我反思和错误修正用例

<img src="https://img.saraba1st.com/forum/202401/31/222727ex9gyss4i4euh49d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222113__01.jpg</strong> (424.57 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

使用无效和不正确操作后的自我反思和错误修正用例，其中操作“点击文本(添加评论)”导致了错误的页面，而操作“点击文本(发布)”是一个无效操作，无效和不正确操作以红色突出显示

<img src="https://img.saraba1st.com/forum/202401/31/222732gzajfpqwmjfh4mfg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222120__01.jpg</strong> (337.86 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

操作多个应用程序以搜索游戏结果的用例

<img src="https://img.saraba1st.com/forum/202401/31/222736g7ue187eiese81fp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222127__01.jpg</strong> (252.44 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

操作多个应用程序以撰写温度分析的用例

<img src="https://img.saraba1st.com/forum/202401/31/222742ax2601fw6tvtex8j.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222136__01.jpg</strong> (150.08 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

操作中文系统和应用的用例

<img src="https://img.saraba1st.com/forum/202401/31/222746x7j4thgajt3jonhb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222147__01.jpg</strong> (485.27 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

玩游戏的用例

<img src="https://img.saraba1st.com/forum/202401/31/222752d2iyly4f7f44amzf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222159__01.jpg</strong> (382.87 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

从Alibaba.com批发帽子的用例

<img src="https://img.saraba1st.com/forum/202401/31/222759uly6ckhcpmd6j9yk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222211__01.jpg</strong> (390.93 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

搜索YouTube视频并评论该视频的用例

<img src="https://img.saraba1st.com/forum/202401/31/222804kv4v5bsn227nsyb9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222222__01.jpg</strong> (404.92 KB, 下载次数: 0)

下载附件

2024-1-31 22:28 上传

在Google Play下载特定应用程序的用例

<img src="https://img.saraba1st.com/forum/202401/31/222809mpxtpx7vqp708v8s.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222236__01.jpg</strong> (265.58 KB, 下载次数: 0)

下载附件

2024-1-31 22:28 上传

使用地图应用程序进行导航的用例

<img src="https://img.saraba1st.com/forum/202401/31/222814ihq2q77r7rq25i7z.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222247__01.jpg</strong> (334.15 KB, 下载次数: 0)

下载附件

2024-1-31 22:28 上传

使用Amazon Music搜索和播放特定内容音乐的用例

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1234#       发表于 2024-1-31 22:28

Mobile-Agent

具有视觉感知的自主多模态移动设备代理者(Agent)

github项目代码仓库:https://github.com/X-PLUG/MobileAgent

基于多模态大型语言模型(MLLM)的移动设备代理者正成为流行应用，在本文中，介绍了Mobile-Agent，一种自主多模态移动设备代理者

Mobile-Agent首先利用视觉感知工具准确识别和定位应用前端界面中的视觉和文本元素，根据感知到的视觉内容，它自主规划和分解复杂的操作任务，并通过逐步操作导航移动应用程序，与之前依赖于应用程序的XML文件或移动系统元数据的解决方案不同，Mobile-Agent以视觉为中心的方式在各种移动操作环境中具有更高的适应性，从而消除了对系统进行特定定制的必要性

为了评估Mobile-Agent的性能，引入了Mobile-Eval，用于评估移动设备操作的基准测试，基于Mobile-Eval，对Mobile-Agent进行了全面的评估

实验结果表明，Mobile-Agent实现了显著的准确性和完成率，即使在具有挑战性的指令(例如多应用程序操作)下，Mobile-Agent依然能够完成要求

<img src="https://img.saraba1st.com/forum/202401/31/222655utgnbnfbh4jif3tr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-221959__01.jpg</strong> (358.73 KB, 下载次数: 0)

下载附件

2024-1-31 22:26 上传

移动代理者是用于操作移动设备的自主代理者，基于用户指令，移动代理者可以规划一系列操作来完成需求

<img src="https://img.saraba1st.com/forum/202401/31/222700pa3rfaf433j7arzr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222020__01.jpg</strong> (331.72 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

移动代理者的框架

<img src="https://img.saraba1st.com/forum/202401/31/222705x4m10sitttdphih4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222039__01.jpg</strong> (370.05 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

Mobile-Eval中使用的应用程序和指令

<img src="https://img.saraba1st.com/forum/202401/31/222710brar66rat57gw6gs.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222045__01.jpg</strong> (205.35 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

Mobile-Agent在Mobile-Eval上取得的整体评估结果，其中RE的两个值分别代表Mobile-Agent和人类花费的步骤数

<img src="https://img.saraba1st.com/forum/202401/31/222716mknslrdsf9mm94m1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222058__01.jpg</strong> (599.76 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

指令理解和执行规划的用例

<img src="https://img.saraba1st.com/forum/202401/31/222722hf99pv2syrb6c8gg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222106__01.jpg</strong> (539.22 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

进行无效操作后的自我反思和错误修正用例

<img src="https://img.saraba1st.com/forum/202401/31/222727ex9gyss4i4euh49d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222113__01.jpg</strong> (424.57 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

使用无效和不正确操作后的自我反思和错误修正用例，其中操作“点击文本(添加评论)”导致了错误的页面，而操作“点击文本(发布)”是一个无效操作，无效和不正确操作以红色突出显示

<img src="https://img.saraba1st.com/forum/202401/31/222732gzajfpqwmjfh4mfg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222120__01.jpg</strong> (337.86 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

操作多个应用程序以搜索游戏结果的用例

<img src="https://img.saraba1st.com/forum/202401/31/222736g7ue187eiese81fp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222127__01.jpg</strong> (252.44 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

操作多个应用程序以撰写温度分析的用例

<img src="https://img.saraba1st.com/forum/202401/31/222742ax2601fw6tvtex8j.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222136__01.jpg</strong> (150.08 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

操作中文系统和应用的用例

<img src="https://img.saraba1st.com/forum/202401/31/222746x7j4thgajt3jonhb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222147__01.jpg</strong> (485.27 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

玩游戏的用例

<img src="https://img.saraba1st.com/forum/202401/31/222752d2iyly4f7f44amzf.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222159__01.jpg</strong> (382.87 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

从Alibaba.com批发帽子的用例

<img src="https://img.saraba1st.com/forum/202401/31/222759uly6ckhcpmd6j9yk.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222211__01.jpg</strong> (390.93 KB, 下载次数: 0)

下载附件

2024-1-31 22:27 上传

搜索YouTube视频并评论该视频的用例

<img src="https://img.saraba1st.com/forum/202401/31/222804kv4v5bsn227nsyb9.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222222__01.jpg</strong> (404.92 KB, 下载次数: 0)

下载附件

2024-1-31 22:28 上传

在Google Play下载特定应用程序的用例

<img src="https://img.saraba1st.com/forum/202401/31/222809mpxtpx7vqp708v8s.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222236__01.jpg</strong> (265.58 KB, 下载次数: 0)

下载附件

2024-1-31 22:28 上传

使用地图应用程序进行导航的用例

<img src="https://img.saraba1st.com/forum/202401/31/222814ihq2q77r7rq25i7z.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-222247__01.jpg</strong> (334.15 KB, 下载次数: 0)

下载附件

2024-1-31 22:28 上传

使用Amazon Music搜索和播放特定内容音乐的用例

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1235#       发表于 2024-1-31 23:46

MouSi

多视觉专家(Poly-Visual-Expert)视觉语言模型

github项目主页:https://github.com/FudanNLPLAB/MouSi

最近的大型视觉语言模型(VLMs)经常会遇到诸如单个视觉组件的能力不足和过长的视觉Token之类的挑战，这些问题可能会限制模型在准确解释复杂的视觉信息和过长的上下文信息方面的效果，解决这些挑战对于提高VLM的性能和适用性至关重要

本文提出了聚合专家技术(ensemble experts technique)，通过与单独视觉编码器协作处理，包括擅长图像文本匹配、OCR、图像分割等能力的专家，该技术引入了一个融合网络，统一处理来自不同视觉专家的输出，并弥合了图像编码器和预训练LLMs之间的差距

此外，还探索了不同的位置编码方案，以减少由于长图像特征序列问题引起的位置编码的浪费，有效解决了位置溢出(position overflow)和长度限制(length limitations)的问题，例如，在本文的具体实现中，这项技术显著减少了像SAM这样的模型中的位置占用，从4096减少到更高效和可管理的64甚至1

实验结果表明，具有多个专家的VLMs在性能上表现出一致的优势，相比孤立的视觉编码器，集成更多的专家可以更显著提升性能

<img src="https://img.saraba1st.com/forum/202401/31/234444o1iu5d5dur4du1zy.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-233609__01.jpg</strong> (280.98 KB, 下载次数: 0)

下载附件

2024-1-31 23:44 上传

左侧:对比InstructBLIP、Qwen-VL-Chat、LLaVA-1.5-7B，poly-visual-expert MouSi在九个基准测试中达到了SoTA

右侧:在九个基准数据集上，不同数量的专家的最佳模型表现，总体而言，三个专家比两个专家更好，而两个专家又比一个专家更好

<img src="https://img.saraba1st.com/forum/202401/31/234451a3o2e232l2l9e3hg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-233630__01.jpg</strong> (279.33 KB, 下载次数: 0)

下载附件

2024-1-31 23:44 上传

MouSi模型结构概览图，多视觉专家MouSi模型支持集成具有不同类型和能力的视觉专家

<img src="https://img.saraba1st.com/forum/202401/31/234458f58vnzuuj1keum5t.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-233651__01.jpg</strong> (195.78 KB, 下载次数: 0)

下载附件

2024-1-31 23:44 上传

六个预训练视觉专家的对比

Res.表示图像分辨率，d_hid表示隐藏维度，Param.表示参数数量

<img src="https://img.saraba1st.com/forum/202401/31/234504vw5b55dutw5ty4tb.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-233701__01.jpg</strong> (207.1 KB, 下载次数: 0)

下载附件

2024-1-31 23:45 上传

两种多专家融合网络的示例，展示了MLP方法如何使用“2-patches-1-token”压缩视觉信息，以及Q-Former方法如何使用3个可训练的查询压缩信息，具有渐变颜色的模块表示多个专家之间参数共享以传递知识

<img src="https://img.saraba1st.com/forum/202401/31/234512xts3a03iffc7asfa.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-233715__01.jpg</strong> (219.17 KB, 下载次数: 0)

下载附件

2024-1-31 23:45 上传

四种位置编码方案的示意图，⊕运算符表示行位置编码和列位置编码相加

<img src="https://img.saraba1st.com/forum/202401/31/234518jmfoz6mhlfi0eaee.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-233732__01.jpg</strong> (221.67 KB, 下载次数: 0)

下载附件

2024-1-31 23:45 上传

九个基准测试上的六个视觉专家的对比

Param表示参数数量

<img src="https://img.saraba1st.com/forum/202401/31/234523f9knno9u5nzkru2n.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-233749__01.jpg</strong> (448.11 KB, 下载次数: 0)

下载附件

2024-1-31 23:45 上传

不同的双专家方法的性能对比，∆标记的行与单专家方法进行对比，蓝色单元格表示双专家模型更好，红色单元格表示单专家模型更好

<img src="https://img.saraba1st.com/forum/202401/31/234529eqqw2quzfqqqfq56.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-233758__01.jpg</strong> (245.97 KB, 下载次数: 0)

下载附件

2024-1-31 23:45 上传

不同的三专家方法的性能对比，∆标记的行与双专家方法进行对比，蓝色单元格表示三专家模型更好，红色单元格表示双专家模型更好

<img src="https://img.saraba1st.com/forum/202401/31/234534u3hq0ef7c9o8ag81.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-233806__01.jpg</strong> (160.64 KB, 下载次数: 0)

下载附件

2024-1-31 23:45 上传

不同多专家融合方法的性能对比

<img src="https://img.saraba1st.com/forum/202401/31/234538mh0iu4im4d31em6g.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-233812__01.jpg</strong> (168.67 KB, 下载次数: 0)

下载附件

2024-1-31 23:45 上传

不同专家顺序的性能对比，交换了“DINOv2+CLIP”和“ConvNext+CLIP”中的专家顺序

<img src="https://img.saraba1st.com/forum/202401/31/234543k00cddiduqchnfds.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-233817__01.jpg</strong> (178.33 KB, 下载次数: 0)

下载附件

2024-1-31 23:45 上传

九个基准测试上的四种位置编码方案的对比

<img src="https://img.saraba1st.com/forum/202401/31/234548nqy9ykfy309x5iu0.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-233824__01.jpg</strong> (59.22 KB, 下载次数: 0)

下载附件

2024-1-31 23:45 上传

“LayoutLMv3+DINOv2+CLIP”三专家视觉编码器的平均注意力概率(%)分配

<img src="https://img.saraba1st.com/forum/202401/31/234553g1kwjycw17w1m12m.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-233829__01.jpg</strong> (335.13 KB, 下载次数: 0)

下载附件

2024-1-31 23:45 上传

对三专家模型(LayoutLMv3+DINOv2+CLIP)进行的扰动实验，具体扰动是屏蔽对应视觉专家的所有输出

<img src="https://img.saraba1st.com/forum/202401/31/234606e8gkvg7gkmom2oul.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-233837__01.jpg</strong> (283.66 KB, 下载次数: 0)

下载附件

2024-1-31 23:46 上传

数据增强对九个基准测试的影响

Param.表示参数数量

<img src="https://img.saraba1st.com/forum/202401/31/234613kllbnozlboehjotc.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240131-233930__01.jpg</strong> (395.02 KB, 下载次数: 0)

下载附件

2024-1-31 23:46 上传

由Mousi生成的定性示例

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1236#       发表于 2024-2-1 02:43

 本帖最后由 Machinery 于 2024-2-1 02:44 编辑 

H2O-Danube-1.8B

H2O.ai训练的18亿参数基础模型系列

arxiv技术报告:https://arxiv.org/abs/2401.16818

hugface Base模型权重下载:https://huggingface.co/h2oai/h2o-danube-1.8b-base

hugface Chat模型权重下载:https://huggingface.co/h2oai/h2o-danube-1.8b-chat

H2O-Danube-1.8B，一个遵循LLama 2和Mistral核心原则，在1T Token上训练的1.8B参数语言模型，通过利用和改进各种预训练大型语言模型技术，尽管本系列模型训练的总Token数量相比类似规模的参考模型要少得多，但在多项基准测试中表现出了极具竞争力的指标结果

此外，还发布了一个通过监督微调(supervised fine-tuning)和直接偏好优化(direct preference optimization)训练获得的聊天模型，本系列模型以Apache 2.0许可协议公开发布提供，以使更广泛的经济受众能够进一步使用LLM

<img src="https://img.saraba1st.com/forum/202402/01/024230lm787ih5w7ow4wpp.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240201-024025.jpg</strong> (153.48 KB, 下载次数: 0)

下载附件

2024-2-1 02:42 上传

训练日志

训练(左上角)和验证(右上角)的交叉熵损失，学习率调度(左下角)和序列长度(右下角)，X轴则是训练到该步骤的Token数

<img src="https://img.saraba1st.com/forum/202402/01/024236trh8rpjp3blkqkr3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240201-024045.jpg</strong> (175.98 KB, 下载次数: 0)

下载附件

2024-2-1 02:42 上传

常识推理、世界知识和阅读理解基准测试

与其他相似规模的模型相比，H2O-Danube-1.8B在所有基准测试中表现均一致且良好，它在所有基准测试中的表现都优于Qwen(除了BoolQ)，尽管大小相同，但训练的Token数少了2.2倍，Stable LM 2在大多数基准测试中略优于H2O-Danube-1.8B，但它的训练Token数是H2O-Danube-1.8B的4倍

此外，Qwen和Stable LM 2模型都不具备Apache 2.0许可证，而且商业使用还需要满足额外条件

<img src="https://img.saraba1st.com/forum/202402/01/024302gw408w81pttkw5lw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240201-024104.jpg</strong> (174.54 KB, 下载次数: 0)

下载附件

2024-2-1 02:43 上传

Open LLM排行榜，对于表中的每个模型，报告了所有独立基准测试的得分，以及不包括GSM8k基准测试的平均得分

H2O-Danube-1.8B在大多数基准测试中的结果与Qwen和Stable LM 2模型相似，除了GSM8k和MMLU，这可以通过模型训练使用的数据来解释，例如，Qwen在数学推理上使用了更好的gsm8k-ScRel数据集

<img src="https://img.saraba1st.com/forum/202402/01/024308hticw1p6j6xcyiyh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240201-024125.jpg</strong> (120.56 KB, 下载次数: 0)

下载附件

2024-2-1 02:43 上传

Mt-bench聊天基准测试

该表展示了mt-bench除了编码类别之外的第1轮和第2轮评估结果，结果突出了H2O-Danube-1.8B-Chat的出色表现，尤其是在单轮对话中，它在多个类别和平均Mt-bench得分中都表现最高

<img src="https://img.saraba1st.com/forum/202402/01/024313hodv9fmuxxuzhxm5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240201-024147.jpg</strong> (84.63 KB, 下载次数: 0)

下载附件

2024-2-1 02:43 上传

聊天模型的常识推理、世界知识和阅读理解基准测试

H2O-Danube-1.8B-Chat在所有零样本常识推理基准测试中的表现都优于TinyLlama-Chat和Qwen-Chat模型，并与Stablelm-2-Zephyr模型相当

<img src="https://img.saraba1st.com/forum/202402/01/024318u91cvjv6nnt8iq0n.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240201-024159.jpg</strong> (80.9 KB, 下载次数: 0)

下载附件

2024-2-1 02:43 上传

聊天模型的Open LLM排行榜

H2O-Danube-1.8B-Chat在大多数基准测试中的表现优于TinyLlama-Chat，并与Qwen-Chat和Stablelm-2-Zephyr模型在大多数基准测试中表现相似，除了GSM8k和MMLU

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1237#       发表于 2024-2-2 09:50

 本帖最后由 Machinery 于 2024-2-2 09:53 编辑 

LongAlign

大型语言模型的长上下文对齐秘方

github项目主页:https://github.com/THUDM/LongAlign

拓展大型语言模型以有效处理长上下文需要对相似长度的输入序列进行指令微调，为了解决这个问题，本文提出了LongAlign，一种用于长上下文对齐的指令数据、训练和评估方法

首先，通过使用自指导(Self-Instruct)构建了一个长指令跟随数据集，为了确保数据的多样性，它涵盖了来自各种长上下文来源的广阔任务，其次，采用了打包和排序批处理(packing and sorted batching)策略，以加速对具有不同长度分布的数据进行监督微调的速度，此外，还开发了一种损失加权(loss weighting)方法，在打包训练期间平衡不同序列对损失的贡献，最后还引入了LongBench-Chat基准测试，用于评估在长度为10k-100k的查询上的指令跟随能力

实验证明，LongAlign在长上下文任务中的性能比现有的LLM配方提高了多达30％，同时也维持了它们处理较短的通用任务的熟练程度

<img src="https://img.saraba1st.com/forum/202402/02/095301giex07hkznntmiko.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240202-094503.jpg</strong> (157.91 KB, 下载次数: 0)

下载附件

2024-2-2 09:53 上传

LongBench-Chat上的测试结果，包含10k-100k长度的真实世界查询

数据构建示例

在长尾数据长度分布下，打包或排序批处理可以减少空闲时间并加速训练过程，在打包过程中需要进行损失加权，以平衡序列的损失贡献

标注者之间的相关性，GPT-4(有无Few-shot)与人类之间的相关性

在不同数量和类型的长指令数据上训练后的ChatGLM3-6B-64k性能

与ShareGPT混合的不同套件的长数据上训练的ChatGLM3-6B-64k的1k-60k Needle测试性能

ChatGLM3-6B-64k和Llama-2-7B-64k在不同的训练方法下的性能

不同的训练方法下，使用8个A800 80G GPU的训练时间(小时)

LLama-2-13B上的LongAlign

ChatGLM3-6B-64k在长任务和短任务上至始至终的相对性能

—— 来自 [S1Fun](https://s1fun.koalcat.com)


*****

####  Machinery  
##### 1238#       发表于 2024-2-2 20:58

 本帖最后由 Machinery 于 2024-2-2 20:59 编辑 

OLMo

加速语言模型学科的发展

技术报告:https://arxiv.org/abs/2402.00838

hugface模型权重:https://huggingface.co/allenai/OLMo-7B

github项目代码仓库:https://github.com/allenai/OLMo

hugface预训练数据集下载:https://huggingface.co/datasets/allenai/dolma

github模型评估套件:https://github.com/allenai/OLMo-Eval

微调适配项目页:https://github.com/allenai/open-instruct

语言模型(LM)已经在自然语言处理研究和商业产品中变得无处不在，随着它们在商业上的重要性日益增长，最强力的模型逐渐变得封闭，通常只能通过专有接口访问，其训练数据、架构和开发的重要细节也未公开，鉴于这些细节对于科学研究这些模型、包括它们的偏见和潜在风险的重要性，研究界访问功能强大且真正开放的语言模型因此变得至关重要

为此，本技术报告详细介绍了OLMo的首次发布，这是一个SOTA的、真正开放的语言模型及其构建和研究语言建模科学的框架，与以往只发布模型权重和推理代码的大多数研究不同，本次发布了OLMo和整个框架，包括训练数据、训练和评估代码，希望这次发布能为开源研究社区提供动力和支持，并激发新一轮的创新
————
模型描述与细节

<img src="https://img.saraba1st.com/forum/202402/02/205832h3cmlan98g9a3wjg.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240202-205205.jpg</strong> (326.04 KB, 下载次数: 0)

下载附件

2024-2-2 20:58 上传

<img src="https://img.saraba1st.com/forum/202402/02/205832kz66fukh7lklunn1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240202-205222.jpg</strong> (116.46 KB, 下载次数: 0)

下载附件

2024-2-2 20:58 上传

<img src="https://img.saraba1st.com/forum/202402/02/205832vm3xzprx3124753k.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240202-205327.jpg</strong> (205.42 KB, 下载次数: 0)

下载附件

2024-2-2 20:58 上传

————
模型的使用以及微调与评估

<img src="https://img.saraba1st.com/forum/202402/02/205902qnrsttngt9txyfnw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240202-205240.jpg</strong> (221.84 KB, 下载次数: 0)

下载附件

2024-2-2 20:59 上传

<img src="https://img.saraba1st.com/forum/202402/02/205902w977fqk6dqczxq56.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240202-205250.jpg</strong> (73.78 KB, 下载次数: 0)

下载附件

2024-2-2 20:59 上传

<img src="https://img.saraba1st.com/forum/202402/02/205902b8n1zpeza8vm0e1a.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240202-205304.jpg</strong> (174.77 KB, 下载次数: 0)

下载附件

2024-2-2 20:59 上传

————
训练环境的影响与偏差风险限制等

<img src="https://img.saraba1st.com/forum/202402/02/205908aw4ho4ah8hg778gh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240202-205443.jpg</strong> (109.48 KB, 下载次数: 0)

下载附件

2024-2-2 20:59 上传

—— 来自 [S1Fun](https://s1fun.koalcat.com)

*****

####  Machinery  
##### 1239#       发表于 2024-2-5 22:37

 本帖最后由 Machinery 于 2024-2-5 22:39 编辑 

TravelPlanner

测试语言代理者进行现实世界规划的基准

项目主页:https://osu-nlp-group.github.io/TravelPlanner/

github项目代码仓库:https://github.com/OSU-NLP-Group/TravelPlanner

hugface数据集下载:https://huggingface.co/datasets/osunlp/TravelPlanner

基准测试排行榜:https://huggingface.co/spaces/osunlp/TravelPlannerLeaderboard

自从人工智能的概念诞生以来，规划(planning)一直是其核心追求之一，但早期的AI代理者多数关注于受限环境设置下的测试，这主要是因为模型缺乏实现人类级别水平的规划所需的许多认知基础，最近，大型语言模型(LLMs)驱动的语言代理者们展现出了一些例如工具使用和推理之类的有趣能力，这些语言代理者们是否能在更复杂的环境中进行超越的先前AI代理者们的复杂规划吗？

为了推进这项研究，本文提出了TravelPlanner，这是一个新的规划基准，其中重点关注了旅行规划，一种常见的真实世界规划场景，它提供了一个丰富的沙箱环境，各种用于访问近400万条数据记录的工具，以及1225个精心策划的规划意图(planning intents)和参考计划(reference plans)

全面的评估表明，目前的语言代理者还不能处理如此复杂的规划任务，即使是GPT-4的成功率也只有0.6%。语言代理依然在保持任务连贯性、使用正确工具收集信息、遵从多个约束的规划方面都存在困难

然而，当前的语言代理者们仅仅能够应对如此复杂的问题本身就是不平凡的进步，TravelPlanner为未来的语言代理者们提供了一个具有挑战性富有意义的测试平台

<img src="https://img.saraba1st.com/forum/202402/05/223809b00b53kp053euc4q.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240205-223250__01.jpg</strong> (630.86 KB, 下载次数: 0)

下载附件

2024-2-5 22:38 上传

TravelPlanner概览图，给定一个查询，语言代理者被要求使用各种搜索工具收集信息，根据收集到的信息，语言代理者需要提供一个计划，既满足查询中用户指定的需求，又符合常识约束

<img src="https://img.saraba1st.com/forum/202402/05/223829oftu3uuzv9hua196.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240205-223307__01.jpg</strong> (577.94 KB, 下载次数: 0)

下载附件

2024-2-5 22:38 上传

约束描述，环境约束通过从环境接收的反馈来体现，用于评估语言代理者是否能够适当地调整其计划。常识约束和硬约束是根据语言代理者的计划与这些特定标准的一致性来评估的

<img src="https://img.saraba1st.com/forum/202402/05/223840tssltpl0tr9g4atv.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240205-223315__01.jpg</strong> (70.26 KB, 下载次数: 0)

下载附件

2024-2-5 22:38 上传

数据库中的数据条目数量

<img src="https://img.saraba1st.com/forum/202402/05/223850nxnwr1cxv9xiwcco.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240205-223341__01.jpg</strong> (473.22 KB, 下载次数: 0)

下载附件

2024-2-5 22:38 上传

不同的LLM与不同规划策略在TravelPlanner验证集和测试集上的主要结果

最佳结果用粗体标记，当收集的信息不足时，Gemini Pro倾向于直接拒绝提供计划，与标注者的访谈显示，手动标注一个计划平均需要约12分钟，然而，语言代理者们，如GPT-3.5-Turbo，只需1到2分钟就可以完成这个任务，这展现出了它们的效率

<img src="https://img.saraba1st.com/forum/202402/05/223857bc86mrycjtw2wfct.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240205-223400__01.jpg</strong> (110.71 KB, 下载次数: 0)

下载附件

2024-2-5 22:38 上传

测试集上的工具使用错误分布，如果代理者连续三次失败尝试或重复操作，将触发提前停止，这代表语言代理者进入了死循环

<img src="https://img.saraba1st.com/forum/202402/05/223904u4acangtoiggk1ah.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240205-223400__02.jpg</strong> (291.57 KB, 下载次数: 0)

下载附件

2024-2-5 22:39 上传

GPT-4-Turbo在测试集上的约束通过率，独立规划(sole-planning)模式的结果基于直接策略(Direct strategy)

<img src="https://img.saraba1st.com/forum/202402/05/223912x8b9za2cu7alppbo.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240205-223408__01.jpg</strong> (94.88 KB, 下载次数: 0)

下载附件

2024-2-5 22:39 上传

对GPT-4-Turbo和参考之间的不同工具使用次数的对比，代理者的结果基于写入“Notebook”的条目数量

<img src="https://img.saraba1st.com/forum/202402/05/223918yqnw6fzhdmff6h22.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240205-223414__01.jpg</strong> (663.03 KB, 下载次数: 0)

下载附件

2024-2-5 22:39 上传

失败案例研究，代理由于重复错误(如日期错误)、信息细节混淆导致的幻觉性回答以及推理和行动之间的脱节而未能完成计划

所有案例均基于GPT-4-Turbo的代理，关于使用反思策略的GPT-4-Turbo的详细信息，请参见原论文

—— 来自 [S1Fun](https://s1fun.koalcat.com)

*****

####  Machinery  
##### 1240#       发表于 2024-2-6 00:05

 本帖最后由 Machinery 于 2024-2-6 00:06 编辑 

MAGDi

对多代理者交互图(Multi-Agent Interaction Graphs)的结构化蒸馏(Structured Distillation)改进了小型语言模型的推理能力

github项目主页:https://github.com/dinobby/MAGDi

大型语言模型(LLM)代理者之间的交互推理方法，在不同的推理任务上都呈现出了改进，然而，这些方法涉及多个模型在多轮中进行长时间生成，导致计算成本高昂，此外，这些多代理者方法无法提供一个最终的、用于高效推理的单一模型

为了解决这个问题，本文引入了MAGDi，一种将多个LLM之间的推理交互进行结构化蒸馏进更小的语言模型的新方法，MAGDi通过将多代理者交互表征为图(graphs)，利用图编码器(graph encoder)增强基础学生模型，并使用三个目标函数进行知识蒸馏:下一个Token预测、正确和错误推理之间的对比损失，以及基于图形的目标函数以建模交互结构

在七个广泛使用的常识和数学推理基准测试中的实验证明，MAGDi提高了较小模型的推理能力，优于其他几种从单个教师和多个教师进行蒸馏的方法

此外，MAGDi还展现了比其教师更高的效率，进行的广泛分析显示MAGDi(1)增强了对OOD任务的泛化能力，(2)随着基础学生模型的规模和强度的增加而呈正相关缩放，(3)通过多教师训练，在应用自我一致性时(self-consistency)时，获得了更大的改进

<img src="https://img.saraba1st.com/forum/202402/06/000518qb83vr3rwwwycc32.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-000100__01.jpg</strong> (323.81 KB, 下载次数: 0)

下载附件

2024-2-6 00:05 上传

本文蒸馏方法MAGDI的概览图，给定一个推理问题，多个教师LLMs进行多轮讨论，生成一个多代理交互图(MAG/multi-agent interaction graph)，然后本文的结构化蒸馏方法MAGDI将这些图中的推理知识蒸馏到基础学生模型中

<img src="https://img.saraba1st.com/forum/202402/06/000524sw8p54t6p6b5twk4.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-000120__01.jpg</strong> (311.11 KB, 下载次数: 0)

下载附件

2024-2-6 00:05 上传

左边(a):使用GPT4、Bard和Claude2协同解决一个数学推理问题的多代理者交互图，经过三轮讨论生成

右边(b-e):MAGDI的四个不同级别，每个级别逐步从MAG的组成部分蒸馏知识

<img src="https://img.saraba1st.com/forum/202402/06/000529x9nwzk8ynn3op3aw.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-000128__01.jpg</strong> (413.44 KB, 下载次数: 0)

下载附件

2024-2-6 00:05 上传

训练数据构建:给定一个推理问题，多个教师经过多轮讨论过程，生成多代理者交互图，MAGDI使用图神经网络(本文中为GCN)来增强基础学生模型，学习推理链的结构感知表征，然后使用涉及正向链、负向链和底层交互(positive chains, negative chains, and the underlying interactions)的三个目标进行微调

<img src="https://img.saraba1st.com/forum/202402/06/000549w3v33s9365i1gc3i.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-000154__01.jpg</strong> (300.45 KB, 下载次数: 0)

下载附件

2024-2-6 00:05 上传

结构化蒸馏(MAGDI)与无教师、单教师和多教师蒸馏基线的对比

首先，MAGDI在所有五个推理基准测试中表现优于所有基线，平均而言，MAGDI比最强的SIT-GPT4基线提高了4.61%，比无教师基线提高了10.71%，其次，从MAG的每个组成部分进行知识蒸馏都能改善学生模型，从Level 1到Level 4，性能一直稳步提升

<img src="https://img.saraba1st.com/forum/202402/06/000554azldluhl3lip2tti.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-000201__01.jpg</strong> (100.49 KB, 下载次数: 0)

下载附件

2024-2-6 00:05 上传

RECONCILE(一个多代理者交互框架)和MAGDI生成的Token计数的对比

<img src="https://img.saraba1st.com/forum/202402/06/000557obn4hh38ouq22njn.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-000201__02.jpg</strong> (53.17 KB, 下载次数: 0)

下载附件

2024-2-6 00:05 上传

性能和效率之间的权衡，MAGDI超越了之前研究工作方法的帕累托边界，既在性能上超过了单教师模型，又在效率上超过了RECONCILE，效率定义为1/平均(Token数)

<img src="https://img.saraba1st.com/forum/202402/06/000601kbgf00mhqvszs0qq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-000213__01.jpg</strong> (38.02 KB, 下载次数: 0)

下载附件

2024-2-6 00:06 上传

单教师多任务(SIT-GPT4-MT)和MAGDI多任务(MAGDI-MT)模型在OOD数据集上的对比，即使在OOD数据集上(57.52 vs. 64.30)，MAGDI-MT的性能也比单教师基线提高了多达7%

<img src="https://img.saraba1st.com/forum/202402/06/000605bbbsmfsxph4tmxsi.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-000213__02.jpg</strong> (78.62 KB, 下载次数: 0)

下载附件

2024-2-6 00:06 上传

使用不同的基础学生模型进行MAGDI蒸馏的缩放结果，随着基础模型的平均(零样本)性能的提高(Mistral-7B &gt; LLaMA-2-13B &gt; LLaMA-2-7B)，MAGDI蒸馏性能也相应增加

<img src="https://img.saraba1st.com/forum/202402/06/000609n3sak86ekiibjo1k.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-000221__01.jpg</strong> (50.63 KB, 下载次数: 0)

下载附件

2024-2-6 00:06 上传

MAGDI在GSM8K上的自我一致性相比基础学生模型和单教师蒸馏模型实现了最大的收益(高达15%)

*****

####  Machinery  
##### 1241#       发表于 2024-2-6 04:47

 本帖最后由 Machinery 于 2024-2-6 04:48 编辑 

Nomic Embed

可重现的长上下文文本嵌入器(Long Context Text Embedder)

技术报告:https://arxiv.org/abs/2402.01613

github项目主页:https://github.com/nomic-ai/contrastors

这份技术报告描述了nomic-embed-text-v1的训练过程，它是第一个可完全复现的、开源、开放权重、开放数据、上下文长度为8192的英文文本嵌入模型，在短文本和长文本任务上均优于OpenAI的Ada-002和OpenAI text-embedding-3-small

同时，以Apache 2许可证发布了训练代码和模型权重，与其他开源模型不同，还发布了一个训练数据加载器，其中包含了2.35亿个经过筛选的文本对，可以完全复制nomic-embed-text-v1的训练过程

<img src="https://img.saraba1st.com/forum/202402/06/044736z8h86fd6qthjtwas.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-044506.jpg</strong> (102.82 KB, 下载次数: 0)

下载附件

2024-2-6 04:47 上传

文本嵌入模型的基准测试结果，nomic-embed-text-v1、OpenAI text-embedding-ada、OpenAI text-embedding-3-small和jina-embedding-base-v2在短文本和长文本基准测试中的综合性能

Nomic Embed是唯一一个可以完全审计的长文本模型，它在短文本和长文本基准测试中都超过了OpenAI text-embedding-ada、OpenAI text-embedding-3-small和Jina的性能，X轴的单位因基准套件而异

<img src="https://img.saraba1st.com/forum/202402/06/044743r6wwdq3cczibyzwq.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-044529.jpg</strong> (109.71 KB, 下载次数: 0)

下载附件

2024-2-6 04:47 上传

将nomic-embed-text-v1与OpenAI模型和其他顶级长文本开源模型进行基准测试，Nomic-embed-text-v1是唯一一个具有1亿参数级别的开源模型，它在短文本和长文本任务上均优于OpenAI text-embedding-ada和text-embedding-3-small

Nomic-embed-text-v1-ablated是指第5.4节中描述的训练设置，其中省略了HotpotQA和FEVER数据，“Seq”表示模型的上下文长度，Jina LC是Jina长上下文基准测试中任务的平均值

<img src="https://img.saraba1st.com/forum/202402/06/044749xi3yxlao3j3a37fl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-044541.jpg</strong> (99.13 KB, 下载次数: 0)

下载附件

2024-2-6 04:47 上传

GLUE Dev Set集结果，除了2048模型之外，以与nomic-bert-2048相同的方式进行评估

<img src="https://img.saraba1st.com/forum/202402/06/044755rc61vgd0ibz0x8wl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-044559.jpg</strong> (298.74 KB, 下载次数: 0)

下载附件

2024-2-6 04:47 上传

MTEB基准测试结果，每个类别的数据均取平均值

<img src="https://img.saraba1st.com/forum/202402/06/044802mmrrvwustv7dm0p3.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-044621.jpg</strong> (200.35 KB, 下载次数: 0)

下载附件

2024-2-6 04:48 上传

Jina长上下文评估基准测试

—— 来自 [S1Fun](https://s1fun.koalcat.com)

*****

####  Machinery  
##### 1242#       发表于 2024-2-6 05:35

 本帖最后由 Machinery 于 2024-2-6 05:38 编辑 

PokéLLMon

通过大型语言模型在宝可梦对战中实现人类水准的代理者

github项目主页:https://github.com/git-disl/PokeLLMon

PokéLLMon，它是第一个在战略战斗游戏中实现人类水平表现的LLM具身代理者，就像在宝可梦战斗中所展示的，PokéLLMon的设计包含三个关键策略:
(i)上下文强化学习，即时利用从战斗中产生的基于文本的反馈来迭代改进策略
(ii)知识增强生成，即检索外部知识以抵消幻觉，并使代理者能够及时正确地行动
(iii)一致的动作生成，以减轻代理者面对强大对手并想要躲避战斗时的“恐慌切换(panic switching)”现象

展示了与人类进行的在线战斗，证明了PokéLLMon的类人战斗策略和即时决策能力，其在排行比赛中胜率达到49％，在邀请战斗中胜率达到56％

<img src="https://img.saraba1st.com/forum/202402/06/053618l2hiqxgg2uub0l4h.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-052948.jpg</strong> (155.94 KB, 下载次数: 0)

下载附件

2024-2-6 05:36 上传

在每一轮中，玩家被要求决定采取哪个行动，例如，是让快龙出招还是切换到场外的另一个宝可梦

<img src="https://img.saraba1st.com/forum/202402/06/053624i9fa3atf4pb3b00z.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-053004.jpg</strong> (198.93 KB, 下载次数: 0)

下载附件

2024-2-6 05:36 上传

两个代表性的宝可梦:喷火龙和妙蛙花，每个宝可梦都有(复数)类型、能力、属性和四个战斗招式

<img src="https://img.saraba1st.com/forum/202402/06/053630bcyadz39ssdffxec.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-053018.jpg</strong> (184.48 KB, 下载次数: 0)

下载附件

2024-2-6 05:36 上传

类型相克关系，"+"表示超有效/2倍伤害；"-"表示无效/0.5倍伤害；"×"表示没有效果/0倍伤害，未标记的则为标准1倍伤害

<img src="https://img.saraba1st.com/forum/202402/06/053637gtsstrm9y5vx66z5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-053056.jpg</strong> (607.15 KB, 下载次数: 0)

下载附件

2024-2-6 05:36 上传

使LLMs能够与人类玩家进行战斗的框架:它解析从战斗服务器接收到的消息，并将状态日志转换为文本，LLMs将这些状态描述和历史回合日志作为输入，并为下一步生成一个行动，然后将该行动发送到战斗服务器，并与对手选择的行动一起执行

<img src="https://img.saraba1st.com/forum/202402/06/053644efduersj16zn8dtt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-053109.jpg</strong> (118.16 KB, 下载次数: 0)

下载附件

2024-2-6 05:36 上传

LLMs在与bot对战中的表现

<img src="https://img.saraba1st.com/forum/202402/06/053649i1xs1msxrswtbfvr.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-053133.jpg</strong> (73.22 KB, 下载次数: 0)

下载附件

2024-2-6 05:36 上传

类型相克预测的混合矩阵

<img src="https://img.saraba1st.com/forum/202402/06/053654qbtttnslina3tlht.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-053210.jpg</strong> (104.76 KB, 下载次数: 0)

下载附件

2024-2-6 05:36 上传

POKELLMON配备了三种策略:
(1)ICRL利用战斗中的即时反馈来迭代改进生成
(2)KAG检索外部知识来对抗幻觉，并及时正确地行动
(3)一致的行动生成以预防恐慌切换问题

<img src="https://img.saraba1st.com/forum/202402/06/053701p72b2bwdgd7gz01e.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-053234.jpg</strong> (87.23 KB, 下载次数: 0)

下载附件

2024-2-6 05:37 上传

代理者重复使用相同的攻击招式，但由于其能力“干燥皮肤”，对对方宝可梦没有任何效果

<img src="https://img.saraba1st.com/forum/202402/06/053709idulizwh2i9c26rh.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-053241.jpg</strong> (80.33 KB, 下载次数: 0)

下载附件

2024-2-6 05:37 上传

在第3回合中，代理者使用“精神冲击”，对对方宝可梦造成了零伤害，通过ICRL，代理者切换到另一个宝可梦

<img src="https://img.saraba1st.com/forum/202402/06/053716ezc7ec1dhctchd77.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-053300.jpg</strong> (71.29 KB, 下载次数: 0)

下载附件

2024-2-6 05:37 上传

ICRL在与bot对战中的表现

<img src="https://img.saraba1st.com/forum/202402/06/053731rj2iag6j8j66a5ag.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-053319.jpg</strong> (92.89 KB, 下载次数: 0)

下载附件

2024-2-6 05:37 上传

KAG在与bot对战中的表现

<img src="https://img.saraba1st.com/forum/202402/06/053737xm1mu78xydu7umu1.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-053331.jpg</strong> (91.53 KB, 下载次数: 0)

下载附件

2024-2-6 05:37 上传

代理者理解了招式的效果并正确使用:钥圈儿对钻角犀兽的地面属性攻击很脆弱，代理者没有交换宝可梦，而是使用了“电磁飘浮”这个招式，可以保护自己免受地面属性攻击的影响，持续五回合，从而使对方的钻角犀兽的地面属性攻击“地震”无效

<img src="https://img.saraba1st.com/forum/202402/06/053750t4mf6umfhkikuynd.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-053347.jpg</strong> (92.44 KB, 下载次数: 0)

下载附件

2024-2-6 05:37 上传

提示方法在与bot对战中的表现

<img src="https://img.saraba1st.com/forum/202402/06/053758bws5upsd23wc3s3d.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-053406.jpg</strong> (146.14 KB, 下载次数: 0)

下载附件

2024-2-6 05:37 上传

当面对一个强大的宝可梦时，具有CoT的代理者连续三次换宝可梦来逃避战斗，这给了对手三个免费回合来四倍增加攻击属性，并迅速击败了代理者的整个队伍

<img src="https://img.saraba1st.com/forum/202402/06/053807pz77i8i0gngt7pob.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-053417.jpg</strong> (96.33 KB, 下载次数: 0)

下载附件

2024-2-6 05:38 上传

恐慌切换宝可梦的统计分析

<img src="https://img.saraba1st.com/forum/202402/06/053811ngqajlugeeqelw25.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-053428.jpg</strong> (168.49 KB, 下载次数: 0)

下载附件

2024-2-6 05:38 上传

POKELLMON每回合都选择了有效的招式，使对手的整个队伍都倒下了，只用了一个宝可梦

<img src="https://img.saraba1st.com/forum/202402/06/053816yntnqqjqrotncwco.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-053434.jpg</strong> (57.78 KB, 下载次数: 0)

下载附件

2024-2-6 05:38 上传

POKELLMON对抗人类玩家的表现

<img src="https://img.saraba1st.com/forum/202402/06/053820po4pmmzzpmptmum5.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-053455.jpg</strong> (155.56 KB, 下载次数: 0)

下载附件

2024-2-6 05:38 上传

POKELLMON受到了消耗战策略的困扰:对手玩家经常恢复高防御的宝可梦，要打破这个困境需要跨越多个回合的联合效果

<img src="https://img.saraba1st.com/forum/202402/06/053830ropwztzzthioxapt.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-053514.jpg</strong> (55.15 KB, 下载次数: 0)

下载附件

2024-2-6 05:38 上传

战斗表现受到消耗战策略的影响

<img src="https://img.saraba1st.com/forum/202402/06/053837o78ohl79oz6lq1fl.jpg" referrerpolicy="no-referrer">

<strong>Screenshot_20240206-053527.jpg</strong> (174.49 KB, 下载次数: 0)

下载附件

2024-2-6 05:38 上传

一个经验丰富的人类玩家误导代理者使用龙属性攻击，首先派出一个龙属性宝可梦，然后立即换成另一个免疫龙属性攻击的宝可梦

*****

####  yesicant  
##### 1243#         楼主| 发表于 2024-2-8 07:01

先暂停更新，等泥潭把bug修好，大家新年快乐<img src="https://static.saraba1st.com/image/smiley/face2017/068.png" referrerpolicy="no-referrer">

*****

####  李少卿  
##### 1244#       发表于 2024-3-19 07:24

大佬不更新了吗？

—— 来自 OnePlus GM1910, Android 10上的 [S1Next-鹅版](https://github.com/ykrank/S1-Next/releases) v2.5.4


*****

####  yesicant  
##### 1245#         楼主| 发表于 2024-3-19 07:38

<blockquote><a href="httphttps://bbs.saraba1st.com/2b/forum.php?mod=redirect&amp;goto=findpost&amp;pid=64295183&amp;ptid=2126390" target="_blank">李少卿 发表于 2024-3-19 07:24</a>

大佬不更新了吗？

—— 来自 OnePlus GM1910, Android 10上的 S1Next-鹅版 v2.5.4</blockquote>
感觉最近还沉浸在春节<img src="https://static.saraba1st.com/image/smiley/face2017/068.png" referrerpolicy="no-referrer">

实际上最近没啥大的进展，生态也逐渐起来了，这楼也许可以转讨论楼？

