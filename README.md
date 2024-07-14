# Poisson non-Negative Matrix Factorization for Regression

# Model
下記にこのモデルのグラフィカルモデルを示す．
![image](image/prob_model.jpg)

## Matrix factorization
Poisson分布から観測されたスペクトルデータセット$\bm{X} \in \mathbb{R}_{+}^{D \times N}$は：
$$
    X \sim \mathcal{P}(\Lambda) \:\:\:\: \text{where} \:\: \Lambda = WH
$$
で表現されると仮定する．$D$はエネルギー方向の次元数で，次元$N$はサンプル方向の次元数である．

基底スペクトル$\bm{W} \in \mathbb{R}_{+}^{D \times K}$，潜在変数$\bm{H} \in \mathbb{R}_{+}^{K \times N}$は，それぞれ非負を仮定するため，ガンマ分布から生成する：
$$
    W \sim \mathcal{G}(a_W, b_W), \:\:\:
    H \sim \mathcal{G}(a_H, b_H).
$$

## Regression
目的変数$\bm{y} \in \mathbb{R}^{N}$は，潜在変数を係数$\bm{\beta} \in \mathbb{R}^{K}$による線形和で表現でき，分散\sigma^2のガウス分布から生成されると仮定する：
$$
    y \sim \mathcal{N}(\mu_y = \bm{\beta} H, \sigma_y^2=\sigma^2)
$$

回帰係数$\bm{\beta}$と分散$\sigma^2$はそれぞれガウス分布と半正規分布から生成されると仮定する．サンプリングにおいては，回帰係数$\bm{\beta}$は，最小２乗法により確定的に推定する．
