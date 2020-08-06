---
title: 處理 CLR 中的大型物件 (LOB) 參數 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- large data, CLR integration
- LOB data [SQL Server], CLR integration
- SqlBytes data type
- SqlChars data type
ms.assetid: d07956f6-9543-4476-9426-536f95991150
author: rothja
ms.author: jroth
ms.openlocfilehash: ee791c73a6610761c2086723f9e41c2351b37dd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709637"
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a><span data-ttu-id="bfd24-102">處理 CLR 中的大型物件 (LOB) 參數</span><span class="sxs-lookup"><span data-stu-id="bfd24-102">Handling Large Object (LOB) Parameters in the CLR</span></span>
  <span data-ttu-id="bfd24-103">使用 `SqlBytes` 和 `SqlChars` 分別傳遞大型物件 (LOB) 二進位類型 (`varbinary(max)`) 和 LOB 字元類型 (`nvarchar(max)`) 參數。</span><span class="sxs-lookup"><span data-stu-id="bfd24-103">Use `SqlBytes` and `SqlChars` to pass large object (LOB) binary type (`varbinary(max)`) and LOB character type (`nvarchar(max)`) parameters, respectively.</span></span> <span data-ttu-id="bfd24-104">這些類型允許將 LOB 值從資料庫串流到 Common Language Runtime (CLR) 常式，而非將整個值複製到 Managed 空間。</span><span class="sxs-lookup"><span data-stu-id="bfd24-104">These types allow streaming the LOB values from the database to the common language runtime (CLR) routine, instead of copying the entire value into managed space.</span></span> <span data-ttu-id="bfd24-105">`SqlBinary` 和 `SqlString` 應該僅用於小型二進位和字元字串值。</span><span class="sxs-lookup"><span data-stu-id="bfd24-105">`SqlBinary` and `SqlString` should be used only for small binary and character string values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfd24-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfd24-106">See Also</span></span>  
 [<span data-ttu-id="bfd24-107">.NET Framework 的 SQL Server 資料類型</span><span class="sxs-lookup"><span data-stu-id="bfd24-107">SQL Server Data Types in the .NET Framework</span></span>](sql-server-data-types-in-the-net-framework.md)  
  
  
