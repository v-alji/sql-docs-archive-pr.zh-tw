---
title: 在資料流程元件中將查詢參數對應至變數 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- queries [Integration Services], parameter mapping
- parameters [Integration Services]
- mapping query parameters to variables [Integration Services]
- variables [Integration Services], mapping parameters to
ms.assetid: 5e26977c-758c-46d6-acf1-4fd9238f0950
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b38940313397c7be7a8bcdbd2bf7f5233583096e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708509"
---
# <a name="map-query-parameters-to-variables-in-a-data-flow-component"></a><span data-ttu-id="012a5-102">在資料流程元件中將查詢參數對應至變數</span><span class="sxs-lookup"><span data-stu-id="012a5-102">Map Query Parameters to Variables in a Data Flow Component</span></span>
  <span data-ttu-id="012a5-103">將 OLE DB 來源設定為使用參數化查詢時，可以將參數對應至變數。</span><span class="sxs-lookup"><span data-stu-id="012a5-103">When you configure the OLE DB source to use parameterized queries, you can map the parameters to variables.</span></span>  
  
 <span data-ttu-id="012a5-104">當 OLE DB 來源連接到資料來源時，會使用參數化查詢來篩選資料。</span><span class="sxs-lookup"><span data-stu-id="012a5-104">The OLE DB source uses parameterized queries to filter data when the source connects to a data source.</span></span>  
  
### <a name="to-map-a-query-parameter-to-a-variable"></a><span data-ttu-id="012a5-105">將查詢參數對應至變數</span><span class="sxs-lookup"><span data-stu-id="012a5-105">To map a query parameter to a variable</span></span>  
  
1.  <span data-ttu-id="012a5-106">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="012a5-106">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="012a5-107">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="012a5-107">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="012a5-108">按一下 **[資料流程]** 索引標籤，然後將 OLE DB 來源從 **[工具箱]** 拖曳到設計介面。</span><span class="sxs-lookup"><span data-stu-id="012a5-108">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the OLE DB source to the design surface.</span></span>  
  
4.  <span data-ttu-id="012a5-109">以滑鼠右鍵按一下 [OLE DB 來源]，然後按一下 [編輯]  。</span><span class="sxs-lookup"><span data-stu-id="012a5-109">Right-click the OLE DB source, and then click **Edit**.</span></span>  
  
5.  <span data-ttu-id="012a5-110">在 [OLE DB 來源編輯器]  中選取用來連接資料來源的 OLE DB 連線管理員，或按一下 [新增]  以建立新的 OLE DB 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="012a5-110">In the **OLE DB Source Editor**, select an OLE DB connection manager to use to connect to the data source, or click **New** to create a new OLE DB connection manager.</span></span>  
  
6.  <span data-ttu-id="012a5-111">為資料存取模式選取 [SQL 命令]  選項，然後在 [SQL 命令文字]  窗格中輸入參數化查詢。</span><span class="sxs-lookup"><span data-stu-id="012a5-111">Select the **SQL command** option for data access mode, and then type a parameterized query in the **SQL command text** pane.</span></span>  
  
7.  <span data-ttu-id="012a5-112">按一下 **[參數]** 。</span><span class="sxs-lookup"><span data-stu-id="012a5-112">Click **Parameters**.</span></span>  
  
8.  <span data-ttu-id="012a5-113">在 [設定查詢參數] 對話方塊中，將 [參數] 清單中每個參數對應至 [變數] 清單中的變數，或按一下 **\<New variable>** 來建立新變數。</span><span class="sxs-lookup"><span data-stu-id="012a5-113">In the **Set Query Parameters** dialog box, map each parameter in the **Parameters** list to a variable in the **Variables** list, or create a new variable by clicking **\<New variable>**.</span></span> <span data-ttu-id="012a5-114">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="012a5-114">Click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="012a5-115">只有封裝、「Foreach 迴圈」之類的父容器或包含資料流程元件之「資料流程」工作等範圍內的系統變數和使用者自訂變數才可用於對應。</span><span class="sxs-lookup"><span data-stu-id="012a5-115">Only system variables and user-defined variables that are in the scope of the package, a parent container such as a Foreach Loop, or the Data Flow task that contains the data flow component are available for mapping.</span></span> <span data-ttu-id="012a5-116">變數的資料類型必須與指派參數之 WHERE 子句中的資料行相容。</span><span class="sxs-lookup"><span data-stu-id="012a5-116">The variable must have a data type that is compatible with the column in the WHERE clause to which the parameter is assigned.</span></span>  
  
9. <span data-ttu-id="012a5-117">您可以按一下 [預覽]  ，以檢視查詢所傳回之最多 200 個資料列的資料。</span><span class="sxs-lookup"><span data-stu-id="012a5-117">You can click **Preview** to view up to 200 rows of the data that the query returns.</span></span>  
  
10. <span data-ttu-id="012a5-118">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="012a5-118">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="012a5-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="012a5-119">See Also</span></span>  
 <span data-ttu-id="012a5-120">[OLE DB 來源](ole-db-source.md) </span><span class="sxs-lookup"><span data-stu-id="012a5-120">[OLE DB Source](ole-db-source.md) </span></span>  
 [<span data-ttu-id="012a5-121">查閱轉換</span><span class="sxs-lookup"><span data-stu-id="012a5-121">Lookup Transformation</span></span>](transformations/lookup-transformation.md)  
  
  
