---
title: 第3課：處理自行車購買者的採礦結構 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e748c2cd-339d-4e82-82f1-be2d0fc41b61
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2e3f85016b32884b9a6b809e28d20d9985f97cd9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703526"
---
# <a name="lesson-3-processing-the-bike-buyer-mining-structure"></a><span data-ttu-id="83dfd-102">第 3 課：處理自行車買主採礦結構</span><span class="sxs-lookup"><span data-stu-id="83dfd-102">Lesson 3: Processing the Bike Buyer Mining Structure</span></span>
  <span data-ttu-id="83dfd-103">在這一課，您將使用範例資料庫中的 INSERT INTO 語句和 vTargetMail view， [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 來處理您在[第1課：建立自行車購買者採礦結構](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md)和[第2課：將採礦模型加入自行車購買者採礦結構](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)中所建立的採礦結構和採礦模型。</span><span class="sxs-lookup"><span data-stu-id="83dfd-103">In this lesson, you will use the INSERT INTO statement and the vTargetMail view from the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample database to process the mining structures and mining models that you created in [Lesson 1: Creating the Bike Buyer Mining Structure](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md) and [Lesson 2: Adding Mining Models to the Bike Buyer Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md).</span></span>  
  
 <span data-ttu-id="83dfd-104">當您處理採礦結構時，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 會讀取來源資料並建立支援採礦模型的結構。</span><span class="sxs-lookup"><span data-stu-id="83dfd-104">When you process a mining structure, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] reads the source data and builds the structures that support mining models.</span></span> <span data-ttu-id="83dfd-105">當您處理採礦模型時，採礦結構所定義的資料會透過您選擇的資料採礦演算法來傳遞。</span><span class="sxs-lookup"><span data-stu-id="83dfd-105">When you process a mining model, the data defined by the mining structure is passed through the data mining algorithm that you choose.</span></span> <span data-ttu-id="83dfd-106">此演算法會搜尋趨勢和模式，然後將此資訊儲存在採礦模型中。</span><span class="sxs-lookup"><span data-stu-id="83dfd-106">The algorithm searches for trends and patterns, and then stores this information in the mining model.</span></span> <span data-ttu-id="83dfd-107">因此，採礦模型不包含實際來源資料，而包含演算法所發現的資訊。</span><span class="sxs-lookup"><span data-stu-id="83dfd-107">The mining model, therefore, does not contain the actual source data, but instead contains the information that was discovered by the algorithm.</span></span> <span data-ttu-id="83dfd-108">如需處理採礦模型的詳細資訊，請參閱[&#40;資料採礦&#41;的處理需求和考慮](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="83dfd-108">For more information about processing mining models, see [Processing Requirements and Considerations &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).</span></span>  
  
 <span data-ttu-id="83dfd-109">只有當您變更結構資料行或變更來源資料時，才需要重新處理採礦結構。</span><span class="sxs-lookup"><span data-stu-id="83dfd-109">You need to reprocess a mining structure only if you change a structure column or change the source data.</span></span> <span data-ttu-id="83dfd-110">如果您將採礦模型加入已處理的採礦結構中，您可以使用 INSERT INTO MINING MODEL 陳述式來定型新的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="83dfd-110">If you add a mining model to a mining structure that has already been processed, you can use the INSERT INTO MINING MODEL statement to train the new mining model.</span></span>  
  
## <a name="train-structure-template"></a><span data-ttu-id="83dfd-111">定型結構範本</span><span class="sxs-lookup"><span data-stu-id="83dfd-111">Train Structure Template</span></span>  
 <span data-ttu-id="83dfd-112">若要將採礦結構和其相關聯的採礦模型定型，請使用[INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)語句。</span><span class="sxs-lookup"><span data-stu-id="83dfd-112">In order to train the mining structure and its associated mining models, use the [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) statement.</span></span> <span data-ttu-id="83dfd-113">陳述式中的程式碼可分成下列各部份：</span><span class="sxs-lookup"><span data-stu-id="83dfd-113">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="83dfd-114">識別採礦結構</span><span class="sxs-lookup"><span data-stu-id="83dfd-114">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="83dfd-115">列出採礦結構中的資料行</span><span class="sxs-lookup"><span data-stu-id="83dfd-115">Listing the columns in the mining structure</span></span>  
  
-   <span data-ttu-id="83dfd-116">定義定型資料</span><span class="sxs-lookup"><span data-stu-id="83dfd-116">Defining the training data</span></span>  
  
 <span data-ttu-id="83dfd-117">以下是 INSERT INTO 陳述式的一般範例：</span><span class="sxs-lookup"><span data-stu-id="83dfd-117">The following is a generic example of the INSERT INTO statement:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
)  
OPENQUERY([<datasource>],'<SELECT statement>')  
```  
  
 <span data-ttu-id="83dfd-118">程式碼的第一行識別您將定型的採礦結構：</span><span class="sxs-lookup"><span data-stu-id="83dfd-118">The first line of the code identifies the mining structure that you will train:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="83dfd-119">程式碼的下一行指定採礦結構定義的資料行。</span><span class="sxs-lookup"><span data-stu-id="83dfd-119">The next line of the code specifies the columns that are defined by the mining structure.</span></span> <span data-ttu-id="83dfd-120">您必須列出採礦結構的每一個資料行，且每一個資料行必須對應到來源查詢資料內包含的資料行。</span><span class="sxs-lookup"><span data-stu-id="83dfd-120">You must list each column in the mining structure, and each column must map to a column contained within the source query data.</span></span>  
  
```  
(  
   <mining structure columns>  
)  
```  
  
 <span data-ttu-id="83dfd-121">程式碼的最後一行定義將用來定型採礦結構的資料：</span><span class="sxs-lookup"><span data-stu-id="83dfd-121">The final line of the code defines the data that will be used to train the mining structure:</span></span>  
  
```  
OPENQUERY([<datasource>],'<SELECT statement>')  
```  
  
 <span data-ttu-id="83dfd-122">在這一課，您使用 `OPENQUERY` 來定義來源資料。</span><span class="sxs-lookup"><span data-stu-id="83dfd-122">In this lesson, you use `OPENQUERY` to define the source data.</span></span> <span data-ttu-id="83dfd-123">如需有關定義來源查詢之其他方法的詳細資訊，請參閱[&#60;來源資料查詢&#62;](/sql/dmx/source-data-query)。</span><span class="sxs-lookup"><span data-stu-id="83dfd-123">For information about other methods of defining the source query, see [&#60;source data query&#62;](/sql/dmx/source-data-query).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="83dfd-124">課程工作</span><span class="sxs-lookup"><span data-stu-id="83dfd-124">Lesson Tasks</span></span>  
 <span data-ttu-id="83dfd-125">您將在這一課執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="83dfd-125">You will perform the following task in this lesson:</span></span>  
  
-   <span data-ttu-id="83dfd-126">處理自行車買主採礦結構</span><span class="sxs-lookup"><span data-stu-id="83dfd-126">Process the Bike Buyer mining structure</span></span>  
  
## <a name="processing-the-predictive-mining-structure"></a><span data-ttu-id="83dfd-127">處理預測採礦結構</span><span class="sxs-lookup"><span data-stu-id="83dfd-127">Processing the Predictive Mining Structure</span></span>  
  
#### <a name="to-process-the-mining-structure-by-using-insert-into"></a><span data-ttu-id="83dfd-128">若要使用 INSERT INTO 處理採礦結構</span><span class="sxs-lookup"><span data-stu-id="83dfd-128">To process the mining structure by using INSERT INTO</span></span>  
  
1.  <span data-ttu-id="83dfd-129">在**物件總管**中，以滑鼠右鍵按一下的實例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 [追加**查詢**]，然後按一下 [ **DMX**]。</span><span class="sxs-lookup"><span data-stu-id="83dfd-129">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="83dfd-130">此時會開啟 [查詢編輯器] 且包含新的空白查詢。</span><span class="sxs-lookup"><span data-stu-id="83dfd-130">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="83dfd-131">將 INSERT INTO 陳述式的一般範例複製到空白查詢中。</span><span class="sxs-lookup"><span data-stu-id="83dfd-131">Copy the generic example of the INSERT INTO statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="83dfd-132">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="83dfd-132">Replace the following:</span></span>  
  
    ```  
    [<mining structure name>]   
    ```  
  
     <span data-ttu-id="83dfd-133">成為：</span><span class="sxs-lookup"><span data-stu-id="83dfd-133">with:</span></span>  
  
    ```  
    Bike Buyer  
    ```  
  
4.  <span data-ttu-id="83dfd-134">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="83dfd-134">Replace the following:</span></span>  
  
    ```  
    <mining structure columns>  
    ```  
  
     <span data-ttu-id="83dfd-135">成為：</span><span class="sxs-lookup"><span data-stu-id="83dfd-135">with:</span></span>  
  
    ```  
    [Customer Key],  
    [Age],  
    [Bike Buyer],  
    [Commute Distance],  
    [Education],  
    [Gender],  
    [House Owner Flag],  
    [Marital Status],  
    [Number Cars Owned],  
    [Number Children At Home],  
    [Occupation],  
    [Region],  
    [Total Children],  
    [Yearly Income]  
    ```  
  
5.  <span data-ttu-id="83dfd-136">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="83dfd-136">Replace the following:</span></span>  
  
    ```  
    OPENQUERY([<datasource>],'<SELECT statement>')  
    ```  
  
     <span data-ttu-id="83dfd-137">成為：</span><span class="sxs-lookup"><span data-stu-id="83dfd-137">with:</span></span>  
  
    ```  
    OPENQUERY([Adventure Works DW],  
       'SELECT CustomerKey, Age, BikeBuyer,  
             CommuteDistance,EnglishEducation,  
             Gender,HouseOwnerFlag,MaritalStatus,  
             NumberCarsOwned,NumberChildrenAtHome,   
             EnglishOccupation,Region,TotalChildren,  
             YearlyIncome   
        FROM dbo.vTargetMail')  
    ```  
  
     <span data-ttu-id="83dfd-138">OPENQUERY 陳述式會參考 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 資料來源來存取 vTargetMail 檢視表。</span><span class="sxs-lookup"><span data-stu-id="83dfd-138">The OPENQUERY statement references the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] data source to access the view vTargetMail.</span></span> <span data-ttu-id="83dfd-139">此檢視包含將用來定型採礦模型的來源資料。</span><span class="sxs-lookup"><span data-stu-id="83dfd-139">The view contains the source data that will be used to train the mining models.</span></span>  
  
     <span data-ttu-id="83dfd-140">現在，完整的陳述式應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="83dfd-140">The complete statement should now be as follows:</span></span>  
  
    ```  
    INSERT INTO MINING STRUCTURE [Bike Buyer]  
    (  
       [Customer Key],  
       [Age],  
       [Bike Buyer],  
       [Commute Distance],  
       [Education],  
       [Gender],  
       [House Owner Flag],  
       [Marital Status],  
       [Number Cars Owned],  
       [Number Children At Home],  
       [Occupation],  
       [Region],  
       [Total Children],  
       [Yearly Income]     
    )  
    OPENQUERY([Adventure Works DW],  
       'SELECT CustomerKey, Age, BikeBuyer,  
             CommuteDistance,EnglishEducation,  
             Gender,HouseOwnerFlag,MaritalStatus,  
             NumberCarsOwned,NumberChildrenAtHome,   
             EnglishOccupation,Region,TotalChildren,  
             YearlyIncome   
        FROM dbo.vTargetMail')  
    ```  
  
6.  <span data-ttu-id="83dfd-141">**在 [檔案**] 功能表上，按一下 [**將 DMXQuery1 另存為**]。</span><span class="sxs-lookup"><span data-stu-id="83dfd-141">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="83dfd-142">在 [**另存**新檔] 對話方塊中，流覽至適當的資料夾，並將檔案命名為 `Process Bike Buyer Structure.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="83dfd-142">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Process Bike Buyer Structure.dmx`.</span></span>  
  
8.  <span data-ttu-id="83dfd-143">在工具列上，按一下 [**執行**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="83dfd-143">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="83dfd-144">在下一課，您將探索這一課加入採礦結構中的採礦模型內容。</span><span class="sxs-lookup"><span data-stu-id="83dfd-144">In the next lesson, you will explore content in the mining models you added to the mining structure in this lesson.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="83dfd-145">下一課</span><span class="sxs-lookup"><span data-stu-id="83dfd-145">Next Lesson</span></span>  
 [<span data-ttu-id="83dfd-146">第 4 課：瀏覽自行車買主採礦模型</span><span class="sxs-lookup"><span data-stu-id="83dfd-146">Lesson 4: Browsing the Bike Buyer Mining Models</span></span>](../../2014/tutorials/lesson-4-browsing-the-bike-buyer-mining-models.md)  
  
  
