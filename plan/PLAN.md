> **Experimental. We are just trying this.** [Disclaimer](../DISCLAIMER.md) · This page does not start a machine. Pre-run 18. Not Wednesday. Not Tuesday. Not pre-run 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, or 17.

# Targets

There is no T0. There is no public clock. There is no latest minute. Nothing in pre-run 18 is scored: every step is an observation of whole minutes.

The hash file comes first and does not wait for the open. Nothing else in this page starts until the gates are true: Mini's TN10 node is synced with DAA moving; the desk's private TN10 node is up from its own data (PowerShell 7, no wipe) and synced; no Tuesday, Wednesday, or pre-run 1 to 17 runner is up; the operator has armed (no paste; see the README); our heavy lane's calibration on the node passed; and this repo's `logs/PRE-RUN-OPEN.md` is on origin.

## Order

1. **Nodes live.** Both TN10 nodes synced, DAA moving. No wipe.
2. **Calibration.** One lane transaction, read back from the desk mempool: node storage mass within 1 percent of our SDK's, fee rate 99–101. Otherwise the lane does not run and that is recorded.
3. **Hashes first.** [hashes/SIXTEEN.md](../hashes/README.md): sixteen rows, family label, tier, sha256 of the lowercase hex covenant id, and an On origin line.
4. **Families.** The sixteen covenant families start on the desk's private node, 1.2 hop/s offered. No payment sender of ours is started.
5. **Our two heavy lanes** start at N = 0 and follow one timeline of whole minutes set by the runner:

| Order | File | Lane 1 | Lane 2 | Length |
|---:|---|---|---|---|
| 1 | BASE | 0 (control) | 0 (control) | 10 whole minutes |
| 2 | HOLD-1 (the reference) | 30 at 150 | 30 at 150 | 10 whole minutes |
| 3 | HOLD-2 (greedy duel, part 1) | 30, greedy: wants 110 percent of its reference, never steps down | 30, the normal rule | 12 whole minutes |
| 4 | HOLD-3 (greedy duel, part 2, no reset) | the same | the same | 12 whole minutes |
| 5 | HOLD-3 (symmetric repeat) | 30, from 150, the normal rule | 30, from 150, the normal rule | 8 whole minutes |
| 6 | drain, HOLD-4 | 0 | 0 | the pinned minute; the bot sends only on a free third public kaspad, or files `NO SEND` |
| 7 | RETURN (after-duel control) | 0 | 0 | 10 whole minutes |
| 8 | tail | families and lanes stopped, the counter reads on | | 5 minutes |

The lanes' N changes on the minute boundary, on a timeline fixed when the lanes start. The minutes between HOLD-3's end and the pinned minute are the start of the drain; they are in `counts/chain/TIMELINE.md`. **Why shorter steps than pre-run 17:** the run is sized on key 0's coins (about 760 usable tKAS a family minute): 10-minute BASE, reference and RETURN keep about 72 family minutes in all, and the greedy duel keeps its 24 minutes in one piece. The symmetric repeat is kept short; it is the part pre-run 17 already saw.

## Cohorts (families, node rates): the bystanders

| Cohort | Families | Rate, sompi/gram of node mass | Weight against the outside stream at 100, (rate/100)^3 |
|---|---|---:|---:|
| floor | 1–4 | 100, fixed | 1.00 |
| r150 | 5–8 | 150, fixed | 3.38 |
| r300 | 9–12 | 300, fixed | 27.0 |
| r450 | 13–16 | 450, fixed | 91.1 |

A hop is about 41,100–41,700 node mass (storage mass; compute 9,123), a lane transaction about 266,700. kit24 is pre-run 17's, unchanged; no family reads a live rate in this run.

## The duel rule

Once a minute, at 22 seconds past the minute or later (the counter's line for the minute just closed is final about 20 seconds after it ends), the desk runner reads that minute and moves both rates:

| Side | What it is | Metric | Reference |
|---|---|---|---|
| A | lane 1, 30 chains | lane 1 transactions landed in the minute | lane 1's median in HOLD-1 minutes 2–10 (both at 150) |
| B | lane 2, 30 chains | lane 2 transactions landed in the minute | lane 2's median in HOLD-1 minutes 2–10 |

- **greedy (lane 1, the 24 greedy minutes):** metric under 110 percent of the reference: rate × 1.25, rounded, at most 2,000; it never steps down;
- **normal (lane 2; both lanes in the symmetric repeat):** under 90 percent: × 1.25, at most 2,000; at or over 90 percent for 2 minutes in a row: × 0.8, rounded, at least 100; otherwise unchanged;
- an unread, partial or lagging minute holds both rates;
- **cap guard:** 4 decided minutes in a row with the greedy lane, or both lanes, at 2,000 → `CAP_REACHED` (minutes since the start or the last reset, fees so far), both back to 150, counters cleared;
- the greedy duel starts both at 150; its second part continues from where the first ended (no reset); the symmetric repeat starts both at 150 again with cleared counters; the minute that changes the rule holds.

Each rule only sees its own lane's landings. The new rates take effect about 22 seconds into the next minute. The per-minute snapshot of both rates and every decision are in `logs/duel.log`. Which lane submits first alternates every second.

## Prediction, written before the run

- **Pre-run 17 says** the symmetric rule between equals drifts down (both 150 → 100 in four minutes). **Our offline run of this controller** (`tools/sim/dueltest18.mjs`: the controller's own code against a toy world where the two lanes split 580–700 heavy places a minute by weight rate^3, each lane capped at 300–350 a minute, no bystanders) climbed in every case: lane 1 steps up because it is under 110 percent, takes places from lane 2, lane 2 falls under 90 percent and steps up too, and the pair leapfrogs **150 → 2,000 in about 13 minutes**, the cap guard fires at about 16 minutes, both go back to 150 and climb again; the symmetric repeat then comes down to 100/100 within about four minutes. Toy fees for the whole lane plan: about 29,000–35,000 tKAS.
- **What we expect in the real run:** a climb, slower than the toy's, because the real heavy places are not a fixed pie: the node merges more blocks some minutes, the bystanders and other traffic take places too, and in pre-run 17 at 100/100 the lanes landed 103–112 percent of their references. So lane 1 may reach 110 percent at a modest rate, lane 2 may stay over 90 percent, and the pair may settle with lane 1 at about 1.25–2 times lane 2. Our best guess: **lane 1 climbs to 300–1,000 in the 24 minutes; lane 2 follows part of the way; a cap in 24 minutes has perhaps a one-in-three chance.**
- **What would tell us it is not the rival:** if lane 1 stays under 110 percent while lane 2 is still at or over 90 percent and at the floor, 30 chains may not be able to land 110 percent at any rate on this node; we then call it a ceiling, not a spiral.
- **The symmetric repeat** should come back down to 100–150 within its 8 minutes, as in pre-run 17.
- **Bystanders.** The fixed tiers should lose more the higher the lanes go: floor and r150 badly once the lanes are above 150, r300 and r450 when the lanes pass 300 and 450. At 2,000 every fixed tier should slow, but a chained hop still lands.
- **Other users** at up to about the lanes' rate lose more the higher the lanes go; at 150 about 6–13 percent of other traffic landed on our node (pre-runs 15–17).
- **Cost.** At 150 a lane transaction costs about 0.40 tKAS, at 600 about 1.6, at 2,000 about 5.34; with both lanes at the cap about 3,200 tKAS a minute. The fee cap (32,000) can end the lanes early; that is an answer too ("gave up (budget)").

## Our heavy lanes

- **Shape.** One input (the chain's own coin, from the payment key), two plain pay-to-key outputs: 0.0375 tKAS to a dedicated sink key of ours, and the change back into the chain. Storage mass about 266,670 (KIP-9: 10^12 / 3,750,000 sompi for the small output, the change and input terms nearly cancel). Compute mass about 2,000. Fee rate × mass: about 0.40 tKAS at 150, 2.67 at 1,000 and 5.34 at the 2,000 cap.
- **Why this shape.** Our SDK counts every output at UTXO plurality 1 (pre-run 12's source check); plain outputs have plurality 1 on the node too, so the two agree. A covenant output (plurality 2) would be under-read by the SDK by a factor of four.
- **Two lanes, one process.** Lane 1 uses chain slots 1–100 and lane 2 slots 101–200 of one lane process, one node connection and one key-16 pile; each has its own N, rate and submit bucket (1,200 a minute, 20 a second), and lane 2's ids are logged apart so the counter reads lane 1 and lane 2 landed separately (hv1, hv2).
- **Ready count.** A chain's next transaction goes out only after the previous one has left the desk mempool. So each lane has at most N entries in the mempool and all are ready. About one 267,000-mass transaction fits a 500,000 block, so at about 10 blocks a second the chain takes at most about 600 heavy transactions a minute, shared with any outside heavy. At 30 + 30 the two lanes hold about 32 blocks of ready mass.
- **Money.** Only from the payment key (key 16: 5,438 coins, 113,552 tKAS, before this run's refill of key 0, which moved 3,500 of them, 74,071 tKAS; 1,938 coins, 39,482 tKAS, after). Each chain takes one pile coin and runs it down to under 2 tKAS, then takes the next. The family lane (key 0) is not touched by the heavy lane. The operator said tKAS is not a limit; the caps stay as guards, and the spend is logged.
- **Caps.** 1,200 lane submits a minute; pause above N + 2 lane entries for three probe samples; hold at mempool 90,000 or ready mass over 80 blocks; rate at most **2,000**; stop at **32,000** tKAS of fees or **34,500** tKAS moved, or the pile estimate under **3,500** tKAS (pre-run 17: 90,000 / 100,000 / 15,000); stop on any rejection that is not a timing one, or if the node's rate or mass on our own entries drifts from the calibration.
- **Not swept in this run.** The 0.0375 tKAS sink outputs (pre-runs 13 to 17's, about 107,000, and this run's) stay where they are, on the same sink key. A sweep is a separate, later, logged step.

## Why this shape

- Pre-run 17's symmetric duel drifted down, and its one-sided variant never ran (the run failed first). A greedy side that wants more than its share is the simplest case where a climb can start, so it goes first and gets 24 minutes in one piece.
- HOLD-1 gives each lane a reference at the duel's starting point (both at 150); BASE gives the bystanders' reference.
- The symmetric repeat after the climb asks whether the normal rule comes back down from wherever the greedy part left the rates; it restarts at 150, so it is a short repeat of pre-run 17's case under this run's conditions.
- The steps are shorter than pre-run 17's so that key 0 stays well over its line (checked before genesis), and the lanes' budget stays in the pile.
- No payments: the only load is the families, our lanes and whatever other TN10 traffic is there.

## What we read

For each minute: each lane's N and rate and every duel decision (`logs/duel.log`); lane 1 and lane 2 landed (counter) and their share; hops per tier and each tier's node rate (as built and as the probe read it in the mempool) (desk counter, accepted on chain); our heavy in the mempool and ready (probe), our heavy landed (counter), lane submits (the lane's log); outside heavy at 100 (probe, entries not in our logs); the ready mass in blocks of 500,000 (from the full mempool read up to 10,000 entries, from the node's own figures above); the mempool size and the fee estimate. Mini is a second read of the hops.

## Selection rule

The desk node and the public kaspads answered serverVersion 2.1.0. In rusty-kaspa tag v2.1.0 (commit 01b532e8b553523216471682649693af92f0fd16), `mining/src/mempool/model/frontier.rs` takes every ready transaction best-first while the ready set's mass fits one block, and otherwise samples at random with weight (fee/mass)^3 (`ALPHA = 3`). Only a transaction with no parent in the mempool is ready, so a chained hop is not a candidate until its parent is out of the mempool. A higher fee raises the odds of being drawn; it does not buy a place in a queue. This is the source's rule, read from the code; the run reads the desk node's own template, not a miner's.

Abort line **18,000 usable tKAS** (key 0 coins over 3 tKAS, less 3 tKAS each). The coin count is logged, not a gate (pre-run 13 tripped on change fragments). Key 0 was consolidated and refilled before the open (sized on use; the runner's `BUDGET_CHECK`). Do not lower it.
