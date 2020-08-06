---
title: SQL Server 2014 中管理工具功能的重大變更 |Microsoft Docs
ms.custom: ''
ms.date: 11/27/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 3ff3fad8-b569-4516-bd58-5a3efeb537e2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0487b6ab0958e0b83d4e8e34be507b5b3211ac87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597381"
---
# <a name="breaking-changes-to-management-tools-features-in-sql-server-2014"></a><span data-ttu-id="f58a3-102">SQL Server 2014 中管理工具功能的突破性變更</span><span class="sxs-lookup"><span data-stu-id="f58a3-102">Breaking Changes to Management Tools Features in SQL Server 2014</span></span>
  <span data-ttu-id="f58a3-103">此主題描述管理工具功能的突破性變更。</span><span class="sxs-lookup"><span data-stu-id="f58a3-103">This topic describes breaking changes to management tools features.</span></span> <span data-ttu-id="f58a3-104">這些變更可能會中斷以舊版 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]為根據的應用程式、指令碼或功能。</span><span class="sxs-lookup"><span data-stu-id="f58a3-104">These changes might break applications, scripts, or functionalities that are based on earlier versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f58a3-105">當您升級時可能會遇到這些問題。</span><span class="sxs-lookup"><span data-stu-id="f58a3-105">You might encounter these issues when you upgrade.</span></span> <span data-ttu-id="f58a3-106">如需詳細資訊，請參閱＜ [Use Upgrade Advisor to Prepare for Upgrades](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)＞。</span><span class="sxs-lookup"><span data-stu-id="f58a3-106">For more information, see [Use Upgrade Advisor to Prepare for Upgrades](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).</span></span>  
  
## <a name="breaking-changes-in-sssql14"></a><span data-ttu-id="f58a3-107"> 的最新變更</span><span class="sxs-lookup"><span data-stu-id="f58a3-107">Breaking Changes in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]</span></span>  
 <span data-ttu-id="f58a3-108">將於日後提供資訊。</span><span class="sxs-lookup"><span data-stu-id="f58a3-108">Information to come later.</span></span>  
  
## <a name="breaking-changes-in-sssql11"></a><span data-ttu-id="f58a3-109"> 的最新變更</span><span class="sxs-lookup"><span data-stu-id="f58a3-109">Breaking Changes in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]</span></span>  
  
### <a name="you-cannot-use-sssql11-management-tools-to-create-a-utility-control-point-on-a-sskilimanjaro-instance-of-sql-server"></a><span data-ttu-id="f58a3-110">您無法在 SQL Server 的 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 執行個體上，使用 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 管理工具建立公用程式控制點。</span><span class="sxs-lookup"><span data-stu-id="f58a3-110">You cannot use [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Management Tools to create a utility control point on a [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] instance of SQL Server</span></span>  
 <span data-ttu-id="f58a3-111">若要在 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]的執行個體上建立公用程式控制點，請使用 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 管理工具。</span><span class="sxs-lookup"><span data-stu-id="f58a3-111">To create a utility control point on an instance of [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)], use [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] Management Tools.</span></span>  
  
### <a name="smo-has-been-reversioned-in-sssql11"></a><span data-ttu-id="f58a3-112">SMO 已經在 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 中還原</span><span class="sxs-lookup"><span data-stu-id="f58a3-112">SMO has been reversioned in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]</span></span>  
 <span data-ttu-id="f58a3-113">使用 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 或更早版本的 SMO 所開發的程式碼必須稍微修改，才能針對 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 進行建立。</span><span class="sxs-lookup"><span data-stu-id="f58a3-113">Code developed with SMO from [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] or earlier versions might not build against [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] without minor modifications.</span></span> <span data-ttu-id="f58a3-114">如需詳細資訊，請參閱 [Backward Compatibility in SMO](../relational-databases/server-management-objects-smo/backward-compatibility-in-smo.md)。</span><span class="sxs-lookup"><span data-stu-id="f58a3-114">For more information, see [Backward Compatibility in SMO](../relational-databases/server-management-objects-smo/backward-compatibility-in-smo.md).</span></span>  

## <a name="breaking-changes-in-sql-server-2005"></a><a name="previous-versions"></a><span data-ttu-id="f58a3-115">SQL Server 2005 中的重大變更</span><span class="sxs-lookup"><span data-stu-id="f58a3-115">Breaking Changes in SQL Server 2005</span></span>  

[!INCLUDE[Archived documentation for very old versions of SQL Server](../includes/paragraph-content/previous-versions-archive-documentation-sql-server.md)]

## <a name="see-also"></a><span data-ttu-id="f58a3-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f58a3-116">See Also</span></span>  
 [<span data-ttu-id="f58a3-117">回溯相容性</span><span class="sxs-lookup"><span data-stu-id="f58a3-117">Backward Compatibility</span></span>](../../2014/getting-started/backward-compatibility.md)  
 [<span data-ttu-id="f58a3-118">深入瞭解 SQL Server 2014 中管理工具功能的重大變更</span><span class="sxs-lookup"><span data-stu-id="f58a3-118">More about Breaking Changes to Management Tools Features in SQL Server 2014</span></span>](breaking-changes-to-database-engine-features-in-sql-server-2016.md?view=sql-server-2014)  
  
  
