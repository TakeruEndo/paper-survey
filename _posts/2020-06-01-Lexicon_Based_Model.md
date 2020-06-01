---
layout: post
title: A Lexicon-Based Supervised Attention Model for Neural Sentiment Analysis
summary: 感情レキシコン+Attentionで感情分析をした
featured-img: bird
categories: NLP
---


## 概要
感情分類タスクにおいてアテンションメカニズムが活用される。それは、全ての語が同程度の重要度を持っているわけではないからだ。しかし、既存のアテンションモデルの多くは感情レキシコンを考慮していなかった。
>言語学における語彙目録（ごいもくろく）、あるいは単に語彙、またはレキシコンもしくはレクシコン（lexicon）とは、言語の知識の一部で、ある言語の全ての丸ごと覚えている単位（語、形態素、イディオムなど）の形式・意味・文法的特性についての知識の総体である。(語彙目録 - Wikipedia)

そこで感情表現に注釈したRNNモデルであるlexicon-based supervised attention model (LBSA)を提案する。

## 導入
- 感情分析の結果を改善するために大規模な感情レキシコンが作られている。これは語に対してpositive or negativeのスコアづけがされている。
- レキシコンによって分類性能が大幅に向上した
- 感情レキシコンにはセンチメント強度(文の感情表現に対する単語の貢献度)がある
- 上記はアテンションメカニズムと同じ考え方ができる
- ローカルの文章の中だけで学習させると、固有表現（映画のタイトル)などに引っ張られてうまく感情を分析できていないという問題があった  
  
### そこで...!
感情レキシコンとアテンションメカニズムを組み合わせた新しいアーキテクチャーを提案する。

<img width="524" alt="" src="https://user-images.githubusercontent.com/40351074/83418480-a0360f80-a45e-11ea-9347-33c4cd9f575c.png">

### 本論文の貢献
-  本モデルは文章中の感情内容を正確に識別し、正確な感情情報を取得することができる
- ノイズが少ないモデルを作成した
- ３つの感情分析データセットでSOTAを達成(IMDB, Yelp13, Yelp14)

## 評価
- AccuracyとRMSEを使用

* [Yicheng Zou, Tao Gui, Qi Zhang, Xuanjing Huang，"A Lexicon-Based Supervised Attention Model for Neural Sentiment Analysis，"ACL，2018](https://www.aclweb.org/anthology/C18-1074/)

