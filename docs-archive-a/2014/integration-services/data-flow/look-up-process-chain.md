---
title: 查閱處理序鏈結 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f6303ea4-fbbf-4cba-bc60-828df62be8c2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2e0d3743071d018a8a82f60eeaf04fd86dec3e63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700072"
---
# <a name="look-up-process-chain"></a><span data-ttu-id="b73cf-102">查閱 ProcessChain</span><span class="sxs-lookup"><span data-stu-id="b73cf-102">Look Up Process Chain</span></span>
  <span data-ttu-id="b73cf-103">使用 **[查閱 ProcessChain]** 對話方塊可以查閱 SAP Netweaver BW 系統中定義的處理序鏈結。</span><span class="sxs-lookup"><span data-stu-id="b73cf-103">Use the **Look Up Process Chain** dialog box to look up a process chain that is defined in the SAP Netweaver BW system.</span></span> <span data-ttu-id="b73cf-104">出現可用的處理序鏈結清單時，請選取您要的鏈結，然後來源就會將必要的值填入相關聯的選項。</span><span class="sxs-lookup"><span data-stu-id="b73cf-104">When the list of available process chains appears, select the chain that you want, and the source will populate the associated options with the required values.</span></span>  
  
 <span data-ttu-id="b73cf-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 來源會使用 **[查閱 ProcessChain]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b73cf-105">The SAP BW source of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW uses the **Look Up Process Chain** dialog box.</span></span> <span data-ttu-id="b73cf-106">若要了解有關 SAP BW 來源的詳細資訊，請參閱＜ [SAP BW Source](sap-bw-source.md)＞。</span><span class="sxs-lookup"><span data-stu-id="b73cf-106">To learn more about the SAP BW source, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b73cf-107">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="b73cf-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="b73cf-108">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="b73cf-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="b73cf-109">**若要開啟查閱 ProcessChain 對話方塊**</span><span class="sxs-lookup"><span data-stu-id="b73cf-109">**To open the Look Up Process Chain dialog box**</span></span>  
  
1.  <span data-ttu-id="b73cf-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含 SAP BW 來源的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="b73cf-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="b73cf-111">在 [資料流程]  索引標籤上，按兩下 SAP BW 來源。</span><span class="sxs-lookup"><span data-stu-id="b73cf-111">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="b73cf-112">在 **[SAP BW 來源編輯器]** 中，按一下 **[連接管理員]** 開啟編輯器的 **[連接管理員]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="b73cf-112">In the **SAP BW Source Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="b73cf-113">在 **[處理序鏈結]** 群組方塊中，按一下 **[查閱]** 顯示 **[查閱 ProcessChain]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b73cf-113">In the **Process Chain** group box, click **Look up** to display the **Look Up Process Chain** dialog box.</span></span>  
  
     <span data-ttu-id="b73cf-114">只有當 [執行模式] 的值是 [P - 觸發處理鏈結] 時，才會出現 [處理序鏈結] 群組方塊。</span><span class="sxs-lookup"><span data-stu-id="b73cf-114">The **Process Chain** group box appears only if the value for **Execution mode** is **P - Trigger process chain**.</span></span>  
  
## <a name="lookup-options"></a><span data-ttu-id="b73cf-115">查閱選項</span><span class="sxs-lookup"><span data-stu-id="b73cf-115">Lookup Options</span></span>  
 <span data-ttu-id="b73cf-116">在查閱欄位中，您可以使用星號萬用字元 (\*) 或結合星號萬用字元使用部分字串來篩選結果。</span><span class="sxs-lookup"><span data-stu-id="b73cf-116">In the lookup fields, you can filter results by using the asterisk wildcard character (\*), or by using a partial string in combination with the asterisk wildcard character.</span></span> <span data-ttu-id="b73cf-117">不過，如果您將查閱欄位保留空白，查閱作業就只會比對該欄位中的空白字串。</span><span class="sxs-lookup"><span data-stu-id="b73cf-117">However, if you leave a lookup field empty, the lookup operation will only match empty strings in that field.</span></span>  
  
 <span data-ttu-id="b73cf-118">**處理序鏈結**</span><span class="sxs-lookup"><span data-stu-id="b73cf-118">**Process chain**</span></span>  
 <span data-ttu-id="b73cf-119">輸入您想要查閱的處理序鏈結名稱，或輸入包含星號萬用字元 (\*) 的部分名稱。</span><span class="sxs-lookup"><span data-stu-id="b73cf-119">Enter the name of the process chain that you want to look up, or enter a partial name with the asterisk wildcard character (\*).</span></span> <span data-ttu-id="b73cf-120">或者，單獨使用星號萬用字元來包含所有處理序鏈結。</span><span class="sxs-lookup"><span data-stu-id="b73cf-120">Or, use the asterisk wildcard character alone to include all process chains.</span></span>  
  
 <span data-ttu-id="b73cf-121">**查閱**</span><span class="sxs-lookup"><span data-stu-id="b73cf-121">**Look up**</span></span>  
 <span data-ttu-id="b73cf-122">查閱 SAP Netweaver BW 系統中定義的相符處理序鏈結。</span><span class="sxs-lookup"><span data-stu-id="b73cf-122">Look up matching process chains that are defined in the SAP Netweaver BW system.</span></span>  
  
## <a name="lookup-results"></a><span data-ttu-id="b73cf-123">查閱結果</span><span class="sxs-lookup"><span data-stu-id="b73cf-123">Lookup Results</span></span>  
 <span data-ttu-id="b73cf-124">在您按一下 [查閱] 按鈕之後，SAP Netweaver BW 系統中的處理序鏈結清單就會顯示在包含下列資料行標題的資料表中：</span><span class="sxs-lookup"><span data-stu-id="b73cf-124">After you click the Look up button, a list of the process chains in the SAP Netweaver BW system appears in a table with the following column headings:</span></span>  
  
 <span data-ttu-id="b73cf-125">**[處理序鏈結]**</span><span class="sxs-lookup"><span data-stu-id="b73cf-125">**Process Chain**</span></span>  
 <span data-ttu-id="b73cf-126">顯示 SAP Netweaver BW 系統中定義的處理序鏈結名稱。</span><span class="sxs-lookup"><span data-stu-id="b73cf-126">Displays the name of the process chain that is defined in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="b73cf-127">**說明**</span><span class="sxs-lookup"><span data-stu-id="b73cf-127">**Description**</span></span>  
 <span data-ttu-id="b73cf-128">顯示處理序鏈結的描述。</span><span class="sxs-lookup"><span data-stu-id="b73cf-128">Displays the description of the process chain.</span></span>  
  
 <span data-ttu-id="b73cf-129">出現可用的處理序鏈結清單時，請選取您要的鏈結，然後來源就會將必要的值填入相關聯的選項。</span><span class="sxs-lookup"><span data-stu-id="b73cf-129">When the list of available process chains appears, select the chain that you want, and the source will populate the associated options with the required values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b73cf-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b73cf-130">See Also</span></span>  
 <span data-ttu-id="b73cf-131">[SAP BW 來源編輯器 &#40;連線管理員頁面&#41;](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="b73cf-131">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="b73cf-132">Microsoft Connector 1.1 for SAP BW F1 說明</span><span class="sxs-lookup"><span data-stu-id="b73cf-132">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
