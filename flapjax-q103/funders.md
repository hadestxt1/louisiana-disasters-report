# FlapJax Q103 — first BNB funder per recipient (2026-11-19 COT)

- Task: TaskMarket FlapJax Series 3, task Q103 (task ID `0x6ebb27085d014b4e4b8cc915c38760ba2578c8208cc75e6466adfd62129bf48f`)
- Treasury: `0x7C34E9e21eE28A49Ff0b84B61774119E6633359f`
- Day audited: **2026-11-19 COT (UTC-5)**, blocks 134443555–134635477. 11 transfers, 225,000 FLAPJAX, 8 distinct recipients.
- Full audit: `README.md` in this folder; full transfer table: `transfers.csv`.
- Method: for every recipient with BNB balance > 0 or nonce > 0 at latest block (24 Nov 2026), binary search on archive RPC `https://bsc-mainnet.public.blastapi.io` for the first block with balance > 0, then `eth_getBlockByNumber(full=true)` on the Binance dataseed to find the single tx to the recipient in that block whose value equals the balance increase, then `eth_getTransactionReceipt` to verify status 1. Nonce at each first-nonzero block was 0, so no earlier fully-spent inflow could have been missed. Balances/nonces were checked at latest block on two independent RPCs (Binance dataseed and rpc-bsc.48.club) and agreed.

## Proven: 5 recipients never received any BNB on BSC

Each has **BNB balance 0 and nonce 0, and no contract code (EOA)** at latest block (24 Nov 2026), verified on two RPCs:

| Recipient | BNB now | Nonce now | First BNB funder |
|---|---|---|---|
| 0x97cd18b8bbb629b17675d868259ea84c0a2a5a9c | 0 | 0 | NONE |
| 0x56b40205e0f8cd49eecb253ae82a5308f45a1cf3 | 0 | 0 | NONE |
| 0xac958f0925a31a2c3844179ab62f12d480baa76d | 0 | 0 | NONE |
| 0xa4c86f4e9d9ec8990f843aa49470083cece5f908 | 0 | 0 | NONE |
| 0xaf7f0f0fe64e4304a6e48f89b714b21746f0c0f6 | 0 | 0 | NONE |

Reasoning: nonce 0 means the wallet has never sent a transaction, so it has never spent BNB. Balance 0 therefore means total BNB ever received = 0. **First BNB funder for each of these five: NONE — no such transaction exists.** They received FLAPJAX passively (token receipt needs no gas) and have never held BNB. (0x97cd… was already proven NONE in the Q104 audit; re-verified here at latest block.)

## Found: 3 recipients did receive BNB — all three funders identified

| Recipient | BNB now | Nonce now | First funder | Funding tx | Block | Time (COT) | Amount BNB |
|---|---|---|---|---|---|---|---|
| 0xa15c58e7008fc7a0331cfcc86a28af99fd21b93c | 0.000084949702228733 | 3 | 0xa5a5491bca93dd4c076e4906e79e7673f4a5a142 | 0x9a2aad5e93baea6dbee144b4a9615172a6dd82eddd26007186436a39caa27639 | 132005597 | 2026-11-06 07:04:40 | 0.000193009353538407 |
| 0xfd5efa5c47fb3be071b2fd38fc88dfa30318c5d2 | 0.000402208 | 1 | **treasury 0x7C34E9e21eE28A49Ff0b84B61774119E6633359f** | 0x13ff2afcbc50a6ef03f603650ad84642c23c9c26a896612e8e16f5698e6ef2c6 | 126835416 | 2026-10-10 08:25:35 | 0.0005 |
| 0xca58696564492ef9c3229c89072365b253bda246 | 0.000463392 | 1 | **treasury 0x7C34E9e21eE28A49Ff0b84B61774119E6633359f** | 0x87443eff758296585f6d6eb7b68800ea6c73f143239e60541a6ef5b1f072d456 | 130097514 | 2026-10-27 08:29:06 | 0.0005 |

Details:
- **0xa15c…** — same funder as in the Q104 audit, re-verified here: the Blast binary search reproduced the same first-nonzero block 132005597 (balance 0 at 132005596, exactly 0.000193009353538407 BNB at 132005597, nonce 0 at that block), and the funding tx was re-fetched with receipt status 1. Link: https://bscscan.com/tx/0x9a2aad5e93baea6dbee144b4a9615172a6dd82eddd26007186436a39caa27639
- **0xfd5e…** — first funded by **the treasury itself**: balance 0 at block 126835415, exactly 0.0005 BNB at block 126835416, nonce 0 at that block; that block (116 txs) contains exactly one tx to this recipient, value = balance increase. Funding tx is a plain transfer (input `0x`), receipt status 1, gasUsed 0x5208 (21,000). Link: https://bscscan.com/tx/0x13ff2afcbc50a6ef03f603650ad84642c23c9c26a896612e8e16f5698e6ef2c6
- **0xca58…** — first funded by **the treasury itself**: balance 0 at block 130097513, exactly 0.0005 BNB at block 130097514, nonce 0 at that block; that block (97 txs) contains exactly one tx to this recipient, value = balance increase. Funding tx is a plain transfer (input `0x`), receipt status 1, gasUsed 0x5208 (21,000). Link: https://bscscan.com/tx/0x87443eff758296585f6d6eb7b68800ea6c73f143239e60541a6ef5b1f072d456

Treasury's own first BNB funder (known from the Q104 audit, sanity-checked here): balance 0 at block 123473816, exactly 0.12638071 BNB at block 123473817 — funder `0x5ba434b40be6cfc7033bf8d4545320fa609a4268`, tx `0xe0f7aeeedd38558ba63a596b8eb6b73e53af63d6282fc3e370160f3b2109bfd0`, block 123473817, 2026-09-22 20:03:46 COT. Link: https://bscscan.com/tx/0xe0f7aeeedd38558ba63a596b8eb6b73e53af63d6282fc3e370160f3b2109bfd0

## Funder groups and implied operators

| Group | Members | First funder |
|---|---|---|
| 1 | 0x97cd18b8…5a9c | NONE |
| 2 | 0x56b40205…cf3 | NONE |
| 3 | 0xac958f09…a76d | NONE |
| 4 | 0xa4c86f4e…f908 | NONE |
| 5 | 0xaf7f0f0f…0f6 | NONE |
| 6 | 0xa15c58e7…b93c | 0xa5a5491b…5a142 |
| 7 | 0xfd5efa5c…5d2, 0xca586965…246 | **treasury 0x7C34…359f** |

- The 5 no-BNB recipients cannot be grouped together: "no funder" is not a shared wallet, so each is its own funder-group.
- **Key finding: 0xfd5e… and 0xca58… were both first funded by the treasury itself (0.0005 BNB each, on 10 Oct and 27 Oct 2026), so they share a first funder with each other and with the treasury — they count as ONE operator group, not two separate operators.** The treasury appears to have funded these two wallets with gas money (exactly 0.0005 BNB each) weeks before paying them FLAPJAX.
- No other recipient shares a first funder with another recipient or with the treasury: 0xa15c…'s funder (0xa5a5…) is different from the treasury's funder (0x5ba4…) and from the treasury itself.
- **Distinct operators implied: 7** (8 recipients in 7 funder-groups).
