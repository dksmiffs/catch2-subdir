# Catch2 v3 air-gapped use without Git submodules

Alternative to [simplest known](https://github.com/dksmiffs/simplest-catch2v3) Catch2 v3 usage designed to work in air-gapped environments. This approach doesn't use Git submodules.  It uses a Git shallow clone to receive one and only one version of Catch2.  Assuming some Linux flavor:

### Prepare while online
1. Clone this repo to your local machine
1. `mkdir -p external/Catch2` from the top level of your working directory
1. `cd external/Catch2`
1. `git clone git@github.com:catchorg/Catch2.git --branch v3.4.0 --single-branch --depth 1 v3.4.0`
1. Create a tarball of this working directory, including `src` and `external` subdirectories, sneakernet it to the air-gapped system

### On air-gapped system
1. Receive and extract the sneakernet tarball
1. `mkdir build` as a sibling to the `src` directory in your working directory
1. `cd build`
1. `cmake -S ../ -B .`
1. `cmake --build .`
1. `./src/tests`
