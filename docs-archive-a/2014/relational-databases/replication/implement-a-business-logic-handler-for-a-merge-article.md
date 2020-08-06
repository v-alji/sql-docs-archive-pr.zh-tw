---
title: 為合併發行項實作商務邏輯處理常式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], business logic handlers
- merge replication business logic handlers [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
- business logic handlers [SQL Server replication]
- BusinessLogicModule class
ms.assetid: ed477595-6d46-4fa2-b0d3-a5358903ec05
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c2996a8ca8471ef59d4781e21239a72262daa759
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585831"
---
# <a name="implement-a-business-logic-handler-for-a-merge-article"></a><span data-ttu-id="63e86-102">為合併發行項實作商務邏輯處理常式</span><span class="sxs-lookup"><span data-stu-id="63e86-102">Implement a Business Logic Handler for a Merge Article</span></span>
  <span data-ttu-id="63e86-103">本主題描述如何使用複寫程式設計或 Replication Management Objects (RMO)，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中實作合併發行項的商務邏輯處理常式。</span><span class="sxs-lookup"><span data-stu-id="63e86-103">This topic describes how to implement a business logic handler for a merge article in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using replication programming or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="63e86-104"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> 命名空間會實作一個介面，此介面可讓您撰寫複雜商務邏輯來處理合併複寫同步處理程序期間所發生的事件。</span><span class="sxs-lookup"><span data-stu-id="63e86-104">The <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> namespace implements an interface that enables you to write complex business logic to handle events that occur during the merge replication synchronization process.</span></span> <span data-ttu-id="63e86-105">在同步處理期間複寫之每一個變更資料列的複寫程序可以叫用商務邏輯處理常式中的方法。</span><span class="sxs-lookup"><span data-stu-id="63e86-105">Methods in the business logic handler can be invoked by the replication process for each changed row that is replicated during synchronization.</span></span>  
  
 <span data-ttu-id="63e86-106">實作商務邏輯處理常式的一般程序如下：</span><span class="sxs-lookup"><span data-stu-id="63e86-106">The general process for implementing a business logic handler is:</span></span>  
  
1.  <span data-ttu-id="63e86-107">建立商務邏輯處理常式組件。</span><span class="sxs-lookup"><span data-stu-id="63e86-107">Create the business logic hander assembly.</span></span>  
  
2.  <span data-ttu-id="63e86-108">在散發者上註冊此組件。</span><span class="sxs-lookup"><span data-stu-id="63e86-108">Register the assembly at the Distributor.</span></span>  
  
3.  <span data-ttu-id="63e86-109">在合併代理程式執行所在的伺服器上部署此組件。</span><span class="sxs-lookup"><span data-stu-id="63e86-109">Deploy the assembly at the server on which the Merge Agent runs.</span></span> <span data-ttu-id="63e86-110">若為提取訂閱，代理程式會在訂閱者端執行；若為發送訂閱，代理程式會在散發者端執行。</span><span class="sxs-lookup"><span data-stu-id="63e86-110">For a pull subscription the agent runs on the Subscriber, and for a push subscription the agent runs on the Distributor.</span></span> <span data-ttu-id="63e86-111">當您正在使用 Web 同步處理時，此代理程式會在 Web 伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="63e86-111">When you are using Web synchronization, the agent runs on the Web server.</span></span>  
  
4.  <span data-ttu-id="63e86-112">建立使用商務邏輯處理常式的發行項，或是修改現有的發行項來使用商務邏輯處理常式。</span><span class="sxs-lookup"><span data-stu-id="63e86-112">Create an article that uses the business logic handler or modify an existing article to use the business logic handler.</span></span>  
  
 <span data-ttu-id="63e86-113">指定的商務邏輯處理常式會針對要同步處理的每一個資料列執行。</span><span class="sxs-lookup"><span data-stu-id="63e86-113">The business logic handler you specify is executed for every row that is synchronized.</span></span> <span data-ttu-id="63e86-114">對其他應用程式或網路服務的複雜邏輯與呼叫可能會影響效能。</span><span class="sxs-lookup"><span data-stu-id="63e86-114">Complex logic and calls to other applications or network services can impact performance.</span></span> <span data-ttu-id="63e86-115">如需商務邏輯處理常式的詳細資訊，請參閱[在合併同步處理期間執行商務邏輯](merge/execute-business-logic-during-merge-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="63e86-115">For more information about business logic handlers, see [Execute Business Logic During Merge Synchronization](merge/execute-business-logic-during-merge-synchronization.md).</span></span>  
  
 <span data-ttu-id="63e86-116">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="63e86-116">**In This Topic**</span></span>  
  
-   <span data-ttu-id="63e86-117">**若要針對合併發行項實作商務邏輯處理常式，請使用：**</span><span class="sxs-lookup"><span data-stu-id="63e86-117">**To implement a business logic handler for a merge article, using:**</span></span>  
  
     [<span data-ttu-id="63e86-118">複寫程式設計</span><span class="sxs-lookup"><span data-stu-id="63e86-118">Replication Programming</span></span>](#ReplProg)  
  
     [<span data-ttu-id="63e86-119">Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="63e86-119">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-replication-programming"></a><a name="ReplProg"></a> <span data-ttu-id="63e86-120">使用複寫程式設計</span><span class="sxs-lookup"><span data-stu-id="63e86-120">Using Replication Programming</span></span>  
  
#### <a name="to-create-and-deploy-a-business-logic-handler"></a><span data-ttu-id="63e86-121">建立及部署商務邏輯處理常式</span><span class="sxs-lookup"><span data-stu-id="63e86-121">To create and deploy a business logic handler</span></span>  
  
1.  <span data-ttu-id="63e86-122">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 中，針對 .NET 組件建立新的專案，其中包含實作此商務邏輯處理常式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="63e86-122">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio, create a new project for the .NET assembly that contains the code that implements the business logic handler.</span></span>  
  
2.  <span data-ttu-id="63e86-123">針對下列命名空間加入此專案的參考。</span><span class="sxs-lookup"><span data-stu-id="63e86-123">Add references to the project for the following namespaces.</span></span>  
  
    |<span data-ttu-id="63e86-124">組件參考</span><span class="sxs-lookup"><span data-stu-id="63e86-124">Assembly Reference</span></span>|<span data-ttu-id="63e86-125">Location</span><span class="sxs-lookup"><span data-stu-id="63e86-125">Location</span></span>|  
    |------------------------|--------------|  
    |<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]<span data-ttu-id="63e86-126">COM (預設安裝)</span><span class="sxs-lookup"><span data-stu-id="63e86-126">COM (default installation)</span></span>|  
    |<xref:System.Data>|<span data-ttu-id="63e86-127">GAC (.NET Framework 的元件)</span><span class="sxs-lookup"><span data-stu-id="63e86-127">GAC (component of the .NET Framework)</span></span>|  
    |<xref:System.Data.Common>|<span data-ttu-id="63e86-128">GAC (.NET Framework 的元件)</span><span class="sxs-lookup"><span data-stu-id="63e86-128">GAC (component of the .NET Framework)</span></span>|  
  
3.  <span data-ttu-id="63e86-129">加入會覆寫 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> 類別的類別。</span><span class="sxs-lookup"><span data-stu-id="63e86-129">Add a class that overrides the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> class.</span></span>  
  
4.  <span data-ttu-id="63e86-130">實作 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> 屬性來指示要處理的變更類型。</span><span class="sxs-lookup"><span data-stu-id="63e86-130">Implement the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> property to indicate the types of changes that are handled.</span></span>  
  
5.  <span data-ttu-id="63e86-131">覆寫 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> 類別的下列其中一個或多個方法：</span><span class="sxs-lookup"><span data-stu-id="63e86-131">Override one or more of the following methods of the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> class:</span></span>  
  
    -   <span data-ttu-id="63e86-132"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> - 在同步處理期間認可資料變更時叫用。</span><span class="sxs-lookup"><span data-stu-id="63e86-132"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> - invoked when a data change is committed during synchronization.</span></span>  
  
    -   <span data-ttu-id="63e86-133"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> - 在上傳或下載 DELETE 陳述式期間發生錯誤時叫用。</span><span class="sxs-lookup"><span data-stu-id="63e86-133"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> - invoked when an error occurs when a DELETE statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="63e86-134"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> - 在上傳或下載 DELETE 陳述式時叫用。</span><span class="sxs-lookup"><span data-stu-id="63e86-134"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> - invoked when DELETE statements are being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="63e86-135"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> - 在上傳或下載 INSERT 陳述式期間發生錯誤時叫用。</span><span class="sxs-lookup"><span data-stu-id="63e86-135"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> - invoked when an error occurs when an INSERT statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="63e86-136"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> - 在上傳或下載 INSERT 陳述式時叫用。</span><span class="sxs-lookup"><span data-stu-id="63e86-136"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> - invoked when INSERT statements are being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="63e86-137"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> - 當發行者和訂閱者上發生衝突的 UPDATE 陳述式時叫用。</span><span class="sxs-lookup"><span data-stu-id="63e86-137"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> - invoked when conflicting UPDATE statements occur at the Publisher and Subscriber.</span></span>  
  
    -   <span data-ttu-id="63e86-138"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> - 當發行者和訂閱者上發生與 DELETE 陳述式衝突的 UPDATE 陳述式時叫用。</span><span class="sxs-lookup"><span data-stu-id="63e86-138"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> - invoked when UPDATE statements conflict with DELETE statements at the Publisher and Subscriber.</span></span>  
  
    -   <span data-ttu-id="63e86-139"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> - 在上傳或下載 UPDATE 陳述式期間發生錯誤時叫用。</span><span class="sxs-lookup"><span data-stu-id="63e86-139"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> - invoked when an error occurs when an UPDATE statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="63e86-140"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> - 在上傳或下載 UPDATE 陳述式時叫用。</span><span class="sxs-lookup"><span data-stu-id="63e86-140"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> - invoked when UPDATE statements are being uploaded or downloaded.</span></span>  
  
6.  <span data-ttu-id="63e86-141">建立專案來建立商務邏輯處理常式組件。</span><span class="sxs-lookup"><span data-stu-id="63e86-141">Build the project to create the business logic handler assembly.</span></span>  
  
7.  <span data-ttu-id="63e86-142">將此組件部署在包含合併代理程式可執行檔 (replmerg.exe) 的目錄中 (它的預設安裝位置為 [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM)，或是將它安裝在 .NET 全域組件快取 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="63e86-142">Deploy the assembly in the directory that contains the Merge Agent executable file (replmerg.exe), which for a default installation is [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM, or install it in the .NET global assembly cache (GAC).</span></span> <span data-ttu-id="63e86-143">只有當合併代理程式以外的應用程式需要存取此組件時，您才應該將此組件安裝在 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="63e86-143">You should only install the assembly in the GAC if applications other than the Merge Agent require access to the assembly.</span></span> <span data-ttu-id="63e86-144">您可使用 .NET Framework SDK 中提供的全域組件快取工具 (**Gacutil.exe)** ，將此組件安裝在 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="63e86-144">The assembly can be installed into the GAC using the Global Assembly Cache tool (**Gacutil.exe)** provided in the .NET Framework SDK.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="63e86-145">您必須在合併代理程式執行所在的每一部伺服器上部署商務邏輯處理常式，其中包括使用 Web 同步處理時，主控 replisapi.dll 的 IIS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="63e86-145">A business logic handler must be deployed on every server on which the Merge Agent runs, which includes the IIS server that hosts the replisapi.dll when using Web synchronization.</span></span>  
  
#### <a name="to-register-a-business-logic-handler"></a><span data-ttu-id="63e86-146">註冊商務邏輯處理常式</span><span class="sxs-lookup"><span data-stu-id="63e86-146">To register a business logic handler</span></span>  
  
1.  <span data-ttu-id="63e86-147">在發行者端，執行 [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql)，以確定此組件尚未註冊為商務邏輯處理常式。</span><span class="sxs-lookup"><span data-stu-id="63e86-147">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) to verify that the assembly has not already been registered as a business logic handler.</span></span>  
  
2.  <span data-ttu-id="63e86-148">在散發者上，執行[sp_registercustomresolver &#40;transact-sql&#41;，並](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql)針對指定商務邏輯處理常式的易記名稱 **@article_resolver** 、針對指定、針對指定元件的名稱，並針對 `true` **@is_dotnet_assembly** **@dotnet_assembly_name** 覆寫的類別提供完整名稱 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> **@dotnet_class_name** 。</span><span class="sxs-lookup"><span data-stu-id="63e86-148">At the Distributor, execute [sp_registercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql), specifying a friendly name for the business logic handler for **@article_resolver**, a value of `true` for **@is_dotnet_assembly**, the name of the assembly for **@dotnet_assembly_name**, and the fully-qualified name of the class that overrides <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> for **@dotnet_class_name**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="63e86-149">如果元件未部署在與合併代理程式可執行檔相同的目錄中、與同步啟動合併代理程式之應用程式相同的目錄中，或在全域組件快取中 (GAC) ，您就必須指定具有元件名稱的完整路徑 **@dotnet_assembly_name** 。</span><span class="sxs-lookup"><span data-stu-id="63e86-149">If the assembly is not deployed in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent, or in the global assembly cache (GAC), you need to specify the full path with the assembly name for **@dotnet_assembly_name**.</span></span> <span data-ttu-id="63e86-150">當您正在使用 Web 同步處理時，必須指定組件在 Web 伺服器上的位置。</span><span class="sxs-lookup"><span data-stu-id="63e86-150">When using Web synchronization, you must specify the location of assembly at the Web server.</span></span>  
  
#### <a name="to-use-a-business-logic-handler-with-a-new-table-article"></a><span data-ttu-id="63e86-151">搭配新的資料表發行項使用商務邏輯處理常式</span><span class="sxs-lookup"><span data-stu-id="63e86-151">To use a business logic handler with a new table article</span></span>  
  
1.  <span data-ttu-id="63e86-152">執行 [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) 來定義發行項，並針對 **@article_resolver** 指定商務邏輯處理常式的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="63e86-152">Execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) to define an article, specifying the friendly name of the business logic handler for **@article_resolver**.</span></span> <span data-ttu-id="63e86-153">如需詳細資訊，請參閱 [定義發行項](publish/define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="63e86-153">For more information, see [Define an Article](publish/define-an-article.md).</span></span>  
  
#### <a name="to-use-a-business-logic-handler-with-an-existing-table-article"></a><span data-ttu-id="63e86-154">搭配現有的資料表發行項使用商務邏輯處理常式</span><span class="sxs-lookup"><span data-stu-id="63e86-154">To use a business logic handler with an existing table article</span></span>  
  
1.  <span data-ttu-id="63e86-155">執行[sp_changemergearticle &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)、指定 **@publication** 、、的 **@article** **article_resolver**值 **@property** ，以及的商務邏輯處理常式的易記名稱 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="63e86-155">Execute [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), specifying **@publication**, **@article**, a value of **article_resolver** for **@property**, and the friendly name of the business logic handler for **@value**.</span></span>  
  
###  <a name="examples-replication-programming"></a><a name="TsqlExample"></a> <span data-ttu-id="63e86-156">範例 (複寫程式設計)</span><span class="sxs-lookup"><span data-stu-id="63e86-156">Examples (Replication Programming)</span></span>  
 <span data-ttu-id="63e86-157">這個範例會示範建立稽核記錄的商務邏輯處理常式。</span><span class="sxs-lookup"><span data-stu-id="63e86-157">This example shows a business logic handler that creates an audit log.</span></span>  
  
 [!code-csharp[HowTo#rmo_BusinessLogicCode](../../snippets/csharp/SQL15/replication/howto/cs/businesslogic.cs#rmo_businesslogiccode)]  
  
 [!code-vb[HowTo#rmo_vb_BusinessLogicCode](../../snippets/visualbasic/SQL15/replication/howto/vb/businesslogic.vb#rmo_vb_businesslogiccode)]  
  
 <span data-ttu-id="63e86-158">下列範例會在散發者上註冊商務邏輯處理常式組件，並將現有的合併發行項變更為使用這個自訂商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="63e86-158">The following example registers a business logic handler assembly at the Distributor and changes an existing merge article to use this custom business logic.</span></span>  
  
 [!code-sql[HowTo#sp_RegisterBLH_10](../../snippets/tsql/SQL15/replication/howto/tsql/registerblh_10.sql#sp_registerblh_10)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="63e86-159">使用 Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="63e86-159">Using Replication Management Objects (RMO)</span></span>  
  
#### <a name="to-create-a-business-logic-handler"></a><span data-ttu-id="63e86-160">建立商務邏輯處理常式</span><span class="sxs-lookup"><span data-stu-id="63e86-160">To create a business logic handler</span></span>  
  
1.  <span data-ttu-id="63e86-161">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 中，針對 .NET 組件建立新的專案，其中包含實作此商務邏輯處理常式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="63e86-161">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio, create a new project for the .NET assembly that contains the code that implements the business logic handler.</span></span>  
  
2.  <span data-ttu-id="63e86-162">針對下列命名空間加入此專案的參考。</span><span class="sxs-lookup"><span data-stu-id="63e86-162">Add references to the project for the following namespaces.</span></span>  
  
    |<span data-ttu-id="63e86-163">組件參考</span><span class="sxs-lookup"><span data-stu-id="63e86-163">Assembly Reference</span></span>|<span data-ttu-id="63e86-164">Location</span><span class="sxs-lookup"><span data-stu-id="63e86-164">Location</span></span>|  
    |------------------------|--------------|  
    |<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]<span data-ttu-id="63e86-165">COM (預設安裝)</span><span class="sxs-lookup"><span data-stu-id="63e86-165">COM (default installation)</span></span>|  
    |<xref:System.Data>|<span data-ttu-id="63e86-166">GAC (.NET Framework 的元件)</span><span class="sxs-lookup"><span data-stu-id="63e86-166">GAC (component of the .NET Framework)</span></span>|  
    |<xref:System.Data.Common>|<span data-ttu-id="63e86-167">GAC (.NET Framework 的元件)</span><span class="sxs-lookup"><span data-stu-id="63e86-167">GAC (component of the .NET Framework)</span></span>|  
  
3.  <span data-ttu-id="63e86-168">加入會覆寫 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> 類別的類別。</span><span class="sxs-lookup"><span data-stu-id="63e86-168">Add a class that overrides the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> class.</span></span>  
  
4.  <span data-ttu-id="63e86-169">實作 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> 屬性來指示要處理的變更類型。</span><span class="sxs-lookup"><span data-stu-id="63e86-169">Implement the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> property to indicate the types of changes that are handled.</span></span>  
  
5.  <span data-ttu-id="63e86-170">覆寫 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> 類別的下列其中一個或多個方法：</span><span class="sxs-lookup"><span data-stu-id="63e86-170">Override one or more of the following methods of the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> class:</span></span>  
  
    -   <span data-ttu-id="63e86-171"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> - 在同步處理期間認可資料變更時叫用。</span><span class="sxs-lookup"><span data-stu-id="63e86-171"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> - invoked when a data change is committed during synchronization.</span></span>  
  
    -   <span data-ttu-id="63e86-172"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> - 在上傳或下載 DELETE 陳述式期間發生錯誤時叫用。</span><span class="sxs-lookup"><span data-stu-id="63e86-172"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> - invoked if an error occurs while a DELETE statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="63e86-173"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> - 在上傳或下載 DELETE 陳述式時叫用。</span><span class="sxs-lookup"><span data-stu-id="63e86-173"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> - invoked when DELETE statements are being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="63e86-174"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> - 在上傳或下載 INSERT 陳述式期間發生錯誤時叫用。</span><span class="sxs-lookup"><span data-stu-id="63e86-174"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> - invoked if an error occurs when an INSERT statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="63e86-175"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> - 在上傳或下載 INSERT 陳述式時叫用。</span><span class="sxs-lookup"><span data-stu-id="63e86-175"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> - invoked when INSERT statements are being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="63e86-176"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> - 當發行者和訂閱者上發生衝突的 UPDATE 陳述式時叫用。</span><span class="sxs-lookup"><span data-stu-id="63e86-176"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> - invoked when conflicting UPDATE statements occur at the Publisher and Subscriber.</span></span>  
  
    -   <span data-ttu-id="63e86-177"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> - 當發行者和訂閱者上發生與 DELETE 陳述式衝突的 UPDATE 陳述式時叫用。</span><span class="sxs-lookup"><span data-stu-id="63e86-177"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> - invoked when UPDATE statements conflict with DELETE statements at the Publisher and Subscriber.</span></span>  
  
    -   <span data-ttu-id="63e86-178"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> - 在上傳或下載 UPDATE 陳述式期間發生錯誤時叫用。</span><span class="sxs-lookup"><span data-stu-id="63e86-178"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> - invoked if an error occurs when an UPDATE statement is being uploaded or downloaded.</span></span>  
  
    -   <span data-ttu-id="63e86-179"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> - 在上傳或下載 UPDATE 陳述式時叫用。</span><span class="sxs-lookup"><span data-stu-id="63e86-179"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> - invoked when UPDATE statements are being uploaded or downloaded.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="63e86-180">自訂商務邏輯未明確處理的任何發行項衝突，都會由此發行項的預設解決器所處理。</span><span class="sxs-lookup"><span data-stu-id="63e86-180">Any article conflicts not explicitly handled by your custom business logic are handled by the default resolver for the article.</span></span>  
  
6.  <span data-ttu-id="63e86-181">建立專案來建立商務邏輯處理常式組件。</span><span class="sxs-lookup"><span data-stu-id="63e86-181">Build the project to create the business logic handler assembly.</span></span>  
  
#### <a name="to-register-a-business-logic-handler"></a><span data-ttu-id="63e86-182">註冊商務邏輯處理常式</span><span class="sxs-lookup"><span data-stu-id="63e86-182">To register a business logic handler</span></span>  
  
1.  <span data-ttu-id="63e86-183">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與散發者的連接。</span><span class="sxs-lookup"><span data-stu-id="63e86-183">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="63e86-184">建立 <xref:Microsoft.SqlServer.Replication.ReplicationServer> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="63e86-184">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span> <span data-ttu-id="63e86-185">傳遞步驟 1 的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 。</span><span class="sxs-lookup"><span data-stu-id="63e86-185">Pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1.</span></span>  
  
3.  <span data-ttu-id="63e86-186">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumBusinessLogicHandlers%2A> 並檢查傳回的 <xref:System.Collections.ArrayList> 物件，以確定此組件尚未註冊為商務邏輯處理常式。</span><span class="sxs-lookup"><span data-stu-id="63e86-186">Call <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumBusinessLogicHandlers%2A> and check the returned <xref:System.Collections.ArrayList> object to ensure that the assembly has not already been registered as a business logic handler.</span></span>  
  
4.  <span data-ttu-id="63e86-187">建立 <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="63e86-187">Create an instance of the <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler> class.</span></span> <span data-ttu-id="63e86-188">指定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="63e86-188">Specify the following properties:</span></span>  
  
    -   <span data-ttu-id="63e86-189"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetAssemblyName%2A> - .NET 組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="63e86-189"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetAssemblyName%2A> - the name of the .NET assembly.</span></span> <span data-ttu-id="63e86-190">如果此組件未部署在與合併代理程式可執行檔相同的目錄中、與同步啟動合併代理程式之應用程式相同的目錄中或是 GAC 中，您就必須包含具有組件名稱的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="63e86-190">If the assembly is not deployed in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent, or in the GAC, you must include the full path with the assembly name.</span></span> <span data-ttu-id="63e86-191">當您搭配 Web 同步處理使用商務邏輯處理常式時，必須包含具有組件名稱的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="63e86-191">You must include the full path with the assembly name when using a business logic handler with Web synchronization.</span></span>  
  
    -   <span data-ttu-id="63e86-192"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetClassName%2A> - 覆寫 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> 及實作商務邏輯處理常式之類別的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="63e86-192"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetClassName%2A> - the fully-qualified name of the class that overrides <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> and implements the business logic handler.</span></span>  
  
    -   <span data-ttu-id="63e86-193"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> - 當您存取商務邏輯處理常式時所要使用的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="63e86-193"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> - a friendly name you use when you access the business logic handler.</span></span>  
  
    -   <span data-ttu-id="63e86-194"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.IsDotNetAssembly%2A> - `true` 的值。</span><span class="sxs-lookup"><span data-stu-id="63e86-194"><xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.IsDotNetAssembly%2A> - a value of `true`.</span></span>  
  
#### <a name="to-deploy-a-business-logic-handler"></a><span data-ttu-id="63e86-195">部署商務邏輯處理常式</span><span class="sxs-lookup"><span data-stu-id="63e86-195">To deploy a business logic handler</span></span>  
  
1.  <span data-ttu-id="63e86-196">將此組件部署在合併代理程式執行所在的伺服器上，商務邏輯處理常式已在散發者上註冊時所指定的檔案位置內。</span><span class="sxs-lookup"><span data-stu-id="63e86-196">Deploy the assembly on the server where the Merge Agent runs in the file location specified when the business logic handler was registered at the Distributor.</span></span> <span data-ttu-id="63e86-197">若為提取訂閱，代理程式會在訂閱者端執行；若為發送訂閱，代理程式會在散發者端執行。</span><span class="sxs-lookup"><span data-stu-id="63e86-197">For a pull subscription the agent runs on the Subscriber, and for a push subscription the agent runs on the Distributor.</span></span> <span data-ttu-id="63e86-198">當您正在使用 Web 同步處理時，此代理程式會在 Web 伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="63e86-198">When you are using Web synchronization, the agent runs on the Web server.</span></span> <span data-ttu-id="63e86-199">如果在註冊商務邏輯處理常式時，組件名稱中未包含完整路徑，請將此組件部署在與合併代理程式可執行檔相同的目錄中，或是與同步啟動合併代理程式之應用程式相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="63e86-199">If the full path was not included with the assembly name when the business logic handler was registered, deploy the assembly in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent.</span></span> <span data-ttu-id="63e86-200">如果有多個應用程式使用相同的組件，您可能要將此組件安裝在 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="63e86-200">You may install the assembly in the GAC if there are multiple applications that use the same assembly.</span></span>  
  
#### <a name="to-use-a-business-logic-handler-with-a-new-table-article"></a><span data-ttu-id="63e86-201">搭配新的資料表發行項使用商務邏輯處理常式</span><span class="sxs-lookup"><span data-stu-id="63e86-201">To use a business logic handler with a new table article</span></span>  
  
1.  <span data-ttu-id="63e86-202">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與發行者的連接。</span><span class="sxs-lookup"><span data-stu-id="63e86-202">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="63e86-203">建立 <xref:Microsoft.SqlServer.Replication.MergeArticle> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="63e86-203">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeArticle> class.</span></span> <span data-ttu-id="63e86-204">設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="63e86-204">Set the following properties:</span></span>  
  
    -   <span data-ttu-id="63e86-205">將 <xref:Microsoft.SqlServer.Replication.Article.Name%2A>設定為發行項名稱。</span><span class="sxs-lookup"><span data-stu-id="63e86-205">The name of the article for <xref:Microsoft.SqlServer.Replication.Article.Name%2A>.</span></span>  
  
    -   <span data-ttu-id="63e86-206">將 <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>設定為發行集名稱。</span><span class="sxs-lookup"><span data-stu-id="63e86-206">The name of the publication for <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="63e86-207">將 <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A>設定為發行集資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="63e86-207">The name of the publication database for <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A>.</span></span>  
  
    -   <span data-ttu-id="63e86-208">將<xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A>設定為商務邏輯處理常式的易記名稱 ( <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>)。</span><span class="sxs-lookup"><span data-stu-id="63e86-208">The friendly name of the business logic handler (<xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A>) for <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>.</span></span>  
  
3.  <span data-ttu-id="63e86-209">呼叫 <xref:Microsoft.SqlServer.Replication.Article.Create%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="63e86-209">Call the <xref:Microsoft.SqlServer.Replication.Article.Create%2A> method.</span></span> <span data-ttu-id="63e86-210">如需詳細資訊，請參閱 [定義發行項](publish/define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="63e86-210">For more information, see [Define an Article](publish/define-an-article.md).</span></span>  
  
#### <a name="to-use-a-business-logic-handler-with-an-existing-table-article"></a><span data-ttu-id="63e86-211">搭配現有的資料表發行項使用商務邏輯處理常式</span><span class="sxs-lookup"><span data-stu-id="63e86-211">To use a business logic handler with an existing table article</span></span>  
  
1.  <span data-ttu-id="63e86-212">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與發行者的連接。</span><span class="sxs-lookup"><span data-stu-id="63e86-212">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="63e86-213">建立 <xref:Microsoft.SqlServer.Replication.MergeArticle> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="63e86-213">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeArticle> class.</span></span>  
  
3.  <span data-ttu-id="63e86-214">設定 <xref:Microsoft.SqlServer.Replication.Article.Name%2A>、 <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>和 <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="63e86-214">Set the <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, and <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="63e86-215">針對 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性設定步驟 1 中的連接。</span><span class="sxs-lookup"><span data-stu-id="63e86-215">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="63e86-216">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="63e86-216">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="63e86-217">如果此方法傳回 `false`，則表示步驟 3 中的發行項屬性定義不正確，或者該發行項不存在。</span><span class="sxs-lookup"><span data-stu-id="63e86-217">If this method returns `false`, either the article properties in step 3 were defined incorrectly or the article does not exist.</span></span> <span data-ttu-id="63e86-218">如需詳細資訊，請參閱 [View and Modify Article Properties](publish/view-and-modify-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="63e86-218">For more information, see [View and Modify Article Properties](publish/view-and-modify-article-properties.md).</span></span>  
  
6.  <span data-ttu-id="63e86-219">將 <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>設定為商務邏輯處理常式的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="63e86-219">Set the friendly name of the business logic handler for <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>.</span></span> <span data-ttu-id="63e86-220">這是當註冊商務邏輯處理常式時，所指定之 <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="63e86-220">This is the value of the <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> property specified when registering the business logic handler.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="63e86-221">範例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="63e86-221">Examples (RMO)</span></span>  
 <span data-ttu-id="63e86-222">這個範例是一個商務邏輯處理常式，它會記錄有關在訂閱者上插入、更新和刪除的資訊。</span><span class="sxs-lookup"><span data-stu-id="63e86-222">This example is a business logic handler that logs information about inserts, updates, and deletes at the Subscriber.</span></span>  
  
 [!code-csharp[HowTo#rmo_BusinessLogicCode](../../snippets/csharp/SQL15/replication/howto/cs/businesslogic.cs#rmo_businesslogiccode)]  
  
 [!code-vb[HowTo#rmo_vb_BusinessLogicCode](../../snippets/visualbasic/SQL15/replication/howto/vb/businesslogic.vb#rmo_vb_businesslogiccode)]  
  
 <span data-ttu-id="63e86-223">這個範例會在散發者上註冊商務邏輯處理常式。</span><span class="sxs-lookup"><span data-stu-id="63e86-223">This example registers a business logic handler at the Distributor.</span></span>  
  
 [!code-csharp[HowTo#rmo_RegisterBLH_10](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_registerblh_10)]  
  
 [!code-vb[HowTo#rmo_vb_RegisterBLH_10](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_registerblh_10)]  
  
 <span data-ttu-id="63e86-224">此範例會變更現有的發行項來使用商務邏輯處理常式。</span><span class="sxs-lookup"><span data-stu-id="63e86-224">This example changes an existing article to use the business logic handler.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeMergeArticle_BLH](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changemergearticle_blh)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergeArticle_BLH](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changemergearticle_blh)]  
  
## <a name="see-also"></a><span data-ttu-id="63e86-225">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63e86-225">See Also</span></span>  
 <span data-ttu-id="63e86-226">[為合併發行項執行自訂衝突解析程式](implement-a-custom-conflict-resolver-for-a-merge-article.md) </span><span class="sxs-lookup"><span data-stu-id="63e86-226">[Implement a Custom Conflict Resolver for a Merge Article](implement-a-custom-conflict-resolver-for-a-merge-article.md) </span></span>  
 <span data-ttu-id="63e86-227">[&#40;複寫程式設計中的商務邏輯處理常式進行 Debug&#41;](debug-a-business-logic-handler-replication-programming.md) </span><span class="sxs-lookup"><span data-stu-id="63e86-227">[Debug a Business Logic Handler &#40;Replication Programming&#41;](debug-a-business-logic-handler-replication-programming.md) </span></span>  
 <span data-ttu-id="63e86-228">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="63e86-228">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="63e86-229">複寫管理物件概念</span><span class="sxs-lookup"><span data-stu-id="63e86-229">Replication Management Objects Concepts</span></span>](concepts/replication-management-objects-concepts.md)  
  
  
