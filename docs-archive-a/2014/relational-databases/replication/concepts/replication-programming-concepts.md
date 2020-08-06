---
title: 複寫程式設計概念 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: reference
helpviewer_keywords:
- replication [SQL Server], planning
- programming [SQL Server replication], planning
- programming [SQL Server replication]
ms.assetid: 2cd846e7-5bf3-4144-8772-703c4f439a2a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: db4ab6196c138eaf21de08afc27731225df398e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595919"
---
# <a name="replication-programming-concepts"></a><span data-ttu-id="1cb8c-102">複寫程式設計概念</span><span class="sxs-lookup"><span data-stu-id="1cb8c-102">Replication Programming Concepts</span></span>
  <span data-ttu-id="1cb8c-103">在開發使用複寫功能的應用程式之前，您應該遵循下列一般規劃步驟：</span><span class="sxs-lookup"><span data-stu-id="1cb8c-103">Before developing an application that uses replication functionalities, you should follow the following general planning steps:</span></span>  
  
1.  <span data-ttu-id="1cb8c-104">定義您的複寫拓撲。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-104">Define your replication topology.</span></span>  
  
2.  <span data-ttu-id="1cb8c-105">定義應用程式功能。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-105">Define application functionality.</span></span>  
  
3.  <span data-ttu-id="1cb8c-106">規劃安全性。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-106">Plan for security.</span></span>  
  
4.  <span data-ttu-id="1cb8c-107">選擇開發環境。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-107">Choose a development environment.</span></span>  
  
5.  <span data-ttu-id="1cb8c-108">選擇適當的複寫程式設計介面。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-108">Choose the appropriate replication programming interface.</span></span>  
  
 <span data-ttu-id="1cb8c-109">本主題的其餘部分將更詳細地描述這些步驟。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-109">The rest of this topic describes these steps in more detail.</span></span> <span data-ttu-id="1cb8c-110">為了說明規劃程序，本主題中還包括範例。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-110">To help illustrate the planning process, an example has been included.</span></span>  
  
## <a name="defining-the-replication-topology"></a><span data-ttu-id="1cb8c-111">定義複寫拓撲</span><span class="sxs-lookup"><span data-stu-id="1cb8c-111">Defining the Replication Topology</span></span>  
 <span data-ttu-id="1cb8c-112">程式設計複寫中的第一個步驟，是為應用程式定義複寫拓撲。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-112">The first step in programming replication is to define the replication topology for your application.</span></span> <span data-ttu-id="1cb8c-113">如果您正在撰寫將使用現有複寫拓撲的應用程式，例如存取現有訂閱者資料的用戶端應用程式，您應該移到下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-113">If you are writing an application that will use an existing replication topology, such as a client application that accesses data at an existing subscriber, you should move onto the next step.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1cb8c-114">在某些情況下，部署複寫拓撲將是應用程式的唯一目的。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-114">In some cases, deploying the replication topology will be the sole purpose of the application.</span></span>  
  
 <span data-ttu-id="1cb8c-115">您定義的複寫拓撲取決於許多因素，其中包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="1cb8c-115">The replication topology that you define depends on many factors, including the following:</span></span>  
  
-   <span data-ttu-id="1cb8c-116">是否需要更新複寫的資料以及由誰來更新。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-116">Whether or not replicated data needs to be updated, and by whom.</span></span>  
  
-   <span data-ttu-id="1cb8c-117">有關您的一致性、自主性和延遲的資料散發需求。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-117">Your data distribution needs regarding consistency, autonomy, and latency.</span></span>  
  
-   <span data-ttu-id="1cb8c-118">複寫環境，包括商務使用者、技術基礎結構、網路與安全性以及資料特性。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-118">The replication environment, including business users, technical infrastructure, network and security, and data characteristics.</span></span>  
  
-   <span data-ttu-id="1cb8c-119">複寫及複寫選項的類型。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-119">The types of replication and replication options.</span></span>  
  
-   <span data-ttu-id="1cb8c-120">複寫拓撲以及它們如何搭配複寫類型使用。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-120">The replication topologies and how they align with the types of replication.</span></span>  
  
 <span data-ttu-id="1cb8c-121">如果您不熟悉 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 複寫，請參閱[複寫類型](../types-of-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-121">If you are new to [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication, see [Types of Replication](../types-of-replication.md).</span></span>  
  
## <a name="defining-application-functionality"></a><span data-ttu-id="1cb8c-122">定義應用程式功能</span><span class="sxs-lookup"><span data-stu-id="1cb8c-122">Defining Application Functionality</span></span>  
 <span data-ttu-id="1cb8c-123">定義好複寫拓撲之後，您應該決定應用程式將提供的功能。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-123">Once the replication topology has been defined, you should decide on the functionalities that your application will offer.</span></span> <span data-ttu-id="1cb8c-124">這些功能包括的範圍可從同步處理訂閱的指令碼，到具有使用者介面以設定複寫的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-124">These functionalities can range from a script that synchronizes a subscription to an application with a user interface to configure replication.</span></span> <span data-ttu-id="1cb8c-125">複寫支援下列一般程式設計工作：</span><span class="sxs-lookup"><span data-stu-id="1cb8c-125">Replication supports the following general programming tasks:</span></span>  
  
-   <span data-ttu-id="1cb8c-126">設定複寫。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-126">Setting up replication.</span></span>  
  
-   <span data-ttu-id="1cb8c-127">同步處理訂閱者。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-127">Synchronizing Subscribers.</span></span>  
  
-   <span data-ttu-id="1cb8c-128">維護複寫拓撲。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-128">Maintaining a replication topology.</span></span>  
  
-   <span data-ttu-id="1cb8c-129">監視複寫拓撲。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-129">Monitoring a replication topology.</span></span>  
  
-   <span data-ttu-id="1cb8c-130">疑難排解複寫。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-130">Troubleshooting replication.</span></span>  
  
 <span data-ttu-id="1cb8c-131">透過結合複寫功能與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 提供的其他功能來擴充應用程式，也是很常見的事。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-131">It is also common extend your application by combining replication functionalities with other functionalities provided by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1cb8c-132">下表僅挑出一些您可在複寫應用程式中提供的擴充功能。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-132">The following table highlights some extended functionalities that you might provide in your replication application.</span></span>  
  
|<span data-ttu-id="1cb8c-133">功能</span><span class="sxs-lookup"><span data-stu-id="1cb8c-133">Functionality</span></span>|<span data-ttu-id="1cb8c-134">範例</span><span class="sxs-lookup"><span data-stu-id="1cb8c-134">Example</span></span>|  
|-------------------|-------------|  
|<span data-ttu-id="1cb8c-135">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理物件 (SMO) 的伺服器管理</span><span class="sxs-lookup"><span data-stu-id="1cb8c-135">Server administration using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO)</span></span>|<span data-ttu-id="1cb8c-136">允許管理員在複寫拓撲中將資料庫附加並設定為發行者的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-136">An application that enables an administrator to attach and configure a database as a Publisher in a replication topology.</span></span>|  
|<span data-ttu-id="1cb8c-137">使用 ADO.NET 的資料存取</span><span class="sxs-lookup"><span data-stu-id="1cb8c-137">Data access using ADO.NET</span></span>|<span data-ttu-id="1cb8c-138">這個應用程式允許使用者在離線時於本機訂閱者資料庫中，以程式設計方式存取和變更複寫的銷售資料，然後按一下按鈕連接和同步處理提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-138">An application that enables users to programmatically access and change replicated sales data in a local Subscriber database while offline and then connect and synchronize the pull subscription by clicking a button.</span></span>|  
  
## <a name="planning-for-security"></a><span data-ttu-id="1cb8c-139">安全性規劃</span><span class="sxs-lookup"><span data-stu-id="1cb8c-139">Planning for Security</span></span>  
 <span data-ttu-id="1cb8c-140">安全性在任何應用程式中都很重要，而且安全性的規劃應該在撰寫任何程式碼之前先完成。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-140">Security is important in any application, and planning for security should be completed before writing any code.</span></span> <span data-ttu-id="1cb8c-141">應用程式安全性可以分成三個主要的部分：保護資料庫的安全、保護複寫的安全以及撰寫安全的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-141">Application security can be divided into three main parts: securing the database, securing replication, and writing secure code.</span></span>  
  
 <span data-ttu-id="1cb8c-142">下列主題提供有關安全性的資訊：</span><span class="sxs-lookup"><span data-stu-id="1cb8c-142">The following topics provide information on security:</span></span>  
  
-   [<span data-ttu-id="1cb8c-143">SQL Server 複寫安全性</span><span class="sxs-lookup"><span data-stu-id="1cb8c-143">SQL Server Replication Security</span></span>](../security/view-and-modify-replication-security-settings.md)  
  
-   [<span data-ttu-id="1cb8c-144">SQL Server Database Engine 和 Azure SQL Database 的資訊安全中心</span><span class="sxs-lookup"><span data-stu-id="1cb8c-144">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](../../security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
## <a name="choosing-a-development-environment"></a><span data-ttu-id="1cb8c-145">選擇開發環境</span><span class="sxs-lookup"><span data-stu-id="1cb8c-145">Choosing a Development Environment</span></span>  
 <span data-ttu-id="1cb8c-146">當開發複寫應用程式時，有三個要考慮的基本開發環境。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-146">When developing a replication application, there are three basic development environments to consider.</span></span> <span data-ttu-id="1cb8c-147">每個開發環境都可以存取相同的複寫功能，但有一些例外。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-147">Each development environment has access to the same replication functionalities with some exceptions.</span></span> <span data-ttu-id="1cb8c-148">複寫應用程式可以在下列每個環境中開發。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-148">Replication applications can be developed in each of the following environments.</span></span>  
  
-   <span data-ttu-id="1cb8c-149">**Managed 程式碼**</span><span class="sxs-lookup"><span data-stu-id="1cb8c-149">**Managed code**</span></span>  
  
     <span data-ttu-id="1cb8c-150">物件導向開發環境，利用 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 程式設計與 .NET Common Language Runtime (CLR) 的優點。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-150">Object oriented development environment that leverages the benefits of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] programming and the .NET common language runtime (CLR).</span></span> <span data-ttu-id="1cb8c-151">Managed 程式碼是 .NET 開發與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 應用程式建議的程式設計環境。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-151">Managed code is the recommended programming environment for both .NET development and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] applications.</span></span> <span data-ttu-id="1cb8c-152">Managed 複寫介面允許以物件導向的方式設計複寫管理的程式，而無須了解 [!INCLUDE[tsql](../../../includes/tsql-md.md)]，而且當執行無法從指令碼中取得的複寫代理程式時，也提供一些回撥功能。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-152">Managed replication interfaces enable the programming of replication administration in an object-oriented manner without having to know [!INCLUDE[tsql](../../../includes/tsql-md.md)], and it also provides some callback functionalities when running replication agents that are not available from scripts.</span></span> <span data-ttu-id="1cb8c-153">Managed 程式碼是開發可重複使用元件與使用者介面應用程式的最佳環境。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-153">Managed code is the best environment for developing reusable components and user interface applications.</span></span>  
  
-   <span data-ttu-id="1cb8c-154">**指令碼**</span><span class="sxs-lookup"><span data-stu-id="1cb8c-154">**Scripting**</span></span>  
  
     <span data-ttu-id="1cb8c-155">簡單的應用程式，可將一系列的命令以 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 指令碼的複寫系統預存程序或是批次檔中的命令來執行。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-155">Simple applications that execute a series of commands as either replication system stored procedures in [!INCLUDE[tsql](../../../includes/tsql-md.md)] scripts or commands in batch files.</span></span> <span data-ttu-id="1cb8c-156">雖然您可以使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 同處理序 Managed 提供者在 Managed 環境中執行指令碼，不過也可以使用有提供回撥功能之 Managed 複寫介面來取得相同的功能。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-156">While you can execute scripts in a managed environment using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in-process managed provider, the same functionality can obtained by using managed replication interfaces, which also provide callback functionalities.</span></span> <span data-ttu-id="1cb8c-157">執令碼是執行將只會執行數次且不需要回撥功能的工作之最佳環境，例如安裝複寫伺服器。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-157">Scripting is the best environment for executing tasks that will run only a few times and where callback functionalities are not required, such as installing a replication server.</span></span>  
  
-   <span data-ttu-id="1cb8c-158">**機器碼**</span><span class="sxs-lookup"><span data-stu-id="1cb8c-158">**Native code**</span></span>  
  
     <span data-ttu-id="1cb8c-159">物件導向開發環境，利用系統或是 COM 物件的直接存取，例如不是由 CLR 管理的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-159">Object-oriented development environment that utilizes direct access to the system or COM objects such that code is not managed by the CLR.</span></span> <span data-ttu-id="1cb8c-160">機器碼複寫介面已被取代或停止提供。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-160">Native code replication interfaces are deprecated or discontinued.</span></span> <span data-ttu-id="1cb8c-161">如需詳細資訊，請參閱 [SQL Server 複寫中已被取代的功能](../deprecated-features-in-sql-server-replication.md)或[複寫回溯相容性](../replication-backward-compatibility.md)。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-161">For more information, see [Deprecated Features in SQL Server Replication](../deprecated-features-in-sql-server-replication.md) or [Replication Backward Compatibility](../replication-backward-compatibility.md).</span></span>  
  
## <a name="choose-the-appropriate-replication-programming-interface"></a><span data-ttu-id="1cb8c-162">選擇適當的複寫程式設計介面。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-162">Choose the Appropriate Replication Programming Interface</span></span>  
 <span data-ttu-id="1cb8c-163">最後的規劃步驟是選擇適當的複寫程式設計介面，來為選擇的開發環境實作所需的複寫功能。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-163">The final planning step is choosing the appropriate replication programming interface that implements the desired replication functionality for the chosen development environment.</span></span> <span data-ttu-id="1cb8c-164">下表顯示可用的複寫程式設計介面。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-164">The following table shows the replication programming interfaces available.</span></span>  
  
|<span data-ttu-id="1cb8c-165">介面</span><span class="sxs-lookup"><span data-stu-id="1cb8c-165">Interface</span></span>|<span data-ttu-id="1cb8c-166">環境</span><span class="sxs-lookup"><span data-stu-id="1cb8c-166">Environment</span></span>|<span data-ttu-id="1cb8c-167">使用</span><span class="sxs-lookup"><span data-stu-id="1cb8c-167">Uses</span></span>|  
|---------------|-----------------|----------|  
|[<span data-ttu-id="1cb8c-168">複寫管理物件概念</span><span class="sxs-lookup"><span data-stu-id="1cb8c-168">Replication Management Objects Concepts</span></span>](replication-management-objects-concepts.md)|<span data-ttu-id="1cb8c-169">Managed 程式碼</span><span class="sxs-lookup"><span data-stu-id="1cb8c-169">Managed code</span></span>|<span data-ttu-id="1cb8c-170">管理、監視和同步處理。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-170">Administration, monitoring, and synchronization.</span></span>|  
|<xref:Microsoft.SqlServer.Replication>|<span data-ttu-id="1cb8c-171">Managed 程式碼</span><span class="sxs-lookup"><span data-stu-id="1cb8c-171">Managed code</span></span>|<span data-ttu-id="1cb8c-172">同步處理。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-172">Synchronization.</span></span>|  
|<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|<span data-ttu-id="1cb8c-173">Managed 程式碼</span><span class="sxs-lookup"><span data-stu-id="1cb8c-173">Managed code</span></span>|<span data-ttu-id="1cb8c-174">建立商務邏輯處理常式，以整合自訂邏輯及合併同步處理：</span><span class="sxs-lookup"><span data-stu-id="1cb8c-174">Creation of business logic handlers to integrate custom logic with the merge synchronization process.</span></span>|  
|[<span data-ttu-id="1cb8c-175">複寫預存程序 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1cb8c-175">Replication Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql)|<span data-ttu-id="1cb8c-176">指令碼</span><span class="sxs-lookup"><span data-stu-id="1cb8c-176">Scripting</span></span>|<span data-ttu-id="1cb8c-177">管理和監視。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-177">Administration and monitoring.</span></span>|  
|[<span data-ttu-id="1cb8c-178">Replication Agent Executables Concepts</span><span class="sxs-lookup"><span data-stu-id="1cb8c-178">Replication Agent Executables Concepts</span></span>](replication-agent-executables-concepts.md)|<span data-ttu-id="1cb8c-179">指令碼</span><span class="sxs-lookup"><span data-stu-id="1cb8c-179">Scripting</span></span>|<span data-ttu-id="1cb8c-180">同步處理。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-180">Synchronization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1cb8c-181">範例</span><span class="sxs-lookup"><span data-stu-id="1cb8c-181">Example</span></span>  
 <span data-ttu-id="1cb8c-182">在 [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)]，需要為全世界的 200 位銷售代表發行資料。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-182">At [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)], data needs to be published for 200 sales representatives around the world.</span></span> <span data-ttu-id="1cb8c-183">銷售代表經常需要出差，而且將需要使用膝上型電腦或是個人數位助理 (PDA) 來變更客戶資料和增加新訂單。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-183">The sales representatives travel often and will need to use laptop computers or personal digital assistants (PDAs) to change customer data and add new orders.</span></span> <span data-ttu-id="1cb8c-184">銷售代表將膝上型電腦連接到網路時，將需要與發行者同步處理變更。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-184">The changes will then need to be synchronized with the Publisher when the sales representative connects the laptop to the network.</span></span>  
  
 <span data-ttu-id="1cb8c-185">就這個應用程式而言，規劃步驟可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="1cb8c-185">For this application, the planning steps might look like the following:</span></span>  
  
1.  <span data-ttu-id="1cb8c-186">這個應用程式的複寫拓撲已經存在。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-186">The replication topology for this application already exists.</span></span> <span data-ttu-id="1cb8c-187">不過，在用戶端必須建立新的提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-187">However, a new pull subscription must be created at the client.</span></span> <span data-ttu-id="1cb8c-188">發行集應該使用參數化的篩選，來將唯一的資料集複寫到每個銷售代表。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-188">The publication should use parameterized filters to replicate a unique set of data to each sales representative.</span></span>  
  
2.  <span data-ttu-id="1cb8c-189">除了銷售應用程式所需的一般資料存取之外，此應用程式應該允許銷售人員按一下按鈕，視需要同步處理提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-189">In addition to the typical data access required for a sales application, this application should enable a salesperson to synchronize the pull subscription on demand by clicking a button.</span></span> <span data-ttu-id="1cb8c-190">既然銷售代表將會安裝和執行應用程式，因此它也需要能夠在用戶端設定訂閱並套用初始快照集。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-190">Since a sales representative will install and run the application, it also needs to be able to configure a subscription and apply the initial snapshot at the client.</span></span> <span data-ttu-id="1cb8c-191">否則，應用程式將使用 Windows 提供的基礎結構來感應無線連接，以便在偵測到連接時，自動同步處理訂閱。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-191">Optionally, the application will use the infrastructure provided by Windows for sensing wireless connectivity to automatically synchronize the subscription when a connection is detected.</span></span>  
  
3.  <span data-ttu-id="1cb8c-192">當連接到發行者時，請遵循所有的複寫安全性指導方針，包括 Windows 驗證與虛擬的私人網路 (VPN)。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-192">Follow all of the security guidelines for replication, including using Windows Authentication and a virtual private network (VPN) when connecting to the publisher.</span></span> <span data-ttu-id="1cb8c-193">如果實作 Web 同步處理，請使用安全通訊端層 (SSL) 連接。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-193">If implementing Web synchronization, use a secure sockets layer (SSL) connection.</span></span> <span data-ttu-id="1cb8c-194">如需詳細資訊，請參閱 [Configure Web Synchronization](../configure-web-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-194">For more information, see [Configure Web Synchronization](../configure-web-synchronization.md).</span></span>  
  
4.  <span data-ttu-id="1cb8c-195">為了利用 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 的功能，應用程式是使用 Managed 程式碼語言來開發。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-195">In order to take advantage of the features of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], the application is developed using a managed code language.</span></span>  
  
5.  <span data-ttu-id="1cb8c-196">根據這些需求，Replication Management Objects (RMO) 的管理介面，可以為這個應用程式提供所有需要的應用程式功能。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-196">Based on these requirements, the Replication Management Objects (RMO) managed interface can provide all of the needed replication functionality for this application.</span></span>  
  
 <span data-ttu-id="1cb8c-197">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 隨附的範例應用程式中，已實作這個範例案例。</span><span class="sxs-lookup"><span data-stu-id="1cb8c-197">This example scenario has been implemented in a sample application that ships with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
  
