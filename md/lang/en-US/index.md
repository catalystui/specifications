![The CatalystUI Logo](/images/catalyst/logo-black.png)

> “If we cannot define what something is, how can we know whether we have built it correctly?”

## Introduction

CatalystUI specifications are not intended to mirror traditional computer science definitions exactly. Many existing definitions are useful in their own contexts, but CatalystUI is concerned with something slightly different: defining a consistent set of specifications that can be individually examined, implemented, and verified. To keep those specifications precise, CatalystUI uses principles from mathematics, including set theory and proofs, while still allowing practical implementations to vary across languages, services, frameworks, and systems.

### What “Within Spec” Means

When something is determined to be “within spec,” it does not mean it perfectly matches every theoretical detail of the specification in the most rigid possible way. Instead, it means the CatalystUI Team has manually reviewed it and found it reasonable to assume that the required behavior described by the specification can be represented, supported, or implemented within that environment.

This distinction is important. A specification defines what must be reasonably possible, not necessarily what must appear in one exact form. Different programming languages, services, and implementations may express the same underlying behavior in different ways while still satisfying the intent of the specification. This manual review process is what allows something to become **CatalystUI Verified**.

### Verification Categories

Different forms of CatalystUI Verification may apply to different kinds of work. Some specifications may define requirements for programming languages, while others may define requirements for available data representations, interface features, accessibility behavior, or implementation patterns used in user-interface design.

The primary verification category is **CatalystUI Verified for Programming Languages**. This indicates that a programming language provides enough primitives, representations, and foundational behavior to reasonably support an implementation of the CatalystUI stack.

Other verification categories may apply to services, frameworks, applications, libraries, or other systems depending on what the related specifications are designed to evaluate.

### Accessibility Verification

One important verification category is **CatalystUI Verified for Accessibility**.

For this verification, CatalystUI identifies three primary senses involved in most user-interface interactions: **sight**, **sound**, and **touch**. To be verified for accessibility, a service must remain reasonably usable when any one of these three primary senses is missing by relying on the remaining senses.

If sight is unavailable, the service should still be reasonably usable through sound and touch. If sound is unavailable, the service should still be reasonably usable through sight and touch. If touch is unavailable, the service should still be reasonably usable through sight and sound.

The additional sensory domains of **taste** and **smell** may also be considered during verification. These senses are inclusive for verification, meaning they may strengthen or support an accessibility review when they are meaningfully used. However, they are not exclusive for failure, meaning a service does not fail accessibility verification simply because it does not provide taste-based or smell-based interaction. CatalystUI’s accessibility review is primarily concerned with whether the service can still be reasonably used when one of the primary senses are individually unavailable.

### Requesting Verification

The goal of this documentation is to organize each specification according to the verification it supports. Each verification category will contain the related specifications needed to understand what is being reviewed, what requirements must be satisfied, and how eligibility is determined.

Requesting CatalystUI Verification is meant to be approachable. This is not intended to feel like submitting a proposal to a distant standards body or navigating an intimidating technical bureaucracy. While review may require a small fee to support the time involved, the process is designed to remain accessible, practical, and encouraging. The purpose of CatalystUI Verification is to help developers, language designers, service providers, and organizations clearly understand what their systems make possible.

### Verification Validity

CatalystUI Verification applies only to the reviewed state of a language, service, framework, application, library, or system at the time the verification is issued. This matters because usability and accessibility are not abstract labels; they depend on the actual interface, behavior, structure, and features people are expected to use. When major changes are made—especially changes to navigation, interaction patterns, accessibility behavior, or user-facing structure—the previous review can no longer guarantee that the system remains within spec. In those cases, the verification is invalidated and a new review, including its associated verification fee, is required. This encourages verified systems to preserve clear, stable, and accessible experiences rather than repeatedly disrupting users with unnecessary changes that must be relearned, rechecked, and reverified.

Programming languages are treated as a special case. A language may retain its verification across later versions so long as it preserves backward compatibility with the previously verified features, primitives, representations, and foundational behavior. If those verified capabilities remain available and reasonably usable, the language does not need to be reviewed again simply because a new version has been released. However, if a future version removes, breaks, or substantially changes the behavior CatalystUI Verification depended on, a new review may be required.

If you believe a CatalystUI Verified service or language has made sufficient changes to invalidate its verification, [please contact us](mailto:contact@catalystui.org).
