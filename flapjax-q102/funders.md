# FlapJax Q102 — first BNB funder per recipient (2026-11-18 COT)

- Task: TaskMarket FlapJax Series 3, task Q102 (TaskMarket task ID `0xc1d799a4aaa844b60c182d42a19af0a3fc7b333116611960946d105c8ef31cb2`)
- Treasury: `0x7C34E9e21eE28A49Ff0b84B61774119E6633359f`
- FLAPJAX token (BSC, 18 decimals): `0x90c8889f428F9Ebb77BB8f15CAD3a50a9aC680df`
- Day audited: **2026-11-18 COT (UTC-5)**, blocks 134251698–134443554
- Full audit: `README.md` in this folder (14 transfers, 1,005,000 FLAPJAX, 10 recipients).
- Method: Blast archive RPC (`https://bsc-mainnet.public.blastapi.io`) binary search for the
  first block with balance > 0, then block/receipt lookup on the Binance dataseed —
  the same method as the Q104/Q103 funder hunts. Nonce 0 at each first-nonzero block,
  so no earlier fully-spent inflow could have been missed.

## Proven: 7 recipients never received any BNB on BSC

Verified at latest block (24 Nov 2026) on two independent RPCs. Each has
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
passively (token receipt needs no gas) and have never held BNB.

## Found: 3 recipients did receive BNB — all three funders identified

| Recipient | BNB now | Nonce now | First funder | Funding tx | Block | Time (COT) | Amount BNB |
|---|---|---|---|---|---|---|---|
| 0x335aa55c12b260e604d93cb0b0895bb13a4e93e3 | 0.000361044 | 3 | 0xc76c41cd1ab2c6a730865cd58cfedfada6e631ab | 0x13040ac5c98df487cbbc466a17923ccb412095cb9422c54e7672fa7ac26db8e4 | 123994439 | 2026-09-25 13:09:54 | 0.00077032 |
| 0xa15c58e7008fc7a0331cfcc86a28af99fd21b93c | 0.000084949702228733 | 3 | 0xa5a5491bca93dd4c076e4906e79e7673f4a5a142 | 0x9a2aad5e93baea6dbee144b4a9615172a6dd82eddd26007186436a39caa27639 | 132005597 | 2026-11-06 07:04:40 | 0.000193009353538407 |
| 0xfb200657f7266157a45dfcc6c09690726daa24e6 | 0.0005 | 0 | **treasury 0x7C34E9e21eE28A49Ff0b84B61774119E6633359f** | 0xa3d7042983f4f2352b9b8f324414688db10887e2b2b2a125deca9a8bec6624e7 | 126835408 | 2026-10-10 08:25:31 | 0.0005 |

Details:
- **0x335a…** — balance 0 at block 123994438, exactly 0.00077032 BNB at block 123994439,
  nonce 0 at that block; that block (62 txs) contains exactly one tx to this recipient,
  value = balance increase. Plain transfer (input `0x`), receipt status 1, gasUsed 0x5208,
  txIndex 0x1f. Link: https://bscscan.com/tx/0x13040ac5c98df487cbbc466a17923ccb412095cb9422c54e7672fa7ac26db8e4
- **0xa15c…** — same funder as in the Q103 and Q104 audits, re-verified here (balance
  boundary re-checked, funding tx receipt re-fetched, status 1, gasUsed 0x5708,
  txIndex 0x20). Link: https://bscscan.com/tx/0x9a2aad5e93baea6dbee144b4a9615172a6dd82eddd26007186436a39caa27639
- **0xfb20…** — first funded by **the treasury itself**: balance 0 at block 126835407,
  exactly 0.0005 BNB at block 126835408, nonce 0 at that block; that block (93 txs)
  contains exactly one tx to this recipient, value = balance increase. Plain transfer
  (input `0x`), receipt status 1, gasUsed 0x5208, txIndex 0x41.
  Link: https://bscscan.com/tx/0xa3d7042983f4f2352b9b8f324414688db10887e2b2b2a125deca9a8bec6624e7

Treasury's own first BNB funder (known from the Q104 audit, sanity-checked here):
balance 0 at block 123473816, exactly 0.12638071 BNB at block 123473817 — funder
`0x5ba434b40be6cfc7033bf8d4545320fa609a4268`, tx
`0xe0f7aeeedd38558ba63a596b8eb6b73e53af63d6282fc3e370160f3b2109bfd0`,
block 123473817, 2026-09-22 20:03:46 COT. Link:
https://bscscan.com/tx/0xe0f7aeeedd38558ba63a596b8eb6b73e53af63d6282fc3e370160f3b2109bfd0

## Funder groups and implied operators

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
- **Key finding: 0xfb20… was first funded by the treasury itself (0.0005 BNB,
  10 Oct 2026), so it shares a first funder with the treasury — it counts as the
  treasury's operator group, not a separate operator.**
- **10-Oct batch-funding observation:** the treasury funded 0xfb20… at 08:25:31 COT
  on 10 Oct (block 126835408) and 0xfd5e… (a Q103 recipient) at 08:25:35 COT the same
  morning (block 126835416) — four seconds apart, both exactly 0.0005 BNB — i.e. the
  treasury was funding wallets with gas money in a batch that morning. (0xca58…, the
  other Q103 treasury-funded recipient, got its 0.0005 BNB later, on 27 Oct.)
- No other recipient shares a first funder with another recipient or with the treasury.
- **Distinct operators implied: 10** (10 recipients in 10 funder-groups — no two
  recipients share a funder, and only 0xfb20… groups with the treasury).
