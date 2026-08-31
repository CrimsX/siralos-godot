# siralos-godot

Godot domain — standalone Plugin crate extracted from [Siralos](https://github.com/CrimsX/Siralos) monorepo.

**Origin:** `crates/siralos-godot` in Siralos monorepo at `e2c3540` (Stage 6 Verified, corpus v52/320, 315/315, decision 60 inventory 41 files). Extraction per [decisions 34/37/61](../../siralos/docs/wayfinder/decisions/61-siralos-godot-externalization-entry-review.md) (C1–C6).

**Boundary:** `siralos:domain-abi@1.0.0` (`crates/siralos-adapters/wit/domain-abi.wit` canonical in monorepo until ADR 0036 §32 unification). This crate re-exports the 6+3 R8/R9 Godot surfaces plus `runtime_adapter` (Stage 4.3):

- R8 (6): discovery/profiling, recovery, knowledge, diagnostics, LSP, scene/resource intelligence
- R9 (3): review/impact, scene_mutation prepare, develop plan
- 4.3: `decide_godot_launch` over generic `siralos-core::runtime`

**Dependency:** `siralos-godot → siralos-core` only (local dev via `path = "../siralos/crates/siralos-core"`; published consumers via git rev as pinned by monorepo `Cargo.lock` + `cargo deny` per decision 61 C3).

**Monorepo pin:** `siralos-godot = { git = "https://github.com/CrimsX/siralos-godot", rev = "<sha>" }` in monorepo `Cargo.toml [workspace.dependencies]` (never `branch = "main"`, never committed `path =`).

**Verification:** `cargo fmt --all --check` + `cargo clippy --workspace --all-targets --all-features -- -D warnings` + `cargo test --workspace --all-features` (72 tests) — zero spawn paths, `forbid(unsafe_code)` preserved.

**License:** Same as Siralos (currently no published license — owner `CrimsX`, see monorepo `README.md:330`).

**Host pin:** `siralos.toml [plugins.godot] { digest }` + `siralos.lock` via `DomainHost::install` (lstat/is_path_within/SHA-256 before `Enabled→Active` per decisions 38/39) remains Host authority gate.
