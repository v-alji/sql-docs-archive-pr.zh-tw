---
title: 資料連接是使用 Windows 驗證，而且無法委派使用者認證。 下列連接無法重新整理： PowerPivot 資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d2006df1-d244-4786-b272-49d8996cc88c
author: minewiskan
ms.author: owend
ms.openlocfilehash: be4c61ad4514f3aa4f6f1eda1fe44ad97c4c064f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594250"
---
# <a name="the-data-connection-uses-windows-authentication-and-user-credentials-could-not-be-delegated-the-following-connections-failed-to-refresh-powerpivot-data"></a><span data-ttu-id="473e4-103">資料連接是使用 Windows 驗證，而且無法委派使用者認證。</span><span class="sxs-lookup"><span data-stu-id="473e4-103">The data connection uses Windows Authentication and user credentials could not be delegated.</span></span> <span data-ttu-id="473e4-104">下列連接無法重新整理：PowerPivot 資料</span><span class="sxs-lookup"><span data-stu-id="473e4-104">The following connections failed to refresh: PowerPivot Data</span></span>
  <span data-ttu-id="473e4-105">如果是包含 PowerPivot 資料的 Excel 活頁簿，Excel Services 會在無法連接到 SharePoint 中的 PowerPivot 伺服器執行個體時傳回這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="473e4-105">For Excel workbooks that contain PowerPivot data, Excel Services returns this error if it cannot connect to a PowerPivot server instance in SharePoint.</span></span>  
  
## <a name="details"></a><span data-ttu-id="473e4-106">詳細資料</span><span class="sxs-lookup"><span data-stu-id="473e4-106">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="473e4-107">適用於</span><span class="sxs-lookup"><span data-stu-id="473e4-107">Applies to</span></span>|<span data-ttu-id="473e4-108">PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="473e4-108">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="473e4-109">產品版本</span><span class="sxs-lookup"><span data-stu-id="473e4-109">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="473e4-110">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="473e4-110">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="473e4-111">原因</span><span class="sxs-lookup"><span data-stu-id="473e4-111">Cause</span></span>|<span data-ttu-id="473e4-112">嘗試使用 PowerPivot 資料提供者時發生連接失敗。</span><span class="sxs-lookup"><span data-stu-id="473e4-112">Connection failed when attempting to use a PowerPivot data provider.</span></span>|  
|<span data-ttu-id="473e4-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="473e4-113">Message Text</span></span>|<span data-ttu-id="473e4-114">資料連接是使用 Windows 驗證，而且無法委派使用者認證。</span><span class="sxs-lookup"><span data-stu-id="473e4-114">The data connection uses Windows Authentication and user credentials could not be delegated.</span></span> <span data-ttu-id="473e4-115">下列連接無法重新整理：PowerPivot 資料</span><span class="sxs-lookup"><span data-stu-id="473e4-115">The following connections failed to refresh: PowerPivot Data</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="473e4-116">說明</span><span class="sxs-lookup"><span data-stu-id="473e4-116">Explanation</span></span>  
 <span data-ttu-id="473e4-117">這個錯誤訊息有多個原因。</span><span class="sxs-lookup"><span data-stu-id="473e4-117">There are multiple causes for this error message.</span></span> <span data-ttu-id="473e4-118">所有原因背後的共同因素就是 Excel Services 無法從 SharePoint 中的宣告 Token 取得有效的 Windows 使用者識別。</span><span class="sxs-lookup"><span data-stu-id="473e4-118">The common factor behind all of them is that Excel Services cannot get a valid Windows user identity from a claims token in SharePoint.</span></span> <span data-ttu-id="473e4-119">如果是包含 PowerPivot 資料的 Excel 活頁簿，下列任何條件存在時就會發生這個錯誤：</span><span class="sxs-lookup"><span data-stu-id="473e4-119">In the case of Excel workbooks that contain PowerPivot data, this error occurs when any of the following conditions exist:</span></span>  
  
-   <span data-ttu-id="473e4-120">對 Windows Token Service 的宣告未在執行中。</span><span class="sxs-lookup"><span data-stu-id="473e4-120">The Claims to Windows Token Service is not running.</span></span> <span data-ttu-id="473e4-121">您可以檢視 SharePoint 記錄檔來確認這個錯誤的原因。</span><span class="sxs-lookup"><span data-stu-id="473e4-121">You can confirm the cause of this error by viewing the SharePoint log file.</span></span> <span data-ttu-id="473e4-122">如果 SharePoint 記錄檔包含「本機電腦上找不到管線端點 'net.pipe://localhost/s4u/022694f3-9fbd-422b-b4b2-312e25dae2a2'」訊息，就表示對 Windows Token Service 的宣告未在執行中。</span><span class="sxs-lookup"><span data-stu-id="473e4-122">If the SharePoint logs include the message "The pipe endpoint 'net.pipe://localhost/s4u/022694f3-9fbd-422b-b4b2-312e25dae2a2' could not be found on your local machine", the Claims to Windows Token Service is not running.</span></span> <span data-ttu-id="473e4-123">若要啟動它，請使用管理中心，然後確認此服務正在服務主控台應用程式中執行。</span><span class="sxs-lookup"><span data-stu-id="473e4-123">To start it, use Central Administration and then verify the service is running in the Services console application.</span></span>  
  
-   <span data-ttu-id="473e4-124">無法使用網域控制站來驗證使用者識別。</span><span class="sxs-lookup"><span data-stu-id="473e4-124">A domain controller is not available to validate the user identity.</span></span> <span data-ttu-id="473e4-125">對 Windows Token Service 的宣告無法使用快取認證。</span><span class="sxs-lookup"><span data-stu-id="473e4-125">The Claims to Windows Token Service does not use cached credentials.</span></span> <span data-ttu-id="473e4-126">它會針對每一個連接來驗證使用者識別。</span><span class="sxs-lookup"><span data-stu-id="473e4-126">It validates the user identity for each connection.</span></span> <span data-ttu-id="473e4-127">您可以檢視 SharePoint 記錄檔來確認這個錯誤的原因。</span><span class="sxs-lookup"><span data-stu-id="473e4-127">You can confirm the cause of this error by viewing the SharePoint log file.</span></span> <span data-ttu-id="473e4-128">如果 SharePoint 記錄檔包含「無法從 IClaimsIdentity 取得 WindowsIdentity」訊息，則表示無法驗證使用者識別。</span><span class="sxs-lookup"><span data-stu-id="473e4-128">If the SharePoint logs include the message "Failed to get WindowsIdentity from IClaimsIdentity", the user identity could not be authenticated.</span></span>  
  
-   <span data-ttu-id="473e4-129">電腦必須是相同網域的成員，或是位於具有雙向信任關係的網域中。</span><span class="sxs-lookup"><span data-stu-id="473e4-129">The computers must be members of the same domain or in domains that have a two-way trust relationship.</span></span>  
  
-   <span data-ttu-id="473e4-130">您必須使用 Windows 網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="473e4-130">You must use Windows domain user accounts.</span></span> <span data-ttu-id="473e4-131">帳戶必須具有通用主要名稱 (UPN)。</span><span class="sxs-lookup"><span data-stu-id="473e4-131">The accounts must have a Universal Principal Name (UPN).</span></span>  
  
-   <span data-ttu-id="473e4-132">Excel Services 服務帳戶必須具有查詢物件的 Active Directory 權限。</span><span class="sxs-lookup"><span data-stu-id="473e4-132">The Excel Services service account must have Active Directory permissions to query the object.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="473e4-133">使用者動作</span><span class="sxs-lookup"><span data-stu-id="473e4-133">User Action</span></span>  
 <span data-ttu-id="473e4-134">使用下列指示來檢查對 Windows Token Service 的宣告狀態。</span><span class="sxs-lookup"><span data-stu-id="473e4-134">Use the following instructions to check the status of the Claims to Windows Token Service.</span></span>  
  
 <span data-ttu-id="473e4-135">如需了解所有其他案例，請向網路管理員查詢。</span><span class="sxs-lookup"><span data-stu-id="473e4-135">For all other scenarios, check with your network administrator.</span></span>  
  
#### <a name="enable-claims-to-windows-token-service"></a><span data-ttu-id="473e4-136">啟用對 Windows Token Service 的宣告</span><span class="sxs-lookup"><span data-stu-id="473e4-136">Enable Claims to Windows Token Service</span></span>  
  
1.  <span data-ttu-id="473e4-137">在 [管理中心] 的 [系統設定] 中，按一下 [**管理伺服器上的服務**]。</span><span class="sxs-lookup"><span data-stu-id="473e4-137">In Central Administration, in System Settings, click **Manage services on server**.</span></span>  
  
2.  <span data-ttu-id="473e4-138">選取 [對 Windows Token 服務的宣告]\*\*\*\*，然後按一下 [啟動]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="473e4-138">Select **Claims to Windows Token Service**, and then click **Start**.</span></span>  
  
3.  <span data-ttu-id="473e4-139">確認該服務也在服務主控台中執行：</span><span class="sxs-lookup"><span data-stu-id="473e4-139">Verify the service is also running in the Services console:</span></span>  
  
    1.  <span data-ttu-id="473e4-140">在 [系統管理工具] 中，按一下 [服務]。</span><span class="sxs-lookup"><span data-stu-id="473e4-140">In Administrative Tools, click Services.</span></span>  
  
    2.  <span data-ttu-id="473e4-141">如果對 Windows Token Service 的宣告未在執行中，則啟動它。</span><span class="sxs-lookup"><span data-stu-id="473e4-141">Start the Claims to Windows Token Service if it is not running.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="473e4-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="473e4-142">See Also</span></span>  
 [<span data-ttu-id="473e4-143">設定 PowerPivot 服務帳戶</span><span class="sxs-lookup"><span data-stu-id="473e4-143">Configure PowerPivot Service Accounts</span></span>](configure-power-pivot-service-accounts.md)  
  
  
