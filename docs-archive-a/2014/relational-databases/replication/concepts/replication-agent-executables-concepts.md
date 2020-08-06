---
title: 複寫代理程式可執行檔概念 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: reference
helpviewer_keywords:
- programming interfaces [SQL Server replication]
- programming [SQL Server replication], agents
- replication [SQL Server], agents and profiles
- agents [SQL Server replication], executables
- command prompt [SQL Server replication]
ms.assetid: cba476df-d4ea-44c9-bb86-81488971e328
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 73f9fe0d1a98fa1afc813cd113dcced685b4f98a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709214"
---
# <a name="replication-agent-executables-concepts"></a><span data-ttu-id="919e8-102">複寫代理程式可執行檔概念</span><span class="sxs-lookup"><span data-stu-id="919e8-102">Replication Agent Executables Concepts</span></span>
  <span data-ttu-id="919e8-103">複寫代理程式可以用下列方式以程式設計方式來控制：</span><span class="sxs-lookup"><span data-stu-id="919e8-103">Replication agents can be controlled programmatically in the following ways:</span></span>  
  
-   <span data-ttu-id="919e8-104">在 <xref:Microsoft.SqlServer.Replication> 命名空間中使用 Managed 代理程式來程式設計介面。</span><span class="sxs-lookup"><span data-stu-id="919e8-104">Using the managed agent programming interfaces in the <xref:Microsoft.SqlServer.Replication> Namespace.</span></span>  
  
-   <span data-ttu-id="919e8-105">從命令提示字元以一組提供的參數來叫用代理程式可執行檔。</span><span class="sxs-lookup"><span data-stu-id="919e8-105">Invoking agent executable files from the command prompt with a supplied set of parameters.</span></span>  
  
 <span data-ttu-id="919e8-106">從命令提示字元直接叫用複寫代理程式，可讓代理程式從批次檔的命令列指令碼中以程式設計的方式存取。</span><span class="sxs-lookup"><span data-stu-id="919e8-106">Directly invoking replication agents from the command prompt enables agents to be programmatically accessed from command-line scripting in batch files.</span></span> <span data-ttu-id="919e8-107">從命令提示字元叫用代理程式時，它會在叫用代理程式或是啟動批次檔之該使用者的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 安全性帳戶之下執行。</span><span class="sxs-lookup"><span data-stu-id="919e8-107">When an agent is invoked from the command prompt, it runs under the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows security account of the user that invoked the agent or started the batch file.</span></span>  
  
 <span data-ttu-id="919e8-108">下列複寫代理程式的執行個體，可以使用可執行檔來執行。</span><span class="sxs-lookup"><span data-stu-id="919e8-108">Instances of the following replication agents can be run using executable files.</span></span>  
  
-   [<span data-ttu-id="919e8-109">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="919e8-109">Replication Distribution Agent</span></span>](../agents/replication-distribution-agent.md)  
  
-   [<span data-ttu-id="919e8-110">複寫記錄讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="919e8-110">Replication Log Reader Agent</span></span>](../agents/replication-log-reader-agent.md)  
  
-   [<span data-ttu-id="919e8-111">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="919e8-111">Replication Merge Agent</span></span>](../agents/replication-merge-agent.md)  
  
-   [<span data-ttu-id="919e8-112">複寫佇列讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="919e8-112">Replication Queue Reader Agent</span></span>](../agents/replication-queue-reader-agent.md)  
  
-   [<span data-ttu-id="919e8-113">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="919e8-113">Replication Snapshot Agent</span></span>](../agents/replication-snapshot-agent.md)  
  
 <span data-ttu-id="919e8-114">叫用複寫代理程式時，您可以使用效能設定檔，將一組定義的參數自動傳遞到代理程式可執行檔。</span><span class="sxs-lookup"><span data-stu-id="919e8-114">When invoking replication agents, you can use performance profiles to automatically pass a defined set of parameters to the agent executable.</span></span> <span data-ttu-id="919e8-115">如需相關資訊，請參閱 [Replication Agent Profiles](../agents/replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="919e8-115">For more information, see [Replication Agent Profiles](../agents/replication-agent-profiles.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="919e8-116">範例</span><span class="sxs-lookup"><span data-stu-id="919e8-116">Examples</span></span>  
 <span data-ttu-id="919e8-117">下列範例顯示如何從命令提示字元叫用複寫代理程式。</span><span class="sxs-lookup"><span data-stu-id="919e8-117">The following examples show how to invoke replication agents from the command prompt.</span></span> <span data-ttu-id="919e8-118">複寫代理程式也可以透過 Replication Management Objects (RMO) 來叫用。</span><span class="sxs-lookup"><span data-stu-id="919e8-118">Replication agents can also be invoked using Replication Management Objects (RMO).</span></span> <span data-ttu-id="919e8-119">如需詳細資訊，請參閱[同步處理訂閱 &#40;複寫&#41;](../synchronize-data.md)。</span><span class="sxs-lookup"><span data-stu-id="919e8-119">For more information, see [Synchronize Subscriptions &#40;Replication&#41;](../synchronize-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="919e8-120">在這些範例中加入了分行符號，以提升可讀性。</span><span class="sxs-lookup"><span data-stu-id="919e8-120">Line breaks in these examples were added to improve readability.</span></span> <span data-ttu-id="919e8-121">在批次檔中，必須在單一行中撰寫命令。</span><span class="sxs-lookup"><span data-stu-id="919e8-121">In a batch file, commands must be made in a single line.</span></span>  
  
### <a name="running-the-snapshot-agent"></a><span data-ttu-id="919e8-122">執行快照集代理程式。</span><span class="sxs-lookup"><span data-stu-id="919e8-122">Running the Snapshot Agent</span></span>  
 <span data-ttu-id="919e8-123">這個範例批次檔會從命令提示字元叫用「快照集代理程式」，以產生 **AdvWorksSalesOrdersMerge** 發行集的快照集</span><span class="sxs-lookup"><span data-stu-id="919e8-123">This example batch file invokes the Snapshot Agent from the command prompt to generate a snapshot for the **AdvWorksSalesOrdersMerge** publication.</span></span>  
  
```  
REM -- Declare variables  
SET Publisher=%InstanceName%;  
SET PublicationDB=AdventureWorks2012;   
SET Publication=AdvWorksSalesOrdersMerge;   
  
REM --Start the Snapshot Agent to generate the snapshot for AdvWorksSalesOrdersMerge.  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %Publication%   
-Publisher %Publisher% -Distributor %Publisher% -PublisherDB %PublicationDB%   
-ReplicationType 2 -OutputVerboseLevel 1 -DistributorSecurityMode 1 ;  
  
```  
  
### <a name="running-the-distribution-agent"></a><span data-ttu-id="919e8-124">執行散發代理程式。</span><span class="sxs-lookup"><span data-stu-id="919e8-124">Running the Distribution Agent</span></span>  
 <span data-ttu-id="919e8-125">這個範例批次檔會從命令提示字元叫用「散發代理程式」，以繼續從 **AdvWorksProductTran** 發行集將變更複寫到發送訂閱者。</span><span class="sxs-lookup"><span data-stu-id="919e8-125">This example batch file invokes the Distribution Agent from the command prompt to continuously replicate changes from the **AdvWorksProductTran** publication to a push subscriber.</span></span>  
  
```  
REM -- Declare the variables.  
SET Publisher=%instancename%;  
SET Subscriber=%instancename%;  
SET PublicationDB=AdventureWorks2012;  
SET SubscriptionDB=AdventureWorks2012Replica;   
SET Publication=AdvWorksProductsTran;  
  
REM -- Start the Distribution Agent with four subscription streams.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\DISTRIB.EXE" -Subscriber %Subscriber%   
-SubscriberDB %SubscriptionDB% -SubscriberSecurityMode 1 -Publication %Publication%   
-Publisher %Publisher% -PublisherDB %PublicationDB% -Distributor %Publisher%   
-DistributorSecurityMode 1 -Continuous -SubscriptionType 0 -SubscriptionStreams 4 ;  
  
```  
  
### <a name="running-the-merge-agent"></a><span data-ttu-id="919e8-126">執行合併代理程式</span><span class="sxs-lookup"><span data-stu-id="919e8-126">Running the Merge Agent</span></span>  
 <span data-ttu-id="919e8-127">這個範例批次檔會從命令提示字元叫用「合併代理程式」，以將提取訂閱同步處理到 **AdvWorksSalesOrdersMerge** 發行集。</span><span class="sxs-lookup"><span data-stu-id="919e8-127">This example batch file invokes the Merge Agent from the command prompt to synchronize a pull subscription to the **AdvWorksSalesOrdersMerge** publication.</span></span>  
  
```  
REM -- Declare the variables.  
SET Publisher=%instancename%;  
SET Subscriber=%instancename%;  
SET PublicationDB=AdventureWorks2012;  
SET SubscriptionDB=AdventureWorks2012Replica;   
SET Publication=AdvWorksSalesOrdersMerge;  
  
REM --Start the Merge Agent with concurrent upload and download processes.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE" -Publication %Publication%    
-Publisher %Publisher%  -Subscriber  %Subscriber%  -Distributor %Publisher%    
-PublisherDB %PublicationDB%  -SubscriberDB %SubscriptionDB% -PublisherSecurityMode 1    
-OutputVerboseLevel 2  -SubscriberSecurityMode 1  -SubscriptionType 1 -DistributorSecurityMode 1    
-Validate 3  -ParallelUploadDownload 1 ;  
  
```  
  
  
