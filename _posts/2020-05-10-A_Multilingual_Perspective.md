---
layout: post
title: Cross-modal Speaker Verification and Recognition A Multilingual Perspective
summary: 顔と声による生体認証を他言語でも使用できるかを検証した
featured-img: system
categories: Multimodal Biometrics
---

## 概要
生体認証アプリケーションにおいて、顔と声の関連性の発見が急増している。
本論文では，同一人物が話す複数の言語にまたがる顔と声の関連性を確立するという困難な課題を紹介している。また、本論文の目的は以下の二つの疑問を解消することにある。

- 顔と声の関連付けは言語に依存しないのか
- 話し手は話し言葉に関係なく認識されるのか

<img width="400" alt="スクリーンショット 2020-05-10 10 43 10" src="https://user-images.githubusercontent.com/40351074/81489074-61bc9300-92ac-11ea-897f-c699169daeec.png">

## 関連研究
### Cross-modal Verification Between Faces and Voices
これまではマルチモーダルアプリケーションは画像とテキスト情報を使用することが重傷あったが、近年は視聴覚情報を使用しようとする試みが増加してきた。[33]はクロスモーダルな生体認証において顔と声の関連性を確立した。[26, 32]はembeddingを導入した。
- シングルストリームネットワークを用いて音声情報と視覚情報を抽出
- ディスジョイントマッピングネットワーク

###  Speaker Recognition
- MFCC特徴
- VGG-Vox

<img width="400" alt="スクリーンショット 2020-05-10 10 54 50" src="https://user-images.githubusercontent.com/40351074/81489100-bbbd5880-92ac-11ea-9500-3150570d2e4a.png">


- [33] Nagrani, A., Albanie, S., Zisserman, A.: Seeing voices and hearing faces: Crossmodal biometric matching. In: Proceedings of the IEEE conference on computer
vision and pattern recognition. pp. 8427–8436 (2018)
- [26] . Kim, C., Shin, H.V., Oh, T.H., Kaspar, A., Elgharib, M., Matusik, W.: On learning
associations of faces and voices. In: Asian Conference on Computer Vision. pp.
276–292. Springer (2018)
- [32] Nagrani, A., Albanie, S., Zisserman, A.: Learnable pins: Cross-modal embeddings
for person identity. In: Proceedings of the European Conference on Computer Vision (ECCV). pp. 71–88 (2018)

## データセット
VGGFace2

## 本論
- 'softmax'と'center loss'を併用したCNN(deep face recognition)
- VGGFace2[11]のデータセットを用いてInception ResNet-V1ネットワーク[43]を訓練


### アーキテクチャ
<img width="400" alt="スクリーンショット 2020-05-10 11 01 55" src="https://user-images.githubusercontent.com/40351074/81489174-b3b1e880-92ad-11ea-8c27-fe26cbf8aadd.png">

<img width="400" alt="スクリーンショット 2020-05-10 11 03 00" src="https://user-images.githubusercontent.com/40351074/81489184-d3e1a780-92ad-11ea-9ae2-8dacaf13f43b.png">

## 結果
<img width="400" alt="スクリーンショット 2020-05-10 11 04 48" src="https://user-images.githubusercontent.com/40351074/81489233-16a37f80-92ae-11ea-8ad8-8fcd0f44fbb5.png">

EU分割では平均11.9%、EH分割では平均5.9%、EH分割では平均15.6%、15.7%の性能低下が見られた。
これらの結果は、顔と声の関連付けが言語に依存しないことを明確に示している。性能の低下は、2つの言語のデータ分布が異なることに起因しており、典型的にはドメインシフトとして知られている[41]。

- [41] : Improving predictive inference under covariate shift by weighting
the log-likelihood function
<img width="524" alt="" src="">

<img width="400" alt="スクリーンショット 2020-05-10 11 07 27" src="https://user-images.githubusercontent.com/40351074/81489273-7437cc00-92ae-11ea-953e-7c2bd74af2f8.png">

- 他言語だと性能低下とオーバーフィットが見られる
- しかし、その性能は、聞き取れない言語のランダム分類よりも定量的に優れている
- これらの結果から、話者識別は言語に依存したタスクであると結論づけられる
- さらに、これらの結果は、人間の話者識別性能が未知言語を話す人よりも身近な言語を話す人の方が高いことを示した先行研究[37]と一致している
- 話者検証は言語に依存しないことがわかる

## 問題点と課題
ドメインシフトに対応させること


* [Muhammad Saad Saeed, Shah Nawaz, Pietro Morerio, Arif Mahmood, Ignazio Gallo, Muhammad Haroon Yousaf, Alessio Del Bue，"Cross-modal Speaker Verification and Recognition: A Multilingual Perspective，2020](https://arxiv.org/abs/2004.13780v1)
