SELECT
    CASE
        WHEN col IS NULL OR col = '' THEN col
        WHEN LENGTH(col) = 6
            THEN SUBSTR(col, 1, 4) || '/' || SUBSTR(col, 5, 2)
        ELSE col
    END AS col
FROM your_table;