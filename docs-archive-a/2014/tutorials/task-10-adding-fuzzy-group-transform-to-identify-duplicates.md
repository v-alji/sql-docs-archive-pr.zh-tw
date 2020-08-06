---
title: 工作10：新增模糊群組轉換以識別重複專案 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 90b2b323-babd-464a-8914-9dc5e66aca74
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 086625197850fdfd6381e9c0a4a7deac8ce3ae45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699001"
---
# <a name="task-10-adding-fuzzy-group-transform-to-identify-duplicates"></a><span data-ttu-id="8d682-102">工作 10：新增模糊群組轉換來識別重複項</span><span class="sxs-lookup"><span data-stu-id="8d682-102">Task 10: Adding Fuzzy Group Transform to Identify Duplicates</span></span>
  <span data-ttu-id="8d682-103">在這項工作中，您會將模糊群組轉換加入至資料流程。</span><span class="sxs-lookup"><span data-stu-id="8d682-103">In this task, you add a Fuzzy Group Transform to the data flow.</span></span> <span data-ttu-id="8d682-104">模糊群組轉換有助於識別來源資料中的重複項。</span><span class="sxs-lookup"><span data-stu-id="8d682-104">The Fuzzy Group transformation can help identify duplicates in the source data.</span></span> <span data-ttu-id="8d682-105">如需詳細資訊，請參閱[模糊群組轉換](../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="8d682-105">See [Fuzzy Grouping Transformation](../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md) for more details.</span></span>  
  
1.  <span data-ttu-id="8d682-106">將 [ **SSIS 工具箱**] 的**其他轉換**中的 [**模糊群組**轉換] 拖放到 [**結合正確和更正的記錄**] 底下的 [**資料流程**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8d682-106">Drag-drop **Fuzzy Group** transform in **Other Transforms** on the **SSIS Toolbox** to the **Data Flow** tab under **Combine Correct and Corrected Records**.</span></span>  
  
2.  <span data-ttu-id="8d682-107">以滑鼠右鍵**按一下 [資料流程**] 索引標籤中的 [**模糊群組**轉換]，然後按一下 [**重新命名**]。</span><span class="sxs-lookup"><span data-stu-id="8d682-107">Right-click **Fuzzy Group** Transform in the **Data Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="8d682-108">輸入**群組具有相符識別碼的供應商**，然後按**enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="8d682-108">Type **Group Suppliers with matching IDs** and press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="8d682-109">使用藍色連接器，將**正確和已更正的記錄結合**為符合**識別碼的群組供應商**。</span><span class="sxs-lookup"><span data-stu-id="8d682-109">Connect **Combine Correct and Corrected Records** to **Group Suppliers with matching IDs** using the blue connector.</span></span>  
  
     <span data-ttu-id="8d682-110">![連接有相符識別碼的 [供應商] 群組](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-01.jpg "連接有相符識別碼的 [供應商] 群組")</span><span class="sxs-lookup"><span data-stu-id="8d682-110">![Connection to Group Suppliers with Matching IDs](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-01.jpg "Connection to Group Suppliers with Matching IDs")</span></span>  
  
4.  <span data-ttu-id="8d682-111">按兩下 [**群組具有相符識別碼的供應商**]。</span><span class="sxs-lookup"><span data-stu-id="8d682-111">Double-click **Group Suppliers with matching IDs**.</span></span>  
  
5.  <span data-ttu-id="8d682-112">在 [**模糊群組轉換編輯器**] 中，按一下 [ **OLE DB 連接管理員] 下拉式清單**旁邊的 [**新增**]，以啟動 [**設定 OLE DB 連線管理員**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8d682-112">In the **Fuzzy Group Transformation Editor**, click **New** next to **OLE DB Connection Manager drop-down list** to launch **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
6.  <span data-ttu-id="8d682-113">在對話方塊中，按一下 [**新增**] 以啟動 [**連線管理員**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8d682-113">In the dialog box, click **New** to launch **Connection Manager** dialog box.</span></span>  
  
7.  <span data-ttu-id="8d682-114">在 [伺服器名稱] 中，輸入\*\* (local) **或**period\*\* (. ) 。</span><span class="sxs-lookup"><span data-stu-id="8d682-114">Type **(local)** or **period** (.) for the Server name.</span></span>  
  
8.  <span data-ttu-id="8d682-115">針對 [**選取或輸入資料庫名稱**] 欄位選取 [ **MDS** ]。</span><span class="sxs-lookup"><span data-stu-id="8d682-115">Select **MDS** for **Select or enter a database name** field.</span></span> <span data-ttu-id="8d682-116">您將使用 MDS 資料庫做為**模糊群組轉換**的暫存儲存體。</span><span class="sxs-lookup"><span data-stu-id="8d682-116">You will use the MDS database as the temporary storage for the **Fuzzy Group Transform**.</span></span> <span data-ttu-id="8d682-117">「**模糊群組**」轉換需要連接到 SQL Server 的實例，以建立轉換演算法執行其工作所需的暫存 SQL Server 資料表。</span><span class="sxs-lookup"><span data-stu-id="8d682-117">The **Fuzzy Grouping** transformation requires a connection to an instance of SQL Server to create the temporary SQL Server tables that the transformation algorithm requires to do its work.</span></span> <span data-ttu-id="8d682-118">您可以建立資料庫，或使用另一個現有的資料庫供此用途使用。</span><span class="sxs-lookup"><span data-stu-id="8d682-118">You can create a database or use another existing database for this purpose.</span></span>  
  
9. <span data-ttu-id="8d682-119">按一下 [**測試連接**] 來測試連接，然後按一下訊息方塊上的 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="8d682-119">Click **Test Connection** to test the connection and click **OK** on the message box.</span></span>  
  
10. <span data-ttu-id="8d682-120">在 [**連線管理員**] 對話方塊中，按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8d682-120">In the **Connection Manager** dialog box, click **OK**.</span></span>  
  
11. <span data-ttu-id="8d682-121">選取 [ \*\* (本機) MDS\*\* (或**localhost。MDS**) **資料連線清單**中，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8d682-121">Select **(local).MDS** (or **localhost.MDS**) from the **list of Data Connections** and click **OK**.</span></span>  
  
12. <span data-ttu-id="8d682-122">在 [**模糊群組轉換編輯器**] 中，確認\*\* (本機) MDS**或**localhost。\*\* 已針對**OLE DB 連線管理員**選取 MDS。</span><span class="sxs-lookup"><span data-stu-id="8d682-122">In the **Fuzzy Grouping Transformation Editor**, confirm that **(local).MDS** or **localhost.MDS** is selected for the **OLE DB Connection Manager**.</span></span>  
  
13. <span data-ttu-id="8d682-123">切換至 [資料**行**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8d682-123">Switch to the **Columns** tab.</span></span>  
  
14. <span data-ttu-id="8d682-124">從**可用輸入資料行**的清單中選取 [ (] 核取方塊) **SupplierID_Output** 。</span><span class="sxs-lookup"><span data-stu-id="8d682-124">Select (check box) **SupplierID_Output** from the list of **Available Input Columns**.</span></span> <span data-ttu-id="8d682-125">若要設定轉換，請選取在識別重複項時所要使用的輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="8d682-125">To configure the transformation, select the input columns to use when identifying duplicates.</span></span> <span data-ttu-id="8d682-126">為了維持單純化，您在此步驟中只會使用 SupplierID。</span><span class="sxs-lookup"><span data-stu-id="8d682-126">To keep it simple, you only use the SupplierID in this step.</span></span>  
  
     <span data-ttu-id="8d682-127">![模糊群組轉換編輯器](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-02.jpg "模糊群組轉換編輯器")</span><span class="sxs-lookup"><span data-stu-id="8d682-127">![Fuzzy Grouping Transformation Editor](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-02.jpg "Fuzzy Grouping Transformation Editor")</span></span>  
  
15. <span data-ttu-id="8d682-128">按一下 **[確定]** 以關閉 [**模糊群組轉換編輯器**]。</span><span class="sxs-lookup"><span data-stu-id="8d682-128">Click **OK** to close the **Fuzzy Group Transformation Editor**.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="8d682-129">後續步驟</span><span class="sxs-lookup"><span data-stu-id="8d682-129">Next Step</span></span>  
 [<span data-ttu-id="8d682-130">工作 11：新增條件式分割轉換來篩選重複項</span><span class="sxs-lookup"><span data-stu-id="8d682-130">Task 11: Adding Conditional Split Transform to Filter Duplicates</span></span>](../../2014/tutorials/task-11-adding-conditional-split-transform-to-filter-duplicates.md)  
  
  
