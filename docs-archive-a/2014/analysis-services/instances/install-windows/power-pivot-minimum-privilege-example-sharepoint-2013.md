---
title: PowerPivot for SharePoint 2013 的最低許可權設定範例 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c1e09e6c-52d3-48ab-8c70-818d5d775087
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0188f314e4c354b33d03e6e7948aed1ba4cf8be2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688318"
---
# <a name="example-of-a-minimum-privilege-configuration-for-powerpivot-for-sharepoint-2013"></a><span data-ttu-id="9d4c5-102">PowerPivot for SharePoint 2013 的最低權限組態範例</span><span class="sxs-lookup"><span data-stu-id="9d4c5-102">Example of a Minimum-Privilege Configuration for PowerPivot for SharePoint 2013</span></span>
  <span data-ttu-id="9d4c5-103">本主題描述具有最低權限的 PowerPivot for SharePoint 2013 組態範例。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-103">This topic describes an example PowerPivot for SharePoint 2013 configuration with minimum privileges.</span></span> <span data-ttu-id="9d4c5-104">此組態會分別針對三個元件使用不同的帳戶，而且每個帳戶都具有最低層級的權限。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-104">The configuration utilizes a different account for each of the three components and each account has the minimum level of privileges.</span></span>  
  
## <a name="summary-of-accounts"></a><span data-ttu-id="9d4c5-105">帳戶摘要</span><span class="sxs-lookup"><span data-stu-id="9d4c5-105">Summary of Accounts</span></span>  
 <span data-ttu-id="9d4c5-106">PowerPivot for SharePoint 2013 支援使用網路服務帳戶做為 Analysis Services 服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-106">PowerPivot for SharePoint 2013 supports the use of the Network Service account for the Analysis Services service account.</span></span> <span data-ttu-id="9d4c5-107">網路服務帳戶並非 SharePoint 2010 的支援案例。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-107">The Network Service account is not a supported scenario with SharePoint 2010.</span></span> <span data-ttu-id="9d4c5-108">如需服務帳戶的詳細資訊，請參閱[設定 Windows 服務帳戶和許可權](../../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) (https://msdn.microsoft.com/library/ms143504.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-108">For more information on Service accounts, see [Configure Windows Service Accounts and Permissions](../../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) (https://msdn.microsoft.com/library/ms143504.aspx).</span></span>  
  
 <span data-ttu-id="9d4c5-109">下表將摘要說明用於這個最低權限組態範例的三個帳戶。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-109">The following table summarizes the three accounts used in this example of a minimum privileged configuration.</span></span>  
  
|<span data-ttu-id="9d4c5-110">範圍</span><span class="sxs-lookup"><span data-stu-id="9d4c5-110">Scope</span></span>|<span data-ttu-id="9d4c5-111">名稱</span><span class="sxs-lookup"><span data-stu-id="9d4c5-111">Name</span></span>|  
|-----------|----------|  
|<span data-ttu-id="9d4c5-112">SharePoint 管理員帳戶</span><span class="sxs-lookup"><span data-stu-id="9d4c5-112">SharePoint Administrator account</span></span>|<span data-ttu-id="9d4c5-113">**SPAdmin**</span><span class="sxs-lookup"><span data-stu-id="9d4c5-113">**SPAdmin**</span></span>|  
|<span data-ttu-id="9d4c5-114">SharePoint 伺服器陣列帳戶</span><span class="sxs-lookup"><span data-stu-id="9d4c5-114">SharePoint Farm account</span></span>|<span data-ttu-id="9d4c5-115">**SPFarm**</span><span class="sxs-lookup"><span data-stu-id="9d4c5-115">**SPFarm**</span></span>|  
|<span data-ttu-id="9d4c5-116">Analysis Services 服務帳戶</span><span class="sxs-lookup"><span data-stu-id="9d4c5-116">Analysis Services service account</span></span>|<span data-ttu-id="9d4c5-117">**SPsvc**</span><span class="sxs-lookup"><span data-stu-id="9d4c5-117">**SPsvc**</span></span>|  
  
### <a name="the-sharepoint-administrator-account-spadmin"></a><span data-ttu-id="9d4c5-118">SharePoint 管理員帳戶 (SpAdmin)</span><span class="sxs-lookup"><span data-stu-id="9d4c5-118">The SharePoint Administrator account (SpAdmin)</span></span>  
 <span data-ttu-id="9d4c5-119">**SPAdmin** 是您用來安裝和設定伺服器陣列的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-119">**SPAdmin** is a domain account you use to install and configure the farm.</span></span> <span data-ttu-id="9d4c5-120">這是用來執行 SharePoint 設定向導和適用于 SharePoint 2013 的 PowerPivot 設定工具的帳戶。 **SPAdmin**帳戶是唯一需要本機系統管理員許可權的帳戶。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-120">It is the account used to run the SharePoint Configuration Wizard and the PowerPivot Configuration Tool for SharePoint 2013.The **SPAdmin** account is the only account that requires local Administrator rights.</span></span> <span data-ttu-id="9d4c5-121">執行 PowerPivot 設定工具之前，請將**SPAdmin**帳戶許可權授與 SharePoint 建立內容和設定資料庫的 SQL Server 資料庫實例。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-121">Before running the PowerPivot Configuration tool, grant the **SPAdmin** account privileges to the SQL Server database instance where SharePoint creates content and configuration databases.</span></span> <span data-ttu-id="9d4c5-122">若要在最低權限案例中設定 SPAdmin 帳戶，它必須是 **securityadmin** 和 **dbcreator**角色的成員。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-122">To configure the SPAdmin account in a minimum privilege scenario, it should be a member of the roles **securityadmin** and **dbcreator**.</span></span>  
  
### <a name="the-farm-account-spfarm"></a><span data-ttu-id="9d4c5-123">伺服器陣列帳戶 (SPFarm)</span><span class="sxs-lookup"><span data-stu-id="9d4c5-123">The Farm account (SPFarm)</span></span>  
 <span data-ttu-id="9d4c5-124">**SPFarm** 是 SharePoint Timer Service 和管理中心 Web 應用程式用來存取 SharePoint 內容資料庫的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-124">**SPFarm** is a domain account that the SharePoint Timer service and the web application for Central Administration use to access the SharePoint content database.</span></span> <span data-ttu-id="9d4c5-125">這個帳戶不需要是本機系統管理員。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-125">This account does not need to be a local administrator.</span></span> <span data-ttu-id="9d4c5-126">[SharePoint 組態精靈] 會授與後端 SQL Server 資料庫的適當最低權限。最低 SQL Server 權限組態就是 **securityadmin** 和 **dbcreator**角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-126">The SharePoint configuration wizard grants the proper minimal privilege in the back-end SQL Server database.The minimum SQL Server privilege configuration is membership in the roles **securityadmin** and **dbcreator**.</span></span>  
  
### <a name="the-service-account-for-powerpivot-service-spsvc"></a><span data-ttu-id="9d4c5-127">PowerPivot 服務的服務帳戶 (SPsvc)</span><span class="sxs-lookup"><span data-stu-id="9d4c5-127">The Service Account for PowerPivot Service (SPsvc)</span></span>  
 <span data-ttu-id="9d4c5-128">如果您沒有在執行 PowerPivot 組態工具之前設定新的 SharePoint 伺服器陣列，則 PowerPivot 組態工具預設將建立下列項目：</span><span class="sxs-lookup"><span data-stu-id="9d4c5-128">If a new SharePoint farm is not configured before you run the PowerPivot Configuration tool, then by default the PowerPivot Configuration tool will create the following:</span></span>  
  
-   <span data-ttu-id="9d4c5-129">PowerPivot 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-129">PowerPivot Service application.</span></span>  
  
-   <span data-ttu-id="9d4c5-130">Excel Services 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-130">Excel Services application.</span></span>  
  
-   <span data-ttu-id="9d4c5-131">安全存放應用程式。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-131">Secure Store application.</span></span>  
  
 <span data-ttu-id="9d4c5-132">PowerPivot 組態工具會在預設應用程式集區中設定這三個服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-132">The PowerPivot configuration tool configures all three of the service applications in the default application pool.</span></span> <span data-ttu-id="9d4c5-133">該應用程式集區通常設定為以 SPFarm 帳戶的身分執行，這個帳戶可存取服務帳戶不需要的許多資源。若要讓環境成為最低權限的環境，請設定要由適當應用程式集區和 Web 應用程式使用的新網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-133">That application pool is typically configured to run as the SPFarm account, which has access to many resources that a service account does not require.To make the environment a minimum-privileged environment, configure a new domain account to be use by the appropriate application pool and web application.</span></span>  
  
 <span data-ttu-id="9d4c5-134">**若要建立要當做 SharePoint 服務帳戶使用的新網域帳戶 SPsvc：**</span><span class="sxs-lookup"><span data-stu-id="9d4c5-134">**To create a new domain account SPsvc to be used as a SharePoint Service account:**</span></span>  
  
1.  <span data-ttu-id="9d4c5-135">在 SharePoint 管理中心內，按一下 [**安全性**]。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-135">In SharePoint Central Administration, click **Security**.</span></span>  
  
2.  <span data-ttu-id="9d4c5-136">按一下 [**設定服務帳戶**]</span><span class="sxs-lookup"><span data-stu-id="9d4c5-136">Click **Configure Service Accounts**</span></span>  
  
3.  <span data-ttu-id="9d4c5-137">按一下 [**註冊新的受管理帳戶**]。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-137">Click **Register new managed account**.</span></span>  
  
 <span data-ttu-id="9d4c5-138">**SPSvc** 帳戶沒有任何本機系統管理員權限，而且 SPsvc 沒有 SharePoint 資料庫的任何權限。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-138">The **SPSvc** account has no local administrator privileges and SPsvc will not have any privileges in the SharePoint database.</span></span> <span data-ttu-id="9d4c5-139">SPsvc 所需的唯一權限就是 Analysis Services 之 PowerPivot 執行個體的管理權限。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-139">The only privileges SPsvc requires is administrative rights to the PowerPivot Instance of the Analysis Services.</span></span>  
  
 <span data-ttu-id="9d4c5-140">**若要將適當的應用程式集區設定為使用 SPsvc 帳戶：**</span><span class="sxs-lookup"><span data-stu-id="9d4c5-140">**To configure the appropriate application pool to use the SPsvc account :**</span></span>  
  
1.  <span data-ttu-id="9d4c5-141">在 SharePoint 管理中心內，按一下 [**安全性**]。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-141">In SharePoint Central Administration, click **Security**.</span></span>  
  
2.  <span data-ttu-id="9d4c5-142">按一下 [**設定服務帳戶**]。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-142">Click **Configure Service Accounts**.</span></span>  
  
3.  <span data-ttu-id="9d4c5-143">選取 PowerPivot 服務應用程式所使用的服務應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-143">Select the service application pool used by the PowerPivot Service application.</span></span> <span data-ttu-id="9d4c5-144">然後，選取 SPSvc 帳戶。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-144">Then select the SPSvc account.</span></span>  
  
 <span data-ttu-id="9d4c5-145">**若要使用 PowerShell，將存取權授與 Web 應用程式：**</span><span class="sxs-lookup"><span data-stu-id="9d4c5-145">**To Grant access to the web application with PowerShell:**</span></span>  
  
1.  <span data-ttu-id="9d4c5-146">使用系統管理員權限來執行 SharePoint 2013 管理命令介面。</span><span class="sxs-lookup"><span data-stu-id="9d4c5-146">Run the SharePoint 2013 Management Shell with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="9d4c5-147">執行下列 PowerShell 程式碼：</span><span class="sxs-lookup"><span data-stu-id="9d4c5-147">Run the following PowerShell code:</span></span>  
  
    ```powershell
    $webApp = Get-SPWebApplication "http://<servername>"  
    $webApp.GrantAccessToProcessIdentity("DOMAIN\<ServiceAccountName>")
    ```  
