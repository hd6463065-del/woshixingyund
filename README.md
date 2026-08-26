import pandas as pd

# ---------------------- 模拟测试数据 ----------------------
data = [
    {"法人key":"K001", "科目名":"A", "残高":100},
    {"法人key":"K001", "科目名":"B", "残高":200},
    {"法人key":"K002", "科目名":"A", "残高":50},
    {"法人key":"K002", "科目名":"B", "残高":150},
    {"法人key":"K003", "科目名":"A", "残高":300},
]
df = pd.DataFrame(data)
print("====原始数据====")
print(df)

# ---------------------- groupby sum（得到Series） ----------------------
ser = df.groupby("法人key")["残高"].sum()
print("\n====groupby sum 之后 Series====")
print(ser)
print(type(ser)) # pandas.core.series.Series

# ---------------------- 业务用：转成DataFrame（推荐写法） ----------------------
result_df = df.groupby("法人key")["残高"].sum().rename("合計残高").reset_index()
print("\n====处理完成，DataFrame，用于merge====")
print(result_df)
print(type(result_df))

# ---------------------- 再演示多列求和 ----------------------
df2 = pd.DataFrame([
    {"法人key":"K001","残高":100,"限度額":1000},
    {"法人key":"K001","残高":200,"限度額":2000},
    {"法人key":"K002","残高":50,"限度額":500},
])
multi_sum_df = df2.groupby("法人key")[["残高","限度額"]].sum().reset_index()
print("\n====多列求和====")
print(multi_sum_df)
