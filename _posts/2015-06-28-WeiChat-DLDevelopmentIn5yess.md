---
layout: post
title:  斯坦福、谷歌、百度、阿里人工智能顶级专家，探讨未来5年产业机会微信讲座实录
date:   2015-06-28
categories:  record
published: false
author: wubin

---

## 嘉宾介绍

1）李飞飞：

斯坦福大学人工智能中心主任，终身教授；CVPR程序主席，NIPS，ICCV，ECCV领域主席。

2）沙飞：

南加州大学终身教授； ICML，NIPS，AISTATS领域主席。

3）余凯：

前百度深度学习研究院（IDL）创办人，副院长；ICML，NIPS领域主席。

4）漆远：

阿里巴巴数据科学技术研究院（iDST）执行院长；前普渡大学终身教授。 

5）杨克：

谷歌大脑项目早期团队核心科学家；资深机器学习和人工智能专家。

## 前言

这次大家是天南海北，李飞飞和杨克在美国硅谷（特别感谢，现在时他们早上7点），沙飞在德国，余凯、漆远和我在中国，聚在一起不容易啊！

本次讲座有十多名工作人员和志愿者在进行7个群的同步和组织工作，请对他们的辛勤工作表示感谢！

## 讨论环节

### 问题一：
雷鸣：首先，我们现在人工智能到底在什么阶段，从科研来看，从商业化来看？从各个方面看，比如自然语言对话、图像识别、推荐系统、机器人等

请几位都从自己的角度回答一下，大家可以都各自输入，完了发出来就行，谢谢！

### 回答：

杨克：我最近几年都在google里工作。从我这一方面看到的情况，人工智能还处在非常初级的阶段，但是已经有了很多商业的应用。你说的这几个方面都是典型的人工智能的 Application。

杨克：Very early stage, far far from what you see in movies, but enough progress to make useful products and sometimes impressive ones.

余凯：推荐系统目前已经广泛商业化，在商品推荐，个性化广告等，但是推荐系统虽然在互联网公司广泛运用，但是似乎很难依靠推荐系统做出一个独立的服务商业模式，这点和搜索以及广告不同。图像识别和语音识别最近的进展，主要得益于深度学习，目前语音识别在从90%向97%~98%冲刺。而图像识别，要相对滞后，但是最近几年发展迅速，将会看到一些成熟的商业应用。

李飞飞：从历史看AI的基础科学走过了两个阶段：expert system 的研究发展和应用，和machine learning的研究发展和应用（虽然后者的潜力还远没开发完）。每一次基础科研的进步，一定会带动科技工程和产业的发展。我认为我们现在看到的，就是机器学习这三十年积累下来的果实。从视觉来看，视觉分几个层面：perception, cognition, and action.  perception主要是指的基本识别，如shape, color, motion, objects, etc. 在这方面，因为机器学习的进步，尤其是软硬件的飞跃，我们开始看到接近应用层面的结果了，虽然object识别还有待提高。但是，我们离cognition还很远。

李飞飞：这里指的cognition,包括了类似人类的知识acquisition, abstraction and creation的能力，分析能力，情感和情绪能力，推理能力，等等。

沙飞：人工智能近来的发展确实振奋人心，这主要是得益基于大数据的机器学习进展。一些well-defined benchmark问题得到很大的进展。

漆远：但是同时一些关键问题，比如逻辑和知识的表达，仍未很好地解决。

沙飞：但是有很多问题，还不能很好地归结在现有的机器学习的框架下。

余凯：关于机器人，我认为大的发展刚刚开始，目前在perception （感知）, control方面会有很大的进展，但是cognition（认知）等方面，涉及高层语义以及世界知识，还有巨大距离。所以，如果说现在机器人，想实现阿猫阿狗等宠物的智能水平，我觉得是有现实意义的，但是离人的智能，还不现实。所以在考虑商业模式的的时候，这点要考虑。

### 问题2：
雷鸣：说一下当前最热的人脸识别，现在识别准确率真的超过人了吗？如果没有，那么在最近的一段时间里，会超过吗？

### 回答：

李飞飞：特定情况下超过了人，或者说普通人。这也不奇怪呀，人的基本计算能力很差劲的。

杨克：我看过一段Andrew N的视频。他提到现在的深度学习有很大的发展，因为有很好的Rocket Engine (faster computes and esp. GPUs) and Rocket Fuel (big data)。 我觉得很有道理。人脸识别的确机器可以比人做得更好。我自己的人脸识别能力就非常弱。

沙飞：我同意Andrew的说法，但想补充一点：这些问题解决好的有well-specified performance metric and optimization criteria, so they will benefit more from big data and fast computation.

漆远：哈哈，人脸识别上机器可能更好。但在变形物体上人一般比机器强。

李飞飞：AI的各个分支会在不久的将来在PERCEPTION方面大大超过普通人。但是就像今天的人造飞机比小鸟飞的又快又高，到现在也做不到小鸟的灵活、起落和其他各种飞行能力。

沙飞：IBM Research 在做语音识别时，很早就提出了superhuman recognition (of speech).

余凯：人脸识别的能力，应该是和人相近，或者在有的方面超过人了。比如关于对于身份证件照的人脸验证，在误认率为0.01%时，拒识率可以达到10%，对于百万级别的人脸库，这个能力已经超过人类。人类的人脸识别水平，没有我们想象的高。大家对于高中同年级的同学，可能除了同班的，大部分都记不住人脸，尽管在校园里打过多次照面。

李飞飞：人类的智慧在cognition and action方面的能力是很深刻的，我们还有很多基础科学的工作需要做。

余凯：是的，飞飞说的有道理

杨克：完全同意飞飞的观点。目前的人工智能可以在某些特定的应用上超过人类。但是这和造出一个像电影里面的机器人还是有很大的差距。

漆远：关于沙飞说的现有框架的有限性，一个例子是目前人工智能系统在因果关系上的推理能力也很有限。

### 问题3:

雷鸣：我们接着谈一下当前在人工智能领域最火的名词“深度学习”。当前特别火的深度学习，为什么这么火，能够解决什么问题，有什么优势？有什么局限吗？

### 回答：
余凯：深度学习的基本思想和方法，其实在80年代末就提出。今天之所以受到重视，更多的是因为大数据和计算能力，以及互联网应用需求的拉动。

余凯：目前深度学习的巨大优势，主要体现在感知，比如语音识别，图像识别。

沙飞：Alan的例子很好 可能也是深度学习现在还没解决好的一个问题: causality inference, does not necessarily depend on the amount of data one needs to see.

李飞飞：深度学习是80年代的一支机器学习神经网络的新名字。数学框架没有变得。但是硬件和数据的支持使得这种有high capacity的计算结构发挥的优势。

漆远：能够解决什么问题： 语音和图像是深度学习的经典应用。 在NLP上大家也看到希望。

杨克：从数学上讲，所谓机器学习就是用一堆的数据去fit在一个model in a sparse model space. if your model space is bigger, you can potentially find a better fit.

余凯：深度学习在最近针对序列数据，比如使用RNN, LSTM, 有非常激动人心的发展，这些进展很可能推动语音识别和自然语言处理向前大踏步前进。

李飞飞：深度学习在工业和产业界的大量应用是machine learning既regression和support vector machine之后的又一激动人心的应用。在perception的问题上会让我们看到很多有用的产品。

漆远：或者客服应用里的Q&A上。

沙飞：@Ke: 问题是how to prevent overfitting. 深度学习主要是通过大数据来实现。

李飞飞：但是想大家所说的，今天的深度学习是“浅层思考”, Deep Learning but Shallow Reasoning。


杨克：深度学习无非是把这个model space增大了很多 — RNNs are proven to be Turing complete. 所以他的potential很大。传统上来大家不知道有什么好的方法来train.但是现在的rocket fuel and rocket engine makes it possible


漆远：@沙飞，是的，causal inference has been there for a while but largely ignored by machine learning and AI people. I don't see how deep learning can help here.

余凯：深度学习还有一个激动人心的应用，就是learning to control. 我认为机器人的控制，会因为DNN reinforcement learnign的方法而发生改变。现在的机器人跳舞，只是邯郸学步，很笨，很傻。基于深度学习的机器人，会听着音乐节奏，自己跳舞。

漆远：是的，learning to control echoes neural dynamic programming

余凯：所以，在从感知到控制，DNN是rocket engine. 在认知层面，DNN刚开始，但我相信是正确方向。

雷鸣：听起来深度学习是当前最有突破点的技术，有很多可能。

### 问题4：

除了深度学习之外，最近还有什么在机器学习领域令人振奋的点吗。

### 回答：

杨克：从数学上看，深度学习是机器学习的非常自然的下一步: you move to a more complicated model with bigger model space so that you can fit better without outfitting

漆远：and has tons of potential applications.

余凯：从数学上看，深度学习是机器学习的非常自然的下一步:  — agree Ke Yang

李飞飞：深度学习急需解决的一个问题是knowledge representation。不能什么都靠大数据，即使是shallow的transfer learning也解决不了这个问题。

沙飞：agree with Fei-fei

杨克：在google有人开玩笑说 60% of the time, google brain works all the time.我觉得很有道理。深度学习在一些领域非常成功，但并不是万能药。

漆远：我觉得深度学习是机器学习的一个重要方向，但未必是唯一方向。

余凯：关于飞飞提到的knowlege representation, 需要顺着目前深度学习distributed representation的思路进一步发展，但是我认为需要有新的创新

漆远：agree with Feifei

沙飞：Let me give an example of "shallow reasoning":  I am traveling in Germany. I do not speak German but I need to take subways to go between places.

沙飞：An important "skill" I need to do is to infer from subway announcements of arriving stations whether I have reached the right destination.

余凯：just to make the discussion more interesting — 我认为深度学习是机器学习的唯一方向 [得意]

雷鸣：@余凯 自己找靶子啊[调皮]

余凯：哈哈，我3年前是这么认为的，现在更加坚定了

雷鸣：各位同意余凯的观点吗？

李飞飞：@余凯 主要是现在什么都叫深度学习，所以当然是“所有方向就是唯一方向”嘛[调皮]

漆远：哈哈，now it is more interesting :) 我爱余凯但更爱真理

沙飞：This requires me to figure out (1) how to determine the prounancing  of the destinations in German (2) how to segment the sounds in a language that I do not know, in a noisy environment (3) how to match robustly.  All those require "deep reasoning"

杨克：我觉得作研究的人也喜欢跟风。现在深度学习热了，什么人都在作深度学习。所以放眼望过去，深度学习真的是唯一的方向 — for now.

余凯： 主要是现在什么都叫深度学习，所以当然是“所有方向就是唯一方向”嘛[调皮] — [偷笑]

李飞飞：但是我觉得讨论所谓的深度学习是不是“唯一方向”意义不大，尤其是如果这只是一个文字游戏的话。

雷鸣：我虽然相对各位外行一些，不过确实满眼都是“深度学习”

沙飞：取决于怎么定义深度学习 。

杨克；但是我相信以后会有更多的理论和技术出来，那时候他们还叫不叫深度学习，真的只是一个文字游戏

余凯：在三年前，或者六年前，其实不是这样的。90%的机器学者是怀疑的。

漆远：要知道机器学习领域像是时装界，最时髦的词汇一直在变。

李飞飞：深度学习的思路结合机器学习这三、四十年的很多精髓：optimization theory, hierarchical architecture, and supervised learning. 如果这些叫深度学习的话，也就是文字游戏而已。

漆远：是的，这个争论可能更多的是文字游戏。

余凯：深度学习其实本身的确是一张方法论，一种框架，不是几个具体的模型。

余凯：其实不是文字游戏。我举一点： end-to-end training, 这是深度学习带来的思想。

沙飞：@余凯 那也不是新的 －－ LeCun et al's gradient-based modular learning system has been around for a long while.

雷鸣：不过看来从广义角度来讲，深度学习当前确实代表一个大方向。

余凯：但是我同意飞飞讲的，深度学习的确吸取了几十年来机器学习的很多精髓， 比如: structured output, latent-variable models

余凯：沙飞， LeCun恰恰是一直以来深度学习思想的鼓吹者。

沙飞：That is why he says "What is wrong with deep learning?"  haha

漆远：深度学习也不能刻画uncertainty,在金融应用中往往不确定性和风险联系在一起。

余凯；end-to-end training对深度学习hard core的人来讲，是一种宗教信仰

漆远：这是一个实用的例子。

余凯：深度学习也不能刻画uncertainty — 当然可以，你可以给weights加上prior

李飞飞：其实end to end是很多machine learning algorithm的理念，但是目前确实深度学习应用的最好！[强][强]

沙飞：事实上，uncertainty quantification is a big problem for just about any learning models

余凯：yes

### 问题5: 
雷鸣；最后，从未来5年来看，大家可以看到在什么领域或则方面，人工智能会进入人们的生活，哪些产品或者服务会大有机会，比如智能家居？自动驾驶？智能监控？机器人？，在更宏观的领域，会对医疗，金融，教育，工业等，带来什么深远的影响。

雷鸣：注意关键词：5年，实际影响到人的生活

### 回答：

李飞飞：只要有数据的地方就会有数据分析，只要有数据分析的需要就有人工智能。

雷鸣：其实是给企业家，投资者，创业者看的，从我们专家的眼里，看到的未来几年的热工智能产业机会在哪里？

余凯：只要有数据的地方就会有数据分析，只要有数据分析的需要就有人工智能 — 是的

漆远：同意目前深度学习实用性最好，更general 的深度学习观念可以更广的实用。

余凯：更general 的深度学习观念可以更广的实用 — 是的。

漆远：不过，对实用的深度学习，加了prior 就没法算了。                            雷鸣：我们的社会正转型为数据时代，那么人工智能就是数据时代的王者了[微笑]漆远：所以，uncertainty还是搞不定的，在大规模实用系统里。

余凯：我们不应该过多的看过去，深度学习已经做了什么，更应该看未来，我觉得漆远说的对，更general的深度学习可以更广泛更实用。其实刚才几位也说到了，其实叫不叫深度学习，并不重要，重要的是什么思想。
 
漆远：完全同意

杨克：人工智能早已进入你的生活了。语音识别又是一根很好的例子。搜索引擎里也用到很多人工智能的东西。这一方面百度好像还走在谷歌前面。现代的汽车一般都有几十个电脑－－都不需要自动驾驶车。

李飞飞：但是广大老百姓心目中的人工智能是带有情感、情绪和像人一样的灵活分析纠错和行动能力的东东。

雷鸣：@Ke Yang 同意。但看起来还是早期。我觉得现在的人工智能应用，跟94-96年互联网那样

余凯：我觉得，在线教育，是深度学习大规模应用的一个垂直领域

杨克：实话实说。其是谷歌里面还是有很多深度学习的应用。很多我们也没有说。但是我们总体会慢一些事真的。
                      
雷鸣：非常早期，一切都有可能，但是都没有真正大规模的用起来，到用户非常满意的程度
           
李飞飞：但是人工智能的产业应用还是更低层，更实际。

余凯：实话实说，百度过去在机器学习方面的积累少，所以可以更大胆的应用深度学习，这有历史原因。我也爱阿里的alan qi, 哈哈

杨克：我们的社会正转型为数据时代，那么人工智能就是数据时代的王者了[微笑] －－ 这句话我不一定赞同。就想说大家都用电脑了，做CPU才是王道。

雷鸣：任何一个事情都需要多方面的积累，但是CPU是关键的一环。
余凯：语音识别，图像识别，自然语音理解，我觉得会持续推进。这三个领域，应该会诞生3个500亿美金市值的公司，在今后的10年里。大家拭目以待  

杨克：我觉得人工智能会慢慢变成一种commodity，所有人都会用到。就像多核处理器一样，原来觉得很玄妙的东东，现在手机里都变的士。关键是要找到好的killer app


漆远：同意杨克的说法，不过在人工智能变成一种commodity前，确实会很可能有人工智能公司的rising

雷鸣：我同意杨克的观点，技术本身会慢慢变成不是最关键的，关键的是使用这些技术，真正解决实际问题 

余凯：教育，金融，医疗，交通，智能家居，娱乐，等领域，都会有大的机会。

漆远：5年可能太快了吧。

李飞飞：首先从辅助诊断开始。

雷鸣：到达到医生水平需要多久？你觉得？5年，10年

雷鸣：@余凯，确实，现在机器学习工程师确实一人难求啊！各位搞这个方面的，可是生逢其时啊！

李飞飞：说实话，要是数据不是问题，我认为今天的人工智能已经能在80%的病症方面达到普通医生水平。

漆远：这得看是哪一个科目的医生

雷鸣：哈哈，看来医疗这个方面，未来大有可为啊。教育方面呢？大家如何看？
余凯：医疗是人工智能的大战场

雷鸣：人工智能如何提升教育，老师会被替代吗？

余凯：不会，再好的老师，也需要助教不是

雷鸣：@余凯，那就是人工智能做好老师和家长的教学助理？对吧

余凯：是的，我觉得是

沙飞：more precisely,  "data-driven personalized education monitoring/tutoring systems"
雷鸣：机器人方向呢？你们觉得服务机器人未来5年会大行其道吗？

李飞飞：传教，授业，解惑。人工智能可以做一小部分。

雷鸣：阿里巴巴也投资了

漆远：follow 前面的话题：大部分人大部分时间得的病都是小病，所以人工智能在医疗上可能会很有实际用处的。

漆远：在中国，服务机器人没准也很有用处的；银行的服务窗前队伍太长。

余凯：比如Nest的平台，本身就在朝着智能机器人的方向走，虽然不是人形机器人

雷鸣：那就是智能硬件，智能家居这个方向？传统的东西，更有智慧

李飞飞：这些家用的物联网上的东西，会最早应用到底层的人工智能，形成智能物联网。

杨克：人工智能会从最琐碎的事情开始代替人。现在的电梯都是无人的。现在的车的cruise control越来越好，都是典型

杨克：所以我觉得医疗上会是从边缘的地方开始，比如说 triage, screening, etc. 取代医生还需要一段时间


### 问题6:
雷鸣：各位觉得，在人工智能方向，创业公司和大公司相比有什么优势劣势？小公司有机会翻盘吗？

### 回答：

李飞飞：纵观人类上下五千年，小公司永远有机会翻盘，然后变成大公司被淘汰[偷笑]

漆远：大公司有机器有技术有数据，但可能少了些craziness和不同的角度。

漆远：还少了些灵活度。大象跳舞不太容易的。所以小公司总有机会。但大公司，也许尤其在中国，确实是有天时地利人和的优势。

杨克：同意。余凯同学刚刚离开百度，所以我可以猜到他是怎么想的。我前天刚刚从谷歌离职，也要加入一家小公司。smaller companies distrupt bigger ones


余凯：大公司会在自己的核心领域不断加力，但是在核心领域之外有所作为，会比较难。

## 提问环节

雷鸣：要么对话部分先到这里，我们进入群友提问时间，如何？


大家有什么问题希望和嘉宾探讨，请开始提出。限时一分钟，请群务记录问题

### 1.
漆远：很好地问题，但是不好意思，机器学习可不只是offline learning
李飞飞：机器学习算法是离线学习(offline learning)，生物神经网络是在线学习(online learning)。如何发展深度学习以实现在线学习？
余凯：好问题。深度学习，虽然目前在模型上和以前的模型不同，但是在学习方式上，和传统方法没有太大改变。本质上，我认为未来的深度学习应该和机器人结合在一起，从动态中学习，从运动中学习，从交互中学习

杨克：机器学习算法是离线学习(offline learning)，生物神经网络是在线学习(online learning)。如何发展深度学习以实现在线学习？－－ 深度学习可以实现在线学习呀，叫做reinforcement learning.谷歌收购的一家叫做deepmind的公司就是做einforcement learning名气很大。


沙飞：“机器学习算法是离线学习(offline learning)，生物神经网络是在线学习(online learning)。如何发展深度学习以实现在线学习” 本质是在问， 如何在online learning 时不遗忘以前的knowledge?   这需要有一些特殊的 memory mechanism to prevent loss of previously learned knowledge.

杨克：尤其在盈利的大公司，有这样一种现象，最顶级的机器学习人才集中在商业变现部门为公司创收。有人认为这是一种浪费，应该把人力集中在创新业务和科技进步，各位怎么看？ －－ 我不觉得这是一个binary的问题。研究核应用必须同时开展。不是either or而是and.

智能对话能很好体现机器人的智能。但是目前的智能对话貌似都是人为的智能，也就是人说的话必须是符合预先编程好的场景，出了这些场景，机器人就无法回答了。

###2.
问题：机器在自动学习能力方面现状如何，未来智能对话能力需要多久能够体现真正的自我学习的智能?” 智能对话并非已编好的场景。但确实目前还很肤浅，其实主要还是用一些sequential model to learn familiar patterns. 我还是认为下一步是对knowledge 的 representation. 有了这个才能真正开始对话（李飞飞）
###3.
“最近看到一种ADMM优化技术，不知道诸位嘉宾对于优化领域的研究成果有什么看法，对于深度学习的严格化分析是不是有重要的影响？谢谢”是的，优化理论对于深度学习的模型训练非常有用。但是，可能需要更多的理论，比如统计和数学上的理论，来更好地深化目前对深度学习的理解。（漆远）

"最近看到一种ADMM优化技术，不知道诸位嘉宾对于优化领域的研究成果有什么看法，对于深度学习的严格化分析是不是有重要的影响" :  there are several recent advances in optimization for deep learning, which believe the (very bad) non-convexity is a "rare" event for large-scale models — thus, possibly, convex techniques such as ADMM could be useful（沙飞）
###4.
各位老师，深度学习的一个重要组成部分是大规模的数据，您们认为数据跟方法哪个更重要一些？如果研究变成了拼数据量的话，那么研究的意义何在？”都重要，引擎和汽油，没有任何一个汽车都跑不动。（李飞飞）
###5.
如何看待大数据在金融领域的应用，分别在信用分析的角度和证券交易的角度？在信用分析上，大数据会变得越来越重要，可以比传统的模型（比如经典的FICO模型）更全面地刻画一个自然人，来建立对他的信用分里理解。（漆远）
###6.
"各位老师，深度学习的一个重要组成部分是大规模的数据，您们认为数据跟方法哪个更重要一些？如果研究变成了拼数据量的话，那么研究的意义何在？"   这是研究爱好和倾向吧 － 我个人喜欢方法一些。可是，大数据量可以 prevent false discovery/claim of methods（沙飞）

如果数据不是问题，那么人工智能能解决80%的问题，可是现在的数据就是问题，大量的非结构化文本，需要进行清理，这种耗时的工作，对于小初创企业该如何解决？”首先我的那个数字猜测是有关普通医疗疾病的，非泛指。这个问题非常好。如果是做科研，我会说从非结构数据中学习是非常好的研究方向。但如果是创公司，建议三思。数据是基础，可以考虑和大公司合作拿数据，或与数据公司合作做好数据。（李飞飞）
###7.
有没有什么对于想在人工智能领域创业的兄弟们一点建议？我相信大家在技术上已经是一身武艺，所以应该聚焦于人工智能之外的东西，忘掉自己是人工智能公司，而是思考自己是解决一个什么问题的公司。（余凯）
###8.
"如何看待神经科学与深度学习？深度学习的新一轮理论突破是否需要关注神经科学的发展？" I am going to say something that is controversial:  I do not believe there is an inherent link between deep learning and neuroscience and whether that link exists is largely immaterial to advancing either AI or machine learning.（沙飞）
###9.
“如果从人工智能创业方面来说，小创业公司可以从什么地方做起？” 可以从“从大公司没覆盖到的pain point 下手”，同时也可以考虑和大公司合做，比如帮助解决大公司的问题来获得大公司的支持甚至收购，或者利用大公司的资源（比如阿里云的计算环境）来加速公司发展。（漆远）
###10.
如何看待神经科学与深度学习？深度学习的新一轮理论突破是否需要关注神经科学的发展？以及神经科学的发展对于未来的强人工智能时代有何推进作用？”好问题[强]我个人大赞推神经生物和认知学。人类的希望还是在对真理的追求中的。不过我认为deep learning和神经生物学相差甚远，过于混淆不是好事。（李飞飞）

雷鸣：那就到此结束，谢谢几位嘉宾了！



