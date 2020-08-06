---
title: 將 UCP 從一個 SQL Server 執行個體移到另一個 (SQL Server 公用程式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b402fd9e-0bea-4c38-a371-6ed7fea12e96
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2cf17a79c9a1bb1bd7e86e1ecb36ef671414fb46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595965"
---
# <a name="move-a-ucp-from-one-instance-of-sql-server-to-another-sql-server-utility"></a><span data-ttu-id="ad986-102">將 UCP 從一個 SQL Server 執行個體移到另一個 (SQL Server 公用程式)</span><span class="sxs-lookup"><span data-stu-id="ad986-102">Move a UCP from One Instance of SQL Server to Another (SQL Server Utility)</span></span>
  <span data-ttu-id="ad986-103">此主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中的 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]執行個體之間移動公用程式控制點 (UCP)。</span><span class="sxs-lookup"><span data-stu-id="ad986-103">This topic describes how to move a utility control point (UCP) from one instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to another in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ad986-104">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ad986-104">Using SQL Server Management Studio</span></span>  
  
#### <a name="move-a-ucp-from-one-instance-of-sql-server-to-another"></a><span data-ttu-id="ad986-105">將 UCP 從一個 SQL Server 執行個體移到另一個</span><span class="sxs-lookup"><span data-stu-id="ad986-105">Move a UCP from one instance of SQL Server to another.</span></span>  
  
1.  <span data-ttu-id="ad986-106">在將會是新的 UCP 主機執行個體的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上建立新的 UCP。</span><span class="sxs-lookup"><span data-stu-id="ad986-106">Create a new UCP on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that will be the new host instance of the UCP.</span></span> <span data-ttu-id="ad986-107">如需詳細資訊，請參閱[建立 SQL Server 公用程式控制點 &#40;SQL Server 公用程式&#41;](create-a-sql-server-utility-control-point-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="ad986-107">For more information, see [Create a SQL Server Utility Control Point &#40;SQL Server Utility&#41;](create-a-sql-server-utility-control-point-sql-server-utility.md).</span></span>  
  
2.  <span data-ttu-id="ad986-108">如果您已經在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式內針對任何 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體設定非預設原則設定，請記下原則臨界值，好讓您可以在新的 UCP 上重新建立。</span><span class="sxs-lookup"><span data-stu-id="ad986-108">If non-default policy settings have been set for any instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, make note of the policy thresholds so that you can re-establish them on the new UCP.</span></span> <span data-ttu-id="ad986-109">當執行個體加入至新的 UCP 時，將會套用預設的原則。</span><span class="sxs-lookup"><span data-stu-id="ad986-109">Default policies are applied when instances are added to the new UCP.</span></span> <span data-ttu-id="ad986-110">如果預設原則有效， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式清單檢視會在 **[原則類型]** 資料行中顯示 **[全域]** 。</span><span class="sxs-lookup"><span data-stu-id="ad986-110">If default policies are in effect, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility list view displays **Global** in the **Policy Type** column.</span></span>  
  
3.  <span data-ttu-id="ad986-111">從舊的 UCP 中移除所有受管理的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ad986-111">Remove all managed instances from the old UCP.</span></span> <span data-ttu-id="ad986-112">如需詳細資訊，請參閱 [從 SQL Server 公用程式中移除 SQL Server 執行個體](remove-an-instance-of-sql-server-from-the-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="ad986-112">For more information, see [Remove an Instance of SQL Server from the SQL Server Utility](remove-an-instance-of-sql-server-from-the-sql-server-utility.md).</span></span>  
  
4.  <span data-ttu-id="ad986-113">從舊的 UCP 備份公用程式的管理資料倉儲 (UMDW)。</span><span class="sxs-lookup"><span data-stu-id="ad986-113">Back up the utility management data warehouse (UMDW) from the old UCP.</span></span> <span data-ttu-id="ad986-114">檔案名稱為 Sysutility_mdw_\<GUID>_DATA，且資料庫預設位置為 \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\，其中 \<System drive> 通常是 C:\ 磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ad986-114">The filename is Sysutility_mdw_\<GUID>_DATA, and the database default location is \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\, where \<System drive> is normally the C:\ drive.</span></span> <span data-ttu-id="ad986-115">如需詳細資訊，請參閱 [使用備份與還原複製資料庫](../databases/copy-databases-with-backup-and-restore.md)。</span><span class="sxs-lookup"><span data-stu-id="ad986-115">For more information, see [Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md).</span></span>  
  
5.  <span data-ttu-id="ad986-116">將 UMDW 的備份還原到新的 UCP。</span><span class="sxs-lookup"><span data-stu-id="ad986-116">Restore the backup of the UMDW to the new UCP.</span></span> <span data-ttu-id="ad986-117">如需詳細資訊，請參閱 [使用備份與還原複製資料庫](../databases/copy-databases-with-backup-and-restore.md)。</span><span class="sxs-lookup"><span data-stu-id="ad986-117">For more information, see [Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md).</span></span>  
  
6.  <span data-ttu-id="ad986-118">將執行個體註冊到新的 UCP，使其受 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式所管理。</span><span class="sxs-lookup"><span data-stu-id="ad986-118">Enroll instances into the new UCP to make them managed by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="ad986-119">如需詳細資訊，請參閱[註冊 SQL Server 的執行個體 &#40;SQL Server 公用程式&#41;](enroll-an-instance-of-sql-server-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="ad986-119">For more information, see [Enroll an Instance of SQL Server &#40;SQL Server Utility&#41;](enroll-an-instance-of-sql-server-sql-server-utility.md).</span></span>  
  
7.  <span data-ttu-id="ad986-120">必要時針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]受管理的執行個體實作自訂原則定義。</span><span class="sxs-lookup"><span data-stu-id="ad986-120">Implement custom policy definitions for the managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], as necessary.</span></span>  
  
8.  <span data-ttu-id="ad986-121">大約等候 1 小時，讓資料收集和彙總作業完成。</span><span class="sxs-lookup"><span data-stu-id="ad986-121">Wait approximately 1 hour for data collection and aggregation operations to complete.</span></span>  
  
9. <span data-ttu-id="ad986-122">若要重新整理資料，請以滑鼠右鍵按一下 [公用程式總管] 中的 [受管理的執行個體] 節點，然後選取 [重新整理]。</span><span class="sxs-lookup"><span data-stu-id="ad986-122">To refresh data, right-click the **Managed Instances** node in **Utility Explorer**, then select **Refresh**.</span></span> <span data-ttu-id="ad986-123">清單檢視資料會顯示在 **[公用程式總管]** 內容窗格中。</span><span class="sxs-lookup"><span data-stu-id="ad986-123">List view data are displayed in the **Utility Explorer** content pane.</span></span> <span data-ttu-id="ad986-124">如需詳細資訊，請參閱[檢視資源健全狀況原則結果 &#40;SQL Server 公用程式&#41;](view-resource-health-policy-results-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="ad986-124">For more information, see [View Resource Health Policy Results &#40;SQL Server Utility&#41;](view-resource-health-policy-results-sql-server-utility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad986-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad986-125">See Also</span></span>  
 <span data-ttu-id="ad986-126">[SQL Server 公用程式的功能與工作](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="ad986-126">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="ad986-127">註冊 SQL Server 的執行個體 &#40;SQL Server 公用程式&#41;</span><span class="sxs-lookup"><span data-stu-id="ad986-127">Enroll an Instance of SQL Server &#40;SQL Server Utility&#41;</span></span>](enroll-an-instance-of-sql-server-sql-server-utility.md)  
  
  
