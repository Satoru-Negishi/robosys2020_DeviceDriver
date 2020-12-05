# robosys2020_DeviceDriver
ロボットシステム学の課題で作成したデバイスドライバのコードです。

## 目次
- 概要
- 用意・構築環境
- 回路
- コマンド
- 動作
- ライセンス

## 概要
大学の講義の課題として作成したデバイスドライバで、下記の動作を行います。
- 数字の0~4の入力に応じたLEDの点灯・消灯
- 交通信号機を模したパターンでのLEDの点灯

## 用意・構築環境
- Rasbery Pi 4
- ブレッドボード
- LED
- 抵抗 220Ω
- ジャンパー線
- WSL(Ubuntu 18.04 LTS)

## 回路
LEDを光らせるための電子回路は以下の写真のように作成しました。
- 回路写真URL  

LEDはRabery PIのGPIO[17,23,25,26,27]とそれぞれGNDに接続しています。

## 実行
実際に動作させるために、このリポジトリをクローンする。
```
$ git clone https://github.com/Satoru-Negishi/robosys_devicedriver_2020-12.git
```
クローンしたファイル内で、以下のコードを実行し数字を入力できる状態にする。
```
$ make
$ sudo insmod myled.ko
$ sudo chmod 666 /dev/myled0
```

### LEDの点灯・消灯
#### 1.入力['0' / '1']
```
$ echo 0 > /dev/myled0
```
'0'を入力するとGPIO[23,25,26]に接続されたLEDを消灯します。
```
$ echo 1 > /dev/myled0
```
'1'を入力するとGPIO[23,25,26]に接続されたLEDを点灯します。  
LED点灯時は以下のようになります。  
- 入力1写真

#### 2.入力['2' / '3']
```
$ echo 2 > /dev/myled0
```
'2'を入力するとGPIO[17, 27]に接続されたLEDが消灯します。
```
$ echo 3 > /dev/myled0
```
'3'を入力するとGPIO[17, 27]に接続されたLEDが点灯します。
LED点灯時は以下のようになります。
- 入力3写真

#### 3.入力['4']
```
$ echo 4 > /dev/myled0
```
'4'を入力すると交通信号機を模したパターンでLEDを点灯・消灯させます。  
動作の様子は以下のURLリンクから確認できます。  
- youtubeURL

## ライセンス
[GNU GENERAL PUBLIC LICENSE](https://github.com/Satoru-Negishi/robosys_devicedriver_2020-12/blob/main/COPYING)
