# Sprout for Claude

Sprout is an AI finance assistant for personal and business finances. This plugin connects Claude to your Sprout account so you can review cash flow, income, expenses, spending categories, merchants and vendors, subscriptions and recurring bills, possible duplicate or unusual charges, and transaction history from the US and Canadian bank and credit card accounts you connected to Sprout.

## What it includes

- A remote MCP server, `https://api-sprout.z4k.app/mcp`, with read-only finance tools (`list_accounts`, `get_cash_flow`, `get_spending_breakdown`, `compare_periods`, `search_transactions`, `get_recurring_charges`, `find_unusual_transactions`, and others) plus `update_settings`, which saves your default reporting period.
- Four skills: `get-started`, `money-review`, `subscription-review`, and `charge-review`.

## Requirements

A Sprout account (sign in with Google, Apple, or email) and a supported US or Canadian bank connected through Plaid in the Sprout app at https://app-sprout.z4k.app.

## Install

```
claude plugin marketplace add MindCraftersGroup/sprout-claude-plugin
claude plugin install sprout-finance@mindcrafters
```

The first tool call asks you to connect Sprout. Claude signs you in through Sprout's OAuth server (WorkOS AuthKit); no credentials are stored in this plugin.

## Data and network access

- Claude sends tool requests, including the dates, accounts, categories, and search text you ask about, to `https://api-sprout.z4k.app/mcp` with your OAuth access token. The server returns balances, transactions, and summaries from your own Sprout account only.
- In Claude apps that render MCP Apps, `open_sprout` shows the Sprout web app from `https://app-sprout.z4k.app` beside the conversation. That view reports errors to Sprout's GlitchTip instance at `https://glitchtip.mindcrafters.group`.
- Bank access is read-only. Sprout cannot move money, pay bills, cancel subscriptions, dispute charges, or execute trades.
- Transaction descriptions come from banks and are treated as data, never as instructions.

## Support

- Support: https://sprout.z4k.app/support (support@chatwithyourfinance.com)
- Privacy policy: https://sprout.z4k.app/privacy
- Terms: https://sprout.z4k.app/terms

Published by MindCrafters LLC.
