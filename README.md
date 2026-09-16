amount_cols = df_out.columns[2:]
     # 判断：该行金额区域全部是NaN
     all_empty_mask = df_out[amount_cols].isna().all(axis=1)
     # 只对不是全空的行补0
     target_rows = ~all_empty_mask
     df_out.loc[target_rows, amount_cols] = df_out.loc[target_rows, amount_cols].fillna(0)
     return df_out