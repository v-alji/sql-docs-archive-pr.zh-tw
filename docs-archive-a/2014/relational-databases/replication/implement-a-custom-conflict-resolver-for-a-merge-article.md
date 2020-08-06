---
title: 針對合併發行項實作自訂衝突解析程式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], stored procedure-based resolvers
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 76bd8524-ebc1-4d80-b5a2-4169944d6ac0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 23e684213114f3c9bb2f1ad56de06fcfc89b819a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585829"
---
# <a name="implement-a-custom-conflict-resolver-for-a-merge-article"></a><span data-ttu-id="583ce-102">針對合併發行項實作自訂衝突解析程式</span><span class="sxs-lookup"><span data-stu-id="583ce-102">Implement a Custom Conflict Resolver for a Merge Article</span></span>
  <span data-ttu-id="583ce-103"> 本主題描述如何使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 或[以 COM 為基礎的自訂解析程式](merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md)，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中針對合併發行項實作自訂衝突解析程式。</span><span class="sxs-lookup"><span data-stu-id="583ce-103">This topic describes how to implement custom conflict resolver for a merge article in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)] or a [COM-based custom resolver](merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md).</span></span>  
  
 <span data-ttu-id="583ce-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="583ce-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="583ce-105">**若要針對合併發行項實作自訂衝突解析程式，請使用：**</span><span class="sxs-lookup"><span data-stu-id="583ce-105">**To implement custom conflict resolver for a merge article, using:**</span></span>  
  
     [<span data-ttu-id="583ce-106">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="583ce-106">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="583ce-107">以 COM 為基礎的解析程式</span><span class="sxs-lookup"><span data-stu-id="583ce-107">COM-based Resolver</span></span>](#COM)  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="583ce-108">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="583ce-108">Using Transact-SQL</span></span>  
 <span data-ttu-id="583ce-109">您可以將自訂衝突解決器撰寫為每一個發行者上的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序。</span><span class="sxs-lookup"><span data-stu-id="583ce-109">You can write your own custom conflict resolver as a [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure at each Publisher.</span></span> <span data-ttu-id="583ce-110">在同步處理期間，當註冊解決器的發行項中遇到衝突時，就會叫用此預存程序，而且衝突資料列的相關資訊會由合併代理程式傳遞給此程序所需的參數。</span><span class="sxs-lookup"><span data-stu-id="583ce-110">During synchronization, this stored procedure is invoked when conflicts are encountered in an article to which the resolver was registered, and information on the conflict row is passed by the Merge Agent to the required parameters of the procedure.</span></span> <span data-ttu-id="583ce-111">一定會在發行者上建立以預存程序為基礎的自訂衝突解決器。</span><span class="sxs-lookup"><span data-stu-id="583ce-111">Stored procedure-based custom conflict resolvers are always created at the Publisher.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="583ce-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]預存程式解析程式的叫用目的，只是為了處理資料列變更為基礎的衝突。</span><span class="sxs-lookup"><span data-stu-id="583ce-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedure resolvers are only invoked to handle row change-based conflicts.</span></span> <span data-ttu-id="583ce-113">這些解決器不能用於處理其他類型的衝突，例如因為 PRIMARY KEY 違規或唯一索引條件約束違規而發生的插入失敗。</span><span class="sxs-lookup"><span data-stu-id="583ce-113">They cannot be used to handle other types of conflicts such as insert failures due to PRIMARY KEY violations or unique index constraint violations.</span></span>  
  
#### <a name="to-create-a-stored-procedure-based-custom-conflict-resolver"></a><span data-ttu-id="583ce-114">建立以預存程序為基礎的自訂衝突解決器</span><span class="sxs-lookup"><span data-stu-id="583ce-114">To create a stored procedure-based custom conflict resolver</span></span>  
  
1.  <span data-ttu-id="583ce-115">在發行集或 **msdb** 資料庫的發行者上，建立新的系統預存程序，以實作下列必要的參數：</span><span class="sxs-lookup"><span data-stu-id="583ce-115">At the Publisher in either the publication or **msdb** database, create a new system stored procedure that implements the following required parameters:</span></span>  
  
    |<span data-ttu-id="583ce-116">參數</span><span class="sxs-lookup"><span data-stu-id="583ce-116">Parameter</span></span>|<span data-ttu-id="583ce-117">資料類型</span><span class="sxs-lookup"><span data-stu-id="583ce-117">Data type</span></span>|<span data-ttu-id="583ce-118">描述</span><span class="sxs-lookup"><span data-stu-id="583ce-118">Description</span></span>|  
    |---------------|---------------|-----------------|  
    |**@tableowner**|`sysname`|<span data-ttu-id="583ce-119">解決衝突所針對之資料表的擁有者名稱。</span><span class="sxs-lookup"><span data-stu-id="583ce-119">Name of the owner of the table for which a conflict is being resolved.</span></span> <span data-ttu-id="583ce-120">這是發行集資料庫中資料表的擁有者。</span><span class="sxs-lookup"><span data-stu-id="583ce-120">This is the owner for the table in the publication database.</span></span>|  
    |**@tablename**|`sysname`|<span data-ttu-id="583ce-121">解決衝突所針對之資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="583ce-121">Name of the table for which a conflict is being resolved.</span></span>|  
    |**@rowguid**|`uniqueidentifier`|<span data-ttu-id="583ce-122">發生衝突之資料列的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="583ce-122">Unique identifier for the row having the conflict.</span></span>|  
    |**@subscriber**|`sysname`|<span data-ttu-id="583ce-123">傳播衝突變更所在的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="583ce-123">Name of the server from where a conflicting change is being propagated.</span></span>|  
    |**@subscriber_db**|`sysname`|<span data-ttu-id="583ce-124">傳播衝突變更所在的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="583ce-124">Name of the database from where conflicting change is being propagated.</span></span>|  
    |<span data-ttu-id="583ce-125">**@log_conflict輸出**</span><span class="sxs-lookup"><span data-stu-id="583ce-125">**@log_conflict OUTPUT**</span></span>|`int`|<span data-ttu-id="583ce-126">合併處理是否應該記錄衝突供稍後解決之用：</span><span class="sxs-lookup"><span data-stu-id="583ce-126">Whether the merge process should log a conflict for later resolution:</span></span><br /><br /> <span data-ttu-id="583ce-127">**0** = 不記錄衝突。</span><span class="sxs-lookup"><span data-stu-id="583ce-127">**0** = Do not log the conflict.</span></span><br /><br /> <span data-ttu-id="583ce-128">**1** = 訂閱者為衝突失敗者。</span><span class="sxs-lookup"><span data-stu-id="583ce-128">**1** = Subscriber is the conflict loser.</span></span><br /><br /> <span data-ttu-id="583ce-129">**2** = 發行者為衝突失敗者。</span><span class="sxs-lookup"><span data-stu-id="583ce-129">**2** = Publisher is the conflict loser.</span></span>|  
    |<span data-ttu-id="583ce-130">**@conflict_message輸出**</span><span class="sxs-lookup"><span data-stu-id="583ce-130">**@conflict_message OUTPUT**</span></span>|`nvarchar(512)`|<span data-ttu-id="583ce-131">當記錄衝突時，要提供之有關解決方法的訊息。</span><span class="sxs-lookup"><span data-stu-id="583ce-131">Message to be given about the resolution if the conflict is logged.</span></span>|  
    |**@destowner**|`sysname`|<span data-ttu-id="583ce-132">訂閱者上發行之資料表的擁有者。</span><span class="sxs-lookup"><span data-stu-id="583ce-132">The owner of the published table at the Subscriber.</span></span>|  
  
     <span data-ttu-id="583ce-133">此預存程序會使用由合併代理程式傳遞給這些參數的值，以實作自訂衝突解決邏輯；它必須傳回結構上與基底資料表相同的單一資料列結果集，並包含此資料列之獲勝版本的資料值。</span><span class="sxs-lookup"><span data-stu-id="583ce-133">This stored procedure uses the values passed by the Merge Agent to these parameters to implement your custom conflict resolution logic; it must return a single row result set that is identical in structure to the base table and contains the data values for the winning version of the row.</span></span>  
  
2.  <span data-ttu-id="583ce-134">將預存程序的 EXECUTE 權限授與給訂閱者使用的任何登入，以連接到發行者。</span><span class="sxs-lookup"><span data-stu-id="583ce-134">Grant EXECUTE permissions on the stored procedure to any logins used by Subscribers to connect to the Publisher.</span></span>  
  
#### <a name="to-use-a-custom-conflict-resolver-with-a-new-table-article"></a><span data-ttu-id="583ce-135">搭配新的資料表發行項使用自訂衝突解決器</span><span class="sxs-lookup"><span data-stu-id="583ce-135">To use a custom conflict resolver with a new table article</span></span>  
  
1.  <span data-ttu-id="583ce-136">執行 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) 來定義發行項，針對 **@article_resolver** **參數指定** Microsoft SQL **@article_resolver** 的值，並針對 **@resolver_info** 參數指定可實作衝突解決器邏輯的預存程序名稱。</span><span class="sxs-lookup"><span data-stu-id="583ce-136">Execute [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) to define an article, specifying a value of **MicrosoftSQL** **Server Stored Procedure Resolver** for the **@article_resolver** parameter and the name of the stored procedure that implements the conflict resolver logic for the **@resolver_info** parameter.</span></span> <span data-ttu-id="583ce-137">如需詳細資訊，請參閱 [定義發行項](publish/define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="583ce-137">For more information, see [Define an Article](publish/define-an-article.md).</span></span>  
  
#### <a name="to-use-a-custom-conflict-resolver-with-an-existing-table-article"></a><span data-ttu-id="583ce-138">搭配現有的資料表發行項使用自訂衝突解決器</span><span class="sxs-lookup"><span data-stu-id="583ce-138">To use a custom conflict resolver with an existing table article</span></span>  
  
1.  <span data-ttu-id="583ce-139">執行[sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)， **@publication** 並指定、 **@article** 、的**Article_resolver**值 **@property** ，以及為**MicrosoftSQL** **伺服器儲存的 ProcedureResolver**值 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="583ce-139">Execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), specifying **@publication**, **@article**, a value of **article_resolver** for **@property**, and a value of **MicrosoftSQL** **Server Stored ProcedureResolver** for **@value**.</span></span>  
  
2.  <span data-ttu-id="583ce-140">執行[sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)， **@publication** 並指定、 **@article** 、 **resolver_info**的值，以及為執行 **@property** 衝突解決器邏輯的預存程式名稱 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="583ce-140">Execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), specifying **@publication**, **@article**, a value of **resolver_info** for **@property**, and the name of the stored procedure that implements the conflict resolver logic for **@value**.</span></span>  
  
##  <a name="using-a-com-based-custom-resolver"></a><a name="COM"></a><span data-ttu-id="583ce-141">使用以 COM 為基礎的自訂解析程式</span><span class="sxs-lookup"><span data-stu-id="583ce-141">Using a COM-based Custom Resolver</span></span>  
 <span data-ttu-id="583ce-142"><xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> 命名空間會實作一個介面，此介面可讓您撰寫複雜的商務邏輯來處理事件，並解決合併複寫同步處理程序期間所發生的衝突。</span><span class="sxs-lookup"><span data-stu-id="583ce-142">The <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> namespace implements an interface that enables you to write complex business logic to handle events and resolve conflicts that occur during the merge replication synchronization process.</span></span> <span data-ttu-id="583ce-143">如需詳細資訊，請參閱 [為合併發行項實作商務邏輯處理常式](implement-a-business-logic-handler-for-a-merge-article.md)。</span><span class="sxs-lookup"><span data-stu-id="583ce-143">For more information, see [Implement a Business Logic Handler for a Merge Article](implement-a-business-logic-handler-for-a-merge-article.md).</span></span> <span data-ttu-id="583ce-144">您也可以撰寫自己的原生程式碼式自訂商務邏輯，以解決衝突。</span><span class="sxs-lookup"><span data-stu-id="583ce-144">You can also write your own native code-based custom business logic to resolve conflicts.</span></span> <span data-ttu-id="583ce-145">此邏輯會建立為 COM 元件，並編譯成動態連結程式庫 (DLL) (使用類似 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C++ 的產品)。</span><span class="sxs-lookup"><span data-stu-id="583ce-145">This logic is built as a COM component and compiled into dynamic-link libraries (DLL), using products such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C++.</span></span> <span data-ttu-id="583ce-146">這類以 COM 為基礎的自訂衝突解決器必須實**ICustomResolver**介面，這是特別針對衝突解決所設計。</span><span class="sxs-lookup"><span data-stu-id="583ce-146">Such a COM-based custom conflict resolver must implement the **ICustomResolver** interface, which is designed specifically for conflict resolution.</span></span>  
  
#### <a name="to-create-and-register-a-com-based-custom-conflict-resolver"></a><span data-ttu-id="583ce-147">建立及註冊以 COM 為基礎的自訂衝突解決器</span><span class="sxs-lookup"><span data-stu-id="583ce-147">To create and register a COM-based custom conflict resolver</span></span>  
  
1.  <span data-ttu-id="583ce-148">在 COM 相容的撰寫環境中，加入對自訂衝突解決器程式庫的參考。</span><span class="sxs-lookup"><span data-stu-id="583ce-148">In a COM-compatible authoring environment, add references to the Custom Conflict Resolver library.</span></span>  
  
2.  <span data-ttu-id="583ce-149">針對 Visual C++ 專案，使用 #import 指示詞將此程式庫匯入專案中。</span><span class="sxs-lookup"><span data-stu-id="583ce-149">For a Visual C++ project, use the #import directive to import this library into your project.</span></span>  
  
3.  <span data-ttu-id="583ce-150">建立可實作 **ICustomResolver** 介面的類別。</span><span class="sxs-lookup"><span data-stu-id="583ce-150">Create a class that implements the **ICustomResolver** interface.</span></span>  
  
4.  <span data-ttu-id="583ce-151">實作特定的方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="583ce-151">Implement certain methods and properties.</span></span>  
  
5.  <span data-ttu-id="583ce-152">建立專案來建立自訂衝突解決器程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="583ce-152">Build the project to create the custom conflict resolver library file.</span></span>  
  
6.  <span data-ttu-id="583ce-153">在包含合併代理程式可執行檔的目錄中 (通常是 \Microsoft SQL Server\100\COM) 部署此程式庫。</span><span class="sxs-lookup"><span data-stu-id="583ce-153">Deploy the library in the directory containing the merge agent executable (usually \Microsoft SQL Server\100\COM).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="583ce-154">如果是提取訂閱，則必須在訂閱者上部署自訂衝突解決器，如果是發送訂閱，則必須在散發者上部署，或是在搭配 Web 同步處理的 Web 伺服器上部署。</span><span class="sxs-lookup"><span data-stu-id="583ce-154">A custom conflict resolver must be deployed at the Subscriber for a pull subscription, at the Distributor for a push subscription, or at the Web server used with Web synchronization.</span></span>  
  
7.  <span data-ttu-id="583ce-155">從部署目錄使用 regsvr32.exe 註冊自訂衝突解決器程式庫，如下面所示：</span><span class="sxs-lookup"><span data-stu-id="583ce-155">Register the custom conflict resolver library using regsvr32.exe from the deployment directory as follows:</span></span>  
  
    ```  
    regsvr32.exe mycustomresolver.dll  
    ```  
  
8.  <span data-ttu-id="583ce-156">在發行者端，執行 [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql)，以確認此程式庫尚未註冊為自訂衝突解決器。</span><span class="sxs-lookup"><span data-stu-id="583ce-156">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) to verify that the library is not already registered as a custom conflict resolver.</span></span>  
  
9. <span data-ttu-id="583ce-157">若要將程式庫註冊為自訂衝突解決器，請在「散發者」[端執行 &#40;transact-sql&#41;sp_registercustomresolver ](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="583ce-157">To register the library as a custom conflict resolver, execute [sp_registercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql), at the Distributor.</span></span> <span data-ttu-id="583ce-158">為指定 COM 物件的易記名稱、連結 **@article_resolver** 庫的識別碼 (的 CLSID) **@resolver_clsid** ，以及的值 `false` **@is_dotnet_assembly** 。</span><span class="sxs-lookup"><span data-stu-id="583ce-158">Specify the friendly name of the COM object for **@article_resolver**, the library's ID (CLSID) for **@resolver_clsid**, and a value of `false` for **@is_dotnet_assembly**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="583ce-159">當不再需要時，可以使用 [sp_unregistercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql) 來取消註冊自訂衝突解決器。</span><span class="sxs-lookup"><span data-stu-id="583ce-159">When no longer needed, a custom conflict resolver can be unregistered using [sp_unregistercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql).</span></span>  
  
10. <span data-ttu-id="583ce-160">(選擇性) 在叢集上重複步驟 5-8，在此叢集的所有節點上註冊自訂解決器。</span><span class="sxs-lookup"><span data-stu-id="583ce-160">(Optional) On a cluster, repeat steps 5-8 to register the custom resolver on all nodes of the cluster.</span></span> <span data-ttu-id="583ce-161">要確定自訂解決器將能夠在容錯移轉之後適當地載入重新調整器時，必須進行這項處理。</span><span class="sxs-lookup"><span data-stu-id="583ce-161">This is required to ensure that the custom resolver will be able to properly load the reconciler following a failover.</span></span>  
  
#### <a name="to-use-a-custom-conflict-resolver-with-a-new-table-article"></a><span data-ttu-id="583ce-162">搭配新的資料表發行項使用自訂衝突解決器</span><span class="sxs-lookup"><span data-stu-id="583ce-162">To use a custom conflict resolver with a new table article</span></span>  
  
1.  <span data-ttu-id="583ce-163">在發行者上，執行[sp_enumcustomresolvers &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql)並記下所需解析程式的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="583ce-163">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) and note the friendly name of the desired resolver.</span></span>  
  
2.  <span data-ttu-id="583ce-164">在發行集資料庫的發行者端，執行 [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) 來定義發行項。</span><span class="sxs-lookup"><span data-stu-id="583ce-164">At the Publisher on the publication database, execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) to define an article.</span></span> <span data-ttu-id="583ce-165">針對指定步驟1中發行項解析程式的易記名稱 **@article_resolver** 。</span><span class="sxs-lookup"><span data-stu-id="583ce-165">Specify the friendly name of the article resolver from step 1 for **@article_resolver**.</span></span> <span data-ttu-id="583ce-166">如需詳細資訊，請參閱 [定義發行項](publish/define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="583ce-166">For more information, see [Define an Article](publish/define-an-article.md).</span></span>  
  
#### <a name="to-use-a-custom-conflict-resolver-with-an-existing-table-article"></a><span data-ttu-id="583ce-167">搭配現有的資料表發行項使用自訂衝突解決器</span><span class="sxs-lookup"><span data-stu-id="583ce-167">To use a custom conflict resolver with an existing table article</span></span>  
  
1.  <span data-ttu-id="583ce-168">在發行者上，執行[sp_enumcustomresolvers &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql)並記下所需解析程式的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="583ce-168">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) and note the friendly name of the desired resolver.</span></span>  
  
2.  <span data-ttu-id="583ce-169">執行[sp_changemergearticle &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)、指定 **@publication** 、、的 **@article** **article_resolver**值 **@property** ，以及步驟1中發行項解析程式的易記名稱 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="583ce-169">Execute [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), specifying **@publication**, **@article**, a value of **article_resolver** for **@property**, and the friendly name of the article resolver from step 1 for **@value**.</span></span>  
  
#### <a name="viewing-a-sample-custom-resolver"></a><span data-ttu-id="583ce-170">檢視自訂解析程式範例</span><span class="sxs-lookup"><span data-stu-id="583ce-170">Viewing a Sample Custom Resolver</span></span>  
  
1.  <span data-ttu-id="583ce-171">SQL Server 2000 範例檔案中有提供範例。</span><span class="sxs-lookup"><span data-stu-id="583ce-171">A sample is available in the SQL Server 2000 sample files.</span></span> <span data-ttu-id="583ce-172">下載[**sql2000samples.zip**](https://github.com/Microsoft/sql-server-samples/blob/master/samples/tutorials/Miscellaneous/sql2000samples.zip)。</span><span class="sxs-lookup"><span data-stu-id="583ce-172">Download the [**sql2000samples.zip**](https://github.com/Microsoft/sql-server-samples/blob/master/samples/tutorials/Miscellaneous/sql2000samples.zip).</span></span> <span data-ttu-id="583ce-173">這會將3個檔案 amounting 下載到 6.9 MB。</span><span class="sxs-lookup"><span data-stu-id="583ce-173">This downloads 3 files amounting to 6.9 MB.</span></span>  
  
2.  <span data-ttu-id="583ce-174">從下載的 .cab 壓縮檔解壓縮檔案。</span><span class="sxs-lookup"><span data-stu-id="583ce-174">Extract the files from downloaded compressed .cab file.</span></span>  
  
3.  <span data-ttu-id="583ce-175">執行**setup.exe**</span><span class="sxs-lookup"><span data-stu-id="583ce-175">Run **setup.exe**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="583ce-176">選擇安裝選項時，只需要安裝 **複寫** 範例。</span><span class="sxs-lookup"><span data-stu-id="583ce-176">When choosing the installation options, it is only necessary to install the **Replication** samples.</span></span> <span data-ttu-id="583ce-177"> (預設安裝路徑\為\**C:\Program Files (x86) \microsoft SQL Server 2000 Samples\1033 \\\ \**) </span><span class="sxs-lookup"><span data-stu-id="583ce-177">(The default installation path is **C:\Program Files (x86)\Microsoft SQL Server 2000 Samples\1033\\**)</span></span>  
  
4.  <span data-ttu-id="583ce-178">移至安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="583ce-178">Go to installation folder.</span></span> <span data-ttu-id="583ce-179">(預設資料夾是 **C:\Program Files (x86)\Microsoft SQL Server 2000 Samples\1033\sqlrepl\unzip_sqlreplSP3.exe**)</span><span class="sxs-lookup"><span data-stu-id="583ce-179">(The default folder is **C:\Program Files (x86)\Microsoft SQL Server 2000 Samples\1033\sqlrepl\unzip_sqlreplSP3.exe**)</span></span>  
  
5.  <span data-ttu-id="583ce-180">執行 **unzip_sqlreplSP3.exe** 程式。</span><span class="sxs-lookup"><span data-stu-id="583ce-180">Run the **unzip_sqlreplSP3.exe** program.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="583ce-181">範例 COM 解析程式將會安裝至 **C:\Program Files (x86)\Microsoft SQL Server 2000 Samples\1033\sqlrepl\resolver\subspres** 資料夾 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="583ce-181">The sample com resolver will install (by default) to the **C:\Program Files (x86)\Microsoft SQL Server 2000 Samples\1033\sqlrepl\resolver\subspres** folder.</span></span>  
  
6.  <span data-ttu-id="583ce-182">在 **subspres** 資料夾中，於所有來源檔案中尋找 **#include sqlres.h** ，並將其取代為 **#import "replrec.dll" no_namespace, raw_interfaces_only**</span><span class="sxs-lookup"><span data-stu-id="583ce-182">In the **subspres** folder, find all occurrences of **#include sqlres.h** in all of the source files and replace them with **#import "replrec.dll" no_namespace, raw_interfaces_only**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="583ce-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="583ce-183">See Also</span></span>  
 <span data-ttu-id="583ce-184">[進階合併式複寫衝突偵測與解決](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="583ce-184">[Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 <span data-ttu-id="583ce-185">[以 COM 為基礎的自訂解析程式](merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md) </span><span class="sxs-lookup"><span data-stu-id="583ce-185">[COM-Based Custom Resolvers](merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md) </span></span>  
 [<span data-ttu-id="583ce-186">複寫安全性最佳作法</span><span class="sxs-lookup"><span data-stu-id="583ce-186">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
