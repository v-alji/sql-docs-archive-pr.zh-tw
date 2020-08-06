---
title: OLE Automation 結果集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: conceptual
helpviewer_keywords:
- data types [SQL Server], OLE Automation
- two-dimensional arrays
- one-dimensional arrays
- result sets [SQL Server], OLE Automation
- OLE Automation [SQL Server], result sets
- arrays [SQL Server]
ms.assetid: b2f99e33-2303-427c-94b9-9d55f8e2a6ab
author: stevestein
ms.author: sstein
ms.openlocfilehash: f7c9bdc4d51d989db2d4d676b29e0824c0e5b59a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607367"
---
# <a name="ole-automation-result-sets"></a><span data-ttu-id="4bada-102">OLE Automation 結果集</span><span class="sxs-lookup"><span data-stu-id="4bada-102">OLE Automation Result Sets</span></span>
  <span data-ttu-id="4bada-103">如果 OLE Automation 屬性或方法以一維或二維陣列 (One or two Dimension Array) 的形式傳回資料，該陣列將以結果集 (Result Set) 形式傳給用戶端：</span><span class="sxs-lookup"><span data-stu-id="4bada-103">If an OLE Automation property or method returns data in an array with one or two dimensions, the array is returned to the client as a result set:</span></span>  
  
-   <span data-ttu-id="4bada-104">一維陣列會以單一資料列結果集的方式傳回給用戶端，這個資料列中有多個資料行，資料行數目等於陣列的元素數目。</span><span class="sxs-lookup"><span data-stu-id="4bada-104">A one-dimensional array is returned to the client as a single-row result set with as many columns as there are elements in the array.</span></span> <span data-ttu-id="4bada-105">例如，陣列 (10) 將傳回 10 個資料行的單一資料列。</span><span class="sxs-lookup"><span data-stu-id="4bada-105">For example, an array(10) is returned as a single row of 10 columns.</span></span>  
  
-   <span data-ttu-id="4bada-106">二維陣列會以多資料列結果集的方式傳回給用戶端，這個資料列中有多個資料行，資料行數目等於陣列的元素數目。資料行數目等於陣列第一維的元素數目，資料列數目等於陣列第二維的元素數目。</span><span class="sxs-lookup"><span data-stu-id="4bada-106">A two-dimensional array is returned to the client as a result set with as many columns as there are elements in the first dimension of the array and with as many rows as there are elements in the second dimension of the array.</span></span> <span data-ttu-id="4bada-107">例如，陣列 (2,3) 將傳成 2 個資料行的 3 個資料列。</span><span class="sxs-lookup"><span data-stu-id="4bada-107">For example, an array(2,3) is returned as 2 columns in 3 rows.</span></span>  
  
 <span data-ttu-id="4bada-108">當屬性傳回值或方法傳回值為陣列時，sp_OAGetProperty 或 sp_OAMethod 會將結果集傳給用戶端。</span><span class="sxs-lookup"><span data-stu-id="4bada-108">When a property return value or method return value is an array, sp_OAGetProperty or sp_OAMethod returns a result set to the client.</span></span> <span data-ttu-id="4bada-109">(方法輸出參數不能是陣列。)這些程序會掃描陣列中的所有資料值來判斷適當的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型，以及結果集中每個資料行所用的資料長度。</span><span class="sxs-lookup"><span data-stu-id="4bada-109">(Method output parameters cannot be arrays.) These procedures scan all the data values in the array to determine the appropriate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types and data lengths to use for each column in the result set.</span></span> <span data-ttu-id="4bada-110">對於特定資料行，這些程序會利用資料類型和長度來表示這個資料行中的所有資料值。</span><span class="sxs-lookup"><span data-stu-id="4bada-110">For a particular column, these procedures use the data type and length required to represent all data values in that column.</span></span>  
  
 <span data-ttu-id="4bada-111">當資料行中的所有資料值都共用相同的資料類型時，整個資料行都會使用這個資料類型。</span><span class="sxs-lookup"><span data-stu-id="4bada-111">When all data values in a column share the same data type, that data type is used for the whole column.</span></span> <span data-ttu-id="4bada-112">當資料行內的資料值為不同的資料類型時，整個資料行的資料類型將根據下表來做選擇。</span><span class="sxs-lookup"><span data-stu-id="4bada-112">When data values in a column are different data types, the data type of the whole column is chosen based on the following table.</span></span> <span data-ttu-id="4bada-113">若要使用下表，沿著左資料列尋找一個資料類型，並沿著上資料行軸尋找另一個資料類型。</span><span class="sxs-lookup"><span data-stu-id="4bada-113">To use the following table, find one data type along the left row axis and a second data type along the top column axis.</span></span> <span data-ttu-id="4bada-114">資料列和資料行的交集描述結果集資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="4bada-114">The intersection of the row and column describes the data type of the result set column.</span></span>  
  
||||||||  
|-|-|-|-|-|-|-|  
||`int`|`float`|`money`|`datetime`|`varchar`|`nvarchar`|  
|`int`|`int`|`float`|`money`|`varchar`|`varchar`|`nvarchar`|  
|`float`|`float`|`float`|`money`|`varchar`|`varchar`|`nvarchar`|  
|`money`|`money`|`money`|`money`|`varchar`|`varchar`|`nvarchar`|  
|`datetime`|`varchar`|`varchar`|`varchar`|`datetime`|`varchar`|`nvarchar`|  
|`varchar`|`varchar`|`varchar`|`varchar`|`varchar`|`varchar`|`nvarchar`|  
|`nvarchar`|`nvarchar`|`nvarchar`|`nvarchar`|`nvarchar`|`nvarchar`|`nvarchar`|  
  
## <a name="related-content"></a><span data-ttu-id="4bada-115">相關內容</span><span class="sxs-lookup"><span data-stu-id="4bada-115">Related Content</span></span>  
 [<span data-ttu-id="4bada-116">OLE Automation 預存程序 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4bada-116">OLE Automation Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql)  
  
 [<span data-ttu-id="4bada-117">OLE Automation 程序伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="4bada-117">Ole Automation Procedures Server Configuration Option</span></span>](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)  
  
  
