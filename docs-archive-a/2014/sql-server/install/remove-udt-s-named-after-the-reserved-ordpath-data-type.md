---
title: 移除以保留的 ORDPATH 資料類型命名的 UDT&#39;|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 474e910a-6abb-4e28-acc2-055338c011d4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0528d19de17781d863e3a42fdef7db558fe5d190
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710162"
---
# <a name="remove-udt39s-named-after-the-reserved-ordpath-data-type"></a><span data-ttu-id="6d1ee-102">移除以保留的 ORDPATH 資料類型命名的 UDT&#39;</span><span class="sxs-lookup"><span data-stu-id="6d1ee-102">Remove UDT&#39;s named after the reserved ORDPATH data type</span></span>
  <span data-ttu-id="6d1ee-103">Upgrade Advisor 偵測到依據為 `ORDPATH` 資料類型保留之詞彙所命名的使用者定義型別 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="6d1ee-103">Upgrade Advisor detected a user-defined type (UDT) that is named after a term reserved for the `ORDPATH` data type.</span></span>  
  
## <a name="component"></a><span data-ttu-id="6d1ee-104">元件</span><span class="sxs-lookup"><span data-stu-id="6d1ee-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="6d1ee-105">描述</span><span class="sxs-lookup"><span data-stu-id="6d1ee-105">Description</span></span>  
 <span data-ttu-id="6d1ee-106">用於內建資料類型的詞彙不應該當做 Common Language Runtime (CLR) 或別名 UDT 的名稱使用。</span><span class="sxs-lookup"><span data-stu-id="6d1ee-106">The terms used for built-in data types should not be used as names for either common language runtime (CLR) or alias UDTs.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="6d1ee-107">更正動作</span><span class="sxs-lookup"><span data-stu-id="6d1ee-107">Corrective Action</span></span>  
 <span data-ttu-id="6d1ee-108">請移除依據此資料類型所命名的 UDT，然後使用未保留的名稱重新建立 UDT。</span><span class="sxs-lookup"><span data-stu-id="6d1ee-108">Remove the UDT that is named after the data type and recreate the UDT with an unreserved name.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="6d1ee-109">外部資源</span><span class="sxs-lookup"><span data-stu-id="6d1ee-109">External Resources</span></span>  
 [<span data-ttu-id="6d1ee-110">建立使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="6d1ee-110">Creating a User-Defined Type</span></span>](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
