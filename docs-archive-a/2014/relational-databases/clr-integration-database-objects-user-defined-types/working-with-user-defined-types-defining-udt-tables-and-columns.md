---
title: 定義 UDT 資料表和資料行 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- user-defined types [CLR integration], columns
- UDTs [CLR integration], columns
- columns [CLR integration]
- user-defined types [CLR integration], tables
- tables [CLR integration]
- UDTs [CLR integration], tables
- UDTs [CLR integration], indexes
- user-defined types [CLR integration], indexes
- indexes [CLR integration]
ms.assetid: aea495f4-ce26-4952-b019-38f012625f3f
author: rothja
ms.author: jroth
ms.openlocfilehash: aa9596629ed8b4877b1793fa0c56956c52989499
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607414"
---
# <a name="defining-udt-tables-and-columns"></a><span data-ttu-id="23dee-102">定義 UDT 資料表及資料行</span><span class="sxs-lookup"><span data-stu-id="23dee-102">Defining UDT Tables and Columns</span></span>
  <span data-ttu-id="23dee-103">一旦包含使用者自訂類型的元件 (UDT) 定義已在資料庫中註冊 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，就可以在資料行定義中使用。</span><span class="sxs-lookup"><span data-stu-id="23dee-103">Once the assembly containing the user-defined type (UDT) definition has been registered in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, it can be used in a column definition.</span></span>  
  
## <a name="creating-tables-with-udts"></a><span data-ttu-id="23dee-104">建立具有 UDT 的資料表</span><span class="sxs-lookup"><span data-stu-id="23dee-104">Creating Tables with UDTs</span></span>  
 <span data-ttu-id="23dee-105">在資料表中建立 UDT 資料行沒有特殊的語法。</span><span class="sxs-lookup"><span data-stu-id="23dee-105">There is no special syntax for creating a UDT column in a table.</span></span> <span data-ttu-id="23dee-106">您可以在資料行定義中使用 UDT 名稱，就像它是其中一個內部 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型一樣。</span><span class="sxs-lookup"><span data-stu-id="23dee-106">You can use the name of the UDT in a column definition as though it were one of the intrinsic [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span> <span data-ttu-id="23dee-107">下列 CREATE TABLE [!INCLUDE[tsql](../../includes/tsql-md.md)] 語句會建立名為**Points**的資料表，其中包含名為**ID**的資料行，該資料行會定義為 `int` 識別欄位，而是資料表的主鍵。</span><span class="sxs-lookup"><span data-stu-id="23dee-107">The following CREATE TABLE [!INCLUDE[tsql](../../includes/tsql-md.md)] statement creates a table named **Points**, with a column named **ID,** which is defined as an `int` identity column and \ the primary key for the table.</span></span> <span data-ttu-id="23dee-108">第二個數據行的名稱為**PointValue**，其資料類型為**Point**。</span><span class="sxs-lookup"><span data-stu-id="23dee-108">The second column is named **PointValue**, with a data type of **Point**.</span></span> <span data-ttu-id="23dee-109">此範例中使用的架構名稱為**dbo**。</span><span class="sxs-lookup"><span data-stu-id="23dee-109">The schema name used in this example is **dbo**.</span></span> <span data-ttu-id="23dee-110">請注意，您必須具有指定結構描述名稱的必要使用權限。</span><span class="sxs-lookup"><span data-stu-id="23dee-110">Note that you must have the necessary permissions to specify a schema name.</span></span> <span data-ttu-id="23dee-111">如果省略了結構描述名稱，則會使用資料庫使用者的預設結構描述。</span><span class="sxs-lookup"><span data-stu-id="23dee-111">If you omit the schema name, the default schema for the database user is used.</span></span>  
  
```  
CREATE TABLE dbo.Points   
(ID int IDENTITY(1,1) PRIMARY KEY, PointValue Point)  
```  
  
## <a name="creating-indexes-on-udt-columns"></a><span data-ttu-id="23dee-112">在 UDT 資料行上建立索引</span><span class="sxs-lookup"><span data-stu-id="23dee-112">Creating Indexes on UDT Columns</span></span>  
 <span data-ttu-id="23dee-113">索引 UDT 資料行有兩個選項：</span><span class="sxs-lookup"><span data-stu-id="23dee-113">There are two options for indexing a UDT column:</span></span>  
  
-   <span data-ttu-id="23dee-114">索引完整值。</span><span class="sxs-lookup"><span data-stu-id="23dee-114">Index the full value.</span></span> <span data-ttu-id="23dee-115">在這種情況下，如果 UDT 按二進位排序，您就可以使用 CREATE INDEX [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，在整個 UDT 資料行上建立索引。</span><span class="sxs-lookup"><span data-stu-id="23dee-115">In this case, if the UDT is binary ordered, you can create an index over the entire UDT column by using the CREATE INDEX [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
-   <span data-ttu-id="23dee-116">索引 UDT 運算式。</span><span class="sxs-lookup"><span data-stu-id="23dee-116">Index UDT expressions.</span></span> <span data-ttu-id="23dee-117">您可透過 UDT 運算式在保存的計算資料行上建立索引。</span><span class="sxs-lookup"><span data-stu-id="23dee-117">You can create indexes on persisted computed columns over UDT expressions.</span></span> <span data-ttu-id="23dee-118">UDT 運算式可以是 UDT 的欄位、方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="23dee-118">The UDT expression can be a field, method, or property of a UDT.</span></span> <span data-ttu-id="23dee-119">該運算式必須具有決定性，且不能執行資料存取。</span><span class="sxs-lookup"><span data-stu-id="23dee-119">The expression must be deterministic and must not perform data access.</span></span>  
  
 <span data-ttu-id="23dee-120">如需詳細資訊，請參閱[CLR 使用者定義類型](clr-user-defined-types.md)和[CREATE INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/create-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="23dee-120">For more information, see [CLR User-Defined Types](clr-user-defined-types.md) and [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23dee-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23dee-121">See Also</span></span>  
 [<span data-ttu-id="23dee-122">在 SQL Server 中使用使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="23dee-122">Working with User-Defined Types in SQL Server</span></span>](working-with-user-defined-types-in-sql-server.md)  
  
  
