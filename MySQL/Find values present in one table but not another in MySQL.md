Sometimes you want to check to see what data didn't import correctly.

    SELECT `citationid` 
    FROM `cases` c
    WHERE `citationid` NOT IN (SELECT `citationid` FROM `filings`) LIMIT 100