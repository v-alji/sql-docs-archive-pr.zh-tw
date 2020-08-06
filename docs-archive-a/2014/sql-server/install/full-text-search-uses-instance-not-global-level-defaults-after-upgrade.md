---
title: 升級預設會使全文檢索搜尋使用實例層級，而非全域、斷詞工具和篩選 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- filters [Full-Text Search]
- word breakers [Full-Text Search]
ms.assetid: 93ee8fcb-d11c-49fa-8fac-51ed31a8f008
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0b6cea7ab63351fad25f0205a614e364328171a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607243"
---
# <a name="upgrading-will-cause-full-text-search-to-use-instance-level-not-global-word-breakers-and-filters-by-default"></a><span data-ttu-id="dd432-102">升級預設會使全文檢索搜尋使用執行個體層級、非全域的斷詞工具和篩選</span><span class="sxs-lookup"><span data-stu-id="dd432-102">Upgrading will cause Full-Text Search to use instance-level, not global, word breakers and filters by default</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="dd432-103">提供可於執行個體層級註冊新斷詞工具和篩選的方法。</span><span class="sxs-lookup"><span data-stu-id="dd432-103">provides a way to allow instance-level registration of new word breakers and filters.</span></span>  
  
## <a name="component"></a><span data-ttu-id="dd432-104">元件</span><span class="sxs-lookup"><span data-stu-id="dd432-104">Component</span></span>  
 <span data-ttu-id="dd432-105">全文檢索搜尋</span><span class="sxs-lookup"><span data-stu-id="dd432-105">Full-Text Search</span></span>  
  
## <a name="description"></a><span data-ttu-id="dd432-106">描述</span><span class="sxs-lookup"><span data-stu-id="dd432-106">Description</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="dd432-107">允許新斷詞工具和篩選的執行個體層級註冊。</span><span class="sxs-lookup"><span data-stu-id="dd432-107">allows the instance-level registration of new word breakers and filters.</span></span> <span data-ttu-id="dd432-108">這種執行個體層級註冊提供了執行個體之間的功能和安全性隔離。</span><span class="sxs-lookup"><span data-stu-id="dd432-108">This instance-level registration provides functional and security isolation between instances.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="dd432-109">更正動作</span><span class="sxs-lookup"><span data-stu-id="dd432-109">Corrective Action</span></span>  
 <span data-ttu-id="dd432-110">升級之後，請使用 `sp_fulltext_service` 來設定服務屬性以及允許載入元件的 `load_os_resources`。</span><span class="sxs-lookup"><span data-stu-id="dd432-110">After upgrading, use the `sp_fulltext_service` to set the service property and `load_os_resources`, which allows the components to be loaded.</span></span> <span data-ttu-id="dd432-111">您必須執行下列項目：</span><span class="sxs-lookup"><span data-stu-id="dd432-111">You must run the following:</span></span>  
  
 `sp_fulltext_service 'load_os_resources', 1`  
  
## <a name="see-also"></a><span data-ttu-id="dd432-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd432-112">See Also</span></span>  
 [<span data-ttu-id="dd432-113">使用升級建議程式</span><span class="sxs-lookup"><span data-stu-id="dd432-113">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
