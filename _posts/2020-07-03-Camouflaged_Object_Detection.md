---
layout: post
title: Towards Real-Time Multi-Object Tracking
summary: 物体検出+トラッキングを行うワンショットアーキテクチャー(JDE)
featured-img: camouflaged
categories: CV ObjectDetection COD
---

## Abstract
- 周囲にシームレスに溶け込む物体の検出を目的としたCamouflaged Object Detection(COD)を行う。
- CODのために新たなデータセットを作成。


**COD10K**  

カテゴリー数 : 78class  
画像数 : 10,000枚   
アノテーションの内容:   
category, bounding-box, object-/instance-level, and mattinglevel labels    
- CODのための新たなデータセットを作成   
Search Identification Network (SINet)
 
## introduction

### 応用例
- medical image segmentation
- agriculture
- art

## 関連研究
### Generic and Salient Object Detection
**Salient Object Detection (SOD)**    

### Dataset
<img width="324" alt="" src="https://user-images.githubusercontent.com/40351074/84623386-1edc8380-af1a-11ea-8453-0def710e9c88.png"> 


## 提案するデータセット
<img width="524" alt="" src="https://user-images.githubusercontent.com/40351074/84668124-29207100-af5e-11ea-908d-a047569524a2.png">


**データセット作成のゴール**  
(1) to provide a new challenging task   
(2) to promote research in a new topic   
(3) to spark novel ideas   

### Image Collection
5,066 camouflaged    
3,000 background    
1,934 noncamouflaged    

### Professional Annotation


### Dataset Features and Statistics

## 提案するフレームワーク
<img width="524" alt="" src="https://user-images.githubusercontent.com/40351074/84668240-59680f80-af5e-11ea-89c8-26a582cb17b8.png">

searchModuleとidentification moduleの二つを作成した
### Search Module (SM)
RFコンポーネントは以下の論文を参考にしている   
> [Songtao Liu, Di Huang, et al. Receptive field block net for
accurate and fast object detection](https://github.com/TakeruEndo/paper-survey/issues/36)
### Identification Module (IM)
以下の論文のe partial decoder component (PDC)を拡張して識別器を作成した。  
>  Cascaded partial decoder for fast and accurate salient object detection
既存の文献では、注意メカニズムが無関係な特徴からの干渉を効果的に除去できることが示されていた


## 結果
<img width="524" alt="" src="https://user-images.githubusercontent.com/40351074/84669644-0d1dcf00-af60-11ea-926d-16805decc8dd.png">


## 次に読む論文
- Ting Zhao and Xiangqian Wu. Pyramid feature attention network for saliency detection. In IEEE CVPR, pages 3085– 3094, 2019.  
浅い層の低レベルの特徴は物体の境界を構築するための空間的な詳細を保持し、深い層の高レベルの特徴は物体の位置を特定するための意味的な情報を保持することが示されている


### 論文情報・リンク
* [Deng-Ping Fan, Ge-Peng Ji, Guolei Sun, Ming-Ming Cheng, Jianbing Shen, Ling Sha，"Camouflaged Object Detection，"CVPR2020，2777-2787，2020](http://openaccess.thecvf.com/content_CVPR_2020/html/Fan_Camouflaged_Object_Detection_CVPR_2020_paper.html)
