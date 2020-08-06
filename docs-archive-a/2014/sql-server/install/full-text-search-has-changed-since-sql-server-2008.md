---
title: 自 SQL Server 2008 之後，全文檢索搜尋已變更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: d253bb05-9166-4b50-bd4a-27b818f514e0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 99d3ed4478f007bbe7f05838250aa33a9c4fe448
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595477"
---
# <a name="full-text-search-has-changed-since-sql-server-2008"></a><span data-ttu-id="c2683-102">自 SQL Server 2008 起，全文檢索搜尋已經變更</span><span class="sxs-lookup"><span data-stu-id="c2683-102">Full-Text Search has changed since SQL Server 2008</span></span>
  <span data-ttu-id="c2683-103">Upgrade Advisor 偵測到全文檢索搜尋即將升級。</span><span class="sxs-lookup"><span data-stu-id="c2683-103">Upgrade Advisor detected that full-text search is going to be upgraded.</span></span> <span data-ttu-id="c2683-104">許多全文檢索搜尋選項和設定都已經變更。</span><span class="sxs-lookup"><span data-stu-id="c2683-104">Many full-text search options and settings have changed.</span></span> <span data-ttu-id="c2683-105">因此，當您升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 全文檢索搜尋時，某些設定可能需要進行修改。</span><span class="sxs-lookup"><span data-stu-id="c2683-105">Therefore, when you upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Full-Text Search, some of your settings might need modification.</span></span>  
  
## <a name="component"></a><span data-ttu-id="c2683-106">元件</span><span class="sxs-lookup"><span data-stu-id="c2683-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="c2683-107">描述</span><span class="sxs-lookup"><span data-stu-id="c2683-107">Description</span></span>  
 <span data-ttu-id="c2683-108">由於在升級時，[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以及許多現有的設定並不會保留，因此許多全文檢索搜尋功能、設定和物件都已經修改。</span><span class="sxs-lookup"><span data-stu-id="c2683-108">Several full-text search features, settings and objects have been modified since [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and many of your existing settings will not be maintained when you upgrade.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="c2683-109">更正動作</span><span class="sxs-lookup"><span data-stu-id="c2683-109">Corrective Action</span></span>  
 <span data-ttu-id="c2683-110">我們也建議您在升級至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，檢閱《[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 線上叢書》中的全文檢索搜尋文件，以便了解突破性變更和最佳做法。</span><span class="sxs-lookup"><span data-stu-id="c2683-110">We also recommend reviewing full-text search documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online for breaking changes and best practices when you upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="c2683-111">外部資源</span><span class="sxs-lookup"><span data-stu-id="c2683-111">External Resources</span></span>  
 [<span data-ttu-id="c2683-112">全文檢索搜尋的回溯相容性</span><span class="sxs-lookup"><span data-stu-id="c2683-112">Full-Text Search Backward Compatibility</span></span>](../../../2014/database-engine/full-text-search-backward-compatibility.md)  
  
 [<span data-ttu-id="c2683-113">全文檢索搜尋升級</span><span class="sxs-lookup"><span data-stu-id="c2683-113">Full-Text Search Upgrade</span></span>](https://go.microsoft.com/fwlink/?LinkId=112291)  
  
 [<span data-ttu-id="c2683-114">對全文檢索搜尋的重大變更</span><span class="sxs-lookup"><span data-stu-id="c2683-114">Breaking Changes to Full-Text Search</span></span>](../../../2014/database-engine/breaking-changes-to-full-text-search.md)  
  
  
