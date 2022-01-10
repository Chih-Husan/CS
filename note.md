正規表達法
==========
>.【點】點可代替所有可能的字元（字母、數字或符號）。EX：.GC → UGC、OGC、PGC、2GC或是nGC等...
>?【問號】比對前一個字串或是不比對。EX：facebo?k → facebook、facebok
>*【星號】比對前一個字串零次或是多次。EX：sky*blue → skblue(y出現0次)、skyblue(y出現1次)、skyyyblue(y出現多次)
>-【破折號】EX：product[A-K] → productA、productB、productC、productD...productK
>+【加號】跟星號類似，差別在於至少要與前一個字比對一次或以上。EX：sky+blue → skyblue(y出現1次)、skyyyblue(y出現多次)
>|【直線】或者。EX：想找到Facebook、Instagram、Wordpress、Google相關的文章，可以使用Facebook | Instagram | Wordpress | Google
>^【插入符號】和$【錢字符號】^插入符號是比對前開頭，$錢字符號則是比對結尾。EX：^eat → eat、eatenEX：eat$ → creat、peat、leat
>\【反斜 線】將任何特殊字元，恢復成  一般字元。EX：transbiz\.com → transbiz.com
>()【括號】把想找的相關字詞放 入括號內，可依照 括號 裡的字元 排序找到可能的結果。EX：(sym) → sympathy、symbol、assym等
>[]【中括號】任意比對字串內的每個項目。EX：product[DEFG] → productD、productE、productF、productG

grep
=====
>-i → 忽略大小寫
>-n → 顯示匹配行及行號
>-r → 遞歸顯示目錄
>-c → 只輸出匹配行的計數
>-v → 只列出不符合的內容
>--color   =ne ver|always|auto → 顏色標示
>-A → 多顯示匹配行的後幾行
>-B → 多顯示匹配行的前幾行
>-C → 多顯示匹配行的前後幾行

grep + 正規表達法
================
1.開頭結尾
>a開頭 → ls | grep “^a ”
>a或b結尾 → ls | grep “[ab]$  ”
2.出現次數○a開頭，出現0次以上 → ls | grep “^a* ”
>a開頭，出現零次或一次 → ls | grep “^a? ”
>a開頭，出現一次以上 → ls | grep “^a+ ”
3.多種組合
>含有ab或cd → ls | grep “ab\|cd   ”
>含有ab開頭或cd結尾 → ls | grep “^ab\|cd$”

WC 文字處理工具
==============
>wc → 計算指定檔案內容的換行數、字數與位元組數
1.-l → 只計算換行數
2.○-w → 只計算字數
3.-c → 只計算位元組數
4.-m → 只計算字元數
5.-L → 計算最常行的長度wc [option] filename

Cut 文字處理工具
===============
>cut → 逐行擷取部分字元或欄位資料
1.-b → 輸出的指定範圍以bytes作為單位
2.-c → 輸出的指定範圍以字元數量作為單位
3.-d → 指定分隔字元，default為tab作為分隔
4.-f → 輸出的指定範圍(每筆data的第幾column作為區分)
5.-s → 若該行無分隔字元則不顯示cut [option] filename

Paste 文字處理工具
=================
>paste → 將每個文件以列對列的方式，一列一列加以合併

Diff 文字處理工具
===============
>diff → 比較文件的內容，特別是兩版本不同的同份文件
1.-y → 以並列方式顯示文件的異同之處
2.-W → 使用-y參數時，指定欄寬
3.-C → 前後輸出格式
4.-u → 統一格式輸出

文字處理工具
===========
> → 覆蓋原有檔案
>>  → 追加檔案，不覆蓋繼續寫

Sort 文字處理工具
================
>sort → 處理各種文字資料的排序問題
1.-f → 忽略大小寫○-u → 去除重複資料
2.-r → 反向排序
3.-t → 指定欄位的分隔字元(default=blank or tab)
4.-k → 指定欄位的編號
5.-n → 依照實際數值的大小排序
6.-h → 對有單位的數值排序
7.-M → 依照月份排序

Uniq 文字處理工具
=================
>uniq → 將連續重複文字刪除
1.-c → 計算文字行重複次數
2.-D → 只輸出有重複的文字行
3.-d → 將重複行刪掉
4.-u → 只輸出沒有重複的文字行
5.-f → 指定要跳過的欄位
6.-s → 跳過每一行開頭幾個字元
7.-w → 只比較每一行開頭幾個字元
8.-i → 忽略大小寫

Tr 文字處理工具
===============
>tr → 替換或刪除操作的字串轉換
1.-c → 用set1中字符 集的補集替換此字符集，且字符集需符合ASCII
2.-d → 刪除檔案中 所有在set1中出現的字元
3.-s → 刪除檔案中重複且set1中出現的字元，只保留一個  

Join 文字處理工具
================
>join → 將兩個文件中，指定欄位內容相同的行連接起來
1.-1 → 連接filename1指定的欄位
2.-2 → 連接filename2指定的欄位
3.-t → 使用欄位的分隔符號
4.-i → 忽略大小寫
5.-o → 按指定的格式顯示結果
6.○-a → 除顯示結果，原檔案的其他行也顯示

awk 文字分析工具
===============
1.常用在對文字和資料進行分析處理
2.檔案逐行的讀入
3.以空格為預設分隔符號

awk Script
===================
>awk 'BEGIN{ print "start" } pattern{ commands } END{ print "end" }' filename
1.第一步執行BEGIN 語句
2.第二步從檔案或標準輸入讀取一行，然後再執行pattern語句，逐行掃描檔案到檔案全部被讀取
3.第三步執行END語句

awk 語法常用引數
===============
1.-F 指定分隔符(可是字串或正規表達法)，預設是空白(space)
2.-f 從指令碼檔案(awk script)中讀取awk命令
3.-v var=value賦值變數，將外部變數遞給

awk print record & field
==========================
>awk -F “\tab” '{print $0}' fruit.txt
>awk '{print $1, $2, $4}' fruit.txt

awk 參數
========
$0    #當前record(列、橫行)
$1~$n  #當前record的第N個欄位
FS   #輸入field直欄分隔符（-F相同作用）預設空格
RS   #輸入record(列、橫行)分割符，預設換行符
NF   #欄位個數
NR   #record數，就是行號，預設從1開始
OFS  #輸出欄位分隔符，預設空格
ORS  #輸出resord分割符，預設換行符 

awk 關係運算子
=============
awk '{if ($3 == 120) print $0}’ filename

awk 邏輯運算子
=============
awk '($2 > 6) && ($3 >= 150) {print $0}’ filename

awk 正則運算子
=============
awk '{if ($3 ~ /0/) print $0}’ filename

awk 賦值運算子
==============
 awk '{for (j=1; j <= NF; j++) { print $j }}' filename
 
 sed 文字分析工具
 ===============
1.「stream editor 」的縮寫，顧名思義是進行串流(stream) 的編輯
2. 字串取代、複製、刪除的功能
3.自動化的修改文字檔

Sed指令
=======
option：以- 符號開頭的功能，如-n、-r、-i，可省略
n1,n2：代表開始行數和結尾行數，一個代表指定的這行，不輸入代表每行都會執行command
command：進行的動作，如s, a, c, d, i
pattern：給command使用的參數
replacement：當使用s指令時會使用
flag：當使用s指令時會使用sed

Sed語法-常用選項
================
sed [-nefi] “[n1,n2] [command] / [pattern] / [replacement] / [flag]” file.txt
>option:
1.-n: 沉默模式，只有經過sed處理的那行才會被印出
2.-e :  直接在命令模式編輯，預設
3.-f :  直接將sed動作寫在一個檔案內，-f file會直接執行file裡面的動作
4.-i :  修改檔案

Sed語法-常用指令
sed [-nefi] “[n1,n2] [command] / [pattern] / [replacement] / [flag]” file.txt
>command:
1.a: 新增，在下一行插入字串，未指定行數的話，則是在每一行之後插入字串
2.c:  取代， 取代指定行數的內容○d : 刪除，後面通常不接任何東西
3.i :  插入，在指定行數的前一行插入字串
4.p : 印出，只印出受影響的行，常搭配-n使用
5.s : 搜尋、取代，最常用的指令，可搭配正規表達式使用，將搜尋的內容進行取代

Sed語法-常用旗幟
===============
sed [-nefi] “[n1,n2] [command] / [pattern] / [replacement] / [flag]” file.txt
>flag
1.g: 全部取代
2.[0-9]: 每行第幾次出現
3.I :  忽略大小寫
4.w :  把符合的結果寫入檔案

 Sed應用-- s搜尋並取代
 ====================
 sed -e ‘s/a/A/1’ apple.txt
 sed ‘s/a/A/g’ apple.txt
 
 Sed應用-- -n沉默模式+p 只印出受影響的行
 ======================================
 sed -n ‘s/a/A/p’ apple.txt
 sed -n ‘s/a/A/p’ apple.txt > apple_output.txt
 
 Sed應用-- -f 讀取檔案手稿
 =========================
 sed -f apple_command.txt apple.txt
 
 Sed應用-- a新增, c取代, d刪除
 =============================
sed '1a apple apple apple' apple.txtsed -i '2,3c hahaha' apple.txtsed 1,5d apple.txt

Sed應用-- s搜尋並取代+正規表達法
===============================
sed 's/.e/E/g' apple.txt

Sed應用-- s搜尋並取代(多個)&存檔
==============================
sed 's/pen/pencil/; s/have/had/' apple.txt
sed 's/pen/pencil/; s/have/had/' apple.txt > apple_output.txt等同於
sed -e 's/pen/pencil/' -e 's/have/had/' apple.txt > apple_output.txt

Grep, Awk, Sed比較
==================
>grep：文字搜尋工具
1.可用正規表達法，找出匹配的內容
>sed ：是一種線上編輯器
1.它一次處理一行內容，可搭配正規表達法
2.主要用來自動編輯一個或多個檔案，簡化對檔案的反覆操作
3.用於行間的內容操作,如增刪改,查詢替換
>awk：文字分析工具
1.逐行的讀入，可搭配正規表達法
2.主要用在對文字和資料進行分析處理，以空格為預設分隔符號
3.同時也是程式語言
4.用於處理有欄位規則的行內內容,並支援格式化輸出

Git 是什麼？
============
1.免費、開源專案管理工具
2.用來做軟體的版本控制與維護
3.記錄版本更動情形，保留對於檔案的新增、修改或是刪除等操作的歷史紀錄
4.分散式系統
5.可離線工作
6.多人合作專案時

Git-版本控制造成的困擾：
====================
>當檔案備份過多時
1.容易忘記每個檔案做了哪些變動，檔案之間的差異
>當多人共同編輯時
1.在整合檔案或是不同人在進行反覆編輯時，容易導致原本的檔案被覆蓋掉
2.修改到別人的程式碼

Git-版本控制的特點
1.版本儲存
a.儲存檔案的重要資訊，EX：編輯者、時間、版本相關資訊
2.共同編輯
a.可藉由repository和共同編輯者分享資料，不會因為兩人同時編輯，導致先進行編輯的人的內容被覆蓋掉
3.儲存空間
a.git並不是記錄版本差異，而是記錄檔案內容的快照，使git體積小、速度快

Git 指令
========
●初始化專案：git init
●單一檔案  加入索引(暫存區)：git add <檔案名稱>
●所有檔案  加入索引(暫存區)：git add .
●觀看當前 狀態：git status
●提交版本：git commit -m “修改紀錄"
●瀏覽歷史紀錄：git log

Git-使用方法
============
一.新增Working directory(工作目錄)
1.建立資料夾(ex：mkdir cs6_git)
2.移動到資料夾：$ cd cs6_git
3.將專案資料夾建立成git repository：$ git init (初始化資料  夾)
4.新增檔案(ex：index.html)
5.查看資料夾內檔案變化：$ git status
二. 進入Staging area(暫存區)
1.將新增或變更的檔案加入追蹤：$ git add index.html
2.查看資料夾內檔案變化：$ git status
3.再新增一個檔案(ex：README.md)
4.查看資料夾內檔案的變化：$ git status
三. 進入Local repository(本地數據庫)
1.將檔案移入本地repo，提交新版本：$ git commit -m “First release of Hello”
2.使用$ git status觀察：$ git status
3.查看新增的版本(歷史紀錄)：$ git log
 


 
















