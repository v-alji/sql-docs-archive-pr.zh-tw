---
title: Using 語句參數 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- ODBC, parameters
- statements [ODBC], parameters
- parameter markers [ODBC]
- SQL Server Native Client ODBC driver, statements
- ODBC applications, statements
ms.assetid: 2427d886-ec6c-49d7-b0b6-0d998b64cdb9
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b7e207416e60af94efd59555980a0edff68a38b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585343"
---
# <a name="using-statement-parameters"></a><span data-ttu-id="7feac-102">使用陳述式參數</span><span class="sxs-lookup"><span data-stu-id="7feac-102">Using Statement Parameters</span></span>
  <span data-ttu-id="7feac-103">參數是 SQL 陳述式內的變數，可讓 ODBC 應用程式進行以下作業：</span><span class="sxs-lookup"><span data-stu-id="7feac-103">A parameter is a variable in an SQL statement that can enable an ODBC application to:</span></span>  
  
-   <span data-ttu-id="7feac-104">有效率地針對資料表中的資料行提供值。</span><span class="sxs-lookup"><span data-stu-id="7feac-104">Efficiently provide values for columns in a table.</span></span>  
  
-   <span data-ttu-id="7feac-105">增強建構查詢準則時的使用者互動。</span><span class="sxs-lookup"><span data-stu-id="7feac-105">Enhance user interaction in constructing query criteria.</span></span>  
  
-   <span data-ttu-id="7feac-106">管理**text**、 **Ntext**和**image**資料，以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 特定的 C 資料類型。</span><span class="sxs-lookup"><span data-stu-id="7feac-106">Manage **text**, **ntext**, and **image** data and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific C data types.</span></span>  
  
 <span data-ttu-id="7feac-107">例如， **part**資料表具有名為**PartID**、 **Description**和**Price**的資料行。</span><span class="sxs-lookup"><span data-stu-id="7feac-107">For example, a **Parts** table has columns named **PartID**, **Description**, and **Price**.</span></span> <span data-ttu-id="7feac-108">加入某個部分而不含參數時，需要建構如下的 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="7feac-108">To add a part without parameters requires constructing an SQL statement such as:</span></span>  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (2100, 'Drive shaft', 50.00)  
```  
  
 <span data-ttu-id="7feac-109">雖然可接受這個陳述式插入具有一組已知值的一個資料列，但是當應用程式需要插入幾個資料列時，還是有點不便。</span><span class="sxs-lookup"><span data-stu-id="7feac-109">Although this statement is acceptable for inserting one row with a known set of values, it is awkward when an application is required to insert several rows.</span></span> <span data-ttu-id="7feac-110">ODBC 為了應付這個狀況，所以讓應用程式可使用參數標記取代 SQL 陳述式中的任何資料值。</span><span class="sxs-lookup"><span data-stu-id="7feac-110">ODBC addresses this by letting an application to replace any data value in an SQL statement by a parameter maker.</span></span> <span data-ttu-id="7feac-111">這是由問號 (?) 表示。</span><span class="sxs-lookup"><span data-stu-id="7feac-111">This is denoted by a question mark (?).</span></span> <span data-ttu-id="7feac-112">在下列範例中，會以參數標記來取代三個資料值：</span><span class="sxs-lookup"><span data-stu-id="7feac-112">In the following example, three data values are replaced with parameter markers:</span></span>  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 <span data-ttu-id="7feac-113">然後會將參數標記繫結到應用程式變數。</span><span class="sxs-lookup"><span data-stu-id="7feac-113">The parameter markers are then bound to application variables.</span></span> <span data-ttu-id="7feac-114">若要插入新的資料列，應用程式只需要設定變數的值，然後再執行此陳述式。</span><span class="sxs-lookup"><span data-stu-id="7feac-114">To insert a new row, the application has only to set the values of the variables and execute the statement.</span></span> <span data-ttu-id="7feac-115">然後驅動程式會擷取目前的變數值，再將其傳送給資料來源。</span><span class="sxs-lookup"><span data-stu-id="7feac-115">The driver then retrieves the current values of the variables and sends them to the data source.</span></span> <span data-ttu-id="7feac-116">如果此陳述式執行多次，應用程式可以預備此陳述式來讓處理程序更有效率。</span><span class="sxs-lookup"><span data-stu-id="7feac-116">If the statement is executed multiple times, the application can make the process even more efficient by preparing the statement.</span></span>  
  
 <span data-ttu-id="7feac-117">每一個參數標記都是根據從左到右指派給參數的序數來參考。</span><span class="sxs-lookup"><span data-stu-id="7feac-117">Each parameter marker is referenced by its ordinal number assigned to the parameters from left to right.</span></span> <span data-ttu-id="7feac-118">SQL 陳述式中最左邊參數標記的序數值為 1，下一個標記的序數值為 2，依此類推。</span><span class="sxs-lookup"><span data-stu-id="7feac-118">The leftmost parameter marker in an SQL statement has an ordinal value of 1; the next one is ordinal 2, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7feac-119">本節內容</span><span class="sxs-lookup"><span data-stu-id="7feac-119">In This Section</span></span>  
  
-   [<span data-ttu-id="7feac-120">繫結參數</span><span class="sxs-lookup"><span data-stu-id="7feac-120">Binding Parameters</span></span>](using-statement-parameters-binding-parameters.md)  
  
## <a name="see-also"></a><span data-ttu-id="7feac-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7feac-121">See Also</span></span>  
 [<span data-ttu-id="7feac-122">&#40;ODBC&#41;執行查詢</span><span class="sxs-lookup"><span data-stu-id="7feac-122">Executing Queries &#40;ODBC&#41;</span></span>](executing-queries-odbc.md)  
  
  
