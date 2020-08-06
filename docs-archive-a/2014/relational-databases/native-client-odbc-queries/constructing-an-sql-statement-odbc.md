---
title: " (ODBC) 來建立 SQL 語句 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC], constructing
- ODBC applications, statements
ms.assetid: 0acc71e2-8004-4dd8-8592-05c022bdd692
author: rothja
ms.author: jroth
ms.openlocfilehash: 1c454f936c49335555ca09b190e4d604c9fbad64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585364"
---
# <a name="constructing-an-sql-statement-odbc"></a><span data-ttu-id="7b862-102">建構 SQL 陳述式 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="7b862-102">Constructing an SQL Statement (ODBC)</span></span>
  <span data-ttu-id="7b862-103">ODBC 應用程式會透過執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，執行幾乎所有資料庫存取作業。</span><span class="sxs-lookup"><span data-stu-id="7b862-103">ODBC applications perform almost all of their database access by executing [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="7b862-104">這些陳述式的形式完全取決於應用程式的需求。</span><span class="sxs-lookup"><span data-stu-id="7b862-104">The form of these statements depends on the application requirements.</span></span> <span data-ttu-id="7b862-105">您可以利用下列方式來建構 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="7b862-105">SQL statements can be constructed in the following ways:</span></span>  
  
-   <span data-ttu-id="7b862-106">寫入程式碼</span><span class="sxs-lookup"><span data-stu-id="7b862-106">Hard-coded</span></span>  
  
     <span data-ttu-id="7b862-107">應用程式當做固定工作執行的靜態陳述式。</span><span class="sxs-lookup"><span data-stu-id="7b862-107">Static statements performed by an application as a fixed task.</span></span>  
  
-   <span data-ttu-id="7b862-108">在執行階段建構</span><span class="sxs-lookup"><span data-stu-id="7b862-108">Constructed at run time</span></span>  
  
     <span data-ttu-id="7b862-109">在執行階段建構的 SQL 陳述式，可讓使用者使用 SELECT、WHERE 和 ORDER BY 等一般子句來調整陳述式。</span><span class="sxs-lookup"><span data-stu-id="7b862-109">SQL statements constructed at run time that enable the user to tailor the statement by using common clauses, such as SELECT, WHERE, and ORDER BY.</span></span> <span data-ttu-id="7b862-110">這包括使用者輸入的隨選查詢。</span><span class="sxs-lookup"><span data-stu-id="7b862-110">This includes ad hoc queries entered by users.</span></span>  
  
 <span data-ttu-id="7b862-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]用戶端 ODBC 驅動程式只會針對不直接支援的 ODBC 和 ISO 語法，剖析 SQL 語句 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ，驅動程式會將它轉換成 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7b862-111">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client ODBC driver parses SQL statements only for ODBC and ISO syntax not directly supported by the [!INCLUDE[ssDE](../../includes/ssde-md.md)], which the driver transforms into [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="7b862-112">所有其他 SQL 語法會原封不動地傳遞至 [!INCLUDE[ssDE](../../includes/ssde-md.md)]，而 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將判斷它是否為有效的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7b862-112">All other SQL syntax is passed to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] unchanged, where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will determine if it is valid [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7b862-113">這個方法會產生兩個優點：</span><span class="sxs-lookup"><span data-stu-id="7b862-113">This approach yields two benefits:</span></span>  
  
-   <span data-ttu-id="7b862-114">減少負擔</span><span class="sxs-lookup"><span data-stu-id="7b862-114">Reduced overhead</span></span>  
  
     <span data-ttu-id="7b862-115">驅動程式的處理負擔會降到最低，因為它只需要掃描少數 ODBC 和 ISO 子句。</span><span class="sxs-lookup"><span data-stu-id="7b862-115">Processing overhead for the driver is minimized because it only has to scan for a small set of ODBC and ISO clauses.</span></span>  
  
-   <span data-ttu-id="7b862-116">彈性</span><span class="sxs-lookup"><span data-stu-id="7b862-116">Flexibility</span></span>  
  
     <span data-ttu-id="7b862-117">程式設計人員可以調整其應用程式的可攜性。</span><span class="sxs-lookup"><span data-stu-id="7b862-117">Programmers can tailor the portability of their applications.</span></span> <span data-ttu-id="7b862-118">若要針對多個資料庫強化可攜性，請主要使用 ODBC 和 ISO 語法。</span><span class="sxs-lookup"><span data-stu-id="7b862-118">To enhance portability against multiple databases, use primarily ODBC and ISO syntax.</span></span> <span data-ttu-id="7b862-119">若要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 特有的增強功能，請使用適當的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語法。</span><span class="sxs-lookup"><span data-stu-id="7b862-119">To use enhancements specific to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], use the appropriate [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax.</span></span> <span data-ttu-id="7b862-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式支援完整的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語法，因此，以 ODBC 為基礎的應用程式可以利用中的所有功能 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7b862-120">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports the complete [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax so ODBC-based applications can take advantage of all the features in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="7b862-121">SELECT 陳述式中的資料行清單應該僅包含執行目前工作所需的資料行。</span><span class="sxs-lookup"><span data-stu-id="7b862-121">The column list in a SELECT statement should contain only the columns required to perform the current task.</span></span> <span data-ttu-id="7b862-122">這樣做不僅可減少透過網路傳送的資料量，還能減少資料庫變更對應用程式造成的影響。</span><span class="sxs-lookup"><span data-stu-id="7b862-122">Not only does this reduce the amount of data sent across the network, but also it reduces the effect of database changes on the application.</span></span> <span data-ttu-id="7b862-123">如果某個應用程式沒有參考資料表中的資料行，此應用程式就不會受到對該資料行所做之任何變更的影響。</span><span class="sxs-lookup"><span data-stu-id="7b862-123">If an application does not reference a column from a table, then the application is not affected by any changes made to that column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b862-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b862-124">See Also</span></span>  
 [<span data-ttu-id="7b862-125">&#40;ODBC&#41;執行查詢</span><span class="sxs-lookup"><span data-stu-id="7b862-125">Executing Queries &#40;ODBC&#41;</span></span>](executing-queries-odbc.md)  
  
  
