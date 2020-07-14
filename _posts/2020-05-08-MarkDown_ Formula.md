---
layout: post
title: Markdown Formula
summary: 数式のチートシート
featured-img: formula
categories: Markdown
mathjax: True
---

## 数式の記述
`mathjax: True`を設定する

```
$$
\begin{align*}

LaTexの数式＿1  \\
LaTexの数式＿2

\end{align*}
$$
```

$$
\begin{align*}

LaTexの数式＿1  \\
LaTexの数式＿2

\end{align*}
$$

## 単行で記述

```
$$ e^{i\theta} = \cos\theta + i\sin\theta $$
```

$$ e^{i\theta} = \cos\theta + i\sin\theta $$

## イコール(＝)を揃える

```
$$
\begin{align*}

f(x) &= x^2+3x+2 \\
&= (x+1)(x+2)

\end{align*}
$$
```


## 極限(lim)
```
$$
\begin{align}

\lim_{x \to \infty} f(x) \\
\lim_{h \to 0} \frac{f(x+h)-f(x)}{h} \\
\lim_{\substack{x \to \infty \ y \to \infty}} f(x,y)

\end{align}
$$
```

$$
\begin{align}

\lim_{x \to \infty} f(x) \\
\lim_{h \to 0} \frac{f(x+h)-f(x)}{h} \\
\lim_{\substack{x \to \infty \ y \to \infty}} f(x,y)

\end{align}
$$


## 平方根
```
\sqrt{a^2+b^2} \\
\sqrt[3]{a}
```

$$
\begin{align*}

\sqrt{x^2+y^2} \\
\sqrt[5]{a}

\end{align*}
$$

## 様々な数式
```
# 対数オッズ線型表現
logit(p=(y=1|x))=w_0x_0+w_1x_1+\cdots+w_mx_m = \sum_{i=0}^{m}w_ix_{i} = w^{\mathrm{T}}x

```



## 参考記事
- [Qiitaの数式チートシート](https://qiita.com/PlanetMeron/items/63ac58898541cbe81ada)
