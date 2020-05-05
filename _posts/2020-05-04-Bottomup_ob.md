---
layout: post
title: Bottom-up Object Detection by Grouping Extreme and Center Points
summary: 4つの極値ポイントと中心点による物体検出
featured-img: article1
categories: Survey CV ObjectDetection 
---

## 1. どんなもの？
![スクリーンショット 2020-04-14 14 57 17](https://user-images.githubusercontent.com/40351074/79190987-86198100-7e60-11ea-87d9-c8c8064fa436.png)

ボトムアップの手法によって物体検出を行うExtremeNetを提案。標準のキーポイント推定ネットワークを使用して、4つの極値ポイント（最上部、左端、最下部、右端）とオブジェクトの1つの中心点を検出する。
5つのキーポイントを検出するには[HourglassNet](https://arxiv.org/abs/1603.06937)を使用。学習のセットアップやオフセットの予測はCornerNetを使用。

#### ボトムアップアプローチ
画像中のキーポイントを全て検出した後に、それらをつなぎ合わせていく方式
#### トップダウンアプローチ
認識する対象を検出し、その対象に対して処理を施す方式

### 本論文が指摘するトップダウンのデメリット
- bbox内に背景が多く混入すること
- ポーズなどの詳細なオブジェクト情報が得られないこと

![スクリーンショット 2020-04-14 14 18 44](https://user-images.githubusercontent.com/40351074/79189054-b874af80-7e5b-11ea-8822-9e079c171f5f.png)


## 2. 先行研究と比べてどこがすごいの？
物体の形状をより細かに検出するためにボトムアップ方式の物体検出法を取り入れている  
-----segmentationはどうやって検出しているのか----
## 3. 技術や手法の"キモ"はどこにある？
４つの極値を用いて物体検出を行なっている点。
## 4. どうやって有効だと検証した？
![スクリーンショット 2020-04-14 14 58 11](https://user-images.githubusercontent.com/40351074/79190980-8023a000-7e60-11ea-898c-13f90a8c11a1.png)

## 5. 議論はあるか？
いまいちすごさがわからなかったのでもう一度読みたい

## 6. 次に読むべき論文はあるか？
- セグメンテーション系の論文を読みたい

### 論文情報・リンク

* [Xingyi Zhou, Jiacheng Zhuo, Philipp Krähenbühl，"Bottom-up Object Detection by Grouping Extreme and Center Points，2019](https://arxiv.org/abs/1901.08043)
