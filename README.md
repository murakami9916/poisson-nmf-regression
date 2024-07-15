[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

# Poisson Non-negative Matrix Factorization for Linear Regression

# Model
下記にこのモデルのグラフィカルモデルを示す．

![image](image/prob_model.jpg)

## Matrix factorization
観測されたスペクトルデータセット$`X \in \mathbb{R}_{+}^{D \times N}`$は期待値を$`\Lambda`$とする$Poisson分布$`\mathcal{P}(\lambda)`$から生成されると仮定すると：

$$
    X \sim \mathcal{P}(\Lambda)　\text{where}　\Lambda = WH.
$$

ここで，$`\Lambda`$は$`K`$次元の潜在変数により行列分解できると仮定する．$D$はエネルギー方向の次元数で，次元$N$はサンプル方向の次元数である．

基底スペクトル$`W \in \mathbb{R}_{+}^{D \times K}`$，潜在変数$`H \in \mathbb{R}_{+}^{K \times N}`$は，それぞれ非負を仮定するため，ガンマ分布$`\mathcal{G}(a, b)`$から生成する：

$$
    W \sim \mathcal{G}(a_W, b_W), \text{}　H \sim \mathcal{G}(a_H, b_H).
$$

## Regression
目的変数$`\boldsymbol{y} \in \mathbb{R}^{N}`$は，潜在変数を係数$`\boldsymbol{\beta} \in \mathbb{R}^{K}`$による線形和で表現でき，分散$`\sigma^2`$のガウス分布から生成されると仮定する：

$$
    \boldsymbol{y} \sim \mathcal{N}(\mu_y = \boldsymbol{\beta} H, \sigma_y^2=\sigma^2)
$$

回帰係数$`\boldsymbol{\beta}`$と分散$`\sigma^2`$はそれぞれガウス分布と半正規分布から生成されると仮定する．サンプリングにおいては，回帰係数$`\boldsymbol{\beta}`$は，最小２乗法により確定的に推定する．

# Example

## 真のスペクトル基底

![image](https://github.com/user-attachments/assets/20038f1f-d5c5-41fb-b03c-19727be0b8e8)


## 真のターゲット変数の生成

真の重み係数$`\beta_{t}`$を$`\beta_{t} = (1.0, 1.5, -1.0, -1.5)^{\top}`$に設定した．  
ターゲット変数の真の観測ノイズ$`\sigma_t`$は$`\sigma_t=0.7`$に設定した．

生成したデータ

![image](https://github.com/user-attachments/assets/ea01e497-9bec-4edc-a869-b11d90ced3da)


