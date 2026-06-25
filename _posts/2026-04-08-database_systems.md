---
title: "Database Systems"
date: 2026-04-08
path: /assets/img/posts/4.jpg
categories: [Blogs, Database_blog]
tags: [Journey, UET Faisalabad, Computer Engineering, Database, MySQL, Learning]
---

# Database Systems: Learning How Data Actually Lives Somewhere

Before this semester, I never really thought about where data goes when an app "saves" something. You tap a button, you see a confirmation message, and that is it the rest happens somewhere invisible. Database Systems was the course that pulled back that curtain for me. It is also one of the two courses Dr. Bilal Ahmad taught us this semester, and the way he framed it from day one stuck with me: a database is not just storage, it is a structure that has to stay correct even when hundreds of things are happening to it at once.

The first few weeks were mostly conceptual  what a database actually is, why we do not just keep everything in flat files, and what problems arise when data is duplicated or inconsistent across a system. It sounds dry written like this, but the examples made it click quickly. We talked about what happens to a banking system if a customer's address is stored in five different places and only four of them get updated. Suddenly the abstract idea of "data integrity" stopped being a textbook phrase and became something I could picture going wrong.

Once we moved into MySQL, the course became much more hands on, and this is where I started actually building things instead of just reading about them. I created my first database from scratch, decided on a simple structure for storing student records, and started writing the queries that would let me interact with that structure.

```sql
CREATE DATABASE student_db;

CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT
);

INSERT INTO students VALUES (1, 'Anas', 20);

SELECT * FROM students;
```

It looks like a tiny example, but it taught me more than its size suggests. Choosing `id` as a primary key forced me to understand why every table needs something that uniquely identifies each row, and why two students with the same name should never be confused with each other just because their names match. That single design decision a primary key turned out to be the foundation almost everything else in the course built on top of.

From there, we expanded into multiple related tables, and this is where the subject started to feel less like memorizing syntax and more like designing a small system. I had to think about which pieces of information belonged together in one table, and which needed to live in a separate table connected by a relationship. Splitting student records from course enrollment records, for example, made the whole structure easier to update without duplicating information everywhere.

Working through assignments also meant getting comfortable with the full set of basic operations: inserting new records, updating existing ones when information changed, deleting records that were no longer needed, and querying the data back out in different ways depending on what question I was trying to answer. Each of these felt simple individually, but combining them correctly making sure an update did not accidentally affect more rows than intended, or that a delete did not remove something I still needed required a level of carefulness I had not needed in earlier programming exercises.

One thing Dr. Bilal Ahmad mentioned that stayed with me is how often real-world databases are evaluated not just on whether they store data, but on how reliably they can be trusted with messy, high-volume, real information. He often pointed to the kind of large medical and operational datasets used in machine learning work as an example of why structure and precision in data matters so much a model is only as good as the data underneath it, and a database is the discipline that keeps that data trustworthy in the first place. Hearing that connection between databases and the AI/ML side of the field gave the course a bigger context than I expected going in.

By the end of the semester, the gap between my very first `CREATE TABLE` statement and the small multi-table structures I was designing later felt significant. Database Systems did not just teach me MySQL commands; it taught me to think about data as something with structure, relationships, and rules that need to be respected, rather than just values sitting in a spreadsheet. That mindset is something I expect to carry into almost every future project, since very few real systems exist without some form of data sitting underneath them.

If I had to summarize the biggest lesson from this course in one sentence, it would be this: a database is only useful if you can trust it, and trust comes from careful design decisions made early, not from fixing problems after the data is already messy. That is a lesson that applies far beyond MySQL, and it is one I am glad I learned this semester rather than later, the hard way, on a larger system.

Something I did not expect from this course was how much it changed the way I look at ordinary apps and websites I use every day. A simple food delivery app, for instance, now reads to me as a small case study in database design there is clearly a table of restaurants, a table of menu items linked to those restaurants, a table of orders linked to users, and probably several more tables handling addresses, payments, and delivery status, all quietly working together behind a clean interface. Before this semester, none of that complexity was visible to me; I just saw a button that placed an order. Now I find myself half-consciously trying to guess the schema behind almost everything I interact with, which is a strange but genuinely fun side effect of actually understanding how this layer of software works.

Working in a team for one of the database assignments added a dimension the individual exercises did not. Agreeing on a shared schema with a classmate meant we both had to explain our reasoning out loud, defend decisions about which table should hold which column, and occasionally admit that the other person's structure handled an edge case ours did not. That back-and-forth was uncomfortable at times, since neither of us wanted to redo work we had already finished, but it produced a noticeably better final design than either of us would have built alone, simply because two people questioning the same structure caught more weak points than one person reviewing their own work usually does.

I also spent some time exploring indexes toward the end of the semester, mostly out of curiosity after Dr. Bilal Ahmad mentioned how much query performance can change once a table grows from a few hundred rows to millions. Our assignments never reached a scale where the difference was dramatic, but reading about how an index lets the database avoid scanning every single row gave me a glimpse of why database design decisions matter even more in real, large-scale systems than they do in a classroom exercise with a handful of sample records.

By the end of the semester, I had stopped thinking of "database" as a synonym for "spreadsheet with extra rules" and started thinking of it as its own discipline, with its own correctness, its own failure modes, and its own kind of elegance when a schema is designed well. That shift in perspective is, in many ways, the most valuable thing this course gave me — more valuable, even, than any individual query I learned to write.

Beyond the technical content, the course also changed how I think about everyday software I had been using for years without much thought. Every time I now log into a banking app, check a class schedule, or scroll through an online store, I find myself thinking about the database sitting behind that interface — how the tables might be structured, what the primary keys probably are, and how a single query is likely pulling together the exact screen I am looking at. That kind of curiosity did not exist before this semester, and it has made even ordinary apps feel slightly more interesting to use.

I also came to appreciate how much database design decisions affect things far beyond the immediate assignment. A table structure that seems perfectly fine for ten rows of test data can behave very differently once it needs to handle thousands of records reliably, and thinking ahead about that kind of scale, even at a beginner level, felt like a genuinely new way of evaluating my own work. Instead of asking only "does this query give the right answer right now," I started asking "would this design still make sense if the data grew much larger or was used by many people at once." I do not yet have full answers to questions like that, but learning to ask them at all feels like real progress from where I started the semester.
