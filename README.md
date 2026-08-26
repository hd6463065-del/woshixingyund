from datetime import datetime

s = "2026/08/26"
dt = datetime.strptime(s,"%Y/%m/%d")
res = dt.strftime("%Y/%m")
print(res) # '2026/08'
