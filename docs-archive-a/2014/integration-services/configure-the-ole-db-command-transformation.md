---
title: 設定 OLE DB 命令轉換 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- parameters [Integration Services]
- OLE DB Command transformation
ms.assetid: c800f167-3d2e-4c10-8ba3-a02f1872ccea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d1714a6b798c6d8256052fd3c16bd86182480bcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706665"
---
# <a name="configure-the-ole-db-command-transformation"></a><span data-ttu-id="a1037-102">設定 OLE DB 命令轉換</span><span class="sxs-lookup"><span data-stu-id="a1037-102">Configure the OLE DB Command Transformation</span></span>
  <span data-ttu-id="a1037-103">若要加入及設定「OLE DB 命令」轉換，封裝必須至少已包含一個「資料流程」工作和一個來源 (例如「一般檔案」來源或 OLE DB 來源)。</span><span class="sxs-lookup"><span data-stu-id="a1037-103">To add and configure an OLE DB Command transformation, the package must already include at least one Data Flow task and a source such as a Flat File source or an OLE DB source.</span></span> <span data-ttu-id="a1037-104">此轉換通常用於執行參數化查詢。</span><span class="sxs-lookup"><span data-stu-id="a1037-104">This transformation is typically used for running parameterized queries.</span></span>  
  
### <a name="to-configure-the-ole-db-command-transformation"></a><span data-ttu-id="a1037-105">設定 OLE DB 命令轉換</span><span class="sxs-lookup"><span data-stu-id="a1037-105">To configure the OLE DB Command transformation</span></span>  
  
1.  <span data-ttu-id="a1037-106">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="a1037-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="a1037-107">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="a1037-107">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="a1037-108">按一下 **[資料流程]** 索引標籤，然後將「OLE DB 命令」轉換從 **[工具箱]** 拖曳至設計介面。</span><span class="sxs-lookup"><span data-stu-id="a1037-108">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the OLE DB Command transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="a1037-109">將連接子 (綠色或紅色的箭頭) 從資料來源或前一個轉換拖曳至「OLE DB 命令」轉換，將「OLE DB 命令」轉換連線到資料流程。</span><span class="sxs-lookup"><span data-stu-id="a1037-109">Connect the OLE DB Command transformation to the data flow by dragging a connector-the green or red arrow-from a data source or a previous transformation to the OLE DB Command transformation.</span></span>  
  
5.  <span data-ttu-id="a1037-110">以滑鼠右鍵按一下元件，選取 [編輯] 或顯示 [進階編輯器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a1037-110">Right-click the component and select Edit or Show **Advanced Editor**.</span></span>  
  
6.  <span data-ttu-id="a1037-111">在 **[連接管理員]** 索引標籤上，選取 **[連接管理員]** 清單中的 OLE DB 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="a1037-111">On the **Connection Managers** tab, select an OLE DB connection manager in the **Connection Manager** list.</span></span> <span data-ttu-id="a1037-112">如需相關資訊，請參閱 [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="a1037-112">For more information, see [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md).</span></span>  
  
7.  <span data-ttu-id="a1037-113">按一下 [元件屬性]\*\*\*\* 索引標籤，然後按一下 [SqlCommand]\*\*\*\* 方塊中的省略符號按鈕 **(...)**。</span><span class="sxs-lookup"><span data-stu-id="a1037-113">Click the **Component Properties** tab and click the ellipsis button **(...)** in the **SqlCommand** box.</span></span>  
  
8.  <span data-ttu-id="a1037-114">在 [字串值編輯器]\*\*\*\* 中，輸入參數化 SQL 陳述式，並使用問號 (?) 作為每個參數的參數標記。</span><span class="sxs-lookup"><span data-stu-id="a1037-114">In the **String Value Editor**, type the parameterized SQL statement using a question mark (?) as the parameter marker for each parameter.</span></span>  
  
9. <span data-ttu-id="a1037-115">按一下 [重新整理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a1037-115">Click **Refresh**.</span></span> <span data-ttu-id="a1037-116">當您按一下 [重新整理]\*\*\*\* 時，轉換會在「外部資料行」集合中為每個參數建立資料行，並設定 DBParamInfoFlags 屬性。</span><span class="sxs-lookup"><span data-stu-id="a1037-116">When you click **Refresh**, the transformation creates a column for each parameter in the External Columns collection and sets the DBParamInfoFlags property.</span></span>  
  
10. <span data-ttu-id="a1037-117">按一下 **[輸入與輸出屬性]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a1037-117">Click the **Input and Output Properties** tab.</span></span>  
  
11. <span data-ttu-id="a1037-118">展開 **[OLE DB 命令輸入]**，然後展開 **[外部資料行]**。</span><span class="sxs-lookup"><span data-stu-id="a1037-118">Expand **OLE DB Command Input**, and then expand **External Columns**.</span></span>  
  
12. <span data-ttu-id="a1037-119">請確認 **[外部資料行]** 會列出 SQL 陳述式中每個參數的資料行。</span><span class="sxs-lookup"><span data-stu-id="a1037-119">Verify that **External Columns** lists a column for each parameter in the SQL statement.</span></span> <span data-ttu-id="a1037-120">資料行的名稱為 **Param_0**、 **Param_1**等。</span><span class="sxs-lookup"><span data-stu-id="a1037-120">The column names are **Param_0**, **Param_1**, and so on.</span></span>  
  
     <span data-ttu-id="a1037-121">請不要變更這些資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="a1037-121">You should not change the column names.</span></span> <span data-ttu-id="a1037-122">如果您變更了這些資料行名稱， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 就會針對 OLE DB 命令轉換產生驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="a1037-122">If you change the column names, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a validation error for the OLE DB Command transformation.</span></span>  
  
     <span data-ttu-id="a1037-123">此外，請不要變更資料類型。</span><span class="sxs-lookup"><span data-stu-id="a1037-123">Also, you should not change the data type.</span></span> <span data-ttu-id="a1037-124">每個資料行的 DataType 屬性都會設定為正確的資料類型。</span><span class="sxs-lookup"><span data-stu-id="a1037-124">The DataType property of each column is set to the correct data type.</span></span>  
  
13. <span data-ttu-id="a1037-125">如果 **[外部資料行]** 沒有列出資料行，則您必須手動將其加入。</span><span class="sxs-lookup"><span data-stu-id="a1037-125">If **External Columns** lists no columns you must add them manually.</span></span>  
  
    -   <span data-ttu-id="a1037-126">針對 SQL 陳述式中的每個參數，一次按一下 **[加入資料行]** 。</span><span class="sxs-lookup"><span data-stu-id="a1037-126">Click **Add Column** one time for each parameter in the SQL statement.</span></span>  
  
    -   <span data-ttu-id="a1037-127">將資料行的名稱更新為 **Param_0**、 **Param_1**等。</span><span class="sxs-lookup"><span data-stu-id="a1037-127">Update the column names to **Param_0**, **Param_1**, and so on.</span></span>  
  
    -   <span data-ttu-id="a1037-128">指定 DBParamInfoFlags 屬性中的值。</span><span class="sxs-lookup"><span data-stu-id="a1037-128">Specify a value in the DBParamInfoFlags property.</span></span> <span data-ttu-id="a1037-129">該值必須與 OLE DB DBPARAMFLAGSENUM 列舉中的值相符。</span><span class="sxs-lookup"><span data-stu-id="a1037-129">The value must match a value in the OLE DB DBPARAMFLAGSENUM enumeration.</span></span> <span data-ttu-id="a1037-130">如需詳細資訊，請參閱 OLE DB 參考文件集。</span><span class="sxs-lookup"><span data-stu-id="a1037-130">For more information, see the OLE DB reference documentation.</span></span>  
  
    -   <span data-ttu-id="a1037-131">指定資料行的資料類型，並依據該資料類型指定資料行的字碼頁、長度、有效位數和小數位數。</span><span class="sxs-lookup"><span data-stu-id="a1037-131">Specify the data type of the column and, depending on the data type, specify the code page, length, precision, and scale of the column.</span></span>  
  
    -   <span data-ttu-id="a1037-132">若要刪除不使用的參數，請選取 **[外部資料行]** 中的參數，然後按一下 **[移除資料行]**。</span><span class="sxs-lookup"><span data-stu-id="a1037-132">To delete an unused parameter, select the parameter in **External Columns**, and then click **Remove Column**.</span></span>  
  
    -   <span data-ttu-id="a1037-133">按一下 **[資料行對應]** ，然後將 **[可用的輸入資料行]** 清單中的資料行對應至 **[可用的目的地資料行]** 清單中的參數。</span><span class="sxs-lookup"><span data-stu-id="a1037-133">Click **Column Mappings** and map columns in the **Available Input Columns** list to parameters in the **Available Destination Columns** list.</span></span>  
  
14. <span data-ttu-id="a1037-134">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="a1037-134">Click **OK**.</span></span>  
  
15. <span data-ttu-id="a1037-135">若要儲存更新的封裝，請按一下 **[檔案]** 功能表上的 **[儲存]** 。</span><span class="sxs-lookup"><span data-stu-id="a1037-135">To save the updated package, click **Save** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1037-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1037-136">See Also</span></span>  
 <span data-ttu-id="a1037-137">[OLE DB 命令轉換](data-flow/transformations/ole-db-command-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="a1037-137">[OLE DB Command Transformation](data-flow/transformations/ole-db-command-transformation.md) </span></span>  
 <span data-ttu-id="a1037-138">[Integration Services 轉換](data-flow/transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="a1037-138">[Integration Services Transformations](data-flow/transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="a1037-139">[Integration Services 路徑](data-flow/integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="a1037-139">[Integration Services Paths](data-flow/integration-services-paths.md) </span></span>  
 [<span data-ttu-id="a1037-140">資料流程工作</span><span class="sxs-lookup"><span data-stu-id="a1037-140">Data Flow Task</span></span>](control-flow/data-flow-task.md)  
  
  
