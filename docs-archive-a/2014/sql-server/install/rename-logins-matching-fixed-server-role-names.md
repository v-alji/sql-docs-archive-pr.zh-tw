---
title: 重新命名符合固定伺服器角色名稱的登入 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- user-defined login names [SQL Server]
- fixed server roles [SQL Server]
- renamed logins [SQL Server]
- logins [SQL Server], names
ms.assetid: 10a1d77c-3153-474f-a6a0-969556794467
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 296ae4d4051e79e3c5d3bc158ef3e87c9164ecd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704701"
---
# <a name="rename-logins-matching-fixed-server-role-names"></a><span data-ttu-id="b791a-102">重新命名符合固定伺服器角色名稱的登入</span><span class="sxs-lookup"><span data-stu-id="b791a-102">Rename logins matching fixed server role names</span></span>
  <span data-ttu-id="b791a-103">Upgrade Advisor 偵測到與固定伺服器角色名稱相符的一個或多個使用者自訂登入名稱。</span><span class="sxs-lookup"><span data-stu-id="b791a-103">Upgrade Advisor detected one or more user-defined login names that match the names of fixed server roles.</span></span> <span data-ttu-id="b791a-104">會保留固定伺服器角色名稱。</span><span class="sxs-lookup"><span data-stu-id="b791a-104">Fixed server role names are reserved.</span></span> <span data-ttu-id="b791a-105">升級之前，請先重新命名登入。</span><span class="sxs-lookup"><span data-stu-id="b791a-105">Rename the login before you upgrade.</span></span>  
  
## <a name="component"></a><span data-ttu-id="b791a-106">元件</span><span class="sxs-lookup"><span data-stu-id="b791a-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="b791a-107">描述</span><span class="sxs-lookup"><span data-stu-id="b791a-107">Description</span></span>  
 <span data-ttu-id="b791a-108">下列固定伺服器角色名稱已保留，無法當做使用者自訂登入名稱使用。</span><span class="sxs-lookup"><span data-stu-id="b791a-108">The following fixed server role names are reserved and cannot be used as user-defined login names.</span></span>  
  
-   <span data-ttu-id="b791a-109">**sysadmin**</span><span class="sxs-lookup"><span data-stu-id="b791a-109">**sysadmin**</span></span>  
  
-   <span data-ttu-id="b791a-110">**serveradmin**</span><span class="sxs-lookup"><span data-stu-id="b791a-110">**serveradmin**</span></span>  
  
-   <span data-ttu-id="b791a-111">**setupadmin**</span><span class="sxs-lookup"><span data-stu-id="b791a-111">**setupadmin**</span></span>  
  
-   <span data-ttu-id="b791a-112">**securityadmin**</span><span class="sxs-lookup"><span data-stu-id="b791a-112">**securityadmin**</span></span>  
  
-   <span data-ttu-id="b791a-113">**processadmin**</span><span class="sxs-lookup"><span data-stu-id="b791a-113">**processadmin**</span></span>  
  
-   <span data-ttu-id="b791a-114">**dbcreator**</span><span class="sxs-lookup"><span data-stu-id="b791a-114">**dbcreator**</span></span>  
  
-   <span data-ttu-id="b791a-115">**diskadmin**</span><span class="sxs-lookup"><span data-stu-id="b791a-115">**diskadmin**</span></span>  
  
-   <span data-ttu-id="b791a-116">**bulkadmin**</span><span class="sxs-lookup"><span data-stu-id="b791a-116">**bulkadmin**</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="b791a-117">更正動作</span><span class="sxs-lookup"><span data-stu-id="b791a-117">Corrective Action</span></span>  
 <span data-ttu-id="b791a-118">升級之前，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="b791a-118">Before upgrading, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="b791a-119">執行下列陳述式來記錄登入的安全性識別碼 (SID)。</span><span class="sxs-lookup"><span data-stu-id="b791a-119">Record the security identifiers (SIDs) of the logins by executing the following statement.</span></span>  
  
    ```  
    SELECT name, sid   
    FROM master.dbo.syslogins   
    WHERE name IN('sysadmin', 'serveradmin','setupadmin', 'securityadmin','processadmin', 'dbcreator','diskadmin','bulkadmin')  
    ```  
  
2.  <span data-ttu-id="b791a-120">卸除登入。</span><span class="sxs-lookup"><span data-stu-id="b791a-120">Drop the logins.</span></span>  
  
3.  <span data-ttu-id="b791a-121">使用**sp_addlogin**系統程式來建立新的登入。</span><span class="sxs-lookup"><span data-stu-id="b791a-121">Use the **sp_addlogin** system procedure to create new logins.</span></span> <span data-ttu-id="b791a-122">針對每個對應的登入，在\*\* \@ sid\*\*參數中指定步驟1中傳回的 sid。</span><span class="sxs-lookup"><span data-stu-id="b791a-122">Specify the SID returned in step 1 in the **\@sid** parameter for each corresponding login.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b791a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b791a-123">See Also</span></span>  
 <span data-ttu-id="b791a-124">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="b791a-124">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="b791a-125">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="b791a-125">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
