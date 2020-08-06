---
title: SAP BW 來源編輯器 (錯誤輸出頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b6e23b0c-949a-46d1-8424-4dc3d9035e79
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a4ad2d02d3f5ec5c1a786019e18fa01665fdc0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687073"
---
# <a name="sap-bw-source-editor-error-output-page"></a><span data-ttu-id="42cca-102">SAP BW 來源編輯器 (錯誤輸出頁面)</span><span class="sxs-lookup"><span data-stu-id="42cca-102">SAP BW Source Editor (Error Output Page)</span></span>
  <span data-ttu-id="42cca-103">使用 **[SAP BW 來源編輯器]** 的 **[錯誤輸出]** 頁面可以選取錯誤處理選項，並設定錯誤輸出資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="42cca-103">Use the **Error Output** page of the **SAP BW Source Editor** to select error handling options and to set properties on error output columns.</span></span>  
  
 <span data-ttu-id="42cca-104">若要深入了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 來源元件，請參閱 [SAP BW 來源](sap-bw-source.md)。</span><span class="sxs-lookup"><span data-stu-id="42cca-104">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="42cca-105">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="42cca-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="42cca-106">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="42cca-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="42cca-107">擷取 SAP Netweaver BW 中的資料需要額外的 SAP 授權。</span><span class="sxs-lookup"><span data-stu-id="42cca-107">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="42cca-108">請洽詢 SAP 以確認這些需求。</span><span class="sxs-lookup"><span data-stu-id="42cca-108">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="42cca-109">**開啟錯誤輸出頁面**</span><span class="sxs-lookup"><span data-stu-id="42cca-109">**To open the Error Output page**</span></span>  
  
1.  <span data-ttu-id="42cca-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含 SAP BW 來源的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="42cca-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="42cca-111">在 [資料流程]  索引標籤上，按兩下 SAP BW 來源。</span><span class="sxs-lookup"><span data-stu-id="42cca-111">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="42cca-112">在 **[SAP BW 來源編輯器]** 中，按一下 **[錯誤輸出]** 開啟編輯器的 **[錯誤輸出]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="42cca-112">In the **SAP BW Source Editor**, click **Error Output** to open the **Error Output** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="42cca-113">選項。</span><span class="sxs-lookup"><span data-stu-id="42cca-113">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="42cca-114">如果您不知道設定來源的所有必要值，可能必須詢問 SAP 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="42cca-114">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="42cca-115">**輸入或輸出**</span><span class="sxs-lookup"><span data-stu-id="42cca-115">**Input or Output**</span></span>  
 <span data-ttu-id="42cca-116">檢視資料來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="42cca-116">View the name of the data source.</span></span>  
  
 <span data-ttu-id="42cca-117">**資料行**</span><span class="sxs-lookup"><span data-stu-id="42cca-117">**Column**</span></span>  
 <span data-ttu-id="42cca-118">檢視您在 [SAP BW 來源編輯器] 對話方塊之 [資料行] 頁面上所選取的外部 (來源) 資料行。</span><span class="sxs-lookup"><span data-stu-id="42cca-118">View the external (source) columns that you selected on the **Columns** page of the **SAP BW Source Editor** dialog box.</span></span> <span data-ttu-id="42cca-119">如需此對話方塊的詳細資訊，請參閱 [SAP BW 來源編輯器 &#40;資料行頁面&#41;](sap-bw-source-editor-columns-page.md)。</span><span class="sxs-lookup"><span data-stu-id="42cca-119">For more information about this dialog box, see [SAP BW Source Editor &#40;Columns Page&#41;](sap-bw-source-editor-columns-page.md).</span></span>  
  
 <span data-ttu-id="42cca-120">**錯誤**</span><span class="sxs-lookup"><span data-stu-id="42cca-120">**Error**</span></span>  
 <span data-ttu-id="42cca-121">指定 SAP BW 來源元件應該在發生錯誤時採取的動作：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="42cca-121">Specify what the SAP BW source component should do when there is an error: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="42cca-122">**截斷**</span><span class="sxs-lookup"><span data-stu-id="42cca-122">**Truncation**</span></span>  
 <span data-ttu-id="42cca-123">指定 SAP BW 來源元件應該在發生截斷時採取的動作：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="42cca-123">Specify what the SAP BW source component should do when a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="42cca-124">**說明**</span><span class="sxs-lookup"><span data-stu-id="42cca-124">**Description**</span></span>  
 <span data-ttu-id="42cca-125">檢視錯誤的描述。</span><span class="sxs-lookup"><span data-stu-id="42cca-125">View the description of the error.</span></span>  
  
 <span data-ttu-id="42cca-126">**將這個值設定到選取的資料格**</span><span class="sxs-lookup"><span data-stu-id="42cca-126">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="42cca-127">指定 SAP BW 來源元件應該在發生錯誤或截斷時對所有選取之資料格採取的動作：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="42cca-127">Specify what the SAP BW source component should do to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="42cca-128">**套用**</span><span class="sxs-lookup"><span data-stu-id="42cca-128">**Apply**</span></span>  
 <span data-ttu-id="42cca-129">將錯誤處理選項套用至選取的資料格。</span><span class="sxs-lookup"><span data-stu-id="42cca-129">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42cca-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42cca-130">See Also</span></span>  
 <span data-ttu-id="42cca-131">[SAP BW 來源編輯器 &#40;連線管理員頁面&#41;](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="42cca-131">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="42cca-132">[SAP BW 來源編輯器 &#40;資料行頁面&#41;](sap-bw-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="42cca-132">[SAP BW Source Editor &#40;Columns Page&#41;](sap-bw-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="42cca-133">[SAP BW 來源編輯器 &#40;進階頁面&#41;](sap-bw-source-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="42cca-133">[SAP BW Source Editor &#40;Advanced Page&#41;](sap-bw-source-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="42cca-134">Microsoft Connector 1.1 for SAP BW F1 說明</span><span class="sxs-lookup"><span data-stu-id="42cca-134">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
