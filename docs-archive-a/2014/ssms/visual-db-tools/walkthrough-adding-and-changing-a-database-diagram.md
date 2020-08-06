---
title: 逐步解說：加入與變更資料庫圖表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- database diagrams [SQL Server], about database diagrams
- database diagrams [SQL Server], designing
- database diagrams [SQL Server], creating
ms.assetid: 228caa0d-8f24-46ab-86d1-b6d8631322bc
author: stevestein
ms.author: sstein
ms.openlocfilehash: c35eb3674c817e98a25a74cd0309fc7376fe2f58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585742"
---
# <a name="walkthrough-adding-and-changing-a-database-diagram"></a><span data-ttu-id="097df-102">逐步解說：加入與變更資料庫圖表</span><span class="sxs-lookup"><span data-stu-id="097df-102">Walkthrough: Adding and Changing a Database Diagram</span></span>
  <span data-ttu-id="097df-103">這個逐步解說將說明如何建立與修改資料庫圖表，以及透過資料庫圖表元件對資料庫進行變更。</span><span class="sxs-lookup"><span data-stu-id="097df-103">This walkthrough illustrates how to create and modify a database diagram and make changes to the database through the database diagrams component.</span></span> <span data-ttu-id="097df-104">您將看到如何將資料表加入至圖表、建立資料表之間的關聯性、建立資料行上的條件約束和索引，以及變更您查看每個資料表的資訊層級。</span><span class="sxs-lookup"><span data-stu-id="097df-104">You will see how to add tables to diagrams, create relationships between tables, create constraints and indexes on columns, and change the level of information you see for each table.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="097df-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="097df-105">Prerequisites</span></span>  
 <span data-ttu-id="097df-106">為了完成這個逐步解說，您需要：</span><span class="sxs-lookup"><span data-stu-id="097df-106">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="097df-107">存取含有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 範例資料庫的 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]</span><span class="sxs-lookup"><span data-stu-id="097df-107">Access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database</span></span>  
  
-   <span data-ttu-id="097df-108">具有資料庫擁有者 `dbo` 權限的帳戶</span><span class="sxs-lookup"><span data-stu-id="097df-108">An account with database owner `dbo` privileges</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="097df-109">如果沒有足夠權限的帳戶，嘗試對資料表進行變更時，就會出現錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="097df-109">If you attempt to make changes when using an account without sufficient privileges to make changes to tables, then an error message appears.</span></span>  
  
## <a name="creating-a-diagram"></a><span data-ttu-id="097df-110">建立圖表</span><span class="sxs-lookup"><span data-stu-id="097df-110">Creating a Diagram</span></span>  
  
#### <a name="to-create-a-new-database-diagram"></a><span data-ttu-id="097df-111">若要建立新的資料庫圖表</span><span class="sxs-lookup"><span data-stu-id="097df-111">To create a new database diagram</span></span>  
  
1.  <span data-ttu-id="097df-112">在 [檢視]  功能表上，按一下 [物件總管]  。</span><span class="sxs-lookup"><span data-stu-id="097df-112">On the **View** menu, click **Object Explorer**.</span></span>  
  
2.  <span data-ttu-id="097df-113">開啟 [資料庫] 節點，然後開啟 [[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]] 節點。</span><span class="sxs-lookup"><span data-stu-id="097df-113">Open the Databases node and then open the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] node.</span></span>  
  
3.  <span data-ttu-id="097df-114">以滑鼠右鍵按一下 [資料庫圖表] 節點，再選擇 [新增資料庫圖表]  。</span><span class="sxs-lookup"><span data-stu-id="097df-114">Right-click the Database Diagrams node and choose **New Database Diagram**.</span></span>  
  
     <span data-ttu-id="097df-115">如果資料庫沒有建立圖表所需的物件，便會顯示下列訊息： **此資料庫沒有使用資料庫圖表所需的一或多個支援物件。要建立資料庫物件嗎?**</span><span class="sxs-lookup"><span data-stu-id="097df-115">If the database does not have objects necessary to create diagrams, the following message appears: **This database does not have one or more of the support objects required to use database diagramming. Do you wish to create them?**</span></span> <span data-ttu-id="097df-116">選擇 [是]  。</span><span class="sxs-lookup"><span data-stu-id="097df-116">Choose **Yes**.</span></span>  
  
     <span data-ttu-id="097df-117">出現 [新增資料表]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="097df-117">The **Add Table** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="097df-118">選取 [AddressType (Person)]  和 [Address (Person)]  ，然後按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="097df-118">Select **AddressType (Person)** and **Address (Person)** and click **Add**.</span></span>  
  
     <span data-ttu-id="097df-119">兩個資料表便會加入至圖表。</span><span class="sxs-lookup"><span data-stu-id="097df-119">Two tables are added to the diagram.</span></span>  
  
5.  <span data-ttu-id="097df-120">關閉 [新增資料表]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="097df-120">Close the **Add Table** dialog box.</span></span>  
  
#### <a name="to-view-different-column-data"></a><span data-ttu-id="097df-121">若要檢視不同的資料行資料</span><span class="sxs-lookup"><span data-stu-id="097df-121">To view different column data</span></span>  
  
1.  <span data-ttu-id="097df-122">以滑鼠右鍵按一下 `Address` 資料表。</span><span class="sxs-lookup"><span data-stu-id="097df-122">Right-click the `Address` table.</span></span> <span data-ttu-id="097df-123">在快速鍵功能表上，指向 [資料表檢視]  ，然後按一下 [標準]  。</span><span class="sxs-lookup"><span data-stu-id="097df-123">On the shortcut menu, point to **Table View**, and then click **Standard**.</span></span>  
  
     <span data-ttu-id="097df-124">資料表方格會顯示三個資料行：[資料行名稱]  、[資料類型]  和 [允許 Null]  。</span><span class="sxs-lookup"><span data-stu-id="097df-124">The table grid shows three columns: **Column Name**, **Data Type**, and **Allow Nulls**.</span></span>  
  
2.  <span data-ttu-id="097df-125">以滑鼠右鍵按一下 `Address` 資料表、按一下 [資料表檢視]  ，再選取 [索引鍵]  。</span><span class="sxs-lookup"><span data-stu-id="097df-125">Right-click the `Address` table, click **Table View** and select **Keys**.</span></span>  
  
     <span data-ttu-id="097df-126">資料表方格會顯示一個資料行，內含資料表資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="097df-126">The table grid shows one column, with the table-column names.</span></span> <span data-ttu-id="097df-127">只有那些參與索引的資料行才會出現。</span><span class="sxs-lookup"><span data-stu-id="097df-127">Only those columns participating in indexes appear.</span></span>  
  
## <a name="creating-new-tables"></a><span data-ttu-id="097df-128">建立新資料表</span><span class="sxs-lookup"><span data-stu-id="097df-128">Creating New Tables</span></span>  
  
#### <a name="to-create-tables-within-diagram-designer"></a><span data-ttu-id="097df-129">若要在圖表設計工具中建立資料表</span><span class="sxs-lookup"><span data-stu-id="097df-129">To create tables within Diagram Designer</span></span>  
  
1.  <span data-ttu-id="097df-130">以滑鼠右鍵按一下現有資料表外側的 [圖表設計工具]，再選擇 [新增資料表]  。</span><span class="sxs-lookup"><span data-stu-id="097df-130">Right-click the Diagram Designer outside the existing tables and choose **New Table**.</span></span>  
  
2.  <span data-ttu-id="097df-131">在 [**選擇名稱**] 對話方塊中，按一下 **[確定]** 以接受預設名稱 `Table1` 。</span><span class="sxs-lookup"><span data-stu-id="097df-131">In the **Choose Name** dialog box, click **OK** to accept the default name `Table1`.</span></span>  
  
     <span data-ttu-id="097df-132">隨即出現新的資料表方格，其中會有三個資料行：[資料行名稱]  、[資料類型]  和 [允許 Null]  。</span><span class="sxs-lookup"><span data-stu-id="097df-132">A new table grid appears with three columns: **Column Name**, **Data Type**, and **Allow Nulls**.</span></span>  
  
3.  <span data-ttu-id="097df-133">將下列資訊新增至 `Table1` ：</span><span class="sxs-lookup"><span data-stu-id="097df-133">Add the following information to `Table1`:</span></span>  
  
    |<span data-ttu-id="097df-134">**資料行名稱**</span><span class="sxs-lookup"><span data-stu-id="097df-134">**Column Name**</span></span>|<span data-ttu-id="097df-135">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="097df-135">**Data Type**</span></span>|<span data-ttu-id="097df-136">**允許 Null**</span><span class="sxs-lookup"><span data-stu-id="097df-136">**Allow Nulls**</span></span>|  
    |---------------------|-------------------|---------------------|  
    |`T1col1`|`int`|<span data-ttu-id="097df-137">checked</span><span class="sxs-lookup"><span data-stu-id="097df-137">checked</span></span>|  
    |`T1col2`|`varchar(50)`|<span data-ttu-id="097df-138">checked</span><span class="sxs-lookup"><span data-stu-id="097df-138">checked</span></span>|  
    |`T1col3`|`float`|<span data-ttu-id="097df-139">已選取</span><span class="sxs-lookup"><span data-stu-id="097df-139">checked</span></span>|  
  
4.  <span data-ttu-id="097df-140">以滑鼠右鍵按一下 `T1col1`，再選取 [設定主索引鍵]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="097df-140">Right-click `T1col1` and select **Set Primary Key**.</span></span>  
  
     <span data-ttu-id="097df-141">資料行名稱旁邊將會出現索引鍵圖示。</span><span class="sxs-lookup"><span data-stu-id="097df-141">A key icon will appear beside the column name.</span></span>  
  
5.  <span data-ttu-id="097df-142">從 [檔案]\*\*\*\* 功能表中按一下 [儲存 Diagram1]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="097df-142">From the **File** menu, click **Save Diagram1**.</span></span>  
  
6.  <span data-ttu-id="097df-143">在 [**選擇名稱**] 對話方塊中，按一下 **[確定]** 以接受預設名稱 `Diagram1` 。</span><span class="sxs-lookup"><span data-stu-id="097df-143">In the **Choose Name** dialog box, click **OK** to accept the default name `Diagram1`.</span></span>  
  
7.  <span data-ttu-id="097df-144">[儲存]\*\*\*\* 對話方塊會顯示訊息，表示要將 `Table1` 儲存到資料庫。</span><span class="sxs-lookup"><span data-stu-id="097df-144">The **Save** dialog box appears with a message that `Table1` will be saved to the database.</span></span> <span data-ttu-id="097df-145">按一下 [是] 。</span><span class="sxs-lookup"><span data-stu-id="097df-145">Click **Yes**.</span></span>  
  
## <a name="modifying-table-structure"></a><span data-ttu-id="097df-146">修改資料表結構</span><span class="sxs-lookup"><span data-stu-id="097df-146">Modifying Table Structure</span></span>  
 <span data-ttu-id="097df-147">您可以在圖表設計工具中加入檢查條件約束，以及建立資料表間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="097df-147">You can add check constraints and make relationships between tables in Diagram Designer.</span></span>  
  
#### <a name="to-create-check-constraints"></a><span data-ttu-id="097df-148">若要建立檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="097df-148">To create check constraints</span></span>  
  
1.  <span data-ttu-id="097df-149">在 `Table1` 中，以滑鼠右鍵按一下 `T1col3` 資料列，再選擇 [檢查條件約束]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="097df-149">In `Table1`, right-click the `T1col3` row and choose **Check Constraints**.</span></span>  
  
     <span data-ttu-id="097df-150">此時會出現 [檢查條件約束]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="097df-150">The **Check Constraints** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="097df-151">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="097df-151">Click **Add**.</span></span>  
  
     <span data-ttu-id="097df-152">[選取的檢查條件約束]\*\*\*\* 清單中會出現新的條件約束，其預設名稱為 `CK_Table1`。</span><span class="sxs-lookup"><span data-stu-id="097df-152">A new constraint appears in the **Selected Check Constraint** list, with the default name `CK_Table1`.</span></span>  
  
3.  <span data-ttu-id="097df-153">選取方格中的 [運算式]\*\*\*\* 資料列，然後按一下省略符號按鈕。</span><span class="sxs-lookup"><span data-stu-id="097df-153">Select the **Expression** row in the grid and click the ellipsis button.</span></span>  
  
     <span data-ttu-id="097df-154">[檢查條件約束運算式]\*\*\*\* 對話方塊便會出現。</span><span class="sxs-lookup"><span data-stu-id="097df-154">The **Check Constraint Expression** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="097df-155">輸入 `T1col3 > 5` ，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="097df-155">Type `T1col3 > 5` and click **OK**.</span></span>  
  
     <span data-ttu-id="097df-156">`Table1` 現在便會有一項條件約束，規定所有輸入 `T1col3` 的值都必須大於 5。</span><span class="sxs-lookup"><span data-stu-id="097df-156">`Table1` now has a constraint that all values entered into `T1col3` must be greater than 5.</span></span>  
  
5.  <span data-ttu-id="097df-157">按一下 **關閉**。</span><span class="sxs-lookup"><span data-stu-id="097df-157">Click **Close**.</span></span>  
  
#### <a name="to-create-relationships-between-tables"></a><span data-ttu-id="097df-158">若要建立資料表之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="097df-158">To create relationships between tables</span></span>  
  
1.  <span data-ttu-id="097df-159">在圖表設計工具中建立新資料表，將其命名為 `Table2` ，並且包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="097df-159">Create a new table in Diagram designer named `Table2` with the following columns:</span></span>  
  
    |<span data-ttu-id="097df-160">**資料行名稱**</span><span class="sxs-lookup"><span data-stu-id="097df-160">**Column Name**</span></span>|<span data-ttu-id="097df-161">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="097df-161">**Data Type**</span></span>|<span data-ttu-id="097df-162">**允許 Null**</span><span class="sxs-lookup"><span data-stu-id="097df-162">**Allow Nulls**</span></span>|  
    |---------------------|-------------------|---------------------|  
    |`T2col1`|`int`|<span data-ttu-id="097df-163">未選取</span><span class="sxs-lookup"><span data-stu-id="097df-163">not checked</span></span>|  
    |`T2col2`|`varchar(50)`|<span data-ttu-id="097df-164">checked</span><span class="sxs-lookup"><span data-stu-id="097df-164">checked</span></span>|  
    |`T2col3`|`xml`|<span data-ttu-id="097df-165">checked</span><span class="sxs-lookup"><span data-stu-id="097df-165">checked</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="097df-166">外部索引鍵關聯性的主索引鍵端的資料行必須加入主索引鍵或唯一的條件約束。</span><span class="sxs-lookup"><span data-stu-id="097df-166">The columns on the primary key side of a foreign key relationship must participate in either a Primary Key or a Unique Constraint.</span></span>  
  
2.  <span data-ttu-id="097df-167">將 `T2col1` 拖曳到 `T1col1`。</span><span class="sxs-lookup"><span data-stu-id="097df-167">Drag `T2col1` to `T1col1`.</span></span>  
  
     <span data-ttu-id="097df-168">會出現兩個對話方塊：背景中的 [外部索引鍵關聯性]\*\*\*\* 以及前景中的 [資料表與資料行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="097df-168">Two dialog boxes appear: **Foreign Key Relationship** in the background and **Tables and Columns** in the foreground.</span></span>  
  
3.  <span data-ttu-id="097df-169">按一下 [確定]\*\*\*\* 以儲存新的關聯性。</span><span class="sxs-lookup"><span data-stu-id="097df-169">Click **OK** to save the new relationship.</span></span>  
  
4.  <span data-ttu-id="097df-170">再按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="097df-170">Click **OK** again.</span></span>  
  
## <a name="creating-indexes"></a><span data-ttu-id="097df-171">建立索引</span><span class="sxs-lookup"><span data-stu-id="097df-171">Creating Indexes</span></span>  
 <span data-ttu-id="097df-172">您可以在大部分的資料類型上建立索引，包括 XML。</span><span class="sxs-lookup"><span data-stu-id="097df-172">You can create indexes on most types of data, including XML.</span></span>  
  
#### <a name="to-create-a-standard-index"></a><span data-ttu-id="097df-173">若要建立標準索引</span><span class="sxs-lookup"><span data-stu-id="097df-173">To create a standard index</span></span>  
  
1.  <span data-ttu-id="097df-174">以滑鼠右鍵按一下 `Table1`，再選擇 [索引/索引鍵]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="097df-174">Right-click `Table1` and choose **Indexes/Keys**.</span></span>  
  
     <span data-ttu-id="097df-175">[索引/索引鍵]\*\*\*\* 對話方塊便會出現。</span><span class="sxs-lookup"><span data-stu-id="097df-175">The **Indexes/Keys** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="097df-176">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="097df-176">Click **Add**.</span></span>  
  
     <span data-ttu-id="097df-177">[選取的主/唯一索引鍵或索引]\*\*\*\* 清單中會出現新的索引，其預設名稱類似 `IX_Table1`。</span><span class="sxs-lookup"><span data-stu-id="097df-177">A new index appears in the **Selected Primary/Unique Key or Index** list, with a default name similar to `IX_Table1`.</span></span>  
  
3.  <span data-ttu-id="097df-178">選取 [資料行]\*\*\*\* 資料列，然後按一下省略符號按鈕。</span><span class="sxs-lookup"><span data-stu-id="097df-178">Select the **Columns** row and click the ellipsis button.</span></span>  
  
     <span data-ttu-id="097df-179">[索引資料行]\*\*\*\* 對話方塊便會出現。</span><span class="sxs-lookup"><span data-stu-id="097df-179">The **Index Columns** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="097df-180">按一下 [資料行名稱]\*\*\*\* 下方的下拉箭頭，然後選取 `T1col2`。</span><span class="sxs-lookup"><span data-stu-id="097df-180">Click the drop-down arrow under **Column Name** and select `T1col2`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="097df-181">您選取 `T1col2` 下面的資料格，再選擇另一個資料行名稱，即可將其他資料行加入至這個索引。</span><span class="sxs-lookup"><span data-stu-id="097df-181">You may add additional columns to this index by selecting the cell below `T1col2` and choosing another column name.</span></span>  
  
5.  <span data-ttu-id="097df-182">按一下 [確定]\*\*\*\* 以儲存這個索引。</span><span class="sxs-lookup"><span data-stu-id="097df-182">Click **OK** to save this index.</span></span>  
  
6.  <span data-ttu-id="097df-183">按一下 [索引/索引鍵]\*\*\*\* 對話方塊中的 [關閉]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="097df-183">Click **Close** in the **Indexes/Keys** dialog box.</span></span>  
  
#### <a name="to-create-an-xml-index"></a><span data-ttu-id="097df-184">若要建立 XML 索引</span><span class="sxs-lookup"><span data-stu-id="097df-184">To create an XML index</span></span>  
  
1.  <span data-ttu-id="097df-185">以滑鼠右鍵按一下 `T2col1`，再選擇 [設定主索引鍵]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="097df-185">Right-click `T2col1` and choose **Set Primary Key**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="097df-186">加入 XML 索引時，需要將資料表中的另一個資料行設定為叢集主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="097df-186">Adding an XML index requires that another column in the table be set as a clustered primary key.</span></span>  
  
2.  <span data-ttu-id="097df-187">以滑鼠右鍵按一下 `Table2` 中的 `T2col3` 資料列，再選取 [XML 索引]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="097df-187">Right-click the `T2col3` row in `Table2` and select **XML Indexes**.</span></span>  
  
     <span data-ttu-id="097df-188">[XML 索引]\*\*\*\* 對話方塊便會出現。</span><span class="sxs-lookup"><span data-stu-id="097df-188">The **XML Indexes** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="097df-189">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="097df-189">Click **Add**.</span></span>  
  
     <span data-ttu-id="097df-190">便會將含有預設值的 XML 索引新增至 [選取的 XML 索引]\*\*\*\* 清單。</span><span class="sxs-lookup"><span data-stu-id="097df-190">An XML index with default values will be added to the **Selected XML Index** list.</span></span>  
  
4.  <span data-ttu-id="097df-191">按一下 **關閉**。</span><span class="sxs-lookup"><span data-stu-id="097df-191">Click **Close**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="097df-192">XML 索引會針對個別資料行建立。</span><span class="sxs-lookup"><span data-stu-id="097df-192">XML indexes are created per-column.</span></span> <span data-ttu-id="097df-193">第一個 XML 索引是主索引；任何額外的索引則為次要索引。</span><span class="sxs-lookup"><span data-stu-id="097df-193">The first XML index is primary; any additional indexes are secondary.</span></span>  
  
## <a name="saving-the-diagram"></a><span data-ttu-id="097df-194">儲存圖表</span><span class="sxs-lookup"><span data-stu-id="097df-194">Saving the Diagram</span></span>  
 <span data-ttu-id="097df-195">您對圖表所做的變更要等到儲存之後，才會傳送到資料庫。</span><span class="sxs-lookup"><span data-stu-id="097df-195">All of the changes you make to a diagram are not posted to the database until you save it.</span></span> <span data-ttu-id="097df-196">如果有問題或衝突發生，就會顯示帶有詳細資訊的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="097df-196">If there are problems or conflicts, a dialog box appears with more information.</span></span>  
  
#### <a name="to-save-a-database-diagram"></a><span data-ttu-id="097df-197">若要儲存資料庫圖表</span><span class="sxs-lookup"><span data-stu-id="097df-197">To save a database diagram</span></span>  
  
1.  <span data-ttu-id="097df-198">在 [檔案]\*\*\*\* 功能表上選取 [儲存 Diagram1]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="097df-198">On the **File** menu, select **Save Diagram1**.</span></span>  
  
     <span data-ttu-id="097df-199">此時會出現 [儲存]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="097df-199">The **Save** dialog box appears.</span></span> <span data-ttu-id="097df-200">如果選取了 [受影響資料表的警告]\*\*\*\*，便會列出有關新的或變更的資料表的資訊。</span><span class="sxs-lookup"><span data-stu-id="097df-200">If **Warn about Tables Affected** is selected, information about new or changed tables is listed.</span></span>  
  
2.  <span data-ttu-id="097df-201">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="097df-201">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="097df-202">如果發生任何錯誤，[儲存後告知]\*\*\*\* 對話方塊會顯示錯誤及其原因。</span><span class="sxs-lookup"><span data-stu-id="097df-202">If any errors occurred, the **Post-Save Notifications** dialog box appears with the errors and their causes.</span></span> <span data-ttu-id="097df-203">修正錯誤並再一次儲存圖表。</span><span class="sxs-lookup"><span data-stu-id="097df-203">Fix the errors and save the diagram again.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="097df-204">後續步驟</span><span class="sxs-lookup"><span data-stu-id="097df-204">Next Steps</span></span>  
 <span data-ttu-id="097df-205">這是含有兩個現有的及兩個新的資料表的基本圖表，但是已經具體而微地說明其圖表化現有資料庫或透過視覺化方式建立新結構描述的潛力。</span><span class="sxs-lookup"><span data-stu-id="097df-205">This is a basic diagram with just two existing and two new tables, but it illustrates the potential for diagramming an existing database or creating a new schema visually.</span></span> <span data-ttu-id="097df-206">建議您進一步研究的部分包括：</span><span class="sxs-lookup"><span data-stu-id="097df-206">Suggestions for more exploration include:</span></span>  
  
-   <span data-ttu-id="097df-207">建立含有相關資料表群組的新圖表</span><span class="sxs-lookup"><span data-stu-id="097df-207">Create new diagrams containing groups of related tables</span></span>  
  
-   <span data-ttu-id="097df-208">自訂每個資料表顯示的資訊數量</span><span class="sxs-lookup"><span data-stu-id="097df-208">Customize the amount of information shown for each table</span></span>  
  
-   <span data-ttu-id="097df-209">變更配置以及加入註解</span><span class="sxs-lookup"><span data-stu-id="097df-209">Change the layout and add annotations</span></span>  
  
-   <span data-ttu-id="097df-210">將圖表複製為點陣圖</span><span class="sxs-lookup"><span data-stu-id="097df-210">Copy the diagram to a bitmap</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="097df-211">另請參閱</span><span class="sxs-lookup"><span data-stu-id="097df-211">See Also</span></span>  
 <span data-ttu-id="097df-212">[自訂圖表中顯示的資訊量 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="097df-212">[Customize the Amount of Information Displayed in Diagrams &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="097df-213">[設定資料庫關係圖設計工具 &#40;Visual Database Tools&#41;](set-up-database-diagram-designer-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="097df-213">[Set Up Database Diagram Designer &#40;Visual Database Tools&#41;](set-up-database-diagram-designer-visual-database-tools.md) </span></span>  
 <span data-ttu-id="097df-214">[將資料表加入至圖表 &#40;Visual Database Tools&#41;](add-tables-to-diagrams-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="097df-214">[Add Tables to Diagrams &#40;Visual Database Tools&#41;](add-tables-to-diagrams-visual-database-tools.md) </span></span>  
 <span data-ttu-id="097df-215">[在圖表上建立資料表之間的關聯性 &#40;Visual Database Tools&#41;](create-relationships-between-tables-on-a-diagram-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="097df-215">[Create Relationships Between Tables on a Diagram &#40;Visual Database Tools&#41;](create-relationships-between-tables-on-a-diagram-visual-database-tools.md) </span></span>  
 <span data-ttu-id="097df-216">[建立 XML 索引](../../relational-databases/xml/create-xml-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="097df-216">[Create XML Indexes](../../relational-databases/xml/create-xml-indexes.md) </span></span>  
 <span data-ttu-id="097df-217">[將資料庫關係圖的影像複製到剪貼簿 &#40;Visual Database Tools&#41;](copy-an-image-of-a-database-diagram-to-the-clipboard-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="097df-217">[Copy an Image of a Database Diagram to the Clipboard &#40;Visual Database Tools&#41;](copy-an-image-of-a-database-diagram-to-the-clipboard-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="097df-218">使用圖表配置 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="097df-218">Work with Diagram Layout &#40;Visual Database Tools&#41;</span></span>](work-with-diagram-layout-visual-database-tools.md)  
  
  
