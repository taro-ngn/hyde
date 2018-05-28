
Tuning up your optimizer can be regarded as a small step in model training. Nevertheless, this job can become quite delicate, require understanding on different aspects of your problems. In this post, I want to focus on the intimate relation between 'initial learning rate' of Adam optimizer and 'weight initialization'.

Let's talk first about weight initialization . Given an optimization problem , initial weights can be regarded our first guess. If your optimization problem is convex- that means the gradient of your cost function will always point to the same optimal region of optimal parameters-, our first guess is not really important. By 'important' I mean it won't affect the eventual performance of the underlying model, then only thing that make us worry when choosing the initial weights is that 'bad weight initialization' can lead to long training time. In sum, with good 'learning schedule' we can always compensate that problem.

However, the problem is not same if our optimization problem has way many local minimums. At that time, they should be classified in 2 groups : 'good local minimums' and 'bad local minimums', and interestingly points in each of previous groups are likely to be clustered together. We can somehow call them 'bad region' and 'good region'. In this case - which is also the most probable case in practice, the initial weights is the most important factor that decides whether our model will fall in 'bad region' at the training or not.

I would like to emphasis that if a model is stuck in a 'bad region' (with bad local minimums), they cannot get out of it if we don't increase the learning rate high enough. However, the beginner mistake is that they don't realize it, and they use 'decaying learning-rate ' to find the best possible local minimum. Yet the best local minimum amongst the bad ones cannot beat a good local minimum (by definition).

So then, why the initial learning rate is important ? Well, it's important because it is the first thing decides the fist gradients come to interact with the initial weights. A too big initial learning rate makes our first guess obsolete, i.e , our careful choice of weight initialization means nothing and we lose our only control over the 'region' of which our model starts. This problem is noteworthy because it's the common beginner mistake.


[
