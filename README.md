# Enumerative Program Synthesis

Finds the smallest program in the DSL

```
E ::= x | y | 0 | 1 | 2 | + E E | - E E | * E E
```

(written in Polish notation) that matches a set of `i_1, i_2, o_1` input-output examples.

# How it works

1. Build programs bottom-up by size: size 1 is the leaves, and size n is `op L R` where `size(L) + size(R) = n - 1`.
2. Store each program's outputs on the examples, so bigger programs are computed from their children's outputs without re-evaluating anything.
3. Skip any program whose outputs match one already seen (observational equivalence). This keeps the search small without changing the answer.
4. Return the first program whose outputs equal the expected outputs, or `None` if nothing up to size 9 works.

See `program_synthesis.ipynb` for the code and explanations. The 20 course tests are in `tests/` and the answer key is in `answer_key.txt`. The notebook matches all 20, including the smallest program and the number of programs enumerated.
