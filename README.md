import pandas as pd
df = df.astype(object).where(pd.notna(df), "")
value = a.iloc[0][b].replace("/", "")