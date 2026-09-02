# ✅ 推荐的加载方式
wb = load_workbook(filename, keep_vba=False, data_only=False) 
# data_only=True 会丢弃公式，有时也会导致格式关联丢失
