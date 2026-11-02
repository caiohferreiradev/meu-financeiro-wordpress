# Meu Financeiro — WordPress Personal Finance Dashboard

Meu Financeiro is a private, self-hosted finance dashboard for organizing monthly income and expenses in WordPress. It turns a spreadsheet-style workflow into a responsive, full-screen interface with monthly summaries, interactive charts, quick payment controls, and editable records.

> **Language:** The current interface is in Brazilian Portuguese and formats amounts in BRL (R$). This README is in English so contributors and Playground users can understand how to install and run the project.

## What it does

- **Overview:** monthly income, planned expenses, balance, paid and pending amounts, a six-month income/expense chart, and expense breakdown by category.
- **Income and expenses:** add, edit, and remove entries; classify an expense as fixed or variable; set a due date and reference month; mark income received and bills paid; optionally mark recurring entries.
- **Credit cards:** track statement amounts by month and responsible person, with a paid checkbox.
- **Subscriptions:** record recurring services, monthly or annual billing, responsible person, and active/paused status.
- **Financing and debt:** track installment labels, monthly amounts, reference months, and payment status.
- **Goals and investments:** track monthly contributions, saved totals, and target progress.
- **Month and year filters:** review one month at a time. The overview chart compares the selected month with the previous five months.
- **Data backup:** download the current records as a JSON file from the dashboard footer.
- **Full-screen presentation:** the page containing the shortcode hides the standard theme header and footer for a focused app-like experience.

## Privacy and storage

The plugin starts with empty collections. It does not include the example names, transactions, or amounts shown in the reference screenshots.

Records are stored in the WordPress database under an option associated with the currently logged-in WordPress user. The REST endpoint requires an authenticated user and a WordPress REST nonce. This is intended for a personal, authenticated WordPress site. On a production site, restrict the dashboard page to your account and use HTTPS. A private page alone is not an authentication boundary if the site allows anonymous access to it.

The Playground demo uses a temporary browser-based WordPress instance. Treat it as a preview; use a properly secured WordPress installation for ongoing financial records.

## Requirements

- WordPress 6.0 or newer
- PHP 7.4 or newer
- A logged-in WordPress account with permission to read

## Install on a WordPress site

1. Download the plugin ZIP from this repository.
2. In WordPress Admin, open **Plugins → Add New Plugin → Upload Plugin**.
3. Choose the ZIP, install it, and activate **Meu Financeiro**.
4. Create a page and add the shortcode [meu_financeiro] in a Shortcode block.
5. Publish the page and restrict access to your own account. The dashboard is shown to logged-in users only.

## Run in WordPress Playground

Playground can install a plugin from a GitHub repository only when that repository is publicly accessible. This repository is public so Playground can fetch the plugin package directly.

The repository includes a blueprint.json configured to download the clean plugin ZIP, activate it, create a dashboard page, and open that page. Open this link to start the demo:

https://playground.wordpress.net/?blueprint-url=https://raw.githubusercontent.com/caiohferreiradev/meu-financeiro-wordpress/main/blueprint.json

The demo starts empty. Do not put real financial records in a public demo.

### Manual Playground setup

1. Open https://playground.wordpress.net/.
2. Open the Playground admin and go to Plugins → Add New Plugin → Upload Plugin.
3. Upload the plugin ZIP from this repository and activate it.
4. Create a page with [meu_financeiro] and open it while signed in.

## Repository contents

- financas-pessoais.php — plugin entry point, shortcode, assets, authenticated REST API, and per-user storage.
- assets/app.js — dashboard interface, forms, charts, filters, payment toggles, and JSON export.
- assets/app.css — responsive dashboard styling and full-screen page treatment.
- blueprint.json — WordPress Playground Blueprint for the public demo.
- meu-financeiro-wordpress.zip — installable plugin package without screenshot records.

## Development notes

The plugin has no build step or third-party JavaScript dependencies. Edit the PHP, CSS, and JavaScript files directly, then package the financas-pessoais directory as a ZIP for WordPress installation. Keep the plugin folder as the ZIP's top-level directory.

When changing the REST data shape, keep the allowed collections in sync across the PHP endpoint and assets/app.js. Never add real personal finance data or credentials to source control.

## Known scope

The current app is a personal tracker, not a bank integration or accounting system. It does not connect to financial institutions, import bank statements, or provide automated recurring-charge generation. The recurring field is a record attribute; a user still manages each month's entries.

## License

GPL-2.0-or-later, as declared in the plugin header.
