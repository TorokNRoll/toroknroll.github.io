この投稿の公開から2週間以内に、Taprootはブロック{{site.trb}}でアクティベートされる予定です。
何が起こるかは分かっていますし、いくつか起こる可能性のある障害も分かっています。

ベストで最も可能性の高い結果は、すべてがうまくいくことです。
何も起こらなければ、通常のユーザーには何も見えないはずです。
ノードを注意深く観察したり、Taprootトランザクションを作成しようとする人だけがなにかに気づくでしょう。
ブロック709,631では、私たちが認識しているほぼすべてのフルノードが同じコンセンサスルールを適用します。
その1ブロック後、Bitcoin Core 0.21.1、22.0または関連リリースを実行しているノードは、
それより前のソフトウェアリリースでは実行されていなかった追加の[Taproot][topic taproot]ルールを適用します。

これには、ノードソフトウェアの以前のバージョンと新しいバージョンで異なるブロックを受け入れるというリスクが伴います。
これは2015年の[BIP66][]ソフトフォークのアクティベーション中に発生し、
6ブロックのチェーン分岐といくつかの短いチェーン分岐が発生しました。
この問題の再発を防ぐために、かなりの技術的な努力が払われてきました。
同様の問題は、マイナーが意図的にTaprootで無効なブロックをマイニングするか、
Bitcoin Coreや関連ノードソフトウェアにハードコードされた安全対策を無効にした場合にのみTaprootで起こるでしょう。

具体的には、チェーン分岐を発生させるためには、マイナーはTaprootのルールに従わずに
（segwit v1アウトプットである）Taprootアウトプットから支払いをするトランザクションを作成または受け入れる必要があります。
マイナーがそうした場合、Bitcoinノードのオペレーターが経済的なコンセンサスから、
Taproot無効ブロックを拒否した場合、マイナーは少なくとも6.25 BTC（執筆時点で約$400,000 USD）を失うことになります。

ノードオペレーターがどうするかは、無効なブロックを作ってみないことには分かりません。
ノードは完全にプライベートに実行できますが、[プロキシの測定値][bitnodes]では、
ノードオペレーターの50%以上がBitcoin CoreのTaproot適用バージョンを実行していることを示しています。
これはTaproot無効ブロックを作成したマイナーが、ネットワークによって拒否されることを確実にするのに十分すぎるほどでしょう。

非常に可能性は低いですが、一時的なチェーン分岐は理論的には可能です。
[ForkMonitor.info][]のようなサービスやBitcoin Coreの`getchaintips` RPCを使って、分岐を監視することが可能です。
分岐が発生した場合、軽量クライアントは誤った承認を受け取る可能性があります。
2015年のチェーン分岐のように、6承認得ることは理論的に可能ですが、
それはマイナーが250万ドル近い価値を失ったことを意味します（2015年の損失は約5万ドルでした）。
これほど大きな価値がかかっているので、マイナーは半年前に準備を通知したTaprootのルールを実際に適用することが期待できます。

私たちが想像するほぼすべての障害状況において、シンプルで効果的な一時的な対応は、承認数の上限を上げることです。
通常、支払いを受け入れるのに6承認待っている場合、
問題が解決されるか、さらに高い承認数が必要であることが明確になるまでの数時間、
承認数を30回にすぐに上げることができます。

フルノードオペレーターの経済的なコンセンサスからTaprootのルールを適用すると確信しているユーザーやサービスにとっては、
さらにシンプルな解決策として、どのトランザクションが承認されたかという情報のみを
Bitcoin Core 0.21.1以降（まてあは互換性のあるノード実装）から取得することができます。

Optechでは、Taprootのアクティベーションはスムーズに進むと予想していますが、
取引所やブロック{{site.trb}}付近で大きな金額を受け入れる人は、
ノードをアップグレードするか、問題の兆候がある場合には承認数の上限を一時的に引き上げる準備をすることを勧めています。

[forkmonitor.info]: https://forkmonitor.info/nodes/btc
[bitnodes]: https://bitnodes.io/nodes/
