![The CatalystUI Logo](/images/catalyst/logo-black.png)

![The CatalystUI Logo](/images/catalyst/logo-black.png)

> “If we cannot define what something is, how can we know whether we have built it correctly?”

## Introduction

CatalystUI specifications define the concepts, behaviors, and requirements used throughout the CatalystUI ecosystem. They are not written to perfectly mirror traditional computer science definitions. Many existing definitions are useful in their own contexts, but CatalystUI is concerned with a different goal: creating specifications that can be clearly examined, implemented, reviewed, and verified.

To keep these specifications precise, CatalystUI uses principles from mathematics, including set theory and proofs, while still allowing practical implementations to vary across languages, services, frameworks, applications, libraries, and systems.

The purpose of this section is to organize CatalystUI specifications according to the kinds of verification they support.

## What “Within Spec” Means

When something is determined to be **within spec**, it does not mean it perfectly matches every theoretical detail of a specification in the most rigid possible way.

Instead, it means the CatalystUI Team has manually reviewed it and found it reasonable to conclude that the required behavior described by the specification can be represented, supported, or implemented within the reviewed environment.

This distinction matters. A specification defines what must be reasonably possible, not necessarily what must appear in one exact form. Different languages, services, frameworks, applications, libraries, and systems may express the same underlying behavior in different ways while still satisfying the intent of the specification.

This manual review process is what allows something to become **CatalystUI Verified**.

## Verification Categories

CatalystUI Verification is organized into categories. Each category defines what kind of system is being reviewed, which specifications apply, and what requirements must be satisfied.

Current verification categories include:

* **CatalystUI Verified for Programming Languages** — Reviews whether a programming language provides enough primitives, representations, and foundational behavior to reasonably support CatalystUI-compatible implementation.
* **CatalystUI Verified for Internationalization** — Reviews whether a system provides sufficient essential translation coverage across the required CatalystUI language set and gives users a reasonable way to change languages.
* **CatalystUI Verified for Accessibility** — Reviews whether a system remains reasonably usable when sight, sound, or touch is individually unavailable.

Each category has its own documentation page with the detailed requirements, assumptions, scope, and review guidance for that type of verification.

## Requesting Verification

Requesting CatalystUI Verification is meant to be approachable.

The goal is not to make verification feel like submitting a proposal to a distant standards body or navigating an intimidating technical bureaucracy. While review may require a small fee to support the time involved, the process is designed to remain practical, direct, and encouraging.

The purpose of CatalystUI Verification is to help developers, language designers, service providers, framework authors, application developers, and organizations clearly understand what their systems make possible.

In general, the verification process asks:

1. What is being reviewed?
2. Which verification category applies?
3. Which specifications or requirements are relevant?
4. Can the required behavior be represented, supported, or implemented?
5. Are there any warnings, limitations, or failures that should be documented?

A verified result does not mean the reviewed system is perfect. It means the reviewed system has been found to satisfy the applicable CatalystUI requirements within the documented scope.

## Verification Validity

CatalystUI Verification applies only to the reviewed state of a language, service, framework, application, library, or system at the time verification is issued.

This matters because verification depends on the actual behavior, structure, features, and user-facing experience being reviewed. If major changes are made after verification, the previous review may no longer describe the system accurately.

A new review may be required when a verified system removes required functionality, breaks behavior the verification depended on, substantially changes its user-facing structure, or alters its implementation in a way that affects the verified foundation.

Programming languages are treated as a special case. A language may retain verification across later versions so long as it preserves backward compatibility with the previously verified features, primitives, representations, and foundational behavior. If those verified capabilities remain available and reasonably usable, the language does not need to be reviewed again simply because a new version has been released.

If you believe a CatalystUI Verified service, language, framework, application, library, or system has made sufficient changes to invalidate its verification, [please contact us](mailto:contact@catalystui.org).
