
# Tokenomics Model Documentation

## Key Points

- **Maximum Supply**: The total number of tokens that will ever exist.
- **Circulating Supply**: The number of tokens currently available in the market.
- **Initial Treasury**: Tokens initially set aside for the treasury.
- **PoV Team Pool**: A percentage of the tokens reserved for the Proof of Value (PoV) team.
- **Block Rewards to Treasury**: Percentage of block rewards directed to the treasury for both Proof of Stake (PoS) and PoV.

## Core Elements

- **Total Emissions**: Defined annually, emissions appear to decrease by a set percentage each year, which likely impacts both the staking rewards and treasury allocations.
- **Block Rewards to Treasury**: Specified percentages for both PoS and PoV indicate a certain fraction of the rewards per block allocated to the treasury.
- **PoV Team Pool**: A defined amount and percentage of tokens allocated to the team involved in the Proof of Value operations.
- **Block Time and Total Annual Blocks**: Indicates how often blocks are produced and the total number of blocks per year, which is crucial for understanding the rate of emissions and reward distributions.

## Implementation in Substrate

### Define the Economic Model
Substrate allows for extensive customization of the economic model, including total supply, emissions schedule, and reward mechanisms.

### Implement Staking and Rewards Logic
Substrate's runtime allows for defining custom logic for how tokens are staked and how rewards are calculated and distributed. This involves creating modules (called pallets in Substrate) that handle staking mechanisms, reward calculations, and treasury allocations.

### Use Hooks and Events
Substrate's architecture allows you to use hooks for integrating business logic into block production and finalization processes. This is useful for integrating emissions reductions and reward distributions at the end of each block or epoch.

## Pallet Setup and Initial Configuration

### Pallet Tokenomics
- **Purpose**: To handle the token supply, distribution, and emissions schedule.
- **Key Features**:
  - Define storage items for total supply, circulating supply, and emission details.
  - Functions to handle the emission reductions yearly based on your emissions schedule.

### Pallet Staking
- **Purpose**: To manage staking operations for both PoS and PoV.
- **Key Features**:
  - Staking logic to handle token locking, reward calculation, and distribution.
  - Separate mechanisms for PoS and PoV if their staking logic differs significantly.

### Pallet Treasury
- **Purpose**: To manage treasury funds and allocate them according to predefined rules.
- **Key Features**:
  - Functions to receive a certain percentage of block rewards.
  - Management of treasury funds, including spending proposals and approvals.

## Emissions Calculation
Emissions are the number of new tokens generated and distributed within a specific time frame, typically tied to block creation. If your model specifies an annual reduction in emissions, the calculation would adjust the number of tokens generated each year based on a set percentage.

- **Example**:
  - **Initial Annual Emissions**: 4,750,000 tokens
  - **Annual Reduction**: 12%
  - **Calculation**:
    - For each subsequent year, the emissions would be:
      - `Emissions_year = Emissions_previous_year * (1 - Reduction rate)`
    - For the second year:
      - `Emissions_year2 = 4,750,000 * (1 - 0.12) = 4,180,000`