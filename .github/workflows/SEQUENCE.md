# SEQUENCE

Dependency order across `src/` — common infra, endpoints, and subendpoints.
`A ─→ B` means B is built on A: every endpoint reads the common `storage` +
`routing` state, and a carrier/tenant write cascades into its subendpoint
builder (`carriers/merge`, `tenants/wan`).

```text
api/common/storage ─┐
api/common/routing ─┤
                    ├─→ api/endpoints/carriers ─→ api/endpoints/carriers/merge
                    ├─→ api/endpoints/csps
                    └─→ api/endpoints/tenants ──→ api/endpoints/tenants/wan
```
