RPT_TMP_FILE_MAPPING = {
    # -------- 1階：出力言語 --------
    "JA": {
        # -------- 2階：帳票区分 --------
        "INVOICE": {
            # -------- 3階：帳票種別 --------
            "NORMAL": {
                # -------- 4階：ファイル情報 --------
                "template_file_nm": "請求書_通常_JA.xlsx",
                "template_path": "templates/請求書_通常_JA.xlsx"
            },
            "SUM": {
                "template_file_nm": "請求書_集計_JA.xlsx",
                "template_path": "templates/請求書_集計_JA.xlsx"
            }
        },
        "REPORT": {
            "NORMAL": {
                "template_file_nm": "報告書_JA.xlsx",
                "template_path": "templates/報告書_JA.xlsx"
            }
        }
    },
    "ZH": {
        "INVOICE": {
            "NORMAL": {
                "template_file_nm": "請求書_ZH.xlsx",
                "template_path": "templates/請求書_ZH.xlsx"
            }
        }
    }
}
