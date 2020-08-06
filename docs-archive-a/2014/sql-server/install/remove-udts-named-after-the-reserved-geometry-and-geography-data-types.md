---
title: 移除以保留的 GEOMETRY 和 GEOGRAPHY 資料類型命名的 Udt |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- geometry data type [SQL Server], UDTs
- geography data type [SQL Server], UDTs
ms.assetid: a167ce3a-50b4-4e77-a884-adb23b586c72
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 4977d45d53e1114edc8e04ad504963bae0b9eb9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710161"
---
# <a name="remove-udts-named-after-the-reserved-geometry-and-geography-data-types"></a><span data-ttu-id="282ce-102">移除依據保留之 GEOMETRY 和 GEOGRAPHY 資料類型所命名的 UDT</span><span class="sxs-lookup"><span data-stu-id="282ce-102">Remove UDTs named after the reserved GEOMETRY and GEOGRAPHY data types</span></span>
  <span data-ttu-id="282ce-103">Upgrade Advisor 偵測到依據針對 `geometry` 或 `geography` 資料類型保留之詞彙所命名的使用者定義型別 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="282ce-103">Upgrade Advisor detected a user-defined type (UDT) that is named after a term reserved for either the `geometry` or the `geography` data types.</span></span> <span data-ttu-id="282ce-104">`geometry` 和 `geography` 資料類型屬於空間資料功能的一部分。</span><span class="sxs-lookup"><span data-stu-id="282ce-104">The `geometry` and `geography` data types are part of the spatial data feature.</span></span>  
  
## <a name="component"></a><span data-ttu-id="282ce-105">元件</span><span class="sxs-lookup"><span data-stu-id="282ce-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="282ce-106">描述</span><span class="sxs-lookup"><span data-stu-id="282ce-106">Description</span></span>  
 <span data-ttu-id="282ce-107">用於空間資料類型的詞彙不應該當做 Common Language Runtime (CLR) 或別名 UDT 的名稱使用。</span><span class="sxs-lookup"><span data-stu-id="282ce-107">The terms used for spatial data types should not be used as names for either common language runtime (CLR) or alias UDTs.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="282ce-108">更正動作</span><span class="sxs-lookup"><span data-stu-id="282ce-108">Corrective Action</span></span>  
 <span data-ttu-id="282ce-109">請移除依據此資料類型所命名的 UDT，然後使用未保留的名稱重新建立 UDT。</span><span class="sxs-lookup"><span data-stu-id="282ce-109">Remove the UDT that is named after the data type and recreate the UDT with an unreserved name.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="282ce-110">外部資源</span><span class="sxs-lookup"><span data-stu-id="282ce-110">External Resources</span></span>  
 [<span data-ttu-id="282ce-111">建立使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="282ce-111">Creating a User-Defined Type</span></span>](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
 [<span data-ttu-id="282ce-112">空間資料類型概觀</span><span class="sxs-lookup"><span data-stu-id="282ce-112">Spatial Data Types Overview</span></span>](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  
