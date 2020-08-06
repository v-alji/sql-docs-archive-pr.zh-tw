---
title: 已記錄與未記錄的修改 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- logged vs. nonlogged modifications [SQL Server Native Client]
- columns [ODBC]
- ODBC data types, image columns
- nonlogged vs. logged modifications
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 20aa5b27-4a2c-46e7-8356-beb0eebf4b7e
author: rothja
ms.author: jroth
ms.openlocfilehash: 8768acc75d18ea2236f0e9280e5d0c805e688107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709301"
---
# <a name="logged-vs-unlogged-modifications"></a><span data-ttu-id="054d9-102">已記錄與未記錄的修改</span><span class="sxs-lookup"><span data-stu-id="054d9-102">Logged vs. Unlogged Modifications</span></span>
  <span data-ttu-id="054d9-103">應用程式可以要求 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式不會記錄**text**、 **Ntext**和**image**修改。</span><span class="sxs-lookup"><span data-stu-id="054d9-103">An application can request that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver not log **text**, **ntext**, and **image** modifications.</span></span> <span data-ttu-id="054d9-104">但是在使用這個選項時，應該要特別小心。</span><span class="sxs-lookup"><span data-stu-id="054d9-104">Care should be used with this option, however.</span></span> <span data-ttu-id="054d9-105">只有當**text**、 **Ntext**或**image**資料不重要，而且資料擁有者願意將復原資料的能力視為較高的效能時，才應該使用此功能。</span><span class="sxs-lookup"><span data-stu-id="054d9-105">It should be used only for those situations where the **text**, **ntext**, or **image** data is not critical and data owners are willing to trade off the ability to recover data for higher performance.</span></span>  
  
 <span data-ttu-id="054d9-106">**Text**、 **Ntext**和**image**修改的記錄是藉由呼叫[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) ，並將*Attribute*參數設定為 SQL_SOPT_SS_ TEXTPTR_LOGGING，並將*valueptr 是*設定為 SQL_TL_ON 或 SQL_TL_OFF 來控制。</span><span class="sxs-lookup"><span data-stu-id="054d9-106">The logging of **text**, **ntext**, and **image** modifications is controlled by calling [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) with the *Attribute* parameter set to SQL_SOPT_SS_ TEXTPTR_LOGGING and *ValuePtr* set to either SQL_TL_ON or SQL_TL_OFF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="054d9-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="054d9-107">See Also</span></span>  
 [<span data-ttu-id="054d9-108">管理 Text 和 Image 資料行</span><span class="sxs-lookup"><span data-stu-id="054d9-108">Managing Text and Image Columns</span></span>](managing-text-and-image-columns.md)  
  
  
