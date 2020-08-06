---
title: 移除以保留的日期和時間資料類型命名的 UDT&#39;|Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- time data type [SQL Server], UDTs
- date data type [SQL Server], UDTs
ms.assetid: 48f109af-b1d1-4f03-a7e3-8a0b05ed94e8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 827f060b309a7a620fd448554b074f45d78d3cb0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598146"
---
# <a name="remove-udt39s-named-after-the-reserved-date-and-time-data-types"></a><span data-ttu-id="81702-102">移除以保留的日期和時間資料類型命名的 UDT&#39;</span><span class="sxs-lookup"><span data-stu-id="81702-102">Remove UDT&#39;s named after the reserved DATE and TIME data types</span></span>
  <span data-ttu-id="81702-103">Upgrade Advisor 偵測到依據針對 `date` 或 `time` 資料類型保留之詞彙所命名的使用者定義型別 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="81702-103">Upgrade Advisor detected a user-defined type (UDT) that is named after a term reserved for either the `date` or the `time` data types.</span></span>  
  
## <a name="component"></a><span data-ttu-id="81702-104">元件</span><span class="sxs-lookup"><span data-stu-id="81702-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="81702-105">描述</span><span class="sxs-lookup"><span data-stu-id="81702-105">Description</span></span>  
 <span data-ttu-id="81702-106">用於資料類型的詞彙不應該當做 Common Language Runtime (CLR) 或別名 UDT 的名稱使用。</span><span class="sxs-lookup"><span data-stu-id="81702-106">The terms used for data types should not be used as names for either common language runtime (CLR) or alias UDTs.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="81702-107">更正動作</span><span class="sxs-lookup"><span data-stu-id="81702-107">Corrective Action</span></span>  
 <span data-ttu-id="81702-108">請移除依據此資料類型所命名的 UDT，然後使用未保留的名稱重新建立 UDT。</span><span class="sxs-lookup"><span data-stu-id="81702-108">Remove the UDT that is named after the data type and recreate the UDT with an unreserved name.</span></span>  
  
  
