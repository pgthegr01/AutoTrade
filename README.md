AutoTrade
=========

Automated Trade Testing Platform

Database:

1 - Root table contains each http response (get price)
    id . time . symbol . price
2 - Each "view" will be a table, triggered by a timer (gather data)
    id . time . symbol . open . high . low . close . indicator0 . indicator1 ...
3 - Each indicator will be calculated against the "view" table, triggered by a timer

4 - Betting program will be triggered by a timer - all views saved to the same betting table
    id . otime . ctime . obetid . cbetid . oprice . cprice . viewid . 
    
