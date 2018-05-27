

If you learnt ML, did you spend hours sitting in front of your computer, trying different hyper parameters and tuning them in and out in order to make your model converge ? Then the training result was bad ? I did and I was quite frustrate.
One time, my training loss didn't go below 2.0 while my classmates effortlessly achieved 0.5 . They even asked teacher why training process had been so easy.

I encountered this problem while training a script generator model. To understand this, I did some paper researches, I looked at my classmates' code, compared theirs with mine. Then I rediscovered that :

> Adam doesn't guarantee a better result than a simple SGD optimizer. It's how you tune it that matters.

Why is that ? I think all of important points are already mentioned in a paper of Yoshua Bengio [1]

It was implicitly mentioned in a paper of Yoshua Bengio[1], yet the paper didn't explain the relation between intial learning

The first one is about the initial learning rate. To avoid reinvent the wheel, I wouldn't repeat what is well explained by Mr. Bengio in his paper. I only would like to explain why 'decaying learning rate' practice cannot compensate this problem and why we should care.

> And big initial learning rate makes that guess useless.

Initial weights of our model are our first guess. We care about the first guess because we want to avoid 'bad local minimums'. Needless to say, if our model falls in 'bad local minimum' region, training schedule can hardly help it. Big initial learning rate makes that guess useless. That's why we should reinitialize model if we deem it's in bad region.

> we should reinitialize model if we deem it's in bad region

Secondly, Adam optimizer is not so good.  It's not so good because of its strong point: Well-designed for stochastic training practice, taking in account of momentum. Its design make it possible that for a bad big initial gradient can affect adversely the model in many steps after.[3]


>...[Implementation of Adam's optimizer[2]]<br/>
>$m_t \leftarrow \beta_1 m_{t-1} +(1-\beta_1) g_t$ <br/>
> $v_t \leftarrow \beta_2 v_{t-1}  +(1- \beta_2)g_t^2$ <br/>
> ...

In sum, as far as my experience, to find a good set up to train a learning model, it's worth having a good understanding on both your model and your optimizer. By understanding, I mean to grasp how each code block works, what are the expected training results, how the model's optimizer updates weights, etc.


[1] https://arxiv.org/pdf/1206.5533.pdf

[2] https://arxiv.org/abs/1412.6980

[3]: I found out that Tensorflow does save optimizer's weights, then I suspect that 'reintialize optimizer' may be a good pratice after each time the learning rate decays , but I didn't test that idea.
