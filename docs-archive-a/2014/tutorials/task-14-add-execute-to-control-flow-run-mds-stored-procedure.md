---
title: 工作14：將執行 SQL 工作新增至控制流程，以執行 MDS 的預存程式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 9a5d1b52-d505-4e6f-8a89-569329c094e2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: da8e80b25706c40e749fc364baeb578681e76b42
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698929"
---
# <a name="task-14-adding-execute-sql-task-to-control-flow-to-run-the-stored-procedure-for-mds"></a><span data-ttu-id="5bae6-102">工作 14：將執行 SQL 工作新增至控制流程，為 MDS 執行預存程序</span><span class="sxs-lookup"><span data-stu-id="5bae6-102">Task 14: Adding Execute SQL Task to Control Flow to Run the Stored Procedure for MDS</span></span>
  <span data-ttu-id="5bae6-103">將資料載入 MDS 的暫存資料表之後，您會執行與該資料表有關的預存程序，將暫存中的資料載入 MDS 資料庫中的適當資料表。</span><span class="sxs-lookup"><span data-stu-id="5bae6-103">After loading data into the staging tables of MDS, you run a stored procedure associated with that table to load the data from staging into the appropriate tables in the MDS database.</span></span> <span data-ttu-id="5bae6-104">這個預存程序具有您必須傳遞的兩個必要參數：LogFlag 和 VersionName。</span><span class="sxs-lookup"><span data-stu-id="5bae6-104">This stored procedure has two required parameters that you need to pass: LogFlag and VersionName.</span></span> <span data-ttu-id="5bae6-105">LogFlag 會指定暫存處理序期間所記錄的交易，而 VersionName 則代表模型的版本。</span><span class="sxs-lookup"><span data-stu-id="5bae6-105">LogFlag specifies whether transactions are logged during the staging process and VersionName represents the version of the model.</span></span> <span data-ttu-id="5bae6-106">如需詳細資訊，請參閱[分段預存](https://msdn.microsoft.com/library/hh231028.aspx)程式主題。</span><span class="sxs-lookup"><span data-stu-id="5bae6-106">See [Staged Stored Procedure](https://msdn.microsoft.com/library/hh231028.aspx) topic for more details.</span></span>

 <span data-ttu-id="5bae6-107">在這項工作中，您會將「執行 SQL 工作」加入至控制流程來叫用預存程序，以便將暫存資料載入至適當的 MDS 資料表。</span><span class="sxs-lookup"><span data-stu-id="5bae6-107">In this task, you add the Execute SQL Task to the control flow to invoke the stored procedure to load the staged data into appropriate MDS tables.</span></span>

1.  <span data-ttu-id="5bae6-108">現在，切換到 [**控制流程**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5bae6-108">Now, switch to the **Control Flow** tab.</span></span>

2.  <span data-ttu-id="5bae6-109">從 [ **SSIS 工具箱**] 將 [**執行 SQL**工作] 拖放至 [**控制流程**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5bae6-109">Drag-drop **Execute SQL Task** from the **SSIS Toolbox** to the **Control Flow** tab.</span></span>

3.  <span data-ttu-id="5bae6-110">以滑鼠右鍵按一下 [**控制流程**] 索引標籤中的 [**執行 SQL**工作]，然後按一下 [**重新命名**]</span><span class="sxs-lookup"><span data-stu-id="5bae6-110">Right-click **Execute SQL Task** in the **Control Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="5bae6-111">輸入**觸發程式預存程式，將資料載入 MDS** ，然後按**enter**。</span><span class="sxs-lookup"><span data-stu-id="5bae6-111">Type **Trigger Stored Procedure to Load Data into MDS** and press **ENTER**.</span></span>

4.  <span data-ttu-id="5bae6-112">連接**接收、清理、比對和策展供應商資料**，以使用綠色連接器來**觸發預存程式來載入資料**。</span><span class="sxs-lookup"><span data-stu-id="5bae6-112">Connect **Receive, Cleanse, Match, and Curate Supplier Data** to **Trigger Stored Procedure to Load Data** using the green connector.</span></span>

     <span data-ttu-id="5bae6-113">![連接至「執行 SQL」工作](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-01.jpg "連接至「執行 SQL」工作")</span><span class="sxs-lookup"><span data-stu-id="5bae6-113">![Connect to Execute SQL Task](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-01.jpg "Connect to Execute SQL Task")</span></span>

5.  <span data-ttu-id="5bae6-114">使用 [**變數**] 視窗，使用下列設定加入兩個新的變數。</span><span class="sxs-lookup"><span data-stu-id="5bae6-114">Using the **Variables** window, add two new variables with the following settings.</span></span> <span data-ttu-id="5bae6-115">如果您看不到 [**變數**] 視窗，請按一下功能表列上的 [ **SSIS** ]，然後按一下 [**變數**]。</span><span class="sxs-lookup"><span data-stu-id="5bae6-115">If you do not see the **Variables** window, click **SSIS** on the menu bar and click **Variables**.</span></span>

    |<span data-ttu-id="5bae6-116">名稱</span><span class="sxs-lookup"><span data-stu-id="5bae6-116">Name</span></span>|<span data-ttu-id="5bae6-117">資料類型</span><span class="sxs-lookup"><span data-stu-id="5bae6-117">Data Type</span></span>|<span data-ttu-id="5bae6-118">值</span><span class="sxs-lookup"><span data-stu-id="5bae6-118">Value</span></span>|
    |----------|---------------|-----------|
    |<span data-ttu-id="5bae6-119">LogFlag</span><span class="sxs-lookup"><span data-stu-id="5bae6-119">LogFlag</span></span>|<span data-ttu-id="5bae6-120">Int32</span><span class="sxs-lookup"><span data-stu-id="5bae6-120">Int32</span></span>|<span data-ttu-id="5bae6-121">1</span><span class="sxs-lookup"><span data-stu-id="5bae6-121">1</span></span>|
    |<span data-ttu-id="5bae6-122">VersionName</span><span class="sxs-lookup"><span data-stu-id="5bae6-122">VersionName</span></span>|<span data-ttu-id="5bae6-123">String</span><span class="sxs-lookup"><span data-stu-id="5bae6-123">String</span></span>|<span data-ttu-id="5bae6-124">VERSION_1</span><span class="sxs-lookup"><span data-stu-id="5bae6-124">VERSION_1</span></span>|

     <span data-ttu-id="5bae6-125">![SSIS 變數視窗](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-02.jpg "SSIS 變數視窗")</span><span class="sxs-lookup"><span data-stu-id="5bae6-125">![SSIS Variables Window](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-02.jpg "SSIS Variables Window")</span></span>

6.  <span data-ttu-id="5bae6-126">按兩下 [**觸發預存程式]，將資料載入 MDS**。</span><span class="sxs-lookup"><span data-stu-id="5bae6-126">Double-click **Trigger Stored Procedure to Load Data into MDS**.</span></span>

7.  <span data-ttu-id="5bae6-127">在 [**執行 SQL 工作編輯器**] 對話方塊中，選取 [ \*\* (本機) MDS\*\* (或**localhost。** 適用于**連接**的 MDS) 。</span><span class="sxs-lookup"><span data-stu-id="5bae6-127">In the **Execute SQL Task Editor** dialog box, select **(local).MDS** (or **localhost.MDS**) for **Connection**.</span></span>

8.  <span data-ttu-id="5bae6-128">輸入**EXEC [stg.<]. [udp_Supplier_Leaf]?,?,?**</span><span class="sxs-lookup"><span data-stu-id="5bae6-128">Type **EXEC [stg].[udp_Supplier_Leaf] ?, ?, ?**</span></span> <span data-ttu-id="5bae6-129">適用于**SQL 語句**。</span><span class="sxs-lookup"><span data-stu-id="5bae6-129">for **SQL Statement**.</span></span> <span data-ttu-id="5bae6-130">您可以使用 SQL Server Management Studio 來驗證此名稱。</span><span class="sxs-lookup"><span data-stu-id="5bae6-130">You can verify the name by using SQL Server Management Studio.</span></span>

     <span data-ttu-id="5bae6-131">![執行 SQL 編輯器對話方塊 - 一般設定](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-03.jpg "執行 SQL 編輯器對話方塊 - 一般設定")</span><span class="sxs-lookup"><span data-stu-id="5bae6-131">![Execute SQL Editor Dialog Box - General Settings](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-03.jpg "Execute SQL Editor Dialog Box - General Settings")</span></span>

9. <span data-ttu-id="5bae6-132">按一下左側功能表中的 [**參數對應**]。</span><span class="sxs-lookup"><span data-stu-id="5bae6-132">Click **Parameter Mapping** from the menu on left.</span></span>

10. <span data-ttu-id="5bae6-133">在 [**參數對應**] 頁面上，按一下 [**新增**] 以新增對應。</span><span class="sxs-lookup"><span data-stu-id="5bae6-133">In the **Parameter Mapping** page, click **Add** to add a mapping.</span></span> <span data-ttu-id="5bae6-134">最大化視窗並調整資料行的大小，讓您可以適當地查看下拉式清單中的值。</span><span class="sxs-lookup"><span data-stu-id="5bae6-134">Maximize the window and resize columns so that you can see values in drop-down lists properly.</span></span>

11. <span data-ttu-id="5bae6-135">從 [**變數名稱**] 的下拉式清單中，選取 [ **User：： VersionName** ]。</span><span class="sxs-lookup"><span data-stu-id="5bae6-135">Select **User::VersionName** from the drop-down list for the **Variable Name**.</span></span>

12. <span data-ttu-id="5bae6-136">針對 [**資料類型**] 選取 [ **NVARCHAR** ]。</span><span class="sxs-lookup"><span data-stu-id="5bae6-136">Select **NVARCHAR** for **Data Type**.</span></span>

13. <span data-ttu-id="5bae6-137">在 [**參數名稱**] 中，輸入**0** (零) 。</span><span class="sxs-lookup"><span data-stu-id="5bae6-137">Type **0** (zero) for **Parameter Name**.</span></span>

14. <span data-ttu-id="5bae6-138">重複上述四個步驟來加入其他兩個變數。</span><span class="sxs-lookup"><span data-stu-id="5bae6-138">Repeat the previous four steps to add two more variables.</span></span>

    |<span data-ttu-id="5bae6-139">變數名稱</span><span class="sxs-lookup"><span data-stu-id="5bae6-139">Variable Name</span></span>|<span data-ttu-id="5bae6-140">資料類型 (重要)</span><span class="sxs-lookup"><span data-stu-id="5bae6-140">Data Type (important)</span></span>|<span data-ttu-id="5bae6-141">參數名稱</span><span class="sxs-lookup"><span data-stu-id="5bae6-141">Parameter Name</span></span>|
    |-------------------|-----------------------------|--------------------|
    |<span data-ttu-id="5bae6-142">User::LogFlag</span><span class="sxs-lookup"><span data-stu-id="5bae6-142">User::LogFlag</span></span>|<span data-ttu-id="5bae6-143">LONG</span><span class="sxs-lookup"><span data-stu-id="5bae6-143">LONG</span></span>|<span data-ttu-id="5bae6-144">1</span><span class="sxs-lookup"><span data-stu-id="5bae6-144">1</span></span>|
    |<span data-ttu-id="5bae6-145">User::BatchTag</span><span class="sxs-lookup"><span data-stu-id="5bae6-145">User::BatchTag</span></span>|<span data-ttu-id="5bae6-146">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="5bae6-146">NVARCHAR</span></span>|<span data-ttu-id="5bae6-147">2</span><span class="sxs-lookup"><span data-stu-id="5bae6-147">2</span></span>|

     <span data-ttu-id="5bae6-148">![執行 SQL 工作編輯器 - 參數對應](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-04.jpg "執行 SQL 工作編輯器 - 參數對應")</span><span class="sxs-lookup"><span data-stu-id="5bae6-148">![Execute SQL Task Editor - Parameter Mapping](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-04.jpg "Execute SQL Task Editor - Parameter Mapping")</span></span>

15. <span data-ttu-id="5bae6-149">按一下 **[確定]** 以關閉 [**執行 SQL 編輯器**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5bae6-149">Click **OK** to close the **Execute SQL Editor** dialog box.</span></span>

## <a name="next-step"></a><span data-ttu-id="5bae6-150">後續步驟</span><span class="sxs-lookup"><span data-stu-id="5bae6-150">Next Step</span></span>
 [<span data-ttu-id="5bae6-151">工作 15：建置及執行 SSIS 專案</span><span class="sxs-lookup"><span data-stu-id="5bae6-151">Task 15: Building and Running the SSIS Project</span></span>](../../2014/tutorials/task-15-building-and-running-the-ssis-project.md)


