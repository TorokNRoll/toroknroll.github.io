---
title: 'Bitcoin Optech Newsletter #160'
permalink: /en/newsletters/2021/08/04/
name: 2021-08-04-newsletter
slug: 2021-08-04-newsletter
type: newsletter
layout: newsletter
lang: en
---
This week's newsletter includes our regular sections describing how you
can prepare for taproot, summarizing the latest releases and release
candidates, and listing notable changes to popular Bitcoin
infrastructure projects.

## News

*No significant news this week.*

## Preparing for taproot #7: multisignatures

*A weekly [series][series preparing for taproot] about how developers
and service providers can prepare for the upcoming activation of taproot
at block height {{site.trb}}.*

{% include specials/taproot/en/06-multisignatures.md %}

## Releases and release candidates

*New releases and release candidates for popular Bitcoin infrastructure
projects.  Please consider upgrading to new releases or helping to test
release candidates.*

- [C-Lightning 0.10.1rc2][C-Lightning 0.10.1] is a release candidate for
  an upgrade that contains a number of new features, several bug fixes,
  and a few updates to developing protocols (including [dual
  funding][topic dual funding] and [offers][topic offers]).

## Notable code and documentation changes

*Notable changes this week in [Bitcoin Core][bitcoin core repo],
[C-Lightning][c-lightning repo], [Eclair][eclair repo], [LND][lnd repo],
[Rust-Lightning][rust-lightning repo], [libsecp256k1][libsecp256k1
repo], [Hardware Wallet Interface (HWI)][hwi repo],
[Rust Bitcoin][rust bitcoin repo], [BTCPay Server][btcpay server repo],
[Bitcoin Improvement Proposals (BIPs)][bips repo], and [Lightning
BOLTs][bolts repo].*

- [Bitcoin Core #22006][] adds [documentation][tracing doc] for User-Space, Statically Defined
  Tracing (USDT) and the first three tracepoints - build support and macros for which were added in
  [Bitcoin Core #19866][]. Users that build Bitcoin Core with eBPF tracing enabled can hook into the
  tracepoints with the provided [example scripts][contrib tracing doc] or write their own tracing
  scripts for greater observability into the node when a new block is connected, inbound P2P messages
  are received, and outbound P2P messages are sent. The documentation also includes usage examples and
  guidelines for the addition of new tracepoints.

- [Eclair #1893][] allows separate configuration of feerates for [unannounced
  channels][topic unannounced channels], announced channels, and
  [trampoline][topic trampoline payments] relay minimums. This PR also sets
  different default relay feerates for unannounced channels (0.01%) in contrast
  to announced channels (0.02%).

- [Rust-Lightning #967][] adds support for making [keysend-style spontaneous
  payments][keysend onion] via the
  `send_spontaneous_payment` function call. With this change, all four LN
  implementations we cover will have support for keysend.

  The author has also submitted [corresponding documentation][BOLTs #892] (yet
  unmerged) on keysend payments as a [BLIP][news156 blips] (Bitcoin Lightning
  Improvement Proposals), a proposed way to document features and best practices
  which do not belong as part of the LN BOLTs specification.

{% include references.md %}
{% include linkers/issues.md issues="22006,19866,1893,967,892" %}
[C-Lightning 0.10.1]: https://github.com/ElementsProject/lightning/releases/tag/v0.10.1rc2
[tracing doc]: https://github.com/bitcoin/bitcoin/blob/8f37f5c2a562c38c83fc40234ade9c301fc4e685/doc/tracing.md
[contrib tracing doc]: https://github.com/bitcoin/bitcoin/tree/8f37f5c2a562c38c83fc40234ade9c301fc4e685/contrib/tracing
[keysend onion]: /en/topics/spontaneous-payments/#add-data-to-the-routing-packet
[news156 blips]: /en/newsletters/2021/07/07/#blips
