---
title: "Commands"
description: ""
lead: ""
date: 2021-02-18T10:43:15-05:00
lastmod: 2021-02-18T10:43:15-05:00
draft: false
images: []
menu: 
  docs:
    parent: "dgctl"
weight: 310
toc: true
---

```daoctl``` remains under heavy development. Expect breaking changes.

#### Commands
##### View Roles
```
./daoctl get roles
```
##### Include proposals
```
./daoctl get roles --include-proposals
```
##### View Assignments
```
./daoctl get payouts
```
##### View Treasury
```
./daoctl get treasury
```
##### View Treasury Redemption Requests
```
./daoctl treasury get requests
```
##### View Treasury Payments (fulfilling requests)
```
./daoctl treasury get payments
```
##### View Details of a Ballot
```
./daoctl get ballot d4
```
##### Serve prometheus metrics
```
./daoctl get ballot d4
```


#### Treasury Commands

The treasury requires multisig approvals from treasurers. See below for creating payment and attestation records.

Submitting a new payment against a Redemption Request 
```bash
# in the below command, the redemption_id is 6
./daoctl --vault-file hyphanewyork.json treasury newpayment 6 "3500.00 HUSD" --network BTC --trxid b475e94c6a86dd18cce0ab7a1dfc9d0f94e20baf6c91317c14ce669da4111e1c --memo "just a memo field for any additional context"
```

Attesting to an existing payment. Treasurers have the responsibility of reviewing and validating transaction payments. To attest that a posted payment is true and accurate, use the ```attest``` command.
```bash
# in the below example, the paymentID is 4 and the requestID is 6
./daoctl --vault-file hyphanewyork.json treasury attest 4 6 "3500.00 HUSD" 
```

