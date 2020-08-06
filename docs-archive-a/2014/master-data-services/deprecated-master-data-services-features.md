---
title: SQL Server 2014 中已淘汰的 Master Data Services 功能 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: d8506bda-66dd-45a4-bfc9-3a10fa665acc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ce532e9f407ec475f7e59c0d79659265a9e0bf3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687010"
---
# <a name="deprecated-master-data-services-features-in-sql-server-2014"></a><span data-ttu-id="0b122-102">SQL Server 2014 中已被取代的 Master Data Services 功能</span><span class="sxs-lookup"><span data-stu-id="0b122-102">Deprecated Master Data Services Features in SQL Server 2014</span></span>
  <span data-ttu-id="0b122-103">本主題描述 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中仍然可用但已被取代的 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="0b122-103">This topic describes the deprecated [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] features that are still available in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="0b122-104">這些功能將在未來的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]版本中移除。</span><span class="sxs-lookup"><span data-stu-id="0b122-104">These features are scheduled to be removed in a future release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0b122-105">已被取代的功能不應在新應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="0b122-105">Deprecated features should not be used in new applications.</span></span>  
  
## <a name="staging-process"></a><span data-ttu-id="0b122-106">暫存處理序</span><span class="sxs-lookup"><span data-stu-id="0b122-106">Staging Process</span></span>  
 <span data-ttu-id="0b122-107">[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] Web 應用程式中不再提供 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 中所使用的暫存處理序，不過仍可在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 使用。</span><span class="sxs-lookup"><span data-stu-id="0b122-107">The staging process that was used in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] is no longer available in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application; however it is still available in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="0b122-108">來自 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 暫存處理序的暫存錯誤不再顯示在使用者介面中。</span><span class="sxs-lookup"><span data-stu-id="0b122-108">Staging errors from the [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] staging process are no longer displayed in the UI.</span></span> <span data-ttu-id="0b122-109">在暫存進程期間填入的錯誤碼仍可在臨時表中使用，您可以在這裡找到： [https://msdn.microsoft.com/library/ff487022.aspx](https://msdn.microsoft.com/library/ff487022.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="0b122-109">Error codes that are populated during the staging process are still available in the staging tables, and can be found here: [https://msdn.microsoft.com/library/ff487022.aspx](https://msdn.microsoft.com/library/ff487022.aspx).</span></span>  
  
 <span data-ttu-id="0b122-110">暫存資料表 (tblStgMember、tblStgMemberAttribute 及 tblStgRelationship) 仍在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="0b122-110">The staging tables (tblStgMember, tblStgMemberAttribute, and tblStgRelationship) are still available in the database.</span></span> <span data-ttu-id="0b122-111">用來起始暫存處理序 (mdm.udpStagingSweep) 的預存程序仍在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="0b122-111">The stored procedure used to initiate the staging process (mdm.udpStagingSweep) is still available in the database.</span></span>  
  
 <span data-ttu-id="0b122-112">仍可使用呼叫暫存處理序的 Web 服務方法。</span><span class="sxs-lookup"><span data-stu-id="0b122-112">The web service methods that call the staging process are still available.</span></span>  
  
 <span data-ttu-id="0b122-113">在 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]中設定的暫存間隔會套用至 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 和 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 中的暫存處理序。</span><span class="sxs-lookup"><span data-stu-id="0b122-113">The staging interval set in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] applies to the staging process in both [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] and [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="0b122-114"> 中已實作新的、效能更高的暫存處理序。</span><span class="sxs-lookup"><span data-stu-id="0b122-114">A new, higher performance staging process has been implemented in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="0b122-115">如需詳細資訊，請參閱[資料匯入 &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="0b122-115">For more information, see [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).</span></span>  
  
## <a name="metadata"></a><span data-ttu-id="0b122-116">中繼資料</span><span class="sxs-lookup"><span data-stu-id="0b122-116">Metadata</span></span>  
 <span data-ttu-id="0b122-117">雖然中繼資料模型仍然顯示在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 應用程式中，不過您不應該使用它。</span><span class="sxs-lookup"><span data-stu-id="0b122-117">Though the Metadata model is still displayed in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application, it should not be used.</span></span> <span data-ttu-id="0b122-118">未來的版本將予以移除。</span><span class="sxs-lookup"><span data-stu-id="0b122-118">It will be removed in a future release.</span></span> <span data-ttu-id="0b122-119">使用者也不能再于 [ **Explorer** ] 功能區域中查看中繼資料，而且您也無法再建立元資料模型的版本。</span><span class="sxs-lookup"><span data-stu-id="0b122-119">Users can also no longer view metadata in the **Explorer** functional area, and you can no longer create versions of the Metadata model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b122-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b122-120">See Also</span></span>  
 [<span data-ttu-id="0b122-121">SQL Server 2014 中已停止的 Master Data Services 功能</span><span class="sxs-lookup"><span data-stu-id="0b122-121">Discontinued Master Data Services Features in SQL Server 2014</span></span>](discontinued-master-data-services-features.md)  
  
  
