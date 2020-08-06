---
title: 新增、編輯、重新整理報表資料窗格中的欄位 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2e36f0fe-8100-4513-b169-14d611646f81
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2a20880b84383fc5d9f96c5611419a08facb9ac2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585082"
---
# <a name="add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs"></a><span data-ttu-id="89831-102">加入、編輯、重新整理報表資料窗格中的欄位 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="89831-102">Add, Edit, Refresh Fields in the Report Data Pane (Report Builder and SSRS)</span></span>
  <span data-ttu-id="89831-103">資料集欄位是欄位名稱的內建集合，代表資料集查詢在外部資料來源上執行時所傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="89831-103">Dataset fields are the built-in collection of field names that represent the data that is returned when a dataset query runs on an external data source.</span></span>  
  
 <span data-ttu-id="89831-104">如果是內嵌資料集，資料集欄位就是當您建立查詢並關閉 [查詢設計工具] 窗格之後所建立的欄位，以及您所建立的導出欄位。</span><span class="sxs-lookup"><span data-stu-id="89831-104">For an embedded dataset, the dataset fields are the fields that are created after you finish building a query and close the Query Designer pane, and calculated fields that you create.</span></span>  
  
 <span data-ttu-id="89831-105">如果是共用資料集，資料集欄位就是當您將共用資料集定義加入至報表時，該定義中的欄位。</span><span class="sxs-lookup"><span data-stu-id="89831-105">For a shared dataset, the dataset fields are the fields from the shared dataset definition when you added it to your report.</span></span> <span data-ttu-id="89831-106">雖然當您執行報表時，一定會使用報表伺服器上共用資料集中的查詢，但是報表中的資料集欄位清單是靜態的。</span><span class="sxs-lookup"><span data-stu-id="89831-106">Although the query from the shared dataset on the report server is always used when you run the report, the list of dataset fields in the report is static.</span></span>  
  
 <span data-ttu-id="89831-107">使用 **[重新整理欄位]** 來更新報表中的欄位清單，以符合共用資料集查詢中的目前欄位清單。</span><span class="sxs-lookup"><span data-stu-id="89831-107">Use **Refresh Fields** to update the list of fields in the report to match the current list of fields from the shared dataset query.</span></span> <span data-ttu-id="89831-108">重新整理此欄位清單並不會影響您在報表內定義的導出欄位。</span><span class="sxs-lookup"><span data-stu-id="89831-108">Refreshing the field list does not affect the calculated fields that you define in your report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-query-field"></a><span data-ttu-id="89831-109">若要加入查詢欄位</span><span class="sxs-lookup"><span data-stu-id="89831-109">To add a query field</span></span>  
  
1.  <span data-ttu-id="89831-110">在 [報表資料] 窗格中，以滑鼠右鍵按一下資料集，然後按一下 [新增查詢欄位]  。</span><span class="sxs-lookup"><span data-stu-id="89831-110">In the Report Data pane, right-click the dataset, and then click **Add Query Field**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="89831-111">如果您看不到 [報表資料] 窗格，請按一下 [檢視]  功能表上的 [報表資料]  。</span><span class="sxs-lookup"><span data-stu-id="89831-111">If you cannot see the Report Data pane, from the **View** menu, click **Report Data**.</span></span>  
  
2.  <span data-ttu-id="89831-112">在 **[資料集屬性]** 對話方塊的 **[欄位]** 頁面上，按一下 **[加入]** ，然後按一下 **[查詢欄位]** 。</span><span class="sxs-lookup"><span data-stu-id="89831-112">In the **Fields** page of the **Dataset Properties** dialog box, click **Add**, and then click **Query Field**.</span></span> <span data-ttu-id="89831-113">新的資料列就會加入方格的底部。</span><span class="sxs-lookup"><span data-stu-id="89831-113">A new row is added to the bottom of the grid.</span></span>  
  
3.  <span data-ttu-id="89831-114">在 **[欄位名稱]** 文字方塊中，輸入欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="89831-114">In the **Field Name** text box, type the name for the field.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="89831-115">名稱在資料集內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="89831-115">Names must be unique in the dataset.</span></span>  
  
4.  <span data-ttu-id="89831-116">在 **[欄位來源]** 文字方塊中，輸入資料來源上現有欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="89831-116">In the **Field Source** text box, type the name of an existing field on the data source.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-add-a-calculated-field"></a><span data-ttu-id="89831-117">加入導出欄位</span><span class="sxs-lookup"><span data-stu-id="89831-117">To add a calculated field</span></span>  
  
1.  <span data-ttu-id="89831-118">在 [報表資料] 窗格中，以滑鼠右鍵按一下資料集，然後按一下 [新增導出欄位]  。</span><span class="sxs-lookup"><span data-stu-id="89831-118">In the Report Data pane, right-click the dataset, and then click **Add Calculated Field**.</span></span>  
  
2.  <span data-ttu-id="89831-119">在 **[資料集屬性]** 對話方塊的 **[欄位]** 頁面上，按一下 **[加入]** ，然後按一下 **[導出欄位]** 。</span><span class="sxs-lookup"><span data-stu-id="89831-119">In the **Fields** page of the **Dataset Properties** dialog box, click **Add**, and then click **Calculated Field**.</span></span> <span data-ttu-id="89831-120">新的資料列就會加入方格的底部。</span><span class="sxs-lookup"><span data-stu-id="89831-120">A new row is added to the bottom of the grid.</span></span>  
  
3.  <span data-ttu-id="89831-121">在 **[欄位名稱]** 文字方塊中，輸入欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="89831-121">In the **Field Name** text bo, type the name for the field.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="89831-122">名稱在資料集內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="89831-122">Names must be unique in the dataset.</span></span>  
  
4.  <span data-ttu-id="89831-123">在 **[欄位來源]** 文字方塊中，輸入欄位的運算式。</span><span class="sxs-lookup"><span data-stu-id="89831-123">In the **Field Source** text box, type the expression for the field.</span></span> <span data-ttu-id="89831-124">按一下運算式 (**fx**) 按鈕，即可建立運算式。</span><span class="sxs-lookup"><span data-stu-id="89831-124">Click the expression (**fx**) button to build an expression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="89831-125">導出欄位的運算式不能包含報表項目的彙總或參考。</span><span class="sxs-lookup"><span data-stu-id="89831-125">The expression for a calculated field cannot contain aggregates or references to report items.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-edit-a-query-field-or-a-dataset-field"></a><span data-ttu-id="89831-126">編輯查詢欄位或資料集欄位</span><span class="sxs-lookup"><span data-stu-id="89831-126">To edit a query field or a dataset field</span></span>  
  
1.  <span data-ttu-id="89831-127">在 [報表資料] 窗格中，以滑鼠右鍵按一下欄位，然後按一下 [欄位屬性]  。</span><span class="sxs-lookup"><span data-stu-id="89831-127">In the Report Data pane, right-click the field, and then click **Field Properties**.</span></span>  
  
2.  <span data-ttu-id="89831-128">在 **[資料集屬性]** 對話方塊的 **[欄位]** 頁面上，按一下現有的欄位來選取資料列。</span><span class="sxs-lookup"><span data-stu-id="89831-128">In the **Fields** page of the **Dataset Properties** dialog box, click an existing field to select the row.</span></span>  
  
3.  <span data-ttu-id="89831-129">變更欄位的名稱或欄位的值。</span><span class="sxs-lookup"><span data-stu-id="89831-129">Change the name of the field or the value of the field.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-query-field-or-a-calculated-field"></a><span data-ttu-id="89831-130">刪除查詢欄位或導出欄位</span><span class="sxs-lookup"><span data-stu-id="89831-130">To delete a query field or a calculated field</span></span>  
  
1.  <span data-ttu-id="89831-131">在 [報表資料] 窗格中，展開資料集來顯示欄位集合。</span><span class="sxs-lookup"><span data-stu-id="89831-131">In the Report Data pane, expand the dataset to display the field collection.</span></span>  
  
2.  <span data-ttu-id="89831-132">以滑鼠右鍵按一下您要移除的欄位，然後按一下 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="89831-132">Right-click the field you want to remove, and then click **Delete**.</span></span>  
  
### <a name="to-refresh-the-field-collection-in-the-report-data-pane-for-a-shared-dataset"></a><span data-ttu-id="89831-133">若要在 [報表資料] 窗格中重新整理共用資料集的欄位集合</span><span class="sxs-lookup"><span data-stu-id="89831-133">To refresh the field collection in the Report Data Pane for a shared dataset</span></span>  
  
1.  <span data-ttu-id="89831-134">在 [報表資料] 窗格中，以滑鼠右鍵按一下資料集，然後按一下 [查詢]  。</span><span class="sxs-lookup"><span data-stu-id="89831-134">In the Report Data pane, right-click the dataset, and then click **Query**.</span></span>  
  
2.  <span data-ttu-id="89831-135">按一下 **[重新整理欄位]** 。</span><span class="sxs-lookup"><span data-stu-id="89831-135">Click **Refresh Fields**.</span></span>  
  
     <span data-ttu-id="89831-136">在報表伺服器上，共用資料集查詢會執行並傳回目前的欄位集合。</span><span class="sxs-lookup"><span data-stu-id="89831-136">On the report server, the shared dataset query runs and returns the current field collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89831-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89831-137">See Also</span></span>  
 <span data-ttu-id="89831-138">[資料集欄位集合 &#40;報表產生器及 SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="89831-138">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="89831-139">[將資料加入報表 &#40;報表產生器和 SSRS&#41;](report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="89831-139">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="89831-140">[報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="89831-140">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="89831-141">[Reporting Services 查詢設計工具](../reporting-services-query-designers.md) </span><span class="sxs-lookup"><span data-stu-id="89831-141">[Reporting Services Query Designers](../reporting-services-query-designers.md) </span></span>  
 [<span data-ttu-id="89831-142">查詢設計工具 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="89831-142">Query Designers &#40;Report Builder&#41;</span></span>](../query-designers-report-builder.md)  
  
  
