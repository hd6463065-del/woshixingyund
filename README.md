import pandas as pd

jpn_map = {
    "請求書 账票": 1,
    "仕入明細 明细": 2,
    "受領書 收据": 3
}
# 反转map value→key
rev_map = {v: k for k, v in jpn_map.items()}

df = pd.DataFrame({"code":[1,2,3]})
# 根据code拿到带空格的key文本
df["full_text"] = df["code"].map(rev_map)
# 按半角空格切分
df[["jpn","eng"]] = df["full_text"].str.split(" ", expand=True)

print(df)
