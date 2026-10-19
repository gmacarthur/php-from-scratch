# PHP-101 — Movie Ticket Booking CLI

**Type:** Learning story · **Priority:** Medium · **Estimate:** 1–2 hours  
**Week:** 01 / 12 · **Status:** To Do  
**Topics:** Variables · arrays · `foreach`/`for` · `if`/`elseif` · input/output · simple arithmetic

## User story

**As a** cinema customer,  
**I want** to choose a movie, enter how many people are attending and their ages,  
**so that** I can see whether everyone can watch the film and how much the tickets will cost.

## Background

You've been asked to build a very small cinema booking system. It runs in the **terminal**, not a website. The customer answers questions, and the app produces a simple receipt. The first bit of the program is already written so you can run it immediately. **You must build the rest.**

## Getting started

From the repository's root folder:

```bash
php -v
php index.php
```

You should see:

```text
================================
       THE PHP CINEMA
================================

Welcome! What is your name? Sam

Hi, Sam! Your movie booking starts here.
```

Edit **`index.php`** in the repository root. Look for `TODO 1` through `TODO 8`. You do not need to create a web server or install anything with Composer.

## Requirements

### Movie catalogue

Create **an array** of at least three movies. Every movie must have a **title** and an Australian **classification**. Use this catalogue, or choose your own titles with the same mix of classifications:

| Menu number | Movie | Classification |
| --- | --- | --- |
| 1 | Star Voyage | PG |
| 2 | The Last Dragon | M |
| 3 | Midnight Escape | MA15+ |
| 4 *(optional)* | The Haunted House | R18+ |

Show a numbered menu. Users enter the number, not the movie name.

### Ticket pricing

| Ticket type | Age | Price (AUD) |
| --- | --- | ---: |
| Child | 0–17 | $10.00 |
| Adult | 18–64 | $18.00 |
| Senior | 65+ | $12.00 |

Pricing is purely an exercise rule: someone aged 17 pays the child price even if they are old enough to see an MA15+ film.

### Classification rules

| Rating | Rule for this exercise |
| --- | --- |
| G | All ages |
| PG | All ages |
| M | All ages (advisory rating, not an age restriction) |
| MA15+ | Customers must be at least 15 |
| R18+ | Customers must be at least 18 |

**Teaching simplification:** In real Australian classification rules, children under 15 may attend MA15+ films if accompanied by a parent or adult guardian. For this *first-week* exercise, apply the stricter 15+ rule above so you can focus on `if` statements. Do not describe the simplified rule as actual cinema law.

If **any** age fails the classification check, don't create a successful booking or charge for it. Show a friendly explanation of why the booking cannot proceed.

## Acceptance criteria

Check each box only after you have run the program and verified it works.

- [ ] **AC1 — Movie list:** The application displays at least three movies in a numbered list, including their classifications.
- [ ] **AC2 — Movie selection:** The customer can select a movie by number. Invalid numbers are rejected without crashing; the customer is asked again.
- [ ] **AC3 — Ticket count:** The customer enters a number of tickets between **1 and 6**. Invalid entries (e.g. `0`, `7`, or `hello`) are rejected and requested again.
- [ ] **AC4 — Ages:** For each ticket, the program asks for an age and stores the values. Only whole-number ages between **0 and 120** are accepted; invalid values are requested again.
- [ ] **AC5 — Ticket type:** The program classifies each age as child, adult or senior using the table above.
- [ ] **AC6 — Film ratings:** The program checks every attendee against the chosen classification. If anyone is underage, it clearly rejects the booking and **does not show a payable total**.
- [ ] **AC7 — Price calculation:** For an allowed booking, the program adds the correct price for every ticket.
- [ ] **AC8 — Receipt:** The program prints the selected movie, classification, ticket count, each attendee's age and ticket type/price, and the final total with two decimal places.
- [ ] **AC9 — Code readability:** Variables have clear names; at least **three useful comments** explain non-obvious logic or decisions; the code uses at least one array, one loop and one conditional.
- [ ] **AC10 — Working CLI:** The program can be run with `php index.php` and doesn't require a framework, database or extra packages.
- [ ] **AC11 — Boundary tests:** Run tests for ages immediately **below, at, and above** each relevant cutoff. Record expected and actual outcomes.
- [ ] **AC12 — Negative tests:** Confirm invalid numbers, blank responses, underage customers and invalid ticket counts are handled without PHP warnings or a false successful booking.
- [ ] **AC13 — Git workflow:** Work on a clearly named feature branch, make at least **three meaningful commits**, and open a pull request using the template with your test evidence.

### Expected behaviour examples

These are **example user experiences**, not a complete solution or prescribed text layout.

**Example A — successful booking**

```text
Select movie: 1
How many tickets? 3
Age for ticket 1: 12
Age for ticket 2: 35
Age for ticket 3: 67

Movie: Star Voyage (PG)
Tickets: 3
1. Age 12 — Child — $10.00
2. Age 35 — Adult — $18.00
3. Age 67 — Senior — $12.00
TOTAL: $40.00
```

**Example B — rating blocked**

```text
Select movie: 3
How many tickets? 2
Age for ticket 1: 16
Age for ticket 2: 12

Sorry, Midnight Escape (MA15+) requires everyone to be at least 15.
Booking not completed.
```

**Example C — invalid entry**

```text
How many tickets? bananas
Please enter a whole number from 1 to 6.
How many tickets? 2
```

## Implementation tasks

- [ ] **Task 1 — Model movies:** Decide how an array can hold a movie's title and classification. Create at least three entries.
- [ ] **Task 2 — Show the menu:** Use a loop to print each movie with a number.
- [ ] **Task 3 — Read the choice:** Ask for a movie number; validate it; find the chosen movie.
- [ ] **Task 4 — Read the group:** Get a valid ticket quantity. Repeat an age question that many times.
- [ ] **Task 5 — Work out prices:** Use age ranges to choose a ticket category, then calculate its price.
- [ ] **Task 6 — Check the rating:** Ensure *every* person meets the rating requirement before accepting the booking.
- [ ] **Task 7 — Print the receipt:** Display readable lines and a two-decimal currency total.
- [ ] **Task 8 — Test and explain:** Complete the testing matrix below, investigate any failures, and add comments explaining important decisions.
- [ ] **Task 9 — Submit for review:** Create meaningful commits, push your feature branch and open a pull request with the required evidence.

## Testing & edge cases — required before the PR

**Do not start here by writing code.** First think through the questions, predict the result, then run the program to see whether it matches. A program that works for one ordinary booking is not necessarily correct.

### Boundary-value testing: test either side *and* the boundary

If a rule changes at **13**, don't just test **12** and **14**: test **12, 13 and 14**. The value **at** the boundary is where `>` instead of `>=` (or `<` instead of `<=`) often causes a bug.

Your application has pricing boundaries at **18 and 65**, classification boundaries at **15 and 18**, ticket-count boundaries at **1 and 6**, and accepted age boundaries at **0 and 120**. The tests below are a starting point; also invent **two of your own**.

| ID | Input or scenario | Expected result | Actual result | Pass? |
| --- | --- | --- | --- | --- |
| T01 | PG movie, age **17** | Child, $10 | _Fill in_ | ☐ |
| T02 | PG movie, age **18** | Adult, $18 | _Fill in_ | ☐ |
| T03 | PG movie, age **19** | Adult, $18 | _Fill in_ | ☐ |
| T04 | PG movie, age **64** | Adult, $18 | _Fill in_ | ☐ |
| T05 | PG movie, age **65** | Senior, $12 | _Fill in_ | ☐ |
| T06 | PG movie, age **66** | Senior, $12 | _Fill in_ | ☐ |
| T07 | MA15+ movie, age **14** | Booking rejected | _Fill in_ | ☐ |
| T08 | MA15+ movie, age **15** | Booking allowed; child price | _Fill in_ | ☐ |
| T09 | MA15+ movie, age **16** | Booking allowed; child price | _Fill in_ | ☐ |
| T10 | R18+ movie, age **17** | Booking rejected | _Fill in_ | ☐ |
| T11 | R18+ movie, age **18** | Booking allowed; adult price | _Fill in_ | ☐ |
| T12 | R18+ movie, age **19** | Booking allowed; adult price | _Fill in_ | ☐ |
| T13 | PG movie, ages **0** and **120** | Both valid; correct prices | _Fill in_ | ☐ |
| T14 | Age **-1**, then **121** | Each rejected; asks again | _Fill in_ | ☐ |
| T15 | Ticket count **0**, **1**, **6**, **7** | Reject 0/7; accept 1/6 | _Fill in_ | ☐ |
| T16 | Blank, `hello`, `12.5` as age | Reject each; ask again | _Fill in_ | ☐ |
| T17 | Unknown movie number | Reject; show prompt again | _Fill in_ | ☐ |
| T18 | M movie, age **10** | Booking allowed (M is advisory) | _Fill in_ | ☐ |
| T19 | MA15+, ages **15, 14, 65** | **Whole booking** rejected; no payable total | _Fill in_ | ☐ |
| T20 | PG, ages **12, 35, 67** | Total **$40.00** | _Fill in_ | ☐ |
| T21 | Your own edge case | Write predicted result first | _Fill in_ | ☐ |
| T22 | Your own edge case | Write predicted result first | _Fill in_ | ☐ |

**Questions to answer in your PR:**

1. What could go wrong if you write `if ($age > 18)` when adulthood starts at 18?
2. Why should you test a classification check independently of the ticket price? Could someone qualify for a *child-priced ticket* but be permitted into an MA15+ film?
3. What happens if three people book and only the **second** person is underage? Is the whole booking stopped?
4. What if the user enters `0`, a negative number, an empty string, or letters? Does the program recover, or does it continue with bad data?
5. Which **two additional** edge cases did you think of yourself, and why?

You are **not** expected to learn a test framework yet. These are **manual CLI tests**. If you fix a bug, rerun the failing test **and** one nearby boundary test to check for regressions. Use a small markdown table in your PR to record evidence. Do not commit a finished test suite handed to you by someone else.

## Git workflow — part of the exercise

Start from an up-to-date `main` branch. **Do not work directly on `main`.** Replace `your-name` with a short identifier; keep names lowercase and use hyphens.

```bash
git switch main
git pull
git switch -c feature/week-01-movie-tickets-your-name
```

Commit as you build (at least **three** commits that represent distinct progress), for example:

```bash
git add index.php
git commit -m "feat: add movie selection menu"
# After your next change:
git add index.php
git commit -m "feat: calculate ticket prices by age"
# After validation and testing:
git add index.php
git commit -m "fix: reject invalid ages and restricted bookings"
```

These are **examples**, not messages to copy regardless of what your commits contain. Each commit should describe an actual change; avoid `update`, `stuff`, or `final fix`. Check `git status` before each commit. Push and open a PR **to `main`**:

```bash
git push -u origin feature/week-01-movie-tickets-your-name
```

Use GitHub's **Compare & pull request** button (or create a PR through the repository). Title it `PHP-101: Movie tickets — Your Name`. Complete the PR template: summary, acceptance criteria, manual test evidence, edge cases you discovered, key decisions and any questions for review. **Do not merge your own PR**; ask your mentor to review it. Be ready to respond to feedback with a further commit.

### What your reviewer will look for

- Correctness at boundaries, not just happy-path output.
- Sensible variable names, comments explaining **why**, and readable control flow.
- Clear, incremental commit history and a focused PR description.
- Evidence you actually ran tests, including a failing/rejected input.
- Your ability to explain the logic in your own words, without AI.

## Hints (read only if stuck)

<details>
<summary>Hint 1 — Reading another answer</summary>

The name question in `index.php` already demonstrates reading from the terminal using `trim(fgets(STDIN))`. Can you reuse the same idea for a movie number or age?

</details>

<details>
<summary>Hint 2 — Choosing an array</summary>

Arrays can store other arrays. For example, an unrelated item might look like:

```php
$product = ['name' => 'Popcorn', 'size' => 'Large'];
```

Think about how to store several movies that each have two pieces of information.

</details>

<details>
<summary>Hint 3 — Repeating work</summary>

A `foreach` loop is useful for showing every item in an array. A `for` loop can be useful when you know exactly how many times to ask a question.

</details>

<details>
<summary>Hint 4 — Checking a whole number</summary>

Read input as text first. Look up [`filter_var`](https://www.php.net/manual/en/function.filter-var.php) and `FILTER_VALIDATE_INT`. Be careful: a valid value of `0` is different from a failed validation result (`false`).

</details>

<details>
<summary>Hint 5 — Calculating money</summary>

Start with a total of zero and add the ticket price for each attendee. Look up [`number_format`](https://www.php.net/manual/en/function.number-format.php) to display the final result with two decimal places.

</details>

## Bonus challenges (only after all ACs pass)

- **BONUS 1 — Group summary:** Show `2 Adults, 1 Child` as well as individual ticket lines.
- **BONUS 2 — Multiple bookings:** Let the customer book another movie without restarting the program, and display a final total across bookings.
- **BONUS 3 — Discounts:** Add a Tuesday 20% discount, show the original amount and the discount, then calculate the discounted total.
- **BONUS 4 — Real MA15+ rule:** Ask which attendees are parents or adult guardians and model the actual accompanied-under-15 scenario. Write down the assumptions and test them.
- **BONUS 5 — Functions:** If you have already learned functions, extract a reusable input/validation helper. Avoid doing this just to make the code more complicated.

## Definition of done / PR review

Before submitting, complete the PR template, show the **boundary and invalid-input testing evidence**, identify **two edge cases you invented**, explain **what was most difficult**, and suggest **one improvement**. Another person should be able to clone your branch, run `php index.php` and complete a booking.

**Learning agreement:** No AI-generated implementation, no copy/pasted full solutions. You may consult the [official PHP manual](https://www.php.net/manual/en/) and ask a mentor for conceptual hints. We care more about your explanation than about fancy code.
