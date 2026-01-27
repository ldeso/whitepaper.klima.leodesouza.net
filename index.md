# Klima 2.0
The Dark Sole Enterprise Ltd <ds@darksole.vip>  
with contributions from the Klima and Carbonmark teams

27 Jan 2026 (Version 1.48)

<img src="brand/klimaprotocol.svg" style="width:50.0%"
alt="Klima Protocol Logo." data-fig-align="center" />

**Copyright Notice**

This document represents original work by dark_sole <ds@darksole.vip>.
While contributions from others are gratefully acknowledged, all
intellectual property rights remain with the author. The models,
algorithms, processes, products, methodologies, and concepts described
herein are licenced exclusively for commercial use by the Klima
Protocol. No other party may implement, copy, modify, or derive works
from these materials without explicit written permission from the
author.

© 2025 dark_sole. All rights reserved.

## Prologue

Klima 2.0 is an autonomous, rules-based coordination protocol designed
to support the retirement of carbon credits through continuous and
transparent execution terms.

It is not a financial product, investment vehicle, or asset management
system, but a piece of market infrastructure that enables carbon supply
and retirement demand to interact under predefined conditions.

The protocol operates through a dual-token architecture that facilitates
coordination without discretionary control: **kVCM** functions as the
internal unit of account and pricing reference for protocol-facilitated
carbon retirement, while **K2** provides signalling inputs related to
system capacity. Together, these tokens inform protocol parameters
through deterministic smart-contract logic. This architecture enables
the protocol to:

- define execution rates and intake eligibility for carbon credits
  against transparent, pre-defined rules;

- make acquired credits available exclusively for irreversible
  retirement;

- coordinate liquidity provision and participation incentives required
  for continuous operation.

Participant actions such as locking tokens, signalling preferences, or
providing liquidity serve inputs into a coordination mechanism that
adjusts protocol parameters within predefined bounds. These inputs do
not confer ownership rights, redemption rights, or claims on
protocol-held carbon, nor do they constitute discretionary management of
assets.

The protocol consists of three interdependent functional layers:

- a carbon inventory layer that holds credits solely for the purpose of
  facilitating retirement;

- a coordination layer that aggregates participant signals to inform
  protocol parameters; and

- a liquidity layer that supports access and withdrawal from the system
  through external markets.

These layers are designed to operate together as a self-contained
system, adjusting to observable supply and retirement demand without
reliance on external oracles, manual intervention, or fee-extractive
intermediaries.

Klima 2.0 abstracts complex carbon market interactions into a
transparent and auditable execution framework, enabling participants to
interact with carbon retirement infrastructure directly,
programmatically, and on equal terms.

Any economic effects arising from protocol activity result from
predefined rules and market interaction, rather than from asset
ownership, portfolio management, or profit extraction.

## Klima 2.0

KlimaDAO launched in 2021 on the Polygon blockchain as an early
experiment in applying tokenisation and onchain liquidity to voluntary
carbon markets. The initial design centred on the KLIMA token and a
treasury-based mechanism intended to bootstrap liquidity and
participation in a nascent onchain carbon ecosystem.

That first iteration played a meaningful role in demonstrating that
carbon credits could be represented, transferred, and retired using
blockchain infrastructure. It also catalysed the development of a
broader ecosystem of tools and services, including integrations with
multiple carbon registries, marketplaces and point-of-sale interfaces,
APIs for third-party applications, and direct onchain issuance by
project developers.

Over time, it became clear that the original architecture was not well
suited to serving large-scale, enterprise carbon buyers or to supporting
continuous, rules-based market operation without manual intervention. In
particular, treasury-centric designs introduced complexity, opacity, and
governance challenges that limited scalability and operational clarity.

Klima 2.0 is a ground-up redesign informed by these lessons. Rather than
relying on treasury management or discretionary allocation, the new
protocol is structured as neutral, non-extractive market infrastructure
focused exclusively on facilitating carbon retirement through
transparent pricing, programmatic settlement, and open participation.

The Klima 2.0 protocol replaces treasury-backed mechanisms with a
rules-based coordination model that uses protocol-native tokens to
parameterise execution rates, intake capacity, and participation
incentives. Carbon credits handled by the protocol are acquired solely
to fulfil retirement demand and are not held, traded, or managed for
financial gain.

This shift reflects a deliberate move away from capital-centric designs
toward infrastructure that prioritises auditability, predictability, and
long-term operational resilience. Klima 2.0 is intended to function as a
shared execution layer for carbon markets, enabling suppliers, buyers,
and integrators to interact under predefined conditions without reliance
on discretionary intermediaries.

### Protocol Tokens

Klima 2.0 operates using two protocol-native tokens, **kVCM** and
**K2**, which together enable rules-based coordination and participation
within the system. These tokens do not confer ownership rights,
redemption rights, or claims on protocol-handled carbon, and do not
represent investment interests.

**kVCM** functions as the internal unit of account and pricing reference
for protocol-facilitated carbon retirement, while **K2** provides
signalling inputs related to system capacity. Both tokens are used
exclusively to parameterise protocol behaviour through deterministic
smart-contract logic.

**kVCM** tokens set core allocation choices, whereas **K2** acts as the
calibration mechanism for inventory development.

### High-Level Architecture

Klima 2.0 is composed of three interdependent functional layers that
together support continuous, non-discretionary operation:

1.  **Carbon Inventory Layer**:

    - Accumulates carbon credits by minting **kVCM**.
    - Sells carbon certificates by burning **kVCM**.
    - Sets carbon execution rates based on the system’s code.

    Carbon credits handled by the protocol cannot be withdrawn,
    transferred, or resold. They may only be retired.

2.  **Governance Layer**:

    - **kVCM** holders may **time-lock** their **kVCM** for a fixed time
      period and become eligible to select carbon assets for the
      inventory.
    - This action creates a **kVCM** Base Accrual curve, which is
      distributed to the time-locked holders. This is utilised to derive
      discount rates and governance weightings.

3.  **Liquidity Layer**:

    - **kVCM** and **K2** holders are able to pair their tokens
      together, or in the case of **kVCM** with USDC, in order to
      generate liquidity fees in the standard way.
    - Staking the resulting liquidity provider tokens may generate a
      share of protocol incentives.
    - Liquidity locked in the **kVCM**/**K2** liquidity pool
      participates in general governance alongside time-locked **kVCM**
      holders.

These layers operate together as a self-contained system that responds
only to its own observable state, without reliance on external oracles
or centralised intervention.

### Incentives and Participation

The protocol issues incentives to participants who provide defined
services necessary for system operation.

#### kVCM Incentives

**kVCM** incentives are continuously emitted to:

1.  Time-locked **kVCM** (‘**kVCM** Base Accrual’).

2.  User-locked **K2**.

3.  Both **kVCM** and **K2** liquidity providers.

#### K2 Incentives

The supply of K2 is allocated at various rates, depending on overall
system balances:

1.  Time-locked **kVCM**.

2.  User-locked **K2**.

3.  Both **kVCM** and **K2** liquidity providers.

### Carbon Inventory

The protocol’s carbon inventory layer accumulates and retires carbon. It
is driven by parameters determined by its rules-based smart contracts,
and user activities.

<div id="fig-carbon-inventory">

![](figures/carbon-inventory.svg)

Figure 1: Klima 2.0 Carbon Inventory.

</div>

Carbon credits are acquired from suppliers, and consumed by offset
buyers. Carbon credits are grouped by pre-defined classifications called
**carbon classes**.

Aggregate token holder allocations collectively set the parameters for
the execution rates of **each class** for, both suppliers and retirees,
by defining:

- Inventory weighting.

- Capacity.

Additional **global** parameters are also determined by the aggregate
allocations, including the **kVCM** incentive curve.

Thus the Protocol is driven in response to its own native token
balances, acting as rules-based carbon market infrastructure to connect
available supply with retirement demand. It is able to do so without
using oracles or external inputs, and without discretionary allocation,
resale, or optimisation of inventory.

### Tokens

Locking or staking the protocol’s tokens allows participants to signal
preferences within the system. Doing so may make them eligible for
protocol incentives when they perform defined coordination functions.

Holding or locking protocol tokens does not represent ownership of
protocol carbon assets, profit participation, or direct exposure to
carbon price movements.

Together, **kVCM** and **K2** enable the protocol to operate as neutral,
non-extractive infrastructure, coordinating participation and execution
without discretionary management.

#### kVCM

**kVCM** is the protocol’s primary utility token. Its supply is <u>not
capped</u>: it grows when new carbon is supplied to the protocol, and
contracts when it is retired.

- When **time-locked**:

  - It may vote for carbon classes for inventory weighting.

  - It receives **kVCM** base accrual and **K2** incentives.

  - In aggregate, time-locks determine the rate of incentive issuance.

- **Transactional** usage:

  - **Mint**: when suppliers deliver carbon to the protocol.

  - **Burn**: when credits are retired from the protocol.

- When **staked** in liquidity pools it is also eligible for incentives,
  based on the position’s relative share of the pool.

<div id="fig-token-utility">

![](figures/token-utility.svg)

Figure 2: Token utility.

</div>

#### K2

**K2** is a <u>fixed-supply</u> token distributed programmatically over
time.

- When **user-locked**:

  - It may vote for carbon classes to reduce the difference between
    execution terms on carbon intake and retirements.

  - It receives **kVCM** and **K2** incentives.

  - In aggregate, user-locks influence the rates of incentive issuance.

- When **staked** in the kVCM/K2 liquidity pool it is also eligible for
  incentives, based on the position’s relative share of the pool.

#### Utility Functions

The **kVCM** token has <u>two</u> utility functions which are not
independent:

<div id="fig-kvcm-utility">

![](figures/kvcm-utility.svg)

Figure 3: **kVCM** utility functions.

</div>

1.  **Time lock**: The **kVCM** token is locked for a specific period of
    time which determines a kVCM ‘base accrual’ rate. This cannot be
    amended.

2.  **Execution rate allocation**: Collective signalling of carbon
    classes via **kVCM** allocations determines determines the
    protocol’s execution rate for carbonintake and retirement, expressed
    in kVCM units. These parameters govern how the protocol issues or
    burns kVCM when carbon is supplied or retired. Allocations may be
    updated over time.

The **K2** token also has <u>two</u> utility functions:

1.  **User lock**: The **K2** token remains locked for at least 24
    hours.

2.  **Capacity allocation**: Collective selection of carbon classes via
    K2 allocations determines the protocol-defined execution capacity
    for carbon intake and retirement operations for a given class.
    Higher capacity allocations increase the system’s ability to process
    additional carbon activity without materially altering the execution
    rate, as defined by kVCM allocations.

Both tokens support the operation of the infrastructure, with**kVCM**
informing execution rateios, and the **K2** token modulating capacity.

### Token Initialisation

There is an initial issuance of tokens at the genesis of Klima 2.0. All
future emissions are distributed autonomously via incentives.

<div id="tbl-token-summary">

<table class="column-body-outset">
<colgroup>
<col style="width: 10%" />
<col style="width: 15%" />
<col style="width: 75%" />
</colgroup>
<thead>
<tr>
<th style="text-align: left;">Token</th>
<th style="text-align: left;">Supply</th>
<th style="text-align: left;">Notes</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: left;"><strong>kVCM</strong></td>
<td style="text-align: left;">20 million</td>
<td style="text-align: left;"><ul>
<li>Supply expands and contracts programmatically in response to carbon
intake and retirement activity.</li>
<li>A portion of the initial supply is allocated to existing KLIMA
holders.</li>
</ul></td>
</tr>
<tr>
<td style="text-align: left;"><strong>K2</strong></td>
<td style="text-align: left;">100 million</td>
<td style="text-align: left;"><ul>
<li>Fixed supply.</li>
<li>Distributed programatically over time, with a portion allocated to
existing KLIMA holders.</li>
</ul></td>
</tr>
</tbody>
</table>

Table 1: Token Summary

</div>

### Participants

1.  **Carbon Suppliers & Retirees**

    Participants may supply or retire eligible, tokenised carbon credits
    to the protocol at quoted execution rates. Supplied credits are
    handled solely for retirement and cannot be withdrawn, transferred,
    resold or otherwise arbitraged.

    **Carbon inventory**: Indicative excution rates for suppliers and
    retirees are continuously updated based on protocol state.

2.  **Liquidity Providers**

    Participants may provide liquidity in supported token pairs to
    facilitate entry and exit from the system. Liquidity provision
    supports continuous execution and is incentivised according to
    predefined protocol rules.

    **Staked liquidity**: Protocol incentives may be issued for
    participants providing liquidity to support system operation.

3.  **Coordinators**

    Participants may influence execution conditions by allocating
    **kVCM** and **K2** tokens within pre-defined protocol parameters.

    **Time locks & user locks**: Protocol incentives may be issued for
    those contributing activities that coordinate the protocol and
    signal long-term participation.

### Protocol Design Principles

1.  **Infrastructure, Not Extraction**:

    Klima 2.0 is designed as shared market infrastructure rather than an
    extractive financial product. The protocol does not charge fees,
    take hidden spreads, or operate profit-taking mechanisms for any
    sponsor, foundation, or investor. All protocol behaviour is
    rules-based and applies uniformly to all participants, with no
    privileged economic positions or revenue capture layers.

    **Design intent**: Reduce opaque intermediation and hidden margins
    common in carbon markets, not replace them with a new rent-seeking
    intermediary.

2.  **Consumption-only Carbon Access**:

    Carbon credits handled by the protocol are not exposed for resale,
    speculation, or secondary trading. Once accepted by the protocol,
    credits may only be accessed for irreversible retirement through
    protocol-defined processes.

    **Design intent**: Align the system with carbon’s end use
    (retirement), rather than treating credits as financial instruments.

3.  **Coordination Through Signalling**:

    Protocol tokens do not represent ownership of carbon, claims on
    protocol-held assets, or entitlement to surplus value. Instead,
    tokens function as signalling and coordination inputs that influence
    protocol parameters (such as execution conditions and capacity)
    within predefined bounds.

    **Design intent**: Enable decentralised coordination in a complex
    and competitive environment.

4.  **Autonomous, Rules-based Operation**

    All protocol behaviour is governed by deterministic smart contracts.
    Once deployed, the system operates autonomously and does not rely on
    discretionary decisions by any individual, committee, or
    organisation.

    **Design intent**: Build a trustless, auditable system, that is not
    based on subjective, opaque intervention.

5.  **Equal Access and Uniform Treatment**

    All participants interact with the protocol on identical terms.
    There are no side agreements, preferential execution paths,
    differentiated rights, or bespoke economic arrangements. Protocol
    rules apply uniformly to all users, including the protocol’s
    creators and affiliated entities.

    **Design intent**: Ensure credibility, neutrality, and resistance to
    capture.

6.  **Market-driven Outcomes, Not Managed returns**

    Any economic effects associated with protocol participation arise
    solely from predefined rules and participant interaction with the
    system. The protocol does not manage assets on behalf of users,
    target returns, or seek to optimise outcomes for any class of
    participant.

    **Design intent**: Enable transparent market coordination without
    positioning the protocol as an asset manager or investment vehicle

## Core Protocol Layers

From this section we refer to **kVCM** tokens as **A**, **K2** tokens as
**G**, USDC tokens as **Q**, carbon credits as **C**, and carbon offset
certificates as **C\***.

Three layers enable the Klima Protocol to find equilibrium through
continuous, rule-based feedback mechanisms representing system
state (supply, demand, coordinator allocations). There is no centralised
management entity with discretionary powers, or fees that can be turned
on.

1.  **Time-locking mechanics**: **A** token holders can time-lock their
    tokens until a set date to influence system parameters and to have
    the ability to select carbon classes for system weighting.

    - The collective locks influence the **A** incentives, as well as
      the real-time execution price for carbon credit acquisitions or
      retirements.

2.  **Carbon inventory layer**: the protocol swaps **A** for carbon
    credits **C** (in) or carbon offset certificates **C\*** (out).

    - Both allocations of time-locked **A** tokens and user-locked **G**
      tokens are used in the protocol: allocations of **A** determine
      the execution rates of carbon, and allocations of **G** determine
      capacity.

3.  **Liquidity layer**: External liquidity pools enable conversion
    between **kVCM** and supported settlement assets. Liquidity
    provision supports system availability and may make participants
    eligible for protocol incentives.

    - <span class="overline">**AG**</span> liquidity pool: Native token
      swap **A** and **G**.

    - <span class="overline">**AQ**</span> liquidity pool: The asset
      token **A** with USDC **Q**.

The Klima system enables each participant to contribute to various
aspects of the model, in the interests of their own use and preference.
This, in conjunction with the autonomous model, enables the protocol to
fulfill continuous carbon retirement activity within the carbon markets.

### Time-locking Mechanics

Time-locking **A** tokens represents a commitment to protocol
participation for a fixed duration. Lock durations are standardised at
90 days increments and expire on a rolling schedule. There are always 40
durations, extending out to approximately 10 years.

- **Discount curve**: Aggregate time-locking determines the shape of the
  discount curve of the **A** token.

- **Incentives**: Time-locked **A** tokens may receive incentives, with
  a rate determined by the base accrual. The base accrual is calculated
  daily based on user positions, via the ‘time-weighted incentive
  curve’.

- **Locks**: Time-locked tokens and any associated **A** incentives are
  released only upon time-lock expiration. Early exit is not possible.

**G** tokens are <u>not</u> involved in the time-locking mechanics. The
discount curve is agnostic to carbon class although only time-locked
**A** token holders can allocate their token to carbon classes for
portfolio pricing.

#### Time-weighted Incentive Curve

Defining:

- $S$: Total time-locked **A** tokens expressed as a proportion of the
  outstanding supply of **A**.

- $S_t$: Total **A** tokens time-locked in bucket $t$, expressed as a
  proportion of the outstanding supply of **A**, where ${\sum S_t = S}$,
  and $t$ is the index of standard durations
  $t \in \{1, 2, 3, \dots, 40\}$.

- $E_t$: Duration expressed in years.

Calculating curve parameters $D$ and $C$:

<span id="eq-curve-parameter-d">$$
D = \frac{1}{S} \sum_{t=1}^{40} S_t \, E_t
 \qquad(1)$$</span>

<span id="eq-curve-parameter-c">$$
C = \frac{1}{S} \sum_{t=1}^{40} S_t \, E_t^2
 \qquad(2)$$</span>

The shape of the time-weighted incentive curve is produced:

<span id="eq-time-weighted-incentive-curve-shape">$$
\gamma_t = \max \left( \frac{E_t}{D} - \frac{E_t^2}{2 \, C}, \, 0 \right)
 \qquad(3)$$</span>

Normalising $\gamma_t$ to $\hat \gamma_t$:

<span id="eq-time-weighted-incentive-curve-normalised">$$
\hat \gamma_t = \frac{\gamma_t}{\sum_{t=1}^{40} \gamma_t}
 \qquad(4)$$</span>

With the cumulative sum of the normalised values expressed as
$\Gamma_t$:

<span id="eq-time-weighted-incentive-curve-normalized-sum">$$
\Gamma_t = \sum_{i=1}^t \hat \gamma_i \quad \text{for } t = 1, \dots, 40
 \qquad(5)$$</span>

The time-weighted incentive curve $Z_t$ is solved:

<span id="eq-time-weighted-incentive-curve">$$
Z_t = (1 - S) \, \frac{\Gamma_t}{E_t}
 \qquad(6)$$</span>

Whereupon, the discount rate $B_t$ that forms the discount curve is
derived:

<span id="eq-discount-rate">$$
B_t = \exp(-Z_t \, E_t)
 \qquad(7)$$</span>

The incentives due on time-locked **A** tokens are calculated daily and
added to the locked balance, hence the daily accrual for each duration
is calculated:

<span id="eq-daily-time-weighted-incentives">$$
Y_t = \exp \left( \frac{Z_t}{365} \right) - 1
 \qquad(8)$$</span>

Hence, any time-locked **A** stake $S_t$ will increase by a base accrual
$\Delta S_t$:

<span id="eq-base-accrual">$$
\Delta S_t = S_t \, Y_t
 \qquad(9)$$</span>

With the total **A** tokens created on a daily basis for time-locked
inflation as

<span id="eq-inflation">$$
R = \sum_{t=1}^{40} \Delta S_t
 \qquad(10)$$</span>

<div class="panel-sidebar">

</div>

<div class="panel-fill">

<div id="fig-time-locked-incentives-example">

<div id="fig-time-locked-incentives-example-curve">

<img src="figures/time-locked-incentives-example-curve.svg"
data-fig-alt="Time-weighted incentives (Total Stake = 55.00%, Inflation = 1.75%)."
data-ref-parent="fig-time-locked-incentives-example" />

(a) Time-weighted incentives (Total Stake = 55.00%, Inflation = 1.75%).

</div>

<div id="fig-time-locked-incentives-example-discount-rates">

<img src="figures/time-locked-incentives-example-discount-rates.svg"
data-fig-alt="Discount rates."
data-ref-parent="fig-time-locked-incentives-example" />

(b) Discount rates.

</div>

Figure 4: Example of time-locked incentives.

</div>

</div>

For visualising the sensitivity of overall **A** inflation rates with
respect to staking and duration,
<a href="#fig-inflation-rate" class="quarto-xref">Figure 5</a> assumes a
single duration over the staking range to provide an approximation of
inflation $\Delta S \approx Z \, S$.

<div id="fig-inflation-rate">

![](figures/inflation-rate.svg)

Figure 5: **A** inflation rate from base accrual $\Delta S$.

</div>

#### Protocol Governance Signals

Protocol governance signals can be derived from two participation
cohorts:

1.  Time-locked **A** tokens: $S_t$

2.  Staked liquidity in the **A**-**G** pair
    <span class="overline">**AG**</span> (see
    <a href="#sec-liquidity-markets" class="quarto-xref">Section 3.3</a>),
    defined here as $A_{Gt}$, representing the quantity of **A** tokens
    held in the liquidity pool expressed as a proportion of circulating
    supply.

Voting power is allocated by time and applied to the respective balance
of **A**:

1.  Initial voting weights for time-locked **A** tokens $v_t$:

    <span id="eq-voting-weights-time-locks-initial">$$
     v_t = Z_t \, S_t
      \qquad(11)$$</span>

2.  Initial voting weights for staked liquidity $w_t$:

    <span id="eq-voting-weights-lps-initial">$$
     w_t = Z_t \, A_{Gt}
      \qquad(12)$$</span>

3.  Final voting weights for time-locked **A** tokens $V_t$:

    <span id="eq-voting-weights-time-locks">$$
     V_t = \frac{v_t}{\sum_{j=1}^{40} (v_j + 2 w_j)}
      \qquad(13)$$</span>

4.  Final voting weights for staked liquidity $W_t$:

    <span id="eq-voting-weights-lps">$$
     W_t = \frac{w_t}{\sum_{j=1}^{40} \left( \frac 1 2 v_j + w_j \right)}
      \qquad(14)$$</span>

### Carbon Inventory Mechanics

The carbon inventory layer ultimately swaps carbon through a set of
smart contracts, driven by carbon supply, demand, and user-inputs. The
combined allocations of **A** and **G** tokens creates a dynamic
real-time execution price curve by carbon class.

<div id="fig-carbon-inventory-mechanics">

![](figures/carbon-inventory-mechanics.svg)

Figure 6: Klima 2.0 carbon inventory mechanics.

</div>

#### Carbon Supply

*User swaps carbon credits for **A** tokens.*

##### Existing Carbon in the Inventory

For carbon pricing, both **A** tokens and **G** tokens may be allocated
to specific carbon classes ${i \in \{1, 2, 3, \dots, n\}}$ and these are
independent allocations between the two tokens.

<div id="fig-token-staking-class-structure">

![](figures/token-staking-class-structure.svg)

Figure 7: Token staking class structure.

</div>

For a carbon class quantity to be supplied to the protocol, it must have
a strictly positive quantity of **A** tokens allocated to that carbon
class, otherwise there is no price, and the carbon cannot be sold.

Defining:

- $C_i$: Total tonnes of carbon class $i$ currently held in the
  inventory.

- $A_i$: **A** tokens allocated to carbon class $i$ expressed as a
  proportion of the outstanding supply of **A** tokens, where
  ${\sum A_i = A}$.

- $G_i$: **G** tokens allocated to carbon class $i$ expressed as a
  proportion of the outstanding supply of **G** Tokens.

Where $\Delta C_i$ is expressed as the relative increment to its
respective pool balance, the amount of **A** tokens issued to pay for
carbon, $\Delta A$, expressed as a proportion of current supply, is
determined as:

<span id="eq-a-change-intermediary-step">$$
\ln(1 + \Delta A) =
  \left( A_i - \frac{A_i^2 \, (1 - G_i)^2}{2} \right) \ln(1 + \Delta C_i)
 \qquad(15)$$</span>

Denoting the expression on the right hand side of
<a href="#eq-a-change-intermediary-step"
class="quarto-xref">Equation 15</a> as $\mathsf{RHS}$:

<span id="eq-a-change">$$
\Delta A = \exp(\mathsf{RHS}) - 1
 \qquad(16)$$</span>

Finally, $\Delta A$ is applied to the outstanding supply of **A** to
solve for token quantities.

<a href="#fig-a-price-curves" class="quarto-xref">Figure 8</a>
illustrates the **G** token’s capacity to maintain the initial execution
terms of the **A** token. The data has been normalised in
<a href="#fig-a-price-curves-normalised"
class="quarto-xref">Figure 9</a> to $\Delta C_i \, A_i$.

<div class="panel-sidebar">

</div>

<div class="panel-fill">

<div id="fig-a-price-curves">

![](figures/a-price-curves.svg)

Figure 8: **A** price curves ($\Delta A$).

</div>

<div id="fig-a-price-curves-normalised">

![](figures/a-price-curves-normalised.svg)

Figure 9: Normalised **A** price curves.

</div>

</div>

Noting that the sensitivity to $G_i$ increases as $A_i$ increases and
the effects become more pronounced as $\Delta C_i$ increases.

##### Zero Carbon Scenario

There are circumstances when there is zero carbon held in the inventory
for a particular class, i.e. ${C_i = 0}$, which invalidates the
calculation of $\Delta C_i$ and a different approach is required.

Taking $\Delta C_\emptyset$ as the tonnes of carbon tokens (implying an
existing balance of 1 tonne) to be supplied for any carbon class that
has a strictly positive **A** allocation $A_\emptyset$, together with
**G** allocation $G_\emptyset$:

<span id="eq-a-change-zero-carbon">$$
\Delta A =
  \frac{\Delta C_\emptyset}{1 + \Delta C_\emptyset} \,
  \left( A_\emptyset - \frac{A_\emptyset^2 (1 - G_\emptyset)^2}{2} \right)^2
 \qquad(17)$$</span>

<div class="panel-sidebar">

</div>

<div class="panel-fill">

<div id="fig-a-price-curves-zero-carbon">

![](figures/a-price-curves-zero-carbon.svg)

Figure 10: **A** price curves ($\Delta A$) in the zero carbon scenario.

</div>

<div id="fig-a-price-curves-zero-carbon-normalised">

![](figures/a-price-curves-zero-carbon-normalised.svg)

Figure 11: Normalised **A** price curves in the zero carbon scenario.

</div>

</div>

#### Carbon Credit Retirements

*User swaps **A** tokens for carbon offset certificates.*

##### Weighted Carbon Class

For retiring carbon that is *weighted*, that is for which there is a
strictly positive **A** token allocation, an **A** token holder can
extract the carbon class offset certificate of their choice $C_i$:

<span id="eq-carbon-change-intermediary-step">$$
\ln(1 + \Delta C_i) =
  \frac{-\ln(1 + \Delta A)}{A_i + \frac 1 2 A_i^2 \, (1 - G_i)^2}
 \qquad(18)$$</span>

As before, denoting the expression on the right hand side of
<a href="#eq-carbon-change-intermediary-step"
class="quarto-xref">Equation 18</a> as $\mathsf{RHS}$:

<span id="eq-carbon-change">$$
\Delta C_i = \exp(\mathsf{RHS}) - 1
 \qquad(19)$$</span>

<div class="panel-sidebar">

</div>

<div class="panel-fill">

<div id="fig-proportion-of-carbon-retired">

![](figures/proportion-of-carbon-retired.svg)

Figure 12: Proportion of carbon retired.

</div>

</div>

<a href="#fig-proportion-of-carbon-retired"
class="quarto-xref">Figure 12</a> shows the cost of carbon increasing
with $A_i$ and decreasing on $G_i$.

##### Unweighted Carbon Class

An offset certificate for a carbon class with a zero **A** allocation
cannot be extracted from the portfolio by swapping in **A** tokens.

##### Round Trip Difference

Any difference between the **A** tokens issued in connection with carbon
intake and the **A** tokens burned in connection with retirement is
reflected solely as a change in the circulating supply of **A** tokens,
according to the above protocol rules. No margin, profit, or financial
surplus is retained or extracted by any entity.

<a href="#fig-carbon-difference" class="quarto-xref">Figure 13</a> below
shows the difference captured on a ‘round trip’ by the system where
$\varepsilon$ is the proportion retained:

<div class="panel-sidebar">

</div>

<div class="panel-fill">

<div id="fig-carbon-difference">

![](figures/carbon-difference.svg)

Figure 13: Carbon ‘difference’.

</div>

</div>

<a href="#fig-carbon-difference-components"
class="quarto-xref">Figure 14</a> shows the component difference
contributions on a carbon supply and purchase round trip of a carbon
offset certificate.

<div class="panel-sidebar">

</div>

<div class="panel-fill">

<div id="fig-carbon-difference-components">

<div id="fig-carbon-difference-component-delta-a">

<img src="figures/carbon-difference-component-delta-a.svg"
data-fig-alt="Carbon Difference Component Delta A."
data-ref-parent="fig-carbon-difference-components" />

(a) Carbon ‘difference’ component $\Delta A$.

</div>

<div id="fig-carbon-difference-component-delta-c">

<img src="figures/carbon-difference-component-delta-c.svg"
data-fig-alt="Carbon Difference Component Delta C."
data-ref-parent="fig-carbon-difference-components" />

(b) Carbon ‘difference’ component $\Delta C$.

</div>

Figure 14: Carbon ‘difference’ components.

</div>

</div>

### Liquidity Markets

Both **A** and **G** tokens can be used for providing liquidity.

<div id="fig-token-liquidity">

![](figures/token-liquidity.svg)

Figure 15: Token liquidity and pricing structure.

</div>

There are two core liquidity pools:

1.  An AAM 50:50 pairing of **A** and **G** tokens: pool
    <span class="overline">**AG**</span>.

2.  A hard currency USDC denoted as **Q** paired with **A**: pool
    <span class="overline">**AQ**</span>.

#### Liquidity Fees

The <span class="overline">**AQ**</span> pool will have its own set of
fees in the normal way.[^1]

The <span class="overline">**AG**</span> pool has different economics as
the assets are highly correlated since they represent the same economy.
For this reason, the fees are extremely low.

By staking liquidity (liquidity provider tokens) to the **standard
maturities**, both pools may receive a distribution of **A** tokens
determined from the Risk Premium calculation below. This is an
<u>additional</u> primary issuance to the Base Accrual already
discussed.

#### Risk Premium: Beta Determination

We can consider the Time-Locked Market yield as the system’s *risk-free*
rate. In addition to this mechanism, a *risky* spread is determined that
is ultimately paid to the staked liquidity providers of the **A** and
**G** tokens as compensation for the risk levels assumed.

As we have seen, the **G** token has an impact on risk-pricing of **A**.
As **G** staking increases, the relationship between the carbon class
selected under $G_i$ and the portfolio token **A** strengthens. We can
consider $G_i$ staking as an estimate of residual or idiosyncratic risk
in the carbon class and this allows us to calculate a portfolio beta
$\beta$ from the implied betas of each carbon class $i$.

<span id="eq-beta">$$
\beta = \sqrt{\sum_{i=1}^n A_i - A_i \, (1 - G_i)^2}
 \qquad(20)$$</span>

The portfolio $\beta$ determines a yield factor for the liquidity pools
of **A** to compensate for the implied risk levels.

For intuition, the map in
<a href="#fig-range-of-beta-i" class="quarto-xref">Figure 16</a> shows
the various outputs of the function per carbon class.

<div id="fig-range-of-beta-i">

![](figures/range-of-beta-i.svg)

Figure 16: Range of $\beta_i$.

</div>

The table and figure below show an example of the effects on $\beta$ of
allocating large $G_i$ values to small $A_i$ values where the shift in
$G_i$ results in a lower $\beta$ (0.27 from 0.55) with no change to
total **G** and **A** allocations.

<div id="tbl-effect-on-beta-from-outsized-g-staking">

| Class | 1 | 2 | 3 | 4 | $\beta$ |
|:---|:---|:---|:---|:---|:---|
| $A_i$ | 0.50 | 0.20 | 0.10 | 0.05 |  |
| Initial $G_i$ | <span class="blue">0.30</span> | <span class="blue">0.10</span> | <span class="blue">0.05</span> | <span class="blue">0.01</span> |  |
| Initial $\beta_i^2$ | 0.2550 | 0.0380 | 0.0098 | 0.0010 | <span class="blue">0.5511</span> |
| New $G_i$ | <span class="red">0.01</span> | <span class="red">0.05</span> | <span class="red">0.10</span> | <span class="red">0.30</span> |  |
| New $\beta_i^2$ | 0.0100 | 0.0195 | 0.0190 | 0.0255 | <span class="red">0.2719</span> |
| $\Delta G_i$ | (0.29) | (0.05) | 0.05 | 0.29 |  |
| $\Delta \beta_i^2$ | (0.2451) | (0.0185) | 0.0092 | 0.0245 |  |

Table 2: Effect on $\beta$ from outsized **G** allocation.

</div>

<div id="fig-example-of-g-stake-on-beta">

![](figures/example-of-g-stake-on-beta.svg)

Figure 17: Example of **G** allocation on $\beta$.

</div>

<a href="#fig-example-of-g-stake-on-beta"
class="quarto-xref">Figure 17</a> shows $\beta$’s sensitivity to **G**
allocation as a function of **A** allocation; that is to say that a
large $G_i$ stake on a small $A_i$ stake has limited
effects (notwithstanding other consequential factors).

#### Allocation of Risk Premium

The full issuance of **A** tokens is depicted below including now the
Risk Premium for the liquidity pools accordingly.

<div id="fig-a-token-flow-structure">

![](figures/a-token-flow-structure.svg)

Figure 18: **A** token flow structure.

</div>

#### Share of Risk Premium

The Risk Premium allocation is shared between user-locked **G** tokens,
<span class="overline">**AG**</span>. and
<span class="overline">**AQ**</span> pools, with shares $\lambda_{GG}$,
$\lambda_G$, and $\lambda_Q$ respectively.

Defining:

- $G_G$: Total **G** tokens in the <span class="overline">**AG**</span>
  pool, expressed as a proportion of the outstanding supply of **G**.

- $A_G$: Total **A** tokens in the <span class="overline">**AG**</span>
  pool, expressed as a proportion of the outstanding supply of **A**.

- $A_Q$: Total **A** tokens in the <span class="overline">**AQ**</span>
  pool, expressed as a proportion of the outstanding supply of **A**.

The allocation to user-locked **G** tokens, $\lambda_{GG}$:

<span id="eq-lambda-gg">$$
\lambda_{GG} = \frac{1 - A_Q}{1 + \left( \frac{\sum_{i=1}^{n}{G_i}}{G_G} \right)^2}
 \qquad(21)$$</span>

<div id="fig-g-stake-allocation">

![](figures/g-stake-allocation.svg)

Figure 19: **G** stake allocation (assuming $G_G = 1 - G_i$).

</div>

Noting the relationship between $G$ and $\beta$, and particularly if
$G = 0$, $\beta = 0$.

The residual share, $1 - \lambda_{GG}$, is split between the liquidity
pools:

<span id="eq-lambda-g">$$
\lambda_G = (1 - \lambda_{GG}) \frac{2 A_G}{2 A_G + A_Q \sqrt 2}
 \qquad(22)$$</span>

For completeness:

<span id="eq-lambda-q">$$
\lambda_Q = 1 - \lambda_{GG} - \lambda_G
 \qquad(23)$$</span>

<div id="fig-liquidity-pool-split">

![](figures/liquidity-pool-split.svg)

Figure 20: Liquidity pool split $\lambda_G, \lambda_Q$.

</div>

#### Risk Premium Distribution

For $\lambda_{GG}$, $\lambda_G$, $\lambda_Q$ we apply $\beta$:

<span id="eq-capital-lambda">$$
\Lambda_X = \lambda_X \, \beta, \quad \text{for } X \in \{GG, G, Q\}
 \qquad(24)$$</span>

Taking $b$ as a discount parameter:

<span id="eq-discount-parameter">$$
b = \frac{\sum_1^{40} Z_t \, S_t \, B_t}{\sum_1^{40} Z_t \, S_t }
 \qquad(25)$$</span>

The total Risk Premium tokens $R_\lambda$:

<span id="eq-risk-premium">$$
R_\lambda = b \, R \, (\Lambda_{GG} + \Lambda_G + \Lambda_Q)
 \qquad(26)$$</span>

The allocations of $R_\lambda$ are pro-rata to $\Lambda_{GG}$,
$\Lambda_G$, $\Lambda_Q$, and thereafter:

1.  Locked **G**: $\Lambda_{GG}$ in proportion to **G**.

2.  Locked <span class="overline">**AG**</span>,
    <span class="overline">**AQ**</span> tokens are allocated a
    weighting $G_t$, $Q_t$ depending on their time bucket $t$:

    <span id="eq-risky-premium-weighting-ag-pool">$$
     G_t = \frac{Z_t \, L_{Gt} \, B_t}{\sum Z_t \, L_{Gt} \, B_t}
      \qquad(27)$$</span>

    <span id="eq-risky-premium-weighting-aq-pool">$$
     Q_t = \frac{Z_t \, L_{Qt} \, B_t}{\sum Z_t \, L_{Qt} \, B_t}
      \qquad(28)$$</span>

    Where $L_{Gt}$, $L_{Qt}$ are the proportion of all liquidity locked
    in each time bucket for <span class="overline">**AG**</span> and
    <span class="overline">**AQ**</span> respectively.

Thereafter each time bucket allocation is proportionate to staked
liquidity provider token holdings.

## Klima 2.0 Token Distribution

### Planned Allocations

<div id="tbl-kvcm-token">

| Cohort        | Proportion | Quantity (m) |
|:--------------|-----------:|-------------:|
| Klima Holders |      87.5% |         17.5 |
| DAO/Treasury  |      10.0% |          2.0 |
| 01X           |       2.5% |          0.5 |
| **Total**     | **100.0%** |     **20.0** |

Table 3: **kVCM** token.

</div>

<div id="tbl-k2-token">

| Cohort | Proportion | Quantity (m) | Liquidity |
|:---|---:|---:|:---|
| Klima Holders | 40.0% | 40.0 | Logistic Vesting 48 months |
| Ecosystem Grant | 5.0% | 5.0 | Logistic Vesting 48 months |
| Programmatic Incentives | 40.0% | 40.0 | Incentive Curve |
| pKlima Holders | 3.0% | 3.0 | Logistic Vesting 48 months |
| DAO/Treasury | 4.5% | 4.5 | 24 month locked LP of <span class="overline">**AG**</span> |
| 01X | 2.5% | 2.5 | 24 month locked LP of <span class="overline">**AG**</span> |
| Product Design and Development | 5.0% | 5.0 | Logistic Vesting 48 months |
| **Total** | **100.0%** | **100.0** |  |

Table 4: **K2** token.

</div>

<div id="fig-k2-token-allocations">

![](figures/k2-token-allocations.svg)

Figure 21: **K2** token allocations.

</div>

### Programmatic Incentive Curve

The incentive issuance is built on a logistic function,
$\operatorname{P}$, to generate total proportion of supply in issue. It
is calibrated from the initial issuance at TGE $P_0$ and the inflection
point time $T$ where 50% of **G** token incentives have been released.

Setting $x_0$ from the initial supply parameter:

<span id="eq-incentives-issuance-x-0">$$
x_0 = \ln\left( \frac{P_0}{1 - P_0} \right)
 \qquad(29)$$</span>

With $x_t$ at time point $t \in (0, \infty)$:

<span id="eq-incentives-issuance-x-t">$$
x_t = x_0 \, \left( 1 - \frac t T \right)
 \qquad(30)$$</span>

Giving supply function $\operatorname{P}(t)$ as:

<span id="eq-incentives-issuance-curve">$$
\operatorname{P}(t) = \frac{\exp(x_t)}{\exp(x_t) + 1}
 \qquad(31)$$</span>

$P_0$ set at 7% and $T$ at 24 months:

<div class="panel-sidebar">

</div>

<div class="panel-fill">

<div id="fig-incentive-issuance">

![](figures/incentive-issuance.svg)

Figure 22: Incentive Issuance

</div>

<div id="fig-k2-token-supply-circulating">

![](figures/k2-token-supply-circulating.svg)

Figure 23: **K2** token circulating supply over time.

</div>

<div id="fig-k2-token-supply-total">

<div id="fig-k2-token-supply-total-stacked">

<img src="figures/k2-token-supply-total-stacked.svg"
data-fig-alt="Total Supply (Stacked)."
data-ref-parent="fig-k2-token-supply-total" />

(a) Total supply (stacked).

</div>

<div id="fig-k2-token-supply-total-unstacked">

<img src="figures/k2-token-supply-total-unstacked.svg"
data-fig-alt="Total Supply (Unstacked)."
data-ref-parent="fig-k2-token-supply-total" />

(b) Total supply (unstacked).

</div>

Figure 24: **K2** token total supply over time.

</div>

<div id="fig-k2-risk-metrics">

<div id="fig-k2-risk-metrics-differential">

<img src="figures/k2-risk-metrics-differential.svg"
data-fig-alt="Total supply differential (stacked)."
data-ref-parent="fig-k2-risk-metrics" />

(a) Total supply differential (stacked).

</div>

<div id="fig-k2-risk-metrics-yield">

<img src="figures/k2-risk-metrics-yield.svg"
data-fig-alt="Utility incentive yield."
data-ref-parent="fig-k2-risk-metrics" />

(b) Utility incentive yield.

</div>

Figure 25: **K2** token supply risk metrics.

</div>

</div>

### Incentive Allocations

<div id="fig-k2-incentive-distribution">

![](figures/k2-incentive-distribution.svg)

Figure 26: **K2** token incentive distribution structure.

</div>

The **relative utilisation** measurement factor $\upsilon$ is calculated
as follows.

Defining initially:

- $G$: Total **G** tokens staked expressed as a proportion of the
  circulating supply, $G \in [0, 1]$.

- $L$: Total **G** tokens held in the
  <span class="overline">**AG**</span> pool expressed as a proportion of
  circulating supply, $L \in (0, 1]$.

Where $\upsilon = 0$ if $G + L = 0$, otherwise:

<span id="eq-relative-utilisation">$$
\upsilon = \left( \frac{2 G L}{G^2 + L^2} \right)^2
 \qquad(32)$$</span>

<div id="fig-relative-utilisation">

![](figures/relative-utilisation.svg)

Figure 27: Upsilon $\upsilon$ range of values.

</div>

The **absolute utilisation** parameter $\eta$ is defined as $\eta = 0$
if $G + L = 0$, otherwise:

<span id="eq-absolute-utilisation">$$
\eta = \frac{2 G L}{G (1 - G) + L ( 1 - L)}
 \qquad(33)$$</span>

<div id="fig-absolute-utilisation">

![](figures/absolute-utilisation.svg)

Figure 28: Eta $\eta$ range of values.

</div>

Incentives $I$ are allocated as follows:

#### Treasury

The allocation to the Treasury $I_T$ is the imbalance generated from
$\upsilon$:

<span id="eq-allocation-treasury">$$
I_T = 1 - \upsilon \, \eta
 \qquad(34)$$</span>

#### Post Treasury

The residual post-treasury allocation is shared four ways within 2
buckets:

1.  Time-locked **A** & user-locked **G** tokens

    Where $S$ is the proportion of time-locked **A** tokens (as defined
    previously in <a href="#sec-time-weighted-incentive-curve"
    class="quarto-xref">Section 3.1.1</a>):

    1.  Time-locked **A**, $I_S$:

        <span id="eq-allocation-locked-a">$$
         I_S = S \, \frac{L^2}{G^2 + L^2}
          \qquad(35)$$</span>

    2.  User-locked **G**, $I_G$:

        <span id="eq-allocation-locked-g">$$
         I_G = (1 - S) \, \frac{L^2}{G^2 + L^2}
          \qquad(36)$$</span>

2.  Liquidity

    With $\lambda_G$, $\lambda_Q$, $\lambda_{GG}$ as defined in
    <a href="#sec-share-of-risk-premium"
    class="quarto-xref">Section 3.3.4</a>:

    3.  <span class="overline">**AG**</span> pool $I_{AG}$:

        <span id="eq-allocation-pool-ag">$$
         I_{AG} = \frac{\lambda_G}{1 - \lambda_{GG}} \, \frac{G^2}{G^2 + L^2}
          \qquad(37)$$</span>

    4.  <span class="overline">**AQ**</span> pool $I_{AQ}$:

        <span id="eq-allocation-pool-aq">$$
         I_{AQ} = \frac{\lambda_Q}{1 - \lambda_{GG}} \, \frac{G^2}{G^2 + L^2}
          \qquad(38)$$</span>

<div class="panel-sidebar">

</div>

<div class="panel-fill">

<div id="fig-incentives-non-treasury">

<div id="fig-allocation-token-locks">

<img src="figures/allocation-token-locks.svg"
data-fig-alt="Time-locked A and user-locked G allocations."
data-ref-parent="fig-incentives-non-treasury" />

(a) Time-locked **A** and user-locked **G** allocations.

</div>

<div id="fig-allocation-liquidity-pools">

<img src="figures/allocation-liquidity-pools.svg"
data-fig-alt="Liquidity pools allocations."
data-ref-parent="fig-incentives-non-treasury" />

(b) Liquidity pools allocations

</div>

Figure 29: Share of non-treasury incentives $I_S$, $I_G$, $I_{AG}$ and
$I_{AQ}$.

</div>

</div>

<div id="fig-incentives-treasury">

![](figures/incentives-treasury.svg)

Figure 30: Treasury incentives $I_T$.

</div>

[^1]: Note the development of liquidity pool pricing functionality may
    be applicable.
