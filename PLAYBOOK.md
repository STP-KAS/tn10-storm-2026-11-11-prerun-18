> **Experimental. We are just trying this.** [Disclaimer](DISCLAIMER.md) · Kaspa Testnet-10 only; tKAS has no value.
>
> **This is the playbook for pre-run 18.** It is not Wednesday. It is not Tuesday. It is not pre-run 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, or 17. It does not start a machine and it does not arm one.

# Playbook

Who does what, and the gates before each machine may start. The plan is [plan/PLAN.md](plan/PLAN.md), the locks are [locks/LOCKED.md](locks/LOCKED.md), and the go files are the three GO pages. This page does not override them.

## Oversight

TN10 ops oversees this rehearsal end to end: Mini, the desk (Build), and the bot. TN10 only. Never mainnet. Do not edit the Tuesday repo, the Wednesday repo, or pre-run 1's to 17's go files. Do not write `REVIEW_CLOSED`.

For pre-run 18 the operator does not paste. On 2026-11-12 he asked TN10 ops for covenant pre-runs under congestion and competition, pre-run 11 and then 12, 13 or more as needed (voice, 09:06 and 09:09 Brussels time), and at 10:04 in chat said "Keep exploring". That is the arm. The agents start their runners once the gates are facts.

## Start gates

1. **Mini node synced.** Existing TN10 kaspad, existing data, no wipe. `isSynced` true, DAA moving.
2. **Desk node synced.** Existing private TN10 kaspad, existing data, loopback only, started with `pwsh`. No wipe. Synced, DAA moving.
3. **No other runner.** No earlier runner, waiter, or counter on any machine. Lane above the abort line. The desk's private candidate list is present and not empty (`HELD candidates-missing` otherwise).
4. **Hashes.** `hashes/SIXTEEN.md` with sixteen rows and an On origin line, from [tools/sixteen](tools/sixteen/README.md).
5. **Open.** The desk pushes `logs/PRE-RUN-OPEN.md`. Mini then pushes `logs/MINI-ARMED.md`.
6. **Counter, families, senders.** The desk runner starts the counter on its private node and waits for its start line (`HELD counter-down` otherwise). Then the genesis from the bundle that wrote `hashes/SIXTEEN.md`, the families, and the payment steps.

## Who does what

| Who | Role | What not to do |
|---|---|---|
| **Desk (Build)** | Sends the sixteen families (four fixed tiers, one path, one build, kit24) and runs our own two heavy lanes in one lane process (the operator's OK, calibrated first). No payments. Its private TN10 node counts what the chain accepted (lock line (iv)) and its probe reads the mempool (xii). Publishes `hashes/SIXTEEN.md`, `logs/PRE-RUN-OPEN.md`, `counts/desk/` per step, `counts/chain/TIMELINE.md` and `MEMPOOL.md` after the tail, and `logs/METHOD.md`. | Do not stop or wipe the desk node. No Windows PowerShell 5.1, no `KaspaPublicNode`, no miner, no devnet. No 8- or 32-family publisher. No second runner. Never restart the runner mid-run. No payment sender. No heavy lane other than the runner's own lane process (which carries both lanes). |
| **Mini** | Second chain read on its own node. Does not send, mine, or hold a key. Publishes `logs/MINI-ARMED.md`, then `counts/mini/` when the matching desk file is on origin. | Do not wipe. Do not repeat the desk's head as Mini's. |
| **Bot (TN10 ops)** | Sends payments in the HOLD-4 minute only, on a synced public kaspad that is not one the desk kept, or publishes a legal `NO SEND`. | Do not send in any other step. One waiter. No local node. |

## Status when this repo was opened

Not a gate. Read on 2026-11-13 between 02:30Z and 02:40Z. This is our own TN10 testing; status lines are what we read on our own machines.

- Mini: existing TN10 kaspad 2.1.0 up, no wipe. Pre-run 17's Mini runner stopped on pre-run 17's FAILED.md at 02:13:04Z.
- Desk: existing private TN10 kaspad 2.1.0 up with `pwsh`, no wipe. It is not stopped for this pre-run. No pre-run 17 runner or child is running (it stopped itself at 02:12:41Z). `serve.mjs` and its keeper are not touched.
- Box: no local TN10 node. No bot waiter running.
- **Family lane** (key 0), read 02:30Z: 2,433 coins over 3 tKAS, **17,373 usable tKAS** (under the 18,000 abort line: pre-run 17's failure), 2,104 small coins (4,844 tKAS). **Consolidated** 02:35:44Z: 29 transactions, none rejected, the 2,104 small coins into 179, 2.43 tKAS in fees. **Refilled from the payment pile** 02:35:45Z (`refill18.mjs`): 175 transactions, none rejected, 3,500 pile coins (74,071 tKAS) to key 0 at the same sizes (20 in, 20 out each), 8.06 tKAS in fees.
- **Sized on use this time.** Pre-run 17's families used about 1.06 usable tKAS per OK hop, about 730 a minute. This run plans about 72 family minutes (BASE 10, the reference 10, the greedy duel 24, a symmetric repeat 8, the drain to the pinned minute, RETURN 10, and the start). New read-only check `budget18.mjs`, 02:36Z: key 0 **85,043 usable**, less 760 a minute × 72 = **30,323 projected at the end**, over the 18,000 line by more than the 8,000 margin we ask: ok. The runner repeats this check before genesis and holds the run if it fails.
- **Push-back on "aim for about 110,000 usable":** the greedy duel burns the payment pile (key 16, our lanes), not key 0 (the families are at fixed rates). Moving more to key 0 would have left the lanes about 14,000 tKAS. We kept the pile at **1,938 coins, 39,482 tKAS** for the lanes and capped their fees at 32,000.
- Keys 1–15 got a fresh genesis coin from the family lane (15 transactions at 02:36:19Z, none rejected). After: key 0 6,097 coins over 3 tKAS, 85,043 usable, no small coins. Amounts and ids are in private notes.
- **Hop calibration on the node** (kit24, unchanged from pre-run 17), 02:36:52Z: one calibration covenant on key 0 (launch path `…-p18-cal`, not one of the sixteen families and not in `SIXTEEN.md`), its genesis, then two hops built by the family path and submitted on the desk's private node, each read back from the desk mempool:

| Hop | Builder bill rate (on 13,046) | kit24 storage mass | Node storage mass | Node compute mass | Fee, sompi | Node rate (fee ÷ node mass) |
|---|---:|---:|---:|---:|---:|---:|
| family 1 at 100 | 320 | 41,664 | 41,664 | 9,123 | 4,174,720 | 100.20 |
| family 13 (r450) at 450 | 1,429 | 41,425 | 41,425 | 9,123 | 18,642,734 | 450.04 |

  Storage mass matched to the unit and both node rates were within 1 percent of the asked rate (and not under it).
- **Our heavy lanes' calibration** (one lane process carries both lanes): at 2,000, 02:36:58Z: SDK storage mass 266,769, node 266,769 (0.00 percent off), compute 2,036, node rate 2,000.00 (fee 5.34 tKAS). At 100: the first try at 02:37:00Z was refused as an orphan (it picked the coin the 2,000 calibration had just spent, before the node's index showed it); the retry at 02:37:28Z read 266,671 on both sides, node rate 100.00. The sink key is pre-runs 13–17's (its parked outputs are not swept).
- RE_READ_PLACEHOLDER
- Known risks, not fixed mid-run:
  - Our lanes slow other TN10 users' transactions at fees up to about their own rates while they run. If the greedy lane drives the rates up, more of them wait, and at high lane rates every fixed tier and other users' low-fee traffic may slow. The operator OK'd our lane; the rates are capped at 2,000, the lanes' fees at 32,000 tKAS, the cap guard puts both back to 150 after 4 minutes with the greedy lane at the cap, and both lanes step down to zero at the end.
  - If the lanes reach their fee cap or the pile floor (3,500 tKAS) they stop for the rest of the run; that is recorded as "gave up (budget)", and the families go on.
  - A greedy lane that wants 110 percent can climb for a reason that is not the rival: if 30 chains cannot land 110 percent of the reference at any rate. Lane 2's landings in the same minutes tell the two apart.
  - The outside heavy fee-100 stream may also be there.
  - The rule reacts to the minute just closed and takes effect about 22 seconds into the next one.
  - About one heavy transaction fits a block, so heavies together land at most near 600 a minute.
  - The probe reads the desk node's mempool and template, not a miner's. Above 10,000 mempool entries its per-class columns are blank by design.
  - Only two unique public kaspads answered in every check so far, and the desk keeps both, so the bot is expected to file `NO SEND no-free-node`.

## Offline rehearsal, recorded before `PRE-RUN-OPEN`

Rehearsal `p18-a` ran on the desk against the fake node (no network for the sends), 2026-11-13 02:42:33Z to 03:04:24Z, with 2-minute lane steps (`STORM_LANE_MIN=2`, `STORM_RET_MIN=2`) and the probe's full read capped at 5,000 entries, using this pre-run's runner, lane, counter, probe, kit24 and family-fee files (the same files, by hash, as the live run).

- Preflight passed; `BUDGET_CHECK` logged (key 0 85,031 usable, 22 planned family minutes in the rehearsal, projected end 68,311, over the line plus margin); genesis 16 of 16 live; `FEE_SPLIT` verified floor 100, r150 150, r300 300, r450 450; `LANE_PLAN` BASE N0, HOLD-1 the reference, HOLD-2 greedy-1, HOLD-3 greedy-2 and the symmetric repeat, then the drain.
- Both lanes submitted from one process with no rejections and no losses (10,602 OK in all); the counter split our landings into lane 1 and lane 2 (hv1, hv2).
- The duel controller did what the plan says: the reference from HOLD-1; in the greedy part lane 1 stepped up every minute (150 → 188 → 235 → 294; the fake node lands both lanes the same, about 103 percent of the reference, under lane 1's 110 percent) while lane 2 stepped down (150 → 120); **the second greedy part continued from 188 without a reset**; the symmetric repeat started both at 150 and the minute that changed the rule held. No `ERROR` line; no cap in 2-minute steps.
- Every step file, TIMELINE, MEMPOOL and METHOD published to the rehearsal's local origin; `RUNNER_EXIT 0`.
- The cap guard for the greedy lane alone and the budget hold were not reached in the rehearsal; the cap guard ran in the offline controller test (`tools/sim/dueltest18.mjs`: `CAP_REACHED side=a`, then both back to 150).

## Status after the live run

Read on 2026-11-13 between 04:18Z and 04:30Z. Not a gate.

- **The run finished through RETURN.** The desk runner (started 03:07:40Z) ran BASE, HOLD-1 (both lanes' reference), HOLD-2 and HOLD-3 (the greedy duel, 24 minutes, then the 8-minute symmetric repeat), the drain, HOLD-4 and RETURN; every whole minute kept pace and was clean; no repair, no restart. `RUN_STOP return-closed` 04:18:24Z; TIMELINE, MEMPOOL and METHOD on origin 04:23:35–41Z; `RUN end` 04:23:43Z. No runner process was left on the desk. The private TN10 kaspad (2.1.0) was not stopped. No devnet, `KaspaPublicNode` or miner was started; `serve.mjs` and its keeper were not touched.
- **The greedy duel climbed.** Lane 1 (greedy) 150 → 1,405 in about 21 minutes (10 steps up), lane 2 (normal rule) following each time it fell behind (14 up, 4 down) to 1,124, and 1,405 at the last decision; no cap. The two lanes together landed about the same every minute (median 548 at the reference, 560–562 in the climb), so the climb moved places between them rather than adding any. The symmetric repeat came back to 100 / 100 in about four minutes. Fixed tiers (percent of BASE, floor / r150 / r300 / r450): reference 43 / 68 / 96 / 104, second greedy part median 1 / 4 / 22 / 40, at 100 / 100 65 / 86 / 98 / 106, RETURN 101 / 99 / 99 / 102. The duel log is [logs/duel.log](logs/duel.log).
- Our heavy lanes: `LANE_END` 04:18:25Z, 23,211 accepted (lane 1 12,346, lane 2 10,865), 0 rejected, 0 lost, 22,558.34 tKAS fees, 870.41 tKAS parked on our sink key (not swept), 1,169 pile coins taken, 0 pending.
- Inclusion (counter totals): every OK hop (floor 7,413, r150 8,954, r300 11,338, r450 12,340) and every lane transaction (23,211) landed.
- The outside heavy fee-100 stream of pre-runs 14–16 was absent (1 entry in four minutes, 0 otherwise). The probe's mempool read worked every sample (the mempool peaked at 6,374 entries).
- Mini: the runner (MINI-ARMED 03:07:15Z) published every step, each read in full, and matched the desk in 251 of 252 cohort cells (r150 in the 03:54 minute: 130 against 131); 67 removals after a minute had closed over the run. Its TN10 kaspad was not wiped or restarted.
- Bot: `NO SEND no-free-node` for the pinned minute 04:06Z (on origin 04:07:04Z, first try); nothing sent. Its box stalled once (heartbeat gap 03:50:13Z–03:53:04Z; one git fetch took 161.8 s and failed), and its waiter recovered on the next loop.
- Keys after the run (read-only status): key 0 4,646 coins over 3 tKAS, 41,339 usable (abort line 18,000), 1,451 small coins; keys 1–15 have no genesis coin; payment pile 796 coins.
- Results: [logs/LESSONS.md](logs/LESSONS.md), [logs/duel.log](logs/duel.log), and the pre-run 18 block in [locks/LOCKED.md](locks/LOCKED.md).

### Public statement

We run our own two heavy lanes on TN10 in this pre-run, with the operator's OK, 30 chains each: 10 minutes both at 150, then 32 minutes at rates our duel rule sets between 100 and 2,000 sompi/gram, one of them greedy on purpose. While they run, other TN10 users' transactions paying up to about the lanes' rates wait longer on the nodes that see them, and more of them wait as the lanes climb. In this run the lanes ran 42 minutes: 10 at 150, 24 in the greedy duel (they climbed from 150 to 1,405), 8 in a symmetric repeat (back to 100). On our desk node other traffic landed a median of 2,992 a minute with the lanes at 150, 2,904 in the first 12 greedy minutes and 2,404 in the last 12 (single minutes from 425 to 7,764), against 3,132 with the lanes at 0 (BASE): about 5, 7 and 23 percent lower. In the last 12 greedy minutes the desk mempool grew to 6,374 entries and the node's priority fee estimate rose to 2,197 (median 1,370) instead of 144; part of the delayed traffic landed when the backlog cleared. Our own hops at 100, a stand-in for a low-fee user, ran at 43 percent of their BASE pace with the lanes at 150 and at 0–1 percent with the lanes at 1,124–1,405. No outside heavy stream was present. The lanes went to 0 at 04:01:59Z. This is our own testing; tKAS has no value.

## When something breaks

Append a worked fix to [locks/LOCKED.md](locks/LOCKED.md) in the form that page shows, and a repair line to `logs/FIXES.md`. If the run dies before RETURN, write `logs/FAILED.md`, stop every runner, waiter, and counter, and do not resume. The next attempt is a new repo that starts from this repo's lock file.
