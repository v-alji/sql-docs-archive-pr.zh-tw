---
title: 異質資料庫複寫 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- heterogeneous database replication, about heterogeneous database replication
- replication [SQL Server], heterogeneous database replication
- heterogeneous database replication
ms.assetid: 3fd983ad-e206-45db-9054-417c9b5bb815
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d8988a425bc9519d43b8100e4cd34418114edae1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705013"
---
# <a name="heterogeneous-database-replication"></a><span data-ttu-id="621f8-102">異質資料庫複寫</span><span class="sxs-lookup"><span data-stu-id="621f8-102">Heterogeneous Database Replication</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="621f8-103">支援下列交易式與快照式複寫的異質性情況：</span><span class="sxs-lookup"><span data-stu-id="621f8-103">supports the following heterogeneous scenarios for transactional and snapshot replication:</span></span>  
  
-   <span data-ttu-id="621f8-104">將資料從 Oracle 發行到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="621f8-104">Publishing data from Oracle to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="621f8-105">將資料從 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 發行到非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的訂閱者</span><span class="sxs-lookup"><span data-stu-id="621f8-105">Publishing data from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers.</span></span>  
  
 <span data-ttu-id="621f8-106">非 SQL Server 訂閱者的異質性複寫已被取代。</span><span class="sxs-lookup"><span data-stu-id="621f8-106">Heterogeneous replication to non-SQL Server subscribers is deprecated.</span></span> <span data-ttu-id="621f8-107">Oracle 發行已被取代。</span><span class="sxs-lookup"><span data-stu-id="621f8-107">Oracle Publishing is deprecated.</span></span> <span data-ttu-id="621f8-108">若要移動資料，請使用異動資料擷取和 [!INCLUDE[ssIS](../../../includes/ssis-md.md)]建立方案。</span><span class="sxs-lookup"><span data-stu-id="621f8-108">To move data, create solutions using change data capture and [!INCLUDE[ssIS](../../../includes/ssis-md.md)].</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="publishing-data-from-oracle"></a><span data-ttu-id="621f8-109">從 Oracle 發行資料</span><span class="sxs-lookup"><span data-stu-id="621f8-109">Publishing Data from Oracle</span></span>  
 <span data-ttu-id="621f8-110">您可以使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 從大部份功能及易用性皆與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 快照式和異動複寫相同的 Oracle 中發行資料。</span><span class="sxs-lookup"><span data-stu-id="621f8-110">You can use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to publish data from Oracle with most of the same features and ease-of-use as [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] snapshot and transactional replication.</span></span> <span data-ttu-id="621f8-111">下列狀況適合從 Oracle 發行資料：</span><span class="sxs-lookup"><span data-stu-id="621f8-111">Publishing data from Oracle is ideal for the following scenarios:</span></span>  
  
|<span data-ttu-id="621f8-112">狀況</span><span class="sxs-lookup"><span data-stu-id="621f8-112">Scenario</span></span>|<span data-ttu-id="621f8-113">描述</span><span class="sxs-lookup"><span data-stu-id="621f8-113">Description</span></span>|  
|--------------|-----------------|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="621f8-114">.NET Framework 應用程式部署</span><span class="sxs-lookup"><span data-stu-id="621f8-114">.NET Framework application deployments</span></span>|<span data-ttu-id="621f8-115">使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 進行開發，同時操作從非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫複寫的資料。</span><span class="sxs-lookup"><span data-stu-id="621f8-115">Develop with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] while operating on data replicated from a non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>|  
|<span data-ttu-id="621f8-116">資料倉儲臨時伺服器</span><span class="sxs-lookup"><span data-stu-id="621f8-116">Data warehousing staging servers</span></span>|<span data-ttu-id="621f8-117">保持 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 臨時資料庫與非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫的同步處理。</span><span class="sxs-lookup"><span data-stu-id="621f8-117">Keep [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] staging databases synchronized with a non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>|  
|<span data-ttu-id="621f8-118">移轉至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="621f8-118">Migration to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span></span>|<span data-ttu-id="621f8-119">在複寫來源系統的變更時，即時針對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 測試您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="621f8-119">Test your application in real time against [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] while replicating the source system's changes.</span></span> <span data-ttu-id="621f8-120">完成移轉時切換至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="621f8-120">Switch to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when satisfied with the migration.</span></span>|  
  
 <span data-ttu-id="621f8-121">如需詳細資訊，請參閱 [Oracle 發行概觀](oracle-publishing-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="621f8-121">For more information, see [Oracle Publishing Overview](oracle-publishing-overview.md).</span></span>  
  
## <a name="publishing-data-to-non-sql-server-subscribers"></a><span data-ttu-id="621f8-122">將資料發行至非 SQL Server 訂閱者</span><span class="sxs-lookup"><span data-stu-id="621f8-122">Publishing Data to Non-SQL Server Subscribers</span></span>  
 <span data-ttu-id="621f8-123">下列非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫做為快照式和交易式發行集的「訂閱者」得到支援：</span><span class="sxs-lookup"><span data-stu-id="621f8-123">The following non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases are supported as Subscribers to snapshot and transactional publications:</span></span>  
  
-   <span data-ttu-id="621f8-124">Oracle 支援之所有平台的 Oracle。</span><span class="sxs-lookup"><span data-stu-id="621f8-124">Oracle for all platforms that Oracle supports.</span></span>  
  
-   <span data-ttu-id="621f8-125">IBM DB2 (適用於 AS400、MVS、Unix、Linux 和 Windows)。</span><span class="sxs-lookup"><span data-stu-id="621f8-125">IBM DB2 for AS400, MVS, Unix, Linux, and Windows.</span></span>  
  
 <span data-ttu-id="621f8-126">如需詳細資訊，請參閱 [Non-SQL Server Subscribers](non-sql-server-subscribers.md)。</span><span class="sxs-lookup"><span data-stu-id="621f8-126">For more information, see [Non-SQL Server Subscribers](non-sql-server-subscribers.md).</span></span>  
  
  
