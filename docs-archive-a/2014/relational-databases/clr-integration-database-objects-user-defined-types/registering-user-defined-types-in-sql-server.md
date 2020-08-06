---
title: 在 SQL Server 中註冊使用者自訂類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- UDTs [CLR integration], maintaining
- user-defined types [CLR integration], maintaining
- dependencies [CLR integration]
- deploying user-defined types [CLR integration]
- CurrencyConversion function
- user-defined types [CLR integration], deploying
- Transact-SQL deploying UDTs
- assemblies [CLR integration], user-defined types
- cross-database UDT support
- CREATE ASSEMBLY statement
- DROP TYPE statement
- Currency UDT
- CREATE TYPE statement
- registering user-defined types
- UDTs [CLR integration], deploying
- removing user-defined types
- user-defined types [CLR integration], registering
- ALTER ASSEMBLY statement
- UDTs [CLR integration], registering
- ADD FILE clause
ms.assetid: f7da3e92-e407-4f0b-b3a3-f214e442b37d
author: rothja
ms.author: jroth
ms.openlocfilehash: 7d24f7948e093335eff708f3c4a8a7361cfc156f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592714"
---
# <a name="registering-user-defined-types-in-sql-server"></a><span data-ttu-id="74ff7-102">在 SQL Server 中註冊使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="74ff7-102">Registering User-Defined Types in SQL Server</span></span>
  <span data-ttu-id="74ff7-103">若要使用使用者定義型別 (中的 UDT) [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，您必須註冊它。</span><span class="sxs-lookup"><span data-stu-id="74ff7-103">In order to use a user-defined type (UDT) in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must register it.</span></span> <span data-ttu-id="74ff7-104">註冊 UDT 包括註冊組件，以及在要使用該型別的資料庫中建立它。</span><span class="sxs-lookup"><span data-stu-id="74ff7-104">Registering a UDT involves registering the assembly and creating the type in the database in which you wish to use it.</span></span> <span data-ttu-id="74ff7-105">UDT 的使用範圍為單一資料庫，而且除非已經向每個資料庫註冊相同的組件及 UDT，否則無法在多個資料庫中使用。</span><span class="sxs-lookup"><span data-stu-id="74ff7-105">UDTs are scoped to a single database, and cannot be used in multiple databases unless the identical assembly and UDT are registered with each database.</span></span> <span data-ttu-id="74ff7-106">一旦註冊 UDT 組件並建立此型別之後，您便可在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 及用戶端程式碼中使用該 UDT。</span><span class="sxs-lookup"><span data-stu-id="74ff7-106">Once the UDT assembly is registered and the type created, you can use the UDT in [!INCLUDE[tsql](../../includes/tsql-md.md)] and in client code.</span></span> <span data-ttu-id="74ff7-107">如需詳細資訊，請參閱 [CLR 使用者定義型別](clr-user-defined-types.md)。</span><span class="sxs-lookup"><span data-stu-id="74ff7-107">For more information, see [CLR User-Defined Types](clr-user-defined-types.md).</span></span>  
  
## <a name="using-visual-studio-to-deploy-udts"></a><span data-ttu-id="74ff7-108">使用 Visual Studio 部署 UDT</span><span class="sxs-lookup"><span data-stu-id="74ff7-108">Using Visual Studio to Deploy UDTs</span></span>  
 <span data-ttu-id="74ff7-109">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 是部署 UDT 最簡單的方式。</span><span class="sxs-lookup"><span data-stu-id="74ff7-109">The easiest way to deploy your UDT is by using [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio.</span></span> <span data-ttu-id="74ff7-110">但是，若為較複雜的部署案例而且需要最大的彈性，請使用本主題稍後將要討論的 [!INCLUDE[tsql](../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="74ff7-110">For more complex deployment scenarios and the greatest flexibility, however, use [!INCLUDE[tsql](../../includes/tsql-md.md)] as discussed later in this topic.</span></span>  
  
 <span data-ttu-id="74ff7-111">請遵循下列步驟，使用 Visual Studio 建立及部署 UDT：</span><span class="sxs-lookup"><span data-stu-id="74ff7-111">Follow these steps to create and deploy a UDT using Visual Studio:</span></span>  
  
1.  <span data-ttu-id="74ff7-112">在**Visual Basic**或**Visual c #** 語言節點中建立新的**資料庫**專案。</span><span class="sxs-lookup"><span data-stu-id="74ff7-112">Create a new **Database** project in the **Visual Basic** or **Visual C#** language nodes.</span></span>  
  
2.  <span data-ttu-id="74ff7-113">加入將包含 UDT 之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的參考。</span><span class="sxs-lookup"><span data-stu-id="74ff7-113">Add a reference to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that will contain the UDT.</span></span>  
  
3.  <span data-ttu-id="74ff7-114">加入**使用者定義型**別類別。</span><span class="sxs-lookup"><span data-stu-id="74ff7-114">Add a **User-Defined Type** class.</span></span>  
  
4.  <span data-ttu-id="74ff7-115">撰寫程式碼以實作 UDT。</span><span class="sxs-lookup"><span data-stu-id="74ff7-115">Write code to implement the UDT.</span></span>  
  
5.  <span data-ttu-id="74ff7-116">從 [**建立**] 功能表中，選取 [**部署**]。</span><span class="sxs-lookup"><span data-stu-id="74ff7-116">From the **Build** menu, select **Deploy**.</span></span> <span data-ttu-id="74ff7-117">如此將會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中註冊組件並建立型別。</span><span class="sxs-lookup"><span data-stu-id="74ff7-117">This registers the assembly and creates the type in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
## <a name="using-transact-sql-to-deploy-udts"></a><span data-ttu-id="74ff7-118">使用 Transact-SQL 部署 UDT</span><span class="sxs-lookup"><span data-stu-id="74ff7-118">Using Transact-SQL to Deploy UDTs</span></span>  
 <span data-ttu-id="74ff7-119">您可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY 語法，於要使用 UDT 的資料庫中註冊組件。</span><span class="sxs-lookup"><span data-stu-id="74ff7-119">The [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY syntax is used to register the assembly in the database in which you wish to use the UDT.</span></span> <span data-ttu-id="74ff7-120">它會儲存於資料庫系統資料表內部，而非檔案系統外部。</span><span class="sxs-lookup"><span data-stu-id="74ff7-120">It is stored internally in database system tables, not externally in the file system.</span></span> <span data-ttu-id="74ff7-121">如果 UDT 與外部組件相關，也必須將它們載入資料庫。</span><span class="sxs-lookup"><span data-stu-id="74ff7-121">If the UDT is dependent on external assemblies, they too must be loaded into the database.</span></span> <span data-ttu-id="74ff7-122">CREATE TYPE 陳述式可在要使用 UDT 的資料庫內建立 UDT。</span><span class="sxs-lookup"><span data-stu-id="74ff7-122">The CREATE TYPE statement is used to create the UDT in the database in which it is to be used.</span></span> <span data-ttu-id="74ff7-123">如需詳細資訊，請參閱[CREATE ASSEMBLY &#40;transact-sql&#41;](/sql/t-sql/statements/create-assembly-transact-sql)和[Create TYPE &#40;transact-sql&#41;](/sql/t-sql/statements/create-type-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="74ff7-123">For more information, see [CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql) and [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql).</span></span>  
  
### <a name="using-create-assembly"></a><span data-ttu-id="74ff7-124">使用 CREATE ASSEMBLY</span><span class="sxs-lookup"><span data-stu-id="74ff7-124">Using CREATE ASSEMBLY</span></span>  
 <span data-ttu-id="74ff7-125">CREATE ASSEMBLY 語法會在要使用 UDT 的資料庫中註冊組件。</span><span class="sxs-lookup"><span data-stu-id="74ff7-125">The CREATE ASSEMBLY syntax registers the assembly in the database in which you wish to use the UDT.</span></span> <span data-ttu-id="74ff7-126">一旦註冊此組件，它就不具有相依性。</span><span class="sxs-lookup"><span data-stu-id="74ff7-126">Once the assembly is registered, it has no dependencies.</span></span>  
  
 <span data-ttu-id="74ff7-127">不允許在給定資料庫內建立同一組件的多個版本。</span><span class="sxs-lookup"><span data-stu-id="74ff7-127">Creating multiple versions of the same assembly in a given database is not allowed.</span></span> <span data-ttu-id="74ff7-128">但是，根據給定資料庫中的文化特性建立相同組件的多個版本是可行的。</span><span class="sxs-lookup"><span data-stu-id="74ff7-128">However, it is possible to create multiple versions of the same assembly based on culture in a given database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="74ff7-129">會根據 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體內所註冊的不同名稱來區分某個組件的多個文化特性版本。</span><span class="sxs-lookup"><span data-stu-id="74ff7-129">distinguishes multiple culture versions of an assembly by different names as registered in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="74ff7-130">如需詳細資訊，請參閱 .NET Framework SDK 中的＜建立和使用強式名稱的組件＞。</span><span class="sxs-lookup"><span data-stu-id="74ff7-130">For more information, see "Creating and Using Strong-Named Assemblies" in the .NET Framework SDK.</span></span>  
  
 <span data-ttu-id="74ff7-131">當使用 SAFE 或 EXTERNAL_ACCESS 權限集合執行 CREATE ASSEMBLY 時，系統會檢查組件，以確定它可進行驗證且型別是安全的。</span><span class="sxs-lookup"><span data-stu-id="74ff7-131">When CREATE ASSEMBLY is executed with the SAFE or EXTERNAL_ACCESS permission sets, the assembly is checked to make sure that it is verifiable and type safe.</span></span> <span data-ttu-id="74ff7-132">如果您省略指定使用權限集合，則會假設為 SAFE。</span><span class="sxs-lookup"><span data-stu-id="74ff7-132">If you omit specifying a permission set, SAFE is assumed.</span></span> <span data-ttu-id="74ff7-133">系統不會檢查使用 UNSAFE 權限集合的程式碼。</span><span class="sxs-lookup"><span data-stu-id="74ff7-133">Code with the UNSAFE permission set is not checked.</span></span> <span data-ttu-id="74ff7-134">如需有關組件權限集合的詳細資訊，請參閱[設計組件](../../relational-databases/clr-integration/assemblies-designing.md)。</span><span class="sxs-lookup"><span data-stu-id="74ff7-134">For more information about assembly permission sets, see [Designing Assemblies](../../relational-databases/clr-integration/assemblies-designing.md).</span></span>  
  
#### <a name="example"></a><span data-ttu-id="74ff7-135">範例</span><span class="sxs-lookup"><span data-stu-id="74ff7-135">Example</span></span>  
 <span data-ttu-id="74ff7-136">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語句會 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用 SAFE 許可權集合，在**AdventureWorks**資料庫中註冊 Point 元件。</span><span class="sxs-lookup"><span data-stu-id="74ff7-136">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement registers the Point assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the **AdventureWorks** database, with the SAFE permission set.</span></span> <span data-ttu-id="74ff7-137">如果省略 WITH PERMISSION_SET 子句，將會使用 SAFE 權限集合註冊該組件。</span><span class="sxs-lookup"><span data-stu-id="74ff7-137">If the WITH PERMISSION_SET clause is omitted, the assembly is registered with the SAFE permission set.</span></span>  
  
```  
USE AdventureWorks;  
CREATE ASSEMBLY Point  
FROM '\\ShareName\Projects\Point\bin\Point.dll'   
WITH PERMISSION_SET = SAFE;  
```  
  
 <span data-ttu-id="74ff7-138">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語句會使用 FROM 子句中的 *<assembly_bits>* 引數來註冊元件。</span><span class="sxs-lookup"><span data-stu-id="74ff7-138">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement registers the assembly using *<assembly_bits>* argument in the FROM clause.</span></span> <span data-ttu-id="74ff7-139">此 `varbinary` 值將檔案表示為位元組的資料流。</span><span class="sxs-lookup"><span data-stu-id="74ff7-139">This `varbinary` value represents the file as a stream of bytes.</span></span>  
  
```  
USE AdventureWorks;  
CREATE ASSEMBLY Point  
FROM 0xfeac4 ... 21ac78  
```  
  
### <a name="using-create-type"></a><span data-ttu-id="74ff7-140">使用 CREATE TYPE</span><span class="sxs-lookup"><span data-stu-id="74ff7-140">Using CREATE TYPE</span></span>  
 <span data-ttu-id="74ff7-141">一旦將組件載入資料庫，即可使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TYPE 陳述式建立此型別。</span><span class="sxs-lookup"><span data-stu-id="74ff7-141">Once the assembly is loaded into the database, you can then create the type using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TYPE statement.</span></span> <span data-ttu-id="74ff7-142">這樣會將該型別加入該資料庫的可用型別清單。</span><span class="sxs-lookup"><span data-stu-id="74ff7-142">This adds the type to the list of available types for that database.</span></span> <span data-ttu-id="74ff7-143">該型別具有資料庫範圍，而且只能在建立它的資料庫中使用。</span><span class="sxs-lookup"><span data-stu-id="74ff7-143">The type has database scope and the type can only be used in the database in which it was created.</span></span> <span data-ttu-id="74ff7-144">如果資料庫中已存在 UDT，則 CREATE TYPE 陳述式會失敗並出現錯誤。</span><span class="sxs-lookup"><span data-stu-id="74ff7-144">If the UDT already exists in the database, the CREATE TYPE statement fails with an error.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="74ff7-145">CREATE TYPE 語法也可用於建立原生 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 別名資料類型，而且要用來取代 `sp_addtype`，當做建立別名資料類型的一個方式。</span><span class="sxs-lookup"><span data-stu-id="74ff7-145">The CREATE TYPE syntax is also used for creating native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alias data types, and is intended to replace `sp_addtype` as a means of creating alias data types.</span></span> <span data-ttu-id="74ff7-146">CREATE TYPE 語法中的某些選擇性引數會參考建立 UDT，且不適用於建立別名資料類型 (如基底類型)。</span><span class="sxs-lookup"><span data-stu-id="74ff7-146">Some of the optional arguments in the CREATE TYPE syntax refer to creating UDTs, and are not applicable to creating alias data types (such as base type).</span></span>  
  
 <span data-ttu-id="74ff7-147">如需詳細資訊，請參閱[CREATE TYPE &#40;transact-sql&#41;](/sql/t-sql/statements/create-type-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="74ff7-147">For more information, see [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql).</span></span>  
  
#### <a name="example"></a><span data-ttu-id="74ff7-148">範例</span><span class="sxs-lookup"><span data-stu-id="74ff7-148">Example</span></span>  
 <span data-ttu-id="74ff7-149">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式會建立 `Point` 類型。</span><span class="sxs-lookup"><span data-stu-id="74ff7-149">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement creates the `Point` type.</span></span> <span data-ttu-id="74ff7-150">外部名稱是使用*AssemblyName*的兩部分命名語法來指定。*UDTName*。</span><span class="sxs-lookup"><span data-stu-id="74ff7-150">The EXTERNAL NAME is specified using the two-part naming syntax of *AssemblyName*.*UDTName*.</span></span>  
  
```  
CREATE TYPE dbo.Point   
EXTERNAL NAME Point.[Point];  
```  
  
## <a name="removing-a-udt-from-the-database"></a><span data-ttu-id="74ff7-151">從資料庫移除 UDT</span><span class="sxs-lookup"><span data-stu-id="74ff7-151">Removing a UDT from the Database</span></span>  
 <span data-ttu-id="74ff7-152">DROP TYPE 陳述式會從目前資料庫移除 UDT。</span><span class="sxs-lookup"><span data-stu-id="74ff7-152">The DROP TYPE statement removes a UDT from the current database.</span></span> <span data-ttu-id="74ff7-153">一旦卸除 UDT 之後，您就可以使用 DROP ASSEMBLY 陳述式，從資料庫中卸除組件。</span><span class="sxs-lookup"><span data-stu-id="74ff7-153">Once a UDT is dropped, you can use the DROP ASSEMBLY statement to drop the assembly from the database.</span></span>  
  
 <span data-ttu-id="74ff7-154">在下列情況下，將不會執行 DROP TYPE 陳述式：</span><span class="sxs-lookup"><span data-stu-id="74ff7-154">The DROP TYPE statement does not execute in the following situations:</span></span>  
  
-   <span data-ttu-id="74ff7-155">資料庫中包含使用 UDT 定義之資料行的資料表。</span><span class="sxs-lookup"><span data-stu-id="74ff7-155">Tables in the database that contain columns defined using the UDT.</span></span>  
  
-   <span data-ttu-id="74ff7-156">使用 WITH SCHEMABINDING 子句在資料庫中建立的函數、預存程序或觸發程序 (這些項目會使用 UDT 變數或參數)。</span><span class="sxs-lookup"><span data-stu-id="74ff7-156">Functions, stored procedures, or triggers that use variables or parameters of the UDT, created in the database with the WITH SCHEMABINDING clause.</span></span>  
  
### <a name="example"></a><span data-ttu-id="74ff7-157">範例</span><span class="sxs-lookup"><span data-stu-id="74ff7-157">Example</span></span>  
 <span data-ttu-id="74ff7-158">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 必須以下列順序執行。</span><span class="sxs-lookup"><span data-stu-id="74ff7-158">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] must execute in the following order.</span></span> <span data-ttu-id="74ff7-159">首先，必須卸除參考 `Point` UDT 的資料表，然後是型別，最後是組件。</span><span class="sxs-lookup"><span data-stu-id="74ff7-159">First the table which references the `Point` UDT must be dropped, then the type, and finally the assembly.</span></span>  
  
```  
DROP TABLE dbo.Points;  
DROP TYPE dbo.Point;  
DROP ASSEMBLY Point;  
```  
  
### <a name="finding-udt-dependencies"></a><span data-ttu-id="74ff7-160">尋找 UDT 相依性</span><span class="sxs-lookup"><span data-stu-id="74ff7-160">Finding UDT Dependencies</span></span>  
 <span data-ttu-id="74ff7-161">如果有相依物件存在 (如具有 UDT 資料行定義的資料表)，則 DROP TYPE 陳述式會失敗。</span><span class="sxs-lookup"><span data-stu-id="74ff7-161">If there are dependent objects, such as tables with UDT column definitions, the DROP TYPE statement fails.</span></span> <span data-ttu-id="74ff7-162">如果資料庫中有使用 WITH SCHEMABINDING 子句所建立的函數、預存程序或觸發程序，而且這些常式使用使用者定義型別的變數或參數，該陳述式也會失敗。</span><span class="sxs-lookup"><span data-stu-id="74ff7-162">It also fails if there are functions, stored procedures, or triggers created in the database using the WITH SCHEMABINDING clause, if these routines use variables or parameters of the user-defined type.</span></span> <span data-ttu-id="74ff7-163">您必須先卸除所有相依物件，然後再執行 DROP TYPE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="74ff7-163">You must first drop all dependent objects, and then execute the DROP TYPE statement.</span></span>  
  
 <span data-ttu-id="74ff7-164">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢會尋找在**AdventureWorks**資料庫中使用 UDT 的所有資料行和參數。</span><span class="sxs-lookup"><span data-stu-id="74ff7-164">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] query locates all of the columns and parameters that use a UDT in the **AdventureWorks** database.</span></span>  
  
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
  
## <a name="maintaining-udts"></a><span data-ttu-id="74ff7-165">維護 UDT</span><span class="sxs-lookup"><span data-stu-id="74ff7-165">Maintaining UDTs</span></span>  
 <span data-ttu-id="74ff7-166">一旦在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中建立 UDT，便無法對其進行修改，但可以改變此型別所依據的組件。</span><span class="sxs-lookup"><span data-stu-id="74ff7-166">You cannot modify a UDT once it is created in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, although you can alter the assembly on which the type is based.</span></span> <span data-ttu-id="74ff7-167">在大多數情況下，您必須使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] DROP TYPE 陳述式從資料庫中移除 UDT、對基礎組件進行變更，並使用 ALTER ASSEMBLY 陳述式將其重新載入。</span><span class="sxs-lookup"><span data-stu-id="74ff7-167">In most cases, you must remove the UDT from the database with the [!INCLUDE[tsql](../../includes/tsql-md.md)] DROP TYPE statement, make changes to the underlying assembly, and reload it using the ALTER ASSEMBLY statement.</span></span> <span data-ttu-id="74ff7-168">然後需要重新建立 UDT 及一切相依物件。</span><span class="sxs-lookup"><span data-stu-id="74ff7-168">You then need to re-create the UDT and any dependent objects.</span></span>  
  
### <a name="example"></a><span data-ttu-id="74ff7-169">範例</span><span class="sxs-lookup"><span data-stu-id="74ff7-169">Example</span></span>  
 <span data-ttu-id="74ff7-170">當您變更並重新編譯 UDT 組件中的原始程式碼之後，可以使用 ALTER ASSEMBLY 陳述式。</span><span class="sxs-lookup"><span data-stu-id="74ff7-170">The ALTER ASSEMBLY statement is used after you have made changes to the source code in your UDT assembly and recompiled it.</span></span> <span data-ttu-id="74ff7-171">它會將此 .dll 檔案複製到伺服器，並重新繫結至新的組件。</span><span class="sxs-lookup"><span data-stu-id="74ff7-171">It copies the .dll file to the server and rebinds to the new assembly.</span></span> <span data-ttu-id="74ff7-172">如需完整的語法，請參閱[ALTER ASSEMBLY &#40;transact-sql&#41;](/sql/t-sql/statements/alter-assembly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="74ff7-172">For the complete syntax, see [ALTER ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-assembly-transact-sql).</span></span>  
  
 <span data-ttu-id="74ff7-173">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY 陳述式會從指定的磁碟位置重新載入 Point.dll 組件。</span><span class="sxs-lookup"><span data-stu-id="74ff7-173">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY statement reloads the Point.dll assembly from the specified location on disk.</span></span>  
  
```  
ALTER ASSEMBLY Point  
FROM '\\Projects\Point\bin\Point.dll'  
```  
  
### <a name="using-alter-assembly-to-add-source-code"></a><span data-ttu-id="74ff7-174">使用 ALTER ASSEMBLY 加入原始程式碼</span><span class="sxs-lookup"><span data-stu-id="74ff7-174">Using ALTER ASSEMBLY to Add Source Code</span></span>  
 <span data-ttu-id="74ff7-175">ALTER ASSEMBLY 語法中的 ADD FILE 子句不存在於 CREATE ASSEMBLY 中。</span><span class="sxs-lookup"><span data-stu-id="74ff7-175">The ADD FILE clause in the ALTER ASSEMBLY syntax is not present in CREATE ASSEMBLY.</span></span> <span data-ttu-id="74ff7-176">您可以使用它來加入原始程式碼，或與組件相關聯的任何其他檔案。</span><span class="sxs-lookup"><span data-stu-id="74ff7-176">You can use it to add source code or any other files associated with an assembly.</span></span> <span data-ttu-id="74ff7-177">這些檔案會從原始位置複製，並儲存在資料庫的系統資料表中。</span><span class="sxs-lookup"><span data-stu-id="74ff7-177">The files are copied from their original locations and stored in system tables in the database.</span></span> <span data-ttu-id="74ff7-178">如此可在您需要重新建立或記載 UDT 的目前版本時，確保您一定有原始程式碼或其他檔案可用。</span><span class="sxs-lookup"><span data-stu-id="74ff7-178">This ensures that you always have source code or other files on hand should you ever need to re-create or document the current version of the UDT.</span></span>  
  
 <span data-ttu-id="74ff7-179">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY 語句會加入 UDT 的 Point.cs 類別原始碼 `Point` 。</span><span class="sxs-lookup"><span data-stu-id="74ff7-179">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY statement adds the Point.cs class source code for the `Point` UDT.</span></span> <span data-ttu-id="74ff7-180">這會複製 Point.cs 檔案中包含的文字，並將它儲存在名為 PointSource 的資料庫中。</span><span class="sxs-lookup"><span data-stu-id="74ff7-180">This copies the text contained in the Point.cs file and stores it in the database under the name "PointSource".</span></span>  
  
```  
ALTER ASSEMBLY Point  
ADD FILE FROM '\\Projects\Point\Point.cs' AS PointSource;  
```  
  
 <span data-ttu-id="74ff7-181">元件資訊儲存在已安裝元件之資料庫的**sys.databases assembly_files**資料表中。</span><span class="sxs-lookup"><span data-stu-id="74ff7-181">Assembly information is stored in the **sys.assembly_files** table in the database where the assembly has been installed.</span></span> <span data-ttu-id="74ff7-182">**Assembly_files**資料表包含下列資料行。</span><span class="sxs-lookup"><span data-stu-id="74ff7-182">The **sys.assembly_files** table contains the following columns.</span></span>  
  
 <span data-ttu-id="74ff7-183">**assembly_id**</span><span class="sxs-lookup"><span data-stu-id="74ff7-183">**assembly_id**</span></span>  
 <span data-ttu-id="74ff7-184">為組件定義的識別項。</span><span class="sxs-lookup"><span data-stu-id="74ff7-184">The identifier defined for the assembly.</span></span> <span data-ttu-id="74ff7-185">此號碼會指派給與同一組件相關的所有物件。</span><span class="sxs-lookup"><span data-stu-id="74ff7-185">This number is assigned to all objects relating to the same assembly.</span></span>  
  
 <span data-ttu-id="74ff7-186">**name**</span><span class="sxs-lookup"><span data-stu-id="74ff7-186">**name**</span></span>  
 <span data-ttu-id="74ff7-187">物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="74ff7-187">The name of the object.</span></span>  
  
 <span data-ttu-id="74ff7-188">**file_id**</span><span class="sxs-lookup"><span data-stu-id="74ff7-188">**file_id**</span></span>  
 <span data-ttu-id="74ff7-189">識別每個物件的數位，其中第一個物件與給定的**assembly_id**相關聯，而其值為1。</span><span class="sxs-lookup"><span data-stu-id="74ff7-189">A number identifying each object, with the first object associated with a given **assembly_id** being given the value of 1.</span></span> <span data-ttu-id="74ff7-190">如果有多個物件與相同的**assembly_id**相關聯，則每個後續的**file_id**值都會遞增1。</span><span class="sxs-lookup"><span data-stu-id="74ff7-190">If there are multiple objects associated with the same **assembly_id**, then each subsequent **file_id** value is incremented by 1.</span></span>  
  
 <span data-ttu-id="74ff7-191">**content**</span><span class="sxs-lookup"><span data-stu-id="74ff7-191">**content**</span></span>  
 <span data-ttu-id="74ff7-192">組件或檔案的十六進位表示法。</span><span class="sxs-lookup"><span data-stu-id="74ff7-192">The hexadecimal representation of the assembly or file.</span></span>  
  
 <span data-ttu-id="74ff7-193">您可以使用 CAST 或 CONVERT 函數，將**content**資料行的內容轉換成可讀取的文字。</span><span class="sxs-lookup"><span data-stu-id="74ff7-193">You can use the CAST or CONVERT function to convert the contents of the **content** column to readable text.</span></span> <span data-ttu-id="74ff7-194">下列查詢會將 Point.cs 檔案的內容轉換為可讀取的文字，並在 WHERE 子句中使用此名稱，以將結果集限制為單一資料列。</span><span class="sxs-lookup"><span data-stu-id="74ff7-194">The following query converts the contents of the Point.cs file to readable text, using the name in the WHERE clause to restrict the result set to a single row.</span></span>  
  
```  
SELECT CAST(content AS varchar(8000))   
  FROM sys.assembly_files   
  WHERE name='PointSource';  
```  
  
 <span data-ttu-id="74ff7-195">如果您將結果複製並貼至文字編輯器中，將會看到原始檔案中的分行符號及空格均已保留。</span><span class="sxs-lookup"><span data-stu-id="74ff7-195">If you copy and paste the results in to a text editor, you will see that the line breaks and spaces that existed in the original have been preserved.</span></span>  
  
## <a name="managing-udts-and-assemblies"></a><span data-ttu-id="74ff7-196">管理 UDT 及組件</span><span class="sxs-lookup"><span data-stu-id="74ff7-196">Managing UDTs and Assemblies</span></span>  
 <span data-ttu-id="74ff7-197">當規劃 UDT 實作時，請考量 UDT 組件本身需要哪些方法，以及哪些方法應在個別組件中建立，並將其實作為使用者定義函數還是預存程序。</span><span class="sxs-lookup"><span data-stu-id="74ff7-197">When planning your implementation of UDTs, consider which methods are needed in the UDT assembly itself, and which methods should be created in separate assemblies and implemented as user-defined functions or stored procedures.</span></span> <span data-ttu-id="74ff7-198">將各方法劃分到不同組件，可讓您在更新程式碼時不會影響可能儲存在資料表之 UDT 資料行中的資料。</span><span class="sxs-lookup"><span data-stu-id="74ff7-198">Separating methods into separate assemblies allows you to update code without affecting data that may be stored in a UDT column in a table.</span></span> <span data-ttu-id="74ff7-199">只有當新的定義可以讀取先前的值且型別的簽章未變更時，您才可以在不卸除 UDT 資料行及其他相依物件的情況下修改 UDT 組件。</span><span class="sxs-lookup"><span data-stu-id="74ff7-199">You can modify UDT assemblies without dropping UDT columns and other dependent objects only when the new definition can read the former values and the signature of the type does not change.</span></span>  
  
 <span data-ttu-id="74ff7-200">將可能會發生變更的程序性程式碼與實作 UDT 所需的程式碼分開，可以大幅簡化維護作業。</span><span class="sxs-lookup"><span data-stu-id="74ff7-200">Separating procedural code that may change from the code required to implement the UDT greatly simplifies maintenance.</span></span> <span data-ttu-id="74ff7-201">只包含 UDT 運作所需的程式碼並使您的 UDT 定義盡量簡單，這樣就會減少因程式碼修訂或錯誤修復而需要從資料庫卸除 UDT 本身的風險。</span><span class="sxs-lookup"><span data-stu-id="74ff7-201">Including only code that is necessary for the UDT to function, and keeping your UDT definitions as simple as possible, reduces the risk that the UDT itself may need to be dropped from the database for code revisions or bug fixes.</span></span>  
  
### <a name="the-currency-udt-and-currency-conversion-function"></a><span data-ttu-id="74ff7-202">Currency UDT 及貨幣轉換函數</span><span class="sxs-lookup"><span data-stu-id="74ff7-202">The Currency UDT and Currency Conversion Function</span></span>  
 <span data-ttu-id="74ff7-203">**AdventureWorks**範例資料庫中的**Currency** UDT 提供了一種實用的範例，說明如何將 udt 及其相關聯的函式進行結構。</span><span class="sxs-lookup"><span data-stu-id="74ff7-203">The **Currency** UDT in the **AdventureWorks** sample database provides a useful example of the recommended way to structure a UDT and its associated functions.</span></span> <span data-ttu-id="74ff7-204">**貨幣**UDT 是用來根據特定文化特性的貨幣系統來處理 money，並允許儲存不同的貨幣類型，例如美元、歐元等等。</span><span class="sxs-lookup"><span data-stu-id="74ff7-204">The **Currency** UDT is used for handling money based on the monetary system of a particular culture, and allows for storage of different currency types, such as dollars, euros, and so forth.</span></span> <span data-ttu-id="74ff7-205">UDT 類別會將文化特性名稱顯示為字串，而將貨幣金額顯示為 `decimal` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="74ff7-205">The UDT class exposes a culture name as a string, and an amount of money as a `decimal` data type.</span></span> <span data-ttu-id="74ff7-206">所有必要的序列化方法都包含在定義類別的組件中。</span><span class="sxs-lookup"><span data-stu-id="74ff7-206">All of the necessary serialization methods are contained within the assembly defining the class.</span></span> <span data-ttu-id="74ff7-207">函式，可將貨幣從某個文化特性轉換成另一個文化特性，並實作為名為**ConvertCurrency**的外部函數，而此函數位于不同的元件中。</span><span class="sxs-lookup"><span data-stu-id="74ff7-207">The function that implements currency conversion from one culture to another is implemented as an external function named **ConvertCurrency**, and this function is located in a separate assembly.</span></span> <span data-ttu-id="74ff7-208">**ConvertCurrency**函數會藉由從**AdventureWorks**資料庫中的資料表抓取轉換速率來執行其工作。</span><span class="sxs-lookup"><span data-stu-id="74ff7-208">The **ConvertCurrency** function does its work by retrieving the conversion rate from a table in the **AdventureWorks** database.</span></span> <span data-ttu-id="74ff7-209">如果轉換率的來源應該變更，或如果現有的程式碼有任何其他變更，則可以輕鬆地修改元件，而不會影響**Currency** UDT。</span><span class="sxs-lookup"><span data-stu-id="74ff7-209">If the source of the conversion rates should ever change, or if there should be any other changes to the existing code, the assembly can be easily modified without affecting the **Currency** UDT.</span></span>  
  
 <span data-ttu-id="74ff7-210">藉由安裝 common language runtime (CLR) 範例，可以找到**Currency** UDT 和**ConvertCurrency**函式的程式代碼清單。</span><span class="sxs-lookup"><span data-stu-id="74ff7-210">The code listing for the **Currency** UDT and **ConvertCurrency** functions can be found by installing the common language runtime (CLR) samples.</span></span>  
  
### <a name="using-udts-across-databases"></a><span data-ttu-id="74ff7-211">跨資料庫使用 UDT</span><span class="sxs-lookup"><span data-stu-id="74ff7-211">Using UDTs Across Databases</span></span>  
 <span data-ttu-id="74ff7-212">根據定義，UDT 屬於單一資料庫的範圍。</span><span class="sxs-lookup"><span data-stu-id="74ff7-212">UDTs are by definition scoped to a single database.</span></span> <span data-ttu-id="74ff7-213">因此，在一個資料庫內定義的 UDT 無法用於其他資料庫中的資料行定義。</span><span class="sxs-lookup"><span data-stu-id="74ff7-213">Therefore, a UDT defined in one database cannot be used in a column definition in another database.</span></span> <span data-ttu-id="74ff7-214">為了在多個資料庫中使用 UDT，您必須在每個資料庫內的相同組件上執行 CREATE ASSEMBLY 及 CREATE TYPE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="74ff7-214">In order to use UDTs in multiple databases, you must execute the CREATE ASSEMBLY and CREATE TYPE statements in each database on identical assemblies.</span></span> <span data-ttu-id="74ff7-215">具有相同名稱、強式名稱、文化特性、版本、使用權限集合及二進位內容的組件，會視為相同組件。</span><span class="sxs-lookup"><span data-stu-id="74ff7-215">Assemblies are considered identical if they have the same name, strong name, culture, version, permission set, and binary contents.</span></span>  
  
 <span data-ttu-id="74ff7-216">一旦在兩個資料庫中登錄 UDT 並可存取 UDT，您便可從某個資料庫轉換 UDT 值，以用於另一資料庫。</span><span class="sxs-lookup"><span data-stu-id="74ff7-216">Once the UDT is registered and accessible in both databases, you can convert a UDT value from one database for use in another.</span></span> <span data-ttu-id="74ff7-217">在下列情況下，可以跨資料庫使用相同的 UDT：</span><span class="sxs-lookup"><span data-stu-id="74ff7-217">Identical UDTs can be used across databases in the following scenarios:</span></span>  
  
-   <span data-ttu-id="74ff7-218">呼叫不同資料庫中定義的預存程序。</span><span class="sxs-lookup"><span data-stu-id="74ff7-218">Calling stored procedure defined in different databases.</span></span>  
  
-   <span data-ttu-id="74ff7-219">查詢不同資料庫中定義的資料表。</span><span class="sxs-lookup"><span data-stu-id="74ff7-219">Querying tables defined in different databases.</span></span>  
  
-   <span data-ttu-id="74ff7-220">從某個資料庫資料表 UDT 資料行選取 UDT 資料，並將其插入具有相同 UDT 資料行的第二個資料庫中。</span><span class="sxs-lookup"><span data-stu-id="74ff7-220">Selecting UDT data from one database table UDT column and inserting it into a second database with an identical UDT column.</span></span>  
  
 <span data-ttu-id="74ff7-221">在這些情況下，伺服器所需的任何轉換都會自動發生。</span><span class="sxs-lookup"><span data-stu-id="74ff7-221">In these situations, any conversion required by the server occurs automatically.</span></span> <span data-ttu-id="74ff7-222">您將無法使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST 或 CONVERT 函數明確地執行轉換。</span><span class="sxs-lookup"><span data-stu-id="74ff7-222">You are not able to perform the conversions explicitly using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST or CONVERT functions.</span></span>  
  
 <span data-ttu-id="74ff7-223">請注意，在 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] **tempdb**系統資料庫中建立工作資料表時，您不需要採取任何動作來使用 udt。</span><span class="sxs-lookup"><span data-stu-id="74ff7-223">Note that you do not need to take any action for using UDTs when [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] creates work tables in the **tempdb** system database.</span></span> <span data-ttu-id="74ff7-224">這包括處理資料指標、資料表變數，以及使用者定義的資料表值函式，這些函數包含 Udt，而且會以透明的方式使用**tempdb**。</span><span class="sxs-lookup"><span data-stu-id="74ff7-224">This includes the handling of cursors, table variables, and user-defined table-valued functions that include UDTs and that transparently make use of **tempdb**.</span></span> <span data-ttu-id="74ff7-225">不過，如果您在**tempdb**中明確建立定義 UDT 資料行的臨時表，則 UDT 必須以和使用者資料庫相同的方式，在**tempdb**中註冊。</span><span class="sxs-lookup"><span data-stu-id="74ff7-225">However, if you explicitly create a temporary table in **tempdb** that defines a UDT column, then the UDT must be registered in **tempdb** the same way as for a user database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74ff7-226">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74ff7-226">See Also</span></span>  
 [<span data-ttu-id="74ff7-227">CLR 使用者定義類型</span><span class="sxs-lookup"><span data-stu-id="74ff7-227">CLR User-Defined Types</span></span>](clr-user-defined-types.md)  
  
  
