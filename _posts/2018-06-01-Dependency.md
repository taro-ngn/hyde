### Why is it important to understand how Tensorflow controls its computational flow?

TL;DR: Well, because one of the most important features of Tensorflow is to execute distributed programming. And the distributed programming’s main motivation is how to control computational tasks effectively.

Unlike sequential programming, in distributed programming, a computational processor unit (CPU) is supposed to do many computational tasks at the same time. This concept is now widely accepted. But back in the days and during the premier phase of every student, this isn’t something really straightforward. For example, it raises some questions like How computer distributes its tasks? How can it handle conflict? And even some relatively interesting concept appears like ‘dead-lock’.

In programming, there are many software and libraries that are able to handle this tasks like Hadoop, MapReduce, etc. Tensorflow might be regarded as one of these, in the sense that it facilitates the task distribution. What makes Tensorflow different is that it’s a higher-level programming interface. With Tensorflow , we can be less careful about how the low-level code works, but instead mainly focus on how the computational flows run.

Nevertheless, as mentioned about, Tensorflow always concerns task distribution. Even though we are levitated from a massive low-level programming burden, it’s always an obligation to carefully code so that the program works fine. This’s always the case as senior programmers are supposed to do sophisticated tasks, not just stay with basic programs.

What is my last doubt with Tensorflow ?
It’s always confusing to me how Tensorflow distributes computational tasks. We have many codes to run a program, just at which procedure does Tensorflow use parallel programming to perform its magic? Furthermore, how to makes sense of the operator ‘control_dependency’ in tensorflow ?

By doing a quick search on documentation, I now understand. First about how tensorflow works, and second how I can optimize my code.

### So, how Tensorflow works?

Well, when a program (written in Python) , every code is executed sequentially. The program runs sequentially as usual until it meets a code demanding an operator in Tensorflow to be executed. When this happens, all the computations concerning this operator are executed OUTSIDE the current code flow of a program. These computations are executed parallelly (thanks to Tensorflow). When all the computations are finished, the flow of code in the initial program continues.

### Why does one need control_dependency in Tensorflow ?

Because one cannot be sure that the order of computations always matches their expectation. In order that it happens, contrl_dependency must exist as a guideline for Tensorflow. To optimize, one can utilize ‘partial_run’ and ‘control_dependency’ method in Tensorflow.

### Answer that erases my doubt ?
Each time Session.run() runs, only the subgraph of concerning operators runs, and its runs only once.
