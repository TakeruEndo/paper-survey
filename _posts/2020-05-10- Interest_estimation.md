---
layout: post
title: 興味推定に関する研究分野のまとめ
summary: 興味推定
featured-img: system
categories: Interest_Estimate
---

# 興味推定

## [ニューラルネットワークを用いた雑談対話からのユーザの興味推定](https://www.jstage.jst.go.jp/article/tjsai/34/2/34_E-I94/_pdf/-char/ja)
### 概要
- 発話->woed2vec(ベクトル化)->RNN(エンコード)
- Attentionを組み込む

### 使用データ
**検証用**
日本語のテキストチャットのデータと被験者の興味に関するアンケート
**word2vecの学習**
twitterで収集


## [発話内容と口調の関係に基づく発話者の嗜好推定](https://www.jstage.jst.go.jp/article/jsoft/31/5/31_816/_pdf/-char/ja)
### 概要
事象と反応に基づくヒューリスティックと発話の口調から推定した話者感情を用いて、発話内容に関する話者の高感度を推定する
### 情緒計算手法
- BoW(否定単語が欠落してしまう)
- EGCを用いる

<img width="350" alt="" src="{{ site.url }}{{ site.baseurl }}/assets/img/posts/estimate1.png">

## [生体情報を用いた学習者の心的状態推定と学習支援の試み](https://www.jstage.jst.go.jp/article/jsise/36/2/36_360206/_article/-char/ja/)


# 年齢推定

## [Age Estimation in Short Speech Utterances Based on LSTM Recurrent Neural Networks](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=8316819)

### 概要
LSTMによる年齢推定
