# Virtual file system for ICE

ICE aims to be an adaptation of Nix for fast incremental builds. We want to use existing Nix
infrastructure as much as possible. Currently, there is the following problem in ICE:
 - The Nix store needs a full copy of all sources when even a single file changed.
   This means that developing packages incrementally, where e.g. a single file in a
   dependency is updated, the whole dependency needs to be rebuilt from scratch.
   A symptom is described for example in [this issue](https://github.com/NixOS/nix/issues/7284).

The goal of ice-virtualfs is to solve this problem by providing a concept of overlays
for directories, as well as integrating into the concept of incremental computation of ICE.

