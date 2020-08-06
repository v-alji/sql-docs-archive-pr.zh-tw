---
title: 字串長度和子字串行為的變更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 2119b7ba-2e52-44bf-ac57-82c2d46a48ff
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1188823a877b4c5dc9cef13431492dfe3b303e23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595517"
---
# <a name="changes-to-behavior-of-string-length-and-substring"></a><span data-ttu-id="6af82-102">字串長度及子字串行為的變更</span><span class="sxs-lookup"><span data-stu-id="6af82-102">Changes to behavior of string-length and substring</span></span>
  <span data-ttu-id="6af82-103">[字串長度函數 &#40;xquery&#41;](/sql/xquery/functions-on-string-values-string-length)和[Substring 函數 &#40;xquery&#41;](/sql/xquery/functions-on-string-values-substring)函數與包含代理字元的 XML 資料庫搭配使用時，可能會傳回不同的結果。</span><span class="sxs-lookup"><span data-stu-id="6af82-103">The [string-length Function &#40;XQuery&#41;](/sql/xquery/functions-on-string-values-string-length) and [substring Function &#40;XQuery&#41;](/sql/xquery/functions-on-string-values-substring) functions may return different results when used with XML databases that contain surrogate characters.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6af82-104">描述</span><span class="sxs-lookup"><span data-stu-id="6af82-104">Description</span></span>  
 <span data-ttu-id="6af82-105">當資料庫設定為與相容時 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ，[字串長度函數 &#40;xquery&#41;](/sql/xquery/functions-on-string-values-string-length)和 substring 函式的行為，會在處理 Unicode 增補字元時[&#40;xquery&#41;](/sql/xquery/functions-on-string-values-substring)函數變更。</span><span class="sxs-lookup"><span data-stu-id="6af82-105">When a database is set to be compatible with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], the behavior of the [string-length Function &#40;XQuery&#41;](/sql/xquery/functions-on-string-values-string-length) and [substring Function &#40;XQuery&#41;](/sql/xquery/functions-on-string-values-substring) functions changes when dealing with Unicode supplementary characters.</span></span> <span data-ttu-id="6af82-106">這些函數會將每個 Unicode 補充字元 (定義為具有大於 U+FFFF 的字碼指標) 計算成一個字元而非兩個，如同舊版的計算方式。</span><span class="sxs-lookup"><span data-stu-id="6af82-106">Each Unicode supplementary character, which is defined by having a code point larger than U+FFFF, is counted as one character by these functions rather than two, as it was in previous versions.</span></span>  
  
 <span data-ttu-id="6af82-107">如需代理字元的詳細資訊，請參閱[代理和補充字元](https://go.microsoft.com/fwlink/?LinkId=178317)。</span><span class="sxs-lookup"><span data-stu-id="6af82-107">For more information about surrogate characters, see [Surrogates and Supplementary Characters](https://go.microsoft.com/fwlink/?LinkId=178317).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6af82-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6af82-108">See Also</span></span>  
 <span data-ttu-id="6af82-109">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="6af82-109">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="6af82-110">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="6af82-110">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](https://docs.microsoft.com/sql/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
