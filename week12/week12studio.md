---
title: Week 12 Studio
theme: solarized
revealOptions:
    transition: 'slide'
---

# Week 12 Studio

---

### Agenda

- Meta Circular Evaluator (???)
- Studio

---

### What is the Meta-Circular Evaluator?

> It is a Source program that evaluates Source programs.

---

### Where to start off?

- The first function you will encounter in the MCE is `parse_and_eval`.

- This is the function that executes the MCE when given its argument, which is a Source program that you want to evaluate, represented by a string.
```javascript
parse_and_eval("1 + 2;"); // The program that you are evaluating is "1 + 2;"
```
- Let's call this string `program_string`.

---

### What's Next? - Abstract Syntax Tree (AST)

- The `program_string` is then parsed into an AST with the `parse` function.

- [What does it look like?](https://sourceacademy.nus.edu.sg/playground#chap=4&exec=1000&ext=NONE&prgrm=A4QwTgzgpgFARAJgAwAIDUKDMSDccCUOAUAPQkoAmYIA7gPoUgAuIMoksiqG2e%2BhRUuSq0GzVu2jxQASzAwAjABoUCQgQFDK1eoxZtwUuLPnLVhVdyy4UC9Kr6ay20XomHOdgLSqUAKixHHCA)

- What is it for?
    - The parser simplifies and translates the program_string into a structure which contains only the important pieces of the program. This structure then allows for easy processing and handling of data by the MCE.

---

### A little more on AST

- Let's look at a [simple expression](https://sourceacademy.nus.edu.sg/playground#chap=4&exec=1000&ext=NONE&prgrm=A4QwTgzgpgFARAJgAwAIDUKDMSDccCUOAUAPQkoAmYIA7gPoUgAuIMoksiqG2e%2BhRUuSq0GzVu2jxQASzAwAjABoUCQgQFDK1eoxZtwUuLPnLVhVdyy4UC9Kr6ay20XomHOdgLSqUAKixHHCA): `20 + 30;`
    - Produces an AST, which represents a list of only 3 elements, namely:
        - tag name
        - operator
        - operands
    - This particular AST structure represents an "application" in Source. Different statements and expresssions have different AST structures.

- What happens with multiple operators with precedence?

- Don't need to know exactly how it works, but a good intuition on its structure will help you with understanding why and how the MCE works.

---

### What's next?
> Start tracing!

---

### Moral of the story

> Read the code! Trace through it and play around with the MCE program.

---

## Attendance

---

## Studio Sheet 12

---

### Question 1

- [Simpler Solution](https://tinyurl.com/S12-MCE-Q1)

- [Alternative (one shown in class)](https://tinyurl.com/MCE-Q1-class)

---

### Question 2

- [Solution](https://tinyurl.com/MCE-Q2-simple)

- An alternative is to create a global list that keeps track of all the user defined constants, and check against them everytime you want to assign a value to a name. [Sample solution.](https://tinyurl.com/MCE-Q2-global-list)

---

### Question 3

[Solutions](https://tinyurl.com/S12-MCE-Q3)
