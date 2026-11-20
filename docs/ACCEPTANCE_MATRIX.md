# Quality Acceptance & Red-Team Verification Matrix

## Quality Gate Checklist

| Test ID | Description | Acceptance Criteria | Status |
| :--- | :--- | :--- | :--- |
| STAR-AT-001 | Static site routing | All published routes resolve without 404s | VERIFIED |
| STAR-AT-002 | Atlas search | Querying 'Ori' returns Orion (NQ1, 594 sq deg) | VERIFIED |
| STAR-AT-003 | Constellation editorial | Unique scientific content and mythological attribution | VERIFIED |
| STAR-AT-004 | Sky canvas initialization | Canvas initializes with observer coordinates and time | VERIFIED |
| STAR-AT-005 | Time evolution | Sky objects rotate in correct direction across UTC delta | VERIFIED |
| STAR-AT-006 | Observer latitude | Southern hemisphere shows Crux above horizon, Polaris below | VERIFIED |
| STAR-AT-007 | Star selection | Pointer selection and accessible list parity | VERIFIED |
| STAR-AT-008 | Boundary overlay | Toggleable IAU 88 boundary outlines | VERIFIED |
| STAR-AT-013 | Source provenance | CDS VizieR VI/49 and IAU 1922 citations displayed | VERIFIED |
| STAR-AT-015 | Secret leakage prevention | Zero private API secrets or environment variables in bundle | VERIFIED |

## Red-Team Safety Controls
- Hemispheric inversion guard: verified Azimuth zero points true North.
- Boundary wrap: continuous azimuth wrap at 360/0 deg and RA wrap at 24h/0h without visual tearing.
- Offline behavior: core catalog operates 100% offline without remote network dependencies.
