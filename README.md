# PHP From Scratch: 12 Weeks of Building

**Learn PHP by writing programs, not by copying solutions.**

This repository is a collection of 12 weekly, small, practical challenges. Each week introduces a few concepts, gives you a working starting point, and leaves the implementation to **you**.

**Current challenge:** [Week 01 — Movie Ticket Booking](week-01-movie-tickets/README.md)  
**Time budget:** 1–2 hours  
**Runtime:** PHP 8.2+ (command line). No framework, packages, database or web server.

## Get ready

1. Install PHP 8.2 or later. Check: `php -v`.
2. Clone this repository and open it in your editor.
3. From the **repository root**, run:

   ```bash
   php index.php
   ```

4. You should see a cinema welcome message and a question asking for your name. Enter your name and press Enter.
5. Read the [Week 01 ticket](week-01-movie-tickets/README.md) and build the rest.

> If `php` is not recognised, PHP is not installed or isn't on your PATH. Fix that before beginning the exercise.

## The rules

- **No AI assistants or generated code** for the exercises (including ChatGPT, Copilot and code-completion chat). Ordinary editor autocomplete is fine.
- **Use official PHP documentation and tutorials**, and your own notes. Search for an individual concept when stuck; don't copy a completed cinema program.
- **Plain PHP only.** No Laravel, Composer dependencies or third-party libraries.
- **Leave comments explaining *why* you made a decision**, especially where you used a loop, conditional or validation rule. Don't comment every obvious line.
- **Create a feature branch and make at least three small, meaningful commits** with messages describing what changed.
- **Ask questions and explain your thinking** if you're stuck. A mentor may give hints, not write the solution.

## Recommended workflow

1. Read the entire ticket, including acceptance criteria.
2. Write down the data you'll need (movies, ratings, prices, ages) as comments or notes.
3. Implement **one acceptance criterion at a time**; run `php index.php` after every small change.
4. Test both normal and invalid inputs.
5. Complete the **required testing matrix**, including ages below, at and above each cutoff.
6. Commit your changes incrementally, push your feature branch and open a pull request using the template.

## Learning roadmap

| Week | Project | Core focus |
| --- | --- | --- |
| **01** | **Movie Ticket Booking** | CLI, variables, arrays, loops, conditions, user input |
| 02 | Shopping Basket | Functions, parameters, return values |
| 03 | Quiz Game | Associative arrays, nested loops, scoring |
| 04 | Contact Book | Strings, search, validation |
| 05 | Expense Tracker | Files, CSV, persistence |
| 06 | Library Loans | Organising code, simple classes |
| 07 | Task Manager | OOP, constructors, methods |
| 08 | Bank Account Simulator | Encapsulation, exceptions |
| 09 | Weather Data Reporter | JSON, APIs and error handling |
| 10 | Command-line Notes App | Multi-file structure, reusable functions |
| 11 | Mini Test Runner | Testing and edge cases |
| 12 | Final Project | Design, build, test and explain your own CLI app |

Weeks 02–12 are a *proposed roadmap*, not completed exercises. New tickets and starter files will be added as we go.

## PHP learning resources

- [PHP manual — Getting started](https://www.php.net/manual/en/getting-started.php)
- [Basic syntax](https://www.php.net/manual/en/language.basic-syntax.php)
- [Variables](https://www.php.net/manual/en/language.variables.php)
- [Arrays](https://www.php.net/manual/en/language.types.array.php)
- [Control structures](https://www.php.net/manual/en/language.control-structures.php)
- [Reading from standard input: `fgets`](https://www.php.net/manual/en/function.fgets.php)

## Submission

Use a branch named `feature/week-01-movie-tickets-your-name`, make at least three meaningful commits, and open a pull request to `main`. Include:

- Which acceptance criteria you completed.
- Your **manual boundary and invalid-input test results**, including ages on both sides of and exactly at the cutoffs.
- Two additional edge cases you thought of yourself.
- One thing you learned and one question you still have.

There is deliberately **no completed solution** in this repository.
