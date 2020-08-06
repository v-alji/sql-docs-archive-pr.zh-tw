---
title: SQL Server Native Client 11.0 中的 UTF-16 支援 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
author: rothja
ms.author: jroth
ms.openlocfilehash: af8581071400db888fb508b88f8e8ae93bc71f70
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598314"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a><span data-ttu-id="b7ee6-102">SQL Server Native Client 11.0 中的 UTF-16 支援</span><span class="sxs-lookup"><span data-stu-id="b7ee6-102">UTF-16 Support in SQL Server Native Client 11.0</span></span>
  <span data-ttu-id="b7ee6-103">從開始 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ，如果您在系結資料行結果或輸出參數時提供固定長度的緩衝區，而且如果在 `wchar` 終止字元之前寫入緩衝區的字元是代理組的高代理程式碼點，而且下一個 `wchar` 字元是低代理程式碼點，則 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 不會將高代理程式碼點加入緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b7ee6-103">Beginning in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], if you supply a fixed-length buffer when binding a column result or output parameter and if the `wchar` character written into the buffer before the terminating character is a high surrogate code point of a surrogate pair, and if the next `wchar` character is a low surrogate code point, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client will not add the high surrogate code point to the buffer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7ee6-104">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7ee6-104">See Also</span></span>  
 [<span data-ttu-id="b7ee6-105">SQL Server Native Client 功能</span><span class="sxs-lookup"><span data-stu-id="b7ee6-105">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
