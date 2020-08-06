---
title: 擷取與了解變更資料 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],retrieving data
ms.assetid: af366697-6942-42bb-aea5-18fdef018965
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 62f60bf4a79c39b4f0cb7d1ba8fb3f52680a1f11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704349"
---
# <a name="retrieve-and-understand-the-change-data"></a><span data-ttu-id="1814b-102">擷取與了解變更資料</span><span class="sxs-lookup"><span data-stu-id="1814b-102">Retrieve and Understand the Change Data</span></span>
  <span data-ttu-id="1814b-103">在執行累加式變更資料載入之 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝的資料流程中，第一個工作是執行可擷取變更資料的查詢。</span><span class="sxs-lookup"><span data-stu-id="1814b-103">In the data flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the first task is to run the query that retrieves the change data.</span></span> <span data-ttu-id="1814b-104">您可以在「資料流程」工作的來源元件內部執行這個查詢。</span><span class="sxs-lookup"><span data-stu-id="1814b-104">You execute this query inside a source component in a Data Flow task.</span></span> <span data-ttu-id="1814b-105">然後，您可以使用下游轉換和目的地，將變更資料套用到您的目的地。</span><span class="sxs-lookup"><span data-stu-id="1814b-105">You can then use downstream transformations and destinations to apply the change data to your destination.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1814b-106">建立包含資料表值函式的查詢是建立執行累加式變更資料載入之封裝程序的第三個步驟。</span><span class="sxs-lookup"><span data-stu-id="1814b-106">The creation of a query that contains a table-valued function is the third step in the process of creating a package that performs an incremental load of change data.</span></span> <span data-ttu-id="1814b-107">如需此查詢的詳細資訊，請參閱 [建立函數以擷取變更資料](create-the-function-to-retrieve-the-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="1814b-107">For more information about this query, see, [Create the Function to Retrieve the Change Data](create-the-function-to-retrieve-the-change-data.md).</span></span> <span data-ttu-id="1814b-108">如需建立可執行累加式變更資料載入之封裝的完整程序描述，請參閱[異動資料擷取 &#40;SSIS&#41;](change-data-capture-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="1814b-108">For a description of the overall process for creating a package that performs an incremental load of change data, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="adding-the-data-flow-task"></a><span data-ttu-id="1814b-109">加入資料流程工作</span><span class="sxs-lookup"><span data-stu-id="1814b-109">Adding the Data Flow Task</span></span>  
 <span data-ttu-id="1814b-110">在封裝的資料流程中，您可以擷取異動資料、根據發生之變更的類型分隔資料列，然後將變更套用到目的地。</span><span class="sxs-lookup"><span data-stu-id="1814b-110">In the data flow of the package, you retrieve the change data, separate the rows based on the type of change that occurred, and then apply the changes to the destination.</span></span>  
  
#### <a name="to-add-a-data-flow-task-to-the-package"></a><span data-ttu-id="1814b-111">將資料流程工作加入至封裝</span><span class="sxs-lookup"><span data-stu-id="1814b-111">To add a Data Flow task to the package</span></span>  
  
1.  <span data-ttu-id="1814b-112">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的 [控制流程]  索引標籤上，加入「資料流程」工作。</span><span class="sxs-lookup"><span data-stu-id="1814b-112">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], on the **Control Flow** tab, add a Data Flow task.</span></span>  
  
2.  <span data-ttu-id="1814b-113">將準備查詢字串的先前工作連接到「資料流程」工作。</span><span class="sxs-lookup"><span data-stu-id="1814b-113">Connect the preceding task that prepared the query string to the Data Flow task.</span></span>  
  
## <a name="configuring-the-source-component-to-query-for-changes"></a><span data-ttu-id="1814b-114">設定來源元件以查詢變更</span><span class="sxs-lookup"><span data-stu-id="1814b-114">Configuring the Source Component to Query for Changes</span></span>  
 <span data-ttu-id="1814b-115">來源元件會使用以變數準備並儲存的查詢字串，呼叫可擷取變更資料的資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="1814b-115">The source component uses the query string that was prepared and stored in a variable to calls the table-valued function that retrieves the changed data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1814b-116">如需以變數準備並儲存之查詢字串的詳細資訊，請參閱 [準備查詢變更資料](prepare-to-query-for-the-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="1814b-116">For more information about the query string that was prepared and stored in a variable, see [Prepare to Query for the Change Data](prepare-to-query-for-the-change-data.md).</span></span> <span data-ttu-id="1814b-117">如需擷取變更資料之資料表值函式的詳細資訊，請參閱 [建立函數以擷取變更資料](create-the-function-to-retrieve-the-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="1814b-117">For more information about the table-valued function that retrieves the change data, see [Create the Function to Retrieve the Change Data](create-the-function-to-retrieve-the-change-data.md).</span></span>  
  
#### <a name="to-configure-an-ole-db-source-to-retrieve-the-change-data"></a><span data-ttu-id="1814b-118">設定 OLE DB 來源以擷取變更資料</span><span class="sxs-lookup"><span data-stu-id="1814b-118">To configure an OLE DB source to retrieve the change data</span></span>  
  
1.  <span data-ttu-id="1814b-119">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的 [資料流程]  索引標籤上，加入 OLE DB 來源。</span><span class="sxs-lookup"><span data-stu-id="1814b-119">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], on the **Data Flow** tab, add an OLE DB source.</span></span>  
  
2.  <span data-ttu-id="1814b-120">在 [OLE DB 來源編輯器]  的 [連線管理員]  頁面上，選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="1814b-120">In the **OLE DB Source Editor**, on the **Connection Manager** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="1814b-121">將有效的連接設定到來源資料庫。</span><span class="sxs-lookup"><span data-stu-id="1814b-121">Configure a valid connection to the source database.</span></span>  
  
    2.  <span data-ttu-id="1814b-122">針對 [資料存取模式]  ，選取 [來自變數的 SQL 命令]  。</span><span class="sxs-lookup"><span data-stu-id="1814b-122">For **Data access mode**, select **SQL command from variable**.</span></span>  
  
    3.  <span data-ttu-id="1814b-123">針對 [變數名稱]  ，選取 [User::SqlDataQuery]  。</span><span class="sxs-lookup"><span data-stu-id="1814b-123">For **Variable name**, select **User::SqlDataQuery**.</span></span>  
  
3.  <span data-ttu-id="1814b-124">在 [OLE DB 來源編輯器]  的 [資料行]  頁面上，確定您需要的所有資料行都對應到輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="1814b-124">In the **OLE DB Source Editor**, on the **Columns** page, make sure that all the columns that you want are mapped to output columns.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="1814b-125">後續步驟</span><span class="sxs-lookup"><span data-stu-id="1814b-125">Next Step</span></span>  
 <span data-ttu-id="1814b-126">設定 OLE DB 來源以擷取變更資料後，下一個步驟是開始在封裝中設計資料流程。</span><span class="sxs-lookup"><span data-stu-id="1814b-126">After you have configured an OLE DB source to retrieve the change data, the next step is to start designing the data flow in the package.</span></span>  
  
 <span data-ttu-id="1814b-127">**下一個主題：** [處理插入、更新與刪除作業](process-inserts-updates-and-deletes.md)</span><span class="sxs-lookup"><span data-stu-id="1814b-127">**Next topic:** [Process Inserts, Updates, and Deletes](process-inserts-updates-and-deletes.md)</span></span>  
  
  
