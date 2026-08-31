# siralos-godot architecture

Standalone extraction of `crates/siralos-godot` from Siralos monorepo.

- Dependency direction: `siralos-godot → siralos-core` only
- Host boundary: `siralos:domain-abi@1.0.0` canonical in monorepo `crates/siralos-adapters/wit/domain-abi.wit`
- See monorepo `ARCHITECTURE.md` and `docs/architecture/README.md` for system design
- Monorepo `scripts/check-rust-architecture.mjs` EXPECTED_CRATES will drop `crates/siralos-godot` after cutover (decision 62 §2 phase C)
