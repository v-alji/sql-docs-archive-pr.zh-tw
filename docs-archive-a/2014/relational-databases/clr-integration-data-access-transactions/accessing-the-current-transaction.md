---
title: 存取目前的交易 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- current transaction access
- Current property
- Transaction class
ms.assetid: 1a4e2ce5-f627-4c81-8960-6a9968cefda2
author: rothja
ms.author: jroth
ms.openlocfilehash: 34b7e67d30cb9d89a02eb918fcd03651b2915955
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709662"
---
# <a name="accessing-the-current-transaction"></a><span data-ttu-id="527f1-102">存取目前交易</span><span class="sxs-lookup"><span data-stu-id="527f1-102">Accessing the Current Transaction</span></span>
  <span data-ttu-id="527f1-103">如果某個交易在輸入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 上執行的 Common Language Runtime (CLR) 程式碼時處於作用中狀態，系統就會透過 `System.Transactions.Transaction` 類別公開此交易。</span><span class="sxs-lookup"><span data-stu-id="527f1-103">If a transaction is active at the point at which common language runtime (CLR) code running on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is entered, the transaction is exposed through the `System.Transactions.Transaction` class.</span></span> <span data-ttu-id="527f1-104">`Transaction.Current` 屬性可用來存取目前的交易。</span><span class="sxs-lookup"><span data-stu-id="527f1-104">The `Transaction.Current` property is used to access the current transaction.</span></span> <span data-ttu-id="527f1-105">在大部分情況下，您不需要明確存取交易。</span><span class="sxs-lookup"><span data-stu-id="527f1-105">In most cases it is not necessary to access the transaction explicitly.</span></span> <span data-ttu-id="527f1-106">若為資料庫連接，ADO.NET 會在呼叫 `Transaction.Current` 方法時自動檢查 `Connection.Open`，而且以透明方式在該交易中編列連接 (除非連接字串中的 `Enlist` 關鍵字設定為 false)。</span><span class="sxs-lookup"><span data-stu-id="527f1-106">For database connections, ADO.NET checks `Transaction.Current` automatically when the `Connection.Open` method is called, and transparently enlists the connection in that transaction (unless the `Enlist` keyword is set to false in the connection string).</span></span>  
  
 <span data-ttu-id="527f1-107">在下列狀況中，您可能會想要直接使用 `Transaction` 物件：</span><span class="sxs-lookup"><span data-stu-id="527f1-107">You might want to use the `Transaction` object directly in the following scenarios:</span></span>  
  
-   <span data-ttu-id="527f1-108">如果您想要編列不會自動編列的資源，或由於某些原因，無法在初始化期間編列的資源。</span><span class="sxs-lookup"><span data-stu-id="527f1-108">If you want to enlist a resource that does not do automatic enlistment, or that for some reason was not enlisted during initialization.</span></span>  
  
-   <span data-ttu-id="527f1-109">如果您想要在交易中明確編列資源。</span><span class="sxs-lookup"><span data-stu-id="527f1-109">If you want to explicitly enlist a resource in the transaction.</span></span>  
  
-   <span data-ttu-id="527f1-110">如果您想要從預存程序或函數內部結束外部交易。</span><span class="sxs-lookup"><span data-stu-id="527f1-110">If you want to terminate the external transaction from within your stored procedure or function.</span></span> <span data-ttu-id="527f1-111">在此情況下，您可以使用 <xref:System.Transactions.TransactionScope>。</span><span class="sxs-lookup"><span data-stu-id="527f1-111">In this case, you use <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="527f1-112">例如，下列程式碼將回復目前的交易：</span><span class="sxs-lookup"><span data-stu-id="527f1-112">For example, the following code will rollback the current transaction:</span></span>  
  
    ```  
    using(TransactionScope transactionScope = new TransactionScope(TransactionScopeOptions.Required)) { }  
    ```  
  
 <span data-ttu-id="527f1-113">本主題的其餘部分將描述取消外部交易的其他方式。</span><span class="sxs-lookup"><span data-stu-id="527f1-113">The rest of this topic describes other ways to cancel an external transaction.</span></span>  
  
## <a name="canceling-an-external-transaction"></a><span data-ttu-id="527f1-114">取消外部交易</span><span class="sxs-lookup"><span data-stu-id="527f1-114">Canceling an External Transaction</span></span>  
 <span data-ttu-id="527f1-115">您可以使用下列方式，從 Managed 程序或函數取消外部交易：</span><span class="sxs-lookup"><span data-stu-id="527f1-115">You can cancel external transactions from a managed procedure or function in the following ways:</span></span>  
  
-   <span data-ttu-id="527f1-116">Managed 程序或函數可以使用輸出參數來傳回值。</span><span class="sxs-lookup"><span data-stu-id="527f1-116">The managed procedure or function can return a value by using an output parameter.</span></span> <span data-ttu-id="527f1-117">呼叫 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程序可以檢查傳回的值，並且在適當的情況下，執行 `ROLLBACK TRANSACTION`。</span><span class="sxs-lookup"><span data-stu-id="527f1-117">The calling [!INCLUDE[tsql](../../includes/tsql-md.md)] procedure can check the returned value and, if appropriate, execute `ROLLBACK TRANSACTION`.</span></span>  
  
-   <span data-ttu-id="527f1-118">Managed 程序或函數可以擲回自訂例外狀況。</span><span class="sxs-lookup"><span data-stu-id="527f1-118">The managed procedure or function can throw a custom exception.</span></span> <span data-ttu-id="527f1-119">呼叫 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式可以攔截 try/catch 區塊中的 managed 程式或函數所擲回的例外狀況，並執行 `ROLLBACK TRANSACTION` 。</span><span class="sxs-lookup"><span data-stu-id="527f1-119">The calling [!INCLUDE[tsql](../../includes/tsql-md.md)] procedure can catch the exception thrown by the managed procedure or function in a try/catch block and execute `ROLLBACK TRANSACTION`.</span></span>  
  
-   <span data-ttu-id="527f1-120">如果滿足特定條件，Managed 程序或函數可以透過呼叫 `Transaction.Rollback` 方法來取消目前的交易。</span><span class="sxs-lookup"><span data-stu-id="527f1-120">The managed procedure or function can cancel the current transaction by calling the `Transaction.Rollback` method if a certain condition is met.</span></span>  
  
 <span data-ttu-id="527f1-121">在 Managed 程序或函數內部呼叫 `Transaction.Rollback` 方法時，它會擲回含有模稜兩可錯誤訊息的例外狀況而且可能會包裝在 try/catch 區塊中。</span><span class="sxs-lookup"><span data-stu-id="527f1-121">When it is called within a managed procedure or function, the `Transaction.Rollback` method throws an exception with an ambiguous error message and can be wrapped in a try/catch block.</span></span> <span data-ttu-id="527f1-122">此錯誤訊息類似下列內容：</span><span class="sxs-lookup"><span data-stu-id="527f1-122">The error message thresembles similar to the following:</span></span>  
  
```  
Msg 3994, Level 16, State 1, Procedure uspRollbackFromProc, Line 0  
Transaction is not allowed to roll back inside a user defined routine, trigger or aggregate because the transaction is not started in that CLR level. Change application logic to enforce strict transaction nesting.  
```  
  
 <span data-ttu-id="527f1-123">這項例外狀況是在預期中，而必須有 try/catch 區塊，程式碼才能繼續執行。</span><span class="sxs-lookup"><span data-stu-id="527f1-123">This exception is expected and the try/catch block is necessary for code execution to continue.</span></span> <span data-ttu-id="527f1-124">如果沒有 try/catch 區塊，例外狀況就會立即擲回給呼叫 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程序，而且 Managed 程式碼執行將完成。</span><span class="sxs-lookup"><span data-stu-id="527f1-124">Without the try/catch block, the exception will be immediately thrown to the calling [!INCLUDE[tsql](../../includes/tsql-md.md)] procedure and managed code execution will finish.</span></span> <span data-ttu-id="527f1-125">當 Managed 程式碼完成執行時，會引發另一項例外狀況：</span><span class="sxs-lookup"><span data-stu-id="527f1-125">When the managed code finishes execution, another exception is raised:</span></span>  
  
```  
Msg 3991, Level 16, State 1, Procedure uspRollbackFromProc, Line 1   
The context transaction which was active before entering user defined routine, trigger or aggregate " uspRollbackFromProc " has been ended inside of it, which is not allowed. Change application logic to enforce strict transaction nesting. The statement has been terminated.  
```  
  
 <span data-ttu-id="527f1-126">這項例外狀況也在預期中，而且您必須在執行引發觸發程序之動作的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式前後設有 try/catch 區塊，才能繼續執行。</span><span class="sxs-lookup"><span data-stu-id="527f1-126">This exception is also expected, and for execution to continue, you must have a try/catch block around the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that performs the action that fires the trigger.</span></span> <span data-ttu-id="527f1-127">儘管會擲回兩項例外狀況，交易仍會回復，而且不會認可變更。</span><span class="sxs-lookup"><span data-stu-id="527f1-127">Despite the two exceptions thrown, the transaction is rolled back and the changes are not committed.</span></span>  
  
### <a name="example"></a><span data-ttu-id="527f1-128">範例</span><span class="sxs-lookup"><span data-stu-id="527f1-128">Example</span></span>  
 <span data-ttu-id="527f1-129">下面是使用 `Transaction.Rollback` 方法從 Managed 程序回復交易的範例。</span><span class="sxs-lookup"><span data-stu-id="527f1-129">The following is an example of a transaction being rolled back from a managed procedure by using the `Transaction.Rollback` method.</span></span> <span data-ttu-id="527f1-130">請注意 Managed 程式碼中 `Transaction.Rollback` 方法前後的 try/catch 區塊。</span><span class="sxs-lookup"><span data-stu-id="527f1-130">Notice the try/catch block around the `Transaction.Rollback` method in the managed code.</span></span> <span data-ttu-id="527f1-131">[!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼會建立組件和 Managed 預存程序。</span><span class="sxs-lookup"><span data-stu-id="527f1-131">The [!INCLUDE[tsql](../../includes/tsql-md.md)] script creates an assembly and managed stored procedure.</span></span> <span data-ttu-id="527f1-132">請注意， `EXEC uspRollbackFromProc` 語句會包裝在 try/catch 區塊中，因此攔截到 managed 程式完成執行時所擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="527f1-132">Be aware that the `EXEC uspRollbackFromProc` statement is wrapped in a try/catch block, so that the exception thrown when the managed procedure completes execution is caught.</span></span>  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
using System.Transactions;  
  
public partial class StoredProcedures  
{  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void uspRollbackFromProc()  
{  
   using (SqlConnection connection = new SqlConnection(@"context connection=true"))  
   {  
      // Open the connection.  
      connection.Open();  
  
      bool successCondition = true;  
  
      // Success condition is met.  
      if (successCondition)  
      {  
         SqlContext.Pipe.Send("Success condition met in procedure.");   
         // Perform other actions here.  
      }  
  
      //  Success condition is not met, the transaction will be rolled back.  
      else  
      {  
         SqlContext.Pipe.Send("Success condition not met in managed procedure. Transaction rolling back...");  
         try  
         {  
               // Get the current transaction and roll it back.  
               Transaction trans = Transaction.Current;  
               trans.Rollback();  
         }  
         catch (SqlException ex)  
         {  
            // Catch the expected exception.   
            // This allows the connection to close correctly.                      
         }    
      }  
  
      // Close the connection.  
      connection.Close();  
   }  
}  
};  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Transactions  
  
Partial Public Class StoredProcedures  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub  uspRollbackFromProc ()  
   Using connection As New SqlConnection("context connection=true")  
  
   ' Open the connection.  
   connection.Open()  
  
   Dim successCondition As Boolean  
   successCondition = False  
  
   ' Success condition is met.  
   If successCondition Then  
  
      SqlContext.Pipe.Send("Success condition met in procedure.")  
  
      ' Success condition is not met, the transaction will be rolled back.  
  
   Else  
      SqlContext.Pipe.Send("Success condition not met in managed procedure. Transaction rolling back...")  
      Try  
         ' Get the current transaction and roll it back.  
         Dim trans As Transaction  
         trans = Transaction.Current  
         trans.Rollback()  
  
      Catch ex As SqlException  
         ' Catch the exception instead of throwing it.    
         ' This allows the connection to close correctly.                      
      End Try  
  
   End If  
  
   ' Close the connection.  
   connection.Close()  
  
End Using  
End Sub  
End Class  
```  
  
 <span data-ttu-id="527f1-133">**Transact-SQL**</span><span class="sxs-lookup"><span data-stu-id="527f1-133">**Transact-SQL**</span></span>  
  
```  
--Register assembly.  
CREATE ASSEMBLY TestProcs FROM 'C:\Programming\TestProcs.dll'   
Go  
CREATE PROCEDURE uspRollbackFromProc AS EXTERNAL NAME TestProcs.StoredProcedures.uspRollbackFromProc  
Go  
  
-- Execute procedure.  
BEGIN TRY  
BEGIN TRANSACTION   
-- Perform other actions.  
Exec uspRollbackFromProc  
-- Perform other actions.  
PRINT N'Commiting transaction...'  
COMMIT TRANSACTION  
END TRY  
  
BEGIN CATCH  
SELECT ERROR_NUMBER() AS ErrorNum, ERROR_MESSAGE() AS ErrorMessage  
PRINT N'Exception thrown, rolling back transaction.'  
ROLLBACK TRANSACTION  
PRINT N'Transaction rolled back.'   
END CATCH  
Go  
  
-- Clean up.  
DROP Procedure uspRollbackFromProc;  
Go  
DROP ASSEMBLY TestProcs;  
Go  
```  
  
## <a name="see-also"></a><span data-ttu-id="527f1-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="527f1-134">See Also</span></span>  
 [<span data-ttu-id="527f1-135">CLR 整合和交易</span><span class="sxs-lookup"><span data-stu-id="527f1-135">CLR Integration and Transactions</span></span>](../native-client-ole-db-transactions/transactions.md)  
  
  
