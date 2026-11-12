# The `retroteca` branch

[nxnative](https://github.com/seedds/nxnative) by seedds (MIT), as [Retroteca](https://github.com/Gionnio) builds it for Apple M1 and M2 Macs: upstream `main` with a few open pull requests applied on top, nothing else. Each one stays credited to its author and is dropped from this branch once upstream merges it or no longer needs it.

| Pull request | What it does | Why here |
|---|---|---|
| [#1459](https://github.com/seedds/nxnative/pull/1459) | `DM_UPSCALER=metalfx` also takes agl's `agl_ndsr_vr` upscaler networks, with their squared colour | On upstream `main` the option does nothing for games using those networks (issue [#1911](https://github.com/seedds/nxnative/issues/1911)); the network costs about 5 ms a frame on an M1 Pro (issue [#2501](https://github.com/seedds/nxnative/issues/2501)) |
| [#2487](https://github.com/seedds/nxnative/pull/2487) | Compute kernels above 384 threads carry their local size, so their pipelines allow the dispatch on GPUs without Dynamic Caching | On M1 and M2 such kernels ran no invocation, and volumetric effects disappeared (issue [#2425](https://github.com/seedds/nxnative/issues/2425)) |

The branch is rebuilt from upstream `main` each time: `git checkout -B retroteca upstream/main`, the pull requests' commits picked in the order above, then `python3 dm/gfx/tools/dmsh_chain.py --header` for the shader chain. The tests the pull requests name are run before the branch is pushed.

Everything else, including how to build and play, is upstream's: see [README.md](README.md). No game, firmware or key is part of this branch.
