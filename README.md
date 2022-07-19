# 11101泰山職訓作品-投票系統

## 使用者故事(user story)

### 共用
* 主畫面切割為三塊
    * 上方為輪播區塊，可投放廣告banner
    * 中間為目前投票列表及按鈕區    
    * 下方為頁尾版權宣告
* 按鈕區有以下列內容
    * 管理者登入按鈕
    * 會員登入按鈕
    * 註冊會員按鈕
* 投票列表設按鈕可查看當前投票結果
* 會員註冊時需提供以下資料，以供投票分析之用
    * 帳號
    * 密碼
    * 性別
    * 電子郵件
    * 生日
    
### 使用者端
* 進入首頁時，可以看到投票項目列表
* 可以選擇想要了解的項目進行點選
* 未登入的使用者只可以看到投票的結果
* 已登入的使用者可以看到投票結果及"我要投票"按鈕
* 按下"我要投票"時會顯示投票項目
* 選擇項目後，按送出，完成投票
* 完成投票後，跳至投票結果頁
* 投票結果有一顆按鈕可以返回首頁

### 管理者端
* 要透過登入才能進入管理者端
* 登入後在首頁列表有"新增投票"按鈕
* 點選新增投票後進入新增投票表單頁面
* 在新增頁面可以設定投票主題
* 選項可以動態增加
    * 在主題旁有一個"增加選項"的按鈕
    * 每按一次"增加選項"就會在下方增加一個項目
    * 可以刪除選項
* 完成設定後按下"完成新增"，即增加一個投票主題
* 可查看投票結果(含統計分析)
* 可以修改投票主題或選項
* 可以刪除投票

## 功能需求
* 註冊/登入系統
* 前/後台頁面切版
* 前端讀出功能(列表/註冊表單)
* 新增投票
* 修改投票
* 刪除投票
* 投票結果的統計分析

## 資料表設計
### 資料庫名稱:vote
* users
    |名稱|型態|預設值|A_I|備註|
    |--|--|--|--|--|
    |id|int(10)|--|true|序號|
    |user_id|varchar(20)|--|--|帳號|
    |password|varchar(128)|--|--|密碼|
    |gender|tinyint(1)|--|--|性別|
    |birthday|date|--|--|生日|
    |email|varchar(64)|--|--|電子郵件|
    
* admins
    |名稱|型態|預設值|A_I|備註|
    |--|--|--|--|--|
    |id|int(10)|--|true|序號|
    |account|varchar(20)|--|--|帳號|
    |password|varchar(20)|--|--|--|
    |name|varchar(20)|--|--|--|
    
* subjects
    |名稱|型態|預設值|A_I|備註|
    |--|--|--|--|--|
    |id|int(11)|--|true|序號|
    |subject|varchar(128)|--|--|主題描述|
    |multiple|boolean(1)|--|--|單/複選|
    |multi_limit|tinyint(2)|1|--|單/複選項目數|
    |start|date|--|--|投票起始日|
    |end|date|--|--|投票結束日|
    |total|int(11)|--|--|--|
    
* options
    |名稱|型態|預設值|A_I|備註|
    |--|--|--|--|--|
    |id|int(11)|--|true|序號|
    |option|varchar(128)|--|--|選項描述|
    |subject_id|int(11)|--|--|--|
    |total|int(11)|--|--|--|

* logs
    |名稱|型態|預設值|A_I|備註|
    |--|--|--|--|--|
    |id|int(11)|--|true|序號|
    |user_id|int(11)|--|--|投票者|
    |subject_id|int(11)|--|--|投票主題|
    |option_id|int(11)|--|--|投票選項|
    |vote_time|timestamp|--|--|投票時間|
