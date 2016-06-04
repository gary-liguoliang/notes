---
layout: post 
title: 我所理解的敏捷开发 My Understanding of Agile Development
tags:
- agile-敏捷开发
---

小时候我有一条农家田园犬，它在院子里左冲右突，上窜下跳，我觉得它很‘敏捷’。 后来某一个秋天的雨后，我在清澈见底的小河边看水里的鲤鱼，
流畅，灵活，十多年后我变成了一个码农，不幸的是我从来没有觉得自己在软件项目里‘敏捷’过。 

聊聊我所理解/经历的敏捷。

### 几乎所有的团队都声称"敏捷"

当然, 很多团队所指"敏捷"大概只是有"站立式会议", 有一个固定的发布周期，使用JIRA，CI等工具.

### 变更 / Change

我曾经参与过一个某银行内部开发的Python项目, 有一些unittest, 可惜的是很多只为为了凑coverage. 老板要求code coverage达到80%, 
那就凑到80%... 有的unittest会连接到SCM里读Log, 还有的unittest通过与否是通过读取log.production code里充满了各种各样欺诈性
的函数, 譬如verify_config(config)返回的不是true/false/exception, 
而是解析出来的config object，总之，不管是unitest还是production code，到处都是坑。 
所以没有人愿意(敢)改动这样的代码. 由于没有任何integration test, 开发人员心里更加没底.
一旦需要改动, 会让新版本在一个production parallel环境里跑上两三周，跟production的数据(人工)对比，满意后才敢上线。

有为了节省production parallel的测试时间，有时我们会把多个改变放在一个测试里一起跑，在一个周期里要测试跟发布的变更增多, 导致测试发现的问题更多, 发布时间一拖再拖.

**我们声称我们是敏捷团队.**

我的第一个User story很简单, 增加一个非常小的功能, production代码改动大概有10行. unittest也很简单直观. 
在开始之前, architect team挑战我如何确定我的改变不会影响现有的功能? 在没有自动化测试的情况下, 我怎么能确定? 
我能确定的是我增加的功能可以正常运转, 可我不能保证其他的'坑'.
如何测试? 这是个问题. 当然我没有问他们production里的这堆垃圾是怎么发布进来的. 

[problem is "a kaizen (continuous improvement) opportunity in disguise."](http://www.toyota-global.com/company/toyota_traditions/quality/mar_apr_2006.html)
为什么没有integration test? 于是我根据自己的了解写了一堆Gherkin feature，然后放到Jenkins去跑. 由于坑太多, 即使跑过integration test还是会照旧放到production parallel环境
里double check几天. 

这样的项目能坚持下来已经不错, 离'敏捷'还很远. 我相信只有足够坚挺的自动化测试: unittest, automated integration test才能支撑变更, 
否则的话, 怎么敢说ready for release? 

### 用户 / User

大多数变更需求来自用户，所以在开始之前就要明确用户碰到了什么问题，了解问题跟用户的痛点，再提出解决方案。

多年前在上海，我犯了一个**错误**，牙齿在吃坚果时掉了一块，有些晃动，在跟牙医简单描述了状况之后，我啰嗦了一句, 是不是需要拔掉？
医生没有问别的，30分钟后拔掉了我一颗半牙齿，后面的半块因为太牢固而放弃(几年后在新加坡割开牙龈才把那块牙齿取出).
我们没有很多牙齿跟时间可以浪费，我相信这辈子我再也不会去这家诊所了. 错误在我身上, 作为一个不懂牙齿的人提出了坚决方案，
牙医在病历上写道: `主诉拔牙`. 

不要假设你的用户更了解需求/系统，也不要假设你的客户说的都是正确的，他们有时候把表面现象当作了事实。[The Expert (Short Comedy Sketch)](https://www.youtube.com/watch?v=BKorP55Aqvg)

在有些奇葩的团队里，会有些开发人员觉得自己可以替客户提出需求而在backlog里增加变更以取悦用户。 当你打算开始这样的任务，最好问清楚几个问题：
 - 要解决什么问题, 带来什么好处?
 - 谁提的需求
 - 谁来做UAT
然后直接去找用户确认acceptance scenarios.

如果根本找不到用户根本不在意，那最好不要开始。

### 发布 / Release

坚挺的测试保证我们时刻准备着发布，尽早发布，尽早的获得用户的反馈，然后挪到下一个任务，跑起来。

可惜的是, 很多公司发布的成本很高, 譬如需要提早一周准备发布的ticket, 如果需要其他的团队配合, 那就更悲剧了: DBA需要提前三天, 
SA需要提前五天, 然后还要兼顾每位同事的时区, 发布前要准备发布(release)计划跟回滚计划(rollback)计划, 
然后还要催ticket里所有的approver批复请求. 哪位同事愿意谁来处理下一个发布? 

看似复杂的流程, 其实都是枯燥无味的机械操作, 我想大概只有自动化才能解决这些问题. 
如果前面所说的测试都已经足够坚挺的来支持即将发布的产品，那何不直接发布呢？
即使不能随时发布, 但也可以定时到某一个时间点, 让机器来自动化的处理发布/回滚。

 
### 结论 / Conclusion
我所期待的敏捷:

自动化的测试保证产品质量, 快速的发布/回滚, 尽早的联系用户确认需求并获得反馈.
