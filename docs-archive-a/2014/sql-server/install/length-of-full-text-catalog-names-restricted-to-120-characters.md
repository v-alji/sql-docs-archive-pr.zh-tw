---
title: 全文檢索目錄名稱的長度限制為120個字元 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs names
ms.assetid: 50633373-83f6-4ed9-99b9-71f92479a14f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fa9b06fa6fe4acd79782c19a8814357721e59c24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607234"
---
# <a name="length-of-full-text-catalog-names-restricted-to-120-characters"></a><span data-ttu-id="6b2cc-102">全文檢索目錄名稱長度的限制是 120 個字元</span><span class="sxs-lookup"><span data-stu-id="6b2cc-102">Length of full-text catalog names restricted to 120 characters</span></span>
  <span data-ttu-id="6b2cc-103">全文檢索目錄名稱的長度限制已經從舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 128 個字元，調降為 120 個字元。</span><span class="sxs-lookup"><span data-stu-id="6b2cc-103">The length of full-text catalog names is restricted to 120 characters, reduced from the 128 character restriction in previous releases of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="description"></a><span data-ttu-id="6b2cc-104">描述</span><span class="sxs-lookup"><span data-stu-id="6b2cc-104">Description</span></span>  
 <span data-ttu-id="6b2cc-105">此變更不會影響現有目錄名稱。不過，建立名稱超過 120 個字元之全文檢索目錄的指令碼會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="6b2cc-105">This change does not affect existing catalog names; however, scripts that create full-text catalogs with names longer than 120 characters result in an error.</span></span> <span data-ttu-id="6b2cc-106">目錄名稱是用來產生對應至目錄的邏輯檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="6b2cc-106">The catalog names are used to generate logical file names that correspond to catalogs.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="6b2cc-107">更正動作</span><span class="sxs-lookup"><span data-stu-id="6b2cc-107">Corrective Action</span></span>  
 <span data-ttu-id="6b2cc-108">請修改建立全文檢索目錄的所有指令碼，確定它們將目錄名稱限制為 120 個字元。</span><span class="sxs-lookup"><span data-stu-id="6b2cc-108">Modify all scripts that create full-text catalogs to ensure that they restrict catalog names to 120 characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b2cc-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b2cc-109">See Also</span></span>  
 [<span data-ttu-id="6b2cc-110">使用升級建議程式</span><span class="sxs-lookup"><span data-stu-id="6b2cc-110">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
