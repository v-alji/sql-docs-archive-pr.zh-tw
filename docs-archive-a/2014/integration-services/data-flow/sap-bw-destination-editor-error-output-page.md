---
title: SAP BW 目的地編輯器 (錯誤輸出頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a543d811-0bd2-4890-a0d3-f5fdcd4524b8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9ffd58580865a71626252aa2d177530e41156537
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687077"
---
# <a name="sap-bw-destination-editor-error-output-page"></a><span data-ttu-id="2e5b9-102">SAP BW 目的地編輯器 (錯誤輸出頁面)</span><span class="sxs-lookup"><span data-stu-id="2e5b9-102">SAP BW Destination Editor (Error Output Page)</span></span>
  <span data-ttu-id="2e5b9-103">使用 [SAP BW 目的地編輯器] 的 [錯誤輸出] 頁面可以指定錯誤處理選項。</span><span class="sxs-lookup"><span data-stu-id="2e5b9-103">Use the **Error Output** page of the **SAP BW Destination Editor** to specify error handling options.</span></span>  
  
 <span data-ttu-id="2e5b9-104">若要深入了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 目的地，請參閱 [SAP BW 目的地](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="2e5b9-104">To learn more about the SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2e5b9-105">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="2e5b9-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="2e5b9-106">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="2e5b9-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="2e5b9-107">**開啟錯誤輸出頁面**</span><span class="sxs-lookup"><span data-stu-id="2e5b9-107">**To open the Error Output page**</span></span>  
  
1.  <span data-ttu-id="2e5b9-108">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含 SAP BW 目的地的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件。</span><span class="sxs-lookup"><span data-stu-id="2e5b9-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="2e5b9-109">在 [資料流程]  索引標籤上，按兩下 SAP BW 目的地。</span><span class="sxs-lookup"><span data-stu-id="2e5b9-109">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="2e5b9-110">在 [SAP BW 目的地編輯器]  中，按一下 [錯誤輸出]  開啟編輯器的 [錯誤輸出]  頁面。</span><span class="sxs-lookup"><span data-stu-id="2e5b9-110">In the **SAP BW Destination Editor**, click **Error Output** to open the **Error Output** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2e5b9-111">選項。</span><span class="sxs-lookup"><span data-stu-id="2e5b9-111">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2e5b9-112">如果您不知道設定目的地的所有必要值，可能必須詢問 SAP 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="2e5b9-112">If you do not know all the values that are required to configure the destination, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="2e5b9-113">**輸入或輸出**</span><span class="sxs-lookup"><span data-stu-id="2e5b9-113">**Input or Output**</span></span>  
 <span data-ttu-id="2e5b9-114">檢視輸入的名稱。</span><span class="sxs-lookup"><span data-stu-id="2e5b9-114">View the name of the input.</span></span>  
  
 <span data-ttu-id="2e5b9-115">**資料行**</span><span class="sxs-lookup"><span data-stu-id="2e5b9-115">**Column**</span></span>  
 <span data-ttu-id="2e5b9-116">這個選項不適用。</span><span class="sxs-lookup"><span data-stu-id="2e5b9-116">This option is not used.</span></span>  
  
 <span data-ttu-id="2e5b9-117">**錯誤**</span><span class="sxs-lookup"><span data-stu-id="2e5b9-117">**Error**</span></span>  
 <span data-ttu-id="2e5b9-118">指定目的地應該在發生錯誤時採取的動作：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="2e5b9-118">Specify what the destination should do when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="2e5b9-119">**截斷**</span><span class="sxs-lookup"><span data-stu-id="2e5b9-119">**Truncation**</span></span>  
 <span data-ttu-id="2e5b9-120">這個選項不適用。</span><span class="sxs-lookup"><span data-stu-id="2e5b9-120">This option is not used.</span></span>  
  
 <span data-ttu-id="2e5b9-121">**說明**</span><span class="sxs-lookup"><span data-stu-id="2e5b9-121">**Description**</span></span>  
 <span data-ttu-id="2e5b9-122">檢視作業的描述。</span><span class="sxs-lookup"><span data-stu-id="2e5b9-122">View the description of the operation.</span></span>  
  
 <span data-ttu-id="2e5b9-123">**將這個值設定到選取的資料格**</span><span class="sxs-lookup"><span data-stu-id="2e5b9-123">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="2e5b9-124">指定目的地應該在發生錯誤或截斷時對所有選取之資料格採取的動作：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="2e5b9-124">Specify what the destination should do to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="2e5b9-125">**套用**</span><span class="sxs-lookup"><span data-stu-id="2e5b9-125">**Apply**</span></span>  
 <span data-ttu-id="2e5b9-126">將錯誤處理選項套用至選取的資料格。</span><span class="sxs-lookup"><span data-stu-id="2e5b9-126">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e5b9-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e5b9-127">See Also</span></span>  
 <span data-ttu-id="2e5b9-128">[SAP BW 目的地編輯器 &#40;連線管理員頁面&#41;](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="2e5b9-128">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="2e5b9-129">[SAP BW 目的地編輯器 &#40;對應頁面&#41;](sap-bw-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="2e5b9-129">[SAP BW Destination Editor &#40;Mappings Page&#41;](sap-bw-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="2e5b9-130">[SAP BW 目的地編輯器 &#40;進階頁面&#41;](sap-bw-destination-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="2e5b9-130">[SAP BW Destination Editor &#40;Advanced Page&#41;](sap-bw-destination-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="2e5b9-131">Microsoft Connector 1.1 for SAP BW F1 說明</span><span class="sxs-lookup"><span data-stu-id="2e5b9-131">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
