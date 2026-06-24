---
title: "Problem Solving Through Programming"
date: 2026-04-07
categories: [Blogs, PF_blog]
tags: [Journey, UET Faisalabad, Computer Engineering, Problem Solving, Python, Learning]
---

# Problem Solving Through Programming

There is a difference between writing code that works and actually understanding why it works, and this semester taught me that difference the hard way. Early on in Programming Fundamentals, I was content to copy the structure of example programs, change a few variable names, and call it done. It usually worked, but only because the problems were simple enough that imitation was enough to get by. As the assignments grew more involved, that approach stopped being good enough, and I had to learn how to actually think through a problem instead of pattern-matching my way to a solution.

The shift happened gradually through repeated exposure to loops and conditional logic. Loops, in particular, were the concept that finally made programming feel less like writing instructions and more like designing a process. The first time I genuinely understood a for-loop, it was almost a small revelation: instead of writing the same line of code three times to ask a user for three numbers, I could write it once and let the computer repeat it for me. It seems obvious in hindsight, but at the time it changed how I looked at every problem afterward — I started asking myself "is there a pattern here that repeats?" before writing a single line.

One exercise that stuck with me involved taking multiple numbers from a user, checking whether each one was even or odd, and keeping a running total. It is a small program, but it combines several pieces that have to work together correctly: a loop to repeat the input process, a conditional check inside that loop, and a variable that accumulates a result across iterations.

```python
def check_numbers():
    total = 0

    for i in range(3):
        num = int(input(f"Enter number {i+1}: "))

        if num % 2 == 0:
            print(f"{num} is Even")
        else:
            print(f"{num} is Odd")

        total += num

    print(f"Total sum: {total}")

check_numbers()
```

What made this exercise valuable was not the final result, but the number of small mistakes I made while building it. At one point I initialized the total variable inside the loop instead of outside it, which reset the sum back to zero on every iteration and gave me a clearly wrong answer. Finding that bug forced me to slow down and trace through the program line by line, asking exactly what value each variable held at every step. That kind of careful tracing turned out to be one of the most transferable skills from the entire course — it is the same mental process I now use whenever a program does not behave the way I expect, regardless of how complex the code is.

Debugging, more than writing correct code on the first try, is where I think most of my real problem-solving ability developed this semester. Every error message I encountered was, in its own way, a small puzzle. Some were easy — a missing colon, a misspelled variable name. Others took much longer to track down, especially logical errors where the program ran without crashing but still produced the wrong output. Those logical errors are the ones that actually teach you something, because there is no shortcut; you have to genuinely understand the flow of the program to find them.

I also noticed that breaking a problem into smaller pieces made even intimidating assignments feel manageable. Instead of looking at a full assignment description and feeling overwhelmed, I started asking what the very first small step would be, solving just that step, and then moving to the next one. This approach of decomposing a problem before writing any code at all is something I did not appreciate at the start of the semester, but I now consider it more important than knowing any particular syntax. Syntax can always be looked up; the ability to break a vague problem into solvable pieces cannot be looked up in the same way.

Working through these exercises also gave me a better appreciation of how programs actually execute, step by step, rather than as a single static block of text. I started mentally running through code the way the computer would — entering a loop, checking a condition, updating a variable, looping back — instead of just reading it top to bottom once. That mental model of execution is, I think, the real foundation that the rest of Computer Engineering will build on, whether the next course is about databases, circuits, or anything else.

Looking back at this part of the semester, I can clearly see how much my approach to problems changed. The student who once panicked at a wall of red error text is, by the end of the course, someone who can sit down, trace through a problem calmly, and find the one line that is behaving unexpectedly. That confidence did not come from any single lecture; it came from repeatedly facing small problems, getting them wrong, and working through why, until the process of debugging itself stopped feeling like failure and started feeling like a normal, even satisfying, part of writing code.
