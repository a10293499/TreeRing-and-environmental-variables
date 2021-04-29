# Analyzing the Relationship between Tree-Ring and Environmental variables
## Data analysis in R (Cluster analysis/ PCA/ DCA/ RDA)
 * 資料
    * 資料來源:<https://www.ncdc.noaa.gov/data-access/paleoclimatology-data>
    * 物種:*Pinus ponderosa* Douglas (western yellow pine)
    * 介紹:收集的樹輪資料均位於美國地區且為同一物種，但為四個不同作者(Brubaker, Dean, Graulich and Graybil)提供，樣木的位置也有落差
    * ![樣木分布位置](https://github.com/a10293499/TreeRing-and-environmental-variables/blob/main/%E6%A8%A3%E6%9C%A8%E5%88%86%E5%B8%83.PNG)
       * 圖1:樣木分布位置(Red: Brubaker; green: Dean; blue: Graulich; purple: Graybil)
    * 資料為每一年[樹輪輪寬寬度](https://github.com/a10293499/TreeRing-and-environmental-variables/blob/main/chronology%20data.csv)(chronology data)及[每一樣木分布位置及海拔](https://github.com/a10293499/TreeRing-and-environmental-variables/blob/main/chronology%20env%20data.csv)(chronology env data)
 * 目標
    * 由於樹木生長受環境很大影響，通常溫度較溫暖雨量較多，可生長較快造成輪寬較大，反之。Danek et.al (2017) 藉由排序分析發現Carpathian山脈的樹木年輪樹輪與經度（海拔）之間有關係，樹輪會隨著經度的變化而變化。  因此我想知道在其他地區是否仍然有這樣的關係。此外，他們在分析中沒有添加環境變量，因此在本研究中也會加入環境因子進行分析。
    

 * 方法
    * Classification
    > - 以hierarchical agglomerative clustering (Ward’s method)進行分析，k值設定為4，因為資料來自大致來自於4個不同的地方(部分重疊)，能否單純藉由輪寬將四個來源區分開來。
    * Detrended Correspondence Analysis(DCA) and Principle Component Analysis(PCA)
    > -  用DCA決定是linear 或 unimoda，假如第一象限的DCA小於3D則使用linear
    > -  PCA用來將3D降維成2D
    * Redundancy Analysis (RDA)
    > - 加入環境因子，以RDA進行分析
    * [R code](https://github.com/a10293499/TreeRing-and-environmental-variables/blob/main/Classification%20and%20Ordination%20analysis)


 * 結果
   * Classification
   > - 從下圖可看出大致可分成四個分群，同個來源通常會被分到同一群內。值得注意的是C3與C4在圖1中看起來距離近，但在分群上卻是最遠的。
   * ![classification](https://github.com/a10293499/TreeRing-and-environmental-variables/blob/main/classification.PNG)
      * 圖2:群聚分析結果
   * DCA & PCA
   > - DCA第一象限小於3SD，因此選擇linear的方法-PCA。
   > - PCA分析中，第一及第二主成分個別解釋了32.67%與9.47%
   * ![PCA](https://github.com/a10293499/TreeRing-and-environmental-variables/blob/main/PCA.PNG)
      * 圖3:PCA分析結果
