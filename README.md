# daykeep-data

Static tax-parameters data for the [DayKeep](https://github.com/Just-Vlados/daykeep) iOS app,
served via GitHub Pages:

```
https://just-vlados.github.io/daykeep-data/tax-parameters.json
```

## Update workflow (Budget day / fiscal events)

1. Edit `tax-parameters.json` — ground truth is the gov.uk pages listed in
   DayKeep's `PROJECT_SPEC.md` §4 "Primary data sources".
2. **Bump `dataVersion`** (the app only adopts strictly newer versions) and set
   `updated` to today's date.
3. Add any `alerts` entries (see the schema in `PROJECT_SPEC.md` §5).
4. Run DayKeep's regression suite against the new file before pushing:
   `cd TaxEngine && swift test`.
5. Commit and push — Pages redeploys automatically; apps pick it up on next
   launch or background refresh. No app release needed.

`schemaVersion` only changes on breaking structural changes, coordinated with
an app update that can decode both.
