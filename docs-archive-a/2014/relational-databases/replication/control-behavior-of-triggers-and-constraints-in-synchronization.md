---
title: 在同步處理期間控制觸發程式和條件約束的行為 (複寫 Transact-sql 程式設計) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- identities [SQL Server replication]
- constraints [SQL Server], replication
- triggers [SQL Server], replication
- triggers [SQL Server replication]
- constraints [SQL Server replication]
- NOT FOR REPLICATION option
- NFR option
ms.assetid: 7c4e0f0e-cadc-4c99-98f4-69799b9b356b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 88176f43295fe2ab1f5f5643a46db1ce6132c5f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585317"
---
# <a name="control-the-behavior-of-triggers-and-constraints-during-synchronization-replication-transact-sql-programming"></a><span data-ttu-id="a7e2b-102">在同步處理期間控制觸發程序和條件約束的行為 (複寫 Transact-SQL 程式設計)</span><span class="sxs-lookup"><span data-stu-id="a7e2b-102">Control the Behavior of Triggers and Constraints During Synchronization (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="a7e2b-103">在同步處理期間，複寫代理程式會在複寫的資料表上執行 [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)、[UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) 和 [DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) 陳述式，這樣可能會讓這些資料表上的資料操作語言 (DML) 觸發程序得以執行。</span><span class="sxs-lookup"><span data-stu-id="a7e2b-103">During synchronization, replication agents execute [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql), [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql), and [DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) statements on replicated tables, which can cause data manipulation language (DML) triggers on these tables to be executed.</span></span> <span data-ttu-id="a7e2b-104">在某些情況下，您可能需要在同步處理期間避免這些觸發程序的引發或避免條件約束的強制使用。</span><span class="sxs-lookup"><span data-stu-id="a7e2b-104">There are cases when you may need to prevent these triggers from firing or constraints from being enforced during synchronization.</span></span> <span data-ttu-id="a7e2b-105">這個行為取決於觸發程序或條件約束的建立方式而定。</span><span class="sxs-lookup"><span data-stu-id="a7e2b-105">This behavior depends on how the trigger or constraint is created.</span></span>  
  
### <a name="to-prevent-triggers-from-executing-during-synchronization"></a><span data-ttu-id="a7e2b-106">在同步處理期間避免觸發程序的執行</span><span class="sxs-lookup"><span data-stu-id="a7e2b-106">To prevent triggers from executing during synchronization</span></span>  
  
1.  <span data-ttu-id="a7e2b-107">在建立新的觸發程序時，請指定 [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) 的 NOT FOR REPLICATION 選項。</span><span class="sxs-lookup"><span data-stu-id="a7e2b-107">When creating a new trigger, specify the NOT FOR REPLICATION option of [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).</span></span>  
  
2.  <span data-ttu-id="a7e2b-108">對於現有的觸發程序，則指定 [ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) 的 NOT FOR REPLICATION 選項。</span><span class="sxs-lookup"><span data-stu-id="a7e2b-108">For an existing trigger, specify the NOT FOR REPLICATION option of [ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql).</span></span>  
  
### <a name="to-prevent-constraints-from-being-enforced-during-synchronization"></a><span data-ttu-id="a7e2b-109">在同步處理期間避免條件約束的強制使用</span><span class="sxs-lookup"><span data-stu-id="a7e2b-109">To prevent constraints from being enforced during synchronization</span></span>  
  
1.  <span data-ttu-id="a7e2b-110">當建立新的 CHECK 或 FOREIGN KEY 條件約束時，請在 [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) 的條件約束定義中指定 CHECK NOT FOR REPLICATION 選項。</span><span class="sxs-lookup"><span data-stu-id="a7e2b-110">When creating a new CHECK or FOREIGN KEY constraint, specify CHECK NOT FOR REPLICATION option in the constraint definition of [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7e2b-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7e2b-111">See Also</span></span>  
 [<span data-ttu-id="a7e2b-112">建立資料表 &#40;Database Engine&#41;</span><span class="sxs-lookup"><span data-stu-id="a7e2b-112">Create Tables &#40;Database Engine&#41;</span></span>](../tables/create-tables-database-engine.md)  
  
  
