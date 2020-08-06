---
title: SAP BW 目的地編輯器 (進階頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 862957db-bbc6-4dda-bc0e-591457f1baa7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0c5ca943b804ad39cc391cb1cf7f06e056ddbe56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596818"
---
# <a name="sap-bw-destination-editor-advanced-page"></a><span data-ttu-id="da9f7-102">SAP BW 目的地編輯器 (進階頁面)</span><span class="sxs-lookup"><span data-stu-id="da9f7-102">SAP BW Destination Editor (Advanced Page)</span></span>
  <span data-ttu-id="da9f7-103">使用 SAP BW 目的地編輯器  的 [進階]  頁面可以設定進階設定，例如封裝大小和逾時資訊。</span><span class="sxs-lookup"><span data-stu-id="da9f7-103">Use the **Advanced** page of the **SAP BW Destination Editor** to set advanced settings such as package size and time-out information.</span></span>  
  
 <span data-ttu-id="da9f7-104">若要深入了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 目的地，請參閱 [SAP BW 目的地](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="da9f7-104">To learn more about the SAP BW destination of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="da9f7-105">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="da9f7-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="da9f7-106">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="da9f7-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="da9f7-107">**若要開啟進階頁面**</span><span class="sxs-lookup"><span data-stu-id="da9f7-107">**To open the Advanced page**</span></span>  
  
1.  <span data-ttu-id="da9f7-108">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含 SAP BW 目的地的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件。</span><span class="sxs-lookup"><span data-stu-id="da9f7-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="da9f7-109">在 [資料流程]  索引標籤上，按兩下 SAP BW 目的地。</span><span class="sxs-lookup"><span data-stu-id="da9f7-109">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="da9f7-110">在 SAP BW 目的地編輯器  中，按一下 [進階]  開啟編輯器的 [進階]  頁面。</span><span class="sxs-lookup"><span data-stu-id="da9f7-110">In the **SAP BW Destination Editor**, click **Advanced** to open the **Advanced** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="da9f7-111">選項。</span><span class="sxs-lookup"><span data-stu-id="da9f7-111">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="da9f7-112">如果您不知道設定目的地的所有必要值，可能必須詢問 SAP 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="da9f7-112">If you do not know all the values that are required to configure the destination, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="da9f7-113">**封裝大小**</span><span class="sxs-lookup"><span data-stu-id="da9f7-113">**Package size**</span></span>  
 <span data-ttu-id="da9f7-114">指定一次會傳輸多少個資料列。</span><span class="sxs-lookup"><span data-stu-id="da9f7-114">Specify how many rows of data will be transferred at a time.</span></span> <span data-ttu-id="da9f7-115">這個參數的最佳值取決於 SAP Netweaver BW 系統以及可能進行的其他資料處理。</span><span class="sxs-lookup"><span data-stu-id="da9f7-115">The optimal value for this parameter depends on the SAP Netweaver BW system and on additional processing of the data that might occur.</span></span> <span data-ttu-id="da9f7-116">一般而言，介於 2000 到 20000 之間的值可提供最佳效能。</span><span class="sxs-lookup"><span data-stu-id="da9f7-116">Typically, values between 2000 and 20000 offer the best performance.</span></span>  
  
 <span data-ttu-id="da9f7-117">**觸發處理序鏈結**</span><span class="sxs-lookup"><span data-stu-id="da9f7-117">**Trigger process chain**</span></span>  
 <span data-ttu-id="da9f7-118">(選擇性) 指定要在資料載入完成後觸發之處理序鏈結的名稱。</span><span class="sxs-lookup"><span data-stu-id="da9f7-118">(Optional) Specify the name of a process chain to be triggered after the loading of data is completed.</span></span>  
  
 <span data-ttu-id="da9f7-119">**等候 InfoPackage 的逾時**</span><span class="sxs-lookup"><span data-stu-id="da9f7-119">**Timeout for waiting InfoPackage**</span></span>  
 <span data-ttu-id="da9f7-120">指定目的地應該等候 InfoPackage 完成的秒數上限。</span><span class="sxs-lookup"><span data-stu-id="da9f7-120">Specify the maximum number of seconds that the destination should wait for the InfoPackage to finish.</span></span>  
  
 <span data-ttu-id="da9f7-121">**等候資料傳送結束**</span><span class="sxs-lookup"><span data-stu-id="da9f7-121">**Wait for data transfer to finish**</span></span>  
 <span data-ttu-id="da9f7-122">指定目的地是否應該等候直到 SAP Netweaver BW 系統完成資料載入為止。</span><span class="sxs-lookup"><span data-stu-id="da9f7-122">Specify whether the destination should wait until the SAP Netweaver BW system has finished loading the data.</span></span>  
  
 <span data-ttu-id="da9f7-123">**不要啟動 InfoPackage (僅等候)**</span><span class="sxs-lookup"><span data-stu-id="da9f7-123">**No InfoPackage Start (Only Wait)**</span></span>  
 <span data-ttu-id="da9f7-124">指定目的地不會觸發 InfoPackage，而是只會等候 SAP Netweaver BW 系統已開始載入資料的通知。</span><span class="sxs-lookup"><span data-stu-id="da9f7-124">Specify that the destination does not trigger an InfoPackage, but just waits for notification that the SAP Netweaver BW system has started loading the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da9f7-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da9f7-125">See Also</span></span>  
 <span data-ttu-id="da9f7-126">[SAP BW 目的地編輯器 &#40;連線管理員頁面&#41;](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="da9f7-126">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="da9f7-127">[SAP BW 目的地編輯器 &#40;對應頁面&#41;](sap-bw-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="da9f7-127">[SAP BW Destination Editor &#40;Mappings Page&#41;](sap-bw-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="da9f7-128">[SAP BW 目的地編輯器 &#40;錯誤輸出頁面&#41;](sap-bw-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="da9f7-128">[SAP BW Destination Editor &#40;Error Output Page&#41;](sap-bw-destination-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="da9f7-129">Microsoft Connector 1.1 for SAP BW F1 說明</span><span class="sxs-lookup"><span data-stu-id="da9f7-129">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
