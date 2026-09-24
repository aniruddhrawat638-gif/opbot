# Lovemate Activity Rewards v3

Discord activity-credit bot with a small admin panel.

## Reward math

The configured rate is:

1500 counted messages = ₹100 OR $1

Therefore:

1 credit/message = ₹100 / 1500
= ₹0.0666666667

and:

1 credit/message = $1 / 1500
= $0.0006666667

The bot records internal credits only. It does NOT automatically transfer INR, LTC, crypto, or other money.

## Eligibility

Only members who have `ELIGIBLE_ROLE_ID` can earn credits.

## Anti-spam

V1/V2 uses:
- per-user activity cooldown
- daily counted-message cap
- bot-message exclusion

This means the displayed credit balance is based on *counted* activity, not every raw Discord message.

## Commands

/credits
/balance
/leaderboard
/activity
/withdraw amount
/reward-settings

Owner:
/reward-reset user

## Admin panel

The included Express admin panel is a lightweight configuration/monitoring panel.

It can:
- view bot status
- view eligible role ID
- view reward rate
- view total tracked users
- view total credits
- toggle watermark
- change watermark text
- change eligible role ID
- change reward rate values
- save configuration

The panel no longer needs `ADMIN_PANEL_ENABLED`, `ADMIN_PANEL_PORT`, or `ADMIN_PANEL_KEY` in `.env`. It runs on port `3000` and derives a private access key from the bot token + owner ID at runtime. The startup log prints the local panel URL.

For a production deployment, put the panel behind HTTPS and a proper authentication system.

## Discord setup

Enable the required Gateway intents in the Discord Developer Portal for message events. Discord has tightened access requirements around message content and other privileged server data; only request the data your app actually needs.

Official references:
https://discord.com/blog/updated-requirements-to-how-apps-access-data-in-servers
https://support.discord.com/hc/en-us/articles/7933951485975-Visibility-of-Bot-Data-Access
