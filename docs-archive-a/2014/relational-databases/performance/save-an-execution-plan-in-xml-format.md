---
title: 以 XML 格式儲存執行計畫 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- XML query plans [SQL Server]
- opening execution plans
- XML Showplans [SQL Server]
- execution plans [SQL Server], saving
- saving execution plans
ms.assetid: c439e53b-56f3-4442-97c6-dabd48a203d8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 84ed341d186993ed77260e8361156b324c597839
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597779"
---
# <a name="save-an-execution-plan-in-xml-format"></a><span data-ttu-id="b823c-102">以 XML 格式儲存執行計畫</span><span class="sxs-lookup"><span data-stu-id="b823c-102">Save an Execution Plan in XML Format</span></span>
  <span data-ttu-id="b823c-103">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 將執行計畫儲存為 XML 檔，並開啟它們來進行檢視。</span><span class="sxs-lookup"><span data-stu-id="b823c-103">Use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to save execution plans as an XML file, and to open them for viewing.</span></span>  
  
 <span data-ttu-id="b823c-104">若要使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的執行計畫功能，或使用 XML Showplan SET 選項，使用者必須具有適當的權限，才能執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢來產生執行計畫，同時使用者還必須具有查詢所參考之所有資料庫的 SHOWPLAN 權限。</span><span class="sxs-lookup"><span data-stu-id="b823c-104">To use the execution plan feature in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], or to use the XML Showplan SET options, users must have the appropriate permissions to execute the [!INCLUDE[tsql](../../includes/tsql-md.md)] query for which an execution plan is being generated, and they must be granted the SHOWPLAN permission for all databases referenced by the query.</span></span>  
  
### <a name="to-save-a-query-plan-by-using-the-xml-showplan-set-options"></a><span data-ttu-id="b823c-105">若要使用 XML Showplan SET 選項來儲存查詢計畫</span><span class="sxs-lookup"><span data-stu-id="b823c-105">To save a query plan by using the XML Showplan SET options</span></span>  
  
1.  <span data-ttu-id="b823c-106">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，開啟查詢編輯器並連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b823c-106">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] open a query editor and connect to [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b823c-107">利用下列陳述式開啟 SHOWPLAN_XML：</span><span class="sxs-lookup"><span data-stu-id="b823c-107">Turn SHOWPLAN_XML on with the following statement:</span></span>  
  
    ```  
    SET SHOWPLAN_XML ON;  
    GO  
    ```  
  
     <span data-ttu-id="b823c-108">若要開啟 STATISTICS XML，請使用下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="b823c-108">To turn STATISTICS XML on, use the following statement:</span></span>  
  
    ```  
    SET STATISTICS XML ON;  
    GO  
    ```  
  
     <span data-ttu-id="b823c-109">SHOWPLAN_XML 會產生查詢的編譯階段查詢執行計畫資訊，但不會執行查詢。</span><span class="sxs-lookup"><span data-stu-id="b823c-109">SHOWPLAN_XML generates compile-time query execution plan information for a query, but does not execute the query.</span></span> <span data-ttu-id="b823c-110">STATISTICS XML 會產生查詢的執行階段查詢執行計畫資訊，並且執行查詢。</span><span class="sxs-lookup"><span data-stu-id="b823c-110">STATISTICS XML generates run-time query execution plan information for a query, and executes the query.</span></span>  
  
3.  <span data-ttu-id="b823c-111">執行查詢。</span><span class="sxs-lookup"><span data-stu-id="b823c-111">Execute a query.</span></span> <span data-ttu-id="b823c-112">範例：</span><span class="sxs-lookup"><span data-stu-id="b823c-112">Example:</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SET SHOWPLAN_XML ON;  
    GO  
    -- Execute a query.  
    SELECT BusinessEntityID   
    FROM HumanResources.Employee  
    WHERE NationalIDNumber = '509647174';  
    GO  
    SET SHOWPLAN_XML OFF;  
    ```  
  
4.  <span data-ttu-id="b823c-113">在 [結果] 窗格中，以滑鼠右鍵按一下包含查詢計劃的 [Microsoft SQL Server XML 執行程序表]，然後按一下 [儲存結果]。</span><span class="sxs-lookup"><span data-stu-id="b823c-113">In the **Results** pane, right-click the **Microsoft SQL Server XML Showplan** that contains the query plan, and then click **Save Results As**.</span></span>  
  
5.  <span data-ttu-id="b823c-114">在 [儲存 \<Grid or Text> 結果]  對話方塊的 [存檔類型] 方塊中，按一下 [所有檔案 (\*.\*)]。</span><span class="sxs-lookup"><span data-stu-id="b823c-114">In the **Save** \<Grid or Text> **Results** dialog box, in the **Save as type** box, click **All files (\*.\*)**.</span></span>  
  
6.  <span data-ttu-id="b823c-115">在 [檔案名稱] 方塊中，提供格式為 \<name**>.sqlplan\*\* 的名稱，然後按一下 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="b823c-115">In the **File name** box provide a name, in the format \<name**>.sqlplan\*\*, and then click **Save**.</span></span>  
  
### <a name="to-save-an-execution-plan-by-using-sql-server-management-studio-options"></a><span data-ttu-id="b823c-116">若要使用 SQL Server Management Studio 選項來儲存執行計畫</span><span class="sxs-lookup"><span data-stu-id="b823c-116">To save an execution plan by using SQL Server Management Studio options</span></span>  
  
1.  <span data-ttu-id="b823c-117">使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]來產生一個評估的執行計畫或實際執行計畫。</span><span class="sxs-lookup"><span data-stu-id="b823c-117">Generate either an estimated execution plan or an actual execution plan by using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="b823c-118">如需詳細資訊，請參閱 [顯示估計執行計畫](display-the-estimated-execution-plan.md) 或 [顯示實際執行計畫](display-an-actual-execution-plan.md)。</span><span class="sxs-lookup"><span data-stu-id="b823c-118">For more information, see [Display the Estimated Execution Plan](display-the-estimated-execution-plan.md) or [Display an Actual Execution Plan](display-an-actual-execution-plan.md).</span></span>  
  
2.  <span data-ttu-id="b823c-119">在結果窗格的 [執行計畫] 索引標籤中，以滑鼠右鍵按一下圖形執行計畫，然後選擇 [另存執行計畫為]。</span><span class="sxs-lookup"><span data-stu-id="b823c-119">In the **Execution plan** tab of the results pane, right-click the graphical execution plan, and choose **Save Execution Plan As**.</span></span>  
  
     <span data-ttu-id="b823c-120">您也可以從 [檔案] 功能表選擇 [另存執行計畫為]。</span><span class="sxs-lookup"><span data-stu-id="b823c-120">As an alternative, you can also choose **Save Execution Plan As** on the **File** menu.</span></span>  
  
3.  <span data-ttu-id="b823c-121">在 [另存新檔] 對話方塊中，請確認將 [檔案類型] 設為 [執行計畫檔案 (\*.sqlplan)]。</span><span class="sxs-lookup"><span data-stu-id="b823c-121">In the **Save As** dialog box, make sure that the **Save as type** is set to **Execution Plan Files (\*.sqlplan)**.</span></span>  
  
4.  <span data-ttu-id="b823c-122">在 [檔案名稱] 方塊中，提供格式為 \<name**>.sqlplan\*\* 的名稱，然後按一下 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="b823c-122">In the **File name** box provide a name, in the format \<name**>.sqlplan\*\*, and then click **Save**.</span></span>  
  
### <a name="to-open-a-saved-xml-query-plan-in-sql-server-management-studio"></a><span data-ttu-id="b823c-123">若要在 SQL Server Management Studio 中開啟已儲存的 XML 查詢計畫</span><span class="sxs-lookup"><span data-stu-id="b823c-123">To open a saved XML query plan in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="b823c-124">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的 **「檔案」** 功能表上，選擇 **「開啟」** ，然後按一下 **「檔案」** 。</span><span class="sxs-lookup"><span data-stu-id="b823c-124">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **File** menu, choose **Open**, and then click **File**.</span></span>  
  
2.  <span data-ttu-id="b823c-125">在 [開啟檔案] 對話方塊中，將 [檔案類型] 設為 [執行計畫檔案 (\*.sqlplan)]，以產生已儲存之 XML 查詢計劃檔案的篩選清單。</span><span class="sxs-lookup"><span data-stu-id="b823c-125">In the **Open File** dialog box, set **Files of type** to **Execution Plan Files (\*.sqlplan)** to produce a filtered list of saved XML query plan files.</span></span>  
  
3.  <span data-ttu-id="b823c-126">選取您要檢視的 XML 查詢計劃檔案，然後按一下 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="b823c-126">Select the XML query plan file that you want to view, and click **Open**.</span></span>  
  
     <span data-ttu-id="b823c-127">您也可以在 Windows 檔案總管中，按兩下副檔名為 **.sqlplan**的檔案。</span><span class="sxs-lookup"><span data-stu-id="b823c-127">As an alternative, in Windows Explorer, double-click a file with extension **.sqlplan**.</span></span> <span data-ttu-id="b823c-128">計畫會在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中開啟。</span><span class="sxs-lookup"><span data-stu-id="b823c-128">The plan opens in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b823c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b823c-129">See Also</span></span>  
 <span data-ttu-id="b823c-130">[SET SHOWPLAN_XML &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-showplan-xml-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b823c-130">[SET SHOWPLAN_XML &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-showplan-xml-transact-sql) </span></span>  
 [<span data-ttu-id="b823c-131">SET STATISTICS XML &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b823c-131">SET STATISTICS XML &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-statistics-xml-transact-sql)  
  
  
