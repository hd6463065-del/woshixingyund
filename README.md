config = SQL_DB_CONFIG["SC_5_99_01_0"]

ref_db = config["db"]
ref_schema = config["schema"]

session.table(f"{ref_db}.{ref_schema}.{selected_table}")