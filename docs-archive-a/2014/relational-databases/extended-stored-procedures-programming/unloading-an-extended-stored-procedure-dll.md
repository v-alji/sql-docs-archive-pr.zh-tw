---
title: 卸載擴充預存程式 DLL |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], unloading
- unloading extended stored procedures
ms.assetid: 4c75ab14-af54-4965-b376-8d75d385c941
author: rothja
ms.author: jroth
ms.openlocfilehash: 7bd4855390e95d949ab769d6567d6f106959dcde
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584512"
---
# <a name="unloading-an-extended-stored-procedure-dll"></a><span data-ttu-id="1bcec-102">卸載擴充預存程序 DLL</span><span class="sxs-lookup"><span data-stu-id="1bcec-102">Unloading an Extended Stored Procedure DLL</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="1bcec-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="1bcec-103">Use CLR Integration instead.</span></span>  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="1bcec-104">一旦 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 呼叫 DLL 的其中一個函數，就會載入擴充預存程式 DLL。</span><span class="sxs-lookup"><span data-stu-id="1bcec-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] loads an extended stored procedure DLL as soon as a call is made to one of the functions of the DLL.</span></span> <span data-ttu-id="1bcec-105">該 DLL 在伺服器關閉或系統管理員使用 DBCC 陳述式來卸載它之前，都會保持載入狀態。</span><span class="sxs-lookup"><span data-stu-id="1bcec-105">The DLL remains loaded until the server is shut down or until the system administrator uses the DBCC statement to unload it.</span></span> <span data-ttu-id="1bcec-106">例如，此命令會卸載**xp_hello.dll**，讓系統管理員可以將此檔案的較新版本複製到目錄，而不需關閉伺服器：</span><span class="sxs-lookup"><span data-stu-id="1bcec-106">For example, this command unloads the **xp_hello.dll**, allowing the system administrator to copy a newer version of this file to the directory without shutting down the server:</span></span>  
  
```  
DBCC xp_hello(FREE)  
```  
  
## <a name="see-also"></a><span data-ttu-id="1bcec-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bcec-107">See Also</span></span>  
 [<span data-ttu-id="1bcec-108">DBCC dllname &#40;FREE&#41; &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="1bcec-108">DBCC dllname &#40;FREE&#41; &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-dllname-free-transact-sql)  
  
  
