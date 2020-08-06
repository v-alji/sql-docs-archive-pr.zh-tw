---
title: 使用資料列篩選器來執行動態安全性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8bf03c45-caf5-4eda-9314-e4f8f24a159f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 09a15f818f57d7a9d808c89ced41b285536a7883
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585718"
---
# <a name="implement-dynamic-security-by-using-row-filters"></a><span data-ttu-id="33825-102">使用資料列篩選器實作動態安全性</span><span class="sxs-lookup"><span data-stu-id="33825-102">Implement Dynamic Security by Using Row Filters</span></span>
  <span data-ttu-id="33825-103">在這個補充課程中，您將建立實作動態安全性的其他角色。</span><span class="sxs-lookup"><span data-stu-id="33825-103">In this supplemental lesson, you will create an additional role that implements dynamic security.</span></span> <span data-ttu-id="33825-104">動態安全性會根據目前登入使用者的使用者名稱或登入識別碼來提供資料列層級安全性。</span><span class="sxs-lookup"><span data-stu-id="33825-104">Dynamic security provides row-level security based on the user name or login id of the user currently logged on.</span></span> <span data-ttu-id="33825-105">如需詳細資訊，請參閱[角色 &#40;SSAS 表格式&#41;](https://docs.microsoft.com/analysis-services/tabular-models/roles-ssas-tabular)。</span><span class="sxs-lookup"><span data-stu-id="33825-105">To learn more, see [Roles &#40;SSAS Tabular&#41;](https://docs.microsoft.com/analysis-services/tabular-models/roles-ssas-tabular).</span></span>  
  
 <span data-ttu-id="33825-106">若要實作動態安全性，您必須將資料表加入至包含 Windows 使用者名稱的模型，這些使用者可以建立與模型的連接做為資料來源並且瀏覽模型物件與資料。</span><span class="sxs-lookup"><span data-stu-id="33825-106">To implement dynamic security, you must add a table to your model containing the Windows user names of those users that can create a connection to the model as a data source and browse model objects and data.</span></span> <span data-ttu-id="33825-107">您使用本教學課程建立的模型位於 Adventure Works Corp. 內容中；不過為了完成本課程，您必須加入包含您自己的網域使用者的資料表。</span><span class="sxs-lookup"><span data-stu-id="33825-107">The model you create using this tutorial is in the context of Adventure Works Corp.; however, in order to complete this lesson, you must add a table containing users from your own domain.</span></span> <span data-ttu-id="33825-108">您將不需要所加入使用者名稱的密碼。</span><span class="sxs-lookup"><span data-stu-id="33825-108">You will not need the passwords for the user names that will be added.</span></span> <span data-ttu-id="33825-109">若要 Employee Security 資料表，其中包含幾個您網域中的範例使用者，您將使用 [貼上] 功能從 Excel 試算表貼入員工資料。</span><span class="sxs-lookup"><span data-stu-id="33825-109">To create an Employee Security table, with a small sample of users from your own domain, you will use the Paste feature, pasting employee data from an Excel spreadsheet.</span></span> <span data-ttu-id="33825-110">在真實情況中，包含您加入模型中之使用者名稱的資料表通常會使用來自實際資料庫的資料表做為資料來源；例如，實際的 dimEmployee 資料表。</span><span class="sxs-lookup"><span data-stu-id="33825-110">In a real-world scenario, the table containing user names you add to a model would typically use a table from an actual database as a data source; for example, a real dimEmployee table.</span></span>  
  
 <span data-ttu-id="33825-111">為了實現動態安全性，您將使用兩個新的 DAX 函數： [USERNAME 函數 &#40;dax&#41;](/dax/username-function-dax)和[LOOKUPVALUE 函數 &#40;dax&#41;](/dax/lookupvalue-function-dax)。</span><span class="sxs-lookup"><span data-stu-id="33825-111">In order to implement dynamic security, you will use two new DAX functions: [USERNAME Function &#40;DAX&#41;](/dax/username-function-dax) and [LOOKUPVALUE Function &#40;DAX&#41;](/dax/lookupvalue-function-dax).</span></span> <span data-ttu-id="33825-112">套用於資料列篩選公式的這些函式，會以新的角色定義。</span><span class="sxs-lookup"><span data-stu-id="33825-112">These functions, applied in a row filter formula, are defined in a new role.</span></span> <span data-ttu-id="33825-113">該公式會使用 LOOKUPVALUE 函數從 Employee Security 資料表指定一個值，然後將該值傳遞給 USERNAME 函數，此函數會指定登錄使用者的使用者名稱屬於此角色。</span><span class="sxs-lookup"><span data-stu-id="33825-113">Using the LOOKUPVALUE function, the formula specifies a value from the Employee Security table and then passes that value to the USERNAME function, which specifies the user name of the user logged on belongs to this role.</span></span> <span data-ttu-id="33825-114">然後，使用者可以只流覽角色的資料列篩選所指定的資料。</span><span class="sxs-lookup"><span data-stu-id="33825-114">The user can then browse only data specified by the role's row filters.</span></span> <span data-ttu-id="33825-115">在這個案例中，您將指定銷售員工只能瀏覽本身所屬銷售地區的網際網路銷售資料。</span><span class="sxs-lookup"><span data-stu-id="33825-115">In this scenario, you will specify that sales employees can only browse internet sales data for the sales territories in which they are a member.</span></span>  
  
 <span data-ttu-id="33825-116">您將要完成一系列工作，才能完成這個補充課程。</span><span class="sxs-lookup"><span data-stu-id="33825-116">In order to complete this supplemental lesson, you will complete a series of tasks.</span></span> <span data-ttu-id="33825-117">這麼一來，便會識別此 Adventure Works 表格式模型案例獨有，但不一定適用於真實案例的工作。</span><span class="sxs-lookup"><span data-stu-id="33825-117">Those tasks that are unique to this Adventure Works tabular model scenario, but would not necessarily apply to a real-world scenario are identified as such.</span></span> <span data-ttu-id="33825-118">每個工作都包含描述工作目的的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="33825-118">Each task includes additional information describing the purpose of the task.</span></span>  
  
 <span data-ttu-id="33825-119">這堂課的預估完成時間：**30 分鐘**</span><span class="sxs-lookup"><span data-stu-id="33825-119">Estimated time to complete this lesson: **30 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="33825-120">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="33825-120">Prerequisites</span></span>  
 <span data-ttu-id="33825-121">此補充課程主題是表格式模型教學課程的一部分，請依序完成。</span><span class="sxs-lookup"><span data-stu-id="33825-121">This supplemental lesson topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="33825-122">在此補充課程中執行工作之前，您必須已完成所有前面的課程。</span><span class="sxs-lookup"><span data-stu-id="33825-122">Before performing the tasks in this supplemental lesson, you should have completed all previous lessons.</span></span>  
  
## <a name="add-the-dimsalesterritory-table-to-the-aw-internet-sales-tabular-model-project"></a><span data-ttu-id="33825-123">將 dimSalesTerritory 資料表加入至 AW Internet Sales 表格式模型專案</span><span class="sxs-lookup"><span data-stu-id="33825-123">Add the dimSalesTerritory table to the AW Internet Sales Tabular Model Project</span></span>  
 <span data-ttu-id="33825-124">若要實作此 Adventure Works 案例的動態安全性，您必須在模型中加入兩個額外的資料表。</span><span class="sxs-lookup"><span data-stu-id="33825-124">In order to implement dynamic security for this Adventure Works scenario, you must add two additional tables to your model.</span></span> <span data-ttu-id="33825-125">第一個要加入的資料表是來自相同 AdventureWorksDW 資料庫的 dimSalesTerritory (也就是銷售地區)。</span><span class="sxs-lookup"><span data-stu-id="33825-125">The first table you will add is dimSalesTerritory (as Sales Territory) from the same AdventureWorksDW database.</span></span> <span data-ttu-id="33825-126">稍後您將在 Sales Territory 資料表中套用資料列篩選器，以定義登入的使用者可以瀏覽的特定資料。</span><span class="sxs-lookup"><span data-stu-id="33825-126">You will later apply a row filter to the Sales Territory table that defines the particular data the logged on user can browse.</span></span>  
  
#### <a name="to-add-the-dimsalesterritory-table"></a><span data-ttu-id="33825-127">若要加入 dimSalesTerritory 資料表</span><span class="sxs-lookup"><span data-stu-id="33825-127">To add the dimSalesTerritory table</span></span>  
  
1.  <span data-ttu-id="33825-128">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，按一下 **[模型]** 功能表，然後按一下 **[現有連接]**。</span><span class="sxs-lookup"><span data-stu-id="33825-128">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click on the **Model** menu, and then click **Existing Connections**.</span></span>  
  
2.  <span data-ttu-id="33825-129">在 [現有連接]\*\*\*\* 對話方塊中，確認已選取 [Adventure Works DB from SQL]\*\*\*\* 資料來源連接，然後按一下 [開啟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="33825-129">In the **Existing Connections** dialog box, verify the **Adventure Works DB from SQL** data source connection is selected, and then click **Open**.</span></span>  
  
     <span data-ttu-id="33825-130">如果出現 [模擬認證] 對話方塊，請輸入您在「第 2 課︰新增資料」中使用的模擬認證。</span><span class="sxs-lookup"><span data-stu-id="33825-130">If the Impersonation Credentials dialog box appears, type the impersonation credentials you used in Lesson 2: Add Data.</span></span>  
  
3.  <span data-ttu-id="33825-131">在 [選擇如何匯入資料]\*\*\*\* 頁面上，讓 [從資料表和檢視表清單來選取要匯入的資料]\*\*\*\* 保持選取狀態，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="33825-131">On the **Choose How to Import the Data** page, leave **Select from a list of tables and views to choose the data to import** selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="33825-132">在 [選取資料表和檢視表]\*\*\*\* 頁面上，選取 [DimSalesTerritory]\*\*\*\* 資料表。</span><span class="sxs-lookup"><span data-stu-id="33825-132">On the **Select Tables and Views** page, select the **DimSalesTerritory** table.</span></span>  
  
5.  <span data-ttu-id="33825-133">在 [易記名稱] 資料行中，輸入 **Sales Territory**。</span><span class="sxs-lookup"><span data-stu-id="33825-133">In the Friendly Name column, type **Sales Territory**.</span></span>  
  
6.  <span data-ttu-id="33825-134">按一下 [預覽和篩選]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="33825-134">Click **Preview and Filter**.</span></span>  
  
7.  <span data-ttu-id="33825-135">取消選取 [SalesTerritoryAlternateKey]\*\*\*\* 資料行，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="33825-135">Deselect the **SalesTerritoryAlternateKey** column, and then click **Ok**.</span></span>  
  
8.  <span data-ttu-id="33825-136">在 [選取資料表和檢視表]\*\*\*\* 頁面上，按一下 [完成]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="33825-136">On the **Select Tables and Views** page, click **Finish**.</span></span>  
  
     <span data-ttu-id="33825-137">新的資料表將會加入至模型工作空間。</span><span class="sxs-lookup"><span data-stu-id="33825-137">The new table will be added to the model workspace.</span></span> <span data-ttu-id="33825-138">來源 dimSalesTerritory 資料表中的物件和資料隨後將匯入 AW Internet Sales 表格式模型的新 Sales Territory 資料表中。</span><span class="sxs-lookup"><span data-stu-id="33825-138">Objects and data from the source dimSalesTerritory table are then imported into the new Sales Territory table in your AW Internet Sales Tabular Model.</span></span>  
  
9. <span data-ttu-id="33825-139">匯入資料表之後，按一下 [關閉]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="33825-139">After the table has been imported, click **Close**.</span></span>  
  
## <a name="give-the-columns-friendly-names"></a><span data-ttu-id="33825-140">為資料行指定易記名稱</span><span class="sxs-lookup"><span data-stu-id="33825-140">Give the Columns Friendly Names</span></span>  
 <span data-ttu-id="33825-141">在這項工作中，您將重新命名 Sales Territory 資料表中的資料行，為其指定易記名稱。</span><span class="sxs-lookup"><span data-stu-id="33825-141">In this task, you will rename the columns in the Sales Territory table, giving them friendly names.</span></span> <span data-ttu-id="33825-142">不一定要為資料表及/或資料行提供易記名稱，不過，它的確可以讓您的模型專案更容易在模型設計工具中進行導覽，並可讓使用者瀏覽用戶端應用程式欄位清單中的模型物件和資料。</span><span class="sxs-lookup"><span data-stu-id="33825-142">It is not always necessary to give tables and/or columns friendly names; however, it does make your model project easier to navigate in the model designer as well as for users browsing model objects and data in a client application field list.</span></span>  
  
#### <a name="to-rename-columns-in-the-sales-territory-table"></a><span data-ttu-id="33825-143">若要重新命名 Sales Territory 資料表中的資料行</span><span class="sxs-lookup"><span data-stu-id="33825-143">To rename Columns in the Sales Territory Table</span></span>  
  
-   <span data-ttu-id="33825-144">在模型設計師中，重新命名 **Sales Territory** 資料表中的資料行：</span><span class="sxs-lookup"><span data-stu-id="33825-144">In the model designer, rename the columns in the **Sales Territory** table:</span></span>  
  
     <span data-ttu-id="33825-145">**銷售領域**</span><span class="sxs-lookup"><span data-stu-id="33825-145">**Sales Territory**</span></span>  
  
    |<span data-ttu-id="33825-146">來源名稱</span><span class="sxs-lookup"><span data-stu-id="33825-146">Source Name</span></span>|<span data-ttu-id="33825-147">易記名稱</span><span class="sxs-lookup"><span data-stu-id="33825-147">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="33825-148">SalesTerritoryKey</span><span class="sxs-lookup"><span data-stu-id="33825-148">SalesTerritoryKey</span></span>|<span data-ttu-id="33825-149">Sales Territory Id</span><span class="sxs-lookup"><span data-stu-id="33825-149">Sales Territory Id</span></span>|  
    |<span data-ttu-id="33825-150">SalesTerritoryRegion</span><span class="sxs-lookup"><span data-stu-id="33825-150">SalesTerritoryRegion</span></span>|<span data-ttu-id="33825-151">Sales Territory Region</span><span class="sxs-lookup"><span data-stu-id="33825-151">Sales Territory Region</span></span>|  
    |<span data-ttu-id="33825-152">SalesTerritoryCountry</span><span class="sxs-lookup"><span data-stu-id="33825-152">SalesTerritoryCountry</span></span>|<span data-ttu-id="33825-153">Sales Territory Country</span><span class="sxs-lookup"><span data-stu-id="33825-153">Sales Territory Country</span></span>|  
    |<span data-ttu-id="33825-154">SalesTerritoryGroup</span><span class="sxs-lookup"><span data-stu-id="33825-154">SalesTerritoryGroup</span></span>|<span data-ttu-id="33825-155">Sales Territory Group</span><span class="sxs-lookup"><span data-stu-id="33825-155">Sales Territory Group</span></span>|  
  
## <a name="add-a-table-with-user-name-data"></a><span data-ttu-id="33825-156">新增具有使用者名稱資料的資料表</span><span class="sxs-lookup"><span data-stu-id="33825-156">Add a table with user name data</span></span>  
 <span data-ttu-id="33825-157">由於 AdventureWorksDW 範例資料庫中的 dimEmployee 資料表包含來自 AdventureWorks 網域的使用者，而這些使用者名稱並不存在您自己的環境中，因此您必須在模型中建立包含幾個 (三個) 您組織中實際使用者的資料表。</span><span class="sxs-lookup"><span data-stu-id="33825-157">Because the dimEmployee table in the AdventureWorksDW sample database contains users from the AdventureWorks domain, and those user names do not exist in your own environment, you must create a table in your model that contains a small sample (three) of actual users from your organization.</span></span> <span data-ttu-id="33825-158">之後您會加入這些使用者做為新角色的成員。</span><span class="sxs-lookup"><span data-stu-id="33825-158">You will then add these users as members to the new role.</span></span> <span data-ttu-id="33825-159">您不需要範例使用者名稱的密碼，但是需要您自己網域中的實際 Windows 使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="33825-159">You do not need the passwords for the sample user names, but you will need actual Windows user names from your own domain.</span></span>  
  
#### <a name="to-add-an-employee-security-table"></a><span data-ttu-id="33825-160">若要加入 Employee Security 資料表</span><span class="sxs-lookup"><span data-stu-id="33825-160">To add an Employee Security table</span></span>  
  
1.  <span data-ttu-id="33825-161">開啟 Microsoft Excel，並建立新的工作表。</span><span class="sxs-lookup"><span data-stu-id="33825-161">Open Microsoft Excel, creating a new worksheet.</span></span>  
  
2.  <span data-ttu-id="33825-162">複製下列資料表 (包括標頭資料列)，然後將它貼到工作表中。</span><span class="sxs-lookup"><span data-stu-id="33825-162">Copy the following table, including the header row, and then paste it into the worksheet.</span></span>  
  
    |<span data-ttu-id="33825-163">Employee Id</span><span class="sxs-lookup"><span data-stu-id="33825-163">Employee Id</span></span>|<span data-ttu-id="33825-164">Sales Territory Id</span><span class="sxs-lookup"><span data-stu-id="33825-164">Sales Territory Id</span></span>|<span data-ttu-id="33825-165">名字</span><span class="sxs-lookup"><span data-stu-id="33825-165">First Name</span></span>|<span data-ttu-id="33825-166">姓氏</span><span class="sxs-lookup"><span data-stu-id="33825-166">Last Name</span></span>|<span data-ttu-id="33825-167">Login Id</span><span class="sxs-lookup"><span data-stu-id="33825-167">Login Id</span></span>|  
    |-----------------|------------------------|----------------|---------------|--------------|  
    |<span data-ttu-id="33825-168">1</span><span class="sxs-lookup"><span data-stu-id="33825-168">1</span></span>|<span data-ttu-id="33825-169">2</span><span class="sxs-lookup"><span data-stu-id="33825-169">2</span></span>|\<user first name>|\<user last name>|\<domain\username>|  
    |<span data-ttu-id="33825-170">1</span><span class="sxs-lookup"><span data-stu-id="33825-170">1</span></span>|<span data-ttu-id="33825-171">3</span><span class="sxs-lookup"><span data-stu-id="33825-171">3</span></span>|\<user first name>|\<user last name>|\<domain\username>|  
    |<span data-ttu-id="33825-172">2</span><span class="sxs-lookup"><span data-stu-id="33825-172">2</span></span>|<span data-ttu-id="33825-173">4</span><span class="sxs-lookup"><span data-stu-id="33825-173">4</span></span>|\<user first name>|\<user last name>|\<domain\username>|  
    |<span data-ttu-id="33825-174">3</span><span class="sxs-lookup"><span data-stu-id="33825-174">3</span></span>|<span data-ttu-id="33825-175">5</span><span class="sxs-lookup"><span data-stu-id="33825-175">5</span></span>|\<user first name>|\<user last name>|\<domain\username>|  
  
3.  <span data-ttu-id="33825-176">在新的工作表中，將 first name、last name 和 domain\username 取代為您組織中三個使用者的姓名和登入識別碼。</span><span class="sxs-lookup"><span data-stu-id="33825-176">In the new worksheet, replace the first name, last name, and domain\username with the names and login ids of three users in your organization.</span></span> <span data-ttu-id="33825-177">在 Employee Id 1 的前兩個資料列中放入相同的使用者。</span><span class="sxs-lookup"><span data-stu-id="33825-177">Put the same user on the first two rows, for Employee Id 1.</span></span> <span data-ttu-id="33825-178">這樣表示這個使用者屬於多個銷售地區。</span><span class="sxs-lookup"><span data-stu-id="33825-178">This will show this user belongs to more than one sales territory.</span></span> <span data-ttu-id="33825-179">Employee Id 和 Sales Territory Id 欄位保持不變。</span><span class="sxs-lookup"><span data-stu-id="33825-179">Leave the Employee Id and Sales Territory Id fields as they are.</span></span>  
  
4.  <span data-ttu-id="33825-180">將工作表另存為 `Sample Employee` 。</span><span class="sxs-lookup"><span data-stu-id="33825-180">Save the worksheet as `Sample Employee`.</span></span>  
  
5.  <span data-ttu-id="33825-181">在該工作表中，選取所有包含員工資料的資料格 (包括標頭)，然後以滑鼠右鍵按一下選取的資料，再按一下 [複製]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="33825-181">In the worksheet, select all of the cells with employee data, including the headers, then right click the selected data, and then click **Copy**.</span></span>  
  
6.  <span data-ttu-id="33825-182">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中，按一下 [編輯]\*\*\*\* 功能表，然後按一下 [貼上]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="33825-182">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Edit** menu, and then click **Paste**.</span></span>  
  
     <span data-ttu-id="33825-183">如果 [貼上] 呈現灰色，請按一下模型設計師視窗中任何資料表的任何資料行，然後按一下 [編輯]\*\*\*\* 功能表，再按一下 [貼上]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="33825-183">If Paste is greyed out, click any column in any table in the model designer window, and then click the **Edit** menu, and then click **Paste**.</span></span>  
  
7.  <span data-ttu-id="33825-184">在 [**貼上預覽**] 對話方塊的 [**資料表名稱**] 中，輸入 `Employee Security` 。</span><span class="sxs-lookup"><span data-stu-id="33825-184">In the **Paste Preview** dialog box, in **Table Name**, type `Employee Security`.</span></span>  
  
8.  <span data-ttu-id="33825-185">在 [要貼上的資料]\*\*\*\* 中，確認資料包含 Sample Employee 工作表中的所有使用者資料和標頭。</span><span class="sxs-lookup"><span data-stu-id="33825-185">In **Data to be pasted**, verify the data includes all of the user data and headers from the Sample Employee worksheet.</span></span>  
  
9. <span data-ttu-id="33825-186">確認已核取 [使用第一個資料列做為資料行標頭]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="33825-186">Verify **Use first row as column headers** is checked, and then click **Ok**.</span></span>  
  
     <span data-ttu-id="33825-187">這樣就會建立名為 Employee Security 的新資料表，其中包含從 Sample Employee 工作表複製的員工資料。</span><span class="sxs-lookup"><span data-stu-id="33825-187">A new table named Employee Security with employee data copied from the Sample Employee worksheet is created.</span></span>  
  
## <a name="create-relationships-between-internet-sales-geography-and-sales-territory-table"></a><span data-ttu-id="33825-188">在 Internet Sales、Geography 和 Sales Territory 資料表之間建立關聯性</span><span class="sxs-lookup"><span data-stu-id="33825-188">Create Relationships Between Internet Sales, Geography, and Sales Territory table</span></span>  
 <span data-ttu-id="33825-189">[網際網路銷售]、[地理位置] 和 [銷售領域] 資料表全都包含一個通用資料行 [銷售領域識別碼]。[銷售領域] 資料表中的 [銷售領域識別碼] 資料行包含每個銷售領域具有不同識別碼的值。</span><span class="sxs-lookup"><span data-stu-id="33825-189">The Internet Sales, Geography, and Sales Territory table all contain a common column, Sales Territory Id. The Sales Territory Id column in the Sales Territory table contains values with a different Id for each sales territory.</span></span>  
  
#### <a name="to-create-relationships-between-the-internet-sales-geography-and-the-sales-territory-table"></a><span data-ttu-id="33825-190">若要在 Internet Sales、Geography 和 Sales Territory 資料表之間建立關聯性</span><span class="sxs-lookup"><span data-stu-id="33825-190">To create relationships between the Internet Sales, Geography, and the Sales Territory table</span></span>  
  
1.  <span data-ttu-id="33825-191">在模型設計師中，於 [圖表檢視] 的 [Geography]\*\*\*\* 資料表中按住 [Sales Territory Id]\*\*\*\* 資料行，然後將資料指標拖曳至 [Sales Territory]\*\*\*\* 資料表的 [Sales Territory Id]\*\*\*\* 資料行中，再放開。</span><span class="sxs-lookup"><span data-stu-id="33825-191">In the model designer, in Diagram View, in the **Geography** table, click and hold on the **Sales Territory Id** column, then drag the cursor to the **Sales Territory Id** column in the **Sales Territory** table, and then release.</span></span>  
  
2.  <span data-ttu-id="33825-192">在 [Internet Sales]\*\*\*\* 資料表中，按住 [Sales Territory Id]\*\*\*\* 資料行，然後將資料指標拖曳至 [Sales Territory]\*\*\*\* 資料表的 [Sales Territory Id]\*\*\*\* 資料行中，再放開。</span><span class="sxs-lookup"><span data-stu-id="33825-192">In the **Internet Sales** table, click and hold on the **Sales Territory Id** column, then drag the cursor to the **Sales Territory Id** column in the **Sales Territory** table, and then release.</span></span>  
  
     <span data-ttu-id="33825-193">請注意，此關聯性的 [作用中] 屬性為 False，表示它為非作用中。</span><span class="sxs-lookup"><span data-stu-id="33825-193">Notice the Active property for this relationship is False, meaning it is inactive.</span></span> <span data-ttu-id="33825-194">這是因為 Internet Sales 資料表已有另一個在量值中使用的作用中關聯性。</span><span class="sxs-lookup"><span data-stu-id="33825-194">This is because the Internet Sales table already has another active relationship that is used in measures.</span></span>  
  
## <a name="hide-the-employee-security-table-from-client-applications"></a><span data-ttu-id="33825-195">對用戶端應用程式隱藏 Employee Security 資料表</span><span class="sxs-lookup"><span data-stu-id="33825-195">Hide the Employee Security Table from Client Applications</span></span>  
 <span data-ttu-id="33825-196">在這項工作中，您將隱藏 Employee Security 資料表，使其不會出現在用戶端應用程式的欄位清單中。</span><span class="sxs-lookup"><span data-stu-id="33825-196">In this task, you will hide the Employee Security table, keeping it from appearing in a client application's field list.</span></span> <span data-ttu-id="33825-197">請注意，隱藏資料表並不會保護它。</span><span class="sxs-lookup"><span data-stu-id="33825-197">Keep in-mind that hiding a table does not secure it.</span></span> <span data-ttu-id="33825-198">使用者仍然可以查詢 Employee Security 資料表的資料 (如果使用者知道如何查詢的話)。</span><span class="sxs-lookup"><span data-stu-id="33825-198">Users can still query Employee Security table data if they know how.</span></span> <span data-ttu-id="33825-199">為了保護 Employee Security 資料表資料的安全，防止使用者查詢其中的任何資料，您將在稍後的工作中套用篩選器。</span><span class="sxs-lookup"><span data-stu-id="33825-199">In order to secure the Employee Security table data, preventing users from being able to query any of its data, you will apply a filter in a later task.</span></span>  
  
#### <a name="to-hide-the-employee-table-from-client-applications"></a><span data-ttu-id="33825-200">若要對用戶端應用程式隱藏 Employee 資料表</span><span class="sxs-lookup"><span data-stu-id="33825-200">To hide the Employee Table from client applications</span></span>  
  
-   <span data-ttu-id="33825-201">在模型設計工具的 [圖表檢視] 中，以滑鼠右鍵按一下 [員工]\*\*\*\* 資料表標題，，然後按一下 [在用戶端工具中隱藏]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="33825-201">In the model designer, in Diagram View, right-click the **Employee** table heading, and then click **Hide from Client Tools**.</span></span>  
  
## <a name="create-a-sales-employees-by-territory-user-role"></a><span data-ttu-id="33825-202">建立「銷售地區員工」使用者角色</span><span class="sxs-lookup"><span data-stu-id="33825-202">Create a Sales Employees by Territory user role</span></span>  
 <span data-ttu-id="33825-203">在這項工作中，您將建立新的使用者角色。</span><span class="sxs-lookup"><span data-stu-id="33825-203">In this task, you will create a new user role.</span></span> <span data-ttu-id="33825-204">這個角色將包含一個資料列篩選器，用於定義使用者可以看見 Sales Territory 資料表中的哪些資料列。</span><span class="sxs-lookup"><span data-stu-id="33825-204">This role will include a row filter defining which rows of the Sales Territory table are visible to users.</span></span> <span data-ttu-id="33825-205">這個篩選器隨後會在一對多關聯性方向中套用至與 Sales Territory 相關的所有其他資料表。</span><span class="sxs-lookup"><span data-stu-id="33825-205">The filter is then applied in the one-to many relationship direction to all other tables related to Sales Territory.</span></span> <span data-ttu-id="33825-206">您還會套用一個簡單的篩選器，用來保護整個 Employee Security 資料表的安全，防止屬於該角色成員的任何使用者查詢。</span><span class="sxs-lookup"><span data-stu-id="33825-206">You will also apply a simple filter that secures the entire Employee Security table from being queryable by any user that is a member of the role.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="33825-207">您在這堂課中建立的「銷售地區員工」角色會限制成員只能瀏覽 (或查詢) 其所屬銷售地區的銷售資料。</span><span class="sxs-lookup"><span data-stu-id="33825-207">The Sales Employees by Territory role you create in this lesson restricts members to browse (or query) only sales data for the sales territory to which they belong.</span></span> <span data-ttu-id="33825-208">如果您將使用者新增為 Sales Employees by Territory 角色的成員，而該使用者同時是 [第 12 課：建立角色](../analysis-services/lesson-11-create-roles.md)中所建立角色的成員，則會獲得合併的權限。</span><span class="sxs-lookup"><span data-stu-id="33825-208">If you add a user as a member to the Sales Employees by Territory role that also exists as a member in a role created in [Lesson 12: Create Roles](../analysis-services/lesson-11-create-roles.md), you will get a combination of permissions.</span></span> <span data-ttu-id="33825-209">當使用者是多個角色的成員時，則針對每個角色定義的權限和資料列篩選條件會累計。</span><span class="sxs-lookup"><span data-stu-id="33825-209">When a user is a member of multiple roles, the permissions, and row filters defined for each role are cumulative.</span></span> <span data-ttu-id="33825-210">也就是說，該使用者將具有大於角色組合所決定的權限。</span><span class="sxs-lookup"><span data-stu-id="33825-210">That is, the user will have the greater permissions determined by the combination of roles.</span></span>  
  
#### <a name="to-create-a-sales-employees-by-territory-user-role"></a><span data-ttu-id="33825-211">建立「銷售地區員工」使用者角色</span><span class="sxs-lookup"><span data-stu-id="33825-211">To create a Sales Employees by Territory user role</span></span>  
  
1.  <span data-ttu-id="33825-212">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中，按一下 [模型]\*\*\*\* 功能表，然後按一下 [角色]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="33825-212">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Roles**.</span></span>  
  
2.  <span data-ttu-id="33825-213">在 [角色管理員]\*\*\*\* 對話方塊中，按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="33825-213">In the **Role Manager** dialog box, click **New**.</span></span>  
  
     <span data-ttu-id="33825-214">清單中會新增 [無] 權限的新角色。</span><span class="sxs-lookup"><span data-stu-id="33825-214">A new role with the None permission is added to the list.</span></span>  
  
3.  <span data-ttu-id="33825-215">按一下 [新增] 角色，然後在 [**名稱**] 資料行中，將角色重新命名為 `Sales Employees by Territory` 。</span><span class="sxs-lookup"><span data-stu-id="33825-215">Click on the new role, and then in the **Name** column, rename the role to `Sales Employees by Territory`.</span></span>  
  
4.  <span data-ttu-id="33825-216">在 [權限]\*\*\*\* 資料行中，按一下下拉式清單，然後選取 [讀取]\*\*\*\* 權限。</span><span class="sxs-lookup"><span data-stu-id="33825-216">In the **Permissions** column, click the dropdown list, and then select the **Read** permission.</span></span>  
  
5.  <span data-ttu-id="33825-217">按一下 [成員]\*\*\*\* 索引標籤，然後按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="33825-217">Click on the **Members** tab, and then click **Add**.</span></span>  
  
6.  <span data-ttu-id="33825-218">在 [選取使用者或群組]\*\*\*\* 對話方塊中，於 [輸入要選取的物件名稱]\*\*\*\* 輸入您建立 Employee Security 資料表時使用的第一個範例使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="33825-218">In the **Select User or Group** dialog box, in **Enter the object named to select**, type the first sample user name you used when creating the Employee Security table.</span></span> <span data-ttu-id="33825-219">按一下 [檢查名稱]\*\*\*\* 來驗證使用者名稱是否有效，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="33825-219">Click **Check Names** to verify the user name is valid, and then click **Ok**.</span></span>  
  
     <span data-ttu-id="33825-220">重複這個步驟，加入您建立 Employee Security 資料表時使用的其他範例使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="33825-220">Repeat this step, adding the other sample user names you used when creating the Employee Security table.</span></span>  
  
7.  <span data-ttu-id="33825-221">按一下 [資料列篩選器]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="33825-221">Click on the **Row Filters** tab.</span></span>  
  
8.  <span data-ttu-id="33825-222">針對 `Employee Security` 資料表，在 [ **DAX 篩選**] 資料行中，輸入下列公式。</span><span class="sxs-lookup"><span data-stu-id="33825-222">For the `Employee Security` table, in the **DAX Filter** column, type the following formula.</span></span>  
  
     `=FALSE()`  
  
     <span data-ttu-id="33825-223">完成建立公式時，按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="33825-223">When you have finished building the formula, press ENTER.</span></span>  
  
     <span data-ttu-id="33825-224">這個公式會指定所有資料行都解析為 False 布林值條件；因此，Sales Employees by Territory 使用者角色的成員無法查詢 Employee Security 資料表的任何資料行。</span><span class="sxs-lookup"><span data-stu-id="33825-224">This formula specifies that all columns resolve to the false Boolean condition; therefore, no columns for the Employee Security table can be queried by a member of the Sales Employees by Territory user role.</span></span>  
  
9. <span data-ttu-id="33825-225">針對 [Sales Territory]\*\*\*\* 資料表，輸入下列公式。</span><span class="sxs-lookup"><span data-stu-id="33825-225">For the **Sales Territory** table, type the following formula.</span></span>  
  
     `='Sales Territory'[Sales Territory Id]=LOOKUPVALUE('Employee Security'[Sales Territory Id], 'Employee Security'[Login Id], USERNAME(), 'Employee Security'[Sales Territory Id], 'Sales Territory'[Sales Territory Id])`  
  
     <span data-ttu-id="33825-226">完成建立公式時，按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="33825-226">When you have finished building the formula, press ENTER.</span></span>  
  
     <span data-ttu-id="33825-227">在這個公式中，LOOKUPVALUE 函數會傳回 Employee Security[Sales Territory Id] 資料行的所有值，其中 Employee Security[Login Id] 與目前登入的 Windows 使用者名稱相同，而 Employee Security[Sales Territory Id] 與 Sales Territory[Sales Territory Id] 相同。</span><span class="sxs-lookup"><span data-stu-id="33825-227">In this formula, the LOOKUPVALUE function returns all values for the Employee Security[Sales Territory Id] column, where the Employee Security[Login Id] is the same as the current logged on Windows user name, and Employee Security[Sales Territory Id] is the same as the Sales Territory[Sales Territory Id].</span></span>  
  
     <span data-ttu-id="33825-228">LOOKUPVALUE 所傳回的 Sales Territory ID 集會用來限至 Sales Territory 資料表中顯示的資料列。</span><span class="sxs-lookup"><span data-stu-id="33825-228">The set of Sales Territory IDs returned by LOOKUPVALUE is then used to restrict the rows shown in the Sales Territory table.</span></span> <span data-ttu-id="33825-229">只有資料列的 Sales Territory ID 落在 LOOKUPVALUE 函數所傳回的 ID 集之中的資料列才會顯示。</span><span class="sxs-lookup"><span data-stu-id="33825-229">Only rows where the Sales Territory ID for the row is in the set of IDs returned by the LOOKUPVALUE function are displayed.</span></span>  
  
10. <span data-ttu-id="33825-230">在 [角色管理員] 對話方塊中，按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="33825-230">In the Role Manager dialog box, click **Ok**.</span></span>  
  
## <a name="test-the-sales-employees-by-territory-user-role"></a><span data-ttu-id="33825-231">測試「銷售地區員工」使用者角色</span><span class="sxs-lookup"><span data-stu-id="33825-231">Test the Sales Employees by Territory User Role</span></span>  
 <span data-ttu-id="33825-232">在這項工作中，您將使用 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中的 [在 Excel 中進行分析] 功能來測試 Sales Employees by Territory 使用者角色的效用。</span><span class="sxs-lookup"><span data-stu-id="33825-232">In this task, you will use the Analyze in Excel feature in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] to test the efficacy of the Sales Employees by Territory user role.</span></span> <span data-ttu-id="33825-233">您將指定其中一個加入至 Employee Security 資料表且做為角色成員的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="33825-233">You will specify one of the user names you added to the Employee Security table and as a member of the role.</span></span> <span data-ttu-id="33825-234">然後這個使用者名稱會做為 Excel 和模型之間所建立連接中的有效使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="33825-234">This user name will then be used as the effective user name in the connection created between Excel and the model.</span></span>  
  
#### <a name="to-test-the-sales-employees-by-territory-user-role"></a><span data-ttu-id="33825-235">測試「銷售地區員工」使用者角色</span><span class="sxs-lookup"><span data-stu-id="33825-235">To test the Sales Employees by Territory user role</span></span>  
  
1.  <span data-ttu-id="33825-236">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，按一下 **[模型]** 功能表，然後按一下 **[在 Excel 中進行分析]**。</span><span class="sxs-lookup"><span data-stu-id="33825-236">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Analyze in Excel**.</span></span>  
  
2.  <span data-ttu-id="33825-237">在 [使用 Excel 分析]\*\*\*\* 對話方塊的 [指定要用來連線至模型的使用者名稱或角色]\*\*\*\* 中，選取 [其他 Windows 使用者]\*\*\*\*，然後按一下 [瀏覽]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="33825-237">In the **Analyze in Excel** dialog box, in **Specify the user name or role to use to connect to the model**, select **Other Windows User**, and then click **Browse**.</span></span>  
  
3.  <span data-ttu-id="33825-238">在 [選取使用者或群組]\*\*\*\* 對話方塊中，於 [輸入要選取的物件名稱]\*\*\*\* 輸入您加入 Employee 資料表中的其中一個使用者名稱，然後按一下 [檢查名稱]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="33825-238">In the **Select User or Group** dialog box, in **Enter the object name to select**, type one of the user names you included in the Employee table, and then click **Check Names**.</span></span>  
  
4.  <span data-ttu-id="33825-239">按一下 [確定]\*\*\*\* 以關閉 [選取使用者或群組]\*\*\*\* 對話方塊，然後按一下 [確定]\*\*\*\* 以關閉 [使用 Excel 分析]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="33825-239">Click **Ok** to close the **Select User or Group** dialog box, and then click **Ok** to close the **Analyze in Excel** dialog box.</span></span>  
  
     <span data-ttu-id="33825-240">Excel 會開啟新的活頁簿。</span><span class="sxs-lookup"><span data-stu-id="33825-240">Excel will open with a new workbook.</span></span> <span data-ttu-id="33825-241">樞紐分析表會自動建立。</span><span class="sxs-lookup"><span data-stu-id="33825-241">A Pivot table is automatically created.</span></span> <span data-ttu-id="33825-242">[樞紐分析表欄位清單] 包含新模型中大部分可用的資料欄位。</span><span class="sxs-lookup"><span data-stu-id="33825-242">The Pivot Table Field List includes most of the data fields available in your new model.</span></span>  
  
     <span data-ttu-id="33825-243">請注意，Employee Security 資料表不會在 [樞紐分析表欄位清單] 中顯示。</span><span class="sxs-lookup"><span data-stu-id="33825-243">Notice the Employee Security table is not visible in the Pivot Table Field List.</span></span> <span data-ttu-id="33825-244">這是因為您在前一項工作中選擇了對用戶端工具隱藏這個資料表。</span><span class="sxs-lookup"><span data-stu-id="33825-244">This is because you chose to hide this table from client tools in a previous task.</span></span>  
  
5.  <span data-ttu-id="33825-245">在 [樞紐分析表欄位]\*\*\*\* 清單中，於 [∑ Internet Sales]\*\*\*\* (量值) 中選取 [Internet Total Sales]\*\*\*\* 量值。</span><span class="sxs-lookup"><span data-stu-id="33825-245">In the **Pivot Table Field** list, in **∑ Internet Sales** (measures), select the **Internet Total Sales** measure.</span></span> <span data-ttu-id="33825-246">這個量值將會輸入 [值]\*\*\*\* 欄位中。</span><span class="sxs-lookup"><span data-stu-id="33825-246">The measure will be entered into the **Values** fields.</span></span>  
  
6.  <span data-ttu-id="33825-247">在 [樞紐分析表欄位]\*\*\*\* 清單中，從 [Sales Territory]\*\*\*\* 資料表選取 [Sales Territory Id]\*\*\*\* 資料行。</span><span class="sxs-lookup"><span data-stu-id="33825-247">In the **Pivot Table Field** list, select the **Sales Territory Id** column from the **Sales Territory** table.</span></span> <span data-ttu-id="33825-248">這個資料行將會輸入 [資料列標籤]\*\*\*\* 欄位中。</span><span class="sxs-lookup"><span data-stu-id="33825-248">The column will be entered into the **Row Labels** fields.</span></span>  
  
     <span data-ttu-id="33825-249">請注意，只會針對您使用的有效使用者名稱所屬的區域顯示網際網路銷售數字。</span><span class="sxs-lookup"><span data-stu-id="33825-249">Notice Internet sales figures appear only for the one region to which the effective user name you used belongs.</span></span> <span data-ttu-id="33825-250">如果您從 Geography 資料表選取另一個資料行 (例如，City) 做為 [資料列標籤] 欄位，則只會顯示有效使用者所屬銷售地區中的城市。</span><span class="sxs-lookup"><span data-stu-id="33825-250">If you select another column; for example, City, from the Geography table as Row Label field, only cities in the sales territory to which the effective user belongs are displayed.</span></span>  
  
     <span data-ttu-id="33825-251">這個使用者無法瀏覽或查詢本身所屬地區以外之地區的任何網際網路銷售資料，因為 Sales Employees by Territory 使用者角色中針對 Sales Territory 資料表所定義的資料列篩選器有效地保護了與其他銷售地區相關之所有資料的安全。</span><span class="sxs-lookup"><span data-stu-id="33825-251">This user cannot browse or query any Internet sales data for territories other than the one they belong because the row filter defined for the Sales Territory table in the Sales Employees by Territory user role effectively secures data for all data related to other sales territories.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33825-252">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33825-252">See Also</span></span>  
 <span data-ttu-id="33825-253">[USERNAME 函數 &#40;DAX&#41;](/dax/username-function-dax) </span><span class="sxs-lookup"><span data-stu-id="33825-253">[USERNAME Function &#40;DAX&#41;](/dax/username-function-dax) </span></span>  
 <span data-ttu-id="33825-254">[&#40;DAX&#41;的 LOOKUPVALUE 函數](/dax/lookupvalue-function-dax) </span><span class="sxs-lookup"><span data-stu-id="33825-254">[LOOKUPVALUE Function &#40;DAX&#41;](/dax/lookupvalue-function-dax) </span></span>  
 [<span data-ttu-id="33825-255">&#40;DAX&#41;的 CUSTOMDATA 函數</span><span class="sxs-lookup"><span data-stu-id="33825-255">CUSTOMDATA Function &#40;DAX&#41;</span></span>](/dax/customdata-function-dax)  
  
  
