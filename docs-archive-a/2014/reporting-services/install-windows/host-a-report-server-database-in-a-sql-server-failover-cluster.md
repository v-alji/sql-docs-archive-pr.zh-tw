---
title: 在 SQL Server 容錯移轉叢集中裝載報表伺服器資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 7bd5f019-2857-452f-a023-cc3b9e93aec4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 921ce03fd08e7820266b828d5848f64db1e257ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700840"
---
# <a name="host-a-report-server-database-in-a-sql-server-failover-cluster"></a><span data-ttu-id="493f8-102">在 SQL Server 容錯移轉叢集中裝載報表伺服器資料庫</span><span class="sxs-lookup"><span data-stu-id="493f8-102">Host a Report Server Database in a SQL Server Failover Cluster</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="493f8-103">提供容錯移轉叢集支援，可讓您針對一或多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體使用多個磁碟。</span><span class="sxs-lookup"><span data-stu-id="493f8-103">provides failover clustering support so that you can use multiple disks for one or more [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances.</span></span> <span data-ttu-id="493f8-104">只有報表伺服器資料庫才支援容錯移轉叢集。您無法將報表伺服器服務當做容錯移轉叢集的一部分執行。</span><span class="sxs-lookup"><span data-stu-id="493f8-104">Failover clustering is supported only for the report server database; you cannot run the Report Server service as part of a failover cluster.</span></span>  
  
 <span data-ttu-id="493f8-105">若要在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集上主控報表伺服器資料庫，必須已經安裝及設定該叢集。</span><span class="sxs-lookup"><span data-stu-id="493f8-105">To host a report server database on a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, the cluster must already be installed and configured.</span></span> <span data-ttu-id="493f8-106">然後，在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具的 [資料庫安裝] 頁面中建立報表伺服器資料庫時，您就可以選取容錯移轉叢集當做伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="493f8-106">You can then select the failover cluster as the server name when you create the report server database in the Database Setup page of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool.</span></span>  
  
 <span data-ttu-id="493f8-107">雖然報表伺服器服務無法參與容錯移轉叢集，但是您可以在已安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 容錯移轉叢集的電腦上安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="493f8-107">Although the Report Server service cannot participate in a failover cluster, you can install [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on a computer that has a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster installed.</span></span> <span data-ttu-id="493f8-108">報表伺服器的執行與容錯移轉叢集無關。</span><span class="sxs-lookup"><span data-stu-id="493f8-108">The report server runs independently of the failover cluster.</span></span> <span data-ttu-id="493f8-109">如果您在屬於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉執行個體之一部分的電腦上安裝報表伺服器，就不需要針對報表伺服器資料庫使用容錯移轉叢集。您可以使用不同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體來主控此資料庫。</span><span class="sxs-lookup"><span data-stu-id="493f8-109">If you install a report server on a computer that is part of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover instance, you are not required to use the failover cluster for the report server database; you can use a different [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to host the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="493f8-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="493f8-110">See Also</span></span>  
 <span data-ttu-id="493f8-111">[報表伺服器資料庫 &#40;SSRS 原生模式&#41;](../report-server/report-server-database-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="493f8-111">[Report Server Database &#40;SSRS Native Mode&#41;](../report-server/report-server-database-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="493f8-112">建立報表伺服器資料庫 &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="493f8-112">Create a Report Server Database  &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)  
  
  
