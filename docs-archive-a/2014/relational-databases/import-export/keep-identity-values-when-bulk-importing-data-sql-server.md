---
title: 大量匯入資料時保留識別值 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- identity values [SQL Server], bulk imports
- data formats [SQL Server], identity values
- bulk importing [SQL Server], identity values
ms.assetid: 45894a3f-2d8a-4edd-9568-afa7d0d3061f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 07f6714f27f60afda91134034509ff439d92f071
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598377"
---
# <a name="keep-identity-values-when-bulk-importing-data-sql-server"></a><span data-ttu-id="750b3-102">大量匯入資料時保留識別值 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="750b3-102">Keep Identity Values When Bulk Importing Data (SQL Server)</span></span>
  <span data-ttu-id="750b3-103">包含識別值的資料檔案可以大量匯入的實例中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="750b3-103">Data files that contain identity values can be bulk imported into an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="750b3-104">根據預設，會忽略所匯入資料檔案中的識別欄位值， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會自動指定唯一值。</span><span class="sxs-lookup"><span data-stu-id="750b3-104">By default, the values for the identity column in the data file that is imported are ignored and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assigns unique values automatically.</span></span> <span data-ttu-id="750b3-105">唯一值的依據是資料表建立期間所指定的初始值及累加值。</span><span class="sxs-lookup"><span data-stu-id="750b3-105">The unique values are based on the seed and increment values that are specified during table creation.</span></span>  
  
 <span data-ttu-id="750b3-106">如果資料檔不包含資料表中識別碼資料行的值，請使用格式檔案指定在匯入資料時應略過資料表中的識別碼資料行。</span><span class="sxs-lookup"><span data-stu-id="750b3-106">If the data file does not contain values for the identifier column in the table, use a format file to specify that the identifier column in the table should be skipped when importing data.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="750b3-107">會自動為資料行指定唯一值。</span><span class="sxs-lookup"><span data-stu-id="750b3-107">assigns unique values for the column automatically.</span></span>  
  
 <span data-ttu-id="750b3-108">若要在將資料列大量匯入資料表時，不讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 指定識別值，請使用適當的 keep-identity 命令限定詞。</span><span class="sxs-lookup"><span data-stu-id="750b3-108">To prevent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from assigning identity values while bulk importing data rows into a table, use the appropriate keep-identity command qualifier.</span></span> <span data-ttu-id="750b3-109">當您指定 keep-identity 限定詞時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會使用資料檔案中的識別值。</span><span class="sxs-lookup"><span data-stu-id="750b3-109">When you specify a keep-identity qualifier, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses the identity values in the data file.</span></span> <span data-ttu-id="750b3-110">這些限定詞如下：</span><span class="sxs-lookup"><span data-stu-id="750b3-110">These qualifiers are as follows:</span></span>  
  
|<span data-ttu-id="750b3-111">Command</span><span class="sxs-lookup"><span data-stu-id="750b3-111">Command</span></span>|<span data-ttu-id="750b3-112">Keep-identity 限定詞</span><span class="sxs-lookup"><span data-stu-id="750b3-112">Keep-identity qualifier</span></span>|<span data-ttu-id="750b3-113">限定詞類型</span><span class="sxs-lookup"><span data-stu-id="750b3-113">Qualifier type</span></span>|  
|-------------|------------------------------|--------------------|  
|`bcp`|<span data-ttu-id="750b3-114">**-E**</span><span class="sxs-lookup"><span data-stu-id="750b3-114">**-E**</span></span>|<span data-ttu-id="750b3-115">Switch</span><span class="sxs-lookup"><span data-stu-id="750b3-115">Switch</span></span>|  
|<span data-ttu-id="750b3-116">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="750b3-116">BULK INSERT</span></span>|<span data-ttu-id="750b3-117">KEEPIDENTITY</span><span class="sxs-lookup"><span data-stu-id="750b3-117">KEEPIDENTITY</span></span>|<span data-ttu-id="750b3-118">引數</span><span class="sxs-lookup"><span data-stu-id="750b3-118">Argument</span></span>|  
|<span data-ttu-id="750b3-119">INSERT ...SELECT \* FROM OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="750b3-119">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>|<span data-ttu-id="750b3-120">KEEPIDENTITY</span><span class="sxs-lookup"><span data-stu-id="750b3-120">KEEPIDENTITY</span></span>|<span data-ttu-id="750b3-121">資料表提示</span><span class="sxs-lookup"><span data-stu-id="750b3-121">Table hint</span></span>|  
  
 <span data-ttu-id="750b3-122">如需詳細資訊，請參閱 [bcp 公用程式](../../tools/bcp-utility.md)、[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)、[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)、[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)、[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) 和[資料表提示 &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)。</span><span class="sxs-lookup"><span data-stu-id="750b3-122">For more information, see [bcp Utility](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql), [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql), [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql), and [Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="750b3-123">若要建立可用於多個資料表中或可在不參考任何資料表的情況下從應用程式進行呼叫的自動遞增數字，請參閱 [序號](../sequence-numbers/sequence-numbers.md)。</span><span class="sxs-lookup"><span data-stu-id="750b3-123">To create an automatically incrementing number that can be used in multiple tables or that can be called from applications without referencing any table, see [Sequence Numbers](../sequence-numbers/sequence-numbers.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="750b3-124">範例</span><span class="sxs-lookup"><span data-stu-id="750b3-124">Examples</span></span>  
 <span data-ttu-id="750b3-125">本主題中的範例會使用 INSERT 來大量匯入資料 .。。SELECT \* FROM OPENROWSET (BULK ... ) 並保留預設值。</span><span class="sxs-lookup"><span data-stu-id="750b3-125">The examples in this topic bulk import data using INSERT ... SELECT \* FROM OPENROWSET(BULK...) and keeping default values.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="750b3-126">範例資料表</span><span class="sxs-lookup"><span data-stu-id="750b3-126">Sample Table</span></span>  
 <span data-ttu-id="750b3-127">大量匯入資料的範例需要在 **dbo** 結構描述下的 **AdventureWorks** 範例資料庫中，建立一個名為 **myTestKeepNulls** 的資料表。</span><span class="sxs-lookup"><span data-stu-id="750b3-127">The bulk-import examples require that a table named **myTestKeepNulls** table be created in the **AdventureWorks** sample database under the **dbo** schema.</span></span> <span data-ttu-id="750b3-128">建立這個資料表。</span><span class="sxs-lookup"><span data-stu-id="750b3-128">To create this table.</span></span> <span data-ttu-id="750b3-129">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查詢編輯器中，執行：</span><span class="sxs-lookup"><span data-stu-id="750b3-129">in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
SELECT * INTO HumanResources.myDepartment   
   FROM HumanResources.Department  
      WHERE 1=0;  
GO  
SELECT * FROM HumanResources.myDepartment;  
```  
  
 <span data-ttu-id="750b3-130">`myDepartment` 所依據的 **Department** 資料表已將 IDENTITY_INSERT 設為 OFF。</span><span class="sxs-lookup"><span data-stu-id="750b3-130">The **Department** table on which `myDepartment` is based has IDENTITY_INSERT is set to OFF.</span></span> <span data-ttu-id="750b3-131">因此，若要將資料匯入至識別欄位，您必須指定 KEEPIDENTITY 或 **-E**。</span><span class="sxs-lookup"><span data-stu-id="750b3-131">Therefore, to import data into an identity column you must specify KEEPIDENTITY or **-E**.</span></span>  
  
### <a name="sample-data-file"></a><span data-ttu-id="750b3-132">範例資料檔</span><span class="sxs-lookup"><span data-stu-id="750b3-132">Sample Data File</span></span>  
 <span data-ttu-id="750b3-133">大量匯入範例中所使用的資料檔包含從 `HumanResources.Department` 資料表中大量匯出的原生格式資料。</span><span class="sxs-lookup"><span data-stu-id="750b3-133">The data file used in the bulk-import examples contains data bulk exported from the `HumanResources.Department` table in native format.</span></span> <span data-ttu-id="750b3-134">若要建立資料檔，請在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="750b3-134">To create the data file, at the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks.HumanResources.Department out myDepartment-n.Dat -n -T  
```  
  
### <a name="sample-format-file"></a><span data-ttu-id="750b3-135">範例格式檔案</span><span class="sxs-lookup"><span data-stu-id="750b3-135">Sample Format File</span></span>  
 <span data-ttu-id="750b3-136">大量匯入範例使用 XML 格式檔案 `myDepartment-f-x-n.Xml`，而它是使用原生資料格式。</span><span class="sxs-lookup"><span data-stu-id="750b3-136">This bulk-import examples use an XML format file, `myDepartment-f-x-n.Xml`, which uses native data formats.</span></span> <span data-ttu-id="750b3-137">這個範例使用 `bcp` 從 `HumanResources.Department` 資料庫的 `AdventureWorks` 資料表來產生這個格式檔案。</span><span class="sxs-lookup"><span data-stu-id="750b3-137">This example uses `bcp` to create to generate this format file from the `HumanResources.Department` table of the `AdventureWorks` database.</span></span> <span data-ttu-id="750b3-138">請在 Windows 命令提示字元之下，輸入：</span><span class="sxs-lookup"><span data-stu-id="750b3-138">At the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks.HumanResources.Department format nul -n -x -f myDepartment-f-n-x.Xml -T  
```  
  
 <span data-ttu-id="750b3-139">如需建立格式檔案的詳細資訊，請參閱[建立格式檔案 &#40;SQL Server&#41;](create-a-format-file-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="750b3-139">For more information about creating a format file, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
### <a name="a-using-bcp-and-keeping-identity-values"></a><span data-ttu-id="750b3-140">A.</span><span class="sxs-lookup"><span data-stu-id="750b3-140">A.</span></span> <span data-ttu-id="750b3-141">使用 bcp 並保留識別值</span><span class="sxs-lookup"><span data-stu-id="750b3-141">Using bcp and Keeping Identity Values</span></span>  
 <span data-ttu-id="750b3-142">下列範例示範如何在使用 `bcp` 大量匯入資料時保留識別值。</span><span class="sxs-lookup"><span data-stu-id="750b3-142">The following example demonstrates how to keep identity values when using `bcp` to bulk import data.</span></span> <span data-ttu-id="750b3-143">`bcp` 命令會使用格式檔案 `myDepartment-f-n-x.Xml`，並包含下列參數：</span><span class="sxs-lookup"><span data-stu-id="750b3-143">The `bcp` command uses the format file, `myDepartment-f-n-x.Xml`, and contains the following switches:</span></span>  
  
|<span data-ttu-id="750b3-144">限定詞</span><span class="sxs-lookup"><span data-stu-id="750b3-144">Qualifiers</span></span>|<span data-ttu-id="750b3-145">描述</span><span class="sxs-lookup"><span data-stu-id="750b3-145">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="750b3-146">**-E**</span><span class="sxs-lookup"><span data-stu-id="750b3-146">**-E**</span></span>|<span data-ttu-id="750b3-147">指定將資料檔案中的識別值用於識別欄位。</span><span class="sxs-lookup"><span data-stu-id="750b3-147">Specifies that identity value or values in the data file are to be used for the identity column.</span></span>|  
|<span data-ttu-id="750b3-148">**-T**</span><span class="sxs-lookup"><span data-stu-id="750b3-148">**-T**</span></span>|<span data-ttu-id="750b3-149">指定 `bcp` 公用程式 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用信任連接來連接到。</span><span class="sxs-lookup"><span data-stu-id="750b3-149">Specifies that the `bcp` utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection.</span></span>|  
  
 <span data-ttu-id="750b3-150">在 Windows 命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="750b3-150">At the Windows command prompt, enter.</span></span>  
  
```  
bcp AdventureWorks.HumanResources.myDepartment in C:\myDepartment-n.Dat -f C:\myDepartment-f-n-x.Xml -E -T  
  
```  
  
### <a name="b-using-bulk-insert-and-keeping-identity-values"></a><span data-ttu-id="750b3-151">B.</span><span class="sxs-lookup"><span data-stu-id="750b3-151">B.</span></span> <span data-ttu-id="750b3-152">使用 BULK INSERT 並保留識別值</span><span class="sxs-lookup"><span data-stu-id="750b3-152">Using BULK INSERT and Keeping Identity Values</span></span>  
 <span data-ttu-id="750b3-153">下列範例使用 BULK INSERT 將資料從 `myDepartment-c.Dat` 檔案大量匯入 `AdventureWorks.HumanResources.myDepartment` 資料表。</span><span class="sxs-lookup"><span data-stu-id="750b3-153">The following example uses BULK INSERT to bulk import data from the `myDepartment-c.Dat` file into the `AdventureWorks.HumanResources.myDepartment` table.</span></span> <span data-ttu-id="750b3-154">該陳述式使用 `myDepartment-f-n-x.Xml` 格式檔案，並包含 KEEPIDENTITY 選項，以確保資料檔案中的任何識別值都會保留下來。</span><span class="sxs-lookup"><span data-stu-id="750b3-154">The statement uses the `myDepartment-f-n-x.Xml` format file and includes the KEEPIDENTITY option to ensure that any identity values in the data file are retained.</span></span>  
  
 <span data-ttu-id="750b3-155">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查詢編輯器中，執行：</span><span class="sxs-lookup"><span data-stu-id="750b3-155">In the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
DELETE HumanResources.myDepartment;  
GO  
BULK INSERT HumanResources.myDepartment  
   FROM 'C:\myDepartment-n.Dat'  
   WITH (  
      KEEPIDENTITY,  
      FORMATFILE='C:\myDepartment-f-n-x.Xml'  
   );  
GO  
SELECT * FROM HumanResources.myDepartment;  
  
```  
  
### <a name="c-using-openrowset-and-keeping-identity-values"></a><span data-ttu-id="750b3-156">C.</span><span class="sxs-lookup"><span data-stu-id="750b3-156">C.</span></span> <span data-ttu-id="750b3-157">使用 OPENROWSET 並保留識別值</span><span class="sxs-lookup"><span data-stu-id="750b3-157">Using OPENROWSET and Keeping Identity Values</span></span>  
 <span data-ttu-id="750b3-158">下列範例使用 OPENROWSET 大量資料列集提供者將資料從 `myDepartment-c.Dat` 檔案大量匯入 `AdventureWorks.HumanResources.myDepartment` 資料表。</span><span class="sxs-lookup"><span data-stu-id="750b3-158">The following example uses the OPENROWSET bulk rowset provider to bulk import data from the `myDepartment-c.Dat` file into the `AdventureWorks.HumanResources.myDepartment` table.</span></span> <span data-ttu-id="750b3-159">該陳述式使用 `myDepartment-f-n-x.Xml` 格式檔案，並包含 KEEPIDENTITY 提示，以確保資料檔中的任何識別值都會保留下來。</span><span class="sxs-lookup"><span data-stu-id="750b3-159">The statement uses the `myDepartment-f-n-x.Xml` format file and includes the KEEPIDENTITY hint to ensure that any identity values in the data file are retained.</span></span>  
  
 <span data-ttu-id="750b3-160">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查詢編輯器中，執行：</span><span class="sxs-lookup"><span data-stu-id="750b3-160">In the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
DELETE HumanResources.myDepartment;  
GO  
  
INSERT INTO HumanResources.myDepartment  
   with (KEEPIDENTITY)  
   (DepartmentID, Name, GroupName, ModifiedDate)  
   SELECT *  
      FROM  OPENROWSET(BULK 'C:\myDepartment-n.Dat',  
      FORMATFILE='C:\myDepartment-f-n-x.Xml') as t1;  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="750b3-161">相關工作</span><span class="sxs-lookup"><span data-stu-id="750b3-161">Related Tasks</span></span>  
  
-   [<span data-ttu-id="750b3-162">大量匯入期間保留 Null 或使用預設值 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="750b3-162">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [<span data-ttu-id="750b3-163">準備大量匯出或匯入的資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="750b3-163">Prepare Data for Bulk Export or Import &#40;SQL Server&#41;</span></span>](prepare-data-for-bulk-export-or-import-sql-server.md)  
  
 <span data-ttu-id="750b3-164">**若要使用格式檔案**</span><span class="sxs-lookup"><span data-stu-id="750b3-164">**To use a format file**</span></span>  
  
-   [<span data-ttu-id="750b3-165">建立格式檔案 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="750b3-165">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="750b3-166">使用格式檔案大量匯入資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="750b3-166">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="750b3-167">使用格式檔案將資料表資料行對應至資料檔案欄位 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="750b3-167">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
-   [<span data-ttu-id="750b3-168">使用格式檔案略過資料欄位 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="750b3-168">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="750b3-169">使用格式檔案略過資料表資料行 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="750b3-169">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 <span data-ttu-id="750b3-170">**若要使用大量匯入或大量匯出的資料格式**</span><span class="sxs-lookup"><span data-stu-id="750b3-170">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="750b3-171">從舊版 SQL Server 匯入原生與字元格式資料</span><span class="sxs-lookup"><span data-stu-id="750b3-171">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="750b3-172">使用字元格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="750b3-172">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="750b3-173">使用原生格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="750b3-173">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="750b3-174">使用 Unicode 字元格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="750b3-174">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="750b3-175">使用 Unicode 原生格式匯入或匯出資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="750b3-175">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 <span data-ttu-id="750b3-176">**若要在使用 bcp 時指定相容性的資料格式**</span><span class="sxs-lookup"><span data-stu-id="750b3-176">**To specify data formats for compatibility when using bcp**</span></span>  
  
1.  [<span data-ttu-id="750b3-177">指定欄位與資料列結束字元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="750b3-177">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
2.  [<span data-ttu-id="750b3-178">使用 bcp 指定資料檔的前置長度 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="750b3-178">Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;</span></span>](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
3.  [<span data-ttu-id="750b3-179">使用 bcp 時指定檔案儲存類型 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="750b3-179">Specify File Storage Type by Using bcp &#40;SQL Server&#41;</span></span>](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="750b3-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="750b3-180">See Also</span></span>  
 <span data-ttu-id="750b3-181">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="750b3-181">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="750b3-182">[bcp 公用程式](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="750b3-182">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="750b3-183">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="750b3-183">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="750b3-184">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="750b3-184">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 [<span data-ttu-id="750b3-185">資料表提示 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="750b3-185">Table Hints &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/hints-transact-sql-table)  
  
  
