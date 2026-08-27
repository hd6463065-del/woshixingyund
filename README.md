if isinstance(val, Decimal):
    row_dict[col_upper] = format(val, "f")
else:
    row_dict[col_upper] = str(val)