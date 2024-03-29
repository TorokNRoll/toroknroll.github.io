---
title: 'Bitcoin Optech Newsletter #258'
permalink: /en/newsletters/2023/07/05/
name: 2023-07-05-newsletter
slug: 2023-07-05-newsletter
type: newsletter
layout: newsletter
lang: en
---
This week's newsletter includes another entry in our limited weekly
series about mempool policy, plus our regular sections announcing new
releases and release candidates and describing notable changes to
popular Bitcoin infrastructure software.

## News

_No significiant news was found this week on the Bitcoin-Dev and
Lightning-Dev mailing lists._

## Waiting for confirmation #8: Policy as an Interface

_A limited weekly [series][policy series] about transaction relay,
mempool inclusion, and mining transaction selection---including why
Bitcoin Core has a more restrictive policy than allowed by consensus and
how wallets can use that policy most effectively._

{% include specials/policy/en/08-interface.md %} {% assign timestamp="0:30" %}

## Releases and release candidates

*New releases and release candidates for popular Bitcoin infrastructure
projects.  Please consider upgrading to new releases or helping to test
release candidates.*

- [Core Lightning 23.05.2][] is a maintenance release of this LN node
  software that contains several bug fixes that may affect users in
  production. {% assign timestamp="10:27" %}

## Notable code and documentation changes

*Notable changes this week in [Bitcoin Core][bitcoin core repo], [Core
Lightning][core lightning repo], [Eclair][eclair repo], [LDK][ldk repo],
[LND][lnd repo], [libsecp256k1][libsecp256k1 repo], [Hardware Wallet
Interface (HWI)][hwi repo], [Rust Bitcoin][rust bitcoin repo], [BTCPay
Server][btcpay server repo], [BDK][bdk repo], [Bitcoin Improvement
Proposals (BIPs)][bips repo], [Lightning BOLTs][bolts repo], and
[Bitcoin Inquisition][bitcoin inquisition repo].*

- [Bitcoin Core #24914][] loads wallet database records in order by
  type instead of iterating through the whole database twice to detect
  dependencies. Some wallets with corrupted records may no longer load
  after this change, but they can be loaded with a previous version of
  Bitcoin Core and ported to a new wallet. {% assign timestamp="22:03" %}

- [Bitcoin Core #27896][] removes the experimental system call (syscall) sandbox
  feature (see [Newsletter #170][news170 syscall]). A [related issue][Bitcoin
  Core #24771] and follow up comments note the drawbacks of the
  feature including maintainability (both of the syscall whitelist and OS
  support), better-supported alternatives, and considerations about whether syscall
  sandboxing should be Bitcoin Core's responsibility. {% assign timestamp="24:47" %}

- [Core Lightning #6334][] updates and expands CLN's experimental
  support for [anchor outputs][topic anchor outputs] (see [Newsletter
  #111][news111 cln anchor] for CLN's initial implementation).  Some of
  the updates in this PR include enabling experimental support for
  zero-fee [HTLC][topic htlc] anchors and adding configurable checks to
  ensure the node has at least the minimum amount of emergency funds it
  needs to operate an anchor channel. {% assign timestamp="27:51" %}

- [BIPs #1452][] updates the [BIP329][] specification for a [wallet
  label][topic wallet labels] export format with a new optional
  `spendable` tag that indicates whether the associated output should be
  spendable by the wallet.  Many wallets implement _coin control_
  features that allow a user to tell the [coin selection][topic coin
  selection] algorithm to not spend certain outputs, such as outputs that
  might reduce the user's privacy. {% assign timestamp="31:08" %}

- [BIPs #1354][] adds [BIP389][] for the multiple derivation path
  [descriptors][topic descriptors] described in [Newsletter #211][news211 desc].  It allows a
  single descriptor to specify two related BIP32 paths for HD key
  generation---the first path for incoming payments and the second path
  for internal wallet payments (such as change). {% assign timestamp="33:55" %}

{% include references.md %}
{% include linkers/issues.md v=2 issues="24914,27896,6334,1452,1354,24771" %}
[policy series]: /en/blog/waiting-for-confirmation/
[news111 cln anchor]: /en/newsletters/2020/08/19/#c-lightning-3830
[news211 desc]: /en/newsletters/2022/08/03/#multiple-derivation-path-descriptors
[core lightning 23.05.2]: https://github.com/ElementsProject/lightning/releases/tag/v23.05.2
[news170 syscall]: /en/newsletters/2021/10/13/#bitcoin-core-20487
