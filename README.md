# PumpFun Token Launch & Pool Creation

This project allows you to **mint a new token**, **create a liquidity pool** for it on **PumpFun**, and perform an **initial buy** right after creating the pool. The process is automated, and you can customize it using variables defined in the `.env` and the script files.

## Project Structure

1. **`createPool.js`**: Script to create the token and launch the pool on **PumpFun**.
2. **`buy.js`**: Script to perform an initial buy right after creating the pool.
3. **`sell.js`**: Script to sell tokens after the pool has been created.
4. **`.env`**: Configuration file for environment variables (e.g., wallet private key, token metadata, slippage, etc.).
5. **`token-launch-info.json`**: This file saves the pool and token details after pool creation.

## Setup Instructions

### 1. Clone the repository

Clone the repository to your local machine:

```bash
git clone https://github.com/yourusername/pumpfun-token-launch.git
cd pumpfun-token-launch
```

### 2. Install Dependencies

Install the necessary dependencies using npm:

```bash
npm install
```

### 3. Set Up Environment Variables

Copy the .env.example to .env:

```bash
cp .env.example .env
```

Open the .env file and fill in the values:

```env
RPC_URL=
WALLET_PRIVATE_KEY=
NETWORK=

# Variables to create pool
INITIAL_BUY_AMOUNT_SOL=

# Global variables
SLIPPAGE=

# Token MetaData configurations
NAME=
SYMBOL=
IMAGE_URI=
EXTERNAL_URL=
DESCRIPTION=

# For buy/sell transactions
SLIPPAGE=
BUY_AMOUNT_SOL=
SELL_AMOUNT_TOKEN=
```

### 4. Create Token and Launch Pool

Run the createPool.js script to create the token and launch its pool:

```bash
npm run createPool
```

This will:

Mint your token using the name, symbol, and metadata URI.

Create a liquidity pool for your token on PumpFun.

Save the pool information to token-launch-info.json.

### 5. Perform Initial Buy

Once the pool is created, you can perform the initial buy using the buy.js script:

```bash
npm run buy
```

This will:

Buy a specified amount of the token using SOL.

Ensure that the pool has enough liquidity to execute the buy.

### 6. Perform Token Sale

If you wish to sell tokens, use the sell.js script:

```bash
npm run sell
```

This will:

Sell the specified amount of your token for SOL.

## File Descriptions

`.env`
This file contains all the configurable environment variables such as wallet private key, RPC URL, token metadata, and transaction parameters like slippage and amounts for buy/sell transactions.

`token-launch-info.json`
This file stores the token mint address, creator's public key, and other important pool and token details after successfully creating the pool. Here’s an example:

```json
{
  "mint": "9ZJR84ZR8P5Y7QjMbwj8JhA1KV3YcwWxcX9MPEtKeunt",
  "creator": "A1YrqK6SUgr1mKDLx88sy992BCx4EAGSkbAsre34tgPz",
  "signature": "9TjrVMHVhxtk7wKxY9EfZW8GjgPgY3q99yFo1oP7MYHNMRMPyVkcwBNfvcPq464sY6iACxoakrFrSafjkhPFTY9",
  "bondingCurve": {
    "virtualTokenReserves": "1069470394772023",
    "virtualSolReserves": "30099009900",
    "realTokenReserves": "46570394772023",
    "realSolReserves": "99009900",
    "complete": false
  },
  "timestamp": "2025-08-07T10:13:47.455Z",
  "config": {
    "name": "CoolCoin",
    "symbol": "CC",
    "uri": "https://gateway.pinata.cloud/ipfs/bafybeidrscqigi5zoa5trbzt527ovdfkykqg72cfote3lka3ykhkcetnwe",
    "initialBuyAmountSOL": 0.1,
    "slippage": 0.05
  }
}
```

This file is updated after pool creation and includes the mint address, creator's public key, signature, bonding curve details, and token metadata.

### Scripts

#### createPool.js:

This script:

1) Mints the token.
2) Creates a liquidity pool.
3) Sets up the bonding curve with no initial liquidity.
4) Performs the initial buy with the INITIAL_BUY_AMOUNT_SOL.

#### buy.js:

This script:
1) Performs an initial buy of the token using the given SOL amount.

#### sell.js:

This script:
1) Allows the user to sell tokens for SOL after the pool has been created.

### Running the Project
1 Ensure all environment variables are correctly set in the .env file.
2 Run the createPool.js script to create the pool.
3 Run the buy.js script to perform the initial buy.
4 Optionally, run the sell.js script to sell tokens after the pool is created.

### Conclusion

This project allows you to:
1 Mint a new token and create a liquidity pool on PumpFun.
2 Automatically perform an initial buy after creating the pool, with easy-to-define variables in the .env file.
