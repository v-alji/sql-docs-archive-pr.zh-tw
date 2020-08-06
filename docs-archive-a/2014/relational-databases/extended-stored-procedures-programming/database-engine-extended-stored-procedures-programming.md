---
title: 擴充預存程式程式設計 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- gateway applications [SQL Server]
- extended stored procedures [SQL Server], about extended stored procedures
- Open Data Services [SQL Server]
- ODS [SQL Server]
ms.assetid: 561305cd-c803-48af-9eec-2c19f4d311ce
author: rothja
ms.author: jroth
ms.openlocfilehash: 30792cc2b431e35a8f7df5ff7bbb2c228892d5c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598398"
---
# <a name="programming-extended-stored-procedures"></a><span data-ttu-id="fef31-102">擴充預存程序程式設計</span><span class="sxs-lookup"><span data-stu-id="fef31-102">Programming Extended Stored Procedures</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="fef31-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="fef31-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="fef31-104">過去 Open Data Services 是用來撰寫伺服器應用程式，例如到非 SQL Server 資料庫環境的閘道。</span><span class="sxs-lookup"><span data-stu-id="fef31-104">In the past, Open Data Services was used to write server applications, such as gateways to non-SQL Server database environments.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="fef31-105">不 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援 Open 資料服務 API 的過時部分。</span><span class="sxs-lookup"><span data-stu-id="fef31-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not support the obsolete portions of the Open Data Services API.</span></span> <span data-ttu-id="fef31-106">原始的 Open Data Services API 中唯一仍受 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援的部分是擴充預存程序函數，所以 API 已重新命名為「擴充預存程序 API」。</span><span class="sxs-lookup"><span data-stu-id="fef31-106">The only part of the original Open Data Services API still supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are the extended stored procedure functions, so the API has been renamed to the Extended Stored Procedure API.</span></span>  
  
 <span data-ttu-id="fef31-107">隨著分散式查詢和 CLR 整合之類的更新和更強大技術的出現，擴充預存程序 API 應用程式的需求也大致被取代。</span><span class="sxs-lookup"><span data-stu-id="fef31-107">With the emergence of newer and more powerful technologies, such as distributed queries and CLR Integration, the need for Extended Stored Procedure API applications has largely been replaced.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fef31-108">如果您具備現有的閘道應用程式，就無法使用隨附於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 opends60.dll 來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="fef31-108">If you have existing gateway applications, you cannot use the opends60.dll that ships with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to run the applications.</span></span> <span data-ttu-id="fef31-109">閘道應用程式已不再受到支援。</span><span class="sxs-lookup"><span data-stu-id="fef31-109">Gateway applications are no longer supported.</span></span>  
  
## <a name="extended-stored-procedures-vs-clr-integration"></a><span data-ttu-id="fef31-110">擴充預存程序與 CLR 整合的比較</span><span class="sxs-lookup"><span data-stu-id="fef31-110">Extended Stored Procedures vs. CLR Integration</span></span>  
 <span data-ttu-id="fef31-111">在舊版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，擴充預存程序 (XP) 提供資料庫應用程式開發人員用來撰寫伺服器端邏輯的唯一機制，這些邏輯在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中不是難以表示，就是無法撰寫。</span><span class="sxs-lookup"><span data-stu-id="fef31-111">In earlier releases of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], extended stored procedures (XPs) provided the only mechanism that was available for database application developers to write server-side logic that was either hard to express or impossible to write in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="fef31-112">CLR 整合會提供更健全的替代方法來撰寫此類預存程序。</span><span class="sxs-lookup"><span data-stu-id="fef31-112">CLR Integration provides a more robust alternative to writing such stored procedures.</span></span> <span data-ttu-id="fef31-113">此外，使用 CLR 整合時，過去以預存程序形式所撰寫的邏輯常可更精準地表示為資料表值函式，如此就可以用 SELECT 陳述式 (將其內嵌於 FROM 子句) 來查詢函數建立的結果。</span><span class="sxs-lookup"><span data-stu-id="fef31-113">Furthermore, with CLR Integration, logic that used to be written in the form of stored procedures is often better expressed as table-valued functions, which allow the results constructed by the function to be queried in SELECT statements by embedding them in the FROM clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fef31-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fef31-114">See Also</span></span>  
 <span data-ttu-id="fef31-115">[Common Language Runtime &#40;CLR&#41; 整合總覽](../clr-integration/common-language-runtime-integration-overview.md) </span><span class="sxs-lookup"><span data-stu-id="fef31-115">[Common Language Runtime &#40;CLR&#41; Integration Overview](../clr-integration/common-language-runtime-integration-overview.md) </span></span>  
 [<span data-ttu-id="fef31-116">CLR 資料表值函式</span><span class="sxs-lookup"><span data-stu-id="fef31-116">CLR Table-Valued Functions</span></span>](../clr-integration-database-objects-user-defined-functions/clr-table-valued-functions.md)  
  
  
