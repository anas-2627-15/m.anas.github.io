---
title: "Problem Solving Through Programming"
date: 2026-04-07
image:
  path: /assets/img/posts/1.jpg
categories:
  - Course Learning
tags: [Journey, UET Faisalabad, Computer Engineering, Problem Solving, Python, Learning]
---

# Problem Solving Through Programming

There is a difference between writing code that works and actually understanding why it works, and this semester taught me that difference the hard way. Early on in Programming Fundamentals, I was content to copy the structure of example programs, change a few variable names, and call it done. It usually worked, but only because the problems were simple enough that imitation was enough to get by. As the assignments grew more involved, that approach stopped being good enough, and I had to learn how to actually think through a problem instead of pattern-matching my way to a solution.

The shift happened gradually through repeated exposure to loops and conditional logic. Loops, in particular, were the concept that finally made programming feel less like writing instructions and more like designing a process. The first time I genuinely understood a for-loop, it was almost a small revelation: instead of writing the same line of code three times to ask a user for three numbers, I could write it once and let the computer repeat it for me. It seems obvious in hindsight, but at the time it changed how I looked at every problem afterward I started asking myself "is there a pattern here that repeats?" before writing a single line.

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

What made this exercise valuable was not the final result, but the number of small mistakes I made while building it. At one point I initialized the total variable inside the loop instead of outside it, which reset the sum back to zero on every iteration and gave me a clearly wrong answer. Finding that bug forced me to slow down and trace through the program line by line, asking exactly what value each variable held at every step. That kind of careful tracing turned out to be one of the most transferable skills from the entire course it is the same mental process I now use whenever a program does not behave the way I expect, regardless of how complex the code is.

Debugging, more than writing correct code on the first try, is where I think most of my real problem-solving ability developed this semester. Every error message I encountered was, in its own way, a small puzzle. Some were easy a missing colon, a misspelled variable name. Others took much longer to track down, especially logical errors where the program ran without crashing but still produced the wrong output. Those logical errors are the ones that actually teach you something, because there is no shortcut; you have to genuinely understand the flow of the program to find them.

I also noticed that breaking a problem into smaller pieces made even intimidating assignments feel manageable. Instead of looking at a full assignment description and feeling overwhelmed, I started asking what the very first small step would be, solving just that step, and then moving to the next one. This approach of decomposing a problem before writing any code at all is something I did not appreciate at the start of the semester, but I now consider it more important than knowing any particular syntax. Syntax can always be looked up; the ability to break a vague problem into solvable pieces cannot be looked up in the same way.

Working through these exercises also gave me a better appreciation of how programs actually execute, step by step, rather than as a single static block of text. I started mentally running through code the way the computer would entering a loop, checking a condition, updating a variable, looping back — instead of just reading it top to bottom once. That mental model of execution is, I think, the real foundation that the rest of Computer Engineering will build on, whether the next course is about databases, circuits, or anything else.

Looking back at this part of the semester, I can clearly see how much my approach to problems changed. The student who once panicked at a wall of red error text is, by the end of the course, someone who can sit down, trace through a problem calmly, and find the one line that is behaving unexpectedly. That confidence did not come from any single lecture; it came from repeatedly facing small problems, getting them wrong, and working through why, until the process of debugging itself stopped feeling like failure and started feeling like a normal, even satisfying, part of writing code.

One pattern I started recognizing across almost every assignment was that the hardest part of solving a problem was rarely the coding itself it was figuring out exactly what the problem was actually asking. More than once I wrote a technically correct program that solved a slightly different problem from the one assigned, simply because I had skimmed the instructions instead of reading them carefully. That mistake taught me to slow down at the very start of any task, restate the problem in my own words before writing a single line, and only then begin thinking about loops or conditions. It sounds like an obvious step, but skipping it was the source of more wasted time than any actual bug ever was.

Working with classmates on similar exercises also showed me that there is rarely only one correct way to solve a problem. Two people could write completely different loops to solve the exact same task, both perfectly valid, just structured around a different way of thinking about the same sequence of steps. Seeing those different approaches side by side stretched my own sense of what counts as a "normal" solution, and it made me less attached to whatever first idea came to mind, since I knew from experience that a better, simpler approach might be sitting right next to it if I kept thinking a little longer.

I also began to notice a kind of rhythm in how I approached unfamiliar problems by the later weeks of the semester: read the problem twice, identify what input is given and what output is expected, sketch the steps in between in plain language, and only then translate those steps into actual code. That rhythm did not exist for me at the start of the semester, when my instinct was always to start typing immediately and figure things out as errors appeared. Both approaches eventually arrive at working code, but the planned approach got me there with far fewer wrong turns, and it left me with code I actually understood afterward rather than code I had stumbled into.

By the end of this stretch of the course, problem solving had stopped feeling like a separate skill layered on top of programming and started feeling like the actual core of it, with syntax simply being the language used to express a solution once the thinking was already done.

I also started noticing a pattern in how I approached new problems compared to earlier in the semester. Before, I would read an assignment description once and try to write a solution in roughly one continuous attempt, fixing whatever broke along the way. By the end of this part of the course, I had shifted toward a much slower, more deliberate first step: writing out, in plain language or rough pseudocode, what the program actually needed to do before typing any real Python. That extra step felt slow at first, almost like wasted time, but it consistently saved me from the kind of confused, half-working code that used to take much longer to fix afterward than it would have taken to plan properly beforehand.

One specific habit that stuck with me was using print statements deliberately as a debugging tool rather than only as a way to show final output. Inserting a print statement in the middle of a loop just to see what a variable held at that exact point, then removing it once I understood the issue, became almost second nature. It is a simple technique, far from sophisticated, but it taught me to stop guessing about what a program was doing internally and instead actually look. That shift from guessing to checking is, I think, the real definition of problem solving in a programming context, and it is the single skill from this part of the semester I expect to use the most going forward, regardless of which language or course comes next.
