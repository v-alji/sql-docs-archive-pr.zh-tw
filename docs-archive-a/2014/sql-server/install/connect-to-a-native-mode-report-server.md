---
title: 連接至原生模式報表伺服器 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.connectiondialog.F1
helpviewer_keywords:
- report servers [Reporting Services], configuring
ms.assetid: 8b9ea8d3-827c-4011-9e02-be2eac3bb364
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9952b81ab95f002587f8b9b7ef67810822016372
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593786"
---
# <a name="connect-to-a-native-mode-report-server"></a><span data-ttu-id="9b8e2-102">連接至原生模式報表伺服器</span><span class="sxs-lookup"><span data-stu-id="9b8e2-102">Connect to a Native Mode Report Server</span></span>
  <span data-ttu-id="9b8e2-103">使用此對話方塊可連接到本機或遠端 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 或更新的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-103">Use this dialog box to connect to a local or remote [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server instance.</span></span> <span data-ttu-id="9b8e2-104">您無法使用此工具來連接到舊版的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-104">You cannot use this tool to connect to earlier versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report servers.</span></span> <span data-ttu-id="9b8e2-105">您一次只能連接到一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-105">You can only connect to one instance at a time.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="9b8e2-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]原生模式。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9b8e2-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員不會用來設定及管理 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-107">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager is not used to configure and administer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span> <span data-ttu-id="9b8e2-108">您可以使用 SharePoint 管理中心和 PowerShell 指令碼，在 SharePoint 模式下設定報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-108">You Use SharePoint Central Administration and PowerShell scripts to configure a report server in SharePoint mode.</span></span> <span data-ttu-id="9b8e2-109">如需詳細資訊，請參閱[安裝 sharepoint 2010 Reporting Services Sharepoint 模式](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)</span><span class="sxs-lookup"><span data-stu-id="9b8e2-109">For more information, see [Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="9b8e2-110">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Configuration Manager ( # A0) 是以 "highestAvailable" 的許可權層級來安裝。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-110">The[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager (RSConfigTool.exe) is installed with a privilege level of "highestAvailable".</span></span> <span data-ttu-id="9b8e2-111">這是設計的行為。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-111">This behavior is by design.</span></span> <span data-ttu-id="9b8e2-112">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員需要與 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI API 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-112">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager requires communication with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI APIs.</span></span> <span data-ttu-id="9b8e2-113">某些 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI 通訊需要更高層級或系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-113">Some of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI communication requires a higher level or administrative of privileges.</span></span>  
  
-   <span data-ttu-id="9b8e2-114">若要連接到本機報表伺服器執行個體，請使用預設值，然後按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-114">To connect to a local report server instance, use the default values and click **Connect**.</span></span> <span data-ttu-id="9b8e2-115">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員會提供本機伺服器名稱，並偵測預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-115">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager provides the local server name and detects the default instance.</span></span> <span data-ttu-id="9b8e2-116">在大部分情況下，您可以按一下 **[連接]** 而不必變更值。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-116">In most cases, you can click **Connect** without having to change the values.</span></span> <span data-ttu-id="9b8e2-117">如果您安裝了一個以上的執行個體，您必須選取您想要使用的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-117">If you installed more than one instance, you must select the one that you want to use.</span></span>  
  
-   <span data-ttu-id="9b8e2-118">若要連接到遠端報表伺服器執行個體，請輸入伺服器名稱，再按一下 **[尋找]**，並選取此執行個體，然後按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-118">To connect to a remote report server instance, type the server name, click **Find**, select the instance, and then click **Connect**.</span></span>  
  
 <span data-ttu-id="9b8e2-119">若要開啟此對話方塊，請啟動 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-119">To open this dialog box, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="9b8e2-120">當您啟動此工具時，這個對話方塊會立即出現。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-120">This dialog box appears immediately when you start the tool.</span></span> <span data-ttu-id="9b8e2-121">如需詳細資訊，請參閱 [Reporting Services 組態管理員 &#40;原生模式&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-121">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="9b8e2-122">選項</span><span class="sxs-lookup"><span data-stu-id="9b8e2-122">Options</span></span>  
 <span data-ttu-id="9b8e2-123">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="9b8e2-123">**Server Name**</span></span>  
 <span data-ttu-id="9b8e2-124">輸入安裝 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 或更新版本 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 之電腦的網路名稱。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-124">Enter the network name of the computer on which [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is installed.</span></span> <span data-ttu-id="9b8e2-125">只需要輸入電腦名稱；請勿包含前置詞或斜線。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-125">Type just the computer name; do not include a prefix or slashes.</span></span>  
  
 <span data-ttu-id="9b8e2-126">**尋找**</span><span class="sxs-lookup"><span data-stu-id="9b8e2-126">**Find**</span></span>  
 <span data-ttu-id="9b8e2-127">尋找 **[伺服器名稱]** 中指定的電腦。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-127">Find the computer specified in **Server Name**.</span></span>  
  
 <span data-ttu-id="9b8e2-128">**報表伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="9b8e2-128">**Report Server Instance**</span></span>  
 <span data-ttu-id="9b8e2-129">如果安裝了多個報表伺服器執行個體，請選取要連接哪一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-129">Select which instance to connect to if multiple report server instances are installed.</span></span> <span data-ttu-id="9b8e2-130">只有有效的執行個體可供選取。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-130">Only valid instances are available for selection.</span></span> <span data-ttu-id="9b8e2-131">如果您要將舊版 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體並存執行，這些執行個體將不會出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-131">If you are running older versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] side-by-side a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, those instances will not appear in the list.</span></span>  
  
 <span data-ttu-id="9b8e2-132">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="9b8e2-132">**Connect**</span></span>  
 <span data-ttu-id="9b8e2-133">連接到您所指定的伺服器和執行個體。</span><span class="sxs-lookup"><span data-stu-id="9b8e2-133">Connect to the server and instance you specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b8e2-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b8e2-134">See Also</span></span>  
 [<span data-ttu-id="9b8e2-135">Reporting Services 組態管理員 &#40;原生模式&#41;</span><span class="sxs-lookup"><span data-stu-id="9b8e2-135">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
