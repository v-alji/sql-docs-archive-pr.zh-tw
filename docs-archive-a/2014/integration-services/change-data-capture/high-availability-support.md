---
title: 高可用性支援 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 2e0f6d3f-0536-46d9-8630-835e199515bf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3075b300061b3d87b12a7cb3c4363b5e218f34d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687116"
---
# <a name="high-availability-support"></a><span data-ttu-id="f8e05-102">高可用性支援</span><span class="sxs-lookup"><span data-stu-id="f8e05-102">High Availability Support</span></span>
  <span data-ttu-id="f8e05-103">Oracle CDC 服務是專為高可用性所設計。</span><span class="sxs-lookup"><span data-stu-id="f8e05-103">The CDC Service for Oracle is designed for high availability.</span></span> <span data-ttu-id="f8e05-104">以下功能會提供部分高可用性支援：</span><span class="sxs-lookup"><span data-stu-id="f8e05-104">The following features provide part of the high availability support:</span></span>  
  
-   <span data-ttu-id="f8e05-105">Oracle CDC 服務不使用任何檔案資源 (本機或其他資源)。</span><span class="sxs-lookup"><span data-stu-id="f8e05-105">The CDC Service for Oracle does not use any file resource (local or otherwise).</span></span> <span data-ttu-id="f8e05-106">其完整狀態會儲存在目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中。</span><span class="sxs-lookup"><span data-stu-id="f8e05-106">Its entire state is stored in the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="f8e05-107">如此一來，如果執行此服務的電腦失敗，便可在使用相同 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的另一部電腦上輕鬆啟動此服務。</span><span class="sxs-lookup"><span data-stu-id="f8e05-107">This makes it easy to start the service on a different computer that uses the same [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance if the computer the service runs on fails.</span></span> <span data-ttu-id="f8e05-108">為了減少復原時間，長時間執行的 Oracle 交易會保留在目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的暫存資料表中，這樣就不需要在失敗之後重新掃描許多 Oracle 交易記錄 (或是重新啟動服務)。</span><span class="sxs-lookup"><span data-stu-id="f8e05-108">To reduce recovery time, long or long-running Oracle transactions are kept in a staging table in the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], preventing the need to re-scan many Oracle transaction logs following a failure (or service restart).</span></span>  
  
-   <span data-ttu-id="f8e05-109">Oracle CDC 服務可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 叢集執行個體，如此一來，它就可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體容錯移轉到另一個叢集節點時復原。</span><span class="sxs-lookup"><span data-stu-id="f8e05-109">The CDC Service for Oracle can use clustered [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances so it can recover after the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance fails over to another cluster node.</span></span> <span data-ttu-id="f8e05-110">在建立 Oracle CDC 服務時，Oracle CDC 服務電腦管理員只需要指定與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 叢集執行個體的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="f8e05-110">The Oracle CDC Service Computer Administrator only needs to specify the connection information to the clustered [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance when creating an Oracle CDC Service.</span></span>  
  
-   <span data-ttu-id="f8e05-111">Oracle CDC 服務可使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**AlwaysOn** 資料庫鏡像功能。</span><span class="sxs-lookup"><span data-stu-id="f8e05-111">The CDC Service for Oracle can use the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**AlwaysOn** database mirroring feature.</span></span> <span data-ttu-id="f8e05-112">此支援要求 MSXDBCDC 與所有 CDC 資料庫位於相同的可用性群組中。</span><span class="sxs-lookup"><span data-stu-id="f8e05-112">This support requires that the MSXDBCDC and all the CDC databases are in the same availability group.</span></span> <span data-ttu-id="f8e05-113">它也需要 Oracle CDC 服務電腦系統管理員指定可用性群組的適當**AlwaysOn**連接資訊 (例如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，連接屬性 `Failover_Partner and Network=dbmssocn`) 。</span><span class="sxs-lookup"><span data-stu-id="f8e05-113">It also requires the Oracle CDC Service Computer Administrator to specify the appropriate **AlwaysOn** connection information to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] availability group (for example, the connection properties `Failover_Partner and Network=dbmssocn`).</span></span> <span data-ttu-id="f8e05-114">這樣可讓 CDC 服務在容錯移轉之後，自動繼續資料庫次要複寫的處理。</span><span class="sxs-lookup"><span data-stu-id="f8e05-114">This allows the CDC service to automatically resume processing on a secondary replication of the databases following a failover.</span></span>  
  
-   <span data-ttu-id="f8e05-115">Oracle CDC 服務可設定為 Windows 容錯移轉叢集上的一般服務資源 (與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]一起或分開)，這樣 CDC 對叢集的容錯移轉和退讓處理就會很輕鬆。</span><span class="sxs-lookup"><span data-stu-id="f8e05-115">The CDC Service for Oracle can be configured as a generic service resource on a Windows failover cluster (along with, or separate from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), making it simple to fail over and fall back CDC processing with the cluster.</span></span> <span data-ttu-id="f8e05-116">若要將 Oracle CDC 服務設定為容錯移轉叢集中的資源，系統管理員必須將 Oracle CDC 服務設定為容錯移轉叢集上每一個節點中的一般服務資源。</span><span class="sxs-lookup"><span data-stu-id="f8e05-116">To configure the CDC Service for Oracle as a resource in a failover cluster, the system administrator must set the CDC Service for Oracle as a Generic Service Resource on each node on the failover cluster.</span></span>  
  
-   <span data-ttu-id="f8e05-117">Oracle CDC 服務支援 Oracle RAC，好讓它與 Oracle 資料庫通訊並處理記錄，即使當其中一個 Oracle RAC 節點關閉時也是如此。</span><span class="sxs-lookup"><span data-stu-id="f8e05-117">The CDC Service for Oracle supports Oracle RAC, which allows it to communicate with the Oracle database and process logs even when one of the Oracle RAC nodes is down.</span></span>  
  
  
