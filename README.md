ws.unmerge_cells("A8:B8")
    # 解除合并完成之后，再删除行
    ws.delete_rows(idx=8, amount=1




amount_series = row.iloc[2:]   # iloc从0开始，第3列就是下标2
     if not amount_series.isna().all():
         sumVisibleFlug = True   # 只要本行有数字/0，打开开关；已经是True也没关系，重复赋值True无害