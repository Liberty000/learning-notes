# level-101



## 代表的な環境変数

![image-20211013215425545](level-101.assets/image-20211013215425545.png)

![image-20211013215447042](level-101.assets/image-20211013215447042.png)

## メタキャラクタ

シェルによって特別に解釈される文字です。

![image-20211121175355899](level-101.assets/image-20211121175355899.png)





## Kernal modules

`lsmod`

`cat /proc/modules`



## modprobeの設定ファイル

`/etc/modprobe.d/myconfig.conf`



## 共有ライブラリの場所 検索ファイル

プログラムの実行時に、共有ライブラリの場所を検索するために使用されるファイルは

`/etc/ld.so.cache`

です。

## Hash計算

![image-20211121175719507](level-101.assets/image-20211121175719507.png)

## 実行中のジョブを一時停止

`Ctrl+Z`



## man

Linuxでは、コマンドや設定ファイルのためのオンラインマニュアルページ(manページ)が用意されています。オンラインマニュアルを参照するコマンドはmanです。

manコマンドの書式と主なオプションは以下のとおりです。

![image-20220110190509741](level-101.assets/image-20220110190509741.png)

なお、同じキーワードにmanページが複数用意されている場合があります(例えばpasswdコマンドと「/etc/passwd」ファイル)。このような場合は、セクション番号を指定してmanコマンドを実行することで、目的のmanページを参照することが出来ます。セクション番号を指定しないで実行した場合は、セクション番号の小さいほうのマニュアルが表示されます。

![image-20220110190520540](level-101.assets/image-20220110190520540.png)

## **systemctl**

![image-20220126221907456](level-101.assets/image-20220126221907456.png)

![image-20220126222050837](level-101.assets/image-20220126222050837.png)



## /etc/fstab

「/etc/fstab」ファイルは、利用するファイルシステムのマウント設定を事前に行っておく設定ファイルです。mountコマンドはこのファイルの設定内容を参照して動作します。

「/etc/fstab」ファイルの書式は以下の通りです。項目は6つです。
(1) デバイス名
(2) マウントポイント
(3) ファイルシステムの種類
(4) マウントオプション
(5) dumpフラグ
(6) fsckフラグ

![image-20220126232317016](level-101.assets/image-20220126232317016.png)



## usb-info

接続されたUSBデバイスの情報を表示

```shell
lsusb

cat /proc/bus/usb/devices
```



## dpkg

dpkgはDebian形式のパッケージのインストール・アンインストールなど、基本的なパッケージ管理を行うコマンドです。

![image-20211121182716260](level-101.assets/image-20211121182716260.png)





## rpm

以下はrpmコマンドのインストール関連の主なオプションです。

![image-20220110203215694](level-101.assets/image-20220110203215694.png)



以下はrpmコマンドの参照・検査関連の主なオプション

![image-20220110200650301](level-101.assets/image-20220110200650301.png)

## yum

![image-20220126232427664](level-101.assets/image-20220126232427664.png)



## apt

パッケージの取得元(リポジトリ)を設定するファイルは

`/etc/apt/sources.list`



## chown

chown [-R] :グループ名 ファイルまたはディレクトリ

なお、「:」の部分は「.」としても同じです。



## chgrp

chgrp [-R] グループ名 ファイルまたはディレクトリ



## history

「!番号」と入力することで特定のコマンドを再実行できます

![image-20220126225552688](level-101.assets/image-20220126225552688.png)



## vi/vim

### options

- -R  指定したファイルを読み取り専用で開きます



### ファイル編集commond

![image-20211011220458352](level-101.assets/image-20211011220458352.png)

![image-20220126230802047](level-101.assets/image-20220126230802047.png)



## service daemon

![image-20211011220933380](level-101.assets/image-20211011220933380.png)

## ps

![image-20211011221356151](level-101.assets/image-20211011221356151.png)



## paste

paste [-d 区切り文字] [ファイル名...]



## run level

### 参考

![image-20211011221846880](level-101.assets/image-20211011221846880.png)

### 調べる

現在および1つ前のランレベルを調べることができるコマンドはrunlevelです。

したがって正解はrunlevelです。

```shell
# runlevel
N 5
```

先頭の文字は以前のランレベル、2つ目の文字は現在のランレベルを表しています。なお、「N」はランレベルの変更がされていないことを意味しています。

### 変更

・init
・telinit

例）ランレベルを5に変更する場合

\# init 5 
または
\# telinit 5

## grub

![image-20211011224840429](level-101.assets/image-20211011224840429.png)

>  GRUBのバージョンが0.9x系のものを「GRUB Legacy」、1.9以降のものを「GRUB2」と呼びます。



### GRUB Legacy

GRUB Legacyの設定ファイルは「/boot/grub/menu.lst」、ディストリビューションによっては「/boot/grub/grub.conf」です。

![image-20211011225028953](level-101.assets/image-20211011225028953.png)

![image-20211011230834406](level-101.assets/image-20211011230834406.png)





### GRUB2

GRUB2の設定ファイルは「/boot/grub2/grub.cfg」です。しかし、「/boot/grub2/grub.cfg」ファイルを直接編集することはありません。設定内容は「/etc/default/grub」ファイルおよび「/etc/grub.d」ディレクトリ内のファイルに記述し、「grub2-mkconfig」コマンドで設定内容を「/boot/grub2/grub.cfg」ファイルに反映させます。

```
 grub2-mkconfig -o /etc/grub2.cfg
 
 /etc/grub2.cfg -> ../boot/grub2/grub.cfg
```



![image-20211011225437750](level-101.assets/image-20211011225437750.png)



## Format Disk



### gdisk



### fdisk

fdiskはMBRのみに対応しています。

![image-20211013212013556](level-101.assets/image-20211013212013556.png)

### mkswap

スワップ領域とは、物理メモリ（実メモリ）に収まらなかった情報を一時的に格納する為の、通常ハードディスク上に作成する領域です。



## XFS

XFSは、シリコングラフィックス社（SGI）が開発したジャーナリングファイルシステムです。

![image-20220110184308285](level-101.assets/image-20220110184308285.png)





## fsck

fsckコマンドはファイルシステムのチェック、および問題を修復することが出来ます。

![image-20220110184134840](level-101.assets/image-20220110184134840.png)



## mount

![image-20220110202041623](level-101.assets/image-20220110202041623.png)

## /etc/fstab

「/etc/fstab」ファイルは、利用するファイルシステムのマウント設定を事前に行っておく設定ファイルです。mountコマンドはこのファイルの設定内容を参照して動作します。
一行一行がひとつのファイルシステムのマウント設定を表しています。

![image-20220110203357264](level-101.assets/image-20220110203357264.png)

「/etc/fstab」ファイルの書式は以下の通りです。

(1) デバイス名
「/dev/sda1」のようにデバイスファイルを書くか、ラベル（あらかじめファイルシステムに対して付けておいた名前）やUUID（Universally Unique Identifier: 汎用一意識別子、全世界で重複が起きないように生成される一意な値）を使った指定を書きます。
ラベルを使う場合は 「LABEL=/boot」のように「LABEL=」の後ろにラベル名を書きます。この場合ラベル名は「/boot」です。
UUIDを使う場合も同様で「UUID=」の後ろに続けてUUID文字列を書きます。

デバイスのUUIDは、blkidコマンドやlsblkコマンドで確認できます。
blkidはブロックデバイス（HDDやCD-ROMなどのようにブロック単位でデータを転送するデバイス）の情報を表示するコマンドです。デバイス名や、UUID、ファイルシステムのタイプを表示できます。
lsblkはブロックデバイスをツリー状に一覧表示するコマンドです。「--output」オプションで表示項目を指定することによって、UUIDやファイルシステムのタイプを表示できます。

例）デバイス名、UUID、ファイルシステムのタイプを表示する

![image-20220110203426624](level-101.assets/image-20220110203426624.png)

(2) マウントポイント
ルートファイルシステム上のどの位置にマウントするかの指定をルートからのパスで書きます。

(3) ファイルシステムの種類
デバイス名で指定したファイルシステムの種類を書きます。

(4) マウントオプション
マウントする際に必要となるオプションを書きます。

![image-20220110203439510](level-101.assets/image-20220110203439510.png)

## grep

![image-20211013212751951](level-101.assets/image-20211013212751951.png)

![image-20220110224041652](level-101.assets/image-20220110224041652.png)



## kill

kill [-シグナル名または-シグナル番号] プロセスID
または
kill -s [シグナル名またはシグナル番号] プロセスID

killall [-シグナル名または-シグナル番号] プロセス名(コマンド名)
または
killall -s [シグナル名またはシグナル番号] プロセス名(コマンド名)

pkill [-シグナル名または-シグナル番号] プロセス名(コマンド名)
または
pkill --signal [-シグナル名または-シグナル番号] プロセス名(コマンド名)

![image-20211013214245208](level-101.assets/image-20211013214245208.png)

## find

findは指定したディレクトリ以下からファイルやディレクトリを検索するコマンドです。

![image-20211121173348533](level-101.assets/image-20211121173348533.png)

## tail

tailはファイルの末尾部分を指定して表示するコマンドです。

![image-20211121173454779](level-101.assets/image-20211121173454779.png)

```
・tail -n 5 httpd.conf
・tail -5 httpd.conf
```



## tr

![image-20220126223845892](level-101.assets/image-20220126223845892.png)

## **tune2fs** 

ファイルシステムをext2からext3に変換するにはtune2fsコマンドを利用します。



ext2ファイルシステムの「/dev/hda5」をext3に変換したい。

`tune2fs -j /dev/hda5`

![image-20220126224121370](level-101.assets/image-20220126224121370.png)



## makewhatis

whatisデータベースとは、オンラインマニュアルページ(manページ)に関する情報を蓄積するデータベースのことです。
makewhatisコマンドを実行することで作成、または更新されます。



whatisデータベースは、「man -k キーワード」(apropos キーワード)コマンドや「man -f キーワード」(whatis キーワード)コマンドなどによって使用されます。

## nice

![image-20220126232219346](level-101.assets/image-20220126232219346.png)



## sed

![image-20211121175104499](level-101.assets/image-20211121175104499.png)

test.txt」ファイル内の全ての「a」を「A」に、また「b」を「B」に置換したい。

```shell
sed y/ab/AB/ test.txt
sed -e s/a/A/g -e s/b/B/g test.txt
```



## sort

![image-20220126231802963](level-101.assets/image-20220126231802963.png)



## bz2

![image-20211011220731180](level-101.assets/image-20211011220731180.png)



## uniq 

![image-20220126232119405](level-101.assets/image-20220126232119405.png)![image-20220126232124864](level-101.assets/image-20220126232124864.png)



## xz 

bzip2よりも圧縮率が高い圧縮形式として、LZMA2圧縮アルゴリズムを採用したxzフォーマットがあります。xzはbzip2よりも多くのCPU／メモリを要求しますが、その分圧縮率が高く、また展開速度はbzip2より短いためファイル配布時の圧縮形式として採用されることが増えています。Linuxカーネルソースの配布形式としても採用されています。

![image-20220110202007592](level-101.assets/image-20220110202007592.png)





