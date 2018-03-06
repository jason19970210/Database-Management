# Database-Management

Class ID : IM 2209  
Resource : ftp://163.25.117.117/chunyi/

## 資料庫
+ 資料庫 = 資料 + 規則

## 為何需要資料庫技術
1. 找資料速度快
2. 多人環境下，維護資料容易
3. 保證資訊正確
4. 保護敏感資料
5. 避免「冗餘資料」
6. 解決資料損毀問題

## 資料庫管理系統 (Database Management System, DBMS)
1. Oracle
2. SQL Server
3. MySQL
4. DB2
5. MS SQL
6. SQlite

## 「關聯式」資料庫管理系統
- 目前最廣的DBMS
- 使用相同觀念所設計
	- 關聯資料模型
- 使用相同語言來操作、管理資料
	- SQL, Structured Query Language

## 關聯資料模型
- 結構部分
	- 資料結構
		- 一個關聯資料庫中有多個資料表(Table)
		- **資料表**是一個資料庫的最基本建構塊
- 完整性規則
	- 確保資料的**有效**
- 操作
	- 允許對資料操作的類型
	- 擷取、新增、修改、刪除

## 資料表 Tables
- A table should have its own name
- 2 Dimensions for the tables
	- 欄位(結構)
		- 欄位名稱
		- 資料型態
			- 定義**資料型態**及其允許的操作
			- 每個資料型態都有一個名稱
			- 可以宣告`長度`或`大小`
	- 紀錄(內容)
#### Data Type
- CHAR[(size)]
	> 固定長度的文字資料
- VARCHAR2(size)
	> 變長的文字資料
- NUMBER[(p,s)]
	```SQL
	NUMBER(3,2) -> -9.99 ~ 9.99
	NUMBER(2)	-> -99 ~ 99
	```
- DATE
	> 日期與時間

## 關聯資料表的七大特性

1. 資料表名稱具**唯一性**
2. 資料表內每個欄位都有一個**獨特**的名字
3. 同一個欄位的值都來自同一個**值域**(資料類型 & 大小)
4. 資料表中的每個儲存格最多只可以包含**一個值**
	> No Repeating Groups
5. 每筆紀錄都是**唯一的**
	> 無重複紀錄
6. 欄位出現的順序不具意義
7. 紀錄出現的順序不具意義

#### 替代用語
![1](https://raw.githubusercontent.com/jason19970210/MarkdownPhotos/master/1.png)

## Microsoft Access
+ Data Type