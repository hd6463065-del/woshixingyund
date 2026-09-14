import pandas as pd

df = 账票传入的DataFrame

if not df.empty:
    # 第2列往后
    cols_2plus = df.columns[1:]
    fill_cols = df.columns[2:]

    # 判断：第2列往后全部是空(空字符串 / NaN)
    all_empty = df[cols_2plus].apply(lambda r: all(pd.isna(x) or x=="" for x in r), axis=1)
    
    # 非全部空的行，第3列起空填0
    df.loc[~all_empty, fill_cols] = df.loc[~all_empty, fill_cols].fillna(0)
