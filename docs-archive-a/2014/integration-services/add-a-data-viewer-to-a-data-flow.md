---
title: 將資料檢視器加入至資料流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data viewers [Integration Services]
- data flow [Integration Services], data viewers
- adding data viewers
ms.assetid: 5e573274-a170-4132-bfc8-a8ff3a8411e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7abd76417552ec50da736afe024a5ae36ee6a2ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585538"
---
# <a name="add-a-data-viewer-to-a-data-flow"></a><span data-ttu-id="713e9-102">將資料檢視器加入資料流程</span><span class="sxs-lookup"><span data-stu-id="713e9-102">Add a Data Viewer to a Data Flow</span></span>
  <span data-ttu-id="713e9-103">本主題描述如何在資料流程中加入和設定資料檢視器。</span><span class="sxs-lookup"><span data-stu-id="713e9-103">This topic describes how to add and configure a data viewer in a data flow.</span></span> <span data-ttu-id="713e9-104">資料檢視器可以顯示在兩個資料流程元件之間移動的資料。</span><span class="sxs-lookup"><span data-stu-id="713e9-104">A data viewer displays data that is moving between two data flow components.</span></span> <span data-ttu-id="713e9-105">例如，在資料流程中的轉換修改從資料來源擷取的資料之前，資料檢視器可以先顯示該資料。</span><span class="sxs-lookup"><span data-stu-id="713e9-105">For example, a data viewer can display the data that is extracted from a data source before a transformation in the data flow modifies the data.</span></span>  
  
 <span data-ttu-id="713e9-106">將一個資料流程元件的輸出與另一元件的輸入連接，路徑可連接資料流程中的元件。</span><span class="sxs-lookup"><span data-stu-id="713e9-106">A path connects components in a data flow by connecting the output of one data flow component to the input of another component.</span></span>  
  
 <span data-ttu-id="713e9-107">在可以將資料檢視器加入封裝之前，該封裝必須包括「資料流程」工作和至少兩個連接的資料流程元件。</span><span class="sxs-lookup"><span data-stu-id="713e9-107">Before you can add data viewers to a package, the package must include a Data Flow task and at least two data flow components that are connected.</span></span>  
  
### <a name="to-add-a-data-viewer-to-a-data-flow"></a><span data-ttu-id="713e9-108">若要將資料檢視器加入資料流程</span><span class="sxs-lookup"><span data-stu-id="713e9-108">To add a data viewer to a data flow</span></span>  
  
1.  <span data-ttu-id="713e9-109">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="713e9-109">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="713e9-110">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="713e9-110">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="713e9-111">如果 [控制流程]  索引標籤尚未處於使用中，請按一下該索引標籤。</span><span class="sxs-lookup"><span data-stu-id="713e9-111">Click the **Control Flow** tab, if it is not already active.</span></span>  
  
4.  <span data-ttu-id="713e9-112">按一下要將資料檢視器附加至其資料流程的 [資料流程] 工作，然後按一下 [資料流程]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="713e9-112">Click the Data Flow task to whose data flow you want to attach a data viewer and then click the **Data Flow** tab.</span></span>  
  
5.  <span data-ttu-id="713e9-113">以滑鼠右鍵按一下兩個資料流程元件之間的路徑，然後按一下 [編輯]  。</span><span class="sxs-lookup"><span data-stu-id="713e9-113">Right-click a path between two data flow components, and click **Edit**.</span></span>  
  
6.  <span data-ttu-id="713e9-114">在 [一般]  頁面上，您可以檢視和編輯路徑屬性。</span><span class="sxs-lookup"><span data-stu-id="713e9-114">On the **General** page, you can view and edit path properties.</span></span> <span data-ttu-id="713e9-115">例如，您可以從 [PathAnnotation]  下拉式清單選取出現在路徑旁的註解。</span><span class="sxs-lookup"><span data-stu-id="713e9-115">For example, from the **PathAnnotation** drop-down list you can select the annotation that appears next to the path.</span></span>  
  
7.  <span data-ttu-id="713e9-116">在 [中繼資料]  頁面上，您可以檢視資料行中繼資料，並且將中繼資料複製到 [剪貼簿]。</span><span class="sxs-lookup"><span data-stu-id="713e9-116">On the **Metadata** page, you can view the column metadata and copy the metadata to the Clipboard.</span></span>  
  
8.  <span data-ttu-id="713e9-117">在 [資料檢視器]  頁面上，按一下 [啟用資料檢視器]  。</span><span class="sxs-lookup"><span data-stu-id="713e9-117">On the **Data Viewer** page, click **Enable data viewer**.</span></span>  
  
9. <span data-ttu-id="713e9-118">在 [要顯示的資料行] 區域中，選取要在資料檢視器中顯示的資料行。</span><span class="sxs-lookup"><span data-stu-id="713e9-118">In the Columns to display area, select the columns you want to display in the data viewer.</span></span> <span data-ttu-id="713e9-119">根據預設，所有可用的資料行都會選取，並且在 [顯示的資料行]  清單中列出。</span><span class="sxs-lookup"><span data-stu-id="713e9-119">By default, all the available columns are selected and listed in the **Displayed Columns** list.</span></span> <span data-ttu-id="713e9-120">將不想使用的資料行移至 [未使用的資料行]  清單，方法是選取它們然後按一下向左箭號。</span><span class="sxs-lookup"><span data-stu-id="713e9-120">Move columns that you do not want to use to the **Unused Column** list by selecting them and then clicking the left arrow.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="713e9-121">在此方格中，代表 DT_DATE、DT_DBTIME2、DT_FILETIME、DT_DBTIMESTAMP、DT_DBTIMESTAMP2 和 DT_DBTIMESTAMPOFFSET 資料類型的值會以 ISO 8601 格式化字串的形式出現，而且空格分隔符號會取代 `T` 分隔符號。</span><span class="sxs-lookup"><span data-stu-id="713e9-121">In the grid, values that represent the DT_DATE, DT_DBTIME2, DT_FILETIME, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, and DT_DBTIMESTAMPOFFSET data types appear as ISO 8601 formatted strings and a space separator replaces the `T` separator.</span></span> <span data-ttu-id="713e9-122">代表 DT_DATE 和 DT_FILETIME 資料類型的值包括小數秒的七位數。</span><span class="sxs-lookup"><span data-stu-id="713e9-122">Values that represent the DT_DATE and DT_FILETIME data types include seven digits for fractional seconds.</span></span> <span data-ttu-id="713e9-123">由於 DT_FILETIME 資料類型只會儲存小數秒的三位數，所以此方格會將其餘四位數顯示為零。</span><span class="sxs-lookup"><span data-stu-id="713e9-123">Because the DT_FILETIME data type stores only three digits of fractional seconds, the grid displays zeros for the remaining four digits.</span></span> <span data-ttu-id="713e9-124">代表 DT_DBTIMESTAMP 資料類型的值包括小數秒的三位數。</span><span class="sxs-lookup"><span data-stu-id="713e9-124">Values that represent the DT_DBTIMESTAMP data type include three digits for fractional seconds.</span></span> <span data-ttu-id="713e9-125">如果是代表 DT_DBTIME2、DT_DBTIMESTAMP2 和 DT_DBTIMESTAMPOFFSET 資料類型的值，則小數秒的位數會對應到針對資料行資料類型指定的小數位數。</span><span class="sxs-lookup"><span data-stu-id="713e9-125">For values that represent the DT_DBTIME2, DT_DBTIMESTAMP2, and DT_DBTIMESTAMPOFFSET data types, the number of digits for fractional seconds corresponds to the scale specified for the column's data type.</span></span> <span data-ttu-id="713e9-126">如需 ISO 8601 格式的詳細資訊，請參閱 [日期和時間格式](../../2014/integration-services/date-and-time-formats.md)。</span><span class="sxs-lookup"><span data-stu-id="713e9-126">For more information about ISO 8601 formats, see [Date and Time Formats](../../2014/integration-services/date-and-time-formats.md).</span></span> <span data-ttu-id="713e9-127">如需有關資料類型的詳細資訊，請參閱＜ [Integration Services Data Types](data-flow/integration-services-data-types.md)＞。</span><span class="sxs-lookup"><span data-stu-id="713e9-127">For more information about data types, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
10. <span data-ttu-id="713e9-128">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="713e9-128">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="713e9-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="713e9-129">See Also</span></span>  
 <span data-ttu-id="713e9-130">[Integration Services 轉換](data-flow/transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="713e9-130">[Integration Services Transformations](data-flow/transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="713e9-131">[Integration Services 路徑](data-flow/integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="713e9-131">[Integration Services Paths](data-flow/integration-services-paths.md) </span></span>  
 <span data-ttu-id="713e9-132">[資料流程](data-flow/data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="713e9-132">[Data Flow](data-flow/data-flow.md) </span></span>  
 [<span data-ttu-id="713e9-133">偵錯資料流程</span><span class="sxs-lookup"><span data-stu-id="713e9-133">Debugging Data Flow</span></span>](troubleshooting/debugging-data-flow.md)  
  
  
