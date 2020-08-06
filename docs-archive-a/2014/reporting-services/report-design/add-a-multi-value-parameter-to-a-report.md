---
title: 將多值參數新增至報表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 12ad0e77-4c28-4bbb-ab11-473ae89ec9f1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5269293b6a21f3b1d82eb6835efbd275e3be9620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687481"
---
# <a name="add-a-multi-value-parameter-to-a-report"></a><span data-ttu-id="0a383-102">將多值參數加入至報表</span><span class="sxs-lookup"><span data-stu-id="0a383-102">Add a multi-value parameter to a Report</span></span>
  <span data-ttu-id="0a383-103">您可以在報表中新增參數，好讓使用者可以為參數選取多個值。</span><span class="sxs-lookup"><span data-stu-id="0a383-103">You can add a parameter to a report that allows the user to select more than one value for the parameter.</span></span>  
  
 <span data-ttu-id="0a383-104">您可以將多個參數值傳遞給報表 URL 中的報表。</span><span class="sxs-lookup"><span data-stu-id="0a383-104">You can pass multiple parameter values to the report within the report URL.</span></span> <span data-ttu-id="0a383-105">如需包含多值參數的 URL 範例，請參閱 [在 URL 內傳遞報表參數](../pass-a-report-parameter-within-a-url.md)。</span><span class="sxs-lookup"><span data-stu-id="0a383-105">For a URL example includes a multi-value parameter, see [Pass a Report Parameter Within a URL](../pass-a-report-parameter-within-a-url.md).</span></span>  
  
 <span data-ttu-id="0a383-106">如需如何將多個參數值傳遞給預存程序的詳細資訊，請參閱 mssqltips.com 上的 [為 SSRS 報表處理複選參數](https://go.microsoft.com/fwlink/?LinkId=321529) 。</span><span class="sxs-lookup"><span data-stu-id="0a383-106">For information on how to pass multiple parameter values to a stored procedure, see [Working With Multi-Select Parameters for SSRS Reports](https://go.microsoft.com/fwlink/?LinkId=321529) on mssqltips.com.</span></span>  
  
### <a name="to-add-a-multi-value-parameter"></a><span data-ttu-id="0a383-107">若要加入多值參數</span><span class="sxs-lookup"><span data-stu-id="0a383-107">To add a multi-value parameter</span></span>  
  
1.  <span data-ttu-id="0a383-108">在「報表產生器」中，開啟您要加入多值參數的報表。</span><span class="sxs-lookup"><span data-stu-id="0a383-108">In Report Builder, open the report that you want to add the multi-value parameter to.</span></span>  
  
2.  <span data-ttu-id="0a383-109">以滑鼠右鍵按一下報表資料集，然後按一下 [資料集屬性] </span><span class="sxs-lookup"><span data-stu-id="0a383-109">Right-click the report dataset, and then click **Dataset Properties**</span></span>  
  
3.  <span data-ttu-id="0a383-110">將變數加入至資料集查詢，其方式是在 **[查詢]** 方塊中編輯查詢文字或是使用查詢設計工具來加入篩選。</span><span class="sxs-lookup"><span data-stu-id="0a383-110">Add a variable to the dataset query by either editing the query text in the **Query** box, or by adding a filter by using the query designer.</span></span> <span data-ttu-id="0a383-111">如需詳細資訊，請參閱[在關聯式查詢設計工具中建立查詢 &#40;報表產生器和 SSRS&#41;](../report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="0a383-111">For more information, see [Build a Query in the Relational Query Designer &#40;Report Builder and SSRS&#41;](../report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="0a383-112">查詢文字的查詢變數不能包含 DECLARE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="0a383-112">The query text must not include the DECLARE statement for the query variable.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="0a383-113">查詢變數的文字必須包含 `IN` 運算子，如以下範例所示。</span><span class="sxs-lookup"><span data-stu-id="0a383-113">The text for the query variable must include the `IN` operator, as shown in the following example.</span></span>  
  
    ```  
    WHERE  
      Production.ProductInventory.ProductID IN (@ProductID)  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="0a383-114">如果您未如上面所示在變數前後加上括弧，報表將無法轉譯，而且會顯示「必須宣告純量變數」錯誤。</span><span class="sxs-lookup"><span data-stu-id="0a383-114">If you don't include the parentheses around the variable as shown above, the report fails to render and the "must declare the scalar variable" error is displayed.</span></span>  
  
     <span data-ttu-id="0a383-115">系統會針對查詢變數自動建立內嵌資料集或共用資料集的資料集參數。</span><span class="sxs-lookup"><span data-stu-id="0a383-115">A dataset parameter for an embedded dataset or a shared dataset is created automatically for the query variable.</span></span> <span data-ttu-id="0a383-116">系統會自動針對資料集參數建立報表參數。</span><span class="sxs-lookup"><span data-stu-id="0a383-116">A report parameter is created automatically for the dataset parameter.</span></span>  
  
4.  <span data-ttu-id="0a383-117">在 [報表資料]\*\*\*\* 窗格中展開 [參數]\*\*\*\* 節點，並以滑鼠右鍵按一下為資料集參數自動建立的報表參數，然後按一下 [參數屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0a383-117">In the **Report Data** pane, expand the **Parameters** node, right-click the report parameter that was automatically created for the dataset parameter, and then click **Parameter Properties**.</span></span>  
  
5.  <span data-ttu-id="0a383-118">在 **[一般]** 索引標籤上選取 **[允許多個值]** ，允許使用者針對參數選取多個值。</span><span class="sxs-lookup"><span data-stu-id="0a383-118">In the **General** tab, select **Allow multiple values** to allow a user to select more than one value for the parameter.</span></span>  
  
6.  <span data-ttu-id="0a383-119">(選擇性) 在 [可用的值]\*\*\*\* 索引標籤中，指定要對使用者顯示的可用值清單。</span><span class="sxs-lookup"><span data-stu-id="0a383-119">(Optionally) In the **Available** values tab, specify a list of available values to display to the user.</span></span>  
  
     <span data-ttu-id="0a383-120">可用值清單會將使用者可以做的選擇限制為參數的有效值。</span><span class="sxs-lookup"><span data-stu-id="0a383-120">An available values list limits the choices a user can make to only valid values for the parameter.</span></span> <span data-ttu-id="0a383-121">如果是多個值，清單的最開頭是 **[全選]** 功能，好讓使用者只需按一下就可以選取或清除所有值。</span><span class="sxs-lookup"><span data-stu-id="0a383-121">For multiple values, the top of list begins with a **Select All** feature so the user can select or clear all values with a single click.</span></span> <span data-ttu-id="0a383-122">如果您選擇從資料集查詢取得報表參數的可用值，請確定選取的資料集不能包含與相同報表參數有關聯的查詢變數。</span><span class="sxs-lookup"><span data-stu-id="0a383-122">If you choose to get the available values for the report parameter from a dataset query, be sure to select a dataset that does not contain the query variable that is associated with the same report parameter.</span></span>  
  
     <span data-ttu-id="0a383-123">如需詳細資訊，請參閱[為報表參數新增、變更或刪除可用的值 &#40;報表產生器和 SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md)。</span><span class="sxs-lookup"><span data-stu-id="0a383-123">For more information, see [Add, Change, or Delete Available Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md).</span></span>  
  
### <a name="to-add-a-multi-value-parameter"></a><span data-ttu-id="0a383-124">若要加入多值參數</span><span class="sxs-lookup"><span data-stu-id="0a383-124">To add a multi-value parameter</span></span>  
  
1.  <span data-ttu-id="0a383-125">在「報表產生器」中，開啟您要加入多值參數的報表。</span><span class="sxs-lookup"><span data-stu-id="0a383-125">In Report Builder, open the report that you want to add the multi-value parameter to.</span></span>  
  
2.  <span data-ttu-id="0a383-126">以滑鼠右鍵按一下報表資料集，然後按一下 [資料集屬性]\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="0a383-126">Right-click the report dataset, and then click **Dataset Properties**</span></span>  
  
3.  <span data-ttu-id="0a383-127">將變數加入至資料集查詢，其方式是在 **[查詢]** 方塊中編輯查詢文字或是使用查詢設計工具來加入篩選。</span><span class="sxs-lookup"><span data-stu-id="0a383-127">Add a variable to the dataset query by either editing the query text in the **Query** box, or by adding a filter by using the query designer.</span></span> <span data-ttu-id="0a383-128">如需詳細資訊，請參閱[在關聯式查詢設計工具中建立查詢 &#40;報表產生器和 SSRS&#41;](../report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="0a383-128">For more information, see [Build a Query in the Relational Query Designer &#40;Report Builder and SSRS&#41;](../report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="0a383-129">查詢文字的查詢變數不能包含 DECLARE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="0a383-129">The query text must not include the DECLARE statement for the query variable.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="0a383-130">查詢變數的文字必須包含 `IN` 運算子，如以下範例所示。</span><span class="sxs-lookup"><span data-stu-id="0a383-130">The text for the query variable must include the `IN` operator, as shown in the following example.</span></span>  
  
    ```  
    WHERE  
      Production.ProductInventory.ProductID IN (@ProductID)  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="0a383-131">如果您未如上面所示在變數前後加上括弧，報表將無法轉譯，而且會顯示「必須宣告純量變數」錯誤。</span><span class="sxs-lookup"><span data-stu-id="0a383-131">If you don't include the parentheses around the variable as shown above, the report fails to render and the "must declare the scalar variable" error is displayed.</span></span>  
  
     <span data-ttu-id="0a383-132">系統會針對查詢變數自動建立內嵌資料集或共用資料集的資料集參數。</span><span class="sxs-lookup"><span data-stu-id="0a383-132">A dataset parameter for an embedded dataset or a shared dataset is created automatically for the query variable.</span></span> <span data-ttu-id="0a383-133">系統會自動針對資料集參數建立報表參數。</span><span class="sxs-lookup"><span data-stu-id="0a383-133">A report parameter is created automatically for the dataset parameter.</span></span>  
  
4.  <span data-ttu-id="0a383-134">在 [報表資料]\*\*\*\* 窗格中展開 [參數]\*\*\*\* 節點，並以滑鼠右鍵按一下為資料集參數自動建立的報表參數，然後按一下 [參數屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0a383-134">In the **Report Data** pane, expand the **Parameters** node, right-click the report parameter that was automatically created for the dataset parameter, and then click **Parameter Properties**.</span></span>  
  
5.  <span data-ttu-id="0a383-135">在 **[一般]** 索引標籤上選取 **[允許多個值]** ，允許使用者針對參數選取多個值。</span><span class="sxs-lookup"><span data-stu-id="0a383-135">In the **General** tab, select **Allow multiple values** to allow a user to select more than one value for the parameter.</span></span>  
  
6.  <span data-ttu-id="0a383-136">(選擇性) 在 [可用的值]\*\*\*\* 索引標籤中，指定要對使用者顯示的可用值清單。</span><span class="sxs-lookup"><span data-stu-id="0a383-136">(Optionally) In the **Available** values tab, specify a list of available values to display to the user.</span></span>  
  
     <span data-ttu-id="0a383-137">可用值清單會將使用者可以做的選擇限制為參數的有效值。</span><span class="sxs-lookup"><span data-stu-id="0a383-137">An available values list limits the choices a user can make to only valid values for the parameter.</span></span> <span data-ttu-id="0a383-138">如果是多個值，清單的最開頭是 **[全選]** 功能，好讓使用者只需按一下就可以選取或清除所有值。</span><span class="sxs-lookup"><span data-stu-id="0a383-138">For multiple values, the top of list begins with a **Select All** feature so the user can select or clear all values with a single click.</span></span> <span data-ttu-id="0a383-139">如果您選擇從資料集查詢取得報表參數的可用值，請確定選取的資料集不能包含與相同報表參數有關聯的查詢變數。</span><span class="sxs-lookup"><span data-stu-id="0a383-139">If you choose to get the available values for the report parameter from a dataset query, be sure to select a dataset that does not contain the query variable that is associated with the same report parameter.</span></span>  
  
     <span data-ttu-id="0a383-140">如需詳細資訊，請參閱[為報表參數新增、變更或刪除可用的值 &#40;報表產生器和 SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md)。</span><span class="sxs-lookup"><span data-stu-id="0a383-140">For more information, see [Add, Change, or Delete Available Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a383-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a383-141">See Also</span></span>  
 <span data-ttu-id="0a383-142">[將串聯參數加入至報表 &#40;報表產生器和 SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0a383-142">[Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="0a383-143">加入、變更或刪除報表參數 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="0a383-143">Add, Change, or Delete a Report Parameter &#40;Report Builder and SSRS&#41;</span></span>](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)  
  
  
