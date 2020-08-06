---
title: 指定交易式發行項變更的傳播方式 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, propagation methods
ms.assetid: a10c5001-22cc-4667-8f0b-3d0818dca2e9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 72d377ba89f1d393eab48bd9c918012b0f503f9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699439"
---
# <a name="specify-how-changes-are-propagated-for-transactional-articles"></a><span data-ttu-id="f395c-102">指定交易式發行項變更的傳播方式</span><span class="sxs-lookup"><span data-stu-id="f395c-102">Specify How Changes Are Propagated for Transactional Articles</span></span>
  <span data-ttu-id="f395c-103">異動複寫可讓您指定資料變更從「發行者」傳播到「訂閱者」的方式。</span><span class="sxs-lookup"><span data-stu-id="f395c-103">Transactional replication allows you to specify how data changes are propagated from the Publisher to Subscribers.</span></span> <span data-ttu-id="f395c-104">對於每個發行的資料表，您都可以指定四種方法之一來傳播每個要傳播到「訂閱者」的作業 (INSERT、UPDATE 或 DELETE)：</span><span class="sxs-lookup"><span data-stu-id="f395c-104">For each published table, you can specify one of four ways that each operation (INSERT, UPDATE, or DELETE) should be propagated to the Subscriber:</span></span>  
  
-   <span data-ttu-id="f395c-105">指定異動複寫應先編寫指令碼，然後呼叫預存程序，以將變更傳播至「訂閱者」(預設值)。</span><span class="sxs-lookup"><span data-stu-id="f395c-105">Specify that transactional replication should script out and subsequently call a stored procedure to propagate changes to Subscribers (the default).</span></span>  
  
-   <span data-ttu-id="f395c-106">指定變更使用 INSERT、UPDATE 或 DELETE 陳述式傳播 (非「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者」的預設值)。</span><span class="sxs-lookup"><span data-stu-id="f395c-106">Specify that the change should be propagated using an INSERT, UPDATE, or DELETE statement (the default for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers).</span></span>  
  
-   <span data-ttu-id="f395c-107">指定使用自訂預存程序。</span><span class="sxs-lookup"><span data-stu-id="f395c-107">Specify that a custom stored procedure should be used.</span></span>  
  
-   <span data-ttu-id="f395c-108">指定不在任何「訂閱者」端執行此動作。</span><span class="sxs-lookup"><span data-stu-id="f395c-108">Specify that this action should not be performed at any Subscriber.</span></span> <span data-ttu-id="f395c-109">不會複寫該類型的交易。</span><span class="sxs-lookup"><span data-stu-id="f395c-109">Transactions of that type are not replicated.</span></span>  
  
 <span data-ttu-id="f395c-110">依預設，異動複寫會透過每個訂閱者上所安裝的一組預存程序，將變更傳播到訂閱者。</span><span class="sxs-lookup"><span data-stu-id="f395c-110">By default, transactional replication propagates changes to Subscribers through a set of stored procedures that are installed on each Subscriber.</span></span> <span data-ttu-id="f395c-111">在「發行者」端的資料表中進行插入、更新或刪除操作時，作業會翻譯為對「訂閱者」端預存程序的呼叫。</span><span class="sxs-lookup"><span data-stu-id="f395c-111">When an insert, update or delete occurs on a table at the Publisher, the operation is translated into a call to a stored procedure at the Subscriber.</span></span> <span data-ttu-id="f395c-112">預存程序接受對應至資料表中資料行的參數，允許在「訂閱者」端變更這些資料行。</span><span class="sxs-lookup"><span data-stu-id="f395c-112">The stored procedure accepts parameters that map to the columns in the table, allowing those columns to be changed at the Subscriber.</span></span>  
  
 <span data-ttu-id="f395c-113">若要設定對交易式發行項之資料變更的傳播方法，請參閱＜ [設定對交易式發行項之資料變更的傳播方法](../publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md)＞。</span><span class="sxs-lookup"><span data-stu-id="f395c-113">To set the propagation method for data changes to transactional articles, see [Set the Propagation Method for Data Changes to Transactional Articles](../publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md).</span></span>  
  
## <a name="default-and-custom-stored-procedures"></a><span data-ttu-id="f395c-114">預設與自訂預存程序</span><span class="sxs-lookup"><span data-stu-id="f395c-114">Default and custom stored procedures</span></span>  
 <span data-ttu-id="f395c-115">依預設，複寫為每個資料表發行項建立的三個程序為：</span><span class="sxs-lookup"><span data-stu-id="f395c-115">The three procedures that replication creates by default for each table article are:</span></span>  
  
-   <span data-ttu-id="f395c-116">**sp_MSins_\<** *tablename* **>** ，負責處理插入。</span><span class="sxs-lookup"><span data-stu-id="f395c-116">**sp_MSins_\<** *tablename* **>**, which handles inserts.</span></span>  
  
-   <span data-ttu-id="f395c-117">**sp_MSupd_\<** *tablename* **>** ，負責處理更新。</span><span class="sxs-lookup"><span data-stu-id="f395c-117">**sp_MSupd_\<** *tablename* **>**, which handles updates.</span></span>  
  
-   <span data-ttu-id="f395c-118">**sp_MSdel_\<** *tablename* **>** ，負責處理刪除。</span><span class="sxs-lookup"><span data-stu-id="f395c-118">**sp_MSdel_\<** *tablename* **>**, which handles deletes.</span></span>  
  
 <span data-ttu-id="f395c-119">程序中使用的 **\<***tablename***>** 取決於發行項新增至發行集的方式，以及訂閱資料庫是否包含擁有者不同的同名資料表。</span><span class="sxs-lookup"><span data-stu-id="f395c-119">The **\<***tablename***>** used in the procedure depends on how the article was added to the publication and whether the subscription database contains a table of the same name with a different owner.</span></span>  
  
 <span data-ttu-id="f395c-120">以上任何程序均可取代為您在將發行項新增至發行集時指定的自訂程序。</span><span class="sxs-lookup"><span data-stu-id="f395c-120">Any of these procedures can be replaced with a custom procedure that you specify when adding an article to a publication.</span></span> <span data-ttu-id="f395c-121">如果應用程式需要自訂邏輯，例如在「訂閱者」端更新資料列時將資料插入稽核資料表，就要使用自訂程序。</span><span class="sxs-lookup"><span data-stu-id="f395c-121">Custom procedures are used if an application requires custom logic, such as inserting data into an audit table when a row is updated at a Subscriber.</span></span> <span data-ttu-id="f395c-122">如需指定自訂預存程序的詳細資訊，請參閱以上所列的「如何」主題。</span><span class="sxs-lookup"><span data-stu-id="f395c-122">For more information about specifying custom stored procedures, see the how to topics listed above.</span></span>  
  
 <span data-ttu-id="f395c-123">如果指定預設複寫程序或自訂程序，則還要指定每個程序的呼叫語法 (如果使用預設程序，複寫會選取預設值)。</span><span class="sxs-lookup"><span data-stu-id="f395c-123">If you specify the default replication procedures or custom procedures, you also specify call syntax for each procedure (replication selects defaults if you use the default procedures).</span></span> <span data-ttu-id="f395c-124">呼叫語法決定提供給程序的參數結構，以及每個資料變更傳送到「訂閱者」的資訊量。</span><span class="sxs-lookup"><span data-stu-id="f395c-124">The call syntax determines the structure of the parameters provided to the procedure and how much information is sent to the Subscriber with each data change.</span></span> <span data-ttu-id="f395c-125">如需詳細資訊，請參閱本主題中的「預存程序的呼叫語法」一節。</span><span class="sxs-lookup"><span data-stu-id="f395c-125">For more information, see the section "Call Syntax for Stored Procedures" in this topic.</span></span>  
  
### <a name="considerations-for-using-custom-stored-procedures"></a><span data-ttu-id="f395c-126">使用自訂預存程序的考量</span><span class="sxs-lookup"><span data-stu-id="f395c-126">Considerations for Using Custom Stored Procedures</span></span>  
 <span data-ttu-id="f395c-127">使用自訂預存程序時，請記住下列考量：</span><span class="sxs-lookup"><span data-stu-id="f395c-127">Keep the following considerations in mind when using custom stored procedures:</span></span>  
  
-   <span data-ttu-id="f395c-128">您必須支援預存程序中的邏輯； [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 不支援自訂邏輯。</span><span class="sxs-lookup"><span data-stu-id="f395c-128">You must support the logic in the stored procedure; [!INCLUDE[msCoName](../../../includes/msconame-md.md)] does not provide support for custom logic.</span></span>  
  
-   <span data-ttu-id="f395c-129">為了避免與複寫使用的交易產生衝突，不應在自訂程序中使用外顯交易。</span><span class="sxs-lookup"><span data-stu-id="f395c-129">In order to avoid conflicts with the transactions used by replication, explicit transactions should not be used in custom procedures.</span></span>  
  
-   <span data-ttu-id="f395c-130">「訂閱者」端的結構描述通常與「發行者」端的結構描述相同，但如果使用的是資料行篩選，則也可能是「發行者」結構描述的子集。</span><span class="sxs-lookup"><span data-stu-id="f395c-130">The schema at the Subscriber is typically identical to the schema at the Publisher, but can also be a subset of the Publisher schema if column filtering is used.</span></span> <span data-ttu-id="f395c-131">不過，如果需要在資料移動時轉換結構描述，好讓訂閱者上的結構描述不是發行者上結構描述的子集，建議採用 [!INCLUDE[ssISCurrent](../../../includes/ssiscurrent-md.md)] 方案。</span><span class="sxs-lookup"><span data-stu-id="f395c-131">However, if you need to transform the schema as the data is moved such that the schema on the Subscriber is not a subset of the schema on the Publisher, [!INCLUDE[ssISCurrent](../../../includes/ssiscurrent-md.md)] is the recommended solution.</span></span> <span data-ttu-id="f395c-132">如需詳細資訊，請參閱 [SQL Server Integration Services](../../../integration-services/sql-server-integration-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f395c-132">For more information, see [SQL Server Integration Services](../../../integration-services/sql-server-integration-services.md).</span></span>  
  
-   <span data-ttu-id="f395c-133">如果對發行的資料表進行了結構描述變更，則必須重新產生自訂程序。</span><span class="sxs-lookup"><span data-stu-id="f395c-133">If you make schema changes to a published table, the custom procedures must be regenerated.</span></span> <span data-ttu-id="f395c-134">如需詳細資訊，請參閱[重新產生自訂交易程序以反映結構描述變更](transactional-articles-regenerate-to-reflect-schema-changes.md)。</span><span class="sxs-lookup"><span data-stu-id="f395c-134">For more information, see [Regenerate Custom Transactional Procedures to Reflect Schema Changes](transactional-articles-regenerate-to-reflect-schema-changes.md).</span></span>  
  
-   <span data-ttu-id="f395c-135">如果「散發代理程式」的 **-SubscriptionStreams** 參數所使用的值大於 1，則必須確定主索引鍵資料行的更新成功。</span><span class="sxs-lookup"><span data-stu-id="f395c-135">If you use a value greater than 1 for **-SubscriptionStreams** parameter of the Distribution Agent, you must ensure that updates to primary key columns are successful.</span></span> <span data-ttu-id="f395c-136">例如：</span><span class="sxs-lookup"><span data-stu-id="f395c-136">For example:</span></span>  
  
    ```  
    update ... set pk = 2 where pk = 1 -- update 1  
    update ... set pk = 3 where pk = 2 -- update 2  
    ```  
  
     <span data-ttu-id="f395c-137">如果「散發代理程式」使用多個連接，則可能會透過不同的連接複寫這兩個更新。</span><span class="sxs-lookup"><span data-stu-id="f395c-137">If the Distribution Agent uses more than one connection, these two updates might be replicated over different connections.</span></span> <span data-ttu-id="f395c-138">如果更新 1 先套用，便不會有問題；如果更新 2 先套用，則會傳回「0 個資料列受影響」，因為更新 1 尚未發生。</span><span class="sxs-lookup"><span data-stu-id="f395c-138">If update 1 is applied first, there is no problem; if update 2 is applied first it will return '0 rows affected' because update 1 has not yet occurred.</span></span> <span data-ttu-id="f395c-139">預設程序會對這種情況進行處理，如果沒有資料列受更新的影響，便會產生錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="f395c-139">This situation is handled in the default procedures by raising an error if no rows are affected on an update:</span></span>  
  
    ```  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sys.sp_MSreplraiserror 20598  
    ```  
  
     <span data-ttu-id="f395c-140">產生錯誤訊息將強制「散發代理程式」透過單一連接重試更新，這樣便會成功。</span><span class="sxs-lookup"><span data-stu-id="f395c-140">Raising the error forces the Distribution Agent to retry the updates over a single connection, which will succeed.</span></span> <span data-ttu-id="f395c-141">自訂預存程序必須包括類似的邏輯。</span><span class="sxs-lookup"><span data-stu-id="f395c-141">Custom stored procedures must include similar logic.</span></span>  
  
### <a name="call-syntax-for-stored-procedures"></a><span data-ttu-id="f395c-142">預存程序的呼叫語法</span><span class="sxs-lookup"><span data-stu-id="f395c-142">Call syntax for stored procedures</span></span>  
 <span data-ttu-id="f395c-143">用於呼叫異動複寫所使用程序的語法有五個選項：</span><span class="sxs-lookup"><span data-stu-id="f395c-143">There are five options for the syntax used to call the procedures used by transactional replication:</span></span>  
  
-   <span data-ttu-id="f395c-144">CALL 語法。</span><span class="sxs-lookup"><span data-stu-id="f395c-144">CALL syntax.</span></span> <span data-ttu-id="f395c-145">可用於插入、更新與刪除。</span><span class="sxs-lookup"><span data-stu-id="f395c-145">Can be used for inserts, updates, and deletes.</span></span> <span data-ttu-id="f395c-146">依預設，複寫使用此語法進行插入和刪除。</span><span class="sxs-lookup"><span data-stu-id="f395c-146">By default, replication uses this syntax for inserts and deletes.</span></span>  
  
-   <span data-ttu-id="f395c-147">SCALL 語法。</span><span class="sxs-lookup"><span data-stu-id="f395c-147">SCALL syntax.</span></span> <span data-ttu-id="f395c-148">僅能使用於更新。</span><span class="sxs-lookup"><span data-stu-id="f395c-148">Can be used for updates only.</span></span> <span data-ttu-id="f395c-149">依預設，複寫使用此語法進行更新。</span><span class="sxs-lookup"><span data-stu-id="f395c-149">By default, replication uses this syntax for updates.</span></span>  
  
-   <span data-ttu-id="f395c-150">MCALL 語法。</span><span class="sxs-lookup"><span data-stu-id="f395c-150">MCALL syntax.</span></span> <span data-ttu-id="f395c-151">僅能使用於更新。</span><span class="sxs-lookup"><span data-stu-id="f395c-151">Can be used for updates only.</span></span>  
  
-   <span data-ttu-id="f395c-152">XCALL 語法。</span><span class="sxs-lookup"><span data-stu-id="f395c-152">XCALL syntax.</span></span> <span data-ttu-id="f395c-153">可用於更新與刪除。</span><span class="sxs-lookup"><span data-stu-id="f395c-153">Can be used for updates and deletes.</span></span>  
  
-   <span data-ttu-id="f395c-154">VCALL。</span><span class="sxs-lookup"><span data-stu-id="f395c-154">VCALL.</span></span> <span data-ttu-id="f395c-155">用於可更新訂閱。</span><span class="sxs-lookup"><span data-stu-id="f395c-155">Used for updatable subscriptions.</span></span> <span data-ttu-id="f395c-156">僅供內部使用。</span><span class="sxs-lookup"><span data-stu-id="f395c-156">Internal use only.</span></span>  
  
 <span data-ttu-id="f395c-157">每種方法傳播到「訂閱者」的資料量都不同。</span><span class="sxs-lookup"><span data-stu-id="f395c-157">Each method differs in the amount of data that is propagated to the Subscriber.</span></span> <span data-ttu-id="f395c-158">例如，SCALL 僅傳遞實際受更新影響的資料行值。</span><span class="sxs-lookup"><span data-stu-id="f395c-158">For example, SCALL passes in values only for the columns that are actually affected by an update.</span></span> <span data-ttu-id="f395c-159">相反地，XCALL 則要求所有資料行 (無論是否受更新影響) 以及每個資料行的所有舊資料值。</span><span class="sxs-lookup"><span data-stu-id="f395c-159">XCALL, by contrast, requires all columns (whether affected by an update or not) and all the old data values for each column.</span></span> <span data-ttu-id="f395c-160">在許多情況下，SCALL 適用於更新，但如果您的複寫在更新過程中要求所有資料值，則 XCALL 適用。</span><span class="sxs-lookup"><span data-stu-id="f395c-160">In many cases, SCALL is appropriate for updates, but if your application requires all the data values during an update, XCALL allows for this.</span></span>  
  
#### <a name="call-syntax"></a><span data-ttu-id="f395c-161">CALL 語法</span><span class="sxs-lookup"><span data-stu-id="f395c-161">CALL Syntax</span></span>  
 <span data-ttu-id="f395c-162">INSERT 預存程序</span><span class="sxs-lookup"><span data-stu-id="f395c-162">INSERT stored procedures</span></span>  
 <span data-ttu-id="f395c-163">處理 INSERT 陳述式的預存程序將會收到所有資料行之插入值：</span><span class="sxs-lookup"><span data-stu-id="f395c-163">Stored procedures handling INSERT statements will be passed the inserted values for all columns:</span></span>  
  
```  
c1, c2, c3,... cn  
```  
  
 <span data-ttu-id="f395c-164">UPDATE 預存程序</span><span class="sxs-lookup"><span data-stu-id="f395c-164">UPDATE stored procedures</span></span>  
 <span data-ttu-id="f395c-165">處理 UPDATE 陳述式的預存程序將會收到在發行項中定義的所有資料行之更新值，接著是主索引鍵資料行的原始值 (不會嘗試判斷哪些資料行作了變更)：</span><span class="sxs-lookup"><span data-stu-id="f395c-165">Stored procedures handling UPDATE statements will be passed the updated values for all columns defined in the article, followed by the original values for the primary key columns (no attempt is made to determine which columns were changed.):</span></span>  
  
```  
c1, c2, c3,... cn, pkc1, pkc2, pkc3,... pkcn  
```  
  
 <span data-ttu-id="f395c-166">DELETE 預存程序</span><span class="sxs-lookup"><span data-stu-id="f395c-166">DELETE stored procedures</span></span>  
 <span data-ttu-id="f395c-167">處理 DELETE 陳述式的預存程序會收到主索引鍵資料行的值：</span><span class="sxs-lookup"><span data-stu-id="f395c-167">Stored procedures handling DELETE statements will be passed values for the primary key columns:</span></span>  
  
```  
pkc1, pkc2, pkc3,... pkcn  
```  
  
#### <a name="scall-syntax"></a><span data-ttu-id="f395c-168">SCALL 語法</span><span class="sxs-lookup"><span data-stu-id="f395c-168">SCALL Syntax</span></span>  
 <span data-ttu-id="f395c-169">UPDATE 預存程序</span><span class="sxs-lookup"><span data-stu-id="f395c-169">UPDATE stored procedures</span></span>  
 <span data-ttu-id="f395c-170">處理 UPDATE 陳述式的預存程序會只收到那些已變更資料行的更新值，接著是主索引鍵資料行的原始值，然後是指出已變更資料行的位元遮罩 (`binary(n)`) 參數。</span><span class="sxs-lookup"><span data-stu-id="f395c-170">Stored procedures handling UPDATE statements will be passed the updated values only for those columns that have changed, followed by the original values for the primary key columns, followed by a bitmask (`binary(n)`) parameter that indicates the changed columns.</span></span> <span data-ttu-id="f395c-171">在下列範例中，資料行 2 (c2) 未變更：</span><span class="sxs-lookup"><span data-stu-id="f395c-171">In the following example, column 2 (c2) has not changed:</span></span>  
  
```  
c1, , c3,... cn, pkc1, pkc2, pkc3,... pkcn, bitmask  
```  
  
#### <a name="mcall-syntax"></a><span data-ttu-id="f395c-172">MCALL 語法</span><span class="sxs-lookup"><span data-stu-id="f395c-172">MCALL Syntax</span></span>  
 <span data-ttu-id="f395c-173">UPDATE 預存程序</span><span class="sxs-lookup"><span data-stu-id="f395c-173">UPDATE stored procedures</span></span>  
 <span data-ttu-id="f395c-174">處理 UPDATE 陳述式的預存程序會收到發行項中所定義的所有資料行之更新值，接著是主索引鍵資料行的原始值，然後是指出已變更資料行的位元遮罩 (`binary(n)`) 參數：</span><span class="sxs-lookup"><span data-stu-id="f395c-174">Stored procedures handling UPDATE statements will be passed the updated values for all columns defined in the article, followed by the original values for the primary key columns, followed by a bitmask (`binary(n)`) parameter that indicates the changed columns:</span></span>  
  
```  
c1, c2, c3,... cn, pkc1, pkc2, pkc3,... pkcn, bitmask  
```  
  
#### <a name="xcall-syntax"></a><span data-ttu-id="f395c-175">XCALL 語法</span><span class="sxs-lookup"><span data-stu-id="f395c-175">XCALL Syntax</span></span>  
 <span data-ttu-id="f395c-176">UPDATE 預存程序</span><span class="sxs-lookup"><span data-stu-id="f395c-176">UPDATE stored procedures</span></span>  
 <span data-ttu-id="f395c-177">處理 UPDATE 陳述式的預存程序會收到發行項中所定義的所有資料行之原始值 (前置資料影像)，接著是發行項中定義的所有資料行之更新值 (後置資料影像)：</span><span class="sxs-lookup"><span data-stu-id="f395c-177">Stored procedures handling UPDATE statements will be passed the original values (the before image) for all columns defined in the article, followed by the updated values (the after image) for all columns defined in the article:</span></span>  
  
```  
old-c1, old-c2, old-c3,... old-cn, c1, c2, c3,... cn,  
```  
  
 <span data-ttu-id="f395c-178">DELETE 預存程序</span><span class="sxs-lookup"><span data-stu-id="f395c-178">DELETE stored procedures</span></span>  
 <span data-ttu-id="f395c-179">處理 DELETE 陳述式的預存程序會收到發行項中定義的所有資料行之原始值 (前置資料影像)：</span><span class="sxs-lookup"><span data-stu-id="f395c-179">Stored procedures handling DELETE statements will be passed the original (the before image) values for all columns defined in the article:</span></span>  
  
```  
old-c1, old-c2, old-c3,... old-cn  
```  
  
> [!NOTE]  
>  <span data-ttu-id="f395c-180">使用 XCALL 時， **text** 與 **image** 資料行的前置資料影像值預期為 NULL。</span><span class="sxs-lookup"><span data-stu-id="f395c-180">When using XCALL, the before image values for **text** and **image** columns are expected to be NULL.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f395c-181">範例</span><span class="sxs-lookup"><span data-stu-id="f395c-181">Examples</span></span>  
 <span data-ttu-id="f395c-182">下列程序是為 `Vendor Table` 範例資料庫中的 [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)] 建立的預設程序。</span><span class="sxs-lookup"><span data-stu-id="f395c-182">The following procedures are the default procedures created for the `Vendor Table` in the [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)] sample database.</span></span>  
  
```  
--INSERT procedure using CALL syntax  
create procedure [sp_MSins_PurchasingVendor]   
  @c1 int,@c2 nvarchar(15),@c3 nvarchar(50),@c4 tinyint,@c5 bit,@c6 bit,@c7 nvarchar(1024),@c8 datetime  
as   
begin   
insert into [Purchasing].[Vendor]([VendorID]  
,[AccountNumber]  
,[Name]  
,[CreditRating]  
,[PreferredVendorStatus]  
,[ActiveFlag]  
,[PurchasingWebServiceURL]  
,[ModifiedDate])  
values (   
 @c1  
,@c2  
,@c3  
,@c4  
,@c5  
,@c6  
,@c7  
,@c8  
 )   
end  
go  
  
--UPDATE procedure using SCALL syntax  
create procedure [sp_MSupd_PurchasingVendor]   
 @c1 int = null,@c2 nvarchar(15) = null,@c3 nvarchar(50) = null,@c4 tinyint = null,@c5 bit = null,@c6 bit = null,@c7 nvarchar(1024) = null,@c8 datetime = null,@pkc1 int  
,@bitmap binary(2)  
as  
begin  
update [Purchasing].[Vendor] set   
 [AccountNumber] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [AccountNumber] end  
,[Name] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [Name] end  
,[CreditRating] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [CreditRating] end  
,[PreferredVendorStatus] = case substring(@bitmap,1,1) & 16 when 16 then @c5 else [PreferredVendorStatus] end  
,[ActiveFlag] = case substring(@bitmap,1,1) & 32 when 32 then @c6 else [ActiveFlag] end  
,[PurchasingWebServiceURL] = case substring(@bitmap,1,1) & 64 when 64 then @c7 else [PurchasingWebServiceURL] end  
,[ModifiedDate] = case substring(@bitmap,1,1) & 128 when 128 then @c8 else [ModifiedDate] end  
where [VendorID] = @pkc1  
if @@rowcount = 0  
    if @@microsoftversion>0x07320000  
        exec sp_MSreplraiserror 20598  
end  
go  
  
--DELETE procedure using CALL syntax  
create procedure [sp_MSdel_PurchasingVendor]   
  @pkc1 int  
as   
begin   
delete [Purchasing].[Vendor]  
where [VendorID] = @pkc1  
if @@rowcount = 0  
    if @@microsoftversion>0x07320000  
        exec sp_MSreplraiserror 20598  
end   
go  
```  
  
## <a name="see-also"></a><span data-ttu-id="f395c-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f395c-183">See Also</span></span>  
 [<span data-ttu-id="f395c-184">Article Options for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="f395c-184">Article Options for Transactional Replication</span></span>](article-options-for-transactional-replication.md)  
  
  
