- Change Name: replace-busybox-dependencies
- Start Date: 2018-05-11
- RFC PR: (leave this empty)
- Core-Plans Issue: (leave this empty)

# Summary
[summary]: #summary

This RFC proposes that binaries from the `core/busybox*` package(s) be replaced, wherever possible, by equivalent GNU binaries (for example, `core/coreutils`).

# Motivation
[motivation]: #motivation

One the adopotion challenges for Habitat is that new users must learn a new set of conventions and patterns. Because Busybox's embedded binaries often behave differently than common GNU binaries, new (and even experienced) users can become frustrated by the need to rewrite code to be Busybox-friendly or struggle to follow documented conventions that assume GNU binaries.

# Guide-level explanation
[guide-level-explanation]: #guide-level-explanation

Packages in the `core` origin will, wherever possible, have `core/busybox*` removed from `pkg_deps` in favor of `core` packages that provide equivalent GNU binaries.

# Reference-level explanation
[reference-level-explanation]: #reference-level-explanation

Only packages in the `core` origin should be overhauled to remove `core/busybox*`. Further, `core/busybox*` packages should continue to be provided and updated for those Habitat users who _do_ need Busybox.

# Drawbacks
[drawbacks]: #drawbacks

Some non-`core` builds may break because they depended on a Busybox binary via a transitive dependency introduced by one of the older `core` packages.

# Rationale and alternatives
[alternatives]: #alternatives

We hope that replacing Busybox binaries with GNU versions will accelerate adoption and adhere to "convention over configuration" principles.

Alternatively, it's possible that we could instead recompile Busybox to exactly mirror the GNU binaries it replaces.

# Unresolved questions
[unresolved]: #unresolved-questions

Busybox is heavily used in the interactive Studio. Should it be removed here as well? By including `core/busybox` in the Studio we encourage users to rely on binaries that only superficially resemble the "real" ones.
