---
title: 全文檢索索引屬性 (排程頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.schedule.f1
ms.assetid: a828e284-097e-4854-8c49-931934eb73bf
author: rothja
ms.author: jroth
ms.openlocfilehash: f49fb37295f0b3eb2f1a2dd04d44ab86236f109a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607041"
---
# <a name="full-text-index-properties-schedules-page"></a><span data-ttu-id="0c3ed-102">全文檢索索引屬性 (排程頁面)</span><span class="sxs-lookup"><span data-stu-id="0c3ed-102">Full-Text Index Properties (Schedules Page)</span></span>
  <span data-ttu-id="0c3ed-103">您可以使用這個頁面來檢視和建立執行 SQL Server Agent 作業的排程，以便針對全文檢索索引的基底資料表啟動更新的累加母體擴展。</span><span class="sxs-lookup"><span data-stu-id="0c3ed-103">Use this page to view and create schedules for running a SQL Server Agent job that starts an incremental population of updates to the base table of the full-text index.</span></span> <span data-ttu-id="0c3ed-104">如果基底資料表或檢視表沒有包含 `timestamp` 資料類型的資料行，就會執行完整母體擴展。</span><span class="sxs-lookup"><span data-stu-id="0c3ed-104">If the base table or view does not contain a column of the `timestamp` data type, a full population is performed.</span></span>  
  
 <span data-ttu-id="0c3ed-105">**若要檢視或變更全文檢索索引的屬性**</span><span class="sxs-lookup"><span data-stu-id="0c3ed-105">**To view or change the properties of a full-text index**</span></span>  
  
-   [<span data-ttu-id="0c3ed-106">管理全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="0c3ed-106">Manage Full-Text Indexes</span></span>](../relational-databases/indexes/indexes.md)  
  
## <a name="ui-element-list"></a><span data-ttu-id="0c3ed-107">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="0c3ed-107">UI element list</span></span>  
 <span data-ttu-id="0c3ed-108">**排程**</span><span class="sxs-lookup"><span data-stu-id="0c3ed-108">**Schedules**</span></span>  
 <span data-ttu-id="0c3ed-109">針對全文檢索索引的基底資料表列出每個排程的累加母體擴展 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="0c3ed-109">Lists each scheduled incremental population, if any, on the base table for the full-text index.</span></span>  
  
 <span data-ttu-id="0c3ed-110">**名稱**</span><span class="sxs-lookup"><span data-stu-id="0c3ed-110">**Name**</span></span>  
 <span data-ttu-id="0c3ed-111">顯示每個排程母體擴展的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c3ed-111">Displays the name of the each scheduled population.</span></span>  
  
 <span data-ttu-id="0c3ed-112">**母體類型**</span><span class="sxs-lookup"><span data-stu-id="0c3ed-112">**Population Type**</span></span>  
 <span data-ttu-id="0c3ed-113">顯示每個排程母體擴展的類型。</span><span class="sxs-lookup"><span data-stu-id="0c3ed-113">Displays the type of each scheduled population.</span></span>  
  
 <span data-ttu-id="0c3ed-114">**已啟用**</span><span class="sxs-lookup"><span data-stu-id="0c3ed-114">**Enabled**</span></span>  
 <span data-ttu-id="0c3ed-115">指出排程的母體擴展目前為啟用或停用。</span><span class="sxs-lookup"><span data-stu-id="0c3ed-115">Indicates whether the scheduled population is currently enabled or disabled.</span></span>  
  
 <span data-ttu-id="0c3ed-116">**說明**</span><span class="sxs-lookup"><span data-stu-id="0c3ed-116">**Description**</span></span>  
 <span data-ttu-id="0c3ed-117">顯示建立排程時所指定的描述。</span><span class="sxs-lookup"><span data-stu-id="0c3ed-117">Displays the description that was specified when the schedule was created.</span></span>  
  
 <span data-ttu-id="0c3ed-118">**新增**</span><span class="sxs-lookup"><span data-stu-id="0c3ed-118">**New**</span></span>  
 <span data-ttu-id="0c3ed-119">按一下即可建立擴展全文檢索索引的新排程。</span><span class="sxs-lookup"><span data-stu-id="0c3ed-119">Click to create a new schedule for populating the full-text index.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c3ed-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c3ed-120">See Also</span></span>  
 <span data-ttu-id="0c3ed-121">[使用全文檢索索引 Wizard](../relational-databases/search/use-the-full-text-indexing-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="0c3ed-121">[Use the Full-Text Indexing Wizard](../relational-databases/search/use-the-full-text-indexing-wizard.md) </span></span>  
 [<span data-ttu-id="0c3ed-122">擴展全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="0c3ed-122">Populate Full-Text Indexes</span></span>](../relational-databases/search/populate-full-text-indexes.md)  
  
  
