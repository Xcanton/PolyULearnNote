# Communication Techniques

## 面部表情识别（Facial Expression Recognition）

* 应用场景：疼痛检测、抑郁症、欺骗、微表情培训等
* How do we measure facial expressions?&#x20;
  * 六种基本的情感
    * Anger 愤怒
      * Fear 恐惧
      * Disgust 恶心
      * Suprise 惊喜
      * Happiness 快乐
      * Sadness 悲伤
  * FACS： Facial Action Coding System
  *   维度方法（Dimensional Approaches）

      <figure><img src="../.gitbook/assets/image (94).png" alt=""><figcaption></figcaption></figure>

      * Face Registration（人脸向量化）
      * Geometric Features（几何特征）
        * 人脸检测（Face Detection）
        * 特征检测（Landmark Detection）
        * 特征点距离（Calculate geometric distance between feature points）
* 面部识别的算法
  *   静态算法（Static Modeling）

      帧是相互独立的

      * 支持向量机
  *   动态建模

      帧被分割成序列

      * 隐马尔可夫模型

## Our Interests in Computer Vision

* Human-Computer Interaction (HCI)
* Find People and Their Body Parts
  * Limbs
  * Heads
  * Faces
* Wired Full Body Interfaces
* 2D Vision-Based Systems
* 3D Body Tracking

## Gesture Recognition

* 为什么姿势识别很困难？
  * 背景多变
  * 多样的阴影
  * 衣着不同
  * 手和腿界限不一定清晰
  * 存在遮挡
* 解决方案一：两台摄像机（Video-Rate Stereo）
  * Estimation Disparity propositional to depth
  * 估算深度有助于
    * segmentation
    * 形状刻画
    * 姿势跟踪
  * 实时地实施方案可以很快地商业化
*   What is a gesture in HCI？

    在交流中发挥作用的有意肢体动作

    * Gestures are not always communicative（盲人）
*

    <figure><img src="../.gitbook/assets/image (95).png" alt=""><figcaption></figcaption></figure>



    *   动作捕捉（Motion Capture）

        将你的动作数字化

        * Activate Sensors（有源传感器：加速器、陀螺仪等）
        * Passive Sensors（被动传感器： 相机）
    * 特征提取（Feature Extraction）
      * 输入信号通常是高维信号
      * 使原始输入更加紧凑、更易于解读
    * 序列分析（Sequence Analysis）
      * 解读输入的功能
      * 主要实现以下三种功能：
        * 姿势分类（Gesture Labeling）
        * 姿势语义划分（Gesture Segmentation）
        * 姿势检测（Gesture Spotting）
          * 有意的姿势
      * 该部分问题都归结于序列标注问题，并使用机器学习算法进行求解
      * 可能是时序或者非时序的模型
* 其中一个子问题是： 身体姿态估计（Body Pose Estimation）
  * 可能通过树的方式加入人工规则，对部分识别过程分解成不同身体部分的动作判别

<figure><img src="../.gitbook/assets/image (96).png" alt=""><figcaption><p>The Kinect pose Estimation Pipeline</p></figcaption></figure>

* 另一个子问题是物体识别（Object Recognition）

