---
title: " (SSAS) 的 [編輯資料表屬性] 對話方塊 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.edittablepropdb.f1
ms.assetid: 8d913e83-7246-44cc-8fc7-31729023c0d8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6664d244f5f653610b37bd628abdb2263e015c0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599241"
---
# <a name="edit-table-properties-dialog-box-ssas"></a><span data-ttu-id="81ace-102">編輯資料表屬性對話方塊 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="81ace-102">Edit Table Properties Dialog Box (SSAS)</span></span>
  <span data-ttu-id="81ace-103">**[編輯資料表屬性]** 對話方塊可讓您檢視與修改使用 [資料表匯入精靈] 匯入至模型設計師之資料表的屬性。</span><span class="sxs-lookup"><span data-stu-id="81ace-103">The **Edit Table Properties** dialog box enables you to view and modify the properties of tables that are imported into the model designer by using the Table Import Wizard.</span></span> <span data-ttu-id="81ace-104">若要存取此對話方塊，請在模型設計師中選取資料表，然後按一下 **[資料表]** 功能表，再按一下 **[資料表屬性]**。</span><span class="sxs-lookup"><span data-stu-id="81ace-104">To access this dialog box, in the model designer, select a table, then click the **Table** menu, and then click **Table Properties**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="81ace-105">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="81ace-105">UI element list</span></span>  
 <span data-ttu-id="81ace-106">依您一開始是透過從清單中選取資料表或使用 SQL 查詢匯入資料，此對話方塊的選項都不同。</span><span class="sxs-lookup"><span data-stu-id="81ace-106">The options for this dialog box are different depending on whether you originally imported data by selecting tables from a list or by using a SQL query.</span></span>  
  
## <a name="table-preview-mode"></a><span data-ttu-id="81ace-107">資料表預覽模式</span><span class="sxs-lookup"><span data-stu-id="81ace-107">Table Preview Mode</span></span>  
 <span data-ttu-id="81ace-108">**資料表名稱**</span><span class="sxs-lookup"><span data-stu-id="81ace-108">**Table name**</span></span>  
 <span data-ttu-id="81ace-109">顯示模型中資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="81ace-109">Displays the name of the data table in the model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="81ace-110">您無法在此處編輯名稱。</span><span class="sxs-lookup"><span data-stu-id="81ace-110">You cannot edit the name here.</span></span> <span data-ttu-id="81ace-111">不過，您可以在模型設計師底部的資料表索引標籤上按一下滑鼠右鍵，來變更資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="81ace-111">However, you can change the name of the table by right-clicking the table tab at the bottom of the model designer.</span></span>  
  
 <span data-ttu-id="81ace-112">**連線名稱**</span><span class="sxs-lookup"><span data-stu-id="81ace-112">**Connection name**</span></span>  
 <span data-ttu-id="81ace-113">顯示目前正在使用之連接的名稱。</span><span class="sxs-lookup"><span data-stu-id="81ace-113">Displays the name of the connection that is currently in use.</span></span>  
  
 <span data-ttu-id="81ace-114">**來源名稱**</span><span class="sxs-lookup"><span data-stu-id="81ace-114">**Source name**</span></span>  
 <span data-ttu-id="81ace-115">顯示或變更從中取得資料的資料表。</span><span class="sxs-lookup"><span data-stu-id="81ace-115">Display or change the table from which the data is obtained.</span></span>  
  
 <span data-ttu-id="81ace-116">如果您將來源變更為具有與目前資料表不同之資料行的資料表，就會顯示資料行不同的警告訊息。</span><span class="sxs-lookup"><span data-stu-id="81ace-116">If you change the source to a table that has different columns than the current table, a message is displayed warning that the columns are different.</span></span> <span data-ttu-id="81ace-117">然後，您必須選取要放入目前資料表中的資料行，並按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="81ace-117">You must then select the columns that you want to put in the current table and click **Save**.</span></span> <span data-ttu-id="81ace-118">您可以選取資料表左邊的核取方塊，以取代整個資料表。</span><span class="sxs-lookup"><span data-stu-id="81ace-118">You can replace the entire table by selecting the check box at the left of the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="81ace-119">當您變更資料表的資料來源時，基本上是以新來源資料表的內容取代目前資料表的內容。</span><span class="sxs-lookup"><span data-stu-id="81ace-119">When you change the data source of a table, you essentially replace the contents of the current table with the contents of the new source table.</span></span>  
  
 <span data-ttu-id="81ace-120">**資料行名稱來自**</span><span class="sxs-lookup"><span data-stu-id="81ace-120">**Column names from**</span></span>  
 |||  
|-|-|  
|<span data-ttu-id="81ace-121">**Source**</span><span class="sxs-lookup"><span data-stu-id="81ace-121">**Source**</span></span>|<span data-ttu-id="81ace-122">選取此選項，以所選來源資料表的資料行名稱取代目前的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="81ace-122">Select this option to replace the current column names with the column names from the selected source table.</span></span>|  
|<span data-ttu-id="81ace-123">**型號**</span><span class="sxs-lookup"><span data-stu-id="81ace-123">**Model**</span></span>|<span data-ttu-id="81ace-124">選取此選項，以使用目前資料行在模型中顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="81ace-124">Select this option to use the current column names as they exist in the model.</span></span>|  
  
 <span data-ttu-id="81ace-125">**重新整理預覽**</span><span class="sxs-lookup"><span data-stu-id="81ace-125">**Refresh preview**</span></span>  
 <span data-ttu-id="81ace-126">按一下以檢視目前所選來源資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="81ace-126">Click to view the columns of data in the currently selected source table.</span></span>  
  
 <span data-ttu-id="81ace-127">**切換到**</span><span class="sxs-lookup"><span data-stu-id="81ace-127">**Switch to**</span></span>  
 |||  
|-|-|  
|<span data-ttu-id="81ace-128">**資料表預覽**</span><span class="sxs-lookup"><span data-stu-id="81ace-128">**Table preview**</span></span>|<span data-ttu-id="81ace-129">選取此選項，以預覽所選資料表及有限數目的資料列。</span><span class="sxs-lookup"><span data-stu-id="81ace-129">Select this option to preview the selected table and a limited number of rows of data.</span></span>|  
|<span data-ttu-id="81ace-130">**查詢編輯器**</span><span class="sxs-lookup"><span data-stu-id="81ace-130">**Query editor**</span></span>|<span data-ttu-id="81ace-131">選取此選項，以檢視對所選資料來源執行的查詢。</span><span class="sxs-lookup"><span data-stu-id="81ace-131">Select this option to view the query against the selected data source.</span></span> <span data-ttu-id="81ace-132">並非所有的資料來源都可使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="81ace-132">This option is not available for all data sources.</span></span>|  
  
 <span data-ttu-id="81ace-133">**資料行標頭中的核取方塊**</span><span class="sxs-lookup"><span data-stu-id="81ace-133">**Checkbox in the column header**</span></span>  
 <span data-ttu-id="81ace-134">選取核取方塊可將資料行納入資料匯入作業。</span><span class="sxs-lookup"><span data-stu-id="81ace-134">Select the checkbox to include the column in the data import.</span></span> <span data-ttu-id="81ace-135">清除核取方塊可從資料匯入作業排除資料行。</span><span class="sxs-lookup"><span data-stu-id="81ace-135">Clear the checkbox to remove the column from the data import.</span></span>  
  
 <span data-ttu-id="81ace-136">**資料行標頭中的向下箭號按鈕**</span><span class="sxs-lookup"><span data-stu-id="81ace-136">**Down-arrow button in the column header**</span></span>  
 <span data-ttu-id="81ace-137">篩選資料行中的資料。</span><span class="sxs-lookup"><span data-stu-id="81ace-137">Filter data in the column.</span></span>  
  
 <span data-ttu-id="81ace-138">**清除資料列篩選**</span><span class="sxs-lookup"><span data-stu-id="81ace-138">**Clear row filters**</span></span>  
 <span data-ttu-id="81ace-139">按一下以移除任何已套用的篩選。</span><span class="sxs-lookup"><span data-stu-id="81ace-139">Click to remove any filters that have been applied.</span></span>  
  
 <span data-ttu-id="81ace-140">**確定**</span><span class="sxs-lookup"><span data-stu-id="81ace-140">**OK**</span></span>  
 <span data-ttu-id="81ace-141">按一下以套用所做的全部變更，包括取代資料行。</span><span class="sxs-lookup"><span data-stu-id="81ace-141">Click to apply all changes that you made, including replacing columns.</span></span>  
  
## <a name="query-design-mode"></a><span data-ttu-id="81ace-142">查詢設計模式</span><span class="sxs-lookup"><span data-stu-id="81ace-142">Query Design Mode</span></span>  
 <span data-ttu-id="81ace-143">**資料表名稱**</span><span class="sxs-lookup"><span data-stu-id="81ace-143">**Table name**</span></span>  
 <span data-ttu-id="81ace-144">顯示模型中資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="81ace-144">Displays the name of the data table in the model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="81ace-145">您無法在此編輯名稱，但是可以滑鼠右鍵按一下設計師底部的資料表索引標籤來變更資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="81ace-145">You cannot edit the name here; however, you can change the name of the table by right-clicking the table tab at the bottom of the designer.</span></span>  
  
 <span data-ttu-id="81ace-146">**連線名稱**</span><span class="sxs-lookup"><span data-stu-id="81ace-146">**Connection name**</span></span>  
 <span data-ttu-id="81ace-147">顯示目前正在使用之連接的名稱。</span><span class="sxs-lookup"><span data-stu-id="81ace-147">Displays the name of the connection that is currently in use.</span></span>  
  
 <span data-ttu-id="81ace-148">**切換到**</span><span class="sxs-lookup"><span data-stu-id="81ace-148">**Switch to**</span></span>  
 |||  
|-|-|  
|<span data-ttu-id="81ace-149">**資料表預覽**</span><span class="sxs-lookup"><span data-stu-id="81ace-149">**Table preview**</span></span>|<span data-ttu-id="81ace-150">選取此選項，以預覽所選資料表及少數資料列。</span><span class="sxs-lookup"><span data-stu-id="81ace-150">Select this option to preview the selected table and a few rows of data.</span></span>|  
|<span data-ttu-id="81ace-151">**查詢編輯器**</span><span class="sxs-lookup"><span data-stu-id="81ace-151">**Query editor**</span></span>|<span data-ttu-id="81ace-152">選取此選項，以檢視將對所選資料來源發出的查詢。</span><span class="sxs-lookup"><span data-stu-id="81ace-152">Select this option to view the query that will be issued against the selected data source.</span></span>|  
  
 <span data-ttu-id="81ace-153">**Sql 語句**</span><span class="sxs-lookup"><span data-stu-id="81ace-153">**Sql statement**</span></span>  
 <span data-ttu-id="81ace-154">顯示依目前資料來源發出以擷取資料列的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="81ace-154">Displays the SQL statement that is issued against the current data source to retrieve rows.</span></span> <span data-ttu-id="81ace-155">在預設情況下會擷取所有資料列，但是您可以設計篩選器或以手動方式編輯 SQL 陳述式，只擷取資料列的子集。</span><span class="sxs-lookup"><span data-stu-id="81ace-155">By default, all rows are retrieved, but you can retrieve a subset of rows, either by designing a filter, or by manually editing the SQL statement.</span></span>  
  
 <span data-ttu-id="81ace-156">**驗證**</span><span class="sxs-lookup"><span data-stu-id="81ace-156">**Validate**</span></span>  
 <span data-ttu-id="81ace-157">按一下以針對所選資料來源和提供者，驗證陳述式的語法是否正確。</span><span class="sxs-lookup"><span data-stu-id="81ace-157">Click to verify that the statement is syntactically correct for the selected data source and provider.</span></span>  
  
 <span data-ttu-id="81ace-158">**設計**</span><span class="sxs-lookup"><span data-stu-id="81ace-158">**Design**</span></span>  
 <span data-ttu-id="81ace-159">按一下以開啟視覺化查詢設計工具，並建立查詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="81ace-159">Click to open a visual query designer and build a query statement.</span></span> <span data-ttu-id="81ace-160">如需有關如何使用設計工具的詳細資訊，請從設計工具按 F1。</span><span class="sxs-lookup"><span data-stu-id="81ace-160">For information about how to use the designer, press F1 from the designer.</span></span>  
  
 <span data-ttu-id="81ace-161">**確定**</span><span class="sxs-lookup"><span data-stu-id="81ace-161">**OK**</span></span>  
 <span data-ttu-id="81ace-162">按一下以套用所做的全部變更，包括取代資料行。</span><span class="sxs-lookup"><span data-stu-id="81ace-162">Click to apply all changes that you made, including replacing columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81ace-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81ace-163">See Also</span></span>  
 [<span data-ttu-id="81ace-164">資料表與資料行 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="81ace-164">Tables and Columns &#40;SSAS Tabular&#41;</span></span>](tabular-models/tables-and-columns-ssas-tabular.md)  
  
  
