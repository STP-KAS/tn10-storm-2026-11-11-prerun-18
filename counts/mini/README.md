> **Experimental. We are just trying this.** [Disclaimer](../../DISCLAIMER.md) · Counts only. No key, seed, txid, covenant id, address, host, or port.
>
> Mini's second chain read for pre-run 18. The desk does not write this folder.

# Mini counts

Mini publishes a scored file when the desk's matching file is on origin. HOLD-4 waits for the bot file, the halt file, or 10 minutes, as [GO-MINI.md](../../GO-MINI.md) says. Mini counts only on its own synced TN10 node.

| File | Target |
|---|---|
| BASE.md | no payments, families plus our heavy lane at N = 0 (control), 12 whole minutes, an observation. The first line is `OBSERVATION` |
| HOLD-1.md | our two heavy lanes, each N = 30 at 150: the reference (10 whole minutes; pre-run 18 has no payment offer) |
| HOLD-2.md | the greedy duel, part 1: both lanes N = 30, lane 1 greedy, lane 2 the normal rule (12 whole minutes) |
| HOLD-3.md | the greedy duel, part 2 (12 whole minutes), then a symmetric repeat (8 whole minutes) |
| HOLD-4.md | the observation minute |
| RETURN.md | lane N = 0 (drain), 12 whole minutes |

In pre-run 18 the desk counter is the first chain count and Mini is the second read. Each file's first line is Mini's own read: `READ`, `PARTIAL`, or `NOT READ`. The chat does not publish this folder.
