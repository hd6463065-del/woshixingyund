import streamlit as st
from openpyxl import load_workbook
from io import BytesIO

# ---------------------- 你封装的Excel处理函数（核心：处理完return结果）----------------------
def process_excel_and_return(template_path: str, save_sheet_name: str, cell_value_map: dict):
    """
    处理Excel模板，赋值后return二进制结果
    :param template_path: 你的模板文件路径/上传的文件对象
    :param save_sheet_name: 要操作的sheet名称
    :param cell_value_map: 要赋值的单元格-值映射，比如 {"A1": "AAA", "B2": 123}
    :return: 处理后的Excel二进制字节
    """
    # 1. 打开模板
    wb = load_workbook(template_path)
    # 2. 取指定sheet
    ws = wb[save_sheet_name]
    # 3. 批量赋值
    for cell_addr, value in cell_value_map.items():
        ws[cell_addr] = value
    # 4. 内存中导出，不写本地磁盘
    bio = BytesIO()
    wb.save(bio)
    # 5. 取出二进制，return出去
    excel_bytes = bio.getvalue()
    return excel_bytes


# ---------------------- 主流程：调用函数，接收return值 ----------------------
if __name__ == "__main__":
    # 1. 上传模板文件
    uploaded_file = st.file_uploader("上传Excel模板", type="xlsx")
    if uploaded_file:
        # 2. 调用处理函数，接收return回来的结果
        processed_excel = process_excel_and_return(
            template_path=uploaded_file,
            save_sheet_name="你的sheet名称",  # 替换成你要操作的sheet名
            cell_value_map={
                "A1": "AAA",
                "B2": "你要赋的其他值",
                "C3": 12345
            }
        )

        # 3. 拿到return值后，2种常用用法
        # 用法1：直接在当前页面生成下载按钮
        st.download_button(
            label="下载处理后的Excel",
            data=processed_excel,
            file_name="出力帳票.xlsx",
            mime="application/vnd.openxmlformats-officedocument.spreadsheetml.sheet"
        )

        # 用法2：存入session_state，跨页面/跳转回前页面使用
        st.session_state["excel_download_bytes"] = processed_excel
