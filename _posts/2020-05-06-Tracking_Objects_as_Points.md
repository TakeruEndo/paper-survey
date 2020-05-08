---
layout: post
title: Tracking Objects as Points
summary: CenterNetの技術をトラッキングに適応させた
featured-img: detection
categories: CV ObjectTracking
---

## 1. どんなもの？
- 検出とトラッキングを兼ね備えたアーキテクチャーであるCenterTrackの提案  
- 物体のセンターポイントを検出し、各フレーム間でセンターポイントを関連づけることでトラッキングを実現
- 現在と過去の２枚の画像とヒートマップを与えるだけで現在のフレームの検出オフセットと追跡オフセットを取得できる
- detectorにはcenternetを採用
<img width="727" alt="スクリーンショット 2020-04-07 13 47 48" src="https://user-images.githubusercontent.com/40351074/78631119-67524200-78d6-11ea-9162-3413714eda13.png">


### 4.1  Tracking-conditioned detection
centernetは追跡に必要な値をすでに取得していた。
- object locations pˆ  
- their size ˆs = Sˆp^  
- confidence measure wˆ = Yˆp   
しかし、そのフレームで隠れているものは検出できない。時間的コヒーレンスを高めるためには過去の画像を与えてやる必要がある。CenterTrackはCenterNetにさらに4つの入力チャネルを与えている。
<img width="725" alt="スクリーンショット 2020-04-07 18 10 56" src="https://user-images.githubusercontent.com/40351074/78651385-3d5f4680-78fb-11ea-94e4-ee8c892b927c.png">

### 4.2 Association through offsets
各フレームのオブジェクトに対して、サイズなどを求める時と同様の回帰をして関連付けを行う。ロス関数は以下。
<img width="385" alt="スクリーンショット 2020-04-07 18 49 14" src="https://user-images.githubusercontent.com/40351074/78655200-a39a9800-7900-11ea-86a0-bd094802d446.png">

## 2. 先行研究と比べてどこがすごいの？
ポイントベースの検出とトラックングのため簡易であること

## 3. 技術や手法の"キモ"はどこにある？
CenterNetとCenterTrackの違いは入力が４つ加わったのと出力が二つになったことだけ。

## 4. どうやって有効だと検証した？
MOT17-challengeにおいて、67.3%のMOTAと22fpsを実現  
KITTI tracking benchmarkでは、89.4%のMOTAと15fpsを実現

<img width="640" alt="スクリーンショット 2020-04-07 21 05 26" src="https://user-images.githubusercontent.com/40351074/78667241-8cb17100-7913-11ea-840c-1051ba8982c0.png">

## 5. 議論はあるか？
dataaugmentationをうまく実装しないと精度が出ない？

## 6. 次に読むべき論文はあるか？

### github
* https://github.com/xingyizhou/CenterTrack

### 論文情報・リンク

* [Xingyi Zhou, Vladlen Koltun, Philipp Krähenbühl, Tracking Objects as Points，2020](https://arxiv.org/abs/2004.01177)
