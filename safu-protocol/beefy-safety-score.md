# Beefy Safety Score

This document outlines the design for the Beefy Safety Score. The purpose of the safety score is to educate users when making a decision to enter a particular Beefy vault. The Safety Score is not necessarily perfect, but it is another tool that helps the user.

The safety score that a vault can get goes from 0 to 10. The best possible score is 10 and the worst is 0. It is technically possible for vaults to score less than 0, in which case 0 will be displayed.

Risks are distributed in three main categories:

* Beefy Risks: Risks that we add by serving as a platform.&#x20;
* Asset Risks: Risks of the asset being handled by the vault.
* Platform Risks: Risks of the underlying farm or platform used.

Each category is responsible for a percentage of the total score. Each category is itself divided in multiple subcategories.

All vaults start with a perfect score of 10 and are subtracted points whenever they have qualities that increase risk.

## Category: Beefy Risks

These are risks related to the Beefy Finance platform itself. These could be risks added by the complexity of the vault strategy, if it's an experimental deployment, if it's been audited by others, etc. Twenty percent of the safety score is determined by the Beefy Risks.

### Subcategory: Complexity

Tracks the complexity of the strategy behind a vault.

#### COMPLEXITY\_LOW

* Title: Low complexity strategy
* Explanation: Low complexity strategies have few, if any, moving parts and their code is easy to read and debug. There is a direct correlation between code complexity and implicit risk. A simple strategy effectively mitigates implementation risks.
* Qualification Criteria: A low complexity strategy should interact with just one audited and well-known smart contract e.g. MasterChef. The strategy serves as a façade for this smart contract, forwarding deposit, harvest and withdrawal calls using a single line of code.&#x20;

#### COMPLEXITY\_MID

* Title: Beefy strategy is of medium complexity
* Explanation: Medium complexity strategies interact with two or more audited and well-known smart contracts. Its code is still easy to read, test and debug. It mitigates most implementation risks by keeping things simple, however the interactions between 2 or more systems add a layer of complexity.
* Qualification Criteria: A medium complexity strategy interacts with 2 or more well-known smart contracts. This strategy automates the execution of a series of steps with no forking paths. Every time deposit(), harvest() and withdraw() is called, the same execution path is followed.

#### COMPLEXITY\_HIGH

* Title: Beefy strategy is complex&#x20;
* Explanation: High complexity strategies interact with one or more well-known smart contracts. These advanced strategies present branching paths of execution. In some cases multiple smart contracts are required to implement the full strategy.
* Qualification Criteria: A high level complexity strategy can be identified by one or more of the following factors: high cyclomatic complexity, interactions between two or more third-party platforms, implementation split between multiple smart contracts.

### Subcategory: Time in Market

Tracks how long has this strategy been running without any major issues.

#### BATTLE\_TESTED

* Title: Beefy strategy is battle tested
* Explanation: The more time a particular strategy is running, the more likely that any potential bugs it had have been found, and fixed. This strategy has been exposed to attacks and usage for some time already, with little to no changes. This makes it sturdier.&#x20;
* Qualification Criteria:
  * Was deployed using a BeefyStratFactory
  * 10+ strategies sharing the same code deployed
  * 3 months working as expected without upgrades

#### NEW\_STRAT

* Title: Strategy has been running for less than a month&#x20;
* Explanation: The more time a particular strategy is running, the more likely that any potential bugs it has have been found, and fixed. This strategy is a modification or iteration of a previous strategy. It hasn't been battle tested as much as others.
* Qualification Criteria: -

#### EXPERIMENTAL\_STRAT

* Title: The strategy has some features which are new&#x20;
* Explanation: The more time a particular strategy is running, the more likely that any potential bugs it had have been found, and fixed. This strategy is brand new and has at least one experimental feature. Use it carefully at your own discretion.
* Qualification Criteria: -

## Category: Asset Risks

Risks relating to the asset or assets handled by the vault. Entering into a vault with BTC has a different set of risks than entering into a vault with a newer and smaller coin. Twenty percent of the score is determined by this category.

### Subcategory: Impermanent Loss

Tracks the risk of impermanent loss within the vault

#### IL\_NONE

* Title: Very low or zero projected IL&#x20;
* Explanation: The asset in this vault has very little or even no expected impermanent loss. This might be because you are staking a single asset, or because the assets in the LP are tightly correlated like USDC-USDT or WBTC-renBTC.
* Qualification Criteria: Single asset vaults and vaults that manage stablecoins with a peg that isn't experimental: USDT, USDC, DAI, sUSD, etc. &#x20;

#### IL\_LOW

* Title: Low projected IL&#x20;
* Explanation: When you are providing liquidity into a token pair, for example ETH-BNB, there is a risk that those assets decouple in price. BNB could drop considerably in relation to ETH. You would lose some funds as a result, compared to just holding ETH and BNB on their own. The assets in this vault have some risks of impermanent loss.&#x20;
* Qualification Criteria: Vaults that handle what are normally referred as “Pool 1” LPs would fit here: ETH-USDC, MATIC-AAVE, etc. Governance tokens for smaller projects are normally known as “Pool 2” and thereby excluded.

#### IL\_HIGH

* Title: High projected IL&#x20;
* Explanation: When you are providing liquidity into a token pair, for example ETH-BNB, there is a risk that those assets decouple in price. BNB could drop considerably in relation to ETH. You would lose some funds as a result, compared to just holding ETH and BNB on their own. The assets in this vault have a high or very high risk of impermanent loss.&#x20;
* Qualification Criteria: Vaults that handle “Pool 2” LPs go here. These LP normally include the governance token of the farm itself.

#### ALGO\_STABLE

* Title: Algorithmic stable, experimental peg
* Explanation: When you are providing liquidity into a token pair, for example ETH-BNB, there is a risk that those assets decouple in price. BNB could drop considerably in relation to ETH. You would lose some funds as a result, compared to just holding ETH and BNB on their own. At least one of the stablecoins held by this vault is an algorithmic stable. This means that the stable peg is experimental and highly risky. Use it carefully at your own discretion.
* Qualification Criteria: “Stablecoins” with experimental pegs, or tokenomics that have failed repeatedly to hold its peg in the past, go here.

### Subcategory: Liquidity

Tracks how difficult it is to buy/sell the vault's token.

#### LIQ\_HIGH

* Title: High trade liquidity
* Explanation: How liquid an asset is affects how risky it is to hold it. Liquid assets are traded in many places and with good volume. The asset held by this vault has high liquidity. This means that you can exchange your earnings easily in plenty of places.
* Qualification Criteria: -

#### LIQ\_LOW

* Title: Low trade liquidity
* Explanation: How liquid an asset is affects how risky it is to hold it. Liquid assets are traded in many places and with good volume. The asset held by this vault has low liquidity. This means that it isn't as easy to swap and you might incur high slippage when doing so.
* Qualification Criteria: -

### Subcategory: Market Cap

Total value of all the coins in circulation. Indirectly tracks how volatile the vault's underlying asset is.

#### MCAP\_LARGE

* Title: High market cap, low volatility asset
* Explanation: The market capitalization of the crypto asset directly affects how risky it is to hold it. Usually a small market cap implies high volatility and low liquidity. The asset held by this vault has a large market cap. This means it's potentially a highly safe asset to hold. The asset has a high potential to stick around and grow over time.
* Qualification Criteria: Top 50 MC by Gecko/CMC

#### MCAP\_MEDIUM

* Title: Medium market cap, medium volatility asset
* Explanation: The market capitalization of the crypto asset directly affects how risky it is to hold it. Usually a small market cap implies high volatility and low liquidity. The asset held by this vault has a medium market cap. This means it's potentially a safe asset to hold. The asset has potential to stick around and grow over time.
* Qualification Criteria: Between 50 and 300 MC by Gecko/CMC

#### MCAP\_SMALL

* Title: Small market cap, high volatility asset
* Explanation: The market capitalization of the crypto asset directly affects how risky it is to hold it. Usually a small market cap implies high volatility and low liquidity. The asset held by this vault has a small market cap. This means it's potentially a risky asset to hold. The asset has low potential to stick around and grow over time.
* Qualification Criteria: Between 300 and 500 MC by Gecko/CMC

#### MCAP\_MICRO

* Title: Micro market cap, Extreme volatility asset
* Explanation: The market capitalization of the crypto asset directly affects how risky it is to hold it. Usually a small market cap implies high volatility and low liquidity. The asset held by this vault has a micro market cap. This means it's potentially a highly risky asset to hold. The asset has low potential to stick around.
* Qualification Criteria: +500 MC by Gecko/CMC

### Subcategory: Supply

Tracks risks related to the asset supply. Can it be altered by anyone? How centralised is it?

#### SUPPLY\_CENTRALIZED

* Title: Few very powerful whales
* Explanation: When the supply is concentrated in a few hands, they can greatly affect the price by selling. Whales can manipulate the price of the coin. The more people that have a vested interest over a coin, the better and more organic the price action is.
* Qualification Criteria: Less than 50 accounts hold more than 50% of the supply.&#x20;

## Category: Platform Risks

Risks relating to the third party platforms used by the vault. How much track record they have, how solid the code is, are there any dangerous actions that an admin can take, etc. Sixty percent of the score is determined by this category.

### Subcategory: Reputation

Tries to give clues about the team and community's track record. How likely are they to rug for example.

#### PLATFORM\_ESTABLISHED

* Title: The platform has a known track record
* Explanation: When taking part in a farm, it can be helpful to know the amount of time that the platform has been around and the degree of its reputation. The longer the track record, the more investment the team and community have behind a project. This vault farms a project that has been around for many months.
* Qualification Criteria: The underlying farm has been around for at least 3 months.

#### PLATFORM\_NEW

* Title: Platform is new with little track record
* Explanation: When taking part in a farm, it can be helpful to know the amount of time that the platform has been around and the degree of its reputation. The longer the track record, the more investment the team and community have behind a project. This vault farms a new project, with less than a few months out in the open.
* Qualification Criteria: The underlying farm has been around for less than 3 months.

### Subcategory: Security

Tracks various smart contract good practices.

#### NO\_AUDIT

* Title: The platform has never been audited by third-party trusted auditors
* Explanation: Audits are reviews of code by a group of third party developers.
* Qualification Criteria: -

#### AUDIT

* Title: The platform has an audit from at least one trusted auditor
* Explanation: Audits are reviews of code by a group of third party developers.
* Qualification Criteria: One or more audits from an auditor that has some positive track record in the space.

#### CONTRACTS\_VERIFIED

* Title: All relevant contracts are publicly verified
* Explanation: Code running in a particular contract is not public by default. Block explorers let developers verify the code behind a particular contract. This is a good practice because it lets other developers audit that the code does what it’s supposed to. All the third party contracts that this vault uses are verified. This makes it less risky.
* Qualification Criteria: -

#### CONTRACTS\_UNVERIFIED

* Title: Some contracts are not verified
* Explanation: Code running in a particular contract is not public by default. Block explorers let developers verify the code behind a particular contract. This is a good practice because it lets other developers audit that the code does what it’s supposed to. Some of the third party contracts that this vault uses are not verified. This means that there are certain things that the Beefy devs have not been able to inspect.
* Qualification Criteria: -

#### ADMIN\_WITH\_TIMELOCK

* Title: Dangerous functions are behind a timelock
* Explanation: Sometimes the contract owner or admin can execute certain functions that could put user funds in jeopardy. The best thing is to avoid these altogether. If they must be present, it’s important to keep them behind a timelock to give proper warning before using them. This contract has certain dangerous admin functions, but they are at least behind a meaningful Timelock.&#x20;
* Qualification Criteria: There is at least one function present that could partially or completely rug user funds. The function must be behind a +6h timelock.

#### ADMIN\_WITHOUT\_TIMELOCK

* Title: Dangerous functions are without a timelock
* Explanation: Sometimes the contract owner or admin can execute certain functions that could put user funds in jeopardy. The best thing is to avoid these altogether. If they must be present, it’s important to keep them behind a timelock to give proper warning before using them. This contract has certain dangerous admin functions, and there is no time lock present. They can be executed at a moment's notice.
* Qualification Criteria: There is at least one function present that could partially or completely rug user funds. The function has no time lock protection.
