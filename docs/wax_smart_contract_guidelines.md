# WAX Smart Contract Guidelines for WAX Community Guardian

This document outlines the best practices and guidelines for developing smart contracts for the WAX Community Guardian project. These guidelines are in addition to the [EOSIO Coding Standards](https://developers.eos.io/) and [WAX-CDT Style Guide](https://developer.wax.io/).

## 1. Code Structure and Naming Conventions

- Use camelCase for function names and variables
- Use PascalCase for class and struct names
- Use UPPER_CASE for constants and macros
- Limit line length to 100 characters

## 2. Smart Contract Best Practices

- Use EOSIO macros for example use `ACTION` macro for contract actions instead of `[[eosio::action]]`
- Use inline comments to explain complex logic
- Implement proper error handling and use descriptive error messages

## 3. Security Considerations

- Always include input validation in action methods
- Use `check` for assertions instead of `eosio::check` or `assert`
- Implement proper permission checks using `require_auth`
- Be cautious with `defer` transactions and understand their implications
- Avoid using `tapos_block_prefix()` for randomness; prefer WAX RNG

## 4. Resource Management

- Optimize for CPU and NET usage
- Use `std::string_view` instead of `std::string` where possible
- Prefer stack-allocated variables over heap-allocated ones
- Be mindful of RAM usage in multi-index tables

## 5. Token Handling

- Use `asset` for handling token amounts
- Always specify token precision and symbol in comparisons
- Implement proper balance checks before transfers

## 6. WAX-Specific Features

- Always utilize WAX Random Number Generator for fair randomness
- Implement WAX specific features like NFT support when relevant

## 7. Testing and Deployment

- Test contracts thoroughly on WAX testnet before mainnet deployment
- Document the deployment process and any required permissions

## Example

```cpp
#include <eosio/eosio.hpp>
#include <eosio/asset.hpp>

using namespace eosio;

CONTRACT WaxGuardian : public contract {
public:
    using contract::contract;

    ACTION tip(name from, name to, asset amount) {
        require_auth(from);
        check(from != to, "Cannot tip yourself");
        check(amount.amount > 0, "Must tip a positive amount");
        check(amount.symbol == symbol("WAX", 8), "Only WAX token is supported");

        // Transfer logic here
    }

    ACTION version() {
        return "1.0.0";
    }

private:
    TABLE balance {
        name user;
        asset funds;
        uint64_t primary_key() const { return user.value; }
    };
    typedef multi_index<"balances"_n, balance> balance_table;
};
```

Always refer to the latest WAX documentation and updates from the WAX team for any changes in best practices or new features.