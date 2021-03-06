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
https://discord.com/api/oauth2/authorize?client_id=982020138352128070&permissions=534723951680&scope=bot

# Testing Interlock-Bouncer

To test if Interlock-Bouncer is working, post the following
known-unsafe link in a channel Interlock-Bouncer is monitoring:
`http://phishing.com`

Your message should immediately be deleted and Interlock-Bouncer
should post the following:

```
Message contains dangerous links! NAME: http://phishing.com
```

# Adding to the allowlist

The allowlist is a set of URLs that are marked as safe by a server. In
order to add an element to the allowlist invoke the following command:

`!allow_domains url1.com url2.com`

where `url1.com` and `url2.com` represent URLs that you wish to add to
the allowlist. Allowlists are not shared between servers.

# Flowchart

The flowchart below will give you an idea of how Bouncer works.

```mermaid
graph TD;
A([Bouncer detects message with a URL]) --> B{Is URL allowlisted by guild owner?}
B --> |Yes|M[Bouncer leaves message untouched]
B -.- |No|F["Bouncer sends URL to backend (BE)"]
F --> P{Is URL listed in BE?}
P -.- |Yes|G[URL known safe]
P -.- |No|I{Is URL found safe through visual AI?}
G --> J[BE sends safe]
H --> K[BE sends unsafe]
I -.-> |Yes|J[BE sends safe]
I -.-> |No|K
P -.- |Yes|H[URL known unsafe]
J --> M[Bouncer leaves message untouched] 
M --> O([Bouncer done])
E --> O
K --> E[Bouncer blocks URL by deleting original message <br> and posts new message alerting users]
```
