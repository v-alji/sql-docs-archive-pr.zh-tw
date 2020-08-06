---
title: 在 DML 觸發程式內，移除已插入和已刪除之資料表的 DDL 作業 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- data definition language [SQL Server]
- DDL statements [SQL Server]
- DML triggers, removing DDL operations
ms.assetid: e49ba7d5-787f-4052-b985-b699195d982b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 61f7ab78b5ab6251b7f27401d36423ec27141c4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704745"
---
# <a name="remove-ddl-operations-on-the-inserted-and-deleted-tables-inside-dml-triggers"></a><span data-ttu-id="8a424-102">在 DML 觸發程序內，移除已插入和已刪除資料表的 DDL 作業</span><span class="sxs-lookup"><span data-stu-id="8a424-102">Remove DDL operations on the inserted and deleted tables inside DML triggers</span></span>
  <span data-ttu-id="8a424-103">資料定義語言 (DDL) 語句（例如 CREATE INDEX）無法在 DML 觸發程式內的插入和刪除資料表上執行。</span><span class="sxs-lookup"><span data-stu-id="8a424-103">Data definition language (DDL) statements, such as CREATE INDEX, cannot be performed on the inserted and deleted tables inside DML triggers.</span></span> <span data-ttu-id="8a424-104">在舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，您可以在插入和刪除的資料表上執行某些 DDL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="8a424-104">Some DDL statements on the inserted and deleted tables are permitted in earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8a424-105">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜使用插入和刪除的資料表＞。</span><span class="sxs-lookup"><span data-stu-id="8a424-105">For more information, see "Using the inserted and deleted Tables" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="component"></a><span data-ttu-id="8a424-106">元件</span><span class="sxs-lookup"><span data-stu-id="8a424-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="8a424-107">更正動作</span><span class="sxs-lookup"><span data-stu-id="8a424-107">Corrective Action</span></span>  
 <span data-ttu-id="8a424-108">請移除在 DML 觸發程序內部所插入和刪除之資料表上執行的任何 DDL 作業。</span><span class="sxs-lookup"><span data-stu-id="8a424-108">Remove any DDL operations that are performed on the inserted and deleted tables inside DML triggers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a424-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a424-109">See Also</span></span>  
 <span data-ttu-id="8a424-110">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="8a424-110">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="8a424-111">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="8a424-111">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
