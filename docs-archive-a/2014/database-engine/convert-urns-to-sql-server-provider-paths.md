---
title: 將 URN 轉換成 SQL Server 提供者路徑 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c9b1b8f1-b117-4e87-9704-2170f62c5c8b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 56c2fdb5f84e57fe3f34348108f14418785659a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596268"
---
# <a name="convert-urns-to-sql-server-provider-paths"></a><span data-ttu-id="dda2e-102">將 URN 轉換成 SQL Server 提供者路徑</span><span class="sxs-lookup"><span data-stu-id="dda2e-102">Convert URNs to SQL Server Provider Paths</span></span>
  <span data-ttu-id="dda2e-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理物件模型 (SMO) 會針對它的物件建立統一資源名稱 (URN)。</span><span class="sxs-lookup"><span data-stu-id="dda2e-103">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Object model (SMO) builds Uniform Resource Names (URN) for its objects.</span></span> <span data-ttu-id="dda2e-104">每個 URN 都可以唯一識別 SMO 物件，而且可以使用 `Convert-UrnToPath` Cmdlet 來轉換為 SQL Server PowerShell 提供者路徑。</span><span class="sxs-lookup"><span data-stu-id="dda2e-104">Each URN uniquely identifies a SMO object, and can be converted to a SQL Server PowerShell provider path by using the `Convert-UrnToPath` cmdlet.</span></span>  
  
## <a name="converting-urns-to-paths"></a><span data-ttu-id="dda2e-105">將 URN 轉換成路徑</span><span class="sxs-lookup"><span data-stu-id="dda2e-105">Converting URNs to Paths</span></span>  
 <span data-ttu-id="dda2e-106">每一個 URN 都有與物件之路徑相同的資訊，但是格式會不同。</span><span class="sxs-lookup"><span data-stu-id="dda2e-106">Each URN has the same information as a path to the object, but in a different form.</span></span> <span data-ttu-id="dda2e-107">例如，以下為資料表的路徑：</span><span class="sxs-lookup"><span data-stu-id="dda2e-107">For example, this is the path to a table:</span></span>  
  
 <span data-ttu-id="dda2e-108">SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Address</span><span class="sxs-lookup"><span data-stu-id="dda2e-108">SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Address</span></span>  
  
 <span data-ttu-id="dda2e-109">以下是相同物件的 URN：</span><span class="sxs-lookup"><span data-stu-id="dda2e-109">And this is the URN to the same object:</span></span>  
  
 <span data-ttu-id="dda2e-110">Server[@Name='MyComputer']\Database[@Name='AdventureWorks2012']\Table[@Name='Address' and @Schema='Person']</span><span class="sxs-lookup"><span data-stu-id="dda2e-110">Server[@Name='MyComputer']\Database[@Name='AdventureWorks2012']\Table[@Name='Address' and @Schema='Person']</span></span>  
  
 <span data-ttu-id="dda2e-111">若您已在 PowerShell 指令碼中建立 SMO 物件，則可以參考 `Urn` 屬性以取得物件的 URN，然後使用 `Convert-UrnToPath` 指令程式，將 SMO URN 字串轉換為 Windows PowerShell 路徑。</span><span class="sxs-lookup"><span data-stu-id="dda2e-111">If you have created a SMO object in a PowerShell script, you can reference the `Urn` property to get the URN for the object, and then use the `Convert-UrnToPath` cmdlet to convert the SMO URN string to a Windows PowerShell path.</span></span> <span data-ttu-id="dda2e-112">然後，您可以使用提供者導覽至路徑上的不同位置。</span><span class="sxs-lookup"><span data-stu-id="dda2e-112">You can then use the provider to navigate to different locations on the path.</span></span>  
  
 <span data-ttu-id="dda2e-113">如果節點名稱包含 Windows PowerShell 路徑名稱不支援的擴充字元，則 `Convert-UrnToPath` 會在其十六進位表示法中編碼這些字元。</span><span class="sxs-lookup"><span data-stu-id="dda2e-113">If node names contain extended characters that are not supported in Windows PowerShell path names, `Convert-UrnToPath` encodes them in their hexadecimal representation.</span></span> <span data-ttu-id="dda2e-114">例如，"My:Table" 會以 "My%3ATable" 的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="dda2e-114">For example "My:Table" is returned as "My%3ATable".</span></span>  
  
 <span data-ttu-id="dda2e-115">在 Windows PowerShell 中，如需使用 Cmdlet 的範例，請執行：</span><span class="sxs-lookup"><span data-stu-id="dda2e-115">For examples of using the cmdlet, in Windows PowerShell, run:</span></span>  
  
```powershell
Get-Help Convert-UrnToPath -Examples  
```  
  
## <a name="see-also"></a><span data-ttu-id="dda2e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dda2e-116">See Also</span></span>  
 <span data-ttu-id="dda2e-117">[查詢運算式和統一資源名稱](../powershell/query-expressions-and-uniform-resource-names.md) </span><span class="sxs-lookup"><span data-stu-id="dda2e-117">[Query Expressions and Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md) </span></span>  
 <span data-ttu-id="dda2e-118">[SQL Server PowerShell 提供者](../powershell/sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="dda2e-118">[SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="dda2e-119">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="dda2e-119">SQL Server PowerShell</span></span>](../powershell/sql-server-powershell.md)  
