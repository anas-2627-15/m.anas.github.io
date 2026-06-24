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
