

# ネットワークの話

まずは、OSI基本参照モデル

アプセトネデ物

- アプリケーション層(L7)
- プレゼンテーション層(L6)
- セッション層(L5)
- トランスレーション層(L4)
- ネットワーク層(L3)
- データリンク層(L2)
- 物理層(L1)



## セグメントについて

セグメントツリーではない。セグメントのつながりはL2。`arp - a`コマンドで同じセグメントの端末とかを列挙できる。それで出てきた端末のIPアドレスとMACアドレスを見ることができる。Address Resolution Protocolの略。

[TCP/IP ARP、RARPとは](https://www.infraexpert.com/study/tcpip2.html#:~:text=ARP%EF%BC%88Address%20Resolution%20Protocol%EF%BC%89%E3%81%AF,%E3%82%92%E5%BE%97%E3%82%89%E3%82%8C%E3%82%8B%20%E3%83%97%E3%83%AD%E3%83%88%E3%82%B3%E3%83%AB%E3%81%A7%E3%81%99%E3%80%82)を参照してくれ～！以下、一部抜粋

> ARP（Address Resolution Protocol）は、IPアドレスからEthernetのMACアドレスの情報を得られる
> 　プロトコルです。[LAN](https://www.infraexpert.com/study/study13.html)に接続されたコンピュータ間で通信するためには、IPパケットは下位のレイヤで
> 　L2ヘッダが付加された上で伝送されることからMACアドレスの情報が必要となります。しかしこれらの
> 　IPアドレスとMACアドレスは自動的な関連づけがないので、ARPでMACアドレスを得る必要があります。
> 　※　TCP/IPを利用したコンピュータのLAN通信では、IPアドレスとMACアドレスの2つのアドレスが分かることで通信できます。



ここで、単語のおさらい？

- ブロードキャストとは

  同じセグメント内の端末全てに通信を送る。

- マルチキャストとは

  同じセグメント内の指定した端末に通信を送る。

- DNSとは

  Domain Network Systemの略。ドメイン名とIPアドレスを1:1で対応させている。

L2はセグメントでつながってる部分っぽい？それかそのルーターでつながってる部分かも？たぶん色んな意味でL2が出るんだろうな



## ドメインについて

google.co.jpってのがあったとする。(google.comだけど)

- .jpの部分

  国をあらわしてる。.enとかがほかにある。

- .coの部分

  coはcompanyの略らしい。comだけじゃないんだね。

- googleの部分

  さすがに会社名とか名前。

ポートについては次の見出し。

そのドメインにアクセスするときに再帰的通信とかを行うらしい。

例:google.co.jpにアクセスするとき

まず、各パソコンには.enとか.jpとか.comとか.ioとか.beautyとかへのドメインに対してどこに通信をすればいいのかが備わっている。

日本の.jpはいくつかのサーバーがあるとのこと。それらのサーバーに通信した後に次の.co.jpサーバーへの通信先がIPアドレスとして返ってくる。

.co.jpにアクセスしたらgoogle.co.jpへのIPアドレスがかえってくる。これが再帰的通信？らしい。

google.co.jpへのIPアドレスにアクセスをして通信を行う。



## ポートについて

http通信は80、https通信は443、sshは22

ポートっていうのはプロトコルとかを決める。どのプロトコルがどのポートなのかが対応付けられている。





## おまけ　会津大学のすこし

std1のパソコンはstd1内で繋がっている(普通なら)

std2も同様で、それらをまとめたルーターがある。そのルーターが学内のコンピュータと繋がっている。

学内のコンピュータの中にはssh-gateサーバもあって、いったんsshで経由してstdとかに飛ぶ仕様なのはそういうことだと思う。

sshするときをまとめると、

1. 全世界のインターネット（それぞれの自宅とか）
2. 学校のssh-gateに対してポート番号22でアクセスする。（sshなので22番）そのときにssh-gateの前のルータを通るっぽいけどそれがファイアーウォール。
3. ssh-gateにアクセスしたらssh-gateは学内のコンピュータとつながっているので各部屋のルータを経由して目的のパソコンにssh接続できる。