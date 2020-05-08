---
layout: post
title: kaggle データ可視化
summary: seaboen, matplotlib基礎
featured-img: data
categories: kaggle seaborn matplotlib
---

## ヒストグラム
```
import seaborn as sns
sns.distplot(train['y']);
```

<img width="524" alt="" src="{{ site.url }}{{ site.baseurl }}/assets/img/posts/ヒストグラム.png">

## 散布図
### 2値の比較
```
sns.jointplot('MunicipalityCode', 'y', a)
```
<img width="524" alt="" src="{{ site.url }}{{ site.baseurl }}/assets/img/posts/散布図2.png">

### 参考
https://qiita.com/hik0107/items/3dc541158fceb3156ee0


### 一括表示
```
sns.pairplot(train)
```
<img width="524" alt="" src="{{ site.url }}{{ site.baseurl }}/assets/img/posts/散布図一括.png">

## ヒートマップ
```
# data.corr()で相関を一括で取得
fig, ax = plt.subplots(figsize=(12, 9)) 
sns.heatmap(data.corr(), square=True, vmax=1, vmin=-1, center=0)
# plt.savefig('seaborn_heatmap_corr.png')
```
<img width="524" alt="" src="{{ site.url }}{{ site.baseurl }}/assets/img/posts/ヒートマップ.png">

## 全データ可視化
```
plt.figure(figsize=(20,5))
res = 10
plt.plot(range(0,train.shape[0],res), train.y[0::res])
# 並べて表示も可能
# plt.plot(range(0,sub4.shape[0],res), y_pred_2[0::res])

plt.title('Test Data Predictions',size=16)
plt.show()
```
<img width="524" alt="" src="{{ site.url }}{{ site.baseurl }}/assets/img/posts/全データ.png">
