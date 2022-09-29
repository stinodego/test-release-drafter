# Drafting multiple releases

This repo tests using [release-drafter](https://github.com/release-drafter/release-drafter) for drafting multiple releases. Conclusion: **it works amazingly well**!

Here's how it works:
* Everything works based on PR tags. No fiddling with conventional commits required.
* An auto-labeler assigns `rust`/`python` tags based on files changed.
  * These determine which release the PR ends up in. A PR can be in multiple releases.
* Another auto-labeler assigns tags for changelog sections, based on branch names.
  * For example, a branch called `feat/cool-stuff` will be tagged `feature` and put under the "Features" header.
  * We should come up with sensible headers. Features / bug fixes / API changes / ...?
  * Multiple tags are allowed. For example, you could create a "Highlights" section and manually add a `highlight` tag to important PRs.
* Versions are automatically incremented based on the previous release of the same type. Adding a `breaking` tag will trigger a minor version bump (as we are in pre-1.0.0 still).
* Changelog entries contain the PR name, so this name should be descriptive (which is great; the convential commit tags are not very readable)
* When ready to release, go to Releases -> Edit release -> Publish release. This creates the release and the tag.
* The tag will trigger the release workflow for publishing wheels/crates.

