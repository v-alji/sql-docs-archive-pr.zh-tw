---
title: 移除卸載系統物件的語句 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- drop system objects [SQL Server]
ms.assetid: cdfc3c50-c801-4039-a4bf-b35f876f1c61
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d9e8fbfd4a436e87cee413d95468ccf5dd36b9dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584986"
---
# <a name="remove-statements-that-drop-system-objects"></a><span data-ttu-id="3f940-102">移除卸除系統物件的陳述式</span><span class="sxs-lookup"><span data-stu-id="3f940-102">Remove statements that drop system objects</span></span>
  <span data-ttu-id="3f940-103">Upgrade Advisor 偵測到卸除系統物件的陳述式。</span><span class="sxs-lookup"><span data-stu-id="3f940-103">Upgrade Advisor detected statements that drop system objects.</span></span> <span data-ttu-id="3f940-104">系統物件（包含擴充預存程式）會部署在唯讀的**resource**資料庫中 (mssqlsystemresource) 且無法卸載。</span><span class="sxs-lookup"><span data-stu-id="3f940-104">System objects, including extended stored procedures, are deployed in the read-only **resource** database (mssqlsystemresource) and cannot be dropped.</span></span> <span data-ttu-id="3f940-105">請修改您的應用程式，以便撤銷或拒絕系統物件的 EXECUTE 權限。</span><span class="sxs-lookup"><span data-stu-id="3f940-105">Modify your applications to either revoke or deny EXECUTE permission on system objects.</span></span>  
  
## <a name="component"></a><span data-ttu-id="3f940-106">元件</span><span class="sxs-lookup"><span data-stu-id="3f940-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="3f940-107">描述</span><span class="sxs-lookup"><span data-stu-id="3f940-107">Description</span></span>  
 <span data-ttu-id="3f940-108">DROP TABLE、DROP PROCEDURE 和**sp_dropextendedproc**之類的語句無法用來移除系統物件，因為這些物件是部署在唯讀的**resource**資料庫中。</span><span class="sxs-lookup"><span data-stu-id="3f940-108">Statements such as DROP TABLE, DROP PROCEDURE, and **sp_dropextendedproc** cannot be used to remove system objects, because these objects are deployed in the read-only **resource** database.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="3f940-109">更正動作</span><span class="sxs-lookup"><span data-stu-id="3f940-109">Corrective Action</span></span>  
 <span data-ttu-id="3f940-110">請移除嘗試從應用程式中卸除系統物件的所有陳述式。</span><span class="sxs-lookup"><span data-stu-id="3f940-110">Remove all statements that try to drop system objects from your applications.</span></span> <span data-ttu-id="3f940-111">請修改您的應用程式，以便撤銷或拒絕系統物件的 EXECUTE 權限。</span><span class="sxs-lookup"><span data-stu-id="3f940-111">Modify your applications to either revoke or deny EXECUTE permission on system objects.</span></span> <span data-ttu-id="3f940-112">或者，您也可以使用介面區組態 (SAC) 工具來停用其中某些物件。</span><span class="sxs-lookup"><span data-stu-id="3f940-112">Alternatively, you can use the Surface Area Configuration (SAC) tool to disable some of these objects.</span></span> <span data-ttu-id="3f940-113">例如，您可以使用 SAC 工具來停用或啟用**xp_cmdshell**擴充預存程式。</span><span class="sxs-lookup"><span data-stu-id="3f940-113">For example, the **xp_cmdshell** extended stored procedure can be disabled or enabled using the SAC tool.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f940-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f940-114">See Also</span></span>  
 <span data-ttu-id="3f940-115">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="3f940-115">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="3f940-116">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="3f940-116">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
