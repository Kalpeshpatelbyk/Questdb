1.--Learning Questdb for finance.
2.--https://github.com/Kalpeshpatelbyk/Questdb.git

1. Create table from csv file and import in respected csv header form.
2. Convert int to double for size columns.
3. Convert timestamp colum to questdb Timestamp.
4. Create ohlc table from existing table for respective table
5. Create new table optionchain

Tables________________________________________

1. Users: ( Username varchar, password varchar , usertype varchar ).
2. Roles: ( Role:admin,  Role:user).
3. Menus: (uploadfile,backup, restore, dashboard, expiry_settings, App_settings, userroles).
4. BackupSettings ( backup_path, Restore_path, Retentions_days).
5. expiry_settings : will consist of ( product, week, strikediff, itm_strike_count, otm_strike_count, description, "timestamp") for calcualting option chain .
 INSERT INTO expirysettings (product, week, strikediff, itm_strike_count, otm_strike_count, description, "timestamp")
VALUES
    ('BTCUSD', 1, 200, 5, 10, '1st week Options Expiry', now()),
    ('BTCUSD', 2, 200, 5, 10, '2nd week Options Expiry', now()),
    ('BTCUSD', 3, 200, 5, 10, '3rd week Options Expiry', now()),
    ('BTCUSD', 4, 500, 5, 10, '4th week Options Expiry', now()),
    ('BTCUSD', 5, 500, 5, 10, '5th week Options Expiry', now()),
    ('BTCUSD', 6, 500, 5, 10, '6th week Options Expiry', now()),
    ('BTCUSD', 7, 1000, 5, 10, '7th week Options Expiry', now()),
    ('BTCUSD', 8, 1000, 5, 10, '8th week Options Expiry', now()),
    ('BTCUSD', 9, 1000, 5, 10, '9th week Options Expiry', now()),
    ('BTCUSD', 10, 1000, 5, 10, '10th week Options Expiry', now());
     
	  Problems: how to identify which expiry is 1 , 2 , 3 ,,7.

          Solutions: take first date get different expiry base on that expiry identify exp1,exp2,exp3 so 
          there would be 365 expiries if expiry is daily expiry apart from declared holidays.
          WeekNo, ExpiryNo, Day
          1,1 -Monday
          1,2 -Tuesday
          1,3 -Wednesday
          1,4 -Thrusday
          1,5 -Friday
          1,6 -Saturday
          1,7 -Sunday
          2,1 -Monday
          2,2 -Tuesday
          2,3 -Wednesday
          2,4 -Thrusday
          2,5 -Friday
          2,6 -Saturday
          2,7 -Sunday

Futures Table from csv imports
  1.Futures_BTCUSDT_2022
  2.Futures_BTCUSDT_2023
  3.Futures_BTCUSDT_2024
  4.Futures_BTCUSDT_2025
    
    Problems: 
    1.Convert int to long for size column, convert timestamp column from varchar to timestamp 
    2.Create OHLC Table from respective table. 
    

Options Table from csv imports    
1.Options_BTCUSDT_2022
2.Options_BTCUSDT_2023
3.Options_BTCUSDT_2024
4.Options_BTCUSDT_2025

id,symbol,price,size,timesamp,buyer_role:
1.P-BTC-47500-010122,1386.5,1,2022-01-01 00:00:00.621540,Taker
2.C-BTC-50000-140122,11705.5,1,2022-01-01 00:00:00.621540,Taker

 Problem: 
 1. Convert int to long for size column, convert timestamp column from varchar to timestamp 
 2. Need to split symbol TO -> P-BTC, Strike, Expiry
 3. Create OHLC Table from respective table base on strike and expiry.
 
 
 
 Option Chain														
	5min Close														
	Future Price	OptionStrike		CE Stike	CE Price	PE Strike	Price	Total	Daystoexpiry	expiry	Time	Strike Diffrence		DAY	CurrentDate
															
	90000	ITM	3	89400	840	90600	940	1780.00	1	09-05-2025	09:00	200		MONDAY	08-05-2025
	90000	ITM	2	89600	640	90400	840	1480.00	1	09-05-2025	09:00	200		MONDAY	08-05-2025
	90000	ITM	1	89800	440	90200	640	1080.00	1	09-05-2025	09:00	200		MONDAY	08-05-2025
	90000	ATM	1	90000	240.00	90000	300.00	540.00	1	09-05-2025	09:00	200		MONDAY	08-05-2025
	90000	ATM	2	90200	216.00	89800	285.00	501.00	1	09-05-2025	09:00	200		MONDAY	08-05-2025
	90000	OTM	1	90400	194.40	89600	270.75	465.15	1	09-05-2025	09:00	200		MONDAY	08-05-2025
	90000	OTM	2	90600	174.96	89400	257.21	432.17	1	09-05-2025	09:00	200		MONDAY	08-05-2025
	90000	OTM	3	90800	157.46	89200	244.35	401.82	1	09-05-2025	09:00	200		MONDAY	08-05-2025
	90000	OTM	4	91000	141.72	89000	232.13	373.85	1	09-05-2025	09:00	200		MONDAY	08-05-2025
	90000	OTM	5	91200	127.55	88800	220.53	348.07	1	09-05-2025	09:00	200		MONDAY	08-05-2025
	90000	OTM	6	91400	114.79	88600	209.50	324.29	1	09-05-2025	09:00	200		MONDAY	08-05-2025
	90000	OTM	7	91600	103.31	88400	199.03	302.34	1	09-05-2025	09:00	200		MONDAY	08-05-2025
	90000	OTM	8	91800	92.98	88200	189.07	282.06	1	09-05-2025	09:00	200		MONDAY	08-05-2025
	90000	OTM	9	92000	83.68	88000	179.62	263.30	1	09-05-2025	09:00	200		MONDAY	08-05-2025
	90000	OTM	10	92200	75.31	87800	170.64	245.95	1	09-05-2025	09:00	200		MONDAY	08-05-2025



