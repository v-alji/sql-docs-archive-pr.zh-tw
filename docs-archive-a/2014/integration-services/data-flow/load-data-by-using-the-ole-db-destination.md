---
title: 使用 OLE DB 目的地來載入資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- loading data
- OLE DB destination [Integration Services]
- destinations [Integration Services], OLE DB
ms.assetid: 78899498-725e-4300-a7af-f983f4ea384b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 43e8d1123ae91d9e68c00fbe3e05c490383afe0c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700090"
---
# <a name="load-data-by-using-the-ole-db-destination"></a><span data-ttu-id="a7b54-102">使用 OLE DB 目的地來載入資料</span><span class="sxs-lookup"><span data-stu-id="a7b54-102">Load Data by Using the OLE DB Destination</span></span>
  <span data-ttu-id="a7b54-103">若要加入及設定 OLE DB 目的地，封裝必須已包括至少一個「資料流程」工作與來源。</span><span class="sxs-lookup"><span data-stu-id="a7b54-103">To add and configure an OLE DB destination, the package must already include at least one Data Flow task and a source.</span></span>  
  
### <a name="to-load-data-using-an-ole-db-destination"></a><span data-ttu-id="a7b54-104">使用 OLE DB 目的地載入資料</span><span class="sxs-lookup"><span data-stu-id="a7b54-104">To load data using an OLE DB destination</span></span>  
  
1.  <span data-ttu-id="a7b54-105">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="a7b54-105">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="a7b54-106">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="a7b54-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="a7b54-107">按一下 [資料流程]  索引標籤，然後將 OLE DB 目的地從 [工具箱]  拖曳至設計介面。</span><span class="sxs-lookup"><span data-stu-id="a7b54-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the OLE DB destination to the design surface.</span></span>  
  
4.  <span data-ttu-id="a7b54-108">將連接子從資料來源或前一個轉換拖曳至目的地，以便將 OLE DB 目的地連接到資料流程。</span><span class="sxs-lookup"><span data-stu-id="a7b54-108">Connect the OLE DB destination to the data flow by dragging a connector from a data source or a previous transformation to the destination.</span></span>  
  
5.  <span data-ttu-id="a7b54-109">按兩下 OLE DB 目的地。</span><span class="sxs-lookup"><span data-stu-id="a7b54-109">Double-click the OLE DB destination.</span></span>  
  
6.  <span data-ttu-id="a7b54-110">在 [連接管理員] 頁面的 [OLE DB 目的地編輯器] 對話方塊中，選取現有的 OLE DB 連接管理員，或按一下 [新增] 以新建連接管理員。</span><span class="sxs-lookup"><span data-stu-id="a7b54-110">In the **OLE DB Destination Editor** dialog box, on the **Connection Manager** page, select an existing OLE DB connection manager or click **New** to create a new connection manager.</span></span> <span data-ttu-id="a7b54-111">如需相關資訊，請參閱 [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="a7b54-111">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
7.  <span data-ttu-id="a7b54-112">選取資料存取方法：</span><span class="sxs-lookup"><span data-stu-id="a7b54-112">Select the data access method:</span></span>  
  
    -   <span data-ttu-id="a7b54-113">**資料表或檢視** ：在資料庫中選取包含資料的資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="a7b54-113">**Table or view** Select a table or view in the database that contains the data.</span></span>  
  
    -   <span data-ttu-id="a7b54-114">**資料表或檢視 - 快速載入**：在資料庫中選取包含資料的資料表或檢視，然後設定快速載入選項：[保留識別]  、[保留 Null]  、[資料表鎖定]  、[檢查條件約束]  、[每批次的資料列]  或 [插入認可大小上限]  。</span><span class="sxs-lookup"><span data-stu-id="a7b54-114">**Table or view - fast load** Select a table or view in the database that contains the data, and then set the fast-load options: **Keep identity**, **Keep null**, **Table lock**, **Check constraint**, **Rows per batch**, or **Maximum insert commit size**.</span></span>  
  
    -   <span data-ttu-id="a7b54-115">**資料表名稱或檢視名稱變數** ：選取使用者自訂變數，該變數包含資料庫中資料表或檢視的名稱。</span><span class="sxs-lookup"><span data-stu-id="a7b54-115">**Table name or view name variable** Select the user-defined variable that contains the name of a table or view in the database.</span></span>  
  
    -   <span data-ttu-id="a7b54-116">**資料表名稱或檢視名稱變數 - 快速載入** ：選取使用者自訂變數，該變數含有資料庫中包含該資料之資料表或檢視的名稱，然後設定快速載入選項。</span><span class="sxs-lookup"><span data-stu-id="a7b54-116">**Table name or view name variable fast load** Select the user-defined variable that contains the name of a table or view in the database that contains the data, and then set the fast-load options.</span></span>  
  
    -   <span data-ttu-id="a7b54-117">**SQL 命令**：輸入 SQL 命令，或按一下 [建立查詢]  ，以使用 [查詢產生器]  來撰寫 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="a7b54-117">**SQL command** Type an SQL command or click **Build Query** to write an SQL command by using the **Query Builder**.</span></span>  
  
8.  <span data-ttu-id="a7b54-118">按一下 **[對應]** ，然後將資料行從一個清單拖曳至另一個清單，使 **[可用的輸入資料行]** 清單中的資料行對應至 **[可用的目的地資料行]** 清單中的資料行。</span><span class="sxs-lookup"><span data-stu-id="a7b54-118">Click **Mappings** and then map columns from the **Available Input Columns** list to columns in the **Available Destination Columns** list by dragging columns from one list to another.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a7b54-119">OLE DB 目的地會自動對應具有相同名稱的資料行。</span><span class="sxs-lookup"><span data-stu-id="a7b54-119">The OLE DB destination automatically maps same-named columns.</span></span>  
  
9. <span data-ttu-id="a7b54-120">若要設定錯誤輸出，請按一下 **[錯誤輸出]** 。</span><span class="sxs-lookup"><span data-stu-id="a7b54-120">To configure the error output, click **Error Output**.</span></span> <span data-ttu-id="a7b54-121">如需詳細資訊，請參閱 [在資料流程元件中設定錯誤輸出](../configure-an-error-output-in-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="a7b54-121">For more information, see [Configure an Error Output in a Data Flow Component](../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
10. <span data-ttu-id="a7b54-122">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="a7b54-122">Click **OK**.</span></span>  
  
11. <span data-ttu-id="a7b54-123">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="a7b54-123">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7b54-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7b54-124">See Also</span></span>  
 <span data-ttu-id="a7b54-125">[OLE DB 目的地](ole-db-destination.md) </span><span class="sxs-lookup"><span data-stu-id="a7b54-125">[OLE DB Destination](ole-db-destination.md) </span></span>  
 <span data-ttu-id="a7b54-126">[Integration Services 轉換](transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="a7b54-126">[Integration Services Transformations](transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="a7b54-127">[Integration Services 路徑](integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="a7b54-127">[Integration Services Paths](integration-services-paths.md) </span></span>  
 [<span data-ttu-id="a7b54-128">資料流程工作</span><span class="sxs-lookup"><span data-stu-id="a7b54-128">Data Flow Task</span></span>](../control-flow/data-flow-task.md)  
  
  
