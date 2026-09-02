TART_ROW = 3
 # 取出样板行单元格
 sample_row_cells = ws[SAMPLE_ROW_NUM]
 # 循环数据，一行数据对应一行样式
 for idx, row_data in enumerate(your_data):
     # 计算当前要处理的行号
     current_row = START_ROW + idx
     target_row_cells = ws[current_row]
     # 复制样式
     for sample_cell, target_cell in zip(sample_row_cells, target_row_cells):
         target_cell.style = sample_cell.style.copy()
     
     # 给这一行写入你的业务数据（按列对应）
     target_row_cells[0].value = row_data["name"]   # A列
     target_row_cells[1].value = row_data["age"]    # B列
     target_row_cells[2].value = row_data["amount"] # C列