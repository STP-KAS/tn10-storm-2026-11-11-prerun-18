> **Experimental. We are just trying this.** [Disclaimer](DISCLAIMER.md) · Kaspa Testnet-10 only; tKAS has no value.
>
> **This is a pre-run. Pre-run 18.** It is not the Wednesday run. It is not the Tuesday run. It is not pre-run 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, or 17. A read does not start a runner.

# tn10-storm-2026-11-11-prerun-18

**Pre-run 18 of the Wednesday neuron.** The neuron stays [tn10-storm-2026-11-11](https://github.com/STP-KAS/tn10-storm-2026-11-11). This repo does not edit that repo, does not write `REVIEW_CLOSED`, and does not set or move a clock for it. [tn10-storm-2026-11-10](https://github.com/STP-KAS/tn10-storm-2026-11-10) (Tuesday) is not edited from here either.

> **Our own testing.** This is our own Kaspa Testnet-10 testing, run on our own machines and nodes. What these pages report is what we observed in this run; it is not a claim of how TN10 or Kaspa behave in general.

**Where this starts.** Pre-runs 1 to 4 failed and are closed. Pre-runs 5 to 12 finished through RETURN and are closed. Pre-run 13 ran through the pinned HOLD-4 minute and failed in RETURN on its coin-count abort line; it is closed. Pre-runs 14, 15 and 16 finished through RETURN and are closed. Pre-run 17 failed before RETURN on its own abort line and is closed. The index of all of them is the [pre-run 2 README](https://github.com/STP-KAS/tn10-storm-2026-11-11-prerun-2#pre-runs-in-this-rehearsal); the cumulative findings are in [tn-master](https://github.com/STP-KAS/tn-master). This repo starts from [pre-run 17's locks/LOCKED.md](https://github.com/STP-KAS/tn10-storm-2026-11-11-prerun-17/blob/2313231/locks/LOCKED.md) at commit 2313231, copied here as [locks/LOCKED.md](locks/LOCKED.md), with a pre-run 18 section added at the end.

## What pre-run 17 left open

[Pre-run 17](https://github.com/STP-KAS/tn10-storm-2026-11-11-prerun-17) put two equal heavy lanes of ours against each other on one symmetric rule. As we observed it, they did not bid each other up: both stepped down from 150 to 100 within four minutes and stayed there, splitting the heavy places about evenly. The run then failed before RETURN on our own abort line (we refilled the family key too little; our setup error), so its one-sided variant, **a greedy lane against a normal one**, never ran. That is the untested piece, and this run puts it first.

## What pre-run 18 tries: the greedy duel

The question: **when one heavy lane is greedy (it wants more than its reference share and never steps down) and an equal lane follows the normal rule, does the pair climb, spiral to the cap, or settle? How fast, at what cost per landed transaction, and what does it do to fixed-rate bystanders and to other TN10 users?**

> **We run our own heavy lanes on TN10 again, and they slow other TN10 users' transactions.** In this pre-run we submit two bounded streams of our own heavy transactions (about 266,700 storage mass each, 30 chains per lane, 60 in all, at rates our duel rule sets between 100 and 2,000 sompi/gram) from our own test coins. One lane is set to be greedy on purpose, so we expect the rates to climb, and while they run other TN10 users' transactions paying up to about the lanes' rates wait longer; the higher the lanes go, the more of them wait. The operator gave the explicit OK for our lane (2026-11-12), said tKAS is not a limit and asked us to test at will. The lanes are calibrated on the node first (at 100 and at 2,000), capped by ready count, by a per-minute submit cap, by a rate cap, by a cap guard and by a spend cap, stepped down to zero at the end, and every step is in this repo. This is our own testing; tKAS has no value.

- **Both sides are ours and the same shape.** Lane 1 and lane 2 are two sets of 30 chains in one lane process on the desk (pre-run 17's), each transaction about 266,700 storage mass, from the same key-16 pile. About one such transaction fits a 500,000 block, so the two lanes (and any outside heavy) share about 600 heavy places a minute.
- **The greedy rule (lane 1), once a minute:** if lane 1 landed under **110 percent** of its own reference, its rate goes up × 1.25 (cap **2,000**); it never steps down. **The normal rule (lane 2):** under **90 percent** of its own reference × 1.25 (cap 2,000); at or over 90 percent for **2 minutes in a row** × 0.8 (floor **100**). Both start at 150. Each reference is the lane's own median in HOLD-1 (minutes 2–10, both at 150). Each lane sees only its own landings. A minute that is unread, partial or lagging holds both. Every decision is logged (`logs/duel.log`, published after the run).
- **24 greedy minutes in one piece** (HOLD-2 and the first 12 minutes of HOLD-3, no reset between them), then **a short symmetric repeat** (8 minutes, both back to 150, the normal rule for both): does the symmetric rule come back down after a climb, as it did from 150 in pre-run 17?
- **Cap guard.** If the greedy lane alone, or both lanes, sit at 2,000 for 4 decided minutes in a row, the runner records it (`CAP_REACHED`: minutes since the start, fees so far) and puts both back to 150, so a climb can show again and the spend stays bounded.
- **Bystanders.** The sixteen covenant families run at four fixed rates, node rates: floor (1–4) **100**, r150 (5–8) **150**, r300 (9–12) **300**, r450 (13–16) **450**. None of them moves.
- **Sized on use, and checked.** Pre-run 17 failed because key 0 (the families' coins) ran under its 18,000 line. This time key 0 was refilled to about 85,000 usable tKAS, and the runner checks before genesis that the usable tKAS projected at the end of the run (760 a planned family minute) stays at least 8,000 over the line; otherwise it holds the run. See [PLAYBOOK.md](PLAYBOOK.md#status-when-this-repo-was-opened).
- **Calibrated on the node before the open.** One hop at 100 and one at 450, and one lane transaction at 2,000 and one at 100, read back from the desk mempool.
- **Steps on one timeline:** BASE (both lanes N = 0, 10 minutes), HOLD-1 (lane 1 and lane 2 each N = 30 at 150, no escalation: the reference, 10 minutes), HOLD-2 and the first 12 minutes of HOLD-3 (the greedy duel: both lanes N = 30, 24 minutes in one piece; lane 1 steps up whenever it landed under 110 percent of its reference and never steps down, lane 2 keeps the normal rule), the last 8 minutes of HOLD-3 (a short symmetric repeat: both back to 150, the normal rule for both), then both lanes N = 0 (the drain and the after-duel control) through the pinned HOLD-4 minute and RETURN (10 minutes), then the counter's 5-minute tail. All are `OBSERVATION`. The HOLD file names are kept so the bot's and Mini's gates read as before.
- **Guards.** The lanes keep pre-run 17's guards (pause at N + 2 entries, hold at mempool 90,000 or ready mass over 80 blocks, stop on a non-timing rejection or a drift from the calibration, 1,200 submits a minute per lane) with the fee cap at **32,000 tKAS**, the moved cap at 34,500 and the pile floor at 3,500 (pre-run 17: 90,000 / 100,000 / 15,000). If the lanes meet a cap they stop for the rest of the run, and that is recorded as "gave up (budget)". The family lane's abort line stays **18,000 usable tKAS**.
- **What this can and cannot say.** Both lanes are ours, on one node, with fixed references and a greedy rule we chose; the outside heavy fee-100 stream may be there too. A greedy lane can also climb because 30 chains cannot land 110 percent of the reference at any rate; lane 2's landings in the same minutes tell that apart from a climb against the rival. It cannot say how other people's wallets, other rules or other nodes would behave.

The prediction, written before the run, is in [plan/PLAN.md](plan/PLAN.md#prediction-written-before-the-run).

All locked lines from earlier pre-runs stay, except where the pre-run 18 block in [locks/LOCKED.md](locks/LOCKED.md) says what changes and why.

## Machines

| Machine | Go file | First sentence |
|---|---|---|
| Desk | [GO-DESK.md](GO-DESK.md) | DESK. I send and count on pre-run 18. This is not Wednesday. |
| Mini | [GO-MINI.md](GO-MINI.md) | MINI. I count pre-run 18 as the second read. I do not send. This is not Wednesday. |
| Bot | [GO-BOT.md](GO-BOT.md) | GROKBOT. I send payments on the pre-run 18 HOLD-4 only. I do not count. This is not Wednesday. |

The operator does not paste. On 2026-11-12 he asked TN10 ops for covenant pre-runs under congestion and competition, pre-run 11 and then 12, 13 or more as needed (voice, 09:06 and 09:09 Brussels time), and at 10:04 in chat said "Keep exploring". For our own heavy lane he gave the explicit OK in chat at about 11:08 and 11:10 Brussels time ("Do whatever you think is needed", then "No need to keep it short. Tn is for testing. Test at will"), and at 15:19 he said tKAS is not a limit ("Use all the tkas you want"). At 23:26 Brussels time he asked "Can we solve the fee escalation open question?", and at 23:28 said "launch run until you’re happy … Use all the tkas you want", and at about 23:30 "Yes keep going. At will." His word at 23:28 ("launch run until you’re happy … Use all the tkas you want") still stands after pre-run 17 failed. That is the arm for pre-run 18, its two heavy lanes and the greedy duel. The agents start the runners once the gates are facts. [GO.md](GO.md) is the map, [PLAYBOOK.md](PLAYBOOK.md) has the roles and gates, and [plan/PLAN.md](plan/PLAN.md) has the targets and the reasons.

## Gates, in order

No clock. Each gate is a fact read from a node or from origin.

1. Mini's TN10 node is up from its own data, synced, DAA moving.
2. The desk's private TN10 node is up from its own data (PowerShell 7), synced, DAA moving.
3. No other runner or waiter is up. The family lane is above its abort line (18,000 usable tKAS). The desk's private candidate list is present.
4. `hashes/SIXTEEN.md` is on origin: sixteen rows and an On origin line, from the sixteen-family path.
5. The desk pushes `logs/PRE-RUN-OPEN.md`; Mini pushes `logs/MINI-ARMED.md`.
6. The probe and the desk counter are up. Then the families, our heavy lane at N = 0, and the observation steps on the lane's timeline.

Before the open: the hop calibration (node rate within 1 percent of 100 and of 450) and the lane's calibration (at 2,000 and at 100) passed.

## What a decent result is

- `hashes/SIXTEEN.md` on origin before the first family submit.
- Every step file on origin, each with hops per minute for the four tiers (floor, r150, r300, r450), each tier's node rate, each lane's N and rate, our heavy (lane 1 and lane 2 apart) and the outside heavy apart, and the probe's table for the same minutes.
- `counts/chain/TIMELINE.md` and `counts/chain/MEMPOOL.md` after the tail, and RETURN on origin.
- The greedy duel's rate path for both lanes, minute by minute, and an answer to the question (climbed, spiralled to the cap, settled, or gave up on budget), with the time to the cap and the cost if it got there, whether lane 2's landings show a rival or a ceiling, the symmetric repeat's path, or an honest "not answered" with the reason.
- A HOLD-4 desk file, a bot file or a legal `NO SEND`, and a Mini file.
- The spend and the leftovers (the parked sink outputs, not swept) stated in the write-up.
- No id, txid, key, address, host, or port in this repo.

A miss stays in this repo. A next attempt is a new repo and starts from this repo's lock file.

**Part of [tn-master](https://github.com/STP-KAS/tn-master).** The rule is [docs/NEURON.md](https://github.com/STP-KAS/tn-master/blob/main/docs/NEURON.md). This pre-run is its own row. It is not row 47.
