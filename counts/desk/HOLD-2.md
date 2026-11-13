OBSERVATION

Not scored. No payment of ours in pre-run 18: families only, on the desk's private node, plus our own heavy lane at the N shown per minute.

# HOLD-2, desk, pre-run 18

> Our own TN10 testing: what we observed in this run, on our own desk node. Counts only. Included is what the desk's private TN10 node accepted on chain, read by the desk counter, by accepting chain block time. Mini's files are a second read.

HOLD-2 in pre-run 18 is the greedy duel, part 1 (both lanes N=30 from 150; lane 1 greedy: wants 110 percent of its reference and never steps down; lane 2 the normal rule): L30x2-greedy-1 12 whole minutes. Families only for payments (no payment of ours); our own heavy lane ran at the N and rate shown per minute (N = how many lane chains may each hold one ready transaction in the mempool). The HOLD file names are kept so the bot's and Mini's gates read as in earlier pre-runs. Not scored.

Families offer 1.2 hop/s, 16 families live, one family-sender process and one builder: floor (families 1–4) 100 sompi/gram on the desk's private node, r150 (families 5–8) 150 sompi/gram on the desk's private node, r300 (families 9–12) 300 sompi/gram on the desk's private node, r450 (families 13–16) 450 sompi/gram on the desk's private node. No payment sender was started.

## Tiers against the mempool, per minute

| Minute (UTC) | Lane 1 N / rate | Lane 2 N / rate | floor (100) | r150 (150) | r300 (300) | r450 (450) | Our heavy in mempool / ready | Our heavy landed, lane 1 / lane 2 | Lane submits OK, lane 1 / lane 2 | Outside heavy at 100 (>200k mass) / ready | Outside at 100, n | Ready mass, blocks | Mempool | Fee estimate priority |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 2026-11-13T03:30 | 30 / 150 | 30 / 150 | 74 | 125 | 185 | 200 | 56 / 56 | 273 / 277 | 278 / 280 | - / - | - | 37.68 | 154 | 352.2 |
| 2026-11-13T03:31 | 30 / 150 | 30 / 150 | 77 | 121 | 194 | 211 | 56 / 56 | 323 / 248 | 320 / 247 | - / - | - | 38.43 | 156 | 379.6 |
| 2026-11-13T03:32 | 30 / 188 | 30 / 150 | 54 | 114 | 182 | 197 | 57 / 57 | 315 / 235 | 312 / 233 | - / - | - | 40.72 | 202 | 408.5 |
| 2026-11-13T03:33 | 30 / 188 | 30 / 188 | 42 | 98 | 178 | 199 | 56 / 56 | 255 / 308 | 261 / 310 | - / - | - | 40.07 | 238 | 418.9 |
| 2026-11-13T03:34 | 30 / 188 | 30 / 235 | 39 | 83 | 174 | 200 | 58 / 58 | 263 / 330 | 262 / 329 | - / - | - | 41.91 | 302 | 487.0 |
| 2026-11-13T03:35 | 30 / 235 | 30 / 235 | 24 | 71 | 163 | 195 | 54 / 54 | 361 / 209 | 361 / 211 | - / - | - | 40.51 | 327 | 486.9 |
| 2026-11-13T03:36 | 30 / 294 | 30 / 188 | 31 | 67 | 165 | 198 | 57 / 57 | 393 / 151 | 391 / 147 | - / - | - | 42.34 | 369 | 517.1 |
| 2026-11-13T03:37 | 30 / 294 | 30 / 235 | 16 | 47 | 150 | 181 | 56 / 56 | 310 / 242 | 311 / 239 | - / - | - | 42.60 | 431 | 528.8 |
| 2026-11-13T03:38 | 30 / 294 | 30 / 294 | 15 | 40 | 127 | 188 | 51 / 51 | 251 / 292 | 251 / 295 | - / - | - | 41.07 | 545 | 575.7 |
| 2026-11-13T03:39 | 30 / 294 | 30 / 368 | 9 | 33 | 123 | 169 | 54 / 54 | 244 / 322 | 244 / 324 | - / - | - | 45.16 | 811 | 655.9 |
| 2026-11-13T03:40 | 30 / 368 | 30 / 368 | 6 | 28 | 108 | 162 | 52 / 52 | 337 / 225 | 338 / 227 | - / - | - | 45.06 | 923 | 710.9 |
| 2026-11-13T03:41 | 30 / 460 | 30 / 294 | 8 | 26 | 112 | 156 | 58 / 58 | 399 / 187 | 396 / 186 | - / - | - | 48.27 | 1,052 | 765.9 |

Lane 1 and lane 2 N / rate are the caps the runner set for that minute (N lane chains each, each chain with at most one ready transaction in the mempool) and each lane's fee rate (in the duel, the rate in effect at the start of the minute). Our heavy in mempool / ready is the probe's median count of our own lane entries; our heavy landed is what the desk counter read as accepted on chain from our lane in the minute; lane submits OK is the lane's own log. Hops are what the desk counter read as accepted on chain in that minute, per tier. Ready mass, blocks, is the median of the probe's samples in the minute (block limit 500,000). Outside at 100 is the median count of mempool entries not in our logs (our lane is in our logs) paying 100 sompi/gram, and heavy is how many of those had a mass over 200,000 (median of samples). The outside stream is not attributed to anyone.

## Chain, desk counter

| Minute (UTC) | Included, all non-coinbase | Our payments included | Floor hops (100) | R150 hops (150) | R300 hops (300) | R450 hops (450) | Other traffic | Chain blocks | DAA gap max | Sink age max, ms | Final after, s | Counter |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| 2026-11-13T03:30 | 4,073 | 0 | 74 | 125 | 185 | 200 | 2,943 | 295 | 1 | 523 | 20 | kept pace |
| 2026-11-13T03:31 | 4,146 | 0 | 77 | 121 | 194 | 211 | 2,972 | 333 | 1 | 514 | 19 | kept pace |
| 2026-11-13T03:32 | 4,087 | 0 | 54 | 114 | 182 | 197 | 2,990 | 333 | 1 | 870 | 21 | kept pace |
| 2026-11-13T03:33 | 4,096 | 0 | 42 | 98 | 178 | 199 | 3,016 | 326 | 1 | 525 | 19 | kept pace |
| 2026-11-13T03:34 | 3,991 | 0 | 39 | 83 | 174 | 200 | 2,902 | 348 | 0 | 580 | 20 | kept pace |
| 2026-11-13T03:35 | 3,991 | 0 | 24 | 71 | 163 | 195 | 2,968 | 330 | 1 | 625 | 21 | kept pace |
| 2026-11-13T03:36 | 3,855 | 0 | 31 | 67 | 165 | 198 | 2,850 | 346 | 1 | 602 | 20 | kept pace |
| 2026-11-13T03:37 | 3,828 | 0 | 16 | 47 | 150 | 181 | 2,882 | 324 | 0 | 493 | 20 | kept pace |
| 2026-11-13T03:38 | 3,556 | 0 | 15 | 40 | 127 | 188 | 2,643 | 324 | 1 | 391 | 20 | kept pace |
| 2026-11-13T03:39 | 3,790 | 0 | 9 | 33 | 123 | 169 | 2,891 | 331 | 0 | 335 | 20 | kept pace |
| 2026-11-13T03:40 | 3,612 | 0 | 6 | 28 | 108 | 162 | 2,746 | 340 | 0 | 401 | 20 | kept pace |
| 2026-11-13T03:41 | 3,794 | 0 | 8 | 26 | 112 | 156 | 2,906 | 351 | 1 | 319 | 20 | kept pace |

Coinbase is taken out as one per merged blue block (on this node a chain block's accepted list carries the coinbase of each blue block it merges). Other traffic is the rest: other users' load, the genesis, and anything not in our logs.

## Hop rate per cohort, as built

Floor (families 1–4, desk private node): 100 sompi/gram per hop. R150 (families 5–8, desk private node): 150 sompi/gram per hop. R300 (families 9–12, desk private node): 300 sompi/gram per hop. R450 (families 13–16, desk private node): 450 sompi/gram per hop. In pre-run 18 that rate is on the hop's node-side mass (kit21): the builder is asked for a bill rate on its own mass so that fee / node mass is the tier's rate.

| Tier | Node rate as built, median (min–max) | Bill rate, median | Node mass, median (min–max) | Node rate in the desk mempool, lowest–highest (probe) |
|---|---|---:|---|---|
| floor (100) | 100.17 (100–100.32) | 317 | 41,271 (40,377–42,006) | 100.01–100.32 |
| r150 (150) | 150.18 (150–150.32) | 475 | 41,254 (40,384–42,165) | 150–150.32 |
| r300 (300) | 300.16 (300–300.32) | 949 | 41,250 (40,403–42,407) | 300–300.32 |
| r450 (450) | 450.16 (450–450.32) | 1424 | 41,255 (40,423–42,586) | 450–450.31 |

Node rate as built is kit21's fee / node mass (rusty-kaspa v2.1.0 storage mass with UTXO plurality, or compute or transient/2 if larger). In the desk mempool the probe divides the node's fee by the larger of the storage and compute mass the node reports.

## Funding coins, as read from the desk node

The funding coins were not one size. Sizes seen, whole tKAS (coins): 17 (422), 19 (407), 16 (400), 18 (387), 15 (377), 14 (375), 20 (365), 13 (299), 21 (280), 12 (240), 11 (197), 22 (175), and 14 more sizes. The fee is not called the whole cause.

## Minutes

| Minute (UTC) | Pay submit-OK | Attempts | Rejects, rate | Rejects, full | Other | Floor OK / att / rate rej / full rej / waiting | R150 OK / att / rate rej / full rej / waiting | R300 OK / att / rate rej / full rej / waiting | R450 OK / att / rate rej / full rej / waiting | Family stalls logged | Family node mempool-high marks | Clean |
|---|---:|---:|---:|---:|---:|---|---|---|---|---:|---:|---|
| 2026-11-13T03:30 | 0 | 0 | 0 | 0 | 0 | 75 / 318 / 0 / 0 / 4 | 125 / 338 / 0 / 0 / 4 | 185 / 358 / 0 / 0 / 4 | 200 / 366 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T03:31 | 0 | 0 | 0 | 0 | 0 | 77 / 317 / 0 / 0 / 4 | 120 / 337 / 0 / 0 / 3 | 194 / 367 / 0 / 0 / 4 | 211 / 381 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T03:32 | 0 | 0 | 0 | 0 | 0 | 53 / 311 / 0 / 0 / 3 | 114 / 336 / 0 / 0 / 3 | 181 / 365 / 0 / 0 / 3 | 195 / 378 / 0 / 0 / 2 | 0 | 0 | yes |
| 2026-11-13T03:33 | 0 | 0 | 0 | 0 | 0 | 43 / 306 / 0 / 0 / 4 | 99 / 326 / 0 / 0 / 4 | 179 / 359 / 0 / 0 / 4 | 201 / 363 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T03:34 | 0 | 0 | 0 | 0 | 0 | 40 / 303 / 0 / 0 / 5 | 83 / 317 / 0 / 0 / 4 | 174 / 364 / 0 / 0 / 4 | 202 / 371 / 0 / 0 / 6 | 0 | 0 | yes |
| 2026-11-13T03:35 | 0 | 0 | 0 | 0 | 0 | 23 / 293 / 0 / 0 / 4 | 71 / 307 / 0 / 0 / 4 | 163 / 361 / 0 / 0 / 4 | 193 / 370 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T03:36 | 0 | 0 | 0 | 0 | 0 | 31 / 293 / 0 / 0 / 4 | 67 / 314 / 0 / 0 / 5 | 164 / 358 / 0 / 0 / 3 | 196 / 373 / 0 / 0 / 2 | 0 | 0 | yes |
| 2026-11-13T03:37 | 0 | 0 | 0 | 0 | 0 | 16 / 291 / 0 / 0 / 4 | 47 / 303 / 0 / 0 / 5 | 150 / 356 / 0 / 0 / 3 | 183 / 367 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T03:38 | 0 | 0 | 0 | 0 | 0 | 15 / 291 / 0 / 0 / 4 | 40 / 303 / 0 / 0 / 5 | 127 / 339 / 0 / 0 / 3 | 188 / 362 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T03:39 | 0 | 0 | 0 | 0 | 0 | 9 / 289 / 0 / 0 / 4 | 32 / 299 / 0 / 0 / 4 | 124 / 341 / 0 / 0 / 4 | 168 / 352 / 0 / 0 / 3 | 0 | 0 | yes |
| 2026-11-13T03:40 | 0 | 0 | 0 | 0 | 0 | 6 / 286 / 0 / 0 / 4 | 29 / 297 / 0 / 0 / 5 | 108 / 336 / 0 / 0 / 4 | 162 / 360 / 0 / 0 / 3 | 2 | 0 | yes |
| 2026-11-13T03:41 | 0 | 0 | 0 | 0 | 0 | 8 / 290 / 0 / 0 / 4 | 26 / 295 / 0 / 0 / 5 | 112 / 335 / 0 / 0 / 4 | 157 / 349 / 0 / 0 / 4 | 1 | 0 | yes |

A family stall is a coordinator mark: no hop of that family landed for a while. The family was still attempting. It is logged, and it does not make the minute dirty.

A mempool-high mark means the family node read a mempool at or over 90,000. In pre-run 18 that does not stop the families: the skip does not apply to them. A skip, if one were set, is dirt with its reason (node-skip-fam) for every minute it covers, and it clears when the mempool falls back under the line.

Within 10 percent means 0 to 0 submit-OK in the minute.

## Public nodes (local numbers)

Kept: 1, 5. The family sender reads and submits every tier on the desk's private node, which the desk counter reads. The kept public kaspads are read for sync and DAA only; no payment of ours went to them.

Kept nodes are unique kaspads: each answered with its own node id at the preflight. 3 candidate endpoints passed the check and were 2 kaspads (node 4 is node 1; the second hostname was not used). 3 payment senders per kaspad.

| Node | Synced every sample | Last DAA | Pay submit-OK | Pay rejects | Dropped sockets | Answer ms, median |
|---:|---|---:|---:|---:|---:|---:|
| 1 | yes | 622053156 | 0 | 0 | 0 | 32 |
| 5 | yes | 622053156 | 0 | 0 | 0 | 32 |

## Hop submit to landing, per cohort

| Cohort | Landed of OK | Median ms | Slow tail (p95) ms |
|---|---:|---:|---:|
| floor | 394 of 396 | 3649 | 24276 |
| r150 | 852 of 853 | 2126 | 10259 |
| r300 | 1861 of 1861 | 1270 | 2642 |
| r450 | 2256 of 2256 | 1133 | 1745 |

Landing is the accepting block header time the desk's coordinator read. Waiting is submitted-OK not yet landed at the minute's end. Every tier has the same hop shape and the same node; only the rate differs.

## Mempool and template, desk node (probe)

| Minute (UTC) | Samples | Mempool | Ready (no parent in mempool) | Ready mass, blocks of 500k | Other traffic in mempool | Other ready | Other at 100, n | Other at 100, mean mass | Our payments in mempool | Our heavy in mempool / ready | Floor in mempool / ready | R150 in mempool / ready | R300 in mempool / ready | R450 in mempool / ready | Template txs | Template storage mass | Template txs over 100k storage mass | Template: payments | Template: our heavy | Template: floor | Template: r150 | Template: r300 | Template: r450 | Template: other | Fee estimate priority / normal / low | Public 1 mempool | Public 5 mempool |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|---:|---:|
| 2026-11-13T03:30 | 3 | 154 | 154 | 37.68 | 81 | 81 | - | - | 0 | 56 / 56 | 3 / 3 | 4 / 4 | 4 / 4 | 4 / 4 | 7 | 472,497 | 1 | 0 | 1 | 0 | 0 | 2 | 3 | 1 | 352.2 / 178.2 / 114.0 | 165 | 177 |
| 2026-11-13T03:31 | 3 | 156 | 163 | 38.43 | 91 | 91 | - | - | 0 | 56 / 56 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 9 | 472,083 | 1 | 0 | 1 | 0 | 0 | 1 | 3 | 3 | 379.6 / 180.6 / 114.2 | 140 | 143 |
| 2026-11-13T03:32 | 3 | 202 | 202 | 40.72 | 135 | 135 | - | - | 0 | 57 / 57 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 9 | 472,598 | 1 | 0 | 1 | 0 | 0 | 1 | 3 | 3 | 408.5 / 182.7 / 114.3 | 189 | 191 |
| 2026-11-13T03:33 | 3 | 238 | 238 | 40.07 | 171 | 171 | - | - | 0 | 56 / 56 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 7 | 472,264 | 1 | 0 | 1 | 0 | 0 | 1 | 4 | 1 | 418.9 / 183.3 / 114.4 | 210 | 226 |
| 2026-11-13T03:34 | 3 | 302 | 313 | 41.91 | 239 | 239 | - | - | 0 | 58 / 58 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 6 | 388,942 | 1 | 0 | 1 | 0 | 0 | 2 | 1 | 2 | 487.0 / 186.8 / 114.7 | 312 | 322 |
| 2026-11-13T03:35 | 3 | 327 | 327 | 40.51 | 260 | 260 | - | - | 0 | 54 / 54 | 4 / 4 | 4 / 4 | 3 / 3 | 4 / 4 | 8 | 349,452 | 1 | 0 | 1 | 0 | 0 | 0 | 2 | 3 | 486.9 / 186.8 / 114.7 | 337 | 355 |
| 2026-11-13T03:36 | 2 | 369 | 369 | 42.34 | 301 | 301 | - | - | 0 | 57 / 57 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 8 | 391,179 | 1 | 0 | 1 | 0 | 0 | 1 | 3 | 4 | 517.1 / 188.0 / 114.8 | 402 | 413 |
| 2026-11-13T03:37 | 3 | 431 | 431 | 42.60 | 366 | 366 | - | - | 0 | 56 / 56 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 6 | 351,012 | 1 | 0 | 1 | 0 | 0 | 1 | 2 | 3 | 528.8 / 188.4 / 114.8 | 427 | 427 |
| 2026-11-13T03:38 | 3 | 545 | 545 | 41.07 | 481 | 481 | - | - | 0 | 51 / 51 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 11 | 431,769 | 1 | 0 | 1 | 0 | 0 | 0 | 3 | 7 | 575.7 / 189.8 / 114.9 | 528 | 543 |
| 2026-11-13T03:39 | 3 | 811 | 811 | 45.16 | 745 | 745 | - | - | 0 | 54 / 54 | 4 / 4 | 4 / 4 | 3 / 3 | 3 / 3 | 9 | 308,373 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 7 | 655.9 / 191.6 / 115.0 | 843 | 848 |
| 2026-11-13T03:40 | 3 | 923 | 947 | 45.06 | 876 | 876 | - | - | 0 | 52 / 52 | 4 / 4 | 4 / 4 | 3 / 3 | 4 / 4 | 6 | 307,562 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 4 | 710.9 / 192.5 / 115.1 | 949 | 961 |
| 2026-11-13T03:41 | 3 | 1,052 | 1,052 | 48.27 | 978 | 978 | - | - | 0 | 58 / 58 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 5 | 266,791 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 4 | 765.9 / 193.3 / 115.1 | 1,036 | 1,040 |

Read by the probe on the desk's private TN10 node every 20 s, read-only; each cell is the median of that minute's samples. Pre-run 17: ready count and ready mass come from the full mempool read up to 10,000 entries and from the node's own figures (getFeeEstimateExperimental, verbose) above that, where the per-class columns stay blank (the node's wRPC replies are capped at 128 MiB, about 12,500 entries). Ready means no parent in the mempool: in rusty-kaspa v2.1.0 only those are in the selector's frontier. Ready mass is compared with one block's mass limit (500,000): at or under 1 the selector takes all ready transactions best-first; over 1 it samples at random weighted by (fee/mass)^3 (over 4, sample_inplace). Mass is the larger of compute and storage mass, as the v2.1.0 selector normalises it (transient mass is not in the RPC). Other traffic is every mempool entry not in our sender logs (our heavy lane is its own class, our heavy); its fee rate is the node's fee over that mass. Template transactions carry no id in the RPC, so each is matched to a mempool entry by its first input. The template is the desk node's own getBlockTemplate (never submitted): what this node would put in a block at that moment, not a miner's template. The fee estimate is the node's getFeeEstimate, read only; no sender reads it. Public mempool is getInfo's mempool size on each kept public kaspad.
