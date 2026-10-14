# 🏰 Reaching the Crystal Castle — Analysis and Design of Algorithms

<p>
  <img alt="Java" src="https://img.shields.io/badge/Java-1f2328?style=flat-square&logo=openjdk&logoColor=white">
  <img alt="Course" src="https://img.shields.io/badge/Course-Analysis%20and%20Design%20of%20Algorithms%20(ADA)-1f2328?style=flat-square">
  <img alt="Year" src="https://img.shields.io/badge/2025%2F26-3rd%20year%2C%202nd%20semester-1f2328?style=flat-square">
</p>

First assignment of *Análise e Desenho de Algoritmos* (Analysis and Design of Algorithms), Computer Science degree at **NOVA School of Science and Technology (FCT NOVA)**.

## About

A **dynamic programming** problem: count how many different paths an explorer can take across a grid, from the top-left tile to the castle in the bottom-right tile.

- She can **step** right or down, or **jump** down, down-left or down-right.
- Jumps are tiring: there's a limit on **consecutive jumps** and on the **total number of jumps** in the journey.
- Some tiles forbid diagonal jumps, some forbid all jumps, and some can't be stepped on at all.
- The answer can be huge, so it's computed modulo 10⁹ + 7.

## Solution

The state is **(row, column, consecutive jumps so far, total jumps so far)**. Path counts are propagated forward, tile by tile, through each of the five allowed moves, respecting the tile rules and both jump limits; the answer is the sum of all states at the bottom-right tile.

This runs in **O(R · C · M · N)** time — on the largest grid allowed (400 × 400, up to 5 consecutive and 10 total jumps) it takes about a quarter of a second.

## Running it

Requires Java 8 or newer.

```bash
javac -d bin src/*.java
java -cp bin Main < input.txt
```

The input has the number of test cases, then for each one a line with `rows columns maxConsecutiveJumps maxTotalJumps` followed by the grid (`.` free, `X` no diagonal jumps, `J` no jumps, `#` blocked). Example:

```text
1
4 5 2 3
..X..
.#..J
...#.
X....
```

```text
114
```

## What I learned

- Modelling a counting problem as a dynamic program with extra state dimensions for constraints
- Keeping the state space small enough for the input limits, and working modulo a prime

## Authors

- **Miguel Carmo** ([@MCCProgrammer](https://github.com/MCCProgrammer))
- **Tomás Ramos Alves** ([@Alvesss04](https://github.com/Alvesss04))

---

<sub>The assignment statement is not included in this repository, as it belongs to the course's teaching staff. This is a student project shared for portfolio purposes.</sub>
