# Unreleased

## Added

- Added two-arity version of `apply-impulse!`, defaults to `wake? false`
- Implement `joints` for body instances. This returns `nil`, since joints are
  part of the world, but it allows code to recurse safely by calling `bodies`
  and `joints` on various entities

## Fixed

- Make return type tags in protocols fully qualified, Clojure seems to like that
  better
- Fix PrismaticJointDef creation, some vector fields are final, we can only
  mutate the existing instance
- Wrap `destroy` in a mutex, to allow for rendering of a consistent world view
- Prevent exceptions in the Clojure2D renderer when the world is being changed
  underneath it

## Changed

- When adding bodies/joints that have an `:id`, remove any bodies/joints with
  the same `:id`. This is to ensure uniqueness, but also makes for a nicer REPL
  experience
- When converting to edn (IValue), include :joints for world, and omit default
  values for body

# 0.6.31 (2022-03-14 / 8d5ff0e)

## Added

- [Clojure2d](https://github.com/Clojure2D/clojure2d) support
- `math/vec-mul`, and shorter math aliases (`v+`, `v*`, `m*`, etc)

## Changed

- Breaking! Return maps from `raycast-seq`, rather than fixtures, allow setting
  raycast-callback return value to set filtering behavior.

# 0.5.23 (2022-03-11 / 7b55d21)

## Fixed

- Rewrite to a single :require form to appease cljdoc

# 0.4.19 (2022-03-11 / 48f72c2)

## Fixed

- Fix cljdoc build
- Fix platformer demo, load images from resources (jar) instead of filesystem
- Switch to Quil 4 snapshot

# 0.1.9 (2022-03-11 / 9627741)

## Added

- First release, with jBox2D (clj) and Planck.js (cljs) support