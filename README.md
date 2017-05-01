# Realtek Wireless Driver for Linux

## Reference Repository

[This repository](https://github.com/diederikdehaas/rtl8812AU) & [This](https://github.com/paralin/rtl8821au) seem to contain approximately the same codebase with several different available versions. I would recommend using it as it's more actively maintained.

## BUFFALO「WI-U2-433DHP」

このリポジトリでは、主に**WI-U2-433DHP**のために編集しました。  
**WI-U2-433DHP**のドライバはWinとMacのみであり、Linuxがなかったのでこのリポジトリを使えばlinuxで使えるようになるかと思います。  

基本的には、無線のチップにRTL8821AUを使用しているため、これのドライバを入れれば使えるようになります。

## Install

```bash
make
sudo make install
sudo modprobe 8821au
```

## Confirm

```bash
$ lsmod
...
8821au
...

$ iwconfig
eth0      no wireless extensions.
 
lo        no wireless extensions.
 
wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated
```

## More information

PCを再起動した時に自動でこのドライバが読み込まれるようにするために`8821au.conf`ファイルを作って、以下の内容で記述する。

```bash
$ sudo emacs /etc/modules-load.d/8821au.conf
#8821auをロード
8821au
```
