---
title: 使用 XML 來源來擷取資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- extracting data [Integration Services]
- sources [Integration Services], XML
- XML source [Integration Services]
ms.assetid: 5d5be54c-2b7e-4957-9193-c5ea5c5d6d15
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 57758353c476badfba4cb12a1ef6b5101f16735d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709789"
---
# <a name="extract-data-by-using-the-xml-source"></a><span data-ttu-id="a75cf-102">使用 XML 來源來擷取資料</span><span class="sxs-lookup"><span data-stu-id="a75cf-102">Extract Data by Using the XML Source</span></span>
  <span data-ttu-id="a75cf-103">若要加入和設定 XML 來源，封裝必須至少含有一個「資料流程」工作。</span><span class="sxs-lookup"><span data-stu-id="a75cf-103">To add and configure an XML source, the package must already include at least one Data Flow task.</span></span>  
  
### <a name="to-extract-data-using-an-xml-source"></a><span data-ttu-id="a75cf-104">使用 XML 來源擷取資料</span><span class="sxs-lookup"><span data-stu-id="a75cf-104">To extract data using an XML source</span></span>  
  
1.  <span data-ttu-id="a75cf-105">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="a75cf-105">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="a75cf-106">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="a75cf-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="a75cf-107">按一下 [資料流程]  索引標籤，然後將 XML 來源從 [工具箱]  拖曳至設計介面。</span><span class="sxs-lookup"><span data-stu-id="a75cf-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the XML source to the design surface.</span></span>  
  
4.  <span data-ttu-id="a75cf-108">按兩下 XML 來源。</span><span class="sxs-lookup"><span data-stu-id="a75cf-108">Double-click the XML source.</span></span>  
  
5.  <span data-ttu-id="a75cf-109">在 [XML 來源編輯器]  的 [連線管理員]  頁面上，選取資料存取模式：</span><span class="sxs-lookup"><span data-stu-id="a75cf-109">In the **XML Source Editor**, on the **Connection Manager** page, select a data access mode:</span></span>  
  
    -   <span data-ttu-id="a75cf-110">若為 [XML 檔案位置]  存取模式，請按一下 [瀏覽]  ，以尋找包含 XML 檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="a75cf-110">For the **XML file location** access mode, click **Browse** and locate the folder that contains the XML file.</span></span>  
  
    -   <span data-ttu-id="a75cf-111">若為 [來自變數的 XML 檔案]  存取模式，請選取包含 XML 檔案路徑的使用者定義變數。</span><span class="sxs-lookup"><span data-stu-id="a75cf-111">For the **XML file from variable** access mode, select the user-defined variable that contains the path of the XML file.</span></span>  
  
    -   <span data-ttu-id="a75cf-112">若為 [來自變數的 XML 資料]  存取模式，請選取包含 XML 資料的使用者定義變數。</span><span class="sxs-lookup"><span data-stu-id="a75cf-112">For the **XML data from variable** access mode, select the user-defined variable that contains the XML data.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a75cf-113">變數必須定義於包含 XML 來源之「資料流程」工作的範圍內，或定義於封裝的範圍內；此外，變數還必須具有字串資料類型。</span><span class="sxs-lookup"><span data-stu-id="a75cf-113">The variables must be defined in the scope of the Data Flow task that contains the XML source, or in the scope of the package; additionally, the variable must have a string data type.</span></span>  
  
6.  <span data-ttu-id="a75cf-114">(選擇性) 選取 [使用內嵌結構描述]  ，來指示 XML 文件包含結構描述資訊。</span><span class="sxs-lookup"><span data-stu-id="a75cf-114">Optionally, select **Use inline schema** to indicate that the XML document includes schema information.</span></span>  
  
7.  <span data-ttu-id="a75cf-115">若要指定 XML 檔案的外部「XML 結構描述定義語言」(XSD) 結構描述，請執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="a75cf-115">To specify an external XML Schema definition language (XSD) schema for the XML file, do one of the following:</span></span>  
  
    -   <span data-ttu-id="a75cf-116">按一下 [瀏覽]  ，以尋找現有 XSD 檔案。</span><span class="sxs-lookup"><span data-stu-id="a75cf-116">Click **Browse** to locate an existing XSD file.</span></span>  
  
    -   <span data-ttu-id="a75cf-117">按一下 [產生 XSD]  ，以從 XML 檔案建立 XSD。</span><span class="sxs-lookup"><span data-stu-id="a75cf-117">Click **Generate XSD** to create an XSD from the XML file.</span></span>  
  
8.  <span data-ttu-id="a75cf-118">若要更新輸出資料行的名稱，請按一下 [資料行]  ，然後編輯 [輸出資料行]  清單中的值。</span><span class="sxs-lookup"><span data-stu-id="a75cf-118">To update the names of output columns, click **Columns** and edit the values in the **Output Column** list.</span></span>  
  
9. <span data-ttu-id="a75cf-119">若要設定錯誤輸出，請按一下 **[錯誤輸出]** 。</span><span class="sxs-lookup"><span data-stu-id="a75cf-119">To configure the error output, click **Error Output**.</span></span> <span data-ttu-id="a75cf-120">如需詳細資訊，請參閱 [在資料流程元件中設定錯誤輸出](../configure-an-error-output-in-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="a75cf-120">For more information, see [Configure an Error Output in a Data Flow Component](../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
10. <span data-ttu-id="a75cf-121">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="a75cf-121">Click **OK**.</span></span>  
  
11. <span data-ttu-id="a75cf-122">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="a75cf-122">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a75cf-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a75cf-123">See Also</span></span>  
 <span data-ttu-id="a75cf-124">[XML 來源](xml-source.md) </span><span class="sxs-lookup"><span data-stu-id="a75cf-124">[XML Source](xml-source.md) </span></span>  
 <span data-ttu-id="a75cf-125">[Integration Services 轉換](transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="a75cf-125">[Integration Services Transformations](transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="a75cf-126">[Integration Services 路徑](integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="a75cf-126">[Integration Services Paths](integration-services-paths.md) </span></span>  
 [<span data-ttu-id="a75cf-127">資料流程工作</span><span class="sxs-lookup"><span data-stu-id="a75cf-127">Data Flow Task</span></span>](../control-flow/data-flow-task.md)  
  
  
