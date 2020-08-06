---
title: SAP BW 目的地編輯器 (對應頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: dfa1f1d6-6b64-4331-bdc5-eaa8b7aa41a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7c4c2803be3e2649f7425a2974dae8ac0a80fae7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687076"
---
# <a name="sap-bw-destination-editor-mappings-page"></a><span data-ttu-id="b42c2-102">SAP BW 目的地編輯器 (對應頁面)</span><span class="sxs-lookup"><span data-stu-id="b42c2-102">SAP BW Destination Editor (Mappings Page)</span></span>
  <span data-ttu-id="b42c2-103">使用 [SAP BW 目的地編輯器] 的 [對應] 頁面可以將輸入資料行對應至目的地資料行。</span><span class="sxs-lookup"><span data-stu-id="b42c2-103">Use the **Mappings** page of the **SAP BW Destination Editor** to map input columns to destination columns.</span></span>  
  
 <span data-ttu-id="b42c2-104">若要深入了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 目的地，請參閱 [SAP BW 目的地](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="b42c2-104">To learn more about the SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b42c2-105">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="b42c2-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="b42c2-106">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="b42c2-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="b42c2-107">**開啟對應頁面**</span><span class="sxs-lookup"><span data-stu-id="b42c2-107">**To open the Mappings page**</span></span>  
  
1.  <span data-ttu-id="b42c2-108">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含 SAP BW 目的地的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件。</span><span class="sxs-lookup"><span data-stu-id="b42c2-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="b42c2-109">在 [資料流程]  索引標籤上，按兩下 SAP BW 目的地。</span><span class="sxs-lookup"><span data-stu-id="b42c2-109">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="b42c2-110">在 [SAP BW 目的地編輯器]  中，按一下 [對應]  開啟編輯器的 [對應]  頁面。</span><span class="sxs-lookup"><span data-stu-id="b42c2-110">In the **SAP BW Destination Editor**, click **Mappings** to open the **Mappings** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b42c2-111">選項。</span><span class="sxs-lookup"><span data-stu-id="b42c2-111">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b42c2-112">如果您不知道設定目的地的所有必要值，可能必須詢問 SAP 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="b42c2-112">If you do not know all the values that are required to configure the destination, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="b42c2-113">[SAP BW 目的地編輯器] 的 [對應] 頁面包含兩個區段：</span><span class="sxs-lookup"><span data-stu-id="b42c2-113">The **Mappings** page of the **SAP BW Destination Editor consists** of two sections:</span></span>  
  
-   <span data-ttu-id="b42c2-114">上方區段會顯示可用的輸入和目的地資料行，並且讓您建立這兩種資料行類型之間的對應。</span><span class="sxs-lookup"><span data-stu-id="b42c2-114">The upper section shows the available input and destination columns and lets you create mappings between these two types of columns.</span></span>  
  
-   <span data-ttu-id="b42c2-115">下方區段是一份資料表，其中列出哪些輸入資料行已經對應至哪些輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="b42c2-115">The lower section is a table that lists which input columns have been mapped to which output columns.</span></span>  
  
### <a name="upper-section-options"></a><span data-ttu-id="b42c2-116">上方區段選項</span><span class="sxs-lookup"><span data-stu-id="b42c2-116">Upper Section Options</span></span>  
 <span data-ttu-id="b42c2-117">上方區段具有下列選項：</span><span class="sxs-lookup"><span data-stu-id="b42c2-117">The upper section has the following options:</span></span>  
  
 <span data-ttu-id="b42c2-118">**可用的輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="b42c2-118">**Available Input Columns**</span></span>  
 <span data-ttu-id="b42c2-119">檢視可用的輸入資料行清單。</span><span class="sxs-lookup"><span data-stu-id="b42c2-119">View the list of available input columns.</span></span>  
  
 <span data-ttu-id="b42c2-120">若要將輸入資料行對應至目的地資料行，請從 [可用的輸入資料行]  清單中拖曳資料行，並且將該資料行放入 [可用的目的地資料行]  清單中的資料行。</span><span class="sxs-lookup"><span data-stu-id="b42c2-120">To map an input column to a destination column, drag a column from the **Available Input Columns** list and drop that column onto a column in the **Available Destination Columns** list.</span></span>  
  
 <span data-ttu-id="b42c2-121">**可用的目的地資料行**</span><span class="sxs-lookup"><span data-stu-id="b42c2-121">**Available Destination Columns**</span></span>  
 <span data-ttu-id="b42c2-122">檢視可用的目的地資料行清單。</span><span class="sxs-lookup"><span data-stu-id="b42c2-122">View the list of available destination columns.</span></span>  
  
 <span data-ttu-id="b42c2-123">若要將輸入資料行對應至目的地資料行，請從 [可用的輸入資料行]  清單中拖曳資料行，並且將該資料行放入 [可用的目的地資料行]  清單中的資料行。</span><span class="sxs-lookup"><span data-stu-id="b42c2-123">To map an input column to destination column, drag a column from the **Available Input Columns** list and drop that column onto a column in the **Available Destination Columns** list.</span></span>  
  
 <span data-ttu-id="b42c2-124">上方區段也具有操作功能表，而且您可以在背景上按一下滑鼠右鍵，即可開啟此功能表。</span><span class="sxs-lookup"><span data-stu-id="b42c2-124">The upper section also has a context menu that you can open by right-clicking on the background.</span></span> <span data-ttu-id="b42c2-125">這個操作功能表包含下列選項：</span><span class="sxs-lookup"><span data-stu-id="b42c2-125">This context menu contains the following options:</span></span>  
  
-   <span data-ttu-id="b42c2-126">**選取全部對應**</span><span class="sxs-lookup"><span data-stu-id="b42c2-126">**Select All Mappings**</span></span>  
  
-   <span data-ttu-id="b42c2-127">**刪除選取的對應**</span><span class="sxs-lookup"><span data-stu-id="b42c2-127">**Delete Selected Mappings**</span></span>  
  
-   <span data-ttu-id="b42c2-128">**藉由比對名稱來對應項目**</span><span class="sxs-lookup"><span data-stu-id="b42c2-128">**Map Items by Matching Names**</span></span>  
  
### <a name="lower-section-columns"></a><span data-ttu-id="b42c2-129">下方區段資料行</span><span class="sxs-lookup"><span data-stu-id="b42c2-129">Lower Section Columns</span></span>  
 <span data-ttu-id="b42c2-130">下方區段是對應的資料表，而且具有下列資料行：</span><span class="sxs-lookup"><span data-stu-id="b42c2-130">The lower section is a table of the mappings, and has the following columns:</span></span>  
  
 <span data-ttu-id="b42c2-131">**輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="b42c2-131">**Input Column**</span></span>  
 <span data-ttu-id="b42c2-132">檢視您已選取的輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="b42c2-132">View the input columns that you have selected.</span></span>  
  
 <span data-ttu-id="b42c2-133">若要將不同的輸入資料行對應至相同的目的地資料行，請在清單中選取不同的輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="b42c2-133">To map a different input column to the same destination column, select a different input column in the list.</span></span> <span data-ttu-id="b42c2-134">若要移除對應，請選取 **\<ignore>** ，即可從輸出中排除輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="b42c2-134">To remove a mapping, select **\<ignore>** to exclude the input column from the output.</span></span>  
  
 <span data-ttu-id="b42c2-135">**目的地資料行**</span><span class="sxs-lookup"><span data-stu-id="b42c2-135">**Destination Column**</span></span>  
 <span data-ttu-id="b42c2-136">檢視每個可用的目的地資料行，不論該資料行是否已經對應。</span><span class="sxs-lookup"><span data-stu-id="b42c2-136">View each available destination column, regardless of whether that column is mapped or not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b42c2-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b42c2-137">See Also</span></span>  
 <span data-ttu-id="b42c2-138">[SAP BW 目的地編輯器 &#40;連線管理員頁面&#41;](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="b42c2-138">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="b42c2-139">[SAP BW 目的地編輯器 &#40;錯誤輸出頁面&#41;](sap-bw-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="b42c2-139">[SAP BW Destination Editor &#40;Error Output Page&#41;](sap-bw-destination-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="b42c2-140">[SAP BW 目的地編輯器 &#40;進階頁面&#41;](sap-bw-destination-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="b42c2-140">[SAP BW Destination Editor &#40;Advanced Page&#41;](sap-bw-destination-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="b42c2-141">Microsoft Connector 1.1 for SAP BW F1 說明</span><span class="sxs-lookup"><span data-stu-id="b42c2-141">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
