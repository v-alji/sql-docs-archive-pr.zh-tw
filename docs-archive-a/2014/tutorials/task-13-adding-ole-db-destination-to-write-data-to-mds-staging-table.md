---
title: 工作13：新增 OLE DB 目的地，以將資料寫入 MDS 臨時表 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: e6c67fa9-bb52-44a9-82f6-d86551cf12b2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 77799782518a3be2441b4c461467e3132781298d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698974"
---
# <a name="task-13-adding-ole-db-destination-to-write-data-to-mds-staging-table"></a><span data-ttu-id="3734e-102">工作 13：新增 OLE DB 目的地來將資料寫入 MDS 暫存資料表</span><span class="sxs-lookup"><span data-stu-id="3734e-102">Task 13: Adding OLE DB Destination to Write Data to MDS Staging Table</span></span>
  <span data-ttu-id="3734e-103">現在您已將**ImportType**和**BatchTag**值新增至所有記錄，您已準備好將它們傳送至 MDS 進行預備。</span><span class="sxs-lookup"><span data-stu-id="3734e-103">Now that you have added **ImportType** and **BatchTag** values to all records, you are ready to send them over to MDS for staging.</span></span> <span data-ttu-id="3734e-104">在這項工作中，您會使用 OLE DB 目的地，將資料寫入**stg.< 中。 supplier_Leaf**臨時表。</span><span class="sxs-lookup"><span data-stu-id="3734e-104">In this task, you use the OLE DB Destination to write the data into **stg.supplier_Leaf** staging table.</span></span>  
  
1.  <span data-ttu-id="3734e-105">將 [ **SSIS 工具箱**] 中 [**其他目的地**] 區段的 [ **OLE DB 目的地**] 拖曳至 [**資料流程**] 索引標籤，然後將它放置在 [**加入 MDS 所需的欄位**</span><span class="sxs-lookup"><span data-stu-id="3734e-105">Drag **OLE DB Destination** from **Other Destinations** section in the **SSIS Toolbox** to the **Data Flow** tab and drop it under **Add Columns Required by MDS**.</span></span>  
  
2.  <span data-ttu-id="3734e-106">以滑鼠右鍵**按一下 [資料流程**] 索引標籤中**OLE DB 目的地**]，然後按一下 [**重新命名**]。</span><span class="sxs-lookup"><span data-stu-id="3734e-106">Right-click **OLE DB Destination** in the **Data Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="3734e-107">輸入**將供應商資料寫入 MDS 臨時表**，然後按**enter**。</span><span class="sxs-lookup"><span data-stu-id="3734e-107">Type **Write Supplier Data to MDS Staging Table** and press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="3734e-108">連接**Mds 所需的新增資料行**，以使用藍色連接器將**供應商資料寫入 mds 臨時表**。</span><span class="sxs-lookup"><span data-stu-id="3734e-108">Connect the **Add Columns Required by MDS** to **Write Supplier Data to MDS Staging Table** using the blue connector.</span></span>  
  
4.  <span data-ttu-id="3734e-109">按兩下 **[資料流程**] 索引標籤中的 [**將供應商資料寫入 MDS 臨時表**]。</span><span class="sxs-lookup"><span data-stu-id="3734e-109">Double-click **Write Supplier Data to MDS Staging Table** in the **Data Flow** tab.</span></span>  
  
5.  <span data-ttu-id="3734e-110">在 [ **OLE DB 目的地編輯器**] 對話方塊中，確認\*\* (本機) MDS\*\* (或**localhost。** 已針對 [ **OLE DB 連接管理員**] 欄位選取 MDS) 。</span><span class="sxs-lookup"><span data-stu-id="3734e-110">In the **OLE DB Destination Editor** Dialog box, make sure that **(local).MDS** (or **localhost.MDS**) is selected for the **OLE DB Connection Manager** field.</span></span>  
  
6.  <span data-ttu-id="3734e-111">選取 [ **stg.<]。Supplier_Leaf**資料表**或視圖名稱**清單中的資料表。</span><span class="sxs-lookup"><span data-stu-id="3734e-111">Select **stg.Supplier_Leaf** table from the list of **Name of the table or the view**.</span></span>  
  
     <span data-ttu-id="3734e-112">![OLEDB 目的地編輯器](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-01.jpg "OLEDB 目的地編輯器")</span><span class="sxs-lookup"><span data-stu-id="3734e-112">![OLEDB Destination Editor](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-01.jpg "OLEDB Destination Editor")</span></span>  
  
7.  <span data-ttu-id="3734e-113">按一下左側功能表**上的 [** 對應]，切換至 [**對應**] 頁面。</span><span class="sxs-lookup"><span data-stu-id="3734e-113">Switch to the **Mappings** page by clicking **Mapping** on the menu on left.</span></span>  
  
8.  <span data-ttu-id="3734e-114">對應**輸入**和**目的地**資料行，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="3734e-114">Map **input** and **destination** columns as shown in the following table.</span></span>  
  
     <span data-ttu-id="3734e-115">![OLEDB 目的地編輯器 - 對應](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-02.jpg "OLEDB 目的地編輯器 - 對應")</span><span class="sxs-lookup"><span data-stu-id="3734e-115">![OLEDB Destination Editor - Mappings](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-02.jpg "OLEDB Destination Editor - Mappings")</span></span>  
  
9. <span data-ttu-id="3734e-116">請確認您使用的是輸入資料行的 **_Output**資料行，而不是 **_Status**或 **_Source**資料行。</span><span class="sxs-lookup"><span data-stu-id="3734e-116">Confirm that you are using **_Output** columns for Input Columns, not the **_Status** or **_Source** columns.</span></span> <span data-ttu-id="3734e-117">**_Output**資料行包含 DQS 清理的輸出值。</span><span class="sxs-lookup"><span data-stu-id="3734e-117">**_Output** columns contain the output values from DQS Cleansing.</span></span>  
  
10. <span data-ttu-id="3734e-118">按一下 **[確定]** 以關閉 [ **OLE DB 目的地編輯器**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3734e-118">Click **OK** to close the **OLE DB Destination Editor** dialog box.</span></span>  
  
11. <span data-ttu-id="3734e-119">資料流程應該類似下圖。</span><span class="sxs-lookup"><span data-stu-id="3734e-119">The data flow should like the following image.</span></span>  
  
     <span data-ttu-id="3734e-120">![完成的資料流程](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-03.jpg "完成的資料流程")</span><span class="sxs-lookup"><span data-stu-id="3734e-120">![Completed Data Flow](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-03.jpg "Completed Data Flow")</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="3734e-121">後續步驟</span><span class="sxs-lookup"><span data-stu-id="3734e-121">Next Step</span></span>  
 [<span data-ttu-id="3734e-122">工作 14：將執行 SQL 工作新增至控制流程，為 MDS 執行預存程序</span><span class="sxs-lookup"><span data-stu-id="3734e-122">Task 14: Adding Execute SQL Task to Control Flow to Run the Stored Procedure for MDS</span></span>](../../2014/tutorials/task-14-add-execute-to-control-flow-run-mds-stored-procedure.md)  
  
  
