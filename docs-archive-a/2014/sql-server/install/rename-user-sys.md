---
title: 重新命名使用者 sys |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sys user names [SQL Server]
ms.assetid: d622d646-83e4-4b6f-9a21-77b301af04b5
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3af9d31a54adc5645cab6fcc7104ae7ff27a61b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584985"
---
# <a name="rename-user-sys"></a><span data-ttu-id="c09d7-102">重新命名使用者 sys</span><span class="sxs-lookup"><span data-stu-id="c09d7-102">Rename user sys</span></span>
  <span data-ttu-id="c09d7-103">Upgrade Advisor 偵測到資料庫中有使用者名稱**sys** 。</span><span class="sxs-lookup"><span data-stu-id="c09d7-103">Upgrade Advisor detected the user name **sys** in a database.</span></span> <span data-ttu-id="c09d7-104">這個名稱是保留的。</span><span class="sxs-lookup"><span data-stu-id="c09d7-104">This name is reserved.</span></span> <span data-ttu-id="c09d7-105">請在升級之前重新命名使用者。</span><span class="sxs-lookup"><span data-stu-id="c09d7-105">Rename the user before you upgrade.</span></span> <span data-ttu-id="c09d7-106">如果使用者未重新命名，在升級程序之後，資料庫將處於可疑狀態，要等到資料庫連線後才可供使用。</span><span class="sxs-lookup"><span data-stu-id="c09d7-106">If the user is not renamed, the database will be in a suspect state after the upgrade process and will be unavailable until the database is brought online.</span></span>  
  
## <a name="component"></a><span data-ttu-id="c09d7-107">元件</span><span class="sxs-lookup"><span data-stu-id="c09d7-107">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="c09d7-108">描述</span><span class="sxs-lookup"><span data-stu-id="c09d7-108">Description</span></span>  
 <span data-ttu-id="c09d7-109">使用者**sys**已保留。</span><span class="sxs-lookup"><span data-stu-id="c09d7-109">User **sys** is reserved.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="c09d7-110">更正動作</span><span class="sxs-lookup"><span data-stu-id="c09d7-110">Corrective Action</span></span>  
  
### <a name="before-upgrade-procedure"></a><span data-ttu-id="c09d7-111">升級前程序</span><span class="sxs-lookup"><span data-stu-id="c09d7-111">Before Upgrade Procedure</span></span>  
 <span data-ttu-id="c09d7-112">在升級之前，請在包含使用者**sys**的每個資料庫中執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c09d7-112">Before you upgrade, in each database that contains user **sys**, do the following:</span></span>  
  
1.  <span data-ttu-id="c09d7-113">建立新的使用者。</span><span class="sxs-lookup"><span data-stu-id="c09d7-113">Create a new user.</span></span>  
  
2.  <span data-ttu-id="c09d7-114">使用下列語句來顯示由使用者**sys**授與並授與使用者**sys**的擁有權限。</span><span class="sxs-lookup"><span data-stu-id="c09d7-114">Use the following statements to display all permissions that are granted by user **sys** and granted to user **sys**.</span></span>  
  
    ```  
    -- Return permissions granted by user sys.  
    SELECT * FROM sysprotects WHERE grantor = USER_ID('sys')  
    -- Return permissions granted to user sys.  
    SELECT * FROM sysprotects WHERE uid = USER_ID('sys')  
    ```  
  
3.  <span data-ttu-id="c09d7-115">若要將**sys**所擁有之所有物件的擁有權轉移給新的使用者，請使用**sp_changeobjectowner**。</span><span class="sxs-lookup"><span data-stu-id="c09d7-115">To transfer ownership of all objects owned by **sys** to the new user, use **sp_changeobjectowner**.</span></span>  
  
4.  <span data-ttu-id="c09d7-116">卸載使用者**sys**。</span><span class="sxs-lookup"><span data-stu-id="c09d7-116">Drop user **sys**.</span></span>  
  
5.  <span data-ttu-id="c09d7-117">若要還原在步驟2中所捕獲的原始許可權，請使用 GRANT 語句的 AS *new_user*子句。</span><span class="sxs-lookup"><span data-stu-id="c09d7-117">To restore the original permissions captured in step 2, use the AS *new_user* clause of the GRANT statement.</span></span>  
  
6.  <span data-ttu-id="c09d7-118">修改指令碼以參考新使用者。</span><span class="sxs-lookup"><span data-stu-id="c09d7-118">Modify scripts to reference the new user.</span></span> <span data-ttu-id="c09d7-119">例如，包含 `SELECT * FROM sys.my`_`table` 等陳述式的指令碼必須變更為 `SELECT * FROM new_user.my_table`。</span><span class="sxs-lookup"><span data-stu-id="c09d7-119">For example, scripts that contain statements such as `SELECT * FROM sys.my`_`table` must be changed to `SELECT * FROM new_user.my_table`.</span></span>  
  
### <a name="after-upgrade-procedure"></a><span data-ttu-id="c09d7-120">升級後程序</span><span class="sxs-lookup"><span data-stu-id="c09d7-120">After Upgrade Procedure</span></span>  
 <span data-ttu-id="c09d7-121">如果在升級之前未重新命名使用者**sys** ，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c09d7-121">If the user **sys** was not renamed prior to upgrading, do the following:</span></span>  
  
1.  <span data-ttu-id="c09d7-122">執行陳述式 `ALTER DATABASE db_name SET ONLINE`。</span><span class="sxs-lookup"><span data-stu-id="c09d7-122">Execute the statement `ALTER DATABASE db_name SET ONLINE`.</span></span> <span data-ttu-id="c09d7-123">資料庫將處於 SINGLE_USER 模式中。</span><span class="sxs-lookup"><span data-stu-id="c09d7-123">The database will be in SINGLE_USER mode.</span></span>  
  
2.  <span data-ttu-id="c09d7-124">遵循「升級前程序」一節中的所有步驟。</span><span class="sxs-lookup"><span data-stu-id="c09d7-124">Follow all steps in the Before Upgrade Procedure section.</span></span>  
  
3.  <span data-ttu-id="c09d7-125">執行陳述式 `ALTER DATABASE db_name SET MULTI_USER`。</span><span class="sxs-lookup"><span data-stu-id="c09d7-125">Execute the statement `ALTER DATABASE db_name SET MULTI_USER`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c09d7-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c09d7-126">See Also</span></span>  
 <span data-ttu-id="c09d7-127">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="c09d7-127">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="c09d7-128">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="c09d7-128">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
