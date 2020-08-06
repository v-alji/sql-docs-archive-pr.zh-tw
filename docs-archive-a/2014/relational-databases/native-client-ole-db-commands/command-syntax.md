---
title: 命令語法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, commands
- commands [OLE DB]
- SQL Server Native Client OLE DB provider, stored procedures
- stored procedures [OLE DB], command syntax
ms.assetid: d463d3d7-e5cb-426d-8e92-aa29980356b6
author: rothja
ms.author: jroth
ms.openlocfilehash: da5ddb75a5c6fc10db031707b7d97ead71363e9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709269"
---
# <a name="command-syntax"></a><span data-ttu-id="c9e90-102">命令語法</span><span class="sxs-lookup"><span data-stu-id="c9e90-102">Command Syntax</span></span>
  <span data-ttu-id="c9e90-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會辨識 DBGUID_SQL 宏指定的命令語法。</span><span class="sxs-lookup"><span data-stu-id="c9e90-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider recognizes command syntax specified by the DBGUID_SQL macro.</span></span> <span data-ttu-id="c9e90-104">對於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者，此規範表示 ODBC SQL、ISO 和的混合物 [!INCLUDE[tsql](../../includes/tsql-md.md)] 是有效的語法。</span><span class="sxs-lookup"><span data-stu-id="c9e90-104">For the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, the specifier indicates that an amalgam of ODBC SQL, ISO, and [!INCLUDE[tsql](../../includes/tsql-md.md)] is valid syntax.</span></span> <span data-ttu-id="c9e90-105">例如，下列 SQL 陳述式會使用 ODBC SQL 逸出序列來指定 LCASE 字串函數：</span><span class="sxs-lookup"><span data-stu-id="c9e90-105">For example, the following SQL statement uses an ODBC SQL escape sequence to specify the LCASE string function:</span></span>  
  
```  
SELECT customerid={fn LCASE(CustomerID)} FROM Customers  
```  
  
 <span data-ttu-id="c9e90-106">LCASE 會傳回字元字串，將所有大寫字元轉換為其小寫的對等項目。</span><span class="sxs-lookup"><span data-stu-id="c9e90-106">LCASE returns a character string, converting all uppercase characters to their lowercase equivalents.</span></span> <span data-ttu-id="c9e90-107">ISO 字串函數 LOWER 會執行相同的作業，因此，下列 SQL 陳述式是相當於以上所顯示之 ODBC 陳述式的 ISO：</span><span class="sxs-lookup"><span data-stu-id="c9e90-107">The ISO string function LOWER performs the same operation, so the following SQL statement is a ISO equivalent to the ODBC statement presented above:</span></span>  
  
```  
SELECT customerid=LOWER(CustomerID) FROM Customers  
```  
  
 <span data-ttu-id="c9e90-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]當指定為命令的文字時，Native Client OLE DB 提供者會成功處理任一種語句的形式。</span><span class="sxs-lookup"><span data-stu-id="c9e90-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider processes either form of the statement successfully when specified as text for a command.</span></span>  
  
## <a name="stored-procedures"></a><span data-ttu-id="c9e90-109">預存程序</span><span class="sxs-lookup"><span data-stu-id="c9e90-109">Stored Procedures</span></span>  
 <span data-ttu-id="c9e90-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者命令來執行預存程式時，請使用命令文字中的 ODBC 呼叫 escape 順序。</span><span class="sxs-lookup"><span data-stu-id="c9e90-110">When executing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedure using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider command, use the ODBC CALL escape sequence in the command text.</span></span> <span data-ttu-id="c9e90-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接著，Native Client OLE DB 提供者會使用的遠端程序呼叫機制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 來優化命令處理。</span><span class="sxs-lookup"><span data-stu-id="c9e90-111">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider then uses the remote procedure call mechanism of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to optimize command processing.</span></span> <span data-ttu-id="c9e90-112">例如，下列 ODBC SQL 陳述式是比 [!INCLUDE[tsql](../../includes/tsql-md.md)] 形式慣用的命令文字：</span><span class="sxs-lookup"><span data-stu-id="c9e90-112">For example, the following ODBC SQL statement is preferred command text over the [!INCLUDE[tsql](../../includes/tsql-md.md)] form:</span></span>  
  
-   <span data-ttu-id="c9e90-113">ODBC SQL</span><span class="sxs-lookup"><span data-stu-id="c9e90-113">ODBC SQL</span></span>  
  
    ```  
    {call SalesByCategory('Produce', '1995')}  
    ```  
  
-   <span data-ttu-id="c9e90-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c9e90-114">Transact-SQL</span></span>  
  
    ```  
    EXECUTE SalesByCategory 'Produce', '1995'  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c9e90-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9e90-115">See Also</span></span>  
 [<span data-ttu-id="c9e90-116">命令</span><span class="sxs-lookup"><span data-stu-id="c9e90-116">Commands</span></span>](commands.md)  
  
  
