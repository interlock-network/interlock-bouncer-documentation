# Interlock-Bouncer

Interlock-Bouncer is a Discord bot that scans your server for malicious
links and neutralizes them. It does this by querying our database of
known-malicious sites. If the site is new, we use our proprietary visual
AI to identify 0-day phishing sites. Setup takes just a minute or two
and it begins protecting your server instantly.

Interlock-Bouncer is a project of [Interlock](https://www.interlock.network/),
a web3 company that is decentralizing security. It's free to use in
exchange for an occasional Interlock partnership post. In the future,
Interlock-Bouncer will be powered by $INTR, Interlock's token launching
later this year.

# Status

Warning: Interlock-Bouncer is in early alpha. The current
implementation results in a high level of false positives (benign
links marked as dangerous). In plain language, we err on the side of
caution to keep your community safe.

# Authorizing Interlock-Bouncer for Your Server

Visit the following URL to authorize Interlock-Bouncer to run on your own
server:
https://discord.com/api/oauth2/authorize?client_id=966558765799342131&permissions=1641751637056&scope=bot

# Testing Interlock-Bouncer

To test if Interlock-Bouncer is working, post the following
known-unsafe link in a channel Interlock-Bouncer is monitoring:
`http://phishing.com`

Your message should immediately be deleted and Interlock-Bouncer
should post the following:

```
Message contains dangerous links! NAME: http://phishing.com
```
