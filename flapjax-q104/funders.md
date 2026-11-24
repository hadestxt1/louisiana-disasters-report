# FlapJax Q104 — first BNB funder hunt (24 Nov 2026)

Read-only research. No install, no CLI, no wallet created, no submission, no paid API signup, no private keys used.

Targets (from `flapjax-q104-audit.md`):
- A: `0x8eefb57b8b45e0671aad79226033d24b0456bbd4` — BNB 0.0000112419, nonce 1
- B: `0xa15c58e7008fc7a0331cfcc86a28af99fd21b93c` — BNB 0.000084949702228733, nonce 3
- Treasury (optional): `0x7C34E9e21eE28A49Ff0b84B61774119E6633359f`

## Result: BOTH FOUND

### Recipient A — 0x8eefb57b8b45e0671aad79226033d24b0456bbd4 — FOUND
- **First BNB funder:** `0x72b39d562635d3e889af89880cc633ae2a284f8a`
- **Funding tx:** `0x8e123cc5fbf4bff0abe0081eeb63d259a4af4d87b7f8d54cd19ded71e1d8a3c2`
- **Block:** 46636417
- **Time:** 2025-02-13 23:51:22 UTC / 2025-02-13 18:51:22 COT
- **Amount:** 12,424,241,900,000,000 wei = **0.0124242419 BNB**
- **Receipt:** status 1, gasUsed 21,000, txIndex 141, plain transfer (`input: 0x`)
- **Link:** https://bscscan.com/tx/0x8e123cc5fbf4bff0abe0081eeb63d259a4af4d87b7f8d54cd19ded71e1d8a3c2
- **Proof:** balance 0 at block 46636416, exactly 0.0124242419 BNB at block 46636417 (binary search on archive RPC `bsc-mainnet.public.blastapi.io`); that block contains exactly one tx to A, with value equal to the balance increase. A later spent almost all of it (1 outgoing tx, nonce 1), leaving the 0.0000112419 BNB dust seen now.
- **Note:** A is an old wallet — first funded in Feb 2025, ~21 months before the 20 Nov 2026 FlapJax payout.

### Recipient B — 0xa15c58e7008fc7a0331cfcc86a28af99fd21b93c — FOUND
- **First BNB funder:** `0xa5a5491bca93dd4c076e4906e79e7673f4a5a142`
- **Funding tx:** `0x9a2aad5e93baea6dbee144b4a9615172a6dd82eddd26007186436a39caa27639`
- **Block:** 132005597
- **Time:** 2026-11-06 12:04:40 UTC / 2026-11-06 07:04:40 COT
- **Amount:** 193,009,353,538,407 wei = **0.000193009353538407 BNB**
- **Receipt:** status 1, gasUsed 22,280, txIndex 32, input `0xf297dd3c…` (66 chars — a call with data to an EOA; data is ignored by an EOA, value still transferred)
- **Link:** https://bscscan.com/tx/0x9a2aad5e93baea6dbee144b4a9615172a6dd82eddd26007186436a39caa27639
- **Proof:** balance 0 at block 132005596, exactly 0.000193009353538407 BNB at block 132005597 (binary search on archive RPC); that block (75 txs) contains exactly one tx to B, with value equal to the balance increase.
- **Note:** B received a second, separate inflow shortly after — balance 0.000386196523192621 by block 132007324 (second inflow ≈ 0.000193187169654214 BNB). B was first funded 14 days before its 20 Nov FlapJax receipt, then spent BNB on 3 outgoing txs (nonce 3), leaving 0.0000849497 BNB.

### Grouping consequence
- The two funders are **different wallets** (`0x72b3…` vs `0xa5a5…`), and **neither is the treasury** (`0x7C34…`). So A and B do **not** share a first funder with each other.
- Combined with the audit's 5 no-BNB recipients (funder: NONE, each its own group), the funder evidence now proves **7 distinct funder-groups / 7 distinct operators** — the audit's upper bound is now proven, not just an upper bound. (Treasury's own first funder still unchecked — see below; if it ever matched one of these two funders, that recipient would group with the treasury, but no such link is known.)

## Treasury first funder — FOUND
- **First BNB funder:** `0x5ba434b40be6cfc7033bf8d4545320fa609a4268`
- **Funding tx:** `0xe0f7aeeedd38558ba63a596b8eb6b73e53af63d6282fc3e370160f3b2109bfd0`
- **Block:** 123473817
- **Time:** 2026-09-23 01:03:46 UTC / 2026-09-22 20:03:46 COT
- **Amount:** 126,380,710,000,000,000 wei = **0.12638071 BNB**
- **Receipt:** status 1, gasUsed 21,000, txIndex 23, plain transfer (`input: 0x`)
- **Link:** https://bscscan.com/tx/0xe0f7aeeedd38558ba63a596b8eb6b73e53af63d6282fc3e370160f3b2109bfd0
- **Proof:** binary search on Blast archive RPC found first nonzero balance at block 123473817 (balance exactly 0.12638071 BNB; 0 at 123473816). Validity check: treasury nonce was 0 at blocks 67,695,405 / 101,543,108 / 118,466,959 / 123,473,816 — it had never sent a tx before its first funding, so its balance could only grow before then and the binary search cannot have missed an earlier, fully-spent inflow. That block (54 txs) contains exactly one tx to the treasury, value = balance increase.
- **Grouping consequence:** the treasury's funder (`0x5ba4…`) is different from both recipients' funders, so **no recipient shares a first funder with the treasury either**. All 7 recipients + treasury = 8 separate funder-groups.

## Attempt log (every route tried, in order)
1. **BscScan API v1, no key + dummy key** (`api.bscscan.com/api`, `txlist`, `txlistinternal`, `balance`): HTTP 200 but body is the Etherscan API docs HTML landing page, not JSON — the endpoint serves docs on this egress regardless of `apikey` param. FAILED.
2. **Etherscan V2 API** (`api.etherscan.io/v2/api`, chainid=56): JSON `{"status":"0","message":"NOTOK","result":"Free API access is not supported for this chain…"}`. FAILED — BSC not covered on free tier.
3. **BscScan web, `browser.open` address page**: HTTP 403 access denied. FAILED, not retried (access denial).
4. **BscScan web, `browser.search` for the address**: returned unrelated BscScan address pages, no hit for either target. FAILED.
5. **Blockscout**: `bsc.blockscout.com/api/v2` → HTTP 404 "default backend"; `blockscout.com/bnb-smart-chain/api/v2` → HTTP 503. FAILED.
6. **Routescan API** (`api.routescan.io/v2/.../56/...`): 400 `NO_BLOCKCHAINS_FOR_PARAMS` / 404. FAILED — BSC not served that way.
7. **OKLink**: API `api/v5/...` → 401 Unauthorized (key required). Web address page → HTTP 200 but only an 18 KB client-side shell, no tx data in HTML. FAILED.
8. **Bitquery explorer page**: HTTP 403. FAILED. **explorer.bnbchain.org API**: 404. FAILED.
9. **Archive RPC tests** (`eth_getBalance` at block 100,000,000):
   - Ankr `rpc.ankr.com/bsc`: "Unauthorized: You must authenticate with an API key". FAILED.
   - PublicNode `bsc.publicnode.com`: 403 "Archive requests require a personal token". FAILED.
   - 1rpc `1rpc.io/bnb`: "usage limit for your current plan". FAILED.
   - Blast `bsc-mainnet.public.blastapi.io`: **WORKED — returned a real historical balance.** ✓
   - LlamaRPC / BlockPi / NodeReal / Chainstack / Pokt: connection closed / 503 "Apikey not found" / 401 / 403 paid plan. FAILED.
   - OnFinality `bnb.api.onfinality.io/public`: "historical state … is not available". FAILED.
   - dRPC `bsc.drpc.org`: 429 public rate limit. FAILED.
   - Omniatech: HTTP 521. FAILED. MeowRPC: "not supported". FAILED.
   - Binance dataseed + rpc-bsc.48.club: "missing trie node" / "header not found" at old blocks (pruned, as before). FAILED for history.
10. **Blast archive binary search — WORKED:**
    - B: 0 at block 120,000,000 → >0 at 134,000,000 → binary search → first nonzero block **132005597** (balance exactly 193,009,353,538,407 wei).
    - A: 0 at block 10,000,000 → >0 at 50,000,000 → binary search → first nonzero block **46636417** (balance exactly 12,424,241,900,000,000 wei).
    - Blast rate-limits (429 / dropped connections) — mitigated with retries + sleeps; full-block fetches via Blast failed, so block contents were fetched from the **pruned Binance dataseed** instead (historical blocks/txs are served fine by pruned nodes; only historical *state* is pruned).
    - Funding txs identified from `eth_getBlockByNumber(full=true)` on dataseed + `eth_getTransactionReceipt` (both status 1). Each first-nonzero block contains exactly one tx to the recipient, value = balance increase.
11. **Outgoing-tx upper bound (route 5)**: not needed — the binary search gave exact blocks directly. (Nonce checks: A nonce 0 at block 46636417, B nonce 0 at 132005597 — funding precedes any outgoing tx, as expected.)
