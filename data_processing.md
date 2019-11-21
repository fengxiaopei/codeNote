# 数据数值编码

from sklearn.preprocessing import LabelEncoder

le = LabelEncoder()

columns = df.columns

for i in columns:
    df[i] = le.fit_transform(df[i])
