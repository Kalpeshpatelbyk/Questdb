--Learning Questdb for finance.
--https://github.com/Kalpeshpatelbyk/Questdb.git

1.Create table from csv file and import in respected csv header form
2.convert int to double for size columns
3.convert timestamp colum to questdb Timestamp

4.Create ohlc table from existing table for respective table
5.create new table optionchain

_____________Tables_________________________________________________________________________
Users: ( Username varchar, password varchar , usertype varchar )
Roles: ( Role:admin,  Role:user)
Menus: (uploadfile,backup, restore, dashboard, expiry_settings, App_settings, userroles)
BackupSettings ( backup_path, Restore_path, Retentions_days)

expiry_settings : will consist of ( Product,ITMStrike_diff,OTMStrike_diff) for calcualting option chain 
  Product: BTCUSD
  ITMSTRIKE:5
  OTMSTRIKE:15
  STRIKE_DIFF_EXP1 : 100
  STRIKE_DIFF_EXP2 : 200
  STRIKE_DIFF_EXP3 : 500
  STRIKE_DIFF_EXP4 : 500
  STRIKE_DIFF_EXP5 : 500
  STRIKE_DIFF_EXP6 : 1000
  STRIKE_DIFF_EXP7 : 1000
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
  Futures_BTCUSDT_2022
  Futures_BTCUSDT_2023
  Futures_BTCUSDT_2024
  Futures_BTCUSDT_2025
    Problems: Convert int to long for size column, convert timestamp column from varchar to timestamp 
    Create OHLC Table from respective table. 
    

    
Options_BTCUSDT_2022
Options_BTCUSDT_2023
Options_BTCUSDT_2024
Options_BTCUSDT_2025
symbol,price,size,timesamp,maker_taker
P-BTC-47500-010122,1386.5,1,2022-01-01 00:00:00.621540,Taker
C-BTC-50000-140122,11705.5,1,2022-01-01 00:00:00.621540,Taker
	
 
 
 
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



