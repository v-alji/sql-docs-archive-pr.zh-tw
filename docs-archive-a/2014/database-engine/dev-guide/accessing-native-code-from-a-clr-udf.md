---
title: 從 CLR UDF 存取機器碼 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: 161afa9d-74a1-40f5-af17-162e355e7a46
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d36e93fc39e9231a4d8677535c6e13c905d55a4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593552"
---
# <a name="accessing-native-code-from-a-clr-udf"></a><span data-ttu-id="03ed1-102">從 CLR UDF 存取機器碼</span><span class="sxs-lookup"><span data-stu-id="03ed1-102">Accessing Native Code from a CLR UDF</span></span>
  <span data-ttu-id="03ed1-103">這個範例會示範如何從資料庫內組件中的使用者定義函數來叫用原生 (Unmanaged) C++ 程式碼的函數。</span><span class="sxs-lookup"><span data-stu-id="03ed1-103">This example shows how to invoke a function in native (unmanaged) C++ code from a user-defined function in an assembly, in your database.</span></span>  
  
 <span data-ttu-id="03ed1-104">在此範例中，工作目錄應為 `c:\test` 。</span><span class="sxs-lookup"><span data-stu-id="03ed1-104">For this example, the working directory should be `c:\test`.</span></span>  
  
 <span data-ttu-id="03ed1-105">請先編譯 C++ 程式碼：</span><span class="sxs-lookup"><span data-stu-id="03ed1-105">First compile the C++ code:</span></span>  
  
```  
// Win32Sleep.cpp  
// compile with: /LD /link /noentry kernel32.lib  
#include <windows.h>  
  
extern "C"  
__declspec( dllexport ) void _cdecl SleepyLoop(DWORD sleep_interval) {  
   Sleep(sleep_interval);  
}  
```  
  
 <span data-ttu-id="03ed1-106">接下來，將 C# 程式碼編譯為組件：</span><span class="sxs-lookup"><span data-stu-id="03ed1-106">Next, compile the C# code to an assembly:</span></span>  
  
```  
// proc.cs  
// compile with: /target:library  
using System;  
using System.Threading;  
using System.Data.Sql;  
using System.Runtime.InteropServices;  
  
public class StoreProcedures {  
  
   public static readonly uint SLEEP_LOOP_TIMES = 10;  
   public static readonly uint SLEEP_DURATION = 1000;  
  
   [DllImport(@"c:\test\Win32Sleep.dll")]  
   internal static extern void SleepyLoop(uint sleepInterval);  
  
   public static void SleepInProcedure(int loopTimes) {  
      for ( int i = 0 ; i < loopTimes ; i++ ) {  
         // invoke the unmanaged routine  
         SleepyLoop(SLEEP_DURATION);  
      }  
   }  
}  
```  
  
 <span data-ttu-id="03ed1-107">最後，執行下列 [!INCLUDE[tsql](../../includes/tsql-md.md)]：</span><span class="sxs-lookup"><span data-stu-id="03ed1-107">Finally, execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)]:</span></span>  
  
```  
USE MASTER  
GO  
  
IF DB_ID('testdb') IS NOT NULL  
DROP DATABASE testdb  
GO  
  
CREATE DATABASE testdb  
GO  
  
USE testdb  
GO  
  
ALTER DATABASE testdb SET TRUSTWORTHY ON   
GO  
  
sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
  
CREATE ASSEMBLY myasm FROM 'c:\test\proc.dll' WITH PERMISSION_SET=UNSAFE   
go  
  
CREATE PROCEDURE SleepProc(@loopTimes INT)  
AS EXTERNAL NAME myasm.[StoreProcedures].[SleepInProcedure]  
go  
  
-- sleep 5 seconds  
EXEC SleepProc 5  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="03ed1-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03ed1-108">See Also</span></span>  
 [<span data-ttu-id="03ed1-109">通用語言執行平台 &#40;CLR&#41; 整合的使用案例和範例</span><span class="sxs-lookup"><span data-stu-id="03ed1-109">Usage Scenarios and Examples for Common Language Runtime &#40;CLR&#41; Integration</span></span>](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  
