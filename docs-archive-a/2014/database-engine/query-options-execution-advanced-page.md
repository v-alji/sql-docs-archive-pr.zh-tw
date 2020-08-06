---
title: 查詢選項執行 (Advanced Page) |Microsoft Docs
ms.prod: sql-server-2014
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.advanced.f1
ms.assetid: 661595ce-99b9-4316-ad80-ed04002d04d5
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: ''
ms.date: 09/03/2019
ms.openlocfilehash: 5b6ab8cc3c788e27946ddb68a3c926e8f926ebd7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705402"
---
# <a name="query-options-execution-advanced-page"></a><span data-ttu-id="c8b37-102">查詢選項執行 (進階頁面)</span><span class="sxs-lookup"><span data-stu-id="c8b37-102">Query Options Execution (Advanced Page)</span></span>

  <span data-ttu-id="c8b37-103">使用 **SET** 陳述式時，有許多選項可用。</span><span class="sxs-lookup"><span data-stu-id="c8b37-103">A variety of options are available using the **SET** statement.</span></span> <span data-ttu-id="c8b37-104">使用此頁面來指定**SET**選項，以執行 Microsoft SQL Server 查詢。</span><span class="sxs-lookup"><span data-stu-id="c8b37-104">Use this page to specify a **SET** option to run Microsoft SQL Server queries.</span></span> <span data-ttu-id="c8b37-105">如需上述各選項的詳細資訊，請參閱《SQL Server 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="c8b37-105">For detailed information on each of these options, see SQL Server Books Online.</span></span>
  
<span data-ttu-id="c8b37-106">**設定 NOCOUNT**不會傳回資料列數目的計數，做為包含結果集的訊息。</span><span class="sxs-lookup"><span data-stu-id="c8b37-106">**SET NOCOUNT** Doesn't return the count of the number of rows, as a message with the result set.</span></span> <span data-ttu-id="c8b37-107">依預設，會清除此選項。</span><span class="sxs-lookup"><span data-stu-id="c8b37-107">This option is cleared by default.</span></span>

<span data-ttu-id="c8b37-108">**設定 NOEXEC**不會執行查詢。</span><span class="sxs-lookup"><span data-stu-id="c8b37-108">**SET NOEXEC** Doesn't run the query.</span></span> <span data-ttu-id="c8b37-109">依預設，會清除此選項。</span><span class="sxs-lookup"><span data-stu-id="c8b37-109">This option is cleared by default.</span></span>

<span data-ttu-id="c8b37-110">**設定 PARSEONLY**檢查每個查詢的語法，但不執行查詢。</span><span class="sxs-lookup"><span data-stu-id="c8b37-110">**SET PARSEONLY** Checks the syntax of each query but Doesn't run the queries.</span></span> <span data-ttu-id="c8b37-111">依預設，會清除此選項。</span><span class="sxs-lookup"><span data-stu-id="c8b37-111">This option is cleared by default.</span></span>  

<span data-ttu-id="c8b37-112">**設定 CONCAT_Null_YIELDS_Null**選取此核取方塊時，串連現有值與的查詢，一律會傳回 `NULL` `NULL` 做為結果。</span><span class="sxs-lookup"><span data-stu-id="c8b37-112">**SET CONCAT_NULL_YIELDS_NULL** When this check box is selected, queries that concatenate an existing value with a `NULL`, always return a `NULL` as the result.</span></span> <span data-ttu-id="c8b37-113">如果清除此核取方塊，現有的值與 `NULL` 串連，則會傳回現有的值。</span><span class="sxs-lookup"><span data-stu-id="c8b37-113">When this check box is cleared, an existing value concatenated with a `NULL`, returns the existing value.</span></span> <span data-ttu-id="c8b37-114">預設會選取這個選項。</span><span class="sxs-lookup"><span data-stu-id="c8b37-114">This option is selected by default.</span></span>

<span data-ttu-id="c8b37-115">**設定 ARITHABORT**當選取這個核取方塊時，當 `INSERT` 、 `DELETE` 或 `UPDATE` 語句遇到算術錯誤 (溢位、零除，或在運算式評估期間) 的定義域錯誤，查詢或批次就會終止。</span><span class="sxs-lookup"><span data-stu-id="c8b37-115">**SET ARITHABORT** When this check box is selected, when an `INSERT`, `DELETE` or `UPDATE` statement encounters an arithmetic error (overflow, divide-by-zero, or a domain error) during expression evaluation the query or batch is terminated.</span></span> <span data-ttu-id="c8b37-116">如果清除此核取方塊，在可能的情況下就會為該值提供 `NULL`，而查詢會繼續進行，並在結果中包含訊息。</span><span class="sxs-lookup"><span data-stu-id="c8b37-116">When this check box is cleared, a `NULL` is provided for that value if possible, the query continues, and a message is included with the result.</span></span> <span data-ttu-id="c8b37-117">請參閱線上叢書，以取得此行為的詳細描述。</span><span class="sxs-lookup"><span data-stu-id="c8b37-117">See Books Online for a more extensive description of this behavior.</span></span> <span data-ttu-id="c8b37-118">預設會選取這個選項。</span><span class="sxs-lookup"><span data-stu-id="c8b37-118">This option is selected by default.</span></span>
  
<span data-ttu-id="c8b37-119">**設定 SHOWPLAN_TEXT**選取這個核取方塊時，會以文字形式傳回查詢計劃與每個查詢。</span><span class="sxs-lookup"><span data-stu-id="c8b37-119">**SET SHOWPLAN_TEXT** When this check box is selected, the query plan is returned in text form with each query.</span></span> <span data-ttu-id="c8b37-120">依預設，會清除此選項。</span><span class="sxs-lookup"><span data-stu-id="c8b37-120">This option is cleared by default.</span></span>
  
<span data-ttu-id="c8b37-121">**SET STATISTICS TIME** 如果選取此核取方塊，則每個查詢就會一併傳回時間統計資料。</span><span class="sxs-lookup"><span data-stu-id="c8b37-121">**SET STATISTICS TIME** When this check box is selected, the time statistics are returned with each query.</span></span> <span data-ttu-id="c8b37-122">依預設，會清除此選項。</span><span class="sxs-lookup"><span data-stu-id="c8b37-122">This option is cleared by default.</span></span>
  
<span data-ttu-id="c8b37-123">**設定統計資料 IO**如果選取此核取方塊，每個查詢都會傳回關於輸入/輸出 (i/o) 的統計資料。</span><span class="sxs-lookup"><span data-stu-id="c8b37-123">**SET STATISTICS IO** When this check box is selected, statistics regarding input/output (I/O) are returned with each query.</span></span> <span data-ttu-id="c8b37-124">依預設，會清除此選項。</span><span class="sxs-lookup"><span data-stu-id="c8b37-124">This option is cleared by default.</span></span>
  
<span data-ttu-id="c8b37-125">**SET TRANSACTION ISOLATION LEVEL** 依預設，會設定 READ COMMITTED 交易隔離等級。</span><span class="sxs-lookup"><span data-stu-id="c8b37-125">**SET TRANSACTION ISOLATION LEVEL** The READ COMMITTED transaction isolation level is set by default.</span></span> <span data-ttu-id="c8b37-126">如需詳細資訊，請參閱 [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c8b37-126">For more information, see [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).</span></span> <span data-ttu-id="c8b37-127">無法使用快照集交易隔離等級。</span><span class="sxs-lookup"><span data-stu-id="c8b37-127">SNAPSHOT transaction isolation level isn't available.</span></span> <span data-ttu-id="c8b37-128">若要使用 SNAPSHOT 隔離，請加入下列 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="c8b37-128">To use SNAPSHOT isolation, add the following [!INCLUDE[tsql](../includes/tsql-md.md)] statement:</span></span>
  
  ```sql
  SET TRANSACTION ISOLATION LEVEL SNAPSHOT;
  GO
  ```

<span data-ttu-id="c8b37-129">**設定鎖死優先順序**預設值為 [**一般**]，可讓每個查詢在發生鎖死時擁有相同的優先順序。</span><span class="sxs-lookup"><span data-stu-id="c8b37-129">**SET DEADLOCK PRIORITY** The default value of **Normal** allows each query to have the same priority when a deadlock occurs.</span></span> <span data-ttu-id="c8b37-130">如果您要此查詢在發生任何死結衝突時失敗，並選取為要結束的查詢，請從下拉式清單中選取「低」優先權。</span><span class="sxs-lookup"><span data-stu-id="c8b37-130">Select the priority Low from the drop-down list, if you want this query to lose any deadlock conflict and be selected as the query to be terminated.</span></span>

<span data-ttu-id="c8b37-131">**設定鎖定超時**預設值-1 表示會保留鎖定，直到交易完成為止。</span><span class="sxs-lookup"><span data-stu-id="c8b37-131">**SET LOCK TIMEOUT** The default value of -1 indicates that locks are held until transactions are completed.</span></span> <span data-ttu-id="c8b37-132">值為 0 表示根本不等候，並在發生鎖定時立刻傳回訊息。</span><span class="sxs-lookup"><span data-stu-id="c8b37-132">A value of 0 means not to wait at all and return a message as soon as a lock is encountered.</span></span> <span data-ttu-id="c8b37-133">提供大於 0 毫秒的值，即可指定當交易的鎖定時間超過指定值，就結束交易。</span><span class="sxs-lookup"><span data-stu-id="c8b37-133">Provide a value of greater than 0 milliseconds to terminate a transaction if the locks for transaction must be held for greater than that time.</span></span>

<span data-ttu-id="c8b37-134">**設定 QUERY_GOVERNOR_COST_LIMIT**使用 [**查詢管理員成本限制**] 選項，即可指定查詢可以執行的時間週期上限。</span><span class="sxs-lookup"><span data-stu-id="c8b37-134">**SET QUERY_GOVERNOR_COST_LIMIT** Use the **query governor cost limit** option to specify an upper limit on the time period in which a query can run.</span></span> <span data-ttu-id="c8b37-135">查詢成本代表在特定的硬體組態上，預估完成查詢所需的時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="c8b37-135">Query cost refers to the estimated elapsed time, in seconds, required to complete a query on a specific hardware configuration.</span></span> <span data-ttu-id="c8b37-136">預設值為 0 表示查詢執行沒有時間長度的限制</span><span class="sxs-lookup"><span data-stu-id="c8b37-136">The default setting of 0 indicates no limit to the length of time a query will run</span></span>

<span data-ttu-id="c8b37-137">**隱藏提供者訊息標頭**選取此核取方塊時，不會顯示來自提供者 (的狀態訊息，例如 OLE DB 提供者) 。</span><span class="sxs-lookup"><span data-stu-id="c8b37-137">**Suppress provider message headers** When this check box is selected, status messages from the provider (such as the OLE DB provider) aren't displayed.</span></span> <span data-ttu-id="c8b37-138">依預設，這個核取方塊為已選取。</span><span class="sxs-lookup"><span data-stu-id="c8b37-138">This check box is selected by default.</span></span> <span data-ttu-id="c8b37-139">當疑難排解查詢於提供者層級失敗時，清除此核取方塊即可查看提供者訊息。</span><span class="sxs-lookup"><span data-stu-id="c8b37-139">Clear this check box to see the provider messages when troubleshooting queries that may be failing at the provider level.</span></span>

<span data-ttu-id="c8b37-140">**查詢執行後中斷**連線選取此核取方塊時，SQL Server 的連接會在查詢完成後終止。</span><span class="sxs-lookup"><span data-stu-id="c8b37-140">**Disconnect after the query executes** When this check box is selected, the connection to SQL Server is terminated after the query completes.</span></span> <span data-ttu-id="c8b37-141">依預設，會清除此選項。</span><span class="sxs-lookup"><span data-stu-id="c8b37-141">This option is cleared by default.</span></span>

<span data-ttu-id="c8b37-142">**顯示完成時間**可讓您在查詢結果之後或 [訊息] 索引標籤中，列印查詢執行完成的時間。</span><span class="sxs-lookup"><span data-stu-id="c8b37-142">**Show completion time** Allows you to print the time at which the query execution completed either after the query results or in the messages tab.</span></span>

<span data-ttu-id="c8b37-143">**適用于 Always Encrypted 的 VBS 記憶體保護區證明通訊協定**可讓您設定以虛擬化為基礎之安全性的證明通訊協定， (VBS) 記憶體保護區由 always Encrypted 搭配安全記憶體保護區使用。</span><span class="sxs-lookup"><span data-stu-id="c8b37-143">**Attestation protocol for VBS enclaves for Always Encrypted** Allows you to set an attestation protocol for Virtualization Based Security (VBS) enclaves used by always Encrypted with secure enclaves.</span></span>

<span data-ttu-id="c8b37-144">目前支援的證明通訊協定為：</span><span class="sxs-lookup"><span data-stu-id="c8b37-144">The current supported attestation protocols are:</span></span>

* <span data-ttu-id="c8b37-145">主機守護者服務-使用 Windows 主機守護者服務 (HGS) 的證明通訊協定。</span><span class="sxs-lookup"><span data-stu-id="c8b37-145">Host Guardian Service - an attestation protocol using Windows Host Guardian Service (HGS).</span></span>

<span data-ttu-id="c8b37-146">如需詳細資訊，請參閱[使用 secure 記憶體保護區](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves?view=sqlallproducts-allversions)和[secure 記憶體保護區證明](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves?view=sqlallproducts-allversions#secure-enclave-attestation)Always Encrypted。</span><span class="sxs-lookup"><span data-stu-id="c8b37-146">For more information, see [Always Encrypted with secure enclaves](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves?view=sqlallproducts-allversions) and [Secure Enclave Attestation](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves?view=sqlallproducts-allversions#secure-enclave-attestation).</span></span>

<span data-ttu-id="c8b37-147">**重設為預設值** 將此頁面上的所有值重設為原始預設值。</span><span class="sxs-lookup"><span data-stu-id="c8b37-147">**Reset to Default** Resets all values on this page to the original default values.</span></span>
