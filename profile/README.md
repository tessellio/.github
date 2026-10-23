<div align="center">

# Tessellio

**A screen codec that paints a surface as independently-placed tiles of cells.**

[![Spec](https://img.shields.io/badge/spec-in%20development-blue)](https://github.com/tessellio/tessellio)
[![License: PolyForm NC](https://img.shields.io/badge/license-PolyForm%20NC-orange)](https://github.com/tessellio/tessellio-core/blob/main/LICENSE)

</div>

---

## What Tessellio is

Tessellio moves a changing surface over a link that loses, reorders, or delays. It paints a surface as **tiles of cells** and moves only the tiles that changed. An update is either:

- **self-contained** — it establishes the whole surface, or
- **chained** — it continues exactly the surface the named base established.

The codec is **not a transport**: it does not frame, address, retransmit, reorder, pace, measure, or acknowledge anything. A transport moves the codec's updates as opaque bytes.

## The one property everything rests on

Change detection compares the same 16-bit cells the receiver's surface holds, and the sender's reference advances only over the cells an update actually carried. So at every instant the receiver's surface equals the sender's reference, cell for cell — and **one lost update heals**, because the sender can roll its reference back and re-encode the difference.

That property is §5.3 of the specification, and it is what the reference implementation's self-check verifies after every update it builds.

## Repositories

| Repository | Language | What it holds |
|---|---|---|
| [`tessellio`](https://github.com/tessellio/tessellio) | Markdown | The normative specification |
| [`tessellio-core`](https://github.com/tessellio/tessellio-core) | Rust | Sans-IO reference implementation + `tessellio-core` CLI + bench |
| [`tessellio-ts`](https://github.com/tessellio/tessellio-ts) | TypeScript | Browser implementation + `SurfaceStream` |
| [`tessellio-proto`](https://github.com/tessellio/tessellio-proto) | Protobuf | Update envelope wire schema |
| [`tessellio-conformance`](https://github.com/tessellio/tessellio-conformance) | JavaScript | Hand-derived vectors + generated corpus + gate |
| [`tessellio-demo`](https://github.com/tessellio/tessellio-demo) | TypeScript | Demo: a surface painted from an update + its byte cost |

## Status

- **Wire format:** frozen by the specification.
- **Implementation:** in development, moving tag `v0.1.0`.
- **Checks:** local (`scripts/verify.sh`); no continuous integration yet.

## Quick start

```bash
# Rust core
cargo build --release -p tessellio-core
./target/release/tessellio-core bench --iterations 5
./target/release/tessellio-core encode --scene office --width 640 --height 360

# TypeScript (browser)
npm install && npm test
```

## License

Reference implementations: **PolyForm Noncommercial 1.0.0** (commercial use requires a separate license). See [LICENSE](https://github.com/tessellio/tessellio-core/blob/main/LICENSE).

## Links

- 📖 [Specification](https://github.com/tessellio/tessellio/blob/main/spec/00-index.md)
- 🛠️ [CLI docs](https://github.com/tessellio/tessellio-core/blob/main/docs/cli.md)
- 🤝 [Contributing](https://github.com/tessellio/tessellio/blob/main/CONTRIBUTING.md)
- 🔒 [Security policy](https://github.com/tessellio/tessellio/blob/main/SECURITY.md)
