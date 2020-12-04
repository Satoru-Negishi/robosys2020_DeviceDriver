# robosys2020_DeviceDriver
ロボットシステム学の課題で作成したデバイスドライバのコードです。

## 目次
- 概要
- 用意・構築環境
- 回路
- コマンド
- 動作
- リンク

## 概要
大学の講義の課題として作成したデバイスドライバで、下記の動作を行います。
- 数字の0~3の入力に応じたLEDの点灯・消灯
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
