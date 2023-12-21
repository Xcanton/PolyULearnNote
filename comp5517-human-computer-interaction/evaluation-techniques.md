# Evaluation Techniques

## 评估技巧

* 测试系统的可用性和功能
* 发生在实验室、县城和用户的交互
* 评估设计环节和实施过程
* 应该在每个设计生命周期的阶段都给予充分的考虑

## 评估目标

* 评估系统功能的范围
* 评估界面对用户的影响
* 确定具体问题

## Evaluating Design

* Cognitive Walkthrough （认知演练）
  * 通常由心理学专家执行，通过心理学知识对用户可能的行为进行预估，进而识别潜在问题
  * 需要考虑
    * 交互会对用户产生什么影响
    * 需要哪些认知过程
    * 可能会出现哪些学习问题
  * 分析侧重于目标和知识：设计是否引导用户产生正确的目标？
* Heuristic Evaluation（启发式评估）
  * 根据既定的标准或者历史经验的标准，让专家检查是否违反某些准则
* Review-Based Evaluation（给予审查的评估）
  * 用于支持或反驳部分设计的文献结果
  * 需要注意确保结果可以转移到新的设计中
  * 给予模型的评估
  * 认知模型可以过滤设计选项

### Evaluating Through User Participation

* Laboratory Studies（实验室研究）
  * 优点
    * 可以使用专业设备
    * 环境不受到干扰
  * 缺点
    * 缺乏场景
    * 难以观察多个用户间的交互现象
  * 适用场景
    * 单用户系统或者让用户提前体验系统是不切实际的时候
* Field Studies（实地研究）
  * 优点&#x20;
    * 处于自然环境中
    * 保留场景的信息（尽管可能随时间改变）
    * 可以进行纵向研究
  * 缺点
    * 干扰多
    * 噪声
  * 适用场景
    * 对纵向研究至关重要的时候

## Evaluating Implementations

* 对交互行为特定方面的受控评估
* 评估者选择要测试的假设
* 一些实验条件是仅考虑某些受控变量的值上的不同
* 行为测量的变化归因于不同的条件
* 实验因素（变量）
  * 受试者（Subjects）
  * 变量（Variables）
    * Independent Variable（自变量）
      * 产生不同条件（characteristic changed to produce different conditions）
    * Dependent Variable（因变量）
      * 实验中测量的特征（characteristics measured in the experiment）
  * 假设（Hypothesis）
    * 结果预测
    * 原假设
      * 假设条件之间没有差异
      * 需要反驳这个假设
  * Experimental Design
    * 组内设计（Within Groups Design）
      * 每个受试者在美中条件下进行实验
      * 可以进行学习迁移
      * 成本较低，并且不太可能收到用户差异的影响
    * 组间设计（Between Groups Design）
      * 每个受试者仅在一种条件下进行
      * 无需进行学习迁移
      * 需要更多的用户
      * 变化可能会导致结果出现偏差（basis）
  * 注意：群体间存在巨大差异

## Observational Methods

* Think Aloud (大声思考)
  * 观察用户执行任务的过程，并且让他说出what、why、how
  * 优点
    * 简单，不需要什么专业知识
    * 可以提供有用的见解
    * 可以显示系统的实际使用方式
  * 缺点
    * 主观性
    * 选择性
    * 描述行为可能会改变任务的表现
* Cooperative Evaluation（合作评价）
  * Think aloud的变种
  * 用户和评估者都可以在整个过程中相互提问
  * 新增的优点
    * 限制更少并且更容易使用
    * 鼓励用户批系统
    * 可以进行任务或问题的解释
* Protocol Analysis（协议分析）
  * 可以分析的内容
    *   纸笔记录

        便宜，但是受限于书写速度
    *   音频

        适合think aloud，难以与其他方式匹配
    *   视频

        准确、真是，但是需要特殊设备，且有干扰性
    *   计算机日志

        自动且不干扰实验进行，但是大量的数据难以分析
    *   用户笔记

        粗略且主观，但是能够提供有用的见解，有利于纵向研究
  * 实验中通常混合使用
  * 视频和音频使用困难，且需要一定的技巧
  * 可以使用一些自动化的工具辅助
* Automated Analysis（自动分析）
  * Workplace Project
  * Post-task Walkthrough
    * 用户在事件发生后对操作做出反应
    * 用户填写意向
  * 优点
    * 分析师有时间专注于相关的事件
    * 避免任务中图被干扰
  * 缺点
    * 缺乏新鲜感
    * 有可能是事后解释，存在幸存者偏差（basis）
* Post-Task Walkthroughs（任务后演练）
  * 将记录回放给参与者，并让他们评价
    * 及时性
    * 延迟性
  * 有助于确定行动和替代方案的原因
  * 在无法出声思考的情况下是必要的

## 采访技巧

* Interviews
  * 分析师通常根据准备好的问题一对一地向用户提问
  * 非正式、主观且相对便宜
  * 优点
    * 可以根据具体情况变化
    * 可以更全面地讨论问题
    * 可以引发用户意见并识别未预料到的问题
  * 缺点
    * 非常主观
    * 耗时
* Questionnaires
  * 想用户提供一组固定的问题
  * 优点
    * 速度快
    * 覆盖用户群体大
    * 可以更严格地分析
  * 缺点
    * 灵活性差
    * 更少探测问题
  * 需要精细设计
    * 什么信息是必须的
    * 如何分析答案
  * 问题类型
    * 一般性的
    * 开放式的
    * 标量
    * 多选题
    * 排名

## Physical Analysis

* Eye Tracking
* Physiological Measurement

## 可穿戴设备

* 好处
  * Superpower Enhancements（超强的功能）
  * Sensing（传感）
  * Proactive Action（积极行动）
  * Instant Interaction（实时互动）
* 坏处
  * 需要考虑人体工程学
  * 影响注意力
  * Social Weight
    * 认知加载：是否容易认知
    * Physical Presence
    * 社交方便性

