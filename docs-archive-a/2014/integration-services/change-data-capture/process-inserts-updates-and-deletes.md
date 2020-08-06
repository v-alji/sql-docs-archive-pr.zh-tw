---
title: 處理插入、更新與刪除 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],processing data
ms.assetid: 13a84d21-2623-4efe-b442-4125a7a2d690
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 67f016aaf4f7f83c0fa506966c4e78f5b8fadef6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585527"
---
# <a name="process-inserts-updates-and-deletes"></a><span data-ttu-id="11d54-102">處理插入、更新與刪除</span><span class="sxs-lookup"><span data-stu-id="11d54-102">Process Inserts, Updates, and Deletes</span></span>
  <span data-ttu-id="11d54-103">在執行累加式變更資料載入之 Integration Services 封裝的資料流程中，第二個工作是分隔插入、更新與刪除。</span><span class="sxs-lookup"><span data-stu-id="11d54-103">In the data flow of an Integration Services package that performs an incremental load of change data, the second task is to separate inserts, updates, and deletes.</span></span> <span data-ttu-id="11d54-104">然後，您可以使用適當的命令，將其套用到目的地。</span><span class="sxs-lookup"><span data-stu-id="11d54-104">Then, you can use appropriate commands to apply them to the destination.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="11d54-105">設計執行累加式變更資料載入之封裝資料流程的第一個工作是，設定執行擷取變更資料之查詢的來源元件。</span><span class="sxs-lookup"><span data-stu-id="11d54-105">The first task in designing the data flow of a package that performs an incremental load of change data is to configure the source component that runs the query that retrieves the change data.</span></span> <span data-ttu-id="11d54-106">如需此元件的詳細資訊，請參閱 [擷取與了解變更資料](retrieve-and-understand-the-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="11d54-106">For more information about this component, see [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md).</span></span> <span data-ttu-id="11d54-107">如需建立可執行累加式變更資料載入之封裝的完整程序描述，請參閱[異動資料擷取 &#40;SSIS&#41;](change-data-capture-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="11d54-107">For a description of the overall process for creating a package that performs an incremental load of change data, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="associating-friendly-values-to-separate-inserts-updates-and-deletes"></a><span data-ttu-id="11d54-108">將易記值與個別的插入、更新與刪除產生關聯</span><span class="sxs-lookup"><span data-stu-id="11d54-108">Associating Friendly Values to Separate Inserts, Updates, and Deletes</span></span>  
 <span data-ttu-id="11d54-109">在擷取變更資料的範例查詢中，**cdc.fn_cdc_get_net_changes_<擷取執行個體>** 函數僅會傳回名稱為 **__$operation** 之中繼資料的資料行。</span><span class="sxs-lookup"><span data-stu-id="11d54-109">In the example query that retrieves change data, the **cdc.fn_cdc_get_net_changes_<capture_instance>** function returns only the column of metadata named **__$operation**.</span></span> <span data-ttu-id="11d54-110">此中繼資料行包含表示哪個作業造成變更的序數值。</span><span class="sxs-lookup"><span data-stu-id="11d54-110">This metadata column contains an ordinal value that indicates which operation caused the change.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="11d54-111">如需使用呼叫 **cdc.fn_cdc_get_net_changes_<擷取執行個體>** 函數之查詢的詳細資訊，請參閱[建立函數以擷取變更資料](create-the-function-to-retrieve-the-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="11d54-111">For more information about the query that uses calls the **cdc.fn_cdc_get_net_changes_<capture_instance>** function, see [Create the Function to Retrieve the Change Data](create-the-function-to-retrieve-the-change-data.md).</span></span>  
  
 <span data-ttu-id="11d54-112">比對序數值及其對應作業的方式不像使用作業的助憶鍵那麼容易。</span><span class="sxs-lookup"><span data-stu-id="11d54-112">Matching an ordinal value to its corresponding operation is not as easy as using a mnemonic of the operation.</span></span> <span data-ttu-id="11d54-113">例如，'D' 可以輕易地表示刪除作業，而 'I' 則表示插入作業。</span><span class="sxs-lookup"><span data-stu-id="11d54-113">For example, 'D' can easily represent a delete operation and 'I' represent an insert operation.</span></span> <span data-ttu-id="11d54-114">在＜ [建立函數以擷取變更資料](create-the-function-to-retrieve-the-change-data.md)＞主題中建立的範例查詢可以進行從序數值轉換為在新資料行中傳回之易記字串值的這個轉換。</span><span class="sxs-lookup"><span data-stu-id="11d54-114">The example query that was created in the topic, [Creating the Function to Retrieve the Change Data](create-the-function-to-retrieve-the-change-data.md), makes this conversion from an ordinal value to a friendly string value that is returned in a new column.</span></span> <span data-ttu-id="11d54-115">下列程式碼區段會示範這項轉換：</span><span class="sxs-lookup"><span data-stu-id="11d54-115">The following segment of code shows this conversion:</span></span>  
  
```  
select   
    ...  
    case __$operation  
        when 1 then 'D'  
        when 2 then 'I'  
        when 4 then 'U'  
        else null  
     end as CDC_OPERATION  
```  
  
## <a name="configuring-a-conditional-split-transformation-to-direct-inserts-updates-and-deletes"></a><span data-ttu-id="11d54-116">將條件式分割轉換設定為直接插入、更新與刪除</span><span class="sxs-lookup"><span data-stu-id="11d54-116">Configuring a Conditional Split Transformation to Direct Inserts, Updates, and Deletes</span></span>  
 <span data-ttu-id="11d54-117">若要將變更資料的資料列直接轉換為三種輸出之一，「條件式分割」轉換最為理想。</span><span class="sxs-lookup"><span data-stu-id="11d54-117">To direct rows of change data to one of three outputs, the Conditional Split transformation is ideal.</span></span> <span data-ttu-id="11d54-118">此轉換只會檢查每個資料列中 **CDC_OPERATION** 資料行的值，然後判斷該變更為插入、更新還是刪除。</span><span class="sxs-lookup"><span data-stu-id="11d54-118">The transformation just checks the value of the **CDC_OPERATION** column in each row and determines whether that change was an insert, update, or delete.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="11d54-119">CDC_OPERATION 資料行包含從 **__$operation** 資料行中之數值衍生的易記字串值。</span><span class="sxs-lookup"><span data-stu-id="11d54-119">The CDC_OPERATION column contains a friendly string value derived from the numeric value in the **__$operation** column.</span></span>  
  
#### <a name="to-split-inserts-updates-and-deletes-for-processing-by-using-a-conditional-split-transformation"></a><span data-ttu-id="11d54-120">使用條件式分割轉換分割要處理的插入、更新與刪除</span><span class="sxs-lookup"><span data-stu-id="11d54-120">To split inserts, updates, and deletes for processing by using a Conditional Split transformation</span></span>  
  
1.  <span data-ttu-id="11d54-121">在 **[資料流程]** 索引標籤上，加入「條件式分割」轉換。</span><span class="sxs-lookup"><span data-stu-id="11d54-121">On the **Data Flow** tab, add a Conditional Split transformation.</span></span>  
  
2.  <span data-ttu-id="11d54-122">將 OLE DB 來源的輸出連接到「條件式分割」轉換。</span><span class="sxs-lookup"><span data-stu-id="11d54-122">Connect the output of the OLE DB source to the Conditional Split transformation.</span></span>  
  
3.  <span data-ttu-id="11d54-123">在 **[條件式分割轉換編輯器]** 的下方窗格中，輸入下列三行以指定三種輸出</span><span class="sxs-lookup"><span data-stu-id="11d54-123">In the **Conditional Split Transformation Editor**, in the lower pane of the editor, enter the following three lines to designate the three outputs</span></span>  
  
    1.  <span data-ttu-id="11d54-124">針對直接插入的資料列，將條件為 `CDC_OPERATION == "I"` 的行輸入到插入的輸出。</span><span class="sxs-lookup"><span data-stu-id="11d54-124">Enter a line with the condition `CDC_OPERATION == "I"` to direct inserted rows to the output for inserts.</span></span>  
  
    2.  <span data-ttu-id="11d54-125">針對直接更新的資料列，將條件為 `CDC_OPERATION == "U"` 的行輸入到更新的輸出。</span><span class="sxs-lookup"><span data-stu-id="11d54-125">Enter a line with the condition `CDC_OPERATION == "U"` to direct updated rows to the output for updates.</span></span>  
  
    3.  <span data-ttu-id="11d54-126">針對直接刪除的資料列，將條件為 `CDC_OPERATION == "D"` 的行輸入到刪除的輸出。</span><span class="sxs-lookup"><span data-stu-id="11d54-126">Enter a line with the condition `CDC_OPERATION == "D"` to direct deleted rows to the output for deletes.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="11d54-127">後續步驟</span><span class="sxs-lookup"><span data-stu-id="11d54-127">Next Step</span></span>  
 <span data-ttu-id="11d54-128">分割要處理的資料列後，下一個步驟是將變更套用到目的地。</span><span class="sxs-lookup"><span data-stu-id="11d54-128">After you split the rows for processing, the next step is to apply the changes to the destination.</span></span>  
  
 <span data-ttu-id="11d54-129">**下一個主題：** [將變更套用到目的地](apply-the-changes-to-the-destination.md)</span><span class="sxs-lookup"><span data-stu-id="11d54-129">**Next topic:** [Apply the Changes to the Destination](apply-the-changes-to-the-destination.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11d54-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11d54-130">See Also</span></span>  
 <span data-ttu-id="11d54-131">[Conditional Split Transformation](../data-flow/transformations/conditional-split-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="11d54-131">[Conditional Split Transformation](../data-flow/transformations/conditional-split-transformation.md) </span></span>  
 [<span data-ttu-id="11d54-132">使用條件式分割轉換來分割資料集</span><span class="sxs-lookup"><span data-stu-id="11d54-132">Split a Dataset by Using the Conditional Split Transformation</span></span>](../data-flow/transformations/split-a-dataset-by-using-the-conditional-split-transformation.md)  
  
  
