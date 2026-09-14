import pandas as pd

df = 账票传入的DataFrame

# 第1列，第2列
col1 = df.columns[0]
col2 = df.columns[1]
# 需要填充0的列：第3列往后全部
fill_cols = df.columns[2:]

# 条件1：从第2列开始，**不是全部为空**（第2列往后至少有一个有值）
cond_has_data = ~df.loc[:, col2:].isna().all(axis=1)

# 满足条件的行：第2列往后有数据 → 对 fill_cols（第3列之后）空值填0
df.loc[cond_has_data, fill_cols] = df.loc[cond_has_data, fill_cols].fillna(0)
