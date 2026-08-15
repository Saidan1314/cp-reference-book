# CP Reference Book

A **competitive programming reference book** in two parallel editions, **C++** and **Python**.
Written in LaTeX, built for printing and for the "I know this algorithm, I just need the exact snippet" moment during a contest.

Originally my personal reference while competing with my university's algorithms club (ICPC-style contests). It also works well as an interview-prep refresher.

| Edition | PDF | Source | Pages |
|---|---|---|---|
| **C++** | [`cpp/cp-reference-cpp.pdf`](cpp/cp-reference-cpp.pdf) | [`cpp/cp-reference-cpp.tex`](cpp/cp-reference-cpp.tex) | 25 |
| **Python** | [`python/cp-reference-python.pdf`](python/cp-reference-python.pdf) | [`python/cp-reference-python.tex`](python/cp-reference-python.tex) | 25 |

Both editions follow the **same 12-section structure**, so a topic sits in the same place in either book. Section 2 is the one deliberate divergence: *C++ STL Toolkit* vs *Python Toolkit*, because that is where the two languages genuinely differ.

---

## The 12 sections

| # | Section | C++ | Python |
|---|---|---|---|
| 1 | Contest Setup and Complexity | template, fast I/O, type limits, `__int128`, sanitizers, `dbg` macro | template, `stdin.buffer` input, buffered output, thread-stack recursion, PyPy vs CPython |
| 2 | **Language Toolkit** | vector/set/map idioms, `nth_element`, `bitset`, `next_permutation`, anti-hash `unordered_map`, `mt19937_64` | slicing, `Counter`/`defaultdict`, `heapq`, `math`, big ints, `itertools`, `lru_cache`, `bytearray` |
| 3 | Math, Modular Arithmetic and Number Theory | GCD, extended Euclid, Diophantine, binexp, inverses, factorials/`nCr`, sieves, totient, Miller–Rabin, Pollard's rho, CRT, matrix exponentiation | same, using built-in `pow(a,b,m)`, `isqrt`, `math.comb` and `bytearray` sieves |
| 4 | Arrays, Prefix Sums and Searching | prefix sums 1D/2D/XOR, difference arrays 1D/2D, binary search (4 shapes), ternary search, two pointers, sliding-window max, Kadane, LIS + reconstruction, coordinate compression, inversion count, monotonic stack | same, plus `accumulate`, `bisect`, and the local-binding speedups |
| 5 | Bit Manipulation | masks, LSB tricks, GCC built-ins, `<bit>`, submasks, Gosper's hack, SOS DP, XOR linear basis | same, with `bit_count`/`bit_length` and arbitrary-width ints |
| 6 | Strings | I/O gotchas, `stringstream`, Z-function, KMP, Manacher, hashing mod $2^{61}-1$, trie | same, plus `str` method reference and the $O(n^2)$ concat trap |
| 7 | Graphs: Traversal and Ordering | representations, DFS (rec + iterative), BFS, multi-source BFS, 0–1 BFS, grids, components, bipartite, cycle detection, topological sort (Kahn + DFS) | same, all iterative, plus greedy coloring |
| 8 | Shortest Paths, MST and DSU | Dijkstra + path reconstruction, Bellman–Ford, Floyd–Warshall, DSU, Kruskal, Prim | same, with the row-wise Floyd–Warshall speedup |
| 9 | Trees and Advanced Graphs | rooting, diameter, LCA binary lifting, Euler tour, tree DP, bridges, articulation points, SCC (Kosaraju) | same, written iteratively (no recursion limit risk) |
| 10 | Dynamic Programming | how to build a DP, 0/1 and unbounded knapsack, LCS, edit distance, bitmask TSP, digit DP, DAG longest path, rolling arrays | same, plus top-down vs bottom-up with `@cache` |
| 11 | Advanced Data Structures | Fenwick (+ range update, + 2D, + `lower_bound`), segment tree (recursive, iterative, lazy), sparse table, PBDS ordered set | same, plus the ordered-set substitutes Python lacks |
| 12 | Contest Techniques and Pitfalls | meet in the middle, interactive I/O, stress testing, greedy proofs, bug checklist, time management | same, plus a CPython speed-up checklist |

Every snippet compiles/runs as written. Complexity is printed next to the heading wherever the choice matters, and the recurring **Use / Tip / Careful** callouts cover the traps that actually cost submissions — `int` overflow before assignment, `mp[k]` inserting on read, `[[0]*m]*n` sharing rows, a forgotten `push` in lazy propagation.

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

## Design

- **Landscape, two columns.** Roughly twice the content per sheet, still readable printed at 100%.
- **Printed contents lists sections only** (one page), while the PDF sidebar carries **full bookmarks down to every snippet** — fast to scan on paper, fast to search on screen.
- **Complexity badges** sit in the heading itself, so choosing an algorithm does not require reading the code.
- **Running headers** name the current section on every page.
- **Code blocks** use a left accent rule instead of a full frame: less ink, clearer column flow, and no boxes breaking across columns.
- Each `.tex` is **fully self-contained** — no shared style file, so either one can be dropped straight into Overleaf.

---

## Building from source

The PDFs rebuild automatically on every push via GitHub Actions, so this is only needed for local edits.

**Requirements:** a TeX distribution with `pdflatex` ([TeX Live](https://tug.org/texlive/), [MiKTeX](https://miktex.org/), MacTeX) including `babel`, `geometry`, `multicol`, `listings`, `titlesec`, `fancyhdr`, `booktabs`, `enumitem`, `hyperref`, `amsmath`, `amssymb`, `xcolor`.

```bash
pdflatex -interaction=nonstopmode cpp/cp-reference-cpp.tex
```

Run `pdflatex` **twice** per file — the first pass builds the table of contents, the second renders it.

No LaTeX installed? Upload the `.tex` to [Overleaf](https://overleaf.com) and it compiles as-is.

---

## Roadmap

Not covered yet, roughly in the order I would add it:

- [ ] Max flow (Dinic) and bipartite matching
- [ ] Computational geometry: cross product, convex hull, segment intersection
- [ ] Suffix array + LCP, Aho–Corasick
- [ ] Heavy-light and centroid decomposition
- [ ] Mo's algorithm and offline query techniques
- [ ] Convex hull trick / divide-and-conquer DP optimisation
- [ ] Persistent segment tree

Missing something you rely on? Open an issue.

---

## Contributing

Corrections and additions are welcome. Edit the `.tex` source rather than the PDF — CI regenerates the PDFs on merge.

## License

[MIT](LICENSE) — use it, print it, fork it, bring it to your next contest.
