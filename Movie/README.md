# MVAutoSort

![執行示例](https://i.imgur.com/whiajFm.png)

## 需求套件
pip install requests bs4 lxml fake-useragent opencc-python-reimplemented html2bbcode

## 說明
未完成待續

### 搜尋模式

- 若資料夾名稱含有IMDbID(tt:d)或DoubanID(db_:d)，則使用ID搜尋對應資料

- 若資料夾內存在.nfo檔，則在其中尋找IMDbID，並以此做搜尋

- 若以上皆非，則解析文件夾名稱調用豆瓣API做搜尋

  - 通常文件夾名稱由3個部分組成 $電影名稱.$年份.$壓制參數，目前採用以$年份為錨點解析出$電影名稱的方式 
  
### 資料採集

- 原採用PT-Gen的API，但受其穩定性&API調用次數限制，故後來棄用。 (若要啟用將Local=False即可)

- 改採參照其代碼簡化成gen.py，以此採集資料。感謝@Rhilip大佬、BFDZ大佬的PT-Gen。

- 如果無法從豆瓣找到資料，則透過IMDbID在IMDb&TMDb分別搜尋資料，並合併

### 自動分類

#### 標題

- 中文標題優先採取台灣地區翻譯標題，若為標記則採用豆瓣中文標題，並使用OpenCC翻譯成繁體中文

- 英文標題為在所有標題清單中找到由純英文組成之標題，若無英文標題則只使用中文標題

## 待加入功能

- [] 手動模式(全手動、錯誤時手動、不使用手動)，手動輸入IMDbID

- [] 搜尋模式切換

- [] 根據TMDB資料搜尋各季資訊(因IMDb不會返回各季資料)，並存放到 合集 資料夾

- [] 引用資料庫已有的資料