# robosys2020_DeviceDriver
ロボットシステム学の課題で作成・改良したデバイスドライバのコードです。

## 目次
- 概要
- 用意・構築環境
- 回路
- 実行コマンド
- ライセンス

## 概要
大学の講義の課題として作成したデバイスドライバで、下記の動作を行います。
- 数字の0~4の入力に応じたLEDの点灯・消灯
- 交通信号機を模したパターンでのLEDの点灯

## 用意・構築環境
- Raspberry Pi 4
- ブレッドボード
- LED
- 抵抗 220Ω
- ジャンパー線

## 回路
LEDを光らせるための電子回路は以下のように作成しました。  
[写真]
![回路全体](https://user-images.githubusercontent.com/73330874/101272214-783cb580-37cd-11eb-8f75-e7550f5e85d6.jpg) 

[回路図]
![robosys1_kairo](https://user-images.githubusercontent.com/73330874/101739219-932f6280-3b0a-11eb-97ed-1b2f01751903.png)

左側のLEDは[青:23,黄:25,赤:26]、右側のLEDは[青:27,赤:17]のGPIOに対応しています。

## 実行コマンド
実際に動作させるために、このリポジトリをクローンする。
```
$ git clone https://github.com/Satoru-Negishi/robosys_devicedriver_2020-12.git
```
クローンしたファイル内で、以下を実行し数字を入力できる状態にする。
```
$ make
$ sudo insmod myled.ko
$ sudo chmod 666 /dev/myled0
```
上記のコマンドの変更を元に戻す際は以下のコマンドを入力してください。
```
$ sudo rmmod myled
$ make clean
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
![echo1](https://user-images.githubusercontent.com/73330874/101271930-e59b1700-37ca-11eb-8fd1-1fa800afbd61.jpg)


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
![echo2](https://user-images.githubusercontent.com/73330874/101272124-b5ed0e80-37cc-11eb-9fb3-b56440f032aa.jpg)

#### 3.入力['4']
```
$ echo 4 > /dev/myled0
```
'4'を入力すると交通信号機を模したパターンでLEDを点灯・消灯させます。  
動作の様子は[こちら](https://youtu.be/paAuUeA_dmM)で確認できます。  

## ライセンス
[GNU GENERAL PUBLIC LICENSE](https://github.com/Satoru-Negishi/robosys_devicedriver_2020-12/blob/main/COPYING)
