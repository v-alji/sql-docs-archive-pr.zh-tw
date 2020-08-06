---
title: 建立 InfoSource | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e7db233b-5464-43de-9d26-6dd24c7ac1b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9620d3170310322c79679e8298ffe465067ae7d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687082"
---
# <a name="create-infosource"></a><span data-ttu-id="cf1bd-102">建立 InfoSource</span><span class="sxs-lookup"><span data-stu-id="cf1bd-102">Create InfoSource</span></span>
  <span data-ttu-id="cf1bd-103">使用 [建立 InfoSource]  對話方塊可以建立新的 InfoSource。</span><span class="sxs-lookup"><span data-stu-id="cf1bd-103">Use the **Create InfoSource** dialog box to create a new InfoSource.</span></span> <span data-ttu-id="cf1bd-104">若要建立新的 InfoSource，您可以使用 [建立交易資料的 InfoSource]  或 [建立主要資料的 InfoSource]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cf1bd-104">To create the new InfoSource, you use either the **Create InfoSource for Transaction Data** or the **Create InfoSource for Master Data** dialog box.</span></span>  
  
 <span data-ttu-id="cf1bd-105">您可以從 [SAP BW 目的地編輯器] 的 [連線管理員] 頁面開啟 [建立 InfoSource] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cf1bd-105">You can open the **Create InfoSource** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="cf1bd-106">若要深入了解 SAP BW 目的地，請參閱 [SAP BW Destination](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="cf1bd-106">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cf1bd-107">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="cf1bd-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="cf1bd-108">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="cf1bd-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="cf1bd-109">**若要開啟建立 InfoSource 對話方塊**</span><span class="sxs-lookup"><span data-stu-id="cf1bd-109">**To open the Create InfoSource dialog box**</span></span>  
  
1.  <span data-ttu-id="cf1bd-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含 SAP BW 目的地的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件。</span><span class="sxs-lookup"><span data-stu-id="cf1bd-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="cf1bd-111">在 [資料流程]  索引標籤上，按兩下 SAP BW 目的地。</span><span class="sxs-lookup"><span data-stu-id="cf1bd-111">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="cf1bd-112">在 **[SAP BW 目的地編輯器]** 中，按一下 **[連接管理員]** 開啟編輯器的 **[連接管理員]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="cf1bd-112">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="cf1bd-113">在 [連線管理員]  頁面的 [建立 SAP BW 物件]  群組方塊中，選取 [InfoSource]  ，然後按一下 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="cf1bd-113">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select **InfoSource**, and then click **Create**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="cf1bd-114">選項。</span><span class="sxs-lookup"><span data-stu-id="cf1bd-114">Options</span></span>  
 <span data-ttu-id="cf1bd-115">**交易資料**</span><span class="sxs-lookup"><span data-stu-id="cf1bd-115">**Transaction data**</span></span>  
 <span data-ttu-id="cf1bd-116">建立交易資料的新 InfoSource。</span><span class="sxs-lookup"><span data-stu-id="cf1bd-116">Create a new InfoSource for transaction data.</span></span>  
  
 <span data-ttu-id="cf1bd-117">如果您選取此選項，就會開啟 [建立交易資料的 InfoSource]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cf1bd-117">If you select this option, the **Create InfoSource for Transaction Data** dialog box opens.</span></span> <span data-ttu-id="cf1bd-118">您可以使用 [建立交易資料的 InfoSource]  對話方塊來建立新的 InfoSource。</span><span class="sxs-lookup"><span data-stu-id="cf1bd-118">You use the **Create InfoSource for Transaction Data** dialog box to create the new InfoSource.</span></span> <span data-ttu-id="cf1bd-119">如需此對話方塊的詳細資訊，請參閱 [建立交易資料的 InfoSource](create-infosource-for-transaction-data.md)。</span><span class="sxs-lookup"><span data-stu-id="cf1bd-119">For more information about this dialog box, see [Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md).</span></span>  
  
 <span data-ttu-id="cf1bd-120">**主要資料**</span><span class="sxs-lookup"><span data-stu-id="cf1bd-120">**Master data**</span></span>  
 <span data-ttu-id="cf1bd-121">建立主要資料的新 InfoSource。</span><span class="sxs-lookup"><span data-stu-id="cf1bd-121">Create a new InfoSource for master data.</span></span>  
  
 <span data-ttu-id="cf1bd-122">如果您選取此選項，就會開啟 [建立主要資料的 InfoSource]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cf1bd-122">If you select this option, the **Create InfoSource for Master Data** dialog box opens.</span></span> <span data-ttu-id="cf1bd-123">您可以使用 [建立主要資料的 InfoSource]  對話方塊來建立新的 InfoSource。</span><span class="sxs-lookup"><span data-stu-id="cf1bd-123">You use the **Create InfoSource for Master Data** dialog box to create the new InfoSource.</span></span> <span data-ttu-id="cf1bd-124">如需此對話方塊的詳細資訊，請參閱 [建立主要資料的 InfoSource](create-infosource-for-master-data.md)。</span><span class="sxs-lookup"><span data-stu-id="cf1bd-124">For more information about this dialog box, see [Create InfoSource for Master Data](create-infosource-for-master-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf1bd-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf1bd-125">See Also</span></span>  
 [<span data-ttu-id="cf1bd-126">Microsoft Connector 1.1 for SAP BW F1 說明</span><span class="sxs-lookup"><span data-stu-id="cf1bd-126">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
