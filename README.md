# catept-plugin-kolmogorov-complexity

Sibling repo of [`jagg-ix/catept-main`](https://github.com/jagg-ix/catept-main).
15th plugin extracted under [Target 5](https://github.com/jagg-ix/catept-main/blob/main/docs/architecture/targets/target-4-plan.md)
(Phase 2 / scale-out, T5 follow-on).

## What this provides

Abstract integration contract for the upstream
`kolmogorov-complexity-lean-inspect` package (`KolmogorovMathlib`)
against CATEPT's information-theoretic foundations.

| Theorem | Statement |
|---|---|
| `kolmogorovComplexity_integration_contract` | `KolmogorovComplexityWitness → KolmogorovComplexityIntegrationContract w` (term-mode) |

Plus `KolmogorovComplexityWitness` (6 fields: universal machine,
complexity function, incompressibility, Chaitin Ω, uncomputability,
2nd incompleteness via K).

The proof is structurally trivial and **depends on no axioms**.

## Dependencies

| Pin | Version |
|---|---|
| Lean toolchain | `leanprover/lean4:v4.29.0` |
| Mathlib | `8a178386ffc0f5fef0b77738bb5449d50efeea95` |

No upstream `KolmogorovMathlib` pin yet (targets v4.29.0-rc8; needs
stable-v4.29.0 release).

## Re-import contract

```lean
require «catept-plugin-kolmogorov-complexity» from git
  "https://github.com/jagg-ix/catept-plugin-kolmogorov-complexity.git" @ "<sha>"
```

```lean
import CATEPTPluginKolmogorovComplexity.IntegrationBridge

open CATEPTPluginKolmogorovComplexity (
  KolmogorovComplexityWitness KolmogorovComplexityIntegrationContract
  kolmogorovComplexity_integration_contract)
```

## Build locally

```bash
lake exe cache get
lake build
```

## License

MIT, matching `catept-main`.
