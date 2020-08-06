---
title: Hello World 範例 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: fed6c358-f5ee-4d4c-9ad6-089778383ba7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0d5616c1d4ef6428a011c8e36be3757931039c9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709865"
---
# <a name="hello-world-sample"></a><span data-ttu-id="587d9-102">Hello World 範例</span><span class="sxs-lookup"><span data-stu-id="587d9-102">Hello World Sample</span></span>
  <span data-ttu-id="587d9-103">這個 Hello World 範例會示範建立、部署和測試以簡單 Common Language Runtime (CLR) 整合為基礎的預存程序過程中所涉及的基本作業。</span><span class="sxs-lookup"><span data-stu-id="587d9-103">The Hello World sample demonstrates the basic operations that are involved in creating, deploying, and testing a simple common language runtime (CLR) integration-based stored procedure.</span></span> <span data-ttu-id="587d9-104">此範例還示範如何透過由預存程序動態建構及傳回至呼叫端的記錄來傳回資料。</span><span class="sxs-lookup"><span data-stu-id="587d9-104">This sample also demonstrates how to return data through a record, which is dynamically constructed by the stored procedure and returned to the caller.</span></span>  
  
 <span data-ttu-id="587d9-105">預存程式會傳回 `HelloWorld` 字串 "Hello world！"</span><span class="sxs-lookup"><span data-stu-id="587d9-105">The `HelloWorld` stored procedure returns the string "Hello world!"</span></span> <span data-ttu-id="587d9-106">在包含一個資料列的結果集中。</span><span class="sxs-lookup"><span data-stu-id="587d9-106">in a result set consisting of one row.</span></span> <span data-ttu-id="587d9-107">這個範例會說明[SqlMetaData](https://go.microsoft.com/fwlink/?LinkID=193572)、 [SqlDataRecord](https://go.microsoft.com/fwlink/?LinkID=193573)和[microsoft](https://go.microsoft.com/fwlink/?LinkID=193571)的類別的一些用途，如下所示：. sql server。</span><span class="sxs-lookup"><span data-stu-id="587d9-107">This example illustrates some uses for the classes [Microsoft.SqlServer.Server.SqlMetaData](https://go.microsoft.com/fwlink/?LinkID=193572), [Microsoft.SqlServer.Server.SqlDataRecord](https://go.microsoft.com/fwlink/?LinkID=193573) and [Microsoft.SqlServer.Server.Pipe](https://go.microsoft.com/fwlink/?LinkID=193571).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="587d9-108">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="587d9-108">Prerequisites</span></span>  
 <span data-ttu-id="587d9-109">若要建立並執行這個專案，您必須安裝下列軟體：</span><span class="sxs-lookup"><span data-stu-id="587d9-109">To create and run this project the following the following software must be installed:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="587d9-110">或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express。</span><span class="sxs-lookup"><span data-stu-id="587d9-110">or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.</span></span> <span data-ttu-id="587d9-111">您可以從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express 文件集和範例[網站](https://www.microsoft.com/sql-server/sql-server-editions-express)免費取得 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express</span><span class="sxs-lookup"><span data-stu-id="587d9-111">You can obtain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express free of charge from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express Documentation and Samples [Web site](https://www.microsoft.com/sql-server/sql-server-editions-express)</span></span>  
  
-   <span data-ttu-id="587d9-112">您可以從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 開發人員[網站](https://go.microsoft.com/fwlink/?linkid=62796)取得 AdventureWorks 資料庫</span><span class="sxs-lookup"><span data-stu-id="587d9-112">The AdventureWorks database that is available at the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Developer [Web site](https://go.microsoft.com/fwlink/?linkid=62796)</span></span>  
  
-   <span data-ttu-id="587d9-113">.NET Framework SDK 2.0 或更新版本或是 Microsoft Visual Studio 2005 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="587d9-113">.NET Framework SDK 2.0 or later or Microsoft Visual Studio 2005 or later.</span></span> <span data-ttu-id="587d9-114">您可以免費取得 .NET Framework SDK。</span><span class="sxs-lookup"><span data-stu-id="587d9-114">You can obtain .NET Framework SDK free of charge.</span></span>  
  
-   <span data-ttu-id="587d9-115">此外，您也必須符合下列條件：</span><span class="sxs-lookup"><span data-stu-id="587d9-115">In addition, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="587d9-116">您所使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體必須啟用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="587d9-116">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using must have CLR integration enabled.</span></span>  
  
-   <span data-ttu-id="587d9-117">若要啟用 CLR 整合，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="587d9-117">In order to enable CLR integration, perform the following steps:</span></span>  
  
    #### <a name="enabling-clr-integration"></a><span data-ttu-id="587d9-118">啟用 CLR 整合</span><span class="sxs-lookup"><span data-stu-id="587d9-118">Enabling CLR Integration</span></span>  
  
    -   <span data-ttu-id="587d9-119">執行下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令：</span><span class="sxs-lookup"><span data-stu-id="587d9-119">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] commands:</span></span>  
  
     `sp_configure 'clr enabled', 1`  
  
     `GO`  
  
     `RECONFIGURE`  
  
     `GO`  
  
    > [!NOTE]  
    >  <span data-ttu-id="587d9-120">若要啟用 CLR 整合，您必須擁有 `ALTER SETTINGS` 伺服器層級權限，此權限是由系統管理員 (`sysadmin`) 和伺服器管理員 (`serveradmin`) 固定伺服器角色的成員以隱含方式持有。</span><span class="sxs-lookup"><span data-stu-id="587d9-120">To enable CLR, you must have `ALTER SETTINGS` server level permission, which is implicitly held by members of the `sysadmin` and `serveradmin` fixed server roles.</span></span>  
  
-   <span data-ttu-id="587d9-121">AdventureWorks 資料庫必須安裝在您所使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上。</span><span class="sxs-lookup"><span data-stu-id="587d9-121">The AdventureWorks database must be installed on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using.</span></span>  
  
-   <span data-ttu-id="587d9-122">如果您不是所使用之實例的系統管理員 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，則必須讓系統管理員授與您**CreateAssembly**許可權，才能完成安裝。</span><span class="sxs-lookup"><span data-stu-id="587d9-122">If you are not an administrator for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using, you must have an administrator grant you **CreateAssembly** permission to complete the installation.</span></span>  
  
## <a name="building-the-sample"></a><span data-ttu-id="587d9-123">建立範例</span><span class="sxs-lookup"><span data-stu-id="587d9-123">Building the Sample</span></span>  
  
#### <a name="create-and-run-the-sample-by-using-the-following-instructions"></a><span data-ttu-id="587d9-124">使用下列指示來建立並執行範例：</span><span class="sxs-lookup"><span data-stu-id="587d9-124">Create and run the sample by using the following instructions:</span></span>  
  
1.  <span data-ttu-id="587d9-125">開啟 Visual Studio 或 .NET Framework 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="587d9-125">Open a Visual Studio or .NET Framework command prompt.</span></span>  
  
2.  <span data-ttu-id="587d9-126">必要時，請建立範例的目錄。</span><span class="sxs-lookup"><span data-stu-id="587d9-126">If necessary, create a directory for your sample.</span></span> <span data-ttu-id="587d9-127">在此範例中，我們將使用 C:\MySample。</span><span class="sxs-lookup"><span data-stu-id="587d9-127">For this example, we will use C:\MySample.</span></span>  
  
3.  <span data-ttu-id="587d9-128">在 c:\MySample 中，建立 `HelloWorld.vb` (適用於 Visual Basic 範例) 或 `HelloWorld.cs` (適用於 C# 範例) 並將適當的 Visual Basic 或 C# 範例程式碼 (下面) 複製到檔案中。</span><span class="sxs-lookup"><span data-stu-id="587d9-128">In c:\MySample, create `HelloWorld.vb` (for the Visual Basic sample) or `HelloWorld.cs` (for the C# sample) and copy the appropriate Visual Basic or C# sample code (below) into the file.</span></span>  
  
4.  <span data-ttu-id="587d9-129">根據您選擇的語言，在命令列提示字元中執行下列其中一段程式碼，藉以編譯範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="587d9-129">Compile the sample code from the command line prompt by executing one of the following, depending on your choice of language.</span></span>  
  
    -   `vbc C:HelloWorld.vb /target:library`  
  
    -   `csc /target:library HelloWorld.cs`  
  
5.  <span data-ttu-id="587d9-130">將 [!INCLUDE[tsql](../../includes/tsql-md.md)] 安裝程式碼複製到檔案中，並將它儲存成範例目錄中的 `Install.sql`。</span><span class="sxs-lookup"><span data-stu-id="587d9-130">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation code into a file and save it as `Install.sql` in the sample directory.</span></span>  
  
6.  <span data-ttu-id="587d9-131">部署組件和預存程序，方法是執行</span><span class="sxs-lookup"><span data-stu-id="587d9-131">Deploy the assembly and stored procedure by executing</span></span>  
  
    -   `sqlcmd -E -I -i install.sql -v root = "C:\MySample\"`  
  
7.  <span data-ttu-id="587d9-132">將 [!INCLUDE[tsql](../../includes/tsql-md.md)] 測試命令腳本複製到檔案中，並將它儲存成 `test.sql` 範例目錄中的。</span><span class="sxs-lookup"><span data-stu-id="587d9-132">Copy [!INCLUDE[tsql](../../includes/tsql-md.md)] test command script into a file and save it as `test.sql` in the sample directory.</span></span>  
  
8.  <span data-ttu-id="587d9-133">使用下列命令來執行測試指令碼</span><span class="sxs-lookup"><span data-stu-id="587d9-133">Execute the test script with the following command</span></span>  
  
    -   `sqlcmd -E -I -i test.sql`  
  
9. <span data-ttu-id="587d9-134">將 [!INCLUDE[tsql](../../includes/tsql-md.md)] 清除指令碼複製到檔案中，並將它儲存成範例目錄中的 `cleanup.sql`。</span><span class="sxs-lookup"><span data-stu-id="587d9-134">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] cleanup script into a file and save it as `cleanup.sql` in the sample directory.</span></span>  
  
10. <span data-ttu-id="587d9-135">使用下列命令來執行指令碼</span><span class="sxs-lookup"><span data-stu-id="587d9-135">Execute the script with the  following command</span></span>  
  
    -   `sqlcmd -E -I -i cleanup.sql`  
  
## <a name="sample-code"></a><span data-ttu-id="587d9-136">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="587d9-136">Sample Code</span></span>  
 <span data-ttu-id="587d9-137">下面是此範例的程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="587d9-137">The following are the code listings for this sample.</span></span>  
  
 <span data-ttu-id="587d9-138">C#</span><span class="sxs-lookup"><span data-stu-id="587d9-138">C#</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
public partial class StoredProcedures  
{  
    [Microsoft.SqlServer.Server.SqlProcedure]  
    public static void HelloWorld()  
    {  
        Microsoft.SqlServer.Server.SqlMetaData columnInfo  
                = new Microsoft.SqlServer.Server.SqlMetaData("Column1", SqlDbType.NVarChar, 12);  
        SqlDataRecord greetingRecord  
            = new SqlDataRecord(new Microsoft.SqlServer.Server.SqlMetaData[] { columnInfo });  
        greetingRecord.SetString(0, "Hello world!");  
        SqlContext.Pipe.Send(greetingRecord);  
    }  
};  
  
```  
  
 <span data-ttu-id="587d9-139">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="587d9-139">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Partial Public NotInheritable Class StoredProcedures  
    <Microsoft.SqlServer.Server.SqlProcedure()> _  
    Public Shared Sub HelloWorld()  
        Dim columnInfo As New Microsoft.SqlServer.Server.SqlMetaData("Column1", _  
            SqlDbType.NVarChar, 12)  
        Dim greetingRecord As New SqlDataRecord(New  _  
            Microsoft.SqlServer.Server.SqlMetaData() {columnInfo})  
        greetingRecord.SetString(0, "Hello World!")  
        SqlContext.Pipe.Send(greetingRecord)  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="587d9-140">這是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 安裝指令碼 (`Install.sql`)，它會部署組件並在資料庫中建立預存程序。</span><span class="sxs-lookup"><span data-stu-id="587d9-140">This is the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation script (`Install.sql`), which deploys the assembly and creates the stored procedure in the database.</span></span>  
  
```  
USE AdventureWorks  
GO  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorld')  
DROP PROCEDURE usp_HelloWorld;  
GO  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorld')  
DROP ASSEMBLY HelloWorld;  
GO  
DECLARE @SamplesPath nvarchar(1024)  
set @SamplesPath = '$(root)'  
CREATE ASSEMBLY HelloWorld   
FROM @SamplesPath + 'HelloWorld.dll'  
WITH permission_set = Safe;  
GO  
  
CREATE PROCEDURE usp_HelloWorld  
--(  
--    @Greeting nvarchar(12) OUTPUT  
--)  
AS EXTERNAL NAME HelloWorld.[StoredProcedures].HelloWorld;  
GO  
```  
  
 <span data-ttu-id="587d9-141">這是 `test.sql`，它會執行預存程序，藉以測試範例。</span><span class="sxs-lookup"><span data-stu-id="587d9-141">This is `test.sql`, which tests the sample by executing the stored procedure.</span></span>  
  
```  
use AdventureWorks  
go  
execute usp_HelloWorld  
  
USE AdventureWorks;  
GO  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorld')  
DROP PROCEDURE usp_HelloWorld;  
GO  
```  
  
 <span data-ttu-id="587d9-142">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 會從資料庫中移除組件和預存程序。</span><span class="sxs-lookup"><span data-stu-id="587d9-142">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] removes the assembly and stored procedure from the database.</span></span>  
  
```  
USE AdventureWorks  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorld')  
DROP PROCEDURE usp_HelloWorld;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorld')  
DROP ASSEMBLY HelloWorld;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="587d9-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="587d9-143">See Also</span></span>  
 [<span data-ttu-id="587d9-144">通用語言執行平台 &#40;CLR&#41; 整合的使用案例和範例</span><span class="sxs-lookup"><span data-stu-id="587d9-144">Usage Scenarios and Examples for Common Language Runtime &#40;CLR&#41; Integration</span></span>](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  
