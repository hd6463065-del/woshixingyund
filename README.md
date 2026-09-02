cell = ws["B2"]  # ← 改成目标单元格
print(f"格式: {repr(cell.number_format)}")
print(f"值类型: {type(cell.value).__name__}")
print(f"值内容: {repr(cell.value)}")
