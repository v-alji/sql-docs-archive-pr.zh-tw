---
title: 工作2：使用適用于 Excel 的 MDS 增益集將供應商資料上傳至 MDS |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 598deb57-e0cc-4e0a-aeb1-94432c094c67
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 16c5fa9db81649b30c12fae4d2e57afa8bf094e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584896"
---
# <a name="task-2-uploading-supplier-data-to-mds-using-mds-add-in-for-excel"></a><span data-ttu-id="faff1-102">工作 2：使用適用於 Excel 的 MDS 增益集將供應商資料上傳到 MDS</span><span class="sxs-lookup"><span data-stu-id="faff1-102">Task 2: Uploading Supplier Data to MDS using MDS Add-in for Excel</span></span>
  <span data-ttu-id="faff1-103">在這項工作中，您會使用**適用于 Excel 的 MDS 增益集**，將清理和供應商資料發行至**mds** 。</span><span class="sxs-lookup"><span data-stu-id="faff1-103">In this task, you publish the cleansed and supplier data to **MDS** using the **MDS Add-in for Excel**.</span></span> <span data-ttu-id="faff1-104">您會在上一課建立的**供應商**模型中，建立名為**供應商**的實體。</span><span class="sxs-lookup"><span data-stu-id="faff1-104">You create an entity named **Supplier** in the **Suppliers** model you created in the previous lesson.</span></span> <span data-ttu-id="faff1-105">此實體將會針對 Excel 檔案中的每個資料行具有一個屬性。</span><span class="sxs-lookup"><span data-stu-id="faff1-105">The entity will have an attribute for each column in the Excel file.</span></span> <span data-ttu-id="faff1-106">[供應商] 實體的 [程式碼] 和 [名稱] 屬性會對應到 Excel 中的 [供貨**商** **] 和 [**</span><span class="sxs-lookup"><span data-stu-id="faff1-106">The Code and Name attributes of the Supplier entity correspond to the **SupplierID** and **Supplier Name** columns in Excel.</span></span>  
  
1.  <span data-ttu-id="faff1-107">在**Excel**中開啟**清理和相符的 Suppliers.xls** 。</span><span class="sxs-lookup"><span data-stu-id="faff1-107">Open **Cleansed and Matched Suppliers.xls** in **Excel**.</span></span>  
  
2.  <span data-ttu-id="faff1-108">按**CTRL + A**選取整個資料。</span><span class="sxs-lookup"><span data-stu-id="faff1-108">Press **CTRL+A** to select entire data.</span></span> <span data-ttu-id="faff1-109">請**務必**選取試算表中的完整資料。</span><span class="sxs-lookup"><span data-stu-id="faff1-109">It is **important** that you select the entire data in the spreadsheet.</span></span>  
  
3.  <span data-ttu-id="faff1-110">按一下功能表列上的 [**主要資料**]。</span><span class="sxs-lookup"><span data-stu-id="faff1-110">Click **Master Data** on the menu bar.</span></span>  
  
4.  <span data-ttu-id="faff1-111">按一下功能區上的 [**建立實體**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="faff1-111">Click **Create Entity** button on the ribbon.</span></span>  
  
     <span data-ttu-id="faff1-112">![Excel - [主要資料] 索引標籤 - [建立實體] 按鈕](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-01.jpg "Excel - [主要資料] 索引標籤 - [建立實體] 按鈕")</span><span class="sxs-lookup"><span data-stu-id="faff1-112">![Excel - Master Data Tab - Create Entity Button](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-01.jpg "Excel - Master Data Tab - Create Entity Button")</span></span>  
  
5.  <span data-ttu-id="faff1-113">在 [**管理連接**] 對話方塊中，如果您在 [**現有連接**] 下看不到**本機 MDS 伺服器**的連接，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="faff1-113">In **Manage Connections** dialog box, if you do not see the connection to **local MDS server** under **Existing connections**, do the following:</span></span>  
  
    1.  <span data-ttu-id="faff1-114">選取 [**建立新的連接**]，然後按一下 [**新增**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="faff1-114">Select **Create a new connection**, and click **New** button.</span></span>  
  
    2.  <span data-ttu-id="faff1-115">在 [**加入新連接**] 對話方塊中，針對 [**描述**] 輸入**本機 Mds 伺服器**，並針對 [ **mds 伺服器位址**] 輸入**HTTP： \/ /localhost/MDS** ，然後按一下 **[確定**] 關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="faff1-115">In the **Add New Connection** dialog box, type **Local MDS Server** for **Description** and **http:\//localhost/MDS** for **MDS server address**, and click **OK** to close the dialog box.</span></span>  
  
6.  <span data-ttu-id="faff1-116">在 [**管理連接**] 對話方塊中，選取 [**本機 MDS 伺服器** (`http://localhost/MDS`) ]，然後按一下 [**測試**] 來測試連接。</span><span class="sxs-lookup"><span data-stu-id="faff1-116">In **Manage Connections** dialog box, select **Local MDS Server** (`http://localhost/MDS`), click **Test** to test the connection.</span></span> <span data-ttu-id="faff1-117">在訊息方塊上按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="faff1-117">Click **OK** on the message box.</span></span>  
  
7.  <span data-ttu-id="faff1-118">按一下 **[連接**]，連接到 MDS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="faff1-118">Click **Connect** to connect to the MDS server.</span></span>  
  
8.  <span data-ttu-id="faff1-119">在 [**建立實體**] 對話方塊中，選取 [**供應商**] 做為**模型**。</span><span class="sxs-lookup"><span data-stu-id="faff1-119">In the **Create Entity** dialog box, select **Suppliers** for the **Model**.</span></span>  
  
9. <span data-ttu-id="faff1-120">確定已針對 [**版本**] 選取 [ **VERSION_1** ]。</span><span class="sxs-lookup"><span data-stu-id="faff1-120">Ensure that **VERSION_1** is selected for **Version**.</span></span>  
  
10. <span data-ttu-id="faff1-121">針對 [**新機構名稱**] 輸入**供應商**。</span><span class="sxs-lookup"><span data-stu-id="faff1-121">Enter **Supplier** for **New entity name**.</span></span>  
  
11. <span data-ttu-id="faff1-122">針對**包含唯一識別碼**欄位的資料行選取 [中繼資料 **]， (** 您也可以) 自動產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="faff1-122">Select **SupplierID** for **the column that contains a unique identifier** field (you can also generate a code automatically).</span></span> <span data-ttu-id="faff1-123">您基本上會將**Excel**中的 [供貨**商**] 資料行對應至 [**供應商**] 實體的 [ **Code** ] 屬性。</span><span class="sxs-lookup"><span data-stu-id="faff1-123">You are essentially mapping the **SupplierID** column in **Excel** to the **Code** attribute of **Supplier** entity.</span></span>  
  
12. <span data-ttu-id="faff1-124">針對**包含 [名稱**] 欄位的資料行，選取 [**供應商名稱**]。</span><span class="sxs-lookup"><span data-stu-id="faff1-124">Select **Supplier Name** for **the column that contains names** field.</span></span> <span data-ttu-id="faff1-125">您基本上會將**Excel**中的**供應商名稱**資料行對應至**供應商**實體的**name**屬性。</span><span class="sxs-lookup"><span data-stu-id="faff1-125">You are essentially mapping the **Supplier Name** column in **Excel** to the **Name** attribute of the **Supplier** entity.</span></span> <span data-ttu-id="faff1-126">**Code**和**NAME**屬性是 MDS 中實體的必要屬性。</span><span class="sxs-lookup"><span data-stu-id="faff1-126">The **Code** and **Name** attributes are mandatory attributes for an entity in MDS.</span></span>  
  
     <span data-ttu-id="faff1-127">![[建立實體] 對話方塊](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-02.jpg "[建立實體] 對話方塊")</span><span class="sxs-lookup"><span data-stu-id="faff1-127">![Create Entity Dialog Box](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-02.jpg "Create Entity Dialog Box")</span></span>  
  
13. <span data-ttu-id="faff1-128">按一下 **[確定]** 以在 MDS 上建立實體、將主要資料發行至實體，然後關閉 [**建立實體**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="faff1-128">Click **OK** to create the entity on MDS, publish the master data to the entity, and close **Create Entity** dialog box.</span></span>  
  
14. <span data-ttu-id="faff1-129">現在，您應該會看到標題為「**供應商**」的新工作表，也就是實體的名稱，加入 Excel 試算表，然後在工作表頂端，您應該會看到工作表已連接到 MDS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="faff1-129">Now, you should see a new sheet titled **Supplier**, which is the name of the entity, added to your Excel spreadsheet and at the top of the worksheet you should see that the worksheet is connected to the MDS server.</span></span> <span data-ttu-id="faff1-130">請注意，原始工作表 (標題為**Sheet1**) 仍然存在。</span><span class="sxs-lookup"><span data-stu-id="faff1-130">Notice that the original worksheet (titled **Sheet1**) still exists.</span></span>  
  
     <span data-ttu-id="faff1-131">![Excel - [供應商] 和 [Sheet1] 索引標籤](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-03.jpg "Excel - [供應商] 和 [Sheet1] 索引標籤")</span><span class="sxs-lookup"><span data-stu-id="faff1-131">![Excel - Supplier and Sheet1 Tabs](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-03.jpg "Excel - Supplier and Sheet1 Tabs")</span></span>  
  
     <span data-ttu-id="faff1-132">![Excel - 顯示 MDS 連接詳細資料](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-04.jpg "Excel - 顯示 MDS 連接詳細資料")</span><span class="sxs-lookup"><span data-stu-id="faff1-132">![Excel - Showing MDS Connection Details](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-04.jpg "Excel - Showing MDS Connection Details")</span></span>  
  
15. <span data-ttu-id="faff1-133">讓**Excel**保持開啟。</span><span class="sxs-lookup"><span data-stu-id="faff1-133">Keep **Excel** open.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="faff1-134">下一項工作</span><span class="sxs-lookup"><span data-stu-id="faff1-134">Next Task</span></span>  
 [<span data-ttu-id="faff1-135">工作 3：在主資料管理員中驗證資料</span><span class="sxs-lookup"><span data-stu-id="faff1-135">Task 3: Verifying the Data in Master Data Manager</span></span>](../../2014/tutorials/task-3-verifying-the-data-in-master-data-manager.md)  
  
  
