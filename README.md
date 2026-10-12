# Sprout: AI Finance & Cash Flow for Claude

Sprout is an AI finance assistant for personal finance and business finance. Chat with your connected bank and credit card accounts in Claude to understand cash flow, track expenses, review subscriptions, and find the transactions behind your questions. Built for individuals, freelancers, self-employed professionals, founders, startups, and small-business owners reviewing their own connected accounts.

## What you can do

- **Personal finance and money management:** review income, spending, bank balances, credit card charges, household expenses, recurring bills, and budget questions. See where your money goes by category or merchant.
- **Business finance and expense analysis:** review business bank accounts, company card spending, operating expenses, vendor payments, supplier payment history, and software costs. Choose the accounts for a business review so personal and business transactions stay separate.
- **Cash flow analysis and income tracking:** posted inflows, outflows, net cash flow, and spending trends by day, week, or month. Compare two periods with exact changes and percentages, excluding transfers between your own accounts.
- **Subscription tracking and SaaS spend:** detected recurring subscriptions and bills, price changes, estimated renewal dates, and annualized costs.
- **Transaction search and charge review:** find bank and card transactions by merchant, date, category, account, currency, or amount, and check possible duplicate charges and unusually large expenses.
- **Bookkeeping preparation and monthly finance reviews:** inspect payment history and categorized spending before talking to your bookkeeper or accountant. USD and CAD accounts stay in their original currencies, never combined or converted.

Try asking: "Where did my money go last month?", "Which vendors did my business spend the most with?", "What changed in my business cash flow?", "Which subscriptions or SaaS tools keep renewing?"

## What it includes

- A remote MCP server, `https://api-sprout.z4k.app/mcp`, with read-only finance tools (`list_accounts`, `get_cash_flow`, `get_spending_breakdown`, `get_period_totals`, `compare_periods`, `search_transactions`, `get_recurring_charges`, `find_unusual_transactions`, `get_data_health`, `open_sprout`, and others) plus `update_settings`, which saves your default reporting period.
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
- Bank access is read-only. Sprout cannot move money, pay bills, cancel subscriptions, dispute charges, or execute trades. Net cash flow is not accounting profit, recurring dates and costs are estimates, and unusual-charge matches are items to review, not fraud findings.
- Transaction descriptions come from banks and are treated as data, never as instructions.

## Support

- Support: https://sprout.z4k.app/support (support@chatwithyourfinance.com)
- Privacy policy: https://sprout.z4k.app/privacy
- Terms: https://sprout.z4k.app/terms

Published by MindCrafters LLC.
