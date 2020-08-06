---
title: SAP BW 目的地 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a612ed91-b89b-4173-a0b1-0bce381e1e28
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8a0d7c5b75da89e665dbe60bbd7e29ce74da67db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597982"
---
# <a name="sap-bw-destination"></a><span data-ttu-id="c789f-102">SAP BW 目的地</span><span class="sxs-lookup"><span data-stu-id="c789f-102">SAP BW Destination</span></span>
  <span data-ttu-id="c789f-103">SAP BW 目的地是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的目的地元件。</span><span class="sxs-lookup"><span data-stu-id="c789f-103">The SAP BW destination is the destination component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span> <span data-ttu-id="c789f-104">因此，SAP BW 目的地會將 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝中資料流程的資料載入 SAP Netweaver BW 版本 7 系統中。</span><span class="sxs-lookup"><span data-stu-id="c789f-104">Thus, the SAP BW destination loads data from the data flow in an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package into an SAP Netweaver BW version 7 system.</span></span>  
  
 <span data-ttu-id="c789f-105">這個目的地具有一個輸入和一個錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="c789f-105">This destination has one input and one error output.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c789f-106">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="c789f-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="c789f-107">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="c789f-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="c789f-108">若要使用 SAP BW 目的地，您必須執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="c789f-108">To use the SAP BW destination, you have to do the following tasks:</span></span>  
  
-   [<span data-ttu-id="c789f-109">準備 SAP Netweaver BW 物件</span><span class="sxs-lookup"><span data-stu-id="c789f-109">Prepare the SAP Netweaver BW objects</span></span>](#bkmk_Prepare_Objects)  
  
-   [<span data-ttu-id="c789f-110">連接到 SAP Netweaver BW 系統</span><span class="sxs-lookup"><span data-stu-id="c789f-110">Connect to the SAP Netweaver BW system</span></span>](#bkmk_Connect_Database)  
  
-   [<span data-ttu-id="c789f-111">設定 SAP BW 目的地</span><span class="sxs-lookup"><span data-stu-id="c789f-111">Configure the SAP BW destination</span></span>](#bkmk_Configure_Destination)  
  
##  <a name="preparing-the-sap-netweaver-bw-objects-that-the-destination-requires"></a><a name="bkmk_Prepare_Objects"></a> <span data-ttu-id="c789f-112">準備目的地所需的 SAP Netweaver BW 物件</span><span class="sxs-lookup"><span data-stu-id="c789f-112">Preparing the SAP Netweaver BW Objects That the Destination Requires</span></span>  
 <span data-ttu-id="c789f-113">SAP BW 目的地要求特定物件必須存在 SAP Netweaver BW 系統中，然後目的地才能運作。</span><span class="sxs-lookup"><span data-stu-id="c789f-113">The SAP BW destination requires that certain objects are in the SAP Netweaver BW system before the destination can function.</span></span> <span data-ttu-id="c789f-114">如果這些物件原本不存在，您就必須遵循下列步驟，在 SAP Netweaver BW 系統中建立並設定這些物件。</span><span class="sxs-lookup"><span data-stu-id="c789f-114">If these objects do not already exist, you have to follow these steps to create and configure these objects in the SAP Netweaver BW system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c789f-115">如需有關這些物件和這些組態設定步驟的其他詳細資料，請參閱 SAP Netweaver BW 文件集。</span><span class="sxs-lookup"><span data-stu-id="c789f-115">For additional details about these objects and these configuration steps, see the SAP Netweaver BW documentation.</span></span>  
  
1.  <span data-ttu-id="c789f-116">建立新的來源系統：</span><span class="sxs-lookup"><span data-stu-id="c789f-116">Create a new Source System:</span></span>  
  
    1.  <span data-ttu-id="c789f-117">選取 [協力廠商/暫存 BAPI]  類型。</span><span class="sxs-lookup"><span data-stu-id="c789f-117">Select the type, **"Third Party/Staging BAPIs"**.</span></span>  
  
    2.  <span data-ttu-id="c789f-118">針對 [目標系統的通訊類型]  ，選取 [非 Unicode (非使用中 MDMP 設定)]  。</span><span class="sxs-lookup"><span data-stu-id="c789f-118">For **Communication Type with Target System**, select **Non-Unicode (Inactive MDMP Settings)**.</span></span>  
  
    3.  <span data-ttu-id="c789f-119">指派適當的程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="c789f-119">Assign an appropriate Program ID.</span></span>  
  
2.  <span data-ttu-id="c789f-120">將來源系統指派給 InfoSource。</span><span class="sxs-lookup"><span data-stu-id="c789f-120">Assign the Source System to an InfoSource.</span></span>  
  
3.  <span data-ttu-id="c789f-121">建立 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="c789f-121">Create an InfoPackage.</span></span>  
  
     <span data-ttu-id="c789f-122">InfoPackage 是 SAP BW 目的地所需的最重要物件。</span><span class="sxs-lookup"><span data-stu-id="c789f-122">The InfoPackage is the most important object that is required by the SAP BW destination.</span></span>  
  
 <span data-ttu-id="c789f-123">您也可以建立其他支援將資料載入 SAP Netweaver BW 系統所需的 InfoObject、InfoCube、InfoSource 和 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="c789f-123">You can also create additional InfoObjects, InfoCubes, InfoSources, and InfoPackages that are required to support loading data into the SAP Netweaver BW system.</span></span>  
  
##  <a name="connecting-to-the-sap-netweaver-bw-system"></a><a name="bkmk_Connect_Database"></a> <span data-ttu-id="c789f-124">連接到 SAP Netweaver BW 系統</span><span class="sxs-lookup"><span data-stu-id="c789f-124">Connecting to the SAP Netweaver BW System</span></span>  
 <span data-ttu-id="c789f-125">為了連接到 SAP Netweaver BW 版本 7 系統，SAP BW 目的地會使用屬於 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 封裝一部分的 SAP BW 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="c789f-125">To connect to the SAP Netweaver BW version 7 system, the SAP BW destination uses the SAP BW connection manager that is part of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW package.</span></span> <span data-ttu-id="c789f-126">SAP BW 連接管理員是 SAP BW 目的地可以使用的唯一 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="c789f-126">The SAP BW connection manager is the only [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] connection manager that the SAP BW destination can use.</span></span>  
  
 <span data-ttu-id="c789f-127">如需有關 SAP BW 連接管理員的詳細資訊，請參閱＜ [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md)＞。</span><span class="sxs-lookup"><span data-stu-id="c789f-127">For more information about the SAP BW connection manager, see [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md).</span></span>  
  
##  <a name="configuring-the-sap-bw-destination"></a><a name="bkmk_Configure_Destination"></a> <span data-ttu-id="c789f-128">設定 SAP BW 目的地</span><span class="sxs-lookup"><span data-stu-id="c789f-128">Configuring the SAP BW Destination</span></span>  
 <span data-ttu-id="c789f-129">您可以利用下列方式設定 SAP BW 目的地：</span><span class="sxs-lookup"><span data-stu-id="c789f-129">You can configure the SAP BW destination in the following ways:</span></span>  
  
-   <span data-ttu-id="c789f-130">查閱並選取要用來載入資料的 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="c789f-130">Look up and select the InfoPackage to use to load data.</span></span>  
  
-   <span data-ttu-id="c789f-131">將資料流程中的每個資料行對應至 InfoPackage 中的適當 InfoObject。</span><span class="sxs-lookup"><span data-stu-id="c789f-131">Map each column in the data flow to the appropriate InfoObject in the InfoPackage.</span></span>  
  
-   <span data-ttu-id="c789f-132">透過設定 `PackageSize` 屬性，指定一次會傳輸多少個資料列。</span><span class="sxs-lookup"><span data-stu-id="c789f-132">Specify how many rows of data will be transferred at a time by configuring the `PackageSize` property.</span></span>  
  
-   <span data-ttu-id="c789f-133">選擇要等候直到 SAP Netweaver BW 系統完成資料載入為止。</span><span class="sxs-lookup"><span data-stu-id="c789f-133">Choose to wait until the loading of data is completed by the SAP Netweaver BW system.</span></span>  
  
-   <span data-ttu-id="c789f-134">選擇不要觸發 InfoPackage，而是等候 SAP Netweaver BW 系統已開始載入資料的通知。</span><span class="sxs-lookup"><span data-stu-id="c789f-134">Choose not to trigger the InfoPackage, but to wait for notification that the SAP Netweaver BW system has started the loading of data.</span></span>  
  
-   <span data-ttu-id="c789f-135">(選擇性) 在資料載入完成之後觸發另一個處理序鏈結。</span><span class="sxs-lookup"><span data-stu-id="c789f-135">Optionally, trigger another process chain after the loading of data is completed.</span></span>  
  
-   <span data-ttu-id="c789f-136">(選擇性) 建立目的地所需的 SAP Netweaver BW 物件。</span><span class="sxs-lookup"><span data-stu-id="c789f-136">Optionally, create the SAP Netweaver BW objects that are required by the destination.</span></span> <span data-ttu-id="c789f-137">這包括建立 InfoObject、InfoCube、InfoSource 和 InfoPackage。</span><span class="sxs-lookup"><span data-stu-id="c789f-137">This includes creating InfoObjects, InfoCubes, InfoSources, and InfoPackages.</span></span>  
  
-   <span data-ttu-id="c789f-138">使用您已選取的選項來測試資料的載入。</span><span class="sxs-lookup"><span data-stu-id="c789f-138">Test the loading of data with the options that you have selected.</span></span>  
  
 <span data-ttu-id="c789f-139">您也可以針對目的地的 RFC 函數呼叫啟用記錄</span><span class="sxs-lookup"><span data-stu-id="c789f-139">You can also enable logging of RFC function calls by the destination.</span></span> <span data-ttu-id="c789f-140">(這項記錄與您針對 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝啟用的選擇性記錄是分開的)。您可以在設定目的地將使用的 SAP BW 連接管理員時啟用 RFC 函數呼叫的記錄。</span><span class="sxs-lookup"><span data-stu-id="c789f-140">(This logging is separate from the optional logging that you can enable on [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.) You enable logging of RFC function calls when you configure the SAP BW connection manager that the destination will use.</span></span> <span data-ttu-id="c789f-141">如需有關如何設定 SAP BW 連接管理員的詳細資訊，請參閱＜ [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md)＞。</span><span class="sxs-lookup"><span data-stu-id="c789f-141">For more information about how to configure the SAP BW connection manager, see [SAP BW Connection Manager](../connection-manager/sap-bw-connection-manager.md).</span></span>  
  
 <span data-ttu-id="c789f-142">如果您不知道設定目的地的所有必要值，可能必須詢問 SAP 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="c789f-142">If you do not know all the values that are required to configure the destination, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="c789f-143">如需示範如何設定及使用 SAP BW 連接管理員、來源和目的地的逐步解說，請參閱＜ [搭配 SAP BI 7.0 使用 SQL Server 2008 Integration Services](https://go.microsoft.com/fwlink/?LinkID=137090)＞技術白皮書。</span><span class="sxs-lookup"><span data-stu-id="c789f-143">For a walkthrough that demonstrates how to configure and use the SAP BW connection manager, source, and destination, see the white paper, [Using SQL Server 2008 Integration Services with SAP BI 7.0](https://go.microsoft.com/fwlink/?LinkID=137090).</span></span> <span data-ttu-id="c789f-144">這份技術白皮書也會示範如何設定 SAP BW 中的必要物件。</span><span class="sxs-lookup"><span data-stu-id="c789f-144">This white paper also shows how to configure the required objects in SAP BW.</span></span>  
  
### <a name="using-the-ssis-designer-to-configure-the-destination"></a><span data-ttu-id="c789f-145">使用 SSIS 設計師設定目的地</span><span class="sxs-lookup"><span data-stu-id="c789f-145">Using the SSIS Designer to Configure the Destination</span></span>  
 <span data-ttu-id="c789f-146">如需有關可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中設定之 SAP BW 目的地屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="c789f-146">For more information about the properties of the SAP BW destination that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="c789f-147">SAP BW 目的地編輯器 &#40;連線管理員頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="c789f-147">SAP BW Destination Editor &#40;Connection Manager Page&#41;</span></span>](sap-bw-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="c789f-148">SAP BW 目的地編輯器 &#40;對應頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="c789f-148">SAP BW Destination Editor &#40;Mappings Page&#41;</span></span>](sap-bw-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="c789f-149">SAP BW 目的地編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="c789f-149">SAP BW Destination Editor &#40;Error Output Page&#41;</span></span>](sap-bw-destination-editor-error-output-page.md)  
  
-   [<span data-ttu-id="c789f-150">SAP BW 目的地編輯器 &#40;進階頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="c789f-150">SAP BW Destination Editor &#40;Advanced Page&#41;</span></span>](sap-bw-destination-editor-advanced-page.md)  
  
 <span data-ttu-id="c789f-151">設定 SAP BW 目的地時，您也可以使用各種對話方塊來查閱或建立 SAP Netweaver BW 物件。</span><span class="sxs-lookup"><span data-stu-id="c789f-151">While you are configuring the SAP BW destination, you can also use various dialog boxes to look up or to create SAP Netweaver BW objects.</span></span> <span data-ttu-id="c789f-152">如需有關這些對話方塊的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="c789f-152">For more information about these dialog boxes, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="c789f-153"> InfoPackage</span><span class="sxs-lookup"><span data-stu-id="c789f-153">Look Up InfoPackage</span></span>](look-up-infopackage.md)  
  
-   [<span data-ttu-id="c789f-154">建立新的 InfoObject</span><span class="sxs-lookup"><span data-stu-id="c789f-154">Create New InfoObject</span></span>](create-new-infoobject.md)  
  
-   [<span data-ttu-id="c789f-155">建立交易資料的 InfoCube</span><span class="sxs-lookup"><span data-stu-id="c789f-155">Create InfoCube for Transaction Data</span></span>](create-infocube-for-transaction-data.md)  
  
-   [<span data-ttu-id="c789f-156">查詢 InfoObject</span><span class="sxs-lookup"><span data-stu-id="c789f-156">Look Up InfoObject</span></span>](look-up-infoobject.md)  
  
-   [<span data-ttu-id="c789f-157">建立 InfoSource</span><span class="sxs-lookup"><span data-stu-id="c789f-157">Create InfoSource</span></span>](create-infosource.md)  
  
-   [<span data-ttu-id="c789f-158">建立交易資料的 InfoSource</span><span class="sxs-lookup"><span data-stu-id="c789f-158">Create InfoSource for Transaction Data</span></span>](create-infosource-for-transaction-data.md)  
  
-   [<span data-ttu-id="c789f-159">建立主要資料的 InfoSource</span><span class="sxs-lookup"><span data-stu-id="c789f-159">Create InfoSource for Master Data</span></span>](create-infosource-for-master-data.md)  
  
-   [<span data-ttu-id="c789f-160">建立 InfoPackage</span><span class="sxs-lookup"><span data-stu-id="c789f-160">Create InfoPackage</span></span>](create-infopackage.md)  
  
## <a name="see-also"></a><span data-ttu-id="c789f-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c789f-161">See Also</span></span>  
 [<span data-ttu-id="c789f-162">Microsoft Connector 1.1 for SAP BW 元件</span><span class="sxs-lookup"><span data-stu-id="c789f-162">Microsoft Connector 1.1 for SAP BW Components</span></span>](../microsoft-connector-for-sap-bw-components.md)  
  
  
