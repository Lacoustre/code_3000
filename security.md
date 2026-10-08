# Security Statement

This document describes who is meant to use this repository, what could go wrong
if its contents were obtained or altered by someone else, and what controls are
in place.

Repository: `Lacoustre/code_3000` — a public fork of `batmandoescalc/code_3000`,
containing coursework for CSE 3000.

## Intended users

| User | Access | Purpose |
|---|---|---|
| Me (repository owner) | Read/write | Complete and submit assignments |
| Course instructor and TAs | Read | Grade submitted work; listed in `CODEOWNERS` as `@batmandoescalc` |
| Gradescope | Read | Pull the graded commit through the GitHub integration |
| General public | Read-only | Incidental — the repository is public because it is a fork of public course materials |

No one else is intended to write to this repository. There are no collaborators,
no deploy keys, and no CI workflows with credentials.

## Assessment of security risk

**Overall risk: low.** The repository contains no real personal data, no
credentials, and no proprietary code. A full-text scan for API keys, tokens,
passwords, and private keys returns nothing.

The datasets are synthetic and generated for teaching. This deserves emphasis
because `mod06_data/` looks alarming at first glance: `auxiliary.csv` pairs names
with age, three-digit ZIP, and gender, and `anonymized.csv` is the same table
with names replaced by identifiers. That is exactly the shape of a real
re-identification dataset, but the names are machine-generated and correspond to
no actual people. The same is true of the bot-account, demographic, and emissions
data in the other modules. **There is no personal data here to breach.**

The realistic threats are therefore not data-breach threats:

1. **Academic integrity (most likely risk).** Because the repository is public,
   any classmate can read my completed solutions. If someone copies them, both
   of us may face academic-misconduct findings, and I cannot prove I was the
   original author from a public repo alone. This is the one threat with a
   genuine chance of causing me harm.
2. **Account compromise leading to tampering.** If my GitHub credentials were
   stolen, an attacker could alter or delete work before the grading deadline, or
   push commits under my name. The damage would be to my coursework and
   attribution rather than to any third party.
3. **Dual-use code.** `mod06_deanonymize.py` implements a record-linkage attack:
   it joins an anonymized table to an auxiliary table on quasi-identifiers to
   recover identities. Published openly, it is a working template for
   re-identifying people in a real dataset. The technique is textbook and widely
   documented, so the marginal uplift to an attacker is small, but it is a
   capability rather than inert data and is worth naming honestly.
4. **Accidental credential disclosure.** The largest practical way this
   repository could cause real harm is if I committed a secret to it by mistake.
   Nothing of the sort is present today, and the control below now blocks it.
5. **Unpinned dependencies.** There is no `requirements.txt`, so packages are
   installed ad hoc. This creates a modest supply-chain exposure and means
   results are not exactly reproducible by a grader.

## Steps taken to secure the repository

- **Secret scanning and push protection are enabled** (GitHub, 7 October 2026).
  Push protection rejects any commit containing a recognized credential pattern
  before it reaches GitHub, which directly addresses risk 4 above — the one
  failure mode that could expose something genuinely sensitive.
- **A branch ruleset, "Pull request approvals," is active on `main`** (applied
  from the course template, 7 October 2026). It requires changes to arrive by
  pull request with code-owner review, and it blocks two destructive operations
  outright: deletion of the default branch and non-fast-forward (force) pushes
  that would rewrite published history. No bypass actors are configured, so the
  rules apply to me as repository owner as well.
- **`CODEOWNERS`** designates the course instructor as owner of the repository's
  contents, so any pull request automatically requests their review. Paired with
  the ruleset above, this is now enforced rather than advisory.
- **`.gitignore` excludes local environment and secret-bearing files**:
  `3000-env/` (the virtual environment), `setup_env.py`, `__pycache__/`, and
  `.DS_Store`. Environment setup therefore never enters version control.
- **No credentials are committed.** Verified by scanning all tracked source,
  notebook, and data files.
- **Two-factor authentication** is required by GitHub for all accounts that
  contribute code, so write access cannot be obtained with a password alone.

### Residual risk accepted

The ruleset above addresses tampering and accidental history loss, but it does
not address the academic-integrity exposure in risk 1, which follows from the
repository being a public fork of public course materials. Making it private
would mitigate that risk and would also break the Gradescope integration the
assignments depend on, so I note the tradeoff rather than claim it is solved.

Dependencies remain unpinned (risk 5). Adding a `requirements.txt` would close
that gap and make results reproducible for a grader; it is not yet done.

If this repository ever held real personal data, a live credential, or more than
one contributor, the controls here would need to be revisited — in particular,
required approving reviewers above zero and private visibility.

---

*Last reviewed: 7 October 2026*
