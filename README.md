# Lean-4-Literature

## Beginner friendly
1. [Theorem Proving in Lean 4](https://leanprover.github.io/theorem_proving_in_lean4/) - Use Lean 4 as a proof assistant to prove theorems. 
2. [Functional Programming in Lean](https://lean-lang.org/functional_programming_in_lean/) - Use Lean 4 as a programming language.
3. [Mathematics in Lean](https://leanprover-community.github.io/mathematics_in_lean/index.html) - Use Lean 4 to do 'common' mathematics.
4. [The Mechanics of Proof](https://hrmacbeth.github.io/math2001/index.html) - Use Lean 4 to do 'common' mathematics.
5. [The Hitchhiker's Guide to Logical Verification](https://github.com/lean-forward/logical_verification_2024) - Use Lean 4 to do 'common' computer science.
6. [Logic and Proof](https://leanprover-community.github.io/logic_and_proof/) - Use Lean 4 to do logic in Lean 4. 

## Intermediate and onwards
1. [Metaprogramming in Lean 4](https://leanprover-community.github.io/lean4-metaprogramming-book/) - Extend Lean 4 with custom functionality.
2. [Type Checking in Lean 4](https://ammkrn.github.io/type_checking_in_lean4/title_page.html) - Learn about Lean 4 metatheory.
3. [Scientific Computing in Lean - **WIP**](https://lecopivo.github.io/scientific-computing-lean/) - Modern approach to scientific computing melding convenience of use, correctness, ~~and performance~~.

This list is a superset of documentation recommended at [the official Lean 4 website](https://lean-lang.org/documentation/).

# Lean-4-not-so-Literature
WARNING: subjective and broad; grain of salt recommended, reader discretion required.

List of thoughts/guidelines. While I may use examples to explain what to do / not to do - I do not say _why_ for the sake of brevity.
_Why_ left as an exercise for the reader.
While I am happy to discuss nuances and pertinence of these at length, this is not a repo in which to do it.

## Environment
1. Use VS Code and its Lean 4 extension.
2. Use [JuliaMono font](https://juliamono.netlify.app/).

## Lean
1. Do _not_ (ab)use dependent types. Give **strong** preference to extrinsic properties.
```
section Bad
def foo (n : Nat) : { m : Nat // 42 < m } := ...
end Bad

section Good
def foo (n : Nat) : Nat := ...
theorem 42_lt_foo {n : Nat) : 42 < foo n := ...
end Good
```

2. Do _not_ unfold more than 1 definition per theorem. State lemmas about definitions you use, unfold these definitions in the lemmas that are specifically about them.

3. Only use `simp [...]` (and its derivatives, a'la `aesop`) to discharge the enclosing goal - i.e. as the final tactic in a goal.
   Use `simp only` otherwise. Invoking `simp?` gives you the appropriate `simp only` to use, if you 'must' use simp in the middle of a proof.

A part of my job is to address Lean-specific issues - I use this repository for my own reference, but I am happy to accept PRs. If they gucci.
