import pandas as pd

df = df.astype(object).where(pd.notna(df), "")