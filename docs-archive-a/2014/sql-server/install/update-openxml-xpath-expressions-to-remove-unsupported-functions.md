---
title: 更新 OPENXML XPath 運算式來移除不支援的函式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- OPENXML queries
ms.assetid: b459abaf-8787-4b65-9231-ae30e5469fd0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2c64408d6d705654014b6d071012001374a5f486
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595430"
---
# <a name="update-openxml-xpath-expressions-to-remove-unsupported-functions"></a><span data-ttu-id="7283f-102">更新 OPENXML XPath 運算式來移除不受支援的函數</span><span class="sxs-lookup"><span data-stu-id="7283f-102">Update OPENXML XPath expressions to remove unsupported functions</span></span>
  <span data-ttu-id="7283f-103">Upgrade Advisor 偵測到使用了 XPath 功能。</span><span class="sxs-lookup"><span data-stu-id="7283f-103">Upgrade Advisor detected the use of XPath functionality.</span></span> <span data-ttu-id="7283f-104">升級之後，您可能會受到在 OPENXML 功能之 XPath 功能中所做變更的影響。</span><span class="sxs-lookup"><span data-stu-id="7283f-104">You may be affected by changes in XPath functionality for OPENXML features after you upgrade.</span></span>  
  
## <a name="component"></a><span data-ttu-id="7283f-105">元件</span><span class="sxs-lookup"><span data-stu-id="7283f-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="7283f-106">描述</span><span class="sxs-lookup"><span data-stu-id="7283f-106">Description</span></span>  
 <span data-ttu-id="7283f-107">MSXML 3.0 已經成為用來處理 OPENXML 查詢內使用之 XPath 運算式的基礎引擎。</span><span class="sxs-lookup"><span data-stu-id="7283f-107">MSXML 3.0 is now the underlying engine that is used to process XPath expressions that are used within OPENXML queries.</span></span> <span data-ttu-id="7283f-108">MSXML 3.0 有較嚴格的 XPath 1.0 引擎，其中已移除下列函數的支援：</span><span class="sxs-lookup"><span data-stu-id="7283f-108">MSXML 3.0 has a stricter XPath 1.0 engine in which support for the following functions has been removed:</span></span>  
  
-   <span data-ttu-id="7283f-109">format-number()</span><span class="sxs-lookup"><span data-stu-id="7283f-109">format-number()</span></span>  
  
-   <span data-ttu-id="7283f-110">formatNumber()</span><span class="sxs-lookup"><span data-stu-id="7283f-110">formatNumber()</span></span>  
  
-   <span data-ttu-id="7283f-111">current()</span><span class="sxs-lookup"><span data-stu-id="7283f-111">current()</span></span>  
  
-   <span data-ttu-id="7283f-112">element-available()</span><span class="sxs-lookup"><span data-stu-id="7283f-112">element-available()</span></span>  
  
-   <span data-ttu-id="7283f-113">function-available()</span><span class="sxs-lookup"><span data-stu-id="7283f-113">function-available()</span></span>  
  
-   <span data-ttu-id="7283f-114">system-property()</span><span class="sxs-lookup"><span data-stu-id="7283f-114">system-property()</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="7283f-115">更正動作</span><span class="sxs-lookup"><span data-stu-id="7283f-115">Corrective Action</span></span>  
 <span data-ttu-id="7283f-116">在 format-number() 和 formatNumber() 的情況中，您可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7283f-116">In the case of format-number() and formatNumber(), you can use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="7283f-117">若為先前列出的其他不支援函數，沒有直接的因應措施。</span><span class="sxs-lookup"><span data-stu-id="7283f-117">For the other unsupported functions listed earlier, there is no direct workaround.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7283f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7283f-118">See Also</span></span>  
 <span data-ttu-id="7283f-119">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="7283f-119">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="7283f-120">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="7283f-120">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
