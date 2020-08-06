---
title: 主動式快取 (維度) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], proactive caching
- proactive caching [Analysis Services]
ms.assetid: 7d57fe93-6e5f-4a50-844f-dd2bbdbb94a5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 50c723d46b6c51fae0ccc227b5e58cf96f72c7b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592308"
---
# <a name="proactive-caching-dimensions"></a><span data-ttu-id="b80a3-102">主動式快取 (維度)</span><span class="sxs-lookup"><span data-stu-id="b80a3-102">Proactive Caching (Dimensions)</span></span>
  <span data-ttu-id="b80a3-103">主動式快取會提供自動 MOLAP 快取建立及 OLAP 物件的管理。</span><span class="sxs-lookup"><span data-stu-id="b80a3-103">Proactive caching provides automatic MOLAP cache creation and management for OLAP objects.</span></span> <span data-ttu-id="b80a3-104">Cube 會根據從資料庫接收而來的通知，立即併入對資料庫資料所做的變更。</span><span class="sxs-lookup"><span data-stu-id="b80a3-104">The cubes immediately incorporate changes that are made to the data in the database, based upon notifications received from the database.</span></span> <span data-ttu-id="b80a3-105">主動式快取的目標是要提供傳統 MOLAP 的效能，同時保持 ROLAP 所提供的立即性與便於管理性。</span><span class="sxs-lookup"><span data-stu-id="b80a3-105">The goal of proactive caching is to provide the performance of traditional MOLAP, while retaining the immediacy and ease of management offered by ROLAP.</span></span>  
  
 <span data-ttu-id="b80a3-106">簡單的 <xref:Microsoft.AnalysisServices.ProactiveCaching> 物件是由時間指定和資料表通知所組成。</span><span class="sxs-lookup"><span data-stu-id="b80a3-106">A simple <xref:Microsoft.AnalysisServices.ProactiveCaching> object is composed of: timing specification, and table notification.</span></span> <span data-ttu-id="b80a3-107">時間指定會定義在收到變更通知以後，用於更新快取的時間範圍。</span><span class="sxs-lookup"><span data-stu-id="b80a3-107">The timing specification defines the timeframe for updating the cache after a change notification has been received.</span></span> <span data-ttu-id="b80a3-108">資料表通知會定義在資料表與 <xref:Microsoft.AnalysisServices.ProactiveCaching> 物件之間的通知結構描述。</span><span class="sxs-lookup"><span data-stu-id="b80a3-108">The table notification defines the notification schema between the data table and the <xref:Microsoft.AnalysisServices.ProactiveCaching> object.</span></span>  
  
  
