---
title: 修改使用已停止全文檢索搜尋屬性的預存程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- discontinued properties [Full-Text Search]
- stored procedures [Full-Text Search]
ms.assetid: 8d9392d9-a9ba-4378-84e4-59f516b67ddb
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 12262a588742f0e3be094e32a2a0208a85b6f28a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595473"
---
# <a name="modify-stored-procedures-that-use-discontinued-full-text-search-properties"></a><span data-ttu-id="0ae81-102">修改使用停止全文檢索搜尋屬性的預存程序</span><span class="sxs-lookup"><span data-stu-id="0ae81-102">Modify stored procedures that use discontinued Full-Text Search properties</span></span>
  <span data-ttu-id="0ae81-103">若要確保您的預存程序會正確執行，您應該編輯現有的程序並移除已經被移除或取代的全文檢索相關屬性。</span><span class="sxs-lookup"><span data-stu-id="0ae81-103">To ensure that your stored procedures perform correctly, you should edit existing procedures and remove those full-text related properties and settings that have been removed or deprecated.</span></span>  
  
## <a name="component"></a><span data-ttu-id="0ae81-104">元件</span><span class="sxs-lookup"><span data-stu-id="0ae81-104">Component</span></span>  
 <span data-ttu-id="0ae81-105">全文檢索搜尋</span><span class="sxs-lookup"><span data-stu-id="0ae81-105">Full-Text Search</span></span>  
  
## <a name="description"></a><span data-ttu-id="0ae81-106">描述</span><span class="sxs-lookup"><span data-stu-id="0ae81-106">Description</span></span>  
 <span data-ttu-id="0ae81-107">下列全文檢索搜尋相關的屬性和設定已移除。</span><span class="sxs-lookup"><span data-stu-id="0ae81-107">The following Full-Text Search-related properties and settings have been removed.</span></span>  
  
-   <span data-ttu-id="0ae81-108">**DataTimeout**</span><span class="sxs-lookup"><span data-stu-id="0ae81-108">**DataTimeout**</span></span>  
  
-   <span data-ttu-id="0ae81-109">**ConnectTimeout**</span><span class="sxs-lookup"><span data-stu-id="0ae81-109">**ConnectTimeout**</span></span>  
  
-   <span data-ttu-id="0ae81-110">**Clean_up**</span><span class="sxs-lookup"><span data-stu-id="0ae81-110">**Clean_up**</span></span>  
  
-   <span data-ttu-id="0ae81-111">**LogSize**</span><span class="sxs-lookup"><span data-stu-id="0ae81-111">**LogSize**</span></span>  
  
 <span data-ttu-id="0ae81-112">下列全文檢索搜尋相關的屬性和設定已移除或被取代：</span><span class="sxs-lookup"><span data-stu-id="0ae81-112">The following Full-Text Search-related properties and settings have been removed or deprecated:</span></span>  
  
-   <span data-ttu-id="0ae81-113">全文檢索目錄的「路徑」。</span><span class="sxs-lookup"><span data-stu-id="0ae81-113">'Path' of the Full-Text Catalog.</span></span> <span data-ttu-id="0ae81-114">全文檢索目錄是不含系統中特定檔案路徑的邏輯物件。</span><span class="sxs-lookup"><span data-stu-id="0ae81-114">The Full-Text Catalog will be a logic object without a specific file path in the system.</span></span>  
  
-   <span data-ttu-id="0ae81-115">SP_FULLTEXT_DATABASE 中的 Enable/Disable 已經沒有任何作用，因為在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 中，資料庫永遠預設會啟用全文檢索搜尋。</span><span class="sxs-lookup"><span data-stu-id="0ae81-115">Enable/disable in SP_FULLTEXT_DATABASE has no effect anymore as databases are enabled for Full-Text Search at all times and by default in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="0ae81-116">更正動作</span><span class="sxs-lookup"><span data-stu-id="0ae81-116">Corrective Action</span></span>  
 <span data-ttu-id="0ae81-117">請修改您的預存程序來移除這些屬性。</span><span class="sxs-lookup"><span data-stu-id="0ae81-117">Modify your stored procedures to remove these properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ae81-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ae81-118">See Also</span></span>  
 [<span data-ttu-id="0ae81-119">使用升級建議程式</span><span class="sxs-lookup"><span data-stu-id="0ae81-119">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
