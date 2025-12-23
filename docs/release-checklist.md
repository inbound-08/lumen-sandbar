# Lumen Sandbar — Release Checklist

Short checklist to run before tagging or deploying a release.

---

## Testnet Validation (Base Sepolia)

- [ ] App loads successfully on Base Sepolia
- [ ] Read-only calls succeed (balances, metadata)
- [ ] Smart account creation (if used) works as expected
- [ ] No hardcoded Mainnet-only assumptions

---

## Explorer Verification

- [ ] Explorer links resolve correctly (BaseScan / Sepolia BaseScan)
- [ ] Transaction hashes open on the correct explorer
- [ ] Chain IDs match network selection

---

## Dependency Hygiene

- [ ] Dependencies align with Base ecosystem usage
- [ ] No unused or redundant SDKs
- [ ] Versions are pinned or intentionally ranged
- [ ] No direct forks without documentation

---

## Final Checks

- [ ] `config/base.networks.json` unchanged or reviewed
- [ ] No secrets or private keys committed
- [ ] Documentation updated if behavior changed

_Release only after all items are checked._
