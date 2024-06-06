# Solidity Token Contract

A Solidity contract for a token with mint and burn functionalities.

## Description

This project implements a basic ERC-20-like token in Solidity, featuring public variables for token details, a mapping for address balances, a mint function to create tokens, and a burn function to destroy tokens. It's a foundational contract for understanding token development on the Ethereum blockchain.

## Getting Started

### Prerequisites

- A Solidity development environment, such as:
  - [Remix IDE](https://remix.ethereum.org/)
  - [Truffle Suite](https://www.trufflesuite.com/)
  - [Hardhat](https://hardhat.org/)

### Installation

1. **Clone the Repository**:
    ```bash
    git clone https://github.com/your-username/solidity-token-contract.git
    cd solidity-token-contract
    ```

2. **Open in Remix IDE**:
    - Open [Remix IDE](https://remix.ethereum.org/).
    - Create a new file named `MyToken.sol`.
    - Copy and paste the contract code into `MyToken.sol`.

### Usage

1. **Deploy the Contract**:
    - Compile the `MyToken.sol` file in Remix.
    - Deploy the contract to a desired network (e.g., JavaScript VM, a local blockchain, or a testnet).

2. **Mint Tokens**:
    - Call the `mint` function to create new tokens and assign them to a specific address.
    - Example:
      ```solidity
      mint(0xYourAddress, 1000);
      ```

3. **Burn Tokens**:
    - Call the `burn` function to destroy tokens from a specific address.
    - Example:
      ```solidity
      burn(0xYourAddress, 500);
      ```

### Example Code

Here's the contract code for reference:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract MyToken {

    // Public variables to store the token details
    string public name = "MyToken";
    string public symbol = "MTK";
    uint256 public totalSupply;

    // Mapping to store balances of addresses
    mapping(address => uint256) public balances;

    // Mint function to create new tokens
    function mint(address _to, uint256 _value) public {
        totalSupply += _value;
        balances[_to] += _value;
    }

    // Burn function to destroy tokens
    function burn(address _from, uint256 _value) public {
        require(balances[_from] >= _value, "Insufficient balance to burn");
        totalSupply -= _value;
        balances[_from] -= _value;
    }
}
