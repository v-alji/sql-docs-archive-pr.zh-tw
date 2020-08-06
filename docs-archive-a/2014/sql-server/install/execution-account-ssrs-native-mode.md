---
title: 執行帳戶 (SSRS 原生模式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.executionaccount.F1
ms.assetid: 440b5a09-5fd4-4c3a-b510-f3c33cbf1c82
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 10e158eb38b9d1f94257f48339bb63bae2d3b61b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598189"
---
# <a name="execution-account-ssrs-native-mode"></a><span data-ttu-id="1e50a-102">執行帳戶 (SSRS 原生模式)</span><span class="sxs-lookup"><span data-stu-id="1e50a-102">Execution Account (SSRS Native Mode)</span></span>
  <span data-ttu-id="1e50a-103">使用此頁面，即可設定自動處理所使用的帳戶。</span><span class="sxs-lookup"><span data-stu-id="1e50a-103">Use this page to configure an account to use for unattended processing.</span></span> <span data-ttu-id="1e50a-104">當其他認證來源無法使用的特殊情況下，請使用此帳戶：</span><span class="sxs-lookup"><span data-stu-id="1e50a-104">This account is used under special circumstances when other sources of credentials are not available:</span></span>  
  
-   <span data-ttu-id="1e50a-105">當報表伺服器連接到不需要認證的資料來源時。</span><span class="sxs-lookup"><span data-stu-id="1e50a-105">When the report server connects to a data source that does not require credentials.</span></span> <span data-ttu-id="1e50a-106">可能不需要認證的資料來源範例包括 XML 文件和某些用戶端資料庫應用程式。</span><span class="sxs-lookup"><span data-stu-id="1e50a-106">Examples of data sources that might not require credentials include XML documents and some client-side database applications.</span></span>  
  
-   <span data-ttu-id="1e50a-107">當報表伺服器連接到另一個伺服器，以擷取報表中所參考的外部影像檔或其他資源時。</span><span class="sxs-lookup"><span data-stu-id="1e50a-107">When the report server connects to another server to retrieve external image files or other resources that are referenced in a report.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="1e50a-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]原生模式。</span><span class="sxs-lookup"><span data-stu-id="1e50a-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="1e50a-109">設定這個帳戶是選擇性的，但若未設定此帳戶，當您使用外部影像及連接某些資料來源時，將會受到限制。</span><span class="sxs-lookup"><span data-stu-id="1e50a-109">Setting this account is optional, but not setting it limits your use of external images and connections to some data sources.</span></span> <span data-ttu-id="1e50a-110">擷取外部影像檔時，報表伺服器會檢查是否可以建立匿名連接。</span><span class="sxs-lookup"><span data-stu-id="1e50a-110">When retrieving external image files, the report server checks to see if an anonymous connection can be made.</span></span> <span data-ttu-id="1e50a-111">如果連接有密碼保護，報表伺服器便會使用自動報表處理帳戶連接到遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="1e50a-111">If the connection is password protected, the report server uses the unattended report processing account to connect to the remote server.</span></span> <span data-ttu-id="1e50a-112">擷取報表的資料時，報表伺服器會模擬目前使用者、提示使用者提供認證、使用預存認證，或如果資料來源連接指定認證類型為 **[無]** 時，則會使用自動處理帳戶。</span><span class="sxs-lookup"><span data-stu-id="1e50a-112">When retrieving data for a report, the report server either impersonates the current user, prompts the user to provide credentials, uses stored credentials, or uses the unattended processing account if the data source connection specifies **None** as the credential type.</span></span> <span data-ttu-id="1e50a-113">報表伺服器不允許系統在連接到其他電腦時，委派或模擬其服務帳戶認證，因此如果沒有其他認證可以使用，報表伺服器就必須使用自動處理帳戶。</span><span class="sxs-lookup"><span data-stu-id="1e50a-113">The report server does not allow its service account credentials to be delegated or impersonated when connecting to other computers, so it must use the unattended processing account if no other credentials are available.</span></span>  
  
 <span data-ttu-id="1e50a-114">您所指定的帳戶應該與用於執行服務帳戶的帳戶不同。</span><span class="sxs-lookup"><span data-stu-id="1e50a-114">The account you specify should be different from the one used to run the service account.</span></span> <span data-ttu-id="1e50a-115">如果您設定此帳戶，則會以加密值儲存於 RSReportServer.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="1e50a-115">If you configure this account, it is stored in the RSReportServer.config file as an encrypted value.</span></span> <span data-ttu-id="1e50a-116">如果您在向外延展部署中執行報表伺服器，您必須在每一部報表伺服器上使用相同的方式設定此帳戶。</span><span class="sxs-lookup"><span data-stu-id="1e50a-116">If you are running the report server in a scale-out deployment, you must configure this account the same way on each report server.</span></span>  
  
 <span data-ttu-id="1e50a-117">您可以使用任何 Windows 使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="1e50a-117">You can use any Windows user account.</span></span> <span data-ttu-id="1e50a-118">為求最佳效果，請選擇擁有讀取權限及網路登入權限的帳戶，以連接到其他電腦。</span><span class="sxs-lookup"><span data-stu-id="1e50a-118">For best results, choose an account that has read permissions and network logon permissions to support connections to other computers.</span></span> <span data-ttu-id="1e50a-119">此帳戶必須擁有您想在報表中使用之任何外部影像或資料檔案的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="1e50a-119">It must have read permissions on any external image or data file that you want to use in a report.</span></span> <span data-ttu-id="1e50a-120">除非所有的報表資料來源和外部影像全都儲存在報表伺服器電腦上，否則請勿指定本機帳戶。</span><span class="sxs-lookup"><span data-stu-id="1e50a-120">Do not specify a local account unless all report data sources and external images are stored on the report server computer.</span></span> <span data-ttu-id="1e50a-121">這種帳戶只適用於自動報表處理。</span><span class="sxs-lookup"><span data-stu-id="1e50a-121">Use the account only for unattended report processing.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1e50a-122">如果您正在使用 [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)] with Advanced Services，當您在報表中參考外部影像，而需要有存取該影像檔的權限時，您就只需要設定此帳戶。</span><span class="sxs-lookup"><span data-stu-id="1e50a-122">If you are using [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)] with Advanced Services, you only need to configure this account if you are referencing external images in a report and permission is required to access the image file.</span></span> <span data-ttu-id="1e50a-123">SQL Server Express 不支援遠端伺服器的資料來源連接。</span><span class="sxs-lookup"><span data-stu-id="1e50a-123">SQL Server Express does not support a data source connection to a remote server.</span></span> <span data-ttu-id="1e50a-124">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本支援的功能清單，請參閱 [SQL Server 2012 版本支援的功能](https://go.microsoft.com/fwlink/?linkid=232473)。</span><span class="sxs-lookup"><span data-stu-id="1e50a-124">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
 <span data-ttu-id="1e50a-125">若要開啟此頁面，請啟動 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員，並選取導覽窗格中的 **[執行帳戶]** 。</span><span class="sxs-lookup"><span data-stu-id="1e50a-125">To open this page, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager and select **Execution Account** in the navigation pane.</span></span> <span data-ttu-id="1e50a-126">如需詳細資訊，請參閱 [Reporting Services 組態管理員 &#40;原生模式&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="1e50a-126">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="1e50a-127">選項</span><span class="sxs-lookup"><span data-stu-id="1e50a-127">Options</span></span>  
 <span data-ttu-id="1e50a-128">**指定執行帳戶**</span><span class="sxs-lookup"><span data-stu-id="1e50a-128">**Specify an execution account**</span></span>  
 <span data-ttu-id="1e50a-129">選取此項目來指定帳戶。</span><span class="sxs-lookup"><span data-stu-id="1e50a-129">Select to specify an account.</span></span>  
  
 <span data-ttu-id="1e50a-130">**帳戶**</span><span class="sxs-lookup"><span data-stu-id="1e50a-130">**Account**</span></span>  
 <span data-ttu-id="1e50a-131">輸入 Windows 網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="1e50a-131">Enter a Windows domain user account.</span></span> <span data-ttu-id="1e50a-132">請使用此格式： \* \<domain> \\<使用者 \> 帳戶\*。</span><span class="sxs-lookup"><span data-stu-id="1e50a-132">Use this format: *\<domain>\\<user account\>*.</span></span>  
  
 <span data-ttu-id="1e50a-133">**密碼**</span><span class="sxs-lookup"><span data-stu-id="1e50a-133">**Password**</span></span>  
 <span data-ttu-id="1e50a-134">輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="1e50a-134">Type the password.</span></span>  
  
 <span data-ttu-id="1e50a-135">**確認密碼**</span><span class="sxs-lookup"><span data-stu-id="1e50a-135">**Confirm password**</span></span>  
 <span data-ttu-id="1e50a-136">重新輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="1e50a-136">Retype the password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e50a-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e50a-137">See Also</span></span>  
 <span data-ttu-id="1e50a-138">[Reporting Services 組態管理員 &#40;SSRS 原生模式的 F1 說明主題&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="1e50a-138">[Reporting Services Configuration Manager F1 Help Topics &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="1e50a-139">[儲存加密的報表伺服器資料 &#40;SSRS 組態管理員&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span><span class="sxs-lookup"><span data-stu-id="1e50a-139">[Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span></span>  
 [<span data-ttu-id="1e50a-140">設定自動執行帳戶 &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="1e50a-140">Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;</span></span>](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)  
  
  
