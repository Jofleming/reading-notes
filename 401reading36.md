# DSA Review

## Whiteboard Advice

[Reading](https://hackernoon.com/the-best-whiteboard-interview-advice-i-ever-received-3ebbfa72e4a)

First piece of advice is communicate. First restate the question and seek affirmation. There is no way that restating the question will hurt you. Then take the time to ask about edge cases. This shows you are analytical and will work hard to prevent bugs. Then finally ask if there are any test cases your function should pass.

Again, you don’t actually want to start writing code in an actual language. You’ll find yourself constrained by trying to remember the methods or other idiosyncrasies of the language rather than trying to come up with the correct logic. Instead, let your interviewer know you’re going to start by writing pseudocode and fill in the actual code later. (Coincidentally, this is a reasonable way to write actual code as well).

The example shows them writing commented out sentences as their psuedo code. You can do this and then don't even get rid of the doc strings. It explains what your code is doing and can also help if you get stuck.


## 6 tips

[Reading](https://medium.com/@steve_45636/6-tips-to-ace-a-whiteboard-programming-interview-f06c1b378bc6)

First is to take time. It is insanely hard to think and talk at the same time. Repeat the problem, ask for any edges/test cases/clarification. Then let them know you need a moment to think. When you have an idea come back and explain.

After that actually write down the steps of the solution.

Write pseudocode first.

Don't sweat the small stuff. Programming interviews are not about how well you’ve remembered your semicolons, nor are they about being able to remember all of the flags on a TCP packet. They’re about demonstrating depth and breadth of knowledge, personality strengths, and problem-solving abilities. If you make a mistake, it’s okay. Brush it off and move on.

If you can’t remember something like this, it’s often acceptable to say that you’d look it up.

A programming interview isn’t just a written exam. It’s an assessment of your programming abilities, and there are plenty of things that fall into that category beyond mere coding prowess. For example:

* Are you able to express your ideas and solutions clearly and effectively?
* Do you treat the interviewer with respect?
* How do you accept criticism (technical, constructive or otherwise)?
* Are you able to collaborate with others to come up with solutions?
* Do you communicate in a way that demonstrates empathy?
* Are you honest (especially about yourself)?

If you are given criticism in an interview, you need to take it and be grateful for it. No snide remarks, no “oh, I was gonna do that in a second anyway”, no anger or raised voice. The interviewer has their opinion, and they didn’t have to share it — they could’ve just written it down silently and rejected you as a candidate later. They’ve given you a chance to correct course because they think you’re worth it, and they’ve extended an opportunity for you to demonstrate how you accept feedback from your peers. Don’t waste it.

### Review your work

You won’t always finish questions in the time permitted, but occasionally you’ll have extra time after coming up with a solution. If this happens, it’s tempting to say “Well, I’m done!”. Interviews are stressful and we want them to be over as fast as possible. This is reasonable, but:

Think about how silly you look if your solution is not right.

Instead, if you have the time, review your code as you would in a peer review. Show the interviewer that you are committed to producing accurate, high-quality work, and that they can trust you to do so without being prompted.

In particular, focus on these two areas, as they receive heavy scrutiny in interviews:

* Algorithmic efficiency. Have you found the fastest and most optimal solution given the requirements? Take some time and consider other approaches. It’s worth noting two things here: 1) If the problem involves a sorted dataset, you can bet your pants there’s a solution involving ` O(log(n)) lookup time (even if there’s additional cost, the total complexity will still contain the log(n), for example, O(n * log(n)) if iterating over an array, as sorting algorithms do), and 2) For a disgustingly large number of programming interview questions, the answer involves a hash table and O(1) lookup time — so if you’re seeking a better algorithm, try a hash table.
* Correctness. Sure, you’ve solved for the simple, easy use case, but have you checked for edge cases? Off-by-one errors? Issues with negative numbers or empty arrays or missing keys or strings with weird patterns of characters? Maybe you won’t find all of them, but failing to at least LOOK for edge cases before declaring your solution to be correct is a pretty hefty mistake in an interview.

## Engineering Interview Process Deconstructed

[Video](https://www.youtube.com/watch?v=KdXAUst8bdo)

The interview should be more about the thought process and not the correct answers. 

[Back](README.md)