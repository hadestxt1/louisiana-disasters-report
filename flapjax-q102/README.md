# FlapJax Q102 audit — FLAPJAX transfers out of the treasury, 2026-11-18 COT

- Task: TaskMarket FlapJax Series 3, task Q102 (TaskMarket task ID not recorded in this audit — see the task page; Q103 was `0x6ebb27085d014b4e4b8cc915c38760ba2578c8208cc75e6466adfd62129bf48f`, Q104 was `0x3530b68f364cf93cb8a53a7b5a0e6109f1a4a6634786ae3ef262bb2d7a527013`)
- Treasury: `0x7C34E9e21eE28A49Ff0b84B61774119E6633359f`
- FLAPJAX token (BSC, 18 decimals): `0x90c8889f428F9Ebb77BB8f15CAD3a50a9aC680df`
- Day audited: **2026-11-18 COT (UTC-5)** = 2026-11-18 00:00:00 to 23:59:59 COT
  = 2026-11-18 05:00:00 UTC to 2026-11-19 05:00:00 UTC
  (unix 1794978000 to 1795064399 inclusive)
- Audit date: 2026-11-24. Read-only research only. No submission made, no wallet created, no contact with FlapJax / TaskMarket.
- Method reused from the Q104 audit (`flapjax-q104-audit.md`, 2026-11-20) and the Q103 audit (`flapjax-q103-audit.md`, 2026-11-19), including the Blast archive-RPC funder hunt (`flapjax-q104-funders.md`).

## Method (public on-chain data only)

- Block range for the day was fixed by binary search on block timestamps via public BSC RPC:
  - First block of the day: **134251698** — timestamp 1794978000 = 2026-11-18 00:00:00 COT exactly.
    Previous block 134251697 is 1794977999 (23:59:59 COT on 17 Nov).
  - Last block of the day: **134443554** — timestamp 1795064399 = 2026-11-18 23:59:59 COT.
    Next block 134443555 is 1795064400 = 2026-11-19 00:00:00 COT (this is also the first block of the Q103 day, as established in the Q103 audit — cross-check confirmed on two RPCs).
  - Note on the day's block rate: the day spans 191,857 blocks in 86,400 seconds (~0.45 s/block in this range, consistent with the Q103/Q104 day ranges measured the same way).
- Transfer list: `eth_getLogs` on public RPC `https://rpc-bsc.48.club`, filtered to
  Transfer events (`0xddf252ad…`) from the treasury (`topic1` = treasury) on the FLAPJAX
  contract, over blocks 134251698–134443554 inclusive, in 192 chunks of 1,000 blocks.
  The first pass had 13 failed chunks (transient RPC errors, all in the range
  134251698–134415697); that range was re-scanned in full with per-chunk retries and
  **0 failed chunks**, and the union of both passes was deduplicated by tx hash.
  **Full coverage of the range, 0 failed chunks remaining. 14 logs found, all unique.**
  Every log was re-checked to be inside the day's block range, from the treasury, on the FLAPJAX contract.
- Verification: `eth_getTransactionReceipt` + `eth_getTransactionByHash` checked for
  3 transfers (first, middle, last — see below). All three: status `0x1`, `from` = treasury,
  `to` = FLAPJAX token contract, input starts `0xa9059cbb` (`transfer(address,uint256)`),
  exactly 1 Transfer log each, amount matches the log. (One transient null-receipt
  response from rpc-bsc.48.club was re-fetched on the Blast archive RPC and verified.)
- Amounts are exact integers (raw value / 10^18, integer division — no float rounding).
- Recipient balances / nonces were checked at latest block on **two** independent RPCs
  (Binance dataseed and rpc-bsc.48.club) and agreed; a few transient empty responses
  were re-fetched (incl. nonce on the Blast archive RPC) until both RPCs agreed.
  FLAPJAX holdings now were read with `balanceOf` (`eth_call`) on rpc-bsc.48.club at
  latest block, 2026-11-24 (latest block seen: 135404115).
- Funder hunt: for every recipient with BNB balance > 0 or nonce > 0 at latest block,
  binary search on archive RPC `https://bsc-mainnet.public.blastapi.io` for the first block
  with balance > 0, then `eth_getBlockByNumber(full=true)` on the Binance dataseed to find the
  single tx to the recipient in that block whose value equals the balance increase, then
  `eth_getTransactionReceipt` to verify status 1. Nonce at each first-nonzero block was 0,
  so no earlier fully-spent inflow could have been missed. All RPC calls were made with
  `curl` (Python `urllib` kept dropping connections in the Q103 run).
- BscScan web pages were NOT used for cross-checking (the BscScan token page returned HTTP 403
  in the Q104 audit and was not retried). Per-transfer links below are links only.

## Summary

| Item | Value |
|---|---|
| Transfers out of treasury on 2026-11-18 COT | **14** |
| Total FLAPJAX sent | **1,005,000** |
| Distinct recipients | **10** |
| Distinct operators implied by funder groups | **10** |
| Transfers that could not be explained | **0** (all 14 are plain successful `transfer()` calls from the treasury) |
| First block of the day | **134251698** |
| Last block of the day | **134443554** |

Recipient totals (Nov 18 only):

| Recipient | Transfers | FLAPJAX on 2026-11-18 | FLAPJAX held now (24 Nov) |
|---|---|---|---|
| 0x335aa55c12b260e604d93cb0b0895bb13a4e93e3 | 1 | 300,000 | 6,925,000 |
| 0x575a6975ff11d5a72896ff1e3c9f1b2bcf5731cd | 2 | 150,000 | 150,000 |
| 0x7d1db846f808eefe9ec5e1931174e74e9cf21ef2 | 2 | 150,000 | 150,000 |
| 0xde58c1a7c40a1a83e62a0ea056408b04252f8930 | 2 | 150,000 | 150,000 |
| 0xd8ef7b0ead57345265f376940b0644e75c9b482e | 2 | 150,000 | 150,000 |
| 0xa15c58e7008fc7a0331cfcc86a28af99fd21b93c | 1 | 25,000 | 175,000 |
| 0xee0821be193086fe6648b8051e39510ac95b358f | 1 | 25,000 | 215,000 |
| 0xfb200657f7266157a45dfcc6c09690726daa24e6 | 1 | 25,000 | 6,665,000 |
| 0xa8fe84bdcae37e978511012dfec736b07b00fc55 | 1 | 15,000 | 115,000 |
| 0x42c812fc1d6fb10600e99a1518df970f5be67ad6 | 1 | 15,000 | 115,000 |
| **Total** | **14** | **1,005,000** | — |

## All transfers (full table in `flapjax-q102-transfers.csv`)

| # | Time (COT) | Block | Tx hash | Recipient | Amount |
|---|---|---|---|---|---|
| 1 | 2026-11-18 09:28:51 | 134327449 | 0x2526b8ffd88d3f1159bb2648700a9e3f06d6e51af44277bd87b00f23febbe085 | 0x575a6975ff11d5a72896ff1e3c9f1b2bcf5731cd | 100,000 |
| 2 | 2026-11-18 09:29:14 | 134327500 | 0x5c6b9649b930d6e9109c1fe16b4a7b7e28aab989035af08ee916d859760b6e1f | 0x7d1db846f808eefe9ec5e1931174e74e9cf21ef2 | 100,000 |
| 3 | 2026-11-18 09:30:40 | 134327691 | 0x470b6ffff50a997013d4f0a39fe8da1f2e684df0974138313cb76079969266fa | 0x575a6975ff11d5a72896ff1e3c9f1b2bcf5731cd | 50,000 |
| 4 | 2026-11-18 09:31:05 | 134327747 | 0x9af4a1e2cb8ac4a58c9b8f4b0b3d1aad77fd9fc90e25533dfe26c8f02c8a9faa | 0x7d1db846f808eefe9ec5e1931174e74e9cf21ef2 | 50,000 |
| 5 | 2026-11-18 09:32:25 | 134327925 | 0xc976a342f542b121ae7620684294c6bf34b3fb2f5b7a2c4917eda3e8c4235623 | 0xa8fe84bdcae37e978511012dfec736b07b00fc55 | 15,000 |
| 6 | 2026-11-18 09:32:48 | 134327976 | 0xd8288c185bd2fc059cdd4f49d3e90465050a02ae81ec41e41a56ce5e8a9b0f74 | 0x42c812fc1d6fb10600e99a1518df970f5be67ad6 | 15,000 |
| 7 | 2026-11-18 09:33:13 | 134328032 | 0x79ce6690816844bcde7753f66b6e53fdab5beb8334eac9a5dab61c6c8c964f05 | 0x335aa55c12b260e604d93cb0b0895bb13a4e93e3 | 300,000 |
| 8 | 2026-11-18 13:23:30 | 134358724 | 0x32012168666656d925c3d0df3fd8cbb1921fcadd90e4050e2eeb5d1da875f667 | 0xa15c58e7008fc7a0331cfcc86a28af99fd21b93c | 25,000 |
| 9 | 2026-11-18 13:23:51 | 134358772 | 0x4dede2a5861a7aaa523e5c8e802bb392f522a8b556522bd430ff28a3de7df37b | 0xee0821be193086fe6648b8051e39510ac95b358f | 25,000 |
| 10 | 2026-11-18 18:14:02 | 134397455 | 0x6c87337ad73a15c5a3267b91fee0071d7b09ec85bf5bc33e800253f5e3578c45 | 0xde58c1a7c40a1a83e62a0ea056408b04252f8930 | 100,000 |
| 11 | 2026-11-18 18:15:06 | 134397599 | 0x5c6ae24fa24c1f08a78f0d4ce1c25f60a3203453afffb944b61845871d8d3569 | 0xde58c1a7c40a1a83e62a0ea056408b04252f8930 | 50,000 |
| 12 | 2026-11-18 18:15:49 | 134397694 | 0xa0c909e3e5e1fdd76b720211c2181756a06fc10d081bf62c52e9c29ec461e55d | 0xfb200657f7266157a45dfcc6c09690726daa24e6 | 25,000 |
| 13 | 2026-11-18 22:11:59 | 134429167 | 0x0f893bf45f1f446678164c7748009669922d3298eccc7212e1dcd256df6d38f2 | 0xd8ef7b0ead57345265f376940b0644e75c9b482e | 100,000 |
| 14 | 2026-11-18 22:12:52 | 134429285 | 0x8bc1664f3d6f7e336e41a55d607f91376ed162f460789e3e209b7080bafade01 | 0xd8ef7b0ead57345265f376940b0644e75c9b482e | 50,000 |

Sum check: 100,000 + 100,000 + 50,000 + 50,000 + 15,000 + 15,000 + 300,000 + 25,000 + 25,000 + 100,000 + 50,000 + 25,000 + 100,000 + 50,000
= **1,005,000 FLAPJAX**. All 14 transfers fall inside the day's block range; no transfer
was found in the first or last blocks of the day (earliest is block 134327449, latest 134429285).

Receipts verified in full (status, from, to, input, logs):
- #1 `0x2526b8ffd88d3f1159bb2648700a9e3f06d6e51af44277bd87b00f23febbe085` — status 1, gasUsed 0xd1cc, log data = 100,000 FLAPJAX
- #7 `0x79ce6690816844bcde7753f66b6e53fdab5beb8334eac9a5dab61c6c8c964f05` — status 1, gasUsed 0x8f00, log data = 300,000 FLAPJAX
- #14 `0x8bc1664f3d6f7e336e41a55d607f91376ed162f460789e3e209b7080bafade01` — status 1, gasUsed 0x8f00, log data = 50,000 FLAPJAX

## First BNB funder per recipient

### Proven: 7 recipients never received any BNB on BSC

Verified at latest block (24 Nov 2026) on two independent RPCs. Each of these has
**BNB balance 0 and nonce 0, and no contract code (EOA)**:

| Recipient | BNB now | Nonce now |
|---|---|---|
| 0x575a6975ff11d5a72896ff1e3c9f1b2bcf5731cd | 0 | 0 |
| 0x7d1db846f808eefe9ec5e1931174e74e9cf21ef2 | 0 | 0 |
| 0xa8fe84bdcae37e978511012dfec736b07b00fc55 | 0 | 0 |
| 0x42c812fc1d6fb10600e99a1518df970f5be67ad6 | 0 | 0 |
| 0xee0821be193086fe6648b8051e39510ac95b358f | 0 | 0 |
| 0xde58c1a7c40a1a83e62a0ea056408b04252f8930 | 0 | 0 |
| 0xd8ef7b0ead57345265f376940b0644e75c9b482e | 0 | 0 |

Reasoning: nonce 0 means the wallet has never sent a transaction, so it has never
spent BNB. Balance 0 therefore means total BNB ever received = 0. **First BNB funder
for each of these seven: NONE — no such transaction exists.** They received FLAPJAX
passively (token receipt needs no gas) and have never held BNB. (0xee08…'s nonce was
confirmed 0 on the Blast archive RPC after two empty responses from the dataseed;
0xd8ef…'s balance 0 was re-fetched on the dataseed after an empty first response.)

### Found: 3 recipients did receive BNB — all three funders identified

| Recipient | BNB now | Nonce now | First funder | Funding tx | Block | Time (COT) | Amount BNB |
|---|---|---|---|---|---|---|---|
| 0x335aa55c12b260e604d93cb0b0895bb13a4e93e3 | 0.000361044 | 3 | 0xc76c41cd1ab2c6a730865cd58cfedfada6e631ab | 0x13040ac5c98df487cbbc466a17923ccb412095cb9422c54e7672fa7ac26db8e4 | 123994439 | 2026-09-25 13:09:54 | 0.00077032 |
| 0xa15c58e7008fc7a0331cfcc86a28af99fd21b93c | 0.000084949702228733 | 3 | 0xa5a5491bca93dd4c076e4906e79e7673f4a5a142 | 0x9a2aad5e93baea6dbee144b4a9615172a6dd82eddd26007186436a39caa27639 | 132005597 | 2026-11-06 07:04:40 | 0.000193009353538407 |
| 0xfb200657f7266157a45dfcc6c09690726daa24e6 | 0.0005 | 0 | **treasury 0x7C34E9e21eE28A49Ff0b84B61774119E6633359f** | 0xa3d7042983f4f2352b9b8f324414688db10887e2b2b2a125deca9a8bec6624e7 | 126835408 | 2026-10-10 08:25:31 | 0.0005 |

Details:
- **0x335a…** — first funded by `0xc76c41cd1ab2c6a730865cd58cfedfada6e631ab`: balance 0 at block 123994438,
  exactly 0.00077032 BNB at block 123994439, nonce 0 at that block; that block (62 txs)
  contains exactly one tx to this recipient, value = balance increase. Funding tx is a
  plain transfer (input `0x`), receipt status 1, gasUsed 0x5208 (21,000), txIndex 0x1f.
  Link: https://bscscan.com/tx/0x13040ac5c98df487cbbc466a17923ccb412095cb9422c54e7672fa7ac26db8e4
- **0xa15c…** — same funder as in the Q103 and Q104 audits, re-verified here: the Blast binary search
  was not re-run, but the balance boundary was re-checked (balance 0 at 132005596, exactly
  0.000193009353538407 BNB at 132005597) and the funding tx receipt re-fetched (status 1,
  gasUsed 0x5708, txIndex 0x20, from 0xa5a5…).
  Link: https://bscscan.com/tx/0x9a2aad5e93baea6dbee144b4a9615172a6dd82eddd26007186436a39caa27639
- **0xfb20…** — first funded by **the treasury itself**: balance 0 at block 126835407,
  exactly 0.0005 BNB at block 126835408, nonce 0 at that block; that block (93 txs)
  contains exactly one tx to this recipient, value = balance increase. Funding tx is a
  plain transfer (input `0x`), receipt status 1, gasUsed 0x5208 (21,000), txIndex 0x41.
  Link: https://bscscan.com/tx/0xa3d7042983f4f2352b9b8f324414688db10887e2b2b2a125deca9a8bec6624e7

Treasury's own first BNB funder (known from the Q104 audit, sanity-checked here):
balance 0 at block 123473816, exactly 0.12638071 BNB at block 123473817 — funder
`0x5ba434b40be6cfc7033bf8d4545320fa609a4268`, tx
`0xe0f7aeeedd38558ba63a596b8eb6b73e53af63d6282fc3e370160f3b2109bfd0`,
block 123473817, 2026-09-22 20:03:46 COT. Link:
https://bscscan.com/tx/0xe0f7aeeedd38558ba63a596b8eb6b73e53af63d6282fc3e370160f3b2109bfd0

## Funder groups and implied operators

Funder groups (recipients sharing a first funder):

| Group | Members | First funder |
|---|---|---|
| 1 | 0x575a6975…31cd | NONE |
| 2 | 0x7d1db846…21ef2 | NONE |
| 3 | 0xa8fe84bd…0fc55 | NONE |
| 4 | 0x42c812fc…7ad6 | NONE |
| 5 | 0xee0821be…358f | NONE |
| 6 | 0xde58c1a7…8930 | NONE |
| 7 | 0xd8ef7b0e…482e | NONE |
| 8 | 0x335aa55c…93e3 | 0xc76c41cd…31ab |
| 9 | 0xa15c58e7…b93c | 0xa5a5491b…5a142 |
| 10 | 0xfb200657…24e6 | **treasury 0x7C34…359f** |

- The 7 no-BNB recipients cannot be grouped together: "no funder" is not a shared
  wallet, so each is its own funder-group.
- **The key finding of this audit: 0xfb20… was first funded by the treasury itself
  (0.0005 BNB, 10 Oct 2026), so it shares a first funder with the treasury — it counts
  as the treasury's operator group, not a separate operator.** Notably, the treasury
  funded 0xfb20… at 08:25:31 COT on 10 Oct (block 126835408) and 0xfd5e… (a Q103
  recipient) at 08:25:35 COT the same morning (block 126835416) — four seconds apart,
  both exactly 0.0005 BNB — i.e. the treasury was funding wallets with gas money in a
  batch that morning. (0xca58…, the other Q103 treasury-funded recipient, got its
  0.0005 BNB later, on 27 Oct.)
- No other recipient shares a first funder with another recipient or with the treasury:
  0x335a…'s funder (0xc76c…) and 0xa15c…'s funder (0xa5a5…) are different from each
  other, from the treasury, and from the treasury's own funder (0x5ba4…).
- **Distinct operators implied: 10** (10 recipients in 10 funder-groups — no two
  recipients share a funder, and only 0xfb20… groups with the treasury).

## Transfers that could not be explained

None. All 14 transfers are explained: successful `transfer()` calls from the treasury
to the FLAPJAX contract, one Transfer log each, amounts as listed.

Observations only (not proof of shared operator):
- Four tight clusters: 09:28–09:33 (7 transfers in 262 seconds), 13:23 (2 transfers in 21 seconds),
  18:14–18:15 (3 transfers in 107 seconds), 22:11–22:12 (2 transfers in 53 seconds).
  Identical amounts and close timing are consistent with a payout schedule, not by
  themselves evidence of one operator.
- The morning pair 0x575a… / 0x7d1d… received identical amounts in the same pattern
  (100,000 then 50,000, ~2 minutes apart), as did the evening pair 0xde58… (100,000 +
  50,000) and 0xd8ef… (100,000 + 50,000) — the same 100k-then-50k pattern repeats
  across the day.
- 0x335a… is the only recipient with a single 300,000 transfer, the largest of the day;
  it now holds 6,925,000 FLAPJAX and 0xfb20… now holds 6,665,000 — both kept receiving
  FLAPJAX after 18 Nov. The other eight recipients still hold exactly their 18 Nov
  amounts or close to them (0x575a… / 0x7d1d… / 0xde58… / 0xd8ef… exactly 150,000 each;
  0xa8fe… / 0x42c8… exactly 115,000 each; 0xa15c… 175,000 vs 25,000 on 18 Nov;
  0xee08… 215,000 vs 25,000) — exact later receipts were not audited here.

## Coverage by existing submissions — UNVERIFIED

- The public task page lists submission filenames only; it does not show which tx hashes
  each submission covered, and the submission files themselves were not downloaded or opened.
- I therefore **cannot determine which of the 14 tx hashes are already covered**, and
  I do not claim any of them is uncovered.
- Candidate tx hashes that are *guesses only* for a least-likely-covered pick
  (**UNVERIFIED — do not treat as uncovered**):
  1. `0x8bc1664f3d6f7e336e41a55d607f91376ed162f460789e3e209b7080bafade01`
     (#14, 50,000 FLAPJAX, 22:12:52 COT — the last transfer of the day)
  2. `0x0f893bf45f1f446678164c7748009669922d3298eccc7212e1dcd256df6d38f2`
     (#13, 100,000 FLAPJAX, 22:11:59 COT — the other transfer in the final cluster)
  3. `0x4dede2a5861a7aaa523e5c8e802bb392f522a8b556522bd430ff28a3de7df37b`
     (#9, 25,000 FLAPJAX, 13:23:51 COT — the only transfer that day to 0xee08…, a
     recipient with a single transfer; the midday cluster is the smallest cluster)
  - Reasoning for the guess: with many submissions all presumably listing all 14
    transfers, every hash is likely already covered in at least one submission; the
    above are only the latest / most isolated ones. This is not evidence.

## Is this complete enough to submit?

**Yes — as an audit, this is complete.** The transfer list is complete and verified
(14 transfers, 1,005,000 FLAPJAX, blocks named, receipts checked for first/middle/last),
and **every** recipient has an identified first BNB funder (or NONE, proven) with a
re-checkable tx hash, so the funder grouping is proven, not estimated: **10 distinct
operators**.

Remaining risks, disclosed honestly (not gaps in the audit itself):
1. The **uncovered_tx claim cannot be verified from the public task page** — the page
   lists submission filenames only, with no per-hash coverage list. The candidates
   above are guesses only.
2. **Account-age gate:** Agung's TaskMarket web account was registered only on
   24 Nov 2026. If the task requires the account and agent ID to be at least 7 days
   old at check time, and Q102 closes ~27 Nov, the account would be only ~3 days old
   — payout may be blocked even for a correct audit. That is a payout risk, not a
   reason to stop the audit.

## Sources

- Block range / timestamps: `eth_getBlockByNumber` (Binance dataseed + Blast, via curl).
- Transfer logs: `eth_getLogs`, FLAPJAX contract, Transfer topic, from=treasury,
  blocks 134251698–134443554, `https://rpc-bsc.48.club` (192 × 1,000-block chunks, first pass
  13 failed chunks, full re-scan of the affected range with retries, 0 failed chunks remaining).
- Receipts: `eth_getTransactionReceipt` / `eth_getTransactionByHash` (rpc-bsc.48.club +
  Blast archive RPC) for tx #1, #7, #14.
- Balances / nonces / holdings: `eth_getBalance`, `eth_getTransactionCount`,
  `eth_getCode`, `balanceOf` via `eth_call` (Binance dataseed + rpc-bsc.48.club + Blast, agreed).
- Funder binary searches: `eth_getBalance` at historical blocks on archive RPC
  `https://bsc-mainnet.public.blastapi.io`; funding txs identified from
  `eth_getBlockByNumber(full=true)` on the Binance dataseed + receipts.
- Per-transfer links: `https://bscscan.com/tx/<tx-hash>` (links only — BscScan web pages
  were not fetched).
- Full transfer table: `flapjax-q102-transfers.csv` (same directory as this file).
- Prior work reused: `flapjax-q104-audit.md` (method, 2026-11-20 day), `flapjax-q103-audit.md`
  (method, 2026-11-19 day) and `flapjax-q104-funders.md` (Blast archive method; 0xa15c…
  and treasury funders).
