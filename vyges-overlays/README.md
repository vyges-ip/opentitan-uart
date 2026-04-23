# Vyges overlays — opentitan-uart

Same-name overrides that mask upstream files at vendor time.
Declared in `vyges-metadata.json → vyges_overlays[]`.

Upstream-sync policy: pulls proceed normally; any upstream change
to a path listed under `vyges_overlays[].replaces` is flagged for
human review — upstream may have fixed the original issue, making
the overlay obsolete.

## Files

| File | Replaces | Reason |
|---|---|---|
| `uart_reg_top.sv` | `rtl/uart_reg_top.sv` | Upstream tie-off `assign unused_policy_sel = ^racl_policies_i` uses a struct-level XOR reduction that Vivado 2025.2 rejects as unsupported. Replaced with `assign unused_policy_sel = 1'b0` which RACL-disabled builds accept cleanly. |
