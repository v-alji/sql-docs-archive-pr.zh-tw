---
title: CLR 交易範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: b09161af-6ac1-406c-9d62-e40be3b4cf8d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a78d7ced8a7d60e4f3853c7c214d8494a04a460f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593543"
---
# <a name="clr-transactions-sample"></a><span data-ttu-id="58b3a-102">CLR 交易範例</span><span class="sxs-lookup"><span data-stu-id="58b3a-102">CLR Transactions Sample</span></span>
  <span data-ttu-id="58b3a-103">此範例會示範如何使用位於 `System.Transactions` 命名空間內的 Managed API 來控制交易。</span><span class="sxs-lookup"><span data-stu-id="58b3a-103">This sample demonstrates controlling transactions by using the managed APIs located in the `System.Transactions` namespace.</span></span> <span data-ttu-id="58b3a-104">特別的是，`System.Transactions.TransactionScope` 類別是用來建立交易界限，以確保除非有足夠庫存可應付要求，否則不調整庫存數字，而且如果有足夠庫存，則庫存是以不可部分完成的方式從某個位置轉移到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="58b3a-104">In particular, the `System.Transactions.TransactionScope` class is used to establish a transaction boundary to ensure that inventory figures are not adjusted unless there is sufficient inventory to cover the request, and if there is sufficient inventory that the transfer from of the inventory from one location to another occurs in an atomic fashion.</span></span> <span data-ttu-id="58b3a-105">示範在分散式交易中自動註冊，其方式是將庫存的變更記錄到儲存在另一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上的稽核資料庫。</span><span class="sxs-lookup"><span data-stu-id="58b3a-105">Automatic registration in a distributed transaction is demonstrated by logging changes in inventory to an auditing database stored on a separate instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="58b3a-106">先決條件</span><span class="sxs-lookup"><span data-stu-id="58b3a-106">Prerequisites</span></span>  
 <span data-ttu-id="58b3a-107">若要建立並執行這個專案，您必須安裝下列軟體：</span><span class="sxs-lookup"><span data-stu-id="58b3a-107">To create and run this project the following the following software must be installed:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="58b3a-108">或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express。</span><span class="sxs-lookup"><span data-stu-id="58b3a-108">or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.</span></span> <span data-ttu-id="58b3a-109">您可以從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express 文件集和範例[網站](https://www.microsoft.com/sql-server/sql-server-editions-express)免費取得 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express</span><span class="sxs-lookup"><span data-stu-id="58b3a-109">You can obtain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express free of charge from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express Documentation and Samples [Web site](https://www.microsoft.com/sql-server/sql-server-editions-express)</span></span>  
  
-   <span data-ttu-id="58b3a-110">您可以從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 開發人員[網站](https://go.microsoft.com/fwlink/?linkid=62796)取得 AdventureWorks 資料庫</span><span class="sxs-lookup"><span data-stu-id="58b3a-110">The AdventureWorks database that is available at the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Developer [Web site](https://go.microsoft.com/fwlink/?linkid=62796)</span></span>  
  
-   <span data-ttu-id="58b3a-111">.NET Framework SDK 2.0 或更新版本或是 Microsoft Visual Studio 2005 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="58b3a-111">.NET Framework SDK 2.0 or later or Microsoft Visual Studio 2005 or later.</span></span> <span data-ttu-id="58b3a-112">您可以免費取得 .NET Framework SDK。</span><span class="sxs-lookup"><span data-stu-id="58b3a-112">You can obtain .NET Framework SDK free of charge.</span></span>  
  
-   <span data-ttu-id="58b3a-113">此外，您也必須符合下列條件：</span><span class="sxs-lookup"><span data-stu-id="58b3a-113">In addition, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="58b3a-114">您所使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體必須啟用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="58b3a-114">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using must have CLR integration enabled.</span></span>  
  
-   <span data-ttu-id="58b3a-115">若要啟用 CLR 整合，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="58b3a-115">In order to enable CLR integration, perform the following steps:</span></span>  
  
    #### <a name="enabling-clr-integration"></a><span data-ttu-id="58b3a-116">啟用 CLR 整合</span><span class="sxs-lookup"><span data-stu-id="58b3a-116">Enabling CLR Integration</span></span>  
  
    -   <span data-ttu-id="58b3a-117">執行下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令：</span><span class="sxs-lookup"><span data-stu-id="58b3a-117">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] commands:</span></span>  
  
     `sp_configure 'clr enabled', 1`  
  
     `GO`  
  
     `RECONFIGURE`  
  
     `GO`  
  
    > [!NOTE]  
    >  <span data-ttu-id="58b3a-118">若要啟用 CLR 整合，您必須擁有 `ALTER SETTINGS` 伺服器層級權限，此權限是由系統管理員 (`sysadmin`) 和伺服器管理員 (`serveradmin`) 固定伺服器角色的成員以隱含方式持有。</span><span class="sxs-lookup"><span data-stu-id="58b3a-118">To enable CLR, you must have `ALTER SETTINGS` server level permission, which is implicitly held by members of the `sysadmin` and `serveradmin` fixed server roles.</span></span>  
  
-   <span data-ttu-id="58b3a-119">AdventureWorks 資料庫必須安裝在您所使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上。</span><span class="sxs-lookup"><span data-stu-id="58b3a-119">The AdventureWorks database must be installed on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using.</span></span>  
  
-   <span data-ttu-id="58b3a-120">如果您不是所使用之實例的系統管理員 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，則必須讓系統管理員授與您**CreateAssembly**許可權，才能完成安裝。</span><span class="sxs-lookup"><span data-stu-id="58b3a-120">If you are not an administrator for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using, you must have an administrator grant you **CreateAssembly** permission to complete the installation.</span></span>  
  
## <a name="building-the-sample"></a><span data-ttu-id="58b3a-121">建立範例</span><span class="sxs-lookup"><span data-stu-id="58b3a-121">Building the Sample</span></span>  
  
#### <a name="create-and-run-the-sample-by-using-the-following-instructions"></a><span data-ttu-id="58b3a-122">使用下列指示來建立並執行範例：</span><span class="sxs-lookup"><span data-stu-id="58b3a-122">Create and run the sample by using the following instructions:</span></span>  
  
1.  <span data-ttu-id="58b3a-123">開啟 Visual Studio 或 .NET Framework 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="58b3a-123">Open a Visual Studio or .NET Framework command prompt.</span></span>  
  
2.  <span data-ttu-id="58b3a-124">必要時，請建立範例的目錄。</span><span class="sxs-lookup"><span data-stu-id="58b3a-124">If necessary, create a directory for your sample.</span></span> <span data-ttu-id="58b3a-125">在此範例中，我們將使用 C:\MySample。</span><span class="sxs-lookup"><span data-stu-id="58b3a-125">For this example, we will use C:\MySample.</span></span>  
  
3.  <span data-ttu-id="58b3a-126">因為此範例需要已簽署的組件，所以請輸入下列命令，藉以建立非對稱金鑰：</span><span class="sxs-lookup"><span data-stu-id="58b3a-126">Since this example requires a signed assembly, create an asymmetric key by typing the command:</span></span>  
  
     `sn -k SampleKey.snk`  
  
4.  <span data-ttu-id="58b3a-127">根據您選擇的語言，在命令列提示字元中執行下列其中一段程式碼，藉以編譯範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="58b3a-127">Compile the sample code from the command line prompt by executing one of the following, depending on your choice of language.</span></span>  
  
    -   `Vbc /reference:"C:\Program Files (x86)\Reference Assemblies\Microsoft\Framework\v3.5\System.Core.dll","C:\Program Files (x86)\Reference Assemblies\Microsoft\Framework\v3.5\System.Data.DataSetExtensions.dll","C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll","C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll","C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Transactions.dll","C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Xml.dll" /keyfile:Key.snk /target:Library /out:Transaction.dll InventoryMover.vb`  
  
    -   `Csc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Transactions.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Xml.dll /keyfile:key.snk /out:Transaction.dll /target:library InventoryMover.cs`  
  
5.  <span data-ttu-id="58b3a-128">將 [!INCLUDE[tsql](../../includes/tsql-md.md)] 安裝程式碼複製到檔案中，並將它儲存成範例目錄中的 `install.sql`。</span><span class="sxs-lookup"><span data-stu-id="58b3a-128">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation code into a file and save it as `install.sql` in the sample directory.</span></span>  
  
6.  <span data-ttu-id="58b3a-129">部署組件和預存程序，方法是執行</span><span class="sxs-lookup"><span data-stu-id="58b3a-129">Deploy the assembly and stored procedure by executing</span></span>  
  
    -   `sqlcmd -E -I -i install.sql -v root = "C:\MySample\"`  
  
7.  <span data-ttu-id="58b3a-130">將 [!INCLUDE[tsql](../../includes/tsql-md.md)] 資料庫安裝程式碼複製到檔案中，並將它儲存成 `installDB.sql` 範例目錄中的。</span><span class="sxs-lookup"><span data-stu-id="58b3a-130">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] database installation code into a file and save it as `installDB.sql` in the sample directory.</span></span>  
  
8.  <span data-ttu-id="58b3a-131">安裝稽核資料庫，方法是執行</span><span class="sxs-lookup"><span data-stu-id="58b3a-131">Install the audit database by executing</span></span>  
  
    -   `Sqlcmd -S server_name [ \instance_name ] -E -I -i installDB.sql`  
  
     <span data-ttu-id="58b3a-132">並搭配適當的執行個體和伺服器值。</span><span class="sxs-lookup"><span data-stu-id="58b3a-132">with appropriate values of the instance and server.</span></span>  
  
9. <span data-ttu-id="58b3a-133">將 [!INCLUDE[tsql](../../includes/tsql-md.md)] 測試命令腳本複製到檔案中，並將它儲存成 `test.sql` 範例目錄中的。</span><span class="sxs-lookup"><span data-stu-id="58b3a-133">Copy [!INCLUDE[tsql](../../includes/tsql-md.md)] test command script into a file and save it as `test.sql` in the sample directory.</span></span>  
  
10. <span data-ttu-id="58b3a-134">使用下列命令來執行測試指令碼</span><span class="sxs-lookup"><span data-stu-id="58b3a-134">Execute the test script with the following command</span></span>  
  
    -   `sqlcmd -E -I -i test.sql`  
  
11. <span data-ttu-id="58b3a-135">將 [!INCLUDE[tsql](../../includes/tsql-md.md)] 資料庫清除指令碼複製到檔案中，並將它儲存成範例目錄中的 `cleanupDB.sql`。</span><span class="sxs-lookup"><span data-stu-id="58b3a-135">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] database cleanup script into a file and save it as `cleanupDB.sql` in the sample directory.</span></span>  
  
12. <span data-ttu-id="58b3a-136">使用下列命令來執行指令碼</span><span class="sxs-lookup"><span data-stu-id="58b3a-136">Execute the script with the following command</span></span>  
  
    -   `Sqlcmd -S server_name [ \instance_name ] -E -I -i cleanup.sql`  
  
         <span data-ttu-id="58b3a-137">並搭配適當的執行個體和伺服器值。</span><span class="sxs-lookup"><span data-stu-id="58b3a-137">with appropriate values of the instance and server.</span></span>  
  
13. <span data-ttu-id="58b3a-138">將 [!INCLUDE[tsql](../../includes/tsql-md.md)] 清除指令碼複製到檔案中，並將它儲存成範例目錄中的 `cleanup.sql`。</span><span class="sxs-lookup"><span data-stu-id="58b3a-138">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] cleanup script into a file and save it as `cleanup.sql` in the sample directory.</span></span>  
  
14. <span data-ttu-id="58b3a-139">使用下列命令來執行指令碼</span><span class="sxs-lookup"><span data-stu-id="58b3a-139">Execute the script with the following command</span></span>  
  
    -   `sqlcmd -E -I -i cleanup.sql`  
  
## <a name="sample-code"></a><span data-ttu-id="58b3a-140">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="58b3a-140">Sample Code</span></span>  
 <span data-ttu-id="58b3a-141">下面是此範例的程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="58b3a-141">The following are the code listings for this sample.</span></span>  
  
 <span data-ttu-id="58b3a-142">C#</span><span class="sxs-lookup"><span data-stu-id="58b3a-142">C#</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using System.Transactions;  
using Microsoft.SqlServer.Server;  
using System.Security.Principal;  
  
    public static class InventoryMover  
    {  
        const string contextConnectionString = "context connection=true";  
  
        // **********  
        // Important: Change this connection string to refer to a server other than the one  
        // you have installed the AdventureWorks database.  This sample demonstrates   
        // two-phase commit across multiple servers, and loopback to the same server is not  
        // permitted from CLR integrated based stored procedures.  
        // **********  
        const string auditConnectionString = "server=<YourServer>; database=InventoryAudit; user=<YourUser>; password=<YourPassword>";  
  
        [SqlMethod(DataAccess = DataAccessKind.Read, IsMutator = true)]  
        public static void ExecuteTransfer(int productID, short fromLocationID,  
            short toLocationID, short quantityToTransfer)  
        {  
                       // Establish bounds of the transaction  
            using (TransactionScope transScope = new TransactionScope())  
            {  
                using (SqlConnection adventureworksConnection = new  
                   SqlConnection(contextConnectionString))  
                {  
                    // Opening adventureworksConnection automatically enlists it in the   
                    // TransactionScope as part of the transaction.  
                    adventureworksConnection.Open();  
  
                    SqlCommand checkCommand = adventureworksConnection.CreateCommand();  
                    checkCommand.CommandText = "SELECT TOP 1 Quantity"  
                        + " FROM Production.ProductInventory WITH (REPEATABLEREAD)"  
                        + " WHERE ProductID = @ProductID AND LocationID = @LocationID;";  
                    checkCommand.Parameters.Add("@ProductID", SqlDbType.Int);  
                    checkCommand.Parameters[0].Value = productID;  
                    checkCommand.Parameters.Add("@LocationID", SqlDbType.Int);  
                    checkCommand.Parameters[1].Value = fromLocationID;  
  
                    object result = checkCommand.ExecuteScalar();  
                    short availableQuantity = (short)result;  
  
                    if (availableQuantity < quantityToTransfer)  
                        //It would be better to throw a custom error, and in some cases to actually  
                        //RAISERROR.  Also, it would be better to map product IDs and location IDs to   
                        //names for the error message.  
                        throw new ArgumentOutOfRangeException("quantityToTransfer",  
                            string.Format("Attempt to transfer {0} of product {1} from"  
                                + " location {2} but only {3} is available.",  
                                quantityToTransfer, productID, fromLocationID,  
                                availableQuantity));  
  
                    //Remove inventory count from source  
                    SqlCommand reduceCommand = adventureworksConnection.CreateCommand();  
                    reduceCommand.CommandText = "UPDATE Production.ProductInventory"  
                        + " SET Quantity = Quantity - @QuantityToTransfer"  
                        + " WHERE ProductID = @ProductID AND LocationID = @LocationID;";  
                    reduceCommand.Parameters.Add("@ProductID", SqlDbType.Int);  
                    reduceCommand.Parameters[0].Value = productID;  
                    reduceCommand.Parameters.Add("@LocationID", SqlDbType.SmallInt);  
                    reduceCommand.Parameters[1].Value = fromLocationID;  
                    reduceCommand.Parameters.Add("@QuantityToTransfer", SqlDbType.SmallInt);  
                    reduceCommand.Parameters[2].Value = quantityToTransfer;  
  
                    reduceCommand.ExecuteNonQuery();  
  
                    //Increate inventory count at destination  
                    SqlCommand increaseCommand = adventureworksConnection.CreateCommand();  
                    increaseCommand.CommandText = "UPDATE Production.ProductInventory"  
                        + " SET Quantity = Quantity + @QuantityToTransfer"  
                        + " WHERE ProductID = @ProductID AND LocationID = @LocationID;";  
                    increaseCommand.Parameters.Add("@ProductID", SqlDbType.Int);  
                    increaseCommand.Parameters[0].Value = productID;  
                    increaseCommand.Parameters.Add("@LocationID", SqlDbType.SmallInt);  
                    increaseCommand.Parameters[1].Value = toLocationID;  
                    increaseCommand.Parameters.Add("@QuantityToTransfer", SqlDbType.SmallInt);  
                    increaseCommand.Parameters[2].Value = quantityToTransfer;  
  
                    increaseCommand.ExecuteNonQuery();  
  
                    // Create an audit trail of the inventory transfer.  We must impersonate the  
                    // client credentials in order for this to work.  Otherwise we'd have to  
                    // set up security for the machine account.  
//                    SqlConnection auditConnection = adventureworksConnection;  
                    using (SqlConnection auditConnection = new SqlConnection(auditConnectionString))  
                    {  
                        SqlCommand auditCommand = auditConnection.CreateCommand();  
                        auditCommand.CommandText = "INSERT InventoryChange "  
                            + " (ProductID, FromLocationID, ToLocationID, Quantity) "  
                            + " VALUES (@ProductID, @FromLocationID, @ToLocationID, @Quantity);";  
                        auditCommand.Parameters.Add("@ProductID", SqlDbType.Int);  
                        auditCommand.Parameters[0].Value = productID;  
                        auditCommand.Parameters.Add("@FromLocationID", SqlDbType.SmallInt);  
                        auditCommand.Parameters[1].Value = fromLocationID;  
                        auditCommand.Parameters.Add("@ToLocationID", SqlDbType.SmallInt);  
                        auditCommand.Parameters[2].Value = toLocationID;  
                        auditCommand.Parameters.Add("@Quantity", SqlDbType.SmallInt);  
                        auditCommand.Parameters[3].Value = quantityToTransfer;  
  
                        // Opening auditConnection automatically enlists it in the   
                        // TransactionScope as part of the transaction.  
                        auditConnection.Open();  
                        auditCommand.ExecuteNonQuery();  
                    }  
  
                }  
                //  The Complete method commits the transaction.  
                transScope.Complete();  
            }  
        }  
    }  
  
```  
  
 <span data-ttu-id="58b3a-143">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="58b3a-143">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Collections.Generic  
Imports System.Text  
Imports System.Data  
Imports System.Data.SqlTypes  
Imports System.Data.SqlClient  
Imports System.Transactions  
Imports Microsoft.SqlServer.Server  
Imports System.Security.Principal  
Imports System.Globalization  
  
Public NotInheritable Class InventoryMover  
    Private Const contextConnectionString As String = "context connection=true"  
  
    Private Sub New()  
  
    End Sub  
  
    ' **********  
    ' Important: Change this connection string to refer to a server other than the one  
    ' you have installed the AdventureWorks database.  This sample demonstrates   
    ' two-phase commit across multiple servers, and loopback to the same server is not  
    ' permitted from CLR integrated based stored procedures.  
    ' **********  
    Private Const auditConnectionString As String = "server=<YourServer>; database=InventoryAudit; user=<YourUser>; password=<YourPassword>"  
    <SqlMethod(DataAccess:=DataAccessKind.Read, IsMutator:=True)> _  
    Public Shared Sub ExecuteTransfer(ByVal productID As Integer, ByVal fromLocationID As Short, _  
        ByVal toLocationID As Short, ByVal quantityToTransfer As Short)  
        ' Establish bounds of the transaction  
        Using transScope As New TransactionScope()  
            Using adventureworksConnection As New SqlConnection(contextConnectionString)  
                ' Opening adventureworksConnection automatically enlists it in the   
                ' TransactionScope as part of the transaction.  
                adventureworksConnection.Open()  
  
                Dim checkCommand As SqlCommand = adventureworksConnection.CreateCommand()  
                checkCommand.CommandText = "SELECT TOP 1 Quantity" _  
                        & " FROM Production.ProductInventory WITH (REPEATABLEREAD)" _  
                        & " WHERE ProductID = @ProductID AND LocationID = @LocationID;"  
                checkCommand.Parameters.Add("@ProductID", SqlDbType.Int)  
                checkCommand.Parameters(0).Value = productID  
                checkCommand.Parameters.Add("@LocationID", SqlDbType.Int)  
                checkCommand.Parameters(1).Value = fromLocationID  
  
                Dim result As Object = checkCommand.ExecuteScalar()  
                Dim availableQuantity As Short = CType(result, Short)  
  
                If (availableQuantity < quantityToTransfer) Then  
                    'It would be better to throw a custom error, and in some cases to actually  
                    'RAISERROR.  Also, it would be better to map product IDs and location IDs to   
                    'names for the error message.  
                    Throw New ArgumentOutOfRangeException("quantityToTransfer", _  
                        String.Format(CultureInfo.InvariantCulture, "Attempt to transfer {0} of product {1} from" _  
                        & " location {2} but only {3} is available.", _  
                        quantityToTransfer, productID, fromLocationID, _  
                        availableQuantity))  
                End If  
  
                'Remove inventory count from source  
                Dim reduceCommand As SqlCommand = adventureworksConnection.CreateCommand()  
                reduceCommand.CommandText = "UPDATE Production.ProductInventory" _  
                    & " SET Quantity = Quantity - @QuantityToTransfer" _  
                    & " WHERE ProductID = @ProductID AND LocationID = @LocationID;"  
                reduceCommand.Parameters.Add("@ProductID", SqlDbType.Int)  
                reduceCommand.Parameters(0).Value = productID  
                reduceCommand.Parameters.Add("@LocationID", SqlDbType.SmallInt)  
                reduceCommand.Parameters(1).Value = fromLocationID  
                reduceCommand.Parameters.Add("@QuantityToTransfer", SqlDbType.SmallInt)  
                reduceCommand.Parameters(2).Value = quantityToTransfer  
  
                reduceCommand.ExecuteNonQuery()  
  
                'Increate inventory count at destination  
                Dim increaseCommand As SqlCommand = adventureworksConnection.CreateCommand()  
                increaseCommand.CommandText = "UPDATE Production.ProductInventory" _  
                    & " SET Quantity = Quantity + @QuantityToTransfer" _  
                    & " WHERE ProductID = @ProductID AND LocationID = @LocationID;"  
                increaseCommand.Parameters.Add("@ProductID", SqlDbType.Int)  
                increaseCommand.Parameters(0).Value = productID  
                increaseCommand.Parameters.Add("@LocationID", SqlDbType.SmallInt)  
                increaseCommand.Parameters(1).Value = toLocationID  
                increaseCommand.Parameters.Add("@QuantityToTransfer", SqlDbType.SmallInt)  
                increaseCommand.Parameters(2).Value = quantityToTransfer  
  
                increaseCommand.ExecuteNonQuery()  
  
                ' Create an audit trail of the inventory transfer.  We must impersonate the  
                ' client credentials in order for this to work.  Otherwise we'd have to  
                ' set up security for the machine account.  
                'SqlConnection auditConnection = adventureworksConnection  
                Using auditConnection As New SqlConnection(auditConnectionString)  
                    Dim auditCommand As SqlCommand = auditConnection.CreateCommand()  
                    auditCommand.CommandText = "INSERT InventoryChange " _  
                        & " (ProductID, FromLocationID, ToLocationID, Quantity) " _  
                        & " VALUES (@ProductID, @FromLocationID, @ToLocationID, @Quantity);"  
                    auditCommand.Parameters.Add("@ProductID", SqlDbType.Int)  
                    auditCommand.Parameters(0).Value = productID  
                    auditCommand.Parameters.Add("@FromLocationID", SqlDbType.SmallInt)  
                    auditCommand.Parameters(1).Value = fromLocationID  
                    auditCommand.Parameters.Add("@ToLocationID", SqlDbType.SmallInt)  
                    auditCommand.Parameters(2).Value = toLocationID  
                    auditCommand.Parameters.Add("@Quantity", SqlDbType.SmallInt)  
                    auditCommand.Parameters(3).Value = quantityToTransfer  
  
                    ' Opening auditConnection automatically enlists it in the   
                    ' TransactionScope as part of the transaction.  
                    auditConnection.Open()  
                    auditCommand.ExecuteNonQuery()  
  
                End Using  
            End Using  
  
            '  The Complete method commits the transaction.  
            transScope.Complete()  
        End Using  
    End Sub  
End Class  
  
```  
  
 <span data-ttu-id="58b3a-144">這是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 安裝指令碼 (`Install.sql`)，它會部署組件並在資料庫中建立預存程序。</span><span class="sxs-lookup"><span data-stu-id="58b3a-144">This is the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation script (`Install.sql`), which deploys the assembly and creates the stored procedure in the database.</span></span>  
  
```  
USE AdventureWorks  
GO  
  
-- Drop existing sproc and assembly if any.  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_ExecuteTransfer')  
DROP PROCEDURE usp_ExecuteTransfer;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'Transaction')  
DROP ASSEMBLY [Transaction];  
GO  
  
USE master  
GO  
  
IF EXISTS (SELECT * FROM sys.server_principals WHERE [name] = 'ExternalSample_Login')  
DROP LOGIN ExternalSample_Login;  
GO  
  
IF EXISTS (SELECT * FROM sys.asymmetric_keys WHERE [name] = 'ExternalSample_Key')  
DROP ASYMMETRIC KEY ExternalSample_Key;  
GO  
DECLARE @SamplesPath nvarchar(1024)  
-- You may need to modify the value of the this variable if you have installed the sample someplace other than the default location.  
set @SamplesPath = 'C:\MySample\'  
  
EXEC('CREATE ASYMMETRIC KEY ExternalSample_Key FROM EXECUTABLE FILE = ''' + @SamplesPath + 'Transaction.dll'';');  
CREATE LOGIN ExternalSample_Login FROM ASYMMETRIC KEY ExternalSample_Key  
GRANT EXTERNAL ACCESS ASSEMBLY TO ExternalSample_Login  
GO  
  
USE AdventureWorks  
GO  
  
DECLARE @SamplesPath nvarchar(1024)  
-- You may need to modify the value of this variable if you have installed the sample someplace other than the default location.  
set @SamplesPath = 'C:\MySample\'  
-- Add the assembly and CLR integration based stored procedure  
  
CREATE ASSEMBLY [Transaction]   
FROM @SamplesPath + 'Transaction.dll'  
WITH permission_set = External_Access;  
GO  
  
CREATE PROCEDURE usp_ExecuteTransfer  
(  
@ProductID int,  
@FromLocationID smallint,  
@ToLocationID smallint,  
@QuantityToTransfer smallint  
)  
AS EXTERNAL NAME [Transaction].[InventoryMover].ExecuteTransfer;  
GO  
```  
  
 <span data-ttu-id="58b3a-145">這是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 安裝指令碼 (`InstallDB.sql`)，它會在第二個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中建立稽核資料庫。</span><span class="sxs-lookup"><span data-stu-id="58b3a-145">This is the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation script (`InstallDB.sql`), which creates the audit database in the second instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
```  
SET NOCOUNT OFF;  
GO  
  
PRINT CONVERT(varchar(1000), @@VERSION);  
GO  
  
PRINT '';  
PRINT 'Started - ' + CONVERT(varchar, GETDATE(), 121);  
GO  
  
USE [master];  
GO  
  
-- ****************************************  
-- Drop Database  
-- ****************************************  
PRINT '';  
PRINT '*** Dropping Database';  
GO  
  
IF EXISTS (SELECT [name] FROM [master].[sys].[databases] WHERE [name] = N'InventoryAudit')  
    DROP DATABASE [InventoryAudit];  
  
-- If the database has any other open connections close the network connection.  
IF @@ERROR = 3702   
    RAISERROR('[InventoryAudit] database cannot be dropped because there are still other open connections', 127, 127) WITH NOWAIT, LOG;  
GO  
  
-- ****************************************  
-- Create Database  
-- ****************************************  
PRINT '';  
PRINT '*** Creating Database';  
GO  
  
DECLARE   
    @sql_path nvarchar(256),   
    @sql_cmd nvarchar(256);  
  
SELECT @sql_path = SUBSTRING([physical_name], 1, CHARINDEX(N'master.mdf', LOWER([physical_name])) - 1)  
FROM [master].[sys].[master_files]   
WHERE [database_id] = 1   
    AND [file_id] = 1;  
  
-- COLLATE Latin1_General_CS_AS  
EXECUTE (N'CREATE DATABASE [InventoryAudit]   
    ON (NAME = ''InventoryAudit_Data'', FILENAME = N''' + @sql_path + N'InventoryAudit_Data.mdf'', SIZE = 120, FILEGROWTH = 8)   
    LOG ON (NAME = ''InventoryAudit_Log'', FILENAME = N''' + @sql_path + N'InventoryAudit_Log.ldf'' , SIZE = 2, FILEGROWTH = 96);');  
GO  
  
ALTER DATABASE [InventoryAudit]   
SET RECOVERY SIMPLE,   
    ANSI_NULLS ON,   
    ANSI_PADDING ON,   
    ANSI_WARNINGS ON,   
    ARITHABORT ON,   
    CONCAT_NULL_YIELDS_NULL ON,   
    QUOTED_IDENTIFIER ON,   
    NUMERIC_ROUNDABORT OFF,   
    PAGE_VERIFY CHECKSUM,   
    ALLOW_SNAPSHOT_ISOLATION OFF;  
GO  
  
USE [InventoryAudit];  
GO  
  
PRINT '';  
PRINT '*** Creating Table';  
GO  
  
CREATE TABLE [InventoryChange] (  
[InventoryChangeID] int IDENTITY (1, 1) NOT NULL,  
[ProductID] int NOT NULL,  
[FromLocationID] smallint,  
[ToLocationID] smallint,  
[Quantity] smallint NOT NULL  
);  
GO  
  
```  
  
 <span data-ttu-id="58b3a-146">這是 `test.sql`，它會執行函數，藉以測試範例。</span><span class="sxs-lookup"><span data-stu-id="58b3a-146">This is `test.sql`, which tests the sample by executing the functions.</span></span>  
  
```  
USE AdventureWorks  
GO  
SELECT 'Before first transfer quantity of adjustable races at Tool Crib = ', Quantity FROM Production.ProductInventory  
WHERE ProductID = 1 AND LocationID = 1  
  
SELECT 'Before first transfer quantity of adjustable races at Miscellaneous Storage = ', Quantity FROM Production.ProductInventory  
WHERE ProductID = 1 AND LocationID = 6  
  
--Move 12 adjustable race parts (product id 1) from the Tool Crib (location id 1)   
--to Miscellaneous Storage (location id 6).  
EXEC usp_ExecuteTransfer 1, 1, 6, 12  
  
SELECT 'After first transfer quantity of adjustable races at Tool Crib = ', Quantity FROM Production.ProductInventory  
WHERE ProductID = 1 AND LocationID = 1  
  
SELECT 'After first transfer quantity of adjustable races at Miscellaneous Storage = ', Quantity FROM Production.ProductInventory  
WHERE ProductID = 1 AND LocationID = 6  
  
--Move them back  
EXEC usp_ExecuteTransfer 1, 6, 1, 12  
  
SELECT 'After second transfer quantity of adjustable races at Tool Crib = ', Quantity FROM Production.ProductInventory  
WHERE ProductID = 1 AND LocationID = 1  
  
SELECT 'After second transfer quantity of adjustable races at Miscellaneous Storage = ', Quantity FROM Production.ProductInventory  
WHERE ProductID = 1 AND LocationID = 6  
  
The following tsql removes the assembly and stored procedure from the database (Cleanup.sql).  
USE AdventureWorks  
GO  
  
-- Drop existing sproc and assembly if any.  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_ExecuteTransfer')  
DROP PROCEDURE usp_ExecuteTransfer;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'Transaction')  
DROP ASSEMBLY [Transaction];  
GO  
  
USE master  
GO  
  
IF EXISTS (SELECT * FROM sys.server_principals WHERE [name] = 'ExternalSample_Login')  
DROP LOGIN ExternalSample_Login;  
GO  
  
IF EXISTS (SELECT * FROM sys.asymmetric_keys WHERE [name] = 'ExternalSample_Key')  
DROP ASYMMETRIC KEY ExternalSample_Key;  
GO  
  
USE AdventureWorks  
GO  
```  
  
 <span data-ttu-id="58b3a-147">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 會從第二個執行個體中移除稽核資料庫。</span><span class="sxs-lookup"><span data-stu-id="58b3a-147">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] removes the audit database from the second instance</span></span>  
  
```  
SET NOCOUNT OFF;  
GO  
  
PRINT CONVERT(varchar(1000), @@VERSION);  
GO  
  
PRINT '';  
PRINT 'Started - ' + CONVERT(varchar, GETDATE(), 121);  
GO  
  
USE [master];  
GO  
  
-- ****************************************  
-- Drop Database  
-- ****************************************  
PRINT '';  
PRINT '*** Dropping Database';  
GO  
  
IF EXISTS (SELECT [name] FROM [master].[sys].[databases] WHERE [name] = N'InventoryAudit')  
    DROP DATABASE [InventoryAudit];  
  
-- If the database has any other open connections close the network connection.  
IF @@ERROR = 3702   
    RAISERROR('[InventoryAudit] database cannot be dropped because there are still other open connections', 127, 127) WITH NOWAIT, LOG;  
GO  
```  
  
 <span data-ttu-id="58b3a-148">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 會從資料庫中移除組件和函數。</span><span class="sxs-lookup"><span data-stu-id="58b3a-148">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] removes the assembly and functions from the database.</span></span>  
  
```  
SE AdventureWorks  
GO  
  
-- Drop existing sproc and assembly if any.  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_ExecuteTransfer')  
DROP PROCEDURE usp_ExecuteTransfer;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'Transaction')  
DROP ASSEMBLY [Transaction];  
GO  
  
USE master  
GO  
  
IF EXISTS (SELECT * FROM sys.server_principals WHERE [name] = 'ExternalSample_Login')  
DROP LOGIN ExternalSample_Login;  
GO  
  
IF EXISTS (SELECT * FROM sys.asymmetric_keys WHERE [name] = 'ExternalSample_Key')  
DROP ASYMMETRIC KEY ExternalSample_Key;  
GO  
  
USE AdventureWorks  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="58b3a-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58b3a-149">See Also</span></span>  
 [<span data-ttu-id="58b3a-150">通用語言執行平台 &#40;CLR&#41; 整合的使用案例和範例</span><span class="sxs-lookup"><span data-stu-id="58b3a-150">Usage Scenarios and Examples for Common Language Runtime &#40;CLR&#41; Integration</span></span>](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  
