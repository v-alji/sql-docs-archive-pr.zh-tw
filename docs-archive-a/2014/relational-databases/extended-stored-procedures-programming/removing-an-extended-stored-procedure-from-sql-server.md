---
title: 從 SQL Server 中移除擴充預存程式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- deleting extended stored procedures
- removing extended stored procedures
- extended stored procedures [SQL Server], removing
- dropping extended stored procedures
ms.assetid: 7827e574-3f59-4279-9a9b-532582e041cb
author: rothja
ms.author: jroth
ms.openlocfilehash: 284da815de073248669da032c06ddeeb68c697a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710617"
---
# <a name="removing-an-extended-stored-procedure-from-sql-server"></a><span data-ttu-id="13276-102">從 SQL Server 中移除擴充預存程序</span><span class="sxs-lookup"><span data-stu-id="13276-102">Removing an Extended Stored Procedure from SQL Server</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="13276-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="13276-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="13276-104">若要將每個擴充預存程式函數放在使用者定義的擴充預存程式 DLL 中， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統管理員必須執行**sp_dropextendedproc**系統預存程式，並指定函式的名稱以及該函式所在的 DLL 名稱。</span><span class="sxs-lookup"><span data-stu-id="13276-104">To drop each extended stored procedure function in a user-defined extended stored procedure DLL, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator must run the **sp_dropextendedproc** system stored procedure, specifying the name of the function and the name of the DLL in which that function resides.</span></span> <span data-ttu-id="13276-105">例如，此命令會從下列位置移除名為 xp_hello.dll 的 DLL 中的函式**xp_hello** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="13276-105">For example, this command removes the function **xp_hello**, located in a DLL named xp_hello.dll, from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
```  
sp_dropextendedproc 'xp_hello'  
```  
  
 <span data-ttu-id="13276-106">從開始 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ， **sp_dropextendedproc**不會卸載系統擴充預存程式。</span><span class="sxs-lookup"><span data-stu-id="13276-106">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], **sp_dropextendedproc** does not drop system extended stored procedures.</span></span> <span data-ttu-id="13276-107">相反地，系統管理員應該拒絕將擴充預存程式的 EXECUTE 許可權授與**public**角色。</span><span class="sxs-lookup"><span data-stu-id="13276-107">Instead, the system administrator should deny EXECUTE permission on the extended stored procedure to the **public** role.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13276-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13276-108">See Also</span></span>  
 [<span data-ttu-id="13276-109">sp_dropextendedproc &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="13276-109">sp_dropextendedproc &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
