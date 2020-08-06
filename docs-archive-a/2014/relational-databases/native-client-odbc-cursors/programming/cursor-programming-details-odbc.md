---
title: ODBC) 的資料指標程式設計細節 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC applications, cursors
- ODBC cursors, programming
- cursors [ODBC], programming
ms.assetid: 6bae29c4-7f49-419c-8712-90db734f992e
author: rothja
ms.author: jroth
ms.openlocfilehash: 4108e195c16d321578a70852dd990f4f8d658832
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594063"
---
# <a name="cursor-programming-details-odbc"></a><span data-ttu-id="8266e-102">資料指標程式設計詳細內容 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="8266e-102">Cursor Programming Details (ODBC)</span></span>
  <span data-ttu-id="8266e-103">選擇正確的資料指標類型可以改善應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="8266e-103">Choosing the correct cursor type can improve application performance.</span></span> <span data-ttu-id="8266e-104">在某些情況下，當您執行所要求之資料指標類型不支援的 SQL 陳述式時，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 可能會隱含轉換資料指標類型。</span><span class="sxs-lookup"><span data-stu-id="8266e-104">Under certain conditions, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] may implicitly convert a cursor type when you execute an SQL statement that is not supported by the cursor type you requested.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8266e-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="8266e-105">In This Section</span></span>  
  
-   [<span data-ttu-id="8266e-106">&#40;ODBC&#41;的隱含資料指標轉換</span><span class="sxs-lookup"><span data-stu-id="8266e-106">Implicit Cursor Conversions &#40;ODBC&#41;</span></span>](implicit-cursor-conversions-odbc.md)  
  
-   [<span data-ttu-id="8266e-107">使用自動擷取搭配 ODBC 資料指標</span><span class="sxs-lookup"><span data-stu-id="8266e-107">Using Autofetch with ODBC Cursors</span></span>](using-autofetch-with-odbc-cursors.md)  
  
-   [<span data-ttu-id="8266e-108">&#40;ODBC&#41;快速順向資料指標</span><span class="sxs-lookup"><span data-stu-id="8266e-108">Fast Forward-Only Cursors &#40;ODBC&#41;</span></span>](fast-forward-only-cursors-odbc.md)  
  
## <a name="see-also"></a><span data-ttu-id="8266e-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8266e-109">See Also</span></span>  
 [<span data-ttu-id="8266e-110">&#40;ODBC&#41;使用資料指標</span><span class="sxs-lookup"><span data-stu-id="8266e-110">Using Cursors &#40;ODBC&#41;</span></span>](../using-cursors-odbc.md)  
  
  
