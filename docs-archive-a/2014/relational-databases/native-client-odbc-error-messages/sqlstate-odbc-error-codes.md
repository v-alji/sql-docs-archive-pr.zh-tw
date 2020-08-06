---
title: SQLSTATE (ODBC 錯誤碼) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- ODBC error handling, cause information
- messages [ODBC], cause information
- SQLSTATEs
- errors [ODBC], cause information
ms.assetid: 84cce528-edb0-473f-a85f-3eb87fbe2cf3
author: rothja
ms.author: jroth
ms.openlocfilehash: ff3ec0a5cdc8f24f34e42849f7c8f6d1d9d41478
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584486"
---
# <a name="sqlstate-odbc-error-codes"></a><span data-ttu-id="46d3e-102">SQLSTATE (ODBC 錯誤碼)</span><span class="sxs-lookup"><span data-stu-id="46d3e-102">SQLSTATE (ODBC Error Codes)</span></span>
  <span data-ttu-id="46d3e-103">SQLSTATE 會提供警告或錯誤原因的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="46d3e-103">SQLSTATE provides detailed information about the cause of a warning or error.</span></span> <span data-ttu-id="46d3e-104">對於偵測到並傳回的資料來源發生的錯誤 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE Client ODBC 驅動程式會將傳回的原生錯誤號碼對應至適當的 SQLSTATE。</span><span class="sxs-lookup"><span data-stu-id="46d3e-104">For errors that occur in the data source detected and returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver maps the returned native error number to the appropriate SQLSTATE.</span></span> <span data-ttu-id="46d3e-105">如果原生錯誤號碼沒有要對應的 ODBC 錯誤碼， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式會傳回 SQLSTATE 42000 ( 「語法錯誤或存取違規」 ) 。</span><span class="sxs-lookup"><span data-stu-id="46d3e-105">If a native error number does not have an ODBC error code to map to, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver returns SQLSTATE 42000 ("syntax error or access violation").</span></span> <span data-ttu-id="46d3e-106">對於驅動程式所偵測到的錯誤， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式會產生適當的 SQLSTATE。</span><span class="sxs-lookup"><span data-stu-id="46d3e-106">For errors that are detected by the driver, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver generates the appropriate SQLSTATE.</span></span>  
  
 <span data-ttu-id="46d3e-107">如需有關狀態錯誤碼的詳細資訊，請查看下列主題：</span><span class="sxs-lookup"><span data-stu-id="46d3e-107">For more information about the state error codes, see the following topics:</span></span>  
  
-   [<span data-ttu-id="46d3e-108">附錄 A：ODBC 錯誤碼</span><span class="sxs-lookup"><span data-stu-id="46d3e-108">Appendix A: ODBC Error Codes</span></span>](https://go.microsoft.com/fwlink/?LinkId=89356)  
  
-   [<span data-ttu-id="46d3e-109">SQLSTATE 對應</span><span class="sxs-lookup"><span data-stu-id="46d3e-109">SQLSTATE Mappings</span></span>](https://go.microsoft.com/fwlink/?LinkId=89355)  
  
## <a name="see-also"></a><span data-ttu-id="46d3e-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46d3e-110">See Also</span></span>  
 [<span data-ttu-id="46d3e-111">處理錯誤與訊息</span><span class="sxs-lookup"><span data-stu-id="46d3e-111">Handling Errors and Messages</span></span>](handling-errors-and-messages.md)  
  
  
