---
title: 改變元件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], modifying
- permissions [CLR integration]
- altering assemblies
- ALTER ASSEMBLY statement
ms.assetid: 9e765fbd-f339-473c-8537-22f478e79696
author: rothja
ms.author: jroth
ms.openlocfilehash: c22ca979675d3b7f263e3bc6de0c41c134a1abcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704173"
---
# <a name="altering-an-assembly"></a><span data-ttu-id="feec1-102">變更組件</span><span class="sxs-lookup"><span data-stu-id="feec1-102">Altering an Assembly</span></span>
  <span data-ttu-id="feec1-103">已經在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中註冊的組件可以使用 ALTER ASSEMBLY 陳述式，從比較新的版本更新。</span><span class="sxs-lookup"><span data-stu-id="feec1-103">Assemblies that have been registered in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can be updated from a more recent version using the ALTER ASSEMBLY statement.</span></span> <span data-ttu-id="feec1-104">若要更新組件，請使用 ALTER ASSEMBLY 陳述式搭配下列語法：</span><span class="sxs-lookup"><span data-stu-id="feec1-104">To update an assembly, use the ALTER ASSEMBLY statement with the following syntax:</span></span>  
  
```  
ALTER ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
```  
  
 <span data-ttu-id="feec1-105">ALTER ASSEMBLY 不會中斷目前使用組件正在執行的處理序；處理序會繼續執行未變更的組件。</span><span class="sxs-lookup"><span data-stu-id="feec1-105">ALTER ASSEMBLY does not disrupt currently running processes that are using the assembly; the processes continue executing with the unaltered assembly.</span></span> <span data-ttu-id="feec1-106">ALTER ASSEMBLY 無法用於變更 Common Language Runtime (CLR) 函數、彙總函式、預存程序和觸發程序的簽章。</span><span class="sxs-lookup"><span data-stu-id="feec1-106">ALTER ASSEMBLY cannot be used to change the signatures of common language runtime (CLR) functions, aggregate functions, stored procedures, and triggers.</span></span> <span data-ttu-id="feec1-107">新的公用方法可以加入到組件、私用方法可以用任何方式修改，而且只要簽章或屬性沒有變更，就可以修改公用方法。</span><span class="sxs-lookup"><span data-stu-id="feec1-107">New public methods can be added to the assembly, private methods can be modified in any way, and public methods can be modified as long as signatures or attributes are not changed.</span></span> <span data-ttu-id="feec1-108">包含在原生序列化使用者定義型別 (包括資料成員或基底類別) 中的欄位，不能使用 ALTER ASSEMBLY 加以變更。</span><span class="sxs-lookup"><span data-stu-id="feec1-108">Fields that are contained within a native-serialized user-defined type, including data members or base classes, cannot be changed by using ALTER ASSEMBLY.</span></span> <span data-ttu-id="feec1-109">所有其他變更亦不受支援。</span><span class="sxs-lookup"><span data-stu-id="feec1-109">All other changes are unsupported.</span></span> <span data-ttu-id="feec1-110">如需詳細資訊，請參閱[ALTER ASSEMBLY &#40;transact-sql&#41;](/sql/t-sql/statements/alter-assembly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="feec1-110">For more information, see [ALTER ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-assembly-transact-sql).</span></span>  
  
## <a name="changing-the-permission-set-of-an-assembly"></a><span data-ttu-id="feec1-111">變更組件的權限集合</span><span class="sxs-lookup"><span data-stu-id="feec1-111">Changing the Permission Set of an Assembly</span></span>  
 <span data-ttu-id="feec1-112">組件的權限集合也可以使用 ALTER ASSEMBLY 陳述式進行變更。</span><span class="sxs-lookup"><span data-stu-id="feec1-112">The permission set of an assembly can also be changed using the ALTER ASSEMBLY statement.</span></span> <span data-ttu-id="feec1-113">下列陳述式會將 SQLCLRTest 組件的權限集合變更為 `EXTERNAL_ACCESS`。</span><span class="sxs-lookup"><span data-stu-id="feec1-113">The following statement changes the permission set of the SQLCLRTest assembly to `EXTERNAL_ACCESS`.</span></span>  
  
```  
ALTER ASSEMBLY SQLCLRTest  
WITH PERMISSION_SET = EXTERNAL_ACCESS   
```  
  
 <span data-ttu-id="feec1-114">如果組件的權限集合要從 `SAFE` 變更為 `EXTERNAL_ACCESS` 或 `UNSAFE`，則必須先建立包含組件之 `EXTERNAL ACCESS ASSEMBLY` 權限或 `UNSAFE ASSEMBLY` 權限的非對稱金鑰和對應的登入。</span><span class="sxs-lookup"><span data-stu-id="feec1-114">If the permission set of an assembly is being changed from `SAFE` to `EXTERNAL_ACCESS` or `UNSAFE`, an asymmetric key and corresponding login with `EXTERNAL ACCESS ASSEMBLY` permission or `UNSAFE ASSEMBLY` permission for the assembly must first be created.</span></span> <span data-ttu-id="feec1-115">如需詳細資訊，請參閱 [建立組件](creating-an-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="feec1-115">For more information, see [Creating an Assembly](creating-an-assembly.md).</span></span>  
  
## <a name="adding-the-source-code-of-an-assembly"></a><span data-ttu-id="feec1-116">加入組件的原始程式碼</span><span class="sxs-lookup"><span data-stu-id="feec1-116">Adding the Source Code of an Assembly</span></span>  
 <span data-ttu-id="feec1-117">ALTER ASSEMBLY 語法中的 ADD FILE 子句不存在於 CREATE ASSEMBLY 中。</span><span class="sxs-lookup"><span data-stu-id="feec1-117">The ADD FILE clause in the ALTER ASSEMBLY syntax is not present in CREATE ASSEMBLY.</span></span> <span data-ttu-id="feec1-118">您可以使用它來加入原始程式碼，或與組件相關聯的任何其他檔案。</span><span class="sxs-lookup"><span data-stu-id="feec1-118">You can use it to add source code or any other files associated with an assembly.</span></span> <span data-ttu-id="feec1-119">這些檔案會從原始位置複製，並儲存在資料庫的系統資料表中。</span><span class="sxs-lookup"><span data-stu-id="feec1-119">The files are copied from their original locations and stored in system tables in the database.</span></span> <span data-ttu-id="feec1-120">如此可在您需要重新建立或記載 UDT 的目前版本時，確保您一定有原始程式碼或其他檔案可用。</span><span class="sxs-lookup"><span data-stu-id="feec1-120">This ensures that you always have source code or other files on hand should you ever need to re-create or document the current version of the UDT.</span></span>  
  
 <span data-ttu-id="feec1-121">下列陳述式會對 Point UDT 加入 Point.cs 類別原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="feec1-121">The following statement adds the Point.cs class source code for the Point UDT.</span></span> <span data-ttu-id="feec1-122">這會複製 Point.cs 檔案中包含的文字，並將它儲存在名為 PointSource 的資料庫中。</span><span class="sxs-lookup"><span data-stu-id="feec1-122">This copies the text contained in the Point.cs file and stores it in the database under the name "PointSource".</span></span>  
  
 `ALTER ASSEMBLY Point`  
  
 `ADD FILE FROM 'C:\Projects\Point\Point.cs' AS PointSource`  
  
## <a name="see-also"></a><span data-ttu-id="feec1-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="feec1-123">See Also</span></span>  
 <span data-ttu-id="feec1-124">[管理 CLR 整合元件](managing-clr-integration-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="feec1-124">[Managing CLR Integration Assemblies](managing-clr-integration-assemblies.md) </span></span>  
 <span data-ttu-id="feec1-125">[建立元件](creating-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="feec1-125">[Creating an Assembly](creating-an-assembly.md) </span></span>  
 <span data-ttu-id="feec1-126">[卸載元件](dropping-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="feec1-126">[Dropping an Assembly](dropping-an-assembly.md) </span></span>  
 [<span data-ttu-id="feec1-127">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="feec1-127">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
  
