# CP Reference Book

A two-page-per-topic **competitive programming reference sheet**, available in **C++** and **Python**.
Written in LaTeX, built for printing and for the "I know this algorithm, I just need the exact snippet" moment during a contest.

Originally put together as my personal reference while competing with my university's algorithms club (ICPC-style contests). It also works well as an interview-prep refresher.

| Version | PDF | Source | Prose language |
|---|---|---|---|
| **C++** | [`cpp/cp-reference-cpp.pdf`](cpp/cp-reference-cpp.pdf) | [`cpp/cp-reference-cpp.tex`](cpp/cp-reference-cpp.tex) | Spanish |
| **Python** | [`python/cp-reference-python.pdf`](python/cp-reference-python.pdf) | [`python/cp-reference-python.tex`](python/cp-reference-python.tex) | English |

> Both versions cover the same core material. Code and algorithm names are identical; only the surrounding explanations differ in language.

---

## What's inside

### C++ version — 8 sections

1. **C++ basics & complexity** — fast I/O, decimal precision, type limits, common complexity classes, STL complexity cheat table, constraint-to-complexity rules of thumb
2. **Math, modular arithmetic & number theory** — GCD/LCM, notable sums, modular properties, binary exponentiation, modular inverse, factorials, `nCr`, classic sieve, linear SPF sieve, Euler's totient (single + sieve)
3. **Arrays & general techniques** — prefix sums 1D/2D, prefix XOR, difference arrays, binary search, binary search on answer, `lower_bound`/`upper_bound`, Kadane, LIS in `O(n log n)`
4. **Bit manipulation** — set/check/toggle/clear, LSB tricks, GCC built-ins, subset iteration, submask iteration, Gosper's hack, fast integer `log2`
5. **Strings** — `getline`/`cin.ignore`/`stringstream` gotchas, Z-function, KMP prefix function, Manacher (odd + even)
6. **Basic graphs** — adjacency lists, graph identities, DFS, BFS, BFS distances, grid directions, bipartite check, cycle detection (directed + undirected)
7. **Advanced graphs & DSU** — Dijkstra, DSU with path compression + union by size
8. **Advanced data structures** — recursive segment tree, Fenwick tree (BIT), PBDS ordered set (`find_by_order` / `order_of_key`)

### Python version — 15 sections

1. **Python contest setup** — fast input patterns, essential imports, recursion limit, constants, performance notes
2. **Complexities & Python structures** — complexity classes, cost of `list`/`dict`/`deque`/`heapq`/`bisect`, realistic constraints for Python
3. **Input, strings & parsing**
4. **Binary search** — manual, on answer, `bisect`, first-true/last-true pattern
5. **Math & number theory** — GCD/LCM, classic sieve, linear SPF sieve, Euler's totient (single + sieve), notable sums
6. **Modular arithmetic & combinatorics** — binary exponentiation, modular inverse, factorials, `nCr`, precomputed inverse factorials
7. **Prefix sums & difference arrays** — 1D, XOR, 2D, range updates
8. **Bit manipulation** — including Python-native `bit_count()` / `bit_length()`
9. **Core graph algorithms** — adjacency lists, recursive + **iterative** DFS, BFS, BFS distances, grid directions
10. **Graph coloring & cycle detection** — bipartite coloring, greedy coloring, cycle detection (directed + undirected)
11. **Shortest paths & DSU** — Dijkstra, DSU, Floyd-Warshall
12. **String matching** — KMP, Z-function, Manacher (odd + even)
13. **Dynamic programming & sequences** — LIS, Kadane, 1D DP skeleton, bitmask DP skeleton
14. **Advanced data structures** — Fenwick tree, **iterative** segment tree, coordinate compression, order statistics via Fenwick, heap usage
15. **General techniques** — two pointers, sliding window, frequency maps, sorting with keys, fast output, memory tricks

---

## Repository layout

```
cp-reference-book/
├── cpp/
│   ├── cp-reference-cpp.tex      # LaTeX source (C++ edition)
│   └── cp-reference-cpp.pdf      # compiled, ready to print
├── python/
│   ├── cp-reference-python.tex   # LaTeX source (Python edition)
│   └── cp-reference-python.pdf   # compiled, ready to print
├── .github/workflows/build-pdf.yml  # rebuilds both PDFs on every push
├── LICENSE
└── README.md
```

Both PDFs are committed on purpose — most people want to download and print, not compile.

---

## Building from source

The PDFs rebuild automatically on every push via GitHub Actions, so you only need this if you want to compile locally.

**Requirements:** a TeX distribution with `pdflatex` ([TeX Live](https://tug.org/texlive/), [MiKTeX](https://miktex.org/), or MacTeX) including the packages `babel`, `geometry`, `multicol`, `listings`, `titlesec`, `enumitem`, `hyperref`, `amsmath`, `amssymb`, `xcolor` and `needspace`.

```bash
pdflatex -interaction=nonstopmode cpp/cp-reference-cpp.tex
```

Run `pdflatex` **twice** on each file — the first pass builds the table of contents, the second one renders it.

No LaTeX installed? Upload the `.tex` file to [Overleaf](https://overleaf.com) and it compiles as-is.

---

## Design notes

- **Landscape + two columns.** Fits far more per page, and stays readable when printed at 100%.
- **Clickable table of contents.** Finding a snippet on a laptop during a virtual contest takes one click.
- **Snippets are copy-paste ready.** No pseudocode, no `...` placeholders — everything compiles/runs as written.
- **Complexity is stated wherever it matters**, because picking the algorithm is usually the actual problem.

---

## Roadmap

Things not covered yet, roughly in the order I'd add them:

- [ ] Trees: LCA (binary lifting), euler tour, subtree sums
- [ ] Topological sort and SCC (Tarjan / Kosaraju)
- [ ] MST (Kruskal / Prim)
- [ ] Segment tree with lazy propagation
- [ ] Classic DP set: knapsack, LCS, edit distance, digit DP
- [ ] Computational geometry basics: cross product, convex hull
- [ ] Bring the C++ edition's prose in line with the English version

Missing something you rely on? Open an issue — suggestions welcome.

---

## Contributing

Corrections and additions are welcome. Please edit the `.tex` source rather than the PDF; CI regenerates the PDFs on merge.

## License

[MIT](LICENSE) — use it, print it, fork it, bring it to your next contest.
