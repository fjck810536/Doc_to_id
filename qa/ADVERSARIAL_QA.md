# Adversarial QA Checklist

把真實事故變成 engine regression tests。

## Session / state
- New chat with zero memory.
- Book Project not specified.
- Book Project specified by Drive link.
- Missing CURRENT_STATE.
- LAST_GOOD_BUILD older than latest failed build.

## Regression slicing
- Synthetic article kicker inserted around slice boundary.
- Special-layout placeholder inserted around slice boundary.
- Expected Golden Regression remains unchanged unless the reference itself is intentionally versioned.

## Font environment
- Duplicate versioned font folders.
- Nested OTF directories.
- Stale legacy font family still installed.
- Same family/style available from multiple locations.
- Active font differs from expected design lock.
- Font file exists but InDesign cannot resolve it.
- InDesign resolves correct family even when Finder layout is messy.

## Shell / launcher
- UTF-8 BOM + PASS.
- CRLF status file.
- damaged cached ZIP.
- Bash 3.2 + set -u.
- Unicode text adjacent to shell variable.
- Finder routes JSX to wrong Adobe host.

## Full book
- Regression PASS + Full QA FAIL.
- Page with text but no paragraph start.
- article / part / chapter page classes use distinct frame geometry.
- long paragraph crosses page boundary.
- special layout source is unverified.
- running-head title changes after editorial rename.

## Expected policy

A failure must be classified as one of:
- runtime defect
- source defect
- validator false positive
- environment ambiguity
- human visual-QA item

Do not fix by broad refactor until classification is known.
