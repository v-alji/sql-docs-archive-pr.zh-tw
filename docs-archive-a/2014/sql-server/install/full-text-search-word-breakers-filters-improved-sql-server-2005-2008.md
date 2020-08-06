---
title: SQL Server 2005 和 SQL Server 2008 大幅改進全文檢索搜尋斷詞工具和篩選 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- filters [Full-Text Search]
- word breakers [Full-Text Search]
ms.assetid: 8d06bda9-0bbf-4baa-b270-07b1c1f640eb
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d2e7d3b8da56b407d3937b05cd980c3f8a4eb0c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606054"
---
# <a name="full-text-search-word-breakers-and-filters-significantly-improved-in-sql-server-2005-and-sql-server-2008"></a><span data-ttu-id="62ecb-102">SQL Server 2005 和 SQL Server 2008 大幅改進全文檢索搜尋斷詞工具和篩選功能</span><span class="sxs-lookup"><span data-stu-id="62ecb-102">Full-Text Search word breakers and filters significantly improved in SQL Server 2005 and SQL Server 2008</span></span>
  <span data-ttu-id="62ecb-103">斷詞工具與篩選已經大幅修改。</span><span class="sxs-lookup"><span data-stu-id="62ecb-103">The word breakers and filters were significantly changed.</span></span> <span data-ttu-id="62ecb-104">對斷詞工具做了進一步的改進，包括提高語言涵蓋範圍和可靠性。</span><span class="sxs-lookup"><span data-stu-id="62ecb-104">Additional improvements have been made to word breakers, including enhanced language coverage and reliability.</span></span>  
  
## <a name="description"></a><span data-ttu-id="62ecb-105">描述</span><span class="sxs-lookup"><span data-stu-id="62ecb-105">Description</span></span>  
 <span data-ttu-id="62ecb-106">為了改善功能和可靠性，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 全文檢索搜尋所使用的斷詞工具和篩選已經大幅修改。</span><span class="sxs-lookup"><span data-stu-id="62ecb-106">Word breakers and filters used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Full-Text Search have been significantly modified to achieve improvements in functionality and reliability.</span></span> <span data-ttu-id="62ecb-107">在某些特定情況下，對斷詞工具所做的變更可能會影響部分資料的 Token 化方式。</span><span class="sxs-lookup"><span data-stu-id="62ecb-107">In some specific cases, changes to the word breakers can impact how some data is tokenized.</span></span> <span data-ttu-id="62ecb-108">在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 中建立的 Token 可能與先前在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 或 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中建立的 Token 不同。</span><span class="sxs-lookup"><span data-stu-id="62ecb-108">Tokens created in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] may be different from earlier tokens created in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] or [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="62ecb-109">如需斷詞工具的相關資訊，請參閱[設定及管理搜尋的斷詞工具和字幹分析器](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)。</span><span class="sxs-lookup"><span data-stu-id="62ecb-109">For information about word breakers, see [Configure and Manage Word Breakers and Stemmers for Search](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62ecb-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62ecb-110">See Also</span></span>  
 [<span data-ttu-id="62ecb-111">使用升級建議程式</span><span class="sxs-lookup"><span data-stu-id="62ecb-111">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
