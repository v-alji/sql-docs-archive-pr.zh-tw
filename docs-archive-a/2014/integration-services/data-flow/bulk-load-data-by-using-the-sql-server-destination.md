---
title: 使用 SQL Server 目的地來大量載入資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server destination
- loading data
- destinations [Integration Services], SQL Server
- inserting data
- bulk load [Integration Services]
ms.assetid: 8f982f85-a82e-4e2d-9cd8-cd2f85402d8e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 92ed530ae849f7a4ce123cded421ac0cd0c411ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595219"
---
# <a name="bulk-load-data-by-using-the-sql-server-destination"></a><span data-ttu-id="70cbc-102">使用 SQL Server 目的地來大量載入資料</span><span class="sxs-lookup"><span data-stu-id="70cbc-102">Bulk Load Data by Using the SQL Server Destination</span></span>
  <span data-ttu-id="70cbc-103">若要加入及設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目的地，封裝至少必須包含一個「資料流程」工作及一個資料來源。</span><span class="sxs-lookup"><span data-stu-id="70cbc-103">To add and configure a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, the package must already include at least one Data Flow task and a data source.</span></span>  
  
### <a name="to-load-data-using-a-sql-server-destination"></a><span data-ttu-id="70cbc-104">使用 SQL Server 目的地載入資料</span><span class="sxs-lookup"><span data-stu-id="70cbc-104">To load data using a SQL Server destination</span></span>  
  
1.  <span data-ttu-id="70cbc-105">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="70cbc-105">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="70cbc-106">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="70cbc-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="70cbc-107">按一下 [資料流程] 索引標籤，然後將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目的地從 [工具箱] 拖曳到設計介面。</span><span class="sxs-lookup"><span data-stu-id="70cbc-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination to the design surface.</span></span>  
  
4.  <span data-ttu-id="70cbc-108">將連接子拖曳到目的地，以便將目的地連接到資料流程中的來源或前一個轉換。</span><span class="sxs-lookup"><span data-stu-id="70cbc-108">Connect the destination to a source or a previous transformation in the data flow by dragging a connector to the destination.</span></span>  
  
5.  <span data-ttu-id="70cbc-109">按兩下目的地。</span><span class="sxs-lookup"><span data-stu-id="70cbc-109">Double-click the destination.</span></span>  
  
6.  <span data-ttu-id="70cbc-110">在 [連線管理員] 頁面上的 [SQL Server 目的地編輯器] 中，選取現有的 OLE DB 連線管理員，或按一下 [新增] 以新建連線管理員。</span><span class="sxs-lookup"><span data-stu-id="70cbc-110">In the **SQL Server Destination Editor**, on the **Connection Manager** page, select an existing OLE DB connection manager or click **New** to create a new connection manager.</span></span> <span data-ttu-id="70cbc-111">如需相關資訊，請參閱 [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="70cbc-111">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
7.  <span data-ttu-id="70cbc-112">若要指定載入資料的資料表或檢視，請執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="70cbc-112">To specify the table or view into which to load the data, do one of the following:</span></span>  
  
    -   <span data-ttu-id="70cbc-113">選取現有的資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="70cbc-113">Select an existing table or view.</span></span>  
  
    -   <span data-ttu-id="70cbc-114">按一下 [新增]  ，然後在 [建立資料表]  對話方塊中撰寫建立資料表或檢視的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="70cbc-114">Click **New**, and in the **Create Table** dialog boxwrite an SQL statement that creates a table or view.</span></span>  
  
        > [!NOTE]  
        >  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="70cbc-115">會根據連接的資料來源來產生預設 CREATE TABLE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="70cbc-115">generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="70cbc-116">這個預設 CREATE TABLE 陳述式將不會包含 FILESTREAM 屬性，即使來源資料表包含有宣告 FILESTREAM 屬性的資料行亦然。</span><span class="sxs-lookup"><span data-stu-id="70cbc-116">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="70cbc-117">若要執行具有 FILESTREAM 屬性的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 元件，請先在目的地資料庫上實作 FILESTREAM 儲存體。</span><span class="sxs-lookup"><span data-stu-id="70cbc-117">To run an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="70cbc-118">然後在 **[建立資料表]** 對話方塊中，將 FILESTREAM 屬性加入至 CREATE TABLE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="70cbc-118">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="70cbc-119">如需詳細資訊，請參閱[二進位大型物件 &#40;Blob&#41; 資料 &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="70cbc-119">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
8.  <span data-ttu-id="70cbc-120">按一下 [對應]  ，然後將一個清單中的資料行拖曳到另一個清單，來將 [可用的輸入資料行]  清單中的資料行對應到 [可用的目的地資料行]  清單中的資料行。</span><span class="sxs-lookup"><span data-stu-id="70cbc-120">Click **Mappings** and map columns from the **Available Input Columns** list to columns in the **Available Destination Columns** list by dragging columns from one list to another.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="70cbc-121">目的地會自動對應名稱相同的資料行。</span><span class="sxs-lookup"><span data-stu-id="70cbc-121">The destination automatically maps same-named columns.</span></span>  
  
9. <span data-ttu-id="70cbc-122">按一下 [進階]  ，然後設定大量載入選項：[保留識別]  、[保留 Null]  、[資料表鎖定]  、[檢查條件約束]  和 [引發觸發程序]  。</span><span class="sxs-lookup"><span data-stu-id="70cbc-122">Click **Advanced** and set the bulk load options: **Keep identity**, **Keep nulls**, **Table lock**, **Check constraints**, and **Fire triggers**.</span></span>  
  
     <span data-ttu-id="70cbc-123">(選擇性) 指定要插入的第一個和最後一個輸入資料列，插入作業停止之前發生的最大錯誤數目，以及排序插入的資料行。</span><span class="sxs-lookup"><span data-stu-id="70cbc-123">Optionally, specify the first and last input rows to insert, the maximum number of errors that can occur before the insert operation stops, and the columns on which the insert is sorted.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="70cbc-124">排序次序是由資料行列出的順序決定的。</span><span class="sxs-lookup"><span data-stu-id="70cbc-124">The sort order is determined by the order in which the columns are listed.</span></span>  
  
10. <span data-ttu-id="70cbc-125">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="70cbc-125">Click **OK**.</span></span>  
  
11. <span data-ttu-id="70cbc-126">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="70cbc-126">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70cbc-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70cbc-127">See Also</span></span>  
 <span data-ttu-id="70cbc-128">[SQL Server Destination](sql-server-destination.md) </span><span class="sxs-lookup"><span data-stu-id="70cbc-128">[SQL Server Destination](sql-server-destination.md) </span></span>  
 <span data-ttu-id="70cbc-129">[Integration Services 轉換](transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="70cbc-129">[Integration Services Transformations](transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="70cbc-130">[Integration Services 路徑](integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="70cbc-130">[Integration Services Paths](integration-services-paths.md) </span></span>  
 [<span data-ttu-id="70cbc-131">資料流程工作</span><span class="sxs-lookup"><span data-stu-id="70cbc-131">Data Flow Task</span></span>](../control-flow/data-flow-task.md)  
  
  
