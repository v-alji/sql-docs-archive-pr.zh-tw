---
title: 非 SQL Server 發行者 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- heterogeneous database replication, non-SQL Server Publishers
- non-SQL Server Publishers
- heterogeneous data sources, non-SQL Server Publishers
- Publishers [SQL Server replication], Oracle
ms.assetid: 08a160a6-33be-46b5-bc7b-d53180d8bdf1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f15f07dbf294d697afd385318f3dbf1447c8e2d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585298"
---
# <a name="non-sql-server-publishers"></a><span data-ttu-id="c664b-102">非 SQL Server 發行者</span><span class="sxs-lookup"><span data-stu-id="c664b-102">Non-SQL Server Publishers</span></span>
  <span data-ttu-id="c664b-103">從非來源發行資料 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，可讓您合併中的資料 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c664b-103">Publishing data from non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sources allows you to consolidate data in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="c664b-104">可訂閱從 Oracle 資料庫發行的快照或交易資料。</span><span class="sxs-lookup"><span data-stu-id="c664b-104">can subscribe to snapshot or transactional data published from an Oracle database.</span></span> <span data-ttu-id="c664b-105">如需從 Oracle 發行的詳細資訊，請參閱 [Oracle 發行概觀](oracle-publishing-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c664b-105">For more information about publishing from Oracle, see [Oracle Publishing Overview](oracle-publishing-overview.md).</span></span>  
  
 <span data-ttu-id="c664b-106">非 SQL Server 訂閱者的異質性複寫已被取代。</span><span class="sxs-lookup"><span data-stu-id="c664b-106">Heterogeneous replication to non-SQL Server subscribers is deprecated.</span></span> <span data-ttu-id="c664b-107">Oracle 發行已被取代。</span><span class="sxs-lookup"><span data-stu-id="c664b-107">Oracle Publishing is deprecated.</span></span> <span data-ttu-id="c664b-108">若要移動資料，請使用異動資料擷取和 [!INCLUDE[ssIS](../../../includes/ssis-md.md)]建立方案。</span><span class="sxs-lookup"><span data-stu-id="c664b-108">To move data, create solutions using change data capture and [!INCLUDE[ssIS](../../../includes/ssis-md.md)].</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 <span data-ttu-id="c664b-109">從非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫發行對於下列狀況來說相當理想︰</span><span class="sxs-lookup"><span data-stu-id="c664b-109">Publishing from non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases is ideal for the following scenarios:</span></span>  
  
|<span data-ttu-id="c664b-110">案例</span><span class="sxs-lookup"><span data-stu-id="c664b-110">Scenario</span></span>|<span data-ttu-id="c664b-111">描述</span><span class="sxs-lookup"><span data-stu-id="c664b-111">Description</span></span>|  
|--------------|-----------------|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="c664b-112">.NET Framework 應用程式部署</span><span class="sxs-lookup"><span data-stu-id="c664b-112">.NET Framework application deployments</span></span>|<span data-ttu-id="c664b-113">使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 進行開發，同時操作從非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫複寫的資料。</span><span class="sxs-lookup"><span data-stu-id="c664b-113">Develop with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] while operating on data replicated from a non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>|  
|<span data-ttu-id="c664b-114">資料倉儲臨時伺服器</span><span class="sxs-lookup"><span data-stu-id="c664b-114">Data warehousing staging servers</span></span>|<span data-ttu-id="c664b-115">保持 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 臨時資料庫與非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫的同步處理。</span><span class="sxs-lookup"><span data-stu-id="c664b-115">Keep [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] staging databases synchronized with a non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>|  
|<span data-ttu-id="c664b-116">移轉至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c664b-116">Migration to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span></span>|<span data-ttu-id="c664b-117">在複寫來源系統的變更時，即時針對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 測試您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c664b-117">Test your application in real time against [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] while replicating the source system's changes.</span></span> <span data-ttu-id="c664b-118">完成移轉時切換至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c664b-118">Switch to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when satisfied with the migration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c664b-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c664b-119">See Also</span></span>  
 [<span data-ttu-id="c664b-120">異質資料庫複寫</span><span class="sxs-lookup"><span data-stu-id="c664b-120">Heterogeneous Database Replication</span></span>](heterogeneous-database-replication.md)  
  
  
