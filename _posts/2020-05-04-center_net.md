---
layout: post
title: CenterNet Keypoint Triplets for Object Detection
summary: corner + centerのキーポイントで予測
featured-img: article1
categories: CV ObjectDetection
---

## 1. どんなもの？

![スクリーンショット 2020-03-30 9 58 39](https://user-images.githubusercontent.com/40351074/77866207-0dfe6900-726d-11ea-9a4a-80f5a57cbf68.png)

CorneNetをベースに新たにオブジェクトの中心座標を予測することで物体検出の精度を向上させた手法。
### canter pooling
センターキーポイントを予測するために使用
### cascade corner pooling
元々のコーナープーリングモジュール

### 背景
これまではアンカーベースの物体検出が主流だった。これには以下の欠点があった。
- 多くのアンカーが必要
- マニュアルでアンカーのサイズとアスペクト比を決定しなければならない
新しくキーポイントベースの物体検出手法[CorneNet](https://arxiv.org/abs/1808.01244)が提案された。これはコーナーのキーポイントのペアーを使って物体検出を行うアーキテクチャーである。しかしこれはオブジェクトの境界を検出するのは得意だが、ペアのグルーピングを不得意としていた。
そこで新たにオブジェクトのセンターポイントを追加で学習させることにした。


## 2. 先行研究と比べてどこがすごいの？
cornerの情報だけでなくcenterのキーポイントを使用することで正確性が向上した。

## 3. 技術や手法の"キモ"はどこにある？
Corner HeatmapsとCenter Heatmapsの両方を用いてオブジェクトを検出している点。
### Loss
![スクリーンショット 2020-03-30 11 53 48](https://user-images.githubusercontent.com/40351074/77870723-24acbc00-727d-11ea-875e-bf75c6a8f92e.png)

## 4. どうやって有効だと検証した？
MSCOCOのデータセットを使って物体検出を行い、各手法ごとのAPを求めた。  
結果は以下のグラフ。

![スクリーンショット 2020-03-30 12 01 26](https://user-images.githubusercontent.com/40351074/77871159-3478d000-727e-11ea-96f4-2aeb0b00aecf.png)


## 5. 議論はあるか？
センターポイントの検出に失敗すると正しくバウンディングボックスを出力できなくなる。
MSCOCOの真値を使ってcenter keypointを学習させたら以下のようにスコアが向上することが確認できた。

![スクリーンショット 2020-03-30 12 04 55](https://user-images.githubusercontent.com/40351074/77871369-def0f300-727e-11ea-8b1e-418e8d92380b.png)


## 6. 次に読むべき論文はあるか？
- [CorneNet](https://arxiv.org/abs/1808.01244)
- [Faster R-CNN](https://arxiv.org/abs/1506.01497)

### github
* https://github.com/xingyizhou/CenterNet

### 論文情報・リンク

* [Kaiwen Duan, Song Bai, Lingxi Xie, Honggang Qi, Qingming Huang, Qi Tian，CenterNet: Keypoint Triplets for Object Detection, 2019](https://arxiv.org/abs/1904.08189)
