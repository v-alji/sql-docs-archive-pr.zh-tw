---
title: 取得 DDL 觸發程序的資訊 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- metadata [SQL Server], triggers
- status information [SQL Server], DDL triggers
- DDL triggers, metadata
ms.assetid: 462becea-292a-4b9e-bb98-533e89733911
author: rothja
ms.author: jroth
ms.openlocfilehash: 9cd71d188c2f53bd9872359199c07d700688552d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606133"
---
# <a name="get-information-about-ddl-triggers"></a><span data-ttu-id="fd14b-102">取得 DDL 觸發程序的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="fd14b-102">Get Information About DDL Triggers</span></span>
  <span data-ttu-id="fd14b-103">本章節所列的目錄檢視可用來取得 DDL 觸發程序的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fd14b-103">The catalog views listed in this section can be used to get information about DDL Triggers.</span></span>  
  
 <span data-ttu-id="fd14b-104">**取得 DDL 觸發程序引發所在之事件或事件群組的相關資訊**</span><span class="sxs-lookup"><span data-stu-id="fd14b-104">**To get information about the events or event groups on which a DDL trigger can fire.**</span></span>  
  
-   [<span data-ttu-id="fd14b-105">sys.trigger_event_types &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fd14b-105">sys.trigger_event_types &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-trigger-event-types-transact-sql)  
  
 <span data-ttu-id="fd14b-106">**檢視觸發程序的相依性**</span><span class="sxs-lookup"><span data-stu-id="fd14b-106">**To view the dependencies of a trigger**</span></span>  
  
-   [<span data-ttu-id="fd14b-107">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fd14b-107">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
-   [<span data-ttu-id="fd14b-108">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fd14b-108">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
-   [<span data-ttu-id="fd14b-109">sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fd14b-109">sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql)  
  
## <a name="database-scoped-ddl-triggers"></a><span data-ttu-id="fd14b-110">資料庫範圍的 DDL 觸發程序</span><span class="sxs-lookup"><span data-stu-id="fd14b-110">Database-Scoped DDL Triggers</span></span>  
 <span data-ttu-id="fd14b-111">**若要取得資料庫範圍觸發程序的相關資訊**</span><span class="sxs-lookup"><span data-stu-id="fd14b-111">**To get information about database-scoped triggers**</span></span>  
  
-   [<span data-ttu-id="fd14b-112">sys.triggers &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fd14b-112">sys.triggers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql)  
  
 <span data-ttu-id="fd14b-113">**若要取得引發觸發程序之資料庫事件的相關資訊**</span><span class="sxs-lookup"><span data-stu-id="fd14b-113">**To get information about database events that fire triggers**</span></span>  
  
-   [<span data-ttu-id="fd14b-114">sys.trigger_events &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fd14b-114">sys.trigger_events &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql)  
  
 <span data-ttu-id="fd14b-115">**若要檢視資料庫範圍觸發程序的定義**</span><span class="sxs-lookup"><span data-stu-id="fd14b-115">**To view the definition of a database-scoped trigger**</span></span>  
  
-   [<span data-ttu-id="fd14b-116">sys.sql_modules &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fd14b-116">sys.sql_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)  
  
 <span data-ttu-id="fd14b-117">**若要取得 CLR 資料庫範圍觸發程序的相關資訊**</span><span class="sxs-lookup"><span data-stu-id="fd14b-117">**To get information about CLR database-scoped triggers**</span></span>  
  
-   [<span data-ttu-id="fd14b-118">sys.assembly_modules &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fd14b-118">sys.assembly_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql)  
  
## <a name="server-scoped-ddl-triggers"></a><span data-ttu-id="fd14b-119">伺服器範圍的 DDL 觸發程序</span><span class="sxs-lookup"><span data-stu-id="fd14b-119">Server-Scoped DDL Triggers</span></span>  
 <span data-ttu-id="fd14b-120">**若要取得伺服器範圍觸發程序的相關資訊**</span><span class="sxs-lookup"><span data-stu-id="fd14b-120">**To get information about server-scoped triggers**</span></span>  
  
-   [<span data-ttu-id="fd14b-121">sys.server_triggers &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fd14b-121">sys.server_triggers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql)  
  
 <span data-ttu-id="fd14b-122">**若要取得引發觸發程序之伺服器事件的相關資訊**</span><span class="sxs-lookup"><span data-stu-id="fd14b-122">**To get information about server events that fire triggers**</span></span>  
  
-   [<span data-ttu-id="fd14b-123">sys.server_trigger_events &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fd14b-123">sys.server_trigger_events &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql)  
  
 <span data-ttu-id="fd14b-124">**若要檢視伺服器範圍觸發程序的定義**</span><span class="sxs-lookup"><span data-stu-id="fd14b-124">**To view the definition of a server-scoped trigger**</span></span>  
  
-   [<span data-ttu-id="fd14b-125">sys.server_sql_modules &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fd14b-125">sys.server_sql_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql)  
  
 <span data-ttu-id="fd14b-126">**若要取得 CLR 伺服器範圍觸發程序的相關資訊**</span><span class="sxs-lookup"><span data-stu-id="fd14b-126">**To get information about CLR server-scoped triggers**</span></span>  
  
-   [<span data-ttu-id="fd14b-127">sys.server_assembly_modules &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fd14b-127">sys.server_assembly_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="fd14b-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd14b-128">See Also</span></span>  
 [<span data-ttu-id="fd14b-129">DDL 觸發程序</span><span class="sxs-lookup"><span data-stu-id="fd14b-129">DDL Triggers</span></span>](../triggers/ddl-triggers.md)  
  
  
