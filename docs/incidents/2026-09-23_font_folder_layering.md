# Incident — Font folder layering / historical OTF directories

Date: 2026-09-23
Status: OBSERVED / cleanup intentionally deferred

## Observed

On macOS, historical publishing builds left multiple font-related directories under the user font area, including names resembling:

- `共犯者_Prototype01/`
- `共犯者_Prototype01_v3/`

The visible top level did not make the expected Noto OTF provenance obvious, while InDesign builds could still pass the DESIGNLOCK font verification.

There were also historical font assets from earlier workflows (for example GenWanMin-family files), so **directory appearance alone is not enough to infer which font files InDesign is actively using**.

## Unknown

- Which exact on-disk font file instance InDesign resolves for every active family/style.
- Whether the historical directories are exact duplicates.
- Whether either directory contains files still depended on by the current build.
- Whether deleting either directory would affect font discovery/cache behavior.

## Decision

**Do not clean these folders yet.**

Classification:
- `LEGACY_DEBT`
- `MACHINE_SPIRIT_RISK`
- change risk: R3

The correct next step is provenance/inventory, not deletion.

## Future installer requirements

1. Install only exact font files it owns; never copy an entire prototype/build package into the Fonts directory.
2. Write `FONT_INSTALL_MANIFEST.json` with family, style, filename, version, sha256, install path, installer version.
3. Keep core design fonts separate from archival/extra fonts.
4. Verify fonts by **active family/style in InDesign**, not only Finder paths.
5. Treat cleanup as a separate explicit command.
6. Cleanup may delete only files/directories owned by a known installer manifest, proven not active, and recoverable.

## Adversarial test to add

Simulate duplicate historical font folders, nested OTF folders, stale installer directories, and the same family available from multiple locations.

Expected behavior: build remains deterministic; QA reports provenance ambiguity; installer does not silently delete old assets.
