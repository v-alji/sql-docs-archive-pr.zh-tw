---
title: 預覽 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 551494c4-9e27-4592-9200-c6bf19e80c9a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a795338122c1e7a37a23fdb6af6153f74b927e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593469"
---
# <a name="preview"></a><span data-ttu-id="50bef-102">預覽</span><span class="sxs-lookup"><span data-stu-id="50bef-102">Preview</span></span>
  <span data-ttu-id="50bef-103">使用 **[預覽]** 對話方塊可以預覽 SAP BW 來源即將擷取的資料。</span><span class="sxs-lookup"><span data-stu-id="50bef-103">Use the **Preview** dialog box to preview the data that the SAP BW source will extract.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="50bef-104">**[SAP BW 來源編輯器]** 之 **[連接管理員]** 頁面上提供的 **[預覽]** 選項會實際擷取資料。</span><span class="sxs-lookup"><span data-stu-id="50bef-104">The **Preview** option, that is available on the **Connection Manager** page of the **SAP BW Source Editor**, actually extracts data.</span></span> <span data-ttu-id="50bef-105">如果您已將 SAP Netweaver BW 設定為僅擷取自從上次擷取以來已變更的資料，則選取 **[預覽]** 將會從下次擷取中排除已預覽的資料。</span><span class="sxs-lookup"><span data-stu-id="50bef-105">If you have configured SAP Netweaver BW to extract only data that has changed since the previous extraction, selecting **Preview** will exclude the previewed data from the next extraction.</span></span>  
  
 <span data-ttu-id="50bef-106">若要深入了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 來源元件，請參閱 [SAP BW 來源](sap-bw-source.md)。</span><span class="sxs-lookup"><span data-stu-id="50bef-106">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="50bef-107">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="50bef-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="50bef-108">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="50bef-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="50bef-109">擷取 SAP Netweaver BW 中的資料需要額外的 SAP 授權。</span><span class="sxs-lookup"><span data-stu-id="50bef-109">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="50bef-110">請洽詢 SAP 以確認這些需求。</span><span class="sxs-lookup"><span data-stu-id="50bef-110">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="50bef-111">**若要開啟預覽對話方塊**</span><span class="sxs-lookup"><span data-stu-id="50bef-111">**To open the Preview dialog box**</span></span>  
  
1.  <span data-ttu-id="50bef-112">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含 SAP BW 來源的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="50bef-112">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="50bef-113">在 [資料流程] 索引標籤上，按兩下 SAP BW 來源。</span><span class="sxs-lookup"><span data-stu-id="50bef-113">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="50bef-114">在 **[SAP BW 來源編輯器]** 中，按一下 **[連接管理員]** 開啟編輯器的 **[連接管理員]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="50bef-114">In the **SAP BW Source Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="50bef-115">設定 SAP BW 來源。</span><span class="sxs-lookup"><span data-stu-id="50bef-115">Configure the SAP BW source.</span></span>  
  
5.  <span data-ttu-id="50bef-116">在您設定 SAP BW 來源之後，請在 **[連接管理員]** 頁面上，按一下 **[預覽]** ，即可在 **[預覽]** 對話方塊中預覽資料。</span><span class="sxs-lookup"><span data-stu-id="50bef-116">After you configure the SAP BW source, on the **Connection Manager** page, click **Preview** to preview the data in the **Preview** dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="50bef-117">按一下 **[預覽]** 也會開啟 **[要求記錄檔]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="50bef-117">Clicking **Preview** also opens the **Request Log** dialog box.</span></span> <span data-ttu-id="50bef-118">如需有關此對話方塊的詳細資訊，請參閱＜ [Request Log](request-log.md)＞。</span><span class="sxs-lookup"><span data-stu-id="50bef-118">For more information about this dialog box, see [Request Log](request-log.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="50bef-119">選項。</span><span class="sxs-lookup"><span data-stu-id="50bef-119">Options</span></span>  
 <span data-ttu-id="50bef-120">**[預覽]** 對話方塊會顯示向 SAP Netweaver BW 系統要求的資料列。</span><span class="sxs-lookup"><span data-stu-id="50bef-120">The **Preview** dialog box displays the rows that are requested from the SAP Netweaver BW system.</span></span> <span data-ttu-id="50bef-121">顯示的資料行就是來源資料中定義的資料行。</span><span class="sxs-lookup"><span data-stu-id="50bef-121">The columns that are displayed are the columns that are defined in the source data.</span></span>  
  
 <span data-ttu-id="50bef-122">這個對話方塊沒有其他選項。</span><span class="sxs-lookup"><span data-stu-id="50bef-122">There are no other options in this dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50bef-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50bef-123">See Also</span></span>  
 <span data-ttu-id="50bef-124">[SAP BW 來源編輯器 &#40;連線管理員頁面&#41;](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="50bef-124">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="50bef-125">Microsoft Connector 1.1 for SAP BW F1 說明</span><span class="sxs-lookup"><span data-stu-id="50bef-125">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
