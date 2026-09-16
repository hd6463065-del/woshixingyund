import pandas as pd
import numpy as np

# 你的df
amount_cols = df.columns[2:]

# 按行判断：这一行金额是不是全部为空
mask = df[amount_cols].isna().all(axis=1)

# 不是全部空的行，补0
df.loc[~mask, amount_cols] = df.loc[~mask, amount_cols].fillna(0)
