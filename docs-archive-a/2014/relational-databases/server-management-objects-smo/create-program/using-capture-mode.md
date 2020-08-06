---
title: 使用 Capture 模式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, capture mode
- capture mode [SMO]
- SMO [SQL Server], capture mode
ms.assetid: ace29bf0-705a-434f-82e4-db99d01c5008
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4ac69b9403329846b38c7ff61c645eb9879b6225
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704005"
---
# <a name="using-capture-mode"></a><span data-ttu-id="d2834-102">使用擷取模式</span><span class="sxs-lookup"><span data-stu-id="d2834-102">Using Capture Mode</span></span>
  <span data-ttu-id="d2834-103">SMO 程式可以擷取與記錄程式所發出的相等 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式來取代程式所執行的陳述式，或是加上程式所執行的陳述式。</span><span class="sxs-lookup"><span data-stu-id="d2834-103">SMO programs can capture and record the equivalent [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements issued by the program in place of, or in addition to, the statements that are executed by the program.</span></span> <span data-ttu-id="d2834-104">您可以使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件，或使用 <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> 物件的 <xref:Microsoft.SqlServer.Management.Smo.Server> 屬性來啟用擷取模式。</span><span class="sxs-lookup"><span data-stu-id="d2834-104">You enable capture mode by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object, or by using the <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2834-105">範例</span><span class="sxs-lookup"><span data-stu-id="d2834-105">Example</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="enabling-capture-mode-in-visual-basic"></a><span data-ttu-id="d2834-106">在 Visual Basic 中啟用擷取模式</span><span class="sxs-lookup"><span data-stu-id="d2834-106">Enabling Capture Mode in Visual Basic</span></span>  
 <span data-ttu-id="d2834-107">此程式碼範例會啟用擷取模式，然後顯示擷取緩衝區中保留的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 命令。</span><span class="sxs-lookup"><span data-stu-id="d2834-107">This code example enables capture mode, and then displays the [!INCLUDE[tsql](../../../includes/tsql-md.md)] commands held in the capture buffer.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBCapture1](SMO How to#SMO_VBCapture1)]  -->  
  
## <a name="enabling-capture-mode-in-visual-c"></a><span data-ttu-id="d2834-108">在 Visual C# 中啟用擷取模式</span><span class="sxs-lookup"><span data-stu-id="d2834-108">Enabling Capture Mode in Visual C#</span></span>  
 <span data-ttu-id="d2834-109">此程式碼範例會啟用擷取模式，然後顯示擷取緩衝區中保留的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 命令。</span><span class="sxs-lookup"><span data-stu-id="d2834-109">This code example enables capture mode, and then displays the [!INCLUDE[tsql](../../../includes/tsql-md.md)] commands held in the capture buffer.</span></span>  
  
```  
{   
// Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
// Set the execution mode to CaptureSql for the connection.   
srv.ConnectionContext.SqlExecutionModes = SqlExecutionModes.CaptureSql;   
// Make a modification to the server that is to be captured.   
srv.UserOptions.AnsiNulls = true;   
srv.Alter();   
// Iterate through the strings in the capture buffer and display the captured statements.   
string s;   
foreach ( String p_s in srv.ConnectionContext.CapturedSql.Text ) {   
   Console.WriteLine(p_s);   
}   
// Execute the captured statements.   
srv.ConnectionContext.ExecuteNonQuery(srv.ConnectionContext.CapturedSql.Text);   
// Revert to immediate execution mode.   
srv.ConnectionContext.SqlExecutionModes = SqlExecutionModes.ExecuteSql;   
}  
```  
  
  
