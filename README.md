AutoTrade
=========

Automated Trade Testing Platform

Database:

1 - Root table contains each http response (get price)
    id . time . symbol . price . volume

2 - Each "view" will be a table, triggered by a timer (gather data)
    id . time . symbol . open . high . low . close . volume . indicator0 . indicator1 ...

3 - Each indicator will be calculated against the "view" table, triggered by a timer (format data)

4 - Betting program will be triggered by a timer - all views saved to the same betting table (betting)
    id . otime . ctime . obetid . cbetid . oprice . cprice . viewid . 
    
Programs:

1 - Get price
    get stock symbols from stock table
    concatonate list into http string
    execute http call and read response
    insert ignore each price into database with timestamp

2 - Gather Data
    store triggertime
    get stock symbols from stock table
    for each stock symbol
        select the prices where timestamp is between triggertime - timeframe and triggertime
        set open = first
        set high = highest value
        set low = lowest value
        set close = last value
        set volume = last volume
        insert values to viewtable

3 - Format Data
    get stock symbols from stock table
    for each stock symbol
        for each indicator
            calculate indicator
            update row with indicator

4 - Betting
    
