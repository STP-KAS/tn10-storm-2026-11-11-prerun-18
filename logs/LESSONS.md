> **Experimental. We are just trying this.** [Disclaimer](../DISCLAIMER.md) · Kaspa Testnet-10 only; tKAS has no value.
>
> Our own testing. What we observed in this run, on our own nodes. Not a claim about how TN10 or Kaspa behave in general. No key, seed, txid, covenant id, address, host or port.

# Lessons, pre-run 18

Written after the run, 2026-11-13, from the files on origin and the desk's own logs (read-only). Times are UTC unless marked Brussels.

## Short version

- **Pre-run 18 ran through RETURN.** Every step file is on origin for the desk and for Mini, then TIMELINE, MEMPOOL and METHOD; every whole minute kept pace and was clean; no repair, no restart. Every OK family hop landed (floor 7,413, r150 8,954, r300 11,338, r450 12,340) and all 23,211 lane transactions landed (0 rejected, 0 lost).
- **With one lane greedy, we observed a leapfrog climb.** Lane 1 (greedy: steps up × 1.25 whenever it landed under 110 percent of its own reference, never steps down) and lane 2 (the normal rule) both started at 150. Lane 1 went 150 → 188 → 235 → 294 → 368 → 460 → 575 → 719 → 899 → 1,124 → 1,405 in about 21 minutes (10 steps up). Lane 2 followed each time it fell under 90 percent: 14 steps up and 4 down, to 1,124 by the end of the 03:52 minute and to 1,405 at 03:53:22Z, 37 s before the symmetric repeat reset both. The cap (2,000) and the cap guard were not reached in the 24 greedy minutes.
- **It was competition, not capacity.** The two lanes together landed about the same every minute (median 562 a minute in the first greedy part, 560 in the second, against 548 at the reference; 543–595 except one flush minute at 406), and the node merged about the same number of blocks a minute throughout (575–643). Lane 1 went over its 110 percent target many times (up to 151 percent), always by taking places from lane 2 (lane 2 down to 53 percent). Raising both rates about nine-fold did not buy the pair more places; it moved places between them and pushed everyone else out.
- **The fixed tiers were squeezed close to zero.** Per family, percent of BASE (floor 100 / r150 / r300 / r450): at the reference (both lanes 150) 43 / 68 / 96 / 104; first greedy part (150 → 460) median 14 / 35 / 82 / 101; second greedy part (460 → 1,405) median 1 / 4 / 22 / 40; in the 03:51 and 03:52 minutes (lane 1 at 1,124 and 1,405) 0 / 0–1 / 5–8 / 12–18.
- **The symmetric repeat came straight back down.** Both lanes reset to 150 at 03:53:59Z and stepped to 120 and then 100 on the normal rule (decisions on the 03:55 and 03:57 minutes), 100 / 100 in effect from 03:59, about four minutes after the reset. The tiers recovered within minutes: at 150 / 150 again 39–46 / 66–71 / 92–98 / 98–110, at 100 / 100 (03:59–04:01) 64–66 / 85–86 / 98–100 / 104–106; RETURN median 101 / 99 / 99 / 102.
- Our two lanes slowed other TN10 users' transactions while they ran, much more than in earlier pre-runs once they climbed (below).

## The question

Pre-run 17's two equal heavy lanes on one symmetric rule stepped each other down to 100. Pre-run 18 asked the case that can climb: **one lane greedy on purpose** (it wants 110 percent of its own reference and never steps down) against an equal lane on the normal rule. Both lanes are ours: 30 chains each, about 266,700 storage mass a transaction, one lane process, the same key-16 pile. Four fixed-rate covenant tiers are the bystanders (floor 100, r150 150, r300 300, r450 450, four families each, priced on the node's mass).

Rules, once a minute, each lane reading only its own landings against its HOLD-1 reference (both at 150, minutes 2–10): **lane 1 275, lane 2 286** landed a minute.

- Lane 1 (greedy): under 110 percent → × 1.25 (cap 2,000); otherwise unchanged; never down.
- Lane 2 (normal): under 90 percent → × 1.25 (cap 2,000); at or over 90 percent two minutes running → × 0.8 (floor 100); otherwise unchanged.
- Cap guard: 4 decided minutes with both at 2,000, or lane 1 alone at 2,000 → `CAP_REACHED`, both back to 150. Not reached.
- The symmetric repeat (8 minutes): both back to 150, the normal rule for both.

## What happened

- Before the open: key 0's 2,104 small coins consolidated (29 transactions, fees 2.43), key 0 refilled from the pile sized on use (3,500 coins, 74,071 tKAS moved between our own keys, fees 8.06; 85,043 usable after), keys 1–15 funded. A budget check before genesis projected the end at 30,311 usable against the 18,000 line (8,000 margin) and passed. Hop calibration at 100 and 450 and lane calibration at 2,000 and 100 matched the node. An offline run of the controller code predicted a climb (below). Offline rehearsal p18-a exited 0. The bot's free check ran once, read-only, before arming.
- Live run: desk runner from 03:07:40Z. BASE 03:10–03:19 (both lanes 0), HOLD-1 03:20–03:29 (both 30 at 150: the references), HOLD-2 = greedy part 1 03:30–03:41, HOLD-3 = greedy part 2 03:42–03:53 (no reset between the parts) and the symmetric repeat 03:54–04:01, drain (lanes 0) from 04:01:59Z, HOLD-4 pinned minute 04:06, RETURN 04:08–04:17, then a 5-minute counter tail. `RUN_STOP return-closed` 04:18:24Z, `RUN end` 04:23:43Z.
- The outside heavy fee-100 stream of pre-runs 14–16 was absent again (0 in almost every minute, 1 in four minutes).
- The bot's box stalled once, in the middle of the climb: its heartbeat (every 20 s) has a gap from 03:50:13Z to 03:53:04Z, and the waiter's git fetch in flight took 161.8 s and failed (`curl 28 Operation too slow`, rc 128) at 03:53:05Z. The waiter's next loop worked and it saw HOLD-3 6 s after it reached origin. Nothing of the run is on that box, so the desk and Mini were not affected.

## The rate path

Rates are those in effect during each minute (a decision lands about 22 s into the next minute). Decisions are in [duel.log](duel.log).

| Part | Minutes | Lane 1 (greedy) | Lane 2 (normal rule) |
|---|---|---|---|
| HOLD-1 reference | 03:20–03:29 | 150 | 150 |
| Greedy part 1 | 03:30–03:41 | 150 150 188 188 188 235 294 294 294 294 368 460 | 150 150 150 188 235 235 188 235 294 368 368 294 |
| Greedy part 2 | 03:42–03:53 | 460 460 460 575 719 719 719 719 899 1,124 1,405 1,405 | 368 460 575 575 460 575 719 899 899 719 899 1,124 |
| End of the greedy part | 03:53:22Z | 1,405 | stepped to 1,405, in effect 37 s |
| Symmetric repeat | 03:54–04:01 | 150 150 150 120 120 100 100 100 | the same |

- Lane 1: 10 steps up, 0 down. Its landings were 83–151 percent of its reference; it stepped up every time it was under 110 percent, which happened each time lane 2 had just caught up.
- Lane 2: 14 steps up, 4 down (368 → 294 at 03:39, 575 → 460 at 03:44, 899 → 719 at 03:49, and 235 → 188 at 03:34). Its landings were 53–115 percent of its reference.
- Lane 1's share of the two lanes' landings: median 56 percent in part 1 and 58 in part 2 (43–72), against 50 at the reference.
- **No cap.** 2,000 was never reached; the next step for lane 1 would have been 1,756. At the pace we saw (about one step every two minutes), the cap was a few minutes away when the greedy part ended.

**The leapfrog:** lane 1 steps up, takes places from lane 2, lane 2 falls under 90 percent and steps up, lane 1 drops back under 110 percent and steps up again. Neither lane could stay ahead, so neither stopped.

## Landing and cost

| Part | Lane rates | Floor % BASE | R150 % BASE | R300 % BASE | R450 % BASE | Lane 1 / 2 landed, median | Lanes together, median | Other traffic, median | Fee est. priority, median | Ready, blocks, median | Mempool, median |
|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| BASE (10 min) | 0 / 0 | 100 (97–103) | 100 (93–102) | 100 (94–106) | 100 (94–109) | — | — | 3,132 | 144 | 1.3 | 14 |
| HOLD-1 ref (10) | 150 / 150 | 43 (36–46) | 68 (61–71) | 96 (91–100) | 104 (102–112) | 278 / 280 | 548 | 2,992 | 341 | 36.9 | 146 |
| Greedy 1 (12) | 150 → 460 / 150 → 294 | 14 (3–40) | 35 (13–63) | 82 (54–97) | 101 (80–109) | 312 / 245 | 562 | 2,904 | 502 | 41.0 | 348 |
| Greedy 2 (12) | 460 → 1,405 / 368 → 1,124 | 1 (0–18) | 4 (0–20) | 22 (5–46) | 40 (12–76) | 304 / 235 | 560 | 2,404 (425–7,764) | 1,370 | 58.8 | 3,110 |
| Symmetric repeat (8) | 150 → 100 | 58 (39–66) | 79 (66–86) | 98 (92–106) | 105 (98–110) | 274 / 270 | 538 | 2,999 | 317 | 37.0 | 109 |
| of which 100 / 100 (3) | 100 / 100 | 65 (64–66) | 86 (85–86) | 98 (98–100) | 106 (104–106) | 268 / 269 | 527 | 2,943 | 290 | 37.4 | 95 |
| RETURN (10) | 0 / 0 | 101 (92–110) | 99 (90–106) | 99 (92–102) | 102 (93–105) | — | — | 3,120 | 170 | 1.3 | 16 |

BASE per family: floor 47.6, r150 49.4, r300 50.2, r450 48.5 hops a minute.

- **Who lost.** Each fixed tier held its pace until the lanes passed about its own rate, then fell: floor and r150 at once (the lanes were already at 150), r300 once the lanes passed about 300 (82 percent with lane 1 at 294, 54–61 percent with the lanes at 368–460), r450 once they passed about 450 (101–103 percent with the lanes under 300, 76 at 460 / 368, 12 at 1,405 / 899). Once the lanes paid more than a tier, the tier fell behind; the "about twice the competitor's rate" reading of pre-runs 14–17 holds only while the competitor stays put.
- **Every OK hop still landed in the end.** A chain's next hop waits for the last one, so the families slowed rather than lost hops: by the end of the counter tail every OK hop was included (floor 7,413, r150 8,954, r300 11,338, r450 12,340).
- **Cost per lane transaction** (lane log, fees ÷ OK, by the rate in that minute): 0.27 tKAS at 100, 0.30 at 120, 0.40 at 150, 0.55 at 188, 0.84 at 294, 1.32 at 460, 1.64 at 575, 2.04 at 719, 2.56 at 899, 3.49 at 1,124, 3.75 at 1,405.
- **What greed bought.** In the 24 greedy minutes lane 1 landed 7,386 (308 a minute, 12 percent over its reference pace) for 11,360 tKAS (1.54 a landed transaction, about 3.8 times the reference cost). Lane 2 landed 5,857 (244 a minute, 13 percent under its reference) for 7,558 tKAS (1.29 a transaction). Together they landed about what they landed at 150 / 150 and paid about 3.5 times as much.
- **Flushes.** Twice in the second greedy part the mempool dropped from about 6,000 entries to about 1,000 in one minute and other traffic landed in bulk: 03:50 (5,883 other, ready 80 → 35 blocks, mempool 6,076 → 892) and 03:53 (7,764 other, ready 75 → 35 blocks, mempool 6,374 → 1,049); the fixed tiers also landed more in those two minutes (floor 7–8.5 a family). The minute after the reset (03:54) landed 5,063 other. We do not know what caused the two flushes in the climb; our lanes were still at 899–1,405 then, and landed fewer (434 and 406) in those minutes.

## Theory against what we observed

| Written before the run ([plan/PLAN.md](../plan/PLAN.md#prediction-written-before-the-run)) | Observed |
|---|---|
| Offline run of the controller code (toy world): a leapfrog 150 → 2,000 in about 13 minutes, cap guard at about 16 minutes, then a climb again. | A leapfrog, as in the toy, but slower: 150 → 1,405 in about 21 minutes, no cap in 24. |
| Our best guess: lane 1 climbs to 300–1,000 in 24 minutes, lane 2 follows part of the way, a cap perhaps one in three. | Higher than our guess: lane 1 to 1,405, lane 2 all the way (to 1,124, then 1,405 at the last decision). No cap. |
| If lane 1 stays under 110 percent while lane 2 is fine at the floor, it is a ceiling, not a spiral. | Not a ceiling: lane 1 reached 117–151 percent many times, by taking places from lane 2; lane 2 never stayed at the floor; the lanes together landed about the same every minute. |
| The symmetric repeat comes back to 100–150 within 8 minutes. | Yes: 100 / 100 about four minutes after the reset. |
| Fixed tiers lose more the higher the lanes go; at 2,000 every tier slows. | Yes, in order of rate; at 1,124–1,405 even r450 kept only 12–18 percent in a minute. |
| Cost about 0.40 tKAS at 150, about 1.6 at 600. | 0.40 at 150, 1.64 at 575. |
| Lane fees for the plan in the toy: 29,000–35,000 tKAS. | 22,558 (no cap reached). |

## Our lanes slowed other TN10 users

With the lanes on (42 minutes, 03:20–04:01), other traffic landed on our desk node had a median of 2,992 a minute at 150 / 150 (about 4–5 percent under BASE's 3,132), 2,904 in the first greedy part (about 7 percent under) and 2,404 in the second (about 23 percent under, with single minutes from 425 to 7,764). Over the second greedy part's 12 minutes, other traffic landed 34,740 against about 37,600 at BASE's pace (about 8 percent fewer), much of the rest waiting: the desk mempool grew to 6,374 entries and the ready mass to 80 blocks, and the node's priority fee estimate rose to 2,197 (median 1,370 in that part) against 144 in BASE. Some of the delayed traffic landed as the backlog cleared: the symmetric repeat's 8 minutes landed 26,130, about 4 percent over BASE's pace. Our own floor hops at 100, a stand-in for a low-fee user, ran at 0–1 percent of their BASE pace in the minutes our lanes were at 1,124–1,405. We did this on purpose, with the operator's OK, in bounded steps, and it is in this repo's [public statement](../PLAYBOOK.md#public-statement). Other users paying up to about the lanes' rates were hurt most; in our tiers, paying well above the lanes kept pace only while the lanes stayed under about 300, and at the top of the climb the lanes paid about 1,400 sompi/gram.

## Bot

The bot sent nothing. Its waiter saw desk HOLD-3 on origin at 04:02:28Z (6 s after it got there) and pinned 04:06Z; its free check at 04:05:30Z, 29 s before the minute, found the desk's kept nodes 1 and 5 (2 distinct kaspads) and every other node that answered on the same kaspad as a kept node. It filed `NO SEND no-free-node` in [counts/bot/HOLD-4.md](../counts/bot/HOLD-4.md) after the minute closed (on origin 04:07:04Z, first try). Coins were not the reason.

## Mini

Mini read every published minute in full (10 / 10 / 12 / 20 / 1 / 10) and matched the desk in **251 of 252** cohort cells. The one difference is r150 in the 03:54 minute (the minute after the second flush and the reset): Mini 130, desk 131. Mini's counter noted 67 chain-block removals after a minute had closed over the whole run (not taken out; the closed minute is not rewritten), against 0 in pre-run 17; 25 of them came in HOLD-3, during the climb. Its TN10 kaspad was not wiped or restarted.

## Spend

| Item | tKAS |
|---|---:|
| Our two heavy lanes, fees | 22,558.34 (lane 1 13,170.23, lane 2 9,388.11); 870.41 parked on our sink key, not swept |
| of which the 24 greedy minutes | 18,918.27 (lane 1 11,360.01, lane 2 7,558.26) |
| Family hops, fees (floor / r150 / r300 / r450) | 4,545.62 (305.34 / 553.12 / 1,400.57 / 2,286.58), node mass about 41,100–41,200 a hop |
| Consolidation and refill of key 0 before the open | 10.49 (2.43 + 8.06); the refill moved 74,071 tKAS between our own keys |
| Calibrations and genesis funding | a handful of single transactions |
| Bot | 0 |
| **About** | **27,100** |

Family submit results other than OK were `already_spent` and `orphan` only (the builder's waiting retries); 0 rate or full rejects. tKAS is not a limit (operator, 12 Nov).

Keys after the run (read-only status): key 0 4,646 coins over 3 tKAS, **41,339 usable** (85,031 at the budget check; abort line 18,000; projected 30,311), 1,451 small coins; keys 1–15 have no genesis coin; payment pile 796 coins. Key 0 used about 1.09 usable tKAS per OK hop (43,692 for 40,045).

## What this seems to show

- One lane that wants more than its share and never backs down, against one that follows a normal "pay more when behind" rule, was enough to start a climb on this node. The climb was a leapfrog: each step by one side pushed the other under its line. In 24 minutes it went from 150 to 1,405, about nine-fold, and had not stopped.
- The pair did not land more for it. Places per minute were set by the node (about one heavy transaction a block); higher rates only moved them between the two lanes and pushed lower-paying traffic out. The bystanders and other users paid for the duel in waiting time; the two lanes paid for it in fees (about 3.5 times as much for the same landings).
- Taking the greedy side away (the symmetric repeat) brought both back to the floor within about four minutes, and the tiers recovered with them.
- What this cannot say: one run, 24 greedy minutes, both sides ours on fixed rules and fixed references, one node's view, no outside stream; the cap was not reached, so what happens there (and whether the cap guard's reset starts the climb again, as in the toy) is not observed. We are just testing.

## Every minute

Rates in effect during the minute; decisions are the duel log's (rate before → after, applied about 22 s into the next minute). Merged blocks is the counter's coinbase count from the duel log (duel minutes only). Drain minutes 04:02–04:05 and 04:07 are not step minutes.

| Min (UTC) | Step | Part | Lane 1 / lane 2 rate in effect | Floor / fam (% BASE) | R150 / fam | R300 / fam | R450 / fam | Lane 1 landed | Lane 2 landed | Lane 1 / 2, % of ref | Lane 1 decision | Lane 2 decision | Other traffic | Merged blocks | Ready, blocks | Mempool | Fee est. priority |
|---|---|---|---|---:|---:|---:|---:|---:|---:|---|---|---|---:|---:|---:|---:|---:|
| 03:10 | BASE | BASE | 0 / 0 | 47.2 (99%) | 48.0 (97%) | 47.5 (95%) | 48.2 (99%) | 0 | 0 | — | — | — | 3,103 | — | 1.2 | 14 | 124.9 |
| 03:11 | BASE | BASE | 0 / 0 | 47.5 (100%) | 49.5 (100%) | 53.2 (106%) | 52.8 (109%) | 0 | 0 | — | — | — | 3,222 | — | 1.3 | 16 | 151.2 |
| 03:12 | BASE | BASE | 0 / 0 | 47.5 (100%) | 48.2 (98%) | 48.2 (96%) | 48.2 (99%) | 0 | 0 | — | — | — | 3,128 | — | 1.5 | 6 | 155.4 |
| 03:13 | BASE | BASE | 0 / 0 | 46.0 (97%) | 45.8 (93%) | 47.0 (94%) | 47.2 (97%) | 0 | 0 | — | — | — | 3,160 | — | 1.2 | 14 | 140.2 |
| 03:14 | BASE | BASE | 0 / 0 | 48.2 (101%) | 50.2 (102%) | 50.2 (100%) | 48.5 (100%) | 0 | 0 | — | — | — | 3,136 | — | 1.3 | 6 | 151.9 |
| 03:15 | BASE | BASE | 0 / 0 | 49.0 (103%) | 49.8 (101%) | 50.2 (100%) | 50.5 (104%) | 0 | 0 | — | — | — | 3,105 | — | 1.3 | 16 | 150.1 |
| 03:16 | BASE | BASE | 0 / 0 | 47.8 (100%) | 50.5 (102%) | 51.8 (103%) | 50.0 (103%) | 0 | 0 | — | — | — | 3,125 | — | 0.9 | 6 | 100.0 |
| 03:17 | BASE | BASE | 0 / 0 | 49.0 (103%) | 49.2 (100%) | 50.2 (100%) | 48.5 (100%) | 0 | 0 | — | — | — | 3,110 | — | 1.0 | 7 | 118.1 |
| 03:18 | BASE | BASE | 0 / 0 | 49.0 (103%) | 49.8 (101%) | 50.5 (100%) | 50.5 (104%) | 0 | 0 | — | — | — | 3,176 | — | 1.3 | 16 | 148.1 |
| 03:19 | BASE | BASE | 0 / 0 | 46.8 (98%) | 47.2 (96%) | 47.0 (94%) | 45.5 (94%) | 0 | 0 | — | — | — | 3,156 | — | 1.2 | 15 | 136.3 |
| 03:20 | HOLD-1 | HOLD-1 ref | 150 / 150 | 21.2 (45%) | 33.0 (67%) | 48.2 (96%) | 51.0 (105%) | 280 | 265 | — | — | — | 2,945 | — | 31.6 | 132 | 333.4 |
| 03:21 | HOLD-1 | HOLD-1 ref | 150 / 150 | 20.2 (43%) | 35.0 (71%) | 45.5 (91%) | 49.5 (102%) | 293 | 289 | — | — | — | 3,165 | — | 36.1 | 167 | 341.1 |
| 03:22 | HOLD-1 | HOLD-1 ref | 150 / 150 | 17.2 (36%) | 30.2 (61%) | 48.0 (96%) | 50.0 (103%) | 236 | 294 | — | — | — | 2,977 | — | 32.9 | 113 | 301.9 |
| 03:23 | HOLD-1 | HOLD-1 ref | 150 / 150 | 20.5 (43%) | 32.5 (66%) | 49.2 (98%) | 51.0 (105%) | 275 | 294 | — | — | — | 2,987 | — | 36.4 | 139 | 335.4 |
| 03:24 | HOLD-1 | HOLD-1 ref | 150 / 150 | 20.2 (43%) | 34.2 (69%) | 46.8 (93%) | 50.2 (104%) | 284 | 287 | — | — | — | 2,937 | — | 37.9 | 137 | 345.0 |
| 03:25 | HOLD-1 | HOLD-1 ref | 150 / 150 | 20.2 (43%) | 33.8 (68%) | 46.8 (93%) | 49.8 (103%) | 267 | 272 | — | — | — | 3,000 | — | 34.4 | 166 | 307.1 |
| 03:26 | HOLD-1 | HOLD-1 ref | 150 / 150 | 22.0 (46%) | 33.5 (68%) | 50.0 (100%) | 54.2 (112%) | 286 | 286 | — | — | — | 2,998 | — | 36.7 | 153 | 341.7 |
| 03:27 | HOLD-1 | HOLD-1 ref | 150 / 150 | 18.2 (38%) | 35.0 (71%) | 48.8 (97%) | 53.0 (109%) | 269 | 273 | — | — | — | 3,024 | — | 37.5 | 149 | 346.4 |
| 03:28 | HOLD-1 | HOLD-1 ref | 150 / 150 | 20.2 (43%) | 33.2 (67%) | 47.8 (95%) | 49.2 (102%) | 273 | 269 | — | — | — | 2,961 | — | 37.3 | 142 | 349.1 |
| 03:29 | HOLD-1 | HOLD-1 ref | 150 / 150 | 20.5 (43%) | 33.8 (68%) | 49.0 (98%) | 51.2 (106%) | 285 | 266 | — | — | — | 2,997 | — | 37.6 | 160 | 340.5 |
| 03:30 | HOLD-2 | greedy 1 | 150 / 150 | 18.5 (39%) | 31.2 (63%) | 46.2 (92%) | 50.0 (103%) | 273 | 277 | 99% / 97% | 150->188 | 150->150 | 2,943 | 591 | 37.7 | 154 | 352.2 |
| 03:31 | HOLD-2 | greedy 1 | 150 / 150 | 19.2 (40%) | 30.2 (61%) | 48.5 (97%) | 52.8 (109%) | 323 | 248 | 117% / 87% | 188->188 | 150->188 | 2,972 | 603 | 38.4 | 156 | 379.6 |
| 03:32 | HOLD-2 | greedy 1 | 188 / 150 | 13.5 (28%) | 28.5 (58%) | 45.5 (91%) | 49.2 (102%) | 315 | 235 | 115% / 82% | 188->188 | 188->235 | 2,990 | 589 | 40.7 | 202 | 408.5 |
| 03:33 | HOLD-2 | greedy 1 | 188 / 188 | 10.5 (22%) | 24.5 (50%) | 44.5 (89%) | 49.8 (103%) | 255 | 308 | 93% / 108% | 188->235 | 235->235 | 3,016 | 597 | 40.1 | 238 | 418.9 |
| 03:34 | HOLD-2 | greedy 1 | 188 / 235 | 9.8 (20%) | 20.8 (42%) | 43.5 (87%) | 50.0 (103%) | 263 | 330 | 96% / 115% | 235->294 | 235->188 | 2,902 | 643 | 41.9 | 302 | 487.0 |
| 03:35 | HOLD-2 | greedy 1 | 235 / 235 | 6.0 (13%) | 17.8 (36%) | 40.8 (81%) | 48.8 (101%) | 361 | 209 | 131% / 73% | 294->294 | 188->235 | 2,968 | 613 | 40.5 | 327 | 486.9 |
| 03:36 | HOLD-2 | greedy 1 | 294 / 188 | 7.8 (16%) | 16.8 (34%) | 41.2 (82%) | 49.5 (102%) | 393 | 151 | 143% / 53% | 294->294 | 235->294 | 2,850 | 589 | 42.3 | 369 | 517.1 |
| 03:37 | HOLD-2 | greedy 1 | 294 / 235 | 4.0 (8%) | 11.8 (24%) | 37.5 (75%) | 45.2 (93%) | 310 | 242 | 113% / 85% | 294->294 | 294->368 | 2,882 | 590 | 42.6 | 431 | 528.8 |
| 03:38 | HOLD-2 | greedy 1 | 294 / 294 | 3.8 (8%) | 10.0 (20%) | 31.8 (63%) | 47.0 (97%) | 251 | 292 | 91% / 102% | 294->368 | 368->368 | 2,643 | 576 | 41.1 | 545 | 575.7 |
| 03:39 | HOLD-2 | greedy 1 | 294 / 368 | 2.2 (5%) | 8.2 (17%) | 30.8 (61%) | 42.2 (87%) | 244 | 322 | 89% / 113% | 368->460 | 368->294 | 2,891 | 593 | 45.2 | 811 | 655.9 |
| 03:40 | HOLD-2 | greedy 1 | 368 / 368 | 1.5 (3%) | 7.0 (14%) | 27.0 (54%) | 40.5 (84%) | 337 | 225 | 123% / 79% | 460->460 | 294->368 | 2,746 | 602 | 45.1 | 923 | 710.9 |
| 03:41 | HOLD-2 | greedy 1 | 460 / 294 | 2.0 (4%) | 6.5 (13%) | 28.0 (56%) | 39.0 (80%) | 399 | 187 | 145% / 65% | 460->460 | 368->460 | 2,906 | 639 | 48.3 | 1,052 | 765.9 |
| 03:42 | HOLD-3 | greedy 2 | 460 / 368 | 1.5 (3%) | 4.0 (8%) | 23.2 (46%) | 36.8 (76%) | 327 | 242 | 119% / 85% | 460->460 | 460->575 | 2,625 | 611 | 51.5 | 1,323 | 816.6 |
| 03:43 | HOLD-3 | greedy 2 | 460 / 460 | 1.0 (2%) | 3.2 (7%) | 16.5 (33%) | 31.5 (65%) | 241 | 318 | 88% / 111% | 460->575 | 575->575 | 2,411 | 583 | 54.1 | 1,734 | 941.5 |
| 03:44 | HOLD-3 | greedy 2 | 460 / 575 | 0.8 (2%) | 3.0 (6%) | 11.2 (22%) | 28.2 (58%) | 252 | 310 | 92% / 108% | 575->719 | 575->460 | 2,398 | 598 | 56.4 | 2,348 | 1005.0 |
| 03:45 | HOLD-3 | greedy 2 | 575 / 575 | 0.5 (1%) | 2.0 (4%) | 15.0 (30%) | 29.5 (61%) | 363 | 228 | 132% / 80% | 719->719 | 460->575 | 2,663 | 640 | 61.6 | 2,969 | 1106.3 |
| 03:46 | HOLD-3 | greedy 2 | 719 / 460 | 0.0 (0%) | 1.0 (2%) | 10.8 (21%) | 21.0 (43%) | 364 | 191 | 132% / 67% | 719->719 | 575->719 | 2,196 | 598 | 63.3 | 3,250 | 1158.5 |
| 03:47 | HOLD-3 | greedy 2 | 719 / 575 | 0.2 (1%) | 1.8 (4%) | 7.8 (15%) | 19.5 (40%) | 326 | 243 | 119% / 85% | 719->719 | 719->899 | 2,194 | 613 | 69.2 | 3,947 | 1284.3 |
| 03:48 | HOLD-3 | greedy 2 | 719 / 719 | 0.5 (1%) | 1.0 (2%) | 7.2 (14%) | 19.8 (41%) | 279 | 316 | 101% / 110% | 719->899 | 899->899 | 1,916 | 638 | 76.1 | 4,703 | 1455.9 |
| 03:49 | HOLD-3 | greedy 2 | 719 / 899 | 1.0 (2%) | 1.5 (3%) | 5.2 (10%) | 17.0 (35%) | 229 | 296 | 83% / 103% | 899->1124 | 899->719 | 3,323 | 575 | 79.7 | 6,076 | 1534.1 |
| 03:50 | HOLD-3 | greedy 2 | 899 / 899 | 8.5 (18%) | 10.0 (20%) | 12.5 (25%) | 17.2 (36%) | 281 | 153 | 102% / 53% | 1124->1405 | 719->899 | 5,883 | 581 | 35.1 | 892 | 1504.0 |
| 03:51 | HOLD-3 | greedy 2 | 1124 / 719 | 0.0 (0%) | 0.2 (1%) | 4.0 (8%) | 8.5 (18%) | 416 | 164 | 151% / 57% | 1405->1405 | 899->1124 | 425 | 630 | 57.2 | 3,663 | 1945.7 |
| 03:52 | HOLD-3 | greedy 2 | 1405 / 899 | 0.0 (0%) | 0.0 (0%) | 2.5 (5%) | 6.0 (12%) | 373 | 175 | 136% / 61% | 1405->1405 | 1124->1405 | 942 | 582 | 75.0 | 6,374 | 2131.6 |
| 03:53 | HOLD-3 | greedy 2 | 1405 / 1124 | 7.0 (15%) | 8.0 (16%) | 12.0 (24%) | 15.0 (31%) | 211 | 195 | — | — | — | 7,764 | — | 35.5 | 1,049 | 2196.9 |
| 03:54 | HOLD-3 | sym repeat | 150 / 150 | 18.8 (39%) | 32.8 (66%) | 46.5 (93%) | 48.0 (99%) | 297 | 302 | 108% / 106% | 150->150 | 150->150 | 5,063 | 639 | 35.9 | 134 | 372.6 |
| 03:55 | HOLD-3 | sym repeat | 150 / 150 | 19.0 (40%) | 33.0 (67%) | 49.0 (98%) | 53.5 (110%) | 274 | 270 | 100% / 94% | 150->120 | 150->120 | 2,991 | 589 | 35.7 | 134 | 370.8 |
| 03:56 | HOLD-3 | sym repeat | 150 / 150 | 21.8 (46%) | 35.2 (71%) | 46.2 (92%) | 47.5 (98%) | 273 | 260 | 99% / 91% | 120->120 | 120->120 | 3,222 | 581 | 38.2 | 106 | 322.7 |
| 03:57 | HOLD-3 | sym repeat | 120 / 120 | 27.0 (57%) | 38.8 (78%) | 53.2 (106%) | 53.0 (109%) | 265 | 276 | 96% / 97% | 120->100 | 120->100 | 3,007 | 591 | 36.4 | 111 | 326.5 |
| 03:58 | HOLD-3 | sym repeat | 120 / 120 | 28.0 (59%) | 39.8 (81%) | 49.5 (99%) | 49.8 (103%) | 274 | 262 | 100% / 92% | 100->100 | 100->100 | 2,959 | 589 | 40.3 | 110 | 311.9 |
| 03:59 | HOLD-3 | sym repeat | 100 / 100 | 30.2 (64%) | 42.2 (86%) | 49.2 (98%) | 50.5 (104%) | 256 | 269 | 93% / 94% | 100->100 | 100->100 | 3,012 | 584 | 37.6 | 108 | 276.6 |
| 04:00 | HOLD-3 | sym repeat | 100 / 100 | 30.8 (65%) | 42.2 (86%) | 50.0 (100%) | 51.2 (106%) | 268 | 259 | 97% / 91% | 100->100 | 100->100 | 2,943 | 597 | 36.0 | 95 | 298.1 |
| 04:01 | HOLD-3 | sym repeat | 100 / 100 | 31.5 (66%) | 42.0 (85%) | 49.2 (98%) | 51.5 (106%) | 276 | 286 | — | — | — | 2,933 | — | 37.4 | 89 | 289.6 |
| 04:06 | HOLD-4 | drain | 0 / 0 | 47.2 (99%) | 47.5 (96%) | 46.5 (93%) | 47.0 (97%) | 0 | 0 | — | — | — | 3,131 | — | 1.1 | 15 | 173.5 |
| 04:08 | RETURN | N = 0 | 0 / 0 | 48.5 (102%) | 47.2 (96%) | 48.0 (96%) | 48.0 (99%) | 0 | 0 | — | — | — | 3,334 | — | 1.0 | 12 | 151.9 |
| 04:09 | RETURN | N = 0 | 0 / 0 | 47.2 (99%) | 49.0 (99%) | 50.0 (100%) | 49.8 (103%) | 0 | 0 | — | — | — | 3,118 | — | 1.3 | 16 | 173.3 |
| 04:10 | RETURN | N = 0 | 0 / 0 | 48.2 (101%) | 49.0 (99%) | 49.5 (99%) | 47.2 (97%) | 0 | 0 | — | — | — | 3,091 | — | 1.4 | 16 | 172.6 |
| 04:11 | RETURN | N = 0 | 0 / 0 | 50.0 (105%) | 50.8 (103%) | 49.8 (99%) | 49.8 (103%) | 0 | 0 | — | — | — | 3,108 | — | 1.5 | 16 | 170.4 |
| 04:12 | RETURN | N = 0 | 0 / 0 | 50.0 (105%) | 50.5 (102%) | 50.5 (100%) | 50.8 (105%) | 0 | 0 | — | — | — | 3,121 | — | 1.3 | 16 | 169.9 |
| 04:13 | RETURN | N = 0 | 0 / 0 | 52.5 (110%) | 52.2 (106%) | 51.5 (102%) | 50.0 (103%) | 0 | 0 | — | — | — | 3,134 | — | 1.3 | 16 | 169.2 |
| 04:14 | RETURN | N = 0 | 0 / 0 | 47.8 (100%) | 47.8 (97%) | 48.8 (97%) | 47.2 (97%) | 0 | 0 | — | — | — | 3,062 | — | 1.3 | 16 | 169.8 |
| 04:15 | RETURN | N = 0 | 0 / 0 | 48.2 (101%) | 50.0 (101%) | 50.5 (100%) | 50.0 (103%) | 0 | 0 | — | — | — | 3,121 | — | 1.1 | 4 | 157.7 |
| 04:16 | RETURN | N = 0 | 0 / 0 | 43.8 (92%) | 44.5 (90%) | 46.0 (92%) | 45.2 (93%) | 0 | 0 | — | — | — | 3,087 | — | 1.5 | 17 | 169.3 |
| 04:17 | RETURN | N = 0 | 0 / 0 | 48.0 (101%) | 49.2 (100%) | 48.8 (97%) | 49.0 (101%) | 0 | 0 | — | — | — | 3,128 | — | 1.3 | 16 | 167.6 |

## What a next attempt could try (not opened)

- **Let the greedy climb reach the cap,** to see the cap guard and whether a reset starts a second climb (the toy says it does). That needs more greedy minutes and a larger lane budget (at 2,000 a lane transaction costs about 5.3 tKAS; two lanes near the cap about 3,000 tKAS a minute).
- **A greedy lane alone** against fixed tiers (lane 2 off or fixed at 150): is the climb the rival's doing, or does a 110 percent target climb on its own here?
- **A milder greed:** lane 1's target at 100–105 percent instead of 110, or a down step after a long good run, to find where the leapfrog stops.
- Refill key 0 on use again (about 1.09 usable tKAS per OK hop) and keep the budget check before genesis.
