---
title: 擴充預存程式的執行特性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], executing
- executing extended stored procedures [SQL Server]
ms.assetid: 6fe1f7e8-cc02-49df-8a2a-d47a96ec3567
author: rothja
ms.author: jroth
ms.openlocfilehash: edbd73797699d65f694e91bc3035e0dc9366c9d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592025"
---
# <a name="execution-characteristics-of-extended-stored-procedures"></a><span data-ttu-id="a8d21-102">擴充預存程序的執行特性</span><span class="sxs-lookup"><span data-stu-id="a8d21-102">Execution Characteristics of Extended Stored Procedures</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="a8d21-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="a8d21-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="a8d21-104">擴充預存程序的執行具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="a8d21-104">The execution of an extended stored procedure has these characteristics:</span></span>  
  
-   <span data-ttu-id="a8d21-105">擴充預存程式函數會在的安全性內容下執行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a8d21-105">The extended stored procedure function is executed under the security context of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="a8d21-106">擴充預存程序函數會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的處理序空間中執行。</span><span class="sxs-lookup"><span data-stu-id="a8d21-106">The extended stored procedure function runs in the process space of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="a8d21-107">與擴充預存程序執行相關聯的執行緒與用於用戶端連接的執行緒相同。</span><span class="sxs-lookup"><span data-stu-id="a8d21-107">The thread associated with the execution of the extended stored procedure is the same one used for the client connection.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a8d21-108">將擴充預存程序加入伺服器，並將執行權限授與其他使用者之前，系統管理員應徹底檢閱每個擴充預存程序，以確定其中不含任何有害或惡意的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a8d21-108">Before adding extended stored procedures to the server and granting execute permissions to other users, the system administrator should thoroughly review each extended stored procedure to make sure that it does not contain harmful or malicious code.</span></span>  
  
-  
  
 <span data-ttu-id="a8d21-109">載入擴充預存程式 DLL 之後，DLL 會保持載入伺服器的位址空間中，直到停止， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或系統管理員使用 DBCC *DLL_NAME* (FREE) 明確卸載 DLL。</span><span class="sxs-lookup"><span data-stu-id="a8d21-109">After the extended stored procedure DLL is loaded, the DLL remains loaded in the address space of the server until [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is stopped or the administrator explicitly unloads the DLL by using DBCC *DLL_name* (FREE).</span></span>  
  
 <span data-ttu-id="a8d21-110">擴充預存程序可以使用 EXECUTE 陳述式，從 [!INCLUDE[tsql](../../includes/tsql-md.md)] 當做預存程序執行：</span><span class="sxs-lookup"><span data-stu-id="a8d21-110">The extended stored procedure can be executed from [!INCLUDE[tsql](../../includes/tsql-md.md)] as a stored procedure by using the EXECUTE statement:</span></span>  
  
```  
EXECUTE @retval = xp_extendedProcName @param1, @param2 OUTPUT  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8d21-111">參數</span><span class="sxs-lookup"><span data-stu-id="a8d21-111">Parameters</span></span>  
 <span data-ttu-id="a8d21-112">\@ *retval*</span><span class="sxs-lookup"><span data-stu-id="a8d21-112">\@ *retval*</span></span>  
 <span data-ttu-id="a8d21-113">這是傳回值。</span><span class="sxs-lookup"><span data-stu-id="a8d21-113">Is a return value.</span></span>  
  
 <span data-ttu-id="a8d21-114">\@*param1*</span><span class="sxs-lookup"><span data-stu-id="a8d21-114">\@ *param1*</span></span>  
 <span data-ttu-id="a8d21-115">這是輸入參數。</span><span class="sxs-lookup"><span data-stu-id="a8d21-115">Is an input parameter.</span></span>  
  
 <span data-ttu-id="a8d21-116">\@*param2*</span><span class="sxs-lookup"><span data-stu-id="a8d21-116">\@ *param2*</span></span>  
 <span data-ttu-id="a8d21-117">這是輸入/輸出參數。</span><span class="sxs-lookup"><span data-stu-id="a8d21-117">Is an input/output parameter.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="a8d21-118">擴充預存程序會提供效能增強功能並擴充 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="a8d21-118">Extended stored procedures offer performance enhancements and extend [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] functionality.</span></span> <span data-ttu-id="a8d21-119">不過，由於擴充預存程序 DLL 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 共用相同的位址空間，因此問題程序可能會對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 運作造成不利的影響。</span><span class="sxs-lookup"><span data-stu-id="a8d21-119">However, because the extended stored procedure DLL and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] share the same address space, a problem procedure can adversely affect [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] functioning.</span></span> <span data-ttu-id="a8d21-120">雖然擴充預存程序 DLL 擲回的例外會由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理，還是有可能使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料區域受損。</span><span class="sxs-lookup"><span data-stu-id="a8d21-120">Although exceptions thrown by the extended stored procedure DLL are handled by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it is possible to damage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data areas.</span></span> <span data-ttu-id="a8d21-121">基於安全性考量，只有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統管理員可以將擴充預存程序加入到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a8d21-121">As a security precaution, only [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrators can add extended stored procedures to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a8d21-122">這些程序應該經過徹底測試，才能進行安裝。</span><span class="sxs-lookup"><span data-stu-id="a8d21-122">These procedures should be thoroughly tested before they are installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8d21-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8d21-123">See Also</span></span>  
 <span data-ttu-id="a8d21-124">[擴充預存程式程式設計](database-engine-extended-stored-procedures-programming.md) </span><span class="sxs-lookup"><span data-stu-id="a8d21-124">[Programming Extended Stored Procedures](database-engine-extended-stored-procedures-programming.md) </span></span>  
 [<span data-ttu-id="a8d21-125">查詢 SQL Server 中安裝的擴充預存程序</span><span class="sxs-lookup"><span data-stu-id="a8d21-125">Querying Extended Stored Procedures Installed in SQL Server</span></span>](querying-extended-stored-procedures-installed-in-sql-server.md)  
  
  
