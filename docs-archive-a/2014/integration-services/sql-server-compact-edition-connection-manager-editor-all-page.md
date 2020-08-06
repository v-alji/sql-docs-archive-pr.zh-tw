---
title: SQL Server Compact Edition 連線管理員編輯器 (所有頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlmobileconnection.all.f1
helpviewer_keywords:
- SQL Server Compact Connection Manager Editor
ms.assetid: f9fbff4b-c502-44b3-8e7b-398d66e82206
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4f881d63de5435426475c3aed4b666870d706b40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594592"
---
# <a name="sql-server-compact-edition-connection-manager-editor-all-page"></a><span data-ttu-id="5ec4a-102">SQL Server Compact Edition 連接管理員編輯器 (全部頁面)</span><span class="sxs-lookup"><span data-stu-id="5ec4a-102">SQL Server Compact Edition Connection Manager Editor (All Page)</span></span>
  <span data-ttu-id="5ec4a-103">使用 [SQL Server Compact Edition 連線管理員]\*\*\*\* 對話方塊，指定連接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 資料庫的屬性。</span><span class="sxs-lookup"><span data-stu-id="5ec4a-103">Use the **SQL Server Compact Edition Connection Manager** dialog box to specify properties for connecting to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
 <span data-ttu-id="5ec4a-104">若要深入了解 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact Edition 連線管理員，請參閱 [SQL Server Compact Edition 連線管理員](connection-manager/sql-server-compact-edition-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="5ec4a-104">To learn more about the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact Edition connection manager, see [SQL Server Compact Edition Connection Manager](connection-manager/sql-server-compact-edition-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5ec4a-105">選項</span><span class="sxs-lookup"><span data-stu-id="5ec4a-105">Options</span></span>  
 <span data-ttu-id="5ec4a-106">**AutoShrink 臨界值**</span><span class="sxs-lookup"><span data-stu-id="5ec4a-106">**AutoShrink Threshold**</span></span>  
 <span data-ttu-id="5ec4a-107">以百分比指定在執行自動壓縮處理序之前， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 資料庫允許的可用空間數量。</span><span class="sxs-lookup"><span data-stu-id="5ec4a-107">Specify the amount of free space, as a percentage, that is allowed in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database before the autoshrink process runs.</span></span>  
  
 <span data-ttu-id="5ec4a-108">**預設鎖定擴大**</span><span class="sxs-lookup"><span data-stu-id="5ec4a-108">**Default Lock Escalation**</span></span>  
 <span data-ttu-id="5ec4a-109">指定在嘗試擴大鎖定之前， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 資料庫要取得的資料庫鎖定數目。</span><span class="sxs-lookup"><span data-stu-id="5ec4a-109">Specify the number of database locks that the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database acquires before it tries to escalate locks.</span></span>  
  
 <span data-ttu-id="5ec4a-110">**預設鎖定逾時**</span><span class="sxs-lookup"><span data-stu-id="5ec4a-110">**Default Lock Timeout**</span></span>  
 <span data-ttu-id="5ec4a-111">指定交易等候鎖定的預設間隔，以毫秒為單位。</span><span class="sxs-lookup"><span data-stu-id="5ec4a-111">Specify the default interval, in milliseconds, that a transaction will wait for a lock.</span></span>  
  
 <span data-ttu-id="5ec4a-112">**排清間隔**</span><span class="sxs-lookup"><span data-stu-id="5ec4a-112">**Flush Interval**</span></span>  
 <span data-ttu-id="5ec4a-113">指定已認可交易將資料排清到磁碟機之間的間隔，以秒為單位。</span><span class="sxs-lookup"><span data-stu-id="5ec4a-113">Specify the interval, in seconds, between committed transactions to flush data to disk.</span></span>  
  
 <span data-ttu-id="5ec4a-114">**地區設定識別碼**</span><span class="sxs-lookup"><span data-stu-id="5ec4a-114">**Locale Identifier**</span></span>  
 <span data-ttu-id="5ec4a-115">指定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 資料庫的地區設定識別碼 (LCID)。</span><span class="sxs-lookup"><span data-stu-id="5ec4a-115">Specify the Locale ID (LCID) of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
 <span data-ttu-id="5ec4a-116">**緩衝區大小上限**</span><span class="sxs-lookup"><span data-stu-id="5ec4a-116">**Max Buffer Size**</span></span>  
 <span data-ttu-id="5ec4a-117">指定將資料排清到磁碟之前， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 使用的記憶體數量上限 (以 KB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="5ec4a-117">Specify the maximum amount of memory, in kilobytes, that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact uses before flushing data to disk.</span></span>  
  
 <span data-ttu-id="5ec4a-118">**資料庫大小上限**</span><span class="sxs-lookup"><span data-stu-id="5ec4a-118">**Max Database Size**</span></span>  
 <span data-ttu-id="5ec4a-119">指定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 資料庫的大小上限 (以 MB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="5ec4a-119">Specify the maximum size, in megabytes, of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
 <span data-ttu-id="5ec4a-120">**Mode**</span><span class="sxs-lookup"><span data-stu-id="5ec4a-120">**Mode**</span></span>  
 <span data-ttu-id="5ec4a-121">指定用來開啟 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 資料庫的檔案模式。</span><span class="sxs-lookup"><span data-stu-id="5ec4a-121">Specify the file mode in which to open the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span> <span data-ttu-id="5ec4a-122">此屬性的預設值為 [讀取寫入]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5ec4a-122">The default value for this property is **Read Write**.</span></span>  
  
 <span data-ttu-id="5ec4a-123">模式選項有四個值，如下表所述。</span><span class="sxs-lookup"><span data-stu-id="5ec4a-123">The Mode option has four values, as described in the following table.</span></span>  
  
|<span data-ttu-id="5ec4a-124">值</span><span class="sxs-lookup"><span data-stu-id="5ec4a-124">Value</span></span>|<span data-ttu-id="5ec4a-125">描述</span><span class="sxs-lookup"><span data-stu-id="5ec4a-125">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5ec4a-126">**唯讀**</span><span class="sxs-lookup"><span data-stu-id="5ec4a-126">**Read Only**</span></span>|<span data-ttu-id="5ec4a-127">指定唯讀存取資料庫。</span><span class="sxs-lookup"><span data-stu-id="5ec4a-127">Specifies read-only access to the database.</span></span>|  
|<span data-ttu-id="5ec4a-128">**讀寫**</span><span class="sxs-lookup"><span data-stu-id="5ec4a-128">**Read Write**</span></span>|<span data-ttu-id="5ec4a-129">指定資料庫的讀取/寫入權限。</span><span class="sxs-lookup"><span data-stu-id="5ec4a-129">Specifies read/write permission to the database.</span></span>|  
|<span data-ttu-id="5ec4a-130">**排除**</span><span class="sxs-lookup"><span data-stu-id="5ec4a-130">**Exclusive**</span></span>|<span data-ttu-id="5ec4a-131">指定獨佔存取資料庫。</span><span class="sxs-lookup"><span data-stu-id="5ec4a-131">Specifies exclusive access to the database.</span></span>|  
|<span data-ttu-id="5ec4a-132">**共用讀取**</span><span class="sxs-lookup"><span data-stu-id="5ec4a-132">**Shared Read**</span></span>|<span data-ttu-id="5ec4a-133">指定其他使用者可同時讀取資料庫。</span><span class="sxs-lookup"><span data-stu-id="5ec4a-133">Specifies that other users can read from the database at the same time.</span></span>|  
  
 <span data-ttu-id="5ec4a-134">**保存安全性資訊**</span><span class="sxs-lookup"><span data-stu-id="5ec4a-134">**Persist Security Info**</span></span>  
 <span data-ttu-id="5ec4a-135">指定是否將安全性資訊當做連接字串的一部分傳回。</span><span class="sxs-lookup"><span data-stu-id="5ec4a-135">Specify whether security information is returned as part of the connection string.</span></span> <span data-ttu-id="5ec4a-136">這個選項的預設值是 **False**。</span><span class="sxs-lookup"><span data-stu-id="5ec4a-136">The default value for this option is **False**.</span></span>  
  
 <span data-ttu-id="5ec4a-137">**暫存檔目錄**</span><span class="sxs-lookup"><span data-stu-id="5ec4a-137">**Temp File Directory**</span></span>  
 <span data-ttu-id="5ec4a-138">指定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 暫存資料庫檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="5ec4a-138">Specify the location of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact temporary database file.</span></span>  
  
 <span data-ttu-id="5ec4a-139">**資料來源**</span><span class="sxs-lookup"><span data-stu-id="5ec4a-139">**Data Source**</span></span>  
 <span data-ttu-id="5ec4a-140">指定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="5ec4a-140">Specify the name of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
 <span data-ttu-id="5ec4a-141">**密碼**</span><span class="sxs-lookup"><span data-stu-id="5ec4a-141">**Password**</span></span>  
 <span data-ttu-id="5ec4a-142">輸入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 資料庫的密碼。</span><span class="sxs-lookup"><span data-stu-id="5ec4a-142">Enter the password for the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ec4a-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ec4a-143">See Also</span></span>  
 <span data-ttu-id="5ec4a-144">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="5ec4a-144">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="5ec4a-145">SQL Server Compact Edition 連線管理員編輯器 &#40;連接頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="5ec4a-145">SQL Server Compact Edition Connection Manager Editor &#40;Connection Page&#41;</span></span>](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-connection-page.md)  
  
  
