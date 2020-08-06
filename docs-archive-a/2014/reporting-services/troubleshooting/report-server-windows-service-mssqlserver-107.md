---
title: 報表伺服器 Windows 服務 (MSSQLServer) 107 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- MSSQLServer 107 error
ms.assetid: 52b5704b-27f9-400a-a821-d8fa0786afe4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8651f98b47b698fbe3cfb6a152b9220a84ed7256
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594935"
---
# <a name="report-server-windows-service-mssqlserver-107"></a><span data-ttu-id="13a58-102">報表伺服器 Windows 服務 (MSSQLServer) 107</span><span class="sxs-lookup"><span data-stu-id="13a58-102">Report Server Windows Service (MSSQLServer) 107</span></span>
    
## <a name="details"></a><span data-ttu-id="13a58-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="13a58-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="13a58-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="13a58-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="13a58-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="13a58-105">Event ID</span></span>|<span data-ttu-id="13a58-106">107</span><span class="sxs-lookup"><span data-stu-id="13a58-106">107</span></span>|  
|<span data-ttu-id="13a58-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="13a58-107">Event Source</span></span>|<span data-ttu-id="13a58-108">報表伺服器 Windows 服務</span><span class="sxs-lookup"><span data-stu-id="13a58-108">Report Server Windows Service</span></span>|  
|<span data-ttu-id="13a58-109">元件</span><span class="sxs-lookup"><span data-stu-id="13a58-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="13a58-110">訊息文字</span><span class="sxs-lookup"><span data-stu-id="13a58-110">Message Text</span></span>|<span data-ttu-id="13a58-111">報表伺服器 Windows 服務 (MSSQLSERVER) 無法連接到報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="13a58-111">Report Server Windows Service (MSSQLSERVER) cannot connect to the report server database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="13a58-112">說明</span><span class="sxs-lookup"><span data-stu-id="13a58-112">Explanation</span></span>  
 <span data-ttu-id="13a58-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 報表伺服器服務無法連接到報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="13a58-113">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Report Server service cannot connect to the report server database.</span></span> <span data-ttu-id="13a58-114">如果無法建立與報表伺服器資料庫的連接，將會在服務重新啟動期間發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="13a58-114">This error occurs during a service restart if a connection to the report server database cannot be established.</span></span> <span data-ttu-id="13a58-115">發生此錯誤的條件如下：</span><span class="sxs-lookup"><span data-stu-id="13a58-115">Conditions under which this error occurs include the following:</span></span>  
  
-   <span data-ttu-id="13a58-116">當報表伺服器服務啟動時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 服務並未執行。</span><span class="sxs-lookup"><span data-stu-id="13a58-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] service is not running when the Report Server service starts.</span></span>  
  
-   <span data-ttu-id="13a58-117">由於遠端連接或 TCP/IP 通訊協定未啟用，而導致 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 服務的連接失敗。</span><span class="sxs-lookup"><span data-stu-id="13a58-117">The connection to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service fails because remote connections or the TCP/IP protocol is not enabled.</span></span>  
  
-   <span data-ttu-id="13a58-118">未正確設定報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="13a58-118">The report server database is not configured correctly.</span></span>  
  
-   <span data-ttu-id="13a58-119">此服務帳戶未正確設定，或是此帳戶不再有報表伺服器資料庫的權限。</span><span class="sxs-lookup"><span data-stu-id="13a58-119">The service account is not configured correctly, or the account no longer has permissions on the report server database.</span></span> <span data-ttu-id="13a58-120">如果您並未使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具來設定此帳戶或報表伺服器資料庫，則可能會發生這個狀況。</span><span class="sxs-lookup"><span data-stu-id="13a58-120">This can occur if you do not use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool to set up the account or the report server database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="13a58-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="13a58-121">User Action</span></span>  
 <span data-ttu-id="13a58-122">如果 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 服務不在執行中則啟動它，並檢查是否已針對 TCP/IP 通訊協定啟用遠端連接。</span><span class="sxs-lookup"><span data-stu-id="13a58-122">Start the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service if it is not running and check that remote connections are enabled for TCP/IP protocol.</span></span>  
  
 <span data-ttu-id="13a58-123">使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具來設定報表伺服器資料庫和服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="13a58-123">Use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool to configure the report server database and service account.</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="13a58-124">僅供內部使用</span><span class="sxs-lookup"><span data-stu-id="13a58-124">Internal-Only</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13a58-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13a58-125">See Also</span></span>  
 <span data-ttu-id="13a58-126">[設定報表伺服器服務帳戶 &#40;SSRS 組態管理員&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="13a58-126">[Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="13a58-127">[Reporting Services 組態管理員 &#40;原生模式&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="13a58-127">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 [<span data-ttu-id="13a58-128">啟動與停止報表伺服器服務</span><span class="sxs-lookup"><span data-stu-id="13a58-128">Start and Stop the Report Server Service</span></span>](../report-server/start-and-stop-the-report-server-service.md)  
  
  
