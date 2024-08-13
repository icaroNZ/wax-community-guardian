## Bot Commands

Here's a list of possible commands and how to use them:

## Wallet Verification

- `/verify <WAX_address>`: Initiates the wallet verification process. The bot will provide a link to securely log in with your WAX wallet.
- `/wallet`: Displays your currently verified WAX wallet address.

## Wallet Filtering

- `/filter set <criteria> <value>`: Sets a filter criteria for the server. Only admins can use this command.
  - Example: `/filter set min_balance 100` (sets a minimum WAX balance requirement)
- `/filter list`: Lists all active filters for the server.
- `/filter remove <criteria>`: Removes a specific filter criteria.

## Giveaways

- `/giveaway create <prize> <duration> <winners>`: Creates a new giveaway.
  - Example: `/giveaway create "100 WAX" 24h 3` (creates a giveaway for 100 WAX, lasting 24 hours, with 3 winners)
- `/giveaway end <giveaway_id>`: Ends a giveaway early and selects winners.
- `/giveaway list`: Lists all active giveaways in the server.

## Tipping

- `/tip <@user> <amount>`: Sends a tip to the mentioned user.
  - Example: `/tip @Alice 10` (sends 10 WAX to Alice)
- `/balance`: Checks your current WAX balance in the tipping system.
- `/withdraw <amount>`: Withdraws WAX from the tipping system to your verified wallet.
