# 在修改 border 前后分别打印
st.write(f"修改前格式: {cell.number_format}")
st.write(f"修改前值类型: {type(cell.value)}")

cell.border = thin_border

st.write(f"修改后格式: {cell.number_format}")
st.write(f"修改后值类型: {type(cell.value)}")
