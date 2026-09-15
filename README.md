amount_df = rpt_detail_df.iloc[:, 2:]
has_any_amount = amount_df.notna().any().any()
flag_delete_total_row = not has_any_amount
