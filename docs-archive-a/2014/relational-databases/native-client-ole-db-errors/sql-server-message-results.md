---
title: SQL Server 訊息結果 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
ms.assetid: 6663c6f9-def1-4d9e-845b-2085e5efc401
author: rothja
ms.author: jroth
ms.openlocfilehash: aa63445b81ec89b87523fa29c50817e128d48515
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598839"
---
# <a name="sql-server-message-results"></a><span data-ttu-id="6c584-102">SQL Server 訊息結果</span><span class="sxs-lookup"><span data-stu-id="6c584-102">SQL Server Message Results</span></span>
  <span data-ttu-id="6c584-103">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語句不會 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在執行時產生 Native Client OLE DB 提供者資料列集或受影響的資料列計數：</span><span class="sxs-lookup"><span data-stu-id="6c584-103">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements do not generate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider rowsets or a count of affected rows when executed:</span></span>  
  
-   <span data-ttu-id="6c584-104">PRINT</span><span class="sxs-lookup"><span data-stu-id="6c584-104">PRINT</span></span>  
  
-   <span data-ttu-id="6c584-105">具有 10 或更低嚴重性的 RAISERROR</span><span class="sxs-lookup"><span data-stu-id="6c584-105">RAISERROR with a severity of 10 or lower</span></span>  
  
-   <span data-ttu-id="6c584-106">DBCC</span><span class="sxs-lookup"><span data-stu-id="6c584-106">DBCC</span></span>  
  
-   <span data-ttu-id="6c584-107">SET SHOWPLAN</span><span class="sxs-lookup"><span data-stu-id="6c584-107">SET SHOWPLAN</span></span>  
  
-   <span data-ttu-id="6c584-108">SET STATISTICS</span><span class="sxs-lookup"><span data-stu-id="6c584-108">SET STATISTICS</span></span>  
  
 <span data-ttu-id="6c584-109">這些陳述式會傳回一或多個參考用訊息，或使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回參考用訊息來取代資料列集或計數結果。</span><span class="sxs-lookup"><span data-stu-id="6c584-109">These statements either return one or more informational messages or cause [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to return informational messages in place of rowset or count results.</span></span> <span data-ttu-id="6c584-110">成功執行時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native client OLE DB 提供者會傳回 S_OK，而 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 原生用戶端 OLE DB 提供者取用者可以使用訊息。</span><span class="sxs-lookup"><span data-stu-id="6c584-110">On successful execution, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns S_OK, and the messages are available to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer.</span></span>  
  
 <span data-ttu-id="6c584-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native client OLE DB 提供者會傳回 S_OK，而且在執行許多 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語句或取用者執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者成員函式之後，會有一或多個可用的參考訊息。</span><span class="sxs-lookup"><span data-stu-id="6c584-111">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns S_OK and has one or more informational messages available following the execution of many [!INCLUDE[tsql](../../includes/tsql-md.md)] statements or the consumer execution of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider member function.</span></span>  
  
 <span data-ttu-id="6c584-112">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 每個成員函式執行之後，不論傳回碼的值為何、傳回的**IRowset**或**IMultipleResults**介面參考是否存在，或受影響的資料列計數，原生用戶端 OLE DB 提供者取用者允許動態指定查詢文字，都應該檢查錯誤介面。</span><span class="sxs-lookup"><span data-stu-id="6c584-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer allowing dynamic specification of query text should check error interfaces after every member function execution regardless of the value of the return code, the presence or absence of a returned **IRowset** or **IMultipleResults** interface reference, or a count of affected rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c584-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c584-113">See Also</span></span>  
 [<span data-ttu-id="6c584-114">錯誤</span><span class="sxs-lookup"><span data-stu-id="6c584-114">Errors</span></span>](errors.md)  
  
  
