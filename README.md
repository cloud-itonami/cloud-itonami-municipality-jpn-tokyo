# cloud-itonami-municipality-jpn-tokyo

Municipal-ordinance compliance catalog for Tokyo (東京都) — the
municipality-level counterpart to
[`cloud-itonami-iso3166-jpn`](https://github.com/cloud-itonami/cloud-itonami-iso3166-jpn)'s
national-law `statute.facts`. Part of the
[`cloud-itonami`](https://github.com/cloud-itonami) compliance-fact family
(ADR-2607141700, `cloud-itonami-compliance-fact-federation`, in
`com-junkawasaki/root`).

## Scope

A **read-only reference/archive** catalog — not an Advisor⊣Governor
actuation actor, same class as `cloud-itonami-gtin-catalog` /
`cloud-itonami-lei-*`. It proposes or executes nothing on Tokyo
Metropolitan Government's behalf.

Coverage is reported honestly (see `ordinance.facts/coverage`): a
municipality not in `catalog` has **no spec-basis**, full stop — never
fabricate one.

## Data

- `src/ordinance/facts.cljc` — the catalog, source of truth.
- `schema/ordinance.edn` — DataScript schema.
- `data/datascript-tx.edn` — derived DataScript tx-data (query this
  alongside other `cloud-itonami`/`etzhayyim` compliance-fact sources via
  `com-junkawasaki/root`'s `scripts/compliance-fact-query.cljs`).

Every entry cites an official
[reiki.metro.tokyo.lg.jp](https://www.reiki.metro.tokyo.lg.jp/) ordinance
page — each URL was independently fetched and its title/number/enactment
date verified against the live document (2026-07-14), never guessed from
memory.

## Culture catalog

Alongside the ordinance catalog, this repo carries a **regional-culture
catalog** (ADR-2607171400, `cloud-itonami-municipality-culture-catalog`
in `com-junkawasaki/root`) — local dishes, protected products, beverages,
festivals and heritage sites for Tokyo:

- `src/culture/facts.cljc` — the catalog, source of truth.
- `schema/culture.edn` — DataScript schema.
- `data/culture-tx.edn` — derived DataScript tx-data (regenerated from
  the catalog, never hand-edited).

Same provenance discipline as the ordinance catalog: every entry cites a
source URL that was actually fetched and read on `:culture/retrieved-at`;
summaries state only what the cited source confirms. An item not in
`culture.facts/catalog` has no spec-basis — never fabricate one.

## License

AGPL-3.0-or-later (matches the `cloud-itonami-iso3166-*` / `-lei-*`
convention). Ordinance text itself remains Tokyo Metropolitan
Government's; this repo stores only citation metadata (id/title/number/
url/date), not full ordinance text.
