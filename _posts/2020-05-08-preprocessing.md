---
layout: post
title: kaggle 前処理①
summary: 前処理基礎
featured-img: 前処理
categories: kaggle pandas
---

# Dataframe操作

## 値の置換
```
df['y'].apply(lambda x : 0 if x < 0 else x)
```

##　条件を満たす行を置換する
```
train.loc[train['batch'] == 2, 'signal'] = train.loc[train['batch'] == 2, 'signal'] -0.3
```

## 2つの条件を満たす値を置換する
```
train.loc[(train['batch'] == 3) &  (train['signal'] < -1.6), 'signal'] = -1.6
train.loc[(train['batch'] == 7) &  (train['signal'] < -1.8), 'signal'] = -1.8
```

# エンコード
## ワンホットエンコード(特定の文字を含むか否か)
```
data = train['column'].map(lambda x: 1 if '１' in str(x) else 0)
```

## ラベルエンコーディング
```
from sklearn.preprocessing import LabelEncoder


categorical_features = ['Type', 'Region']

for c in categorical_features:
    le = LabelEncoder()
    le.fit(data[c])
    data[c] = le.transform(data[c])
```

# 数値処理
欠損値を平均値・中央値を求める
```
def calc_mean_median(df, df_type):
    dumy = df
    dumy = dumy.dropna()
    dumy = dumy.astype(df_type)
    df = df.fillna(dumy.mean())
    df = df.astype(df_type)
    return df
```

# 特徴量の追加
## groupごとにidを振る
```
train['building_id'] = train.groupby(['MunicipalityCode', 'TimeToNearestStation','BuildingYear', 'Structure', 'Use', 'NearestStation', 'FloorPlan']).grouper.group_info[0]
```

## groupごとに平均・最大などを取る
```
df['max'+c] = df.groupby([c])['signal'].max()
df['min'+c] = df.groupby([c])['signal'].min()
df['std'+c] = df.groupby([c])['signal'].std()
df['mean_abs_chg'+c] = df.groupby([c])['signal'].apply(lambda x: np.mean(np.abs(np.diff(x))))
df['abs_max'+c] = df.groupby([c])['signal'].apply(lambda x: np.max(np.abs(x)))
df['abs_min'+c] = df.groupby([c])['signal'].apply(lambda x: np.min(np.abs(x)))
```

## 移動平均を取る
```
window_sizes = [3,5,10]
for window in window_sizes:
    df["rolling_mean_" + str(window)] = df['signal'].rolling(window=window).mean()
    df["rolling_std_" + str(window)] = df['signal'].rolling(window=window).std()
    df["rolling_var_" + str(window)] = df['signal'].rolling(window=window).var()
    df["rolling_min_" + str(window)] = df['signal'].rolling(window=window).min()
    df["rolling_max_" + str(window)] = df['signal'].rolling(window=window).max()
```

## ラグ特徴量
```
for window in window_sizes:
    df['shift_'+str(window)] = df['signal'].shift(periods=window)
```
