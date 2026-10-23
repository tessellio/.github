## Summary

<!-- What does this PR change and why? -->

## Type of change

- [ ] Specification (contract change)
- [ ] Reference implementation (Rust / TypeScript)
- [ ] Conformance corpus / vectors
- [ ] Tooling / CLI / bench
- [ ] Documentation

## Checklist

- [ ] Specification and implementations agree (or a deliberate divergence is documented)
- [ ] Conformance corpus regenerated and byte-identical (`scripts/verify.sh`)
- [ ] `cargo test` / `npm test` pass locally
- [ ] `cargo clippy --all-targets -- -D warnings` / `npm run typecheck` pass
- [ ] Byte budgets and measured bounds still hold (`tessellio-core bench`)

## Related issues

Closes #