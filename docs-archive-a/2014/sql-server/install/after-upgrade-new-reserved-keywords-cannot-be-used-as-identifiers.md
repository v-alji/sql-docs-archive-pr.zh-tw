---
title: 升級之後，新的保留關鍵字不能當做識別碼使用 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- keywords [SQL Server], after upgrade
- keywords [SQL Server], reserved
- keywords [SQL Server]
ms.assetid: cb242081-54f8-4273-a8ef-52f3751c25ef
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 36f7f8cadcba5e114feee4a3c42de6f40070ce72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595539"
---
# <a name="after-upgrade-new-reserved-keywords-cannot-be-used-as-identifiers"></a><span data-ttu-id="27b87-102">升級之後無法將保留關鍵字當做識別碼</span><span class="sxs-lookup"><span data-stu-id="27b87-102">After upgrade, new reserved keywords cannot be used as identifiers</span></span>
  <span data-ttu-id="27b87-103">Upgrade Advisor 偵測到有使用保留關鍵字。</span><span class="sxs-lookup"><span data-stu-id="27b87-103">Upgrade Advisor detected the use of words that are reserved keywords.</span></span> <span data-ttu-id="27b87-104">保留關鍵字無法當做識別碼或物件名稱使用，除非您分隔此名稱。</span><span class="sxs-lookup"><span data-stu-id="27b87-104">A reserved keyword cannot be used as an identifier or object name unless the name is delimited.</span></span>  
  
## <a name="component"></a><span data-ttu-id="27b87-105">元件</span><span class="sxs-lookup"><span data-stu-id="27b87-105">Component</span></span>  
 <span data-ttu-id="27b87-106">Database Engine</span><span class="sxs-lookup"><span data-stu-id="27b87-106">Database Engine</span></span>  
  
## <a name="description"></a><span data-ttu-id="27b87-107">描述</span><span class="sxs-lookup"><span data-stu-id="27b87-107">Description</span></span>  
 <span data-ttu-id="27b87-108">在 90 或低於 90 的相容性層級上，以下字不是保留關鍵字，而且不能當做 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼中的識別碼或物件名稱。</span><span class="sxs-lookup"><span data-stu-id="27b87-108">At compatibility level 90 or lower, the following words are not reserved keywords and can be used as identifiers or object names in [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.</span></span> <span data-ttu-id="27b87-109">在相容性層級 100 上，這些字是完整保留關鍵字，而且不應該當做識別碼或物件名稱使用。</span><span class="sxs-lookup"><span data-stu-id="27b87-109">At compatibility level 100, these words are fully reserved keywords and should not be used as identifiers or object names.</span></span>  
  
-   <span data-ttu-id="27b87-110">EXTERNAL</span><span class="sxs-lookup"><span data-stu-id="27b87-110">EXTERNAL</span></span>  
  
-   <span data-ttu-id="27b87-111">MERGE</span><span class="sxs-lookup"><span data-stu-id="27b87-111">MERGE</span></span>  
  
-   <span data-ttu-id="27b87-112">PIVOT</span><span class="sxs-lookup"><span data-stu-id="27b87-112">PIVOT</span></span>  
  
-   <span data-ttu-id="27b87-113">REVERT</span><span class="sxs-lookup"><span data-stu-id="27b87-113">REVERT</span></span>  
  
-   <span data-ttu-id="27b87-114">STOPLIST</span><span class="sxs-lookup"><span data-stu-id="27b87-114">STOPLIST</span></span>  
  
-   <span data-ttu-id="27b87-115">TABLESAMPLE</span><span class="sxs-lookup"><span data-stu-id="27b87-115">TABLESAMPLE</span></span>  
  
-   <span data-ttu-id="27b87-116">UNPIVOT</span><span class="sxs-lookup"><span data-stu-id="27b87-116">UNPIVOT</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="27b87-117">更正動作</span><span class="sxs-lookup"><span data-stu-id="27b87-117">Corrective Action</span></span>  
 <span data-ttu-id="27b87-118">我們建議您重新命名物件。</span><span class="sxs-lookup"><span data-stu-id="27b87-118">We recommend that you rename the object.</span></span> <span data-ttu-id="27b87-119">如果您無法在升級之前完成此動作，請使用下列其中一種方法，直到能夠變更名稱為止：</span><span class="sxs-lookup"><span data-stu-id="27b87-119">If that cannot be done before upgrading, use one of the following methods until the name can be changed:</span></span>  
  
-   <span data-ttu-id="27b87-120">保留資料庫相容性層級設定 90 或更低。</span><span class="sxs-lookup"><span data-stu-id="27b87-120">Retain the database compatibility level setting of 90 or lower.</span></span>  
  
-   <span data-ttu-id="27b87-121">使用分隔識別碼來參考物件。</span><span class="sxs-lookup"><span data-stu-id="27b87-121">Refer to the object by using delimited identifiers.</span></span> <span data-ttu-id="27b87-122">例如，語句會 `CREATE TABLE [MERGE] ([MERGE] int);` 使用括弧來分隔物件名稱 MERGE。</span><span class="sxs-lookup"><span data-stu-id="27b87-122">For example, the statement `CREATE TABLE [MERGE] ([MERGE] int);` uses brackets to delimit the object name MERGE.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="27b87-123">外部資源</span><span class="sxs-lookup"><span data-stu-id="27b87-123">External Resources</span></span>  
 [<span data-ttu-id="27b87-124">保留關鍵字 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="27b87-124">Reserved Keywords &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reserved-keywords-transact-sql)  
  
 [<span data-ttu-id="27b87-125">MERGE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="27b87-125">MERGE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/merge-transact-sql)  
  
 [<span data-ttu-id="27b87-126">分隔識別碼 (Database Engine)</span><span class="sxs-lookup"><span data-stu-id="27b87-126">Delimited Identifiers (Database Engine)</span></span>](https://go.microsoft.com/fwlink/?LinkId=112509)  
  
 [<span data-ttu-id="27b87-127">ALTER DATABASE 相容性層級 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="27b87-127">ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
  
  
