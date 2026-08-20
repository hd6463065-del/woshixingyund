import streamlit as st
import openpyxl
from io import BytesIO
from snowflake.snowpark.context import get_active_session

session = get_active_session()

if st.button("账票生成"):

    # 1. 从 Stage 下载模板到临时目录
    session.file.get(
        "@MY_STAGE/templates/invoice_template.xlsx",
        "/tmp/invoice"
    )

    # 2. 读取模板
    wb = openpyxl.load_workbook(
        "/tmp/invoice/invoice_template.xlsx"
    )

    ws = wb["Sheet1"]

    # 3. 写入数据
    ws["B2"] = "株式会社ABC"
    ws["B3"] = "2026/08/20"
    ws["B4"] = 10000

    # 4. 写回内存，不需要再保存到 Stage
    output = BytesIO()
    wb.save(output)
    output.seek(0)

    # 5. 传给前画面，让用户下载
    st.download_button(
        label="账票をダウンロード",
        data=output,
        file_name="invoice.xlsx",
        mime="application/vnd.openxmlformats-officedocument.spreadsheetml.sheet"
    )