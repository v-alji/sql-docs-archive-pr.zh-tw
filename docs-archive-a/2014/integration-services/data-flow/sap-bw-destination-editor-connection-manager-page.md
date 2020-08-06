---
title: SAP BW 目的地編輯器 (連線管理員頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 04ae38f8-5287-45a3-826a-8aac5dd15a91
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0dd628f1a0fec09490e0d3720610d1232882ed92
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687081"
---
# <a name="sap-bw-destination-editor-connection-manager-page"></a><span data-ttu-id="7278d-102">SAP BW 目的地編輯器 (連接管理員頁面)</span><span class="sxs-lookup"><span data-stu-id="7278d-102">SAP BW Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="7278d-103">使用 **[SAP BW 目的地編輯器]** 的 **[連接管理員]** 頁面可以選取 SAP BW 目的地將使用的 SAP BW 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="7278d-103">Use the **Connection Manager** page of the **SAP BW Destination Editor** to select the SAP BW connection manager that the SAP BW destination will use.</span></span> <span data-ttu-id="7278d-104">在這個頁面上，您也可以選取將資料載入 SAP Netweaver BW 系統中所用的參數。</span><span class="sxs-lookup"><span data-stu-id="7278d-104">On this page, you also select the parameters for loading the data into the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="7278d-105">若要深入了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 目的地，請參閱 [SAP BW 目的地](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="7278d-105">To learn more about the SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7278d-106">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="7278d-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="7278d-107">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="7278d-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="7278d-108">**開啟連接管理員頁面**</span><span class="sxs-lookup"><span data-stu-id="7278d-108">**To open the Connection Manager page**</span></span>  
  
1.  <span data-ttu-id="7278d-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含 SAP BW 目的地的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件。</span><span class="sxs-lookup"><span data-stu-id="7278d-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="7278d-110">在 [資料流程]  索引標籤上，按兩下 SAP BW 目的地。</span><span class="sxs-lookup"><span data-stu-id="7278d-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="7278d-111">在 **[SAP BW 目的地編輯器]** 中，按一下 **[連接管理員]** 開啟編輯器的 **[連接管理員]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="7278d-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7278d-112">選項。</span><span class="sxs-lookup"><span data-stu-id="7278d-112">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7278d-113">如果您不知道設定目的地的所有必要值，可能必須詢問 SAP 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="7278d-113">If you do not know all the values that are required to configure the destination, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="7278d-114">**SAP BW 連接管理員**</span><span class="sxs-lookup"><span data-stu-id="7278d-114">**SAP BW connection manager**</span></span>  
 <span data-ttu-id="7278d-115">從清單中選取現有的連線管理員，或按一下 [新增]  來建立新的連線。</span><span class="sxs-lookup"><span data-stu-id="7278d-115">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="7278d-116">**新增**</span><span class="sxs-lookup"><span data-stu-id="7278d-116">**New**</span></span>  
 <span data-ttu-id="7278d-117">使用 [SAP BW 連線管理員]  對話方塊來建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="7278d-117">Create a new connection manager by using the **SAP BW Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="7278d-118">**測試負載**</span><span class="sxs-lookup"><span data-stu-id="7278d-118">**Test Load**</span></span>  
 <span data-ttu-id="7278d-119">執行載入程序的測試，這項測試會使用您已選取的設定，但是不會載入任何資料列。</span><span class="sxs-lookup"><span data-stu-id="7278d-119">Perform a test of the loading process that uses the settings that you have selected and loads zero rows.</span></span>  
  
### <a name="infopackageinfosource-options"></a><span data-ttu-id="7278d-120">InfoPackage/InfoSource 選項</span><span class="sxs-lookup"><span data-stu-id="7278d-120">InfoPackage/InfoSource Options</span></span>  
 <span data-ttu-id="7278d-121">您不需要事先了解並輸入這些值。</span><span class="sxs-lookup"><span data-stu-id="7278d-121">You do not have to know and enter these values in advance.</span></span> <span data-ttu-id="7278d-122">使用 **[查閱]** 按鈕，即可尋找並選取適當的 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="7278d-122">Use the **Look up** button to find and select the appropriate InfoPackage.</span></span> <span data-ttu-id="7278d-123">在您選取 InfoPackage 之後，此元件就會針對這些選項輸入適當的值。</span><span class="sxs-lookup"><span data-stu-id="7278d-123">After you select an InfoPackage, the component enters the appropriate values for these options.</span></span>  
  
 <span data-ttu-id="7278d-124">**InfoPackage**</span><span class="sxs-lookup"><span data-stu-id="7278d-124">**InfoPackage**</span></span>  
 <span data-ttu-id="7278d-125">輸入 InfoPackage 的名稱。</span><span class="sxs-lookup"><span data-stu-id="7278d-125">Enter the name of the InfoPackage.</span></span>  
  
 <span data-ttu-id="7278d-126">**InfoSource**</span><span class="sxs-lookup"><span data-stu-id="7278d-126">**InfoSource**</span></span>  
 <span data-ttu-id="7278d-127">輸入 InfoSource 的名稱。</span><span class="sxs-lookup"><span data-stu-id="7278d-127">Enter the name of the InfoSource.</span></span>  
  
 <span data-ttu-id="7278d-128">**型別**</span><span class="sxs-lookup"><span data-stu-id="7278d-128">**Type**</span></span>  
 <span data-ttu-id="7278d-129">輸入可識別 InfoSource 類型的單一字元。</span><span class="sxs-lookup"><span data-stu-id="7278d-129">Enter the single-character that identifies the type of the InfoSource.</span></span> <span data-ttu-id="7278d-130">下表列出可接受的單一字元值。</span><span class="sxs-lookup"><span data-stu-id="7278d-130">The following table lists the acceptable single-character values.</span></span>  
  
|<span data-ttu-id="7278d-131">值</span><span class="sxs-lookup"><span data-stu-id="7278d-131">Value</span></span>|<span data-ttu-id="7278d-132">描述</span><span class="sxs-lookup"><span data-stu-id="7278d-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7278d-133">**D**</span><span class="sxs-lookup"><span data-stu-id="7278d-133">**D**</span></span>|<span data-ttu-id="7278d-134">交易資料</span><span class="sxs-lookup"><span data-stu-id="7278d-134">Transaction data</span></span>|  
|<span data-ttu-id="7278d-135">**M**</span><span class="sxs-lookup"><span data-stu-id="7278d-135">**M**</span></span>|<span data-ttu-id="7278d-136">主要資料</span><span class="sxs-lookup"><span data-stu-id="7278d-136">Master data</span></span>|  
|<span data-ttu-id="7278d-137">**T**</span><span class="sxs-lookup"><span data-stu-id="7278d-137">**T**</span></span>|<span data-ttu-id="7278d-138">文字</span><span class="sxs-lookup"><span data-stu-id="7278d-138">Texts</span></span>|  
|<span data-ttu-id="7278d-139">**H**</span><span class="sxs-lookup"><span data-stu-id="7278d-139">**H**</span></span>|<span data-ttu-id="7278d-140">階層資料</span><span class="sxs-lookup"><span data-stu-id="7278d-140">Hierarchy data</span></span>|  
  
 <span data-ttu-id="7278d-141">**邏輯系統**</span><span class="sxs-lookup"><span data-stu-id="7278d-141">**Logical system**</span></span>  
 <span data-ttu-id="7278d-142">輸入與 InfoPackage 相關聯之邏輯系統的名稱。</span><span class="sxs-lookup"><span data-stu-id="7278d-142">Enter the name of the logical system that is associated with the InfoPackage.</span></span>  
  
 <span data-ttu-id="7278d-143">**查閱**</span><span class="sxs-lookup"><span data-stu-id="7278d-143">**Look up**</span></span>  
 <span data-ttu-id="7278d-144">使用 [查閱 InfoPackage]  對話方塊來查閱 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="7278d-144">Look up the InfoPackage by using the **Look Up InfoPackage** dialog box.</span></span> <span data-ttu-id="7278d-145">如需有關此對話方塊的詳細資訊，請參閱＜ [Look Up InfoPackage](look-up-infopackage.md)＞。</span><span class="sxs-lookup"><span data-stu-id="7278d-145">For more information about this dialog box, see [Look Up InfoPackage](look-up-infopackage.md).</span></span>  
  
### <a name="rfc-destination-options"></a><span data-ttu-id="7278d-146">RFC 目的地選項</span><span class="sxs-lookup"><span data-stu-id="7278d-146">RFC Destination Options</span></span>  
 <span data-ttu-id="7278d-147">您不需要事先了解並輸入這些值。</span><span class="sxs-lookup"><span data-stu-id="7278d-147">You do not have to know and enter these values in advance.</span></span> <span data-ttu-id="7278d-148">使用 **[查閱]** 按鈕，即可尋找並選取適當的 RFC 目的地。</span><span class="sxs-lookup"><span data-stu-id="7278d-148">Use the **Look up** button to find and select the appropriate RFC destination.</span></span> <span data-ttu-id="7278d-149">在您選取 RFC 目的地之後，此元件就會針對這些選項輸入適當的值。</span><span class="sxs-lookup"><span data-stu-id="7278d-149">After you select an RFC destination, the component enters the appropriate values for these options.</span></span>  
  
 <span data-ttu-id="7278d-150">**閘道器主機**</span><span class="sxs-lookup"><span data-stu-id="7278d-150">**Gateway host**</span></span>  
 <span data-ttu-id="7278d-151">輸入閘道器主機的伺服器名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="7278d-151">Enter the server name or IP address of the gateway host.</span></span> <span data-ttu-id="7278d-152">此名稱或 IP 位址通常與 SAP 應用程式伺服器相同。</span><span class="sxs-lookup"><span data-stu-id="7278d-152">Usually, the name or IP address is the same as the SAP application server.</span></span>  
  
 <span data-ttu-id="7278d-153">**閘道器服務**</span><span class="sxs-lookup"><span data-stu-id="7278d-153">**Gateway service**</span></span>  
 <span data-ttu-id="7278d-154">以 `sapgwNN` 格式輸入閘道服務的名稱，其中 `NN` 是系統編號。</span><span class="sxs-lookup"><span data-stu-id="7278d-154">Enter the name of the gateway service, in the format `sapgwNN`, where `NN` is the system number.</span></span>  
  
 <span data-ttu-id="7278d-155">**程式識別碼**</span><span class="sxs-lookup"><span data-stu-id="7278d-155">**Program ID**</span></span>  
 <span data-ttu-id="7278d-156">輸入與 RFC 目的地相關聯的程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="7278d-156">Enter the Program ID that is associated with the RFC destination.</span></span>  
  
 <span data-ttu-id="7278d-157">**查閱**</span><span class="sxs-lookup"><span data-stu-id="7278d-157">**Look up**</span></span>  
 <span data-ttu-id="7278d-158">使用 [查閱 RFC 目的地]  對話方塊來查閱 RFC 目的地。</span><span class="sxs-lookup"><span data-stu-id="7278d-158">Look up the RFC destination by using the **Look Up RFC Destination** dialog box.</span></span> <span data-ttu-id="7278d-159">如需有關此對話方塊的詳細資訊，請參閱＜ [Look Up RFC Destination](look-up-rfc-destination.md)＞。</span><span class="sxs-lookup"><span data-stu-id="7278d-159">For more information about this dialog box, see [Look Up RFC Destination](look-up-rfc-destination.md).</span></span>  
  
### <a name="create-sap-bw-objects-options"></a><span data-ttu-id="7278d-160">建立 SAP BW 物件選項</span><span class="sxs-lookup"><span data-stu-id="7278d-160">Create SAP BW Objects Options</span></span>  
 <span data-ttu-id="7278d-161">**選取 物件類型**</span><span class="sxs-lookup"><span data-stu-id="7278d-161">**Select object type**</span></span>  
 <span data-ttu-id="7278d-162">選取您想要建立的 SAP Netweaver BW 物件類型。</span><span class="sxs-lookup"><span data-stu-id="7278d-162">Select the type of SAP Netweaver BW object that you want to create.</span></span> <span data-ttu-id="7278d-163">您可以選取下列其中一種類型：</span><span class="sxs-lookup"><span data-stu-id="7278d-163">You can select one of the following types:</span></span>  
  
-   <span data-ttu-id="7278d-164">[InfoObject]</span><span class="sxs-lookup"><span data-stu-id="7278d-164">InfoObject</span></span>  
  
-   <span data-ttu-id="7278d-165">InfoCube</span><span class="sxs-lookup"><span data-stu-id="7278d-165">InfoCube</span></span>  
  
-   <span data-ttu-id="7278d-166">InfoSource</span><span class="sxs-lookup"><span data-stu-id="7278d-166">InfoSource</span></span>  
  
-   <span data-ttu-id="7278d-167">InfoPackage</span><span class="sxs-lookup"><span data-stu-id="7278d-167">InfoPackage</span></span>  
  
 <span data-ttu-id="7278d-168">**建立**</span><span class="sxs-lookup"><span data-stu-id="7278d-168">**Create**</span></span>  
 <span data-ttu-id="7278d-169">建立選取的 SAP Netweaver BW 物件類型。</span><span class="sxs-lookup"><span data-stu-id="7278d-169">Create the selected type of SAP Netweaver BW object.</span></span>  
  
|<span data-ttu-id="7278d-170">物件類型</span><span class="sxs-lookup"><span data-stu-id="7278d-170">Object Type</span></span>|<span data-ttu-id="7278d-171">結果</span><span class="sxs-lookup"><span data-stu-id="7278d-171">Result</span></span>|  
|-----------------|------------|  
|<span data-ttu-id="7278d-172">**InfoObject**</span><span class="sxs-lookup"><span data-stu-id="7278d-172">**InfoObject**</span></span>|<span data-ttu-id="7278d-173">使用 **[建立新的 InfoObject]** 對話方塊來建立新的 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="7278d-173">Create a new InfoObject by using the **Create New InfoObject** dialog box.</span></span> <span data-ttu-id="7278d-174">如需有關此對話方塊的詳細資訊，請參閱＜ [Create New InfoObject](create-new-infoobject.md)＞。</span><span class="sxs-lookup"><span data-stu-id="7278d-174">For more information about this dialog box, see [Create New InfoObject](create-new-infoobject.md).</span></span>|  
|<span data-ttu-id="7278d-175">**InfoCube**</span><span class="sxs-lookup"><span data-stu-id="7278d-175">**InfoCube**</span></span>|<span data-ttu-id="7278d-176">使用 **[建立交易資料的 InfoCube]** 對話方塊來建立新的 InfoCube。</span><span class="sxs-lookup"><span data-stu-id="7278d-176">Create a new InfoCube by using the **Create InfoCube for Transaction Data** dialog box.</span></span> <span data-ttu-id="7278d-177">如需有關此對話方塊的詳細資訊，請參閱＜ [Create InfoCube for Transaction Data](create-infocube-for-transaction-data.md)＞。</span><span class="sxs-lookup"><span data-stu-id="7278d-177">For more information about this dialog box, see [Create InfoCube for Transaction Data](create-infocube-for-transaction-data.md).</span></span>|  
|<span data-ttu-id="7278d-178">**InfoSource**</span><span class="sxs-lookup"><span data-stu-id="7278d-178">**InfoSource**</span></span>|<span data-ttu-id="7278d-179">使用 **[建立 InfoSource]** 對話方塊，然後使用 **[建立交易資料的 InfoSource]** 或 **[建立主要資料的 InfoSource]** 對話方塊來建立新的 InfoSource。</span><span class="sxs-lookup"><span data-stu-id="7278d-179">Create a new InfoSource by using the **Create InfoSource** dialog box, and then by using the **Create InfoSource for Transaction Data** or the **Create InfoSource for Master Data** dialog box.</span></span> <span data-ttu-id="7278d-180">如需有關這些對話方塊的詳細資訊，請參閱＜ [Create InfoSource](create-infosource.md)＞、＜ [Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md) ＞和＜ [Create InfoSource for Master Data](create-infosource-for-master-data.md)＞。</span><span class="sxs-lookup"><span data-stu-id="7278d-180">For more information about these dialog boxes, see [Create InfoSource](create-infosource.md), [Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md) and [Create InfoSource for Master Data](create-infosource-for-master-data.md).</span></span>|  
|<span data-ttu-id="7278d-181">**InfoPackage**</span><span class="sxs-lookup"><span data-stu-id="7278d-181">**InfoPackage**</span></span>|<span data-ttu-id="7278d-182">使用 **[建立 InfoPackage]** 對話方塊來建立新的 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="7278d-182">Create a new InfoPackage by using the **Create InfoPackage** dialog box.</span></span> <span data-ttu-id="7278d-183">如需有關此對話方塊的詳細資訊，請參閱＜ [Create InfoPackage](create-infopackage.md)＞。</span><span class="sxs-lookup"><span data-stu-id="7278d-183">For more information about this dialog box, see [Create InfoPackage](create-infopackage.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7278d-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7278d-184">See Also</span></span>  
 <span data-ttu-id="7278d-185">[SAP BW 目的地編輯器 &#40;對應頁面&#41;](sap-bw-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="7278d-185">[SAP BW Destination Editor &#40;Mappings Page&#41;](sap-bw-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="7278d-186">[SAP BW 目的地編輯器 &#40;錯誤輸出頁面&#41;](sap-bw-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="7278d-186">[SAP BW Destination Editor &#40;Error Output Page&#41;](sap-bw-destination-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="7278d-187">[SAP BW 目的地編輯器 &#40;進階頁面&#41;](sap-bw-destination-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="7278d-187">[SAP BW Destination Editor &#40;Advanced Page&#41;](sap-bw-destination-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="7278d-188">Microsoft Connector 1.1 for SAP BW F1 說明</span><span class="sxs-lookup"><span data-stu-id="7278d-188">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
