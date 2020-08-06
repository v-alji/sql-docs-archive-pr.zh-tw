---
title: 查閱 RFC 目的地 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: db9404d8-4c42-45e5-a100-c7a84b056109
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 397298fce16509e667aa4baccaee62c6ff0f5cca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708510"
---
# <a name="look-up-rfc-destination"></a><span data-ttu-id="7c6a0-102">查閱 RFC 目的地</span><span class="sxs-lookup"><span data-stu-id="7c6a0-102">Look Up RFC Destination</span></span>
  <span data-ttu-id="7c6a0-103">使用 [查閱 RFC 目的地]  對話方塊可以查閱 SAP Netweaver BW 系統中定義的 RFC 目的地。</span><span class="sxs-lookup"><span data-stu-id="7c6a0-103">Use the **Look Up RFC Destination** dialog box to look up an RFC destination that is defined in the SAP Netweaver BW system.</span></span> <span data-ttu-id="7c6a0-104">出現可用的 RFC 目的地清單時，請選取您要的目的地，然後此元件就會將必要的值填入相關聯的選項。</span><span class="sxs-lookup"><span data-stu-id="7c6a0-104">When the list of available RFC destinations appears, select the destination that you want, and the component will populate the associated options with the required values.</span></span>  
  
 <span data-ttu-id="7c6a0-105">SAP BW 來源和 SAP BW 目的地都會使用 [查閱 RFC 目的地]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7c6a0-105">Both the SAP BW source and the SAP BW destination use the **Look Up RFC Destination** dialog box.</span></span> <span data-ttu-id="7c6a0-106">如需 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 這些元件的詳細資訊，請參閱 [SAP BW 來源](sap-bw-source.md) 和 [SAP BW 目的地](sap-bw-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="7c6a0-106">For more information about these components of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md) and [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7c6a0-107">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="7c6a0-107">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="7c6a0-108">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="7c6a0-108">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="7c6a0-109">**若要開啟查閱 RFC 目的地對話方塊**</span><span class="sxs-lookup"><span data-stu-id="7c6a0-109">**To open the Look Up RFC Destination dialog box**</span></span>  
  
1.  <span data-ttu-id="7c6a0-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含 SAP BW 來源或目的地的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="7c6a0-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source or destination.</span></span>  
  
2.  <span data-ttu-id="7c6a0-111">在 [資料流程]  索引標籤中，按兩下 SAP BW 來源或目的地。</span><span class="sxs-lookup"><span data-stu-id="7c6a0-111">On the **Data Flow** tab, double-click the SAP BW source or destination.</span></span>  
  
3.  <span data-ttu-id="7c6a0-112">在 [SAP BW 來源編輯器]  或 [SAP BW 目的地編輯器]  中，按一下 [連線管理員]  開啟編輯器的 [連線管理員]  頁面。</span><span class="sxs-lookup"><span data-stu-id="7c6a0-112">In the **SAP BW Source Editor** or the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="7c6a0-113">在 [連線管理員]  頁面的 [RFC 目的地]  群組方塊中，按一下 [查閱]  顯示 [查閱 RFC 目的地]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7c6a0-113">On the **Connection Manager** page, in the **RFC Destination** group box, click **Look up** to display the **Look Up RFC Destination** dialog box.</span></span>  
  
     <span data-ttu-id="7c6a0-114">在 [SAP BW 來源編輯器] 中，只有當 [執行模式] 的值是 [P - 觸發處理鏈結] 或 [W - 等候通知] 時，才會出現 [RFC 目的地] 群組方塊。</span><span class="sxs-lookup"><span data-stu-id="7c6a0-114">In the **SAP BW Source Editor**, the **RFC Destination** group box appears only if the value for **Execution mode** is **P - Trigger process chain** or **W - Wait for notify**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7c6a0-115">選項。</span><span class="sxs-lookup"><span data-stu-id="7c6a0-115">Options</span></span>  
 <span data-ttu-id="7c6a0-116">**目的地**</span><span class="sxs-lookup"><span data-stu-id="7c6a0-116">**Destination**</span></span>  
 <span data-ttu-id="7c6a0-117">檢視 SAP Netweaver BW 系統中定義的 RFC 目的地名稱。</span><span class="sxs-lookup"><span data-stu-id="7c6a0-117">View the name of the RFC destination that is defined in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="7c6a0-118">**閘道器主機**</span><span class="sxs-lookup"><span data-stu-id="7c6a0-118">**Gateway Host**</span></span>  
 <span data-ttu-id="7c6a0-119">檢視閘道器主機的伺服器名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="7c6a0-119">View the server name or IP address of the gateway host.</span></span> <span data-ttu-id="7c6a0-120">此名稱或 IP 位址通常與 SAP 應用程式伺服器相同。</span><span class="sxs-lookup"><span data-stu-id="7c6a0-120">Usually, the name or IP address is the same as the SAP application server.</span></span>  
  
 <span data-ttu-id="7c6a0-121">**閘道器服務**</span><span class="sxs-lookup"><span data-stu-id="7c6a0-121">**Gateway Service**</span></span>  
 <span data-ttu-id="7c6a0-122">以 `sapgwNN` 格式檢視閘道服務的名稱，其中 `NN` 是系統編號。</span><span class="sxs-lookup"><span data-stu-id="7c6a0-122">View the name of the gateway service, in the format `sapgwNN`, where `NN` is the system number.</span></span>  
  
 <span data-ttu-id="7c6a0-123">**程式識別碼**</span><span class="sxs-lookup"><span data-stu-id="7c6a0-123">**Program ID**</span></span>  
 <span data-ttu-id="7c6a0-124">檢視與 RFC 目的地相關聯的程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="7c6a0-124">View the Program ID that is associated with the RFC destination.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c6a0-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c6a0-125">See Also</span></span>  
 <span data-ttu-id="7c6a0-126">[SAP BW 來源編輯器 &#40;連線管理員頁面&#41;](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="7c6a0-126">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="7c6a0-127">[SAP BW 目的地編輯器 &#40;連線管理員頁面&#41;](sap-bw-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="7c6a0-127">[SAP BW Destination Editor &#40;Connection Manager Page&#41;](sap-bw-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="7c6a0-128">Microsoft Connector 1.1 for SAP BW F1 說明</span><span class="sxs-lookup"><span data-stu-id="7c6a0-128">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
