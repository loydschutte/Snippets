The following snippet will find duplicate rows in your database and delete the ones with the smaller ID. Don't forget to adjust the values to reflect the columns in your table.

    DELETE t1 FROM contacts t1
    INNER JOIN contacts t2 
    WHERE 
        t1.id < t2.id AND 
        t1.email = t2.email;