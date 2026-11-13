# ML-wifi-localization

DS4023 Machine Learning group project on Wi-Fi indoor localization under simulated access point outages.

本项目用 Wi-Fi 扫描预测楼栋和楼层，研究热点失效时定位准确率如何变化。

## 当前进度

- [项目大纲](./Wi-Fi%20%E7%83%AD%E7%82%B9%E5%A4%B1%E6%95%88%E5%AF%B9%E5%AE%A4%E5%86%85%E6%A5%BC%E5%B1%82%E5%AE%9A%E4%BD%8D%E7%9A%84%E5%BD%B1%E5%93%8D.docx)记录研究问题、实验设计和评价指标。
- [基线实验 Notebook](./02_wifi_outage_experiment.ipynb)保存了逻辑回归在内部验证集上的结果。比较原始扫描、随机停用热点和停用常见热点，故障规模为 5、10、20 个热点。

## 复跑实验

1. 从 [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/310/ujiindoorloc) 下载并解压 UJIIndoorLoc。把 `trainingData.csv` 放到 Notebook 同一目录。官方的 `validationData.csv` 留作最终测试。
2. 在 Python 环境中安装 `jupyterlab`、`pandas`、`numpy` 和 `scikit-learn`。
3. 用 JupyterLab 打开 `02_wifi_outage_experiment.ipynb`，从头运行所有代码格。
