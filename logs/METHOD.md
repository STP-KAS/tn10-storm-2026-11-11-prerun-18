# Method, pre-run 18

> This is our own Kaspa Testnet-10 testing. What follows is what we observed in this run, on our own nodes; it is not a claim of how TN10 or Kaspa behave in general.

> Counts only. Desk side. Submit-OK is the desk sender log; included is the desk counter's read of what the desk's private TN10 node accepted on chain. Mini's files are a second read.

Steps (our own heavy lane on one absolute timeline): BASE = N0-control 10 min; HOLD-1 = L30x2-r150-ref 10 min; HOLD-2 = L30x2-greedy-1 12 min; HOLD-3 = L30x2-greedy-2 12 min, L30x2-sym 8 min; then N0-drain through the HOLD-4 minute and RETURN 10 min, then a 5-minute counter tail.

Our heavy lane, from its own log: 23,211 transactions submitted OK of 23,211, 0 rejected, 0 chains lost to an orphan timeout, 22,558 tKAS of fees and 870 tKAS parked on our own sink key, 1169 payment-pile coins taken, stop state none.

Accepted hops per cohort, as the desk's coordinator read them: floor 7,409, r150 8,949, r300 11,334, r450 12,336.

Per step (all OBSERVATION, families plus our own heavy lane, no payment of ours):

- BASE: OBSERVATION, submit-OK 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0; our payments included 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0; hops included floor/r150/r300/r450 1912/1953/1984/1960; counter minutes not kept-pace 0 of 10.
- HOLD-1: OBSERVATION, submit-OK 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0; our payments included 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0; hops included floor/r150/r300/r450 803/1337/1920/2037; counter minutes not kept-pace 0 of 10.
- HOLD-2: OBSERVATION, submit-OK 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0; our payments included 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0; hops included floor/r150/r300/r450 395/853/1861/2256; counter minutes not kept-pace 0 of 12.
- HOLD-3: OBSERVATION, submit-OK 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0; our payments included 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0; hops included floor/r150/r300/r450 912/1367/2084/2620; counter minutes not kept-pace 0 of 20.
- HOLD-4: OBSERVATION, submit-OK 0; our payments included 0; hops included floor/r150/r300/r450 189/190/186/188; counter minutes not kept-pace 0 of 1.
- RETURN: OBSERVATION, submit-OK 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0; our payments included 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0 / 0; hops included floor/r150/r300/r450 1937/1961/1973/1948; counter minutes not kept-pace 0 of 10.

Decent on the desk side: every step file reached origin.

## Selection rule, read before the run

The desk node and the kept public kaspads answered serverVersion 2.1.0 at the preflight. In rusty-kaspa tag v2.1.0 (commit 01b532e8b553523216471682649693af92f0fd16), `mining/src/mempool/model/frontier.rs` `build_selector` takes every ready transaction best-first while the ready set's mass fits one block, and otherwise samples at random with weight (fee/mass)^3 (`ALPHA = 3` in `mining/src/mempool/model/frontier/selectors.rs`, weight in `mining/src/mempool/model/frontier/feerate_key.rs`): `sample_inplace` above four blocks' mass, `MutatingTreeSelector` between one and four. Only a transaction with no parent in the mempool is in the ready set (`mining/src/mempool/model/transactions_pool.rs`), so a chained hop is not a candidate until its parent is out of the mempool. Against an outside stream at 100, the weights are 1.00 (100), 3.38 (150), 27.0 (300) and 91.1 (450), per unit of mass. In the duel our two lanes move between 100 and 2,000 (logs/duel.log, published after the run). A higher fee raises the odds; it does not buy a place in a queue. This is the source's rule, read from the code; the run does not see a miner's template.

Hop rates per hop, one builder: floor (families 1–4) 100 sompi/gram on the desk's private node, r150 (families 5–8) 150 sompi/gram on the desk's private node, r300 (families 9–12) 300 sompi/gram on the desk's private node, r450 (families 13–16) 450 sompi/gram on the desk's private node. Payments 150. The funding coins were not one size, so the fee is not called the whole cause. Every tier was read and submitted on the desk's private TN10 node, which also ran the counter. No payment sender was started; 2 unique public kaspads were read for sync only.

## Misses

- none

## Fixes

- none

## On origin

- counts/desk/BASE.md: 2026-11-13T03:20:22Z
- counts/desk/HOLD-1.md: 2026-11-13T03:30:22Z
- counts/desk/HOLD-2.md: 2026-11-13T03:42:22Z
- counts/desk/HOLD-3.md: 2026-11-13T04:02:22Z
- counts/desk/HOLD-4.md: 2026-11-13T04:07:23Z
- counts/desk/RETURN.md: 2026-11-13T04:18:22Z
- counts/chain/TIMELINE.md: 2026-11-13T04:23:35Z
- counts/chain/MEMPOOL.md: 2026-11-13T04:23:39Z
