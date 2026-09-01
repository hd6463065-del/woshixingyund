def get_cell(base_addr: str, index: int) -> str:
     """输入基础单元格"A10"，index=0返回A10，index=1返回A11"""
     base_row = int(re.search(r"\d+$", base_addr).group())
     new_row = base_row + index
     return re.sub(r"\d+$", str(new_row), base_addr)
 # -----使用-----
 for index, row in rpt_detail_df.iterrows():
     work_sheet[get_cell(detail_cells["hojin_no"], index)] = row["hojin_no"]