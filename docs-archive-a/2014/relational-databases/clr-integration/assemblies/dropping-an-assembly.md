---
title: 卸載元件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- removing assemblies
- DROP ASSEMBLY statement
- assemblies [CLR integration], removing
- dropping assemblies
ms.assetid: 03481034-dc91-4488-ab24-ba44243e2690
author: rothja
ms.author: jroth
ms.openlocfilehash: 45d02cbb57459a4c1c11330446021c32dc897353
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704162"
---
# <a name="dropping-an-assembly"></a><span data-ttu-id="afa6d-102">卸除組件</span><span class="sxs-lookup"><span data-stu-id="afa6d-102">Dropping an Assembly</span></span>
  <span data-ttu-id="afa6d-103">如果您不再需要已經使用 CREATE ASSEMBLY 陳述式在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中註冊之組件所提供的功能，就可以刪除或卸除這些組件。</span><span class="sxs-lookup"><span data-stu-id="afa6d-103">Assemblies that have been registered in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] using the CREATE ASSEMBLY statement can be deleted, or dropped, when the functionality they provide is no longer needed.</span></span> <span data-ttu-id="afa6d-104">卸除組件會從資料庫中移除組件及其所有相關聯的檔案 (例如偵錯檔案)。</span><span class="sxs-lookup"><span data-stu-id="afa6d-104">Dropping an assembly removes the assembly and all of its associated files, such as debug files, from the database.</span></span> <span data-ttu-id="afa6d-105">若要卸除組件，請使用 DROP ASSEMBLY 陳述式搭配下列語法：</span><span class="sxs-lookup"><span data-stu-id="afa6d-105">To drop an assembly, use the DROP ASSEMBLY statement with the following syntax:</span></span>  
  
```  
DROP ASSEMBLY MyDotNETAssembly  
```  
  
 <span data-ttu-id="afa6d-106">雖然 DROP ASSEMBLY 不會干擾參考目前執行中組件的任何程式碼，但是在 DROP ASSEMBLY 執行之後，任何嘗試叫用此組件的行為都會失敗。</span><span class="sxs-lookup"><span data-stu-id="afa6d-106">DROP ASSEMBLY does not interfere with any code referencing the assembly that is currently running, but after DROP ASSEMBLY executes, any attempts to invoke the assembly code fail.</span></span>  
  
 <span data-ttu-id="afa6d-107">如果組件是由資料庫中的另一個組件所參考，或者如果它是由目前資料庫中的 Common Language Runtime (CLR) 函數、程序、觸發程序、使用者定義型別 (UDT) 或使用者定義彙總 (UDA) 所使用，DROP ASSEMBLY 就會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="afa6d-107">DROP ASSEMBLY returns an error if the assembly is referenced by another assembly that exists in the database, or if it is used by common language runtime (CLR) functions, procedures, triggers, user-defined types (UDTs), or user-defined aggregates (UDAs) in the current database.</span></span> <span data-ttu-id="afa6d-108">請先使用 DROP AGGREGATE、DROP FUNCTION、DROP PROCEDURE、DROP TRIGGER 和 DROP TYPE 陳述式來刪除此組件所包含的任何 Managed 資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="afa6d-108">First use the DROP AGGREGATE, DROP FUNCTION, DROP PROCEDURE, DROP TRIGGER, and DROP TYPE statements to delete any managed database objects contained in the assembly.</span></span>  
  
## <a name="removing-a-udt-from-the-database"></a><span data-ttu-id="afa6d-109">從資料庫移除 UDT</span><span class="sxs-lookup"><span data-stu-id="afa6d-109">Removing a UDT from the Database</span></span>  
 <span data-ttu-id="afa6d-110">DROP TYPE 陳述式會從目前資料庫移除 UDT。</span><span class="sxs-lookup"><span data-stu-id="afa6d-110">The DROP TYPE statement removes a UDT from the current database.</span></span> <span data-ttu-id="afa6d-111">一旦卸除 UDT 之後，您就可以使用 DROP ASSEMBLY 陳述式，從資料庫中卸除組件。</span><span class="sxs-lookup"><span data-stu-id="afa6d-111">Once a UDT is dropped, you can use the DROP ASSEMBLY statement to drop the assembly from the database.</span></span>  
  
 <span data-ttu-id="afa6d-112">如果物件相依於 UDT，DROP TYPE 陳述式就會失敗，如下列情況所示：</span><span class="sxs-lookup"><span data-stu-id="afa6d-112">The DROP TYPE statement fails if objects depend on the UDT, as in the following situations:</span></span>  
  
-   <span data-ttu-id="afa6d-113">資料庫中包含使用 UDT 定義之資料行的資料表。</span><span class="sxs-lookup"><span data-stu-id="afa6d-113">Tables in the database that contain columns defined using the UDT.</span></span>  
  
-   <span data-ttu-id="afa6d-114">使用 WITH SCHEMABINDING 子句在資料庫中建立的函數、預存程序或觸發程序 (這些項目會使用 UDT 變數或參數)。</span><span class="sxs-lookup"><span data-stu-id="afa6d-114">Functions, stored procedures, or triggers that use variables or parameters of the UDT, created in the database with the WITH SCHEMABINDING clause.</span></span>  
  
### <a name="finding-udt-dependencies"></a><span data-ttu-id="afa6d-115">尋找 UDT 相依性</span><span class="sxs-lookup"><span data-stu-id="afa6d-115">Finding UDT Dependencies</span></span>  
 <span data-ttu-id="afa6d-116">您必須先卸除所有相依物件，然後再執行 DROP TYPE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="afa6d-116">You must first drop all dependent objects, and then execute the DROP TYPE statement.</span></span> <span data-ttu-id="afa6d-117">下列 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 查詢會尋找在**AdventureWorks**資料庫中使用 UDT 的所有資料行和參數。</span><span class="sxs-lookup"><span data-stu-id="afa6d-117">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] query locates all of the columns and parameters that use a UDT in the **AdventureWorks** database.</span></span>  
  
```  
USE Adventureworks;  
SELECT o.name AS major_name, o.type_desc AS major_type_desc  
     , c.name AS minor_name, c.type_desc AS minor_type_desc  
     , at.assembly_class  
  FROM (  
        SELECT object_id, name, user_type_id, 'SQL_COLUMN' AS type_desc  
          FROM sys.columns  
     UNION ALL  
        SELECT object_id, name, user_type_id, 'SQL_PROCEDURE_PARAMETER'  
          FROM sys.parameters  
     ) AS c  
  JOIN sys.objects AS o  
    ON o.object_id = c.object_id  
  JOIN sys.assembly_types AS at  
    ON at.user_type_id = c.user_type_id;   
```  
  
## <a name="see-also"></a><span data-ttu-id="afa6d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="afa6d-118">See Also</span></span>  
 <span data-ttu-id="afa6d-119">[管理 CLR 整合元件](managing-clr-integration-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="afa6d-119">[Managing CLR Integration Assemblies](managing-clr-integration-assemblies.md) </span></span>  
 <span data-ttu-id="afa6d-120">[改變元件](altering-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="afa6d-120">[Altering an Assembly](altering-an-assembly.md) </span></span>  
 <span data-ttu-id="afa6d-121">[建立元件](creating-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="afa6d-121">[Creating an Assembly](creating-an-assembly.md) </span></span>  
 <span data-ttu-id="afa6d-122">[DROP AGGREGATE &#40;Transact-sql&#41;](/sql/t-sql/statements/drop-aggregate-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="afa6d-122">[DROP AGGREGATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-aggregate-transact-sql) </span></span>  
 <span data-ttu-id="afa6d-123">[DROP FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="afa6d-123">[DROP FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql) </span></span>  
 <span data-ttu-id="afa6d-124">[DROP PROCEDURE &#40;Transact-sql&#41;](/sql/t-sql/statements/drop-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="afa6d-124">[DROP PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-procedure-transact-sql) </span></span>  
 <span data-ttu-id="afa6d-125">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="afa6d-125">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span></span>  
 [<span data-ttu-id="afa6d-126">DROP TYPE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="afa6d-126">DROP TYPE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-type-transact-sql)  
  
  
