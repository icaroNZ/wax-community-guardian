# Smart Contract

The WAX Discord Bot utilizes a smart contract for secure handling of tokens in the tipping system. Here's an overview of the possible contract's tables and actions:

## Tables

1. `users`
   - Stores user information including Discord ID and WAX address
   - Columns: `discord_id` (primary key), `wax_address`

2. `balances`
   - Tracks user balances in the tipping system
   - Columns: `discord_id` (primary key), `balance`

## Actions

1. `verify`
   - Parameters: `discord_id`, `wax_address`
   - Links a Discord ID with a WAX address after successful verification

2. `deposit`
   - Parameters: `discord_id`, `amount`
   - Increases a user's balance in the tipping system
   - Logs the deposit action on the blockchain

3. `withdraw`
   - Parameters: `discord_id`, `amount`
   - Decreases a user's balance and initiates a transfer to their WAX wallet
   - Logs the withdrawal action on the blockchain

4. `tip`
   - Parameters: `from_discord_id`, `to_discord_id`, `amount`
   - Transfers WAX from one user to another within the tipping system

## Usage

To use these actions:

1. `verify`: This action is called automatically when a user successfully verifies their wallet through the Discord bot.

2. `deposit`: Users can deposit WAX to the contract address. Once confirmed, use this action to credit their account.

3. `withdraw`: Called when a user requests a withdrawal through the Discord bot.

4. `tip`: Automatically called when a user uses the tip command in Discord.
