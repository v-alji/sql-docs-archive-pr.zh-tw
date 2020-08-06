---
title: 為 Oracle 發行者設定交易集作業， (複寫 Transact-sql 程式設計) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_publisherproperty
- Oracle publishing [SQL Server replication], configuring
ms.assetid: beea1a5c-0053-4971-a68f-0da53063fcbb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 43a25ce755a505f0efd7c25243b8969a962ea701
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709250"
---
# <a name="configure-the-transaction-set-job-for-an-oracle-publisher-replication-transact-sql-programming"></a><span data-ttu-id="44f5d-102">設定 Oracle 發行者的交易集作業 (複寫 Transact-SQL 程式設計)</span><span class="sxs-lookup"><span data-stu-id="44f5d-102">Configure the Transaction Set Job for an Oracle Publisher (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="44f5d-103">**Xactset** 作業是由在「Oracle 發行者」端執行的複寫所建立的 Oracle 資料庫作業，可在「記錄讀取器代理程式」未與「發行者」連接時建立交易集。</span><span class="sxs-lookup"><span data-stu-id="44f5d-103">The **Xactset** job is an Oracle database job created by replication that runs at an Oracle Publisher to create transaction sets when the Log Reader Agent is not connected to the Publisher.</span></span> <span data-ttu-id="44f5d-104">您可以使用複寫預存程序，以程式設計的方式從「散發者」啟用和設定此作業。</span><span class="sxs-lookup"><span data-stu-id="44f5d-104">You can enable and configure this job from the Distributor programmatically using replication stored procedures.</span></span> <span data-ttu-id="44f5d-105">如需詳細資訊，請參閱 [Oracle 發行者的效能微調](../non-sql/performance-tuning-for-oracle-publishers.md)。</span><span class="sxs-lookup"><span data-stu-id="44f5d-105">For more information, see [Performance Tuning for Oracle Publishers](../non-sql/performance-tuning-for-oracle-publishers.md).</span></span>  
  
### <a name="to-enable-the-transaction-set-job"></a><span data-ttu-id="44f5d-106">若要啟用交易集作業</span><span class="sxs-lookup"><span data-stu-id="44f5d-106">To enable the transaction set job</span></span>  
  
1.  <span data-ttu-id="44f5d-107">在「Oracle 發行者」端，將 **job_queue_processes** 初始化參數設定為足夠的值，以允許 Xactset 作業執行。</span><span class="sxs-lookup"><span data-stu-id="44f5d-107">At the Oracle Publisher, set the **job_queue_processes** initialization parameter to a sufficient value to allow the Xactset job run.</span></span> <span data-ttu-id="44f5d-108">如需有關此參數的詳細資訊，請參閱「Oracle 發行者」的資料庫文件。</span><span class="sxs-lookup"><span data-stu-id="44f5d-108">For more information about this parameter, see the database documentation for the Oracle Publisher.</span></span>  
  
2.  <span data-ttu-id="44f5d-109">在「散發者」端執行 [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="44f5d-109">At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="44f5d-110">指定「 \*\* \@ 發行者**」的「Oracle 發行者」的名稱、針對 `xactsetbatching` \*\* \@ propertyname**使用的值，以及 `enabled` 針對\*\* \@ propertyvalue\*\*指定的值。</span><span class="sxs-lookup"><span data-stu-id="44f5d-110">Specify the name of the Oracle Publisher for **\@publisher**, a value of `xactsetbatching` for **\@propertyname**, and a value of `enabled` for **\@propertyvalue**.</span></span>  
  
3.  <span data-ttu-id="44f5d-111">在「散發者」端執行 [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="44f5d-111">At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="44f5d-112">針對\*\* \@ [發行者]\*\* 指定 [Oracle 發行者] 的名稱，針對 [propertyname] 指定 [值]， `xactsetjobinterval` 並針對 [ \*\* \@ propertyvalue**] 指定 [作業間隔（以分鐘** \@ \*\*為單位）]。</span><span class="sxs-lookup"><span data-stu-id="44f5d-112">Specify the name of the Oracle Publisher for **\@publisher**, a value of `xactsetjobinterval` for **\@propertyname**, and the job interval, in minutes, for **\@propertyvalue**.</span></span>  
  
4.  <span data-ttu-id="44f5d-113">在「散發者」端執行 [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="44f5d-113">At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="44f5d-114">指定「 \*\* \@ 發行者**」的「Oracle 發行者」的名稱、針對 `xactsetjob` \*\* \@ propertyname**使用的值，以及 `enabled` 針對\*\* \@ propertyvalue\*\*指定的值。</span><span class="sxs-lookup"><span data-stu-id="44f5d-114">Specify the name of the Oracle Publisher for **\@publisher**, a value of `xactsetjob` for **\@propertyname**, and a value of `enabled` for **\@propertyvalue**.</span></span>  
  
### <a name="to-configure-the-transaction-set-job"></a><span data-ttu-id="44f5d-115">若要設定交易集作業</span><span class="sxs-lookup"><span data-stu-id="44f5d-115">To configure the transaction set job</span></span>  
  
1.  <span data-ttu-id="44f5d-116">(選擇性) 在「散發者」端執行 [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="44f5d-116">(Optional) At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="44f5d-117">針對 **\@publisher** 指定 Oracle 發行者的名稱。</span><span class="sxs-lookup"><span data-stu-id="44f5d-117">Specify the name of the Oracle Publisher for **\@publisher**.</span></span> <span data-ttu-id="44f5d-118">這麼做會傳回「發行者」端 **Xactset** 作業的屬性。</span><span class="sxs-lookup"><span data-stu-id="44f5d-118">This returns properties of the **Xactset** job at the Publisher.</span></span>  
  
2.  <span data-ttu-id="44f5d-119">在「散發者」端執行 [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="44f5d-119">At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="44f5d-120">指定\*\* \@ 發行者**的「Oracle 發行者」名稱、針對** \@ propertyname**所設定之 Xactset 作業屬性的名稱，以及適用于** \@ propertyvalue\*\*的新設定。</span><span class="sxs-lookup"><span data-stu-id="44f5d-120">Specify the name of the Oracle Publisher for **\@publisher**, the name of the Xactset job property being set for **\@propertyname**, and new setting for **\@propertyvalue**.</span></span>  
  
3.  <span data-ttu-id="44f5d-121">(選擇性) 針對每個要設定的 Xactset 作業屬性重複步驟 2。</span><span class="sxs-lookup"><span data-stu-id="44f5d-121">(Optional) Repeat step 2 for each Xactset job property being set.</span></span> <span data-ttu-id="44f5d-122">變更屬性時 `xactsetjobinterval` ，您必須在「Oracle 發行者」上重新開機作業，新的間隔才會生效。</span><span class="sxs-lookup"><span data-stu-id="44f5d-122">When changing the `xactsetjobinterval` property, you must restart the job on the Oracle Publisher for the new interval to take effect.</span></span>  
  
### <a name="to-view-properties-of-the-transaction-set-job"></a><span data-ttu-id="44f5d-123">若要檢視交易集作業的屬性</span><span class="sxs-lookup"><span data-stu-id="44f5d-123">To view properties of the transaction set job</span></span>  
  
1.  <span data-ttu-id="44f5d-124">在「散發者」端執行 [sp_helpxactsetjob](/sql/relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="44f5d-124">At the Distributor, execute [sp_helpxactsetjob](/sql/relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql).</span></span> <span data-ttu-id="44f5d-125">針對 **\@publisher** 指定 Oracle 發行者的名稱。</span><span class="sxs-lookup"><span data-stu-id="44f5d-125">Specify the name of the Oracle Publisher for **\@publisher**.</span></span>  
  
### <a name="to-disable-the-transaction-set-job"></a><span data-ttu-id="44f5d-126">若要停用交易集作業</span><span class="sxs-lookup"><span data-stu-id="44f5d-126">To disable the transaction set job</span></span>  
  
1.  <span data-ttu-id="44f5d-127">在「散發者」端執行 [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="44f5d-127">At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="44f5d-128">指定「 \*\* \@ 發行者**」的「Oracle 發行者」的名稱、針對 `xactsetjob` \*\* \@ propertyname**使用的值，以及 `disabled` 針對\*\* \@ propertyvalue\*\*指定的值。</span><span class="sxs-lookup"><span data-stu-id="44f5d-128">Specify the name of the Oracle Publisher for **\@publisher**, a value of `xactsetjob` for **\@propertyname**, and a value of `disabled` for **\@propertyvalue**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44f5d-129">範例</span><span class="sxs-lookup"><span data-stu-id="44f5d-129">Example</span></span>  
 <span data-ttu-id="44f5d-130">下列範例會啟用 `Xactset` 作業，並在執行之間設定三分鐘的間隔。</span><span class="sxs-lookup"><span data-stu-id="44f5d-130">The following example enables the `Xactset` job and sets an interval of three minutes between runs.</span></span>  
  
 [!code-sql[HowTo#sp_enable_xactsetjob](../../../snippets/tsql/SQL15/replication/howto/tsql/enablexactsetjob.sql#sp_enable_xactsetjob)]  
  
## <a name="see-also"></a><span data-ttu-id="44f5d-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44f5d-131">See Also</span></span>  
 <span data-ttu-id="44f5d-132">[Oracle 發行者的效能微調](../non-sql/performance-tuning-for-oracle-publishers.md) </span><span class="sxs-lookup"><span data-stu-id="44f5d-132">[Performance Tuning for Oracle Publishers](../non-sql/performance-tuning-for-oracle-publishers.md) </span></span>  
 [<span data-ttu-id="44f5d-133">Replication System Stored Procedures Concepts</span><span class="sxs-lookup"><span data-stu-id="44f5d-133">Replication System Stored Procedures Concepts</span></span>](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
