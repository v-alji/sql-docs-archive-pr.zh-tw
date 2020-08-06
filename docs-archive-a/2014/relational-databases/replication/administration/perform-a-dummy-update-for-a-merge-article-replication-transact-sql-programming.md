---
title: 執行合併發行項的虛擬更新 (複寫 Transact-sql 程式設計) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_mergedummyupdate
- dummy updates [SQL Server replication]
ms.assetid: 2f339210-4d85-4843-bd94-e86f7100d3ef
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 07fa0f868b2c3f98496046b138424d7d3a2fa2fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705090"
---
# <a name="perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming"></a><span data-ttu-id="46305-102">執行合併發行項的虛擬更新 (複寫 Transact-SQL 程式設計)</span><span class="sxs-lookup"><span data-stu-id="46305-102">Perform a Dummy Update for a Merge Article (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="46305-103">合併式複寫會使用觸發程序做為複寫程序的一部分；對已發行資料表進行更新時，就會引發更新觸發程序。</span><span class="sxs-lookup"><span data-stu-id="46305-103">Merge replication uses triggers as part of the replication process; when an update is made to published table, an update trigger fires.</span></span> <span data-ttu-id="46305-104">在某些情況下，可以不引發觸發程序而更新資料，例如在 WRITETEXT 和 UPDATETEXT 作業期間。</span><span class="sxs-lookup"><span data-stu-id="46305-104">In some cases, data can be updated without the trigger firing, such as during the WRITETEXT and UPDATETEXT operations.</span></span> <span data-ttu-id="46305-105">在這些情況下，您需要加入虛擬 UPDATE 陳述式以明確地複寫變更。</span><span class="sxs-lookup"><span data-stu-id="46305-105">In these cases, you need to add a dummy UPDATE statement explicitly to replicate the change.</span></span> <span data-ttu-id="46305-106">您可以使用複寫預存程序加入虛擬 UPDATE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="46305-106">You can add a dummy UPDATE statement using replication stored procedures.</span></span>  
  
### <a name="to-add-a-dummy-update-statement"></a><span data-ttu-id="46305-107">若要加入虛擬 UPDATE 陳述式</span><span class="sxs-lookup"><span data-stu-id="46305-107">To add a dummy UPDATE statement</span></span>  
  
1.  <span data-ttu-id="46305-108">在需要虛擬更新的已發行合併資料表中的資料列上執行作業 (例如，UPDATETEXT)。</span><span class="sxs-lookup"><span data-stu-id="46305-108">Execute the operation (for example, UPDATETEXT) on a row in a merge published table  that requires a dummy update.</span></span>  
  
2.  <span data-ttu-id="46305-109">在伺服器端 (發行者或訂閱者)，在其中進行變更的資料庫上執行 [sp_mergedummyupdate &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergedummyupdate-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="46305-109">At the server (Publisher or Subscriber) on the database where the change was made, execute [sp_mergedummyupdate &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergedummyupdate-transact-sql).</span></span> <span data-ttu-id="46305-110">指定進行變更的資料表 **@source_object** ，以及已變更之資料列的唯一識別碼 **@rowguid** 。</span><span class="sxs-lookup"><span data-stu-id="46305-110">Specify the table on which the change was made for **@source_object**, and the unique identifier of the changed row for **@rowguid**.</span></span>  
  
3.  <span data-ttu-id="46305-111">同步處理訂閱來複寫已變更的資料列。</span><span class="sxs-lookup"><span data-stu-id="46305-111">Synchronize the subscription to replicate the changed row.</span></span>  
  
  
