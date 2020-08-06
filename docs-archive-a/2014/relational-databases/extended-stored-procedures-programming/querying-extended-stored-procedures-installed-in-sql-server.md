---
title: 查詢安裝在 SQL Server 中的擴充預存程式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], querying
ms.assetid: e02348e6-dba6-438a-98b6-684244bb034d
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f44db9053ad18c3a6902a30aaab4f81610c5a8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593399"
---
# <a name="querying-extended-stored-procedures-installed-in-sql-server"></a><span data-ttu-id="ac9f4-102">查詢 SQL Server 中安裝的擴充預存程序</span><span class="sxs-lookup"><span data-stu-id="ac9f4-102">Querying Extended Stored Procedures Installed in SQL Server</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="ac9f4-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="ac9f4-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="ac9f4-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已驗證的使用者可以藉由執行**sp_helpextendedproc**系統程式，顯示目前定義的擴充預存程式，以及每個所屬的 DLL 名稱。</span><span class="sxs-lookup"><span data-stu-id="ac9f4-104">A [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authenticated user can display the currently defined extended stored procedures and the name of the DLL to which each belongs by running the **sp_helpextendedproc** system procedure.</span></span> <span data-ttu-id="ac9f4-105">例如，下列範例會傳回**xp_hello**所屬的 DLL：</span><span class="sxs-lookup"><span data-stu-id="ac9f4-105">For example, the following example returns the DLL to which **xp_hello** belongs:</span></span>  
  
```  
sp_helpextendedproc 'xp_hello'  
```  
  
 <span data-ttu-id="ac9f4-106">如果在未指定擴充預存程式的情況下執行**sp_helpextendedproc** ，則會顯示所有擴充預存程式及其 dll。</span><span class="sxs-lookup"><span data-stu-id="ac9f4-106">If **sp_helpextendedproc** is executed without specifying an extended stored procedure, all the extended stored procedures and their DLLs are displayed.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ac9f4-107">只會針對已登入之使用者所擁有或擁有權限的那些擴充預存程序傳回資訊。</span><span class="sxs-lookup"><span data-stu-id="ac9f4-107">Information will be returned for only those extended stored procedures that the logged in user owns or has permissions to.</span></span> <span data-ttu-id="ac9f4-108">只有**系統管理員（sysadmin** ）固定伺服器角色和**db_owner**、 **db_securityadmin**和**db_ddladmin**固定資料庫角色的成員，才能夠查看所有擴充預存程式的資訊。</span><span class="sxs-lookup"><span data-stu-id="ac9f4-108">Only members of the **sysadmin** fixed server role and the **db_owner**, **db_securityadmin**, and the **db_ddladmin** fixed database roles can view information for all extended stored procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac9f4-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac9f4-109">See Also</span></span>  
 <span data-ttu-id="ac9f4-110">[sp_helpextendedproc &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ac9f4-110">[sp_helpextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql) </span></span>  
 <span data-ttu-id="ac9f4-111">[sp_addextendedproc &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ac9f4-111">[sp_addextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql) </span></span>  
 [<span data-ttu-id="ac9f4-112">sp_dropextendedproc &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ac9f4-112">sp_dropextendedproc &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
