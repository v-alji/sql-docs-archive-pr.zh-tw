---
title: 授與資料庫物件的存取權 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- granting access to database objects
ms.assetid: a44d9bbf-f58e-4734-b7f4-eb3b492b777b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 22bd0bb1f01e59ec30f7cf1bbf128c890d3d5d64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605974"
---
# <a name="granting-access-to-a-database-object"></a><span data-ttu-id="589ac-102">授與資料庫物件的存取權</span><span class="sxs-lookup"><span data-stu-id="589ac-102">Granting Access to a Database Object</span></span>
  <span data-ttu-id="589ac-103"> 作為管理員，您可以從 **Products** 資料表和 **vw_Names** 檢視中執行 SELECT，也可以執行 **pr_Names** 預存程序；但 Mary 則無權這麼做。</span><span class="sxs-lookup"><span data-stu-id="589ac-103">As an administrator, you can execute the SELECT from the **Products** table and the **vw_Names** view, and execute the **pr_Names** procedure; however, Mary cannot.</span></span> <span data-ttu-id="589ac-104">若要授與 Mary 必要的權限，請使用 GRANT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="589ac-104">To grant Mary the necessary permissions, use the GRANT statement.</span></span>  
  
### <a name="procedure-title"></a><span data-ttu-id="589ac-105">程序標題</span><span class="sxs-lookup"><span data-stu-id="589ac-105">Procedure Title</span></span>  
  
1.  <span data-ttu-id="589ac-106">執行下列陳述式，讓 `Mary` 具有 `EXECUTE` 預存程序的 `pr_Names` 權限。</span><span class="sxs-lookup"><span data-stu-id="589ac-106">Execute the following statement to give `Mary` the `EXECUTE` permission for the `pr_Names` stored procedure.</span></span>  
  
    ```  
    GRANT EXECUTE ON pr_Names TO Mary;  
    GO  
    ```  
  
 <span data-ttu-id="589ac-107">在這個狀況中，Mary 只能使用預存程序來存取 **Products** 資料表。</span><span class="sxs-lookup"><span data-stu-id="589ac-107">In this scenario, Mary can only access the **Products** table by using the stored procedure.</span></span> <span data-ttu-id="589ac-108">如果您希望 Mary 能夠在檢視中執行 SELECT 陳述式，則必須也要執行 `GRANT SELECT ON vw_Names TO Mary`。</span><span class="sxs-lookup"><span data-stu-id="589ac-108">If you want Mary to be able to execute a SELECT statement against the view, then you must also execute `GRANT SELECT ON vw_Names TO Mary`.</span></span> <span data-ttu-id="589ac-109">若要移除資料庫物件的存取權，請使用 REVOKE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="589ac-109">To remove access to database objects, use the REVOKE statement.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="589ac-110">如果資料表、檢視和預存程序並不是由相同的結構描述所擁有，則授與權限的過程將會更加複雜。</span><span class="sxs-lookup"><span data-stu-id="589ac-110">If the table, the view, and the stored procedure are not owned by the same schema, granting permissions becomes more complex.</span></span>  
  
## <a name="about-grant"></a><span data-ttu-id="589ac-111">關於 GRANT</span><span class="sxs-lookup"><span data-stu-id="589ac-111">About GRANT</span></span>  
 <span data-ttu-id="589ac-112">您必須具有 EXECUTE 權限，才能執行預存程序。</span><span class="sxs-lookup"><span data-stu-id="589ac-112">You must have EXECUTE permission to execute a stored procedure.</span></span> <span data-ttu-id="589ac-113">若要存取和變更資料，則必須具有 SELECT、INSERT、UPDATE 和 DELETE 權限。</span><span class="sxs-lookup"><span data-stu-id="589ac-113">You must have SELECT, INSERT, UPDATE, and DELETE permissions to access and change data.</span></span> <span data-ttu-id="589ac-114">GRANT 陳述式也可以用來授與其他權限，例如建立資料表的權限。</span><span class="sxs-lookup"><span data-stu-id="589ac-114">The GRANT statement is also used for other permissions, such as permission to create tables.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="589ac-115">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="589ac-115">Next Task in Lesson</span></span>  
 [<span data-ttu-id="589ac-116">摘要：設定資料庫物件的權限</span><span class="sxs-lookup"><span data-stu-id="589ac-116">Summary: Configuring Permissions on Database Objects</span></span>](lesson-2-5-summary-configuring-permissions-on-database-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="589ac-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="589ac-117">See Also</span></span>  
 <span data-ttu-id="589ac-118">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="589ac-118">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span></span>  
 [<span data-ttu-id="589ac-119">REVOKE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="589ac-119">REVOKE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/revoke-transact-sql)  
  
  
