# DiscordBotMods
Warframe Discord 機器人<br/>
基於[MeowXiaoXiang](https://github.com/MeowXiaoXiang/Meow_Bot-Public_Version-/commits?author=MeowXiaoXiang)的[Meow_Bot-Public_Version-](https://github.com/MeowXiaoXiang/Meow_Bot-Public_Version-)開發的Mod<br/>
## Mod列表<br/>
* [worldState.py](worldState.py)查詢當前世界循環狀態<br/>
  * 使用[WFCD](https://github.com/WFCD/)的[API](https://docs.warframestat.us/)數據
* [rivenPrice.py](rivenPrice.py)查詢[wfm](https://warframe.market)上最低價格的五張該武器紫卡<br/>
  * 必須搭配[dict](dict)當中的[Weapons.json](Weapons.json)以及[attributes.json](attributes.json)使用
  * [Weapons.json]當中的武器名稱有機會不齊全，若有無法查詢的武器且你確保自己沒有輸入錯誤，請向我回報bug
* [baroManual.py](baroManual.py)查詢虛空商人Baro Ki'Teer的目前狀態<br/>
  * 感謝[pa001024](https://github.com/pa001024)允許使用[riven.im](https://riven.im)項目的繁體翻譯檔[zh-Hant.json](https://raw.githubusercontent.com/lonnstyle/riven-mirror/dev/src/i18n/lang/zh-Hant.json)作為Dict
  -pip install chinese-converter
* [wfm.py](wfm.py)查詢物品於[wfm](https://warframe.market)上最低價的五個賣家訂單<br/>
  -pip install discord-webhook
  * 請在setting.json當中加入以下數據(可選)：
    "webhook": "<你的webhook URL>"
  <s>需要翻譯Dict以支持功能運行
  * 官方翻譯：[GitLocalize](https://gitlocalize.com/repo/5556/zh/dict/items_en.json)</s>
  * 正在等帶wf.m進行物品翻譯，並使用該翻譯作為日後的官方物品翻譯Dict
  * 自定義暱稱：[Google Sheet](https://docs.google.com/spreadsheets/d/1AMxTBp1_HdVbjdxnpTGqy_16OoP-CBeBc9117ZXGhEQ/edit?usp=sharing)
* [worldStateAuto.py](worldStateAuto.py)自動查詢世界循環狀態<br/>
  * 僅允許owner執行，避免重複查詢對API伺服器造成負擔
  * 目前僅支援仲裁/突擊，避免對伺服器造成洗板；如有大量回饋讚成開啟平原時間查詢，將作出更新
* [wiki.py](wiki.py)生成wiki鏈接<br/>
  -pip install mwclient
  * 查詢順序為[簡中](https://warframe.huijiwiki.com)→[繁中](https://warframe.fandom.com/zh-tw)→[英文](https://warframe.fandom.com)

## 指令列表<br/>
**所有指令均需要搭配指令前綴使用，可在機器人框架中的setting.json中修改**
* [worldState.py](worldState.py)當中的指令
  * POE/夜靈平原時間/poe  查詢夜靈平原目前日夜循環狀態和剩餘時間
  * Earth/地球時間  查詢地球目前日夜循環狀態和剩餘時間
  * Cambion/魔裔禁地時間  查詢魔裔禁地目前日夜循環狀態和剩餘時間
  * Orb/奧布山谷時間/orb  查詢奧布山谷目前日夜循環狀態和剩餘時間
  * Arbitration/仲裁  查詢目前仲裁任務和剩餘時間（此功能由於API不穩定，返回數據未必準確）
  * Sortie/突擊/sortie  查詢目前突擊任務和剩餘時間
* [rivenPrice.py](rivenPrice.py)當中的指令
  * riven/紫卡/紫卡查詢 [武器名稱]  查詢該武器最低價的三個在線賣家訂單
* [baroManual.py](baroManual.py)當中的指令
  * baro/奸商/Baro  查詢虛空商人Baro Ki'Teer目前狀態，如已經抵達中繼站則會顯示所攜帶商品列表
  * 此功能的自動版正在壓力測試中
* [wfm.py](wfm.py)當中的指令
  * wfm/wm/市場查詢 [物品名稱]  查詢該物品於wf.m上最低價的五名賣家訂單
  * reloadDict  Dict更新同步（目前僅支持官方翻譯Dict的更新）
  * 此功能所使用的Dict尚未編寫完成
  * 使用[GitLocalize](https://gitlocalize.com/repo/5556/zh/dict/items_en.json)協助完成官方翻譯的Dict編寫
  * 使用[Google Sheet](https://docs.google.com/spreadsheets/d/1AMxTBp1_HdVbjdxnpTGqy_16OoP-CBeBc9117ZXGhEQ/edit?usp=sharing)編寫自定義Dict
* [worldStateAuto.py](worldStateAuto.py)當中的指令
  * **延遲時間建議為150秒或以上，避免API返回空白數據導致執行出錯**
  * ArbitrationAuto [延遲時間（秒）] 在指定延遲時間後查詢當前仲裁任務和剩餘時間
  * SortieAuto [延遲時間（秒）] 在指定延遲時間後查詢當前突擊任務和剩餘時間
* [wiki.py](wiki.py)
  * wiki [頁面名稱] 查詢wiki並生成鏈接
  * 為避免對wiki伺服器造成過大壓力，未啟用模糊搜索，**請確保你輸入的頁面名稱並無出錯**
  * 由於並非所有wiki頁面均有section,因此嵌入內容為頁面源代碼的前**500**字元
  
<br/><br/>
<a href="https://www.patreon.com/bePatron?u=47066858" data-patreon-widget-type="贊助lonnstyle開發機器人">贊助lonnstyle開發機器人</a>
