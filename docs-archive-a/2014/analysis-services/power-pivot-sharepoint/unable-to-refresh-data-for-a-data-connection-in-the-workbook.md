---
title: 無法重新整理活頁簿中資料連接的資料。 請再試一次或連絡系統管理員。 下列連接無法重新整理： PowerPivot 資料 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0f6fd52d-ac72-43e3-aa08-05a2d2bb873d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9c25c2597bbc7aa16fb8b66d4ffddbf0df14515e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705533"
---
# <a name="unable-to-refresh-data-for-a-data-connection-in-the-workbook-try-again-or-contact-your-system-administrator-the-following-connections-failed-to-refresh-powerpivot-data"></a><span data-ttu-id="7580e-104">無法重新整理活頁簿中資料連接的資料。</span><span class="sxs-lookup"><span data-stu-id="7580e-104">Unable to refresh data for a data connection in the workbook.</span></span> <span data-ttu-id="7580e-105">請再試一次或連絡系統管理員。</span><span class="sxs-lookup"><span data-stu-id="7580e-105">Try again or contact your system administrator.</span></span> <span data-ttu-id="7580e-106">下列連接無法重新整理：PowerPivot 資料</span><span class="sxs-lookup"><span data-stu-id="7580e-106">The following connections failed to refresh: PowerPivot Data</span></span>
  <span data-ttu-id="7580e-107">如果是包含 PowerPivot 資料的 Excel 活頁簿，Excel Services 會在提交連接要求至 PowerPivot 伺服器而且該要求失敗時，傳回這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="7580e-107">For Excel workbooks that contain PowerPivot data, Excel Services returns this error if it submits a connection request to a PowerPivot server and the request fails.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7580e-108">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7580e-108">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7580e-109">適用於：</span><span class="sxs-lookup"><span data-stu-id="7580e-109">Applies to:</span></span>|<span data-ttu-id="7580e-110">PowerPivot for SharePoint 安裝</span><span class="sxs-lookup"><span data-stu-id="7580e-110">PowerPivot for SharePoint installation</span></span>|  
|<span data-ttu-id="7580e-111">產品版本</span><span class="sxs-lookup"><span data-stu-id="7580e-111">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="7580e-112">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7580e-112">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="7580e-113">原因</span><span class="sxs-lookup"><span data-stu-id="7580e-113">Cause</span></span>|<span data-ttu-id="7580e-114">請參閱下文。</span><span class="sxs-lookup"><span data-stu-id="7580e-114">See below.</span></span>|  
|<span data-ttu-id="7580e-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7580e-115">Message Text</span></span>|<span data-ttu-id="7580e-116">無法重新整理活頁簿中資料連接的資料。</span><span class="sxs-lookup"><span data-stu-id="7580e-116">Unable to refresh data for a data connection in the workbook.</span></span> <span data-ttu-id="7580e-117">請再試一次或連絡系統管理員。</span><span class="sxs-lookup"><span data-stu-id="7580e-117">Try again or contact your system administrator.</span></span> <span data-ttu-id="7580e-118">下列連接無法重新整理：PowerPivot 資料</span><span class="sxs-lookup"><span data-stu-id="7580e-118">The following connections failed to refresh: PowerPivot Data</span></span>|  
  
## <a name="explanation-and-resolution"></a><span data-ttu-id="7580e-119">說明與解決方法</span><span class="sxs-lookup"><span data-stu-id="7580e-119">Explanation and Resolution</span></span>  
 <span data-ttu-id="7580e-120">Excel Services 無法連接或載入 PowerPivot 資料。</span><span class="sxs-lookup"><span data-stu-id="7580e-120">Excel Services cannot connect to or load the PowerPivot data.</span></span> <span data-ttu-id="7580e-121">發生此錯誤的條件包括：</span><span class="sxs-lookup"><span data-stu-id="7580e-121">Conditions that cause this error to occur include the following:</span></span>  
  
 <span data-ttu-id="7580e-122">**案例 1：未啟動服務**</span><span class="sxs-lookup"><span data-stu-id="7580e-122">**Scenario 1: Service is not started**</span></span>  
  
 <span data-ttu-id="7580e-123">未啟動 SQL Server Analysis Services (PowerPivot) 執行個體。</span><span class="sxs-lookup"><span data-stu-id="7580e-123">The SQL Server Analysis Services (PowerPivot) instance is not started.</span></span> <span data-ttu-id="7580e-124">過期的密碼使伺服器停止執行。</span><span class="sxs-lookup"><span data-stu-id="7580e-124">An expired password will cause the service to stop running.</span></span> <span data-ttu-id="7580e-125">如需變更密碼的詳細資訊，請參閱[設定 PowerPivot 服務帳戶](configure-power-pivot-service-accounts.md)和[啟動或停止 PowerPivot for SharePoint 伺服器](start-or-stop-a-power-pivot-for-sharepoint-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7580e-125">For more information about changing the password, see [Configure PowerPivot Service Accounts](configure-power-pivot-service-accounts.md) and [Start or Stop a PowerPivot for SharePoint Server](start-or-stop-a-power-pivot-for-sharepoint-server.md).</span></span>  
  
 <span data-ttu-id="7580e-126">**案例 2a：在伺服器上開啟舊版活頁簿**</span><span class="sxs-lookup"><span data-stu-id="7580e-126">**Scenario 2a: Opening an earlier version workbook n the server**</span></span>  
  
 <span data-ttu-id="7580e-127">您嘗試開啟的活頁簿可能是在 SQL Server 2008 R2 版的 PowerPivot for Excel 中建立。</span><span class="sxs-lookup"><span data-stu-id="7580e-127">The workbook you are attempting to open might have been created in the SQL Server 2008 R2 version of PowerPivot for Excel.</span></span> <span data-ttu-id="7580e-128">最有可能是因為資料連接字串中指定的 Analysis Services 資料提供者不存在於處理要求的電腦上。</span><span class="sxs-lookup"><span data-stu-id="7580e-128">Most likely, the Analysis Services data provider that is specified in the data connection string is not present on the computer that is handling the request.</span></span>  
  
 <span data-ttu-id="7580e-129">如果是這種情況，您會在 ULS 記錄檔中找到此訊息：「重新整理活頁簿 ' ' 中的 ' PowerPivot 資料 ' 失敗」 \<URL to workbook> ，後面接著「無法取得連接」。</span><span class="sxs-lookup"><span data-stu-id="7580e-129">If this is the case, you will find this message in the ULS log: "Refresh failed for 'PowerPivot Data' in the workbook '\<URL to workbook>'", followed by "Unable to get a connection".</span></span>  
  
 <span data-ttu-id="7580e-130">若要判斷活頁簿的版本，您可以在 Excel 開啟它並檢查連接字串中指定的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="7580e-130">To determine the version of the workbook, open it in Excel and check which data provider is specified in the connection string.</span></span> <span data-ttu-id="7580e-131">SQL Server 2008 R2 活頁簿使用 MSOLAP.4 做為其資料提供者。</span><span class="sxs-lookup"><span data-stu-id="7580e-131">A SQL Server 2008 R2 workbook uses MSOLAP.4 as its data provider.</span></span>  
  
 <span data-ttu-id="7580e-132">若要解決此問題，您可以升級活頁簿。</span><span class="sxs-lookup"><span data-stu-id="7580e-132">To work around this issue, you can upgrade the workbook.</span></span> <span data-ttu-id="7580e-133">或者，您也可以在執行 PowerPivot for SharePoint 或 Excel Services 的實體電腦上安裝 SQL Server 2008 R2 版 Analysis Services 的用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="7580e-133">Alternatively, you can install client libraries from the SQL Server 2008 R2 version of Analysis Services on the physical computers running PowerPivot for SharePoint or Excel Services:</span></span>  
  
 [<span data-ttu-id="7580e-134">在 SharePoint 伺服器上安裝 Analysis Services OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="7580e-134">Install the Analysis Services OLE DB Provider on SharePoint Servers</span></span>](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)  
  
 <span data-ttu-id="7580e-135">**案例 2b：在用戶端程式庫版本錯誤的應用程式伺服器上執行 Excel Services**</span><span class="sxs-lookup"><span data-stu-id="7580e-135">**Scenario 2b: Excel Services is running on an application server that has the wrong version of the client libraries**</span></span>  
  
 <span data-ttu-id="7580e-136">根據預設，SharePoint Server 2010 會在執行 Excel Services 的應用程式伺服器上安裝 SQL Server 2008 版的 Analysis Services OLE DB 提供者。</span><span class="sxs-lookup"><span data-stu-id="7580e-136">By default, SharePoint Server 2010 installs the SQL Server 2008 version of the Analysis Services OLE DB provider on application servers that run Excel Services.</span></span> <span data-ttu-id="7580e-137">在支援 PowerPivot 資料存取的伺服器陣列中，執行要求 PowerPivot 資料之應用程式 (例如 Excel Services 和 PowerPivot for SharePoint) 的所有實體電腦上都必須使用更新版本的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="7580e-137">In a farm that supports PowerPivot data access, all physical servers running applications that request PowerPivot data, such as Excel Services and PowerPivot for SharePoint, must use a later version of the data provider.</span></span>  
  
 <span data-ttu-id="7580e-138">執行 PowerPivot for SharePoint 的伺服器會自動取得更新的 OLE DB 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="7580e-138">Servers that run PowerPivot for SharePoint get the updated OLE DB data provider automatically.</span></span> <span data-ttu-id="7580e-139">其他伺服器，例如執行 Excel Services 獨立執行個體但在相同電腦上並沒有 PowerPivot for SharePoint 的應用程式伺服器，則必須先安裝修補程式，以使用較新版的用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="7580e-139">Other servers, such as those running a standalone instance Excel Services without PowerPivot for SharePoint on the same computer, must be patched to use the newer client libraries.</span></span> <span data-ttu-id="7580e-140">如需詳細資訊，請參閱 [在 SharePoint 伺服器上安裝 Analysis Services OLE DB 提供者](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="7580e-140">For more information, see [Install the Analysis Services OLE DB Provider on SharePoint Servers](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).</span></span>  
  
 <span data-ttu-id="7580e-141">**案例 3：網域控制站無法使用**</span><span class="sxs-lookup"><span data-stu-id="7580e-141">**Scenario 3: Domain controller is unavailable**</span></span>  
  
 <span data-ttu-id="7580e-142">可能是無法使用網域控制站驗證使用者識別所致。</span><span class="sxs-lookup"><span data-stu-id="7580e-142">The cause might be that a domain controller is not available to validate the user identity.</span></span> <span data-ttu-id="7580e-143">對 Windows Token Service 的宣告需要網域控制站，才能針對每個連接驗證 SharePoint 使用者。</span><span class="sxs-lookup"><span data-stu-id="7580e-143">A domain controller is required by the Claims to Windows Token Service to authenticate the SharePoint user on each connection.</span></span> <span data-ttu-id="7580e-144">對 Windows Token Service 的宣告無法使用快取認證。</span><span class="sxs-lookup"><span data-stu-id="7580e-144">The Claims to Windows Token Service does not use cached credentials.</span></span> <span data-ttu-id="7580e-145">它會針對每一個連接來驗證使用者識別。</span><span class="sxs-lookup"><span data-stu-id="7580e-145">It validates the user identity for each connection.</span></span>  
  
 <span data-ttu-id="7580e-146">您可以檢視 SharePoint 記錄檔來確認這個錯誤的原因。</span><span class="sxs-lookup"><span data-stu-id="7580e-146">You can confirm the cause of this error by viewing the SharePoint log file.</span></span> <span data-ttu-id="7580e-147">如果 SharePoint 記錄檔包含「無法從 IClaimsIdentity 取得 WindowsIdentity」訊息，則表示無法驗證使用者識別。</span><span class="sxs-lookup"><span data-stu-id="7580e-147">If the SharePoint logs include the message "Failed to get WindowsIdentity from IClaimsIdentity", the user identity could not be authenticated.</span></span>  
  
 <span data-ttu-id="7580e-148">若要解決此問題，請將電腦加入至與 PowerPivot 伺服器相同的網域，或在本機電腦上安裝網域控制站。</span><span class="sxs-lookup"><span data-stu-id="7580e-148">To work around this problem, join the computer to the same domain as the PowerPivot server, or install a domain controller on your local computer.</span></span> <span data-ttu-id="7580e-149">第二個解決方案「安裝網域控制站」將需要您為所有服務和使用者建立本機網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="7580e-149">The second solution, installing the domain controller, will require you to create local domain accounts for all services and users.</span></span> <span data-ttu-id="7580e-150">您將需要為您定義的帳戶設定服務帳戶和 SharePoint 權限。</span><span class="sxs-lookup"><span data-stu-id="7580e-150">You will need to configure service accounts and SharePoint permissions for the accounts you define.</span></span>  
  
 <span data-ttu-id="7580e-151">如果您的目標是在離線狀態下使用 PowerPivot for SharePoint，在電腦上安裝網域控制站相當實用。</span><span class="sxs-lookup"><span data-stu-id="7580e-151">Installing a domain controller on your computer is useful if your objective is to use PowerPivot for SharePoint in an offline state.</span></span> <span data-ttu-id="7580e-152">如需有關如何離線使用 PowerPivot 的詳細指示，請參閱的「在網路上取得您的 PowerPivot 服務器」的 blog 專案 [http://www.powerpivotgeek.com](https://go.microsoft.com/fwlink/?LinkId=184241) 。</span><span class="sxs-lookup"><span data-stu-id="7580e-152">For detailed instructions on how to use PowerPivot offline, see the blog entry for "Taking your PowerPivot server off the network" on [http://www.powerpivotgeek.com](https://go.microsoft.com/fwlink/?LinkId=184241).</span></span>  
  
 <span data-ttu-id="7580e-153">**案例 4：伺服器不穩定**</span><span class="sxs-lookup"><span data-stu-id="7580e-153">**Scenario 4: Unstable server**</span></span>  
  
 <span data-ttu-id="7580e-154">可能有一項或多項服務處於不一致的狀態。</span><span class="sxs-lookup"><span data-stu-id="7580e-154">One or more services might be in an inconsistent state.</span></span> <span data-ttu-id="7580e-155">在某些情況下，執行 IISRESET 即可解決問題。</span><span class="sxs-lookup"><span data-stu-id="7580e-155">In some cases, running IISRESET will resolve the problem.</span></span>  
  
  
