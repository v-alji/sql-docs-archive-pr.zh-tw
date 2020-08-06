---
title: MSSQLSERVER_125 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "125"
helpviewer_keywords:
- 125 (Database Engine error)
ms.assetid: 0f58338d-2ea0-48b8-8a20-c438b0940433
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 59c732d80ccfafc8f242bb1c42fe60e3dea81f19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596047"
---
# <a name="mssqlserver_125"></a><span data-ttu-id="e9970-102">MSSQLSERVER_125</span><span class="sxs-lookup"><span data-stu-id="e9970-102">MSSQLSERVER_125</span></span>
    
## <a name="details"></a><span data-ttu-id="e9970-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e9970-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e9970-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e9970-104">Product Name</span></span>|<span data-ttu-id="e9970-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e9970-105">SQL Server</span></span>|  
|<span data-ttu-id="e9970-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e9970-106">Event ID</span></span>|<span data-ttu-id="e9970-107">125</span><span class="sxs-lookup"><span data-stu-id="e9970-107">125</span></span>|  
|<span data-ttu-id="e9970-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="e9970-108">Event Source</span></span>|<span data-ttu-id="e9970-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e9970-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e9970-110">元件</span><span class="sxs-lookup"><span data-stu-id="e9970-110">Component</span></span>|<span data-ttu-id="e9970-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e9970-111">SQLEngine</span></span>|  
|<span data-ttu-id="e9970-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e9970-112">Symbolic Name</span></span>||  
|<span data-ttu-id="e9970-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e9970-113">Message Text</span></span>|<span data-ttu-id="e9970-114">案例運算式的巢狀層級只能到 %d。</span><span class="sxs-lookup"><span data-stu-id="e9970-114">Case expressions may only be nested to level %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e9970-115">說明</span><span class="sxs-lookup"><span data-stu-id="e9970-115">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e9970-116">在 CASE 運算式中只允許 10 層的巢狀層級。</span><span class="sxs-lookup"><span data-stu-id="e9970-116">allows for only 10 levels of nesting in CASE expressions.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e9970-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e9970-117">User Action</span></span>  
 <span data-ttu-id="e9970-118">將 CASE 陳述式的層級降到 10 層以下。</span><span class="sxs-lookup"><span data-stu-id="e9970-118">Reduce the level of CASE statements to 10 or less.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9970-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9970-119">See Also</span></span>  
 [<span data-ttu-id="e9970-120">CASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e9970-120">CASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/case-transact-sql)  
  
  
