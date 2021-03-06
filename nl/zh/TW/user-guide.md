---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

此文件適用於 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。若要查看舊版 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 的文件，[請按一下此鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/docs/services/knowledge-studio/user-guide.html){: new_window}。
{: tip}

# 註釋文件
{: #user-guide}

本節中的資訊可協助已被要求註釋產業文件的主題專家，使用基準編輯器來完成作業。
{: shortdesc}

## 工作區存取
{: #wks_access_for_annotator}

除非其他人建立工作區，並讓您存取該工作區，否則您看不到任何工作區。

管理者將您新增至 {{site.data.keyword.knowledgestudioshort}} 的實例時，會將您新增至註釋人員角色。您無法使用該角色來建立工作區。若要存取工作區，管理者必須建立工作區。然後，管理者或管理者建立其與工作區關聯的專案經理必須執行下列步驟：

1. 建立註釋集，並建立您與其的關聯。
1. 建立可指派給您的作業，以註釋此集合中的文件。

直到將註釋作業指派給您之後，您才能查看工作區。

如果您受邀參與 {{site.data.keyword.knowledgestudioshort}} 工作區，但看不到「工作區」頁面中的任何工作區，請聯絡邀請您的人員，並要求她執行必要步驟。

## 註釋最佳作法
{: #wks_anno_bp}

這些註釋最佳作法會在您開始註釋文件時提供一些指引及範例。

- 完整註釋所有文件。

    不只是從註釋的內容中學習，「機器學習」也會從負面範例中學習（未註釋的內容）。因此，除執行完整工作，更要明智地註釋內容。如果您仔細註釋一組 10 個文件中的前 5 個文件，則您未在後 5 個文件中擷取的註釋會教導模型，忽略那些文件中遺漏的任何實體或關係提及項目。您可以藉由對前 5 個文件執行徹底工作，來扭轉任何您所做的增益。

- 一致註釋至少與正確註釋一樣重要。

    有關註釋準則的部分決策是任意做出的，例如是否應該將汽車裁切線視為模型名稱的一部分，例如 *Camry* 或 *Camry LX*。選擇哪些原則，其重要性遠低於專案團隊同意某個或另一個原則，並根據該原則進行一致的註釋。

- 僅標示單字記號界限上的實體提及項目，因為提及項目偵測搜尋會根據精度的單字記號層次運作。
- 盡可能標示限制為一或兩個相鄰單字的實體提及項目。

    這樣做不一定可行或容易。請考量下列範例：
    - 來源文件包含一個句子，基於將使用類型系統之應用程式的目的，我們想要從中註釋問題及其原因。

        ```
        The electronic module was burnt because the wrong voltage was applied.
        ```
        {: screen}

        有人可能試圖註釋問題及原因，如下所示：

        ```
                    [PROBLEM][CAUSE]
        ```
        {: screen}

        ```
        [The electronic module was burnt][because the wrong voltage was applied].
        ```
        {: screen}

        不過，將這類冗長的詞組作為實體類型進行註釋，這不是良好作法。而是，尋找重要性的實體，並藉由定義關係提及項目來識別它們彼此的關聯方式。

        ```
               [LOCATION][SYMPTOM]                [CAUSE]
        ```
        {: screen}

        ```
        The [electronic module] was [burnt] because the [wrong voltage] was applied.
        ```
        {: screen}

        ```
                      ^---isStatusOf--| |------causedBy-------^
        ```
        {: screen}

    - 來源文件包含您要註釋的分割動詞。如何將非連續文字作為單一實體類型進行註釋？您可以註釋每一個實體提及項目，並使用關係提及項目，將它們識別為彼此相關。

        ```
                  [EVENT_ANSWER][EVENT_ANSWER]
        ```
        {: screen}

        ```
        All of the phones were ringing, but he knew he should [pick] the red phone [up] first.
        ```
        {: screen}

        ```
                            ^----splitType-----^
        ```
        {: screen}

- 避免重疊提及項目，這是兩種不同的實體類型標籤，其會套用至文件中的單一詞組。例如，假設句子 *She donated her father's journals to the JFK Library.*，如果您對單一詞組 *JFK Library* 註釋 `JFK`=`PERSON` 及 `JFK Library`=`LOCATION`，則您將重疊提及項目。詞彙的使用更涉及圖書館，而不是此句子中的人員，因此只應套用後者的註釋。

    解碼此類結構需要多個機器學習模型的平行呼叫，因為提及項目偵測只會尋找單一標籤，或在每一個單字記號上沒有任何標籤。

- 決定團隊將如何處理執行中文字中的清單及複數。例如，KLUE 類型系統具有 `PERSON` 及 `PEOPLE` 實體類型，可識別單數與複數。您可以選擇使用下列其中一種方式，註釋清單 *Barack, Michelle, Malia, and Sasha Obama*：

    - 將清單中的每一個項目註釋為一個單數實體提及項目（*Barack*、*Michelle*、*Malia* 及 *Sasha Obama*，每一個都是 `PERSON` 提及項目）
    - 將整個詞組註釋為一個複數實體提及項目（*Barack, Michelle, Malia, and Sasha Obama* 是單一 `PEOPLE` 提及項目）。

    沒有哪一種方式一定比另一種方法更好。只要確定您的團隊選擇其中一種，並一致地套用至文件中出現的所有清單。

- 當提及項目參照相同的實際實體時，會使用互相參照。會在不同實體之間使用關係。因此，不應該藉由互相參照及關係來連接兩個提及項目。

## 使用基準編輯器進行註釋
{: #wks_hagte}

當註釋人員註釋文件時，文件會在*基準編輯器* 中開啟。基準編輯器是一種視覺化工具，註釋人員用來將標籤套用至文字。

人工註釋的目標是標示提及項目、關係及互相參照的提及項目，以便可以訓練機器學習模型，以在未看到的文字中偵測這些型樣。至少，使用此工具來註釋實體提及項目。如果將使用所產生模型的應用程式不需要尋找及擷取互相參照及關係提及項目，則您不需要註釋互相參照及關係提及項目。

詞語索引是一種選用工具，註釋人員可以用來加快重複提及項目的註釋。

選擇手動註釋文件時要使用的模式：

- **提及項目**模式

    在此模式中，註釋人員會建立類型系統中定義的實體類型與文字中有意義的單字或詞組的關聯。例如，人員名稱的所有提及項目可能與名為 PERSON 的實體類型相關聯。提及項目的註釋是必要註釋，且必須出現，然後您才能將關係類型及提及項目註釋為互相參照。

    註釋人員可以選擇性地使用詞語索引工具，以確保在整個文件中以及各註釋集間使用相同的實體類型註釋相同的文字。

- **關係**模式

    在此模式中，註釋人員會連接提及項目，方法為與類型系統中定義的關係類型產生關聯。例如，提及項目 `John Smith` 可能會藉由關係類型 `employedBy` 連接至提及項目 `{{site.data.keyword.IBM_notm}}`。關係類型的註釋是選用註釋，且可在您將提及項目註釋為互相參照之前或之後出現。

- **互相參照**模式

    在此模式中，註釋人員會識別表示相同事物的提及項目，因此當字組不相同時，有助於確保註釋中的一致性。例如，在第一句中 `{{site.data.keyword.IBM_notm}}` 的提及項目、`International Business Machines` 的提及項目，以及稍後句子中 `{{site.data.keyword.IBM_notm}}` 的提及項目都參照相同的事物，而且全部將由相同的實體類型（例如 `ORGANIZATION`) 加以標示。提及項目的註釋是選用註釋，且可在您註釋關係類型之前或之後出現。

### 使用編輯器的提示
{: #wks_hagte_tips}

- 進行時儲存您的工作。
- 如果犯錯，您可以按 Ctrl+Z 來復原前一個動作。若要在復原動作之後重做該動作，請按 Ctrl+Y。您可以復原在編輯現行文件時所執行的前 10 個動作。一關閉文件之後，即會失去這些動作。這些動作必須以相反順序來復原，且您必須切換至您執行動作來復原它時所處的模式。您無法復原及重做詞語索引工具動作。

## 註釋實體提及項目
{: #wks_haentity}

若要註釋實體提及項目，註釋人員會在文件中選取字串，然後套用最能適當說明字串所代表意義的標籤。可以套用的標籤是工作區類型系統中定義的實體類型。

### 關於本作業
{: #wks_haentity_about}

開始在文件中註釋實體提及項目之前，最好先閱讀整份文件。這麼做有助於在註釋時記住整個上下文，並且可以協助您深入瞭解實體提及項目如何彼此相關，以及哪些提及項目未來可能需要透過文件互相參照。

當您開啟文件來註釋它時，您可能想要使用詞語索引工具，先註釋重複實體提及項目，然後再註釋個別的實體提及項目。接著，您可以用您喜歡的任何順序來註釋關係提及項目和互相參照，或根本不註釋。實體提及項目註釋是必要的。您是否也要註釋關係提及項目及互相參照，視您的模型目的及領域需求而定。不過，除非您識別了互相參照，否則會將每一個實體提及項目視為代表不同的實體。

#### 提示
{: #wks_haentity_tips}

- 請記住，簡短的實體提及項目對訓練而言更好，因為機器學習模型可以更輕鬆地辨識簡短的型樣，並新增正確的註釋記號。
- 如果您選擇使用字典型記號器與工作區搭配，且想要處理訓練資料中的複合詞彙及標點，則可以將詞彙新增至字典，並建立字典註釋程式來預先註釋出現項目。例如，若要避免句子界限因包括標點符號的詞彙而中斷，請將 Yahoo! 及 Dr. 這類詞彙新增至字典。同樣地，如果您的訓練資料包括加連號字詞或英數字首語（如 `Hi-C` 或 `MS-60-70`），請將那些詞彙新增至字典。若不論大小寫的情況都要註釋出現項目，請新增小寫詞彙（例如 `hi-c`）。若要註釋變異，請將變異新增為表面形式（`MS-60-70` 及 `MS 60 70`）。

   **重要事項**：如果您是使用預設記號器，請不要使用此方法。

### 程序
{: #wks_haentity_procedure}

若要在文件中註釋實體提及項目，請執行下列動作：

1. 以註釋人員身分（或以獲指派要註釋之文件的管理者身分）登入。即會顯示包含已指派給您之作業的工作區。
1. 開啟工作區，然後按一下**機器學習模型** > **註釋作業**。即會顯示已指派給您的註釋作業。
1. 開啟您要使用的註釋作業。即會顯示已指派給您的註釋集。
1. 按一下**註釋**來開啟您要使用的註釋集。即會顯示註釋集中的文件。
1. 開啟您要註釋的文件。依預設，文件會在**提及項目**模式下開啟，此模式是您用來註釋提及項目的模式。
1. 開始註釋實體提及項目。

    1. 按一下文字中的單字，您將其辨識為來自類型系統之特定實體類型的提及項目。對於由多個單字組成的實體提及項目，按一下另一個單字或拖曳選取框邊緣，以選取多個單字或複合字。
    1. 從右側窗格中選取您要套用的實體類型，或輸入實體類型的鍵盤快速鍵。

        如果註釋準則先前已連接至工作區，且您需要協助來選擇要套用的正確註釋，請按一下**檢視準則**。視管理準則的網站所設定的存取權而定，您可能可以在開啟這些準則（例如，若要新增說明及範例）之後予以更新。
        {: tip}

    1. 避免建立重疊的提及項目。但是，如果需要有效的重疊提及項目，請按一下**取代**以更輕鬆地新增它。將多個標籤套用至實體提及項目時，會發生重疊。請檢閱以下建議：

        - 將 *Sub-Saharan* 註釋為單一提及項目，不只是 *Saharan* 或只是 *Sub*。
        - 請不要對 *JFK International Airport* 中的 *JFK* 參照建立重疊的 `PERSON` 註釋。整個 *JFK International Airport* 提及項目應該僅標示為 `FACILITY`。
        - 對於文字 *CEOs*，請不要對 *CEO* 建立 `PERSON` 註釋，也不要對 *CEOs* 建立 `PEOPLE` 註釋。僅將 *CEOs* 註釋為 `PEOPLE` 實體類型。

        一般而言，存在過多的重疊提及項目，表示註釋準則不明確，而且需要改善以提供如何在來源資料中處理複合字的更好範例。

    1. 若要移除您剛才新增的註釋，請按 Ctrl+Z 來復原該動作。若要稍後移除實體提及項目，您可以在提及項目上按一下滑鼠左鍵，按 Delete 鍵，或按一下**檢視詳細資料**，然後按一下已指派給提及項目之實體類型旁的 **X**。

1. 視類型系統而定，您或許能夠配置實體提及項目的屬性，例如指派實體角色或子類型，或提及項目類別或類型。若要這樣做，請選取一個提及項目，然後按一下**屬性視圖**。

1. 隨時按一下**儲存**以儲存您的工作。

### 下一步
{: #wks_haentity_next}

在完成註釋文件中的所有實體提及項目、關係提及項目及互相參照之後，如果適用的話，請將文件狀態從**進行中**變更為**已完成**、按一下**儲存**，然後關閉文件。

在完成註釋所有文件並將它們標示為**已完成**之後，註釋集的狀態會變更為**已提交**。如此專案經理就會知道，他們可以開始評估註釋人員內部協議的文件、拒絕或接受文件，以及將它們提升至基準。

## 註釋重複提及項目
{: #wks_haconcordance}

您可以選擇性地使用詞語索引工具，一次標示多個出現的提及項目。此工具可讓您在整個文件中以及各註釋集間，使用相同的實體類型來註釋相同的文字。使用此工具有助於確保在多個文件間進行註釋的一致性。例如，您可以在提及項目模式下個別標示每一個出現的提及項目 *encryption*，或者可以使用詞語索引工具，標示所有出現的提及項目 *encryption*。不論哪種方式，模型都會從您套用至提及項目的實體類型中學習。

### 關於本作業
{: #wks_haconcordance_about}

雖然詞語索引工具是選用的，但在您開始註釋個別文件中的提及項目之前，最佳作法是使用詞語索引工具來註釋文件內或各文件間的提及項目。當您使用詞語索引工具，將實體類型套用至提及項目時，系統會將該實體類型套用至所有相符的提及項目，以置換指派給相符提及項目的任何現有實體類型。為了避免衝突，當詞語索引工具套用新的實體類型時，會從現有的實體類型中移除屬性（例如角色或子類型）。

### 程序
{: #wks_haconcordance_procedure}

若要註釋重複提及項目，請執行下列動作：

1. 以註釋人員身分（或以獲指派要註釋之文件的管理者或專案經理身分）登入。即會顯示包含已指派給您之作業的工作區。
1. 開啟工作區，然後按一下**機器學習模型** > **註釋作業**。即會顯示已指派給您的註釋作業。
1. 開啟您要使用的註釋作業。即會顯示已指派給您的註釋集。
1. 按一下**註釋**來開啟您要使用的註釋集。即會顯示註釋集中的文件。
1. 開啟您要註釋的文件。依預設，文件會在**提及項目**模式下開啟，此模式是您用來註釋提及項目的模式。
1. 如果尚未新增任何註釋，請至少新增一個註釋。從您的類型系統中，選取代表實體類型之提及項目的單字或單字詞組，並將適當類型指派給它。按一下**儲存**以儲存您的註釋。
1. 選取您要註釋之重複文字的單一出現項目，然後按一下**詞語索引**。
1. 選取要套用所選取實體類型的文件。您可以在已指派要註釋的所有文件、已開始註釋的所有文件，或尚未開始註釋的所有文件中建立註釋。
1. 按一下**預覽**，以查看將新增的註釋。

  如果您要檢視更大上下文中的註釋，請按一下圖示來預覽文件內容，或在新視窗中開啟文件。

1. 按一下**套用及檢閱**，以將選取的實體類型套用至所選取文件中的提及項目。您仍有機會檢閱將新增的註釋。如果特定上下文中的註釋不正確，您可以藉由按一下「編輯」圖示，然後移除提及項目的實體類型指派，來移除該出現項目。
1. 當註釋清單符合您的要求時，請按一下**回到建立基準編輯器**。

### 結果
{: #wks_haconcordance_results}

已註釋文件中的提及項目。沒有方法一次移除一組您透過詞語索引所新增的提及項目。您必須移除每一個提及項目（一次一個）。

## 將提及項目註釋為互相參照
{: #wks_hacoref}

若要將提及項目註釋為相同實體的互相參照，註釋人員會選取參照相同事物之提及項目的每個出現項目。互相參照可協助模型辨識以不同方式參照的實體是否將與相同實體相關聯，例如美國州的名稱及其縮寫、公司名稱及其字首語，或參照回該人員的人員名稱及代名詞。

### 開始之前
{: #wks_hacoref_prereqs}

您必須註釋文件中的提及項目，然後才能識別互相參照。

### 關於本作業
{: #wks_hacoref_about}

當您將提及項目註釋為互相參照時，系統會建立一個互相參照鏈結。該鏈結提供一種方式，讓您檢視上下文中的所有提及項目，並驗證所有出現項目都屬於同一個實體。例如，"Barack"、"Michelle"、"he" 及 "she" 全都是相同的實體類型 `PERSON`，但 "Barack" 及 "he" 是一個實體，而 "Michelle" 及 "she" 是另一個實體。在此範例中，您會建立兩個互相參照鏈結。

建立互相參照鏈結時，您必須選取已由相同實體類型所標示的提及項目。不過，在某些情況下，您可能想要在相同的互相參照鏈結中包括不同類型的提及項目。若要這麼做，您必須建立多個鏈結，然後合併它們。例如，想想人們如何漸進使用速記來避免文字中重複的事物。在交通事故報告中，第一個參照的車輛可能是 "2004 Honda Accord Sedan"。稍後，作者可能將車輛稱為 "Accord"，之後只將車輛稱為 "vehicle"。如果類型系統包括車輛製造商、型號及類型的項目，則您可以為每個實體類型建立多個互相參照鏈結，然後合併它們以建立合併的鏈結。合併的鏈結有助於訓練機器學習模型，以辨識所有這些參照相同事物的提及項目。

另一種結合不同實體類型之提及項目的方式，就是使用某個實體類型的提及項目來建立一個鏈結。然後，您可以按一下另一個實體類型的提及項目，接著按一下您已建立的鏈結，將提及項目新增至該鏈結。

視您的註釋準則而定，如果動詞提及相同的動作實例，則您可能想要對動詞以及名詞建立互相參照鏈結。例如，如果動詞 "encrypts" 的兩個提及項目參照同一個出現的加密，則您可以互相參照提及項目。但是，如果 "encrypts" 的某個參照是一般參照，或者如果兩個出現項目參照兩個不同的加密動作，則您不會互相參照它們。如果兩個不同的動詞參照同一個出現的動作，您可能會想要互相參照提及項目。例如，在聲明 "He encrypted the document, and after that processing he sent the file ... " 中，提及項目 "encrypted" 及 "processing" 可以互相參照，因為它們參照相同的動作實例。

最重要的是一致性。明確地利用註釋準則中的範例，決定您要如何註釋互相參照及指定規則。

### 程序
{: #wks_hacoref_procedure}

若要將提及項目註釋為互相參照，請執行下列動作：

1. 以註釋人員身分（或以獲指派要註釋之文件的管理者或專案經理身分）登入。即會顯示包含已指派給您之作業的工作區。
1. 開啟工作區，然後按一下**機器學習模型** > **註釋作業**。即會顯示已指派給您的註釋作業。
1. 開啟您要使用的註釋作業。即會顯示已指派給您的註釋集。
1. 按一下**註釋**來開啟您要使用的註釋集。即會顯示註釋集中的文件。
1. 開啟您要註釋的文件。依預設，文件會在**提及項目**模式下開啟，此模式是您用來註釋提及項目的模式。
1. 按一下**互相參照**。
1. 建立互相參照鏈：

    1. 在文件中四處移動，然後按一下每一個表示相同事物，並由相同實體類型標示的提及項目。例如，假設所有這些提及項目都有實體類型 `ORGANIZATION`，請按一下每個出現的 `{{site.data.keyword.IBM_notm}}`、`International Business Machines` 及 `{{site.data.keyword.IBM_notm}} Corp.`。
    1. 按兩下您要新增至鏈結的最後一個提及項目。互相參照鏈結是在側邊畫面中建立的。鏈結名稱符合您選取的第一個提及項目。
    1. 若要強調顯示鏈結中的所有提及項目，以在上下文中檢閱它們，請將游標移至側邊窗格中的鏈結名稱上方。

1. **單一提及項目清單**會顯示文件中已註釋、但尚未新增至鏈結的詞彙。如果您注意到清單中的提及項目屬於鏈結，則您可以從這裡將它新增至鏈結。

    1. 從側邊畫面的**單一提及項目清單**中，按一下提及項目。
    1. 從提及項目說明下的下拉清單中，選擇代表您要新增提及項目之鏈結的號碼。
    1. 按一下**合併**以將提及項目新增至鏈結，然後按一下**確定**。

    即會從**單一提及項目清單**中移除提及項目，而且現在所屬的鏈結號碼會顯示在文件中提及項目的下方。

1. 您可以使用下列方法來復原工作：

    - 若要移除您剛才新增的互相參照鏈結，請按 Ctrl+Z 來復原該動作。
    - 若要稍後移除互相參照鏈結，請從**互相參照鏈結**側邊畫面中，按一下您要移除之鏈結旁的 **X**。
    - 若要從鏈結中移除單一提及項目，請按一下互相參照 ID，以開啟一個視窗，其中顯示鏈結中的提及項目清單，然後按一下您要移除之提及項目旁的 **X**。

1. 隨時按一下**儲存**以儲存您的工作。

### 下一步
{: #wks_hacoref_next}

在完成註釋文件中的所有實體提及項目、關係提及項目及互相參照之後，如果適用的話，請將文件狀態從**進行中**變更為**已完成**、按一下**儲存**，然後關閉文件。

在完成註釋所有文件並將它們標示為**已完成**之後，註釋集的狀態會變更為**已提交**。該狀態就會讓專案經理知道，他們可以開始評估註釋人員內部協議的文件、拒絕它們或接受它們，以及將它們提升至基準。

## 註釋關係
{: #wks_harelation}

若要註釋關係提及項目，註釋人員會在句子中兩個實體提及項目之間尋找關係的文字證明，然後套用最能適當說明關係類型的標籤。可以套用的標籤是工作區類型系統中定義的關係類型。

### 開始之前

您必須註釋文件中的實體提及項目，然後才能在它們之間定義關係類型。

### 關於本作業

只有在文字明確說明兩個實體提及項目之間的關係時，才能定義關係提及項目。明確的文字證明可能包括所有格代名詞、主動賓結構或同位語。例如，在下列句子中，無法在 `dog` 與 `owner` 之間新增 `ownedBy` 關係提及項目。

<pre><code>NOT VALID: The <u>dog</u> got a treat from its <u>owner</u>.</code></pre>

有效的關係提及項目是在 `its` 與 `owner` 之間，因為句子這個部分的文字明確定義狗與其擁有者之間的關係。`Owner` 可能是房屋擁有者或其他狗的擁有者，但此文字清楚指出句子開頭提及的同一隻狗是由此人擁有。

<pre><code>VALID: The dog got a treat from <u>its</u> <u>owner</u>.</code></pre>

<pre><code>                                |ownedBy^</code></pre>

兩個實體提及項目及定義它們之間關係類型的文字都必須存在於單一句子內的需求，似乎很嚴格。不過，請記住，如同上述範例一樣，只要您也識別文件中的互相參照，就可以識別句子中的關係提及項目，其中包含的單字可作為較不正式的實體提及項目（例如，代名詞）。例如，`Mary is a scientist. She works for {{site.data.keyword.IBM_notm}}.` 中的第二個句子包含 Mary 與 {{site.data.keyword.IBM_notm}} 之間的 `employedBy` 關係的有效文字證明。瞭解互相參照 `She` 是 `PERSON` 實體類型 `Mary` 的參照。它是 `Mary` 與 `She` 之間的互相參照的識別，加上 `She` 與 `{{site.data.keyword.IBM_notm}}` 之間的關係提及項目的識別，合起來完整擷取此關係。註釋關係提及項目的正確方法如下所示：

<pre><code>Mary[<i>#1</i>] is a scientist. <u>She</u>[<i>#1</i>] works for <u>IBM</u>.</code></pre>

<pre><code>                         |----employedBy----^</code></pre>

其中，下標 [<i>#1</i>] 指出 `Mary` 及 `She` 都是文件中第一個互相參照鏈結的成員。

### 程序

若要在文件中實體提及項目之間註釋關係提及項目，請執行下列動作：

1. 以註釋人員身分（或以獲指派要註釋之文件的管理者或專案經理身分）登入。即會顯示包含已指派給您之作業的工作區。
1. 開啟工作區，然後按一下**機器學習模型** > **註釋作業**。即會顯示已指派給您的註釋作業。
1. 開啟您要使用的註釋作業。即會顯示已指派給您的註釋集。
1. 按一下**註釋**來開啟您要使用的註釋集。即會顯示註釋集中的文件。
1. 開啟您要註釋的文件。依預設，文件會在**提及項目**模式下開啟，此模式是您用來註釋提及項目的模式。
1. 按一下**關係**。
1. 若要註釋關係，請執行下列動作：

    1. 按一下文字中的實體提及項目，然後按一下相同句子中您要連接至第一個提及項目的第二個實體提及項目。
    1. 從右側窗格中選取您要套用的關係類型，或輸入關係類型的鍵盤快速鍵。可用關係類型的清單受制於您選取的第一個實體提及項目，並會進一步受制於第二個實體提及項目。在某些情況下，只會保留一個關係類型；您仍須明確選取關係類型才能套用它。

        如果註釋準則先前已連接至工作區，且您需要協助來選擇要套用的正確註釋，請按一下**檢視準則**。視管理準則的網站所設定的存取權而定，您可能可以在開啟這些準則（例如，若要新增說明及範例）之後予以更新。
        {: tip}

1. 若要移除您剛才新增的關係提及項目，請按 Ctrl+Z 來復原該動作。若要稍後移除關係提及項目，您可以在關係類型上按一下滑鼠左鍵，然後按**刪除**鍵，或按一下關係類型旁的 **X**。
1. 視類型系統而定，您或許能夠配置關係的屬性，例如指派關係時態、形態或類別。若要這樣做，請選取一個關係標籤，然後按一下**屬性視圖**。
1. 隨時按一下**儲存**以儲存您的工作。

### 下一步

在完成註釋文件中的所有實體提及項目、關係提及項目及互相參照之後，如果適用的話，請將文件狀態從**進行中**變更為**已完成**、按一下**儲存**，然後關閉文件。

在完成註釋所有文件並將它們標示為**已完成**之後，註釋集的狀態會變更為**已提交**。如此專案經理就會知道，他們可以開始評估註釋人員內部協議的文件，並拒絕它們或接受它們，以及將它們升級成基準。

## 相關資訊

[建立字典](/docs/services/watson-knowledge-studio/dictionaries.html)

[對基準編輯器進行疑難排解](/docs/services/watson-knowledge-studio/user-guide-help.html)

[建立類型系統](/docs/services/watson-knowledge-studio/typesystem.html)
