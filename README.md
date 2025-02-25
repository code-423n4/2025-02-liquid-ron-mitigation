# Liquid Ron Mitigation Review
- Total Prize Pool: $5,000 in USDC
  - Warden awards: $3,750 in USDC
  - Judge awards: $1,000 in USDC
  - Scout awards: $250 in USDC
- [Warden guidelines for C4 mitigation reviews](https://code4rena.notion.site/Guidelines-for-C4-mitigation-reviews-ed10fc5cfbf640bd8dcec66f38b343c4)
- Starts February 26, 2025 20:00 UTC
- Ends March 3, 2025 20:00 UTC

## Important note 

Each warden must submit a mitigation review for *every* individual item listed in the `Scope` section below. **Incomplete mitigation reviews will not be eligible for awards.**

## Findings being mitigated

Mitigations of all High and Medium issues will be considered in-scope and listed here.

- [F-3: The calculation of `totalAssets()` could be wrong if `operatorFeeAmount` > 0, this can cause potential loss for the new depositors](https://code4rena.com/evaluate/2025-01-liquid-ron/findings/F-3)
- [F-23: Operators are unable to perform any actions due to incorrect modifier implementation](https://code4rena.com/evaluate/2025-01-liquid-ron/findings/F-23)
- [F-10: User can earn rewards by frontrunning the new rewards accumulation in Ron staking without actually delegating his tokens](https://code4rena.com/evaluate/2025-01-liquid-ron/findings/F-10)

Mitigations of these additional issues will also be considered in-scope:
- [F-18: `_checkUserCanReceiveRon` does not guarantee that the user can receive RON](https://code4rena.com/evaluate/2025-01-liquid-ron/findings/F-18)
- [F-25: `LiquidRon` vault can be bricked permanently, locking away all `WRON` assets](https://code4rena.com/evaluate/2025-01-liquid-ron/findings/F-25)
- [F-2: Proxies cannot be removed, which can cause `LiquidRon.pruneValidatorList`, `LiquidRon.getTotalStaked`, and `LiquidRon.getTotalRewards` function calls to revert due to out of gas](https://code4rena.com/evaluate/2025-01-liquid-ron/findings/F-2)
- [F-45: Validator Stake Count is not updated in ValidatorTracker](https://code4rena.com/evaluate/2025-01-liquid-ron/findings/F-45)
- [F-32: https://code4rena.com/evaluate/2025-01-liquid-ron/findings/F-32](https://code4rena.com/evaluate/2025-01-liquid-ron/findings/F-32)
- [F-156: `validatorIndex` Not Cleared When Removing a Validator](https://code4rena.com/evaluate/2025-01-liquid-ron/findings/F-156)
- [F-22: Unnecessary loop could lead to DOS because of too much gas is needed](https://code4rena.com/evaluate/2025-01-liquid-ron/findings/F-22)
- [F-1: The paused vault can receive deposits from the user](https://code4rena.com/evaluate/2025-01-liquid-ron/findings/F-1)
- [S-736: QA Report - Low 4 (Inefficient view functions for large datasets)](https://code4rena.com/evaluate/2025-01-liquid-ron/findings/S-736)
- Various QA items (listed in scope table below, i.e. ADD-01 through ADD-04)

## Overview of changes [optional]

[ ⭐️ SPONSORS ADD INFO HERE ]

Please provide context about the mitigations that were applied if applicable and identify any areas of specific concern. 

## Scope

### Branch
- Branch: https://github.com/OwlOfMoistness/liquid_ron/tree/ca4-mitigation
- Commits: https://github.com/OwlOfMoistness/liquid_ron/compare/main...ca4-mitigation

### Mitigation of High & Medium Severity Issues
| Mitigation URL | Mitigation of | Purpose | 
| ----------- | ------------- | ----------- |
| [Link](https://github.com/OwlOfMoistness/liquid_ron/commit/c30c35b1b5a4adcc46f1d20506a9816f1fec275c) | F-3 | Add operatorFeeAmount in totalAssets calculations | 
| [Link](https://github.com/OwlOfMoistness/liquid_ron/commit/af83a41854f38a7defef97dde2e8a5a97a0f13d1) | F-23 | Bad operator modifer | 
| [Link](https://github.com/OwlOfMoistness/liquid_ron/commit/3eb49f91241ef3bf1c8bedda4180ac1c36e80995) | F-10 | Add a deposit fee that can be reset every period based on daily expected rewards | 

### Additional scope to be reviewed
These are additional changes that will be in scope.

| Mitigation URL | Reference ID | Purpose | 
| ----------- | ------------- | ----------- |
| [Link](https://github.com/OwlOfMoistness/liquid_ron/commit/14fd27de293430d97aab2b5fe746d2513426dc05) | F-18 | Update flow of withdrawal to add changeable receiver |
| [Link](https://github.com/OwlOfMoistness/liquid_ron/commit/0d4844c9697a9365760c7eb1673f5e51c37281b2) | F-25 | Replace validator data storage from consensus addresses to IDs which never change |
| [Link](https://github.com/OwlOfMoistness/liquid_ron/commit/ea748e02c9dbf700d24e28db1fb9a586ffc24c87) | F-2 | Add start index to start loop on specif validator and length of computation |
| [Link](https://github.com/OwlOfMoistness/liquid_ron/commit/15ef42af4bd5391b43824b262affe605176b3aa4) | F-45 | QA, remove unused mapping |
| [Link](https://github.com/OwlOfMoistness/liquid_ron/commit/c3b19f0c0ffb5a9cfbf56859a35e3e672bf0cb0d) | F-32 | Fix wrong event emission |
| [Link](https://github.com/OwlOfMoistness/liquid_ron/commit/1780ebde0ec92c1c9523dd56bb72960ef8f9f169) | F-156 | Clear validator Index when removing it |
| [Link](https://github.com/OwlOfMoistness/liquid_ron/commit/af2165659f4c721e9caa91df8f69db4859360955) | F-22 | Remove for loop |
| [Link](https://github.com/OwlOfMoistness/liquid_ron/commit/64a6dfed2ba5691a492883b1efe60f5b7814690e) | F-1 | Prevent native deposits when paused |
| [Link](https://github.com/OwlOfMoistness/liquid_ron/commit/e275282e9365e7b2e0295c464d69197f272c0338) | S-736: Low-4&ast;| Improve getTotalStaked() to prevent recomputing state each call by tracking internally |
| [Link 1](https://github.com/OwlOfMoistness/liquid_ron/commit/08cf347939feafca4681469a2a33606ca826c055), [Link 2](https://github.com/OwlOfMoistness/liquid_ron/commit/415665dcd7b8cac90b3540c90c3bc32ceaec9121) | ADD-01 | QAs: getValidator func, payable withdraw ron, remove _checkIfPaused, immutable proxy var, check src/dst in proxy, remove dead code, deposit payable has receiver param |
| [Link](https://github.com/OwlOfMoistness/liquid_ron/commit/be97c210ae421bc0e9a5147c2ede584caea0bb53) | ADD-02 | Fix test |
| [Link](https://github.com/OwlOfMoistness/liquid_ron/commit/354c741e989f5d27a2f55b68b190a7fc71b26135) | ADD-03 | Add forge lib |
| [Link](https://github.com/OwlOfMoistness/liquid_ron/commit/017f2bb1e2d7de54726969529eec1f3be9cc4329) | ADD-04 | Add periodStartVariable for external data tracking |

&ast;Note: commit title incorrectly mentions `S-726`.

## Out of Scope

All known issues listed in the preceding audit's [repo](https://github.com/code-423n4/2025-01-liquid-ron) are considered known issues and out of scope.