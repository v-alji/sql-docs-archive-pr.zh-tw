---
title: SAP BW 來源編輯器 (進階頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 44f3c991-9e8f-4126-a9a2-2d9da779fb11
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7c78d40555a30031bf39abda18048fda9c648d01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707706"
---
# <a name="sap-bw-source-editor-advanced-page"></a><span data-ttu-id="3de72-102">SAP BW 來源編輯器 (進階頁面)</span><span class="sxs-lookup"><span data-stu-id="3de72-102">SAP BW Source Editor (Advanced Page)</span></span>
  <span data-ttu-id="3de72-103">使用 [SAP BW 來源編輯器] 的 [進階] 頁面可以指定字串轉換規則和逾時期限，也可以重設特定要求識別碼的狀態。</span><span class="sxs-lookup"><span data-stu-id="3de72-103">Use the **Advanced** page of the **SAP BW Source Editor** to specify the string conversion rule and the time-out period, and also to reset the status of a particular Request ID.</span></span>  
  
 <span data-ttu-id="3de72-104">若要深入了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 來源元件，請參閱 [SAP BW 來源](sap-bw-source.md)。</span><span class="sxs-lookup"><span data-stu-id="3de72-104">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3de72-105">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="3de72-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="3de72-106">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="3de72-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3de72-107">擷取 SAP Netweaver BW 中的資料需要額外的 SAP 授權。</span><span class="sxs-lookup"><span data-stu-id="3de72-107">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="3de72-108">請洽詢 SAP 以確認這些需求。</span><span class="sxs-lookup"><span data-stu-id="3de72-108">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="3de72-109">**開啟連接管理員頁面**</span><span class="sxs-lookup"><span data-stu-id="3de72-109">**To open the Connection Manager page**</span></span>  
  
1.  <span data-ttu-id="3de72-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含 SAP BW 來源的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="3de72-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="3de72-111">在 [資料流程]  索引標籤上，按兩下 SAP BW 來源。</span><span class="sxs-lookup"><span data-stu-id="3de72-111">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="3de72-112">在 **[SAP BW 來源編輯器]** 中，按一下 **[進階]** 開啟編輯器的 **[進階]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="3de72-112">In the **SAP BW Source Editor**, click **Advanced** to open the **Advanced** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3de72-113">選項。</span><span class="sxs-lookup"><span data-stu-id="3de72-113">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3de72-114">如果您不知道設定來源的所有必要值，可能必須詢問 SAP 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="3de72-114">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="3de72-115">**字串轉換**</span><span class="sxs-lookup"><span data-stu-id="3de72-115">**String Conversion**</span></span>  
 <span data-ttu-id="3de72-116">指定要針對字串轉換套用的規則。</span><span class="sxs-lookup"><span data-stu-id="3de72-116">Specify the rule to apply for string conversion.</span></span>  
  
|<span data-ttu-id="3de72-117">選項</span><span class="sxs-lookup"><span data-stu-id="3de72-117">Option</span></span>|<span data-ttu-id="3de72-118">描述</span><span class="sxs-lookup"><span data-stu-id="3de72-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="3de72-119">**自動字串轉換**</span><span class="sxs-lookup"><span data-stu-id="3de72-119">**Automatic string conversion**</span></span>|<span data-ttu-id="3de72-120">當 SAP Netweaver BW 系統是 Unicode 系統時，將所有字串轉換為 `nvarchar`。</span><span class="sxs-lookup"><span data-stu-id="3de72-120">Convert all strings to `nvarchar` when the SAP Netweaver BW system is a Unicode system.</span></span> <span data-ttu-id="3de72-121">否則，將所有字串轉換為 `varchar`。</span><span class="sxs-lookup"><span data-stu-id="3de72-121">Otherwise, convert all strings to `varchar`.</span></span>|  
|<span data-ttu-id="3de72-122">**將字串轉換為 varchar**</span><span class="sxs-lookup"><span data-stu-id="3de72-122">**Convert strings to varchar**</span></span>|<span data-ttu-id="3de72-123">將所有字串轉換為 `varchar`。</span><span class="sxs-lookup"><span data-stu-id="3de72-123">Convert all strings to `varchar`.</span></span>|  
|<span data-ttu-id="3de72-124">**將字串轉換為 nvarchar**</span><span class="sxs-lookup"><span data-stu-id="3de72-124">**Convert strings to nvarchar**</span></span>|<span data-ttu-id="3de72-125">將所有字串轉換為 `nvarchar`。</span><span class="sxs-lookup"><span data-stu-id="3de72-125">Convert all strings to `nvarchar`.</span></span>|  
  
 <span data-ttu-id="3de72-126">**逾時 (秒)**</span><span class="sxs-lookup"><span data-stu-id="3de72-126">**Timeout (seconds)**</span></span>  
 <span data-ttu-id="3de72-127">指定來源應該等候的秒數上限。</span><span class="sxs-lookup"><span data-stu-id="3de72-127">Specify the maximum number of seconds that the source should wait.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3de72-128">只有當您已經在編輯器的 [連接管理員] 頁面上，選取 [W - 等候通知] 作為 [執行模式] 的值時，這個選項才有效。</span><span class="sxs-lookup"><span data-stu-id="3de72-128">This option is only valid if you have selected **W - Wait for Notify** as the value of **Execution Mode** on the **Connection Manager** page of the editor.</span></span> <span data-ttu-id="3de72-129">如需詳細資訊，請參閱 [SAP BW 來源編輯器 &#40;連接管理員頁面&#41;](sap-bw-source-editor-connection-manager-page.md)。</span><span class="sxs-lookup"><span data-stu-id="3de72-129">For more information, see [SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md).</span></span>  
  
 <span data-ttu-id="3de72-130">**要求識別碼**</span><span class="sxs-lookup"><span data-stu-id="3de72-130">**Request ID**</span></span>  
 <span data-ttu-id="3de72-131">指定您想要在按一下 [重設]  時將其狀態重設成「G - 綠色」的要求識別碼。</span><span class="sxs-lookup"><span data-stu-id="3de72-131">Specify the Request ID whose status you want to reset to "G - Green" when you click **Reset**.</span></span>  
  
 <span data-ttu-id="3de72-132">**重設**</span><span class="sxs-lookup"><span data-stu-id="3de72-132">**Reset**</span></span>  
 <span data-ttu-id="3de72-133">在提示確認之後，讓您將指定之要求識別碼的狀態重設成「G - 綠色」。</span><span class="sxs-lookup"><span data-stu-id="3de72-133">Lets you reset the status of the specified Request ID to "G - Green", after prompting you for confirmation.</span></span> <span data-ttu-id="3de72-134">在發生問題，而且 SAP Netweaver BW 系統已將要求標幟為黃色或紅色狀態時，這個選項可能很有用。</span><span class="sxs-lookup"><span data-stu-id="3de72-134">This can be useful when a problem has occurred, and the SAP Netweaver BW system has flagged the request with a yellow or red status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3de72-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3de72-135">See Also</span></span>  
 <span data-ttu-id="3de72-136">[SAP BW 來源編輯器 &#40;連線管理員頁面&#41;](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="3de72-136">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="3de72-137">[SAP BW 來源編輯器 &#40;資料行頁面&#41;](sap-bw-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="3de72-137">[SAP BW Source Editor &#40;Columns Page&#41;](sap-bw-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="3de72-138">[SAP BW 來源編輯器 &#40;錯誤輸出頁面&#41;](sap-bw-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="3de72-138">[SAP BW Source Editor &#40;Error Output Page&#41;](sap-bw-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="3de72-139">Microsoft Connector 1.1 for SAP BW F1 說明</span><span class="sxs-lookup"><span data-stu-id="3de72-139">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
