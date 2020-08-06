---
title: SQL Server 2005 (Upgrade Advisor) 偵測到的報表伺服器 Web 服務群組 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- deployment [Reporting Services]
ms.assetid: 699d24eb-7756-4b41-9294-ef1a94b2f267
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 70be2b9c4e7abd55daaa752830a73cbe6e222659
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710154"
---
# <a name="sql-server-2005-report-server-web-service-group-detected-upgrade-advisor"></a><span data-ttu-id="d7340-102">偵測到 SQL Server 2005 報表伺服器 Web 服務群組 (Upgrade Advisor)</span><span class="sxs-lookup"><span data-stu-id="d7340-102">SQL Server 2005 Report Server Web Service group detected (Upgrade Advisor)</span></span>
  <span data-ttu-id="d7340-103">Upgrade Advisor 偵測到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 實例與 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 報表伺服器 Web 服務群組相關聯。</span><span class="sxs-lookup"><span data-stu-id="d7340-103">Upgrade Advisor detected that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance is associated with a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Report Server Web service group.</span></span>  
  
||  
|-|  
|<span data-ttu-id="d7340-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]原生模式。</span><span class="sxs-lookup"><span data-stu-id="d7340-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="d7340-105">元件</span><span class="sxs-lookup"><span data-stu-id="d7340-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="d7340-106">描述</span><span class="sxs-lookup"><span data-stu-id="d7340-106">Description</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="d7340-107">不 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 使用 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]報表伺服器 Web 服務群組。</span><span class="sxs-lookup"><span data-stu-id="d7340-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] does not use the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Report Server Web service group.</span></span> <span data-ttu-id="d7340-108">當您從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 升級為 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 時，系統將在升級期間刪除這個服務群組，而且不會保留這個群組的自訂存取控制清單 (ACL) 或屬於這個群組的使用者。</span><span class="sxs-lookup"><span data-stu-id="d7340-108">When you upgrade from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], this service group is deleted and custom Access Control Lists (ACLs) for this group or users who belong to the group are not retained during the upgrade.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="d7340-109">更正動作</span><span class="sxs-lookup"><span data-stu-id="d7340-109">Corrective Action</span></span>  
 <span data-ttu-id="d7340-110">升級之前，請先備份任何自訂 ACL 或屬於 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 報表伺服器 Web 服務群組的使用者。</span><span class="sxs-lookup"><span data-stu-id="d7340-110">Before you upgrade, back up any custom ACLs or users who belong to the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Report Server Web service group.</span></span> <span data-ttu-id="d7340-111">若要這麼做，您可以使用 sp2 和更新版本中的**Icacls.exe**命令列工具， [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 或在 Sp2 之前的 Windows 作業系統中的 Cacls.exe 命令列工具 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d7340-111">To do this, you can use the **Icacls.exe** command-line tool in [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2 and later or the Cacls.exe command-line tool in Windows operating systems prior to [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2.</span></span> <span data-ttu-id="d7340-112">如需有關這些工具之語法的詳細資訊，請參閱 Windows 產品文件集。</span><span class="sxs-lookup"><span data-stu-id="d7340-112">For more information about the syntax for these tools, see the Windows product documentation.</span></span> <span data-ttu-id="d7340-113">安裝程式成功完成之後，請將自訂 ACL 或使用者套用至報表伺服器執行個體的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 報表伺服器 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="d7340-113">After setup successfully completes, apply the custom ACLs or users to the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Report Server Windows group for your report server instance.</span></span> <span data-ttu-id="d7340-114">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]報表伺服器 Windows 群組會採用 SQLServerReportServerUser $ 的格式 \<*computer_name*> $ \<*instance_name*> 。</span><span class="sxs-lookup"><span data-stu-id="d7340-114">The [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Report Server Windows group takes the form of SQLServerReportServerUser$\<*computer_name*>$\<*instance_name*>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7340-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7340-115">See Also</span></span>  
 [<span data-ttu-id="d7340-116">&#40;Upgrade Advisor Reporting Services 升級問題&#41;</span><span class="sxs-lookup"><span data-stu-id="d7340-116">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
