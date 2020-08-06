---
title: 在90或更新版本的相容性模式中，大型常數的類型為大數數值型別 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- binary constants
- CHARINDEX function
- constants
- character string constants
- PATINDEX function
ms.assetid: 6e309fa0-5fb9-45a1-9739-f13fae525bfe
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 58acde8aaebdcac629463edcfb565eed13355ad4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585765"
---
# <a name="large-constants-are-typed-as-large-value-types-in-90-or-later-compatibility-modes"></a><span data-ttu-id="df493-102">在 90 或之後的相容性模式中，大型常數的類型為大型數值類型</span><span class="sxs-lookup"><span data-stu-id="df493-102">Large constants are typed as large-value types in 90 or later compatibility modes</span></span>
  <span data-ttu-id="df493-103">Upgrade Advisor 偵測到大型常數的存在。</span><span class="sxs-lookup"><span data-stu-id="df493-103">Upgrade Advisor detected the presence of large constants.</span></span> <span data-ttu-id="df493-104">在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 中，大小超過 8,000 個位元組的字元字串常數和二進位常數會被視為大型物件資料類型。</span><span class="sxs-lookup"><span data-stu-id="df493-104">Character string constants and binary constants that are more than 8,000 bytes in size are treated as large object data types in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="df493-105">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更新版本中，大型字元、Unicode 和二進位常數的類型是大型數值類型。</span><span class="sxs-lookup"><span data-stu-id="df493-105">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later versions, large character, Unicode, and binary constants, are typed as large-value types.</span></span>  
  
## <a name="component"></a><span data-ttu-id="df493-106">元件</span><span class="sxs-lookup"><span data-stu-id="df493-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="df493-107">描述</span><span class="sxs-lookup"><span data-stu-id="df493-107">Description</span></span>  
 <span data-ttu-id="df493-108">當字串函數 (例如 CHARINDEX 和 PATINDEX) 與超過 8,000 個位元組的字串或二進位常數搭配使用時，[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 會傳回錯誤號碼 8116，而 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 會傳回錯誤號碼 8152。</span><span class="sxs-lookup"><span data-stu-id="df493-108">When string functions, such as CHARINDEX and PATINDEX, are used with string or binary constants that exceed 8,000 bytes, [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] returns error number 8116, and [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later versions return error number 8152.</span></span>  
  
 <span data-ttu-id="df493-109">在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 中，當字串函數與 `text`、`ntext` 和 `image` 資料類型搭配使用時，會傳回錯誤 8116。</span><span class="sxs-lookup"><span data-stu-id="df493-109">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], the string functions return error 8116 when they are used with the `text`, `ntext`, and `image` data types.</span></span>  
  
 <span data-ttu-id="df493-110">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更新版本中，大型常數會分別被視為 `varchar(max)`、`nvarchar(max)` 和 `varbinary(max)` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="df493-110">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later versions, the large constants are treated as `varchar(max)`, `nvarchar(max)`, and `varbinary(max)` data types, respectively.</span></span> <span data-ttu-id="df493-111">這些資料類型與字串函數相容。</span><span class="sxs-lookup"><span data-stu-id="df493-111">These data types are compatible with string functions.</span></span>  
  
 <span data-ttu-id="df493-112">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更新版本中，字串函數 (例如 CHARINDEX 和 PATINDEX) 會假設包含要尋找之字元序列的字串小於 8,000 個位元組，</span><span class="sxs-lookup"><span data-stu-id="df493-112">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later versions, string functions, such as CHARINDEX and PATINDEX, assume the string that contains the sequence of characters to be found is less than 8,000 bytes.</span></span> <span data-ttu-id="df493-113">這就是為何會針對 CHARINDEX 和 PATINDEX 引發錯誤 8152。</span><span class="sxs-lookup"><span data-stu-id="df493-113">This is why error 8152 is raised for CHARINDEX and PATINDEX.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df493-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df493-114">See Also</span></span>  
 <span data-ttu-id="df493-115">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="df493-115">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="df493-116">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="df493-116">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
