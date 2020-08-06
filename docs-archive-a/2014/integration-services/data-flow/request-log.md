---
title: 要求記錄檔 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 165d3833-0493-490c-9f63-8a134a7fafb8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 024012878ae94c5ba6276648e289e6e6f7c93d7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593459"
---
# <a name="request-log"></a><span data-ttu-id="13565-102">要求記錄檔</span><span class="sxs-lookup"><span data-stu-id="13565-102">Request Log</span></span>
  <span data-ttu-id="13565-103">使用 **[要求記錄檔]** 對話方塊可以檢視對 SAP Netweaver BW 系統提出資料取樣要求期間記錄的事件。</span><span class="sxs-lookup"><span data-stu-id="13565-103">Use the **Request Log** dialog box to view the events that are logged during the request that is made to the SAP Netweaver BW system for sample data.</span></span> <span data-ttu-id="13565-104">如果您需要疑難排解 SAP BW 來源的組態，這項資訊可能很有用。</span><span class="sxs-lookup"><span data-stu-id="13565-104">This information can be useful if you have to troubleshoot your configuration of the SAP BW source.</span></span>  
  
 <span data-ttu-id="13565-105">若要深入了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 來源元件，請參閱 [SAP BW 來源](sap-bw-source.md)。</span><span class="sxs-lookup"><span data-stu-id="13565-105">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="13565-106">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="13565-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="13565-107">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="13565-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="13565-108">擷取 SAP Netweaver BW 中的資料需要額外的 SAP 授權。</span><span class="sxs-lookup"><span data-stu-id="13565-108">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="13565-109">請洽詢 SAP 以確認這些需求。</span><span class="sxs-lookup"><span data-stu-id="13565-109">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="13565-110">**若要開啟要求記錄檔對話方塊**</span><span class="sxs-lookup"><span data-stu-id="13565-110">**To open the Request Log dialog box**</span></span>  
  
1.  <span data-ttu-id="13565-111">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含 SAP BW 來源的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="13565-111">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="13565-112">在 [資料流程]  索引標籤上，按兩下 SAP BW 來源。</span><span class="sxs-lookup"><span data-stu-id="13565-112">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="13565-113">在 **[SAP BW 來源編輯器]** 中，按一下 **[連接管理員]** 開啟編輯器的 **[連接管理員]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="13565-113">In the **SAP BW Source Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="13565-114">在您設定 SAP BW 來源之後，請按一下 **[預覽]** ，即可在 **[要求記錄檔]** 對話方塊中預覽事件。</span><span class="sxs-lookup"><span data-stu-id="13565-114">After you configure the SAP BW source, click **Preview** to preview the events in the **Request Log** dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="13565-115">按一下 **[預覽]** 也會開啟 **[預覽]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="13565-115">Clicking **Preview** also opens the **Preview** dialog box.</span></span> <span data-ttu-id="13565-116">如需有關此對話方塊的詳細資訊，請參閱＜ [Preview](preview.md)＞。</span><span class="sxs-lookup"><span data-stu-id="13565-116">For more information about this dialog box, see [Preview](preview.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="13565-117">選項。</span><span class="sxs-lookup"><span data-stu-id="13565-117">Options</span></span>  
 <span data-ttu-id="13565-118">**Time**</span><span class="sxs-lookup"><span data-stu-id="13565-118">**Time**</span></span>  
 <span data-ttu-id="13565-119">顯示記錄事件的時間。</span><span class="sxs-lookup"><span data-stu-id="13565-119">Displays the time that the event that was logged.</span></span>  
  
 <span data-ttu-id="13565-120">**型別**</span><span class="sxs-lookup"><span data-stu-id="13565-120">**Type**</span></span>  
 <span data-ttu-id="13565-121">顯示記錄的事件類型。</span><span class="sxs-lookup"><span data-stu-id="13565-121">Displays the type of the event that was logged.</span></span> <span data-ttu-id="13565-122">下表列出可能的事件類型。</span><span class="sxs-lookup"><span data-stu-id="13565-122">The following table lists the possible event types.</span></span>  
  
|<span data-ttu-id="13565-123">值</span><span class="sxs-lookup"><span data-stu-id="13565-123">Value</span></span>|<span data-ttu-id="13565-124">描述</span><span class="sxs-lookup"><span data-stu-id="13565-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="13565-125">S</span><span class="sxs-lookup"><span data-stu-id="13565-125">S</span></span>|<span data-ttu-id="13565-126">成功訊息。</span><span class="sxs-lookup"><span data-stu-id="13565-126">Success message.</span></span>|  
|<span data-ttu-id="13565-127">E</span><span class="sxs-lookup"><span data-stu-id="13565-127">E</span></span>|<span data-ttu-id="13565-128">錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="13565-128">Error message</span></span>|  
|<span data-ttu-id="13565-129">W</span><span class="sxs-lookup"><span data-stu-id="13565-129">W</span></span>|<span data-ttu-id="13565-130">警告訊息。</span><span class="sxs-lookup"><span data-stu-id="13565-130">Warning message.</span></span>|  
|<span data-ttu-id="13565-131">I</span><span class="sxs-lookup"><span data-stu-id="13565-131">I</span></span>|<span data-ttu-id="13565-132">參考資訊。</span><span class="sxs-lookup"><span data-stu-id="13565-132">Informational message.</span></span>|  
|<span data-ttu-id="13565-133">A</span><span class="sxs-lookup"><span data-stu-id="13565-133">A</span></span>|<span data-ttu-id="13565-134">作業已中止。</span><span class="sxs-lookup"><span data-stu-id="13565-134">The operation was aborted.</span></span>|  
  
 <span data-ttu-id="13565-135">**訊息**</span><span class="sxs-lookup"><span data-stu-id="13565-135">**Message**</span></span>  
 <span data-ttu-id="13565-136">顯示與記錄之事件相關聯的訊息文字。</span><span class="sxs-lookup"><span data-stu-id="13565-136">Displays the message text that is associated with the logged event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13565-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13565-137">See Also</span></span>  
 <span data-ttu-id="13565-138">[SAP BW 來源編輯器 &#40;連線管理員頁面&#41;](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="13565-138">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="13565-139">Microsoft Connector 1.1 for SAP BW F1 說明</span><span class="sxs-lookup"><span data-stu-id="13565-139">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
