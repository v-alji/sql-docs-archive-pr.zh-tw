---
title: 逸出 SQL Server 識別碼 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 8a73e945-daa6-4e5d-93da-10f000f1f3a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1821187632aeeea0b7a18bf9c4d51d933e947d43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596060"
---
# <a name="escape-sql-server-identifiers"></a><span data-ttu-id="4da3d-102">逸出 SQL Server 識別碼</span><span class="sxs-lookup"><span data-stu-id="4da3d-102">Escape SQL Server Identifiers</span></span>
  <span data-ttu-id="4da3d-103">您可以經常使用 Windows PowerShell 反勾號逸出字元 (\`) 來逸出 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 分隔識別碼中所允許，但是 Windows PowerShell 路徑名稱所不允許的字元。</span><span class="sxs-lookup"><span data-stu-id="4da3d-103">You can often use the Windows PowerShell back-tick escape character (\`) to escape characters that are allowed in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] delimited identifiers but not Windows PowerShell path names.</span></span> <span data-ttu-id="4da3d-104">但是，某些字元無法逸出。</span><span class="sxs-lookup"><span data-stu-id="4da3d-104">Some characters, however, cannot be escaped.</span></span> <span data-ttu-id="4da3d-105">例如，您無法逸出 Windows PowerShell 中的冒號字元 (:)。</span><span class="sxs-lookup"><span data-stu-id="4da3d-105">For example, you cannot escape the colon character (:) in Windows PowerShell.</span></span> <span data-ttu-id="4da3d-106">具有該字元的識別碼必須加以編碼。</span><span class="sxs-lookup"><span data-stu-id="4da3d-106">Identifiers with that character must be encoded.</span></span> <span data-ttu-id="4da3d-107">編碼比逸出更為可靠，因為編碼適用於所有字元。</span><span class="sxs-lookup"><span data-stu-id="4da3d-107">Encoding is more reliable than escaping because encoding works for all characters.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="4da3d-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="4da3d-108">Before You Begin</span></span>  
 <span data-ttu-id="4da3d-109">反勾號字元 (\`) 通常是在鍵盤左上方 ESC 鍵底下的按鍵上。</span><span class="sxs-lookup"><span data-stu-id="4da3d-109">The back-tick character (\`) is usually on the key in the upper left of the keyboard, under the ESC key.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4da3d-110">範例</span><span class="sxs-lookup"><span data-stu-id="4da3d-110">Examples</span></span>  
 <span data-ttu-id="4da3d-111">這是逸出 # 字元的範例：</span><span class="sxs-lookup"><span data-stu-id="4da3d-111">This is an example of escaping a # character:</span></span>  
  
```  
cd SQLSERVER:\SQL\MyComputer\MyInstance\MyDatabase\MySchema\`#MyTempTable  
```  
  
 <span data-ttu-id="4da3d-112">這是指定 (local) 做為電腦名稱時的逸出括號範例：</span><span class="sxs-lookup"><span data-stu-id="4da3d-112">This is an example of escaping the parenthesis when specifying (local) as a computer name:</span></span>  
  
```  
Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
```  
  
## <a name="see-also"></a><span data-ttu-id="4da3d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4da3d-113">See Also</span></span>  
 <span data-ttu-id="4da3d-114">[PowerShell 中的 SQL Server 識別碼](sql-server-identifiers-in-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="4da3d-114">[SQL Server Identifiers in PowerShell](sql-server-identifiers-in-powershell.md) </span></span>  
 <span data-ttu-id="4da3d-115">[SQL Server PowerShell 提供者](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="4da3d-115">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="4da3d-116">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="4da3d-116">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
  
  
