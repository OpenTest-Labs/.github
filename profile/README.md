<p align="center">
  <img src="./assets/opentest-brand-loop-256.png" width="144" alt="OpenTest brand test-loop icon" />
</p>

# OpenTest

OpenTest is a modular ecosystem for laboratory optical-module testing. Its repositories deliberately separate reusable business services, instrument integration, optical-path design, read-only transceiver interpretation, deterministic measurement algorithms, cryptographic utilities, the assembled test platform, and shared visual assets.

It is not a monorepo. Each project owns its source code, releases, architecture decisions, risks, and detailed design documents.

## Ecosystem map

```mermaid
flowchart TB
    FOUNDATION["OpenTest.Foundation<br/>Identity, facilities, machines, fleet,<br/>and the ErrorCatalog module"]
    INSTRUMENTS["OpenTest.Instruments<br/>Device contracts, drivers, and lab sharing"]
    OPTICAL["OpenTest.OpticalPath<br/>Optical topology design and validation"]
    TRANSCEIVERS["OpenTest.Transceivers<br/>Read-only SFF/CMIS module interpretation"]
    ALGORITHMS["OpenTest.Algorithms<br/>Pure measurement calculation and diagnostics"]
    CRYPTO["OpenTest.Crypto<br/>Cryptographic compatibility and utility tools"]
    TESTBENCH["OpenTest.TestBench<br/>Test platform: orchestration, integration, reports"]
    TESTING["OpenTest.TestingPlatform<br/>Target server-side test domain (design; extraction later)"]
    DESIGN["opentest.design-hub<br/>Brand assets"]

    DESIGN -. brand assets .-> FOUNDATION
    DESIGN -. brand assets .-> OPTICAL
    DESIGN -. brand assets .-> CRYPTO
    FOUNDATION --> TESTBENCH
    INSTRUMENTS --> TESTBENCH
    OPTICAL --> TESTBENCH
    TRANSCEIVERS --> TESTBENCH
    ALGORITHMS --> TESTBENCH
    CRYPTO --> TESTBENCH
    INSTRUMENTS -. "implements IModuleMemoryReader" .-> TRANSCEIVERS
    TESTING -. "target domain design" .-> TESTBENCH
```

The arrows express integration through published packages and stable contracts, not source-code coupling. Domain projects publish focused capabilities; TestBench owns test sequencing, product rules, final pass/fail decisions, reporting, and integration verification.

## Repositories

| Repository | Responsibility | Deliberate boundary |
| --- | --- | --- |
| [OpenTest.Foundation](https://github.com/OpenTest-Labs/opentest.foundation) | Identity, facilities, machine management, fleet management, and reusable platform services. It also hosts the ErrorCatalog business module. | It does not own instrument protocols, optical calculations, or test execution. |
| [OpenTest.Instruments](https://github.com/OpenTest-Labs/opentest.instruments) | Instrument contracts, Windows-capable drivers, and shared-lab instrument hosting. | It does not own product test logic or measurement-result interpretation. |
| [OpenTest.OpticalPath](https://github.com/OpenTest-Labs/opentest.opticalpath) | Versioned optical topology contracts, route validation, path plans, and the offline designer. | It does not bind logical paths to physical drivers or perform calibrated measurements. |
| [OpenTest.Transceivers](https://github.com/OpenTest-Labs/opentest.transceivers) | Standards-oriented, transport-independent read-only interpretation of pluggable transceiver module memory (SFF-8472 and CMIS): identity, monitoring, thresholds, alarms, applications, and datapaths as immutable snapshots with stable diagnostics. | It does not own physical I2C/USB adapters, instrument sessions, writes or firmware, product limits, or final pass/fail. |
| [OpenTest.Algorithms](https://github.com/OpenTest-Labs/opentest.algorithms) | Pure, reproducible calculations, fitting, evidence, and diagnostics for completed measurement data. | It does not acquire data, parse device exports, control instruments, or decide product pass/fail. |
| [OpenTest.Crypto](https://github.com/OpenTest-Labs/opentest.crypto) | Cryptographic compatibility helpers and narrowly scoped cryptographic utilities. | It does not own licensing, remote KMS/HSM, or organization-wide key governance. |
| [OpenTest.TestBench](https://github.com/OpenTest-Labs/opentest.testbench) | The assembled test platform: plugin-based test orchestration, MES and system integration, the test framework, and reporting over the other projects. | It does not own the domain capabilities it composes, nor instrument protocols or measurement algorithms. |
| [OpenTest.TestingPlatform](https://github.com/OpenTest-Labs/opentest.testing-platform) | Target design for the server-side test-platform domain: test schemes and product applicability, versioned plan releases, test-case package dependencies, Bench/Resource configuration, MES/simulated context, and run summaries. | It is not a current build or runtime dependency; live execution and device drivers stay in TestBench, and in-place modernization precedes any extraction. |
| [opentest.design-hub](https://github.com/OpenTest-Labs/opentest.design-hub) | OpenTest brand assets. | It does not replace project-level architecture or implementation documentation. |
| `opentest.skills` | Reserved repository for OpenTest-specific reusable skills and workflow assets. It has no published content yet. | It is not an application runtime dependency. |
| `opentest.testpackage-demo` | Reserved demonstration repository for an example published TestCase package. Scaffolded with a license and ignore rules only; it has no published content yet. | It is not a build or runtime dependency of any project. |

> ErrorCatalog is no longer a standalone repository. It is composed into `opentest.foundation` as the `modules/error-catalog/` business module, per Foundation ADR-0010. Its consumer contracts are published independently as `OpenTest.ErrorCatalog.Contracts`, the renamed successor of the retired `OpenTest.ErrorCodes.Contracts` package.

## Tooling direction

Small, single-purpose developer and desktop tools normally live with the domain they explain or validate. Cross-domain orchestration, integrated regression, and system-level validation belong to TestBench, which assembles the other projects.

| Project | Planned focused tooling |
| --- | --- |
| OpenTest.Algorithms | A scriptable algorithm CLI, a result-explanation workbench, and golden-fixture/method-version difference review. |
| OpenTest.Transceivers | A developer fixture tool that imports sanitized CMIS-DUMP memory images, and (later) a read-only snapshot inspection harness. |
| OpenTest.Crypto | A crypto CLI, ciphertext inspection and controlled migration, and lightweight local key use with a clear boundary from remote key governance. |
| OpenTest.TestBench | Test orchestration, integrated regression, test reporting, product rules, and final pass/fail authority. |

These are planning directions, not released components. Their detailed scope, implementation decisions, and acceptance criteria are recorded in the relevant project repository when work is approved.

## Documentation and governance

- Durable, project-specific decisions belong in that repository's `docs/design/`, `docs/adr/`, and `docs/ledger/` records.
- Shared engineering rules remain in the versioned [`dev-standards`](https://github.com/xin-pu/dev-standards) knowledge base; each maintained repository records its adopted revision and any approved project-specific deviations.
- A cross-project capability should depend on published contracts or stable interfaces, not another repository's internal implementation details.

## Brand

The OpenTest glyph is locked: do not alter its shapes, proportions, or red status dot. Production assets and usage guidance live in [opentest.design-hub](https://github.com/OpenTest-Labs/opentest.design-hub).
