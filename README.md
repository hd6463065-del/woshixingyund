import streamlit as st
import os

# ========== 这就是RPT_TMP_FILE_MAPPING 映射 ==========
RPT_TMP_FILE_MAPPING = {
    "JA": {
        "template_file_nm": "invoice_ja.xlsx",
        "template_full_path": os.path.join("report_template", "invoice_ja.xlsx")
    },
    "ZH": {
        "template_file_nm": "invoice_zh.xlsx",
        "template_full_path": os.path.join("report_template", "invoice_zh.xlsx")
    },
    "EN": {
        "template_file_nm": "invoice_en.xlsx",
        "template_full_path": os.path.join("report_template", "invoice_en.xlsx")
    }
}

# 画面：选择出力言語
output_lang = st.selectbox("出力言語", ["JA","ZH","EN"])

# =====等价于 RPT_TMP_FILE_MAPPING[変数.出力言語].values()=====
# 根据语言取出这条mapping记录
mapping_row = RPT_TMP_FILE_MAPPING.get(output_lang)

if not mapping_row:
    st.error(f"{output_lang} に対応するテンプレートマッピングが存在しない")
else:
    st.write("取得したマッピング情報", mapping_row)
    # 读取xlsx二进制
    with open(mapping_row["template_full_path"], "rb") as f:
        xlsx_bytes = f.read()

    st.download_button(
        label="テンプレートダウンロード",
        data=xlsx_bytes,
        file_name=mapping_row["template_file_nm"],
        mime="application/vnd.openxmlformats‑officedocument.spreadsheetml.sheet"
    )
