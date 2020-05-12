---
layout: post
title: Towards Real-Time Multi-Object Tracking
summary: 物体検出+トラッキングを行うワンショットアーキテクチャー(JDE)
featured-img: detection2
categories: CV ReID ObjectDetection
---

## 1. どんなもの？
<br>
物体検出とトラッキングを兼ね備えた最初のモデル。  
実行速度：18.8~24.1FPS  
base_architecture: the Feature Pyramid Network (FPN)   

### 今までのMOT

**SDE( Separate Detection and Embedding)の問題点**
- 単純にDetector+EmbeddingModelの実行時間がかかってしまう
- 特徴量を共有できない  

検出器：region proposal network (RPN)(Faster-R-Cnnと同じ)  
Embedding：h the metric learning supervision  
**問題点**
FPSが10以下でReal Timeには程遠い！

## JDEアーキテクチャーの概要

![スクリーンショット 2020-04-17 11 16 49](https://user-images.githubusercontent.com/40351074/79525074-ff051c80-809c-11ea-90ea-3aba4f8fb3d2.png)

1. バックボーンでfeature-mapを作成(3種類)
2. 分類・bbox予測・Re-IDそれぞれに対応するCNNにfeature-mapを流し込んで学習
3. それぞれのheadで予測マップを出力

###  Appearance Embeddings

**triplet loss**

![スクリーンショット 2020-04-17 11 42 28](https://user-images.githubusercontent.com/40351074/79526583-8b650e80-80a0-11ea-9c71-55d375a8f01b.png)
<br>
f^T: アンカーとして選択されたミニバッチ内のインスタンス  
f^+: positive sample

トリプレットロスは学習が不安定になり収束しない問題がある。改善されたlossが以下。
![スクリーンショット 2020-04-17 11 50 07](https://user-images.githubusercontent.com/40351074/79527064-a71ce480-80a1-11ea-9c45-6000e3a2e644.png)

これはクロスエントロピーとかなり似ている！

![スクリーンショット 2020-04-17 11 51 09](https://user-images.githubusercontent.com/40351074/79527105-bef46880-80a1-11ea-8970-52feb36545de.png)

実際本論文ではCEがもっともパフォーマンスがよかってのでこれを適用！

３つのタスクのlossの合計は以下。
![スクリーンショット 2020-04-17 12 47 11](https://user-images.githubusercontent.com/40351074/79530277-dd5e6200-80a9-11ea-99e2-d9f0fca66cd6.png)
- App.Opt
- Uniform
- MGDA-UB_[参照](https://qiita.com/koreyou/items/57c00bc314a68432de25)
- Loss.Norm


### Online Association

カルマンフィルター+ハンガリアンメソッド

### マルチタスクにおける損失加重戦略
![スクリーンショット 2020-04-17 14 57 46](https://user-images.githubusercontent.com/40351074/79536934-228b8f80-80bc-11ea-95b0-c42e79406810.png)

### SDEとJDEの実行速度と精度の比較
![スクリーンショット 2020-04-17 15 05 07](https://user-images.githubusercontent.com/40351074/79537301-f45a7f80-80bc-11ea-9251-3fab671e981f.png)

![スクリーンショット 2020-04-17 15 06 22](https://user-images.githubusercontent.com/40351074/79537327-04725f00-80bd-11ea-8782-45c478af8418.png)

## 2. 先行研究と比べてどこがすごいの？
検出+追跡の初めてのワンショットアーキテクチャーの提案

## 3. 技術や手法の"キモ"はどこにある？
- バックボーンで得た特徴量から３種類の特徴を新しく定義し、マルチタスクな学習を実現している点

## 4. どうやって有効だと検証した？
SDEとJDEの実行速度と精度の比較

## 5. 次に読むべき論文はあるか？
マルチタスク学習におけるlossの定義を学ぶ
- [Multi-Task Learning as Multi-Objective Optimization](Multi-Task Learning as Multi-Objective Optimization)

## 論文情報・リンク

* [Zhongdao Wang, Liang Zheng, Yixuan Liu, Shengjin Wang，"Towards Real-Time Multi-Object Tracking，" 2019](https://arxiv.org/abs/1909.12605)