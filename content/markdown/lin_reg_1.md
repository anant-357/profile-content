### Motivation
We want to **predict** *something*. Our approach depends on this *something*.

## General Approach
input: **X** <br/>
output: **Y**

We divide the process into 3 parts, *training*, *testing* and the actual *usage*.

### Training

What are we training? -> a *model* or simply a **function**, say **f**. We want to pass our input, **X**, into **f** and get **y**. If I have rainfall data of the past month or year of a certain place, I can expect the function to output the amount of rainfall for tomorrow. But would our expected output always be a number? What if I want to know whether the picture I'm giving as input is of a dog or a cat? A 'dog' or a 'cat' is not a number. We will find out how to handle this later.

If **y** matches **Y**, then we can say that the function is trained.
<center> <b>f</b>(<b>X</b>) = <b>y</b> == <b>Y</b> </center>

But where do we start with **f**. Well, the simplest function (except constant) we can think of is the linear function i.e.
<center> f(x) = m*x + c </center>

Now we have a function to work with. What can we change in this function so that it gets trained? x is passed to the function, that leaves **m** and **c**. These are called the **trainable parameters** of the *model*.
