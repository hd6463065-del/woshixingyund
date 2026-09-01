from openpyxl.styles import Border, Side

thin = Side(style="thin")
thick = Side(style="thick")

def get_border(col_type: str, is_last: bool):
    bot = thick if is_last else thin
    if col_type == "first":
        return Border(left=thick, right=thin, top=thin, bottom=bot)
    elif col_type == "middle":
        return Border(left=thin, right=thin, top=thin, bottom=bot)
    elif col_type == "last":
        return Border(left=thin, right=thick, top=thin, bottom=bot)
    else:
        raise ValueError("col_type必须是 first / middle / last")

total_cnt = len(rpt_detail_df)



for index, row in rpt_detail_df.iterrows():
    is_last = index == total_cnt - 1

    # B 首列 first
    cell = work_sheet[get_cell(a["b"], index)]
    cell.value = row["b"]
    cell.border = get_border("first", is_last)

    # C 中间列 middle
    cell = work_sheet[get_cell(a["c"], index)]
    cell.value = row["c"]
    cell.border = get_border("middle", is_last)

    # D 末列 last
    cell = work_sheet[get_cell(a["d"], index)]
    cell.value = row["d"]
    cell.border = get_border("last", is_last)
