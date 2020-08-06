---
title: 查看已註冊封裝的擴充事件目標 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events]
- viewing event targets
- extended events [SQL Server], viewing targets
ms.assetid: 4985aa5f-ac99-49f6-852c-9d25916549e9
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8e796d141ef943399fc2469c232b34b1956cef3b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607012"
---
# <a name="view-the-extended-events-targets-for-registered-packages"></a><span data-ttu-id="fbd54-102">檢視已註冊之封裝的擴充事件目標</span><span class="sxs-lookup"><span data-stu-id="fbd54-102">View the Extended Events Targets for Registered Packages</span></span>
  <span data-ttu-id="fbd54-103">在您建立 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 「擴充事件」工作階段之前，判斷哪些「擴充事件」目標可用會非常實用。</span><span class="sxs-lookup"><span data-stu-id="fbd54-103">Before you create a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Extended Events session, it is useful to determine what Extended Events targets are available.</span></span> <span data-ttu-id="fbd54-104">這項工作需要在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中使用查詢編輯器來執行以下程序。</span><span class="sxs-lookup"><span data-stu-id="fbd54-104">This task involves using Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to perform the following procedure.</span></span>  
  
 <span data-ttu-id="fbd54-105">當此程序中的陳述式完成之後，查詢編輯器的 **[結果]** 索引標籤會顯示以下兩個資料行：</span><span class="sxs-lookup"><span data-stu-id="fbd54-105">After the statements in this procedure finish, the **Results** tab of Query Editor displays the following two columns:</span></span>  
  
-   <span data-ttu-id="fbd54-106">package_name</span><span class="sxs-lookup"><span data-stu-id="fbd54-106">package_name</span></span>  
  
-   <span data-ttu-id="fbd54-107">target_name</span><span class="sxs-lookup"><span data-stu-id="fbd54-107">target_name</span></span>  
  
## <a name="to-view-the-extended-events-targets-for-registered-packages-using-query-editor"></a><span data-ttu-id="fbd54-108">若要使用查詢編輯器來檢視已註冊之封裝的擴充事件目標</span><span class="sxs-lookup"><span data-stu-id="fbd54-108">To view the Extended Events targets for registered packages using Query Editor</span></span>  
  
-   <span data-ttu-id="fbd54-109">在查詢編輯器中，發出下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="fbd54-109">In Query Editor, issue the following statements.</span></span>  
  
    ```  
    USE msdb  
    SELECT p.name package_name, o.name target_name  
    FROM sys.dm_xe_objects o  
    JOIN sys.dm_xe_packages p  
         ON o.package_guid = p.guid  
    WHERE o.object_type = 'target'  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fbd54-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbd54-110">See Also</span></span>  
 <span data-ttu-id="fbd54-111">[SQL Server 擴充的事件目標](../../2014/database-engine/sql-server-extended-events-targets.md) </span><span class="sxs-lookup"><span data-stu-id="fbd54-111">[SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md) </span></span>  
 <span data-ttu-id="fbd54-112">[sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fbd54-112">[sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span></span>  
 [<span data-ttu-id="fbd54-113">sys.dm_xe_packages &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fbd54-113">sys.dm_xe_packages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
