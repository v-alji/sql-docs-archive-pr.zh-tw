---
title: 內容連接 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context connections [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- context [CLR integration]
ms.assetid: 67dd1925-d672-4986-a85f-bce4fe832ef7
author: rothja
ms.author: jroth
ms.openlocfilehash: 82c739aa9c1952c71e9a16aaa68ec999851b3202
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595120"
---
# <a name="context-connection"></a><span data-ttu-id="f6ff3-102">內容連接</span><span class="sxs-lookup"><span data-stu-id="f6ff3-102">Context Connection</span></span>
  <span data-ttu-id="f6ff3-103">內部資料存取的問題是很常見的案例。</span><span class="sxs-lookup"><span data-stu-id="f6ff3-103">The problem of internal data access is a fairly common scenario.</span></span> <span data-ttu-id="f6ff3-104">也就是說，您想要存取執行 Commn Language Runtime (CLR) 預存程序或函數所在的同一部伺服器。</span><span class="sxs-lookup"><span data-stu-id="f6ff3-104">That is, you wish to access the same server on which your common language runtime (CLR) stored procedure or function is executing.</span></span> <span data-ttu-id="f6ff3-105">有一個選擇是使用 `System.Data.SqlClient.SqlConnection` 建立連接，指定指向本機伺服器的連接字串，並開啟連接。</span><span class="sxs-lookup"><span data-stu-id="f6ff3-105">One option is to create a connection using `System.Data.SqlClient.SqlConnection`, specify a connection string that points to the local server, and open the connection.</span></span> <span data-ttu-id="f6ff3-106">這需要指定認證以進行登入。</span><span class="sxs-lookup"><span data-stu-id="f6ff3-106">This requires specifying credentials for logging in.</span></span> <span data-ttu-id="f6ff3-107">連接與預存程序或函數位於不同的資料庫工作階段中，因此可能會具有不同的 `SET` 選項、位於單獨交易中，或是找不到暫存資料表等。</span><span class="sxs-lookup"><span data-stu-id="f6ff3-107">The connection is in a different database session than the stored procedure or function, it may have different `SET` options, it is in a separate transaction, it does not see your temporary tables, and so on.</span></span> <span data-ttu-id="f6ff3-108">如果 Managed 預存程序或函數程式碼是在 SQL Server 處理序中執行的，則會是因為其他使用者已連接至該伺服器並執行 SQL 陳述式來叫用它。</span><span class="sxs-lookup"><span data-stu-id="f6ff3-108">If your managed stored procedure or function code is executing in the SQL Server process, it is because someone connected to that server and executed a SQL statement to invoke it.</span></span> <span data-ttu-id="f6ff3-109">您可能會想讓預存程序或函數在該連接的內容及其交易、`SET` 選項等條件中執行。</span><span class="sxs-lookup"><span data-stu-id="f6ff3-109">You probably want the stored procedure or function to execute in the context of that connection, along with its transaction, `SET` options, and so on.</span></span> <span data-ttu-id="f6ff3-110">這就稱為內容連接。</span><span class="sxs-lookup"><span data-stu-id="f6ff3-110">This is called the context connection.</span></span>  
  
 <span data-ttu-id="f6ff3-111">內容連接可讓您在第一次叫用程式碼的同一內容中執行 Transact-SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="f6ff3-111">The context connection lets you execute Transact-SQL statements in the same context that your code was invoked in the first place.</span></span> <span data-ttu-id="f6ff3-112">為了取得內容連接，必須使用 "context connection" 連接字串關鍵字，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="f6ff3-112">In order to obtain the context connection, you must use the "context connection" connection string keyword, as in the example below:</span></span>  
  
 <span data-ttu-id="f6ff3-113">[C#]</span><span class="sxs-lookup"><span data-stu-id="f6ff3-113">[C#]</span></span>  
  
```  
using(SqlConnection connection = new SqlConnection("context connection=true"))   
{  
    connection.Open();  
    // Use the connection  
}  
```  
  
 <span data-ttu-id="f6ff3-114">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="f6ff3-114">[Visual Basic]</span></span>  
  
```  
Using connection as new SqlConnection("context connection=true")  
    connection.Open()  
    ' Use the connection  
End Using  
  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="f6ff3-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="f6ff3-115">In This Section</span></span>  
 [<span data-ttu-id="f6ff3-116">一般連線與內容連接</span><span class="sxs-lookup"><span data-stu-id="f6ff3-116">Regular vs. Context Connections</span></span>](context-connections-vs-regular-connections.md)  
 <span data-ttu-id="f6ff3-117">描述正常連接及內容連接之間的差異。</span><span class="sxs-lookup"><span data-stu-id="f6ff3-117">Describes the differences between regular and context connections.</span></span>  
  
 [<span data-ttu-id="f6ff3-118">一般和內容連接的限制</span><span class="sxs-lookup"><span data-stu-id="f6ff3-118">Restrictions on Regular and Context Connections</span></span>](context-connections-and-regular-connections-restrictions.md)  
 <span data-ttu-id="f6ff3-119">描述正常連接及內容連接的限制。</span><span class="sxs-lookup"><span data-stu-id="f6ff3-119">Describes the restrictions on regular and context connections.</span></span>  
  
  
