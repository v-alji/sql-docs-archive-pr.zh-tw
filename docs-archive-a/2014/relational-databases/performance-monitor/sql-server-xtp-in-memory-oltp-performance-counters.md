---
title: XTP (記憶體內部 OLTP) 效能計數器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: fe3cbaf4-65f4-44c5-acc6-7b735cda0c5d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4363a526ada3694e92d18cac0d7abe8a26f6a92f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698044"
---
# <a name="xtp-in-memory-oltp-performance-counters"></a><span data-ttu-id="16ad4-102">XTP (記憶體中 OLTP) 效能計數器</span><span class="sxs-lookup"><span data-stu-id="16ad4-102">XTP (In-Memory OLTP) Performance Counters</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="16ad4-103">提供物件和計數器，可供效能監視器用來監視記憶體中 OLTP 活動。</span><span class="sxs-lookup"><span data-stu-id="16ad4-103">provides objects and counters that can be used by Performance Monitor to monitor In-Memory OLTP activity.</span></span>  
  
##  <a name="xtp-in-memory-oltp-performance-objects"></a><a name="SQLServerPOs"></a><span data-ttu-id="16ad4-104">XTP (記憶體內部 OLTP) 效能物件</span><span class="sxs-lookup"><span data-stu-id="16ad4-104">XTP (In-Memory OLTP) Performance Objects</span></span>  
 <span data-ttu-id="16ad4-105">下表描述 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件。</span><span class="sxs-lookup"><span data-stu-id="16ad4-105">The following table describes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects.</span></span>  
  
|<span data-ttu-id="16ad4-106">效能物件</span><span class="sxs-lookup"><span data-stu-id="16ad4-106">Performance object</span></span>|<span data-ttu-id="16ad4-107">描述</span><span class="sxs-lookup"><span data-stu-id="16ad4-107">Description</span></span>|  
|------------------------|-----------------|  
|[<span data-ttu-id="16ad4-108">XTP 資料指標</span><span class="sxs-lookup"><span data-stu-id="16ad4-108">XTP Cursors</span></span>](../cursors.md)|<span data-ttu-id="16ad4-109">XTP 資料指標效能物件包含與內部 XTP 引擎資料指標相關的計數器。</span><span class="sxs-lookup"><span data-stu-id="16ad4-109">The XTP Cursors performance object contains counters related to internal XTP engine cursors.</span></span> <span data-ttu-id="16ad4-110">資料指標是 XTP 引擎用來處理 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢的低階建置組塊。</span><span class="sxs-lookup"><span data-stu-id="16ad4-110">Cursors are the low-level building blocks the XTP engine uses to process [!INCLUDE[tsql](../../includes/tsql-md.md)] queries.</span></span> <span data-ttu-id="16ad4-111">因此，您通常不會有這些指標的直接控制權。</span><span class="sxs-lookup"><span data-stu-id="16ad4-111">As such, you do not typically have direct control over them.</span></span>|  
|[<span data-ttu-id="16ad4-112">XTP 記憶體回收</span><span class="sxs-lookup"><span data-stu-id="16ad4-112">XTP Garbage Collection</span></span>](sql-server-xtp-garbage-collection.md)|<span data-ttu-id="16ad4-113">XTP 記憶體回收效能物件包含與 XTP 引擎記憶體回收行程相關的計數器。</span><span class="sxs-lookup"><span data-stu-id="16ad4-113">The XTP Garbage Collection performance object contains counters related to the XTP engine's garbage collector.</span></span>|  
|[<span data-ttu-id="16ad4-114">XTP 虛設處理器</span><span class="sxs-lookup"><span data-stu-id="16ad4-114">XTP Phantom Processor</span></span>](sql-server-xtp-phantom-processor.md)|<span data-ttu-id="16ad4-115">XTP 虛設處理器效能物件包含與 XTP 引擎的虛設處理子系統相關的計數器。</span><span class="sxs-lookup"><span data-stu-id="16ad4-115">The XTP Phantom Processor performance object contains counters related to the XTP engine's phantom processing subsystem.</span></span> <span data-ttu-id="16ad4-116">此元件負責偵測在 SERIALIZABLE 隔離等級執行之交易中的虛設項目列。</span><span class="sxs-lookup"><span data-stu-id="16ad4-116">This component is responsible for detecting phantom rows in transactions running at the SERIALIZABLE isolation level.</span></span>|  
|[<span data-ttu-id="16ad4-117">XTP 儲存體</span><span class="sxs-lookup"><span data-stu-id="16ad4-117">XTP Storage</span></span>](sql-server-xtp-storage.md)|<span data-ttu-id="16ad4-118">XTP 儲存體效能物件包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中與 XTP 儲存體相關的計數器。</span><span class="sxs-lookup"><span data-stu-id="16ad4-118">The XTP Storage performance object contains counters related to XTP storage in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="16ad4-119">XTP 交易記錄</span><span class="sxs-lookup"><span data-stu-id="16ad4-119">XTP Transaction Log</span></span>](sql-server-xtp-transaction-log.md)|<span data-ttu-id="16ad4-120">XTP 交易記錄效能物件包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中與 XTP 交易記錄相關的計數器。</span><span class="sxs-lookup"><span data-stu-id="16ad4-120">The XTP Transaction Log performance object contains counters related to XTP transaction logging in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="16ad4-121">XTP 交易</span><span class="sxs-lookup"><span data-stu-id="16ad4-121">XTP Transactions</span></span>](sql-server-xtp-transactions.md)|<span data-ttu-id="16ad4-122">XTP 交易效能物件包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中與 XTP 引擎交易相關的計數器。</span><span class="sxs-lookup"><span data-stu-id="16ad4-122">The XTP Transactions performance object contains counters related to XTP engine transactions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
  
  
