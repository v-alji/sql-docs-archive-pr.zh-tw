---
title: 工作12：加入衍生的資料行轉換，以加入 MDS 所需的資料行 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 98ccb271-04da-4126-9729-67e9a479aaef
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a4a70dd4d288e425beb2821f6b2aaf440b1d1930
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703513"
---
# <a name="task-12-adding-derived-column-transform-to-add-columns-required-by-mds"></a><span data-ttu-id="1c5be-102">工作 12：新增衍生的資料行轉換來新增 MDS 需要的資料行</span><span class="sxs-lookup"><span data-stu-id="1c5be-102">Task 12: Adding Derived Column Transform to Add Columns Required by MDS</span></span>
  <span data-ttu-id="1c5be-103">在這項工作中，您會將衍生的資料行轉換加入至資料流程。</span><span class="sxs-lookup"><span data-stu-id="1c5be-103">In this task, you add the Derive Column Transform to the data flow.</span></span> <span data-ttu-id="1c5be-104">您可以將兩個衍生的資料行**ImportType**和**BatchTag**加入至傳遞給此轉換的記錄。</span><span class="sxs-lookup"><span data-stu-id="1c5be-104">You add two derived columns, **ImportType** and **BatchTag**, to the records passed to this transform.</span></span> <span data-ttu-id="1c5be-105">您應該先加入這兩個資料行，然後再將資料上傳至 MDS 中的暫存資料表。</span><span class="sxs-lookup"><span data-stu-id="1c5be-105">You should add these columns before uploading the data to staging tables in MDS.</span></span> <span data-ttu-id="1c5be-106">這兩個是 MDS 中暫存資料表的必要資料行。</span><span class="sxs-lookup"><span data-stu-id="1c5be-106">These two are required columns for the staging tables in MDS.</span></span> <span data-ttu-id="1c5be-107">如需詳細資訊，請參閱分[葉成員臨時表](../master-data-services/leaf-member-staging-table-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1c5be-107">See [Leaf Member Staging Tables](../master-data-services/leaf-member-staging-table-master-data-services.md) for more details.</span></span>  
  
1.  <span data-ttu-id="1c5be-108">從 [ **SSIS 工具箱**] 的 [**一般**] 區段，將 [衍生的**資料\*\*\*\*行轉換**] 拖放至 [資料流程] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="1c5be-108">Drag-drop **Derived Column transform** from **Common** section in the **SSIS Toolbox** to the **Data Flow** tab.</span></span>  
  
2.  <span data-ttu-id="1c5be-109">以滑鼠右鍵按一下 [資料流程] 索引標籤中的 [衍生**資料\*\*\*\*行**轉換]，然後按一下 [**重新命名**]</span><span class="sxs-lookup"><span data-stu-id="1c5be-109">Right-click **Derived Column** Transform in the **Data Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="1c5be-110">輸入 [**加入 MDS 所需的資料行**]，然後按**enter**。</span><span class="sxs-lookup"><span data-stu-id="1c5be-110">Type **Add Columns Required by MDS** and press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="1c5be-111">連接**篩選重複專案**，以使用藍色連接器**加入 MDS 所需的資料行**。</span><span class="sxs-lookup"><span data-stu-id="1c5be-111">Connect **Filter Duplicates** to **Add Columns Required by MDS** using the blue connector.</span></span> <span data-ttu-id="1c5be-112">您應該會看到 [**輸入輸出選擇**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1c5be-112">You should see the **Input Output Selection** dialog box.</span></span>  
  
4.  <span data-ttu-id="1c5be-113">在 [**輸入輸出選擇**] 對話方塊中，選取 [**唯一記錄**]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="1c5be-113">In the **Input Output Selection** dialog box, select **Unique Records**, and click **OK**.</span></span>  
  
     <span data-ttu-id="1c5be-114">![[輸入輸出選擇] 對話方塊](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-01.jpg "[輸入輸出選擇] 對話方塊")</span><span class="sxs-lookup"><span data-stu-id="1c5be-114">![Input Output Selection Dialog Box](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-01.jpg "Input Output Selection Dialog Box")</span></span>  
  
5.  <span data-ttu-id="1c5be-115">按一下功能表列上的 [ **SSIS** ]，然後按一下 [**變數**]。</span><span class="sxs-lookup"><span data-stu-id="1c5be-115">Click **SSIS** on the menu bar and click **Variables**.</span></span>  
  
6.  <span data-ttu-id="1c5be-116">在 [**變數**] 視窗中，按一下工具列上的 [**加入變數**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1c5be-116">In the **Variables** window, click **Add Variable** button on the toolbar.</span></span>  
  
     <span data-ttu-id="1c5be-117">![SSIS 變數視窗](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-02.jpg "SSIS 變數視窗")</span><span class="sxs-lookup"><span data-stu-id="1c5be-117">![SSIS Variables Window](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-02.jpg "SSIS Variables Window")</span></span>  
  
7.  <span data-ttu-id="1c5be-118">在 [**名稱**] 中輸入**ImportType** ，並在 [**值**] 中輸入**2** 。</span><span class="sxs-lookup"><span data-stu-id="1c5be-118">Type **ImportType** for the **Name** and **2** for the **value**.</span></span> <span data-ttu-id="1c5be-119">您指定的值為 2，因為您要在 MDS 的實體中加入新的成員。</span><span class="sxs-lookup"><span data-stu-id="1c5be-119">You specify the value as 2 because you want to add new members to an entity in MDS.</span></span> <span data-ttu-id="1c5be-120">如需這個參數的詳細資訊，請參閱分[葉成員臨時表](../master-data-services/leaf-member-staging-table-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1c5be-120">For details about this parameter, see [Leaf Member Staging Table](../master-data-services/leaf-member-staging-table-master-data-services.md).</span></span>  
  
8.  <span data-ttu-id="1c5be-121">再次按一下 [**新增變數**] 工具列按鈕。</span><span class="sxs-lookup"><span data-stu-id="1c5be-121">Click **Add Variable** toolbar button again.</span></span>  
  
9. <span data-ttu-id="1c5be-122">在 [**名稱**] 中輸入**BatchTag** ，針對**資料類型**選取 [**字串**]，並針對 [**值**] **EIMBatch** 。</span><span class="sxs-lookup"><span data-stu-id="1c5be-122">Type **BatchTag** for the **Name**, select **String** for the **Data type**, and **EIMBatch** for the **Value**.</span></span> <span data-ttu-id="1c5be-123">**BatchTag**只是您將提交至 MDS 的批次唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="1c5be-123">**BatchTag** is just a unique name for the batch you will be submitting to MDS.</span></span>  
  
10. <span data-ttu-id="1c5be-124">在 [資料流程] 索引標籤中，按兩下 [**加入 MDS 所需的\*\*\*\*資料**行]。</span><span class="sxs-lookup"><span data-stu-id="1c5be-124">In the **Data Flow** tab, double-click **Add Columns Required by MDS**.</span></span>  
  
11. <span data-ttu-id="1c5be-125">在 [**衍生的資料行轉換編輯器**] 對話方塊中，于**底部窗格的清單方塊**中，針對 [**衍生的資料行名稱**] 輸入**ImportType** 。</span><span class="sxs-lookup"><span data-stu-id="1c5be-125">In the **Derived Column Transformation Editor** dialog box, in the **list box in the bottom pane**, type **ImportType** for the **Derived Column Name**.</span></span>  
  
12. <span data-ttu-id="1c5be-126">展開左上方窗格中的 [**變數和參數**]，將**User：： ImportType**拖放到 [**運算式**] 資料行。</span><span class="sxs-lookup"><span data-stu-id="1c5be-126">Expand **Variables and Parameters** in the top-left pane, drag-drop **User::ImportType** to the **Expression** column.</span></span>  
  
     <span data-ttu-id="1c5be-127">![衍生的資料行轉換編輯器](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-03.jpg "衍生的資料行轉換編輯器")</span><span class="sxs-lookup"><span data-stu-id="1c5be-127">![Derived Column Transformation Editor](../../2014/tutorials/media/et-addingdcttoaddcolumnsrequiredbymds-03.jpg "Derived Column Transformation Editor")</span></span>  
  
13. <span data-ttu-id="1c5be-128">在 [衍生的資料行名稱] 的下一個資料**列**中，輸入**BatchTag** 。</span><span class="sxs-lookup"><span data-stu-id="1c5be-128">Type **BatchTag** in the next row for the **Derived Column Name**.</span></span>  
  
14. <span data-ttu-id="1c5be-129">將**User：： BatchTag**從**變數和參數**拖放至**Expression**資料行。</span><span class="sxs-lookup"><span data-stu-id="1c5be-129">Drag-drop **User::BatchTag** from **Variables and Parameters** to the **Expression** column.</span></span>  
  
15. <span data-ttu-id="1c5be-130">按一下 **[確定]** 以關閉 [衍生的資料**行轉換**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1c5be-130">Click **OK** to close the **Derived Column Transformation** dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="1c5be-131">後續步驟</span><span class="sxs-lookup"><span data-stu-id="1c5be-131">Next Step</span></span>  
 [<span data-ttu-id="1c5be-132">工作 13：新增 OLE DB 目的地來將資料寫入 MDS 暫存資料表</span><span class="sxs-lookup"><span data-stu-id="1c5be-132">Task 13: Adding OLE DB Destination to Write Data to MDS Staging Table</span></span>](../../2014/tutorials/task-13-adding-ole-db-destination-to-write-data-to-mds-staging-table.md)  
  
  
