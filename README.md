# xp-split

A C++ quant project split into **three independently-versioned, independently-owned
repositories**, assembled into standalone projects by tag. This repo is just the front door —
the three real repos are included here as git **submodules**.

## Repositories

| Submodule | Owner | Holds | Tagged |
|---|---|---|---|
| [`xp-platform`](../../xp-platform) | build engineers | toolchains, triplets, presets, CMake modules (`xp_pricer`), the review guards | `platform-vX.Y.Z` |
| [`xp-pricer-templates`](../../xp-pricer-templates) | quant developers | pricer code — one `xp_pricer()` call per method | `pricers-vX.Y.Z` |
| [`xp-backstage`](../../xp-backstage) | devops | the scaffolder (`generate.sh`) + self-service portal | `scaffold-vX.Y.Z` |

## Clone with submodules

```sh
git clone --recurse-submodules git@github.com:srikantharun/xp-split.git
# or, if you already cloned without them:
git submodule update --init --recursive
```

## The idea in one paragraph

Quant developers write pricers (**xp-pricer-templates**); build engineers own *how* things compile
(**xp-platform**); devops own scaffolding (**xp-backstage**). A generated project **pins a platform
tag and a pricers tag** and copies the platform in as real content — so "how it builds" and "what it
computes" evolve on independent release cadences, and the build machinery can never be edited by a
developer (enforced by the review guards in `xp-platform`). The three submodules above are pinned to
specific commits, so this front door always points at a known-good combination.
