---
title: 工作 1 (必要條件) ：在 MDS 中移除供應商資料 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6f0a4287-7fd4-4f18-b7e4-a5191a9d4a3c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e78dc5ff04f95d42cf440e3f80b1b349e0315a69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598700"
---
# <a name="task-1-prerequisite-removing-supplier-data-in-mds"></a><span data-ttu-id="41e05-102">工作 1 (必要)：在 MDS 中移除供應商資料</span><span class="sxs-lookup"><span data-stu-id="41e05-102">Task 1 (Prerequisite): Removing Supplier Data in MDS</span></span>
  <span data-ttu-id="41e05-103">在這項工作中，您會移除儲存在 MDS 中的供應商資料。</span><span class="sxs-lookup"><span data-stu-id="41e05-103">In this task, you remove the supplier data stored in MDS.</span></span> <span data-ttu-id="41e05-104">您在上一課使用**MDS Excel 增益集**手動上傳資料。</span><span class="sxs-lookup"><span data-stu-id="41e05-104">You uploaded the data manually using **MDS Excel Add-in** in the previous lesson.</span></span> <span data-ttu-id="41e05-105">您在這一課建立的 SSIS 封裝會將資料自動上傳至 MDS。</span><span class="sxs-lookup"><span data-stu-id="41e05-105">The SSIS package you create in this lesson will automatically upload the data to MDS for you.</span></span> <span data-ttu-id="41e05-106">因此，在測試 SSIS 封裝之前，您必須從 MDS 中移除供應商資料、移除衍生階層、移除 supplier 和 state 實體，並且建立不含任何資料的 supplier 實體。</span><span class="sxs-lookup"><span data-stu-id="41e05-106">Therefore, before testing the SSIS package, you need to remove the supplier data from MDS, remove the derived hierarchy, remove supplier and state entities, and create the supplier entity with no data.</span></span>  
  
1.  <span data-ttu-id="41e05-107">流覽**Master Data Manager**至 `http://localhost/MDS` 或您在設定 MDS 時所指定的網站和應用程式，以啟動主資料管理員。</span><span class="sxs-lookup"><span data-stu-id="41e05-107">Launch **Master Data Manager** by navigating to `http://localhost/MDS` or the website and application you specified when configuring MDS.</span></span> <span data-ttu-id="41e05-108">如果您將**主資料管理員**保持開啟，請按一下頂端的 [ **SQL Server 2012 Master Data Services** ，以切換至**首頁**。</span><span class="sxs-lookup"><span data-stu-id="41e05-108">If you kept the **Master Data Manager** open, click **SQL Server 2012 Master Data Services** at the top to switch to the **home page**.</span></span>  
  
2.  <span data-ttu-id="41e05-109">按一下 [**管理**工作] 區段中的 [**系統管理**]。</span><span class="sxs-lookup"><span data-stu-id="41e05-109">Click **System Administration** in the **Administrative Tasks** section.</span></span>  
  
3.  <span data-ttu-id="41e05-110">將滑鼠停留在功能表上的 [**管理**] 上，然後按一下 [**衍生**階層]。</span><span class="sxs-lookup"><span data-stu-id="41e05-110">Hover the mouse over **Manage** on the menu and click **Derived Hierarchies**.</span></span> <span data-ttu-id="41e05-111">您必須先刪除衍生階層**SuppliersInState** ，才能刪除**供應商**模型中的實體。</span><span class="sxs-lookup"><span data-stu-id="41e05-111">You need to delete the derived hierarchy **SuppliersInState** before deleting the entities in the **Suppliers** model.</span></span>  
  
4.  <span data-ttu-id="41e05-112">從 [**衍生**階層] 清單中選取 [ **SuppliersInState** ]，然後按一下工具列上的 [ \*\*X (刪除) \*\* ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="41e05-112">Select **SuppliersInState** from the **Derived Hierarchy** list and click **X (Delete)** button on the toolbar.</span></span>  
  
5.  <span data-ttu-id="41e05-113">按一下 **[確定]** 以確認刪除。</span><span class="sxs-lookup"><span data-stu-id="41e05-113">Click **OK** to confirm deletion.</span></span>  
  
6.  <span data-ttu-id="41e05-114">將滑鼠停留在功能表上的 [**管理**] 上，然後按一下 [**實體**]。</span><span class="sxs-lookup"><span data-stu-id="41e05-114">Hover the mouse over **Manage** on the menu and click **Entities**.</span></span>  
  
7.  <span data-ttu-id="41e05-115">按一下 [**供應商**]，然後按一下工具列上的 [\*\*刪除 (X) \*\* ] 按鈕，以刪除實體。</span><span class="sxs-lookup"><span data-stu-id="41e05-115">Click **Supplier** and click **Delete (X)** button on toolbar to delete the entity.</span></span> <span data-ttu-id="41e05-116">在訊息方塊上按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="41e05-116">Click **OK** on message boxes.</span></span>  
  
8.  <span data-ttu-id="41e05-117">重複上一個步驟以刪除**狀態**實體。</span><span class="sxs-lookup"><span data-stu-id="41e05-117">Repeat the previous step to delete **State** entity.</span></span>  
  
9. <span data-ttu-id="41e05-118">請勿關閉**主資料管理員**。</span><span class="sxs-lookup"><span data-stu-id="41e05-118">Don't close **Master Data Manager**.</span></span>  
  
10. <span data-ttu-id="41e05-119">切換至已開啟**清理且符合 Suppliers.xls**檔案的 Excel 視窗。</span><span class="sxs-lookup"><span data-stu-id="41e05-119">Switch to the Excel window that has **Cleansed and Matched Suppliers.xls** file open.</span></span> <span data-ttu-id="41e05-120">切換至底部的 [ **Sheet1** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="41e05-120">Switch to the **Sheet1** tab at the bottom.</span></span>  
  
11. <span data-ttu-id="41e05-121">僅選取**具有標頭的第一個資料列**。</span><span class="sxs-lookup"><span data-stu-id="41e05-121">Select only the **first row with headers**.</span></span> <span data-ttu-id="41e05-122">不要選取任何其他資料列。</span><span class="sxs-lookup"><span data-stu-id="41e05-122">Don't select any other row.</span></span> <span data-ttu-id="41e05-123">您想要根據 Excel 資料行建立實體，但不想上傳任何資料。</span><span class="sxs-lookup"><span data-stu-id="41e05-123">You want to create the entities based on the Excel columns but don't want to upload any data.</span></span> <span data-ttu-id="41e05-124">因此，您只選取有標頭的第一個資料列。</span><span class="sxs-lookup"><span data-stu-id="41e05-124">Therefore you select only the first row with the headers.</span></span>  
  
12. <span data-ttu-id="41e05-125">按一下功能表列上的 [**主要資料**]。</span><span class="sxs-lookup"><span data-stu-id="41e05-125">Click **Master Data** on the menu bar.</span></span>  
  
13. <span data-ttu-id="41e05-126">按一下功能區中的 [**建立實體**]。</span><span class="sxs-lookup"><span data-stu-id="41e05-126">Click **Create Entity** from the ribbon.</span></span>  
  
14. <span data-ttu-id="41e05-127">在 [**管理連接**] 對話方塊中，如果您在 [**現有連接**] 下看不到**本機 MDS 伺服器**的連接，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="41e05-127">In **Manage Connections** dialog box, if you do not see the connection to **local MDS server** under **Existing connections**, do the following:</span></span>  
  
    1.  <span data-ttu-id="41e05-128">選取 [**建立新的連接**]，然後按一下 [**新增**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="41e05-128">Select **Create a new connection**, and click **New** button.</span></span>  
  
    2.  <span data-ttu-id="41e05-129">在 [加入新連接] 對話方塊中，針對 [**描述**] 輸入**本機 mds 伺服器**，並針對 [ **mds 伺服器位址**] 輸入**Http： \/ /localhost/MDS** ，然後按一下 **[確定**] 關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="41e05-129">In the Add New Connection dialog box, type **Local MDS Server** for **Description** and **http:\//localhost/MDS** for **MDS server address**, and click **OK** to close the dialog box.</span></span>  
  
15. <span data-ttu-id="41e05-130">在 [**管理連接**] 對話方塊中，選取 [**本機 MDS 伺服器** (`http://localhost/MDS`) ]，然後按一下 [**測試**] 來測試連接。</span><span class="sxs-lookup"><span data-stu-id="41e05-130">In **Manage Connections** dialog box, select **Local MDS Server** (`http://localhost/MDS`), click **Test** to test the connection.</span></span> <span data-ttu-id="41e05-131">在訊息方塊上按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="41e05-131">Click **OK** on the message box.</span></span>  
  
16. <span data-ttu-id="41e05-132">按一下 **[連接]** ，建立與 MDS 伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="41e05-132">Click **Connect** to make a connection to the MDS server.</span></span>  
  
17. <span data-ttu-id="41e05-133">在 [**建立實體**] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="41e05-133">In the **Create Entity** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="41e05-134">確認 [**範圍**] 設定為 **$ 1： $ 1**。</span><span class="sxs-lookup"><span data-stu-id="41e05-134">Confirm that **Range** is set to **$1:$1**.</span></span>  
  
    2.  <span data-ttu-id="41e05-135">選取 [適用于**模型**的**供應商**]。</span><span class="sxs-lookup"><span data-stu-id="41e05-135">Select **Suppliers** for **Model**.</span></span>  
  
    3.  <span data-ttu-id="41e05-136">針對 [**版本**] 選取 [ **VERSION_1** ]。</span><span class="sxs-lookup"><span data-stu-id="41e05-136">Select **VERSION_1** for **Version**.</span></span>  
  
    4.  <span data-ttu-id="41e05-137">輸入**供應商**以取得**新的機構名稱**。</span><span class="sxs-lookup"><span data-stu-id="41e05-137">Type **Supplier** for **New entity name**.</span></span>  
  
    5.  <span data-ttu-id="41e05-138">針對 [程式**代碼**] 選取 [已**供應**]。</span><span class="sxs-lookup"><span data-stu-id="41e05-138">Select **SupplierID** for **Code**.</span></span>  
  
    6.  <span data-ttu-id="41e05-139">選取 [**名稱**] 的 [**供應商名稱**]。</span><span class="sxs-lookup"><span data-stu-id="41e05-139">Select **Supplier Name** for **Name**.</span></span>  
  
    7.  <span data-ttu-id="41e05-140">按一下 **[確定]** 以建立實體，並關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="41e05-140">Click **OK** to create the entity and close the dialog box.</span></span>  
  
18. <span data-ttu-id="41e05-141">關閉**Excel** ，**不要儲存**盤案。</span><span class="sxs-lookup"><span data-stu-id="41e05-141">Close **Excel** and **do not save** the file.</span></span>  
  
19. <span data-ttu-id="41e05-142">在**主資料管理員**中，重新整理網際網路瀏覽器，並確認清單中顯示**供應商**實體。</span><span class="sxs-lookup"><span data-stu-id="41e05-142">In **Master Data Manager**, refresh the internet browser and confirm that **Supplier** entity is displayed in the list.</span></span>  
  
20. <span data-ttu-id="41e05-143">按一下頂端的 [ **SQL Server 2012 Master Data Services** ，切換到**首頁**。</span><span class="sxs-lookup"><span data-stu-id="41e05-143">Switch to the **home page** by clicking **SQL Server 2012 Master Data Services** at the top.</span></span>  
  
21. <span data-ttu-id="41e05-144">確認已針對 [**模型**] 選取 [**供應商**型號]，並針對 [**版本**] 選取 [ **VERSION_1** ]。</span><span class="sxs-lookup"><span data-stu-id="41e05-144">Confirm that **Suppliers** model is selected for **Model** and **VERSION_1** is selected for **Version**.</span></span>  
  
22. <span data-ttu-id="41e05-145">按一下 **[總管]**。</span><span class="sxs-lookup"><span data-stu-id="41e05-145">Click **Explorer**.</span></span> <span data-ttu-id="41e05-146">請注意，會建立具有所有屬性的**供應商**實體，且**不含任何值**。</span><span class="sxs-lookup"><span data-stu-id="41e05-146">Notice that the **Supplier** entity with all the attributes is created with **no values**.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="41e05-147">後續步驟</span><span class="sxs-lookup"><span data-stu-id="41e05-147">Next Step</span></span>  
 [<span data-ttu-id="41e05-148">工作 2 &#40;選擇性&#41;：使用主資料管理員建立 MDS 訂閱視圖</span><span class="sxs-lookup"><span data-stu-id="41e05-148">Task 2 &#40;Optional&#41;: Creating a MDS Subscription View using Master Data Manager</span></span>](../../2014/tutorials/task-2-optional-creating-a-mds-subscription-view-using-master-data-manager.md)  
  
  
