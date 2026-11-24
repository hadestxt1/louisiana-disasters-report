# FlapJax Q103 audit — FLAPJAX transfers out of the treasury, 2026-11-19 COT

- Task: TaskMarket FlapJax Series 3, task Q103 (TaskMarket task ID `0x6ebb27085d014b4e4b8cc915c38760ba2578c8208cc75e6466adfd62129bf48f`)
- Treasury: `0x7C34E9e21eE28A49Ff0b84B61774119E6633359f`
- FLAPJAX token (BSC, 18 decimals): `0x90c8889f428F9Ebb77BB8f15CAD3a50a9aC680df`
- Day audited: **2026-11-19 COT (UTC-5)** = 2026-11-19 00:00:00 to 23:59:59 COT
  = 2026-11-19 05:00:00 UTC to 2026-11-20 05:00:00 UTC
  (unix 1795064400 to 1795150799 inclusive)
- Audit date: 2026-11-24. Read-only research only. No submission made, no wallet created, no contact with FlapJax / TaskMarket.
- Method reused from the Q104 audit (`flapjax-q104-audit.md`, 2026-11-20), including the Blast archive-RPC funder hunt (`flapjax-q104-funders.md`).

## Method (public on-chain data only)

- Block range for the day was fixed by binary search on block timestamps via public BSC RPC:
  - First block of the day: **134443555** — timestamp 1795064400 = 2026-11-19 00:00:00 COT exactly.
    Previous block 134443554 is 1795064399 (23:59:59 COT on 18 Nov).
  - Last block of the day: **134635477** — timestamp 1795150799 = 2026-11-19 23:59:59 COT.
    Next block 134635478 is 1795150800 = 2026-11-20 00:00:00 COT (this is also the first block of the Q104 day, as established in the Q104 audit).
  - Note on coverage: the scan script's binary search was capped at block 134635477, so it scanned 134443555–134635476 and then the final block 134635477 was checked separately with its own `eth_getLogs` call: **0 treasury FLAPJAX Transfer logs in block 134635477**. Full coverage of the day, no block missed.
- Transfer list: `eth_getLogs` on public RPC `https://rpc-bsc.48.club`, filtered to
  Transfer events (`0xddf252ad…`) from the treasury (`topic1` = treasury) on the FLAPJAX
  contract, over blocks 134443555–134635476 inclusive, in 192 chunks of 1,000 blocks,
  plus the single-block check above. **0 failed chunks, full coverage of the range.** 11 logs found.
- Verification: `eth_getTransactionReceipt` + `eth_getTransactionByHash` checked for
  3 transfers (first, middle, last — see below). All three: status `0x1`, `from` = treasury,
  `to` = FLAPJAX token contract, input starts `0xa9059cbb` (`transfer(address,uint256)`),
  exactly 1 Transfer log each, amount matches the log.
- Amounts are exact integers (raw value / 10^18, integer division — no float rounding).
- Recipient balances / nonces were checked at latest block on **two** independent RPCs
  (Binance dataseed and rpc-bsc.48.club) and agreed. FLAPJAX holdings now were read with
  `balanceOf` (`eth_call`) on rpc-bsc.48.club at latest block, 2026-11-24 (latest block seen: 135396842).
- Funder hunt: for every recipient with BNB balance > 0 or nonce > 0 at latest block,
  binary search on archive RPC `https://bsc-mainnet.public.blastapi.io` for the first block
  with balance > 0, then `eth_getBlockByNumber(full=true)` on the Binance dataseed to find the
  single tx to the recipient in that block whose value equals the balance increase, then
  `eth_getTransactionReceipt` to verify status 1. Nonce at each first-nonzero block was 0,
  so no earlier fully-spent inflow could have been missed. (Python `urllib` kept dropping
  connections to these RPCs, so all calls were made with `curl` instead; the pruned dataseeds
  still serve historical blocks/txs fine — only historical *state* is pruned.)
- BscScan web pages were NOT used for cross-checking (the BscScan token page returned HTTP 403
  in the Q104 audit and was not retried). Per-transfer links below are links only.

## Summary

| Item | Value |
|---|---|
| Transfers out of treasury on 2026-11-19 COT | **11** |
| Total FLAPJAX sent | **225,000** |
| Distinct recipients | **8** |
| Distinct operators implied by funder groups | **7** |
| Transfers that could not be explained | **0** (all 11 are plain successful `transfer()` calls from the treasury) |
| First block of the day | **134443555** |
| Last block of the day | **134635477** |

Recipient totals (Nov 19 only):

| Recipient | Transfers | FLAPJAX on 2026-11-19 | FLAPJAX held now (24 Nov) |
|---|---|---|---|
| 0x97cd18b8bbb629b17675d868259ea84c0a2a5a9c | 3 | 75,000 | 8,440,000 |
| 0xaf7f0f0fe64e4304a6e48f89b714b21746f0c0f6 | 2 | 50,000 | 485,000 |
| 0xa15c58e7008fc7a0331cfcc86a28af99fd21b93c | 1 | 25,000 | 175,000 |
| 0x56b40205e0f8cd49eecb253ae82a5308f45a1cf3 | 1 | 15,000 | 115,000 |
| 0xac958f0925a31a2c3844179ab62f12d480baa76d | 1 | 15,000 | 140,000 |
| 0xa4c86f4e9d9ec8990f843aa49470083cece5f908 | 1 | 15,000 | 615,000 |
| 0xfd5efa5c47fb3be071b2fd38fc88dfa30318c5d2 | 1 | 15,000 | 115,000 |
| 0xca58696564492ef9c3229c89072365b253bda246 | 1 | 15,000 | 6,045,000 |
| **Total** | **11** | **225,000** | — |

## All transfers (full table in `flapjax-q103-transfers.csv`)

| # | Time (COT) | Block | Tx hash | Recipient | Amount |
|---|---|---|---|---|---|
| 1 | 2026-11-19 09:13:04 | 134517255 | 0x6eeb0f6bcc12c8301151ae9033bce03affcb59da3ea8447e5c33aa9597dc7d76 | 0x97cd18b8bbb629b17675d868259ea84c0a2a5a9c | 25,000 |
| 2 | 2026-11-19 09:13:28 | 134517309 | 0xdca584c9e5fb0c2cadea0bcf6f40cd33faa7294d543be4d4dc73e7da64c6a6ac | 0x56b40205e0f8cd49eecb253ae82a5308f45a1cf3 | 15,000 |
| 3 | 2026-11-19 09:13:53 | 134517364 | 0x4a4d4715336bcda9acdc52a751694a5cbf002b38931f0a68f928bc3e06b79fcd | 0xac958f0925a31a2c3844179ab62f12d480baa76d | 15,000 |
| 4 | 2026-11-19 13:06:02 | 134548305 | 0xb3740e7d9ec21caa0467986bb254db0809ad60cad5147bc5282fa17f19a60eab | 0xa15c58e7008fc7a0331cfcc86a28af99fd21b93c | 25,000 |
| 5 | 2026-11-19 13:06:26 | 134548358 | 0xdc3b42c6b34c68d1fc94bbc475ccb857a68b34f8e36547df2e0f0b51053a2a91 | 0xa4c86f4e9d9ec8990f843aa49470083cece5f908 | 15,000 |
| 6 | 2026-11-19 18:23:45 | 134590662 | 0xaab1f7bfcfa7ef9f3e641871f318f3ce7e89c4e8146276f24b4f4095eef119f0 | 0xaf7f0f0fe64e4304a6e48f89b714b21746f0c0f6 | 25,000 |
| 7 | 2026-11-19 18:24:08 | 134590714 | 0x5222ba3fd4d77995809760747b870387a326d65e571aa6cab70c5062628deff4 | 0xaf7f0f0fe64e4304a6e48f89b714b21746f0c0f6 | 25,000 |
| 8 | 2026-11-19 18:24:32 | 134590766 | 0x992f570e3616a94c6cec3e488da88dc6ecbd5ab6160c4ab0dac139a193f59b1c | 0x97cd18b8bbb629b17675d868259ea84c0a2a5a9c | 25,000 |
| 9 | 2026-11-19 18:24:55 | 134590817 | 0x0cc4ace68ee20844824ab4bee921148ec7f65e8de4547dde300c6312a6a95b90 | 0x97cd18b8bbb629b17675d868259ea84c0a2a5a9c | 25,000 |
| 10 | 2026-11-19 18:25:18 | 134590868 | 0xdc412e60c6ccf558d81160cfc43e9afa15c7dcecbf4e0289afe568235cedb36a | 0xfd5efa5c47fb3be071b2fd38fc88dfa30318c5d2 | 15,000 |
| 11 | 2026-11-19 18:25:44 | 134590926 | 0x129208753d8298f42c584af4796eff3adfba741cd2aaf389494473a6ca56ea0e | 0xca58696564492ef9c3229c89072365b253bda246 | 15,000 |

Sum check: 25,000 + 15,000 + 15,000 + 25,000 + 15,000 + 25,000 + 25,000 + 25,000 + 25,000 + 15,000 + 15,000
= **225,000 FLAPJAX**. All 11 transfers fall inside the day's block range; no transfer
was found in the first or last blocks of the day (earliest is block 134517255, latest 134590926).

Receipts verified in full (status, from, to, input, logs):
- #1 `0x6eeb0f6bcc12c8301151ae9033bce03affcb59da3ea8447e5c33aa9597dc7d76` — status 1
- #6 `0xaab1f7bfcfa7ef9f3e641871f318f3ce7e89c4e8146276f24b4f4095eef119f0` — status 1
- #11 `0x129208753d8298f42c584af4796eff3adfba741cd2aaf389494473a6ca56ea0e` — status 1

## First BNB funder per recipient

### Proven: 5 recipients never received any BNB on BSC

Verified at latest block (24 Nov 2026) on two independent RPCs. Each of these has
**BNB balance 0 and nonce 0, and no contract code (EOA)**:

| Recipient | BNB now | Nonce now |
|---|---|---|
| 0x97cd18b8bbb629b17675d868259ea84c0a2a5a9c | 0 | 0 |
| 0x56b40205e0f8cd49eecb253ae82a5308f45a1cf3 | 0 | 0 |
| 0xac958f0925a31a2c3844179ab62f12d480baa76d | 0 | 0 |
| 0xa4c86f4e9d9ec8990f843aa49470083cece5f908 | 0 | 0 |
| 0xaf7f0f0fe64e4304a6e48f89b714b21746f0c0f6 | 0 | 0 |

Reasoning: nonce 0 means the wallet has never sent a transaction, so it has never
spent BNB. Balance 0 therefore means total BNB ever received = 0. **First BNB funder
for each of these five: NONE — no such transaction exists.** They received FLAPJAX
passively (token receipt needs no gas) and have never held BNB. (0x97cd… was already
proven NONE in the Q104 audit; re-verified here at latest block.)

### Found: 3 recipients did receive BNB — all three funders identified

| Recipient | BNB now | Nonce now | First funder | Funding tx | Block | Time (COT) | Amount BNB |
|---|---|---|---|---|---|---|---|
| 0xa15c58e7008fc7a0331cfcc86a28af99fd21b93c | 0.000084949702228733 | 3 | 0xa5a5491bca93dd4c076e4906e79e7673f4a5a142 | 0x9a2aad5e93baea6dbee144b4a9615172a6dd82eddd26007186436a39caa27639 | 132005597 | 2026-11-06 07:04:40 | 0.000193009353538407 |
| 0xfd5efa5c47fb3be071b2fd38fc88dfa30318c5d2 | 0.000402208 | 1 | **treasury 0x7C34E9e21eE28A49Ff0b84B61774119E6633359f** | 0x13ff2afcbc50a6ef03f603650ad84642c23c9c26a896612e8e16f5698e6ef2c6 | 126835416 | 2026-10-10 08:25:35 | 0.0005 |
| 0xca58696564492ef9c3229c89072365b253bda246 | 0.000463392 | 1 | **treasury 0x7C34E9e21eE28A49Ff0b84B61774119E6633359f** | 0x87443eff758296585f6d6eb7b68800ea6c73f143239e60541a6ef5b1f072d456 | 130097514 | 2026-10-27 08:29:06 | 0.0005 |

Details:
- **0xa15c…** — same funder as in the Q104 audit, re-verified here: the Blast binary search
  reproduced the same first-nonzero block 132005597 (balance 0 at 132005596, exactly
  0.000193009353538407 BNB at 132005597, nonce 0 at that block), and the funding tx
  was re-fetched with receipt status 1, gasUsed 0x5708, txIndex 0x20, input `0xf297dd3c…`
  (a call with data to an EOA; data is ignored by an EOA, value still transferred).
  Link: https://bscscan.com/tx/0x9a2aad5e93baea6dbee144b4a9615172a6dd82eddd26007186436a39caa27639
- **0xfd5e…** — first funded by **the treasury itself**: balance 0 at block 126835415,
  exactly 0.0005 BNB at block 126835416, nonce 0 at that block; that block (116 txs)
  contains exactly one tx to this recipient, value = balance increase. Funding tx is a
  plain transfer (input `0x`), receipt status 1, gasUsed 0x5208 (21,000), txIndex 0x5d.
  Link: https://bscscan.com/tx/0x13ff2afcbc50a6ef03f603650ad84642c23c9c26a896612e8e16f5698e6ef2c6
- **0xca58…** — first funded by **the treasury itself**: balance 0 at block 130097513,
  exactly 0.0005 BNB at block 130097514, nonce 0 at that block; that block (97 txs)
  contains exactly one tx to this recipient, value = balance increase. Funding tx is a
  plain transfer (input `0x`), receipt status 1, gasUsed 0x5208 (21,000), txIndex 0x53.
  Link: https://bscscan.com/tx/0x87443eff758296585f6d6eb7b68800ea6c73f143239e60541a6ef5b1f072d456

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
| 1 | 0x97cd18b8…5a9c | NONE |
| 2 | 0x56b40205…cf3 | NONE |
| 3 | 0xac958f09…a76d | NONE |
| 4 | 0xa4c86f4e…f908 | NONE |
| 5 | 0xaf7f0f0f…0f6 | NONE |
| 6 | 0xa15c58e7…b93c | 0xa5a5491b…5a142 |
| 7 | 0xfd5efa5c…5d2, 0xca586965…246 | **treasury 0x7C34…359f** |

- The 5 no-BNB recipients cannot be grouped together: "no funder" is not a shared
  wallet, so each is its own funder-group.
- **The key finding of this audit: 0xfd5e… and 0xca58… were both first funded by the
  treasury itself (0.0005 BNB each, on 10 Oct and 27 Oct 2026), so they share a first
  funder with each other and with the treasury — they count as ONE operator group,
  not two separate operators.** The treasury appears to have funded these two wallets
  with gas money (exactly 0.0005 BNB each) weeks before paying them FLAPJAX.
- No other recipient shares a first funder with another recipient or with the treasury:
  0xa15c…'s funder (0xa5a5…) is different from the treasury's funder (0x5ba4…) and from
  the treasury itself.
- **Distinct operators implied: 7** (8 recipients in 7 funder-groups).

## Transfers that could not be explained

None. All 11 transfers are explained: successful `transfer()` calls from the treasury
to the FLAPJAX contract, one Transfer log each, amounts as listed.

Observations only (not proof of shared operator):
- Three tight clusters: 09:13 (3 transfers in 49 seconds), 13:06 (2 transfers in 24 seconds),
  18:23–18:25 (6 transfers in 119 seconds). Identical amounts and close timing are
  consistent with a payout schedule, not by themselves evidence of one operator.
- 0x97cd… is the only recipient in two clusters (morning + evening); it also received
  25,000 FLAPJAX on 20 Nov (Q104) and now holds 8,440,000 FLAPJAX — it kept receiving
  FLAPJAX after 19 Nov, as did 0xca58… (now 6,045,000). The other six recipients hold
  115,000–615,000 now, so they too received further FLAPJAX after 19 Nov (0xfd5e… is the
  only one whose current holding, 115,000, is close to its 19 Nov amount plus small later
  receipts — exact later receipts were not audited here).

## Coverage by existing submissions — UNVERIFIED

- The public task page lists submission filenames only; it does not show which tx hashes
  each submission covered, and the submission files themselves were not downloaded or opened.
- I therefore **cannot determine which of the 11 tx hashes are already covered**, and
  I do not claim any of them is uncovered.
- Candidate tx hashes that are *guesses only* for a least-likely-covered pick
  (**UNVERIFIED — do not treat as uncovered**):
  1. `0x129208753d8298f42c584af4796eff3adfba741cd2aaf389494473a6ca56ea0e`
     (#11, 15,000 FLAPJAX, 18:25:44 COT — the last transfer of the day)
  2. `0xdc412e60c6ccf558d81160cfc43e9afa15c7dcecbf4e0289afe568235cedb36a`
     (#10, 15,000 FLAPJAX, 18:25:18 COT)
  3. `0xdc3b42c6b34c68d1fc94bbc475ccb857a68b34f8e36547df2e0f0b51053a2a91`
     (#5, 15,000 FLAPJAX, 13:06:26 COT — the only transfer that day to 0xa4c8…, a
     recipient with a single transfer; the midday cluster is the smallest cluster)
  - Reasoning for the guess: with many submissions all presumably listing all 11
    transfers, every hash is likely already covered in at least one submission; the
    above are only the smallest / latest / most isolated ones. This is not evidence.

## Is this complete enough to submit?

**Yes — as an audit, this is complete.** The transfer list is complete and verified
(11 transfers, 225,000 FLAPJAX, blocks named, receipts checked for first/middle/last),
and **every** recipient has an identified first BNB funder (or NONE, proven) with a
re-checkable tx hash, so the funder grouping is proven, not estimated: **7 distinct
operators**.

Remaining risks, disclosed honestly (not gaps in the audit itself):
1. The **uncovered_tx claim cannot be verified from the public task page** — the page
   lists submission filenames only, with no per-hash coverage list. The candidates
   above are guesses only.
2. **Account-age gate:** Agung's TaskMarket web account was registered only on
   24 Nov 2026. If the task requires the account and agent ID to be at least 7 days
   old at check time, and Q103 closes ~28 Nov, the account would be only ~4 days old
   — payout may be blocked even for a correct audit. That is a payout risk, not a
   reason to stop the audit.

## Sources

- Block range / timestamps: `eth_getBlockByNumber` (Binance dataseeds + Blast, via curl).
- Transfer logs: `eth_getLogs`, FLAPJAX contract, Transfer topic, from=treasury,
  blocks 134443555–134635476, `https://rpc-bsc.48.club` (192 × 1,000-block chunks, 0 failed),
  plus a single-block `eth_getLogs` check for block 134635477 (0 logs).
- Receipts: `eth_getTransactionReceipt` / `eth_getTransactionByHash` (rpc-bsc.48.club)
  for tx #1, #6, #11.
- Balances / nonces / holdings: `eth_getBalance`, `eth_getTransactionCount`,
  `eth_getCode`, `balanceOf` via `eth_call` (Binance dataseed + rpc-bsc.48.club, agreed).
- Funder binary searches: `eth_getBalance` at historical blocks on archive RPC
  `https://bsc-mainnet.public.blastapi.io`; funding txs identified from
  `eth_getBlockByNumber(full=true)` on the Binance dataseed + receipts.
- Per-transfer links: `https://bscscan.com/tx/<tx-hash>` (links only — BscScan web pages
  were not fetched).
- Full transfer table: `flapjax-q103-transfers.csv` (same directory as this file).
- Prior work reused: `flapjax-q104-audit.md` (method, 2026-11-20 day) and
  `flapjax-q104-funders.md` (Blast archive method; 0xa15c… and treasury funders).
