---
title: 電子郵件設定-Configuration Manager (SSRS 原生模式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.rsconfigtool.emailsettings.f1
helpviewer_keywords:
- SQL11.rsconfigtool.emailsettings.F1
ms.assetid: cdad1529-bfa6-41fb-9863-d9ff1b802577
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8c5f276f8d6566e052ee291118eb1d1c12fbddc9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700846"
---
# <a name="e-mail-settings---configuration-manager-ssrs-native-mode"></a><span data-ttu-id="a268d-102">電子郵件設定 - 組態管理員 (SSRS 原生模式)</span><span class="sxs-lookup"><span data-stu-id="a268d-102">E-mail Settings - Configuration Manager (SSRS Native Mode)</span></span>
  <span data-ttu-id="a268d-103">使用此頁面，即可指定會啟用從報表伺服器傳遞報表伺服器電子郵件的 Simple Mail Transport Protocol (SMTP) 設定。</span><span class="sxs-lookup"><span data-stu-id="a268d-103">Use this page to specify Simple Mail Transport Protocol (SMTP) settings that enable report server e-mail delivery from the report server.</span></span> <span data-ttu-id="a268d-104">您可以使用報表伺服器電子郵件傳遞延伸模組，透過電子郵件訂閱來散發報表或報表處理通知。</span><span class="sxs-lookup"><span data-stu-id="a268d-104">You can use the Report Server E-Mail delivery extension to distribute reports or report processing notifications through e-mail subscriptions.</span></span> <span data-ttu-id="a268d-105">報表伺服器電子郵件傳遞延伸模組，需要使用 [從:] 欄位中的 SMTP 伺服器和電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="a268d-105">The Report Server E-Mail delivery extension requires an SMTP server and an e-mail address to use in the From: field.</span></span>  
  
 <span data-ttu-id="a268d-106">其他組態設定可用來進一步自訂電子郵件訂閱，其中包含會限制郵件伺服器主機和轉譯延伸模組之可用性的設定。</span><span class="sxs-lookup"><span data-stu-id="a268d-106">Additional configuration settings can be used to further customize e-mail subscriptions, including settings that restrict mail server hosts and rendering extension availability.</span></span> <span data-ttu-id="a268d-107">您無法在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員中指定這些設定。</span><span class="sxs-lookup"><span data-stu-id="a268d-107">You cannot specify these settings in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="a268d-108">若要設定其他設定，則您必須手動編輯 RSReportServer.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="a268d-108">To configure the additional settings, you must manually edit the RSReportServer.config file.</span></span> <span data-ttu-id="a268d-109">如需詳細資訊，請參閱《線上叢書》中的[設定報表伺服器的電子郵件傳遞 &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)和[Reporting Services 設定檔](../report-server/reporting-services-configuration-files.md)案 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a268d-109">For more information, see [Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) and [Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="a268d-110">若要開啟此頁面，請啟動 Reporting Services 組態管理員，然後按一下流覽窗格中的 [**電子郵件設定**]。</span><span class="sxs-lookup"><span data-stu-id="a268d-110">To open this page, start the Reporting Services Configuration Manager and click **E-mail Settings** in the navigation pane.</span></span> <span data-ttu-id="a268d-111">如需詳細資訊，請參閱 [Reporting Services 組態管理員 &#40;原生模式&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="a268d-111">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="a268d-112">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]原生模式。</span><span class="sxs-lookup"><span data-stu-id="a268d-112">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a268d-113">選項</span><span class="sxs-lookup"><span data-stu-id="a268d-113">Options</span></span>  
 <span data-ttu-id="a268d-114">**寄件者位址**</span><span class="sxs-lookup"><span data-stu-id="a268d-114">**Sender Address**</span></span>  
 <span data-ttu-id="a268d-115">指定用於所產生電子郵件之 [從:] 欄位中的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="a268d-115">Specifies the e-mail address to use in the From: field of a generated e-mail.</span></span> <span data-ttu-id="a268d-116">您必須指定有權從 SMTP 伺服器傳送郵件的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a268d-116">You must specify a user account that has permission to send mail from the SMTP server.</span></span>  
  
 <span data-ttu-id="a268d-117">**目前的 SMTP 傳遞方法**</span><span class="sxs-lookup"><span data-stu-id="a268d-117">**Current SMTP Delivery Method**</span></span>  
 <span data-ttu-id="a268d-118">指定報表伺服器電子郵件是透過 SMTP 伺服器來傳送。</span><span class="sxs-lookup"><span data-stu-id="a268d-118">Specifies that report server e-mail is routed through an SMTP server.</span></span> <span data-ttu-id="a268d-119">這是在 Reporting Services 組態管理員中，您唯一可以指定的傳遞方法。</span><span class="sxs-lookup"><span data-stu-id="a268d-119">This is the only delivery method that you can specify in the Reporting Services Configuration Manager.</span></span>  
  
 <span data-ttu-id="a268d-120">替代的傳遞方法是使用本機 SMTP 服務收取目錄。</span><span class="sxs-lookup"><span data-stu-id="a268d-120">An alternative delivery method is to use a local SMTP service pickup directory.</span></span> <span data-ttu-id="a268d-121">如果無法使用網路 SMTP 服務，您就可以使用此傳遞方法。</span><span class="sxs-lookup"><span data-stu-id="a268d-121">You can use this delivery method if a network SMTP service is not available.</span></span> <span data-ttu-id="a268d-122">若要指定本機 SMTP 服務收取目錄，您必須編輯 RSReportServer.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="a268d-122">To specify a local SMTP service pickup directory, you must edit the RSReportServer.config file.</span></span> <span data-ttu-id="a268d-123">如果您編輯設定檔以使用本機 SMTP 服務收取目錄，Reporting Services 組態管理員會將 [**傳遞方法**] 選項設定為 [*自訂*]，以指出傳遞方法是在設定檔中指定。</span><span class="sxs-lookup"><span data-stu-id="a268d-123">If you edit the configuration file to use a local SMTP service pickup directory, the Reporting Services Configuration Manager sets the **Delivery method** option to *custom* to indicate that the delivery method is specified in the configuration file.</span></span>  
  
 <span data-ttu-id="a268d-124">在組態檔中，傳遞方法是透過 `SendUsing` 組態設定來加以設定。</span><span class="sxs-lookup"><span data-stu-id="a268d-124">In the configuration file, the delivery method is set through the `SendUsing` configuration setting.</span></span> <span data-ttu-id="a268d-125">如需有關指定設定的詳細資訊 `SendUsing` ，請參閱[為電子郵件傳遞設定報表伺服器 &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="a268d-125">For more information about specifying the `SendUsing` setting, see [Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="a268d-126">**SMTP 伺服器**</span><span class="sxs-lookup"><span data-stu-id="a268d-126">**SMTP Server**</span></span>  
 <span data-ttu-id="a268d-127">指定要使用的 SMTP 伺服器或閘道。</span><span class="sxs-lookup"><span data-stu-id="a268d-127">Specify the SMTP server or gateway to use.</span></span> <span data-ttu-id="a268d-128">您可以在網路上使用本機伺服器或 SMTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a268d-128">You can use a local server or an SMTP server on your network.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a268d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a268d-129">See Also</span></span>  
 <span data-ttu-id="a268d-130">[針對 &#40;SSRS Configuration Manager 的電子郵件傳遞設定報表伺服器&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="a268d-130">[Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="a268d-131">Reporting Services 組態管理員 &#40;SSRS 原生模式的 F1 說明主題&#41;</span><span class="sxs-lookup"><span data-stu-id="a268d-131">Reporting Services Configuration Manager F1 Help Topics &#40;SSRS Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)  
  
  
