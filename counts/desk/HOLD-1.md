OBSERVATION

Not scored. No payment of ours in pre-run 18: families only, on the desk's private node, plus our own heavy lane at the N shown per minute.

# HOLD-1, desk, pre-run 18

> Our own TN10 testing: what we observed in this run, on our own desk node. Counts only. Included is what the desk's private TN10 node accepted on chain, read by the desk counter, by accepting chain block time. Mini's files are a second read.

HOLD-1 in pre-run 18 is lane 1 N=30 at 150 and lane 2 N=30 at 150 (the reference, no escalation): L30x2-r150-ref 10 whole minutes. Families only for payments (no payment of ours); our own heavy lane ran at the N and rate shown per minute (N = how many lane chains may each hold one ready transaction in the mempool). The HOLD file names are kept so the bot's and Mini's gates read as in earlier pre-runs. Not scored.

Families offer 1.2 hop/s, 16 families live, one family-sender process and one builder: floor (families 1–4) 100 sompi/gram on the desk's private node, r150 (families 5–8) 150 sompi/gram on the desk's private node, r300 (families 9–12) 300 sompi/gram on the desk's private node, r450 (families 13–16) 450 sompi/gram on the desk's private node. No payment sender was started.

## Tiers against the mempool, per minute

| Minute (UTC) | Lane 1 N / rate | Lane 2 N / rate | floor (100) | r150 (150) | r300 (300) | r450 (450) | Our heavy in mempool / ready | Our heavy landed, lane 1 / lane 2 | Lane submits OK, lane 1 / lane 2 | Outside heavy at 100 (>200k mass) / ready | Outside at 100, n | Ready mass, blocks | Mempool | Fee estimate priority |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 2026-11-13T03:20 | 30 / 150 | 30 / 150 | 85 | 132 | 193 | 204 | 52 / 52 | 280 / 265 | 310 / 294 | - / - | - | 31.64 | 132 | 333.4 |
| 2026-11-13T03:21 | 30 / 150 | 30 / 150 | 81 | 140 | 182 | 198 | 58 / 58 | 293 / 289 | 289 / 285 | - / - | - | 36.11 | 167 | 341.1 |
| 2026-11-13T03:22 | 30 / 150 | 30 / 150 | 69 | 121 | 192 | 200 | 53 / 53 | 236 / 294 | 237 / 295 | - / - | - | 32.86 | 113 | 301.9 |
| 2026-11-13T03:23 | 30 / 150 | 30 / 150 | 82 | 130 | 197 | 204 | 56 / 56 | 275 / 294 | 276 / 297 | - / - | - | 36.44 | 139 | 335.4 |
| 2026-11-13T03:24 | 30 / 150 | 30 / 150 | 81 | 137 | 187 | 201 | 58 / 58 | 284 / 287 | 283 / 286 | - / - | - | 37.90 | 137 | 345.0 |
| 2026-11-13T03:25 | 30 / 150 | 30 / 150 | 81 | 135 | 187 | 199 | 51 / 51 | 267 / 272 | 270 / 274 | - / - | - | 34.39 | 166 | 307.1 |
| 2026-11-13T03:26 | 30 / 150 | 30 / 150 | 88 | 134 | 200 | 217 | 54 / 54 | 286 / 286 | 284 / 285 | - / - | - | 36.70 | 153 | 341.7 |
| 2026-11-13T03:27 | 30 / 150 | 30 / 150 | 73 | 140 | 195 | 212 | 55 / 55 | 269 / 273 | 264 / 267 | - / - | - | 37.55 | 149 | 346.4 |
| 2026-11-13T03:28 | 30 / 150 | 30 / 150 | 81 | 133 | 191 | 197 | 58 / 58 | 273 / 269 | 279 / 274 | - / - | - | 37.28 | 142 | 349.1 |
| 2026-11-13T03:29 | 30 / 150 | 30 / 150 | 82 | 135 | 196 | 205 | 55 / 55 | 285 / 266 | 281 / 265 | - / - | - | 37.63 | 160 | 340.5 |

Lane 1 and lane 2 N / rate are the caps the runner set for that minute (N lane chains each, each chain with at most one ready transaction in the mempool) and each lane's fee rate (in the duel, the rate in effect at the start of the minute). Our heavy in mempool / ready is the probe's median count of our own lane entries; our heavy landed is what the desk counter read as accepted on chain from our lane in the minute; lane submits OK is the lane's own log. Hops are what the desk counter read as accepted on chain in that minute, per tier. Ready mass, blocks, is the median of the probe's samples in the minute (block limit 500,000). Outside at 100 is the median count of mempool entries not in our logs (our lane is in our logs) paying 100 sompi/gram, and heavy is how many of those had a mass over 200,000 (median of samples). The outside stream is not attributed to anyone.

## Chain, desk counter

| Minute (UTC) | Included, all non-coinbase | Our payments included | Floor hops (100) | R150 hops (150) | R300 hops (300) | R450 hops (450) | Other traffic | Chain blocks | DAA gap max | Sink age max, ms | Final after, s | Counter |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| 2026-11-13T03:20 | 4,098 | 0 | 85 | 132 | 193 | 204 | 2,945 | 326 | 0 | 480 | 20 | kept pace |
| 2026-11-13T03:21 | 4,348 | 0 | 81 | 140 | 182 | 198 | 3,165 | 349 | 0 | 568 | 20 | kept pace |
| 2026-11-13T03:22 | 4,089 | 0 | 69 | 121 | 192 | 200 | 2,977 | 330 | 1 | 579 | 20 | kept pace |
| 2026-11-13T03:23 | 4,167 | 0 | 82 | 130 | 197 | 204 | 2,987 | 332 | 1 | 600 | 20 | kept pace |
| 2026-11-13T03:24 | 4,114 | 0 | 81 | 137 | 187 | 201 | 2,937 | 344 | 1 | 368 | 21 | kept pace |
| 2026-11-13T03:25 | 4,138 | 0 | 81 | 135 | 187 | 199 | 3,000 | 331 | 1 | 285 | 19 | kept pace |
| 2026-11-13T03:26 | 4,208 | 0 | 88 | 134 | 200 | 217 | 2,998 | 342 | 1 | 310 | 20 | kept pace |
| 2026-11-13T03:27 | 4,186 | 0 | 73 | 140 | 195 | 212 | 3,024 | 316 | 1 | 611 | 20 | kept pace |
| 2026-11-13T03:28 | 4,104 | 0 | 81 | 133 | 191 | 197 | 2,961 | 316 | 0 | 587 | 19 | kept pace |
| 2026-11-13T03:29 | 4,164 | 0 | 82 | 135 | 196 | 205 | 2,997 | 335 | 1 | 557 | 20 | kept pace |

Coinbase is taken out as one per merged blue block (on this node a chain block's accepted list carries the coinbase of each blue block it merges). Other traffic is the rest: other users' load, the genesis, and anything not in our logs.

## Hop rate per cohort, as built

Floor (families 1–4, desk private node): 100 sompi/gram per hop. R150 (families 5–8, desk private node): 150 sompi/gram per hop. R300 (families 9–12, desk private node): 300 sompi/gram per hop. R450 (families 13–16, desk private node): 450 sompi/gram per hop. In pre-run 18 that rate is on the hop's node-side mass (kit21): the builder is asked for a bill rate on its own mass so that fee / node mass is the tier's rate.

| Tier | Node rate as built, median (min–max) | Bill rate, median | Node mass, median (min–max) | Node rate in the desk mempool, lowest–highest (probe) |
|---|---|---:|---|---|
| floor (100) | 100.15 (100–100.32) | 317 | 41,339 (40,377–42,115) | 100–100.32 |
| r150 (150) | 150.19 (150–150.32) | 476 | 41,325 (40,383–42,200) | 150–150.31 |
| r300 (300) | 300.16 (300–300.32) | 951 | 41,340 (40,403–42,381) | 300–300.32 |
| r450 (450) | 450.16 (450–450.32) | 1427 | 41,343 (40,424–42,602) | 450–450.31 |

Node rate as built is kit21's fee / node mass (rusty-kaspa v2.1.0 storage mass with UTXO plurality, or compute or transient/2 if larger). In the desk mempool the probe divides the node's fee by the larger of the storage and compute mass the node reports.

## Funding coins, as read from the desk node

The funding coins were not one size. Sizes seen, whole tKAS (coins): 20 (450), 19 (436), 18 (416), 21 (403), 16 (374), 17 (372), 15 (354), 14 (302), 22 (283), 13 (218), 12 (193), 4 (188), and 14 more sizes. The fee is not called the whole cause.

## Minutes

| Minute (UTC) | Pay submit-OK | Attempts | Rejects, rate | Rejects, full | Other | Floor OK / att / rate rej / full rej / waiting | R150 OK / att / rate rej / full rej / waiting | R300 OK / att / rate rej / full rej / waiting | R450 OK / att / rate rej / full rej / waiting | Family stalls logged | Family node mempool-high marks | Clean |
|---|---:|---:|---:|---:|---:|---|---|---|---|---:|---:|---|
| 2026-11-13T03:20 | 0 | 0 | 0 | 0 | 0 | 88 / 326 / 0 / 0 / 4 | 134 / 342 / 0 / 0 / 4 | 193 / 367 / 0 / 0 / 4 | 204 / 383 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T03:21 | 0 | 0 | 0 | 0 | 0 | 81 / 323 / 0 / 0 / 4 | 140 / 345 / 0 / 0 / 4 | 182 / 365 / 0 / 0 / 4 | 198 / 374 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T03:22 | 0 | 0 | 0 | 0 | 0 | 69 / 310 / 0 / 0 / 4 | 121 / 340 / 0 / 0 / 4 | 193 / 378 / 0 / 0 / 5 | 200 / 375 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T03:23 | 0 | 0 | 0 | 0 | 0 | 82 / 319 / 0 / 0 / 4 | 130 / 344 / 0 / 0 / 4 | 196 / 371 / 0 / 0 / 4 | 204 / 377 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T03:24 | 0 | 0 | 0 | 0 | 0 | 82 / 319 / 0 / 0 / 4 | 138 / 342 / 0 / 0 / 4 | 187 / 373 / 0 / 0 / 4 | 201 / 390 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T03:25 | 0 | 0 | 0 | 0 | 0 | 80 / 317 / 0 / 0 / 4 | 134 / 341 / 0 / 0 / 4 | 187 / 363 / 0 / 0 / 4 | 199 / 369 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T03:26 | 0 | 0 | 0 | 0 | 0 | 88 / 324 / 0 / 0 / 4 | 134 / 348 / 0 / 0 / 4 | 200 / 377 / 0 / 0 / 4 | 217 / 378 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T03:27 | 0 | 0 | 0 | 0 | 0 | 73 / 316 / 0 / 0 / 4 | 139 / 344 / 0 / 0 / 3 | 195 / 367 / 0 / 0 / 4 | 212 / 376 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T03:28 | 0 | 0 | 0 | 0 | 0 | 81 / 323 / 0 / 0 / 4 | 134 / 351 / 0 / 0 / 4 | 191 / 370 / 0 / 0 / 4 | 197 / 377 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T03:29 | 0 | 0 | 0 | 0 | 0 | 81 / 318 / 0 / 0 / 3 | 135 / 347 / 0 / 0 / 4 | 196 / 374 / 0 / 0 / 4 | 205 / 375 / 0 / 0 / 4 | 0 | 0 | yes |

A family stall is a coordinator mark: no hop of that family landed for a while. The family was still attempting. It is logged, and it does not make the minute dirty.

A mempool-high mark means the family node read a mempool at or over 90,000. In pre-run 18 that does not stop the families: the skip does not apply to them. A skip, if one were set, is dirt with its reason (node-skip-fam) for every minute it covers, and it clears when the mempool falls back under the line.

Within 10 percent means 0 to 0 submit-OK in the minute.

## Public nodes (local numbers)

Kept: 1, 5. The family sender reads and submits every tier on the desk's private node, which the desk counter reads. The kept public kaspads are read for sync and DAA only; no payment of ours went to them.

Kept nodes are unique kaspads: each answered with its own node id at the preflight. 3 candidate endpoints passed the check and were 2 kaspads (node 4 is node 1; the second hostname was not used). 3 payment senders per kaspad.

| Node | Synced every sample | Last DAA | Pay submit-OK | Pay rejects | Dropped sockets | Answer ms, median |
|---:|---|---:|---:|---:|---:|---:|
| 1 | yes | 622045921 | 0 | 0 | 0 | 32 |
| 5 | yes | 622045921 | 0 | 0 | 0 | 33 |

## Hop submit to landing, per cohort

| Cohort | Landed of OK | Median ms | Slow tail (p95) ms |
|---|---:|---:|---:|
| floor | 805 of 805 | 2369 | 6540 |
| r150 | 1339 of 1339 | 1552 | 2903 |
| r300 | 1920 of 1920 | 1111 | 1614 |
| r450 | 2037 of 2037 | 1042 | 1508 |

Landing is the accepting block header time the desk's coordinator read. Waiting is submitted-OK not yet landed at the minute's end. Every tier has the same hop shape and the same node; only the rate differs.

## Mempool and template, desk node (probe)

| Minute (UTC) | Samples | Mempool | Ready (no parent in mempool) | Ready mass, blocks of 500k | Other traffic in mempool | Other ready | Other at 100, n | Other at 100, mean mass | Our payments in mempool | Our heavy in mempool / ready | Floor in mempool / ready | R150 in mempool / ready | R300 in mempool / ready | R450 in mempool / ready | Template txs | Template storage mass | Template txs over 100k storage mass | Template: payments | Template: our heavy | Template: floor | Template: r150 | Template: r300 | Template: r450 | Template: other | Fee estimate priority / normal / low | Public 1 mempool | Public 5 mempool |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|---:|---:|
| 2026-11-13T03:20 | 3 | 132 | 132 | 31.64 | 59 | 59 | - | - | 0 | 52 / 52 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 8 | 472,937 | 1 | 0 | 1 | 0 | 0 | 1 | 4 | 2 | 333.4 / 176.2 / 113.8 | 120 | 120 |
| 2026-11-13T03:21 | 3 | 167 | 167 | 36.11 | 94 | 94 | - | - | 0 | 58 / 58 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 8 | 473,573 | 1 | 0 | 1 | 0 | 1 | 1 | 4 | 2 | 341.1 / 177.0 / 113.8 | 150 | 159 |
| 2026-11-13T03:22 | 3 | 113 | 113 | 32.86 | 52 | 52 | - | - | 0 | 53 / 53 | 4 / 4 | 3 / 3 | 3 / 3 | 3 / 3 | 7 | 471,663 | 1 | 0 | 1 | 0 | 1 | 2 | 2 | 2 | 301.9 / 172.3 / 113.4 | 125 | 130 |
| 2026-11-13T03:23 | 3 | 139 | 146 | 36.44 | 74 | 74 | - | - | 0 | 56 / 56 | 3 / 3 | 4 / 4 | 4 / 4 | 4 / 4 | 6 | 472,357 | 1 | 0 | 1 | 0 | 0 | 2 | 3 | 0 | 335.4 / 176.4 / 113.8 | 126 | 129 |
| 2026-11-13T03:24 | 3 | 137 | 164 | 37.90 | 91 | 91 | - | - | 0 | 58 / 58 | 4 / 4 | 4 / 4 | 3 / 3 | 4 / 4 | 8 | 473,369 | 1 | 0 | 1 | 0 | 1 | 2 | 3 | 2 | 345.0 / 177.4 / 113.9 | 118 | 120 |
| 2026-11-13T03:25 | 3 | 166 | 166 | 34.39 | 103 | 103 | - | - | 0 | 51 / 51 | 4 / 4 | 4 / 4 | 3 / 3 | 4 / 4 | 8 | 472,894 | 1 | 0 | 1 | 0 | 0 | 1 | 4 | 5 | 307.1 / 173.0 / 113.5 | 160 | 164 |
| 2026-11-13T03:26 | 3 | 153 | 153 | 36.70 | 84 | 84 | - | - | 0 | 54 / 54 | 4 / 4 | 3 / 3 | 4 / 4 | 4 / 4 | 10 | 472,414 | 1 | 0 | 1 | 0 | 0 | 1 | 4 | 3 | 341.7 / 177.1 / 113.9 | 150 | 145 |
| 2026-11-13T03:27 | 3 | 149 | 152 | 37.55 | 81 | 81 | - | - | 0 | 55 / 55 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 7 | 472,581 | 1 | 0 | 1 | 0 | 0 | 1 | 4 | 2 | 346.4 / 177.6 / 113.9 | 133 | 147 |
| 2026-11-13T03:28 | 3 | 142 | 148 | 37.28 | 75 | 75 | - | - | 0 | 58 / 58 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 8 | 473,422 | 1 | 0 | 1 | 0 | 0 | 1 | 4 | 2 | 349.1 / 177.9 / 113.9 | 128 | 142 |
| 2026-11-13T03:29 | 3 | 160 | 160 | 37.63 | 94 | 94 | - | - | 0 | 55 / 55 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 7 | 474,046 | 1 | 0 | 1 | 0 | 0 | 1 | 4 | 1 | 340.5 / 177.0 / 113.8 | 159 | 167 |

Read by the probe on the desk's private TN10 node every 20 s, read-only; each cell is the median of that minute's samples. Pre-run 17: ready count and ready mass come from the full mempool read up to 10,000 entries and from the node's own figures (getFeeEstimateExperimental, verbose) above that, where the per-class columns stay blank (the node's wRPC replies are capped at 128 MiB, about 12,500 entries). Ready means no parent in the mempool: in rusty-kaspa v2.1.0 only those are in the selector's frontier. Ready mass is compared with one block's mass limit (500,000): at or under 1 the selector takes all ready transactions best-first; over 1 it samples at random weighted by (fee/mass)^3 (over 4, sample_inplace). Mass is the larger of compute and storage mass, as the v2.1.0 selector normalises it (transient mass is not in the RPC). Other traffic is every mempool entry not in our sender logs (our heavy lane is its own class, our heavy); its fee rate is the node's fee over that mass. Template transactions carry no id in the RPC, so each is matched to a mempool entry by its first input. The template is the desk node's own getBlockTemplate (never submitted): what this node would put in a block at that moment, not a miner's template. The fee estimate is the node's getFeeEstimate, read only; no sender reads it. Public mempool is getInfo's mempool size on each kept public kaspad.
