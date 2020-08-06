---
title: SAP BW 來源編輯器 (連線管理員頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 2a6dc531-85ca-43c5-a65f-3ad3f7d537c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8c6b1782daf8c00b3b3d3a7d13b5ffa00adeeba2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687075"
---
# <a name="sap-bw-source-editor-connection-manager-page"></a><span data-ttu-id="47573-102">SAP BW 來源編輯器 (連接管理員頁面)</span><span class="sxs-lookup"><span data-stu-id="47573-102">SAP BW Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="47573-103">使用 **[SAP BW 來源編輯器]** 的 **[連接管理員]** 頁面可以選取 SAP BW 來源的 SAP BW 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="47573-103">Use the **Connection Manager** page of the **SAP BW Source Editor** to select the SAP BW connection manager for the SAP BW source.</span></span> <span data-ttu-id="47573-104">在這個頁面上，您也可以選取執行模式以及從 SAP Netweaver BW 系統中擷取資料所用的參數。</span><span class="sxs-lookup"><span data-stu-id="47573-104">On this page, you also select the execution mode and the parameters for extracting the data from the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="47573-105">若要深入了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 來源元件，請參閱 [SAP BW 來源](sap-bw-source.md)。</span><span class="sxs-lookup"><span data-stu-id="47573-105">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="47573-106">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="47573-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="47573-107">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="47573-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="47573-108">擷取 SAP Netweaver BW 中的資料需要額外的 SAP 授權。</span><span class="sxs-lookup"><span data-stu-id="47573-108">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="47573-109">請洽詢 SAP 以確認這些需求。</span><span class="sxs-lookup"><span data-stu-id="47573-109">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="47573-110">**開啟連接管理員頁面**</span><span class="sxs-lookup"><span data-stu-id="47573-110">**To open the Connection Manager page**</span></span>  
  
1.  <span data-ttu-id="47573-111">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含 SAP BW 來源的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="47573-111">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="47573-112">在 [資料流程]  索引標籤上，按兩下 SAP BW 來源。</span><span class="sxs-lookup"><span data-stu-id="47573-112">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="47573-113">在 **[SAP BW 來源編輯器]** 中，按一下 **[連接管理員]** 開啟編輯器的 **[連接管理員]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="47573-113">In the **SAP BW Source Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="47573-114">靜態選項</span><span class="sxs-lookup"><span data-stu-id="47573-114">Static Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="47573-115">如果您不知道設定來源的所有必要值，可能必須詢問 SAP 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="47573-115">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="47573-116">**SAP BW 連接管理員**</span><span class="sxs-lookup"><span data-stu-id="47573-116">**SAP BW connection manager**</span></span>  
 <span data-ttu-id="47573-117">從清單中選取現有的連線管理員，或按一下 [新增]  來建立新的連線。</span><span class="sxs-lookup"><span data-stu-id="47573-117">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="47573-118">**新增**</span><span class="sxs-lookup"><span data-stu-id="47573-118">**New**</span></span>  
 <span data-ttu-id="47573-119">使用 [SAP BW 連線管理員]  對話方塊來建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="47573-119">Create a new connection manager by using the **SAP BW Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="47573-120">如需有關此對話方塊的詳細資訊，請參閱＜ [SAP BW Connection Manager Editor](../sap-bw-connection-manager-editor.md)＞。</span><span class="sxs-lookup"><span data-stu-id="47573-120">For more information about this dialog box, see [SAP BW Connection Manager Editor](../sap-bw-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="47573-121">**OHS 目的地**</span><span class="sxs-lookup"><span data-stu-id="47573-121">**OHS destination**</span></span>  
 <span data-ttu-id="47573-122">選取要從來源中擷取資料所用的開放式中心服務 (Open Hub Service，OHS) 目的地。</span><span class="sxs-lookup"><span data-stu-id="47573-122">Select the Open Hub Service (OHS) destination to use to extract data from the source.</span></span>  
  
 <span data-ttu-id="47573-123">**執行模式**</span><span class="sxs-lookup"><span data-stu-id="47573-123">**Execution mode**</span></span>  
 <span data-ttu-id="47573-124">指定從來源中擷取資料的方法。</span><span class="sxs-lookup"><span data-stu-id="47573-124">Specify the method for extracting data from the source.</span></span>  
  
|<span data-ttu-id="47573-125">選項</span><span class="sxs-lookup"><span data-stu-id="47573-125">Option</span></span>|<span data-ttu-id="47573-126">描述</span><span class="sxs-lookup"><span data-stu-id="47573-126">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="47573-127">**P - 觸發處理鏈結**</span><span class="sxs-lookup"><span data-stu-id="47573-127">**P - Trigger Process Chain**</span></span>|<span data-ttu-id="47573-128">觸發處理序鏈結。</span><span class="sxs-lookup"><span data-stu-id="47573-128">Trigger a process chain.</span></span> <span data-ttu-id="47573-129">在此情況下， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝會啟動擷取處理序。</span><span class="sxs-lookup"><span data-stu-id="47573-129">In this case, the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package starts the extraction process.</span></span>|  
|<span data-ttu-id="47573-130">**W - 等候通知**</span><span class="sxs-lookup"><span data-stu-id="47573-130">**W - Wait for Notify**</span></span>|<span data-ttu-id="47573-131">等候來自 SAP Netweaver BW 系統的通知，以便開始擷取資料。</span><span class="sxs-lookup"><span data-stu-id="47573-131">Wait for notification from the SAP Netweaver BW system to begin extracting the data.</span></span> <span data-ttu-id="47573-132">在此情況下，SAP Netweaver BW 系統會啟動擷取處理序。</span><span class="sxs-lookup"><span data-stu-id="47573-132">In this case, the SAP Netweaver BW system starts the extraction process.</span></span>|  
|<span data-ttu-id="47573-133">**E - 僅限擷取**</span><span class="sxs-lookup"><span data-stu-id="47573-133">**E - Extract Only**</span></span>|<span data-ttu-id="47573-134">擷取與特定要求識別碼相關聯的資料。</span><span class="sxs-lookup"><span data-stu-id="47573-134">Retrieve the data that is associated with a particular Request ID.</span></span> <span data-ttu-id="47573-135">在此情況下，SAP Netweaver BW 系統已經將資料擷取到內部資料表中，而且 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝剛剛讀取資料。</span><span class="sxs-lookup"><span data-stu-id="47573-135">In this case, the SAP Netweaver BW system has already extracted the data into an internal table, and the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package just reads the data.</span></span>|  
  
 <span data-ttu-id="47573-136">**預覽**</span><span class="sxs-lookup"><span data-stu-id="47573-136">**Preview**</span></span>  
 <span data-ttu-id="47573-137">開啟 [預覽]  對話方塊，以便預覽結果。</span><span class="sxs-lookup"><span data-stu-id="47573-137">Open the **Preview** dialog box in which you can preview results.</span></span> <span data-ttu-id="47573-138">如需詳細資訊，請參閱 [Preview](preview.md)。</span><span class="sxs-lookup"><span data-stu-id="47573-138">For more information, see [Preview](preview.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="47573-139">[SAP BW 來源編輯器] 之 **[連接管理員]** 頁面上提供的 **[預覽]** 選項會實際擷取資料。</span><span class="sxs-lookup"><span data-stu-id="47573-139">The **Preview** option, that is available on the **Connection Manager** page of the SAP BW Source Editor, actually extracts data.</span></span> <span data-ttu-id="47573-140">如果您已將 SAP Netweaver BW 設定為僅擷取自從上次擷取以來已變更的資料，則選取 **[預覽]** 將會從下次擷取中排除已預覽的資料。</span><span class="sxs-lookup"><span data-stu-id="47573-140">If you have configured SAP Netweaver BW to extract only data that has changed since the previous extraction, selecting **Preview** will exclude the previewed data from the next extraction.</span></span>  
  
 <span data-ttu-id="47573-141">當您按一下 **[預覽]** 時，也會開啟 **[要求記錄檔]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="47573-141">When you click **Preview**, you also open the **Request Log** dialog box.</span></span> <span data-ttu-id="47573-142">您可以使用此對話方塊來檢視對 SAP Netweaver BW 系統提出資料取樣要求期間記錄的事件。</span><span class="sxs-lookup"><span data-stu-id="47573-142">You can use this dialog box to view the events that are logged during the request that is made to the SAP Netweaver BW system for sample data.</span></span> <span data-ttu-id="47573-143">如需詳細資訊，請參閱 [Request Log](request-log.md)。</span><span class="sxs-lookup"><span data-stu-id="47573-143">For more information, see [Request Log](request-log.md).</span></span>  
  
## <a name="execution-mode-dynamic-options"></a><span data-ttu-id="47573-144">執行模式動態選項</span><span class="sxs-lookup"><span data-stu-id="47573-144">Execution Mode Dynamic Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="47573-145">如果您不知道設定來源的所有必要值，可能必須詢問 SAP 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="47573-145">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
### <a name="execution-mode--p---trigger-process-chain"></a><span data-ttu-id="47573-146">執行模式 = P - 觸發處理鏈結</span><span class="sxs-lookup"><span data-stu-id="47573-146">Execution Mode = P - Trigger Process Chain</span></span>  
  
#### <a name="rfc-destination-options"></a><span data-ttu-id="47573-147">RFC 目的地選項</span><span class="sxs-lookup"><span data-stu-id="47573-147">RFC Destination Options</span></span>  
 <span data-ttu-id="47573-148">您不需要事先了解並輸入這些值。</span><span class="sxs-lookup"><span data-stu-id="47573-148">You do not have to know and enter these values in advance.</span></span> <span data-ttu-id="47573-149">使用 **[查閱]** 按鈕，即可尋找並選取適當的 RFC 目的地。</span><span class="sxs-lookup"><span data-stu-id="47573-149">Use the **Look up** button to find and select the appropriate RFC destination.</span></span> <span data-ttu-id="47573-150">在您選取 RFC 目的地之後，此元件就會針對這些選項輸入適當的值。</span><span class="sxs-lookup"><span data-stu-id="47573-150">After you select an RFC destination, the component enters the appropriate values for these options.</span></span>  
  
 <span data-ttu-id="47573-151">**閘道器主機**</span><span class="sxs-lookup"><span data-stu-id="47573-151">**Gateway host**</span></span>  
 <span data-ttu-id="47573-152">輸入閘道器主機的伺服器名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="47573-152">Enter the server name or IP address of the gateway host.</span></span> <span data-ttu-id="47573-153">此名稱或 IP 位址通常與 SAP 應用程式伺服器相同。</span><span class="sxs-lookup"><span data-stu-id="47573-153">Usually, the name or IP address is the same as the SAP application server.</span></span>  
  
 <span data-ttu-id="47573-154">**閘道器服務**</span><span class="sxs-lookup"><span data-stu-id="47573-154">**Gateway service**</span></span>  
 <span data-ttu-id="47573-155">以 `sapgwNN` 格式輸入閘道服務的名稱，其中 `NN` 是系統編號。</span><span class="sxs-lookup"><span data-stu-id="47573-155">Enter the name of the gateway service, in the format `sapgwNN`, where `NN` is the system number.</span></span>  
  
 <span data-ttu-id="47573-156">**程式識別碼**</span><span class="sxs-lookup"><span data-stu-id="47573-156">**Program ID**</span></span>  
 <span data-ttu-id="47573-157">輸入與 RFC 目的地相關聯的程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="47573-157">Enter the Program ID that is associated with the RFC destination.</span></span>  
  
 <span data-ttu-id="47573-158">**查閱**</span><span class="sxs-lookup"><span data-stu-id="47573-158">**Look up**</span></span>  
 <span data-ttu-id="47573-159">使用 [查閱 RFC 目的地]  對話方塊來查閱 RFC 目的地。</span><span class="sxs-lookup"><span data-stu-id="47573-159">Look up the RFC destination by using the **Look Up RFC Destination** dialog box.</span></span> <span data-ttu-id="47573-160">如需有關此對話方塊的詳細資訊，請參閱＜ [Look Up RFC Destination](look-up-rfc-destination.md)＞。</span><span class="sxs-lookup"><span data-stu-id="47573-160">For more information about this dialog box, see [Look Up RFC Destination](look-up-rfc-destination.md).</span></span>  
  
#### <a name="process-chain-options"></a><span data-ttu-id="47573-161">處理序鏈結選項</span><span class="sxs-lookup"><span data-stu-id="47573-161">Process Chain Options</span></span>  
 <span data-ttu-id="47573-162">您不需要事先了解並輸入這些值。</span><span class="sxs-lookup"><span data-stu-id="47573-162">You do not have to know and enter these values in advance.</span></span> <span data-ttu-id="47573-163">使用 **[查閱]** 按鈕，即可尋找並選取適當的處理序鏈結。</span><span class="sxs-lookup"><span data-stu-id="47573-163">Use the **Look up** button to find and select the appropriate process chain.</span></span> <span data-ttu-id="47573-164">在您選取處理序鏈結之後，此元件就會針對選項輸入適當的值。</span><span class="sxs-lookup"><span data-stu-id="47573-164">After you select a process chain, the component enters the appropriate value for the option.</span></span>  
  
 <span data-ttu-id="47573-165">**處理序鏈結**</span><span class="sxs-lookup"><span data-stu-id="47573-165">**Process chain**</span></span>  
 <span data-ttu-id="47573-166">輸入要由來源觸發之處理序鏈結的名稱。</span><span class="sxs-lookup"><span data-stu-id="47573-166">Enter the name of the process chain to be triggered by the source.</span></span>  
  
 <span data-ttu-id="47573-167">**查閱**</span><span class="sxs-lookup"><span data-stu-id="47573-167">**Look up**</span></span>  
 <span data-ttu-id="47573-168">使用 [查閱 ProcessChain]  對話方塊來查閱處理序鏈結。</span><span class="sxs-lookup"><span data-stu-id="47573-168">Look up the process chain by using the **Look Up Process Chain** dialog box.</span></span> <span data-ttu-id="47573-169">如需有關此對話方塊的詳細資訊，請參閱＜ [Look Up Process Chain](look-up-process-chain.md)＞。</span><span class="sxs-lookup"><span data-stu-id="47573-169">For more information about this dialog box, see [Look Up Process Chain](look-up-process-chain.md).</span></span>  
  
### <a name="execution-mode--w---wait-for-notify"></a><span data-ttu-id="47573-170">執行模式 = W - 等候通知</span><span class="sxs-lookup"><span data-stu-id="47573-170">Execution Mode = W - Wait for Notify</span></span>  
  
#### <a name="rfc-destination-options"></a><span data-ttu-id="47573-171">RFC 目的地選項</span><span class="sxs-lookup"><span data-stu-id="47573-171">RFC Destination Options</span></span>  
 <span data-ttu-id="47573-172">您不需要事先了解並輸入這些值。</span><span class="sxs-lookup"><span data-stu-id="47573-172">You do not have to know and enter these values in advance.</span></span> <span data-ttu-id="47573-173">使用 **[查閱]** 按鈕，即可尋找並選取適當的 RFC 目的地。</span><span class="sxs-lookup"><span data-stu-id="47573-173">Use the **Look up** button to find and select the appropriate RFC destination.</span></span> <span data-ttu-id="47573-174">在您選取 RFC 目的地之後，此元件就會針對這些選項輸入適當的值。</span><span class="sxs-lookup"><span data-stu-id="47573-174">After you select an RFC destination, the component enters the appropriate values for the options.</span></span>  
  
 <span data-ttu-id="47573-175">**閘道器主機**</span><span class="sxs-lookup"><span data-stu-id="47573-175">**Gateway host**</span></span>  
 <span data-ttu-id="47573-176">輸入閘道器主機的伺服器名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="47573-176">Enter the server name or IP address of the gateway host.</span></span> <span data-ttu-id="47573-177">此名稱或 IP 位址通常與 SAP 應用程式伺服器相同。</span><span class="sxs-lookup"><span data-stu-id="47573-177">Usually, the name or IP address is the same as the SAP application server.</span></span>  
  
 <span data-ttu-id="47573-178">**閘道器服務**</span><span class="sxs-lookup"><span data-stu-id="47573-178">**Gateway service**</span></span>  
 <span data-ttu-id="47573-179">以 `sapgwNN` 格式輸入閘道服務的名稱，其中 `NN` 是系統編號。</span><span class="sxs-lookup"><span data-stu-id="47573-179">Enter the name of the gateway service, in the format `sapgwNN`, where `NN` is the system number.</span></span>  
  
 <span data-ttu-id="47573-180">**程式識別碼**</span><span class="sxs-lookup"><span data-stu-id="47573-180">**Program ID**</span></span>  
 <span data-ttu-id="47573-181">輸入與 RFC 目的地相關聯的程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="47573-181">Enter the Program ID that is associated with the RFC destination.</span></span>  
  
 <span data-ttu-id="47573-182">**查閱**</span><span class="sxs-lookup"><span data-stu-id="47573-182">**Look up**</span></span>  
 <span data-ttu-id="47573-183">使用 [查閱 RFC 目的地]  對話方塊來查閱 RFC 目的地。</span><span class="sxs-lookup"><span data-stu-id="47573-183">Look up the RFC destination by using the **Look Up RFC Destination** dialog box.</span></span> <span data-ttu-id="47573-184">如需有關此對話方塊的詳細資訊，請參閱＜ [Look Up RFC Destination](look-up-rfc-destination.md)＞。</span><span class="sxs-lookup"><span data-stu-id="47573-184">For more information about this dialog box, see [Look Up RFC Destination](look-up-rfc-destination.md).</span></span>  
  
### <a name="execution-mode--e---extract-only"></a><span data-ttu-id="47573-185">執行模式 = E - 僅限擷取</span><span class="sxs-lookup"><span data-stu-id="47573-185">Execution Mode = E - Extract Only</span></span>  
 <span data-ttu-id="47573-186">**要求識別碼**</span><span class="sxs-lookup"><span data-stu-id="47573-186">**Request ID**</span></span>  
 <span data-ttu-id="47573-187">輸入與擷取相關聯的要求識別碼。</span><span class="sxs-lookup"><span data-stu-id="47573-187">Enter the Request ID that is associated with the extraction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47573-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47573-188">See Also</span></span>  
 <span data-ttu-id="47573-189">[SAP BW 來源編輯器 &#40;資料行頁面&#41;](sap-bw-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="47573-189">[SAP BW Source Editor &#40;Columns Page&#41;](sap-bw-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="47573-190">[SAP BW 來源編輯器 &#40;錯誤輸出頁面&#41;](sap-bw-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="47573-190">[SAP BW Source Editor &#40;Error Output Page&#41;](sap-bw-source-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="47573-191">[SAP BW 來源編輯器 &#40;進階頁面&#41;](sap-bw-source-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="47573-191">[SAP BW Source Editor &#40;Advanced Page&#41;](sap-bw-source-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="47573-192">Microsoft Connector 1.1 for SAP BW F1 說明</span><span class="sxs-lookup"><span data-stu-id="47573-192">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
