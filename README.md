# ML-wifi-localization

DS4023 Machine Learning group project on Wi-Fi indoor localization under simulated access point outages.

本项目根据 Wi-Fi 信号预测楼栋和楼层，比较不同热点停用情景下的定位准确率。楼栋和楼层都预测正确才计为正确。

## 当前进度

- [项目大纲](./Wi-Fi%20%E7%83%AD%E7%82%B9%E5%A4%B1%E6%95%88%E5%AF%B9%E5%AE%A4%E5%86%85%E6%A5%BC%E5%B1%82%E5%AE%9A%E4%BD%8D%E7%9A%84%E5%BD%B1%E5%93%8D.docx)记录研究问题、实验设计和评价指标。
- [实验 Notebook](./02_wifi_outage_experiment.ipynb)包含逻辑回归基线、10% 和 20% 遮挡训练对照、按采集位置分组的五折验证，以及独立测试。两种遮挡设置在停用 20 个常见热点时都只在 5 折中的 2 折超过普通训练，因此独立测试使用普通逻辑回归。

## 独立测试结果

用全部 19,937 条训练记录拟合模型，在官方预留的 1,111 条记录上测试。常见热点按训练集里的检测次数排序，随机停用每档取 20 组的平均值。

| 停用热点数 | 随机停用 | 停用最常见热点 |
| ---: | ---: | ---: |
| 0（原始扫描） | 88.21% | 88.21% |
| 5 | 88.03% | 87.76% |
| 10 | 87.70% | 86.05% |
| 20 | 87.25% | 82.99% |

停用 20 个热点时，随机停用使准确率下降 0.95 个百分点，停用最常见的 20 个使准确率下降 5.22 个百分点。

## 复跑实验

1. 从 [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/310/ujiindoorloc) 下载并解压 UJIIndoorLoc。把 `trainingData.csv` 和 `validationData.csv` 放到 Notebook 同一目录。后者只用于最后的独立测试。
2. 复跑时可使用 Python 3.12。运行过的主要库版本为 `pandas==2.2.2`、`numpy==1.26.4`、`scikit-learn==1.9.1` 和 `scipy==1.17.1`。在同一环境中安装 `jupyterlab` 和 `ipykernel`。
3. 在 Notebook 所在目录启动 JupyterLab，打开 `02_wifi_outage_experiment.ipynb`，选择已安装这些依赖的 Python 3 内核，从头运行所有代码格。五折训练会花较长时间。
