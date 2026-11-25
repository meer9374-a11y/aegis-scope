# AegisScope — Zero-Connect Multi-Chain DeFi Approval & Permit2 VaR Scanner

**Live Tool (100% Client-Side, Zero Wallet Connect):** https://meer9374-a11y.github.io/aegis-scope/

AegisScope is a pure client-side multi-chain RPC scanner that audits token approvals, hidden Uniswap `Permit2` sub-allowances, upgradeable spender proxies, and Solana SPL token delegates directly in the browser without requiring a wallet connection.

## Key Capabilities

- **Packed Permit2 Sub-Allowance Decoding (`0x927da105`):** Queries `Permit2.allowance(address owner, address token, address spender)` (`0x000000000022D473030F116dDEE9F6B43aC78BA3`) alongside standard ERC-20 `0xdd62ed3e` (`allowance`) and bit-unpacks `(uint160 amount, uint48 expiration, uint48 nonce)` to distinguish active router sub-allowances from expired signatures.
- **EIP-1967 Upgradeable Proxy Detection (`eth_getStorageAt`):** Inspects EIP-1967 implementation slot `0x360894a13ba1a3210667c828492db98dca3e2076cc3735a920a3ca505d382bbc` on approved spenders to flag mutable proxy routers.
- **Parallel Multi-Chain JSON-RPC Batching:** Scans Ethereum, Base, Arbitrum, Polygon, and Solana (SPL delegates) in parallel directly from browser RPC calls (`~220ms` benchmarked on `vitalik.eth`).
- **Atomic `Safe{Wallet}` `txBuilder` v1.16.5 Export:** Generates ready-to-import `txBuilder` v1.16.5 JSON revoke batches so multisig signers can revoke multiple open approvals in a single transaction.
- **Zero-Backend & Zero-Connect Audit UX:** Paste any EVM or Solana address to audit Value-at-Risk (VaR) with no wallet signature or backend API required.
