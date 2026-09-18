# Learning Relational Action Rules Without a Model

**General relational rules induced from a handful of demonstrations, with no model in the loop, and a
controlled ablation showing the competence is carried by those rules and nothing else.**

Stefan Ragland, Dominion Labs Research & Development. Published 12 November 2024.

- Paper (PDF): [`paper/model-free-rule-induction.pdf`](paper/model-free-rule-induction.pdf)
- Paper (web): <https://dmnlabs.org/research/model-free-rule-induction/>
- Contact: research@dmnlabs.org

## The result

A teacher supplies labelled before/action/after demonstrations and asserts no rule. The learner
generalises by anti-unification, keeps only the body literals the negatives discriminate, and produces
first-order rules with variables, including an explicit delete effect. A rule becomes applicable only
after it is confirmed on validation demonstrations it never saw.

On a frozen suite of 14 held-out cases using only unseen constants, the fully equipped system solves
14/14. Seven ablation conditions, each in its own isolated clone, then localise that competence: deleting
the learned rules or revoking their applicable status drops the score to 7/14, exactly the cases needing
no derivation, while a sham clone-and-restore and a concept-store deletion both retain 14/14 and
reinstating the rules recovers 14/14.

## What the same procedure takes, and what it does under ambiguity

| Question | Result | Data |
|---|---|---|
| The frozen suite, re-run 17 September 2026 | 14/14, with no model entry point importable at all | [`data/kite-evaluation-suite.json`](data/kite-evaluation-suite.json) |
| How many positive demonstrations a rule takes | one is refused as a case rather than a generalisation; three are enough; a fourth changes nothing | [`data/evidence-and-supervision.json`](data/evidence-and-supervision.json) |
| What the counter-demonstrations buy | none, and nothing is induced; one, and the body is a single literal; two, and the body is the full conjunction | [`data/evidence-and-supervision.json`](data/evidence-and-supervision.json) |
| When the evidence admits several hypotheses | concluding on any one of them gives 26 wrong conclusions out of 192; concluding only what all of them accept gives 0 | [`data/ambiguity-policies.json`](data/ambiguity-policies.json) |
| How the ambiguity is closed | the case the learner asks for closes 16 of 16, in a mean of 2.6 rounds; random further examples close 1 of 16 | [`data/ambiguity-resolution.json`](data/ambiguity-resolution.json) |
| The same procedure over perceived structure | 30 of 30 things admitted by a perceptual faculty as individuals holding every measured feature; categories induced over them applied to held-out things with zero wrong conclusions | [`data/induction-over-perceived-structure.json`](data/induction-over-perceived-structure.json) |

Each manifest is the file its run wrote, unedited. The later studies apply the same inducer to
classification over features measured off real images, and are reported in full in the companion paper
([repository](https://github.com/DominionLabsInc/perceive-induce-name),
[paper](https://dmnlabs.org/research/perceive-induce-name/)).

## Citation

```bibtex
@techreport{ragland2024relational,
  title       = {Learning Relational Action Rules Without a Model},
  author      = {Ragland, Stefan},
  institution = {Dominion Labs},
  year        = {2024},
  month       = {11},
  url         = {https://dmnlabs.org/research/model-free-rule-induction/}
}
```

## License

The paper and the data are released under [Creative Commons Attribution 4.0](LICENSE). Please cite the
paper if you use them.
