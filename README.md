# Returns

The common returns vocabulary -- the returns customers start, the items being sent back and the reasons they give -- distilled from the APIs that already exist. Refunds belong to payments and return labels to shipping. Part of [Schema Commons](https://github.com/api-commons/schema-commons),
published by the [API Commons](https://apicommons.org).

Built from the providers tagged Returns, Reverse Logistics, Returns Management, RMA, Exchanges, Post-Purchase, E-Commerce, Order Management, Fulfillment in [APIs.io](https://apis.io) that
publish their own OpenAPI. Only harvested contracts count -- nothing API Evangelist
generated. Every number below is a count of providers.

## What the market already agrees on

<!-- commons:summary -->
| Concept | Expose it | Readable schema | Core properties (share) | Collection named |
| --- | ---: | ---: | --- | --- |
| return_request | 32 | 27 | id 63%, status 63%, created_at 52% | returns 20, return 15, return_requests 1, rmas 1 |

Cohort: 370 providers with harvested OpenAPI, 32 crosswalks. Of the providers exposing a return_request: 75% create, 50% list, 53% fetch, 16% update, 12% delete. Generated 2026-11-11 by build.py.
<!-- /commons:summary -->

Shares are of the providers with a readable resource schema for that concept. The
extended tier and the long tail of every concept are in [profile.yml](profile.yml).

## What the measurement shows

- A return agrees on id, status and created_at across returns platforms and commerce systems. Returns-management tools carry items and reasons; commerce platforms record a return as a status on an order -- so line items and reasons fall just short of core once both count.

## Artifacts

- [openapi.yml](openapi.yml) -- OpenAPI 3.1 of the shared operations. No one serves it; it
  is the shape to map to. Lints clean against the
  [naming ruleset](https://github.com/api-commons/schema-commons/blob/main/ruleset/schema-commons-naming.yaml).
- [schema/](schema) -- JSON Schema 2020-12 per concept; each property carries
  `x-commons-tier`, `x-commons-share`, `x-commons-providers` and the spellings seen.
- [crosswalk/](crosswalk) -- one per provider, common name -> their name, with the harvested
  spec and operations each mapping was read from.
- [adopters.yml](adopters.yml) -- who exposes which concept, linked to their APIs.io page.
- [concepts.yml](concepts.yml) -- the only hand-written input: concepts, path segments and
  their qualifiers, aliases, reviewed exclusions, merged duplicates, and the decisions below.
- [census/](census) -- the cohort and the raw census the profile is built from.

## Decisions

These are calls, not measurements, recorded so they can be revisited as the method matures.

- Returns are `/returns`; RMAs and return requests count. Exchanges do not -- in this cohort they were currency exchanges as often as product exchanges.
- The e-commerce, order-management and fulfillment tags are in the cohort: commerce platforms expose returns that returns-only tools do not. Refunds are payments'; return labels are shipping's.
- Return reasons were measured and dropped.
- Duplicates merged: four listings.

## Rebuild

```bash
../schema-commons/scripts/run.sh .
```

## License

Artifacts CC BY-NC-SA 4.0 ([LICENSE](LICENSE)); code Apache 2.0 ([LICENSE-CODE](LICENSE-CODE)).
