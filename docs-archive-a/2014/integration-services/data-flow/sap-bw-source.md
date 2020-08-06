---
title: SAP BW 來源 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 749afb64-3567-4dc9-8431-783d650c25db
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d64af5e0d881e3b7dbbd2cc4e005aa3dbef3c43a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599119"
---
# <a name="sap-bw-source"></a><span data-ttu-id="95d6a-102">SAP BW 來源</span><span class="sxs-lookup"><span data-stu-id="95d6a-102">SAP BW Source</span></span>
  <span data-ttu-id="95d6a-103">SAP BW 來源是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的來源元件。</span><span class="sxs-lookup"><span data-stu-id="95d6a-103">The SAP BW source is the source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span> <span data-ttu-id="95d6a-104">因此，SAP BW 來源會從 SAP Netweaver BW 版本 7 系統中擷取資料，並將這項資料提供給 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件中的資料流程。</span><span class="sxs-lookup"><span data-stu-id="95d6a-104">Thus, the SAP BW source extracts data from an SAP Netweaver BW version 7 system and makes this data available to the data flow in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span>  
  
 <span data-ttu-id="95d6a-105">此來源有一個輸出和一個錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="95d6a-105">This source has one output and one error output.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="95d6a-106">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="95d6a-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="95d6a-107">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="95d6a-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="95d6a-108">擷取 SAP Netweaver BW 中的資料需要額外的 SAP 授權。</span><span class="sxs-lookup"><span data-stu-id="95d6a-108">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="95d6a-109">請洽詢 SAP 以確認這些需求。</span><span class="sxs-lookup"><span data-stu-id="95d6a-109">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="95d6a-110">若要使用 SAP BW 來源，您必須執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="95d6a-110">To use the SAP BW source, you have to do the following tasks:</span></span>  
  
-   [<span data-ttu-id="95d6a-111">準備 SAP Netweaver BW 物件</span><span class="sxs-lookup"><span data-stu-id="95d6a-111">Prepare the SAP Netweaver BW objects</span></span>](#bkmk_Prepare_Objects)  
  
-   [<span data-ttu-id="95d6a-112">連接到 SAP Netweaver BW 系統</span><span class="sxs-lookup"><span data-stu-id="95d6a-112">Connect to the SAP Netweaver BW system</span></span>](#bkmk_Connect_Database)  
  
-   [<span data-ttu-id="95d6a-113">設定 SAP BW 來源</span><span class="sxs-lookup"><span data-stu-id="95d6a-113">Configure the SAP BW source</span></span>](#bkmk_Configure_Source)  
  
##  <a name="preparing-the-sap-netweaver-bw-objects-that-the-source-requires"></a><a name="bkmk_Prepare_Objects"></a> <span data-ttu-id="95d6a-114">準備來源所需的 SAP Netweaver BW 物件</span><span class="sxs-lookup"><span data-stu-id="95d6a-114">Preparing the SAP Netweaver BW Objects That the Source Requires</span></span>  
 <span data-ttu-id="95d6a-115">SAP BW 來源要求特定物件必須存在 SAP Netweaver BW 系統中，然後來源才能運作。</span><span class="sxs-lookup"><span data-stu-id="95d6a-115">The SAP BW source requires that certain objects are in the SAP Netweaver BW system before the source can function.</span></span> <span data-ttu-id="95d6a-116">如果這些物件原本不存在，您就必須遵循下列步驟，在 SAP Netweaver BW 系統中建立並設定這些物件。</span><span class="sxs-lookup"><span data-stu-id="95d6a-116">If these objects do not already exist, you have to follow these steps to create and configure these objects in the SAP Netweaver BW system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95d6a-117">如需有關這些物件和這些組態設定步驟的其他詳細資料，請參閱 SAP Netweaver BW 文件集。</span><span class="sxs-lookup"><span data-stu-id="95d6a-117">For additional details about these objects and these configuration steps, see the SAP Netweaver BW documentation.</span></span>  
  
1.  <span data-ttu-id="95d6a-118">透過 SAP GUI 登入 SAP Netweaver BW、輸入交易代碼 SM59，並且建立 RFC 目的地：</span><span class="sxs-lookup"><span data-stu-id="95d6a-118">Log on to SAP Netweaver BW through the SAP GUI, enter transaction code SM59, and create an RFC destination:</span></span>  
  
    1.  <span data-ttu-id="95d6a-119">針對 [連接類型]  ，選取 [TCP/IP]  。</span><span class="sxs-lookup"><span data-stu-id="95d6a-119">For **Connection Type**, select **TCP/IP**.</span></span>  
  
    2.  <span data-ttu-id="95d6a-120">針對 **[啟動類型]** ，選取 **[已註冊的伺服器程式]** 。</span><span class="sxs-lookup"><span data-stu-id="95d6a-120">For **Activation Type**, select **Registered Server Program**.</span></span>  
  
    3.  <span data-ttu-id="95d6a-121">針對 [目標系統的通訊類型]  ，選取 [非 Unicode (非使用中 MDMP 設定)]  。</span><span class="sxs-lookup"><span data-stu-id="95d6a-121">For **Communication Type with Target System**, select **Non-Unicode (Inactive MDMP Settings)**.</span></span>  
  
    4.  <span data-ttu-id="95d6a-122">指派適當的程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="95d6a-122">Assign an appropriate Program ID.</span></span>  
  
2.  <span data-ttu-id="95d6a-123">建立開放式中心目的地 (Open Hub Destination)：</span><span class="sxs-lookup"><span data-stu-id="95d6a-123">Create an Open Hub Destination:</span></span>  
  
    1.  <span data-ttu-id="95d6a-124">移至 Administrator Workbench (交易代碼 RSA1)，並且在左窗格中，選取 [開放式中心目的地]  。</span><span class="sxs-lookup"><span data-stu-id="95d6a-124">Go to the Administrator Workbench (transaction code RSA1) and, in the left pane, select **Open Hub Destination**.</span></span>  
  
    2.  <span data-ttu-id="95d6a-125">在中間窗格中，以滑鼠右鍵按一下 InfoArea，然後選取 [建立開放式中心目的地]  。</span><span class="sxs-lookup"><span data-stu-id="95d6a-125">In the middle pane, right-click an InfoArea, and then select **"Create Open Hub Destination"**.</span></span>  
  
    3.  <span data-ttu-id="95d6a-126">針對 **[目的地類型]** ，選取 **[協力廠商工具]** ，然後輸入先前建立的 RFC 目的地。</span><span class="sxs-lookup"><span data-stu-id="95d6a-126">For **Destination Type**, select **"Third Party Tool"**, and then enter the previously created RFC Destination.</span></span>  
  
    4.  <span data-ttu-id="95d6a-127">儲存並啟用新的開放式中心目的地。</span><span class="sxs-lookup"><span data-stu-id="95d6a-127">Save and activate the new Open Hub Destination.</span></span>  
  
3.  <span data-ttu-id="95d6a-128">建立資料傳輸處理序 (DTP)：</span><span class="sxs-lookup"><span data-stu-id="95d6a-128">Create a Data Transfer Process (DTP):</span></span>  
  
    1.  <span data-ttu-id="95d6a-129">在 InfoArea 的中間窗格中，以滑鼠右鍵按一下先前建立的目的地，然後選取 [建立資料傳輸處理序]  。</span><span class="sxs-lookup"><span data-stu-id="95d6a-129">In the middle pane of the InfoArea, right-click the previously created destination, and then select **"Create data transfer process"**.</span></span>  
  
    2.  <span data-ttu-id="95d6a-130">設定、儲存並啟用 DTP。</span><span class="sxs-lookup"><span data-stu-id="95d6a-130">Configure, save, and activate the DTP.</span></span>  
  
    3.  <span data-ttu-id="95d6a-131">在功能表上，按一下 **[移至]** ，然後按一下 **[批次管理員的設定]** 。</span><span class="sxs-lookup"><span data-stu-id="95d6a-131">On the menu, click **Goto**, and then click **Settings for Batch Manager**.</span></span>  
  
    4.  <span data-ttu-id="95d6a-132">將 **[處理序數目]** 更新為 1，進行序列處理。</span><span class="sxs-lookup"><span data-stu-id="95d6a-132">Update **Number of processes** to 1 for serial processing.</span></span>  
  
4.  <span data-ttu-id="95d6a-133">建立處理序鏈結：</span><span class="sxs-lookup"><span data-stu-id="95d6a-133">Create a process chain:</span></span>  
  
    1.  <span data-ttu-id="95d6a-134">設定處理序鏈結時，請選取 **[使用中繼資料鏈結或 API 啟動]** 做為 **[啟動處理序]** 的 **[排程選項]** ，然後加入先前建立的 DTP 做為後續節點。</span><span class="sxs-lookup"><span data-stu-id="95d6a-134">When configuring the process chain, select the **Start Using Metadata Chain or API** as the **Scheduling Options** of the **Start Process**, and then add the previously created DTP as the subsequent node.</span></span>  
  
    2.  <span data-ttu-id="95d6a-135">儲存並啟用處理序鏈結。</span><span class="sxs-lookup"><span data-stu-id="95d6a-135">Save and activate the process chain.</span></span>  
  
     <span data-ttu-id="95d6a-136">SAP BW 來源可以呼叫處理序鏈結以啟用資料傳輸處理序。</span><span class="sxs-lookup"><span data-stu-id="95d6a-136">The SAP BW source can call the process chain to activate the data transfer process.</span></span>  
  
##  <a name="connecting-to-the-sap-netweaver-bw-system"></a><a name="bkmk_Connect_Database"></a> <span data-ttu-id="95d6a-137">連接到 SAP Netweaver BW 系統</span><span class="sxs-lookup"><span data-stu-id="95d6a-137">Connecting to the SAP Netweaver BW System</span></span>  
 <span data-ttu-id="95d6a-138">為了連接到 SAP Netweaver BW 版本 7 系統，SAP BW 來源會使用屬於 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 封裝一部分的 SAP BW 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="95d6a-138">To connect to the SAP Netweaver BW version 7 system, the SAP BW source uses the SAP BW connection manager that is part of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW package.</span></span> <span data-ttu-id="95d6a-139">SAP BW 連接管理員是 SAP BW 來源可以使用的唯一 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="95d6a-139">The SAP BW connection manager is the only [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] connection manager that the SAP BW source can use.</span></span>  
  
 <span data-ttu-id="95d6a-140">如需有關 SAP BW 連接管理員的詳細資訊，請參閱＜ [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md)＞。</span><span class="sxs-lookup"><span data-stu-id="95d6a-140">For more information about the SAP BW connection manager, see [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md).</span></span>  
  
##  <a name="configuring-the-sap-bw-source"></a><a name="bkmk_Configure_Source"></a> <span data-ttu-id="95d6a-141">設定 SAP BW 來源</span><span class="sxs-lookup"><span data-stu-id="95d6a-141">Configuring the SAP BW Source</span></span>  
 <span data-ttu-id="95d6a-142">您可以利用下列方式設定 SAP BW 來源：</span><span class="sxs-lookup"><span data-stu-id="95d6a-142">You can configure the SAP BW source in the following ways:</span></span>  
  
-   <span data-ttu-id="95d6a-143">查閱並選取要用來擷取資料的開放式中心服務 (Open Hub Service，OHS) 目的地。</span><span class="sxs-lookup"><span data-stu-id="95d6a-143">Look up and select the Open Hub Service (OHS) destination to use to extract data.</span></span>  
  
-   <span data-ttu-id="95d6a-144">選取下列其中一種方法來擷取資料：</span><span class="sxs-lookup"><span data-stu-id="95d6a-144">Select one of the following methods for extracting data:</span></span>  
  
    -   <span data-ttu-id="95d6a-145">觸發處理序鏈結。</span><span class="sxs-lookup"><span data-stu-id="95d6a-145">Trigger a process chain.</span></span> <span data-ttu-id="95d6a-146">在此情況下， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝會啟動擷取處理序。</span><span class="sxs-lookup"><span data-stu-id="95d6a-146">In this case, the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package starts the extraction process.</span></span>  
  
    -   <span data-ttu-id="95d6a-147">等候來自 SAP Netweaver BW 系統的通知，以便開始擷取。</span><span class="sxs-lookup"><span data-stu-id="95d6a-147">Wait for notification from the SAP Netweaver BW system to begin an extraction.</span></span> <span data-ttu-id="95d6a-148">在此情況下，SAP Netweaver BW 系統會啟動擷取處理序。</span><span class="sxs-lookup"><span data-stu-id="95d6a-148">In this case, the SAP Netweaver BW system starts the extraction process.</span></span>  
  
    -   <span data-ttu-id="95d6a-149">擷取與特定要求識別碼相關聯的資料。</span><span class="sxs-lookup"><span data-stu-id="95d6a-149">Retrieve the data that is associated with a particular Request ID.</span></span> <span data-ttu-id="95d6a-150">在此情況下，SAP Netweaver BW 系統已經將資料擷取到內部資料表，而且 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝剛剛讀取資料。</span><span class="sxs-lookup"><span data-stu-id="95d6a-150">In this case, the SAP Netweaver BW system has already extracted the data to an internal table, and the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package just reads the data.</span></span>  
  
-   <span data-ttu-id="95d6a-151">根據選取的資料擷取方法，提供下列其他資訊：</span><span class="sxs-lookup"><span data-stu-id="95d6a-151">Depending on the method selected for extracting data, provide the following additional information:</span></span>  
  
    -   <span data-ttu-id="95d6a-152">針對 [P - 觸發處理鏈結]  選項，提供閘道器主機名稱、閘道器服務名稱、RFC 目的地的程式識別碼，以及處理序鏈結的名稱。</span><span class="sxs-lookup"><span data-stu-id="95d6a-152">For the **P - Trigger Process Chain** option, provide the gateway host name, gateway service name, program ID for the RFC destination, and name of the process chain.</span></span>  
  
    -   <span data-ttu-id="95d6a-153">針對 [W - 等候通知]  選項，提供閘道器主機名稱、閘道器伺服器名稱，以及 RFC 目的地的程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="95d6a-153">For the **W - Wait for Notify** option, provide the gateway host name, the gateway server name, and the program ID for the RFC destination.</span></span> <span data-ttu-id="95d6a-154">您也可以指定逾時 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="95d6a-154">You can also specify the timeout (in seconds).</span></span> <span data-ttu-id="95d6a-155">逾時就是來源將等候收到通知的最大期限。</span><span class="sxs-lookup"><span data-stu-id="95d6a-155">The timeout is the maximum period of time that the source will wait to be notified.</span></span>  
  
    -   <span data-ttu-id="95d6a-156">針對 [E - 僅限擷取]  選項，提供要求識別碼。</span><span class="sxs-lookup"><span data-stu-id="95d6a-156">For the **E - Extract Only** option, provide the Request ID.</span></span>  
  
-   <span data-ttu-id="95d6a-157">指定字串轉換的規則</span><span class="sxs-lookup"><span data-stu-id="95d6a-157">Specify rules for string conversion.</span></span> <span data-ttu-id="95d6a-158">(例如，根據 SAP Netweaver BW 系統是否為 Unicode 而轉換所有字串，或將所有字串轉換為 `varchar` 或 `nvarchar`)。</span><span class="sxs-lookup"><span data-stu-id="95d6a-158">(For example, convert all strings depending on whether the SAP Netweaver BW system is Unicode or not, or convert all strings to `varchar` or `nvarchar`).</span></span>  
  
-   <span data-ttu-id="95d6a-159">使用您已選取的選項來預覽要擷取的資料。</span><span class="sxs-lookup"><span data-stu-id="95d6a-159">Use the options that you have selected to preview the data to be extracted.</span></span>  
  
 <span data-ttu-id="95d6a-160">您也可以針對來源的 RFC 函數呼叫啟用記錄</span><span class="sxs-lookup"><span data-stu-id="95d6a-160">You can also enable logging of RFC function calls by the source.</span></span> <span data-ttu-id="95d6a-161">(這項記錄與您針對 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝啟用的選擇性記錄是分開的)。您可以在設定來源將使用的 SAP BW 連接管理員時啟用 RFC 函數呼叫的記錄。</span><span class="sxs-lookup"><span data-stu-id="95d6a-161">(This logging is separate from the optional logging that you can enable on [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.) You enable logging of RFC function calls when you configure the SAP BW connection manager that the source will use.</span></span> <span data-ttu-id="95d6a-162">如需有關如何設定 SAP BW 連接管理員的詳細資訊，請參閱＜ [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md)＞。</span><span class="sxs-lookup"><span data-stu-id="95d6a-162">For more information about how to configure the SAP BW connection manager, see [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md).</span></span>  
  
 <span data-ttu-id="95d6a-163">如果您不知道設定來源的所有必要值，可能必須詢問 SAP 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="95d6a-163">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="95d6a-164">如需示範如何設定及使用 SAP BW 連接管理員、來源和目的地的逐步解說，請參閱＜ [搭配 SAP BI 7.0 使用 SQL Server 2008 Integration Services](https://go.microsoft.com/fwlink/?LinkID=137090)＞技術白皮書。</span><span class="sxs-lookup"><span data-stu-id="95d6a-164">For a walkthrough that demonstrates how to configure and use the SAP BW connection manager, source, and destination, see the white paper, [Using SQL Server 2008 Integration Services with SAP BI 7.0](https://go.microsoft.com/fwlink/?LinkID=137090).</span></span> <span data-ttu-id="95d6a-165">這份技術白皮書也會示範如何設定 SAP BW 中的必要物件。</span><span class="sxs-lookup"><span data-stu-id="95d6a-165">This white paper also shows how to configure the required objects in SAP BW.</span></span>  
  
### <a name="using-the-ssis-designer-to-configure-the-source"></a><span data-ttu-id="95d6a-166">使用 SSIS 設計師設定來源</span><span class="sxs-lookup"><span data-stu-id="95d6a-166">Using the SSIS Designer to Configure the Source</span></span>  
 <span data-ttu-id="95d6a-167">如需有關可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中設定之 SAP BW 來源屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="95d6a-167">For more information about the properties of the SAP BW source that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="95d6a-168">SAP BW 來源編輯器 &#40;連線管理員頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="95d6a-168">SAP BW Source Editor &#40;Connection Manager Page&#41;</span></span>](sap-bw-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="95d6a-169">SAP BW 來源編輯器 &#40;資料行頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="95d6a-169">SAP BW Source Editor &#40;Columns Page&#41;</span></span>](sap-bw-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="95d6a-170">SAP BW 來源編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="95d6a-170">SAP BW Source Editor &#40;Error Output Page&#41;</span></span>](sap-bw-source-editor-error-output-page.md)  
  
-   [<span data-ttu-id="95d6a-171">SAP BW 來源編輯器 &#40;進階頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="95d6a-171">SAP BW Source Editor &#40;Advanced Page&#41;</span></span>](sap-bw-source-editor-advanced-page.md)  
  
 <span data-ttu-id="95d6a-172">設定 SAP BW 來源時，您也可以使用各種對話方塊來查閱 SAP Netweaver BW 物件或預覽來源資料。</span><span class="sxs-lookup"><span data-stu-id="95d6a-172">While you are configuring the SAP BW source, you can also use various dialog boxes to look up SAP Netweaver BW objects or to preview the source data.</span></span> <span data-ttu-id="95d6a-173">如需有關這些對話方塊的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="95d6a-173">For more information about these dialog boxes, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="95d6a-174">查閱 RFC 目的地</span><span class="sxs-lookup"><span data-stu-id="95d6a-174">Look Up RFC Destination</span></span>](look-up-rfc-destination.md)  
  
-   [<span data-ttu-id="95d6a-175">查閱 ProcessChain</span><span class="sxs-lookup"><span data-stu-id="95d6a-175">Look Up Process Chain</span></span>](look-up-process-chain.md)  
  
-   [<span data-ttu-id="95d6a-176">要求記錄檔</span><span class="sxs-lookup"><span data-stu-id="95d6a-176">Request Log</span></span>](request-log.md)  
  
-   [<span data-ttu-id="95d6a-177">預覽</span><span class="sxs-lookup"><span data-stu-id="95d6a-177">Preview</span></span>](preview.md)  
  
## <a name="see-also"></a><span data-ttu-id="95d6a-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95d6a-178">See Also</span></span>  
 [<span data-ttu-id="95d6a-179">Microsoft Connector 1.1 for SAP BW 元件</span><span class="sxs-lookup"><span data-stu-id="95d6a-179">Microsoft Connector 1.1 for SAP BW Components</span></span>](../microsoft-connector-for-sap-bw-components.md)  
  
  
