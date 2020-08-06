---
title: 對 Windows Token Service 的宣告 (C2WTS) 和 Reporting Services |Microsoft Docs
ms.custom: ''
ms.date: 03/25/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- c2wts.exe.config
- SharePoint mode
- C2WTS
- WSS_WPG
ms.assetid: 4d380509-deed-4b4b-a9c1-a9134cc40641
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: cf2e245dfae17556bdb906c134ba0d53898a8631
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595511"
---
# <a name="claims-to-windows-token-service-c2wts-and-reporting-services"></a><span data-ttu-id="ad771-102">對 Windows Token 服務 (C2WTS) 和 Reporting Services 的宣告</span><span class="sxs-lookup"><span data-stu-id="ad771-102">Claims to Windows Token Service (C2WTS) and Reporting Services</span></span>
  <span data-ttu-id="ad771-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]如果您想要針對 sharepoint 伺服器陣列以外的資料來源使用 windows 驗證，sharepoint 模式需要 sharepoint 對 Windows Token 服務的宣告 (c2WTS) 。</span><span class="sxs-lookup"><span data-stu-id="ad771-103">The SharePoint Claims to Windows Token Service (c2WTS) is required with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode if you want to use windows authentication for Data Sources that are outside the SharePoint farm.</span></span> <span data-ttu-id="ad771-104">使用者若是利用 Windows 驗證存取資料來源也是如此，因為 Web 前端 (WFE) 與 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共用服務之間的通訊皆會使用宣告驗證。</span><span class="sxs-lookup"><span data-stu-id="ad771-104">This is true even if the user accesses the data sources with Windows Authentication because the communication between the web front-end (WFE) and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] shared service will always be Claims authentication.</span></span>  
  
 <span data-ttu-id="ad771-105">即使資料來源位於共用服務所在的同一部電腦上，也必須使用 c2WTS。</span><span class="sxs-lookup"><span data-stu-id="ad771-105">c2WTS is needed even if your data source(s) are on the same computer as the shared service.</span></span> <span data-ttu-id="ad771-106">但此情況無須使用限制委派。</span><span class="sxs-lookup"><span data-stu-id="ad771-106">However in this scenario, constrained delegation is not needed.</span></span>  
  
 <span data-ttu-id="ad771-107">c2WTS 所建立的 Token 只可與限制委派 (僅限特定服務使用) 及組態選項 [使用任何驗證通訊協定] 並用。</span><span class="sxs-lookup"><span data-stu-id="ad771-107">The tokens created by c2WTS will only work with constrained delegation (constrains to specific services) and the configuration option "using any authentication protocol".</span></span> <span data-ttu-id="ad771-108">如前文所述，資料來源與共用服務若是位在同一部電腦上，即無須使用限制委派。</span><span class="sxs-lookup"><span data-stu-id="ad771-108">As noted earlier, if your data sources are on the same computer as the shared service, then constrained delegation is not needed.</span></span>  
  
 <span data-ttu-id="ad771-109">如果您的環境會使用 Kerberos 限制委派，則 SharePoint Server 服務及外部資料來源必須位於相同的 Windows 網域。</span><span class="sxs-lookup"><span data-stu-id="ad771-109">If your environment will use Kerberos constrained delegation, then the SharePoint Server service and external data sources need to reside in the same Windows domain.</span></span> <span data-ttu-id="ad771-110">相依於 Windows Token 服務之宣告 (c2WTS) 的任何服務，都必須使用 Kerberos **限制** 委派，才能讓 c2WTS 使用 Kerberos 通訊協定轉換將宣告轉譯成 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="ad771-110">Any service that relies on the Claims to Windows token service (c2WTS) must use Kerberos **constrained** delegation to allow c2WTS to use Kerberos protocol transition to translate claims into Windows credentials.</span></span> <span data-ttu-id="ad771-111">這些需求對於所有 SharePoint Shared 服務都是如此。</span><span class="sxs-lookup"><span data-stu-id="ad771-111">These requirements are true for all SharePoint Shared Services.</span></span> <span data-ttu-id="ad771-112">如需詳細資訊，請參閱[Microsoft SharePoint 2010 產品的 Kerberos 驗證總覽 https://technet.microsoft.com/library/gg502594.aspx) (](https://technet.microsoft.com/library/gg502594.aspx)。</span><span class="sxs-lookup"><span data-stu-id="ad771-112">For more information, see [Overview of Kerberos authentication for Microsoft SharePoint 2010 Products  (https://technet.microsoft.com/library/gg502594.aspx)](https://technet.microsoft.com/library/gg502594.aspx).</span></span>  
  
 <span data-ttu-id="ad771-113">本主題中會概述此程序。</span><span class="sxs-lookup"><span data-stu-id="ad771-113">The procedure is summarized in this topic.</span></span>  
  
||  
|-|  
|<span data-ttu-id="ad771-114">**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="ad771-114">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="ad771-115">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="ad771-115">Prerequisites</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ad771-116">注意：在某些伺服器陣列拓撲中，部分組態步驟可能會有所變更或無法使用。</span><span class="sxs-lookup"><span data-stu-id="ad771-116">Note: Some of the configuration steps may change, or may not work in certain farm topologies.</span></span> <span data-ttu-id="ad771-117">例如單一伺服器安裝並不支援 Windows Identity Foundation c2WTS 服務，因此即無法在此伺服器陣列組態使用對 Windows Token 委派的宣告。</span><span class="sxs-lookup"><span data-stu-id="ad771-117">For instance, a single server install does not support the Windows Identity Foundation c2WTS services so claims to windows token delegation scenarios are not possible with this farm configuration.</span></span>  
  
### <a name="basic-steps-needed-to-configure-c2wts"></a><span data-ttu-id="ad771-118">設定 c2WTS 所需的基本步驟</span><span class="sxs-lookup"><span data-stu-id="ad771-118">Basic steps needed to configure c2WTS</span></span>  
  
1.  <span data-ttu-id="ad771-119">設定 c2WTS 服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="ad771-119">Configure the c2WTS service account.</span></span> <span data-ttu-id="ad771-120">在每部執行 c2WTS 的應用程式伺服器的本機 Administrators 群組中加入服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="ad771-120">Add the service account to the local Administrators group on each application server running c2WTS.</span></span> <span data-ttu-id="ad771-121">此外，確認帳戶具有下列本機安全性原則權限︰</span><span class="sxs-lookup"><span data-stu-id="ad771-121">In addition, verify that the account has the following local security policy rights:</span></span>  
  
    -   <span data-ttu-id="ad771-122">作為作業系統的一部分</span><span class="sxs-lookup"><span data-stu-id="ad771-122">Act as part of the operating system</span></span>  
  
    -   <span data-ttu-id="ad771-123">在驗證後模擬用戶端</span><span class="sxs-lookup"><span data-stu-id="ad771-123">Impersonate a client after authentication</span></span>  
  
    -   <span data-ttu-id="ad771-124">登入為服務</span><span class="sxs-lookup"><span data-stu-id="ad771-124">Log on as a service</span></span>  
  
     <span data-ttu-id="ad771-125">您用於 c2WTS 的帳戶也必須設定為具有通訊協定轉換的限制委派，而且需要委派給所需的服務，才能與 (，例如 SQL Server 引擎、SQL Server Analysis Services) 。若要設定委派，您可以使用 [Active Directory 使用者和電腦] 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="ad771-125">The account you use for c2WTS also needs to be configured for Constrained Delegation with Protocol Transitioning and needs permissions to delegate to the Services it is required to communicate with (i.e. SQL Server Engine, SQL Server Analysis Services).To configure delegation you can use the Active Directory Users and Computer snap-in.</span></span>  
  
    1.  <span data-ttu-id="ad771-126">以滑鼠右鍵按一下各服務帳戶，以開啟屬性對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ad771-126">Right-click each service account and open the properties dialog.</span></span> <span data-ttu-id="ad771-127">按一下對話方塊中的 [委派]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ad771-127">In the dialog click the **Delegation** tab.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="ad771-128">注意：物件必須指派有 SPN，才會顯示委派索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ad771-128">Note: the delegation tab is only visible if the object has an SPN assigned to it.</span></span> <span data-ttu-id="ad771-129">c2WTS 不需要 c2WTS 帳戶的 SPN，但若沒有 SPN，將不會顯示 [**委派**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ad771-129">c2WTS does not require an SPN on the c2WTS Account, however, without an SPN, the **Delegation** tab will not be visible.</span></span> <span data-ttu-id="ad771-130">另一種設定限制委派的方法是使用 **ADSIEdit**這類的公用程式。</span><span class="sxs-lookup"><span data-stu-id="ad771-130">An alternative way to configure constrained delegation is to use a utility such as **ADSIEdit**.</span></span>  
  
    2.  <span data-ttu-id="ad771-131">以下是 [委派] 索引標籤上的主要組態選項：</span><span class="sxs-lookup"><span data-stu-id="ad771-131">Key configuration options on the delegation tab are the following:</span></span>  
  
        -   <span data-ttu-id="ad771-132">選取 [信任這個使用者，但只委派指定的服務]</span><span class="sxs-lookup"><span data-stu-id="ad771-132">Select "Trust this user for delegation to specified services only"</span></span>  
  
        -   <span data-ttu-id="ad771-133">選取 [使用任何驗證通訊協定]</span><span class="sxs-lookup"><span data-stu-id="ad771-133">Select "Use any authentication protocol"</span></span>  
  
         <span data-ttu-id="ad771-134">如需詳細資訊，請參閱下列白皮書中的「設定電腦和服務帳戶的 Kerberos 限制委派」一節，為[SharePoint 2010 和 SQL Server 2008 R2 產品設定 kerberos 驗證](https://docs.microsoft.com/archive/blogs/tothesharepoint/white-paper-configuring-kerberos-authentication-for-sharepoint-2010-and-sql-server-2008-r2-products)</span><span class="sxs-lookup"><span data-stu-id="ad771-134">For more information, see the "configure Kerberos constrained delegation for computers and service accounts" section of the following white paper, [Configuring Kerberos authentication for SharePoint 2010 and SQL Server 2008 R2 products](https://docs.microsoft.com/archive/blogs/tothesharepoint/white-paper-configuring-kerberos-authentication-for-sharepoint-2010-and-sql-server-2008-r2-products)</span></span>  
  
2.  <span data-ttu-id="ad771-135">設定 c2WTS ' AllowedCallers '</span><span class="sxs-lookup"><span data-stu-id="ad771-135">Configure c2WTS 'AllowedCallers'</span></span>  
  
     <span data-ttu-id="ad771-136">c2WTS 需要在設定檔中明確列出「呼叫者」身分識別， **c2wtshost.exe.config**。c2WTS 不接受系統中所有經過驗證之使用者的要求，除非已設定為執行此動作。</span><span class="sxs-lookup"><span data-stu-id="ad771-136">c2WTS requires the 'callers' identities explicitly listed in the configuration file, **c2wtshost.exe.config**. c2WTS does not accept requests from all authenticated users in the system unless it is configured to do so.</span></span> <span data-ttu-id="ad771-137">本例中的 'caller' 是 WSS_WPG Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="ad771-137">In this case the 'caller' is the WSS_WPG Windows group.</span></span> <span data-ttu-id="ad771-138">c2wtshost.exe.confi 檔案會儲存在下列位置：</span><span class="sxs-lookup"><span data-stu-id="ad771-138">The c2wtshost.exe.confi file is saved in the following location:</span></span>  
  
     <span data-ttu-id="ad771-139">**\Program Files\Windows Identity Foundation\v3.5\c2wtshost.exe.config**</span><span class="sxs-lookup"><span data-stu-id="ad771-139">**\Program Files\Windows Identity Foundation\v3.5\c2wtshost.exe.config**</span></span>  
  
     <span data-ttu-id="ad771-140">以下是組態檔的範例：</span><span class="sxs-lookup"><span data-stu-id="ad771-140">The following is an example of the configuration file:</span></span>  
  
    ```  
    <configuration>  
      <windowsTokenService>  
        <!--  
            By default no callers are allowed to use the Windows Identity Foundation Claims To NT Token Service.  
            Add the identities you wish to allow below.  
          -->  
        <allowedCallers>  
          <clear/>  
          <add value="WSS_WPG" />  
        </allowedCallers>  
      </windowsTokenService>  
    </configuration>  
    ```  
  
3.  <span data-ttu-id="ad771-141">啟動作業系統的 c2WTS 服務：</span><span class="sxs-lookup"><span data-stu-id="ad771-141">Start the operating system c2WTS service:</span></span>  
  
    1.  <span data-ttu-id="ad771-142">將該服務設定成使用您在前述步驟中設定的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="ad771-142">Configure the service to use the service account you configured in the previous step.</span></span>  
  
    2.  <span data-ttu-id="ad771-143">將 [啟動類型] 變更為 [**自動**]，然後啟動服務。</span><span class="sxs-lookup"><span data-stu-id="ad771-143">Change the Startup type to "**Automatic**" and start the service.</span></span>  
  
4.  <span data-ttu-id="ad771-144">啟動 SharePoint 的「對 Windows Token 服務的宣告」：在 [**管理伺服器上的服務**] 頁面上，透過 SharePoint 管理中心啟動對 Windows token 服務的宣告。</span><span class="sxs-lookup"><span data-stu-id="ad771-144">Start the SharePoint 'Claims to Windows Token Service': Start the Claims to Windows Token Service through SharePoint Central Administration on the **Manage Services on Server** page.</span></span> <span data-ttu-id="ad771-145">您應在要執行動作的伺服器上啟動該服務。</span><span class="sxs-lookup"><span data-stu-id="ad771-145">The service should be started on the server that will be performing the action.</span></span> <span data-ttu-id="ad771-146">例如您有一部 WFE 伺服器及另一部執行 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共用服務的應用程式伺服器，就只需在應用程式伺服器上啟動 c2WTS。</span><span class="sxs-lookup"><span data-stu-id="ad771-146">For example if you have a server that is a WFE and another server that is an Application Server that has the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] shared service running, you only need to start c2WTS on the Application Server.</span></span> <span data-ttu-id="ad771-147">WFE 並不需要 c2WTS。</span><span class="sxs-lookup"><span data-stu-id="ad771-147">c2WTS is not needed on the WFE.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad771-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad771-148">See Also</span></span>  
 <span data-ttu-id="ad771-149">[對 Windows Token 服務的宣告 (c2WTS) 總覽 (https://msdn.microsoft.com/library/ee517278.aspx)](https://msdn.microsoft.com/library/ee517278.aspx) </span><span class="sxs-lookup"><span data-stu-id="ad771-149">[Claims to Windows Token Service (c2WTS) Overview (https://msdn.microsoft.com/library/ee517278.aspx)](https://msdn.microsoft.com/library/ee517278.aspx) </span></span>  
 [<span data-ttu-id="ad771-150">Microsoft SharePoint 2010 產品的 Kerberos 驗證總覽 (https://technet.microsoft.com/library/gg502594.aspx)</span><span class="sxs-lookup"><span data-stu-id="ad771-150">Overview of Kerberos authentication for Microsoft SharePoint 2010 Products (https://technet.microsoft.com/library/gg502594.aspx)</span></span>](https://technet.microsoft.com/library/gg502594.aspx)  
  
