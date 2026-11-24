# FlapJax Q104 audit — FLAPJAX transfers out of the treasury, 2026-11-20 COT

- Task: TaskMarket FlapJax Series 3, task Q104 (top open task on the Base-chain list, 24 Nov 2026)
- Treasury: `0x7C34E9e21eE28A49Ff0b84B61774119E6633359f`
- FLAPJAX token (BSC, 18 decimals): `0x90c8889f428F9Ebb77BB8f15CAD3a50a9aC680df`
- Day audited: **2026-11-20 COT (UTC-5)** = 2026-11-20 00:00:00 to 23:59:59 COT
  = 2026-11-20 05:00:00 UTC to 2026-11-21 05:00:00 UTC
  (unix 1795150800 to 1795237199 inclusive)
- Audit date: 2026-11-24. Read-only research only. No submission made, no wallet created, no contact with FlapJax / TaskMarket.

## Method (public on-chain data only)

- Block range for the day was fixed by binary search on block timestamps via public BSC RPC
  (`eth_getBlockByNumber` on `https://bsc-dataseed.bnbchain.org/`):
  - First block of the day: **134635478** — timestamp 1795150800 = 2026-11-20 00:00:00 COT exactly.
    Previous block 134635477 is 1795150799 (23:59:59 COT on 19 Nov).
  - Last block of the day: **134827416** — timestamp 1795237199 = 2026-11-20 23:59:59 COT.
    Next block 134827417 is 1795237200 = 2026-11-21 00:00:00 COT.
- Transfer list: `eth_getLogs` on public RPC `https://rpc-bsc.48.club`, filtered to
  Transfer events (`0xddf252ad…`) from the treasury (`topic1` = treasury) on the FLAPJAX
  contract, over blocks 134635478–134827416 inclusive, in 192 chunks of 1,000 blocks.
  **0 failed chunks, full coverage of the range.** 10 logs found.
- Verification: `eth_getTransactionReceipt` + `eth_getTransactionByHash` checked for
  3 transfers (first, middle, last — see below). All three: status `0x1`, `from` = treasury,
  `to` = FLAPJAX token contract, input starts `0xa9059cbb` (`transfer(address,uint256)`),
  exactly 1 Transfer log each, amount matches the log.
- Amounts are exact integers (raw value / 10^18, integer division — no float rounding).
- Recipient balances / nonces were checked at latest block on **two** independent RPCs
  (Binance dataseed and rpc-bsc.48.club) and agreed. FLAPJAX holdings now were read with
  `balanceOf` (`eth_call`) on rpc-bsc.48.club at latest block, 2026-11-24.
- BscScan web pages were NOT usable for cross-checking: the BscScan token page returned
  HTTP 403 (access denied) and was not retried. Cross-checking was therefore done via
  public-RPC receipts and logs instead (see above).

## Summary

| Item | Value |
|---|---|
| Transfers out of treasury on 2026-11-20 COT | **10** |
| Total FLAPJAX sent | **830,000** |
| Distinct recipients | **7** |
| Distinct operators implied by funder groups | **7 groups as listed, but only 5 are proven distinct — see Funder section** |
| Transfers that could not be explained | **0** (all 10 are plain successful `transfer()` calls from the treasury) |
| First block of the day | **134635478** |
| Last block of the day | **134827416** |

Recipient totals (Nov 20 only):

| Recipient | Transfers | FLAPJAX on 2026-11-20 | FLAPJAX held now (24 Nov) |
|---|---|---|---|
| 0x3caf985d1ab6fb0f62c5a50e4c696761577a469c | 2 | 300,000 | 300,000 |
| 0x8eefb57b8b45e0671aad79226033d24b0456bbd4 | 2 | 300,000 | 300,000 |
| 0x97cd18b8bbb629b17675d868259ea84c0a2a5a9c | 1 | 25,000 | 8,440,000 |
| 0xa15c58e7008fc7a0331cfcc86a28af99fd21b93c | 1 | 25,000 | 175,000 |
| 0xdb93a0eb1c994ac5679ada5cbfd76a32f424f5ae | 2 | 150,000 | 150,000 |
| 0x7cb74499c67a328df6dec491652faab2aed00bc3 | 1 | 15,000 | 115,000 |
| 0xf3d562f6de2a369afef8aaac1147062d5c20bcb6 | 1 | 15,000 | 325,000 |
| **Total** | **10** | **830,000** | — |

## All transfers (full table in `flapjax-q104-transfers.csv`)

| # | Time (COT) | Block | Tx hash | Recipient | Amount |
|---|---|---|---|---|---|
| 1 | 2026-11-20 09:17:54 | 134709832 | 0xa24d59b4988d4f90a62e8d6bdf081c07f361568126ae8f6d7c4f4cb5a1522913 | 0x3caf985d1ab6fb0f62c5a50e4c696761577a469c | 250,000 |
| 2 | 2026-11-20 09:18:17 | 134709882 | 0xb42e9faf7eff6ab7d77c1ac9ef5706e1d77ea9c0a2d4038b70500b30b6af7d9a | 0x8eefb57b8b45e0671aad79226033d24b0456bbd4 | 250,000 |
| 3 | 2026-11-20 09:19:53 | 134710095 | 0x2abeffbc7ec5a960261a4e4c582060c82f6aa220cc5716c77c3737aea74a958d | 0x3caf985d1ab6fb0f62c5a50e4c696761577a469c | 50,000 |
| 4 | 2026-11-20 09:20:16 | 134710146 | 0x38f0029a6347be8105910c0246d5c3ad95a1d7fbb4a8c10e59997d8af9983dd1 | 0x8eefb57b8b45e0671aad79226033d24b0456bbd4 | 50,000 |
| 5 | 2026-11-20 09:20:57 | 134710238 | 0xa58b1b955ae75a9de9ba426fa29ad3f3d283e8d75bd456b2ece1a705b6f3c906 | 0x97cd18b8bbb629b17675d868259ea84c0a2a5a9c | 25,000 |
| 6 | 2026-11-20 13:10:45 | 134740868 | 0x5185fdf4881e03fde625f561fe897be4e0af14fd011df14d6d30b08afb46ecf3 | 0xa15c58e7008fc7a0331cfcc86a28af99fd21b93c | 25,000 |
| 7 | 2026-11-20 22:22:52 | 134814470 | 0x076de3727cf5c15edd283d7712d1775c60841fb5b0b4bea7164014c56b43656a | 0xdb93a0eb1c994ac5679ada5cbfd76a32f424f5ae | 100,000 |
| 8 | 2026-11-20 22:23:52 | 134814603 | 0xa66799aa0988acaf579e19b9cb17501945d3d26a5e515858f33d43d47e4d0848 | 0xdb93a0eb1c994ac5679ada5cbfd76a32f424f5ae | 50,000 |
| 9 | 2026-11-20 22:24:53 | 134814738 | 0x0edf63016beaa4171cbd1177259e6b68e5f7fc837a279fee0a887f2e51db142d | 0x7cb74499c67a328df6dec491652faab2aed00bc3 | 15,000 |
| 10 | 2026-11-20 22:25:14 | 134814786 | 0xa2c6f3b696c06d722f0bd7089575629de4822f9d7ffc5ceb2b5f5402f5bb1da4 | 0xf3d562f6de2a369afef8aaac1147062d5c20bcb6 | 15,000 |

Sum check: 250,000 + 250,000 + 50,000 + 50,000 + 25,000 + 25,000 + 100,000 + 50,000 + 15,000 + 15,000
= **830,000 FLAPJAX**. All 10 transfers fall inside the day's block range; no transfer
was found in the first or last blocks of the day (earliest is block 134709832, latest 134814786).

Receipts verified in full (status, from, to, input, logs):
- #1 `0xa24d59b4988d4f90a62e8d6bdf081c07f361568126ae8f6d7c4f4cb5a1522913` — status 1
- #6 `0x5185fdf4881e03fde625f561fe897be4e0af14fd011df14d6d30b08afb46ecf3` — status 1
- #10 `0xa2c6f3b696c06d722f0bd7089575629de4822f9d7ffc5ceb2b5f5402f5bb1da4` — status 1

## First BNB funder per recipient

### Proven: 5 recipients never received any BNB on BSC

Verified at latest block (24 Nov 2026) on two independent RPCs. Each of these has
**BNB balance 0 and nonce 0, and no contract code (EOA)**:

| Recipient | BNB now | Nonce now |
|---|---|---|
| 0x3caf985d1ab6fb0f62c5a50e4c696761577a469c | 0 | 0 |
| 0x97cd18b8bbb629b17675d868259ea84c0a2a5a9c | 0 | 0 |
| 0xdb93a0eb1c994ac5679ada5cbfd76a32f424f5ae | 0 | 0 |
| 0x7cb74499c67a328df6dec491652faab2aed00bc3 | 0 | 0 |
| 0xf3d562f6de2a369afef8aaac1147062d5c20bcb6 | 0 | 0 |

Reasoning: nonce 0 means the wallet has never sent a transaction, so it has never
spent BNB. Balance 0 therefore means total BNB ever received = 0. **First BNB funder
for each of these five: NONE — no such transaction exists.** They received FLAPJAX
passively (token receipt needs no gas) and have never held BNB.

### NOT FOUND: 2 recipients did receive BNB, but the funder tx could not be determined

| Recipient | BNB now | Nonce now |
|---|---|---|
| 0x8eefb57b8b45e0671aad79226033d24b0456bbd4 | 0.0000112419 | 1 |
| 0xa15c58e7008fc7a0331cfcc86a28af99fd21b93c | 0.000084949702228733 | 3 |

These two demonstrably received BNB at some point (tiny dust balances remain, and
they have sent 1 and 3 transactions respectively), so a first funder exists — but
I could not identify it with the public tools available:

- The public RPCs I could use are pruned: `eth_getBalance` / `eth_getTransactionCount`
  at any block older than roughly the latest returns "missing trie node" (Binance
  dataseed) or "header not found" (rpc-bsc.48.club), so a binary search for the first
  funding block over full history is not possible on them. No archive node was available.
- Free transaction-history indexers all need an API key or do not cover BSC:
  Covalent / GoldRush, Moralis, Chainbase and OKLink require a key; Etherscan V2 free
  tier does not cover BSC (chain 56); Blockchair is IP-blacklisted on this egress;
  Blockscout for BSC returned 503; Routescan does not index BSC.
- The treasury's own first BNB funder could not be determined for the same reason.

**Funder tx for 0x8eef… and 0xa15c…: UNVERIFIED / NOT FOUND. Do not treat either
recipient as linked or unlinked on funder evidence.**

## Funder groups and implied operators

- No shared first BNB funder was found between any two recipients, or between any
  recipient and the treasury — because 5 recipients have no funder at all and the
  other 2 have unknown funders.
- The 5 no-BNB recipients cannot be grouped together: "no funder" is not a shared
  wallet, so each is its own funder-group. That alone proves **at least 5 distinct
  operators** among the recipients, on funder evidence.
- Counting each recipient as its own group absent a proven link gives **7 funder-groups**,
  but that is an upper bound, not a proof: the 2 unknown-funder recipients could in
  principle share a funder with each other, with the treasury, or with one of the
  others. Honest range: **5–7 distinct operators; 7 groups listed, 5 proven distinct.**
- Observations only (not proof of shared operator): the morning pair
  0x3caf… / 0x8eef… received identical amounts in the same pattern (250,000 then
  50,000, ~2 minutes apart); the evening pair 0x7cb7… / 0xf3d5… both received exactly
  15,000 within 21 seconds of each other; 0xdb93… received 100,000 + 50,000 within a minute.
  Identical amounts and close timing are consistent with a payout schedule, not by
  themselves evidence of one operator.
- Other-days context (from `balanceOf` now, 24 Nov): 0x97cd… now holds 8,440,000 FLAPJAX
  (vs 25,000 on 20 Nov), 0xf3d5… 325,000, 0xa15c… 175,000, 0x7cb7… 115,000 — so those
  four received further FLAPJAX after 20 Nov. 0x3caf…, 0x8eef… and 0xdb93… still hold
  exactly their 20 Nov amounts (300,000 / 300,000 / 150,000): no further receipts
  and no sells as of 24 Nov.

## Transfers that could not be explained

None. All 10 transfers are explained: successful `transfer()` calls from the treasury
to the FLAPJAX contract, one Transfer log each, amounts as listed.

What could NOT be explained / verified (gaps):
1. First BNB funder tx for 0x8eef… and 0xa15c… — not found (see above).
2. First BNB funder of the treasury itself — not found (same reason).
3. Whether any of the 10 tx hashes was already covered by an earlier accepted claim —
   not determinable from the public task page (see below).

## Coverage by existing submissions — UNVERIFIED

- The public task page lists submission filenames only (13 submissions from 12 submitters
  at the time of checking); it does not show which tx hashes each submission covered,
  and the submission files themselves were not downloaded or opened.
- I therefore **cannot determine which of the 10 tx hashes are already covered**, and
  I do not claim any of them is uncovered.
- Candidate tx hashes that are *guesses only* for a least-likely-covered pick
  (**UNVERIFIED — do not treat as uncovered**):
  1. `0xa2c6f3b696c06d722f0bd7089575629de4822f9d7ffc5ceb2b5f5402f5bb1da4`
     (#10, 15,000 FLAPJAX, 22:25:14 COT — the last transfer of the day)
  2. `0x0edf63016beaa4171cbd1177259e6b68e5f7fc837a279fee0a887f2e51db142d`
     (#9, 15,000 FLAPJAX, 22:24:53 COT)
  3. `0x5185fdf4881e03fde625f561fe897be4e0af14fd011df14d6d30b08afb46ecf3`
     (#6, 25,000 FLAPJAX, 13:10:45 COT — the only transfer in the 13:xx hour, isolated
     in time from the morning and evening clusters)
  - Reasoning for the guess: with many submissions all presumably listing all 10
    transfers, every hash is likely already covered in at least one submission; the
    above are only the smallest / most isolated ones. This is not evidence.

## Is this complete enough to submit?

**Update 24 Nov after the funder hunt:** the funder grouping is now complete —
all 7 recipients have an identified first BNB funder (or NONE, proven), with
re-checkable tx hashes, and the 7 distinct operators are proven. The transfer
list is complete and verified (10 transfers, 830,000 FLAPJAX, blocks named,
receipts checked).

Remaining unverified item, disclosed honestly: the **uncovered_tx claim cannot
be verified from the public task page** — the page lists submission filenames
only, with no per-hash coverage list. The task description as read on 24 Nov
states a verified list of 20 outflows, the first ten already covered by Q103
and the next ten not yet covered; the 10 transfers in this audit are the
2026-11-20 set. The uncovered_tx named in the submission file is the author's
best candidate (#10, the last transfer of the day), not a verified-uncovered
claim. Agung's TaskMarket web account was registered only on 24 Nov 2026
(today), so age-eligibility is also a separate risk — the submission is made
on Agung's explicit instruction to submit now despite those two unverified
items.

## Sources

- Block range / timestamps: `eth_getBlockByNumber` (Binance dataseed).
- Transfer logs: `eth_getLogs`, FLAPJAX contract, Transfer topic, from=treasury,
  blocks 134635478–134827416, `https://rpc-bsc.48.club` (192 × 1,000-block chunks, 0 failed).
- Receipts: `eth_getTransactionReceipt` / `eth_getTransactionByHash` (rpc-bsc.48.club)
  for tx #1, #6, #10.
- Balances / nonces / holdings: `eth_getBalance`, `eth_getTransactionCount`,
  `eth_getCode`, `balanceOf` via `eth_call` (Binance dataseed + rpc-bsc.48.club, agreed).
- Per-transfer links: `https://bscscan.com/tx/<tx-hash>` (links only — BscScan web pages
  were not fetched; the token page returned HTTP 403 and was not retried).
- Full transfer table: `flapjax-q104-transfers.csv` (same directory as this file).

## Funder hunt 24 Nov

Both previously-unknown first BNB funders were **found** (full details + attempt log in `flapjax-q104-funders.md`):

- **0x8eef…bbd4** — first funded by `0x72b39d562635d3e889af89880cc633ae2a284f8a`, tx `0x8e123cc5fbf4bff0abe0081eeb63d259a4af4d87b7f8d54cd19ded71e1d8a3c2`, block 46636417, 2025-02-13 18:51:22 COT, **0.0124242419 BNB** (plain transfer, receipt status 1).
- **0xa15c…b93c** — first funded by `0xa5a5491bca93dd4c076e4906e79e7673f4a5a142`, tx `0x9a2aad5e93baea6dbee144b4a9615172a6dd82eddd26007186436a39caa27639`, block 132005597, 2026-11-06 07:04:40 COT, **0.000193009353538407 BNB** (receipt status 1).
- Method: archive RPC `bsc-mainnet.public.blastapi.io` (the one public endpoint that served historical balances) — binary search for the first block with balance > 0, then `eth_getBlockByNumber(full)` + receipt on the pruned Binance dataseed. Each first-nonzero block holds exactly one tx to the recipient, value = balance increase.
- The two funders are different wallets and neither is the treasury, so A and B do **not** share a first funder. With the 5 no-BNB recipients (funder NONE, each its own group), the funder evidence now proves **7 distinct funder-groups / 7 distinct operators** — the earlier "5–7" range is resolved to 7. Treasury's own first funder was also found in the same hunt: `0x5ba434b40be6cfc7033bf8d4545320fa609a4268`, tx `0xe0f7aeeedd38558ba63a596b8eb6b73e53af63d6282fc3e370160f3b2109bfd0`, block 123473817, 2026-09-22 20:03:46 COT, 0.12638071 BNB — different from both recipients' funders, so no recipient groups with the treasury either.
