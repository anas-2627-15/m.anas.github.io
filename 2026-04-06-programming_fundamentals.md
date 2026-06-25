---
title: "Programming Fundamentals"
date: 2026-04-06
categories: [Blogs, PF_blog]
tags: [Journey, UET Faisalabad, Computer Engineering, Programming, Python, Learning]
---

# Programming Fundamentals: Where Everything Began

Every Computer Engineering student has a course that feels like the real starting point of their journey, and for me that course was Programming Fundamentals. Before this semester, I had read about programming, watched a few videos out of curiosity, and assumed I had a rough idea of what it involved. The first week of actual lectures and lab sessions proved me wrong almost immediately. Writing a program, it turns out, has very little in common with watching someone else write one.

The first few classes were spent on the basics — variables, data types, simple input and output. It sounds simple when written down like this, but at the time it felt overwhelming. I remember spending an embarrassing amount of time trying to figure out why a program would not run, only to realize I had forgotten a colon or mismatched an indentation. Python is supposed to be a forgiving, beginner-friendly language, and it is, but it still has no patience for small mistakes. Every error message forced me to slow down and actually read what I had written instead of assuming it was correct.

As the semester progressed, we moved into conditional statements and loops, and this is where programming started to feel less like memorizing syntax and more like solving small puzzles. I began to enjoy the process of taking a vague requirement — something like "give a discount based on age" — and breaking it down into a series of logical steps a computer could follow exactly. One of the programs I am most proud of from this period is a discount calculator I built during lab work. On the surface it looks like a simple exercise, but it actually combines several layers of logic: it asks for a name and age, applies different discount percentages depending on the age group, and then adds an optional lucky draw feature for adults that adjusts the discount further based on whether their age is even or odd.

```python
def calculate_discount():
    name = input("Enter your name: ")
    age = int(input("Enter your age: "))
    amount = 1800

    if age >= 18:
        discount = 20
    elif 13 <= age <= 17:
        discount = 10
    else:
        discount = 5

    if age >= 18:
        choice = input("Enter lucky draw? (yes/no): ").lower()
        if choice == "yes":
            if age % 2 == 0:
                discount += 10
            else:
                discount += 5

    final_amount = amount - (amount * discount / 100)

    print(f"{name}, Discount: {discount}%")
    print(f"Payable Amount: {final_amount}")

calculate_discount()
```

What I appreciated most about writing this program was how it forced me to think about edge cases. What happens if someone enters an age below thirteen? What if an adult declines the lucky draw? Each small decision in the code had to account for a different real-world possibility, and getting all of those branches to behave correctly taught me more about conditional logic than any lecture slide could have. This code is available on my GitHub repository for anyone who wants to see the full implementation.

Beyond the discount calculator, the course also introduced me to functions, which completely changed how I approached writing programs. Before learning about functions, my code tended to be one long block of instructions, repeated wherever I needed the same behavior again. Once I understood how to wrap logic into a reusable function, my programs became shorter, easier to read, and far less error-prone. I no longer had to copy and paste the same block of code in three different places and hope I had updated all of them consistently when something changed.

Lab sessions played a much bigger role in my learning than I expected going in. Lectures explained the theory, but it was the hands-on lab time, with a teaching assistant walking around answering questions, that actually cemented the concepts. I learned just as much from my own mistakes during labs as I did from the correct examples shown in class. Debugging a program that almost works, but not quite, is in some ways a better teacher than writing a correct program on the first attempt, because it forces you to understand exactly why something is failing.

Programming Fundamentals also happens to be one of the two courses taught by Dr. Bilal Ahmad this semester, and his way of explaining logic — starting from a real problem rather than an abstract rule — made it easier for many of us to connect the syntax to something practical. It is one thing to be told what an if-else statement does; it is another to be walked through why a real program, like a discount system, actually needs one.

By the end of the semester, the gap between the student who struggled to print "Hello, World!" correctly and the one who could design a multi-condition discount calculator felt enormous, even though it happened gradually rather than all at once. That is probably the biggest lesson Programming Fundamentals taught me: progress in programming rarely feels dramatic week to week, but it adds up quietly until one day you realize you can build something you could not have imagined writing a few months earlier.

This course did not just teach me Python syntax. It taught me how to think in steps, how to test my assumptions instead of trusting them blindly, and how to be comfortable with being wrong dozens of times before getting something right. Those habits, more than any single piece of code, are what I am carrying forward into every course and project that comes after this one.

Looking back at the very first program I ever submitted for this course — a short script that printed a greeting and asked for the user's name — it almost feels like it was written by someone else. The hesitation in that code, the unnecessary repetition, the lack of any real structure, all stand out clearly now that I have a few months of practice behind me. That contrast is exactly why I think early assignments are worth keeping rather than deleting once they are graded; they are the clearest evidence of growth that exists, far more convincing than any grade on a transcript.

One habit I picked up almost by accident, simply from repeating the same kind of debugging process over and over, was reading error messages slowly instead of skimming them in frustration. Early on, an error felt like a wall — something to be annoyed at and clicked past as quickly as possible. By the middle of the semester, an error felt more like a clue, often pointing almost directly at the actual problem if I bothered to read the full message instead of just the first line. That single change in attitude, from treating errors as obstacles to treating them as information, probably saved me more time over the semester than any specific trick or shortcut I learned.

I also started noticing how much my code style changed without me deliberately trying to change it. My early programs were long, repetitive, and hard to follow even for me a day after writing them. By the time I built the discount calculator, I was naturally breaking logic into smaller, named pieces, adding short comments where the reasoning was not obvious, and choosing variable names that actually described what they held instead of single letters left over from a rushed first draft. None of this was taught explicitly as a rule; it emerged simply from writing enough code to feel, almost physically, when something was getting too tangled to follow.

If there is one thing I would tell a new student starting Programming Fundamentals next semester, it would be this: the discomfort of not understanding something immediately is not a sign that programming is not for you, it is simply what learning to program actually feels like for almost everyone at the start. The students who get good at it are not the ones who never struggle, but the ones who keep writing small programs anyway, mistake after mistake, until the struggle quietly turns into confidence.

Looking back at my very first attempts, I can see how much of my early frustration came from expecting to understand everything immediately. I wanted a program to work the first time I ran it, and when it did not, I treated that as a sign I was doing something fundamentally wrong rather than as a completely normal part of writing code. It took several weeks of repeated, sometimes tedious practice before I accepted that errors are not a verdict on ability — they are simply information, telling you exactly where your mental model and the actual behavior of the program diverge. Once I stopped taking error messages personally and started reading them as clues, the entire subject became far less stressful.

Another thing I did not expect going into this course was how much it would change the way I read instructions in general, not just programming assignments. Writing a program forces you to be painfully precise about what you mean, because a computer will not fill in the gaps the way a person reading a vague sentence might. That habit of precision started leaking into how I approached lab reports, assignment instructions in other courses, and even how I explained things to classmates. Programming Fundamentals, in that sense, taught me something closer to a general discipline of clear thinking, with Python simply being the language I happened to practice it in.

I also want to note how much the structure of the course mattered. Concepts were introduced in a deliberate order — variables before conditionals, conditionals before loops, loops before functions — and each new idea leaned directly on the one before it. I did not always appreciate that scaffolding while I was inside it, but looking back at the full sequence now, it is obvious how carefully it was designed to build confidence gradually rather than overwhelming a beginner with everything at once. That ordering is something I now try to apply myself whenever I am learning something new outside of class, breaking a big unfamiliar topic into the smallest pieces I can manage first.
