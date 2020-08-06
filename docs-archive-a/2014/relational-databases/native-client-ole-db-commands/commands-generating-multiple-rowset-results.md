---
title: 產生多個資料列集結果的命令 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- SQL Server Native Client OLE DB provider, commands
- SQL Server Native Client OLE DB provider, multiple rowsets
- commands [OLE DB]
- multiple-rowset results
ms.assetid: 4567668d-35fd-4162-b61f-f7536862cdcb
author: rothja
ms.author: jroth
ms.openlocfilehash: 8b42a89c0b043e4c72e8b5634cf70e16b435167a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686922"
---
# <a name="commands-generating-multiple-rowset-results"></a><span data-ttu-id="c61fe-102">產生多個資料列集結果的命令</span><span class="sxs-lookup"><span data-stu-id="c61fe-102">Commands Generating Multiple-Rowset Results</span></span>
  <span data-ttu-id="c61fe-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者可以從語句傳回多個資料列集 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c61fe-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider can return multiple rowsets from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] statements.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c61fe-104">陳述式在下列條件下會傳回多個資料列集結果：</span><span class="sxs-lookup"><span data-stu-id="c61fe-104">statements return multiple-rowset results under the following conditions:</span></span>  
  
-   <span data-ttu-id="c61fe-105">批次的 SQL 陳述式以單一命令提交。</span><span class="sxs-lookup"><span data-stu-id="c61fe-105">Batched SQL statements are submitted as a single command.</span></span>  
  
-   <span data-ttu-id="c61fe-106">預存程序實作 SQL 陳述式批次。</span><span class="sxs-lookup"><span data-stu-id="c61fe-106">Stored procedures implement a batch of SQL statements.</span></span>  
  
## <a name="batches"></a><span data-ttu-id="c61fe-107">批次</span><span class="sxs-lookup"><span data-stu-id="c61fe-107">Batches</span></span>  
 <span data-ttu-id="c61fe-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會將分號字元辨識為 SQL 語句的批次分隔符號：</span><span class="sxs-lookup"><span data-stu-id="c61fe-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider recognizes the semicolon character as a batch delimiter for SQL statements:</span></span>  
  
```  
WCHAR*       wSQLString = L"SELECT * FROM Categories; "  
                          L"SELECT * FROM Products";  
```  
  
 <span data-ttu-id="c61fe-109">以一個批次傳送多個 SQL 陳述式，比分開執行每個 SQL 陳述式的效率高。</span><span class="sxs-lookup"><span data-stu-id="c61fe-109">Sending multiple SQL statements in one batch is more efficient than executing each SQL statement separately.</span></span> <span data-ttu-id="c61fe-110">傳送單一批次可以減少從用戶端到伺服器的網路往返數。</span><span class="sxs-lookup"><span data-stu-id="c61fe-110">Sending one batch reduces the network round trips from the client to the server.</span></span>  
  
## <a name="stored-procedures"></a><span data-ttu-id="c61fe-111">預存程序</span><span class="sxs-lookup"><span data-stu-id="c61fe-111">Stored Procedures</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c61fe-112">會針對預存程序中的每個陳述式傳回結果集，所以大部分的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預存程序都會傳回多個結果集。</span><span class="sxs-lookup"><span data-stu-id="c61fe-112">returns a result set for each statement in a stored procedure, so most [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures return multiple result sets.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c61fe-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="c61fe-113">In This Section</span></span>  
  
-   [<span data-ttu-id="c61fe-114">使用 IMultipleResults 來處理多個結果集</span><span class="sxs-lookup"><span data-stu-id="c61fe-114">Using IMultipleResults to Process Multiple Result Sets</span></span>](using-imultipleresults-to-process-multiple-result-sets.md)  
  
## <a name="see-also"></a><span data-ttu-id="c61fe-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c61fe-115">See Also</span></span>  
 [<span data-ttu-id="c61fe-116">命令</span><span class="sxs-lookup"><span data-stu-id="c61fe-116">Commands</span></span>](commands.md)  
  
  
