# CatalystUI Verified for Programming Languages

Welcome to the CatalystUI Verification documentation for programming languages.

**CatalystUI Verified for Programming Languages** indicates that a programming language has been reviewed by the CatalystUI Team and found to provide the primitives, representations, and behavior needed to support an implementation of the CatalystUI Stack.

This verification is not a general ranking of programming languages. It does not decide whether a language is better, faster, easier, newer, or more enjoyable than another. Instead, it identifies whether the language provides a stable and practical foundation for the specifications required by CatalystUI Verification.

## Purpose

Programming languages form the base of every CatalystUI implementation. Before a framework, library, runtime, or application can follow the CatalystUI Stack, the language itself must be capable of expressing the concepts the model depends on.

This includes the ability to represent data, define structures, model behavior, communicate results, interact with systems, and preserve meaning across implementation boundaries. A verified language gives developers enough clarity and control to build CatalystUI-compatible systems without relying on fragile or unclear workarounds.

In simpler terms, this verification asks whether a programming language can provide the building blocks CatalystUI needs.

## What Verification Means

A programming language becomes **CatalystUI Verified** when it is reviewed against the specifications listed in this section and found to be within spec.

Each specification describes one part of the review. Some specifications may define required data representations. Others may describe expected behavior, interoperability needs, compilation concerns, runtime expectations, or other language-level requirements used by CatalystUI implementations.

A language does not need to satisfy these requirements in the same way as another language. Different languages use different syntax, type systems, standard libraries, compilers, runtimes, and design patterns. CatalystUI Verification allows for those differences so long as the required behavior can be expressed clearly, reliably, and consistently.

## What “Within Spec” Means

When a programming language is considered **within spec**, it means the CatalystUI Team has manually reviewed the language and found it reasonable to assume that the required behavior described by the relevant specifications can be expressed within that language.

This does not require one rigid implementation pattern. A language may satisfy a requirement through built-in primitives, standard library features, compiler behavior, runtime behavior, documented guarantees, or another stable mechanism appropriate to that language.

Verification is concerned with the practical ability to meet the specification, not whether the language uses the exact same names, structures, or internal design as the specification text.

## Why This Verification Exists

CatalystUI is designed around clarity, consistency, and the faithful representation of how humans and computers interact. Programming languages matter because they determine what developers can realistically build and how clearly those systems can be expressed.

If a language cannot provide the required base concepts in a stable way, then higher-level CatalystUI implementations become harder to trust. Developers may be pushed toward unclear abstractions, unpredictable behavior, fragile dependencies, or unnecessary rewrites simply to express ideas that should be reliable from the beginning.

Programming Language Verification exists to identify which languages provide a strong enough base for CatalystUI work. It gives developers, language designers, and organizations a clearer understanding of whether a language is suitable for CatalystUI-compatible implementations.

## How a Language Becomes Verified

To become **CatalystUI Verified for Programming Languages**, a language must be reviewed against the specifications listed in this section.

The general process is:

1. The relevant CatalystUI specifications are identified.
2. The language is reviewed against each required specification.
3. The CatalystUI Team determines whether the language satisfies the intent and requirements of the specifications.
4. If the language is found to be within spec, it may be granted CatalystUI Verification.
5. Once verified, the language may be listed on the [Verified Languages](/verified/) page.

The review may consider official language documentation, standard library behavior, compiler behavior, runtime behavior, implementation examples, test cases, and other evidence needed to determine whether the language meets the requirements.

Compiler and runtime behavior may be considered during review when that behavior is part of how the language is commonly and officially used. However, verifying a programming language does not automatically verify every compiler, runtime, package, framework, library, application, or tool in that language’s ecosystem.

## Applicable Specifications

The specifications listed in this section define the requirements used for Programming Language Verification.

Each specification should be understood as one part of the review. A language becomes verified by satisfying the required specifications for this category, not by satisfying only one isolated document unless that document is the only active requirement.

As additional specifications are finalized, they may be added to this section and included in future reviews. This allows Programming Language Verification to grow with CatalystUI while keeping the review process clear and organized.

## Verification Scope

CatalystUI Verification for Programming Languages applies to the programming language as reviewed.

A verified language provides a suitable base for CatalystUI-compatible development. It does not guarantee that every project written in that language follows CatalystUI correctly, nor does it automatically verify the surrounding ecosystem.

Separate tools, libraries, frameworks, runtimes, applications, or services may require their own review depending on the verification category being requested.

## Verification Validity

CatalystUI Verification applies only to the reviewed state of a programming language at the time verification is issued.

Programming languages are treated as a special case because many languages preserve compatibility across multiple versions. A language may retain its verification across later versions so long as it preserves backward compatibility with the features, primitives, representations, and behavior the original review depended on.

If a future version removes, breaks, or substantially changes verified behavior, a new review may be required.

New language features alone do not invalidate verification. Breaking the verified base might.

## Verified Languages

Known verified programming languages are listed separately on the [Verified Languages](/verified/) page.
