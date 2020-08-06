---
title: 使用 OLE DB 來源擷取資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- extracting data [Integration Services]
- sources [Integration Services], OLE DB
- OLE DB source [Integration Services]
ms.assetid: 4ca6eeb5-b60e-4b81-86dd-0674be8ae8d8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 352d62cc66e3f17fb10839086e7ee9c5307f1a17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709790"
---
# <a name="extract-data-by-using-the-ole-db-source"></a><span data-ttu-id="8b9bc-102">使用 OLE DB 來源來擷取資料</span><span class="sxs-lookup"><span data-stu-id="8b9bc-102">Extract Data by Using the OLE DB Source</span></span>
  <span data-ttu-id="8b9bc-103">若要加入及設定 OLE DB 來源，封裝必須已包含至少一個「資料流程」工作。</span><span class="sxs-lookup"><span data-stu-id="8b9bc-103">To add and configure an OLE DB source, the package must already include at least one Data Flow task.</span></span>  
  
### <a name="to-extract-data-using-an-ole-db-source"></a><span data-ttu-id="8b9bc-104">若要使用 OLE DB 來源擷取資料</span><span class="sxs-lookup"><span data-stu-id="8b9bc-104">To extract data using an OLE DB Source</span></span>  
  
1.  <span data-ttu-id="8b9bc-105">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="8b9bc-105">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="8b9bc-106">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="8b9bc-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="8b9bc-107">按一下 **[資料流程]** 索引標籤，然後將 OLE DB 來源從 **[工具箱]** 拖曳到設計介面。</span><span class="sxs-lookup"><span data-stu-id="8b9bc-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the OLE DB source to the design surface.</span></span>  
  
4.  <span data-ttu-id="8b9bc-108">按兩下 OLE DB 來源。</span><span class="sxs-lookup"><span data-stu-id="8b9bc-108">Double-click the OLE DB source.</span></span>  
  
5.  <span data-ttu-id="8b9bc-109">在 **[連接管理員]** 頁面上的 **[OLE DB 來源編輯器]** 對話方塊中，選取現有的 OLE DB 連接管理員，或按一下 **[新增]** 以新建連接管理員。</span><span class="sxs-lookup"><span data-stu-id="8b9bc-109">In the **OLE DB Source Editor** dialog box, on the **Connection Manager** page, select an existing OLE DB connection manager or click **New** to create a new connection manager.</span></span> <span data-ttu-id="8b9bc-110">如需相關資訊，請參閱 [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="8b9bc-110">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
6.  <span data-ttu-id="8b9bc-111">選取資料存取方法：</span><span class="sxs-lookup"><span data-stu-id="8b9bc-111">Select the data access method:</span></span>  
  
    -   <span data-ttu-id="8b9bc-112">**資料表或檢視** ：選取 OLE DB 連接管理員連接之資料庫中的資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="8b9bc-112">**Table or view** Select a table or view in the database to which the OLE DB connection manager connects.</span></span>  
  
    -   <span data-ttu-id="8b9bc-113">**資料表名稱或檢視名稱變數** ：選取包含 OLE DB 連接管理員連接之資料庫中資料表或檢視名稱的使用者自訂變數。</span><span class="sxs-lookup"><span data-stu-id="8b9bc-113">**Table name or view name variable** Select the user-defined variable that contains the name of a table or view in the database to which the OLE DB connection manager connects.</span></span>  
  
    -   <span data-ttu-id="8b9bc-114">**SQL 命令** ：輸入 SQL 命令，或按一下 **[建立查詢]** ，以使用 **[查詢產生器]** 撰寫 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="8b9bc-114">**SQL command** Type an SQL command or click **Build Query** to write an SQL command using the **Query Builder**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="8b9bc-115">命令可以包含參數。</span><span class="sxs-lookup"><span data-stu-id="8b9bc-115">The command can include parameters.</span></span> <span data-ttu-id="8b9bc-116">如需詳細資訊，請參閱 [在資料流程元件中將查詢參數對應至變數](map-query-parameters-to-variables-in-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="8b9bc-116">For more information, see [Map Query Parameters to Variables in a Data Flow Component](map-query-parameters-to-variables-in-a-data-flow-component.md).</span></span>  
  
    -   <span data-ttu-id="8b9bc-117">**來自變數的 SQL 命令** ：選取包含 SQL 命令的使用者自訂變數。</span><span class="sxs-lookup"><span data-stu-id="8b9bc-117">**SQL command from variable** Select the user-defined variable that contains the SQL command.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="8b9bc-118">變數必須在包含 OLE DB 來源之同一「資料流程」工作的範圍中定義，或在同一封裝的範圍中定義；此外，變數還必須具有字串資料類型。</span><span class="sxs-lookup"><span data-stu-id="8b9bc-118">The variables must be defined in the scope of the same Data Flow task that contains the OLE DB source, or in the scope of the same package; additionally, the variable must have a string data type.</span></span>  
  
7.  <span data-ttu-id="8b9bc-119">若要更新外部及輸出資料行之間的對應，請按一下 **[資料行]** ，並在 **[外部資料行]** 清單中選取不同的資料行。</span><span class="sxs-lookup"><span data-stu-id="8b9bc-119">To update the mapping between external and output columns, click **Columns** and select different columns in the **External Column** list.</span></span>  
  
8.  <span data-ttu-id="8b9bc-120">(選擇性) 藉由編輯 **[輸出資料行]** 清單中的值，更新輸出資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="8b9bc-120">Optionally, update the names of output columns by editing values in the **Output Column** list.</span></span>  
  
9. <span data-ttu-id="8b9bc-121">若要設定錯誤輸出，請按一下 **[錯誤輸出]** 。</span><span class="sxs-lookup"><span data-stu-id="8b9bc-121">To configure the error output, click **Error Output**.</span></span> <span data-ttu-id="8b9bc-122">如需詳細資訊，請參閱 [在資料流程元件中設定錯誤輸出](../configure-an-error-output-in-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="8b9bc-122">For more information, see [Configure an Error Output in a Data Flow Component](../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
10. <span data-ttu-id="8b9bc-123">您可以按一下 **[預覽]** ，以檢視 OLE DB 來源擷取之最多 200 個資料列的資料。</span><span class="sxs-lookup"><span data-stu-id="8b9bc-123">You can click **Preview** to view up to 200 rows of the data extracted by the OLE DB source.</span></span>  
  
11. <span data-ttu-id="8b9bc-124">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="8b9bc-124">Click **OK**.</span></span>  
  
12. <span data-ttu-id="8b9bc-125">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="8b9bc-125">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b9bc-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b9bc-126">See Also</span></span>  
 <span data-ttu-id="8b9bc-127">[OLE DB 來源](ole-db-source.md) </span><span class="sxs-lookup"><span data-stu-id="8b9bc-127">[OLE DB Source](ole-db-source.md) </span></span>  
 <span data-ttu-id="8b9bc-128">[Integration Services 轉換](transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="8b9bc-128">[Integration Services Transformations](transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="8b9bc-129">[Integration Services 路徑](integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="8b9bc-129">[Integration Services Paths](integration-services-paths.md) </span></span>  
 [<span data-ttu-id="8b9bc-130">資料流程工作</span><span class="sxs-lookup"><span data-stu-id="8b9bc-130">Data Flow Task</span></span>](../control-flow/data-flow-task.md)  
  
  
