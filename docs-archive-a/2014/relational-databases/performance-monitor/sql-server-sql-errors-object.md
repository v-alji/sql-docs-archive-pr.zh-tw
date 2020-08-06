---
title: SQL Server 的 SQL Errors 物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQL Errors object
- SQLServer:SQL Errors
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 11bfb728e79b4fc175fb8a2fe16c9f1662a205ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687798"
---
# <a name="sql-server-sql-errors-object"></a><span data-ttu-id="91899-102">SQL Server 的 SQL Errors 物件</span><span class="sxs-lookup"><span data-stu-id="91899-102">SQL Server, SQL Errors Object</span></span>
  <span data-ttu-id="91899-103">Microsoft **中的** SQLServer:SQL Errors [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件，提供用來監視 **SQL Errors**的計數器。</span><span class="sxs-lookup"><span data-stu-id="91899-103">The **SQLServer:SQL Errors** object in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides counters to monitor **SQL Errors**.</span></span>  
  
 <span data-ttu-id="91899-104">下表描述 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQL Errors** 計數器。</span><span class="sxs-lookup"><span data-stu-id="91899-104">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQL Errors** counters.</span></span>  
  
|<span data-ttu-id="91899-105">SQL Server SQL Errors 計數器</span><span class="sxs-lookup"><span data-stu-id="91899-105">SQL Server SQL Errors counters</span></span>|<span data-ttu-id="91899-106">描述</span><span class="sxs-lookup"><span data-stu-id="91899-106">Description</span></span>|  
|------------------------------------|-----------------|  
|<span data-ttu-id="91899-107">**Errors/sec**</span><span class="sxs-lookup"><span data-stu-id="91899-107">**Errors/sec**</span></span>|<span data-ttu-id="91899-108">每秒的錯誤數目。</span><span class="sxs-lookup"><span data-stu-id="91899-108">Number of errors/sec.</span></span>|  
  
 <span data-ttu-id="91899-109">物件中的每個計數器均包含下列執行個體：</span><span class="sxs-lookup"><span data-stu-id="91899-109">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="91899-110">Item</span><span class="sxs-lookup"><span data-stu-id="91899-110">Item</span></span>|<span data-ttu-id="91899-111">定義</span><span class="sxs-lookup"><span data-stu-id="91899-111">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="91899-112">**_Total**</span><span class="sxs-lookup"><span data-stu-id="91899-112">**_Total**</span></span>|<span data-ttu-id="91899-113">所有錯誤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="91899-113">Information for all errors.</span></span>|  
|<span data-ttu-id="91899-114">**DB Offline Errors**</span><span class="sxs-lookup"><span data-stu-id="91899-114">**DB Offline Errors**</span></span>|<span data-ttu-id="91899-115">追蹤導致 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 讓目前資料庫離線的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="91899-115">Tracks severe errors that cause [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to take the current database offline.</span></span>|  
|<span data-ttu-id="91899-116">**Info Errors**</span><span class="sxs-lookup"><span data-stu-id="91899-116">**Info Errors**</span></span>|<span data-ttu-id="91899-117">針對僅提供資訊給使用者而不會導致錯誤的錯誤訊息，提供其相關資訊。</span><span class="sxs-lookup"><span data-stu-id="91899-117">Information related to error messages that provide information to users but do not cause errors.</span></span>|  
|<span data-ttu-id="91899-118">**Kill Connection Errors**</span><span class="sxs-lookup"><span data-stu-id="91899-118">**Kill Connection Errors**</span></span>|<span data-ttu-id="91899-119">追蹤導致 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 清除目前連接的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="91899-119">Tracks severe errors that cause [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to kill the current connection.</span></span>|  
|<span data-ttu-id="91899-120">**User Errors**</span><span class="sxs-lookup"><span data-stu-id="91899-120">**User Errors**</span></span>|<span data-ttu-id="91899-121">使用者錯誤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="91899-121">Information about user errors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="91899-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91899-122">See Also</span></span>  
 [<span data-ttu-id="91899-123">監視資源使用狀況 &#40;System Monitor&#41;</span><span class="sxs-lookup"><span data-stu-id="91899-123">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
