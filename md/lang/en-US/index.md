![CatalystUI Verified for Programming Languages](/images/verification/verified-logo-languages.png)

# CatalystUI Verified for Programming Languages

Welcome to the CatalystUI Verification documentation for programming languages.

**CatalystUI Verified for Programming Languages** indicates that a programming language has been reviewed by the CatalystUI Team and found to provide the foundational data representations and relational structures required to express CatalystUI-compatible systems.

This verification is not a general ranking of programming languages. It does not decide whether a language is better, faster, easier, newer, more popular, or more enjoyable than another. Instead, it identifies whether the language provides a stable and practical foundation for the specifications required by CatalystUI Verification.

In simpler terms, this verification asks whether a programming language can faithfully represent the basic data and relationships CatalystUI depends on.

## Purpose

Programming languages form the representational foundation beneath every CatalystUI implementation. Before a framework, library, runtime, application, or service can follow the CatalystUI Stack, the language used to build it must be capable of expressing the foundational concepts the model depends on.

For programming languages, this primarily means two things:

1. The language must be capable of representing foundational data.
2. The language must be capable of representing foundational relationships between data.

These concerns are defined through the foundational CatalystUI specifications. FDEFSPEC defines the expected foundational data representations. FRELSPEC defines the expected foundational relations between those representations, including collections, memory relationships, operations, threading relationships, and composites.

A verified programming language gives developers enough clarity and control to build CatalystUI-compatible systems without relying on fragile, unclear, or unstable workarounds for the basic concepts CatalystUI requires.

## What Verification Means

A programming language becomes **CatalystUI Verified** when it is reviewed against the specifications listed in this section and found to be within spec.

For Programming Language Verification, the review is focused on whether the language can express the foundational requirements defined by the applicable specifications. This does not mean the language itself is a CatalystUI implementation. It means the language provides a suitable foundation from which CatalystUI-compatible implementations may be built.

A language does not need to satisfy these requirements in the same way as another language. Different languages use different syntax, type systems, standard libraries, compilers, runtimes, and design patterns. CatalystUI Verification allows for those differences so long as the required concepts can be expressed clearly, reliably, and consistently.

## What “Within Spec” Means

When a programming language is considered **within spec**, it means the CatalystUI Team has manually reviewed the language and found it reasonable to conclude that the required behavior described by the applicable specifications can be expressed within that language.

This does not require one rigid implementation pattern. A language may satisfy a requirement through built-in primitives, standard library features, compiler behavior, runtime behavior, documented guarantees, or another stable mechanism appropriate to that language.

Verification is concerned with the practical ability to represent and preserve the meaning of the specification, not whether the language uses the exact same names, structures, syntax, or internal design as the specification text.

## Why This Verification Exists

CatalystUI is designed around clarity, consistency, and the faithful representation of how humans and computers interact. Programming languages matter because they determine what developers can realistically express, how safely those systems can be modeled, and how clearly higher-level implementations can be built.

If a language cannot provide the required foundational concepts in a stable way, then higher-level CatalystUI implementations become harder to trust. Developers may be pushed toward unclear abstractions, unpredictable behavior, fragile dependencies, or unnecessary rewrites simply to express ideas that should be reliable from the beginning.

Programming Language Verification exists to identify which languages provide a strong enough foundation for CatalystUI work. It gives developers, language designers, and organizations a clearer understanding of whether a language is suitable for building CatalystUI-compatible systems.

## How a Language Becomes Verified

To become **CatalystUI Verified for Programming Languages**, a language must be reviewed against the specifications listed in this section.

The general process is:

1. The applicable CatalystUI specifications are identified.
2. The language is reviewed against each required specification.
3. The CatalystUI Team determines whether the language satisfies the intent and requirements of the specifications.
4. If the language is found to be within spec, it may be granted CatalystUI Verification.
5. Once verified, the language may be listed on the [Verified Languages](/verified/) page.

The review may consider official language documentation, standard library behavior, compiler behavior, runtime behavior, implementation examples, test cases, and other evidence needed to determine whether the language meets the requirements.

Compiler and runtime behavior may be considered during review when that behavior is part of how the language is commonly and officially used. However, verifying a programming language does not automatically verify every compiler, runtime, package, framework, library, application, or tool in that language’s ecosystem.

## Applicable Specifications

The specifications listed in this section define the requirements used for Programming Language Verification.

For programming languages, the active foundation is currently centered on the following specification categories:

* **FDEFSPEC**, which defines foundational data representations.
* **FRELSPEC**, which defines foundational relations between data representations.

Together, these specifications establish the minimum foundation required for a programming language to represent CatalystUI-compatible systems.

Additional specifications may be introduced later for more specialized verification categories. Those specifications may define higher-level implementation, platform, accessibility, internationalization, framework, service, or runtime requirements. However, those later specifications build on the foundation rather than replacing it.

A programming language becomes verified by satisfying the required specifications for this category. It is not expected to satisfy unrelated implementation-specific requirements unless those requirements are added to Programming Language Verification.

## Verification Scope

CatalystUI Verification for Programming Languages applies to the programming language as reviewed.

A verified language provides a suitable foundation for CatalystUI-compatible development. It does not guarantee that every project written in that language follows CatalystUI correctly, nor does it automatically verify the surrounding ecosystem.

Separate tools, libraries, frameworks, runtimes, applications, services, or implementations may require their own review depending on the verification category being requested.

Programming Language Verification should therefore be understood as a foundation check. It confirms that the language can represent the required concepts. It does not confirm that every use of the language applies those concepts correctly.

## Verification Validity

CatalystUI Verification applies only to the reviewed state of a programming language at the time verification is issued.

Programming languages are treated as a special case because many languages preserve compatibility across multiple versions. A language may retain its verification across later versions so long as it preserves backward compatibility with the features, primitives, representations, and behavior the original review depended on.

New language features alone do not invalidate verification. A future version may require a new review only if it removes, breaks, or substantially changes the verified foundation.

In other words, extending a language is usually fine. Breaking the verified base may require review.

## Verified Languages

Known verified programming languages are listed separately on the [Verified Languages](/verified/) page.
