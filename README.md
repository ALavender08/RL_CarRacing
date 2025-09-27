# 🏎️ RL_CarRacing

## 科展專題：應用強化學習與生成網路於自動駕駛訓練
> 作者: 吳苡柔、黃品薰、郭依瑾　　指導老師: 邱崑山、段雅培

### 📌 專題簡介

本研究以 **OpenAI Gym CarRacing** 環境為平台，探討如何利用 **深度強化學習 (Deep Reinforcement Learning)** 及 **生成式模型 (AE/VAE)** 來訓練自動駕駛代理人。
透過不同演算法、感知方式及獎勵機制的比較，分析其對模型表現與學習效率的影響，期望能找到更穩定且高效的自動駕駛訓練方式。

---

### 🎯 研究動機

* 2025 CES 展示了自動駕駛的未來潛力，啟發我們探索其實現方式。
* 強化學習可透過「嘗試錯誤」讓智能體學會駕駛決策。
* 我們希望結合 **DQN 改進演算法** 與 **生成式 AI (AE/VAE)**，提升自動駕駛智能體的穩定性與表現。

---

### ⚙️ 研究方法

1. **演算法實驗**

   * DQN
   * Double DQN
   * Dueling DQN

2. **探索策略**

   * ε-greedy 演算法
   * 不同 ε 衰減策略比較

3. **環境改寫**

   * 裁切影像：96×96 → 84×84 → 72×72
   * 修改獎勵機制：鼓勵車輛保持賽道中央
   * Replay Buffer 改進：由均勻採樣 → 步數加權採樣
   * 增加「出界即終止」條件，模擬真實駕駛環境

4. **感知 AI 實驗**

   * 使用不同觀測空間：空照圖、車前影像、感知融合
   * 加入生成式 AI：

     * AE (AutoEncoder)
     * VAE (Variational AutoEncoder)

---

### 🖥️ 實驗設備

* **硬體**：Nvidia Jetson Orin 16GB
* **軟體**：Python 3.10、PyTorch、Google Colab

---

### 📊 研究結果

1. **演算法比較**

   * Dueling DQN > DQN > Double DQN
   * Dueling DQN 收斂較快，表現最穩定。

2. **探索策略**

   * 衰減係數 x=5 表現最佳。
   * 適度探索 + 收斂能平衡學習速度與最終表現。

3. **獎勵機制**

   * 修改後能加快前期學習速度，提升探索效率。

4. **感知方式**

   * 車前影像比空照圖更接近真實，初期學習更快，但後期表現略不穩定。
   * 感知融合未優於單一輸入，可能因環境過於簡單。

5. **生成式 AI 輔助**

   * VAE 效果優於 AE，泛化能力較強。
   * AE/VAE 在探索期能加快學習，但貪婪階段表現略差。

6. **Replay Buffer 改進**

   * 「步數加權採樣」能改善出界即終止所造成的早期重複學習問題。

---

### 📌 結論

* **最佳演算法**：Dueling DQN
* **最佳探索策略**：ε 衰減係數 = 5
* **最佳獎勵設計**：以賽道中央為基準修正獎勵
* **生成式 AI**：VAE 較有潛力提升泛化性
* **改進方向**：

  * 增加真實模擬環境複雜度
  * 探索連續動作空間的演算法（如 DDPG, SAC）
  * 加入緩衝區設計，提升安全性與補救能力

---

### 📎 參考文獻

* Mnih et al. (2015). *Human-level control through deep reinforcement learning*. Nature.
* Wang et al. (2016). *Dueling Network Architectures for Deep Reinforcement Learning*. arXiv.
* Sutton & Barto. *Reinforcement Learning: An Introduction*.
* 其他參考來源包含 Medium、IBM、Udacity 等。

---
> 獲得高雄市第65屆科展_資訊組，團體合作獎
