# 英文中间带空格，比如 Purchase Order
s = "仕入明細 Purchase Order"

jpn_part, eng_part = s.split(" ", maxsplit=1)

print(jpn_part)   # 仕入明細
print(eng_part)   # Purchase Order  ✔后面空格全部保留，不会被拆开
