---
title: 取得元件的相關資訊 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], metadata
- status information [SQL Server], assemblies
- metadata [SQL Server], assemblies
ms.assetid: 6aa7f18e-baad-4481-9777-8c3b230b392f
author: rothja
ms.author: jroth
ms.openlocfilehash: ec559ba5ccbb53dd92f3a5e1175a10a59fbaf43c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704189"
---
# <a name="getting-information-about-assemblies"></a><span data-ttu-id="f1ad1-102">取得組件的相關資訊</span><span class="sxs-lookup"><span data-stu-id="f1ad1-102">Getting Information About Assemblies</span></span>
  <span data-ttu-id="f1ad1-103">您可以查詢下列的目錄檢視及函數，以取得組件的相關中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f1ad1-103">The following catalog views and functions can be queried for metadata about assemblies.</span></span>  
  
 <span data-ttu-id="f1ad1-104">**若要取得個別組件的相關資訊**</span><span class="sxs-lookup"><span data-stu-id="f1ad1-104">**To get information about individual assemblies**</span></span>  
  
-   [<span data-ttu-id="f1ad1-105">ASSEMBLYPROPERTY &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="f1ad1-105">ASSEMBLYPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/assemblyproperty-transact-sql)  
  
 <span data-ttu-id="f1ad1-106">**若要取得資料庫中所有組件的相關資訊**</span><span class="sxs-lookup"><span data-stu-id="f1ad1-106">**To get information about all assemblies in the database**</span></span>  
  
-   [<span data-ttu-id="f1ad1-107">sys.databases &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="f1ad1-107">sys.assemblies &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assemblies-transact-sql)  
  
 <span data-ttu-id="f1ad1-108">**若要取得組件檔案的相關資訊，包括組件二進位、來源檔案及偵錯檔案**</span><span class="sxs-lookup"><span data-stu-id="f1ad1-108">**To get information about assembly files, including assembly binaries, source files, and debug files**</span></span>  
  
-   [<span data-ttu-id="f1ad1-109">assembly_files &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="f1ad1-109">sys.assembly_files &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assembly-files-transact-sql)  
  
 <span data-ttu-id="f1ad1-110">**若要取得跨組件參考的相關資訊**</span><span class="sxs-lookup"><span data-stu-id="f1ad1-110">**To get information about cross-assembly references**</span></span>  
  
-   [<span data-ttu-id="f1ad1-111">assembly_references &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="f1ad1-111">sys.assembly_references &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assembly-references-transact-sql)  
  
 <span data-ttu-id="f1ad1-112">**若要取得使用者定義型別的相關組件資訊**</span><span class="sxs-lookup"><span data-stu-id="f1ad1-112">**To get assembly information about user-defined types**</span></span>  
  
-   [<span data-ttu-id="f1ad1-113">assembly_types &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="f1ad1-113">sys.assembly_types &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assembly-types-transact-sql)  
  
-   [<span data-ttu-id="f1ad1-114">sys.types &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1ad1-114">sys.types &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-types-transact-sql)  
  
 <span data-ttu-id="f1ad1-115">**若要取得 Common Language Runtime (CLR) 預存程序、觸發程序及函數的相關組件資訊**</span><span class="sxs-lookup"><span data-stu-id="f1ad1-115">**To get assembly information about common language runtime (CLR) stored procedures, triggers, and functions**</span></span>  
  
-   [<span data-ttu-id="f1ad1-116">sys.assembly_modules &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1ad1-116">sys.assembly_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql)  
  
 <span data-ttu-id="f1ad1-117">**若要取得非 CLR 物件的相關資訊**</span><span class="sxs-lookup"><span data-stu-id="f1ad1-117">**To get information about non-CLR objects**</span></span>  
  
-   [<span data-ttu-id="f1ad1-118">sys.sql_modules &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f1ad1-118">sys.sql_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="f1ad1-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1ad1-119">See Also</span></span>  
 <span data-ttu-id="f1ad1-120">[元件 &#40;資料庫引擎&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="f1ad1-120">[Assemblies &#40;Database Engine&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span></span>  
 <span data-ttu-id="f1ad1-121">[設計元件](../../relational-databases/clr-integration/assemblies-designing.md) </span><span class="sxs-lookup"><span data-stu-id="f1ad1-121">[Designing Assemblies](../../relational-databases/clr-integration/assemblies-designing.md) </span></span>  
 [<span data-ttu-id="f1ad1-122">實作組件</span><span class="sxs-lookup"><span data-stu-id="f1ad1-122">Implementing Assemblies</span></span>](assemblies-implementing.md)  
  
  
