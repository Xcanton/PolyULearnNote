# Chapter6 Information Systems

## MF vs MLP

* MF 使用内积（inner product）来刻画交互的过程（interaction function）
  * latent factors需要相互独立
  * 经验上来说，在CF modeling上有较好的generalization ability
* MLP使用nonlinear functions来学习交互特征（interaction function）
  * Latent factors are not independent with each other
  * The interaction functions is learnt from data, which theoretically has a better representation ability
  * However, its generalization ability is unknown and it is seldom explored in recommender literature/challenge.
