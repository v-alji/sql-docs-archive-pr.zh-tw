---
title: rsAccessedDenied - Reporting Services 錯誤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsAccessDenied error
ms.assetid: 2f76b1bf-96a2-4755-b76b-84e933220efc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 194006c2ef6f22b9bc27e9e8cbe1eebd027ed6b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596460"
---
# <a name="rsaccesseddenied---reporting-services-error"></a><span data-ttu-id="5d063-102">rsAccessedDenied - Reporting Services 錯誤</span><span class="sxs-lookup"><span data-stu-id="5d063-102">rsAccessedDenied - Reporting Services Error</span></span>
  <span data-ttu-id="5d063-103">當使用者沒有執行動作的權限時，會發生 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 錯誤 **rsAccessedDenied** 。</span><span class="sxs-lookup"><span data-stu-id="5d063-103">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] error **rsAccessedDenied** occurs when a user does not have permission to perform an action.</span></span> <span data-ttu-id="5d063-104">例如，他們並未擁有允許他們開啟報表的角色指派，或者他們沒有使用必要的權限開啟瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="5d063-104">For, example, they do not have a role assignment that allows them to open a report or they did not open their browser with the required permissions.</span></span>  
  
||  
|-|  
|<span data-ttu-id="5d063-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 原生模式 &#124; SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="5d063-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; SharePoint mode</span></span>|  
  
-   <span data-ttu-id="5d063-106">如果在直接透過 URL 存取報表伺服器時發生錯誤，則例外狀況會對應到 HTTP 401 錯誤。</span><span class="sxs-lookup"><span data-stu-id="5d063-106">If the error occurred while accessing the report server directly through a URL, the exception is mapped to an HTTP 401 error.</span></span>  
  
-   <span data-ttu-id="5d063-107">如果錯誤是在使用報表管理員或其他工具時發生，錯誤會顯示在錯誤頁面中。</span><span class="sxs-lookup"><span data-stu-id="5d063-107">If the error occurred while using Report Manager or another tool, the error appears in an error page.</span></span>  
  
-   <span data-ttu-id="5d063-108">如果錯誤是在執行已排程的作業、訂閱或傳遞期間發生，則錯誤將只會顯示在報表伺服器記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="5d063-108">If the error occurred during a scheduled operation, subscription, or delivery, the error will appear in the report server log file only.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5d063-109">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5d063-109">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5d063-110">**產品名稱**</span><span class="sxs-lookup"><span data-stu-id="5d063-110">**Product Name**</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="5d063-111">**事件識別碼**</span><span class="sxs-lookup"><span data-stu-id="5d063-111">**Event ID**</span></span>|<span data-ttu-id="5d063-112">rsAccessedDenied</span><span class="sxs-lookup"><span data-stu-id="5d063-112">rsAccessedDenied</span></span>|  
|<span data-ttu-id="5d063-113">**事件來源**</span><span class="sxs-lookup"><span data-stu-id="5d063-113">**Event Source**</span></span>|<span data-ttu-id="5d063-114">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span><span class="sxs-lookup"><span data-stu-id="5d063-114">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span></span>|  
|<span data-ttu-id="5d063-115">**元件**</span><span class="sxs-lookup"><span data-stu-id="5d063-115">**Component**</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="5d063-116">**訊息文字**</span><span class="sxs-lookup"><span data-stu-id="5d063-116">**Message Text**</span></span>|<span data-ttu-id="5d063-117">授與使用者 'mydomain\myAccount' 的權限不足，無法執行此作業。</span><span class="sxs-lookup"><span data-stu-id="5d063-117">The permissions granted to user 'mydomain\myAccount' are insufficient for performing this operation.</span></span> <span data-ttu-id="5d063-118">(rsAccessDenied) (ReportingServicesLibrary)</span><span class="sxs-lookup"><span data-stu-id="5d063-118">(rsAccessDenied) (ReportingServicesLibrary)</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="5d063-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5d063-119">User Action</span></span>  
 <span data-ttu-id="5d063-120">存取報表伺服器內容和作業的權限是透過角色指派而授與。</span><span class="sxs-lookup"><span data-stu-id="5d063-120">Permission to access report server content and operations are granted through role assignments.</span></span> <span data-ttu-id="5d063-121">在新的安裝上，只有本機管理員具有存取報表伺服器的權限。</span><span class="sxs-lookup"><span data-stu-id="5d063-121">On a new installation, only local administrators have access to a report server.</span></span> <span data-ttu-id="5d063-122">若要授與其他使用者存取權限，本機管理員必須建立角色指派，以指定網域使用者或群組帳戶、一個或多個角色 (用來定義使用者可執行的工作)，以及範圍 (通常是報表伺服器資料夾階層的 [主資料夾] 資料夾或根節點)。</span><span class="sxs-lookup"><span data-stu-id="5d063-122">To grant access to other users, a local administrator must create a role assignment that specifies a domain user or group account, one or more roles that define the tasks the user can perform, and a scope (usually the Home folder or root node of the report server folder hierarchy).</span></span> <span data-ttu-id="5d063-123">您可以使用報表管理員來建立角色指派。</span><span class="sxs-lookup"><span data-stu-id="5d063-123">You can use Report Manager to create the role assignments.</span></span> <span data-ttu-id="5d063-124">如需詳細資訊，請在《SQL Server 線上叢書》中搜尋「角色指派」。</span><span class="sxs-lookup"><span data-stu-id="5d063-124">For more information, search for "Role Assignments" in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="5d063-125">這個錯誤是因為報表伺服器的本機管理所造成。</span><span class="sxs-lookup"><span data-stu-id="5d063-125">This error is also caused by local administration of the report server.</span></span> <span data-ttu-id="5d063-126">如需詳細資訊，請參閱 [設定原生模式報表伺服器進行本機管理 &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="5d063-126">For more information, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d063-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d063-127">See Also</span></span>  
 <span data-ttu-id="5d063-128">[角色指派](../security/role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="5d063-128">[Role Assignments](../security/role-assignments.md) </span></span>  
 <span data-ttu-id="5d063-129">[在原生模式報表伺服器上授與權限](../security/granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="5d063-129">[Granting Permissions on a Native Mode Report Server](../security/granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 [<span data-ttu-id="5d063-130">角色與權限 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="5d063-130">Roles and Permissions &#40;Reporting Services&#41;</span></span>](../security/roles-and-permissions-reporting-services.md)  
  
  
