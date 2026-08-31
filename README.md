np.where(
            cr_lmt_info_df["MEIGI_NO"].notna(),
            cr_lmt_info_df["HOJIN_NO"] + cr_lmt_info_df["MEIGI_NO"],
            cr_lmt_info_df["HOJIN_NO"]
        )