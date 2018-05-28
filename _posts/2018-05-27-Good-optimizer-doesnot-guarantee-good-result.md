

If you learnt ML, did you spend hours sitting in front of your computer, trying different hyper parameters and tuning them in and out in order to make your model converge ? Then the training result was bad ? I did and I was quite frustrate.
One time, my training loss didn't go below 2.0 while my classmates effortlessly achieved 0.5 . They even asked teacher why training process had been so easy.

I encountered this problem while training a script generator model. To understand this, I did some paper researches, I looked at my classmates' code, compared theirs with mine. Then I figured out once again that:

> Adam doesn't guarantee a better result than a simple SGD optimizer. It's how you tune it that matters.

I suspect that I was blind of that fact, because of the way Deep Learning is conveyed in Udacity course. Throughout that course, most of concepts in Deep Learning are just mentioned briefly, and are not well detailed. Some explanations and successful result from Course Projects make me, and probably others students, feel confident of their knowledge on this matter. But yet, needless to say, it's not true.

I don't blame the instructors of that course for that fact. It's expected to happen, and that's what we see in all introductory courses.

Back to my problem, it turned out that I didn't understand how Adam optimizer updates weights and work jointly with other set up of the model - like weights for examples. Then, I chose the initial learning rate carelessly, which made my model diverge. Then eventually, my model slipped out 'good region' , fell into a no-turning point. From then, the performance of my network was stuck.

Personally, I took this experience as a great lesson to learn from. Luckily that I happened to me soon enough.
