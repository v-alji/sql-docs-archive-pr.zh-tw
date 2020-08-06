---
title: 大量匯入期間保留 Null 或使用預設值 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], null values
- bulk importing [SQL Server], default values
- data formats [SQL Server], null values
- bulk rowset providers [SQL Server]
- bcp utility [SQL Server], null values
- BULK INSERT statement
- default values
- OPENROWSET function, bulk importing
- data formats [SQL Server], default values
ms.assetid: 6b91d762-337b-4345-a159-88abb3e64a81
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 856aa12f6ad5e5094324e0df65941bc63d611451
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708413"
---
# <a name="keep-nulls-or-use-default-values-during-bulk-import-sql-server"></a><span data-ttu-id="3b27c-102">大量匯入期間保留 Null 或使用預設值 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3b27c-102">Keep Nulls or Use Default Values During Bulk Import (SQL Server)</span></span>
  <span data-ttu-id="3b27c-103">根據預設，當資料匯入資料表時， **bcp** 命令和 BULK INSERT 陳述式會查看資料表中的資料行是否已定義預設值。</span><span class="sxs-lookup"><span data-stu-id="3b27c-103">By default, when data is imported into a table, the **bcp** command and BULK INSERT statement observe any defaults that are defined for the columns in the table.</span></span> <span data-ttu-id="3b27c-104">例如，若資料檔中有一個 Null 值欄位，將會以載入該資料行的預設值來取代。</span><span class="sxs-lookup"><span data-stu-id="3b27c-104">For example, if there is a null field in a data file, the default value for the column is loaded instead.</span></span> <span data-ttu-id="3b27c-105">**bcp** 命令和 BULK INSERT 陳述式都可讓您指定保留 Null 值。</span><span class="sxs-lookup"><span data-stu-id="3b27c-105">The **bcp** command and BULK INSERT statement both allow you to specify that nulls values be retained.</span></span>  
  
 <span data-ttu-id="3b27c-106">相對地，一般的 INSERT 陳述式會保留 Null 值，而不會插入預設值。</span><span class="sxs-lookup"><span data-stu-id="3b27c-106">In contrast, a regular INSERT statement retains the null value instead of inserting a default value.</span></span> <span data-ttu-id="3b27c-107">INSERT ...SELECT \* FROM OPENROWSET(BULK...) 陳述式所提供的基本行為與一般 INSERT 陳述式相同，但它還支援用於插入預設值的資料表提示。</span><span class="sxs-lookup"><span data-stu-id="3b27c-107">The INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement provides the same basic behavior as regular INSERT but additionally supports a table hint for inserting the default values.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3b27c-108">如需略過資料表資料行的範例格式檔案，請參閱[使用格式檔案略過資料表資料行 &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3b27c-108">For sample format files that skip a table column, see [Use a Format File to Skip a Table Column &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md).</span></span>  
  
## <a name="sample-table-and-data-file"></a><span data-ttu-id="3b27c-109">範例資料表與資料檔</span><span class="sxs-lookup"><span data-stu-id="3b27c-109">Sample Table and Data File</span></span>  
 <span data-ttu-id="3b27c-110">若要執行此主題中的範例，您必須建立範例資料表與資料檔。</span><span class="sxs-lookup"><span data-stu-id="3b27c-110">To run the examples in this topic, you need to create a sample table and data file.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="3b27c-111">範例資料表</span><span class="sxs-lookup"><span data-stu-id="3b27c-111">Sample Table</span></span>  
 <span data-ttu-id="3b27c-112">在此範例中，必須將名為 **MyTestDefaultCol2** 的資料表，建立在 **AdventureWorks** 範例資料庫中的 **dbo** 結構描述下。</span><span class="sxs-lookup"><span data-stu-id="3b27c-112">The examples require that a table named **MyTestDefaultCol2** be created in the **AdventureWorks** sample database under the **dbo** schema.</span></span> <span data-ttu-id="3b27c-113">若要建立此資料表，請在 [ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查詢編輯器] 中執行：</span><span class="sxs-lookup"><span data-stu-id="3b27c-113">To create this table, in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE MyTestDefaultCol2   
(Col1 smallint,  
Col2 nvarchar(50) DEFAULT 'Default value of Col2',  
Col3 nvarchar(50)   
);  
GO  
  
```  
  
 <span data-ttu-id="3b27c-114">請注意，第二個資料表資料行 `Col2` 中有預設值。</span><span class="sxs-lookup"><span data-stu-id="3b27c-114">Notice that the second table column, `Col2`, has a default value.</span></span>  
  
### <a name="sample-format-file"></a><span data-ttu-id="3b27c-115">範例格式檔案</span><span class="sxs-lookup"><span data-stu-id="3b27c-115">Sample Format File</span></span>  
 <span data-ttu-id="3b27c-116">有些大量匯入範例會使用非 XML 格式檔案 `MyTestDefaultCol2-f-c.Fmt`，此檔案與 `MyTestDefaultCol2` 資料表完全對應。</span><span class="sxs-lookup"><span data-stu-id="3b27c-116">Some of the bulk-import examples use a non-XML format file, `MyTestDefaultCol2-f-c.Fmt` that corresponds exactly to the `MyTestDefaultCol2` table.</span></span> <span data-ttu-id="3b27c-117">若要建立此格式檔案，請在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 命令提示字元下，輸入：</span><span class="sxs-lookup"><span data-stu-id="3b27c-117">To create this format file, at the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks..MyTestDefaultCol2 format nul -c -f C:\MyTestDefaultCol2-f-c.Fmt -t, -r\n -T  
  
```  
  
 <span data-ttu-id="3b27c-118">如需建立格式檔案的詳細資訊，請參閱 [建立格式檔案 &#40;SQL Server&#41;](create-a-format-file-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3b27c-118">For more information about creating format files, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
### <a name="sample-data-file"></a><span data-ttu-id="3b27c-119">範例資料檔</span><span class="sxs-lookup"><span data-stu-id="3b27c-119">Sample Data File</span></span>  
 <span data-ttu-id="3b27c-120">此範例將使用範例資料檔 `MyTestEmptyField2-c.Dat`，此檔案在第二個欄位中不含任何值。</span><span class="sxs-lookup"><span data-stu-id="3b27c-120">The example uses a sample data file, `MyTestEmptyField2-c.Dat`, that contains no values in the second field.</span></span> <span data-ttu-id="3b27c-121">`MyTestEmptyField2-c.Dat` 資料檔含有下列記錄。</span><span class="sxs-lookup"><span data-stu-id="3b27c-121">The `MyTestEmptyField2-c.Dat` data file contains the following records.</span></span>  
  
```  
1,,DataField3  
2,,DataField3  
  
```  
  
## <a name="keeping-null-values-with-bcp-or-bulk-insert"></a><span data-ttu-id="3b27c-122">使用 bcp 或 BULK INSERT 保留 Null 值</span><span class="sxs-lookup"><span data-stu-id="3b27c-122">Keeping Null Values with bcp or BULK INSERT</span></span>  
 <span data-ttu-id="3b27c-123">下列限定詞 (qualifier) 可指定資料檔中的空白欄位，在大量匯入作業期間保留其 Null 值，而不要繼承資料表資料行的預設值 (若有的話)。</span><span class="sxs-lookup"><span data-stu-id="3b27c-123">The following qualifiers specify that an empty field in the data file retains its null value during the bulk-import operation, rather than inheriting a default value (if any) for the table columns.</span></span>  
  
|<span data-ttu-id="3b27c-124">Command</span><span class="sxs-lookup"><span data-stu-id="3b27c-124">Command</span></span>|<span data-ttu-id="3b27c-125">Qualifier</span><span class="sxs-lookup"><span data-stu-id="3b27c-125">Qualifier</span></span>|<span data-ttu-id="3b27c-126">限定詞類型</span><span class="sxs-lookup"><span data-stu-id="3b27c-126">Qualifier type</span></span>|  
|-------------|---------------|--------------------|  
|<span data-ttu-id="3b27c-127">**bcp**</span><span class="sxs-lookup"><span data-stu-id="3b27c-127">**bcp**</span></span>|`-k`|<span data-ttu-id="3b27c-128">Switch</span><span class="sxs-lookup"><span data-stu-id="3b27c-128">Switch</span></span>|  
|<span data-ttu-id="3b27c-129">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="3b27c-129">BULK INSERT</span></span>|<span data-ttu-id="3b27c-130">KEEPNullS<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3b27c-130">KEEPNULLS<sup>1</sup></span></span>|<span data-ttu-id="3b27c-131">引數</span><span class="sxs-lookup"><span data-stu-id="3b27c-131">Argument</span></span>|  
  
 <span data-ttu-id="3b27c-132"><sup>1</sup>針對 BULK INSERT，如果無法使用預設值，則必須將資料表資料行定義為允許 null 值。</span><span class="sxs-lookup"><span data-stu-id="3b27c-132"><sup>1</sup> For BULK INSERT, if default values are not available, the table column must be defined to allow null values.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3b27c-133">這些限定詞會使這些大量匯入命令不再檢查資料表上有無 DEFAULT 定義，</span><span class="sxs-lookup"><span data-stu-id="3b27c-133">These qualifiers disable checking of DEFAULT definitions on a table by these bulk-import commands.</span></span> <span data-ttu-id="3b27c-134">但對任何並行 INSERT 陳述式而言，DEFAULT 定義是可預期的。</span><span class="sxs-lookup"><span data-stu-id="3b27c-134">However, for any concurrent INSERT statements, DEFAULT definitions are expected.</span></span>  
  
 <span data-ttu-id="3b27c-135">如需詳細資訊，請參閱 [bcp 公用程式](../../tools/bcp-utility.md)和 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3b27c-135">For more information, see [bcp Utility](../../tools/bcp-utility.md) and [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="3b27c-136">範例</span><span class="sxs-lookup"><span data-stu-id="3b27c-136">Examples</span></span>  
 <span data-ttu-id="3b27c-137">本節中的範例使用 **bcp** 或 BULK INSERT 進行大量匯入，並保留 Null 值。</span><span class="sxs-lookup"><span data-stu-id="3b27c-137">The examples in this section bulk import using **bcp** or BULK INSERT and keep null values.</span></span>  
  
 <span data-ttu-id="3b27c-138">第二個資料表資料行 **Col2** 有預設值。</span><span class="sxs-lookup"><span data-stu-id="3b27c-138">The second table column, **Col2**, has a default value.</span></span> <span data-ttu-id="3b27c-139">資料檔的對應欄位包含空白字串。</span><span class="sxs-lookup"><span data-stu-id="3b27c-139">The corresponding field of the data file contains an empty string.</span></span> <span data-ttu-id="3b27c-140">依預設，若使用 **bcp** 或 BULK INSERT 將資料由此資料檔匯入 **MyTestDefaultCol2** 資料表中，則會插入預設值 **Col2**，進而產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="3b27c-140">By default, when **bcp** or BULK INSERT is used to import data from this data file into the **MyTestDefaultCol2** table, the default value of **Col2** is inserted, producing the following result:</span></span>  
  
||||  
|-|-|-|  
|`1`|`Default value of Col2`|`DataField3`|  
|`2`|`Default value of Col2`|`DataField3`|  
  
 <span data-ttu-id="3b27c-141">若要插入 " `NULL` " 而非 " `Default value of Col2` "，您必須使用 `-k` switch 或 KEEPNull 選項，如下列**bcp**和 BULK INSERT 範例所示。</span><span class="sxs-lookup"><span data-stu-id="3b27c-141">To insert "`NULL`" instead of "`Default value of Col2`", you need to use the `-k` switch or KEEPNULL option, as demonstrated in the following **bcp** and BULK INSERT examples.</span></span>  
  
#### <a name="using-bcp-and-keeping-null-values"></a><span data-ttu-id="3b27c-142">使用 bcp 並保留 Null 值</span><span class="sxs-lookup"><span data-stu-id="3b27c-142">Using bcp and Keeping Null Values</span></span>  
 <span data-ttu-id="3b27c-143">下列範例示範如何使用 **bcp** 命令保留 Null 值。</span><span class="sxs-lookup"><span data-stu-id="3b27c-143">The following example demonstrates how to keep null values in a **bcp** command.</span></span> <span data-ttu-id="3b27c-144">**Bcp**命令包含下列參數：</span><span class="sxs-lookup"><span data-stu-id="3b27c-144">The **bcp** command contains the following switches:</span></span>  
  
|<span data-ttu-id="3b27c-145">Switch</span><span class="sxs-lookup"><span data-stu-id="3b27c-145">Switch</span></span>|<span data-ttu-id="3b27c-146">描述</span><span class="sxs-lookup"><span data-stu-id="3b27c-146">Description</span></span>|  
|------------|-----------------|  
|`-f`|<span data-ttu-id="3b27c-147">指定命令將使用格式檔案。</span><span class="sxs-lookup"><span data-stu-id="3b27c-147">Specifies that the command is using a format file..</span></span>|  
|`-k`|<span data-ttu-id="3b27c-148">指定空白資料行在作業過程中應保持 Null 值，而非保有插入之資料行的任何預設值。</span><span class="sxs-lookup"><span data-stu-id="3b27c-148">Specifies that empty columns should retain a null value during the operation, rather than have any default values for the columns inserted.</span></span>|  
|`-T`|<span data-ttu-id="3b27c-149">指定以信任連接將 bcp 公用程式連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3b27c-149">Specifies that the bcp utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection.</span></span>|  
  
 <span data-ttu-id="3b27c-150">在 Windows 命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="3b27c-150">At the Windows command prompt, enter.</span></span>  
  
```  
bcp AdventureWorks..MyTestDefaultCol2 in C:\MyTestEmptyField2-c.Dat -f C:\MyTestDefaultCol2-f-c.Fmt -k -T  
  
```  
  
#### <a name="using-bulk-insert-and-keeping-null-values"></a><span data-ttu-id="3b27c-151">使用 BULK INSERT 並保留 Null 值</span><span class="sxs-lookup"><span data-stu-id="3b27c-151">Using BULK INSERT and Keeping Null Values</span></span>  
 <span data-ttu-id="3b27c-152">以下範例將示範如何在 BULK INSERT 陳述式中使用 KEEPNULLS 選項。</span><span class="sxs-lookup"><span data-stu-id="3b27c-152">The following example demonstrates how to use the KEEPNULLS option in a BULK INSERT statement.</span></span> <span data-ttu-id="3b27c-153">從查詢工具 (例如 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查詢編輯器) 執行：</span><span class="sxs-lookup"><span data-stu-id="3b27c-153">From a query tool, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT MyTestDefaultCol2  
   FROM 'C:\MyTestEmptyField2-c.Dat'  
   WITH (  
      DATAFILETYPE = 'char',  
      FIELDTERMINATOR = ',',  
      KEEPNULLS  
   );  
GO  
  
```  
  
## <a name="keeping-default-values-with-insert--select--from-openrowsetbulk"></a><span data-ttu-id="3b27c-154">保留預設值與 INSERT .。。SELECT \* FROM OPENROWSET (BULK ... ) </span><span class="sxs-lookup"><span data-stu-id="3b27c-154">Keeping Default Values with INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>  
 <span data-ttu-id="3b27c-155">根據預設，在大量載入作業中未指定的任何資料行都會設定為 Null，方法是使用 INSERT .。。SELECT \* FROM OPENROWSET (BULK ... ) 。不過，如果有任何) ，則您可以將資料檔中的空白欄位指定為對應的資料表資料行，使用預設值 (。</span><span class="sxs-lookup"><span data-stu-id="3b27c-155">By default, any columns that are not specified in the bulk-load operation are set to NULL by INSERT ... SELECT \* FROM OPENROWSET(BULK...). However, you can specify that for an empty field in the data file, the corresponding table column uses its default value (if any).</span></span> <span data-ttu-id="3b27c-156">若要使用預設值，請指定下列資料表提示：</span><span class="sxs-lookup"><span data-stu-id="3b27c-156">To use default values, specify the following table hint:</span></span>  
  
|<span data-ttu-id="3b27c-157">Command</span><span class="sxs-lookup"><span data-stu-id="3b27c-157">Command</span></span>|<span data-ttu-id="3b27c-158">Qualifier</span><span class="sxs-lookup"><span data-stu-id="3b27c-158">Qualifier</span></span>|<span data-ttu-id="3b27c-159">限定詞類型</span><span class="sxs-lookup"><span data-stu-id="3b27c-159">Qualifier Type</span></span>|  
|-------------|---------------|--------------------|  
|<span data-ttu-id="3b27c-160">INSERT ...SELECT \* FROM OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="3b27c-160">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>|<span data-ttu-id="3b27c-161">WITH(KEEPDEFAULTS)</span><span class="sxs-lookup"><span data-stu-id="3b27c-161">WITH(KEEPDEFAULTS)</span></span>|<span data-ttu-id="3b27c-162">資料表提示</span><span class="sxs-lookup"><span data-stu-id="3b27c-162">Table hint</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="3b27c-163">如需詳細資訊，請參閱[INSERT &#40;transact-sql&#41;](/sql/t-sql/statements/insert-transact-sql)、 [SELECT &#40;Transact-sql&#41;](/sql/t-sql/queries/select-transact-sql)、 [OPENROWSET &#40;transact-sql&#41;](/sql/t-sql/functions/openrowset-transact-sql)和[Table 提示 &#40;transact-sql&#41;](/sql/t-sql/queries/hints-transact-sql-table)</span><span class="sxs-lookup"><span data-stu-id="3b27c-163">for more information, see [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql), [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql), [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql), and [Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)</span></span>  
  
### <a name="examples"></a><span data-ttu-id="3b27c-164">範例</span><span class="sxs-lookup"><span data-stu-id="3b27c-164">Examples</span></span>  
 <span data-ttu-id="3b27c-165">下列插入 .。。SELECT \* FROM OPENROWSET (BULK ... ) 範例會大量匯入資料並保留預設值。</span><span class="sxs-lookup"><span data-stu-id="3b27c-165">The following INSERT ... SELECT \* FROM OPENROWSET(BULK...) example bulk imports data and keeps the default values.</span></span>  
  
 <span data-ttu-id="3b27c-166">若要執行範例，您必須建立 **MyTestDefaultCol2** 範例資料表與 `MyTestEmptyField2-c.Dat` 資料檔，並使用格式檔案 `MyTestDefaultCol2-f-c.Fmt`。</span><span class="sxs-lookup"><span data-stu-id="3b27c-166">To run the examples, you need to create the **MyTestDefaultCol2** sample table, the `MyTestEmptyField2-c.Dat` data file, and use a format file, `MyTestDefaultCol2-f-c.Fmt`.</span></span> <span data-ttu-id="3b27c-167">如需建立這些範例的詳細資訊，請參閱本主題稍早的「範例資料表與資料檔」。</span><span class="sxs-lookup"><span data-stu-id="3b27c-167">For information on creating these samples, see "Sample Table and Data File," earlier in this topic.</span></span>  
  
 <span data-ttu-id="3b27c-168">第二個資料表資料行 **Col2** 有預設值。</span><span class="sxs-lookup"><span data-stu-id="3b27c-168">The second table column, **Col2**, has a default value.</span></span> <span data-ttu-id="3b27c-169">資料檔的對應欄位包含空白字串。</span><span class="sxs-lookup"><span data-stu-id="3b27c-169">The corresponding field of the data file contains an empty string.</span></span> <span data-ttu-id="3b27c-170">當 INSERT .。。SELECT \* FROM OPENROWSET (BULK ... ) 將此資料檔的欄位匯入**MyTestDefaultCol2**資料表中，根據預設，Null 會插入至**Col2** ，而不是預設值。</span><span class="sxs-lookup"><span data-stu-id="3b27c-170">When INSERT ... SELECT \* FROM OPENROWSET(BULK...) import the fields of this data file into the **MyTestDefaultCol2** table, by default, NULL is inserted into **Col2** instead of the default value.</span></span> <span data-ttu-id="3b27c-171">此預設行為會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="3b27c-171">This default behavior produces the following result:</span></span>  
  
||||  
|-|-|-|  
|`1`|`NULL`|`DataField3`|  
|`2`|`NULL`|`DataField3`|  
  
 <span data-ttu-id="3b27c-172">若要插入預設值 "`Default value of Col2`" 而非 "`NULL`"，您必須使用 KEEPDEFAULTS 資料表提示，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="3b27c-172">To insert the default value, "`Default value of Col2`", instead of "`NULL`", you need to use KEEPDEFAULTS table hint, as demonstrated in the following example.</span></span> <span data-ttu-id="3b27c-173">從查詢工具 (例如 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查詢編輯器) 執行：</span><span class="sxs-lookup"><span data-stu-id="3b27c-173">From a query tool, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
INSERT INTO MyTestDefaultCol2  
    WITH (KEEPDEFAULTS)  
    SELECT *  
      FROM OPENROWSET(BULK  'C:\MyTestEmptyField2-c.Dat',  
      FORMATFILE='C:\MyTestDefaultCol2-f-c.Fmt'       
      ) as t1 ;  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="3b27c-174">相關工作</span><span class="sxs-lookup"><span data-stu-id="3b27c-174">Related Tasks</span></span>  
  
-   [<span data-ttu-id="3b27c-175">大量匯入資料時保留識別值 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3b27c-175">Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;</span></span>](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [<span data-ttu-id="3b27c-176">準備大量匯出或匯入的資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3b27c-176">Prepare Data for Bulk Export or Import &#40;SQL Server&#41;</span></span>](prepare-data-for-bulk-export-or-import-sql-server.md)  
  
 <span data-ttu-id="3b27c-177">**若要使用格式檔案**</span><span class="sxs-lookup"><span data-stu-id="3b27c-177">**To use a format file**</span></span>  
  
-   [<span data-ttu-id="3b27c-178">建立格式檔案 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3b27c-178">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="3b27c-179">使用格式檔案大量匯入資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3b27c-179">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="3b27c-180">使用格式檔案將資料表資料行對應至資料檔案欄位 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3b27c-180">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
-   [<span data-ttu-id="3b27c-181">使用格式檔案略過資料欄位 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3b27c-181">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="3b27c-182">使用格式檔案略過資料表資料行 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3b27c-182">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 <span data-ttu-id="3b27c-183">**若要使用大量匯入或大量匯出的資料格式**</span><span class="sxs-lookup"><span data-stu-id="3b27c-183">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="3b27c-184">從舊版 SQL Server 匯入原生與字元格式資料</span><span class="sxs-lookup"><span data-stu-id="3b27c-184">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="3b27c-185">使用字元格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3b27c-185">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="3b27c-186">使用原生格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3b27c-186">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="3b27c-187">使用 Unicode 字元格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3b27c-187">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="3b27c-188">使用 Unicode 原生格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3b27c-188">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 <span data-ttu-id="3b27c-189">**若要在使用 bcp 時指定相容性的資料格式**</span><span class="sxs-lookup"><span data-stu-id="3b27c-189">**To specify data formats for compatibility when using bcp**</span></span>  
  
-   [<span data-ttu-id="3b27c-190">指定欄位與資料列結束字元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3b27c-190">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
-   [<span data-ttu-id="3b27c-191">使用 bcp 指定資料檔的前置長度 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3b27c-191">Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;</span></span>](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
-   [<span data-ttu-id="3b27c-192">使用 bcp 時指定檔案儲存類型 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3b27c-192">Specify File Storage Type by Using bcp &#40;SQL Server&#41;</span></span>](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="3b27c-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b27c-193">See Also</span></span>  
 <span data-ttu-id="3b27c-194">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3b27c-194">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="3b27c-195">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3b27c-195">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="3b27c-196">[bcp 公用程式](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="3b27c-196">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="3b27c-197">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3b27c-197">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 [<span data-ttu-id="3b27c-198">資料表提示 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3b27c-198">Table Hints &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/hints-transact-sql-table)  
  
  
