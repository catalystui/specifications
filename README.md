# CatalystUI Verified for Programming Languages

This branch contains the CatalystUI Verified for Programming Languages documents. These documents record whether a programming language can represent the foundational data and relationship concepts required by the CatalystUI specifications.

## Adding a Language

Pull requests for new languages are welcome. You do not need a perfect first draft before opening a PR; an early PR is often the easiest place to discuss evidence, wording, and review scope.

Before adding a language, review the existing language pages under `md/lang/en-US/verified/` and `md/lang/en-US/reviewed/` for structure and tone.

1. Choose the correct status.

   * Use `md/lang/en-US/verified/{language-slug}/index.md` only when the language is being submitted for CatalystUI Verified status.
   * Use `md/lang/en-US/reviewed/{language-slug}/index.md` when the language has been reviewed but is not being submitted as verified, or when the review concludes that the language is not within spec.
2. Use a lowercase, URL-safe slug for the directory name, such as `java`, `csharp`, or `javascript`.
3. Follow the existing language document format:

   * overview
   * good faith or review statement
   * review assumptions
   * warnings
   * failures
   * FDEFSPEC verification
   * FRELSPEC verification
4. Base the review on stable evidence such as official language documentation, language specifications, standard library behavior, compiler behavior, runtime behavior, or focused examples.
5. Add the language to the Verification Index navigation in `md/manifest.json`.

   * Verified languages should be added under `Verified Languages`.
   * Reviewed languages should be added under `Reviewed Languages`.
6. If the language is verified, add it to the `Verified Languages` page.

## Verification Process

Programming Language Verification is a manual CatalystUI Team review. The review asks whether the language can faithfully represent the foundational concepts required by the applicable CatalystUI specifications.

The current programming language verification baseline is:

* FDEFSPEC (Rev. 1)
* FRELSPEC (Rev. 1)

Verification considers whether each required provision is supported, unsupported, or supported with warnings. A language does not need to express every concept in the same way as another language, but the required meaning must be representable clearly, reliably, and consistently.

The general process is:

1. A contributor opens a PR with the proposed language review or verification.
2. The CatalystUI Team reviews the evidence and the proposed status.
3. Any required changes are discussed in the PR.
4. The applicable verification fee is paid before the PR is accepted.
5. If the language is found to be within spec, the PR may be accepted and the language may be listed as verified.

Payment of the verification fee is required before a PR for a verified language will be accepted or merged. Contributors are still encouraged to open PRs before payment so the review can begin, scope can be clarified, and maintainers can help identify any missing evidence. Payment does not guarantee verification or merge; acceptance still depends on the CatalystUI Team's review.

## Manifest Ordering

Languages added to the Verification Index navigation in `md/manifest.json` must be ordered according to their verification status.

Verified Languages must be ordered by the current [TIOBE Index](https://www.tiobe.com/tiobe-index/) position first, then by language name.

Languages with a current TIOBE rank should appear before languages without one. If a verified language does not currently appear in the TIOBE ranking used for the update, place it after ranked verified languages and order it alphabetically by display name.

Reviewed Languages must be ordered by review date first, then alphabetically by language name. Newer review dates should appear before older review dates. If multiple reviewed languages share the same review date, order those languages alphabetically by display name.
