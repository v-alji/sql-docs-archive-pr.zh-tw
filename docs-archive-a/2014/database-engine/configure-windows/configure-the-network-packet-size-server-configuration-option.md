---
title: 設定 network packet size 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default packet size
- size [SQL Server], packets
- packets [SQL Server], size
- network packet size option
ms.assetid: 236985bf-fc4a-4a57-98f7-a71ef977fd7b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 69e5963675349bceff6a0ee022f6dc28da03db59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700210"
---
# <a name="configure-the-network-packet-size-server-configuration-option"></a><span data-ttu-id="83f82-102">設定 network packet size 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="83f82-102">Configure the network packet size Server Configuration Option</span></span>
  <span data-ttu-id="83f82-103">本主題描述如何 `network packet size` 使用或，在中設定 server configuration 選項 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="83f82-103">This topic describes how to configure the `network packet size` server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="83f82-104">`network packet size`選項會設定在整個網路上使用的封包大小 (位元組) 。</span><span class="sxs-lookup"><span data-stu-id="83f82-104">The `network packet size` option sets the packet size (in bytes) that is used across the whole network.</span></span> <span data-ttu-id="83f82-105">封包是在用戶端與伺服器之間傳送要求與結果的固定大小資料區塊。</span><span class="sxs-lookup"><span data-stu-id="83f82-105">Packets are the fixed-size chunks of data that transfer requests and results between clients and servers.</span></span> <span data-ttu-id="83f82-106">預設的封包大小為 4096 個位元組。</span><span class="sxs-lookup"><span data-stu-id="83f82-106">The default packet size is 4,096 bytes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="83f82-107">除非確信有助於提升效能，否則請勿變更封包大小。</span><span class="sxs-lookup"><span data-stu-id="83f82-107">Do not change the packet size unless you are certain that it will improve performance.</span></span> <span data-ttu-id="83f82-108">對於大部分應用程式而言，預設封包大小是最適當的大小。</span><span class="sxs-lookup"><span data-stu-id="83f82-108">For most applications, the default packet size is best.</span></span>  
  
 <span data-ttu-id="83f82-109">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="83f82-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="83f82-110">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="83f82-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="83f82-111">限制事項</span><span class="sxs-lookup"><span data-stu-id="83f82-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="83f82-112">建議</span><span class="sxs-lookup"><span data-stu-id="83f82-112">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="83f82-113">安全性</span><span class="sxs-lookup"><span data-stu-id="83f82-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="83f82-114">**使用下列方法設定 network packet size 選項：**</span><span class="sxs-lookup"><span data-stu-id="83f82-114">**To configure the network packet size option, using:**</span></span>  
  
     [<span data-ttu-id="83f82-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="83f82-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="83f82-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="83f82-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="83f82-117">**後續操作：** [設定網路封包大小 選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="83f82-117">**Follow Up:**  [After you configure the network packet size option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="83f82-118">開始之前</span><span class="sxs-lookup"><span data-stu-id="83f82-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="83f82-119">限制事項</span><span class="sxs-lookup"><span data-stu-id="83f82-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="83f82-120">加密連接的最大 network packet size 為 16,383 個位元組。</span><span class="sxs-lookup"><span data-stu-id="83f82-120">The maximum network packet size for encrypted connections is 16,383 bytes.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="83f82-121">建議</span><span class="sxs-lookup"><span data-stu-id="83f82-121">Recommendations</span></span>  
  
-   <span data-ttu-id="83f82-122">這個選項是進階選項，只有有經驗的資料庫管理員或通過認證的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術人員才可變更。</span><span class="sxs-lookup"><span data-stu-id="83f82-122">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="83f82-123">如果應用程式進行大量複製作業，或是傳送或接收大量的文字或影像資料，則使用大於預設值的封包有助於改善效能，因為這樣可以減少網路讀取與寫入的作業。</span><span class="sxs-lookup"><span data-stu-id="83f82-123">If an application does bulk copy operations or sends or receives large amounts of text or image data, a packet size larger than the default might improve efficiency because it results in fewer network read-and-write operations.</span></span> <span data-ttu-id="83f82-124">如果應用程式傳送與接收的資訊量很少，可以將封包大小設定為 512 位元組，這對大部分資料傳輸而言已經足夠。</span><span class="sxs-lookup"><span data-stu-id="83f82-124">If an application sends and receives small amounts of information, the packet size can be set to 512 bytes, which is sufficient for most data transfers.</span></span>  
  
-   <span data-ttu-id="83f82-125">在使用不同網路通訊協定的系統上，請將 [網路封包大小] 設定為最常用通訊協定的大小。</span><span class="sxs-lookup"><span data-stu-id="83f82-125">On systems that are using different network protocols, set network packet size to the size for the most common protocol used.</span></span> <span data-ttu-id="83f82-126">當網路通訊協定支援大型封包時，network packet size 選項可以改善網路效能。</span><span class="sxs-lookup"><span data-stu-id="83f82-126">The network packet size option improves network performance when network protocols support larger packets.</span></span> <span data-ttu-id="83f82-127">用戶端應用程式可以覆寫此值。</span><span class="sxs-lookup"><span data-stu-id="83f82-127">Client applications can override this value.</span></span>  
  
-   <span data-ttu-id="83f82-128">您也可以呼叫 OLE DB、開放式資料庫連接 (ODBC) 及 DB-Library 函數來要求變更封包大小。</span><span class="sxs-lookup"><span data-stu-id="83f82-128">You can also call OLE DB, Open Database Connectivity (ODBC), and DB-Library functions request a change the packet size.</span></span> <span data-ttu-id="83f82-129">如果伺服器無法支援要求的封包大小， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 將會傳送警告訊息給用戶端。</span><span class="sxs-lookup"><span data-stu-id="83f82-129">If the server cannot support the requested packet size, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] will send a warning message to the client.</span></span> <span data-ttu-id="83f82-130">在某些情況下，變更封包大小可能會導致通訊連結失敗，例如以下狀況：</span><span class="sxs-lookup"><span data-stu-id="83f82-130">In some circumstances, changing the packet size might lead to a communication link failure, such as the following:</span></span>  
  
     `Native Error: 233, no process is on the other end of the pipe.`  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="83f82-131">Security</span><span class="sxs-lookup"><span data-stu-id="83f82-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="83f82-132">權限</span><span class="sxs-lookup"><span data-stu-id="83f82-132">Permissions</span></span>  
 <span data-ttu-id="83f82-133">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="83f82-133">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="83f82-134">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="83f82-134">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="83f82-135">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="83f82-135">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="83f82-136">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="83f82-136">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-network-packet-size-option"></a><span data-ttu-id="83f82-137">設定 network packet size 選項</span><span class="sxs-lookup"><span data-stu-id="83f82-137">To configure the network packet size option</span></span>  
  
1.  <span data-ttu-id="83f82-138">在物件總管中，請以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="83f82-138">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="83f82-139">按一下 **[進階]** 節點。</span><span class="sxs-lookup"><span data-stu-id="83f82-139">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="83f82-140">在 **[網路]** 下，為 **[網路封包大小]** 方塊選取一個值。</span><span class="sxs-lookup"><span data-stu-id="83f82-140">Under **Network**, select a value for the **Network Packet Size** box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="83f82-141">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="83f82-141">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-network-packet-size-option"></a><span data-ttu-id="83f82-142">設定 network packet size 選項</span><span class="sxs-lookup"><span data-stu-id="83f82-142">To configure the network packet size option</span></span>  
  
1.  <span data-ttu-id="83f82-143">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="83f82-143">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="83f82-144">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="83f82-144">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="83f82-145">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="83f82-145">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="83f82-146">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `network packet size` 選項的值設定為 `6500` 個位元組。</span><span class="sxs-lookup"><span data-stu-id="83f82-146">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `network packet size` option to `6500` bytes.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'network packet size', 6500 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="83f82-147">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="83f82-147">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-network-packet-size-option"></a><a name="FollowUp"></a> <span data-ttu-id="83f82-148">後續操作：設定網路封包大小選項之後</span><span class="sxs-lookup"><span data-stu-id="83f82-148">Follow Up: After you configure the network packet size option</span></span>  
 <span data-ttu-id="83f82-149">設定會立即生效，不需要重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="83f82-149">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83f82-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83f82-150">See Also</span></span>  
 <span data-ttu-id="83f82-151">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="83f82-151">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="83f82-152">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="83f82-152">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="83f82-153">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83f82-153">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
