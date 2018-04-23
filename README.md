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
	- 關聯完整性 ( Relational Integrity Rule )
		+ 實體完整性 ( Entity Integrity Rule )
			+ 定義何謂**有效**「實體」
			+ 定義何謂**有效**「紀錄」
				+ 每一筆資料/紀錄都是唯一、可辨識
			+ [主鍵](#PK)的兩個特性
				+ 必有資料
					+ 不會包含空值 NULL
				+ 唯一
					+ 主鍵的值**不會重複**
		+ 參照完整性 ( Referential Integrity Rule )
			+ 定義**有效**「關係」
			+ 關聯式資料庫使用「外鍵」來記錄關係
			+ 定義何謂**有效**「外鍵」
			+ 外鍵的兩種可能性
				+ 有資料
					+ 必須在**參照的主鍵**欄位中找到這個值
				+ 空值
					+ 假設情況允許
	- 任一筆資料都**不可違反上述兩個完整性**
		+ 區域完整性 ( Domain Integrity Rule )
			- 符合儲存格之規則
		+ 使用者定義之完整性 ( User-defined Integrity Rule )
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
	NUMBER(3,2)  -> -9.99 ~ 9.99
	NUMBER(2)    -> -99 ~ 99
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

<a name="PK" />

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

### 被參照
- 假如這筆資料的**主鍵值**出現在另一個資料表中的外鍵欄位上
- 主紀錄 Parent Record : 「被參照」的紀錄
- 子紀錄 Child Record : 「參照」其他紀錄的那些紀錄
	#### 時機點
	- 刪除被參照的紀錄時
	- 修改被參照的紀錄之主鍵值時
	#### 四個可能的行動
	1. RESTRICT
	> 不允許刪除被參照的紀錄 (系統預設行為)
	2. CASECADE
	> 對於參照此筆紀錄的子紀錄執行相同異動
	3. SET NULL
	> 將子紀錄之**外鍵值**設為**空值**
	4. SET DEFAULT
	> 將子紀錄之**外鍵值**設為**預設值**

## 資料表關係
- 1-1 Relationships
	> 「老師」擔任「科系」系主任
	![8](https://raw.githubusercontent.com/jason19970210/MarkdownPhotos/master/8.png)

	- 由一個主鍵與一個外鍵建立關係
		- **且外鍵必須設定為「唯一不會重複」**

- 1-M Relationships
	> 「科系」和「學生」關係
	![10](https://raw.githubusercontent.com/jason19970210/MarkdownPhotos/master/10.png)
	- 一個**PK.** + **FK.**

- M-M Relationships
	> 「員工」擁有的「證照」關係
	![11](https://raw.githubusercontent.com/jason19970210/MarkdownPhotos/master/11.png)

	**(兩組 1對多的關係)+(一個鏈接資料表)**

### 自我參照
- 外鍵參照同一資料表中的主鍵
- 代表同一個資料表不同記錄之間的關係
![12](https://raw.githubusercontent.com/jason19970210/MarkdownPhotos/master/12.png)

## 正規化 Normalization (資料表分割)
- ### 目的
	- 降低資料的「重複性」**Data Redundancy**
	- 避免「更新異常」**Anomalies**

- ### 無損失分解 Lossless Decomposition
	- #### 定義
	是指將原先關聯(表格)的所有資訊，在「分解」之後，仍能由數個新關 聯(表格)中經過「合併」得到相同的資訊。
	- #### 觀念
	當關聯表R被「分解」成數個關聯表R1, R2, ..., Rn 時，則可以再透過 「合併」R1 R2 ... Rn得到相同的資訊R。

- ### 規則
	- #### 第一正規化 1NF (First Normal Form) (去除重複群組、確定主鍵)
		- 每一個欄位只能有一個基元值(Atomic)即單一值
		- 沒有任何兩筆以上的資料是完全重覆
		- 資料表中有主鍵, 而其他所有的欄位都相依於「主鍵」
		P.S. Funtional Dependency 功能支配關係

	- #### 第二正規化 2NF (分離部分相依性、保留完全相依性)
		- 所有**非主鍵**欄位都要與**主鍵**相關
		- 使用外部索引鍵，讓這些資料表產生關聯
		- 為可套用於多筆記錄的多組值建立不同的資料表

	- #### [第三正規化](http://database.klab.tw/teach/t5_3.php) 3NF (分離遞移相依性)
		- 刪除不依賴索引鍵的欄位
		- 消除資料表中的**遞移相依** (Transitive Dependency)
		- 非鍵值欄位之間彼此不能有相關性，否則即產生遞移性

![14](https://raw.githubusercontent.com/jason19970210/MarkdownPhotos/master/14.png)

## Example
![3](https://raw.githubusercontent.com/jason19970210/MarkdownPhotos/master/3.png)

+ Result: True
+ Reason: 若刪除資料時無此資料, 則不進行動作, 亦不顯示錯誤訊息

![4](https://raw.githubusercontent.com/jason19970210/MarkdownPhotos/master/4.png)

+ Result: True
+ Reason: 若修改資料時無此資料, 則不進行動作, 亦不顯示錯誤訊息

![5](https://raw.githubusercontent.com/jason19970210/MarkdownPhotos/master/5.png)

+ Result: False
+ Reason: 外鍵有被參照

## Microsoft Access
+ Data Type