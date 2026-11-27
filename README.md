# Window Walk

A community-run service that helps residents discover, connect with and keep supporting local businesses that sell goods, starting in one Portland neighborhood. Browsing should feel like window shopping, with character over catalog.

The project is in early planning. See the [concept](docs/concept/window-walk-concept.md) for the full picture.

## Repository layout

| Path | What lives there |
| --- | --- |
| [TODO.md](TODO.md) | The single list of open conceptual, organizational and technical work |
| [docs/](docs/) | Research and planning documentation |
| [docs/concept/](docs/concept/) | What Window Walk is, who it serves, and how it should work |
| [docs/research/](docs/research/) | Landscape, past attempts, the Portland ecosystem, data sources, naming |
| [docs/architecture/](docs/architecture/) | Technical design: components, data model, key flows |
| [docs/decisions/](docs/decisions/) | Short records of decisions as open questions get settled |
| `poc/` | Proof-of-concept code: small, throwaway experiments that answer one question each. Not published here (see below) |

Production code will get its own top-level home once Phase 1 work begins. Proofs of concept stay in `poc/` so experiments never get mixed up with what ships.

**About `poc/`:** the proof-of-concept code, including a clickable shopper prototype built on real Portland shop data, is kept on a separate branch that isn't published. Links to `poc/` in [TODO.md](TODO.md) and the docs point to that unpublished code.
