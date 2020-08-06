---
title: XTP 虛設處理器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 0f691b3d-a8fd-4459-ad21-2cfc8574a8c0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 14158b7097427b6704cf5e747fa998a11217ecd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698041"
---
# <a name="xtp-phantom-processor"></a><span data-ttu-id="c2a93-102">XTP 虛設處理器</span><span class="sxs-lookup"><span data-stu-id="c2a93-102">XTP Phantom Processor</span></span>
  <span data-ttu-id="c2a93-103">XTP 虛設處理器效能物件包含與 XTP 引擎的虛設處理子系統相關的計數器。</span><span class="sxs-lookup"><span data-stu-id="c2a93-103">The XTP Phantom Processor performance object contains counters related to the XTP engine's phantom processing subsystem.</span></span> <span data-ttu-id="c2a93-104">此元件負責偵測在 SERIALIZABLE 隔離等級執行之交易中的虛設項目列。</span><span class="sxs-lookup"><span data-stu-id="c2a93-104">This component is responsible for detecting phantom rows in transactions running at the SERIALIZABLE isolation level.</span></span>  
  
 <span data-ttu-id="c2a93-105">下表描述**XTP 虛設處理器**計數器。</span><span class="sxs-lookup"><span data-stu-id="c2a93-105">This table describes the **XTP Phantom Processor** counters.</span></span>  
  
|<span data-ttu-id="c2a93-106">計數器</span><span class="sxs-lookup"><span data-stu-id="c2a93-106">Counter</span></span>|<span data-ttu-id="c2a93-107">描述</span><span class="sxs-lookup"><span data-stu-id="c2a93-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c2a93-108">**塵封角落掃描重試次數/秒 (由虛設項目發出)**</span><span class="sxs-lookup"><span data-stu-id="c2a93-108">**Dusty corner scan retries/sec (Phantom-issued)**</span></span>|<span data-ttu-id="c2a93-109">虛設處理器發出塵封角落掃掠期間，(平均) 每秒因為發生寫入衝突而進行掃描的重試次數。</span><span class="sxs-lookup"><span data-stu-id="c2a93-109">The number of scan retries due to write conflicts during dusty corner sweeps issued by the phantom processor (on average), per second.</span></span> <span data-ttu-id="c2a93-110">這是層級非常低的計數器，非供客戶使用。</span><span class="sxs-lookup"><span data-stu-id="c2a93-110">This is a very low-level counter, not intended for customer use.</span></span>|  
|<span data-ttu-id="c2a93-111">**移除的虛設過期資料列/秒**</span><span class="sxs-lookup"><span data-stu-id="c2a93-111">**Phantom expired rows removed/sec**</span></span>|<span data-ttu-id="c2a93-112">(平均) 每秒虛設掃描移除的過期資料列數。</span><span class="sxs-lookup"><span data-stu-id="c2a93-112">The number of expired rows removed by phantom scans (on average), per second.</span></span>|  
|<span data-ttu-id="c2a93-113">**接觸到的虛設過期資料列/秒**</span><span class="sxs-lookup"><span data-stu-id="c2a93-113">**Phantom expired rows touched/sec**</span></span>|<span data-ttu-id="c2a93-114">(平均) 每秒虛設掃描接觸到的過期資料列數。</span><span class="sxs-lookup"><span data-stu-id="c2a93-114">The number of expired rows touched by phantom scans (on average), per second.</span></span>|  
|<span data-ttu-id="c2a93-115">**接觸到的虛設將過期資料列/秒**</span><span class="sxs-lookup"><span data-stu-id="c2a93-115">**Phantom expiring rows touched/sec**</span></span>|<span data-ttu-id="c2a93-116">(平均) 每秒虛設掃描接觸到的將過期資料列數。</span><span class="sxs-lookup"><span data-stu-id="c2a93-116">The number of expiring rows touched by phantom scans (on average), per second.</span></span>|  
|<span data-ttu-id="c2a93-117">**接觸到的虛設項目列/秒**</span><span class="sxs-lookup"><span data-stu-id="c2a93-117">**Phantom rows touched/sec**</span></span>|<span data-ttu-id="c2a93-118">(平均) 每秒虛設掃描接觸到的資料列數。</span><span class="sxs-lookup"><span data-stu-id="c2a93-118">The number of rows touched by phantom scans (on average), per second.</span></span>|  
|<span data-ttu-id="c2a93-119">**啟動的虛設掃描/秒**</span><span class="sxs-lookup"><span data-stu-id="c2a93-119">**Phantom scans started/sec**</span></span>|<span data-ttu-id="c2a93-120">(平均) 每秒啟動的虛設掃描次數。</span><span class="sxs-lookup"><span data-stu-id="c2a93-120">The number of phantom scans started (on average), per second.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2a93-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2a93-121">See Also</span></span>  
 [<span data-ttu-id="c2a93-122">XTP &#40;記憶體內部 OLTP&#41; 效能計數器</span><span class="sxs-lookup"><span data-stu-id="c2a93-122">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)  
  
  
