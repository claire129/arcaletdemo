arcalet物件模型
===============

Release Note
------------

2016/0331 API 2.3.0

新增ArcaletGuild與ArcaletMailbox兩個class

2015/1105 API 2.2.2 Build 1439

新增GetPlayerRank()的overloading參數與回傳結果

2015/0920 API 2.2.1 Build 1425

1.  **新增
    GetPlayerRank()的Overloading，傳回包含玩家自己以外，排行榜上下的名單**

2.  **新增GetItemInstanceEx()，如果Item在後台設定為公開，可以透過此函式讀取別的玩家的資料。**

3.  **GetPlayerRegister() 會一併傳回register上次更新的時間**

4.  **GetRandomPlayer() 會一併傳回register上次更新的時間**

2015/09/20 API 2.2.0 Build 1411

1.  新增api: ArcaletSystem.ResetPlayerPassword()

2.  暱稱系統改版:

>   原本暱稱是跟著玩家帳號，改為跟著玩家與遊戲，也就是說，同一玩家在不同遊戲可以有不同的帳號。

>   ArcaletGame.SetPlayerNickname() 設定目前登入的遊戲中的暱稱

>   ArcaletGame.GetPlayerNickname() 取得目前登入的遊戲中的暱稱

>   ArcaletGame.suSetPlayerNickname() super user可以修改其它玩家的暱稱

1.  新增玩家在遊戲中的暫存器，共4個，AX,BX,CX,DX，都是32位元有號整數

>   ArcaletGame.SetPlayerRegister()
>   設定玩家暫存器(參數傳null，表示不設定該暫存器)

>   ArcaletGame.suSetPlayerRegister()
>   設定玩家暫存器(參數傳null，表示不設定該暫存器)

>   ArcaletGame.GetPlayerRegister() 讀取玩家暫存器

>   ArcaletGame.suGetPlayerRegister() 讀取玩家暫存器

1.  隨機挑選玩家，傳回其userid與register

>   ArcaletGame.GetRandomPlayer()

2014/07/28(文件補充)

1.  ArcaletGame.SetPlayerNicknam()補充說明ArcaletGame.nickname

2014/04/23 API 2.0.1 Build 1259

1. 取消ArcaletScene.SendOnClose()，當玩家離線時廣播訊息至場景改為

ArcaletGame.SendOnClose(String,ArcaletScene)

2. 修改ArcaletGame.SendOnClose(int poid,String
msg)的參數順序，把poid放到後面，這樣和Send()的，當玩家離線時廣播訊息至場景改為

2014/03/26 API 2.0.1

1. 取消ArcaletSystem.ApplyNewUser的ArcaletGame參數

2. 取消ArcaletGame的無參數建構子

2014/03/25 API 2.0.1

>   1. 全新Super User
>   API，可指定玩家帳號隨時存取其資料，玩家改由參數userid指定，並且不受該玩家必須在線，或剛離線的限制，原本以poid指定的方式仍然相容，但未來將會取消。

>   2. Super User API的Method名稱都以「su」開頭，方便識別。

>   3. 新增ArcaletShop.CommitInAppBilling()，提供Google
>   Play內置購買的收據與電子簽章驗證。

>   4. 取消ArcaletGame.EventDispatcher()。

>   5. 修正在Unity Web Player中，API程式無法持續的問題。

>   6. 整合STALaunch()到 Launch()中，可以自動使用STA，另外，因為Unity3D
>   4.X已經支援.Net HTTP，所以也不需要使用WebLaunch()。

>   7. 修改建立帳號的Method參數

>   8. 新增ArcaletSystem.ServerTimeOfLastApiCall()的說明

>   9. 新增ArcaletGame.SendOnClose()的overloading

>   10. 新增ArcaletScene.SendOnClose()，當玩家離線時廣播訊息至場景。

>   11.新增ArcaletSystem.UnityEnvironment()，在AGCC的Update()呼叫。

2014/01/14 API 1.7.8

>   1. 優化API對arcalet資料庫伺服器網路存取校能。

>   2. 新增ArcaletSystem.SetDatabaseApiConcurrentRequest(int
>   MaxValue)讓開發者可以調整同時發出資料庫存取API的最大數。

2013/11/13 API 1.7.5

>   1.
>   優化API的背景服務效能，尤其是針對DP程式的鉅量服務需求，對於場景(ArcaletScene)、資料庫(ArcaletItem,
>   ArcaletScore, ArcaletShop,
>   ArcaletSystem)等API使用更佳的執行緒池(ThreadPool)演算法。此演算法並提供ArcaletSystem類別庫方法讓開發者進行參數微調。

>   2. 提供高效能的ArcaletThreadPool讓開發者選擇，以替代.Net
>   Framework的ThreadPool。此演算法的優點是當背景工作時程較短，且在短時間有大量的背景工作需求時，系統不會有大量執行緒物件的生成與消滅，避免DP長時間工作之後發生Garbage
>   Collection對於新執行緒的生成產生嚴重的延遲，如果背景工作對於即時性的要求較高時，這樣的延遲就會對服務產生極大的影響。

2013/10/31 API 1.6.18

1.
本文件ArcaletScore.GetLeaderBoard()之說明中，參數type=0改為總排行，而非全部排行。

2. 優化ArcaletGame.Send()與ArcaletScene.Send()

2013/09/27 API 1.6.16

>   1.
>   新增兩個(含超級使用者)GetItemInstanceAttribute()的overlading，參數attrName為陣列字串，一次可以讀取多個屬性欄位，並且傳回List\<Hahtable\>。

>   2.
>   新增兩個(含超級使用者)GetItemInstance()的overlading，參數iguid為陣列字串，一次可以讀取多個不同的iguid的item
>   instance。

>   3.
>   新增兩個(含超級使用者)GetItemClass()的overlading，參數iguid為陣列字串，一次可以讀取多個不同的iguid的item
>   class資料。

2013/09/05 API 1.6.14

>   新增兩個(含超級使用者)SetItemInstanceAttribute()的overlading，參數attrName,attrValue為陣列字串，一次可以設定多個屬性欄位。

2013/09/02 API 1.6.13

1.
ArcateItem.GetItemInstance()新增兩個Overloading，當有iguid參數時，可以指定autonew參數。

autonew=true 如果玩家物品還沒有實例時，則自動新增後傳回

2.登入時會自動取得玩家暱稱，並放在ArcaletGame.nickname中，如果失敗，

則OnCompletion的code參數為108

3.新增ArcaletGame.SetPlayerNickname()，用來改變(設定)玩家的暱稱

4.新增兩個ArcaletScore.CommitLeaderBoard()的Overloading

以參數Note傳入備註字串，並寫入排行版資料中，日後讀取排行榜時，此備註字串會伴隨成績資料被讀取出來。

5.新增兩個ArcaletScore.GetLeaderBoard()傳回的成績Hashtable增加兩個Key:
nickname與note

2013/07/16 API 1.6.8

>   ◎增加由伺服器建立玩家帳號的API

>   1. **ArcaletSystem.ApplyNewUser之**Overloading Method  
>   static void ApplyNewUser(ArcaletGame game, string gguid, byte[] gamecode,
>   OnCallCompletionWithData cb, object token, bool usePSTA);

>   2. **ArcaletSystem.UpgradeUser**  
>   static void UpgradeUser(ArcaletGame game, string userid,string passwd,string
>   email, OnCallCompletion cb, object token);

>   3. **ArcaletGame之Overloading Constructor**  
>   ArcaletGame();

>   ◎ArcaletGame.GetUserStatus()改為ArcaletGame.GetUserLevel()，並調整Level值。

arcalet API說明
---------------

1. Synchronization問題

arcalet
API物件的所有method都是設計成non-blocking，呼叫的狀態結果由Event與Callback兩種方式通知呼叫者。由於多數視窗平台與遊戲引擎限制只能在主執行緒中控制應用程式的GUI，因此呼叫者必須在主執行緒中建立物件或是呼叫有callback的物件method，arcalet
API將會在主執行緒觸發Event或Callback。

請注意:
在原執行緒觸發Event或Callback並非絕對，因為執行緒是無法被應用系統中斷的。因此若要arcalet
API能在原執行緒觸發Event或Callback，則主執行緒必須由訊息佇列的所控制，一般來說Windows應用程式的每一個控制項，包含視窗本身，都是由主視窗的訊息佇列的所控制，但如果開發者是以類似console應用程式開發遊戲，就必須採用虛擬STA
(Pseudo Single Thread Apartment)的執行緒模型來完成原執行緒觸發Event與Callback。

虛擬STA模型是由主執行緒定時不斷的呼叫ArcaletGame.EventDispatcher
()，多數的遊戲引擎都是frame-based的系統，開發者可在每一個frame觸發處呼叫此method。

2. 事件處理

遊戲開發者有兩種方式撰寫事件處理程式，第一種是使用override
method，開發者可以自行設計繼承自arcalet
calss的物件，然後在此物件內改寫class內的事件。另外一種是使用「事件屬性變數」，指定某事件的處理函式，這種方法不必另外設計物件，可直接使用。

另外要注意的事，若沒有指定「事件屬性變數」，也沒有改寫原class內的事件，那麼事件將會失效，可是不會發生錯誤；如果指定了「事件屬性變數」，也在繼承物件中改寫了原事件，那麼只有「事件屬性變數」所指示的事件函式會被觸發。

3. Callback

Callback有兩種，分別是OnCallCompletion與OnCallCompletionWithData，前者只是單純傳回method的執行狀態，後者除了傳回狀態外，還可傳回物件。OnCallCompletion與OnCallCompletionWithData的method
prototype如下:

void OnCallCompletion(int *code*, object *token*)

void OnCallCompletionWithData(int *code*, object *data*, object *token*)

4. arcalet API共有六個class

1.  ArcaletGame (遊戲class)

>   建立此物件將會讓玩家的遊戲與arcalet的遊戲伺服器建立連線，在連線的狀態的下才能與其他玩家即時互動，也才能使用ArcaletScene、ArcaletItem、ArcaletScore等物件。

>   由於遊戲一開始都會進入所謂的「大廳系統」，因此arcalet設計每一個遊戲都會有一個預設的場景做為大廳場景，預設場景是「靜態場景」，也是在建立遊戲時一併建立的。大廳場景跟一般遊戲場景不同，它不能進入與離開，它在遊戲物件的連線完成後就已經存在，除非連線終止，玩家始終會收到大廳中的訊息，也隨時可以發送訊息至大廳。

>   遊戲進行有時也會傳遞私人訊息，因此遊戲物件裡面也有一個特殊的場景，我們稱之為私人場景。私人場景與一般的遊戲場景最大的不同是，私人場景沒有進入與離開的概念，它在遊戲連線之後就已經存在，直到連線終止。

1.  ArcaletScene (場景class)

>   場景是遊戲玩家互動的基礎，在arcalet的場景概念裡，玩家可以同時身處多個場景，其設計與規劃基礎由遊戲開發者自行決定。

>   場景又分為「靜態場景」與「動態場景」，「靜態場景」不會有多個複本(instance)，只能進入、離開，不能創建；「動態場景」則可依開發者與玩家的需要建立新的複本，因此可以被創見而產生一個複本，已經創建的動態場景複本才能進入與離開。

1.  ArcaletItem (物品class)

>   物品分為三種，商品(Goods)、性質(Property)、資料(Data)。

>   「商品」是遊戲中的寶物或道具，可在arcalet商城中販售，玩家付出arca幣後取得商品，arca幣則轉存至開發者的arca帳戶中，開發者可在累積一定的arca幣之後提領現金。

>   「性質」可讓程式設計師用來描述玩家在遊戲中的某些特性，例如身高、體重等，不只如此，它也可以用來代表寶物、道具、功能等，不過由於性質無法販售，所以不會在商城中顯示。新增或存取性質只能透過arcalet
>   API在遊戲程式中實現。

>   「資料」是玩家存放遊戲資料的記憶體，內容不會因為玩家離線或關機而消失，是一種超越本機電腦的非揮發性(non-volatile)記憶體。

1.  ArcaletScore (積分版class)

>   登錄遊戲分數，由伺服器可統計分數，並產生積分版(Leaderboard)。

5. ArcaletShop(商店Class)

>   這是專為iOS App Store與Google Play所設計，支援App內置購買的收據簽章檢查。

>   (1) iOS App Store: 支援App應用程式以「Server Product
>   Delivery」模式直接購買商品。

>   由於App
>   Store上架準則規定應用程式內不可以使用Apple公司以外的電子商務系統，所以應用程式遵照iOS開發守則建立In-App
>   Purchase功能，當玩家購買商品後，必須透過ArcaletShop.CommitInAppPurchase()函式，由Arcalet伺服器向App
>   Store驗證購買後的收據(Receipt)是否合法。

>   (2) Google Play In-App Billing

>   檢查Google Play商店傳回的收據電子簽章是否合法。

6. ArcaletSystem (系統Class)

>   與arcalet系統有關的功能函式。

arcalet物件摘要
---------------

ArcaletGame

Constructor

ArcaletGame(string *userid*,string *passwd*,string *gguid*,string *sguid,*
byte[] *certificate*)

**ArcaletGame()**

Method

void Dispoise()

void Launch()

void Launch(int timeout)

void WebLaunch() (Unity3D 3.X版 Web Player使用)

void WebLaunch(int timeout)

void STALaunch() (Unity3D使用，arcalet 2.X已經整合到Launch())

void STALaunch(int timeout)

void Send(string *msg*)

void PrivacySend(string *msg*,int *poid*)

void SendOnClose(string *msg*)

void SendOnClose(string *msg,* int *poid*)

**void SendOnClose(string msg, ArcaletScene scene)**

void StartDelayDetectionRadar(int *speed*)

void GetDelayMilliseconds()

void SetPlayerStatus(int *status*,OnCallCompletion *cb*, object *token*)

void SetPlayerStatus(int *status*,int *level*, OnCallCompletion *cb*, object
*token*)

void SetPlayerLevel(int *level*, OnCallCompletion *cb*, object *token*)

void FindPlayersByStatus(int *status*, OnCallCompletionWithData *cb*, object
*token*)

void FindPlayersByLevel(int *level,* OnCallCompletionWithData *cb*, object
*token*)

void GetSceneInstances(string *sguid*, OnCallCompletionWithData *cb*, object
*token*)

void EventDispatcher()

void SetPlayerNickname(string *nickname*, OnCallCompletion *cb*, object *token*)

void suSetPlayerNickname(string *userid*, string *nickname*, OnCallCompletion
*cb*, object *token*)

void suGetPlayerNickname(string *userid*,OnCallCompletionWithData *cb*, object
*token*)

void SetPlayerRegister(object *AX*, object *BX*, object *CX*, object *DX*,  
OnCallCompletion *cb*, object *token*)

void suSetPlayerRegister(string *userid*, object *AX*, object *BX*, object *CX*,
object *DX*,  
OnCallCompletion *cb*, object *token*)

void GetPlayerRegister(OnCallCompletionWithData *cb*, object *token*)

void suGetPlayerRegister(string *userid*, OnCallCompletionWithData *cb*, object
*token*)

void GetRandomPlayer(OnCallCompletionWithData *cb*, object *token*)

void GetRandomPlayer(int *number*,OnCallCompletionWithData *cb*, object *token*)

void GetRandomPlayer(bool *online*, OnCallCompletionWithData *cb*, object
*token*)

void GetRandomPlayer(string *registercondition*, OnCallCompletionWithData *cb*,
object *token*)

void GetRandomPlayer(int *number*, bool *online*, OnCallCompletionWithData *cb*,
object *token*)

void GetRandomPlayer(int *number*, string *registercondition*,
OnCallCompletionWithData *cb*, object *token*)

void GetRandomPlayer(object *online*, string *registercondition*,
OnCallCompletionWithData cb, object *token*)

void GetRandomPlayer(int *number*, object *online*, string *registercondition*,  
OnCallCompletionWithData *cb*, object *token*)

Property

int *sid* (read only)

int *poid* (read only)

object *token* (read / write)

string *nickanem* (read only)

Event (可以override)

void OnCompletion(int *code*, ArcaletGame *game*)

void OnStateChanged(int *state*, int *code*, ArcaletGame *game*)

void OnMessageIn(string *Msg*, int *delayMilliSecond*, ArcaletGame *game*)

void OnPrivateMessageIn(string *Msg*, int *delayMilliSecond*, ArcaletGame
*game*)

Event Property (Event與Event Property可擇一使用)

onCompletion

onStateChanged

onMessageIn

onPrivateMessageIn

以上Event
Property所指定的Event處理函式的定義與Event函式完全一樣，請參考前Event定義原型。

ArcaletScene

Constructor

ArcaletScene(ArcaletGame *game*,string *sguid*)

ArcaletScene(ArcaletGame *game*,string sguid,int *sid*)

ArcaletScene(ArcaletGame *game*,string *sguid*,bool *isLocked*)

Method

void Launch()

void Match()

void FairMatch()

void Send(string *msg*)

void SetProperty(string *key*,string *value*, OnCallCompletion *cb*, object
*token*)

void SetProperty(string *key*, int *value*, OnCallCompletion *cb*, object
*token*)

void GetCreatorInfo(OnCallCompletionWithData *cb*, object *token*)

void Leave(OnCallCompletion *cb*, object *token*)

void SendOnClose(string *msg*)

Property

int *sid* (read only)

string *sguid* (read only)

object *token* (read / write)

Event (可以override)

void OnCompletion(int *code*, ArcaletScene *scene*)

void OnMessageIn(string *Msg*, int *delayMilliSecond*, ArcaletScene *scene*)

Event Property (Event與Event Property可擇一使用)

onCompletion

onMessageIn

以上Event
Property所指定的Event處理函式的定義與Event函式完全一樣，請參考Event定義原型。

ArcaletItem

ArcaletSystem

static String ServerTimeOfLastApiCall()

static void UpgradeUser(ArcaletGame *game*, string *userid*,string
*passwd*,string *email*,  
OnCallCompletion *cb*, object *token*)

static void ApplyNewUser(string *gguid*, byte[] *gcert*, string *userid*, string
*passwd*, string *email*,  
OnCallCompletion cb, object *token*)

static void ApplyNewUser(string *gguid*, byte[] *gcert*,
OnCallCompletionWithData *cb*, object *token*)

static void UnityEnvironment()

static void ResetUserPassword(string *userid*, string *oldpasswd*, string
*newpasswd*,  
string *gguid*, byte[] *gcert*, OnCallCompletion *cb*, object *token*)

ArcaletGame

### Description

>   使用arcalet遊戲伺服器要先建立此物件，遊戲的建立與管理必須在arcalet開發者網站http://api.arcalet.com中進行，開發者建立了一個新的遊戲時，系統會產生一個唯一的遊戲識別碼，我們稱為Game
>   GUID，簡稱GGUID，同時也會自動建立一個靜態場景，這個場景是用來做為大廳系統的訊息傳遞之用的，同樣的，場景也會有一個唯一的場景識別碼，我們稱為Scene
>   GUID，簡稱SGUID。此外，系統也會產生一個用來做安全識別的「遊戲憑證碼」，長度為128
>   bytes。有了GGUID、SGUID、遊戲憑證碼與帳號密碼，就可以用來產生ArcaletGame物件。

>   ArcaletGame建立之後，程式設計師必須接著使用Launch()
>   method讓遊戲程式連線到遊戲伺服器，連線成功後才能進行即時訊息傳遞與接收，訊息收發是以遊戲場景為主，對於在同一場景內的遊戲玩家們而言，訊息是完全透明可見的。

>   ArcaletGame物件內有一個做為大廳使用的靜態場景，與接收私人訊息用的私人場景，遊戲開發者必須自訂訊息內容，並依其自訂的訊息內容處理遊戲場景畫面。

### Constructor

>   ArcaletGame( string *playerUserId*,

>   string *playerGamePasswd*,

>   string *gameGUID*,

>   string *sceneGUID*,

>   byte[] game*Certificate*)

*playerUserId* 遊戲玩家之帳號

*playerGamePasswd*  
遊戲玩家之遊戲登入密碼(非web管理後台登入密碼)

*gameGUID* 遊戲之GUID，簡稱GGUID，是遊戲建立時由系統自動產生。

*sceneGUID*
遊戲預設場景之GUID，簡稱SGUID，此場景為靜態場景，是遊戲建立時系統自動建立之預設場景，通常被用在遊戲大廳。

*gameCertificate* 遊戲憑證碼，是一個128
bytes的陣列，是遊戲建立時由系統自動產生。

>   ArcaletGame()

>   沒有指定任何參數，也不能Launch()，用來呼叫ArcaletSystem.ApplyNewUser()以註冊正式帳號。

### Method

>   void Launch()

建立arcalet物件後，呼叫Launch()進行伺服器連線，有兩個overloading，此一overloading沒有指定連線逾，使用系統預設值，超過時間若無法連線成功，則以連線逾時觸發OnCompletion。

>   void Launch(int *timeout*)

*timeout* 指定連線逾時秒數。

>   void WebLaunch()

※Unity3D 4.x版後已經不需要使用WebLaunch()。

如果是Unit3D 3.x版，在建立Web應用程式(也就是Unity3D的Web
Player程式)，建立arcalet物件後，必須呼叫WebLaunch()進行伺服器連線，有兩個overloading，此一overloading沒有指定連線逾，使用系統預設值，超過時間若無法連線成功，則以連線逾時觸發OnCompletion。

>   void WebLaunch(int *timeout*)

*timeout* 指定連線逾時秒數。

>   void STALaunch()

※arcalet API 2.x已經不需要STALaunch()，但為與前版相容仍舊存在。

在某些無法使用標準執行緒的開發環境(例如Unity3D)，在建立arcalet物件後，必須呼叫STALaunch()進行伺服器連線，有兩個overloading，此一overloading沒有指定連線逾，使用系統預設值，超過時間若無法連線成功，則以連線逾時觸發OnCompletion。

>   void STALaunch(int *timeout*)

*timeout* 指定連線逾時秒數。

>   Int GetUserLevel()

玩家登入成功後，透過此method傳回玩家的會員狀態。

0: 所登入的帳號「系統取得帳號」

1: 玩家註冊之正式帳號，或是由Level 0升級之正式帳號，但未通過e-mail認證

2: 已通過e-mail認證之正式帳號

3: VIP玩家，不受遊戲之CCU Max限制。

>   void Dispose()

結束與伺服器的連線，此後ArcaletGame物件就無法再使用，若要重新連線，必須重新建立一個全新的ArcaletGame物件，然後再Launch()。

>   void Send(string *msg*)

*msg* 訊息資料

傳送資料到預設場景，位於此場景內的所有玩家都會收到，包括自己也會收到，因此遊戲開發者在訂定訊息內容時，必須注意到這點。

>   void SendOnClose(string *msg*)

*msg* 訊息資料

預存訊息資料到伺服器，當玩家斷線時才將此訊息傳送給其他玩家，接收者以預設場景(大廳)接收此訊息。

>   void SendOnClose(string *msg,* int *poid*)

*msg* 訊息資料

預存訊息資料到伺服器，當玩家斷線時才將此訊息傳送給其他玩家，此overloading可以指定接收者的poid，將離線訊息傳給特定在線的使用者，在實務上通常是DP的poid。

>   **void SendOnClose(string msg, ArcaletScene scene)**

>   **scene 指定要傳到此場景**

>   **msg 訊息資料**

**預存訊息資料到伺服器，當玩家斷線時才將此訊息傳送給其他玩家，此overloading可以指定特定場景，將離線訊息傳給在此場景中的使用者。**

>   void PrivacySend(string *data*,int *poid*)

*data* 訊息資料

*poid* 接收者的*poid*

傳送訊息給指定的玩家，以*poid* (私人場景*id*)指定收訊者。

>   void StartDelayDetectionRadar(int *speed*)

*speed* 偵測間隔擋次，共分0到5擋，。

啟用封包延遲偵測雷達，用來偵測本地與遊戲伺服器之間封包傳遞之延遲時間。

偵測雷達共分5個檔次，依雷達偵測間隔而定，5檔間隔最短，適合用在對即時性要求較高的遊戲，1檔間隔最長，適合用在對即時要求不高的遊戲。0擋則為停止偵測。

擋次的選擇請依遊戲特性而定，選擇高速擋，獲得的資訊最新最正確，但是會耗去玩家較大的頻寬，反之選擇低速擋可減少頻寬耗用，但獲得的可能是較早之前的偵測資訊。

偵測雷達請在ArcaletGame物件啟動成功，也就是ArcaletGame.OnCompletion()被觸發，且狀態碼是成功時啟動。

>   void GetDelayMillisecond()

取得目前本地與遊戲伺服器之間封包傳遞之延遲時間，單位為millisecond。使用此資訊必須先以StartDelayDetectionRadar()啟動封包延遲偵測雷達。

>   void SetPlayerStatus(int *status*,OnCallCompletion *cb*, object *token*)

設定本地玩家的status，讓其他玩家可以透過FindPlayersByStatus()搜尋所有相同status的玩家。

void cb(int *code*, object *token*)

*code* 0 設定成功

非0 設定失敗

>   void SetPlayerStatus(int *status*,int *level*, OnCallCompletion *cb*, object
>   *token*)

設定本地玩家的status與level，他玩家可以透過FindPlayersByStatus()或FindPlayersByLevel()搜尋所有相同status若level的玩家。

void cb(int *code*, object *token*)

*code* 0 設定成功

非0 設定失敗

>   void SetPlayerLevel(int *level*, OnCallCompletion *cb*, object *token*)

設定本地玩家的level，讓其他玩家可以透過FindPlayersByLevel()搜尋所有相同status的玩家。

void cb(int *code*, object *token*)

*code* 0 設定成功

非0 設定失敗

>   void FindPlayersByStatus(int *status,* OnCallCompletionWithData *cb*, object
>   *token*)

依status搜尋所有符合條件的玩家，*cb*傳回List\<Hashtable\>，當中每一個Hashtable包含兩欄玩家資訊，分別是”userid”與”poid”，其中”userid”是該玩家的帳號名稱，”poid”是其私人的場景ID。

void cb(int *code,* object *obj*, object *token*)

>   *code* 0
>   Find成功，obj要改型成List\<Hashtable\>，存放找的的Players資料，如果List.Count為零，表示沒有找到符合status的player。

非0 Find失敗

*obj* 型態為List\<Hashtable\>，Hashtable包含兩個Key：  
userid 玩家帳號

poid 私人場景

範例: 取出傳回的玩家資訊

>   List\<Hashtable\> s = (List\<Hashtable\>)obj;

>   string userid;

>   int poid;

>   foreach (Hashtable node in s) {

>   userid=node[“userid”];

>   poid=node[“userid”];

>   // to process userid and poid here

>   }

>   void FindPlayersByLevel(int *level*, OnCallCompletionWithData *cb*, object
>   *token*)

依level搜尋我有符合條件的玩家，詳情請參考FindPlayersByStatus()。

>   void GetSceneInstance(string *sguid*,OnCallCompletionWithData *cb*, object
>   *token*)

取得動態場景目前已經建立的場景複本，*cb*傳回List\<Hashtable\>，當中每一個Hashtable包含兩欄玩家資訊，分別是”sid”與”count”，其中”sid”是場景複本ID，”count”是進入該場景的玩家人數。

void cb(int *code,* object *obj*, object *token*)

*code* 0 設定成功

非0 設定失敗

範例: 取出傳回的場景複本資訊

>   List\<Hashtable\> s = (List\<Hashtable\>)obj;

>   int sid;

>   int count;

>   foreach (Hashtable node in s) {

>   sid=node[“sid”];

>   count=node[“count”];

>   // to process sid userid and count here

>   }

>   void EventDispatcher()

在執行Launch()之前設定物件屬性UsePseudoSTA為true，開發者在主控執行緒中必須周期性的呼叫EventDispatcher()，API將會使用Pseudo
STA的執行緒模型來觸發事件與呼叫callback函數。

>   void SetPlayerNickname(string *nickname*, OnCallCompletion *cb*, object
>   *token*)

設定(更改)玩家的暱稱，暱稱不可以有空白字元，特殊符號只能是「.」、「-」。

設定(更改)玩家的暱稱，暱稱若為空白將會清除該玩家的暱稱。

暱稱不限定是否英數字，開發者若希望自己的遊戲世界的暱稱不要太奇怪，請自行增設過濾條件，讓玩家只能輸入合於該遊戲規定的暱稱格式。

暱稱預設是可以重複的，開發者可在arcalet管理後台設定該遊戲是否要限制玩家暱稱是否不能重複，不過請注意，遊戲一但設定玩家暱稱不可重複，就無法再改回可重複。

void cb(int *code*, object *token*)

*code* 0 設定成功，同時更新ArclatGame.nickname的值

非0 設定失敗

>   void SetPlayerRegister(object *AX*, object *BX*, object *CX*, object *DX*,  
>   OnCallCompletion *cb*, object *token*)

*AX* 要設定的AX register資料，必須是整數，若不要設定AX，則傳入null。

*BX* 要設定的BX register資料，必須是整數，若不要設定BX，則傳入null。

*CX* 要設定的CX register資料，必須是整數，若不要設定CX，則傳入null。

*DX* 要設定的DX register資料，必須是整數，若不要設定DX，則傳入null。

設定玩家的register資料。Register是一種比ArcaletItem更快速方便儲存玩家狀態的資料系統，每個玩家在遊戲中都有專屬的四個register，名稱分別是AX,
BX, CX,
DX，這四個register都是整數型別，開發者可以自行定義其用途，除了可以透過GetPlayerRegister()讀取外它們的值，更重要是的，如果遊戲想要透過ArcaletGame.GetRandomPlayer()請求arcalet系統隨機挑選不特定的玩家，(例如隨機組隊)，還可以指定register的條件，符合條件的玩家才有可能被挑選出來。隨機挑選玩家的詳細說明請參考ArcaletGame.GetRandomPlayer()。

請注意，CX與DX只有玩家自己與super
user可以讀取，ArcaletGame.GetRandomPlayer()隨機挑選到的玩家，只會傳回userid、nickname、還有AX與BX。

>   void GetPlayerRegister(OnCallCompletionWithData cb, object token)

讀取玩家的register資料，透過callback傳回，放在Hashtable中。

void cb(int *code,* object *obj*, object *token*)

*code* 0 設定成功

非0 設定失敗

*obj* Hashtable，所讀取的的register資料

**Key Value**

userid 玩家的userid

ax 玩家的ax register值

bx 玩家的bx register值

cx 玩家的cx register值

dx 玩家的dx register值

**axstamp 上次設定ax register的時間。**

**bxstamp 上次設定bx register的時間。**

**cxstamp 上次設定cx register的時間。**

**dxstamp 上次設定dx register的時間。**

>   void GetRandomPlayer(OnCallCompletionWithData cb, object *obj*, object
>   token)

隨機傳回一個玩家資料，不設任何條件，玩家資料透過callback參數傳回。

*code* 0 設定成功

非0 設定失敗

>   *obj*
>   List\<Hashtable\>,傳回的玩家資料，因為只傳回一個玩家資料，所以List只會有一個Hashtable:

**Key Value**

userid 玩家的userid

nickname 玩家的暱稱，如果玩家沒有設定，就不會有這個key

online 0: 玩家不在線上，1: 玩家在線上

ax 玩家的ax register值

bx 玩家的bx register值

cx 玩家的cx register值

dx 玩家的dx register值

**axstamp 上次設定ax register的時間。**

**bxstamp 上次設定bx register的時間。**

**cxstamp 上次設定cx register的時間。**

**dxstamp 上次設定dx register的時間。**

void GetRandomPlayer(int *number*,OnCallCompletionWithData *cb*, object *token*)

*number* 要求傳回的玩家數，最大值25，超過仍是25。

隨機傳回多個玩家資料，不設任何條件，玩家資料透過callback參數傳回，傳回的格式請參考第一個overloading。

void GetRandomPlayer(bool *online*, OnCallCompletionWithData *cb*, object
*token*)

*online* true，只要線上的玩家，false，只要離線的玩家

隨機傳回一個玩家資料，並且指定要線上或離線玩家，玩家資料透過callback參數傳回，傳回的格式請參考第一個overloading。

void GetRandomPlayer(string *registercondition*, OnCallCompletionWithData *cb*,
object *token*)

>   *registercondition*
>   指定register狀態值的條件運算式，運算式是以「\>」、「\<」、「=」、「&」、「\|」和ax,
>   bx, cx, dx, now-axstamp, now-bxstamp, now-cxstamp,
>   now-dxstamp組成的運算式字串，例如:  
>   “(ax \> 3 & ax\< 5) \| ( cx = 3) & (now-axstamp\>36800)”

隨機傳回一個玩家資料，並且限定在符合register狀態值的條件運算式下隨機取得，玩家資料透過callback參數傳回，傳回的格式請參考第一個overloading。

void GetRandomPlayer(int *number*, bool *online*, OnCallCompletionWithData *cb*,
object *token*)

*number* 要求傳回的玩家數，最大值25，超過仍是25。

*online* true，只要線上的玩家，false，只要離線的玩家

隨機傳回多個玩家資料，並且指定要線上或離線玩家，玩家資料透過callback參數傳回，傳回的格式請參考第一個overloading。

void GetRandomPlayer(int *number*, string *registercondition*,
OnCallCompletionWithData *cb*, object *token*)

*number* 要求傳回的玩家數，最大值25，超過仍是25。

>   *registercondition*
>   指定register狀態值的條件運算式，運算式是以「\>」、「\<」、「=」、「&」、「\|」和ax,
>   bx, cx, dx, now-axstamp, now-bxstamp, now-cxstamp,
>   now-dxstamp組成的運算式字串，例如:  
>   “(ax \> 3 & ax\< 5) \| ( cx = 3) & (now-axstamp\>36800)”

隨機傳回多個玩家資料，並且限定在符合register狀態值的條件運算式下隨機取得，玩家資料透過callback參數傳回，傳回的格式請參考第一個overloading。

void GetRandomPlayer(object *online*, string *registercondition*,
OnCallCompletionWithData cb, object *token*)

*online* true，只要線上的玩家，false，只要離線的玩家

>   *registercondition*
>   指定register狀態值的條件運算式，運算式是以「\>」、「\<」、「=」、「&」、「\|」和ax,
>   bx, cx, dx, now-axstamp, now-bxstamp, now-cxstamp,
>   now-dxstamp組成的運算式字串，例如:  
>   “(ax \> 3 & ax\< 5) \| ( cx = 3) & (now-axstamp\>36800)”

隨機傳回一個玩家資料，並且指定要線上或離線玩家，且限定在符合register狀態值的條件運算式下隨機取得，玩家資料透過callback參數傳回，傳回的格式請參考第一個overloading。

void GetRandomPlayer(int *number*, object *online*, string *registercondition*,  
OnCallCompletionWithData *cb*, object *token*)

*number* 要求傳回的玩家數，最大值25，超過仍是25。

*online* true，只要線上的玩家，false，只要離線的玩家

>   *registercondition*
>   指定register狀態值的條件運算式，運算式是以「\>」、「\<」、「=」、「&」、「\|」和ax,
>   bx, cx, dx, now-axstamp, now-bxstamp, now-cxstamp,
>   now-dxstamp組成的運算式字串，例如:  
>   “(ax \> 3 & ax\< 5) \| ( cx = 3) & (now-axstamp\>36800)”

隨機傳回多個玩家資料，並且指定要線上或離線玩家，且限定在符合register狀態值的條件運算式下隨機取得，玩家資料透過callback參數傳回，傳回的格式請參考第一個overloading。

### Property

int *sid* (read only)

遊戲預設場景(大廳)的場景ID。

int *poid* (read only)

玩家登入遊戲後，系統所指派的識別代號，*poid*也可以視為玩家的私人場景ID。

string *nickname* (read only)

玩家的暱稱，修改此暱稱請使用ArcaletGame.SetPlayerNickname()

bool *UsePseudoSTA*

在執行Launch()之前設定物件屬性UsePseudoSTA為true，啟用Pseudo
STA執行緒模型來觸發事件與呼叫callback函數。若不設定，則為false。

### Event

>   void OnCompletion(int *code*)

物件Launch()結束，*code*為0表示Launch成功，非零則為其錯誤碼，以下是其代表意義：

99 Exception or timeout

101 遊戲登入人數已達Max CCU上線

102 重複登入同一遊戲

103 帳號密碼錯誤

104 無法建立場景

105 無法連線到arcalet遊戲伺服器

106 找不到arcalet遊戲伺服器

>   void OnStateChanged(int *state*,int *code*)

與arcalet遊戲伺服器的連限狀態改變時便會觸發，*state*值之意義如下:

| *State* | **意義**                            | *code*     |
|---------|-------------------------------------|------------|
| 0       | 尚未連線                            | 0          |
| 100     | 正要連線(已經找到arcalet遊戲伺服器) | 0          |
| 200     | 已連線到遊戲伺服器                  | 0          |
| 300     | 已通過伺服器審核                    | 0          |
| 400     | 已通過帳號密碼驗證                  | 0          |
| 500     | 已進入私人場景                      | 0          |
| 600     | 已進入此遊戲的主大廳場景            | 0          |
| 901     | 接收資料時發生錯誤(斷線)            | 系統錯誤碼 |
| 902     | 傳送資料時發生錯誤(斷線)            | 系統錯誤碼 |
| 903     | 偵測網路品質時發生錯誤(斷線)        | 系統錯誤碼 |
| 904     | 接收資料時發生背景作業錯誤(斷線)    | 系統錯誤碼 |
| 905     | 傳送資料時發生背景作業錯誤(斷線)    | 系統錯誤碼 |

>   void OnMessageIn(string *Msg*,int *delayMilliSecond*)

預設場景收到訊息時觸發，若本地程式與訊息發送者兩者都已打開「封包延遲偵測雷達」，參數*delayMilliSecond*會指示訊息可能在多少毫秒前發出。

>   void OnPrivateMessageIn(string *Msg*, int *delayMilliSecond*)

私人場景收到訊息時觸發，若本地程式與訊息發送者兩者都已打開「封包延遲偵測雷達」，參數*delayMilliSecond*會指示訊息可能在多少毫秒前發出。

<br>ArcaletScene
----------------

### Description

>   ArcaletScene是遊戲場景物件，場景分為「靜態場景」與「動態場景」兩種，其建立與管理請至arcalet開發者管理後台網站http://api.arcalet.com進行，當開發者在管理後台建立一個新的場景時，系統會產生一個唯一的場景識別碼，我們稱為Scene
>   GUID，簡稱SGUID。

>   場景物件有三種constructor，使用細節請參閱稍後的說明，物件建立後，程式設計師接著必須呼叫Launch()來進入場景，或是在動態場景使用Match()與FairMatch()，由arcalet伺服器配對進入已經建立的動態場景複本中。

>   玩家進入場景無論成功與否，都會觸發OnCompletion()事件，如果成功進入場景，則會在物件屬性*sid*中存放該場景的SID，與SGUID不同的是，SID是在遊戲進行時才會產生。因此我們通常會將SGUID稱為場景的Class
>   ID，SID則稱為場景的實體ID (Instance ID)，

### Constructor

>   ArcaletScene(ArcaletGame *game*,string *sguid*)

*game* 已建立並連線成功的ArcaletGame物件。

*sguid* 場景的SGUID。

若*sguid*是靜態場景，則接著呼叫Launch()直接進入場景中。

若*sguid*是動態場景，有以下三種做法：

1.  呼叫Launch()建立一個新的場景複本，並進入該場景中。

2.  呼叫Match()，由arcalet伺服器配對進入一個已經建立的場景複本，配對順序以先建立的場景複本為優先，直到該場景的玩家數已到開發者設定的上限後才會再配對至下一個。

>   請注意：若場景的玩家數沒有上限，則arcalet伺服器會自動改採FairMatch()方法配對。

1.  呼叫FairMatch()，依序一個接一個將玩家配對至已建立的場景複本，使用此method可讓各個場景複本都能公平的配對到玩家。

玩家進入場景無論成功與否，都會觸發OnCompletion()事件，如果成功進入場景，傳入OnCompletion的code參數值為零，反之失敗則為非零，如果目前沒有玩家正在等待配對，失敗碼將傳回22，此時就必須重新建立一個ArcaletScene，同時使用Launch()建立一個新的場景實例，等待它人配對進來。

>   ArcaletScene(ArcaletGame *game*,string sguid,int *sid*)

*game* 已建立並連線成功的ArcaletGame物件。

*sguid* 場景的SGUID。

*sid* 場景的SID。

用在動態場景，已知某個已建立的場景複本，用此Constructor建立場景物件，然後呼叫Launch()進入該場景複本。

ArcaletScene(ArcaletGame *game*,string *sguid*,bool *isLocked*)

*game* 已建立並連線成功的ArcaletGame物件。

*sguid* 場景的SGUID。

*isLocked* 決定此場景複本是否接受arcalet伺服器的自動配對。

用在建立動態場景複本，但接下來只能呼叫Launch()，參數*isLocked*為true時，表示這個場景複本不接受arcalet伺服器的自動配對。為false時則與第一個Constructor功能相同。

### Method

void Launch()

進入場景，詳細說明請參考Constructor。

void Match()

配對進入場景，詳細說明請參考Constructor。

void FairMatch()

配對進入場景，詳細說明請參考Constructor。

void Send(string *msg*)

*msg* 訊息資料

傳送資料到預設場景，位於此場景內的所有玩家都會收到，包括自己也會收到，因此遊戲開發者在訂定訊息內容時，必須注意到這點。

void SetProperty(string *key*,string *value*,OnCallCompletion *cb*, object
*token*)

>   *key* 屬性key值

>   *value* 字串型別之屬性值

設定場景屬性，屬性為字串值，如同*key* = value。

void cb(int *code*, object *token*)

*code* 0 設定成功

非0 設定失敗

void SetProperty(string *key*, int *value*, OnCallCompletion *cb*, object
*token*)

>   *key* 屬性key值

>   *value* 整數型別之屬性值

設定場景屬性，屬性為整數值，如同*key* = value。。

void cb(int *code*, object *token*)

*code* 0 設定成功

非0 設定失敗

void GetCreatorInfo(OnCallCompletionWithData *cb*, object *token*)

取得動態場景建立者相關資料。*cb*傳回List\<Hashtable\>，當中每一個Hashtable包含三欄建立此場景副本的玩家資訊，分別是”userid”、”poid”、”certificate”，其中”userid”是玩家帳號，”poid”是該玩家的私人場景代號，”certificate”是該玩家的憑證碼。

void cb(int *code,* object *obj*, object *token*)

*code* 0 設定成功

非0 設定失敗

範例: 取得傳回的動態場景建立者資料

>   List\<Hashtable\> s = (List\<Hashtable\>)obj;

>   string userid;

>   int poid;

>   string certificate;

>   foreach (Hashtable node in s) {

>   userid=node[“userid”];

>   poid=node[“poid”];

>   certificate=node[“certificate”];

>   // to process userid poid and certificate here

>   }

void Leave(OnCallCompletion *cb*, object *token*)

離開場景。

void cb(int *code*, object *token*)

*code* 0 設定成功

非0 設定失敗

void SendOnClose(string *msg*)

*msg* 訊息資料

預存訊息資料到伺服器，當玩家斷線時才將此訊息傳送給其他玩家，接收者以目前場景(大廳)接收此訊息。

### Property

int *sid* (read only)

場景的SID。

string *sguid* (read only)

場景的SGUID。

### Event

>   void OnCompletion(int *code*)

物件Launch()或Match()結束，*code*為0表示成功，非零則為其錯誤碼。

>   void OnMessageIn(string *Msg*, int *delayMilliSecond*)

預設場景收到訊息時觸發，若本地程式與訊息發送者兩者都已打開「封包延遲偵測雷達」，參數*delayMilliSecond*會指示訊息可能在多少毫秒前發出。

<br>ArcaletItem
---------------

### Description

此物件類別用來管理遊戲中的物資，開發者可於arcalet的開發者後台(http://developer.arcalet.com)定義遊戲所需的各種物資類別(Item
Class)，再利用此物件類別中的Method來處裡遊戲中所需的物資。

ArcaltItem是由靜態Method所組成，沒有Constructor，也沒有Property，程式設計師可以直接使用這些Function。

### Method

**一般玩家**

static void GetItemInstance(ArcaletGame *game*,OnCallCompletionWithData *cb*,
object *token*)

*game* 登入的遊戲

>   取得玩家在該遊戲所擁有的物品，又稱為物品實例(instance)。

>   cb(*code*,*obj,token*)的*obj*的型別為List\<Hashtable\>，List的每一元素即為玩家所擁的物品之instance，以Hashtable記錄該物品的資料，共有四個Key:

>   "iguid" 該物品的iguid

>   "name" 該物品的名稱

>   "id" 該物品instance的id

>   "now" 目前伺服器的系統時間，格式為 yyyy/mm/dd hh:mm:ss

>   "expire" 該物品實例的到期時間，格式為 yyyy/mm/dd hh:mm:ss

>   "attr" 屬性。屬性資料為 key =
>   value，其中key是在開發者後台設定物品類別時就已經指定好了，value除了定義時的預設值外，其值是可以改變的。

>   由於屬性可以不只一個，因此此處也是以List\<Hashtable\>來記錄，List的元素型別為Hashtable，當中有三個Key:

>   "name" 屬性名稱，也就是key。

>   "value" 屬性值

>   "stamp" 寫入此屬性值的時間

>   如果這個物品沒有設定屬性，則 Hashtable[“attr”] = null

void cb(int *code,* object *obj*, object *token*)

*code* 0 設定成功

非0 設定失敗

>   以下範例可將List\<Hashtable\>中的元素一個一個取出:

>   private void ShowList(List\<Hashtable\> list,int deep)

>   {

>   DictionaryEntry dentry;

>   foreach (Hashtable node in list) {

>   IDictionaryEnumerator denum = node.GetEnumerator();

>   if (denum!=null) {

>   while (denum.MoveNext()) {

>   dentry = (DictionaryEntry)denum.Current;

>   if (dentry.Value != null &&  
>   dentry.Value.GetType() == typeof(List\<Hashtable\>)) {

>   ShowList((List\<Hashtable\>)dentry.Value, deep+1);

>   }

>   else {

>   // to process dentry.Key and dentry.Value here

>   }

>   }

>   }

>   }

>   }

static void GetItemInstance(ArcaletGame *game*,string *iguid*,  
OnCallCompletionWithData *cb*, object *token*)

*game* 登入的遊戲

*iguid* 指定要取得的物品的iguid

>   取得玩家在該遊戲所擁有的*特定iguid之物品*，又稱為物品實例(instance)。

>   cb(*code*,*obj,token*)的*obj*的型別為List\<Hashtable\>，List的每一元素即為玩家所擁的物品之instance，以Hashtable記錄該物品的資料，共有四個Key:

>   "iguid" 該物品的iguid

>   "name" 該物品的名稱

>   "id" 該物品instance的id

>   "now" 目前伺服器的系統時間，格式為 yyyy/mm/dd hh:mm:ss

>   "expire" 該物品實例的到期時間，格式為 yyyy/mm/dd hh:mm:ss

>   "attr" 屬性。屬性資料為 key =
>   value，其中key是在開發者後台設定物品類別時就已經指定好了，value除了定義時的預設值外，其值是可以改變的。

>   由於屬性可以不只一個，因此此處也是以List\<Hashtable\>來記錄，List的元素型別為Hashtable，當中有三個Key:

>   "name" 屬性名稱，也就是key。

>   "value" 屬性值

>   "stamp" 寫入此屬性值的時間

>   如果這個物品沒有設定屬性，則 Hashtable[“attr”] = null

void cb(int *code,* object *obj*, object *token*)

*code* 0 設定成功

非0 設定失敗

static void GetItemInstance(ArcaletGame *game*,string *iguid*, bool *autonew*,  
OnCallCompletionWithData *cb*, object *token*)

*game* 登入的遊戲

*iguid* 指定要取得的物品的iguid

*autonew* true: 當玩家沒有此物品的實例(instance)時，則自動新增後傳回。

>   取得玩家在該遊戲所擁有的*特定iguid之物品*，又稱為物品實例(instance)。

>   cb(*code*,*obj,token*)的*obj*的型別為List\<Hashtable\>，List的每一元素即為玩家所擁的物品之instance，以Hashtable記錄該物品的資料，共有四個Key:

>   "iguid" 該物品的iguid

>   "name" 該物品的名稱

>   "id" 該物品instance的id

>   "now" 目前伺服器的系統時間，格式為 yyyy/mm/dd hh:mm:ss

>   "expire" 物品效期，格式為 yyyy/mm/dd
>   hh:mm:ss。物品效期必需在開發者後台的物品管理中設定，如果效期為「永久有效」，則傳回空字串。

>   "attr" 屬性。屬性資料為 key =
>   value，其中key是在開發者後台設定物品類別時就已經指定好了，value除了定義時的預設值外，其值是可以改變的。

>   由於屬性可以不只一個，因此此處也是以List\<Hashtable\>來記錄，List的元素型別為Hashtable，當中有三個Key:

>   "name" 屬性名稱，也就是key。

>   "value" 屬性值

>   "stamp" 寫入此屬性值的時間

>   如果這個物品沒有設定屬性，則 Hashtable[“attr”] = null

void cb(int *code,* object *obj*, object *token*)

*code* 0 設定成功

非0 設定失敗

static void GetItemInstance(ArcaletGame *game*,string[] *iguidArray*,
OnCallCompletionWithData *cb*, object *token*)

*game* 登入的遊戲

*iguidArray* 指定要取得的物品的iguid的字串陣列

>   取得玩家在該遊戲所擁有的*特定iguid之物品*，又稱為物品實例(instance)，此一Overloading傳遞iguid陣列，用來指定多個物品。

>   cb(*code*,*obj,token*)的*obj*的型別為List\<Hashtable\>，List的每一元素即為玩家所擁的物品之instance，以Hashtable記錄該物品的資料，共有四個Key:

>   "iguid" 該物品的iguid

>   "name" 該物品的名稱

>   "id" 該物品instance的id

>   "now" 目前伺服器的系統時間，格式為 yyyy/mm/dd hh:mm:ss

>   "expire" 物品效期，格式為 yyyy/mm/dd
>   hh:mm:ss。物品效期必需在開發者後台的物品管理中設定，如果效期為「永久有效」，則傳回空字串。

>   "attr" 屬性。屬性資料為 key =
>   value，其中key是在開發者後台設定物品類別時就已經指定好了，value除了定義時的預設值外，其值是可以改變的。

>   由於屬性可以不只一個，因此此處也是以List\<Hashtable\>來記錄，List的元素型別為Hashtable，當中有三個Key:

>   "name" 屬性名稱，也就是key。

>   "value" 屬性值

>   "stamp" 寫入此屬性值的時間

>   如果這個物品沒有設定屬性，則 Hashtable[“attr”] = null

void cb(int *code,* object *obj*, object *token*)

*code* 0 設定成功

非0 設定失敗

>   ※請注意：如果參數*iguidArray*陣列中有任何一個iguid是錯誤的，就不會傳回任何錯誤，但是在傳回的List\<Hashtable\>中就不會有此iguid的instance資料。

**static void GetItemInstanceEx(ArcaletGame game, string userid,**  
**OnCallCompletionWithData cb, object token)**

>   **讀取別的玩家的Item
>   Instance，參數iguid必須已在後台設定為公開的Item，其它參數請參考前面GetItemInstance()
>   overloading函式的說明。**

**static void GetItemInstanceEx(ArcaletGame game,string userid, string iguid,**  
**OnCallCompletionWithData cb, object token)**

>   **讀取別的玩家的Item
>   Instance，參數iguid必須已在後台設定為公開的Item，其它參數請參考前面GetItemInstance()
>   overloading函式的說明。**

**static void GetItemInstanceEx(ArcaletGame game, string userid, string iguid,
bool autonew,**  
**OnCallCompletionWithData cb, object token)**

>   **讀取別的玩家的Item
>   Instance，參數iguid必須已在後台設定為公開的Item，其它參數請參考前面GetItemInstance()
>   overloading函式的說明。**

**static void GetItemInstanceEx(ArcaletGame game, string userid, string[]
iguidArray, OnCallCompletionWithData cb, object token)**

>   **讀取別的玩家的Item
>   Instance，參數iguid必須已在後台設定為公開的Item，其它參數請參考前面GetItemInstance()
>   overloading函式的說明。**

static void GetItemClass(ArcaletGame *game*,int *option*,
OnCallCompletionWithData *cb*, object *token*)

*game* 登入的遊戲

*option* 0 只取得在商城中沒有銷售的物品類別**(性質)**  
1 只取得在商城中銷售的物品類別**(商品)**  
2 全部的物品類別(不含對玩家隱藏物品)**(性質+商品)**  
3 對玩家隱藏的物品**(資料)**

>   根據參數*option*的值，取得在開發者後台所定義的物品，又稱為物品類別。

>   cb(*code*,*obj,token*)的*obj*的型別為List\<Hashtable\>，List的每一元素即為開發者所定義的物品，以Hashtable記錄該物品的資料，共有以下Key:

>   "iguid" (string)物品的iguid

>   "name" (string)物品的名稱

>   "desc" (string)物品的描述

>   "type" (int)物品類型，1: 商品，2: 性質，3: 資料

>   "price" (int)價格

>   "image" (string)物品圖片之URL

>   "attr" 屬性。屬性資料為 key = value。

>   由於屬性可以不只一個，因此此處也是以List\<Hashtable\>來記錄，List的元素型別為Hashtable，當中有兩個Key:

>   "name" 屬性名稱，也就是key。

>   "value" 屬性值

>   如果這個物品沒有設定屬性，則 Hashtable[“attr”] = null

void cb(int *code,* object *obj*, object *token*)

*code* 0 設定成功

非0 設定失敗

>   以下範例可將List\<Hashtable\>中的元素一個一個取出:

>   private void ShowList(List\<Hashtable\> list,int deep)

>   {

>   DictionaryEntry dentry;

>   foreach (Hashtable node in list) {

>   IDictionaryEnumerator denum = node.GetEnumerator();

>   if (denum!=null) {

>   while (denum.MoveNext()) {

>   dentry = (DictionaryEntry)denum.Current;

>   if (dentry.Value != null &&  
>   dentry.Value.GetType() == typeof(List\<Hashtable\>)) {

>   ShowList((List\<Hashtable\>)dentry.Value, deep+1);

>   }

>   else {

>   // to process dentry.Key and dentry.Value here

>   }

>   }

>   }

>   }

>   }

static void GetItemClass(ArcaletGame *game*, string *iguid*,  
OnCallCompletionWithData *cb*, object *token*)

*game* 登入的遊戲

*iguid* 物品類別的iguid

>   依據物品的iguid，取得該物品在開發者後台所定義的類別。

>   *cb(code,obj,token)*的obj的型別為List\<Hashtable\>，List的元素即為開發者所定義的物品，由於此函只會傳回一個物品類別，因此傳回的List只會有一個元素；List的元素Hashtable記錄該物品的資料，共有以下Key:

>   "iguid" (string)物品的iguid

>   "name" (string)物品的名稱

>   "desc" (string)物品的描述

>   "type" (int)物品類型，1: 商品，2: 性質，3: 資料

>   "price" (int)價格

>   "image" (string)物品圖片之URL

>   "attr" 屬性。屬性資料為 key = value。

>   由於屬性可以不只一個，因此此處也是以List\<Hashtable\>來記錄，List的元素型別為Hashtable，當中有兩個Key:

>   "name" 屬性名稱，也就是key。

>   "value" 屬性值

>   如果這個物品沒有設定屬性，則 Hashtable[“attr”] = null

void cb(int *code,* object *obj*, object *token*)

*code* 0 設定成功

非0 設定失敗

static void GetItemClass(ArcaletGame *game*, string[] *iguidArray*,  
OnCallCompletionWithData *cb*, object *token*)

*game* 登入的遊戲

*iguidArray* 欲取的的多個物品類別的iguid陣列

>   依據物品的iguid，取得該物品在開發者後台所定義的類別。

>   *cb(code,obj,token)*的obj的型別為List\<Hashtable\>，List的元素即為開發者所定義的物品，由於此函只會傳回一個物品類別，因此傳回的List只會有一個元素；List的元素Hashtable記錄該物品的資料，共有以下Key:

>   "iguid" (string)物品的iguid

>   "name" (string)物品的名稱

>   "desc" (string)物品的描述

>   "type" (int)物品類型，1: 商品，2: 性質，3: 資料

>   "price" (int)價格

>   "image" (string)物品圖片之URL

>   "attr" 屬性。屬性資料為 key = value。

>   由於屬性可以不只一個，因此此處也是以List\<Hashtable\>來記錄，List的元素型別為Hashtable，當中有兩個Key:

>   "name" 屬性名稱，也就是key。

>   "value" 屬性值

>   如果這個物品沒有設定屬性，則 Hashtable[“attr”] = null

void cb(int *code,* object *obj*, object *token*)

*code* 0 設定成功

非0 設定失敗

>   ※請注意：如果參數*iguidArray*陣列中有任何一個iguid是錯誤的，就不會傳回任何錯誤，但是在傳回的List\<Hashtable\>中就不會有此iguid的instance資料。

static void NewItemInstance(ArcaletGame *game*,string *iguid*,  
OnCallCompletionWithData *cb*, object *token*)

*game* 登入的遊戲

*iguid* 物品類別的iguid

>   新增物品instance。

>   當遊戲進行時，玩家因故取得物件，就可以使用此method新增一個物品的實例。

void cb(int *code*, object *id,* object *token*)

*code* 0 新增物品成功

非0 新增物品失敗

>   *id* 當新增物品成功，此處所傳回的*id*為新增的物品實例之instance
>   id，請將此參數改型(cast)為int。

>   請注意:
>   所新增的物品若在管理後台設定為「合併屬性值且不建立新的物品」，則回傳itemid=0

static void SetItemInstanceAttribute(  
ArcaletGame *game*,string *iguid*,int *id*,string[] *attrNameArray*,  
string *attrValueArray*,OnCallCompletion *cb*, object *token*)

*game* 登入的遊戲

*iguid* 物品類別的iguid

*id* 玩家所擁有，且要設定屬性的物品實例之instance id

*attrNameArray* 要設定的屬性名稱

*attrValueArray* 要設定的屬性值

>   設定玩家在遊戲中的物件實例的屬性值。

void cb(int *code*, object *token*)

*code* 0 設定成功

非0 設定失敗

static void SetItemInstanceAttribute(  
ArcaletGame *game*,string *iguid*,int *id*,string *attrName*,  
string[] *attrValue*,OnCallCompletion *cb*, object *token*)

*game* 登入的遊戲

*iguid* 物品類別的iguid

*id* 玩家所擁有，且要設定屬性的物品實例之instance id

*attrName* 要設定的屬性名稱之陣列字串

*attrValue* 要設定的屬性值之陣列字串

>   設定玩家在遊戲中的物件實例的屬性值。

void cb(int *code*, object *token*)

*code* 0 設定成功

非0 設定失敗

static void GetItemInstanceAttribute(  
ArcaletGame *game*,string *iguid*,int *id*,string *attrName*,  
OnCallCompletionWithData *cb*, object *token*)

*game* 登入的遊戲

*iguid* 物品類別的iguid

*id* 玩家所擁有，且要設定屬性的物品實例之instance id

*attrName* 要取值的屬性名稱

>   取得玩家在遊戲中的物件實例的屬性值。

>   cb(*code*,*obj,token*)的*obj*的型別為Hashtable，共有以下Key:

>   "name" 屬性名稱，也就是參數*attrName*

>   "value" 屬性值

>   "stamp" 寫入此屬性值的時間

>   "now" 目前伺服器的系統時間，格式為 yyyy/mm/dd hh:mm:ss

void cb(int *code,* object *obj*, object *token*)

*code* 0 設定成功

非0 設定失敗

static void GetItemInstanceAttribute(  
ArcaletGame *game*,string *iguid*,int *id*,string[] *attrNameArray*,  
OnCallCompletionWithData *cb*, object *token*)

*game* 登入的遊戲

*iguid* 物品類別的iguid

*id* 玩家所擁有，且要設定屬性的物品實例之instance id

*attrNameArray* 要取值的屬性名稱**之陣列**

>   取得玩家在遊戲中的物件實例的屬性值。

>   cb(*code*,*obj,token*)的*obj*的型別為List\<Hashtable\>，，List中的每個Hasthtable元素就是傳回的屬性資料，Hasthtable共有以下Key:

>   "name" 屬性名稱，也就是參數*attrName*

>   "value" 屬性值

>   "stamp" 寫入此屬性值的時間

>   "now" 目前伺服器的系統時間，格式為 yyyy/mm/dd hh:mm:ss

void cb(int *code,* object *obj*, object *token*)

*code* 0 設定成功

非0 設定失敗

>   ※請注意：如果指定的*attrNameArray*陣列中有任何一個屬性名稱是錯誤或不存在的，並不會傳回任何錯誤，但是傳回的List資料中不會有這個錯誤屬性的資料。

static void DeleteItemInstance(ArcaletGame *game*,string *iguid*,int *id*,  
OnCallCompletion *cb*, object *token*)

*game* 登入的遊戲

*iguid* 物品類別的iguid

*id* 玩家擁有的物品實例之instance id

>   刪除物品instance。

void cb(int *code*, object *token*)

*code* 0 設定成功

非0 設定失敗

static void GetMallURL(  
ArcaletGame *game*, int *type*, string *iguid*,  
OnCallCompletionWithData *cb*, object *token*)

*game* 登入的遊戲

*type* web頁面版本，0: 行動版頁面，1: 一般頁面

*iguid* 物品類別的iguid，如果傳空字串，則URL為該遊戲的商城頁面

>   *cb*(*code*, *obj, token*)
>   *obj*的型別為string，傳回遊戲Item商城URL，分為行動版與一般網頁版

void cb(int *code,* object *obj*, object *token*)

*code* 0 設定成功

非0 設定失敗

static void GetItemInstanceNumber(  
ArcaletGame *game*, string *iguid*,  
OnCallCompletionWithData *cb*, object *token*)

*game* 登入的遊戲

*iguid* 物品類別的iguid

>   取得某物品類別已經建立的物品實例個數，透過callback *cb()*的參數*obj*傳回。

>   *cb*(*code*, *obj, token*) *obj*的型別為int，傳回物品實例個數。

void cb(int *code,* object *obj*, object *token*)

*code* 0 設定成功

非0 設定失敗

*obj* 物品實例個數，必須改型(cast)為int。

static void ResetMallItemStatus(  
ArcaletGame *game*, string *iguid*,  
OnCallCompletion *cb*, object *token*)

*game* 登入的遊戲

*iguid* 物品類別的iguid

>   重置指定iguid的商品在商城中的狀態，商品狀態分為三種，正常、隱藏、鎖住，重置後將變成「正常的狀態」

void cb(int *code,* object *token*)

*code* 0 重置成功

非0 重置失敗

static void ChangeMallItemStatus(  
ArcaletGame *game*, string *iguid*, int *status*,  
OnCallCompletion *cb*, object *token*)

*game* 登入的遊戲

*iguid* 物品類別的iguid

*status* 商品狀態。

0: 正常

1: 隱藏

2: 鎖住

>   依照參數*status*的值，改變指定iguid的商品在商城中的狀態。

void cb(int *code,* object *token*)

*code* 0 設定成功

非0 設定失敗

<br>ArcaletSystem
-----------------

### Description

(略)

### Method

static void ResetUserPassword (string *userid*, string *oldpasswd*, string
*newpasswd*,  
string *gguid*, byte[] *gcert*, OnCallCompletion *cb*, object *token*)

*userid* 要修改的玩家帳號

*oldpasswd* 舊的密碼

*newpasswd* 新的密碼

*gguid* 指定的遊戲的GGUID

*gcert* 指定的遊戲的認證碼

>   重設玩家的密碼。

>   玩家必須是該遊戲的玩家，否則無法重設，而且必須傳進舊的密碼才能重設。

  
**超級使用者與特權函式**

>   超級使用者(Super User)又稱特權使用者，這是DP (Distributed
>   Plug-in)登入遊戲所使用的帳號。由於DP擔任遊戲主控者的角色，因此必須賦與存取其它玩家資料的特權，也就是說，此處的特權使用者函式並不是讓目前的登入者存取自己的資料，而是以額外的參數指定某個玩家，然後直接存取該玩家的資料。

>   特權函式只有登入帳號是超級使用者才能呼叫，否則callback將會傳回「無使用權限」錯誤碼。超級使用者函式的功能與參數和一般玩家函式相似，函式名稱以su開頭，如果該特權函式是針對特定玩家的資料進行操作，函式就會有一個額外的參數*userid*，用來指定該特定玩家的帳號。

>   以下是特權函式，只列出函式定義而無詳細說明者，請參考一般使用者函式的說明。

>   **ArcaletGame**

Void suSetPlayerNickname(string *userid*, string *nickname*, OnCallCompletion
*cb*, object *token*)

Void suGetPlayerNickname(string *userid*, OnCallCompletionWithData *cb*,object
*token*)

*userid* 指定玩家userid

>   取得某指定玩家的暱稱。

>   請注意: 此特權函式沒有對應的一般使用者函式

void cb(int *code*, object *obj*, object *token*)

*code* 0 設定成功

非0 設定失敗

*obj* 傳回的暱稱，型別為string。

string nickname=(string)obj;

Void suSetPlayerRegister(string *userid*, object *AX*, object BX, object *CX*,
object *DX*,  
OnCallCompletion *cb*, object *token*)

void suGetPlayerRegister(string *userid*, OnCallCompletionWithData *cb*, object
*token*)

>   **ArcaletItem**

static void suGetItemInstance(ArcaletGame *game*, string *userid*,

OnCallCompletionWithData *cb*, object *token*)

static void suGetItemInstance(ArcaletGame *game*, string *userid*, string
*iguid*,

OnCallCompletionWithData *cb*, object *token*)

static void suGetItemInstance(ArcaletGame *game*, string *userid*, string[]
*iguidArray*,

OnCallCompletionWithData *cb*, object *token*)

static void suGetItemClass(ArcaletGame *game*, string *userid*, int *option*,

OnCallCompletionWithData *cb*, object *token*)

static void suGetItemClass(ArcaletGame *game*, string *userid*, string *iguid*,  
OnCallCompletionWithData *cb*, object *token*)

static void suGetItemClass(ArcaletGame *game*, string *userid*, string[]
*iguidArray*,  
OnCallCompletionWithData *cb*, object *token*)

static void suNewItemInstance(ArcaletGame *game*, string *userid*, string
*iguid*,  
OnCallCompletionWithData *cb*, object *token*)

static void suSetItemInstanceAttribute(ArcaletGame *game*, string *userid*,  
string *iguid*,int *id*, string *attrName*, string *attrValue*,  
OnCallCompletion *cb*, object *token*)

static void suSetItemInstanceAttribute(ArcaletGame *game*, string *userid*,  
string *iguid*,int *id*,string[] *attrNameArray*, string *attrValue*,  
OnCallCompletion *cb*, object *token*)

static void suGetItemInstanceAttribute(ArcaletGame *game*, string *userid*,  
string *iguid*,int *id*,string *attrName*,  
OnCallCompletionWithData *cb*, object *token*)

static void suGetItemInstanceAttribute(ArcaletGame *game*, string *userid*,  
string[] *iguidArray*,int *id*,string *attrName*,  
OnCallCompletionWithData *cb*, object *token*)

static void suDeleteItemInstance(ArcaletGame *game*, string *userid*, string
*iguid*,  
int *id*, OnCallCompletion *cb*, object *token*)

static void suGetItemInstanceNumber(ArcaletGame *game*, string *userid*, string
*iguid*,  
OnCallCompletionWithData *cb*, object *token*)

static void suResetMallItemStatus(ArcaletGame *game*, string *userid*, string
*iguid*,  
OnCallCompletion *cb*, object *token*)

static void suChangeMallItemStatus(ArcaletGame *game*, string *userid*,

string *iguid*, int *status*,  
OnCallCompletion *cb*, object *token*)

static void suSetItemClassAttribute(ArcaletGame *game*, string *iguid*, string
*attrName*, string *attrValue*,

OnCallCompletion *cb*, object *token*)

*game* 登入的遊戲

*iguid* 物品類別的iguid

*attrName* 屬性名稱。

*attrValue* 屬性值。

>   設定物品類別的預設屬性值。物品類別的預設屬性也就是開發者在管理後台所設定的屬性資料，不屬特定用戶所有。

>   請注意: 此特權函式沒有對應的一般使用者函式

void cb(int *code*, object *token*)

*code* 0 設定成功

非0 設定失敗

static void suSetItemClassAttribute(ArcaletGame *game*, string *iguid*, string[]
*attrNameArray*, string[] *attrValueArray*,

OnCallCompletion *cb*, object *token*)

*game* 登入的遊戲

*iguid* 物品類別的iguid

*attrName* 屬性名稱的陣列。

*attrValue* 屬性值的陣列，*attrName*與*attrValue*的元素個數必須相同。

>   設定物品類別的預設屬性值，可一次設定多個屬性資料。物品類別的預設屬性也就是開發者在管理後台所設定的屬性資料，不屬特定用戶所有。

>   請注意: 此特權函式沒有對應的一般使用者函式

void cb(int *code,* object *token*)

*code* 0 設定成功

非0 設定失敗

static void suSetItemClassAttribute(ArcaletGame *game*, string *iguid*, string[]
*attrNameArray*, string[] *attrValueArray*,

OnCallCompletion *cb*, object *token*)

<br>ArcaletScore
----------------

### Description

積分版是用來記錄玩家遊戲分數並產生成績排行榜，arcalet提供的積分排行榜分為日排行、周排行、月排行、歷史排行。日排行的成績每日會重置歸零，新的成績寫入後再重新排行，周排行、月排行則分別在每周與每月重置歸零。至於歷史排行則永不歸零。

使用arcalet的積分版服務，開發者可在arcalet的開發者後台(http://developer.arcalet.com)定義遊戲各種積分版類別(Leader
Board Class)，並取得積分版的GUID(稱為LGUID)，然後在遊戲程式中以arcalet
API的arcaletscore類別之static method來處理遊戲進行中的各種積分版作業。

除了積分版外，arcalet也提供玩家分數記錄服務，開發者可依遊戲的需要，在遊戲程式中記錄與查閱玩家的分數。由於玩家分數記錄只是玩家個人的分數資料庫，與積分版完全無關。不過，開發者若使用積分版的分數登錄API將玩家分數提交到積分版時，系統也會將此玩家的分數寫入到玩家個人的成績記錄中。

### Method

**一般玩家**

static void CommitLeaderBoard(ArcaletGame *game*,  
string *lguid*, int *tag*, string *score*,  
OnCallCompletion *cb*, object *token*)

*game* 登入的遊戲

*lguid* 積分版類別的lguid

*tag* 寫入個人分數記錄時所指定的標籤

*score* 要登錄的分數  
請注意，如果積分版的類型是「計數器」，score參數值將被忽略。

>   (有一個overloading)

>   提交玩家遊戲分數到積分版，同時也記錄到個人的成績記錄，參數*tag*則用來指定的個人分數記錄表的標籤。

void cb(int *code*, object *token*)

*code* 0 設定成功

非0 設定失敗

(CommitLeaderBoard()的另一個overloading)

static void CommitLeaderBoard(ArcaletGame *game*,  
string *lguid*, int *tag*, string *score*, string *note*  
OnCallCompletion *cb*, object *token*)

*note* 要寫入的note字串

static void RecordPlayerScore(ArcaletGame *game*,int *tag*,  
string *score*,OnCallCompletion *cb*, object *token*)

*game* 登入的遊戲

*tag* 成績記錄標籤，可用來區分不同的分數種類

*score* 要登錄的分數

>   記錄玩家個人分數

void cb(int *code*, object *token*)

*code* 0 設定成功

非0 設定失敗

static void GetPlayerScore(ArcaletGame *game*,  
int *tag*, int *orderby*, int *order*,  
string *startDate*,string *endDate*,  
OnCallCompletionWithData *cb*, object *token*)

*game* 登入的遊戲

*tag* 成績記錄標籤，可用來區分不同的分數種類

*orderby* 0: 依照日期排序，1: 依照分數排序

*order* 0: 升冪排序，1: 降冪排序

*startDate* 查詢期間之起始日期，格式為yyyy/mm/dd
hh:mm:ss，若為空字串表示無起始日期。

*endDate* 查詢期間之結束日期，格式為yyyy/mm/dd
hh:mm:ss，若為空字串表示無結束日期。

>   取得玩家的分數，cb(*code*,*obj,token*)的*obj*的型別為List\<Hashtable\>，List的每一元素即為一筆分數記錄，以Hashtable記錄該筆分數記錄，共有三個Key:

>   "tag" 該分數的標籤，一定與傳入的*tag*參數相同

>   "score" 分數

>   "stamp" 登錄此分數的時間，格式為yyyy/mm/dd hh:mm:ss

>   如果玩家分數是以CommitLeaderBoard()記錄，而該項積分版類型為「計數器」時，在此取得的玩家的分數在Hashtable中的Key將會是:

>   "tag" 該分數的標籤，一定與傳入的*tag*參數相同

>   "daily" 目前的「日」計數值(如果積分板項目有勾選要記錄此值的話才會出現)

>   "weekly" 目前的「周」計數值(如果積分板項目有勾選要記錄此值的話才會出現)

>   "monthly" 目前的「月」計數值(如果積分板項目有勾選要記錄此值的話才會出現)

>   "all" 目前的「總」計數值(如果積分板項目有勾選要記錄此值的話才會出現)

>   "stamp" 登錄此分數的時間，格式為yyyy/mm/dd hh:mm:ss

void cb(int *code,* object *obj*, object *token*)

*code* 0 設定成功

非0 設定失敗

static void GetPlayerScore(ArcaletGame *game*,  
int *tag*, int *orderby*, int *order*,  
string *startDate*,string *endDate*,  
OnCallCompletionWithData *cb*, object *token*,int *Num*)

>   GetPlayerScore()的另一個overloading，多了一個參數*Num*，代表只要讀取*Num*筆分數的資料。

static void GetLeaderBoard(ArcaletGame *game*, string *lguid*, int *type*, int
*ex*,  
OnCallCompletionWithData *cb*, object *token*)

*game* 登入的遊戲

*lguid* 積分版類別的lguid

*type* 0: 總排行，1: 日排行，2: 周排行，3: 月排行

*ex* 0: 目前排行

非0: 歷史排行，表示取得多久前的排行，例如:

*ex*=2、*type*=3，表示要取得三個月前的月排行

*ex*=1、*type*=2，表示要取得兩周前的周排行

>   (有兩個overloading)

>   取得積分版的排行資料，cb(*code*,*obj,token*)的*obj*的型別為List\<Hashtable\>，List的每一元素即為一筆分數記錄，以Hashtable記錄該筆分數計錄，共有三個Key:

>   "userid" 登錄此分數的玩家帳號

>   "score" 分數

>   "nickname" 登錄此分數的玩家暱稱 (2013.9.2 1.6.13新增)

>   "note" 此分數的備註資料，也就是在CommitLeaderBoard()時的「*Note*」參數值。

>   "stamp" 登錄此分數的時間，格式為yyyy/mm/dd hh:mm:ss

>   "now" Server的系統時間

void cb(int *code,* object *obj*, object *token*)

*code* 0 設定成功

非0 設定失敗

static void GetLeaderBoard(ArcaletGame *game*, string *lguid*, int *type*, int
*ex*,  
OnCallCompletionWithData *cb*, object *token*,int *Num*)

>   與前一個GetLeaderBoard()函數一樣，但多了參數*Num*，代表只要讀取*Num*筆分數的資料。

static void GetLeaderBoard(ArcaletGame *game*, string *lguid*, int *type*, int
*orderby*,  
int *ex*, OnCallCompletionWithData *cb*, object *token*)

*game* 登入的遊戲

*lguid* 積分版類別的lguid

*type* 0: 全部排行，1: 日排行，2: 周排行，3: 月排行

*ex* 0: 目前排行

非0: 歷史排行，表示取得多久前的排行，例如:

*ex*=2、*type*=3，表示要取得三個月前的月排行

*ex*=1、*type*=2，表示要取得兩周前的周排行

*orderby* 0: 依分數及根據後台設定的方式排序  
1: 根據寫入時間排序(降序，最近的時間排前面)  
2: 根據寫入時間排序(升序，最久的時間排前面)

>   (有兩個overloading)

>   取得積分版的排行榜，cb(*code*,*obj,token*)的*obj*的型別為List\<Hashtable\>，List的每一元素即為一筆分數記錄，以Hashtable記錄該筆分數計錄，共有三個Key:

>   "userid" 登錄此分數的玩家

>   "score" 分數

>   "nickname" 登錄此分數的玩家暱稱 (2013.9.2 1.6.13新增)

>   "note" 此分數的備註資料，也就是在CommitLeaderBoard()時的「*Note*」參數值。

>   "stamp" 登錄此分數的時間，格式為yyyy/mm/dd hh:mm:ss

void cb(int *code,* object *obj*, object *token*)

*code* 0 設定成功

非0 設定失敗

static void GetLeaderBoard(ArcaletGame *game*, string *lguid*, int *type*, int
*orderby*,  
int *ex*, OnCallCompletionWithData *cb*, object *token*,int *Num*)

>   與前一個GetLeaderBoard()函數一樣，但多了參數*Num*，代表只要讀取*Num*筆分數的資料。

static void GetPlayerRank(ArcaletGame *game*, string *lguid*, int *type*,  
OnCallCompletionWithData *cb*, object *token*)

*game* 登入的遊戲

*lguid* 積分版類別的lguid

*type* 0: 全部排行，1: 日排行，2: 周排行，3: 月排行

>   取得玩家在積分版中的名次

void cb(int *code,* object *obj*, object *token*)

*code* 0 設定成功

非0 設定失敗

>   *obj*
>   改型為int後，存放玩家在積分版中的名次，若名次為-1，表示此玩家在積分版中沒有排進名次內。

**static void GetPlayerRank(ArcaletGame game, string lguid, int type, int
forward, int backward,**  
**int orderby, int ex,**  
**OnCallCompletionWithData cb, object token)**

>   **game 登入的遊戲**

>   **lguid 積分版類別的lguid**

>   **type 0: 全部排行，1: 日排行，2: 周排行，3: 月排行**

>   **forward 目前玩家最佳排行名次再往前幾名**

>   **backward 目前玩家最佳排行名次再往後幾名**

>   *orderby* 0: 依分數及根據後台設定的方式排序  
>   1: 根據寫入時間排序(降序，最近的時間排前面)  
>   2: 根據寫入時間排序(升序，最久的時間排前面)

>   *ex* 0: 目前排行

非0: 歷史排行，表示取得多久前的排行，例如:

*ex*=2、*type*=3，表示要取得三個月前的月排行

*ex*=1、*type*=2，表示要取得兩周前的周排行

>   **取得玩家在積分版中的名次以外，也傳回往前forward名以及往後backward的玩家名次、userid與暱稱。**

**void cb(int code, object obj, object token)**

**code 0 設定成功**

**非0 設定失敗**

>   **obj Hashtable，其中**

>   **obj[“rank”] 型別為int，記錄玩家的排行名次**

>   **obj[“leaderboard”]
>   型別為List\<Hashtable\>，記錄玩家前後幾名的玩家資料，每個玩家佔List中的一個元素，從
>   obj[“leaderboard”][0] 開始，最多會有forward + backward +1個玩家資料。**

>   **obj[“leaderboard”][n][“rank”] 排行名次**

>   **obj[“leaderboard”][n][“userid”] 該名次的玩家userid**

>   **obj[“leaderboard”][n][“nickname”] 該名次的玩家nickname**

>   **obj[“leaderboard”][n][“score”] 該名次的玩家積分版分數**

>   **obj[“leaderboard”][n][“note”]
>   該名次的玩家在**此分數的備註資料，也就是在CommitLeaderBoard()時的「*Note*」參數值。

>   **obj[“leaderboard”][n][“stamp”]
>   該名次的玩家登錄此分數的時間，格式為yyyy/mm/dd hh:mm:ss**

>   **obj[“leaderboard”][n][“now”] Server的系統時間**

h["score"] = reader.GetAttribute("score");

h["note"] = reader.GetAttribute("note");

h["stamp"] = reader.GetAttribute("time");

>   h["now"] = systime;

**超級使用者與特權函式**

static void suCommitLeaderBoard(ArcaletGame *game*, string *userid,*  
string *lguid*, int *tag*, string *score*,  
OnCallCompletion *cb*, object *token*)

static void suCommitLeaderBoard(ArcaletGame *game*, string *userid,*  
string *lguid*, int *tag*, string *score*, string *note*,  
OnCallCompletion *cb*, object *token*)

static void suRecordPlayerScore(ArcaletGame *game*,string *userid*, int
*tag*,string *score*,  
OnCallCompletion *cb*, object *token*)

static void suGetPlayerScore(ArcaletGame *game*,string *userid*,  
int *tag*, int *orderby*, int *order*,  
string *startDate*,string *endDate*,  
OnCallCompletionWithData *cb*, object *token*)

static void suGetPlayerScore(ArcaletGame *game*,string *userid*,  
int *tag*, int *orderby*, int *order*,  
string *startDate*,string *endDate*,  
OnCallCompletionWithData *cb*, object *token*,int *Num*)

static void suGetLeaderBoard(ArcaletGame *game*, string *userid*, string
*lguid*, int *type*,  
OnCallCompletionWithData *cb*, object *token*)

static void suGetLeaderBoard(ArcaletGame *game*, string *userid*, string
*lguid*, int *type*,  
OnCallCompletionWithData *cb*, object *token*,int *Num*)

static void suGetLeaderBoard(ArcaletGame *game*, string *userid*, string
*lguid*, int *type*,

int *orderby*, OnCallCompletionWithData *cb*, object *token*)

static void suGetLeaderBoard(ArcaletGame *game*, string *userid*, string
*lguid*, int *type*,

int *orderby*, OnCallCompletionWithData *cb*,

object *token*,int *Num*)

static void suGetPlayerRank(ArcaletGame *game*, string *userid*, string *lguid*,
int *type*,  
OnCallCompletionWithData *cb*, object *token*)

**static void suGetPlayerRank(ArcaletGame game, string userid, string lguid, int
type,**  
**int forward, int backward,**  
**OnCallCompletionWithData cb, object token)**

ArcaletShop
-----------

### Description

### Method

static void CommitInAppPurchase(ArcaletGame *game*, string *iguid*, int *type*,  
string *receipt*, OnCallCompletion *cb*, object *token*)

*game* 登入的遊戲

*iguid* 所購買物品的iguid

*type* 0: 測試購買(Sandbox)  
1: 實際購買

*receipt* 從App-Store中傳回的交易收據資料(receipt-data)

>   驗證完成後將會呼叫callback函式*cb*，*cb*的定義如下：

void cb(int *code,* object *obj*, object *token*)

*code* 0 設定成功

非0 設定失敗

static void CommitInAppBilling(ArcaletGame *game*, string *iguid*, int *type*,  
string *receipt,* string *signature*,  
OnCallCompletion *cb*, object *token*)

*game* 登入的遊戲

*iguid* 所購買物品的iguid

*type* 0: 測試購買(Sandbox)  
1: 實際購買

*receipt* 從Google Play商店傳回的交易收據資料(receipt-data)

*signature* 收據之電子簽章資料(Base64編碼)

>   驗證完成後將會呼叫callback函式*cb*，*cb*的定義如下：

void cb(int *code,* object *obj*, object *token*)

*code* 0 設定成功

非0 設定失敗

ArcaletSystem
-------------

### Description

### Method

static void ApplyNewUser(string *gguid*, byte[] *gamecode*,  
string *userid*,string *passwd*,string *email*,  
OnCallCompletion *cb*,object *token*)

*gguid* 遊戲的GGUID。

*gamecode* 遊戲驗證碼。

*userid*
所申請的玩家帳號，請注意帳號長度必須介於3到10個字元，而且只能是英數字，符號只能是「-」和「.」。

*passwd* 帳號的密碼，長度限制6到18字元。

*email* 帳號的e-mail信箱，用來驗證身份。

*cb* 完成API後的callback函式，其函式定義如下：

void cb(int code, object token)

>   **code 0 表帳號升級成功**

>   **非0 帳號升級失敗，code為錯誤碼**

*token* 和callback函式傳遞相依資料的物件。

>   這個函式讓使用者在應用程式內直接申請玩家帳號，不必將使用者導向arcalet網站的帳號申請頁面。

static void ApplyNewUser(string *gguid*,byte[] *gamecode*,  
OnCallCompletionWithData *cb*,object *token*)

*gguid* 遊戲的GGUID。

*gamecode* 遊戲驗證碼。

*cb* 完成API後的callback函式，其函式定義如下：

void cb(int code, object data, object token)

data必需改型為Hashtable，內有兩個Key，分別是：

1. userid 系統所建立的帳號

2. passwd 系統所建立的帳號之登入密碼(遊戲密碼)

*token* 和callback函式傳遞相依資料的物件。

>   這個函式讓使用者在應用程式內直接向arcalet伺服器請求玩家帳號，由系統產生帳號密碼後傳回，開發者必須將此帳號存在遊戲用戶端之儲存設備裡(例如Sandbox)，此帳號又稱為「系統取得帳號」或「Level
>   0帳號」，若玩家半年內未再以此帳號登入遊戲，帳號將被刪除。

>   「系統取得帳號」可以透過UpgradeUser()將帳號升級為「玩家正式帳號」，正式帳號是由玩家自定帳號、密碼、e-mail，等同於使用**ApplyNewUser()**的另一個overloading註冊正式帳號。

static void UpgradeUser(ArcaletGame *game*, string *userid*,string
*passwd*,string *email*, OnCallCompletion *cb*, object *token*)

*game* ArcaletGame物件，必須以「系統取得之帳號」登入才能呼叫此method。

*userid*
所申請的玩家帳號，請注意帳號長度必須介於3到10個字元，而且只能是英數字，符號只能是「-」和「.」。

*passwd* 帳號的密碼，長度限制6到18字元。

*email* 帳號的e-mail信箱，用來驗證身份。

*cb* 完成API後的callback函式，其函式定義如下：

void cb(int code, object token)

code 0 表帳號升級成功

非0 帳號升級失敗，code為錯誤碼

*token* 和callback函式傳遞相依資料的物件。

(1.7.005新增以下Method)

static bool SetSceneMaxThreads(int *workerThreads*)

*workerThreads* 設定ArcaletScene背景處理程式所使用的執行緒池之最大執行緒數。

>   這個函式是讓DP開發者依其遊戲特性與玩家規模進行優化調整，一般來說開發者並不需要特別調整。請注意，執行緒越多並不代表效能越好，如果數值調得太高，而TTL值(詳見**SetSceneThreadTTL**)過低，可能會造成大量的執行緒生成與消滅，DP的穩定度將會降低。

static bool SetSceneMinThreads(int *workerThreads*)

*workerThreads* 設定ArcaletScene背景處理程式所使用的執行緒池之最小執行緒數。

>   這個函式是讓DP開發者依其遊戲特性與玩家規模進行優化調整，一般來說開發者並不需要特別調整。

static bool SetSceneThreadTTL(int *workerSeconds*)

*workerSeconds*
設定ArcaletScene背景處理程式所使用的執行緒池之閒置執行緒之最長存活秒數，執行緒閒置超過這個秒數就會從執行緒池中移除。

>   這個函式是讓DP開發者依其遊戲特性與玩家規模進行優化調整，一般來說開發者並不需要特別調整。另外，請勿將此數值調得太低，否則將會造成大量的執行緒生成與消滅，進而影響DP的穩定度。

static bool SetDatabaseMaxThreads(int *workerThreads*)

*workerThreads*
設定ArcaletItem、ArcaletScore、ArcaletShop、ArcaletSystem等與資料庫處理有關的API其使用的執行緒池之最大執行緒數。

>   這個函式是讓DP開發者依其遊戲特性與玩家規模進行優化調整，一般來說開發者並不需要特別調整。請注意，執行緒越多並不代表效能越好，如果數值調得太高，而TTL值(詳見**SetDatabaseThreadTTL**)過低，可能會造成大量的執行緒生成與消滅，DP的穩定度將會降低。

static bool SetDatabaseMinThreads(int *workerThreads*)

*workerThreads*
設定ArcaletItem、ArcaletScore、ArcaletShop、ArcaletSystem等與資料庫處理有關的API其使用的執行緒池之最小執行緒數。

>   這個函式是讓DP開發者依其遊戲特性與玩家規模進行優化調整，一般來說開發者並不需要特別調整。

static bool SetDatabaseThreadTTL(int *workerSeconds*)

*workerSeconds*
設定ArcaletItem、ArcaletScore、ArcaletShop、ArcaletSystem等與資料庫處理有關的API其使用的執行緒池之閒置執行緒之最長存活秒數，執行緒閒置超過這個秒數就會從執行緒池中移除。

>   這個函式是讓DP開發者依其遊戲特性與玩家規模進行優化調整，一般來說開發者並不需要特別調整。另外，請勿將此數值調得太低，否則將會造成大量的執行緒生成與消滅，進而影響DP的穩定度。

static string ServerTimeOfLastApiCall()

>   某些API函式在與伺服器通訊時會取得Arcalet服務的系統時間，可透過這個函式取出時間值，格式為
>   yyyy/mm/dd hh:mm:ss ，時區為UTC標準時間。

static void UnityEnvironment()

>   在Unity3D的開發環境中，請在程式一開始時呼叫此函式。實務上，若不呼叫此函式，在某些平台，例如Android手機上將出現不可預期的錯誤。

>   此函式只須呼叫一次即可，但若多次呼叫也不會有不好的影響，不過第一次呼叫必須在new
>   ArcaletGame()之前。

(1.7.005新增ArcaletThreadPool)

ArcaletThreadPool 
------------------

### Description

這是相較於.Net
Framework效能更高、更穩定的執行緒池系統。當背景工作時程較短，且在短時間有大量的背景工作需求時，ArcaletThreadPool不會有大量執行緒物件的生成與消滅，避免DP長時間工作之後，系統進入Garbage
Collection時，對於新執行緒的生成產生嚴重的延遲，如果背景工作對於即時性的要求較高時，這樣的延遲就會對服務產生極大的影響。

### Method

static void QueueUserWorkItem(WaitCallback *callback*, object *state*)

*callback* 要執行的工作之Method名稱

*state* 要執行的工作之參數

>   此Method的使用與.Net Framework之**QueueUserWorkItem()**完全相容。

static void QueueUserWorkItem(WaitCallback *callback*)

*callback* 要執行的工作之Method名稱

>   此Method的使用與.Net Framework之**QueueUserWorkItem()**完全相容。

static int GetAvailableThreads()

>   取得目前執行緒池中可用的執行緒數量，也就是最大執行緒數減去使用中的執行緒數。此Method的使用與.Net
>   Framework之**QueueUserWorkItem()**完全相容。

static int GetQueuedUserWorkItems()

>   取得目前執行緒池中，尚在等待可用執行緒的工作數量。

static int GetWorkerThreads()

>   取得目前執行緒池中，正在執行工作的執行緒數量。

static int GetSuspendedThreads()

>   取得目前執行緒池中的閒置執行緒數量。

static bool SetMaxThreads(int *workerThreads*)

*workerThreads* 設定執行緒池之最大執行緒數。

>   這個函式是讓DP開發者依其遊戲特性與玩家規模進行優化調整，一般來說開發者並不需要特別調整。請注意，執行緒越多並不代表效能越好，如果數值調得太高，而TTL值(詳見SetThreadTTL)過低，可能會造成大量的執行緒生成與消滅，DP的穩定度將會降低。

static bool SetMinThreads(int *workerThreads*)

*workerThreads* 設定執行緒池之最小執行緒數。

>   這個函式是讓DP開發者依其遊戲特性與玩家規模進行優化調整，一般來說開發者並不需要特別調整。

static bool SetThreadTTL(int *workerSeconds*)

*workerSeconds*
設定執行緒池之閒置執行緒之最長存活秒數，執行緒閒置超過這個秒數就會從執行緒池中移除。

>   這個函式是讓DP開發者依其遊戲特性與玩家規模進行優化調整，一般來說開發者並不需要特別調整。另外，請勿將此數值調得太低，否則將會造成大量的執行緒生成與消滅，進而影響DP的穩定度。

<br>ArcaletGuild
----------------

### Description

公會是用來建立與管理公會，包括公會成員、公會基本資料等

公會成員資料中會有四個int屬性暫存器，分別是R1,R2,R3,R4，這四個暫存器在取得公會成員時，可以指定做為排序的依據，開發者除了可以使用SetPlayerGuildRegister()設定暫存器外，也可在ArcaletItem.SetItemInstanceAttribute()設定Item實例的屬性資料時，指定暫存器代號，同步設定Item屬性資料和Rx暫存器。

### Method

**(建立公會)**

static void CreateGuild(ArcaletGame *game*, string *name*, string *note*,

int *maxmember*, int *permission*, int *tag*,  
int *G1*, int *G2*, int *G3*, int *G4*,

OnCallCompletionWithData *cb*, object *token*)

*name* 公會名稱，系統對名稱無限制，開發者依自己的需要，自行過濾限制的名稱。

*note* 公會描述

*maxmember* 公會最大可加入的會員數(最大值為50)

*permission* 0: 任何人都可以加入公會  
1: 公會管理員或super user才有權限決定加玩家進入公會。

2: 任何人都無法加入。

*tag* 公會標籤

*G1～G4*
公會暫存器，用來存放開發者自定的整數資料(例如，公會等級、公會獎盃等），在呼叫GetGuild()等讀取公會列表函式時，用來指定排序方式。

>   此函式用來建立公會，呼叫者就是公會的會長，呼叫後透過的callback 傳回資料:

void cb(int *code,* object *obj*, object *token*)

*code* 0 成功

非0 失敗

*obj* 當*code*=0時，(int) *obj*存放公會的識別碼

當*code*非0時，(int) *obj*為錯誤碼

請注意，如果開發者在遊戲管理後台設定「一般user」沒有建立公會的權限，則呼叫此函式將會失敗，開發者必須改用suCreateGuild()，透過DP伺服器邏輯程式來建立公會。

static void suCreateGuild(ArcaletGame *game*, string *userid*, string *name*,
string *note*,

int *maxmember*, int *permission*, int *tag*,

int *G1*, int *G2*, int *G3*, int *G4*,

OnCallCompletionWithData *cb*, object *token*)

*userid* 指定*userid*做為公會會長

*name* 公會名稱，系統對名稱無限制，開發者依自己的需要，自行過濾限制的名稱。

*note* 公會描述

*maxmember* 公會最大可加入的會員數(最大值為50)

*permission* 0: 任何人都可以加入公會  
1: 公會管理員或super user才有權限決定加玩家進入公會。

2: 任何人都無法加入。

*tag* 公會標籤

*G1～G4*
公會暫存器，用來存放開發者自定的整數資料，在GetGuild()呼叫時，可以指定排序方式。

由Super User呼叫，指定*userid*為公會會長，建立公會。Callback
cb請參考CreateGuild()。

當開發者在遊戲管裡後台設定此遊戲的「一般使用者」沒有建立公會的權限時，程式設計師必需改用suCreateGuild()在DP中建立公會。

**(刪除公會)**

static void DeleteGuild(ArcaletGame *game*, int *guildid*,

OnCallCompletion *cb*, object *token*)

*guildid* 刪除的公會之識別碼

此函式由公會會長呼叫，只能用來刪除已經存在的公會。刪除後，callback
cb傳回以下參數:

void cb(int *code,* object *token*)

*code* 0 刪除成功

非0 刪除失敗，*code*為錯誤碼

呼叫此函式若無刪除公會的權限，callback cb()將傳進非0的參數*code*。

static void suDeleteGuild(ArcaletGame *game*, int *guildid*,

OnCallCompletion *cb*, object *token*)

*guildid* 刪除的公會之識別碼

此函式由super user呼叫，用來刪除已經存在的公會。刪除後，callback cb傳回以下參數:

void cb(int *code,* object *token*)

*code* 0 刪除成功

非0 刪除失敗，*code*為錯誤碼

呼叫此函式若無刪除公會的權限，callback cb()將傳進非0的參數*code*。

**(加入公會)**

static void JoinGuild(ArcaletGame *game*, int *guildid*, OnCallCompletion *cb*,
object token)

*guildid* 要加入的公會之識別碼

此函式讓呼叫者加入已經存在的公會， callback cb傳回以下參數:

void cb(int *code,* object *token*)

*code* 0 加入公會成功

非0 加入公會失敗，*code*為錯誤碼

權限說明:
呼叫者是一般玩家(非公會會長也不是管理員)，所加入的公會必須在當初建立時，指定*permission*為0，表示任何人都可以加入。

**請注意：**公會會員在加入公會時，每個會員都有四個暫存器，分別是R1, R2, R3,
R4，可用來存放整數資料，開發者可以自行定義其用途，例入會員等級、生命值等，未來在取得公會成員時，R1\~R4可用來做為過濾的條件。此外，R1\~R4暫存器除了可以使用SetPlayerGuildRegister()寫入暫存器值外，另外在ArcaletItem.SetItemInstanceAttribute()，同時寫入屬性資料時與Rx暫存器，詳情請參考ArcaletItem.SetItemInstanceAttribute()。

>   static void JoinGuild(ArcaletGame *game*, string *userid*, int *guildid*,  
>   OnCallCompletion *cb*, object token)

*guildid* 要加入的公會之識別碼

*userid* 要加入公會的玩家之userid

此函式的呼叫必須是公會會長或管理員，將參數*userid*所指定的玩家加入公會。

Callback請參考前一個overloading。

static void suJoinGuild(ArcaletGame *game*, string *userid*, int *guildid*,

OnCallCompletion *cb*, object *token*)

*guildid* 要加入的公會之識別碼

*userid* 要加入公會的玩家之userid

此函式由Super User呼叫，將參數*userid*所指定的玩家加入公會。

Callback請參考前一個overloading。

**(退出公會)**

static void LeaveGuild(ArcaletGame *game*, OnCallCompletion *cb*, object token)

此函式讓呼叫者退出已加入公會， callback cb傳回以下參數:

void cb(int *code,* object *token*)

*code* 0 成功退出公會

非0 失敗，*code*為錯誤碼

權限說明: 呼叫者是一般玩家(非公會會長也不是管理員)

>   static void LeaveGuild(ArcaletGame *game*, string *userid*,  
>   OnCallCompletion *cb*, object token)

*userid* 要退出公會的玩家之userid

此函式的呼叫必須是公會會長或管理員，將參數userid所指定的玩家退出公會，如果*userid*所指定的玩家並沒有加入呼叫者所管理的公會，cb將會回傳錯誤。

Callback請參考前一個overloading。

static void suLeaveGuild(ArcaletGame *game*, string *userid*,

OnCallCompletion *cb*, object *token*)

*userid* 要退出公會的玩家之userid

此函式由Super User呼叫，將參數*userid*所指定的玩家退出他已加入的公會。

Callback請參考前一個overloading。

**(修改公會屬性資料)**

static void UpdateGuild(ArcaletGame *game*, string *name*, string *note*,  
object *maxnumber*, object *permission*, object *tag*,  
object *G1*, object *G2*, object *G3*, object *G4*,  
OnCallCompletionWithData *cb*, object *token*)

*name* 公會名稱，系統對名稱無限制，開發者依自己的需要，自行過濾限制的名稱。

*note* 公會描述。

*maxmember* 公會最大可加入的會員數，必須為整數

*permission* 0: 任何人都可以加入公會  
1: 公會管理員或super user才有權限決定加玩家進入公會。

2: 任何人都無法加入。

*tag* 公會標籤，必須為整數

*G1～G4*
公會暫存器，用來存放開發者自定的整數資料，在GetGuild()呼叫時，可以指定排序方式。

(以上參數若設為null，表示不修改該項屬性資料)

此函式用來修改公會的屬性資料，呼叫必須是公會會長或管理員，否則將會發生權限錯誤，callback
cb會回傳所屬公會的識別碼(Guild ID)

void cb(int *code,* object *obj*, object *token*)

*code* 0 成功

非0 失敗

*obj* 當*code*=0時，(int) *obj*存放公會的識別碼

當*code*非0時，(int) *obj*為錯誤碼

static void suUpdateGuild(ArcaletGame *game*, int *guildid*, string *name*,
string *note*,  
object *maxnumber*, object *permission*, object *tag*,

object *G1*, object *G2*, object *G3*, object *G4*, OnCallCompletionWithData
*cb*, object *token*)

>   *guildid* 公會識別碼。

(其它參數說明詳見UpdateGuild())

此函式用來修改公會的屬性資料，呼叫必須Super
User，以參數*guildid*指定要修改資料的公會之識別碼(Guild ID)，呼叫後，callback
cb會傳回一樣的公會識別碼，cb參數請參考UpdateGuild()。

**(讀取公會列表)**

讀取公會目錄總共分為四大類的函式，每個函式都有多個Overloading，在查閱函式prototype前我們將它們整理如下表，以方便瞭解它們的功能：

|                      | 依照條件     | 排序方法   | 過濾條件(二擇一或兩者都有) |                     |              |
|----------------------|--------------|------------|----------------------------|---------------------|--------------|
|                      | 參數         | 說明       |                            | 暫存器條件運算式    | 公會建立時間 |
| GetGuild             | \-           | 無         | *sortby*                   | *RegisterCondition* | *Start, End* |
| GetGuildByName       | *name*       | 公會名     | *sortby*                   | *RegisterCondition* | *Start, End* |
| GetGuildByPermission | *permission* | 公會類型   | *sortby*                   | *RegisterCondition* | *Start, End* |
| GetGuildByTag        | *tag*        | 公會標籤   | *sortby*                   | *RegisterCondition* | *Start, End* |
| GetGuildByUserid     | *userid*     | 玩家userid | 無                         | 無                  | 無           |

呼叫參數說明:

>   *orderby*
>   呼叫後，傳回公會列表時的排序方式，此參數用字串表示，可以指定用暫存器值、公會建立時間來排序，由於公會暫存器總共有4個(其所代表的意義是由開發者依照其遊戲的需要來定義，詳情請參考CreateGuild()的說明)。  
>   此參數字串中，可用的Keyword有以下數種，另外可加後綴asc或desc表示升序或降序，沒有指定的話，則預設為asc
>   :

| g1         | 依G1暫存器值排序 |
|------------|------------------|
| g2         | 依G2暫存器值排序 |
| g3         | 依G3暫存器值排序 |
| g4         | 依G4暫存器值排序 |
| createtime | 依公會建立時間   |

例如: ”g1 desc”

如果一次要指定多個排序條件，則請用「，」分隔，  
例如: ”g1 asc,g3 desc,createtime desc”

*MaxNumber* 指定讀取資料筆數上限。  
**請注意，GetGuildByName()是依參數name做名稱的關鍵字搜尋，名稱完全符合的會排在第一筆，所以如果只要取得名稱完全符合公會，請設MaxNumber
= 1**。

*RegisterCondition*
指定暫存器條件，傳回符合條件的公會列表，條件式是以「\>」、「\<」、「=」、「&」、「\|」和g1,
g2, g3, g4, now-g1stamp, now-g2stamp, now-g3stamp,
now-g4stamp組成的運算式字串，例如:  
”((g1 \> 3 & g1\< 5) \| (g3 = 3)) & (now-g1stamp\>86400)”

(在不同overloading，此參數不一定提供，如不提供，表示不過濾暫存器條件)

*Start* 列出公會建立時間晚於此時間者

(在不同overloading，此參數不一定提供，如不提供或傳null值，則無開始時間)

*End* 列出公會建立時間早於此時間者

(在不同overloading，此參數不一定提供，如不提供或傳null值，則無結束時間)

*cb*
callback函式，取得的公會資料由此傳回，放在*data*參數中，型別為List\<Hashtable\>，List的每個元素就是一個公會的資料，用Hashtable存放，以下是公會Hastable資料的Key與資料欄位說明：

| Key          | 資料欄位說明                                                                                                                                                      |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| guildid      | 公會識別碼                                                                                                                                                        |
| name         | 公會名稱                                                                                                                                                          |
| note         | 公會描述                                                                                                                                                          |
| leader       | 公會會長的nickname                                                                                                                                                |
| maxnumber    | 公會可加入的最大會員(玩家)數                                                                                                                                      |
| playernumber | 目前公會已加入的會員(玩家)總數                                                                                                                                    |
| tag          | 公會標籤                                                                                                                                                          |
| permission   | 公會類型                                                                                                                                                          |
|              | 0: 任何人都可加入                                                                                                                                                 |
|              | 1: 只有會長或管理員核准才能加入                                                                                                                                   |
|              | 2: 任何人都無法加入。                                                                                                                                             |
| g1           | 暫存器G1，開發者自定屬性                                                                                                                                          |
| g2           | 暫存器G2，開發者自定屬性                                                                                                                                          |
| g3           | 暫存器G3，開發者自定屬性                                                                                                                                          |
| g4           | 暫存器G4，開發者自定屬性                                                                                                                                          |
| g1stamp      | 上次更改G1暫存器的時間                                                                                                                                            |
| g2stamp      | 上次更改G2暫存器的時間                                                                                                                                            |
| g3stamp      | 上次更改G3暫存器的時間                                                                                                                                            |
| g4stamp      | 上次更改G4暫存器的時間                                                                                                                                            |
| createtime   | 公會建立的時間                                                                                                                                                    |
| applystate   | 呼叫者申請加入此公會的申請單狀態 0: 未申請or無資料 (由於申請單不會永久保留，刪掉後就會呈現無資料的狀態) 1: 公會管理員審核中 2: 已接受加入公會 3: 已被拒絕加入公會 |

Callback的參數*code*為0，表示成功取得公會資料，非零則為錯誤碼。請注意，若找不到符合條件的公會，參數*code*
仍舊為0，但傳回的List大小為0。

所有函式:

public static void GetGuild(ArcaletGame *game*, string *orderby*, int
*maxnumber*,  
OnCallCompletionWithData *cb*, object *token*)

public static void GetGuild(ArcaletGame *game*, string *orderby*, int
*maxnumber*,  
DateTime *Start*, DateTime *End*,  
OnCallCompletionWithData *cb*, object *token*)

public static void GetGuild(ArcaletGame *game*, string *orderby*, int
*maxnumber*,  
string RegisterCondition,  
OnCallCompletionWithData *cb*, object *token*)

public static void GetGuild(ArcaletGame *game*, string *orderby*, int
*maxnumber*,  
string RegisterCondition, DateTime *Start*, DateTime *End*,  
OnCallCompletionWithData *cb*, object *token*)

public static void GetGuildByName(ArcaletGame *game*, string *Name*, string
*orderby*, int *maxnumber*, OnCallCompletionWithData *cb*, object *token*)

public static void GetGuildByName(ArcaletGame *game*, string *Name*, string
*orderby*, int *maxnumber*,  
DateTime *Start*, DateTime *End*,  
OnCallCompletionWithData *cb*, object *token*)

public static void GetGuildByName(ArcaletGame *game*, string *Name*, string
*orderby*, int *maxnumber*,  
string *RegisterCondition*,  
OnCallCompletionWithData *cb*, object *token*)

public static void GetGuildByName(ArcaletGame *game*, string *Name*, string
*orderby*, int *maxnumber*,  
string RegisterCondition, DateTime *Start*, DateTime *End*,  
OnCallCompletionWithData *cb*, object *token*)

public static void GetGuildByPermission(ArcaletGame *game*, int *permission*,
string *orderby*,  
int *maxnumber*,  
OnCallCompletionWithData *cb*, object *token*)

public static void GetGuildByPermission(ArcaletGame *game*, int *permission*,
string *orderby*,  
int *maxnumber*, DateTime *Start*, DateTime *End*,  
OnCallCompletionWithData *cb*, object *token*)

public static void GetGuildByPermission(ArcaletGame *game*, int *permission*,
string *orderby*,  
int *maxnumber*, string *RegisterCondition*,  
OnCallCompletionWithData *cb*, object *token*)

public static void GetGuildByPermission(ArcaletGame *game*, int *permission*,
string *orderby*,  
int *maxnumber*, string *RegisterCondition*, DateTime *Start*, DateTime *End*,  
OnCallCompletionWithData *cb*, object *token*)

public static void GetGuildByTag(ArcaletGame *game*, int *tag*, string
*orderby*, int *maxnumber*,  
OnCallCompletionWithData *cb*, object *token*)

public static void GetGuildByTag(ArcaletGame *game*, int *tag*, string
*orderby*, int *maxnumber*,  
DateTime *Start*, DateTime End,  
OnCallCompletionWithData *cb*, object *token*)

public static void GetGuildByTag(ArcaletGame *game*, int *tag*, string
*orderby*,  
int *maxnumber*, string *RegisterCondition*,  
OnCallCompletionWithData *cb*, object *token*)

public static void GetGuildByTag(ArcaletGame *game*, int *tag*, string
*orderby*, int *maxnumber*,  
string *RegisterCondition*, DateTime *Start*, DateTime *End*,  
OnCallCompletionWithData *cb*, object *token*)

**(讀取公會成員)**

讀取公會成員函式有多個Overloading，以下是函式參數說明：

呼叫參數說明:

>   *guildid*
>   指定要讀取的公會之識別碼，如果沒有指定，就傳回呼叫此函式的玩家所加入的公會。

>   *orderby*
>   呼叫後，傳回公會成員列表時的排序方式，此參數用字串表示，可以指定用暫存器值、加入公會時間來排序，由於公會暫存器總共有4個(其所代表的意義是由開發者依照其遊戲的需要來定義，詳情請參考JoinGuild()的說明)。  
>   此參數字串中，可用的Keyword有以下數種，另外可加後綴asc或desc表示升序或降序，沒有指定的話，則預設為asc
>   :

| r1       | 依R1暫存器值排序 |
|----------|------------------|
| r2       | 依R2暫存器值排序 |
| r3       | 依R3暫存器值排序 |
| r4       | 依R4暫存器值排序 |
| jointime | 依加入公會的時間 |

例如: ”r1 desc”

如果一次要指定多個排序條件，則請用「，」分隔，  
例如: ”r1 asc,r3 desc, jointime desc”

*RegiterCondition*
指定暫存器條件，傳回符合條件的公會成員列表，條件式是以「\>」、「\<」、「=」、「&」、「\|」和r1,
r2, r3, r4, now-r1stamp, now-r2stamp, now-r3stamp,
now-44stamp組成的運算式字串，例如:  
”((r1 \> 3 & r1\< 5) \| (r3 = 3)) & (now-r1stamp\>86400) ”

(在不同overloading，此參數不一定提供，如不提供，表示不過濾暫存器條件)

*Start* 列出加入公會時間晚於此時間的成員(開始時間)

(在不同overloading，此參數不一定提供，如不提供或傳null值，則無開始時間)

*End* 列出加入公會時間早於此時間的成員(結束時間)

(在不同overloading，此參數不一定提供，如不提供或傳null值，則無結束時間)

*cb*
callback函式，取得的公會資料由此傳回，放在*data*參數中，型別為List\<Hashtable\>，List的每個元素就是一個公會的資料，用Hashtable存放，以下是公會Hastable的Key與資料欄位說明：

| Key       | 資料欄位說明                                                         |
|-----------|----------------------------------------------------------------------|
| guildid   | 公會識別碼                                                           |
| userid    | 玩家的userid                                                         |
| nickname  | 玩家的暱稱                                                           |
| online    | 0:玩家不再線上，非零:玩家在目前在線上之poid                          |
| privilege | 成員在此公會的權限，0: 一般會員，1:(特權會員)管理員 2:(特權會員)會長 |
| r1        | 暫存器R1，開發者自定屬性                                             |
| r2        | 暫存器R2，開發者自定屬性                                             |
| r3        | 暫存器R3，開發者自定屬性                                             |
| r4        | 暫存器R4，開發者自定屬性                                             |
| r1stamp   | 上次更改R1暫存器的時間                                               |
| r2stamp   | 上次更改R2暫存器的時間                                               |
| r3stamp   | 上次更改R3暫存器的時間                                               |
| r4stamp   | 上次更改R4暫存器的時間                                               |
| jointime  | 加入公會的時間                                                       |

Callback的參數*code*為0，表示成功取得公會資料，非零則為錯誤碼。請注意，若找不到符合條件的公會，參數*code*
仍舊為0，但傳回的List大小為0。

所有函式:

static void GetGuildMember(ArcaletGame game, int guildid, string orderby,  
OnCallCompletionWithData cb, object token)

static void GetGuildMember(ArcaletGame game, string orderby,  
OnCallCompletionWithData cb, object token)

static void GetGuildMember(ArcaletGame game, int guildid, string orderby,  
DateTime Start, DateTime End,  
OnCallCompletionWithData cb, object token)

static void GetGuildMember(ArcaletGame game, string orderby,  
DateTime Start, DateTime End,  
OnCallCompletionWithData cb, object token)

static void GetGuildMember(ArcaletGame game, int guildid, string orderby,  
string RegisterCondition,  
OnCallCompletionWithData cb, object token)

static void GetGuildMember(ArcaletGame game, string orderby,  
string RegisterCondition,  
OnCallCompletionWithData cb, object token)

static void GetGuildMember(ArcaletGame game, int guildid, string orderby,  
string RegisterCondition, DateTime Start, DateTime End,  
OnCallCompletionWithData cb, object token)

static void GetGuildMember(ArcaletGame game, string orderby,  
string RegisterCondition, DateTime Start, DateTime End,  
OnCallCompletionWithData cb, object token)

**(設定或解除公會管理員)**

static void SetGuildManager(ArcaletGame *game*, string *userid*, bool
*ismanager,*

OnCallCompletion *cb*, object *token*)

*userid* 要設定或解除公會管理員資格的userid

*ismanager* true: 設定為公會管理員

false: 解除公會管理員資格

此函式由公會會長呼叫，只能用來設定或解除某玩家在此公會中的管理員資格，callback
cb傳回以下參數:

void cb(int *code,* object *token*)

*code* 0 成功

非0 失敗，*code*為錯誤碼

呼叫此函式時，若無權限，callback cb()將傳進非0的參數*code*。

static void suSetGuildManager(ArcaletGame *game*, int *guildid*, string
*userid*, bool *ismanager,*

OnCallCompletion *cb*, object *token*)

*guildid* 公會識別碼

*userid* 要設定或解除公會管理員資格的userid

*ismanager* true: 設定為公會管理員

false: 解除公會管理員資格

此函式由super
user呼叫，並由參數guildid指定公會，用來設定或解除某玩家在此公會中的管理員資格，callback
cb傳回以下參數:

void cb(int *code,* object *token*)

*code* 0 成功

非0 失敗，*code*為錯誤碼

**(設定玩家的公會暫存器)**

static void SetPlayerGuildRegister(ArcaletGame *game*,  
object *R1,* object *R2,* object *R3,* object *R2*,

OnCallCompletion *cb*, object *token*)

*R1\~R4* 要設定的暫存器，必須是整數，若不設定，則傳null

設定呼叫者自己的公會暫存器，參數*R1*\~*R4*對應公會系統的R1\~R4玩家暫存器，如果不要設定某暫存器，則將對應的參數傳入null即可。

**請注意，若玩家可以自行設定自己的公會暫存器，則必須在管理後台將權限打開，否則只能透過Super
User，在DP中設定。**

呼叫後， callback *cb*傳回以下參數:

void cb(int *code,* object *token*)

*code* 0 成功

非0 失敗，*code*為錯誤碼

static void SetPlayerGuildRegister(ArcaletGame *game*, string *userid*,  
object *R1,* object *R2,* object *R3,* object *R2*,

OnCallCompletion *cb*, object *token*)

*userid* 要設定暫存器的玩家userid

*R1\~R4* 要設定的暫存器，必須是整數，若不設定，則傳null

由公會會長或管理員呼叫，指定要設定的會員之公會暫存器，會員由參數*userid*指定，且必須是會員的userid，否則將傳回權限錯誤。參數*R1*\~*R4*對應公會系統的R1\~R4玩家暫存器，如果不要設某暫存器，則將對應的參數傳入null即可。

**請注意，若公會會長或管理員可以自行設定會員的公會暫存器，則必須在管理後台將權限打開，否則只能透過Super
User，在DP中設定。**

呼叫後， callback *cb*傳回以下參數:

void cb(int *code,* object *token*)

*code* 0 成功

非0 失敗，*code*為錯誤碼

static void suSetPlayerGuildRegister(ArcaletGame *game*, string *userid*,  
object *R1,* object *R2,* object *R3,* object *R2*,

OnCallCompletion *cb*, object *token*)

*userid* 要設定暫存器的玩家userid

*R1\~R4* 要設定的暫存器，必須是整數，若不設定，則傳null

由Super
User呼叫，指定要設定玩家之公會暫存器，玩家由參數*userid*指定。參數*R1*\~*R4*對應公會系統的玩家R1\~R4暫存器，如果不要設定某暫存器，則將對應的參數傳入null即可。

**請注意，若公會會長或管理員可以自行設定會員的公會暫存器，則必須在管理後台將權限打開，否則只能透過Super
User，在DP中設定。**

呼叫後， callback *cb*傳回以下參數:

void cb(int *code,* object *token*)

*code* 0 成功

非0 失敗，*code*為錯誤碼

**(玩家申請加入公會)**

static void ApplyJoinGuild(ArcaletGame *game*, int *guildid*, OnCallCompletion
*cb*, object *token*)

*guildid* 申請要加入的公會之識別碼

這個函式由一般玩家呼叫，向公會的管理員提出加入公會的要求，也就是提交申請單給公會會長與管理員的意思，之後公會管理員必須以ListApplyJoinGuild()讀取申請單，再來決定是否同意或拒絕。

呼叫後， callback *cb*傳回以下參數:

void cb(int *code,* object *token*)

>   *code* 0 提交成功。請注意:
>   這只是提交成功，並不是申請成功。真正申請成功必須由公會管理員核准後才算數。

非0 失敗，*code*為錯誤碼

**(讀取申請加入公會的申請單)**

static void GetApplyJoinGuild(ArcaletGame *game*, \_ApplyType\_ *state*,  
OnCallCompletionWithData *cb*, object *token*)

*state* 要列出的申請單的狀態，_ApplyType_總共有四種:  
enum \_ApplyType\_ { pending=1 , approve = 2, reject = 3, all =0 }  
pending: 待處理，approve: 已核准，reject: 已拒絕，all: 全部

*cb* callback函式:

>   void cb(int *code,* object *data*, object *token*)

>   *code* 0 核准成功。

>   非0 失敗，*code*為錯誤碼

>   *data*
>   取得申請單資料由此傳回，放在*data*參數中，型別為List\<Hashtable\>，List的每個元素就是一個玩家的申請單，用Hashtable存放，以下是Hastable的Key與資料欄位說明：

| Key       | 資料欄位說明                           | Type   |
|-----------|----------------------------------------|--------|
| applyid   | 申請單識別碼                           | int    |
| nickname  | 申請者玩家暱稱                         | string |
| state     | 申請單狀態 1: 待審，2:已核准，3:已拒絕 | int    |
| applytime | 提交申請的時間                         | string |
| timetodel | 預計刪除申請單的時間                   | string |

這個函式只能由公會會長或管理員呼叫，通常是指定參數*state*為pending，讀取等待處理的申請單。如果會會長或管理員想要列出過去已核准過、或是已拒絕過的、或是全部，則*state*可以傳入其它三個參數。

**(處理加入公會申請)**

有兩個函式用來處理加入公會的申請，一個用於核准，另一個用於拒絕。

一、核准

static void ApproveJoinGuild(ArcaletGame *game*, int *applyid*, int
*KeepRecordDays*, OnCallCompletion *cb*, object t*o*ken)

*applyid* 申請單的識別碼

*KeepRecordDays* 處理過後，此申請單要留存的天數。  
請注意:

1.  由於申請單也會佔用開發者所擁有的資料存放額度，所以若指定較長的留存的天數，就會佔用較大的存放空間。

2.  留存的天數可以設為0，處理後就會立即刪除。

呼叫後， callback cb傳回以下參數:

void cb(int *code,* object *token*)

>   *code* 0 核准成功。

非0 失敗，*code*為錯誤碼  
10213: 已處理過，重複處理

二、拒絕

static voidRejectJoinGuild(ArcaletGame *game*, int *applyid*, int
*KeepRecordDays*, OnCallCompletion *cb*, object t*o*ken)

*applyid* 申請單的識別碼

*KeepRecordDays* 處理過後，此申請單要留存的天數。  
請注意:

1.  由於申請單也會佔用開發者所擁有的資料存放額度，所以若指定較長的留存的天數，就會佔用較大的存放空間。

2.  留存的天數可以設為0，處理後就會立即刪除。

3.  **一旦申請單被刪除，被拒絕的玩家就可以再次提出申請，所以申請單要留存的天數不要設定太小。**

呼叫後， callback cb傳回以下參數:

void cb(int *code,* object *token*)

>   *code* 0 拒絕成功。

非0 失敗，*code*為錯誤碼

10213: 已處理過，重複處理

<br>ArcaletMailbox
------------------

信箱信息用來發送離線信息給其它玩家，所發送的信息將會存放在雲端儲存，並佔用遊戲的儲存額度，如果開發者想要節省空間，可以把信息下載後存放在玩家本機設備的儲存體裡，然後把已讀的信息刪除，爾後玩家遊戲程式起動後，若要列出信息，就先讀取本機端的已讀信息，再讀取ArcaletMailbox的信息，讀後再存放在本機後刪除，直到沒有此玩家的信息為止。

### Method

**(寄送信箱信息)**

void SendMail(ArcaletGame *game*,string *touserid*, int *tag*, string *text*,
bool *hasSentBackup*, OnCallCompletionWithData *cb*, object *token*)

>   *touserid* 收信人的user id

>   *tag* 信件標籤，將來讀取郵件列表時可用來做為過濾條件

>   *text* 信件內容，只能是純文字，長度最大1K個字元

>   *hasSentBackup* true:
>   寄送信息後，寄信人也會有一份寄信備份，寄信備份的mailid將在callback
>   *cb*的參數*data*傳回來。

此函式用來*寄送信息給玩家*，玩家以參數*touserid*指定，寄送後callback
cb傳回以下參數:

void cb(int *code,* object *data*, object *token*)

*code* 0 成功

1 失敗

*data* 成功時，若呼叫市有指定要寄信備份，則寄信備份mailid為(int)*data*  
失敗時，錯誤碼為 (int)*data*

void SendMail(ArcaletGame *game*,int *guildid*, \_Whom\_ *whom*, int *tag*,
string *text*, bool *hasSentBackup*, OnCallCompletionWithData *cb*, object
*token*)

>   *guildid* 公會的識別碼，將信息寄給此公會成員

>   *whom* 指定要寄給公會的那些人，其值為enum \_Whom\_ {all=1, manager=2,
>   leader=3}  
>   all: 寄給公會的所有會員  
>   manager: 寄給公會的管理員  
>   leader: 寄給公會的會長

>   *tag* 信件標籤，將來讀取郵件列表時可用來做為過濾條件

>   *text* 信件內容，只能是純文字，長度最大1K個字元

>   *hasSentBackup* true:
>   寄送信息後，寄信人也會有一份寄信備份，寄信備份的mailid將在callback
>   *cb*的參數*data*傳回來。

此函式用來*寄送信息給某公會的所有會員*，公會識別碼以參數*guildid*指定，寄送後callback
cb傳回以下參數:

void cb(int *code,* object *data*, object *token*)

*code* 0 成功

非0 失敗

*data* 成功時，若呼叫時有指定要寄信備份，則寄信備份mailid為(int)*data*  
失敗時，錯誤碼為 (int)*data*

**(讀取信箱信息)**

讀取信箱信息有五個overloading，依照以下參數別而有不同的讀取方式:

>   *mailid* 指定mailid，直接讀取該信息

>   *folder* 指定folder(信匣)，共有三個enum值:  
>   enum \_Folder\_ {sent=1, inbox=2, both=3 };  
>   代表sent:寄信備份匣、inbox:收信匣、both:兩者

>   *tag* 指定tag(標籤)，由開發者自行定義。

>   *start, end* 指定開始與結束時間，讀取這兩個時間之內寄送的信息

>   *datetime, direction* 指定時間與方向，讀取此時間之前或之後寄送的信息  
>   *direction*兩個值，共有兩個enum值:  
>   enum \_Direction\_ {before = 1, after = 2 }  
>   分別代表刪除之前與之後的訊息

>   讀取的郵件透過callback的參數*cb*傳回，在*code*=0表示成功時，讀到的郵件列表資料放在參數*data*中，型別為List\<Hashtable\>，Hashtable的Key與資料欄位說明：

| Key          | 資料欄位說明                                                                                                                                                                                            |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| mailid       | 信息識別碼mailid                                                                                                                                                                                        |
| text         | 信息本文                                                                                                                                                                                                |
| folder       | 信息所在的信匣，1: 寄信備份，2:收信匣                                                                                                                                                                   |
| touserid     | 當folder=2 (收信匣)，則為收信人的userid                                                                                                                                                                 |
|              | 當folder=1 (寄信備份)，有兩種可能，以前導字元「\#」之有無來區別:                                                                                                                                        |
|              | 1.\#guildid: 收信人是公會成員，其值為公會的識別碼 2.userid: 收信人是個人，其值為收信人的userid                                                                                                          |
| tonickname   | 當folder=2 (收信匣)，則為收信人的userid                                                                                                                                                                 |
|              | 當folder=1 (寄信備份)，有兩種可能，以前導字元「\#」之有無來區別:                                                                                                                                        |
|              | 1.\#guildname: 收信人是公會成員，其值為公會的識別碼 2.userid: 收信人是個人，其值為收信人的userid                                                                                                        |
| fromuserid   | 寄信人的userid                                                                                                                                                                                          |
| fromnickname | 寄信人的暱稱                                                                                                                                                                                            |
| senddate     | 寄信時間                                                                                                                                                                                                |
| tag          | 標籤                                                                                                                                                                                                    |

如果發生錯誤，callback cb的參數*code*為非零，參數*data*則傳回錯誤碼。

所有overloading函式定義如下:

void ListMail(ArcaletGame *game*, int *mailid*, OnCallCompletionWithData *cb*,
object *token*)

void ListMail(ArcaletGame *game*, \_Folder\_ *folder*, OnCallCompletionWithData
*cb*, object *token*)

void ListMail(ArcaletGame *game*, \_Folder\_ *folder*, int *tag*,  
OnCallCompletionWithData *cb*, object *token*)

void ListMail(ArcaletGame *game*, \_Folder\_ *folder*, DateTime *start*,
DateTime *end*,  
OnCallCompletionWithData *cb*, object *token*)

void ListMail(ArcaletGame *game*, \_Folder\_ *folder*, int *tag*, DateTime
*start*, DateTime *end*,  
OnCallCompletionWithData *cb*, object *token*)

void ListMail(ArcaletGame *game*, \_Folder\_ *folder,* int *tag*,  
DateTime *datetime*, \_Direction\_ *direction*,  
OnCallCompletionWithData *cb*, object *token*)

**(刪除信箱信息)**

讀取信箱信息有三個overloading，依照以下參數別而有不同的讀取方式:

>   *mailid* 指定mailid，直接刪除該信息

>   *folder* 指定要刪除的folder(信匣)，共有三個enum值，分別是  
>   \_Folder\_ {sent=1, inbox=2, both=3}，  
>   代表要刪1:寄信備份匣、2:收信匣、3:兩者

>   *before* 指定時間，刪除此時間之前的信息。

>   刪除信息後，如果發生錯誤，callback
>   cb的參數*code*傳回非零的錯誤碼；若成功，則參數*code*=0。

所有overloading函式定義如下:

void DeleteMail(ArcaletGame *game*, int *mailid*, OnCallCompletion *cb*, object
*token*)

void DeleteMail(ArcaletGame *game*, \_Folder\_ *folder*, OnCallCompletion *cb*,
object *token*)

void DeleteMail(ArcaletGame *game*, \_Folder\_ *folder*, DateTime *before*,  
OnCallCompletion *cb*, object *token*)

**(設定信息標籤)**

void SetMailTag(ArcaletGame *game*, int *mailid*, int *tag*, OnCallCompletion
*cb*, object *token*)

>   *mailid* 指定mailid，要設定標籤的信息

>   *tag* 要設定標籤值

指定信息的mailid ，用來設定其標籤值。設定完成後，callback cb傳回以下參數:

void cb(int *code,* object *token*)

*code* 0 成功

非零 失敗的錯誤碼
