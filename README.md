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
		- 一個關聯資料庫中有多個資料表 ( Table )
		- [**資料表**](#Tables)是一個資料庫的最基本建構塊
- 完整性規則
	- 確保資料的**有效**
	- 關聯完整性 ( Relational Integrity )
		+ 實體完整性 ( Entity Integrity )
			+ 定義何謂有效「實體」
			+ 定義何謂有效「紀錄」
				+ 每一筆資料/紀錄都是唯一、可辨識
			+ 主鍵的兩個特性
				+ 必有資料
					+ 不會包含空值 NULL
				+ 唯一
					+ 主鍵的值**不會重複**
		+ 參照完整性 ( Referential Integrity )
			+ 定義有效「關係」
			+ 關聯式資料庫使用「外鍵」來記錄關係
			+ 定義何謂有效「外鍵」
			+ 外鍵的兩種可能性
				+ 有資料
					+ 必須在**參照的主鍵**欄位中找到這個值
				+ 空值
					+ 假設情況允許
	- 任一筆資料都**不可違反上述兩個完整性**
- 操作
	- 允許對資料操作的類型
	- 擷取、新增、修改、刪除

<a name="Tables" />

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
3. 同一個欄位的值都來自同一個**值域** ( 資料類型 & 大小 )
4. 資料表中的每個儲存格最多只可以包含**一個值**
	> No Repeating Groups
5. 每筆紀錄都是**唯一的**
	> 無重複紀錄
6. 欄位出現的順序不具意義
7. 紀錄出現的順序不具意義

#### 替代用語
![1](https://raw.githubusercontent.com/jason19970210/MarkdownPhotos/master/1.png)


## Keys
#### Candidate Key 候選鍵
- 一個資料表必須至少有一個候選鍵
- 一個候選鍵可以只含有一個欄位或是多個欄位
	> 當一個候選鍵由多個欄位組成，稱作「複合鍵」
- 候選鍵特質
	- 唯一性 ( Uniqueness )
		> 能夠唯一辨識每一筆資料
	- 不可減少性 ( Irreducibility )
		> 若從表中刪除任何欄位，將使其不再具有唯一辨識性

#### Primary Key, PK 主鍵
- 在所有候選鍵中，擇一作為主鍵
- 在資料運算時，需要唯一辨識紀錄 ( Record )
- 任何時間都擁有資料
- 內容改變的可能性越小越好
- 欄位個數、內容越少越好
- 使用者在資料使用上越方便越好

#### Alternate Key 替代鍵

#### Foreign Key, FK 外來鍵
- Not Unique
- 雙向使用
- 一個或是一組欄位在某資料表中為**候選鍵**  
這些欄位在其他資料表中出現時稱作外鍵
- 其出現代表這兩個資料表的紀錄存在**關係**
- 外鍵與其參照的候選鍵需具有相同的資料型態與大小

註：參照：由外鍵找主鍵  
FK point to PK

### 空值 `NULL`

### 資料字典
![2](https://raw.githubusercontent.com/jason19970210/MarkdownPhotos/master/2.png)

+ X 代表文字
+ Departments.dept_no ：Departments 資料表中的 dept_no 欄位

## Microsoft Access
+ Data Type