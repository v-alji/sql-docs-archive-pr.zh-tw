---
title: 定序和 CLR 整合資料類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- data types [CLR integration]
- parameter collation [CLR integration]
- collations [CLR integration]
ms.assetid: 6ebaed8e-2e2b-4f6d-bf4b-bc25452de441
author: rothja
ms.author: jroth
ms.openlocfilehash: 1a5b0367487aeb80355b8c5c976818e1b6c1ac04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709646"
---
# <a name="collation-and-clr-integration-data-types"></a><span data-ttu-id="4f140-102">定序和 CLR 整合資料類型</span><span class="sxs-lookup"><span data-stu-id="4f140-102">Collation and CLR Integration Data Types</span></span>
  <span data-ttu-id="4f140-103">在 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 中，`CompareInfo` 物件會處理定序。</span><span class="sxs-lookup"><span data-stu-id="4f140-103">In the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], the `CompareInfo` object handles collations.</span></span> <span data-ttu-id="4f140-104">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 字串應用程式開發介面 (API) 會使用與目前執行緒之 `CompareInfo` 物件相關聯的 `CultureInfo` 屬性來執行字串比較。</span><span class="sxs-lookup"><span data-stu-id="4f140-104">The [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] string application programming interfaces (APIs) use the `CompareInfo` property associated with the `CultureInfo` object of the current thread to perform string comparisons.</span></span> <span data-ttu-id="4f140-105">物件的預設設定 `CultureInfo` 是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 以執行之電腦的 Windows 地區設定為基礎 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4f140-105">The default setting of the `CultureInfo` object is based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows locale setting for the computer on which [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span> <span data-ttu-id="4f140-106">如果沒有指定任何明確的 `CultureInfo`，這會決定預設的比較語意來比較 `System.String` 值。</span><span class="sxs-lookup"><span data-stu-id="4f140-106">This determines the default comparison semantics, if no explicit `CultureInfo` is specified, for comparisons of `System.String` values.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4f140-107">不會將 `CompareInfo` 屬性明確地變更為資料庫或伺服器定序。</span><span class="sxs-lookup"><span data-stu-id="4f140-107">does not explicitly change the `CompareInfo` property to the database or server collation.</span></span> <span data-ttu-id="4f140-108">如有需要，使用者必須在其常式中設定適當的 `CompareInfo` 屬性。</span><span class="sxs-lookup"><span data-stu-id="4f140-108">If required, users must set the appropriate `CompareInfo` property in their routines.</span></span>  
  
## <a name="parameter-collation"></a><span data-ttu-id="4f140-109">參數定序</span><span class="sxs-lookup"><span data-stu-id="4f140-109">Parameter Collation</span></span>  
 <span data-ttu-id="4f140-110">當您建立 Common Language Runtime (CLR) 常式，而且繫結至常式的 CLR 方法參數類型為 `SQLString` 時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會使用包含呼叫常式之資料庫的預設定序建立參數的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4f140-110">When you create a common language runtime (CLR) routine, and a parameter of a CLR method bound to the routine is of type `SQLString`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creates an instance of the parameter with the default collation of the database containing the calling routine.</span></span> <span data-ttu-id="4f140-111">如果參數不是 `SqlType` (例如，`String` 而非 `SQLString`)，資料庫中的定序資訊不會與參數相關聯。</span><span class="sxs-lookup"><span data-stu-id="4f140-111">If a parameter is not a `SqlType` (for example, `String` rather than `SQLString`), the collation information from the database is not associated with the parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f140-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f140-112">See Also</span></span>  
 [<span data-ttu-id="4f140-113">.NET Framework 的 SQL Server 資料類型</span><span class="sxs-lookup"><span data-stu-id="4f140-113">SQL Server Data Types in the .NET Framework</span></span>](sql-server-data-types-in-the-net-framework.md)  
  
  
