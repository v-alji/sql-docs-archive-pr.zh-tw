---
title: 檢查資料庫完整性工作 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.checkdatabaseintegritytask.f1
helpviewer_keywords:
- data integrity [Integration Services]
- Check Database Integrity task [Integration Services]
- checking database consistency
- database consistency checks [Integration Services]
- verifying database consistency
- integrity checking [Integration Services]
ms.assetid: 5a82fe99-4503-429f-9337-e6bac7649fe4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 99a2620a6f3f6a9a73c27fe6bb1abd34af73707d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595240"
---
# <a name="check-database-integrity-task"></a><span data-ttu-id="613ee-102">檢查資料庫完整性工作</span><span class="sxs-lookup"><span data-stu-id="613ee-102">Check Database Integrity Task</span></span>
  <span data-ttu-id="613ee-103">「檢查資料庫完整性」工作會檢查指定資料庫中所有物件的配置及結構完整性。</span><span class="sxs-lookup"><span data-stu-id="613ee-103">The Check Database Integrity task checks the allocation and structural integrity of all the objects in the specified database.</span></span> <span data-ttu-id="613ee-104">這項工作可檢查單一資料庫或多個資料庫，而且您可以選擇是否同時檢查資料庫索引。</span><span class="sxs-lookup"><span data-stu-id="613ee-104">The task can check a single database or multiple databases, and you can choose whether to also check the database indexes.</span></span>  
  
 <span data-ttu-id="613ee-105">「檢查資料庫完整性」工作會封裝 DBCC CHECKDB 陳述式。</span><span class="sxs-lookup"><span data-stu-id="613ee-105">The Check Database Integrity task encapsulates the DBCC CHECKDB statement.</span></span> <span data-ttu-id="613ee-106">如需詳細資訊，請參閱 [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="613ee-106">For more information, see [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql).</span></span>  
  
## <a name="configuration-of-the-check-database-integrity-task"></a><span data-ttu-id="613ee-107">設定檢查資料庫完整性工作</span><span class="sxs-lookup"><span data-stu-id="613ee-107">Configuration of the Check Database Integrity Task</span></span>  
 <span data-ttu-id="613ee-108">您可以透過 [ [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師] 設定屬性。</span><span class="sxs-lookup"><span data-stu-id="613ee-108">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="613ee-109">這項工作位於「 **設計師」中** [工具箱] **的** [維護計畫工作] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 區段。</span><span class="sxs-lookup"><span data-stu-id="613ee-109">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="613ee-110">如需有關可在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師中設定之屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="613ee-110">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="613ee-111">檢查資料庫完整性工作 &#40;維護計畫&#41;</span><span class="sxs-lookup"><span data-stu-id="613ee-111">Check Database Integrity Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/check-database-integrity-task-maintenance-plan.md)  
  
 <span data-ttu-id="613ee-112">如需有關如何在「 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="613ee-112">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="613ee-113">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="613ee-113">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
  
