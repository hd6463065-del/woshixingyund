ws.unmerge_cells("A8:B8")
    # 解除合并完成之后，再删除行
    ws.delete_rows(idx=8, amount=1