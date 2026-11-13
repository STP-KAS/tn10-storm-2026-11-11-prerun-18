OBSERVATION

Not scored. No payment of ours in pre-run 18: families only, on the desk's private node, plus our own heavy lane at the N shown per minute.

# RETURN, desk, pre-run 18

> Our own TN10 testing: what we observed in this run, on our own desk node. Counts only. Included is what the desk's private TN10 node accepted on chain, read by the desk counter, by accepting chain block time. Mini's files are a second read.

RETURN is families only with our heavy lane at N=0 (the drain), 10 whole minutes, the last stretch before the families stop. Not scored.

Families offer 1.2 hop/s, 16 families live, one family-sender process and one builder: floor (families 1–4) 100 sompi/gram on the desk's private node, r150 (families 5–8) 150 sompi/gram on the desk's private node, r300 (families 9–12) 300 sompi/gram on the desk's private node, r450 (families 13–16) 450 sompi/gram on the desk's private node. No payment sender was started.

## Tiers against the mempool, per minute

| Minute (UTC) | Lane 1 N / rate | Lane 2 N / rate | floor (100) | r150 (150) | r300 (300) | r450 (450) | Our heavy in mempool / ready | Our heavy landed, lane 1 / lane 2 | Lane submits OK, lane 1 / lane 2 | Outside heavy at 100 (>200k mass) / ready | Outside at 100, n | Ready mass, blocks | Mempool | Fee estimate priority |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 2026-11-13T04:08 | 0 / 100 | 0 / 100 | 194 | 189 | 192 | 192 | 0 / 0 | 0 / 0 | 0 / 0 | - / - | - | 0.98 | 12 | 151.9 |
| 2026-11-13T04:09 | 0 / 100 | 0 / 100 | 189 | 196 | 200 | 199 | 0 / 0 | 0 / 0 | 0 / 0 | - / - | - | 1.32 | 16 | 173.3 |
| 2026-11-13T04:10 | 0 / 100 | 0 / 100 | 193 | 196 | 198 | 189 | 0 / 0 | 0 / 0 | 0 / 0 | - / - | - | 1.36 | 16 | 172.6 |
| 2026-11-13T04:11 | 0 / 100 | 0 / 100 | 200 | 203 | 199 | 199 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.51 | 16 | 170.4 |
| 2026-11-13T04:12 | 0 / 100 | 0 / 100 | 200 | 202 | 202 | 203 | 0 / 0 | 0 / 0 | 0 / 0 | - / - | - | 1.31 | 16 | 169.9 |
| 2026-11-13T04:13 | 0 / 100 | 0 / 100 | 210 | 209 | 206 | 200 | 0 / 0 | 0 / 0 | 0 / 0 | - / - | - | 1.31 | 16 | 169.2 |
| 2026-11-13T04:14 | 0 / 100 | 0 / 100 | 191 | 191 | 195 | 189 | 0 / 0 | 0 / 0 | 0 / 0 | - / - | - | 1.31 | 16 | 169.8 |
| 2026-11-13T04:15 | 0 / 100 | 0 / 100 | 193 | 200 | 202 | 200 | 0 / 0 | 0 / 0 | 0 / 0 | - / - | - | 1.06 | 4 | 157.7 |
| 2026-11-13T04:16 | 0 / 100 | 0 / 100 | 175 | 178 | 184 | 181 | 0 / 0 | 0 / 0 | 0 / 0 | - / - | - | 1.47 | 17 | 169.3 |
| 2026-11-13T04:17 | 0 / 100 | 0 / 100 | 192 | 197 | 195 | 196 | 0 / 0 | 0 / 0 | 0 / 0 | - / - | - | 1.31 | 16 | 167.6 |

Lane 1 and lane 2 N / rate are the caps the runner set for that minute (N lane chains each, each chain with at most one ready transaction in the mempool) and each lane's fee rate (in the duel, the rate in effect at the start of the minute). Our heavy in mempool / ready is the probe's median count of our own lane entries; our heavy landed is what the desk counter read as accepted on chain from our lane in the minute; lane submits OK is the lane's own log. Hops are what the desk counter read as accepted on chain in that minute, per tier. Ready mass, blocks, is the median of the probe's samples in the minute (block limit 500,000). Outside at 100 is the median count of mempool entries not in our logs (our lane is in our logs) paying 100 sompi/gram, and heavy is how many of those had a mass over 200,000 (median of samples). The outside stream is not attributed to anyone.

## Chain, desk counter

| Minute (UTC) | Included, all non-coinbase | Our payments included | Floor hops (100) | R150 hops (150) | R300 hops (300) | R450 hops (450) | Other traffic | Chain blocks | DAA gap max | Sink age max, ms | Final after, s | Counter |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| 2026-11-13T04:08 | 4,050 | 0 | 194 | 189 | 192 | 192 | 3,334 | 356 | 1 | 364 | 20 | kept pace |
| 2026-11-13T04:09 | 3,860 | 0 | 189 | 196 | 200 | 199 | 3,118 | 345 | 1 | 469 | 20 | kept pace |
| 2026-11-13T04:10 | 3,837 | 0 | 193 | 196 | 198 | 189 | 3,091 | 327 | 1 | 324 | 20 | kept pace |
| 2026-11-13T04:11 | 3,865 | 0 | 200 | 203 | 199 | 199 | 3,108 | 352 | 1 | 673 | 21 | kept pace |
| 2026-11-13T04:12 | 3,890 | 0 | 200 | 202 | 202 | 203 | 3,121 | 328 | 2 | 801 | 19 | kept pace |
| 2026-11-13T04:13 | 3,913 | 0 | 210 | 209 | 206 | 200 | 3,134 | 352 | 0 | 545 | 20 | kept pace |
| 2026-11-13T04:14 | 3,792 | 0 | 191 | 191 | 195 | 189 | 3,062 | 319 | 0 | 625 | 19 | kept pace |
| 2026-11-13T04:15 | 3,873 | 0 | 193 | 200 | 202 | 200 | 3,121 | 318 | 0 | 548 | 20 | kept pace |
| 2026-11-13T04:16 | 3,777 | 0 | 175 | 178 | 184 | 181 | 3,087 | 300 | 1 | 651 | 20 | kept pace |
| 2026-11-13T04:17 | 3,862 | 0 | 192 | 197 | 195 | 196 | 3,128 | 311 | 0 | 545 | 19 | kept pace |

Coinbase is taken out as one per merged blue block (on this node a chain block's accepted list carries the coinbase of each blue block it merges). Other traffic is the rest: other users' load, the genesis, and anything not in our logs.

## Hop rate per cohort, as built

Floor (families 1–4, desk private node): 100 sompi/gram per hop. R150 (families 5–8, desk private node): 150 sompi/gram per hop. R300 (families 9–12, desk private node): 300 sompi/gram per hop. R450 (families 13–16, desk private node): 450 sompi/gram per hop. In pre-run 18 that rate is on the hop's node-side mass (kit21): the builder is asked for a bill rate on its own mass so that fee / node mass is the tier's rate.

| Tier | Node rate as built, median (min–max) | Bill rate, median | Node mass, median (min–max) | Node rate in the desk mempool, lowest–highest (probe) |
|---|---|---:|---|---|
| floor (100) | 100.15 (100–100.32) | 314 | 40,947 (40,377–42,186) | 100–100.32 |
| r150 (150) | 150.16 (150–150.32) | 471 | 40,952 (40,383–42,226) | 150–150.32 |
| r300 (300) | 300.17 (300–300.32) | 943 | 40,965 (40,403–42,395) | 300–300.31 |
| r450 (450) | 450.15 (450–450.32) | 1414 | 40,975 (40,423–42,583) | 450–450.31 |

Node rate as built is kit21's fee / node mass (rusty-kaspa v2.1.0 storage mass with UTXO plurality, or compute or transient/2 if larger). In the desk mempool the probe divides the node's fee by the larger of the storage and compute mass the node reports.

## Funding coins, as read from the desk node

The funding coins were not one size. Sizes seen, whole tKAS (coins): 13 (456), 14 (397), 11 (391), 12 (378), 15 (362), 10 (341), 16 (275), 9 (267), 8 (249), 17 (242), 7 (208), 6 (190), and 13 more sizes. The fee is not called the whole cause.

## Minutes

| Minute (UTC) | Pay submit-OK | Attempts | Rejects, rate | Rejects, full | Other | Floor OK / att / rate rej / full rej / waiting | R150 OK / att / rate rej / full rej / waiting | R300 OK / att / rate rej / full rej / waiting | R450 OK / att / rate rej / full rej / waiting | Family stalls logged | Family node mempool-high marks | Clean |
|---|---:|---:|---:|---:|---:|---|---|---|---|---:|---:|---|
| 2026-11-13T04:08 | 0 | 0 | 0 | 0 | 0 | 194 / 374 / 0 / 0 / 4 | 189 / 370 / 0 / 0 / 5 | 192 / 368 / 0 / 0 / 4 | 192 / 368 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T04:09 | 0 | 0 | 0 | 0 | 0 | 189 / 367 / 0 / 0 / 4 | 196 / 367 / 0 / 0 / 5 | 200 / 372 / 0 / 0 / 4 | 199 / 372 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T04:10 | 0 | 0 | 0 | 0 | 0 | 193 / 363 / 0 / 0 / 4 | 196 / 374 / 0 / 0 / 5 | 198 / 384 / 0 / 0 / 4 | 189 / 369 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T04:11 | 0 | 0 | 0 | 0 | 0 | 201 / 375 / 0 / 0 / 5 | 206 / 379 / 0 / 0 / 8 | 203 / 376 / 0 / 0 / 8 | 203 / 379 / 0 / 0 / 8 | 0 | 0 | yes |
| 2026-11-13T04:12 | 0 | 0 | 0 | 0 | 0 | 199 / 374 / 0 / 0 / 4 | 199 / 368 / 0 / 0 / 5 | 198 / 371 / 0 / 0 / 4 | 199 / 371 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T04:13 | 0 | 0 | 0 | 0 | 0 | 210 / 377 / 0 / 0 / 4 | 209 / 388 / 0 / 0 / 5 | 206 / 385 / 0 / 0 / 4 | 200 / 379 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T04:14 | 0 | 0 | 0 | 0 | 0 | 192 / 375 / 0 / 0 / 5 | 194 / 371 / 0 / 0 / 8 | 199 / 379 / 0 / 0 / 8 | 193 / 378 / 0 / 0 / 8 | 0 | 0 | yes |
| 2026-11-13T04:15 | 0 | 0 | 0 | 0 | 0 | 189 / 377 / 0 / 0 / 1 | 196 / 369 / 0 / 0 / 4 | 197 / 370 / 0 / 0 / 3 | 196 / 368 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T04:16 | 0 | 0 | 0 | 0 | 0 | 178 / 360 / 0 / 0 / 4 | 179 / 358 / 0 / 0 / 5 | 185 / 363 / 0 / 0 / 4 | 181 / 363 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T04:17 | 0 | 0 | 0 | 0 | 0 | 192 / 369 / 0 / 0 / 4 | 197 / 374 / 0 / 0 / 5 | 195 / 375 / 0 / 0 / 4 | 196 / 376 / 0 / 0 / 4 | 0 | 0 | yes |

A family stall is a coordinator mark: no hop of that family landed for a while. The family was still attempting. It is logged, and it does not make the minute dirty.

A mempool-high mark means the family node read a mempool at or over 90,000. In pre-run 18 that does not stop the families: the skip does not apply to them. A skip, if one were set, is dirt with its reason (node-skip-fam) for every minute it covers, and it clears when the mempool falls back under the line.

Within 10 percent means 0 to 0 submit-OK in the minute.

## Public nodes (local numbers)

Kept: 1, 5. The family sender reads and submits every tier on the desk's private node, which the desk counter reads. The kept public kaspads are read for sync and DAA only; no payment of ours went to them.

Kept nodes are unique kaspads: each answered with its own node id at the preflight. 3 candidate endpoints passed the check and were 2 kaspads (node 4 is node 1; the second hostname was not used). 3 payment senders per kaspad.

| Node | Synced every sample | Last DAA | Pay submit-OK | Pay rejects | Dropped sockets | Answer ms, median |
|---:|---|---:|---:|---:|---:|---:|
| 1 | yes | 622074721 | 0 | 0 | 0 | 32 |
| 5 | yes | 622074721 | 0 | 0 | 0 | 33 |

## Hop submit to landing, per cohort

| Cohort | Landed of OK | Median ms | Slow tail (p95) ms |
|---|---:|---:|---:|
| floor | 1937 of 1937 | 1110 | 1606 |
| r150 | 1961 of 1961 | 1088 | 1560 |
| r300 | 1973 of 1973 | 1081 | 1534 |
| r450 | 1948 of 1948 | 1091 | 1558 |

Landing is the accepting block header time the desk's coordinator read. Waiting is submitted-OK not yet landed at the minute's end. Every tier has the same hop shape and the same node; only the rate differs.

## Mempool and template, desk node (probe)

| Minute (UTC) | Samples | Mempool | Ready (no parent in mempool) | Ready mass, blocks of 500k | Other traffic in mempool | Other ready | Other at 100, n | Other at 100, mean mass | Our payments in mempool | Our heavy in mempool / ready | Floor in mempool / ready | R150 in mempool / ready | R300 in mempool / ready | R450 in mempool / ready | Template txs | Template storage mass | Template txs over 100k storage mass | Template: payments | Template: our heavy | Template: floor | Template: r150 | Template: r300 | Template: r450 | Template: other | Fee estimate priority / normal / low | Public 1 mempool | Public 5 mempool |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|---:|---:|
| 2026-11-13T04:08 | 3 | 12 | 12 | 0.98 | 0 | 0 | - | - | 0 | 0 / 0 | 4 / 4 | 3 / 3 | 4 / 4 | 4 / 4 | 12 | 490,174 | 0 | 0 | 0 | 2 | 2 | 4 | 4 | 0 | 151.9 / 131.5 / 107.9 | 0 | 5 |
| 2026-11-13T04:09 | 3 | 16 | 16 | 1.32 | 0 | 0 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 452,018 | 0 | 0 | 0 | 0 | 3 | 4 | 4 | 0 | 173.3 / 141.0 / 109.5 | 2 | 2 |
| 2026-11-13T04:10 | 3 | 16 | 17 | 1.36 | 1 | 1 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 13 | 491,379 | 0 | 0 | 0 | 1 | 3 | 4 | 4 | 1 | 172.6 / 140.7 / 109.5 | 1 | 14 |
| 2026-11-13T04:11 | 3 | 16 | 16 | 1.51 | 1 | 1 | 1 | 2,229 | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 492,259 | 0 | 0 | 0 | 1 | 3 | 4 | 4 | 0 | 170.4 / 139.8 / 109.4 | 1 | 16 |
| 2026-11-13T04:12 | 3 | 16 | 16 | 1.31 | 1 | 1 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 13 | 490,680 | 0 | 0 | 0 | 1 | 3 | 4 | 4 | 1 | 169.9 / 139.6 / 109.3 | 3 | 16 |
| 2026-11-13T04:13 | 3 | 16 | 16 | 1.31 | 0 | 0 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 490,656 | 0 | 0 | 0 | 1 | 3 | 4 | 4 | 0 | 169.2 / 139.3 / 109.3 | 0 | 16 |
| 2026-11-13T04:14 | 3 | 16 | 16 | 1.31 | 0 | 0 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 491,215 | 0 | 0 | 0 | 1 | 1 | 4 | 4 | 0 | 169.8 / 139.6 / 109.3 | 1 | 12 |
| 2026-11-13T04:15 | 3 | 4 | 13 | 1.06 | 0 | 0 | - | - | 0 | 0 / 0 | 3 / 3 | 3 / 3 | 4 / 4 | 4 / 4 | 12 | 490,156 | 0 | 0 | 0 | 2 | 2 | 4 | 4 | 0 | 157.7 / 134.3 / 108.4 | 4 | 4 |
| 2026-11-13T04:16 | 3 | 17 | 17 | 1.47 | 1 | 1 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 13 | 491,256 | 0 | 0 | 0 | 1 | 3 | 4 | 4 | 1 | 169.3 / 139.3 / 109.3 | 7 | 13 |
| 2026-11-13T04:17 | 3 | 16 | 16 | 1.31 | 0 | 0 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 490,761 | 0 | 0 | 0 | 1 | 3 | 4 | 4 | 0 | 167.6 / 138.6 / 109.2 | 1 | 12 |

Read by the probe on the desk's private TN10 node every 20 s, read-only; each cell is the median of that minute's samples. Pre-run 17: ready count and ready mass come from the full mempool read up to 10,000 entries and from the node's own figures (getFeeEstimateExperimental, verbose) above that, where the per-class columns stay blank (the node's wRPC replies are capped at 128 MiB, about 12,500 entries). Ready means no parent in the mempool: in rusty-kaspa v2.1.0 only those are in the selector's frontier. Ready mass is compared with one block's mass limit (500,000): at or under 1 the selector takes all ready transactions best-first; over 1 it samples at random weighted by (fee/mass)^3 (over 4, sample_inplace). Mass is the larger of compute and storage mass, as the v2.1.0 selector normalises it (transient mass is not in the RPC). Other traffic is every mempool entry not in our sender logs (our heavy lane is its own class, our heavy); its fee rate is the node's fee over that mass. Template transactions carry no id in the RPC, so each is matched to a mempool entry by its first input. The template is the desk node's own getBlockTemplate (never submitted): what this node would put in a block at that moment, not a miner's template. The fee estimate is the node's getFeeEstimate, read only; no sender reads it. Public mempool is getInfo's mempool size on each kept public kaspad.
