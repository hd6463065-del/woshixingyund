res = rpt_detail_df.loc[:, col3:].isna().all().all()
sumVisibleFlug = not res