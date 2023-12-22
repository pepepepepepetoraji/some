# 加速度データの可視化

このプロジェクトでは、加速度計から取得したデータを可視化するためのPythonスクリプトを提供しています。Seabornライブラリを使用して、異なるソースからのデータを比較する時系列プロットを作成します。

## 必要条件

以下のライブラリが必要です：

- Python 3.x
- Pandas
- Seaborn
- Matplotlib

これらのライブラリは以下のコマンドでインストールできます：

pip install pandas seaborn matplotlib



## 使用方法

1. **ライブラリのインポート：**
   必要なライブラリをインポートします。

2. **データの読み込みと前処理：**
   3つの異なるCSVファイルを読み込みます。ファイルパスはそれぞれの環境に合わせて変更してください。各データフレームにソース識別子を追加し、データを結合します。

3. **データの可視化：**
   Seabornを使用してデータをプロットします。

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

sns.set_theme(style="darkgrid")

# CSVファイルの読み込み
df_1 = pd.read_csv('file_path_1')
df_2 = pd.read_csv('file_path_2')
df_3 = pd.read_csv('file_path_3')

df_1['source'] = 'No1'
df_2['source'] = 'No2'
df_3['source'] = 'No3'

df = pd.concat([df_1, df_2, df_3])

x_col = 'relative_time'
y_col = 'AccX'
hue_col = 'source'

sns.lineplot(data=df, x=x_col, y=y_col, hue=hue_col)
plt.xlabel(x_col)
plt.ylabel(y_col)
plt.title('加速度計データの時系列プロット')
plt.show()

if __name__ == "__main__":
    main()
