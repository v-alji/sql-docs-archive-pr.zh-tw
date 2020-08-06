---
title: PowerShell 中的 SQL Server 識別碼 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
helpviewer_keywords:
- Cmdlets [SQL Server], Encode-Sqlname
- PowerShell [SQL Server], identifiers
- Encode-Sqlname cmdlet
- PowerShell [SQL Server], Encode-Sqlname
- Decode-Sqlname cmdlet
- PowerShell [SQL Server], Decode-Sqlname
- identifiers [SQL Server], PowerShell
- Cmdlets [SQL Server], Decode-Sqlname
ms.assetid: 651099b0-33b4-453a-a864-b067f21eb8b9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5c54fb352fb17c099bda78c80f00f91dbba428f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698338"
---
# <a name="sql-server-identifiers-in-powershell"></a><span data-ttu-id="4a544-102">PowerShell 中的 SQL Server 識別碼</span><span class="sxs-lookup"><span data-stu-id="4a544-102">SQL Server Identifiers in PowerShell</span></span>
  <span data-ttu-id="4a544-103">適用於 Windows PowerShell 的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供者會使用 Windows PowerShell 路徑中的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 識別碼。</span><span class="sxs-lookup"><span data-stu-id="4a544-103">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider for Windows PowerShell uses [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifiers in Windows PowerShell paths.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="4a544-104">識別碼可能包含 Windows PowerShell 路徑中不支援的字元。</span><span class="sxs-lookup"><span data-stu-id="4a544-104">identifiers can contain characters that Windows PowerShell does not support in paths.</span></span> <span data-ttu-id="4a544-105">當您使用 Windows PowerShell 路徑中的識別碼時，必須逸出這些字元或針對這些字元使用特殊編碼。</span><span class="sxs-lookup"><span data-stu-id="4a544-105">You must escape these characters or use special encoding for them when using the identifiers in Windows PowerShell paths.</span></span>  
  
## <a name="sql-server-identifiers-in-windows-powershell-paths"></a><span data-ttu-id="4a544-106">Windows PowerShell 路徑中的 SQL Server 識別碼</span><span class="sxs-lookup"><span data-stu-id="4a544-106">SQL Server Identifiers in Windows PowerShell Paths</span></span>  
 <span data-ttu-id="4a544-107">Windows PowerShell 提供者會使用與 Windows 檔案系統所使用之路徑結構類似的結構來公開資料階層。</span><span class="sxs-lookup"><span data-stu-id="4a544-107">Windows PowerShell providers expose data hierarchies using a path structure similar to that used for the Windows file system.</span></span> <span data-ttu-id="4a544-108">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供者會實作 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 物件的路徑。</span><span class="sxs-lookup"><span data-stu-id="4a544-108">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider implements paths to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects.</span></span> <span data-ttu-id="4a544-109">如果是 [!INCLUDE[ssDE](../includes/ssde-md.md)]，磁碟機會設定為 SQLSERVER:、第一個資料夾會設定為 \SQL，而且資料庫物件會當做容器和項目來參考。</span><span class="sxs-lookup"><span data-stu-id="4a544-109">For the [!INCLUDE[ssDE](../includes/ssde-md.md)], the drive is set to SQLSERVER:, the first folder is set to \SQL, and the database objects are referenced as containers and items.</span></span> <span data-ttu-id="4a544-110">這是預設 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 執行個體中 [!INCLUDE[ssDE](../includes/ssde-md.md)]資料庫之 Purchasing 結構描述的 Vendor 資料表路徑：</span><span class="sxs-lookup"><span data-stu-id="4a544-110">This is the path to the Vendor table in the Purchasing schema of the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database in a default instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)]:</span></span>  
  
```  
SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Purchasing.Vendor  
```  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="4a544-111">識別碼為 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 物件的名稱，例如資料表或資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="4a544-111">identifiers are the names of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects, such as table or column names.</span></span> <span data-ttu-id="4a544-112">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 識別碼有兩種：</span><span class="sxs-lookup"><span data-stu-id="4a544-112">There are two types of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifiers:</span></span>  
  
-   <span data-ttu-id="4a544-113">一般識別碼限制為 Windows PowerShell 路徑中也支援的一組字元。</span><span class="sxs-lookup"><span data-stu-id="4a544-113">Regular identifiers are limited to a set of characters that are also supported in Windows PowerShell paths.</span></span> <span data-ttu-id="4a544-114">這些名稱可以在 Windows PowerShell 路徑中使用，而不需變更。</span><span class="sxs-lookup"><span data-stu-id="4a544-114">These names can be used in Windows PowerShell paths without being changed.</span></span>  
  
-   <span data-ttu-id="4a544-115">分隔識別碼可以使用 Windows PowerShell 路徑名稱中不支援的字元。</span><span class="sxs-lookup"><span data-stu-id="4a544-115">Delimited identifiers can use characters not supported in Windows PowerShell path names.</span></span> <span data-ttu-id="4a544-116">分隔識別碼如果放在括號內 ([IdentifierName])，則稱為括號識別碼，而如果是放在雙引號內 ("IdentifierName")，則稱為引號識別碼。</span><span class="sxs-lookup"><span data-stu-id="4a544-116">Delimited identifiers are called bracketed identifiers if they are enclosed in brackets ([IdentifierName]) and quoted identifiers if they are enclosed in double quotes ("IdentifierName").</span></span> <span data-ttu-id="4a544-117">如果分隔識別碼使用 Windows PowerShell 路徑中不支援的字元，這些字元必須先編碼或逸出，然後才可以使用該識別碼當做容器或項目名稱。</span><span class="sxs-lookup"><span data-stu-id="4a544-117">If a delimited identifier uses characters not supported in Windows PowerShell paths, the characters must either be encoded or escaped before using the identifier as a container or item name.</span></span> <span data-ttu-id="4a544-118">編碼適用於所有字元。</span><span class="sxs-lookup"><span data-stu-id="4a544-118">Encoding works for all characters.</span></span> <span data-ttu-id="4a544-119">某些字元 (例如冒號字元 (:)) 無法逸出。</span><span class="sxs-lookup"><span data-stu-id="4a544-119">Some characters, such as the colon character (:), cannot be escaped.</span></span>  
  
## <a name="sql-server-identifiers-in-cmdlets"></a><span data-ttu-id="4a544-120">Cmdlet 中的 SQL Server 識別碼</span><span class="sxs-lookup"><span data-stu-id="4a544-120">SQL Server Identifiers in cmdlets</span></span>  
 <span data-ttu-id="4a544-121">某些 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Cmdlet 有一個參數會將識別碼當做輸入。</span><span class="sxs-lookup"><span data-stu-id="4a544-121">Some [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlets have a parameter that takes an identifier as input.</span></span> <span data-ttu-id="4a544-122">參數值通常會以加上引號的字串常數形式提供，或是在字串變數中提供。</span><span class="sxs-lookup"><span data-stu-id="4a544-122">The parameter values are typically supplied as quoted string constants or in string variables.</span></span> <span data-ttu-id="4a544-123">當以字串常數的形式或是在變數中提供識別碼時，不會與 Windows PowerShell 支援的字元集合發生衝突。</span><span class="sxs-lookup"><span data-stu-id="4a544-123">When identifiers are supplied as string constants or in variables, there is no conflict with the set of characters that are supported by Windows PowerShell.</span></span>  
  
## <a name="sql-server-identifier-tasks"></a><span data-ttu-id="4a544-124">SQL Server 識別碼工作</span><span class="sxs-lookup"><span data-stu-id="4a544-124">SQL Server Identifier Tasks</span></span>  
  
|<span data-ttu-id="4a544-125">工作描述</span><span class="sxs-lookup"><span data-stu-id="4a544-125">Task Description</span></span>|<span data-ttu-id="4a544-126">主題</span><span class="sxs-lookup"><span data-stu-id="4a544-126">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="4a544-127">描述如何指定執行個體名稱，包括執行個體在其上執行的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="4a544-127">Describes how to specify an instance name, including the name of the computer the instance is running on.</span></span>|[<span data-ttu-id="4a544-128">指定 SQL Server PowerShell 提供者中的執行個體</span><span class="sxs-lookup"><span data-stu-id="4a544-128">Specify Instances in the SQL Server PowerShell Provider</span></span>](sql-server-powershell-provider.md)|  
|<span data-ttu-id="4a544-129">描述如何指定用於 Windows PowerShell 路徑中不支援之分隔識別碼的十六進位編碼。</span><span class="sxs-lookup"><span data-stu-id="4a544-129">Describes how to specify the hexadecimal encoding for characters in delimited identifiers that are not supported in Windows PowerShell paths.</span></span> <span data-ttu-id="4a544-130">同時描述如何解碼十六進位字元。</span><span class="sxs-lookup"><span data-stu-id="4a544-130">Also describes how to decode the hexadecimal characters.</span></span>|[<span data-ttu-id="4a544-131">編碼及解碼 SQL Server 識別碼</span><span class="sxs-lookup"><span data-stu-id="4a544-131">Encode and Decode SQL Server Identifiers</span></span>](encode-and-decode-sql-server-identifiers.md)|  
|<span data-ttu-id="4a544-132">描述如何使用 PowerShell 路徑中不支援字元的 Windows PowerShell 逸出字元。</span><span class="sxs-lookup"><span data-stu-id="4a544-132">Describes how to use the Windows PowerShell escape character for characters not supported in PowerShell paths.</span></span>|[<span data-ttu-id="4a544-133">逸出 SQL Server 識別碼</span><span class="sxs-lookup"><span data-stu-id="4a544-133">Escape SQL Server Identifiers</span></span>](escape-sql-server-identifiers.md)|  
  
## <a name="see-also"></a><span data-ttu-id="4a544-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a544-134">See Also</span></span>  
 <span data-ttu-id="4a544-135">[SQL Server PowerShell 提供者](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="4a544-135">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 <span data-ttu-id="4a544-136">[SQL Server PowerShell](sql-server-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="4a544-136">[SQL Server PowerShell](sql-server-powershell.md) </span></span>  
 [<span data-ttu-id="4a544-137">資料庫識別碼</span><span class="sxs-lookup"><span data-stu-id="4a544-137">Database Identifiers</span></span>](../relational-databases/databases/database-identifiers.md)  
  
  
