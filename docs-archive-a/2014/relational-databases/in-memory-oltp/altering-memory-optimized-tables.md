---
title: 改變記憶體最佳化資料表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 690b70b7-5be1-4014-af97-54e531997839
author: rothja
ms.author: jroth
ms.openlocfilehash: 4eedc6fdb45efc6c87765cd2208ead90c1887c27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599508"
---
# <a name="altering-memory-optimized-tables"></a><span data-ttu-id="da87c-102">改變記憶體最佳化資料表</span><span class="sxs-lookup"><span data-stu-id="da87c-102">Altering Memory-Optimized Tables</span></span>
  <span data-ttu-id="da87c-103">不支援執行記憶體最佳化資料表上的 ALTER 作業。</span><span class="sxs-lookup"><span data-stu-id="da87c-103">Performing ALTER operations on memory-optimized tables is not supported.</span></span> <span data-ttu-id="da87c-104">這些作業包括變更 bucket_count、加入或移除索引，以及加入或移除資料行等等。</span><span class="sxs-lookup"><span data-stu-id="da87c-104">This includes such operations as changing the bucket_count, adding or removing an index, and adding or removing a column.</span></span> <span data-ttu-id="da87c-105">本主題提供如何更新記憶體最佳化之資料表的指導方針。</span><span class="sxs-lookup"><span data-stu-id="da87c-105">This topic provides guidelines on how to update memory-optimized tables.</span></span>  
  
## <a name="updating-the-definition-of-a-memory-optimized-table"></a><span data-ttu-id="da87c-106">更新記憶體最佳化資料表的定義</span><span class="sxs-lookup"><span data-stu-id="da87c-106">Updating the Definition of a Memory-Optimized Table</span></span>  
 <span data-ttu-id="da87c-107">若要更新記憶體最佳化資料表的定義，則需建立包含更新之資料表定義的新資料表、將資料複製到新資料表，並且開始使用新資料表。</span><span class="sxs-lookup"><span data-stu-id="da87c-107">Updating the definition of a memory-optimized table requires you to create a new table with the updated table definition, copy the data to the new table, and start using the new table.</span></span> <span data-ttu-id="da87c-108">除非資料表是唯讀的，否則就需要停止資料表上的工作負載，以確保複製資料時不會對資料表進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="da87c-108">Unless the table is read-only, this requires stopping the workload on the table, to ensure no changes are made to the table while the data copy is performed.</span></span>  
  
 <span data-ttu-id="da87c-109">以下程序概述更新資料表所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="da87c-109">The following procedure outlines the steps required to update a table.</span></span> <span data-ttu-id="da87c-110">在這個範例中，更新會加入索引。</span><span class="sxs-lookup"><span data-stu-id="da87c-110">In this example, the update adds an index.</span></span> <span data-ttu-id="da87c-111">此程序會保留資料表的名稱，並需要進行兩次資料複製作業：一次是複製到暫存資料表，另一次是複製到新的資料表。</span><span class="sxs-lookup"><span data-stu-id="da87c-111">This procedure preserves the name of the table and requires two data copy operations: once to a temporary table, and once to the new table.</span></span> <span data-ttu-id="da87c-112">變更索引的 bucket_count，或是加入或移除資料行都是以相同方式執行。</span><span class="sxs-lookup"><span data-stu-id="da87c-112">Changing the bucket_count of an index or adding or removing a column is performed the same way.</span></span>  
  
1.  <span data-ttu-id="da87c-113">停止資料表上的工作負載。</span><span class="sxs-lookup"><span data-stu-id="da87c-113">Stop the workload on the table.</span></span>  
  
2.  <span data-ttu-id="da87c-114">產生資料表的指令碼，並將新索引加入至指令碼。</span><span class="sxs-lookup"><span data-stu-id="da87c-114">Generate script for the table and add the new index to the script.</span></span>  
  
3.  <span data-ttu-id="da87c-115">產生參考 T 之結構描述繫結物件的指令碼 (主要是原生編譯預存程序) 及其權限。</span><span class="sxs-lookup"><span data-stu-id="da87c-115">Generate script for the schema-bound objects (mainly natively compiled stored procedures) referencing T and their permissions.</span></span>  
  
     <span data-ttu-id="da87c-116">可使用下列查詢找到參考資料表的結構描述繫結物件：</span><span class="sxs-lookup"><span data-stu-id="da87c-116">The schema-bound objects referencing the table can be found using the following query:</span></span>  
  
    ```sql  
    declare @t nvarchar(255) = N'<table name>'  
  
    select r.referencing_schema_name, r.referencing_entity_name  
    from sys.dm_sql_referencing_entities (@t, 'OBJECT') as r join sys.sql_modules m on r.referencing_id=m.object_id  
    where r.is_caller_dependent = 0 and m.is_schema_bound=1;  
    ```  
  
     <span data-ttu-id="da87c-117">您可以使用下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 撰寫預存程序之權限的指令碼：</span><span class="sxs-lookup"><span data-stu-id="da87c-117">The permissions of a stored procedure can be scripted using the following [!INCLUDE[tsql](../../includes/tsql-md.md)]:</span></span>  
  
    ```sql  
    declare @sp nvarchar(255) = N'<procedure name>'  
    declare @permissions nvarchar(max) = N''  
  
    select @permissions += dp.state_desc + N' ' + dp.permission_name + N' ON ' +   
       quotename(schema_name(o.schema_id)) + N'.' + quotename(o.name) + N' TO ' +  
       quotename(u.name) + N'; ' + char(13)  
    from sys.database_permissions as dp  
  
    join sys.database_principals as u  
       on u.principal_id = dp.grantee_principal_id  
  
    join sys.objects as o  
       on o.object_id = dp.major_id  
    where dp.class = 1 /* object */  
       and dp.minor_id = 0 and o.object_id=object_id(@sp);  
  
    select @permissions  
    ```  
  
4.  <span data-ttu-id="da87c-118">建立資料表的副本，並且從原始資料表將資料複製到資料表副本。</span><span class="sxs-lookup"><span data-stu-id="da87c-118">Create a copy of the table and copy the data from the original table to the copy of the table.</span></span> <span data-ttu-id="da87c-119">您可以使用下列1來建立複本 [!INCLUDE[tsql](../../includes/tsql-md.md)] <sup> </sup>。</span><span class="sxs-lookup"><span data-stu-id="da87c-119">The copy can be created using the following [!INCLUDE[tsql](../../includes/tsql-md.md)]<sup>1</sup>.</span></span>  
  
    ```sql  
    select * into dbo.T_copy from dbo.T  
    ```  
  
     <span data-ttu-id="da87c-120">如果有足夠的可用記憶體，可以 `T_copy` 是記憶體優化資料表，讓資料複製更快。<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="da87c-120">If there is enough available memory, `T_copy` could be a memory-optimized table, which makes the data copy faster.<sup>2</sup></span></span>  
  
5.  <span data-ttu-id="da87c-121">卸除參考原始資料表的結構描述繫結物件。</span><span class="sxs-lookup"><span data-stu-id="da87c-121">Drop the schema-bound objects referencing the original table.</span></span>  
  
6.  <span data-ttu-id="da87c-122">卸除原始資料表。</span><span class="sxs-lookup"><span data-stu-id="da87c-122">Drop the original table.</span></span>  
  
7.  <span data-ttu-id="da87c-123">建立新資料表 (`T`)，其中的指令碼會包含新索引。</span><span class="sxs-lookup"><span data-stu-id="da87c-123">Create the new table (`T`) with the script containing the new index.</span></span>  
  
8.  <span data-ttu-id="da87c-124">從 `T_copy` 將資料複製到 `T`。</span><span class="sxs-lookup"><span data-stu-id="da87c-124">Copy the data from `T_copy` to `T`.</span></span>  
  
9. <span data-ttu-id="da87c-125">重新建立參考的結構描述繫結物件，並套用權限。</span><span class="sxs-lookup"><span data-stu-id="da87c-125">Recreate the referencing schema-bound objects and apply the permissions.</span></span>  
  
10. <span data-ttu-id="da87c-126">在 `T` 上啟動工作負載。</span><span class="sxs-lookup"><span data-stu-id="da87c-126">Start the workload on `T`.</span></span>  
  
 <span data-ttu-id="da87c-127"><sup>1</sup>請注意， `T_copy` 在此範例中，會保存到磁片。</span><span class="sxs-lookup"><span data-stu-id="da87c-127"><sup>1</sup> Note that `T_copy` is persisted to disk in this example.</span></span> <span data-ttu-id="da87c-128">如果有 `T` 的備份可用，`T_copy` 可以是暫存或非持久資料表。</span><span class="sxs-lookup"><span data-stu-id="da87c-128">If a backup of `T` is available, `T_copy` could be a temporary or a non-durable table.</span></span>  
  
 <span data-ttu-id="da87c-129"><sup>2</sup>必須有足夠的記憶體可供 `T_copy` 。</span><span class="sxs-lookup"><span data-stu-id="da87c-129"><sup>2</sup> There must be enough memory for `T_copy`.</span></span> <span data-ttu-id="da87c-130">記憶體不會在 `DROP TABLE` 上立即釋放。</span><span class="sxs-lookup"><span data-stu-id="da87c-130">Memory is not freed immediately on `DROP TABLE`.</span></span> <span data-ttu-id="da87c-131">如果 `T_copy` 為記憶體最佳化，則必須有足夠的記憶體可供兩個額外的 `T` 副本使用。</span><span class="sxs-lookup"><span data-stu-id="da87c-131">If `T_copy` is memory optimized, there needs to be enough memory for two additional copies of `T`.</span></span> <span data-ttu-id="da87c-132">如果 `T_copy` 是以磁碟為基礎的資料表，就只需要足夠的記憶體以進行額外一次 `T` 複製，因為卸除舊版 `T` 之後，需讓記憶體回收行程趕上進度。</span><span class="sxs-lookup"><span data-stu-id="da87c-132">If `T_copy` is a disk-based table, there only needs to be enough memory for one additional copy of `T`, due to the garbage collector needing to catch up after dropping the old version of `T`.</span></span>  
  
## <a name="changing-schema-powershell"></a><span data-ttu-id="da87c-133">變更結構描述 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="da87c-133">Changing Schema (PowerShell)</span></span>  
 <span data-ttu-id="da87c-134">下列 PowerShell 指令碼會藉由撰寫資料庫和相關權限的指令碼，以準備並產生結構描述變更。</span><span class="sxs-lookup"><span data-stu-id="da87c-134">The following PowerShell scripts prepare and generate for schema changes by scripting the table and associated permissions.</span></span>  
  
```powershell
prepare_schema_change.ps1 <serverName> <databaseName> <schemaName> <tableName>
```
  
 <span data-ttu-id="da87c-135">此指令碼會採用資料表做為引數，並且撰寫在目前資料夾中物件與其權限以及參考結構描述繫結物件與其權限的指令碼。</span><span class="sxs-lookup"><span data-stu-id="da87c-135">This script takes as arguments a table, and scripts the object and its permissions and referencing schema-bound objects and their permissions in the current folder.</span></span> <span data-ttu-id="da87c-136">總共會產生 7 個指令碼用於更新輸入資料表的結構描述：</span><span class="sxs-lookup"><span data-stu-id="da87c-136">A total of 7 scripts are generated for updating the schema of the input table:</span></span>  
  
-   <span data-ttu-id="da87c-137">將資料複製到暫存資料表 (堆積)。</span><span class="sxs-lookup"><span data-stu-id="da87c-137">Copy data to a temporary table (a heap).</span></span>  
  
-   <span data-ttu-id="da87c-138">卸除參考資料表的結構描述繫結物件。</span><span class="sxs-lookup"><span data-stu-id="da87c-138">Drop schema-bound objects referencing the table.</span></span>  
  
-   <span data-ttu-id="da87c-139">卸除資料表。</span><span class="sxs-lookup"><span data-stu-id="da87c-139">Drop the table.</span></span>  
  
-   <span data-ttu-id="da87c-140">重新建立具有新結構描述的資料表，並重新套用權限。</span><span class="sxs-lookup"><span data-stu-id="da87c-140">Recreate the table with the new schema and reapply permissions.</span></span>  
  
-   <span data-ttu-id="da87c-141">從暫存資料表將資料複製到重新建立的資料表。</span><span class="sxs-lookup"><span data-stu-id="da87c-141">Copy data from the temporary table to the recreated table.</span></span>  
  
-   <span data-ttu-id="da87c-142">重新建立參考資料表的結構描述繫結物件與其權限。</span><span class="sxs-lookup"><span data-stu-id="da87c-142">Recreate schema-bound objects referencing the table and their permissions.</span></span>  
  
-   <span data-ttu-id="da87c-143">卸除暫存資料表。</span><span class="sxs-lookup"><span data-stu-id="da87c-143">Drop the temporary table.</span></span>  
  
 <span data-ttu-id="da87c-144">步驟 4 的指令碼應會更新，以反映所需的結構描述變更。</span><span class="sxs-lookup"><span data-stu-id="da87c-144">The script for step 4 should be updated to reflect the desired schema changes.</span></span> <span data-ttu-id="da87c-145">資料表的資料行中如有變更，也會視需要更新步驟 5 (從暫存資料表複製資料) 和 6 (重新建立預存程序) 的指令碼。</span><span class="sxs-lookup"><span data-stu-id="da87c-145">If there are any changes in the columns of the table, the scripts for steps 5 (copy data from temporary table) and 6 (recreate stored procedures) should be updated as necessary.</span></span>  
  
```powershell
# Prepare for schema changes by scripting out the table, as well as associated permissions
# Usage: prepare_schema_change.ps1 server_name db_name schema_name table_name  
# stop execution once an error occurs  
$ErrorActionPreference="Stop"  
  
if($args.Count -le 3)  
{  
   throw "Usage prepare_schema_change.ps1 server_name db_name schema_name table_name"  
}  
  
$servername = $args[0]  
$database = $args[1]  
$schema = $args[2]  
$object = $args[3]  
  
$object_heap = "$object$(Get-Random)"  
  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.SMO") | Out-Null  
  
$server =  New-Object ("Microsoft.SqlServer.Management.SMO.Server") ($servername)  
$scripter = New-Object ("Microsoft.SqlServer.Management.SMO.Scripter") ($server)  
  
## initialize table variable  
$tableUrn = $server.Databases[$database].Tables[$object, $schema]  
if($tableUrn.Count -eq 0)  
{  
   throw "Table or database not found"  
}  
  
## initialize scripting object  
$scriptingOptions = New-Object ("Microsoft.SqlServer.Management.SMO.ScriptingOptions")
$scriptingOptions.Permissions = $True  
$scriptingOptions.ScriptDrops = $True  
  
$scripter.Options = $scriptingOptions;  
  
Write-Host "(1) Scripting SELECT INTO $object_heap for table [$object] to 1_copy_to_heap_for_$schema`_$object.sql"  
Echo "SELECT * INTO $schema.$object_heap FROM $schema.$object WITH (SNAPSHOT)" | Out-File "1_copy_to_heap_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(2) Scripting DROP for procs schema-bound to [$object] 2_drop_procs_$schema`_$object.sql"  
## query referencing schema-bound objects  
$dt = $server.Databases[$database].ExecuteWithResults("select r.referencing_schema_name, r.referencing_entity_name  
from sys.dm_sql_referencing_entities ('$schema.$object', 'OBJECT') as r join sys.sql_modules m on r.referencing_id=m.object_id  
where r.is_caller_dependent = 0 and m.is_schema_bound=1;")  
  
## initialize out file  
Echo "" | Out-File "2_drop_procs_$schema`_$object.sql"  
## loop through schema-bound objects  
ForEach ($t In $dt.Tables)  
{    
   ForEach ($r In $t.Rows)  
   {    
      ## script object   
      $so =  $server.Databases[$database].StoredProcedures[$r[1], $r[0]]  
      $scripter.Script($so) | Out-File -Append "2_drop_procs_$schema`_$object.sql"  
   }  
}  
Write-Host "--done--"  
Write-Host ""  
Write-Host "(3) Scripting DROP table for [$object] to 3_drop_table_$schema`_$object.sql"
$scripter.Script($tableUrn) | Out-File "3_drop_table_$schema`_$object.sql";
Write-Host "--done--"  
Write-Host ""  
  
## now script creates  
$scriptingOptions.ScriptDrops = $False  
  
Write-Host "(4) Scripting CREATE table and permissions for [$object] to !please_edit_4_create_table_$schema`_$object.sql"  
Write-Host "***** rename this script to 4_create_table.sql after completing the updates to the schema"
$scripter.Script($tableUrn) | Out-File "!please_edit_4_create_table_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(5) Scripting INSERT INTO table from heap and UPDATE STATISTICS for [$object] to 5_copy_from_heap_$schema`_$object.sql"  
Write-Host "[update this script if columns are added to or removed from the table]"  
Echo "INSERT INTO [$schema].[$object] SELECT * FROM [$schema].[$object_heap]; UPDATE STATISTICS [$schema].[$object] WITH FULLSCAN, NORECOMPUTE" | Out-File "5_copy_from_heap_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(6) Scripting CREATE PROC and permissions for procedures schema-bound to [$object] to 6_create_procs_$schema`_$object.sql"  
Write-Host "[update the procedure definitions if columns are renamed or removed]"  
## initialize out file  
Echo "" | Out-File "6_create_procs_$schema`_$object.sql"  
## loop through schema-bound objects  
ForEach ($t In $dt.Tables)  
{    
   ForEach ($r In $t.Rows)  
   {    
      ## script the schema-bound object  
      $so =  $server.Databases[$database].StoredProcedures[$r[1], $r[0]]  
      ForEach($s In $scripter.Script($so))  
        {  
            Echo $s | Out-File -Append "6_create_procs_$schema`_$object.sql"  
            Echo "GO" | Out-File -Append "6_create_procs_$schema`_$object.sql"  
        }  
   }  
}  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(7) Scripting DROP $object_heap to 7_drop_heap_$schema`_$object.sql"  
Echo "DROP TABLE $schema.$object_heap" | Out-File "7_drop_heap_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
```  
  
 <span data-ttu-id="da87c-146">下列 PowerShell 指令碼會執行前述範例中所撰寫的結構描述變更指令碼。</span><span class="sxs-lookup"><span data-stu-id="da87c-146">The following PowerShell script executes the schema changes that were scripted in the previous sample.</span></span> <span data-ttu-id="da87c-147">此指令碼會採用資料表做為引數，並執行為該資料表與相關預存程序產生的結構描述變更指令碼。</span><span class="sxs-lookup"><span data-stu-id="da87c-147">This script takes as argument a table, and executes the schema change scripts that were generated for that table and the associated stored procedures.</span></span>  
  
 <span data-ttu-id="da87c-148">使用方式： execute_schema_change.ps1 *server_name \* \* db_name `schema_name` table_name*</span><span class="sxs-lookup"><span data-stu-id="da87c-148">Usage: execute_schema_change.ps1 *server_name\*\*db_name`schema_name`table_name*</span></span>  
  
```powershell
# stop execution once an error occurs  
$ErrorActionPreference="Stop"  
  
if($args.Count -le 3)  
{  
   throw "Usage execute_schema_change.ps1 server_name db_name schema_name table_name"  
}  
  
$servername = $args[0]  
$database = $args[1]  
$schema = $args[2]  
$object = $args[3]  
  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.SMO") | Out-Null  
  
$server =  New-Object ("Microsoft.SqlServer.Management.SMO.Server") ($servername)  
$database = $server.Databases[$database]  
$table = $database.Tables[$object, $schema]  
if($table.Count -eq 0)  
{  
   throw "Table or database not found"  
}  
  
$1 = Get-Item "1_copy_to_heap_$schema`_$object.sql"  
$2 = Get-Item "2_drop_procs_$schema`_$object.sql"  
$3 = Get-Item "3_drop_table_$schema`_$object.sql"  
$4 = Get-Item "4_create_table_$schema`_$object.sql"  
$5 = Get-Item "5_copy_from_heap_$schema`_$object.sql"  
$6 = Get-Item "6_create_procs_$schema`_$object.sql"  
$7 = Get-Item "7_drop_heap_$schema`_$object.sql"  
  
Write-Host "(1) Running SELECT INTO heap for table [$object] from 1_copy_to_heap_for_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $1.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(2) Running DROP for procs schema-bound from [$object] 2_drop_procs_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $2.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(3) Running DROP table for [$object] to 4_drop_table_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $3.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(4) Running CREATE table and permissions for [$object] from 4_create_table_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $4.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(5) Running INSERT INTO table from heap for [$object] and UPDATE STATISTICS from 5_copy_from_heap_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $5.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(6) Running CREATE PROC and permissions for procedures schema-bound to [$object] from 6_create_procs_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $6.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(7) Running DROP heap from 7_drop_heap_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $7.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
```  
  
## <a name="see-also"></a><span data-ttu-id="da87c-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da87c-149">See Also</span></span>  
 [<span data-ttu-id="da87c-150">記憶體最佳化資料表</span><span class="sxs-lookup"><span data-stu-id="da87c-150">Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
