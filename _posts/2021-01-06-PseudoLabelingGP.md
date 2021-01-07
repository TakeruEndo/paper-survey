---
layout: post
title: Pseudo-Labeling Using Gaussian Process for Semi-Supervised Deep Learning
summary: GPを用いてPseudo-Labelingを行った
featured-img: system
categories: CV GaussianProcess
---

## 1. どんなもの？
1) ラベル付きデータでGPCを訓練する。
2) GPCを用いてラベルの付いていないデータのラベルを予測する。
3) ディープラーニングモデルを擬似的にラベル化したデータを用いてモデルを微調整する。
4) ラベル付けされたデータを用いてモデルを微調整する。
## 2. 先行研究と比べてどこがすごいの？
1) 特にサンプル数の少ない問題に適している。GPCでは，ハイパーパラメータを調整するためにラベル化されたデータの小さなセットを必要とするだけである．
2) 実装が簡単である。基本的には、まずGPCを訓練し、その出力をラベル付けされていないデータ上でディープラーニングモデルに送ります。そのため、損失関数の設計や層別学習を行う必要がない。
3) 任意の深層学習モデルとの組み合わせが可能である。擬似ラベルをあたかも真のラベルであるかのように利用している。理論的には、どのような教師付き学習モデルでも利用可能である。

### 論文情報・リンク

* [Zhun Li，"Pseudo-Labeling Using Gaussian Process for Semi-Supervised Deep Learning，"ieee，2018](https://www.computer.org/csdl/proceedings-article/bigcomp/2018/364901a263/12OmNzlUKKR)
