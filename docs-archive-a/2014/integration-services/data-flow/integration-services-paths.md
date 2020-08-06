---
title: Integration Services 路徑 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- paths [Integration Services], about paths
- data flow [Integration Services], paths
- paths [Integration Services]
- destinations [Integration Services], paths
- sources [Integration Services], paths
ms.assetid: 6c4629a9-2ede-4011-9101-3b342249640e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c52bbd06974311a7fc94b3058309399d70df0034
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700120"
---
# <a name="integration-services-paths"></a><span data-ttu-id="db689-102">Integration Services 路徑</span><span class="sxs-lookup"><span data-stu-id="db689-102">Integration Services Paths</span></span>
  <span data-ttu-id="db689-103">將一個資料流程元件的輸出與另一元件的輸入連接，路徑可連接資料流程中的兩個元件。</span><span class="sxs-lookup"><span data-stu-id="db689-103">A path connects two components in a data flow by connecting the output of one data flow component to the input of another component.</span></span> <span data-ttu-id="db689-104">路徑具有一個來源和一個目的地。</span><span class="sxs-lookup"><span data-stu-id="db689-104">A path has a source and a destination.</span></span> <span data-ttu-id="db689-105">例如，如果路徑連接 OLE DB 來源和「排序」轉換，則 OLE DB 來源是路徑的來源，而「排序」轉換是路徑的目的地。</span><span class="sxs-lookup"><span data-stu-id="db689-105">For example, if a path connects an OLE DB source and a Sort transformation, the OLE DB source is the source of the path, and the Sort transformation is the destination of the path.</span></span> <span data-ttu-id="db689-106">來源是路徑開始處的元件，而目的地是路徑結束處的元件。</span><span class="sxs-lookup"><span data-stu-id="db689-106">The source is the component where the path starts, and the destination is the component where the path ends.</span></span>  
  
 <span data-ttu-id="db689-107">如果您在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中執行封裝，則可將資料檢視器附加到路徑，來檢視資料流程中的資料。</span><span class="sxs-lookup"><span data-stu-id="db689-107">If you run a package in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, you can view the data in a data flow by attaching data viewers to a path.</span></span> <span data-ttu-id="db689-108">資料檢視器可以設定為在方格中顯示資料。</span><span class="sxs-lookup"><span data-stu-id="db689-108">A data viewer can be configured to display data in a grid.</span></span> <span data-ttu-id="db689-109">資料檢視器是一種有用的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="db689-109">A data viewer is a useful debugging tool.</span></span> <span data-ttu-id="db689-110">如需詳細資訊，請參閱 [偵錯資料流程](../troubleshooting/debugging-data-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="db689-110">For more information, see [Debugging Data Flow](../troubleshooting/debugging-data-flow.md).</span></span>  
  
## <a name="configuration-of-the-path"></a><span data-ttu-id="db689-111">設定路徑</span><span class="sxs-lookup"><span data-stu-id="db689-111">Configuration of the Path</span></span>  
 <span data-ttu-id="db689-112">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師提供 [資料流程路徑編輯器]  對話方塊，用以設定路徑屬性、檢視通過該路徑之資料行的中繼資料，並設定資料檢視器。</span><span class="sxs-lookup"><span data-stu-id="db689-112">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer provides the **Data Flow Path Editor** dialog box for setting path properties, viewing the metadata of the data columns that pass through the path, and configuring data viewers.</span></span>  
  
 <span data-ttu-id="db689-113">可設定的路徑屬性包括名稱、描述及路徑的註解。</span><span class="sxs-lookup"><span data-stu-id="db689-113">The configurable path properties include the name, description, and annotation of the path.</span></span> <span data-ttu-id="db689-114">您還可以程式設計方式設定路徑。</span><span class="sxs-lookup"><span data-stu-id="db689-114">You can also configure paths programmatically.</span></span> <span data-ttu-id="db689-115">如需詳細資訊，請參閱 [以程式設計方式連接資料流程元件](../building-packages-programmatically/connecting-data-flow-components-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="db689-115">For more information, see [Connecting Data Flow Components Programmatically](../building-packages-programmatically/connecting-data-flow-components-programmatically.md).</span></span>  
  
 <span data-ttu-id="db689-116">路徑註解顯示路徑來源的名稱，或在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中 [資料流程] 索引標籤設計介面上的路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="db689-116">A path annotation displays the name of the path source or the path name on the design surface of the **Data Flow** tab in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="db689-117">路徑註解與您可加入資料流程、控制流程和事件處理常式的註解相似。</span><span class="sxs-lookup"><span data-stu-id="db689-117">Path annotations are similar to the annotations you can add to data flows, control flows, and event handlers.</span></span> <span data-ttu-id="db689-118">唯一不同之處在於路徑註解是附加到路徑上的，而其他註解則顯示於 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師的 [資料流程]、[控制流程] 和 [事件處理常式] 索引標籤上。</span><span class="sxs-lookup"><span data-stu-id="db689-118">The only difference is that a path annotation is attached to a path, whereas other annotations appear on the **Data Flow**, **Control Flow**, and **Event Handle**r tabs of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="db689-119">中繼資料顯示上一個元件輸出中之每個資料行的名稱、資料類型、有效位數、小數位數、長度、字碼頁和來源元件。</span><span class="sxs-lookup"><span data-stu-id="db689-119">The metadata shows the name, data type, precision, scale, length, code page, and source component of each column in the output of the previous component.</span></span> <span data-ttu-id="db689-120">來源元件是建立資料行的資料流程元件。</span><span class="sxs-lookup"><span data-stu-id="db689-120">The source component is the data flow component that created the column.</span></span> <span data-ttu-id="db689-121">但不一定是資料流程中的第一個元件。</span><span class="sxs-lookup"><span data-stu-id="db689-121">This may or may not be the first component in the data flow.</span></span> <span data-ttu-id="db689-122">例如，「聯集全部」和「排序」轉換都會建立自己的資料行，因此它們是其輸出資料行的來源。</span><span class="sxs-lookup"><span data-stu-id="db689-122">For example, the Union All and Sort transformations create their own columns, and they are the sources of their output columns.</span></span> <span data-ttu-id="db689-123">相反地，「複製資料行」轉換可以通過資料行而不對其進行變更，或可以藉由複製輸入資料行來建立新的資料行。</span><span class="sxs-lookup"><span data-stu-id="db689-123">In contrast, a Copy Column transformation can pass through columns without changing them or can create new columns by copying input columns.</span></span> <span data-ttu-id="db689-124">因此「複製資料行」轉換僅是新資料行的來源元件。</span><span class="sxs-lookup"><span data-stu-id="db689-124">The Copy Column transformation is the source component only of the new columns.</span></span>  
  
 <span data-ttu-id="db689-125">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="db689-125">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="db689-126">如需可在 [資料流程路徑編輯器]\*\*\*\* 對話方塊中設定之屬性的詳細資訊，請按一下下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="db689-126">For more information about the properties that you can set in the **Data Flow Path Editor** dialog box, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="db689-127">[[資料流程路徑編輯器] &#40;一般頁面&#41;](../general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="db689-127">[Data Flow Path Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md)</span></span>  
  
-   [<span data-ttu-id="db689-128">資料流程路徑編輯器 &#40;中繼資料頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="db689-128">Data Flow Path Editor &#40;Metadata Page&#41;</span></span>](../data-flow-path-editor-metadata-page.md)  
  
-   [<span data-ttu-id="db689-129">資料檢視器頁面 &#40;的資料流程路徑編輯器&#41;</span><span class="sxs-lookup"><span data-stu-id="db689-129">Data Flow Path Editor &#40;Data Viewers Page&#41;</span></span>](../data-flow-path-editor-data-viewers-page.md)  
  
 <span data-ttu-id="db689-130">如需可透過程式設計方式設定之屬性的詳細資訊，請參閱[路徑屬性](../path-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="db689-130">For more information about the properties that you can set programmatically, see [Path Properties](../path-properties.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="db689-131">相關工作</span><span class="sxs-lookup"><span data-stu-id="db689-131">Related Tasks</span></span>  
  
-   [<span data-ttu-id="db689-132">在資料流程路徑編輯器中檢視路徑中繼資料</span><span class="sxs-lookup"><span data-stu-id="db689-132">View Path Metadata in the Data Flow Path Editor</span></span>](../view-path-metadata-in-the-data-flow-path-editor.md)  
  
-   [<span data-ttu-id="db689-133">連接資料流程中的元件</span><span class="sxs-lookup"><span data-stu-id="db689-133">Connect Components in a Data Flow</span></span>](connect-components-in-a-data-flow.md)  
  
## <a name="see-also"></a><span data-ttu-id="db689-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db689-134">See Also</span></span>  
 [<span data-ttu-id="db689-135">資料流程</span><span class="sxs-lookup"><span data-stu-id="db689-135">Data Flow</span></span>](data-flow.md)  
  
  
