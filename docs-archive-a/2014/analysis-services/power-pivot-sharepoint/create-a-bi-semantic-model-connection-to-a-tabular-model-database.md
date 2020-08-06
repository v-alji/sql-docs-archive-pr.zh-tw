---
title: 建立與表格式模型資料庫的 BI 語義模型連接 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 69b306f6-ee8a-44d2-8f51-0cad2c0bc135
author: minewiskan
ms.author: owend
ms.openlocfilehash: 42b4281050b8672891fc01e8bbeb4b3bc1920c94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598577"
---
# <a name="create-a-bi-semantic-model-connection-to-a-tabular-model-database"></a><span data-ttu-id="43b47-102">建立與表格式模型資料庫的 BI 語意模型連接</span><span class="sxs-lookup"><span data-stu-id="43b47-102">Create a BI Semantic Model Connection to a Tabular Model Database</span></span>
  <span data-ttu-id="43b47-103">使用本主題的資訊可設定 BI 語意模型連接，重新導向至 SharePoint 伺服器陣列外部的 Analysis Services 執行個體上執行的表格式模型資料庫。</span><span class="sxs-lookup"><span data-stu-id="43b47-103">Use the information in this topic to set up a BI semantic model connection that redirects to a tabular model database running on an Analysis Services instance outside the SharePoint farm.</span></span>  
  
 <span data-ttu-id="43b47-104">在您建立 BI 語意模型連接並且設定 SharePoint 和 Analysis Services 權限之後，人們可以將其當做 Excel 或 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 報表的資料來源使用。</span><span class="sxs-lookup"><span data-stu-id="43b47-104">After you create a BI semantic model connection and configure SharePoint and Analysis Services permissions, people can use it as a data source for Excel or [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] reports.</span></span>  
  
 <span data-ttu-id="43b47-105">本主題包含下列各節。</span><span class="sxs-lookup"><span data-stu-id="43b47-105">This topic includes the following sections.</span></span> <span data-ttu-id="43b47-106">請依指定順序執行每個工作。</span><span class="sxs-lookup"><span data-stu-id="43b47-106">Perform each task in the order given.</span></span>  
  
 [<span data-ttu-id="43b47-107">檢閱必要條件</span><span class="sxs-lookup"><span data-stu-id="43b47-107">Review Prerequisites</span></span>](#bkmk_prereq)  
  
 [<span data-ttu-id="43b47-108">授與 Analysis Services 管理權限給共用服務應用程式</span><span class="sxs-lookup"><span data-stu-id="43b47-108">Grant Analysis Services Administrative Permissions to Shared Service Applications</span></span>](#bkmk_ssas)  
  
 [<span data-ttu-id="43b47-109">授與表格式模型資料庫的讀取權限</span><span class="sxs-lookup"><span data-stu-id="43b47-109">Grant Read Permissions on the Tabular Model Database</span></span>](#bkmk_BISM)  
  
 [<span data-ttu-id="43b47-110">建立與表格式模型資料庫的 BI 語義模型連接</span><span class="sxs-lookup"><span data-stu-id="43b47-110">Create a BI Semantic Model Connection to a Tabular Model Database</span></span>](#bkmk_connect)  
  
 [<span data-ttu-id="43b47-111">設定 BI 語意模型連接的 SharePoint 權限</span><span class="sxs-lookup"><span data-stu-id="43b47-111">Configure SharePoint permissions on the BI Semantic Model Connection</span></span>](#bkmk_permissions)  
  
 [<span data-ttu-id="43b47-112">後續步驟</span><span class="sxs-lookup"><span data-stu-id="43b47-112">Next Steps</span></span>](#bkmk_next)  
  
##  <a name="review-prerequisites"></a><a name="bkmk_prereq"></a><span data-ttu-id="43b47-113">審查必要條件</span><span class="sxs-lookup"><span data-stu-id="43b47-113">Review Prerequisites</span></span>  
 <span data-ttu-id="43b47-114">您必須有 [參與] 以上權限，才能建立 BI 語意模型連接檔案。</span><span class="sxs-lookup"><span data-stu-id="43b47-114">You must have Contribute permissions or above to create a BI semantic model connection file.</span></span>  
  
 <span data-ttu-id="43b47-115">您必須具有支援 BI 語意模型連接內容類型的文件庫。</span><span class="sxs-lookup"><span data-stu-id="43b47-115">You must have a library that supports the BI semantic model connection content type.</span></span> <span data-ttu-id="43b47-116">如需詳細資訊，請參閱[將 BI 語義模型連接內容類型新增至程式庫 &#40;PowerPivot for SharePoint&#41;](add-bi-semantic-model-connection-content-type-to-library.md)。</span><span class="sxs-lookup"><span data-stu-id="43b47-116">For more information, see [Add a BI Semantic Model Connection Content Type to a Library &#40;PowerPivot for SharePoint&#41;](add-bi-semantic-model-connection-content-type-to-library.md).</span></span>  
  
 <span data-ttu-id="43b47-117">您必須知道要設定 BI 語意模型連接的伺服器和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="43b47-117">You must know the server and database name for which you are setting up a BI semantic model connection.</span></span> <span data-ttu-id="43b47-118">Analysis Services 必須設定表格式模式。</span><span class="sxs-lookup"><span data-stu-id="43b47-118">Analysis Services must be configured for tabular mode.</span></span> <span data-ttu-id="43b47-119">在伺服器上執行的資料庫必須是表格式模型資料庫。</span><span class="sxs-lookup"><span data-stu-id="43b47-119">Databases running on the server must be tabular model databases.</span></span> <span data-ttu-id="43b47-120">如需如何檢查伺服器模式的指示，請參閱 [判斷 Analysis Services 執行個體的伺服器模式](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="43b47-120">For instructions on how to check for server mode, see [Determine the Server Mode of an Analysis Services Instance](../instances/determine-the-server-mode-of-an-analysis-services-instance.md).</span></span>  
  
 <span data-ttu-id="43b47-121">在某些情況下，SharePoint 環境中的共用服務必須有 Analysis Services 執行個體的管理權限。</span><span class="sxs-lookup"><span data-stu-id="43b47-121">In certain scenarios, the shared services in a SharePoint environment must have administrative permissions on the Analysis Services instance.</span></span> <span data-ttu-id="43b47-122">這些服務包括 PowerPivot 服務應用程式、Reporting Services 服務應用程式和 PerformancePoint 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="43b47-122">These services include PowerPivot service applications, Reporting Services service applications, and PerformancePoint service applications.</span></span> <span data-ttu-id="43b47-123">在授與管理權限之前，您必須知道這些服務應用程式的識別。</span><span class="sxs-lookup"><span data-stu-id="43b47-123">Before you can grant administrative permissions, you must know the identity of these service applications.</span></span> <span data-ttu-id="43b47-124">您可以使用管理中心判斷識別。</span><span class="sxs-lookup"><span data-stu-id="43b47-124">You can use Central Administration to determine the identity.</span></span>  
  
 <span data-ttu-id="43b47-125">您必須是 SharePoint 服務管理員，才能在管理中心檢視安全性資訊。</span><span class="sxs-lookup"><span data-stu-id="43b47-125">You must be a SharePoint service administrator to view security information in Central Administration.</span></span>  
  
 <span data-ttu-id="43b47-126">您必須是 Analysis Services 系統管理員，才能在 Management Studio 中授與管理權限。</span><span class="sxs-lookup"><span data-stu-id="43b47-126">You must be an Analysis Services system administrator to grant administrative rights in Management Studio.</span></span>  
  
 <span data-ttu-id="43b47-127">PowerPivot for SharePoint 必須透過使用傳統驗證模式的 Web 應用程式來存取。</span><span class="sxs-lookup"><span data-stu-id="43b47-127">PowerPivot for SharePoint must be accessed via web applications that use classic authentication mode.</span></span> <span data-ttu-id="43b47-128">與外部資料來源的 BI 語意模型連接相依於傳統模式登入。</span><span class="sxs-lookup"><span data-stu-id="43b47-128">BI semantic model connections to external data sources have a dependency on classic mode sign-in.</span></span> <span data-ttu-id="43b47-129">如需詳細資訊，請參閱[PowerPivot 驗證和授權](power-pivot-authentication-and-authorization.md)。</span><span class="sxs-lookup"><span data-stu-id="43b47-129">For more information, see [PowerPivot Authentication and Authorization](power-pivot-authentication-and-authorization.md).</span></span>  
  
 <span data-ttu-id="43b47-130">參與連接順序的所有電腦和使用者都必須是在相同網域或受信任網域 (雙向信任) 中。</span><span class="sxs-lookup"><span data-stu-id="43b47-130">All computers and users that participate in the connection sequence must be in the same domain or trusted domain (two-way trust).</span></span>  
  
##  <a name="grant-analysis-services-administrative-permissions-to-shared-service-applications"></a><a name="bkmk_ssas"></a><span data-ttu-id="43b47-131">授與 Analysis Services 共用服務應用程式的系統管理許可權</span><span class="sxs-lookup"><span data-stu-id="43b47-131">Grant Analysis Services Administrative Permissions to Shared Service Applications</span></span>  
 <span data-ttu-id="43b47-132">從 SharePoint 到 Analysis Services 伺服器上表格式模型資料庫的連接有時是由共用服務代表要求資料的使用者所建立。</span><span class="sxs-lookup"><span data-stu-id="43b47-132">Connections that originate from SharePoint to a tabular model database on an Analysis Services server are sometimes made by a shared service on behalf of the user requesting the data.</span></span> <span data-ttu-id="43b47-133">發出要求的服務可能是 PowerPivot 服務應用程式、Reporting Services 服務應用程式或 PerformancePoint 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="43b47-133">The service making the request might be a PowerPivot service application, a Reporting Services service application, or a PerformancePoint service application.</span></span> <span data-ttu-id="43b47-134">為了要讓連接成功，此服務必須擁有 Analysis Services 伺服器的管理權限。</span><span class="sxs-lookup"><span data-stu-id="43b47-134">In order for the connection to succeed, the service must have administrative permissions on the Analysis Services server.</span></span> <span data-ttu-id="43b47-135">在 Analysis Services 中，只允許管理員代表其他使用者建立模擬連接。</span><span class="sxs-lookup"><span data-stu-id="43b47-135">In Analysis Services, only an administrator is allowed to make an impersonated connection on behalf of another user.</span></span>  
  
 <span data-ttu-id="43b47-136">在下列情況下使用連接時需要管理權限：</span><span class="sxs-lookup"><span data-stu-id="43b47-136">Administrative permissions are necessary when the connection is used under these conditions:</span></span>  
  
-   <span data-ttu-id="43b47-137">在 BI 語意模型連接檔案的設定期間驗證連接資訊時。</span><span class="sxs-lookup"><span data-stu-id="43b47-137">When verifying the connection information during the configuration of a BI semantic model connection file.</span></span>  
  
-   <span data-ttu-id="43b47-138">當使用 BI 語意模型連接啟動 Power View 報表時。</span><span class="sxs-lookup"><span data-stu-id="43b47-138">When starting a Power View report using a BI semantic model connection.</span></span>  
  
-   <span data-ttu-id="43b47-139">當使用 BI 語意模型連接擴展 PerformancePoint Web 組件時。</span><span class="sxs-lookup"><span data-stu-id="43b47-139">When populating a PerformancePoint web part using a BI semantic model connection.</span></span>  
  
 <span data-ttu-id="43b47-140">為確保這些行為如預期執行，請將 Analysis Services 執行個體的管理權限授與每個服務識別。</span><span class="sxs-lookup"><span data-stu-id="43b47-140">To ensure these behaviors perform as expected, grant to each service identity administrative permissions on the Analysis Services instance.</span></span> <span data-ttu-id="43b47-141">請使用下列指示來授與必要權限。</span><span class="sxs-lookup"><span data-stu-id="43b47-141">Use the following instructions to grant the necessary permission.</span></span>  
  
 <span data-ttu-id="43b47-142">**將服務識別加入至伺服器管理員角色**</span><span class="sxs-lookup"><span data-stu-id="43b47-142">**Add service identities to the Server Administrator role**</span></span>  
  
1.  <span data-ttu-id="43b47-143">在 SQL Server Management Studio 中，連接到 Analysis Services 執行個體。</span><span class="sxs-lookup"><span data-stu-id="43b47-143">In SQL Server Management Studio, connect to the Analysis Services instance.</span></span>  
  
2.  <span data-ttu-id="43b47-144">以滑鼠右鍵按一下伺服器名稱，然後選取 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="43b47-144">Right-click the server name and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="43b47-145">按一下 [安全性]\*\*\*\*，然後按一下 [加入]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="43b47-145">Click **Security**, and then click **Add**.</span></span> <span data-ttu-id="43b47-146">輸入用來執行服務應用程式的 Windows 使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="43b47-146">Enter the Windows user account that is used to run the service application.</span></span>  
  
     <span data-ttu-id="43b47-147">您可以使用管理中心判斷識別。</span><span class="sxs-lookup"><span data-stu-id="43b47-147">You can use Central Administration to determine the identity.</span></span> <span data-ttu-id="43b47-148">在 [安全性] 區段中開啟 [設定服務帳戶]\*\*\*\*，以檢視哪一個 Windows 帳戶與每一個應用程式所使用的服務應用程式集區相關聯，然後依照本主題所提供的指示將管理權限授與帳戶。</span><span class="sxs-lookup"><span data-stu-id="43b47-148">In the Security section, open the **Configure service accounts** to view which Windows account is associated with the service application pool used for each application, then follow the instructions provided in this topic to grant the account administrative permissions.</span></span>  
  
##  <a name="grant-read-permissions-on-the-tabular-model-database"></a><a name="bkmk_BISM"></a> <span data-ttu-id="43b47-149">授與表格式模型資料庫的讀取權限</span><span class="sxs-lookup"><span data-stu-id="43b47-149">Grant Read Permissions on the Tabular Model Database</span></span>  
 <span data-ttu-id="43b47-150">由於資料庫在伺服器陣列外部的伺服器上執行，因此在設定連接的過程中，將會包含授與後端 Analysis Services 伺服器的資料庫使用者權限。</span><span class="sxs-lookup"><span data-stu-id="43b47-150">Because the database is running on a server that is external to the farm, part of setting up your connections will include granting database user permissions on the backend Analysis Services server.</span></span> <span data-ttu-id="43b47-151">Analysis Services 會使用以角色為基礎的權限模型。</span><span class="sxs-lookup"><span data-stu-id="43b47-151">Analysis Services uses a role-based permission model.</span></span> <span data-ttu-id="43b47-152">連接到模型資料庫的使用者必須使用「讀取」權限或更高的權限，透過授與讀取權限給其成員的角色來進行。</span><span class="sxs-lookup"><span data-stu-id="43b47-152">Users who connect to model databases must do so with Read permissions or higher, through a role that grants read access to its members.</span></span>  
  
 <span data-ttu-id="43b47-153">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中建立模型時會定義角色 (有時也會定義角色成員資格)。</span><span class="sxs-lookup"><span data-stu-id="43b47-153">Roles, and sometimes role membership, are defined when the model is created in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="43b47-154">您不能使用 SQL Server Management Studio 建立角色，但是可以用來將成員加入至已經定義的角色。</span><span class="sxs-lookup"><span data-stu-id="43b47-154">You cannot use SQL Server Management Studio to create roles, but you can use it to add members to a role that is already defined.</span></span> <span data-ttu-id="43b47-155">如需建立角色的詳細資訊，請參閱[建立及管理角色 &#40;SSAS 表格式&#41;](../tabular-models/roles-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="43b47-155">For more information about creating roles, see [Create and Manage Roles &#40;SSAS Tabular&#41;](../tabular-models/roles-ssas-tabular.md).</span></span>  
  
#### <a name="assign-role-membership"></a><span data-ttu-id="43b47-156">指派角色成員資格</span><span class="sxs-lookup"><span data-stu-id="43b47-156">Assign role membership</span></span>  
  
1.  <span data-ttu-id="43b47-157">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，連接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體，然後在 [物件總管] 中展開資料庫，再展開 [角色]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="43b47-157">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], expand the database in Object Explorer, and then expand **Roles**.</span></span> <span data-ttu-id="43b47-158">您應該看到已定義的角色。</span><span class="sxs-lookup"><span data-stu-id="43b47-158">You should see a role that is already defined.</span></span> <span data-ttu-id="43b47-159">如果角色不存在，請與模型的作者聯繫，並要求加入角色。</span><span class="sxs-lookup"><span data-stu-id="43b47-159">If a role does not exist, contact the author of the model and request the addition or a role.</span></span> <span data-ttu-id="43b47-160">在 Management Studio 中看到角色之前，必須重新部署模型。</span><span class="sxs-lookup"><span data-stu-id="43b47-160">The model must be redeployed before the role is visible in Management Studio.</span></span>  
  
2.  <span data-ttu-id="43b47-161">以滑鼠右鍵按一下角色，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="43b47-161">Right-click the role, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="43b47-162">在 [成員資格] 頁面中，加入需要存取權的 Windows 群組和使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="43b47-162">In the Membership page, add the Windows group and user accounts that require access.</span></span>  
  
##  <a name="create-a-bi-semantic-model-connection-to-a-tabular-model-database"></a><a name="bkmk_connect"></a> <span data-ttu-id="43b47-163">建立與表格式模型資料庫的 BI 語意模型連接</span><span class="sxs-lookup"><span data-stu-id="43b47-163">Create a BI Semantic Model Connection to a Tabular Model Database</span></span>  
 <span data-ttu-id="43b47-164">在 Analysis Services 中設定權限之後，您可以返回 SharePoint 並建立 BI 語意模型連接。</span><span class="sxs-lookup"><span data-stu-id="43b47-164">After you set permissions in Analysis Services, you can return to SharePoint and create a BI semantic model connection.</span></span>  
  
1.  <span data-ttu-id="43b47-165">在包含 BI 語意模型連接的文件庫中，按一下 SharePoint 功能區上的 [文件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="43b47-165">In the library that will contain the BI semantic model connection, click **Documents** on the SharePoint ribbon.</span></span>  
  
2.  <span data-ttu-id="43b47-166">按一下 [新文件] 上的向下箭號，然後選取 [BI 語意模型連接檔案]\*\*\*\*，開啟 [新增 BI 語意模型連接] 頁面。</span><span class="sxs-lookup"><span data-stu-id="43b47-166">Click the down arrow on New Document, and select **BI Semantic Model Connection File** to open the New BI Semantic Model Connection page.</span></span>  
  
3.  <span data-ttu-id="43b47-167">同時設定 [伺服器]\*\*\*\* 和 [資料庫]\*\*\*\* 屬性。</span><span class="sxs-lookup"><span data-stu-id="43b47-167">Set both **Server** and **Database** properties.</span></span> <span data-ttu-id="43b47-168">如果您不確定資料庫名稱，請使用 SQL Server Management Studio 檢視在伺服器上部署之資料庫的清單。</span><span class="sxs-lookup"><span data-stu-id="43b47-168">If you are unsure of the database name, use SQL Server Management Studio to view a list of the databases that are deployed on the server.</span></span>  
  
     <span data-ttu-id="43b47-169">[伺服器名稱]\*\*\*\* 可以是伺服器的網路名稱、IP 位址或完整網域名稱 (例如 myserver.mydomain.corp.adventure-works.com)。</span><span class="sxs-lookup"><span data-stu-id="43b47-169">**Server name** is either the network name of the server, the IP address, or the fully qualified domain name (for example, myserver.mydomain.corp.adventure-works.com).</span></span> <span data-ttu-id="43b47-170">如果伺服器當做具名執行個體安裝，請使用下列格式輸入伺服器名稱：computername\instancename。</span><span class="sxs-lookup"><span data-stu-id="43b47-170">If the server is installed as a named instance, enter the server name in this format: computername\instancename.</span></span>  
  
     <span data-ttu-id="43b47-171">[資料庫]\*\*\*\* 必須是目前可以在伺服器上使用的表格式資料庫。</span><span class="sxs-lookup"><span data-stu-id="43b47-171">**Database** must be a tabular database that is currently available on the server.</span></span> <span data-ttu-id="43b47-172">請勿指定另一個 BI 語意模型連接檔案、Office 資料連線 (.odc) 檔案、Analysis Services OLAP 資料庫或 PowerPivot 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="43b47-172">Do not specify another BI semantic model connection file, an Office Data Connection (.odc) file, an Analysis Services OLAP database, or a PowerPivot workbook.</span></span> <span data-ttu-id="43b47-173">若要取得資料庫名稱，您可以使用 Management Studio 連接到伺服器並檢視可用資料庫的清單。</span><span class="sxs-lookup"><span data-stu-id="43b47-173">To get the database name, you can use Management Studio to connect to the server and view the list of available databases.</span></span> <span data-ttu-id="43b47-174">使用資料庫的屬性頁可確保您擁有正確的名稱。</span><span class="sxs-lookup"><span data-stu-id="43b47-174">Use the property page of the database to ensure you have the correct name.</span></span>  
  
4.  <span data-ttu-id="43b47-175">按一下 [確定]\*\*\*\* 以儲存頁面。</span><span class="sxs-lookup"><span data-stu-id="43b47-175">Click **OK** to save the page.</span></span> <span data-ttu-id="43b47-176">此時，PowerPivot 服務應用程式會驗證該連接。</span><span class="sxs-lookup"><span data-stu-id="43b47-176">At this point, the PowerPivot service application will verify the connection.</span></span>  
  
     <span data-ttu-id="43b47-177">如果連接資訊是正確的，而且您已經將管理權限授與 PowerPivot 服務應用程式，讓它以目前使用者的身分連接到 Analysis Services，驗證就會成功。</span><span class="sxs-lookup"><span data-stu-id="43b47-177">Verification succeeds if the connection information is correct, and you have granted administrative permissions to the PowerPivot service application so that it can connect to Analysis Services as the current user.</span></span>  
  
     <span data-ttu-id="43b47-178">如果連接資訊是錯誤的，或服務應用程式缺少權限，驗證就會失敗。</span><span class="sxs-lookup"><span data-stu-id="43b47-178">Verification fails if the connection information is wrong, or the service application lacks permissions.</span></span> <span data-ttu-id="43b47-179">頁面上會顯示驗證訊息，詢問您是否要儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="43b47-179">A validation message will appear on the page asking whether you want to save the file.</span></span> <span data-ttu-id="43b47-180">如果您知道連接是有效的，還是應該儲存檔案，因為錯誤是缺少權限所致，而不是連接資訊無效。</span><span class="sxs-lookup"><span data-stu-id="43b47-180">If you know that the connection is valid, you should save the file anyway, because the error is the result of missing permissions rather than invalid connection information.</span></span>  
  
     <span data-ttu-id="43b47-181">您可以在 Excel 或 Power View 中使用它來連接到表格式模型資料庫，藉以驗證連接。</span><span class="sxs-lookup"><span data-stu-id="43b47-181">You can verify the connection by using it in Excel or Power View to connect to tabular model database.</span></span> <span data-ttu-id="43b47-182">如果資料來源連接成功，儘管驗證警告，連接仍然有效。</span><span class="sxs-lookup"><span data-stu-id="43b47-182">If the data source connection succeeds, the connection is valid despite the verification warning.</span></span>  
  
##  <a name="configure-sharepoint-permissions-on-the-bi-semantic-model-connection"></a><a name="bkmk_permissions"></a><span data-ttu-id="43b47-183">設定 BI 語義模型連接的 SharePoint 許可權</span><span class="sxs-lookup"><span data-stu-id="43b47-183">Configure SharePoint permissions on the BI Semantic Model Connection</span></span>  
 <span data-ttu-id="43b47-184">需要有 SharePoint 文件庫中 BI 語意模型連接項目的 [讀取]\*\*\*\* 權限，才能使用 BI 語意模型連接作為 Excel 活頁簿或 Reporting Services 報表的資料來源。</span><span class="sxs-lookup"><span data-stu-id="43b47-184">Ability to use a BI semantic model connection as a data source for an Excel workbook or Reporting Services report requires **Read** permissions on the BI semantic model connection item in a SharePoint library.</span></span> <span data-ttu-id="43b47-185">[讀取] 權限等級包含 [開啟項目]\*\*\*\* 權限，此權限允許將 BI 語意模型連接資訊下載到 Excel 桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="43b47-185">The Read permission level includes the **Open Items** permission that enables downloading BI semantic model connection information to an Excel desktop application.</span></span>  
  
 <span data-ttu-id="43b47-186">有數種方法可以在 SharePoint 中授與權限。</span><span class="sxs-lookup"><span data-stu-id="43b47-186">There are several ways to grant permissions in SharePoint.</span></span> <span data-ttu-id="43b47-187">下列指示說明如何建立具有 [讀取]\*\*\*\* 權限等級、稱為「BISM 使用者」\*\*\*\* 的新群組。</span><span class="sxs-lookup"><span data-stu-id="43b47-187">The following instructions explain how to create a new group called **BISM Users** that have the **Read** permission level.</span></span>  
  
 <span data-ttu-id="43b47-188">您必須是網站擁有者，才能變更權限。</span><span class="sxs-lookup"><span data-stu-id="43b47-188">You must be a site owner to change permissions.</span></span>  
  
1.  <span data-ttu-id="43b47-189">在 [網站動作] 中，按一下 [網站權限]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="43b47-189">In Site Actions, click **Site Permissions**.</span></span>  
  
2.  <span data-ttu-id="43b47-190">按一下 [建立群組]\*\*\*\*，並將新群組命名為「BISM 使用者」\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="43b47-190">Click **Create Group** and name the new group **BISM Users**.</span></span>  
  
3.  <span data-ttu-id="43b47-191">選擇 [讀取]\*\*\*\* 權限等級，然後按一下 [建立]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="43b47-191">Choose the **Read** permission level and click **Create**.</span></span>  
  
4.  <span data-ttu-id="43b47-192">選取 [人員與群組] 中的 [BISM 使用者]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="43b47-192">Select **BISM Users** in People and Groups.</span></span>  
  
5.  <span data-ttu-id="43b47-193">指向 [新增]，按一下 [加入使用者]\*\*\*\*，然後加入使用者或群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="43b47-193">Point to New, click **Add Users**, and then add user or group accounts.</span></span>  
  
     <span data-ttu-id="43b47-194">這些使用者和群組現在具有整個網站 (包括從網站層級繼承權限的所有文件庫和清單) 的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="43b47-194">These users and groups will now have Read permissions throughout the site, including all libraries and lists that inherit permissions from the site level.</span></span> <span data-ttu-id="43b47-195">如果這些權限太高，您可以從特定文件庫、清單或項目中選擇地移除此群組。</span><span class="sxs-lookup"><span data-stu-id="43b47-195">If these permissions are too high, you can selectively remove this group from specific libraries, lists, or items.</span></span>  
  
 <span data-ttu-id="43b47-196">若要選擇地在項目層級移除權限，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="43b47-196">To selectively remove permissions at the item level, do the following:</span></span>  
  
1.  <span data-ttu-id="43b47-197">在文件庫中，選取文件。</span><span class="sxs-lookup"><span data-stu-id="43b47-197">In a library, select a document.</span></span> <span data-ttu-id="43b47-198">按一下右下箭頭，然後按一下 [管理權限]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="43b47-198">Click the right down arrow and then click **Manage Permissions**.</span></span>  
  
2.  <span data-ttu-id="43b47-199">根據預設，項目會繼承權限。</span><span class="sxs-lookup"><span data-stu-id="43b47-199">By default, an item inherits permissions.</span></span> <span data-ttu-id="43b47-200">若要變更此文件庫中個別文件的權限，請按一下 [停止繼承權限]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="43b47-200">To change the permissions of individual documents in this library, click **Stop Inheriting Permissions**.</span></span>  
  
3.  <span data-ttu-id="43b47-201">選取 [BISM 使用者]\*\*\*\* 旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="43b47-201">Select the checkbox next to **BISM Users**.</span></span>  
  
4.  <span data-ttu-id="43b47-202">按一下 [移除使用者權限]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="43b47-202">Click **Remove User Permissions**.</span></span>  
  
##  <a name="next-steps"></a><a name="bkmk_next"></a> <span data-ttu-id="43b47-203">後續步驟</span><span class="sxs-lookup"><span data-stu-id="43b47-203">Next Steps</span></span>  
 <span data-ttu-id="43b47-204">在建立 BI 語意模型連接並且確保其安全之後，可以將此連接指定為資料來源。</span><span class="sxs-lookup"><span data-stu-id="43b47-204">After you create and secure a BI semantic model connection, you can specify it as a data source.</span></span> <span data-ttu-id="43b47-205">如需詳細資訊，請參閱 [在 Excel 或 Reporting Services 使用 BI 語意模型連接](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="43b47-205">For more information, see [Use a BI Semantic Model Connection in Excel or Reporting Services](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43b47-206">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43b47-206">See Also</span></span>  
 <span data-ttu-id="43b47-207">[PowerPivot BI 語義模型連接 &#40;. bism&#41;](power-pivot-bi-semantic-model-connection-bism.md) </span><span class="sxs-lookup"><span data-stu-id="43b47-207">[PowerPivot BI Semantic Model Connection &#40;.bism&#41;](power-pivot-bi-semantic-model-connection-bism.md) </span></span>  
 [<span data-ttu-id="43b47-208">建立與 PowerPivot 活頁簿的 BI 語意模型連接</span><span class="sxs-lookup"><span data-stu-id="43b47-208">Create a BI Semantic Model Connection to a PowerPivot Workbook</span></span>](create-a-bi-semantic-model-connection-to-a-power-pivot-workbook.md)  
  
  
