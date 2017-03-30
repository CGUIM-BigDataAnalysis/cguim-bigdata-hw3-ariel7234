長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
#這是R Code Chunk
#install.packages("rvest")
library(rvest) ##第一次使用要先安裝 
```

    ## Warning: package 'rvest' was built under R version 3.3.3

    ## Loading required package: xml2

    ## Warning: package 'xml2' was built under R version 3.3.3

``` r
##read_html
TJ_url1 <- "https://www.ptt.cc/bbs/Tech_Job/index.html"
TJ_url2 <- "https://www.ptt.cc/bbs/Tech_Job/index2584.html"
TJ_url3 <- "https://www.ptt.cc/bbs/Tech_Job/index2583.html"
TJ_url4 <- "https://www.ptt.cc/bbs/Tech_Job/index2582.html"
TJ_url5 <- "https://www.ptt.cc/bbs/Tech_Job/index2581.html"
url <- c(TJ_url1,TJ_url2,TJ_url3,TJ_url4, TJ_url5)
dataframeAll <- NULL
for (n in url){
    TJ <- read_html(n)
    TJ_title <- TJ %>% html_nodes(".title") %>% html_text()
    TJ_pushNum <- TJ %>% html_nodes(".nrec") %>% html_text()
    TJ_author <- TJ %>% html_nodes(".author")%>% html_text()
    TJ_post <- data.frame(title = TJ_title, PushNum = TJ_pushNum , author= TJ_author)
    dataframeAll <- rbind(dataframeAll, TJ_post)
}
```

爬蟲結果呈現
------------

``` r
#install.packages("knitr")
#這是R Code Chunk
knitr::kable(dataframeAll) ##請將iris取代為上個步驟中產生的爬蟲資料資料框
```

| title                                               | PushNum | author       |
|:----------------------------------------------------|:--------|:-------------|
| Re: \[新聞\] 這家隱形冠軍年終20個月起跳　擬徵才130  | 9       | tw689        |
| (本文已被刪除) \[jjkobe\]                           |         | -            |
| Re: \[新聞\] 這家隱形冠軍年終20個月起跳　擬徵才130  |         | pinkowa      |
| \[請益\] 台塑私專機械人員                           | 5       | Lennonking   |
| (本文已被刪除) \[chien40\]                          |         | -            |
| \[請益\] 請問有人面過 Taylormade(高雄)嗎?           |         | bboycookie   |
| \[討論\] 高薪無妹 vs 低薪妹超多                     | 27      | CrystalNik   |
| \[請益\] 請問資歷查詢                               | 6       | taleb        |
| \[新聞\] 宏碁去年再虧損　提撥公積放0.5元股息        | 1       | qazxc1156892 |
| \[請益\] 通訊所研替                                 | 1       | susumiya     |
| \[討論\] 主管每次forward issue都只單獨轉寄??        | 4       | yamakazi     |
| \[請益\]漢翔與台塑選擇                              | 3       | super14      |
| Re: \[討論\] 高薪無妹 vs 低薪妹超多                 |         | brave00      |
| Re: \[面試\] 南科艾爾斯半導體                       |         | turtle6188   |
| \[討論\] 鴻海月薪六萬 大概是什麼職等                | 3       | su27         |
| 律師為您解惑－線上勞動法免費諮詢即日為勞工 …        | 爆      | pzs          |
| \[公告\] Tech\_Job板板規 2014.03.01                 | 7       | mmkntust     |
| \[公告\] 置底 檢舉/推薦 文章                        | 爆      | mmkntust     |
| \[免費\]工作人生顧問                                | 爆      | zodiac       |
| 捷普 綠點刀具                                       | 3       | tn372845     |
| \[請益\] 日商安立知                                 | 5       | pjc202       |
| \[情報\] 蘋果申請具備iPhone核心之Macbook產品        | 4       | zxcvxx       |
| \[請益\]有人收到德州儀器技術行銷工程師面試邀請?     | 4       | wer11        |
| \[請益\] 請問陸資的IC設計公司                       | 10      | DigiTalent   |
| \[請益\] 德州儀器設備工程師實習                     | 4       | oeys         |
| \[討論\] 國家光電好嗎                               |         | chag06       |
| Re: \[請益\] 請問陸資的IC設計公司                   | 20      | DigiTalent   |
| \[請益\] 是否該調往偏鄉工作？                       | 54      | NakiXIII     |
| (本文已被刪除) \[lponnn\]                           | 5       | -            |
| (本文已被刪除) \[dfg512\]                           | 3       | -            |
| \[請益\] Advantest二手設備商                        | 5       | CA42         |
| Fw: \[請益\] 夜間進修                               |         | neon2102     |
| \[請益\] 華通電腦                                   | 6       | jackjack0805 |
| \[討論\] 矽品好像沒有板上說的那麼不好吧~            | 63      | goodlike     |
| (本文已被刪除) \[ScrewYou\]                         | 15      | -            |
| \[討論\] 台積電VS中油                               | 12      | ej4g4        |
| (本文已被刪除) \[p4818046\]                         | 1       | -            |
| \[請益\] 金屬工業中心面試                           | 1       | huaygina     |
| \[請益\] 在職碩班選擇請益，中興vs中央               | 11      | AKFG         |
| 敬鵬-資訊系統開發管理師                             | 2       | incoterms    |
| \[請益\] 美亞科技                                   | 6       | key9028      |
| \[新聞\] 總經理巡廠要整理桌面　群創員工爆比當兵     | 35      | zzzz8931     |
| Re: \[討論\] 關於機台零件是不是都撐到最後？         | 1       | c1823akimo   |
| 創群科技                                            | 13      | jamiefly     |
| \[討論\] 有人因為辦公室太舊太髒離職的嗎??           | 48      | yamakazi     |
| (本文已被刪除) \[VamYU\]                            | 12      | -            |
| Re: \[心得\] 我在拓凱(台中工業區)的日子             | 6       | simplep2002  |
| Re: \[新聞\]【台GG別走動畫】台積傳將赴美砸5千億建3  | 2       | egnaro123    |
| \[聘書\] 緯創/建漢/帆宣                             | 3       | tomandjim    |
| (本文已被刪除) \[piggg\]                            |         | -            |
| \[徵才\] 交大電子所誠徵碩士級研究助理               | 1       | xgin         |
| \[情報\] 國網中心擴大舉辦工讀生/實習生徵才活動      |         | ZhaoYun      |
| \[請益\] 亞太國際電機 製程 疑問                     | 1       | ian00727     |
| \[徵才\] 掃描器/光學元件/韌體工程師 BioInspira, Inc |         | Herc         |
| (本文已被刪除) \[Crosswise\]                        | 1       | -            |
| Re: \[心得\]小寶跟大寶 真的不一樣                   | 25      | ikeru        |
| Re: \[請益\] Offer請益 英業達/鴻海                  | 1       | wer11        |
| (本文已被刪除) \[pjc202\]                           |         | -            |
| Re: \[請益\] 陶氏化學CDP面試詢問                    | 8       | piggg        |
| (已被mmkntust刪除) <sht255>                         | 10      | -            |
| 〔疑惑〕台GG要在竹南設廠的傳聞有下文嗎？            | 39      | q99518g      |
| (本文已被刪除) \[lovetire\]                         | 12      | -            |
| \[請益\] Offer請益 英業達/鴻海                      | 34      | kusahara     |
| \[請益\] 聯電職務請益                               | 11      | blacktea0930 |
| \[請益\] offer請益 garmin自動化機構/國外sales       | 8       | Blueicex     |
| \[面試\] 友達晶材IE面試與錄取                       | 13      | nick800418   |
| (本文已被刪除) \[pptgov\]                           |         | -            |
| \[請益\] offer 選擇(美光vs力晶）                    | 43      | chsweet      |
| Fw: \[請益\] 科技工程師練英文                       | 5       | ggggggh      |
| \[請益\] offer 上無註明保障年月薪                   | 26      | ck49         |
| \[心得\] 面試心得(乾坤/正新/台灣荏原/Lam/)          | 8       | Sorry5566    |
| \[徵才\] 汐止-徵求會PHP與SQL的工程師                | 8       | MobileMan    |
| \[請益\] 頎邦科技                                   | 4       | popularman   |
| \[面試\] 台達化學公司(前鎮廠) 工作環境與福利        | 5       | tcl2830      |
| \[請益\] 點晶科技 推嗎                              | 5       | okmijnuhb    |
| (本文已被刪除) \[tcl2830\]                          |         | -            |
| \[心得\] 面試心得(基恩斯/精材/ASML/艾克爾)          | 30      | Sorry5566    |
| (本文已被刪除) \[Kovainen\]                         | 6       | -            |
| (本文已被刪除) \[nntn\]                             | 3       | -            |
| \[徵才\] ucfunnel-媒體開發/PM/Node.js/Frontend      | 1       | livingroom   |
| \[請益\] 第一份工作薪水重要還是練功重要?            | 爆      | s6307        |
| Re: \[請益\] 覆晶封裝製程轉職問題                   | 6       | gnh1021      |
| \[請益\] 研發替代役                                 | 6       | leo710215    |
| \[請益\]offer選擇                                   | 10      | david597     |
| \[心得\] 面試 大立光電/艾克爾/采鈺/百佳泰/美光      | 13      | goodboy8899  |
| \[請益\] 電機女生找工作                             | 75      | alice2520200 |
| \[心得\] 我在拓凱(台中工業區)的日子                 | 72      | dash0804     |
| Re: \[心得\] 群聯不舒服的面試經驗                   | 10      | magic704226  |
| (本文已被刪除) \[catdogter\]                        | 31      | -            |
| (已被mmkntust刪除) <stan1111> 版規六                |         | -            |
| \[請益\] 內湖緯創ＥＢＧ情況                         | 11      | wort         |
| \[請益\] 在台灣工作未來方向                         | 15      | omega0210    |
| \[請益\] 陶氏化學CDP面試詢問                        | 7       | chengyuche   |
| \[請益\] 做Power ICdesign的前景？                   | 30      | golover      |
| \[討論\] 關於機台零件是不是都撐到最後？             | 22      | s4001        |
| \[討論\] 關於伺服器代工                             | 15      | orz3qonz     |
| \[請益\] 請問有人了解三浦鍋爐嗎                     | 3       | skatopia     |
| \[新聞\]【台GG別走動畫】台積傳將赴美砸5千億建3      | 46      | DickMartin   |
| \[新聞\] 靠文青打敗台積電　新鮮人最嚮往企業出爐     | 61      | popoallan    |

解釋爬蟲結果
------------

``` r
#這是R Code Chunk
nrow(dataframeAll) 
```

    ## [1] 99

用nrow()算dataframeAll資料框中有幾個row，表示抓了幾筆資料 結果顯示有102筆文章標題。

``` r
#這是R Code Chunk
sort(decreasing = TRUE,table(dataframeAll$author))
```

    ## 
    ##            -     mmkntust     yamakazi   DigiTalent        wer11 
    ##           18            2            2            2            2 
    ##    Sorry5566   bboycookie      brave00   CrystalNik   Lennonking 
    ##            2            1            1            1            1 
    ##      pinkowa          pzs qazxc1156892         su27      super14 
    ##            1            1            1            1            1 
    ##     susumiya        taleb   turtle6188        tw689       zodiac 
    ##            1            1            1            1            1 
    ##         AKFG         CA42       chag06        ej4g4     goodlike 
    ##            1            1            1            1            1 
    ##     huaygina jackjack0805     NakiXIII     neon2102         oeys 
    ##            1            1            1            1            1 
    ##       pjc202     tn372845       zxcvxx   c1823akimo    egnaro123 
    ##            1            1            1            1            1 
    ##         Herc     ian00727        ikeru    incoterms     jamiefly 
    ##            1            1            1            1            1 
    ##      key9028        piggg  simplep2002    tomandjim         xgin 
    ##            1            1            1            1            1 
    ##      ZhaoYun     zzzz8931 blacktea0930     Blueicex      chsweet 
    ##            1            1            1            1            1 
    ##         ck49      ggggggh     kusahara    MobileMan   nick800418 
    ##            1            1            1            1            1 
    ##    okmijnuhb   popularman      q99518g      tcl2830 alice2520200 
    ##            1            1            1            1            1 
    ##   chengyuche     dash0804     david597   DickMartin      gnh1021 
    ##            1            1            1            1            1 
    ##      golover  goodboy8899    leo710215   livingroom  magic704226 
    ##            1            1            1            1            1 
    ##    omega0210     orz3qonz    popoallan        s4001        s6307 
    ##            1            1            1            1            1 
    ##     skatopia         wort 
    ##            1            1

用table()把資料框中author欄位中的資料抓出來，再用sort()做大到小的排序，結果顯示wer11的文章數最多，有3篇。

其他結果: (1)由上表知，科技工作版大多數的人都只po過一次文 (2)作者"-"有17筆表示有17篇文章被刪除，因為文章被刪除後作者會顯示為"-" (3)在dataframeAll資料框中可以看到推文數多的大多都是\[討論\]或\[請益\]
