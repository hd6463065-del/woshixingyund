update_msg = st.session_state.get(SESSION_KEY.SS_KEY_UPDATE_MSG, None)

if update_msg:
    ddd.aaa(update_msg)
    ss["display_flag"] = False
    st.session_state.pop(SESSION_KEY.SS_KEY_UPDATE_MSG, None)
else:
    error_msg = st.session_state.get(SESSION_KEY.SS_KEY_DB_ERROR, None)

    if error_msg:
        ddd.aaa("3")
        ss["display_flag"] = False

return data