# 美國西南部樹輪生長與環境因子之排序分析 
### Dendrochronology Ordination Analysis: Environmental Drivers of *Pinus ponderosa* in Southwestern USA

[![R-Version](https://img.shields.io/badge/R-4.2+-blue.svg)](https://www.r-project.org/)
[![Quarto](https://img.shields.io/badge/Rendered%20with-Quarto-emerald)](https://quarto.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 專案簡介
本專案探討美國西南部 **西黃松 (*Pinus ponderosa*)** 的樹輪寬度（Chronology）與地理環境因子之間的交互關係。透過一系列統計排序分析（Ordination），量化緯度、經度與海拔對長期生長趨勢的解釋力 。

### 研究目標
* **空間異質性分析**：探討不同來源區的樹輪樣本是否能單純藉由生長規律進行區分 。
* **環境驅動力量化**：驗證地理梯度（經緯度、垂直高度）如何共同約束樹木的生長。

---

## 資料說明
* ]**資料來源**：[NOAA Paleoclimatology Data](https://www.ncdc.noaa.gov/data-access/paleoclimatology-data) 。
* **研究物種**：*Pinus ponderosa* Douglas (Western yellow pine) 。
* **樣區範圍**：包含 72 個樣區，分布於美國西南部（包含 Brubaker, Dean, Graulich, Graybil 等作者提供之資料） 。
* **資料處理**：排除生長年份小於 100 年的樣本，並篩選重疊年份區間以確保分析一致性。

---

## 分析流程與核心發現

### 1. 階層式群聚分析 (Hierarchical Clustering)
採用 **Ward's Method** 與歐基里德距離進行分析 。
* **結果**：將樣區初步歸類為 4 個主要群聚 (C1~C4) 。
* **洞察**：同來源樣本大多歸於同群，但 C3 與 C4 雖地理距離近，樹輪特徵卻最遠，顯示非地理因子之潛在影響 。

### 2. 排序分析 (Ordination)
* [cite_start]**DCA 檢測**：第一軸梯度長度為 **0.698 (< 3 S.D.)**，證實樣區生長特徵呈線性反應，適用 PCA 模型 。
* **PCA + Environmental Fitting**：
    * [cite_start]**緯度 ($r^2=0.686$)**：解釋力最強，與 PC1 呈強烈負相關 。
    * [cite_start]**海拔 ($r^2=0.417$)** 與 **經度 ($r^2=0.362$)**：與 PC1 呈正相關。
* **RDA (冗餘分析)**：
    * [cite_start]**總解釋率**：環境模型對整體資料的淨貢獻度為 **23.6% (Adjusted $R^2$)** 。
    * [cite_start]**軸向特徵**：RDA1 主要捕捉了「緯度」與「海拔/經度」對立所構成的南北梯度 。

---

## 視覺化呈現
本專案透過 Quarto 生成動態報告，包含以下視覺化組件：
* **Leaflet 互動式地圖**：呈現樣區地理分布與原始作者分類 。
* **PCA & RDA Biplots**：視覺化環境因子向量對樣區生長的拉扯關係。

---

## 使用套件
本專案主要使用以下 R 套件進行開發：
* `vegan`: 核心排序分析 (DCA, PCA, RDA, envfit)
* `dendextend`: 樹狀圖美化與標註
* `leaflet`: 互動式地圖繪製
* `quarto`: 自動化學術報告生成

---

