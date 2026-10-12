# Repository audit and portfolio selection

Date: 2026-10-12. Account: Korniszon99. Scope: 11 owned repositories accessible through the connected GitHub account.

**Publication status:** 11 pull requests are open on separate review branches. Their application checks and current-source secret scans passed on GitHub. All PRs are ready for review; no default branch was merged and no exposed runtime credential was rotated.

## Portfolio priorities

| Priority | Project | Evidence and decision |
| --- | --- | --- |
| 1 | nerf_vs_gaussian | Strongest direct 3D CV/AI fit: dataset/pose models, Nerfstudio runner, metrics/artifacts and a Django experiment UI. 103 web/service tests pass after repairs, using mocked GPU tooling. Publish real held-out reconstruction benchmarks before claiming comparative performance. |
| 2 | fotogrametia_projekt_nalotu | Relevant camera/photogrammetry geometry and image acquisition planning. Four tests cover units, overlap, invalid inputs and CSRF. Present as an educational model, with reproducible numerical examples and existing screenshots. |
| 3 | eurorace_backend | Supporting spatial backend: PostGIS, REST, WebSockets and event data. Demonstrates engineering around spatial/visual workloads. PostGIS integration tests, migration checks and a Docker build passed on GitHub; deployment configuration remains a readiness gate. |
| Supporting | Geometria_Obliczeniowa | Small orientation predicate demo; three tests pass. Useful for foundations, too limited to lead the portfolio. |
| Supporting | PW_hub_flutter | UI/mobile prototype; the README and smoke test were replaced. Full historical scan and device validation remain incomplete. |
| Supporting | SSPWPhotoTaskGame / PWGame | Related event photo-game code; show one case study with accurate contribution/ownership, rather than two nearly identical projects. |
| Supporting | varso_mapka | Full-stack event experience; repaired password handling and write authorization. Not an AI project. |
| Supporting | training-azure-102026 | Teaching/DevOps contribution with attributed upstream sample. Do not describe the entire sample architecture as original work. |
| Presentation | korneliusz.musial / Korniszon99 | Website/profile presentation. The website redesign is a separate planned task. |

## Security findings

| Repository | Finding | Source remediation | Operator action |
| --- | --- | --- | --- |
| nerf_vs_gaussian | Hardcoded Django key; tracked experiment SQLite database | Environment configuration; production staff access; database removed from current tree | Rotate any deployed key; retain/migrate required experiment data from the old revision before replacing a deployment |
| fotogrametia_projekt_nalotu | Hardcoded key, DEBUG defaults, old dependencies | Explicit environment modes, updated packages, CSRF, safer Gunicorn container | Configure HTTPS, persistent storage and a new key |
| eurorace_backend | Hardcoded key, wildcard hosts/CORS, inconsistent dependency manifests; authorization gaps | Environment settings, one dependency manifest, owner-scoped location access, staff-only task mutation, coordinate validation | Rotate deployed key; verify frontend/integration behavior and database migrations |
| varso_mapka | Public admin/team/station passwords; unauthenticated whole-state writes | Server authentication, scoped writes, image restrictions and regression test | Rotate credentials, validate browser event flows, provision backups |
| SSPWPhotoTaskGame / PWGame | Default admin/admin and demo registration-code bootstrap; debug endpoint in SSPW copy; missing tracked SQLite schema | Explicit bootstrap, no recurring password reset, schema and smoke check; debug removed; HTTP file protections | Change existing privileged passwords/codes; test the complete game flow in staging |

Documentation token examples and the copied CircleCI badge were scanner candidates, not proof of active provider credentials. They were replaced/removed. No found credential was used or tested against a live provider. No Git history was rewritten.

## Dependency audit

| Scope | Before | After / limitation |
| --- | --- | --- |
| varso_mapka npm lock | 4 affected packages: 1 critical, 1 high, 2 moderate | 0 known findings after updating Express/Multer and the lock |
| Azure training npm lock | 138 affected packages, including 6 critical and 87 high | 20 moderate development-tooling findings; no high/critical findings after updates and removal of unused CLI/SWC tooling |
| Planner Python resolution | Old pinned Django 4.2.7 and image/numeric stack | Updated bounded requirements; pip-audit reported no known findings in the resolved set |
| NeRF web Python resolution | Runtime and test packages mixed | Runtime/dev separation; pip-audit reported no known findings in the resolved web/test set. Nerfstudio/PyTorch/CUDA environment was not installed or audited |
| Geometry Python resolution | No dependency manifest | Runtime/dev manifests; pip-audit reported no known findings in the resolved set |
| EuroRace | Duplicate manifests; non-canonical django-rest-framework package; Docker list drift | Canonical djangorestframework and one manifest. GitHub CI passed dependency installation, PostGIS integration tests, migration checks, a Docker build and a dependency audit. Those checks were unavailable in the local environment |
| Flutter | Unused cupertino_icons; stale template test | Removed unused icon dependency, replaced smoke test and added CI; GitHub CI passed Flutter analysis, widget tests and the web build; physical-device/release-signing validation remains unverified |

Counts refer to affected dependency packages, not distinct advisories. Audits describe the resolved versions on this date and do not establish exploitability or permanent safety.

## Verification and operational limits

Local verification: 103 NeRF tests, four planner tests, three geometry tests and one Varso security integration test pass. NeRF/planner migration-drift checks pass. NeRF/planner production checks have two intentionally unset, domain-dependent HSTS subdomain/preload warnings. Azure's NestJS tests/build, Fastify root test and Vite build pass after dependency updates.

PHP runtime, Flutter SDK, Docker and PostGIS integration were not available locally. New CI workflows provide those checks where supported. No live service was deployed or production credential rotated during the audit.

Git history was scanned from all fetched refs of the ten fully materialized mirrors. Flutter's partial mirror was incomplete: automatic review rejected the implicit network fetch during the historical scan. Its downloaded current text was scanned locally; full Flutter history remains unverified. Binary assets, external hosted services and actual runtime configurations were not comprehensively audited.

The current NeRF database snapshot contained no user/session rows, three datasets and twelve runs. Its historical copies remain available in Git; removing the file from the source tree is not a history purge.

## Published changes and GitHub verification

| Repository | Pull request | GitHub CI |
| --- | --- | --- |
| eurorace_backend | [#1](https://github.com/Korniszon99/eurorace_backend/pull/1) | Passed on the current head |
| fotogrametia_projekt_nalotu | [#1](https://github.com/Korniszon99/fotogrametia_projekt_nalotu/pull/1) | Passed on the current head |
| Geometria_Obliczeniowa | [#1](https://github.com/Korniszon99/Geometria_Obliczeniowa/pull/1) | Passed on the current head |
| korneliusz.musial | [#5](https://github.com/Korniszon99/korneliusz.musial/pull/5) | Passed on the current head |
| Korniszon99 | [#1](https://github.com/Korniszon99/Korniszon99/pull/1) | Passed on the current head |
| nerf_vs_gaussian | [#10](https://github.com/Korniszon99/nerf_vs_gaussian/pull/10) | Passed on the current head |
| PWGame | [#1](https://github.com/Korniszon99/PWGame/pull/1) | Passed on the current head |
| PW_hub_flutter | [#1](https://github.com/Korniszon99/PW_hub_flutter/pull/1) | Passed on the current head |
| SSPWPhotoTaskGame | [#3](https://github.com/Korniszon99/SSPWPhotoTaskGame/pull/3) | Passed on the current head |
| training-azure-102026 | [#2](https://github.com/Korniszon99/training-azure-102026/pull/2) | Passed on the current head |
| varso_mapka | [#1](https://github.com/Korniszon99/varso_mapka/pull/1) | Passed on the current head |

EuroRace includes regression checks for location ownership, authenticated identity binding, malformed coordinate payloads and restricted task mutation. Both PHP bootstraps check absence of default credentials, explicit creation from operator input and preservation of existing account passwords. The SSPW SQLite URL bug found by CI was fixed; the rerun passed.

Passing CI is not a production-readiness guarantee. Complete deployment-specific credential rotation, TLS/storage configuration and browser/device checks before rollout. Existing workflows can deploy from a default-branch merge, so no automatic merge or production rollout was performed.

## Next portfolio work

1. Produce one reproducible NeRF/Gaussian comparison with the same images, poses, evaluation split and training budget; record hardware, time, memory, held-out metrics and failure cases.
2. Record a short reconstruction comparison and a planner demo with numerical examples.
3. Document the exact personal contribution and context of EuroRace and team projects.
4. Rewrite the portfolio page around these three case studies, with supporting projects presented briefly.
