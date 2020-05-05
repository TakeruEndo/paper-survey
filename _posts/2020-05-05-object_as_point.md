---
layout: post
title: Objects as Points
summary: 従来のアンカー方式と違い、キーポイント(センター)を予測することで物体検出を行う
featured-img: article1
categories: CV ObjectDetection
---

## 1. どんなもの？
bboxの中心を予測することで効率的に物体検出を行う。オブジェクトのサイズや向きなどのプロパティは画像の特徴から回帰して求める。

## 2. 先行研究と比べてどこがすごいの？
シンプルな構造であり、NMSの処理なしで高速かつ正確に動作するend-to-endのアーキテクチャーであること。またobject detectionのみならず、pose estimation・ 3D detectionなど様々なタスクにも利用できる。

## 3. 技術や手法の"キモ"はどこにある？
オブジェクトの表現として新しく中心座標を使用したこと

## 4. どうやって有効だと検証した？
COCO test-devを使って検証したところ、他のSOTの手法より高速であることがわかった。
<img width="682" alt="center-result" src="https://user-images.githubusercontent.com/40351074/77842798-a47d4c80-71d1-11ea-9087-7cdd1d5fd5b2.png">

## 5. 次に読むべき論文はあるか？
- [Deep Layer Aggregation](http://openaccess.thecvf.com/content_cvpr_2018/papers/Yu_Deep_Layer_Aggregation_CVPR_2018_paper.pdf)
- [CenterNet: Keypoint Triplets for Object Detection](https://arxiv.org/abs/1904.08189)
### github
* https://github.com/xingyizhou/CenterNet
### 論文情報・リンク

* [Xingyi Zhou, Dequan Wang, Philipp Krähenbühl, Objects as Points, 16 Apr 2019 ](https://arxiv.org/abs/1904.07850)